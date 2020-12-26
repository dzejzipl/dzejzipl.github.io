---
title: "Improve security for your private accounts or on your company with ATKey! (Part one!)"
categories:
    - ATKey
tags:
    - ATKey
    - Fido
    - YubiKey

header-img: "/assets/images/top_images/ATKeyTOP.jpg"
subtitle:   "Improve security for your private accounts or on your company with ATKey!"
---
![Improve security for your private accounts or on your company with ATKey!](/assets/images/top_images/ATKeyTOP.jpg) Be more secure with ATKey secure keys!

A couple of weeks ago I received a package from AuthenTrend company with security keys. I decided to show you, how I will use the content of this package, also... How to improve some security for your private accounts, like Outlook, Google, Facebook accounts. I don't want to write only about Azure AD, but that will be of course described too.

I want to shortly introduce what I will describe in my posts:

* What are those security keys which I received?
* How I can use it?
* How I can do an initial configuration?
* How to update firmware on those keys?
* How to configure Azure AD for End-Users
* How to enable Azure AD MFA using that keys
* How to secure your private accounts
* Also, how to work with On-Prem environment and Windows Hello
* Comparision to YubiKey (YubiKey 5 NFC and YubiKey 5C)

![Improve security for your private accounts or on your company with ATKey!](/assets/images/posts/ATKeys-PartOne/01.jpg)

In the below picture, you see every of the key which I have.

The list of topics, which I want to cover is quite long, so that post which are you currently reading is only an introduction. Tomorrow I will show you how to configure Azure AD and how to enroll key by end-user to use it to **logon to websites**. In the next posts, I will show you how to configure a workstation to use a key as the authentification method and many, many more!

![Improve security for your private accounts or on your company with ATKey!](/assets/images/top_images/ATKeyTOP.jpg)

* On the left, we have **ATKey.Hello** - more details [here](https://authentrend.com/atkey-hello/)
* In the middle we have **ATKey.Pro** - more details [here](https://authentrend.com/atkey-pro/)
* And on the right is **ATKey.Card**, you can read about it [here](https://authentrend.com/atkey-card/)

Three keys, many possibilities to use.

Keys, which I received allow us to use it with Windows devices, Android, and iOS phones with built-in NFC or Mac Devices. Let's look at the below table to get more information:

|     Key    |          Interfaces          |            Where we can use it?            |
|:----------:|:----------------------------:|:---------------------------------------:|
|  ATKey.Pro |   USB 2.0 A and USB type C   |        Windows and macOS devices        |
| ATKey.Card | USB 2.0 A, Bluetooth, and NFC | Windows, macOS, iOS, and Android devices |
|  ATK.Hello |        USB 2.0 A only        |           Windows Devices only          |

What is important, each key is HID compatible, so you don't need to download drivers to each of the devices. Also, if you want to add your fingerprint to the key, you don't need to download additional software. If you have a Windows operating system, you can do this on Windows Settings, also there is a stand-alone mode to enroll your fingerprint without any of the software. Just click three times the side-button and enroll your finger to the device!

There is one magic word that can define each of the keys I have.

### Passwordless.

What it does mean?

> "Passwordless authentication is an authentication method in which a user can log in to a computer system without entering (and remembering) a password or any other knowledge-based secret."
>
> *Source: [Wikipedia](https://en.wikipedia.org/wiki/Passwordless_authentication)*

### If you're working for any of company you will be interested about below information:

AuthenTrend has an offer to SMB companies. If your company has more than 250 users, you can signup in for the Passwordless program which is co-hosted with Microsoft. What is the best benefit? You can receive 20 ATKey.Pro to use them with your users and improve security in your organization.
Unfortunately, this program is limited only to 200 customers, so don't waste your time and enroll today! **You have time only to 31 of January 2021!**

### Biggest difference between ATKey and YubiKey?

If you're using YubiKey keys, to logon you need to touch golden circle using any of finger. If you're using ATKey, you need to use a finger that was enrolled.
What does it mean? That means if you using an ATKey you are more secured because even if someone will steal your key, they still need your finger to logon into the device or service!

What next? As I wrote earlier, it is only an introduction. In the next post, I will show you a real example of how to use one of those keys. We will start by enrolling our fingerprint to key and updating the device with a new firmware.

Stay safe and wait for other posts!
