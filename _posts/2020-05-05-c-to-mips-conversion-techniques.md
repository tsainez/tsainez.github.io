---
layout: post
title:  "C to MIPS Conversion Techniques"
date:   2020-05-05 01:28:00 -0700
tag: computer science
comments: true
---
<p class="meta">05 May 2020</p>

# Comparisons

If you are using any comparisons in C, the equivalent instruction in MIPS is the opposite. So, given that `$t0` maps to `x`, `$t1` maps to `y` , you have the following C code:

{% highlight c %}
if (x == y) {
    // do something...
    } else {
    // do something else...
}
{% endhighlight %}

becomes in MIPS:

{% highlight mips %}
        bne $t0,    $t1,    else
        # do something...
        j after
else:   
        # do something else
        j after
after:
        # the program continues...
{% endhighlight %}

Notice the inclusion of the else clause is optional, and you could remove it entirely and only have to change where the `bne` instruction branches to— which is probably the `after` label.

# Loops

Generally, `while` and `for` loops vary only slightly from conditionals. Here's a few examples that are fully fleshed out.

Given `$t0` maps to `x`, `$t1` maps to `y` and `$t2` maps to `z`, we can have the following C code:

{% highlight c %}
while (x <= y) {
    x = x * z;
}
{% endhighlight %}

which then becomes in MIPS:

{% highlight MIPS %}
while:  bgt $t0,    $t1,    after
        mul $t0, $t0, $t2
        j while
after: 
{% endhighlight %}

Notice it follows the same pattern as the comparisons listed previously, but we've only changed it so that the branch instruction exits the loop, which makes sense. We want to break only when `x <= y`, so the instructions continue until it will *when* `$t0` *is greater than* `t1`.

`for` loops follow a similar process, though it is more useful to think of them as `while` loops written with a different syntax. Consider the following loop in C:

{% highlight c %}
for(int i = 0, i < y, i++) {
    // do something!
}
{% endhighlight %}

This can be similarly expressed as:

{% highlight c %}
int i = 0;
while (i < y) {
    // do something!
    i++;
}
{% endhighlight %}

Now we can use the same conventions we knew from before and create the final MIPS code:

{% highlight MIPS %}
        addi $t0,   $zero,  0       # int i = 0
while:  bge $t0,    $t1,    after   # while ( i < y) 
        # do something!
        j while
after:
{% endhighlight %}

# Functions

A good example of a very basic function in C would be the following:

{% highlight c %}
int max(int x, int y) {
    if (x > y)
        return x;
    else
        return y;
}
{% endhighlight %}

The above C code will become the following MIPS code.

{% highlight MIPS %}
max:
        slt $t0,    $a0,    $a1
        bne $t0,    $zero,  maxy
        add $v0,    $zero,  $a0
        
        j   end
        
        maxy:   add $v0,    $zero,  $a1
        end:    jr  $ra
{% endhighlight %}

This code uses the proper register conventions, where `$v0` is the return value and `$a0` and `$a1` are `x` and `y` respectively, since they are the arguments of the `max` function.

Notice that there's a few statements here that could easily be shortened, most notably `add $v0,    $zero,  $a0` could be a `move   $v0,  $a0`. 

# Using the Stack
Things can get messy really quickly if you're calling subroutines within subroutines, or if you're using `syscall` inside of a subroutine. That's why using the stackpointer to save values can be very useful.

Some general rules,

* `lw` is used to load arguments.
* `sw` is used to store the return value or other data that requires persistence.

So, for instance, the `max` function we examined earlier might look something like this:

{% highlight MIPS %}
max:
    lw  $t0,    8($sp)  # load x from the stack
    lw  $t1,    4($sp)  # load y from the stack

    slt $t3,    $t0,    $t1
    bne $t3,    $zero,  maxy
    sw  #t0,    0($sp)  # save the return value
    j end
    
    maxy:   sw  $t1,    0($sp)  # save the return value
    
    end:    jr $ra
{% endhighlight %}

Note that we count backwards using the stack pointer, and we keep the pointer word aligned by only incrementing and decrementing in multiples of 4.  

# Recursion
Recursion requires a mastery of all the aforementioned techniques. 

Let's look at an example: calculating the factorial of a number n. You would write this in C like so:

{% highlight c %}
int factorial(int n) {
    if (n < 1)
        return 1;
    else
        return  n * factorial(n-1);
}
{% endhighlight %}

You would convert this to the following MIPS code:

{% highlight MIPS %}
factorial:
    addi    $sp,    $sp,    -8  # save space for 2 words.
    sw  $ra,    4($sp)          # keep $ra safe, this is no leaf function!
    sw  $a0,    0($sp)          # store arg
    
    slti    $t0,    $a0,    1   # n < 1?
    beq $t0,    $zero,  label
    
    # if so, return 1
    addi    $v0,    $zero,  1
    
    addi    $sp,    $sp,    8   # pop 2 words
    jr  $ra
    
    label:  # n > 1, we must recurse
    addi    $a0,    $a0,    -1  # decrement n
    jal fact
    
    lw  $a0,    0($sp)  # restore the original n
    lw  $ra,    4($sp)  # restore original $ra
    addi    $sp,    $sp,    8   # pop 2 words
    
    mul $v0,    $a0,    $v0 # mult for result
    jr  $ra
{% endhighlight %}

Remember: the argument is in `$a0` and the result is stored in `$v0` following register conventions. 