---
layout: post
title:  "Automating Text Messages with Tasker"
date:   2015-11-20 8:00 PM
tags: [communication, productivity]
---
My wife likes to know when I'm going to be home after work. She often makes dinner for the whole family or the kids need something from me or she simply wants to know when her relief is going to arrive.

My commute from the office to home can range from 45 minutes to 1.5 hours. So sending my wife a message to let her know I'm on the way is super helpful. Except I always forget. For a long time she'd remind me and I'd continue to forget.

It took an automated solution to get the task off my list and ensure it was done each time I leave work.

Here's the basics of what I did. I use a mobile Android app called [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) ($3 US) which runs various user-configured profiles. When I connect to my work Wi-Fi Tasker configures my phone for work. It's doing simple things such as turning the media volume down and setting the phone to vibrate on notifications. It's also continually looking at the time of day and will send my wife a text if I'm still at the office late in the day.

Additionally, when I finally leave the office (disconnect from my work Wi-Fi) Tasker will send her another text message letting her know I've left. All of these messages are tagged with *--autosent from my phone* at the end so she knows which messages are automated and when it's really me.

Here are some screenshots of the Tasker configuration.

![Tasker profiles]({{ site.url }}/images/posts/2015-11-20/tasker-profiles.png)

This screenshot shows a profile called *Work*. When I connect to my office Wi-Fi network, the task called *At Work* executes. This task does things like silence my phone.

When I disconnect from my office Wi-Fi, the task called *Leave Work* executes. We'll explore what this does below.

![Tasker leave work]({{ site.url }}/images/posts/2015-11-20/tasker-leave-work.png)

This screenshot shows the details of the *Leave Work* task. It's pretty much reversing settings the *At Work* task configured. The last step of the workflow is the key.

![Tasker send sms]({{ site.url }}/images/posts/2015-11-20/tasker-send-sms.png)

This screenshot shows the configuration of the *Send SMS* step in the *Leave Work* task. Here I configure the destination phone number, the message I want to text, and some conditional logic. I only want a text to be sent if I'm leaving the office Monday - Friday after 5:00pm. This logic keeps me from sending texts if I go out for lunch or work on a weekend.

Tasker is an amazing little app and this is only a small sampling of what it can do. It's certainly helped me better communicate with my family without having to think about it. You can do a search online and find all sorts of useful recipes if you're interested in automating you're life and/or mobile experience.
