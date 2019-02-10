---
layout: post
title: Why I Chose Jekyll For My Second Review Site
---

I've had an increasing interest in anime and manga, and to have a little fun I decided to set up a second site to review this on. At first, I was going to use Wordpress, but after trying to set up add on domains, I just gave up. Besides, I wanted something light and simple, so Wordpress would defiantly not come to mind in that. I also didn't want the stress of a second Wordpress site, so I decided to use Jekyll and GitHub pages.

The URL I settled with was [takanodan.net](https://takanodan.net). This means *Band of the Hawk*, which comes from my favourite manga and anime *Berserk*. Plus, I think that the name sounds good, and the domain was £10 on Namecheap which is the domain registrar I use.

First, to find a theme. I settled with the free [Mediumish](https://github.com/wowthemesnet/mediumish-theme-jekyll) theme. I wanted a free theme as I didn't want to spend too much on the second site, however I wanted something that looked professional and that worked well on GitHub pages. I needed something that would be able to cope with tons of review posts, and something which would allow the user to sort and search the reviews. Luckily, Mediumish allows you to do that. The search feature also works great, so when I finally start adding more reviews users can search the posts.

Another reason I like Mediumish is that I can insert my custom CSS easily, and then use that in my own posts with HTML. For example, I give star reviews for each review, and I can simply insert my code and it shows up great. I use the following HTML:

```
<span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>
```

And in the `scss` file, I added:

```
.checked {
	color: orange;
}
```

This allows me to easily give stars at the bottom of a post. For example, in my [Slime review on the site](https://takanodan.net/slime-review/), I use the stars to give it a rating at the bottom of the page. I think it looks clean, and doesn't affect site performance.

![Star rating](/images/stars.png)

Overall, I really like Jekyll and GitHub pages. It's free, and runs really quickly. In addition, the developer of the theme I am using is very responsive to issues and questions, and the theme is maintained and new features are added which is really nice. The only thing that I have an issue with is caching, and I can't figure a way out to clear the cache. But I don't plan to update it that frequently so it shouldn't be too much of an issue.

Jekyll is great for people who don't want to spend hours sorting out site speed, issues with plugins, and so much more that Wordpress comes with. I had to do this for [The Nerdy Student](https://thenerdystudent.com), and it wasn't fun. I have to keep an eye on the site for issues, which is a pain too. But with Jekyll and [Taka No Dan](https://takanodan.net), I have no issues. The site is fast, lightweight and easy to maintain. Perfect for a side project I don't want to spend time on optimizing, but writing.