---
layout: post
title: "Using ChatGPT to make a blog"
---

# Using ChatGPT to make a blog
As an experiment, let's see if [ChatGPT Jan 9 Version](https://help.openai.com/en/articles/6825453-chatgpt-release-notes) can be wrangled to create a blog. 

When it's asked "*please help me design a blog that I can develop on GitHub on a Windows and Mac device*," it basically outputs a list of instructions for you to follow. They are as follows:

> 1. **Choose a static website generator**: A static website generator, such as Jekyll or Hexo, will help you create a blog that is easy to host on GitHub.
> 2. **Install Git**: Git is a version control system that is required to work with GitHub. You can download it from the official website (https://git-scm.com/downloads) and install it on your Windows or Mac device.
> 3. **Create a GitHub account**: You will need a GitHub account to host your blog on the platform. Sign up for an account on the GitHub website (https://github.com/).
> 4. **Create a new repository**: Once you have a GitHub account, you can create a new repository for your blog. Give it a name and make it public.
> 5. **Create the blog**: Use your static website generator to create the basic structure of your blog. You can customize the layout, add pages, and create posts.
> 6. **Push the code to GitHub**: Once you've finished creating your blog, you can push the code to your GitHub repository. You can use Git commands to do this or use a Git client like SourceTree.
> 7. **Configure GitHub Pages**: GitHub Pages allows you to host your website directly from a GitHub repository. Go to the settings of your repository and enable GitHub Pages.
> 8. **Customize your domain**: You can purchase a custom domain and configure it to point to your GitHub Pages site.
> 9. **Test your blog**: Once your blog is live on GitHub Pages, you can test it to make sure everything is working correctly.
> 10. **Update and maintain your blog**: You can continue to make changes and updates to your blog by pushing new code to your GitHub repository.

The next prompt I entered was: *is there a cross-platform IDE that works for both Mac and Windows for this particular usecase?*

> "Yes; There's [Visual Studio Code](https://code.visualstudio.com/) [*which is what I use*], Atom [*which has now been sunset since December 15, 2022...*], [Sublime Text](https://www.sublimetext.com/) and [Brackets](https://brackets.io/)."

## Troubleshooting
In order to see if this thing really can be useful to me as a tool, I wanna see if it can help me troubleshoot. I set up this website a really long time ago and now I can't run it on my Windows PC anymore! Let's see if ChatGPT can help me get this back up and running natively so that I can test it out before I deploy it to the internet.

I know! I'll give ChatGPT a monologue. I'm gonna be extra lazy about this and give it all the details it needs to get the job done. Extra handholding!

> I have a Jekyll project configured in Visual Studio on my Windows 10 machine. But when I type 'bundle exec jekyll serve' into the terminal it just says 'bundle' is not recognized as an internal or external command,
operable program or batch file.

It spits out:

> This error message occurs when the bundle command is not recognized by the command prompt on your Windows machine. It means that the bundle command, which is used to manage dependencies in a Ruby project, is not installed or is not in the system's PATH.

> To fix this issue, you can try the following:

> 1. Install the bundler gem: bundle is a Ruby gem that is used to manage dependencies in a Ruby project. You can install it by running gem install bundler in the command prompt.

> 2. Check the Ruby version: Make sure that you are using the correct version of Ruby. Jekyll requires version 2.4 or higher. You can check your current version by running ruby -v in the command prompt.

> 3. Update your PATH: Make sure that the folder containing the bundle command is included in your system's PATH. This will allow the command prompt to find the command and execute it.

> 4. Reinstall Jekyll: If the above steps don't work, you may need to reinstall Jekyll. You can do this by running gem install jekyll in the command prompt.

> 5. If you have multiple version of ruby installed on your machine and you are not sure which one you are using, you can use chruby to switch between the versions.

> It's worth noting that, in addition to the aforementioned solutions, you can use the windows subsystem for Linux (WSL) to run Jekyll on Windows, it will give you a Linux environment and you can use Jekyll as it is on a Linux machine.

> After you have done the above steps, you should be able to run the bundle exec jekyll serve command without any issues, and the Jekyll server should start running.

Indeed, I did not have Ruby installed on this PC yet, so I went ahead and did that and the ran `gem install jekyll` successfully in the terminal.