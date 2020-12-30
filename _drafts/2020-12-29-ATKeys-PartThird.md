---
title: "Personal usage of ATKeys (Third part of ATKey Series!)"
categories:
    - ATKey
tags:
    - ATKey
    - Fido
    - YubiKey

header-img: "/assets/images/top_images/ATKeyTOP.jpg"
subtitle:   "Personal usage of ATKeys (Third part of ATKey Series!)"
---
![Personal usage of ATKeys (Third part of ATKey Series!)](/assets/images/top_images/ATKeyTOP.jpg)Personal usage of ATKeys (Third part of ATKey Series!)

Previously, I written two posts about ATKey:

* [Improve security for your private accounts or on your company with ATKey! (First part of ATKey Series!)](https://www.piesik.me/2020/12/25/ATKeys-PartOne/)
* [Configure Azure AD and add keys to the end-user account (Second part of ATKey Series!)](https://www.piesik.me/2020/12/28/ATKeys-PartTwo/)

Today, I want to write less technical post about personal usage of ATKeys.

In previous post I written about usage those keys with Azure Active Directory, now I will focus on personal usage, like Microsoft Account, Facebook account, Chrome / Edge etc...

I will configure **ATKey.Card** to be my primary key for all personal usage.

![Personal usage of ATKeys (Third part of ATKey Series!)](/assets/images/posts/ATKeys-PartThird/01.jpg)

Why those key, instead of for example ATKey.Pro? Because **ATKey.Card** has a support for NFC, Bluetooth and USB-HID. So it is ideally to usage with my Windows device and Android telephones which I'm using daily.

I will start with adding my fingerprint to this key. For this, I will use software which can be downloaded from Microsoft Store, named *ATKey for Windows*. To download this application, follow [this link](https://www.microsoft.com/en-us/p/atkey-for-windows/9p7gr8w9sjd3)

When we install this software, first step what we need to do is...

![Personal usage of ATKeys (Third part of ATKey Series!)](/assets/images/posts/ATKeys-PartThird/02.png)

## Add and registery ATKey

To do this, you need to click on this option, provide name for your Key, touch multiple times sensor to add your fingerprint. Last step is verification of lastly added fingerprint.

This step is very easy to do, but if you have a problems with that - please watch a short movie which I prepared for you:

<iframe width="560" height="315" src="https://www.youtube.com/embed/vvvofkUcJYY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

If we properly enrolled this key, we can try to update key to receive a newest firmware.

## Updating firmware

To do this, select Options button for earlier added key, click on **Firmware update** and do necessary update.

From me, that was take aproximetly one minute to upgrade firmware on this key.

Like earlier, I prepared a short movie about that:

<iframe width="560" height="315" src="https://www.youtube.com/embed/yc1sjZ8soxE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Let's move to the next step - use key as logon methon (Windows Hello via CDF), instead of password.

This method is similar to those which we do last time

## Use a key as logon method

This step can be done also using *ATKey for Windows*. Everything what we need to do is open settings for our key, select **Companion for Windows Login** and do all steps, one by one. It is a very simple wizard.

If you have issues, let's watch below movie which I prepared for you:

<iframe width="560" height="315" src="https://www.youtube.com/embed/1UOvhq0imuw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

After the reboot, you need to touch key to login to the workstation. Nothing more.

### No passwords.

So, we have configured and up-to-date our security key, we can logon to our workstation using those key, but what next? How to use that key with our browser?



