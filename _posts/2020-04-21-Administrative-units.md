---
title: "Azure AD - Administrative Units"
categories:
    - Azure AD
tags:
    - Azure AD
    - Administrative Units
---
![Azure AD - Administrative Units](/assets/images/top_images/AzureADTOP.jpg)
Couple words about a new feature on Azure AD - Administrative Units.

There is a new feature on Azure AD - **Administrative Units**. Imagine, that you have three offices. One main office and two branches. Your HelpDesk users have access to all of the users, but you don't want that HelpDesk from the first branch can reset passwords for users from the secondary Branch Office and vice versa.

So, as a first step, you need to login to Azure Portal, go to the Azure Active Directory and open **Administrative units**. Here, you need to create a new location. You can see on the screenshot, I created two offices. 

* S01-Wroclaw
* S02-Warsaw

If you want to create a new Unit, you need to click *Add button*

!["Azure AD - Administrative Units"](/assets/images/posts/Administrative-units/01.png)

When you create an object, you can add directly users or groups to this Unit using **Users** or **Groups** tab. For example, I added three users to Wroclaw location

!["Azure AD - Administrative Units"](/assets/images/posts/Administrative-units/02.png)

Next step is to check **Roles and administrators** where you can find sample roles to add:

* Authentication administrator
* Groups administrator 
* Helpdesk administrator
* License administrator
* Password administrator
* User administrator

I think in the future more roles will be added.

!["Azure AD - Administrative Units"](/assets/images/posts/Administrative-units/03.png)

For example, I will add another user to role **User administrator**

!["Azure AD - Administrative Units"](/assets/images/posts/Administrative-units/04.png)

So, Lidia should have access to edit details of the user from Wroclaw location, but not other users. Let's check if that works.

I will log in to the Azure portal as Lidia and check:

For user: *Megan Bowen* edit button is disabled

!["Azure AD - Administrative Units"](/assets/images/posts/Administrative-units/05.png)

But for user *Grady Archie* edit button is enabled because Grady is added to the Wroclaw unit.

!["Azure AD - Administrative Units"](/assets/images/posts/Administrative-units/06.png)

Looks nice, right? 

That will help you to organize work for your helpdesk users.
