---
layout: post
title:  "Generating SSH Keys on Mac OS X"
date:   2015-01-09 4:41 PM
tags: cli, "os x"
---
Generating an SSH key without a password. For example, for passphraseless old school Hadoop clusters. This is generally done from within a users home directory such as /Users/username on Mac.

```bash
ssh-keygen -t rsa -P ""
```

Generating an SSH key with a password. This is generally done from within a users home directory such as /User/username on Mac.

```bash
ssh-keygen -t rsa
```

How to copy a generated SSH key to the Mac clipboard. This is arguably better than manually copying and pasting.

```bash
cat ~/.ssh/id_rsa.pub | pbcopy
```
