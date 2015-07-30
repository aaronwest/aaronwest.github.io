---
layout: post
title:  "Exporting and Importing GitHub Labels"
date:   2015-07-30 10:46 AM
tags: [cli, github]
---
At work we're in the process of migrating all of our code repositories from [Bitbucket](https://bitbucket.org/) to [GitHub](https://github.com). Our main driver for this change, and something I should probably write about here, is integrating all of our project management and process orchestration in one tool. This brings our issue management, project planning, state visualization, and more into the tool we use to manage code.

A large part of the migration process is moving our individual repos and getting them set up like they were on Bitbucket. One of these tasks is configuring GitHub Labels in each repo/project. We have a documented and standardized set of labels and I began the process by manually adding each label into the first repo. Then I did the same thing for a second repo. It's fairly tedious work so I looked around to see if you could export/import labels in GitHub.

I found a solution but it wasn't something offered by GitHub natively.

## Export existing labels as JSON

The first step is to export the labels in an existing repo. I found some [JavaScript code](https://gist.github.com/MoOx/93c2853fee760f42d97f) that did this. The code is also below. To use it I navigated to a repo with the labels already configured like I wanted. Then I opened the JS console, pasted the code below, and ran it. This created a JSON data set in the console which I copied into a new file called `github-labels.json` on my Mac.

```javascript
var labels = [];
[].slice.call(document.querySelectorAll(".label-link"))
.forEach(function(element) {
  labels.push({
    name: element.textContent.trim(),
    // using style.backgroundColor might returns "rgb(...)"
    color: element.getAttribute("style")
      .replace("background-color:", "")
      .replace(/color:.*/,"")
      .trim()
      // github wants hex code only without # or ;
      .replace(/^#/, "")
      .replace(/;$/, "")
      .trim(),
  })
})
console.log(JSON.stringify(labels, null, 2))
```

## Install `github-labels` package via NPM

Next, I used a tool called [`git-labels`](https://github.com/popomore/github-labels) to read the saved JSON file on my Mac and import the labels, including the corresponding color value, into a new testing repo. You can review `git-labels` [here](https://github.com/popomore/github-labels).

Install `git-labels` as a global NPM module.

```bash
npm install -g github-labels
```

With `git-labels` installed there are two choices for importing labels into an existing repo. You can read from the saved JSON file and append to an existing label set or you can overwrite all the labels in the repo. For my use case, the overwrite method provided exactly what I needed.

Change the path and filename to your JSON file, `user` with your GitHub username or organization name, and `repo` with your repository name.

_Add labels from JSON to existing GitHub labels (no overwrite)_

```bash
labels -c /path/to/github-labels.json user/repo
```

_Overwrite all existing GitHub labels with labels from JSON file_

```bash
labels -c /path/to/github-labels.json -f user/repo
```
