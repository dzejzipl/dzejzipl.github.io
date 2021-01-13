---
title: "Deploy Azure Information Protection as Win32App on Intune"
categories:
    - Intune
tags:
    - Intune
    - Win32 Apps
    - AIP
---
![Deploy Azure Information Protection as Win32App on Intune]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/IntuneTOP.png) If you are interested, how to automatically deploy **Azure Information Protection** on your environment using Intune, that post is for you! :)

Last time I prepared a post about [deploying Chrome using Intune (PL language)](https://www.piesik.me/2019/05/05/deployment-chrome-za-pomoca-intune/#), so it will be a similar post. Let's start!

First, we should start with download the proper version of AIP. If we are using Unified Labeling, please download that version which contains "UL" on the name file. If not, we will use standard version: *AzInfoProtection_MSI_for_central_deployment.msi*

You can download that files from that page: https://www.microsoft.com/en-us/download/details.aspx?id=53018

Once you're done with downloading, please be sure that you have downloaded IntuneWinAppUtil.exe from GitHub. 

Let's open PowerShell and start with converting files. The proper command will be (please remember to change to your own paths):

```powershell
 .\IntuneWinAppUtil.exe -c "E:\IntuneWork\Win32App\AIP\MSI" -s "AzInfoProtection_MSI_for_central_deployment.msi" -o "E:\IntuneWork\Win32App\AIP\FinalFiles"
 ```

Where:

* ***-c*** is source folder
* ***-s*** is installation file
* ***-o*** is outpout folder

Final results looks like on my screen:

![Deploy Azure Information Protection as Win32App on Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Information-Protection-as-Win32App/01.png)

If that step is finished, please open [Device Management Portal](https://devicemanagement.portal.azure.com/), go to **Client Apps** > **Apps** > **Add**  and add new *Windows app (Win32)*.

Upload file which you're created on the latest step, configure the first tab named: **App Information** and go to the tab named **Program**. As you can see, Win32 Converter automatically created installation and uninstallation command.

![Deploy Azure Information Protection as Win32App on Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Information-Protection-as-Win32App/02.png)

You can choose your own requirements options and return codes, but you should check how to detect that software. I'm using for that **MSI detection rules**.

![Deploy Azure Information Protection as Win32App on Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Information-Protection-as-Win32App/03.png)

It's this same MSI content that you see on installation string.

When you configure those options, please create Save, assign to proper group and assing.

It will be deployed without any issues.
