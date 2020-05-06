---
layout: post
title:  "Using Jekyll to Run a Blog"
date:   2020-05-05 22:51:10 -0700
categories: jekyll update
---
# Set up

I run this blog using Jekyll: here's how I did it.

As of writing, I am running macOS Catalina version 10.15.4. 

I set up the basic site using GitHub pages, and then I installed Jekyll using Homebrew. I used Homebrew since I didn't want to change my preinstalled Ruby directory.

Upon running `jekyll new .` in your GitHub pages repository, you should see a bunch of files being generated in that directory. 

You can create new posts for the blog in the  `_posts` directory; they are in the markdown file format. You can run a live-reloading version of Jekyll to watch your blog change in real time, which can be useful for making it look prettier.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

`YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Also important, at the top of your posts you should include the following code snippet:

{% highlight md %}
---
layout:     post
title:      "Using Jekyll to Run a Blog"
date:       2020-05-05 22:51:10 -0700
categories: jekyll update
---
{% endhighlight %}

That's the basic format for creating blog posts in Jekyll. 
