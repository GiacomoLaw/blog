---
layout: post
title:  "Get back the Wordpress Classic editor, and disable Guternburg in one line"
author: giacomo
categories: [ php, wordpress ]
image: images/2019-02-21-wpeditor/cover.png
featured: true
description: "How to go back the the better Wordpress Classic editor in under a minute."
---

I really don't like the Guternburg editor that Wordpress introduced in version 5, and I am certainly not alone. Suprisngly, not many people know how easy it is to revert to the old version, with simply one line of code. Here is a step by step guide on how to do it. I will be guiding you through using the Wordpress client to do it, as that is easier for more people, but for more advanced users it's best to do it via FTP.

1. Hover over `Appearance`, and then `Editor`.
2. Select `functions.php` from the right pane (see final image).
3. Go to the bottom of the file, and add this line: `add_filter('use_block_editor_for_post', '__return_false');`.
4. Save the file, clear your cache, and enjoy editing again.

![Old WP editor]({{ site.baseurl }}/images/2019-02-21-wpeditor/functions.png)

It's that easy. I also added a comment above mine, so I know what the line is for.

{% highlight php %}
// disable block editor
add_filter('use_block_editor_for_post', '__return_false');
{% endhighlight %}

As a note, if your theme is updated often, you may want to look at [using a child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/) so your changes are still in place every time you update the theme.

If you have any questions or need any help, please feel free to comment below!