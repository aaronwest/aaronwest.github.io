---
layout: post
title:  "YubiKey and GitHub"
date:   2015-07-31 4:43 PM
tags: [security, yubikey, github]
---
don't forget about the Authenticator screenshot

I was able to get my Yubikey Edge working with GitHub 2 factor auth yesterday. On github.com I went through the 2 factor setup and selected authentication app. When I got to the screen with the QR code I launched the Yubikey Authenticator app on Mac OS X Yosemite (10.10.x) and plugged in my Yubikey Edge. I then went to File -> Add. I actually had to click back and forth between the Yubikey Authenticator icon in the doc and any other app icon in order to get the Yubikey Authenticator menu to show in the menubar on OS X. Once this was done I could click File -> Add.

Then, I went back to github.com and copied the text version of the QR code secret key and pasted it into the Secret key (base32) field in the Yubikey Authenticator app. I selected the Slot 2 radio button, ticked the box for Require touch, ensured Number of digits was set to 6 and pressed Ok. This wrote the configuration to Slot 2 on my Yubikey Edge.

With the configuration in place I was then able to touch the Yubikey Edge button to generate a code, copy the code to my clipboard, and paste it on github.com completing the 2 factor set up process. After I did that I signed out of GitHub and walked through the sign-in process a few times to make sure everything was working. After entering a valid un/pw on GitHub the site asks for an authentication code. I simply switched to the Yubikey Authenticator app, pressed the device button to generate a code, and then used the clipboard icon in the app to copy the code. Switching back to the browser I pasted the code and was logged in.

One big downside to setting up auth on GitHub with a Yubikey is logging into the website on your mobile device. When you are out of the office or otherwise away from your computer you won't be able to log into the site without generating a backup SMS message or using a backup authentication code. I know there's a Yubikey Authenticator app for mobile but I haven't tested it yet and I believe it only works with the NEO / NEO-n. Ultimately, I switched my GitHub account back to Google Authenticator for 2 factor.
