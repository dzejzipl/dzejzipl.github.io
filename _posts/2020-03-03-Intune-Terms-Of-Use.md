---
title: "Microsoft Intune - Terms of use"
categories:
    - Intune
tags:
    - Intune
---
![„Microsoft Intune - Terms of use"](/assets/images/top_images/IntuneTOP.png)Ask your users to read and accept Terms of use.

Sometimes we need to be sure that users read and accepted internal Terms of use, but how to do this? Send an email and ask them for a reply with the message: "Yes, I read this email and accepted all rules"? Nope, it's not a good choice. 

There is a better way to do this - using Intune > Conditional Access and Terms of use. If we add any terms, they will be shown to the user on any of the software to accept. For example, today we create new terms, tomorrow end-user will open the first Outlook and on this Outlook client should accept terms. If that will be rejected, the connection will be rejected. 

That will be the first of posts which will be related to Conditional Access.

But how to create that terms of use and assign it to our users?

First, please logon to [Device Management](https://devicemanagement.portal.azure.com/) portal, open **Endpoint security** > **Conditional Access** > ***Terms of use**. We need to create a new one term:

!["Microsoft Intune - Terms of use"](/assets/images/posts/Intune-Terms-Of-use/01.png)

We need to provide our name, display name for end-users, upload *.pdf files with proper languages (could be one or more), set up requirements for end-users to accept on all devices and expand rules. We can set up expiring rules, for example, I set up this for one year. What is important, in the end, I selected the option that I will create manually Conditional Access policy later.

And how to create this Conditional Access policy?

First, open again Device Management Portal > **Endpoint Security** > **Conditional Access** > ***Policies*** and create a new one policy.

!["Microsoft Intune - Terms of use"](/assets/images/posts/Intune-Terms-Of-use/02.png)

* Users and group: Please select to which users this policy should be applied. Please remember to **TEST ON SMALL GROUPS OF USERS**
* Cloud apps or actions: I selected here to apply for all cloud apps, like Portal.Office.com / Exchange Online / Sharepoint, etc
* Conditions: On that case is not used
* Grant: Like on this screen access is granted only if my ToU is accepted.
* Session: like on Conditions, is not used on that case

Enable policy: I selected **On** because I'm testing it on small groups of users.

How does it look from the end-user site? For example like this:

!["Microsoft Intune - Terms of use"](/assets/images/posts/Intune-Terms-Of-use/03.png)

And it's it. This is the first of post related to the Conditional Access.
