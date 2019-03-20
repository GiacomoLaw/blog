---
layout: post
title:  "Setting up a HTML Email Signature"
author: giacomo
categories: [ other ]
tags: [ html ]
image: images/IMG_8713.PNG
description: "How to set up your own HTML email signature, to make your emails look better and more professional."
---

I use email a lot when, probably more than any other form of contact or social media. I decided to make a HTML email signature for myself, but found that I couldn't put the raw code into the email, and have the email render it into a signature. However, there is an easy way to get around this.

![My personal email signature](https://github.com/GiacomoLaw/blog/raw/master/images/FullSizeRender.jpeg "My personal email signature")

You can make a HTML signature as complex or as simple as you want, and there is so much flexibility in making one.

Here is my source code for my blog signature:

{% highlight html %}
<table cellpadding="0" cellspacing="0" border="0" >
    <tbody><tr>
        <td style="padding-bottom: 5px;">
            <table cellpadding="0" cellspacing="0" border="0">
                <tbody> <!-- <tr>
                    <td style="padding-bottom: 5px;"><a href="http://thenerdystudent.com"><img data-class="external" src="https://github.com/GiacomoLaw/TNS-images/raw/master/AN%20header.png" width="400px" alt="The Nerdy Student" style="display: block"></a></td>
                </tr> -->
                <tr>
                    <td style="padding-bottom: 5px; font-family: Arial; font-size: 12pt; color: rgb(51, 51, 51);"><font style="color: #333333; font-size: 12pt; font-family: Arial"><b>Giacomo Lawrance</b></font></td>
                </tr>
                
                <tr>
                    <td style="font-family: Arial; font-size: 10pt;"><font style="color: #333333; font-size: 10pt; font-family: Arial">Email:&nbsp;<a href="mailto:thenerdystudent@gmail.com" style="color: #06c">thenerdystudent@gmail.com</a></font></td>
                </tr>
                <tr>
                    <td style="font-family: Arial; font-size: 10pt;"><font style="color: #333333; font-size: 10pt; font-family: Arial">Blog:&nbsp;<a href="http://thenerdystudent.com" style="color: #06c">thenerdystudent.com</a></font></td>
                    </tr>
                    <tr>
<td style="font-family: Arial; font-size: 10pt;"><font style="color: #333333; font-size: 10pt; font-family: Arial">Website:&nbsp;<a href="http://giacomolaw.me" style="color: #06c">giacomolaw.me</a></font></td>
                </tr>
            </tbody></table>
        </td>
        <td align="right" valign="bottom" style="padding-bottom: 5px; vertical-align: bottom;">
            <table cellpadding="0" cellspacing="0" border="0">
                <tbody><tr>
                    
                    <td style="padding-left: 5px;">
                        <a href="https://www.twitter.com/GiacomoLaw">
                            
                        </a>
                    </td>
                    
                    
                </tr>
            </tbody></table>
        </td>
    </tr>
    <tr>
        <td colspan="2">
            <table cellpadding="0" cellspacing="0" border="0">
                <tbody><tr>
                    <td style="padding-bottom: 5px; padding-top: 5px;"><a href="http://thenerdystudent.com"><img data-class="external" src="https://github.com/GiacomoLaw/TNS-images/raw/master/Header.png" width="420px" alt="The Nerdy Student" style="display: block"></a></td>
                
                <a href="https://twitter.com/GiacomoLaw" target="_blank"><img src="https://github.com/GiacomoLaw/giacomolaw.github.io/raw/master/img/twitter.png" width="40px" alt="Twitter"/></a>&nbsp;
<a href="https://github.com/GiacomoLaw" target="_blank"><img src="https://github.com/GiacomoLaw/giacomolaw.github.io/raw/master/img/Github.png" width="40px" alt="Github"/></a> 
</tr>
            </tbody></table>
        </td>
    </tr>
</tbody></table>
{% endhighlight %}

It's quite long, but it does look good:

![Blog email signature](https://github.com/GiacomoLaw/blog/raw/master/images/IMG_8713.PNG "My blog email signature")

After storing my signature code into a GitHub repo, I found a very useful site that allows you to edit HTML, and see the results in real time. You can find it [here](http://htmledit.squarefree.com). 

It's pretty simple to get the resulting HTLM into the email signature - just highlight the preview and copy and paste it into your email app. In Gmail, you can just paste it straight into the signature box, and if you use [Spark for iPad and iPhone](https://itunes.apple.com/gb/app/spark-love-your-email-again/id997102246?mt=8), you can select HTML and paste it in there. 

That's it! Now you have a lovely looking HTML signature. 🙂 

> If you are unsure where to start, you could always find a email signature you like, and use that source code. Or, you could use a signature maker and use that source code, and then work of that.

Hope this helped!
