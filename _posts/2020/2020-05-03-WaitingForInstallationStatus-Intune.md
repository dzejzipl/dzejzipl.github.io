---
title: "Intune: Waiting for install status"
categories:
    - Intune
tags:
    - applications
    - intune
---
![Intune: Waiting for install status](/assets/images/top_images/IntuneTOP.png)Couple words about Kiosk Profile and "Waiting for install status"

A couple of weeks ago I bought another new device to my lab - this time was HP EliteDesk 705 DM - really nice hardware with physical TPM 2.0 to test AutoPilot features. 

I have a plan to test Self-Deploying mode like for a Kiosk Devices, where end-users and admins don't need to do anything to deploy a device.

I configured a profile, added a new device, added applications like Company Portal and Kiosk Browser, assigned to the group with that machine... And I wait for the results. Kiosk profile was deployed successfully, but what with applications? On Intune I see only this:

![Intune: Waiting for install status](/assets/images/posts/WaitingForInstallationStatus-Intune/01.png)

Nothing more, applications weren't deployed to the device. I tried multiple times. Nothing change.

Today, Michael Niehaus from https://oofhours.com/ blog gives information that I should use an offline version of an application, not the Online. Yep, he was right, for that case I used an online version, like on below screen:

![Intune: Waiting for install status](/assets/images/posts/WaitingForInstallationStatus-Intune/02.png)

But how to get the Offline version of the application on Windows Store for Business? You need to enable that feature first on the Windows Store for Business > Manage > Settings > Shop> **Show offline apps** to *On*

![Intune: Waiting for install status](/assets/images/posts/WaitingForInstallationStatus-Intune/03.png)

After that, I check again the Kiosk Browser and the Offline option was here!

![Intune: Waiting for install status](/assets/images/posts/WaitingForInstallationStatus-Intune/04.png)


I assigned the application to Device Group and set **License type** to Device, not to user.

![Intune: Waiting for install status](/assets/images/posts/WaitingForInstallationStatus-Intune/05.png)

That's all. After that, application are properly deployed and Kiosk Profile works without any issues!

Thanks Michael! :)
