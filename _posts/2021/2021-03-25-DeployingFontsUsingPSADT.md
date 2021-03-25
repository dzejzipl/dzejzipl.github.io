---
title: "Deploy fonts using PSAppDeployTookit trough Microsoft Endpoint Manager"
categories:
    - MEM
    - PSAppDeployToolkit
tags:
    - Intune
    - PSADT

header-img: "/assets/images/top_images/psadt.png"
subtitle:   "Deploy fonts using PSAppDeployTookit through Microsoft Endpoint Manager"
---

![Deploy fonts using PSAppDeployTookit through Microsoft Endpoint Manager](/assets/images/top_images/psadt.png)A short manual about deploying fonts to end-user devices using Microsoft Endpoint Manager and PSAppDeployToolkit.

A couple of weeks ago I received a question from my colleague about how to deploy fonts to end-user devices using Microsoft Endpoint Manager (Intune).

Earlier, I saw multiple posts on how to do this using simple PowerShell scripts. Of course - that can be done this way, but I decided to learn how to use PSADT in different cases.

So what I have done?

## PSADT part

1) I downloaded a package from a GitHub page, copy files from the "Toolkit" folder to my work folder.
2) In the Deploy-application.ps1 file I changed information in the *VARIABLE DECLARATION* section to information about my package.
3) I copied necessary fonts to *SupportFiles* folder
4) Next thing, was removing the default installation prompt because in this case, I don't need it.

   ```powershell
   Show-InstallationWelcome -CloseApps 'iexplore' -AllowDefer -DeferTimes 3 -CheckDiskSpace -PersistPrompt
   ```

5) Now we need to install fonts, I will show you which code I created for that purpose:

    ```powershell
        $fonts = Get-ChildItem -Path $dirSupportFiles
        foreach ($font in $fonts) {
            Copy-File -Path "$dirSupportFiles\$($font.name)" -Destination "$envWindir\Fonts\$($font.name)"
            if ($font.Extension -eq ".ttf") {
                $fontType = "TrueType"
            }
            else {
                $fontType = "OpenType"
            }

            Set-RegistryKey -Key 'HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Fonts' -Name "$($font.baseName) $($fontType)" -Value $font.name -Type String
        }
    ```

    Code is very simple - get all fonts from the SupportFiles folder, copy them to the Fonts folder and register it in the registry
6) From PSADT it's is everything. We don't need to do anything else.

## Microsoft Win32 Content Prep Tool

1) You need to pack the earlier created package to the .intunewin file. The whole process I described [here](https://www.piesik.me/2019/09/06/Azure-Information-Protection-as-Win32App/#).

## MEM part

1) You need to login into the MEM portal and add a new Win32 application. Select created earlier package and provide the necessary information.
2) For Installation command use: **%windir%\sysnative\windowspowershell\v1.0\powershell.exe -ExecutionPolicy Bypass -file "Deploy-Application.ps1"**
3) For uninstallation command you can use: **%windir%\sysnative\windowspowershell\v1.0\powershell.exe -ExecutionPolicy Bypass -file "Deploy-Application.ps1 -DeploymentType Uninstall"** but in my script there is no uinstallation commands.
4) Because I'm installing it for everyone in the company, I selected System as Install behavior.
5) As detection rule I provided to check if a file with the font exists in the C:\Windows\Fonts folder.
6) In the end, I assigned **as required** for all devices.

How it is finally look in Installation Status?

![Deploy fonts using PSAppDeployTookit through Microsoft Endpoint Manager](/assets/images/posts/2021/DeployingFontsUsingPSADT/01.png)

I'm planning more posts about PSADT because I'm in love with that software.

Thanks for reading!
