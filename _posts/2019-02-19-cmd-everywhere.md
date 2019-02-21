---
layout: post
title:  "Save time with .bat files"
author: giacomo
categories: [ localdev ]
image: images/2019-02-19-cmd/batfiles.png
featured: true
description: "How to run .bat files from anywhere on Windows CMD like a command."
---

If you often type in the same repetitive commands on your CMD, .bat files are a great way to speed up your workflow. Essentially, you can create a .bat file to quickly run a script. For a simple example, if I wanted to build a site with Jekyll, usually I would have to type `set JEKYLL_ENV=production` to set Jekyll to build for a production environment, then type out `bundle exec jekyll build` to build the site. However, with .bat files, I can simply run the file from the command line and it runs it automatically.

The issue I faced is that I wanted to add the .bat name as a command that I could execute in any folder I wanted. Luckily, this is incredibly easy to do.

1. Put all your .bat files into a folder. I put mine into a scripts folder under /documents for easy access.
2. Copy the address of the folder.
3. Search for environment variables in Windows search. Select the 'Edit the system environment variables'.
4. In the Window that pops up, hit the 'Environment Variables' button.
5. You should see an option for `Path` like below. Click on it, and then click 'Edit'.
6. Click 'New' on the right side.
7. Paste in your address of the folder that you copied in step 2.

![Path]({{ site.baseurl }}/images/2019-02-19-cmd/pathloc.png)

Now you are done! You can call your .bat files by typing their names into the CMD.

![Path]({{ site.baseurl }}/images/2019-02-19-cmd/batfiles.png)

I use this a lot when working with this blog and a few other Jekyll sites. It lets me serve, and build them, in a second instead of having to type out the command.