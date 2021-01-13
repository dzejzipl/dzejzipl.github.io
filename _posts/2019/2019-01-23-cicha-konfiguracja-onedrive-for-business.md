---
title: "[PL] „Cicha” konfiguracja OneDrive for Business"
categories:
    - Intune
tags:
    - Intune
    - Administrative Templates
    - OneDrive for Business
    - PL post
---
![„Cicha” konfiguracja OneDrive for Business]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/IntuneTOP.jpg)Backup danych jest ważny. Można do tego wykorzystać OneDrive for Business, gdzie nasi pracownicy będą musieli trzymać swoje wszystkie dane.

Ale to wymaga wpisania przez nich loginu i hasła podczas pierwszej konfiguracji, po co ich męczyć z tym?

Ostatnio opisałem nowość, którą Microsoft wprowadził – [Administrative Templates](https://piesik.me/2018/12/18/administrative-templates-w-intune/). Idealnym przykładem w jaki sposób możemy wykorzystać takie Intunowe GPO jest właśnie cicha konfiguracja OneDrive for Business. Zrobimy to w taki sposób, aby po restarcie użytkownik widział swój folder.

Bez klikania. Bez wpisywania loginów, haseł. Wszystko automatycznie.

![„Cicha” konfiguracja OneDrive for Business]({{ site.url }}{{ site.baseurl }}/assets/images/posts/cicha-konfiguracja-onedrive-for-business/1.png)

Dla przykładu tak jak tutaj:

![„Cicha” konfiguracja OneDrive for Business]({{ site.url }}{{ site.baseurl }}/assets/images/posts/cicha-konfiguracja-onedrive-for-business/2.png)

Jak tego dokonać?

Przechodzimy na stronę [https://devicemanagement.portal.azure.com/](https://devicemanagement.portal.azure.com/) > **Device configuration** > **Profiles** i rozpoczynamy dodawanie nowego profilu.
Platform: **Windows 10 and later**
Profil type: **Administrative templates**

![„Cicha” konfiguracja OneDrive for Business]({{ site.url }}{{ site.baseurl }}/assets/images/posts/cicha-konfiguracja-onedrive-for-business/3.png)

Rozpoczynamy od skonfigurowania opcji:

![„Cicha” konfiguracja OneDrive for Business]({{ site.url }}{{ site.baseurl }}/assets/images/posts/cicha-konfiguracja-onedrive-for-business/4.png)

Gdzie pod **Allow syncing OneDrive accounts for only specific organizations** mam wpisanego swojego tenanta.

I co? Nic więcej? Ano nic więcej.

Dzięki puszczeniu takiego profilu nastąpi cicha konfiguracja OneDrive i użytkownik będzie miał swoje dane na komputerze.
