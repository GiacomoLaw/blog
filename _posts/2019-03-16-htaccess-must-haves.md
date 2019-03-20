---
layout: post
title:  "What should you have in your .htaccess?"
author: giacomo
categories: [ Web ]
tags: [ server side ]
image: images/2019-03-16-htaccess/cover.png
description: "Important snippets to include in your servers .htaccess to make your site better."
---

Whilst many people say that <a href="https://www.quora.com/Will-too-many-lines-in-an-htaccess-file-slow-a-websites-load-time/answer/Jonathan-Klein-1?ch=10&share=b21f726d&srid=pns5" target="_blank">.htaccess can slow down your website</a> (<a href="https://www.danielmorell.com/guides/htaccess-seo/basics/dont-use-htaccess-unless-you-must" target="_blank">here</a> is another interesting article on it), which is true, chances are that if you run a website on an Apache server you'll have one, and you'll use it, and frankly, the slow down is only a few milliseconds even for a huge .htaccess file.

So, what do you include in it?

## HTTPS and www. sub domains
Firstly, if your site uses HTTPS (which it should to rank higher in SEO rankings), you'll want to force HTTPS across all pages.

{% highlight apache %}
# force https
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
{% endhighlight %}

This snippet will force HTTPS on all pages of your site.

But what about if you want the www. sub domain too? I use this as it means that cookies aren't carried across to other sub domains. For this, you'll want to use the following snippet (that enforces https too):

{% highlight apache %}
# force www & https
RewriteCond %{HTTP_HOST} ^example\.com$ [OR]
RewriteCond %{HTTPS} !on
RewriteRule ^(.*)$ https://www.example.com/$1 [R,L]
{% endhighlight %}

## Pretty links
I also like to remove the `.html` line endings on my sites I build, and you can do this by enabling multiviews like so:

{% highlight apache %}
# Allow links without .html ending
Options +Multiviews
{% endhighlight %}

This makes links a lot cleaner - simply refer to links as `<a href="page">` instead of `<a href="page.html">`.

## Site security
Securing your site is also very important. Whilst most hosts disable access to directory listing and .htaccess, I always like to make sure that everything is prevented from being viewed by the public. Therefore:

{% highlight apache %}
# Disable directory browsing
Options -Indexes

# Deny access to .htaccess
<Files .htaccess>
    Order allow,deny
    Deny from all
</Files>
{% endhighlight %}

You can also block access to files such as `.env` by using this:

{% highlight apache %}
# Deny access to .env
<Files .env>
    Order allow,deny
    Deny from all
</Files>
{% endhighlight %}

## Caching and site speed
Caching is also important for websites. I like to enable gzip on most of my sites, as well as set expiry headers for images and other website objects that are unlikely to change.

You can enable gzip like so. Be sure to include or exclude files you want to compress.

{% highlight apache %}
# enable gzip
<ifModule mod_gzip.c>
    mod_gzip_on Yes
    mod_gzip_dechunk Yes
    mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
    mod_gzip_item_include handler ^cgi-script$
    mod_gzip_item_include mime ^text/.*
    mod_gzip_item_include mime ^application/x-javascript.*
    mod_gzip_item_exclude mime ^image/.*
    mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</ifModule>
{% endhighlight %}

You can set caching like so:

{% highlight apache %}
# BEGIN Expire headers  
<ifModule mod_expires.c>  
        ExpiresActive On  
        ExpiresDefault "access plus 5 seconds"  
        ExpiresByType image/x-icon "access plus 2592000 seconds"  
        ExpiresByType image/jpeg "access plus 2592000 seconds"  
        ExpiresByType image/png "access plus 2592000 seconds"  
        ExpiresByType image/gif "access plus 2592000 seconds"  
        ExpiresByType image/svg+xml "access plus 2592000 seconds"
        ExpiresByType application/x-font-ttf "access plus 2592000 seconds"
        ExpiresByType application/x-font-truetype "access plus 2592000 seconds"
        ExpiresByType application/x-font-opentype "access plus 2592000 seconds"
        ExpiresByType application/x-font-woff "access plus 2592000 seconds"
        ExpiresByType application/font-woff2 "access plus 2592000 seconds"
        ExpiresByType application/vnd.ms-fontobject "access plus 2592000 seconds"
        ExpiresByType application/font-sfnt "access plus 2592000 seconds"
        ExpiresByType application/x-shockwave-flash "access plus 2592000 seconds"  
        ExpiresByType text/css "access plus 604800 seconds"  
        ExpiresByType text/javascript "access plus 216000 seconds"  
        ExpiresByType application/javascript "access plus 216000 seconds"  
        ExpiresByType application/x-javascript "access plus 216000 seconds"  
        ExpiresByType text/html "access plus 600 seconds"  
        ExpiresByType application/xhtml+xml "access plus 600 seconds"  
</ifModule>  
# END Expire headers  
{% endhighlight %}

Whilst the above way is longer, and you could cut down on lines by using `mod_headers`, I like to do it the above way as it makes it easier to change caching lengths are more readable.

## Custom error pages
Custom error pages are incredibly important - they make sites look more professional, and increase user retention. I usually make a few custom error pages for things such as PHP errors, 404s, 403s, and a few more. Here is an example of how you can refer to them in case a user encounters an error:

{% highlight apache %}
# Point to error pages
ErrorDocument 404 /errordocs/404.html
ErrorDocument 403 /errordocs/403.html
{% endhighlight %}

The above links to error pages under the `errordocs` folder. I like to separate error pages from the root directory.

## Site under maintenance
If you ever want to make a large change to your site, you can redirect users to a certain page, or even a different website entirely when the main one is under maintenance. This is also great if you are having issues on a new version of a Wordpress template, or are updating your online store.

This will redirect everyone but your IP and `127.0.0.1` to that page.

{% highlight apache %}
# redirect to maintenance page
RewriteCond %{REMOTE_ADDR}  !ip_address
RewriteCond %{REMOTE_ADDR}  !127.0.0.1
RewriteRule !offline.php$ https://www.example.com/back_soon.html [L,R=307]
{% endhighlight %}

## 301 redirection
If you move domain, you'll want to redirect users to your new domain. You can do this with .htaccess:

{% highlight apache %}
RewriteEngine On
RewriteCond %{HTTP_HOST} ^example.com [NC,OR]
RewriteCond %{HTTP_HOST} ^www.example.com [NC]
RewriteRule ^(.*)$ http://www.example.net/$1 [L,R=301,NC]
{% endhighlight %}

---

.htaccess is a great tool for those using Apache servers. It allows you to have so many options on configuring your server, and unless you are running a very basic site, is a must have. Hopefully these snippets will come in handy for your site!