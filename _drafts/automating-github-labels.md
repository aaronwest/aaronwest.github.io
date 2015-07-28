---
layout: post
title:  "Automating GitHub Labels"
date:   2015-07-31 4:43 PM
tags: [cli, github]
---

# TODO: References to add in this post.
https://github.com/popomore/github-labels
https://gist.github.com/MoOx/93c2853fee760f42d97f

#### Benefits
* keeping labels the same across repos

#### Install `github-labels` package via NPM

```bash
npm install github-labels -g
```

#### Export labels in existing repository to JSON format

Copy this code and paste it into the JS console in your browser. Run the code and copy the resulting JSON into a new file on your computer.

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

#### Add labels from JSON to existing GitHub labels (no overwrite)

labels -c ~/dev/eng-docs/github-labels.json aaronwest/labelstest

#### Overwrite all existing GitHub labels with labels from JSON file

labels -c ~/dev/eng-docs/github-labels.json -f aaronwest/labelstest
