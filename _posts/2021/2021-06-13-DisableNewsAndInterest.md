---
title: "Disable News and Interest using MEM (Intune)"
categories:
    - MEM
tags:
    - Settings Catalog
    - Intune

header-img: "/assets/images/posts/2021/DisableNewsAndInterest/top.jpg"
subtitle:   "Disable News and Interest using MEM (Intune)"
---
![Disable News and Interest using MEM (Intune)](/assets/images/posts/2021/DisableNewsAndInterest/top.jpg)Learn how to disable News and Interest using MEM (Intune)

On the last version of Windows (20H2) every user received a "nice" feature, which is located on the Taskbar. It's called **News and Interest**.

For me is not necessary and I can right-click on my taskbar and disable it. But for most organizations, that option should be configured by IT Admins.

You can use it for that GPO settings, but I will use MEM - Microsoft Endpoint Manager (the old name: Intune)

To disable this setting, create a new **Settings catalog** and select the *News and Interest* section.

Enable it or disable it by default for all users.

![Disable News and Interest using MEM (Intune)](/assets/images/posts/2021/DisableNewsAndInterest/01.png)

After that, assign to a group of devices.

On the next reboot (or resetting explorer.exe process) that option will be gone.
