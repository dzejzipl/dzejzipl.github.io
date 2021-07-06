---
title: "Use Microsoft Store for Business with MEM!"
categories:
    - MEM
tags:
    - Intune
    - Microsoft Store for Business
    - MSfB

header-img: "/assets/images/posts/2021/SSPR/top.jpg"
subtitle:   "Use Microsoft Store for Business with MEM!"
---
![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/top.jpg)Start using and deploying applications from Microsoft Store for Business on your tenant!

There are situations when you need to provide a specific application to the end-users. You can create your own package for that application, use the MSI package directly on the MEM, or... If that application is in Microsoft Store for Business - you can use that method to deploy the specific application to all or groups of users!

In this post I will show you, how to configure Microsoft Store for Business - **MSfB** and deploy some of the applications.

To start, log on to the MEM portal, go to the Tenant Administration tab > Connectors and tokens, and select *Microsoft Store for Business*.

By default, this is disabled and needs to be enabled.

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/01.png)

To enable, click on the link "Open the business store", log on with an account that has the necessary permissions. This will open a new tab. Go to the Manage tab, from the left side select Settings, and after that - Distribute tab.

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/02.png)

Select the **Activate** button nearby the Intune tool and go back to the MEM portal.

Select the **Enable** button nearby the text: *Enabling Microsoft Store for Business sync lets you access volume-purchased apps with Intune.* In my case I will choose the English language, click *Save* on the top and on the end - click **Sync** on the bottom.

This will take some time, but you can refresh the page and you will see that the connection is active.

When the Sync will be completed, the date will change from 1/1/1970, 1:00:00 AM to today's date.

So, basically, Shop is now enabled and users can buy or add their own applications. But we should do make some additional changes.

I prefer to disable the option to allow all users to purchase any of the apps. Do you trust users? The preferred way is to add tools by IT only so check the option named *Make everyone a Basic Purchaser*. After that, go to the Private Store and click on the Activate the Private store and accept the EULA.

To manage, who can buy the application, visit the Permission tab on the Settings and assign a necessary role. By default, the account which configured the Store has an Admin role.

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/03.png)

The next thing is enabling the Offline version of the Installation files. There are situations ([for example during the provisioning Kiosk Mode](https://www.piesik.me/2020/05/03/WaitingForInstallationStatus-Intune/#)) when you need to assign an offline version of the application. For more details - go to the above post.

The last thing is **Allow app requests**. This will allow end-users to request the application to buy or add by IT staff. But please remember to configure, which user will receive a notification about that request. By default, all Global Admins accounts will receive that kind of notification.

View from end-user perspective:

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/04.png)

View from Administrator perspective:

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/05.png)

But how to buy an application? Find an application that you want to add, select a proper licensing type (in most of the cases - Online) and click on the *Get the App* button!

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/06.png)

Now you can go back to the MEM portal, sync Applications from the Connectors tab and go to the Applications tab from the left side, and start assigning those applications!

RDP application is visible but is not assigned.

![Use Microsoft Store for Business with MEM!](/assets/images/posts/2021/MSfB-01/07.png)

Start assigning application which you want to add and... It is everything. Users will see this application later in the Company Portal application.

You have a configured MSfB!
