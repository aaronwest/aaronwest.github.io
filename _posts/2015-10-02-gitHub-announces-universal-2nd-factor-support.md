---
layout: post
title:  "GitHub Announces Universal 2nd Factor Support"
date:   2015-10-02 10:00 AM
tags: [security, yubikey, github]
---
I've written about [getting started with YubiKey]({% post_url 2015-07-21-getting-started-yubikey %}) and [using a YubiKey to authenticate with GitHub]({% post_url 2015-09-04-yubikey-github-two-factor-authentication %}) in the past few months. Yesterday, GitHub [announced](https://github.com/blog/2071-github-supports-universal-2nd-factor-authentication) support for [Universal 2nd Factor (U2F)](https://fidoalliance.org/specifications/overview/) and specifically, support for YubiKey devices. You can read GitHub's [announcement here](https://github.com/blog/2071-github-supports-universal-2nd-factor-authentication) and Yubico's [coverage](https://www.yubico.com/2015/10/github-yubico-u2f/).

Now, the [steps I outlined]({% post_url 2015-09-04-yubikey-github-two-factor-authentication %}) to get up and running with a YubiKey and GitHub aren't needed. With GitHub's new U2F integration you simply set up a new device from your security settings. Instructions on how to do this are [here](https://help.github.com/articles/configuring-two-factor-authentication-via-fido-u2f/).
