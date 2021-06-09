---
title: "Synology Router RT2600ac and MR2200ac on my homelab!"
categories:
    - Review
tags:
    - Synology
    - RT2600ac
    - MR2200ac
    - VPN

header-img: "/assets/images/posts/2021/PolyStudioX30/top.jpg"
subtitle:   "Synology Router RT2600ac and MR2200ac on my home lab!"
---
![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/PolyStudioX30/top.jpg)Another kind of type of devices on my home lab... This time - Synology network devices.

As you can know, one of the primary devices in my home lab is a NAS device. I'm using DS620Slim with 6 of 2,5' HDD disks. It's almost 1,7TB of space to use and it is enough for me. I'm in love with this system, which they created to manage the whole NAS device. It is very simple, clear, and useful. I know where I should click to manage specific options.

A couple of weeks ago I realized, that they have also other devices - like the routers, cameras, additional storage disk for NAS, RAM, etc... So I decided to check them network solution - routers.

After a couple of days I received a package where I was found two devices:

* Synology Router RT2600ac
* Synology Mesh Router MR2200ac

To build a fully functional network you need to buy only one device **RT2600ac**, but if you want to extend your home network for better connectivity on the full house, it is better to buy an additional device - like **MR2200ac** and connect as a mesh router. Like the repeater on the old way!

Because I had some issues with wireless connectivity in my bedroom, where I often work I was happy, that I can also test this second device!

So, what was on the package which I received?

As I said earlier - on two different devices, every device had its power supply and one LAN cable. It's enough because I think most people have their LAN cables at home. Also manuals etc... Nothing special for us.

RT2600ac has 5 Gigabit RJ-45 ports and my old Mikrotik hapAC2 also so I was happy that I don't need to remove any of the switch/device from the current network. So I removed the old router, connected all cables from the home network and Internet provider to the first port, and started the initial configuration by connecting to the newly discovered wifi network named Synology_Number and providing the password: "synology".

## Initial configuration

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/01.png)

After that, I opened a browser and type router.synology.com as the address to open Configuration Wizard. Was very simple, everything you need to do is set up an Administrator Account (and accept EULA), set up a Wi-Fi network, and Operation mode. You can choose between Wireless Router and Wireless AP. I selected the Router mode. You can also select if you want to manage your router externally.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/02.png)

The last step is to choose your Internet connection mode. If you have a modem/router from the provider, you can select AutoIP, if your provider uses PPPoE, select PPPoE mode, etc...

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/03.png)

And... It is everything you don't need to do anything else to start using your router. But I want to do some initial changes.

The first change that I done was the DNS server. I don't want to use the provider's DNS servers, I prefer to use OpenDNS. To change it, I'm opening Network Center and going to the Internet tab from the left side. At the top, I'm selecting to Connection tab and manually configuring the DNS server.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/04.png)

The second thing that I do is checking if there is any update-pending for the System and packages.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/05.png)

The last thing which I have done was add a second device which I received to extend the wireless on my home. I have some problems with wifi - in the bedroom is a very poor signal.

So, I connected the MR2200ac to the power, wait for the proper LED on the device, logged in to the RT2600ac panel.

The next step which I have done was open the **Wi-Fi Connect** and from the left side, I chose the *Wi-Fi Point* tab. Click to *Add* button. Click Next two times and wait to find a proper device. You can add multiple devices once. You don't need to do the same steps many times. When the additional point will be found, you can use one of the pre-defined names or usefully device name. I will use one of the predefined names.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/06.png)

After a while, your device will be added as a mesh router.

It's a very simple process. If you have a big house, you should consider adding additional mesh routers to get a better signal for the whole home.

And if you are curious what are the speeds between routers you can do a performance test. In my case it looks like on the below screen:

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/08.png)

There are many different options to manage uplink connections... If you have more than one mesh router you can configure also to which device selected device can connect etc...

Ah! If you're on this same page - **Wi-Fi Connect** you can also configure the Guest Network. I'm recommending this action to don't let in guests to your home network. It's simple like adding additional mesh routers. Just go to the **Guest Network** tab, fill in the necessary information, and select Apply. You can change the password for the network and optionally - allow users to access your normal network.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/07.png)

Interesting thing is that you can schedule on what hours this network is accessible for people. For example, if you use the router in a small company and you know that you don't have visitors before 8 AM and after 5 PM for the rest of day, you can disable Guest Wi-Fi. You can also enable the Guest Portal to manage users that they need to click manually to connect to Wi-Fi using a dedicated page.

How many options and how easy is configuring this device. The GUI is very easy to work with.

## Secondary WAN interface

This is an important thing not only for companies but also for some home-users that the device has a secondary WAN interface. If you have a second Internet provider, you can connect it to the LAN1 interface and manage how will be used as fail-over or fail-over and load balancer.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/09.png)

I didn't have a chance to configure that so I cannot write anything more from a real perspective on how it works. I know only the theory but... If I can have this router longer, I will prepare a secondary router from my LTE connection and connect it as a secondary network.

Ah, by the way. RT2600ac also supports the 3G and 4G dongles.

