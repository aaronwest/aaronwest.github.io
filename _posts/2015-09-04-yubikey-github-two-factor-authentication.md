---
layout: post
title:  "YubiKey and GitHub Two-factor Authentication"
date:   2015-09-04 2:50 PM
tags: [security, yubikey, github]
---
I was able to get my YubiKey Edge working with [GitHub Fwo-factor Authentication](https://github.com/blog/1614-two-factor-authentication) recently. On github.com I went through the two-factor setup and selected the authentication app option. When I got to the screen with the QR code I launched the YubiKey Authenticator app on Mac OS X Yosemite (10.10.x) and plugged in my YubiKey Edge. I then chose the _File -> Add_ option in the menubar. I actually had to click back and forth between the YubiKey Authenticator icon in the Dock and any other app icon in order to get the YubiKey Authenticator menu to show in the menubar on OS X. Once it was displayed I could click _File -> Add_.

![YubiKey menubar]({{ site.url }}/images/posts/2015-09-04/yubikey-authenticator-menubar.png)

Next, I went back to github.com and copied the text version of the QR code secret key and pasted it into the _Secret key (base32)_ field in the YubiKey Authenticator app. I selected the _Slot 2_ radio button, ticked the box for _Require touch_, ensured _Number of digits_ was set to 6 and pressed Ok. This wrote the configuration to Slot 2 on my YubiKey Edge.

With the configuration written to my device I was able to touch the YubiKey Edge button to generate a code, copy the code to my clipboard, and paste it on github.com completing the two-factor set up process. After I did that I signed out of GitHub and walked through the sign-in process a few times to make sure everything was working. After entering a valid username/password combo on GitHub the site asks for an authentication code. I simply switched to the YubiKey Authenticator OS X app, pressed the device button to generate a code, and then used the clipboard icon in the app to copy the code. Switching back to my browser I pasted the code and was logged in.

One big downside to setting up authentication on GitHub with a YubiKey Edge is logging into the website on your mobile device. When you are out of the office or otherwise away from your computer you won't be able to log into the site using your YubiKey Edge. Instead, you must generate a backup SMS message or use a backup authentication code you've stored elsewhere.

This isn't so much an issue if you have the YubiKey NEO device. It supports NFC (near field communication) and can be used in conjunction with the [Yubico Authenticator](https://play.google.com/store/apps/details?id=com.yubico.yubioath) mobile application (Android only).

Given the mobile login constraints with the YubiKey Edge I decided to switch my GitHub settings back to Google Authenticator.
