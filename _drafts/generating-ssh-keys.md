---
layout: post
title:  "Generating SSH Keys on Mac OS X"
#date:   2015-07-19 8:07 AM
categories:
---
Generating an SSH key without a password. For example, for passphraseless old school Hadoop clusters. This is generally done from within a users home directory such as /Users/username on Mac.
```
ssh-keygen -t rsa -P ""
```

Generating an SSH key with a password. This is generally done from within a users home directory such as /User/aaron on Mac.
```
ssh-keygen -t rsa
```

How to copy a generated SSH key to the Mac clipboard
```
cat ~/.ssh/id_rsa.pub | pbcopy
```
