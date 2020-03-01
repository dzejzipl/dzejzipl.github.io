---
title: "Catch Azure AD Logs to Log Analytics!"
categories:
    - Azure AD
tags:
    - Azure AD
    - Log Analytics
---
!["Catch Azure AD Logs to Log Analytics!"](/assets/images/top_images/AzureADTOP.jpg)Do you know that you can store all logs from Azure AD on Log Analytics and it's completely free? 

Short story. A couple of days ago I created a new test tenant using Microsoft Developer page and now I have 25 licenses M365 E5 and 170€ to use with Microsoft Azure <3. Looks good and I can promise that I will write couple posts. Some of them will be for beginners, another for more advanced users.

So, start first with that which is important for our security team - logs. 

## Logs everywhere.

By default, logs what we have on Azure AD looks like this:

!["Catch Azure AD Logs to Log Analytics!"](/assets/images/posts/Catch-AzureAD-Logs/01.png)

I think for beginning could you enough, but as I wrote - our security teams need more details and time frame, for example from the last 6 months. 

So why don't to use **Azure Log Analytics**? The first 5 GB is free and unfortunately, for free version data retention is only 31 days. For more, we need to pay 0,12$ per GB per month. But to be clear, for a small organization that will be less than one dollar per month. 

First, we will create New Log Analytics Workspace and after that, set settings that proper information from our AAD will be saved to our workspace.

!["Catch Azure AD Logs to Log Analytics!"](/assets/images/posts/Catch-AzureAD-Logs/02.png)

When the resource will be deployed, go to the Azure AD, select from the left menu **Diagnostic Settings** > ***Add diagnostic setting***

Configure all options (select which log you want to export) and select that you want to send logs to Log Analytics (like on my screen) and click Save!

!["Catch Azure AD Logs to Log Analytics!"](/assets/images/posts/Catch-AzureAD-Logs/03.png)

Wait 15 minutes and check if there is a logs on **Logs** tab.

Have fun! :)
