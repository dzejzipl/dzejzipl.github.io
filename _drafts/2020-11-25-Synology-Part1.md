---
title: "Synology DS620Slim - Part one"
categories:
    - Synology
tags:
    - Synology
    - NAS
    - DS620Slim

header-img: "/assets/images/top_images/SynologyTOP.jpg"
subtitle:   "Synology DS620Slim - Part one"
---
![Synology DS620Slim - Part one](/assets/images/top_images/SynologyTOP.jpg) What if I want to show you how to use Synology NAS on your home lab?

Couple months ago I received an new device which was used on my home. I also created a couple of blog post, but all was written in Polish language. Now I want to show you, how I configured **DS620Slim** to be used on my home lab and for enterteiment. 

That will be another series of post on my blog. 

On first part I want to show you how to configure new device and prepare for next part of posts.

One important information for you: ***I'm using BETA software - version 7.0, which will be released to prodution soon, but please remember that can be some changes on production version of firmware***

When device has mounted hard drives and it's connected to LAN connection and power you can open your browser and type: **http://find.synology.com/** to open special webpage, which will find your NAS on your network. If you don't want to do this, you can check DHCP leases on your router. 

For me, it's looks like on below screenshot:

![Synology DS620Slim - Part on](/assets/images/posts/Synology-Part1/01.png)

When you click Connect, there will be a wizard, which will help you to configure your NAS device. 

You should upload *.pat file which latest beta software which you can download from Synology website. 

![Synology DS620Slim - Part on](/assets/images/posts/Synology-Part1/02.png)

When the software will be installed, you're prompted to create account with administrative permissions and set name for this device.

![Synology DS620Slim - Part on](/assets/images/posts/Synology-Part1/03.png)

On next step you will be asked to join Synology account. It's preffered to have this account. If you join to this program, you can receive alerts about your device.

Next step is configuring Dynamic DNS service. You can use it or not - depends of you. If you will use it, you can work with your NAS device if you don't have static IP address. That means - you will be using website: **mycustomname.quickconnect.to**

Another plus of using Synology account it's possibilty to enable monitoring and protection and regullary backup of your DSM configuration. I will enable it. 

From basic setup it will be all.

![Synology DS620Slim - Part on](/assets/images/posts/Synology-Part1/04.png)

