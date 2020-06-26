---
layout: post
title:  "MATLAB Experiments"
date:   2020-06-15 01:58:50 -0700
tag: computer science
comments: true
---

The best way to learn is by doing (sometimes). So, here's some stuff you can do in MATLAB!

# Flower Petals
If you want to create a **rose** or a **rhodonea curve** in code, MATLAB makes it really easy.

{% highlight matlab %}
p1 = 9
p2 = 9

figure(1)

phi = (sqrt(5)-1) / 2
    
theta2 = 0:0.01:2*pi;   % Angle
k = cos(phi);           % Rotation
rho2 = 5*sin(p2*theta2).*cos(p1*theta2)+k;    %Center distance

polarplot(theta2, rho2,"-b","LineWidth",3,"MarkerFaceColor","w")
rlim([0 3.5]);
{% endhighlight %}

If you run the above code, MATLAB should spit out:

```
p1 = 9
p2 = 9
phi = 0.6180
```

Then, you look at the pretty rose you just graphed! Of course, you can change how the rose looks if you change those parameters.

![flower](/assets/flower.png)

# Approximating The Golden Ratio
The Golden Ratio is a number that can be roughly approximated in MATLAB. First, you must initialize a vector to hold the Fibonacci numbers.

{% highlight matlab %}
F = zeros(10,1)

% Input the first two Fibonacci numbers 
F(1) = 1; 
F(2) = 1;

% The following loop uses a recursive relation to calculate the
% reamining 8 Fibonacci numbers we need to find.
for i = 3:10
    F(i) = F(i-1) + F(i-2);
end
{% endhighlight %}

You may have noticed you can add comments to code in MATLAB using `%`. It's interesting that they chose this instead of the traditional `//` or even a `#`. 

So, now that we have those Fibonacci numbers, we can look at their ratio to approximate the Golden Ratio. When we take any two successive (one after the other) Fibonacci Numbers, their ratio is very close to the Golden Ratio. 

{% highlight matlab %}
ri = @(Fi, Fim1) Fi/Fim1; 

% Initialize a vector to hold the ratios for
% the Fibonacci numbers.
r = zeros(10, 1);

% Given
r(1) = 1;

% Computing the ratios using a for loop
for i = 2:10
    r(i) = ri(F(i), F(i-1));
end
{% endhighlight %}

Now, we can plot it to see how close we got. The bigger the pair of Fibonacci Numbers, the closer the approximation.

{% highlight matlab %}
x = linspace(1, 10, 10);

plot(x, r, 'LineWidth', 3)
hold on

plot (x, r(length(r)), 'r*', 'LineWidth', 2)

ylim([0.6, 2.3])
hold off
{% endhighlight %}

![golden](/assets/golden_ratio.png)

# The Mandelbrot Set

Next up, the [Mandelbrot set](https://en.wikipedia.org/wiki/Mandelbrot_set). 

Here's the code.

{% highlight matlab %}
s = 800;
k = 400;

x0 = -2;    x1 = 1;
y0 = -1.5;  y1 = 1.5;

% Produce the coordinates of a rectangular grid (x, y)
[x,y] = meshgrid(linspace(x0, x1, s), linspace(y0, y1, s));

c = x + 1i * y;
z = zeros(size(c));
P = zeros(size(c));

for n = 1:k
    z = z.^2 + c;
    P(abs(z) > 2 & P == 0) = n - s;
end

figure,
imagesc(P)
colormap jet
axis square
{% endhighlight %}

Now, here's the graph.

![mandel](/assets/mandel.png)

Neat. 