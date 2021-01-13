---
title: "My home lab - third part"
categories:
    - Random
tags:
    - Home Lab
---
![My home lab](/assets/images/top_images/HomeLab.jpg)Third post about my Home Lab.

On the [first post](https://www.piesik.me/2020/07/26/HomeLab/) you can read more about hardware. In the [second post](https://www.piesik.me/2020/08/18/HomeLab2/#) I wrote something about hardware changes and what was done - installing AD DS + DNS, installed virtual machines and joined to a domain. Nothing special. 

But today we will install WAC - *Windows Admin Center* and Remote Support Administration Tools on one of a machine (*HV01-M03*). After that - we will install Azure AD Connect to synchronize our data with Azure AD.

## First part. Installing WAC

As always before doing some changes in the lab - I'm doing a snapshot of my VM. It's for backup purposes. 

After that, I downloaded WAC from [this URL](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-admin-center) and started installing. 

Next, next, next... On-screen: *Configure Gateway Endpoint* I selected only the first checkbox. I will not use WinRM over HTTPS because I don't have any certificates yet.

![My home lab - part third](/assets/images/posts/HomeLab-part3/01.png)

On the next screen, I selected that I want to generate a certificate and redirect HTTP port 80 to HTTPS (443)

![My home lab - part third](/assets/images/posts/HomeLab-part3/02.png)

After installation you should be able to open https://yourHostName (for me it's: https://hv01-m03.piesik.online) and see something like this:

![My home lab - part third](/assets/images/posts/HomeLab-part3/03.png)

When you click **Add**, you can add a new Windows 10 devices, Windows Server, Server clusters, or Azure VMs. For now, I will add all of my servers - so I will choose *Servers* > Search Active Directory. As a server name, I will use * (wildcard) to search all servers. 

![My home lab - part third](/assets/images/posts/HomeLab-part3/04.png)

Now if you want to connect - just click a connect and provide username from **local administrators** group. It's important not to use a domain account for that case. How to do this? Please read [this blog post](https://www.piesik.me/2020/08/22/UseWACWithouDomainAdmin/) 

And it's everything. Now you can use WAC of any of your machines.

![My home lab - part third](/assets/images/posts/UseWACWithouDomainAdmin/top.png)

## Second part. Installing RSAT

So, we have installed a WAC and now we should install **Remote Server Administration Tools** on one of the machines to have a possibility to manage all our servers. Yes, we can use for that WAC too, but sometimes - it's faster to user RSAT.

Just connect to the machine which will be used for that case and open *Server Manager* > *Manage* > *Add Roles and Features Wizard*. On the second step select your server. On *Server Roles* we don't select anything, but on the next step, we will select the necessary tools to have installed in our environment.

![My home lab - part third](/assets/images/posts/HomeLab-part3/05.png)

## Third part. Installing Azure AD Connect

About Azure AD Connect I wrote four blog posts, but all of them are in the Polish Language so I will start from the beginning. 

What is an Azure AD connect you can read [here](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect) but the most important benefit is that you have one database for your users and users can use one password for Azure AD and local AD. 

Ok, after downloading exe file from Microsoft site you can start installing AAD Connect. 

![My home lab - part third](/assets/images/posts/HomeLab-part3/06.png)

If you want to change default settings, service accounts or use another database for AAD Connect - select **Customize** or if you're using it as I on home lab - select **Use express settings**

![My home lab - part third](/assets/images/posts/HomeLab-part3/07.png)

A couple of next steps are logging to Global Administrator Account on your tenant, provide domain admin and password for this account and select if you want to start the synchronization after installation. 

When the installation is completed - you will see this information:

![My home lab - part third](/assets/images/posts/HomeLab-part3/08.png)

That means that you don't have enabled Recycle Bin for your AD and it's strongly recommended to enable it. How?

```powershell
Enable-ADOptionalFeature 'Recycle Bin Feature' -Scope ForestOrConfigurationSet -Target "yourDomainName"
```

![My home lab - part third](/assets/images/posts/HomeLab-part3/09.png)

On the end - you can open Azure AD site and check if there is active synchronization for your tenant:

![My home lab - part third](/assets/images/posts/HomeLab-part3/10.png)

In the next part, we will cover some more functions about Azure AD Connect and prepare my lab to work with Intune.
