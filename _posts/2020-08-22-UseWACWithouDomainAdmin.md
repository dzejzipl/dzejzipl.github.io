---
title: "Windows Admin Center - without Domain Admin!"
categories:
    - WAC
tags:
    - WAC
    - Windows Admin Center
---
![Windows Admin Center - without Domain Admin](/assets/images/posts/UseWACWithouDomainAdmin/top.png)Use WAC without **DOMAIN ADMIN** account!

I'm in the middle of deploying WAC on my environment. 

When WAC is installed I saw that I should use the account from Domain Admin groups - this group has full permissions on machines and is assigned to the local administrators group. You **should not use any of domain admin account on a local workstation!**

You should use an account that is on **local administrators** group!

But how to do this? Create an AD user and manually add it to the local administrators group? Boring! 

Let's use it for that GPO!

First I created a new OU on my domain, like on below screen, and moved Windows Servers computers to proper OU. Next - I created a new AD user named *WacUser*. When a user was created - I added it to a new group named: **WACAdmins**.

![Windows Admin Center - without Domain Admin](/assets/images/posts/UseWACWithouDomainAdmin/01.png)

When my OU is ready and I have a group and added WAC user to this group we can create a new GPO.

As you can see I will create it on *WindowsServerDevices* container.

![Windows Admin Center - without Domain Admin](/assets/images/posts/UseWACWithouDomainAdmin/02.png)

Let's edit it and open *Computer Configuration* > *Policies* > *Windows Settings* > *Security Settings* > *Restricted Groups*.

Now you can right-click and select *Add group* and provide the name of a group which you created earlier. 

![Windows Admin Center - without Domain Admin](/assets/images/posts/UseWACWithouDomainAdmin/03.png)

When this group will show up you should type **Administrators** on the field: *This group is member of* like on below screen:

![Windows Admin Center - without Domain Admin](/assets/images/posts/UseWACWithouDomainAdmin/04.png)

Now you can go to your devices which are on *WindowsServerDevices* and do *gpupdate /force* from CMD **with administrator privileges**

When you open *lusrmgr.msc* and edit an Administrator group you should see:

![Windows Admin Center - without Domain Admin](/assets/images/posts/UseWACWithouDomainAdmin/05.png)

And it's done. Nothing more. You've created a user without domain privileges to manage local workstations using WAC!
