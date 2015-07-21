---
layout: post
title:  "Getting Started with YubiKey"
date:   2015-07-21 8:00 AM
tags: [security, yubikey]
---
About a week ago I purchased a [YubiKey Edge](https://www.yubico.com/products/yubikey-hardware/yubikey-edge/), a USB security device from [Yubico](http://www.yubico.com). The company makes [several editions of the YubiKey](https://www.yubico.com/products/yubikey-hardware/) each designed to add security to your interactions on the Internet. The most common use case of the device is functioning as a hardware component in [two-factor authentication](https://en.wikipedia.org/wiki/Two-factor_authentication). Yubico calls this 2FA while others, such as Google, refer to it as 2-step verification. In either case the point is for the end user to supply _something they know_ in conjunction with _something they physically have_ in order to authenticate with an endpoint online.

In addition to 2FA other features may be available depending on which Yubico hardware you purchase. The latest edition in the line up is the NEO and NEO-N. The full-size NEO adds NFC, smart card, OpenPGP and other encryption support. The smaller NEO-N has all the same features except for NFC.

When I began looking at the different editions I wasn't sure which to purchase. I reviewed the information Yubico provides about [individual usage](https://www.yubico.com/why-yubico/for-individuals/) and [developer usage](https://developers.yubico.com) and decided my minimum feature set would be as follows:

* support for one-time passwords (OTP)
* support for two-factor authentication (2FA) with Gmail and business Google Apps accounts, GitHub, and apps such as Evernote
* support for OATH

Two of the YubiKeys appeared to have what I wanted. The NEO/NEO-N and the Edge/Edge-N. The Edge variants were $30 at the time of purchase while the NEO variants were $50. While the $20 gap in price is hardly worth thinking about I didn't feel I needed (or wanted really) support for NFC and OpenPGP which seemed the key differentiators. I purchased the full-size Edge device over the Edge-N since I was worried about losing the smaller device. Plus, being able to attach the Edge to my keychain, something I have everywhere I go, seemed ideal.

In the week I've had the Edge I've set it up in the following ways.

## 2FA with Gmail and Google Apps

Configuring the YubiKey Edge with Gmail and Google Apps was the exact same process. And it was ridiculously quick and easy. In fact, the process was completely different than what Yubico's documentation described.

![Google 2-step authentication]({{ site.url }}/images/posts/2015-07-21/google2fa.png)

You navigate to your Google `My Account` page and then to `Sign-in Settings`. From there, go to `2-Step Verification`. As of the date of this post, you would see a set of tabs illustrated in the screenshot above. Click on the Security Keys tab and walk through the set up process. You'll start with your YubiKey unplugged, press a button to initiate the configuration process, plug-in your YubiKey, and then press your YubiKey's button (full-size device) or side (for the nano versions).

That's it. Crazy easy. I **highly** recommend configuring a secondary authentication such as SMS with your phone. This will allow you to maintain access to your account if you lose your YubiKey or break it.

If you have multiple Gmail or Google Apps accounts you can repeat this process for each account. Each YubiKey device as 2 configuration slots. By default, the first slot comes preconfigured with OTP set up and Yubico recommends you leave this alone. The second slot can be configured for something else such as HOTP or TOTP. NOTE: Setting up Gmail and/or Google Apps _does not use_ any of the slots on the device that I can tell. I suppose it could be using slot 1 since I didn't reconfigure that slot but I know for sure it isn't slot 2. This behavior is good as the slot limits can be somewhat frustrating.

## 2FA with the Yubico Forums

Yubico has an [online forum](http://forum.yubico.com/) which is useful in seeing how other people deploy their device and in getting help when you can't figure things out. I've run into several inconsistencies in the documentation and the forums have been useful in helping me troubleshoot.

![Yubico forum login]({{ site.url }}/images/posts/2015-07-21/yubicoforum.png)

Anyone can read the forum contents but only registered users can create posts and reply to posts. And in order to register you must own a YubiKey. As the screenshot illustrates logging in requires users provide their forum username, password, and a YubiKey one-time password. After you enter your username and password you move the cursor to the `YubiKey OTP` field and press the button or side of your particular device. A one-time password is entered into the form field and the form is automatically submitted. If everything was entered correctly you are logged in and can create posts or reply to posts.

## Basic One-time Password (OTP)

The OTP features of each YubiKey device are configured in slot 1 from the factory. When you receive the device you simply plug it into an available USB port and you're ready to use OTP. It can be used on the [Yubico Forums](http://forum.yubico.com) and on the [Yubico Validation Service](https://www.yubico.com/start/). In the case of the validation service, this was where the documentation started to break down. The page asks you to select which YubiKey you purchased and you'd think this is because the validation is different for each. I didn't find that to be the case. In fact, the Edge and Edge-N aren't even listed on the page. I think I validated my device using the YubiKey Standard and YubiKey Nano sections and found the process to be the same.

I'm still learning all the ways the YubiKey works but the utility of the OTP feature seems really limited to me. Aside from the two examples above there aren't many reasons I'd need to generate a random string where I'm not doing so in my password manager application. One of my colleagues says he uses the OTP feature all the time and I need to sit down with him to learn more.

_OTP / Slot 1 Gotcha_

As I mentioned earlier slot 1 comes preconfigured with OTP. Part of OTP process includes the generation of a 6-byte prefix. Every password generated from your device will use the same prefix in order to identify your specific device. The first two characters of this prefix will be `cc` unless you reconfigure slot 1 then they'll be `vv`. When I received my YubiKey Edge I didn't know slot 1 was preconfigured. Being the security-minded person I am I went through the process of setting up OTP in slot 1 and validating my new settings using the [Yubico Validation Service](https://www.yubico.com/start/). It was here where I learned about the `cc` and `vv` prefixes.

From my research it appears Yubico gives more _validity_ to the `cc` prefix since this indicates the device is still in factory condition. At least as far as slot 1 goes. There's nothing inherently wrong about the `vv` prefix but there are some warnings when you go through the validation process on the Yubico website which made me wish I hadn't messed with it.

## Tools and Issues

_YubiKey Personalization Tool_

Yubico provides a few tools you can use to manage your device and the services you configure. The main tool is the YubiKey Personalization Tool and it's what you use to configure slot 1 and slot 2.

![YubiKey Personalization Tool]({{ site.url }}/images/posts/2015-07-21/yubikeypersonalizationtool.png)

You can download this tool and others from the [Yubico Downloads Page](https://www.yubico.com/support/downloads/). Some of the tools are only available for certain operating systems or certain devices such as the NEO/NEO-N. In many cases it's unclear whether you need a certain tool. While the [documentation](https://www.yubico.com/support/documentation/) is helpful it doesn't spell things out in a way that always makes sense to me. For example, there is supposedly a way to setup OATH 2FA with GitHub using any YubiKey which supports OATH/HOTP/TOTP. The PDF documentation discusses using the TOTP tool - which is only available for Windows and appears to be deprecated - to copy the secret generated by GitHub into the TOTP tool. Then, the TOTP tool, in conjunction with the YubiKey, generates the token you paste into the GitHub website. I'm on a Mac so the TOTP can't be used. I [inquired about this in the forums](http://forum.yubico.com/viewtopic.php?f=16&t=1962) and was directed to use the YubiKey Authenticator application (described below). Long story short, I still haven't figured this out and in the meantime I'm using Google Authenticator with GitHub for two-factor authentication.

_YubiKey Authenticator_

![YubiKey Authenticator]({{ site.url }}/images/posts/2015-07-21/yubicoauthenticator.png)

The YubiKey Authenticator application is supposed to be used in conjunction with 2FA just like you'd use Google Authenticator. In other words, you would enter your username and password on a website and when asked for your 2FA token you'd generate one using YubiKey Authenticator and your YubiKey. It all sounds well and good but I've been unable to get it working. I'm not sure if the cause is an unsupported device (YubiKey Edge) or I'm simply doing something wrong. I'm hoping to get an answer on my [forum post](http://forum.yubico.com/viewtopic.php?f=16&t=1962) soon.

## Summary

I'm happy with the YubiKey Edge so far. At $30 it's hard not to be. But I have been wondering if I should've gone with the NEO. While I don't care for the NFC support I have thought about uses for the OpenPGP support. The NEO also appears to have less limitations with it comes to OATH/HOTP/TOTP. Since it has better integration with OATH/HOTP/TOTP and YubiKey Authenticator you're apparently not limited to slot 1 and slot 2. I haven't looked into this fully so I may be wrong. But it's something I want to check out and see if it's worth spending another $50 on a second device.

The YubiKey Edge wouldn't be a complete sunk cost as Yubico recommends you buy two devices anyway. With two, you can configure the second with some of the same features (or all of the same features if the devices are identical) so you have a backup if you lose your original YubiKey or it gets damaged. The latter is unlikely given the devices are defined by Yubico as `crushproof, waterproof, monoblock design, and no battery`.

The additional security and utility provided by a YubiKey is pretty neat. I plan to continue exploring its usage in my daily technology workflow.
