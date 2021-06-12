---
title: "Deploy Synology VPN Client using MEM and PSAppDeployToolkit"
categories:
    - MEM
tags:
    - PSAppDeployToolkit
    - Synology
    - VPN Client

header-img: "/assets/images/posts/2021/DeploySynologyVPNusingPSADT/top.jpg"
subtitle:   "Deploy Synology VPN Client using MEM and PSAppDeployToolkit"
---
![Deploy Synology VPN Client using MEM and PSAppDeployToolkit](/assets/images/posts/2021/DeploySynologyVPNusingPSADT/top.jpg)Learn how to eploy Synology VPN Client using MEM and PSAppDeployToolkit

Because I have a Synology router in home - you can read entire article [here](https://www.piesik.me/2021/06/09/SynologyRouters/) and I deployed a VPN Plus Server with Synology VPN on this same router I wanted to automatically install a client on my machines. I don't want to manually download MSI file and click next, next, next etc...

So I decided to use PSAppDeployToolkit (PSADT) for that case.

About PSADT I already written article [Deploy fonts using PSAppDeployTookit trough Microsoft Endpoint Manager
](https://www.piesik.me/2021/03/25/DeployingFontsUsingPSADT/#)

So, let's start. I downloaded a MSI from VPN Plus Server page, moved it to Files folder on the PSADT location and on the Installation phase I just used command:

```powershell
Execute-MSI -Action 'Install' -Path "$dirFiles/SynologyVPNClient.msi"
```

For the uninstallation method I provided a command:

```powershell
Execute-MSI -Action 'Uninstall' -Path '{40BA7725-90D6-4377-9F4A-F009CA096592}'
```

After that I packed it using **Microsoft Win32 Content Prep Tool** and moved to Intune.

For a detection method I provided a MSI without version:

```text
{40BA7725-90D6-4377-9F4A-F009CA096592}
```

And... It is everything. Client is installing from a system Context on the Intune.

![Deploy Synology VPN Client using MEM and PSAppDeployToolkit](/assets/images/posts/2021/DeploySynologyVPNusingPSADT/01.png)
