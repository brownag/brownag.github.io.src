---
title: Transitioning to hugo + R blogdown-driven blog
author: Andrew G. Brown
date: '2020-08-01'
slug: transitioning-to-hugo-r-blogdown-driven-blog
categories: []
tags: []
---

The [humus.rocks](http://humus.rocks/) website has used Drupal 7 for the last 2.5 years. I have only tapped a fraction of the resources that are available to me in the Drupal platform -- using it essentially as a glorified RSS feed aggregator and "blog".

I would much rather write my blogs in markdown -- and then I can extend that to Rmarkdown for my more code-oriented topics or any case where I need to generate some content in a programmatic way.

So, I figured out how to use [blogdown](https://bookdown.org/yihui/blogdown/), [hugo](https://gohugo.io/) and [TravisCI](https://travis-ci.org/github/brownag/brownag.github.io.src/builds) to set up a simple pipeline from my personal computer to my GitHub Page (http://brownag.github.io/) for my markdown blog posts. 

Hugo and Blogdown integrate very well into RStudio-based development. There are simple console commands as well as the "AddIns" menu that provide options to serve the local version of the site, create new posts, insert images, and more.

![humus.rocks blog driven by hugo + blogdown and developed in RStudio](/post/2020-08-01-transitioning-to-hugo-r-blogdown-driven-blog_files/hugoblogrstudiodemo.png)

The plan is that my GitHub Page, or a feed from it, would supersede the main Drupal-driven blog on [humus.rocks](http://humus.rocks/). Though, at that point, I am very close to being able to drop the Drupal dependency all together.

The other main convenience offered by Drupal is the built-in RSS feed aggregator. A cron job I set up to run on the humus.rocks server ensures the feed contents are updated on approximately an hourly cycle. What I want to possibly do is modify my blogdown theme to integrate some Javascript code to allow feeds to be read and incorporated in the main page, having the client make the connection directly to the feed. I may pre-digest my feeds using cron job and post-processing on humus.rocks then I can serve up just a small subset via the blogdown blog page.

I am currently using [XMin](https://github.com/yihui/hugo-xmin), a lightweight theme developed by Yihui Xue, the developer of blogdown, knitr and more! This theme should be relatively easy to extend for my new needs.
