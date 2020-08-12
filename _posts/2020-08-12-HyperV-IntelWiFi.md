---
title: "Slow external connection using Hyper-V + Windows 10 and Intel WiFi cards"
categories:
    - Random
tags:
    - Windows 10
    - Random
    - Intel WiFi
    - Hyper-V

header-img: "assets/images/posts/SGMM-37/top.jpg"
subtitle:   "Slow external connection using Hyper-V + Windows 10 and Intel WiFi cards"
---
![Slow external connection using Hyper-V + Windows 10 and Intel WiFi cards](/assets/images/top_images/Windows10Top.jpg)Slow internet connection using Intel Wi-Fi / Hyper-V and Windows 10?

Last time I decided to rebuild my home device - Huawei Matebook D, install the Hyper-V role, and do some labs...

On below screen you can see stats of my network connection:

![Slow external connection using Hyper-V + Windows 10 and Intel WiFi cards](/assets/images/posts/HyperV-IntelWiFi/02.png)

And after creating an External Switch network speed looks like on below screen:

![Slow external connection using Hyper-V + Windows 10 and Intel WiFi cards](/assets/images/posts/HyperV-IntelWiFi/01.png)

Looks strange? Yep, I cannot work anymore on this kind of connection.

I decided to google it and found some interesting information. Most of them - are about set VmqWeight to 0 for network adapter created in our Hyper-V. 

Nope, that wasn't helpful. 

I tried to found another solution and found this solution:

1) Open Control Panel and find your network adapter which you're created on Hyper-V
2) Select Properties > Advanced
3) Find **IPv4 Large Send Offload, or Large Send Offload v2 (IPV4)** and set to *Disabled*

![Slow external connection using Hyper-V + Windows 10 and Intel WiFi cards](/assets/images/posts/HyperV-IntelWiFi/03.png)

That was fixed my issue with a slow Internet connection while using Hyper-V role on Windows 10.
