---
title: "My home lab - part third"
categories:
    - Random
tags:
    - Home Lab
---
![My home lab](/assets/images/top_images/HomeLab.jpg)Third post about my Home Lab.

On the [first post](https://www.piesik.me/2020/07/26/HomeLab/) you can read more about hardware. In the [second post](https://www.piesik.me/2020/08/18/HomeLab2/#) I wrote something about hardware changes and what was done - installing AD DS + DNS, installed virtual machines and joined to domain. Nothing special. 

But today we will install WAC - *Windows Admin Center* and Remote Support Administration Tools on one of machine (*HV01-M03*). After that - we will install Azure AD Connect to synchronize our data with Azure AD.

## First part. Installing WAC

As always before doing some changes on lab - i'm doing a snapshot of my VM. It's for a backup purposes. 

After that I downloaded WAC from [this URL](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-admin-center) and started installing. 

Next, next, next.. On screen: *Configure Gateway Endpoint* I selected only first checkbox. I will not use WinRM over HTTPS because I don't have any certificates yet.

![My home lab - part third](/assets/images/posts/HomeLab-part3/01.png)

On next screen I selected that I want to generate a certificate and redirect HTTP port 80 to HTTPS (443)

![My home lab - part third](/assets/images/posts/HomeLab-part3/02.png)

After installation you should be able to open https://yourHostName (for me it's: https://hv01-m03.piesik.online) and see something like this:

![My home lab - part third](/assets/images/posts/HomeLab-part3/03.png)

When you click **Add**, you can add a new Windows 10 devices, Windows Server, Server clusters or Azure VMs. For now we will add our all of servers - so I will choose *Servers* > Search Active Directory. As server name I will use * (wilcard) to search all servers. 

![My home lab - part third](/assets/images/posts/HomeLab-part3/04.png)

Now if you want to connect - just click a connect and provide username from **local administrators** group. It's important. I'm preparing a another blog post how to

## Second part. Installing RSAT


## Third part. Installing Azure AD Connect