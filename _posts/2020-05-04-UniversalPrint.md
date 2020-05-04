---
title: "M365 - Universal Print"
categories:
    - Microsoft 365
tags:
    - Universal print
    - intune
---
![M365 - Universal Print](/assets/images/top_images/IntuneTOP.png)Couple words about a new Feature on Microsoft 365 suite - Universal Print

Yep, that is this moment when I can share more details about the feature which is currently on public preview - Universal Print.

A couple of weeks ago I received an invite to join in a private program about a new feature - Universal Print. That was a very interesting feature - how to use our printers if we don't use any Print and Document Services on our local Active Directory? How to deploy our printers using Intune? 

For now, the answer is **Universal Print**. Using this functionality we can connect our devices to Azure AD, configure it and allow users to map it using standard Printing settings on their Windows 10 devices joined to our AAD. 

But let's start from the beginning. 

1. First, you need to assign for users and administrators licenses named: Universal Print. Why for Administrator? This account is used later to join the device to Azure AD. Remember, that should be the account with a role: Printer Administrator or Global Administrator.

![M365 - Universal Print](/assets/images/posts/UniversalPrint/01.png)

If you want, you can create a group of users and assign that license using Group licensing:

![M365 - Universal Print](/assets/images/posts/UniversalPrint/02.png)

After that, we need to download Connector on a device where is connected printer and login with account who has permissions which I described earlier.

![M365 - Universal Print](/assets/images/posts/UniversalPrint/03.png)

After logging in, you need to provide a connector name. It's something like a device name where these printers are connected. For example, if you have a two USB printer connected to the PC01, you can use this same name for the connector. That should be a clear name for you for troubleshooting purposes.

![M365 - Universal Print](/assets/images/posts/UniversalPrint/04.png)

When the connector will be registered, you need to choose what printers should be shared from the list from the right side:

![M365 - Universal Print](/assets/images/posts/UniversalPrint/05.png)

If you select one of your printers, button **Register** will be active and you can check if the device will show up on the left side.

Now it's time to check more details on **Universal Print** page on Azure AD > **Connectors**:

![M365 - Universal Print](/assets/images/posts/UniversalPrint/06.png)

As you can see, I named my connector using this same name which my printer has. On this page, you can see only the status of the connector.

If you want to do more with printers, especially share it, you need to go to page: **Printers** and select your printer:

![M365 - Universal Print](/assets/images/posts/UniversalPrint/07.png)

On the above screenshot, you see that it's not shared. Let's fix it!

When you open details, there will be a button to share a device. Use it (1), to share a group of people (2), that you can click a Refresh button to check if it's shared. If you want to check what users are permitted to use that printer, open the Members (4) tab.

![M365 - Universal Print](/assets/images/posts/UniversalPrint/09.png)

From the administrator side, it's everything. Let's now test from the End-User perspective.

User is opening *Printers & scanners* from Options and need a click a button **Add a printer or scanner**. After a couple of seconds, the printer should be available to install.

![M365 - Universal Print](/assets/images/posts/UniversalPrint/10.png)

If you're Administrator, you can back to Azure AD Universal Print page and check the status of printing:

![M365 - Universal Print](/assets/images/posts/UniversalPrint/11.png)

As you can see, deploying this feature is very easy and should help small companies that are using only Intune to manage and maintenance printers. You can choose what users which printer will be assigned. You don't need to assign a printer from the HR room to all of the users.

If you have any questions, please ping me below or using the Contact page!

Thanks for reading!
