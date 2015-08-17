---
layout: post
title:  "What's This Engineering Notebook All About?"
date:   2015-08-17 8:00 AM
tags: [writing]
---
From May 5, 2002 through March 29, 2014 I blogged at trajiklyhip.com and later [aaronwest.net/blog](http://www.aaronwest.net/blog). I wrote 599 posts during this timeframe mostly on programming in Flash, Flex, and ColdFusion. Each post received, on average, 8,053 views. My most viewed post was on [installing ColdFusion 9 on CentOS Linux](http://www.aaronwest.net/blog/index.cfm/2011/2/7/Super-Guide-Installing-ColdFusion-9-on-CentOS-Linux). That post garnered 197,856 views. Total views on the blog to date are 4,823,875.

Many of my posts offered a download of sample code or a complete application. The various files have been downloaded 66,133 times with the most popular download being my twitterAIR application. I [wrote the app](http://www.aaronwest.net/blog/index.cfm/twitterAIR) in the summer of 2007 when Twitter was just getting off the ground.

It's been an amazing ride working on and supporting my technology blog for 12 years. But boy has it been a lot of work. As I've gotten older, changed jobs a few times, and become the dad of two amazing boys, my focus has changed. And the amount of time I have to spend blogging and keeping up with the website code, database, and virtual server has changed too. But, I absolutely love writing and sharing what I learn as I continue my career in technology. I don't want to quit writing and quit sharing what and how I learn but I've realized I need a new approach.

## There must be a better way

A few months ago I was doing some R&D on ways to better document the engineering process. I was also focusing on ways documentation was being approached by those working on highly scientific projects as this is an area important to one of our teams at work. I came across the *lab notebook websites* of [Carl Boettiger](http://www.carlboettiger.info/2012/09/28/Welcome-to-my-lab-notebook.html) and [Mark E. Madsen](http://notebook.madsenlab.org/labnotebook.html).

As I read about their workflow I was reminded how often I create similar notes inside Evernote. I have a fairly large notebook called *Server Config Notes* which has all kinds of useful tidbits on using Linux, Mac OS X, and various software. It's kind of become my treasure trove of experience over the years and the first place I go when I need to look up how to do something I've forgotten. If I've not created a note in the Evernote notebook I search to find what I'm looking for online. Then, I layer in my own experience and opinion given the particular situation and write about it in a new note. The next time I'm in a similar situation I know I'll have my own offline resource in Evernote to turn to.

What I found interesting as I analyzed how Boettiger and Madsen documented their work was how similar my documentation was in Evernote. I also realized how different my Evernote content was from my technology blog. Many of my notes were short and to the point. I was writing in Evernote from the perspective of sharing with my future self. By contrast, my blog posts were often written for people I assumed knew nothing about the topic I was writing. I wrote long posts and spent a ton of time putting them together because I wanted my readers to get the full story and to leave my blog with 100% of the information. In other words, I hoped I was able to provide all the details so readers wouldn't have to continue searching or visit another website. Thinking about that approach today, it seems kind of insane.

## I believe I've found an approach that will work

The irony of my blog is my approach to writing content was the number one reason I didn't write more content. It was too much work to cover everything. It took a terrible amount of energy to research all angles and attempt to answer all questions. It was exhausting. So I only wrote every once in a while.

Seeing the dramatic difference in my blog posts and my Evernote notes was eye opening. I realized I could write more content, much more frequently, if I focused on *getting in and out*. Write as if readers already have much of the information. And if there's a good reason to believe they don't, simply link to what others have contributed. I decided I wanted to try this different approach to writing online but I knew it couldn't be done at aaronwest.net/blog. It was too arduous to get content written, tested, and published.

## Time to create a new website

I was intrigued at how Boettiger and Madsen set up their lab notebook sites. I began to research the tools they used and was inspired by Tom Preston-Werner's article on [blogging like a hacker](http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html). I made a list of the things I thought I needed to make a new website support the content creation process better than my tech blog.

1. **there will be no back-end I have to manage and code**
We're talking about a static website here. No application server and no database server are allowed. This kind of scaffolding can be used in the writing process but not in the hosting and deployment side of things. Speaking of hosting, I really don't want to deal with this. I've done it for 15 years and it's no longer important I control the server where the new site will live.
2. **the software must be fast and simple**
I want to focus on the writing process and good content, not how things work. This goal kind of goes with the first. Static sites are fast since there's no app server needed to render HTML or make roundtrips to a database. Simple here also applies to the writing process. I don't want to be concerned about HTML and making things pretty. I just want to write words in text files and get them onto the site.
3. **everything should be in GitHub**
I've been using GitHub more and more. It's kind of becoming the central component to many of my daily activities personally and professionally. Thus, at a minimum all my content will be stored in a GitHub repo. If there's a way to do more from a hosting standpoint, even better.
4. **incorporate Markdown more**
Markdown is everywhere. As silly as it sounds I want to become an expert in Markdown in 2015. I know it okay now but I find myself looking up how to do things way too often. I want to incorporate Markdown in a way that lets me *level up* a bunch.

## Putting it all together

#### Jekyll

Like Boettiger and Madsen I decided to use [Jekyll](http://jekyllrb.com/) as the backbone for the new website. I chose to call this site *Aaron's Engineering Notebook* as I want it to be almost identical to my approach to writing in my *Server Config Notes* Evernote notebook. I won't cover all the features of Jekyll as you can look them up yourself. Using Jekyll crosses off goal #1, #2, and #4. Everything in Jekyll is static and all content is written in Markdown files. You generate the website locally and then publish it wherever you want. There's a great method for writing draft posts, publishing posts, and testing everything locally. It's super simple and highly customizable though I've chosen to stick with the default theme for the most part.

#### Atom

I'm a huge fan of [Sublime Text 2](http://www.sublimetext.com/) and have used it as my general purpose text/programming editor for several years. While I love Sublime and have no complaints I've been spending more and more time with Atom. Atom is fairly similar but has interesting integration with GitHub out of the box. Most of the customizations I made to Sublime I've been able to add to Atom. Playing in the world of GitHub more and more and using Atom (made by GitHub) seems like the right thing to do. At least for now.

#### GitHub Pages

For hosting I'm using [GitHub Pages](https://pages.github.com/). It's free and has [awesome integration](https://help.github.com/articles/using-jekyll-with-pages/) with Jekyll. To get started all you do is configure a GitHub repo (crossing off goal #3) using a specific naming convention. You write posts locally and test them in browser using `jekyll serve`. When a post is ready to be published you commit to Git locally and `git push` to GitHub. GitHub sees the new push, builds a new version of the static site using `jekyll build`, then deploys it to *yoursite.github.io*. And of course you can host your own domain and set up a CNAME to the github.io address. In addition to having a stellar build and deploy process, GitHub also includes an issue tracker so I can keep up with any enhancements I want to make to the site. I'm also using a Trello-style board visualization tool to keep track of everything for the site. [ZenHub.io](https://www.zenhub.io/) is a Chrome plugin that changes the native GitHub website making visualizing issues, milestones, and pull requests more awesome.

#### Uptime Butler

I'm using [Uptime Butler](https://uptimebutler.com/) to monitor website uptime and notify me when there are issues. Since the site is hosted on GitHub I can't do anything about downtime but I still want to know. Uptime Butler is fairly new and I'm giving it a test run. I currently pay [Site24x7](http://www.site24x7.com/) to monitor aaronwest.net and a few other sites and I've been a paying customer of theirs for several years. Both personally and professionally. I highly recommend them. You can view my public Uptime Butler stats [here](https://uptimebutler.com/checkpublic/93c7edbf21f47936b892f16f).

That's pretty much it. I'm excited to see where this change in direction leads. I'm always writing and documenting what I'm working on and how I solve problems. Hopefully, I can expose this process and content more in a way that helps others learn as well. If just a few people gain knowledge by reading this site it'll make it all worthwhile. If you encounter any issues or you have suggestions for ways I can improve the site please [file an issue here](https://github.com/aaronwest/aaronwest.github.io/issues).