## Package Center

Like on the Synology NAS, RT2600ac has something like the Package Center. Of course - it's much smaller, because it's a router, not a NAS device but has a couple of additional packages, which you can install.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/10.png)

If you need to extend the functionality of your device, you have a couple of possibilities, for example, install your own DNS or RADIUS server for authentification.

Packages are installing on USB drives, so if you can - use a good performance USB drive.

## VPN Connection

As you know, last time many of companies decided to move to the home office instead of sitting in the offices. If people work on Internet-based resources - it is not a problem. They can reach those resources from any place in the world.

But what if they need to connect to the on-premise resources? System Admins need to configure a VPN connection to the office.

By default, it is not a very easy thing to set up. Require a bunch of knowledge and setup for end-user from their perspective.

Synology offers a package named **VPN Server Plus** which is changing our router for a fully functional VPN server.

From my perspective, it's very easy to configure, even you don't need to manually unblock ports on the built-in firewall but you receive a popup with the question if you want to unblock those ports.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/12.png)

When the package will be installed, you will see this:

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/13.png)

RT2600ac supports three different categories of VPN: Standard VPN, Site-To-Site VPN, and Synology VPN.

In a couple of words, Site-To-Site VPN allows Administrators to connect two different locations to one single "location".

Standard VPN - In this Administrator can create a VPN connection using one of the technologies which are preferred by the organization, like SSTP, OpenVPN, L2TP, or PPTP.

But I want to write something about Synology VPN because that was the most important thing for me to check.

You need to know two things about this solution.

* It's not a free solution
* It's very easy to use

But Synology offers 1 license to start using their VPN solution. And I have something better for you! During the COVID time, they decide to provide additional 19 licenses for your users to connect to VPN for **FREEEEE**!

More information from Synology:
> In response to the COVID-19 pandemic, Synology is offering free VPN Plus licenses to all Synology Router users in an effort to support businesses with employees working from home. This special offer ends on September 30, 2021 (PDT).

So, the first thing is clear for now. What with a second thing?

That's right, it is very easy to configure for the user without a big technical knowledge. There a couple of steps that you need to do:

1) Enable DDNS service for your router by opening Network Center > Internet > Quick Connect & DDNS > **DDNS** settings. I will use the of course Synology provider, but you can choose another one.

2) Second thing is enabling SSL VPN.

Basically, it is everything that you need to do to enable the VPN to your location.

Wait, how? How the end-user will should now connect?

For example, I created a test user named *fkonewka* and assigned to this person the possibility to connect to SSL VPN by Permissions tab on the VPN Plus Server.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/14.png)

This user needs to visit the site which was registered on the previous step on the DDNS hostname (in my case on Synology DDNS) and log on using their own credentials.

The next thing what user should do is install the Synology VPN Client. I will write about this article on how to install it using MEM and set up the 8 numbers PIN code and select which options want to configure.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/15.png)

And... It is everything. End-user has a connection to on-prem resources.

Wow, just wow...

I have plans to write more articles about this VPN Server Plus because has more features than I can describe in this one, single article.

## Safe access

Do you have kids and you want to control what and when they are using an Internet connection? Or maybe you want to block some of the websites to kind of colleagues in your office?

Safe access is an answer to that question. It allows creating profiles to manage when they have access to the Internet connection, to which sites they have access. You can select one of the predefined profiles or built custom.

![Synology Router RT2600ac and MR2200ac on my home lab!](/assets/images/posts/2021/SynologyRouter/11.png)

End-user (or child) has the possibility to send a request to unblock a specific site.

You can also select when this device can be connected to the Wi-Fi network or what is a quota for the daily connection.

Uh, my daughter now has only two years, but in the future, that option will be used by me often...

Uh, again - so many options to configure, but everything is easy to set up and easy to understand what a specific option does.

## Threat Prevention

Safety should be first. In life and in virtual life also. Why not help make a more safe network using the built-in functionality from Synology Router?

What is a Threat Prevention?

Synology writes about it:

> Guard your network against network threats and identify malicious activities to refine your firewall rules.

If you need more information, you can [read it here](https://www.synology.com/en-global/srm/feature/secure_network_foundation).

I configured that option, but I forgot to make a proper screenshot before setting up the router again :(

## Download Station

About the Download Station, I have written something in the past in [this article](https://www.piesik.me/2020/12/12/Synology-Part2/#)

In a couple of words - it allows you to download data directly to a USB device connected to your router. Without the computer. It's easy to use. I will don't provide examples of how to use that kind of package ;)

## Performance

I think this router has more resources that I can use on my home, even if I'm using it with my home lab (more than 12 devices etc) and home devices (more than 10 devices)... I didn't see any performance issues.

## Last words...

I'm very impressed with this device. Found one thing which was very annoying for me. Cannot create VLANs for different networks or even cannot create a secondary network for a home lab. So I connected my old Mikrotik to Synology router and the problem is fixed!

Price isn't low, but I think - fully understandable for the functionality which we are receiving. Especially - that VPN solution.

I think every small company which buys this device will be satisfied.

Also - I'm very satisfied with that device.
