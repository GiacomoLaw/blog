---
layout: post
title:  "How to easily defer CSS & JS to improve site speed"
author: giacomo
categories: [ web ]
tags: [ html, css, js ]
image: images/2019-03-19-defer/cover.png
featured: true
description: "Speeding your site up dramatically doesn't have to be hard - deferring CSS & JS can take a few seconds, and have a huge site speed impact."
---

Site speed is one of the most important things when designing a website, and it's surprising the amount of impact that loading in font files and other render blocking JS and CSS files can have on your site speed. However, luckily, there is an incredibly easy way to defer files to load them after your main site has loaded, and therefore allow the user to view content a lot quicker.

First, before your closing `body`

{% highlight javascript %}
var loadDeferredStyles = function () {
	var addStylesNode = document.getElementById("deferred-styles");
	var replacement = document.createElement("div");
	replacement.innerHTML = addStylesNode.textContent;
	document.body.appendChild(replacement);
	addStylesNode.parentElement.removeChild(addStylesNode);
};
var raf = window.requestAnimationFrame || window.mozRequestAnimationFrame ||
	window.webkitRequestAnimationFrame || window.msRequestAnimationFrame;
if (raf) raf(function () {
	window.setTimeout(loadDeferredStyles, 0);
});
else window.addEventListener('load', loadDeferredStyles);
{% endhighlight %}

This will load the items under the id of `deferred-styles` when the site is loading. After your body tag has opened, place this:

{% highlight html %}
<noscript id="deferred-styles">
	<link href="https://fonts.googleapis.com/css?family=Montserrat:800" rel="stylesheet">
	<link href="https://fonts.googleapis.com/css?family=Overpass" rel="stylesheet">
	<link rel="stylesheet" href="//use.fontawesome.com/releases/v5.0.7/css/all.css">
</noscript>
{% endhighlight %}

That's it - simply place your deferred styles in, and watch your site speed increase. Do note however you should place only non-essential items in here, such as font files, Font Awesome scripts, and anything else that you don't need instantly.