---
title: Deploy Start Menu using Intune
categories:
    - Intune
tags:
    - intune
    - profile

---
![Deploy Start Menu using Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploying-wi-fi-profile-connection-using-intune/top.png)
Start menu on fresh installation of Windows is ugly. Is very ugly, just see on my screen:

![Deploy Start Menu using Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploy-start-menu-using-intune/1.png)

Why I should work with that kind of menu?

Maybe better idea will be deploy start menu looks this same on every device in our company?

For example on that blog post we will deploy start menu looks like on below screen:

![Deploy Start Menu using Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploy-start-menu-using-intune/2.png)

It’s quite looks better, right?

Firstly, we need to prepare Start menu on another computer and export that menu to XML file using PowerShell command:

```powershell
Export-StartLayout -path menu.xml
```

When export is completed we can start with creating Device Profile like on below screen:

![Deploy Start Menu using Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploy-start-menu-using-intune/3.png)

* Platform: **Windows 10 and later (1)**
* Profile type: **Device Restriction (2)**
* Scope: **Start (3)**
* On fourth point we need to upload created XML file

When the policy is created, need to be assigned to proper group. On end device you can click: Sync.

After couple minutes you will see new Start Menu on screen.

Have fun!
