---
title: "Joining Synology Router to Active Directory and working with AD Users and Groups"
categories:
    - HomeLab
tags:
    - Synology
    - RT2600ac
    - MR2200ac

header-img: "/assets/images/posts/2021/SynologyRouter/top.jpg"
subtitle:   "Joining Synology Router to Active Directory and working with AD Users and Groups"
---
![Joining Synology Router to Active Directory and working with AD Users and Groups](/assets/images/posts/2021/SynologyRouter/top.jpg)Last time I spend a bunch of time of usage Synology routers in my home (lab), so I decided to connect RT2600ac to my local AD!

Full review of those routers you can read [here](https://www.piesik.me/2021/06/09/SynologyRouters/).

So, I decided to connect this router to the local Active Directory to have a possibility to grant access to VPN services by Active Directory domains instead of creating normal accounts directly on the Synology router.

To do this, you need to open Control Panel on the Router, go to the Domain Tab, fill in the necessary data, and join the domain. The account which you use should have permissions to join devices to the domain.

In my case it looks like on the below screen:

![Joining Synology Router to Active Directory and working with AD Users and Groups](/assets/images/posts/2021/JoiningSynologyRouterToAD/01.png)

You need to select update user/group because by default is disabled.

After a while, you should see groups and users from AD.

![Joining Synology Router to Active Directory and working with AD Users and Groups](/assets/images/posts/2021/JoiningSynologyRouterToAD/02.png)

To assign permissions for specific VPN services, you need to open the *VPN Plus Server*, go to the Permission tab, and select a Domain from the dropdown list.

![Joining Synology Router to Active Directory and working with AD Users and Groups](/assets/images/posts/2021/JoiningSynologyRouterToAD/03.png)

This user can use their AD account to log on to a specific VPN service.
