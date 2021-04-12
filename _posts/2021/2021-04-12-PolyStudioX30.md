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
![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/top.jpg)A short story about Poly Studio X30 in my home lab...

Wait, what? A video bar in my home lab? Why not?

A couple of weeks ago I decided to write an email to the PR company with the question if they can send to me some Poly devices. I had a plan to write a blog post about Microsoft Teams, especially about Microsoft Teams Rooms. Why about Microsoft Teams if I'm specialized in Modern Management? Don't know... I just want to learn some new things. I don't want to be specialized only in Modern Management, but also want to have some other skills.

So, I asked the Public Relations team from Poly if there is a possibility to test the **G40-T** set. Nope, wasn't possible. They asked me if I want to work with the **Studio X30** set.

Yay, why not? This set is worth almost 3500$ from that what I was checking. I never had that expensive device in my home lab.

## Small companies and conference rooms.

Years ago I was working for a firm that has multiple rooms something like meeting rooms but without any of the conference devices. When you need to call someone, you needed to pick your laptop or phone and take it with you. When you're was alone - ok, no problem. You can use your headphones etc. and watch a presentation or video directly from your laptop. What when you are not alone, but with your colleagues? You will still use your laptop or maybe some TV connected to your laptop and speakers? Can be a good idea, but you still need to use your corporate laptop.

And what is important - you will still use a built-in camera on your laptop.

## So why don't use some collaboration bars?

That's right. For conference rooms, you can buy multiple products. Starting from headphones, microphones, telephones, dedicated cameras, TVs, etc. 

Why don't use it all in one? Why don't to buy one - dedicated product for that purpose?

And here we have a hero of my text:

## Poly Studio X30

I don't know if you know the Poly company, but they are creating dedicated hardware to use in Home, Small business, and big business. They have multiple different products in their portfolio.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/top.jpg)

What did I find in my package?

* Poly TC-8 - touch interface which can be used with Studio X family and G7500 with LAN Cable
* Poly Studio X30 - video bar
* All necessary cables
* Monitor clamp and privacy cover

So, we have everything in the box and we can start works with this hardware...

But there is one important thing.

## PoE

**TC-8** needs PoE. In my case - I need to buy special a special switch with a PoE function to run and configure this device. Please remember about this.

When we connect X30 to the power supply, connect an external monitor (or TV), and use the TC-8 station we can start working.

We can use built-in Poly software, but in this article, I will be focused on Microsoft Teams.

Last time - I decided to wrote an article about **Microsoft Teams Rooms**. This article you can read it [here](https://www.piesik.me/2021/03/02/MTR-01/)

If you don't want to use Poly provider or Microsoft Teams there are multiple other chooses, like:

* Zoom Rooms
* GoToRooms
* 8x8 Meeting Rooms
* RingCentral Rooms
* StarLeaf

So, as we see there are multiple possibilities to use that device with almost any of conferencing call providers.

There is one more provider named: *Device mode*. This mode allows us to use X30 as a standard - 4K camera, with a built-in microphone and speakers.

That can be a nice alternative when we need to record some videos with great quality.

But as I wrote earlier, I will be focused on Microsoft Teams.

## How it looks?

Before I will write about technical information, I need to write something about the general look of that device. 

It is **beautiful**. 

When you place this device on your TV or display - it is just fit. It's very heavy, but this monitor clamp is very stable. 

The speaker grille - it's amazing. Gives us information that is a premium device. Also, the Poly TC-8 tablet just stays on the table, it's connected by one cable and... Just working. It is simple plug-and-play. 

## Use as the external device

I wrote earlier that this device can be set up as *device mode*. This mode allows us to use X30 as USB connected device to our device.

I tried this mode and was amazing to use, but don't want to share pictures or videos of my room and me in a public space ;) 

As I use Windows 10 system, I just plugged in one USB cable to my device, and start working. I was able to use the camera, audio, and video.

## What is MTR?

> Transform meeting spaces ranging from small huddle areas to large conference rooms with a rich, collaborative Teams experience that's simple to use, deploy, and manage.
> 
> Start meetings on time with one-touch join, then instantly project to the display in the room and share to remote participants.
>> Source: https://docs.microsoft.com/en-us/microsoftteams/rooms/

## What is the purpose to use certified products of Microsoft?

I was playing with MTR earlier, but not with certified devices. I built in my own system on the Hyper-V platform, but can't manage that MTR using Microsoft Teams Center, because... Wasn't a certified solution.

About creating my own MTR device I will write something later because can be a good idea for very small companies to get started with MTR and help transform some rooms into video collaboration rooms.

The main purpose of using certified products is having a possibility to manage it from *MTC* - Microsoft Teams Center. This is one place, where you can manage your devices, create profiles, checking the usage and status of devices. 

Please remember that there is a couple of type of devices which you can use with MCT:

* Teams Rooms dedicated systems
* Collaboration Bars,
* Teams Display
* Teams Panels
* and IP Phones

In my article, I'm describing Collaborations Bar. 

## Getting started and configuring devices using Microsoft Teams Center

If we have configured an MTR account - for example in my case it will be **MTR01@memcloud.ovh**, which I already configured.

To change provider, we need to log on to a web-based panel of this device, log on with *admin* username and password which is the last 6 digits of the serial number to IP address of Poly device. You can find this address on the Poly device or using DHCP on your router.

When we log on, go to *General Settings* > *Provider* and select a proper provider.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/01.png)

