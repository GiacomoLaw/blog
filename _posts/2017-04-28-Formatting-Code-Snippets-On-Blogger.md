---
layout: post
title:  "Formatting Code Snippets on Google Blogger"
author: giacomo
categories: [ web ]
tags: [ html ]
image: https://github.com/GiacomoLaw/blog/raw/master/images/html_on_blog.PNG
description: "A guide on formatting code snippets on Google Blogger."
---

Lots of people use Blogger to host their blogs, but little know that you can actually edit the CSS that Blogger displays. It's one of the most powerful Blogger features, and lets you truly customize your blog. You can get rid of elements you don't like, change the look of content in your posts, and so much more.

I often have snippets of code on my large blog, [The Nerdy Student](thenerdystudent.com), however Blogger never actually formatted those pieces of code. I had to go into the HTML editor, and add `<code>` to every piece of code, however that only changed the font. 

I decided that the CSS editor may allow me to change this - and to my suprise, it did! I knew you could edit the look of the site with it, but I didn't know you could edit the look of the post content.

![Click the customize button in the Theme tab](https://github.com/GiacomoLaw/blog/raw/master/images/1.PNG)

You then scroll down to the advanced section, and click 'Edit CSS'.

![Hit Advanced, scroll down, and then select CSS](https://github.com/GiacomoLaw/blog/raw/master/images/editingcss.PNG)

I decided to use the Bootstrap style code for my blog - I had used it on many websites before, and I loved the way it looked. I entered this in the box below pre-existing CSS:

{% highlight html %}
code {
  font-family: monospace, monospace;
  font-size: 1em;
    padding: 0.2rem 0.4rem;
  font-size: 90%;
  color: #bd4147;
  background-color: #f7f7f9;
  border-radius: 0.25rem;
}
{% endhighlight %}

And done! I hit save, and now my code snippets on my blog look nice.

![The code snippets as seen in my [Bear Notes](http://www.thenerdystudent.com/2017/02/bear-notes-write-beautifully-on-iphone.html) review](https://github.com/GiacomoLaw/blog/raw/master/images/html_on_blog.PNG)

Thanks for reading!
