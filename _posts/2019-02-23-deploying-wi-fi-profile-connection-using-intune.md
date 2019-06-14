---
title: Deploying Wi-Fi profile connection using Intune
categories:
    - Intune
tags:
    - intune
    - profile

---
![Deploying Wi-Fi profile connection using Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploying-wi-fi-profile-connection-using-intune/top.png)

On that post I want to show you how to deploy Wi-Fi profile using Intune. That means – user don’t need to know what is a password for our small Wi-Fi network.

Let’s start!

First we should create new Device Profile with settings:

* Platform: **Windows 10 and later**
* Profile type: **Wi-Fi**

![Deploying Wi-Fi profile connection using Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploying-wi-fi-profile-connection-using-intune/1.png)

When we select proper option, we can start with configure our settings. On **3** you need to insert SSID and Connection Name, on **4** you need insert password to your network.

It will works only when you have WPA(2) WiFi connection. If you have Enterprise network – select **Enterprise** instead of **Basic** on Wi-Fi type.

After assignment policy should deploy without any issues. When user disconnect LAN cable – Wi-Fi connection will connect automatically.

From end-user there is not exist any requirements.

Have fun!
