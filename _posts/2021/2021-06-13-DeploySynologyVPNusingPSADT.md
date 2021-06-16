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
![Deploy Synology VPN Client using MEM and PSAppDeployToolkit](/assets/images/posts/2021/DeploySynologyVPNusingPSADT/top.jpg)Learn how to deploy Synology VPN Client using MEM and PSAppDeployToolkit

Because I have a Synology router at home - you can read the entire article [here](https://www.piesik.me/2021/06/09/SynologyRouters/) and I deployed a VPN Plus Server with Synology VPN on this same router I wanted to automatically install a client on my machines. I don't want to manually download the MSI file and click next, next, next, etc...

So I decided to use PSAppDeployToolkit (PSADT) for that case.

About PSADT I wrote an article [Deploy fonts using PSAppDeployTookit through Microsoft Endpoint Manager
](https://www.piesik.me/2021/03/25/DeployingFontsUsingPSADT/#)

So, let's start. I downloaded an MSI from the VPN Plus Server page, moved it to the Files folder on the PSADT location, and on the Installation phase I just used the command:

```powershell
Execute-MSI -Action 'Install' -Path "$dirFiles/SynoVPN.msi" -AddParameters "ALLUSERS=1"
```

For the uninstallation method I provided a command:

```powershell
Execute-MSI -Action 'Uninstall' -Path '{40BA7725-90D6-4377-9F4A-F009CA096592}'
```

After that, I packed it using **Microsoft Win32 Content Prep Tool** and moved to Intune.

For a detection method I provided a MSI without version:

```text
{40BA7725-90D6-4377-9F4A-F009CA096592}
```

And... It is everything. The client is installing from a system Context on the Intune.

![Deploy Synology VPN Client using MEM and PSAppDeployToolkit](/assets/images/posts/2021/DeploySynologyVPNusingPSADT/01.png)
