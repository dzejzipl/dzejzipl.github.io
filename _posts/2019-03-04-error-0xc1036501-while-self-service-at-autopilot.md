---
title: Error 0xc1036501 while Self-Service at AutoPilot
categories:
    - Intune
tags:
    - autopilot
    - deployment
    - intune
    - self service
---
![Error 0xc1036501 while Self-Service at AutoPilot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Nested-Virtualization-Internet-Connection/top.jpg)

Hi all.

Last time I was playing with Self-Service AutoPilot, where device is deploying automatically without any interaction from end user / administrator.

After creating profile on Intune, assigning to proper group and started deploying I received message that was problem while deploying etc.. Please contact with your administrator with error code:

**0xc1036501**

Everything what I was able to find on Internet was providing to More than just [ConfigMgr site](https://www.petervanderwoude.nl/) – direct link to post [here](https://www.petervanderwoude.nl/post/windows-autopilot-self-deploying-mode/) But on that site wasn’t provide much information how to fix that issue.

So I decided to find more information about that.

I was started with collecting logs from enrollment to USB drive and check logs from my computer:

![Error 0xc1036501 while Self-Service at AutoPilot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/error-0xc1036501-while-self-service-at-autopilot/1.png)

Looks similar? Nope, for me too isn’t look similar. So how to fix that issue?

You need to check **Azure AD > Mobility (MDM and MAM)** and check if you have more than **ONE** provider. On my case I have two: Microsoft Intune and the second version of Intune which I didn’t remember that i’m adding.

![Error 0xc1036501 while Self-Service at AutoPilot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/error-0xc1036501-while-self-service-at-autopilot/2.png)

After removing that one what you can see on screen, self-service deployment was started without any issues.
