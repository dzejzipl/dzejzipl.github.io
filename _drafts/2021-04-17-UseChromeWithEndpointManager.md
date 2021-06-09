---
title: "Deploy Chrome and manage it on your organization!"
categories:
    - Microsoft Endpoint Manager
tags:
    - Chrome
    - ADMX
    - Configuration Profile

header-img: "/assets/images/posts/2021/UseChromeWithEndpointManager/top.jpg"
subtitle:   "Deploy Chrome and manage it on your organization!"
---
![Deploy Chrome and manage it on your organization!](/assets/images/posts/2021/UseChromeWithEndpointManager/top.jpg)What if I told you that you can easily deploy Chrome and manage it on your organization using Microsoft Endpoint Manager in the cloud using ADMX templates?

Last time I learned something new and now I want to show you what I learned.

Today's topic will be managing Chrome using Microsoft Endpoint Manager. But first, we will deploy Google Chrome using PSAppDeployToolkit.

## Using **PSADT** for Chrome installation

As you know from one of my previous blog posts - I'm in love with PSAppDeployToolkit - *PSADT*. Many times I've used it in my work, but on my blog you can find only one post about it: [Deploy fonts using PSAppDeployTookit trough Microsoft Endpoint Manager](https://www.piesik.me/2021/03/25/DeployingFontsUsingPSADT/#).

To download Chrome with MSI package, navigate to [this](https://chromeenterprise.google/browser/download/) package and download necessary bundle. I've used X64 - 90.0.4430.72 version.

I copied installation file to Files folder and provided installation command in installation phase:

```powershell
Execute-MSI -Action 'Install' -Path "$dirFiles\GoogleChromeStandaloneEnterprise64_90.0.4430.72.msi"
```

For the uninstallation command I used:

```powershell
Execute-MSI -Action 'Uninstall' -Path '{D1DFD7FD-4FBA-3623-AA2E-4A857B4D2546}'
```

After rest of configuration, like name of applications etc I packed that package to win32App which I earlier descrbied [here](https://www.piesik.me/2019/09/06/Azure-Information-Protection-as-Win32App/#)

Now it is time to import this application to the MEM, which was described [here](https://www.piesik.me/2021/03/25/DeployingFontsUsingPSADT/#) in the *MEM part*.

After a some time, my application is installed on one of test machine. I deployed it to user group as optional application instead of required for group of devices.

![Deploy Chrome and manage it on your organization!](/assets/images/posts/2021/UseChromeWithEndpointManager/01.png)

## Configuration profiles in MEM

As always, we need to start from beggining.

For managing Chrome we will use Configuration Profiles. I described it many times in previous posts and I will be using it many times later. Today, we need to use "Custom" configuration profile instead of predefined.

![Deploy Chrome and manage it on your organization!](/assets/images/posts/2021/UseChromeWithEndpointManager/02.png)

In the first step, we need to provide a name and description. Platform and profile type are already selected. Please remember to use a proper name and description. When you have many of profiles, you will be grateful when you will be able to find a proper profile.

## Importing ADMX to MEM

First step, what you need to do is import existing ADMX template to the MEM portal. This is required, because it is not standard solution.

To do this, open a files which you downloaded ealier, go to *ADMX* folder and open file named **chrome.admx**.

Now, you need copy content from that file and go back to MEM portal and create a new OMA-URI settings. Provide a proper name, for example: Importing AMDX template to MEM, use a proper description and for OMA-URI please provide:

```text
./Device/Vendor/MSFT/Policy/ConfigOperations/ADMXInstall/Chrome/Policy/ChromeAdmx
```

For the value field copy content from *chrome.admx* file.

Please remember about this dot on the beggining.

First part is done, but we still don't see how to work with ADMX templates, yes?

## How to read ADMX templates

The first part will be everytime this same:

```code
./Device/Vendor/MSFT/Policy/Config/
```

Now we are moving to second part.

```code
Chrome~Policy~googlechrome
```

For most of cases after that phrase there will be a */NameOfSettingToSet* but not in every case. For example, when we want to set up settings for *LegacySameSiteCookieBehaviorEnabled* we need to add *ContentSettings* to the string before setting name.

So how the string will be look like?

```code
./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~ContentSettings/LegacySameSiteCookieBehaviorEnabled
```

Wait... From what place I know about this ContentSettings ?

1) First I will try to find a setting which I want to set up in the ADMX file
2) After that I will check what is **parentCategory**. If is different than *googlechrome* you need to change it on your OMA-URI path.

## Examples

Because I do some things during my daily work, I want to share with you some examples, which I learned.

### Continue running background apps when Google Chrome is closed

```text
./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome/BookmarkBarEnabled
```

Value:

```text
<enabled/>
```

or

```text
<disabled/>
```

Depending of our requirements.

### Second example

### Etc...
