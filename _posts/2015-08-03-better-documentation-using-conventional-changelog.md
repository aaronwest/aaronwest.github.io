---
layout: post
title:  "Better Documentation Using Conventional-Changelog"
date:   2015-08-03 12:45 PM
tags: [documentation]
---
One of the things I've been playing with at work is `conventional-changelog` and the concept of generating a CHANGELOG.md for most projects. We've double-downed our effort to create more and better documentation and as part of the effort I researched ways to generate documentation automatically and have said documentation be as close to the code as possible.

Our team suggested I look at `conventional-changelog`, a tool two of our engineers were interested in baking into our process. After using it in an R&D capacity for a few weeks I feel comfortable talking about its usage.

If you check out `conventional-changelog` on their [GitHub page](https://github.com/ajoslin/conventional-changelog) you'll see this very short description in their README.

>Generate a changelog from git metadata

## Benefits of conventional-changelog

While the tool will certainly generate - and update over time - a CHANGELOG.md, and bring additional documentation nearer to commits, there are some side benefits as well.

One of these is understanding and readability of the commit log. Developer types are notorious for writing [horrible](http://whatthecommit.com/) commit [messages](http://www.stackprinter.com/export?service=stackoverflow&question=909338&printer=false&linktohome=true) which serve no purpose. They don't explain what was actually changed, where changes were made, and the motivation for making the changes. An obvious answer to this problem is to simply examine a particular commit and see which files were modified. Then, you can browse the code to see what was changed. This works. But it's a *really* terrible way to go about learning what happened in a commit. Writing commit messages using the conventions described by `conventional-changelog` is a much better solution.

>Writing clear and useful commit log messages benefits the team more than the person authoring the commit and that's important to keep in mind. It's kind of like driving a car with a passenger. Perhaps you love to go fast and do donuts. That's great and all, but the goal is to make the ride as smooth as possible.

Here's a full list of benefits I see in using `conventional-changelog`:

1. provide better documentation for team members browsing the `git log`
2. automatic generation of `CHANGELOG.md` from structured git commit messages
3. ability to ignore certain commits and not include them in `CHANGELOG.md`. This can include things such as documentation edits
4. ability to create your own language conventions or use existing language conventions (ex. AngularJS)

## The Convention of conventional-changelog

`conventional-changelog` is nothing more than formatting your commits with a particular structure. Over time, as you build up commits using the structure you create detailed metadata on how your project has changed over time. When you're ready to rollout a new version of your project or app you generate a CHANGELOG.md file which enumerates all the metadata in a very nice display. The changelog includes information on *bug fixes*, *new features*, and *breaking changes*. Each specific item is linked to its commit hash enabling team members to follow changes to the code for further analysis.

Here's a screenshot of a CHANGELOG.md I generated while testing. Other, real-world examples include [Karma Runner](https://github.com/karma-runner/karma/blob/master/CHANGELOG.md) and [AngularJS](https://github.com/angular/angular/blob/master/CHANGELOG.md).

![changelog screenshot]({{ site.url }}/images/posts/2015-08-03/changelog-screenshot.png)

The formatting of commit messages includes having a *header*, a *body*, and a *footer*. The header has a deeper format which includes a *type*, a *scope* and a *subject*. There are a number of flavors of this convention being followed today. Rather than discuss a specific one you can [research them yourself](https://github.com/ajoslin/conventional-changelog/tree/master/conventions).

## Conventional-changelog workflow

There are likely several ways you can go about incorporating `conventional-changelog` into your workflow. During my testing I ran into issues using `git tag` and `conventional-changelog` not producing a CHANGELOG.md or producing a blank file. I tried several permutations of *make changes, commit changes, generate CHANGELOG.md*, and finally settled on a workflow which seemed fitting.

1. commit everything in progress (feature branch changes, sprint work, etc.)
2. bump version in package.json or seed it with a starting value such as v0.1.0 if this is your first CHANGELOG.md iteration
3. create the CHANGELOG.md using `conventional-changelog`
4. commit package.json and CHANGELOG.md
5. tag the latest commit with `git tag` (example: `git tag -a v0.1.0 -m "Initial testing release."`)
6. rinse and repeat

## Basic installation and usage

More detail is provided in the `conventional-changelog` README, but here's the basics of installing and using `conventional-changelog`.

~~~bash
# Install the tool using npm. Since it's a CLI tool you must install with -g
npm install -g conventional-changelog

# Follow the workflow steps outlined above

# Generate CHANGELOG.md using the AngularJS convention
conventional-changelog -o CHANGELOG.md -p angular -v
~~~
