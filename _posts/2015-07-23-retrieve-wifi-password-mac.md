---
layout: post
title:  "How to Retrieve Your Wi-Fi Password on Mac"
date:   2015-07-23 8:00 AM
tags: [cli, os x]
---
I don't generally forget the password for Wi-Fi networks I use, mainly because I use [1Password](http://www.1password.com) to store all secrets. But, I ran across the ability to retrieve the password, in plain text, from the OS X Keychain of an SSID I've previously connected with. Not a huge amount of utility to this but it's interesting the capability exists.

In the command below I read the the keychain and hone in on just the password portion. Replace `<SSID_NAME>` with the name of of a valid SSID you've connected with in the past. Keep in mind case sensitivity matters. You can leave off `| grep password` and retrieve the whole item too. This command requires authentication so you'll be asked to enter your username and password.

```bash
security find-generic-password -ga <SSID_NAME> | grep password
```

There's lots more the `security` program can do. Read the man pages and you'll see a list of available commands such as: `create-keypair`, `add-generic-password`, `list-keychains`.
