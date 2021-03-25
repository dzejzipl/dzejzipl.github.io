---
title: "Poly Studio X30 - a story about video bar"
categories:
    - Review
tags:
    - Poly Studio
    - Poly
    - MTR
    - Microsoft Teams Room

header-img: "/assets/images/posts/2021/PolyStudioX30/top.jpg"
subtitle:   "Poly Studio X30 - a story about video bar"
---
![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/top.jpg)A short story about Poly Studio X30 on my home lab...

Wait, what? A video bar in my home lab? Why not?

Couple weeks ago I decided to write email to one of PR company with question if they can send to me some Poly devices. I have a plan to write couple of posts about Microsoft Teams, especially about Microsoft Teams Rooms. Why about Microsoft Teams if I'm specialized about Modern Management? Don't know.. I just want to learn some new thing. I don't want to be specialized only on Modern Management, but also want have some another skills.

So, I asked Public Releation team from Poly if there is possibity to test **G40-T** set. Nope, wasn't possible. They asked me if I want to check myself with **Studio X30** set.

Yay, why not? This set is worth almost 3500$ from that what I was checking. I never has that expensive device on my home lab.

## Small companies and confereces room.

Couple of years ago I was working for company which has multiple rooms something like meetings rooms, but without any of conferences devices. When you need to call someone, you needed to pick your laptop or phone and take it with you. When you're was alone - ok, no problem. You can use your headphones etc. and watch a presentation or video  directly from your laptop. What when you are not alone, but with your colleagues? You will still use your laptop or maybe some TV connected to your laptop and speakers? Can be a good idea, but you still need use your corporate laptop.

And what is important - you will still use built-in camera to your laptop.

## So why don't use some collaboration bars?

That's right. For conference rooms you can buy multiple products. Starting from headphones, microphones, telephones, decicated cameras, tv's, etc. etc....

Why don't use all in one? Why don't to buy one - dedidacted product for that purposes?

And here we have a hero of my text:

## Poly Studio X30

I don't know if you know the Poly company, but they are creating dedicated hardware to use in Home, Small business and big business. They have multiple different products in their portfolio.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/top.jpg)

What I found on my package?

* Poly TC-8 - touch interface which can be used with Studio X family and G7500 with LAN Cable
* Poly Studio X30 - video bar
* All necessary cables
* Monitor clamp and privacy cover

So, we have everything in the box and we are able to start works with this hardware...

But there is one important thing.

## PoE

**TC-8** needs PoE. In my case - I need to buy special a special switch with PoE function to run and configure this device. Please remember about this.

When we connect X30 to the power supply, connect external monitor (or TV) and use TC-8 station we are able to start working.

We can use built-in Poly software, but in this article I will be focused on Microsoft Teams.

Last time - I decided to wrote some article about **Microsoft Teams Rooms**. This article you can read it [here](https://www.piesik.me/2021/03/02/MTR-01/)

If you don't want to use Poly provider or Microsoft Teams there are mulitple another chooises, like:

* Zoom Rooms
* GoToRooms
* 8x8 Meeting Rooms
* RingCentral Rooms
* StarLeaf

So, as we see there are multiple possibilites to use that device with almost any of conferencing calls providers.

There is one more provider named: *Device mode*. This mode allow to use X30 as standard - 4K camera, with built-in microphone and speakers.

That can be a nice alternative, when we need to record some videos with great quality.

But as I write earlier, I will be focused on Microsoft Teams.

## Getting started.

If we have configured MTR account - for example on my case it will be: **MTR01@memcloud.ovh**.

To change provider, we need to logon to web-based panel of this device, logon with *admin* username and password which is last 6 digits of the serial number.

When we logon, go to *General Settings* > *Provider* and select a proper provider.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/01.png)

When you click *Save*, device will be reseted to default settings, rebooted and configured to use Microsoft Teams as primary provider.

Some important information from my side. A good idea is connect external mouse / keyboard for initial configuration of device. Will be much faster than using bult-in screen in TC-8.

Next step, when device will be restarted - you should select a language for our device.

Next restart and you should logon to this device using our earlier created account. As I wrote earlier - I will use MTR1 account.

Tip: if you don't want to type login / password on this device, select option **Sign in from another device**

**TIP**: Because it is "standard" account, you need to reset a password.

After a while you will see this device as Azure AD registered on Azure portal.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/02.png)

In my case, after 10 minutes, this device show up on MS Teams Admin Center > Devices > **Collaboration bards**.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/03.png)

If we open this device directly on Admin Center, we will see multiple statistic or we can also check "Health" status. In the below screen you can see, that my device can be updated to the newest version.

What is interesting - this update is available only on Teams Admin Center, from device panel - is not available.

I will update it right now. Can take to 10-30 minutes even.


