---
title: "Intune: Administrative templates"
categories:
    - Intune
tags:
    - intune
    - profile
    - administrative templates
---
![Intune: Administrative templates](/assets/images/top_images/IntuneTOP.png)Couple words about Administrative Templates for Windows 10 in Intune.

If you are working with Windows Server you need to know that the on-premise environment exists something like *GPO - Group Policy Object*. Using the GPO we can quickly adjust settings of our Windows for the whole environment. 

But on the Intune, that option does not exist, so Microsoft needs to create something like GPO in the cloud and it's named: **Administrative Templates.**.

Using the Administrative Templates we can adjust our environment - Windows 10, Office, Edge to fit our requirements. 

There are many options, for now almost 3400 settings to customize! They are divided into three parts:

* By product:
  * Windows
  * Office
  * Edge 77 and later
* By state:
  * Enabled
  * Disabled
  * Not configured
* By settings type:
  * User
  * Device

And what is most important - there is a search bar, so there is no need to scroll all pages one by one to search option what we want to customize.

!["Intune: Administrative templates"](/assets/images/posts/Intune-AdministrativeTemplates/01.png)

For example, we want to customize OneDrive settings that our users don't need to manually sign-in to OneDrive and there will be accessible only for selected by us tenants and a couple of other settings. So please find **Onedrive** settings on the list and start customizing:

!["Intune: Administrative templates"](/assets/images/posts/Intune-AdministrativeTemplates/02.png)

On the screen, you can see that I provided my Tenant ID, so users will be able to synchronize data from this company. 

Another thing which is enabled is: **Silently sign in users to the OneDrive sync client with their Windows credentials** which enabling auto-login to OneDrive using Azure AD credentials. 

!["Intune: Administrative templates"](/assets/images/posts/Intune-AdministrativeTemplates/03.png)

As you can see, only for ODB we have 21 settings to customize. New settings are published every month so it's good to check if settings which we need are now available.

When Administrative template will be created, you need to assign this template to group of users.

So - now you can start customizing your Windows 10 on your organization!
