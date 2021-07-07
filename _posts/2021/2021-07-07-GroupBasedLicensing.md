---
title: "How to start using Group Licensing in the AAD?"
categories:
    - Azure AD
tags:
    - MEM
    - Licenses

header-img: "/assets/images/posts/2021/SSPR/top.jpg"
subtitle:   "How to start using Group Licensing in the AAD?"
---
![How to start using Group Licensing in the AAD?](/assets/images/posts/2021/GroupBasedLicensing/top.jpg)Let's clean up the mess with Microsoft Licenses using Group Licensing in the AAD!

Last time I spoke on the small webinar about how to get started with MEM. I had one slide about Group Licensing and today, I want to show you something more about it because it is a very good way to provide a proper license(s) for a specific group of people.

Basically, in small companies, there is a person, which is responsible for licensing, for providing, renewing, and taking back those licenses when someone leaving the firm. This person needs to remember about all necessary options. How we can help?

In the big organizations, where we have 1000+ people managing licenses is much difficult. What group of people should receive access to O365 E3 only without Intune? What group of people should receive access to the F1 version of Office 365? Ah, we cannot forget to test the enrollment to Intune so - we need to assign Intune licenses.

If we have created dynamic groups, based on parameters like the department, Job title, company name or even custom attributes OR we have a static group where we manually added specific users we can use a functionality named Group Licensing.

That will allow assigning a specific license to a specific group.

If we have a dynamic group, based on Department and when the user account is enabled we can assign the license. If we disable this account, the license will be revoked after the next synchronization.

About dynamic groups, I will create later some articles, because this topic is big and very interesting.

For example, I earlier created a group for all users who has something in the Department and the account is enabled.

![How to start using Group Licensing in the AAD?](/assets/images/posts/2021/GroupBasedLicensing/01.png)

From the left side, you can directly go to the Licensing management, by click on the **Licenses** button.

![How to start using Group Licensing in the AAD?](/assets/images/posts/2021/GroupBasedLicensing/02.png)

I already assigned the M365 licenses for that users, because I don't want to troubleshoot why some functions are not working for my test users. It is a developer tenant.

But in the real world, you can use multiple groups with different licensing. You don't need to enable all services.

For example, you can enable only specific services. For example - for first-line workers, enable only the Exchange and Teams. Or Intune, for enrollment. Depends on your requirements.

![How to start using Group Licensing in the AAD?](/assets/images/posts/2021/GroupBasedLicensing/03.png)

To view, what groups are using specific licenses (if we have different licenses on our tenant), go to the Azure AD > Licenses > select interesting for your license and go to the **Licensed groups** tab.

![How to start using Group Licensing in the AAD?](/assets/images/posts/2021/GroupBasedLicensing/04.png)

On this tab, you will see details about groups and on the Licensed Users, you will see all users who have this specific license. And - if they have that license based on group or on direct assignment.

For me - that functionality in the AAD is great!
