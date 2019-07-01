---
title: "[PL] Deployment profili Wi-Fi za pomocą Intune"
categories:
    - Intune
tags:
    - Intune
    - deployment
    - PL post
---
![Deployment profili Wi-Fi za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/IntuneTOP.png)Dlaczego by nie ułatwić końcowemu użytkownikowi nawet takiej opcji jak automatycznego podłączenia pod sieć Wi-Fi w naszej firmie? Po co ma on iść do IT w celu usłyszenia hasła / wpisania tego hasła? Dlaczego by tego nie zautomatyzować?

Wszystko się rozbija o to, aby stworzyć nowy profil, który zostanie przypisany do odpowiedniej grupy urządzeń. Zaczynamy więc!

![Deployment profili Wi-Fi za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploying-wi-fi-profile-connection-using-intune/1.png)

Rozpoczynamy od tworzenia profilu z opcjami:

- Platform: **Windows 10 and later**
- Profile type: **Wi-Fi**

W **3** ustawiamy SSID naszej sieci oraz nazwę połączenia.

W punkcje **4** ustawiamy hasło do naszej sieci Wi-Fi.

I.. To wszystko. Po wdrożeniu tego połączenia do naszych urządzeń, użytkownik odłączając kabel LAN automatycznie podłączy się pod sieć Wi-Fi **nigdy** nie wpisując hasła.

Dosyć mocno ułatwi to pracę dla end-userów 🙂
