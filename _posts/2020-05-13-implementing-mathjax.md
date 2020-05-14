---
layout: post
title:  "Implementing LaTeX through MathJax in Jekyll"
date:   2020-05-13 02:45:25 -0700
categories: latex jekyll mathjax 
---
I officially study computer science, so it's an inveitability that I might end up using $$\LaTeX$$ to showcase some pretty looking formula. But there's a lot of different ways to approach this. Here's some that I found. 

# MathJax one-liner
If you want to implement $$\LaTeX$$ in your Jekyll project in the fastest amount of time, inject this line:

{% highlight html %}
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
{% endhighlight %}

 into the `post.html` file in your `_layouts` folder. 

Since I'm basically braindead, I didn't have these files at first; they depend on your Jekyll theme. For whatever theme you use, you can use `bundle info THEME` to find them. 

After all that's done, it's as easy as `bundle update` and `bundle exec jekyll serve` afterwards in your terminal. This is the fastest way it can be done, though not necessarily the cleanest. 

Nice! Now we can MathJax to render $$\LaTeX$$. Thank you, [Ian Goodfellow](https://github.com/goodfeli).

# Using Jekyll Spaceship for MathJax
If you're looking for something a little more maintainable, check out the [Jekyll Spaceship](https://github.com/jeffreytse/jekyll-spaceship) plugin. It includes more features than $$\LaTeX$$, all of which are very useful, especially the table extension!

Installation is relatively simple! Just add `gem 'jekyll-spaceship'` to the `Gemfile` in your project directory.

You'll also need to add jekyll-spaceship to your `plugins:` section of your `_config.yml` file. Or— however you choose to organize it.

{% highlight yml %}
plugins:
  - jekyll-spaceship
{% endhighlight %}

Thank you, [Jeffrey Tse](https://github.com/jeffreytse).