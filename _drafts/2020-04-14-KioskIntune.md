---
title: "Create a Kiosk Device using Intune"
categories:
    - Intune
tags:
    - Intune
    - Kiosk
---
!["Create a Kiosk Device using Intune"](/assets/images/top_images/IntuneTOP.png)Couple words about deploying Kiosk devices using Intune...

What is a Kiosk Device? Maybe first I will provide a definition from Wikipedia:

> An electronic kiosk (or computer kiosk or interactive kiosk) houses a computer terminal that often employs custom kiosk software designed to function while preventing users from accessing system functions. Indeed, kiosk mode describes such a mode of software operation. Computerized kiosks may store data locally, or retrieve it from a computer network. Some computer kiosks provide a free, informational public service, while others serve a commercial purpose (see mall kiosk). Touchscreens, trackballs, computer keyboards, and pushbuttons are all typical input devices for interactive computer kiosk. Touchscreen kiosks are commercially used as industrial appliances, reducing lines, eliminating paper, improving efficiency and service. Their uses are unlimited from refrigerators to airports, health clubs, movie theaters and libraries.

So, if we are know what is a Kiosk device, let's start with build simple device, which will have only one of software - Kiosk Browser and don't allow users to do anything else.

We will use for that Device Configuration > **Profiles** and create a new one with type **Kiosk** with proper for us name.

## Case first

In that case we will use sample application named Kiosk Browser and allow users to visit only one page. 

First, we need to add Kiosk Browser from Microsoft Store for Business to our tenant and assign to group of devices to which we will apply kiosk profile. 

!["Create a Kiosk Device using Intune"](/assets/images/posts/KioskIntune/01.png)

After that, we will create a profile with selected **Single app, full-screen**, and select **Auto Logon** as *user logon type*. As Application type please select **Add Kiosk Browser**

We can configure our settings like on screen:

!["Create a Kiosk Device using Intune"](/assets/images/posts/KioskIntune/02.png)

And I we want to allow to visit only specific websites, we need to upload *.csv file with website adresess - like on below screen:

!["Create a Kiosk Device using Intune"](/assets/images/posts/KioskIntune/03.png)

When profile will be created, you need to assign it to specific group of devices. I will use that same group which I selected for a Kiosk Browser.