When you click *Save*, the device will be reset to default settings, rebooted, and configured automatically to use Microsoft Teams as a primary provider.

Some important information from my side. A good idea is to connect an external mouse/keyboard for the initial configuration of a device. Will be much faster than using the built-in screen in TC-8.

Next step, when the device will be restarted - you should select a language for our device.

Next restart and you should log on to this device using our earlier created account. As I wrote earlier - I will use the MTR1 account.

Tip: if you don't want to type login/password on this device, select option **Sign in from another device** and use created by Microsoft login method, where you need to provide token from device and assign this token to proper account.

**TIP**: Because it is a "standard" account, you need to reset a password in the Office Portal to use this account on any kind of device.

After a while, you will see this device as Azure AD registered on the Azure portal.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/02.png)

In my case, after 10 minutes, this device shows up on MS Teams Admin Center > Devices > **Collaboration bards**.

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/03.png)

If we open this device directly on Admin Center, we will see multiple statistics or we can also check "Health" status. In the below screen you can see, that my device can be updated to the newest version.

What is interesting - this update is available only on Teams Admin Center, from the device panel - is not available.

![Poly Studio X30 - a story about video  bar](/assets/images/posts/2021/PolyStudioX30/04.png)

I will update it right now. Can take to 10-30 minutes even.

After updating, the device will be restarted and the assigned user will be logged in automatically.

In the MCT you will see details about the usage of your device, general status also you can restart the device if there is a need for that. You don't need to manually restart the device. 

## Configure profiles

So, the device is visible in the MCT, and you want to start configuring it. You can create multiple profiles and assign them to specific devices, but please remember that one device can have only one assigned profile.

For Collaboration Bars you can configure settings:

![Poly Studio X30 - a story about video bar](/assets/images/posts/2021/PolyStudioX30/05.png)

* General Settings
* Device Settings
* and Network Settings.

When you finish configuring profiles, you need to assign them to the proper device. 

Those kinds of configuration profiles can be also created for Teams Displays and Teams Panels and IP Phones. Not for Teams Rooms.

## Working with the device in the daily use

Send an invite to this room and to necessary people, click "Join" to the meeting before couple minutes of start and meeting and... Wait. Nothing more, nothing less. 

It is just working. It is just one click on the TC-8 device to join the meeting. 

This device has a nice option to follow people in the room. For example, if the camera see only me in the room there was zoom on me. But when my wife was in the room - the camera shows us both. If I walked around the room - the camera was following me. That is a nice feature, but can be also disabled if there is a need for that.

If you don't have a planned meeting - you can just click "Start meeting" and invite the necessary people from the touch panel. The device will start a meeting and call those people. They can join from their devices. 

Using Touch Panel, you are able also to mute, change volume, disable and enable the tracking of people and... use navigation buttons. But from my perspective, it was much easier to use those devices with mouse and keyboards. But that is not a primary way to control and use. Did you see any mouse and keyboard in that kind of room? Nope, me neither. 

## Technical information about the device

Poly X30

* 4K camera
* 4K @ 30FPS and 60 FPS @ 1080p resolution
* Digital Zoom: 4X
* Field of view: 120'
* 4X beam-forming Mic array 

## Worth to buy?

I'm just a bit disappointed, that I don't have more possibility to work with that device. In the work, I'm working with the other technologies. I need to build my own MTR device. Maybe It will be not dedicated and visible on the MCT, but...

Also... I learned a lot. I have multiple plans related to Microsoft Teams in my blog.

If you are working for a small company, which don't have any video conferencing systems - yes, it is worth to buy. Your co-workers will be grateful for that. They don't need to pick up their own device to start a call. 

I think the price of that device is high, but... After weeks of working with that device, I can fully understand why is so high.
