---
title: "[PL] WAC + Hyper-V Server"
categories:
    - Windows Server
tags:
    - Windows Server
    - WAC
    - Hyper-V
    - PL post
---
![WAC + Hyper-V Server
]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WACTOP.jpg)
Kiedyś, dawno temu napisałem dwa artykuły:

- [Windows Admin Center](https://piesik.me/2018/06/03/windows-admin-center/) – czyli zarządzanie naszymi serwerami z poziomu jednego GUI
- Oraz o wstępnej konfiguracji [Hyper-V server](https://piesik.me/2017/04/17/microsoft-hyper-v-server-2016-instalacja-oraz-konfiguracja/).  

Temat miał potencjał, niestety brak czasu spowodował, że go nie wykorzystałem.
Ostatnio w komentarzu zobaczyłem, że kolega Ziema pyta się czy da się skonfigurować WAC w taki sposób, aby móc korzystać z Hyper-V server. Główna odpowiedź to:

## Tak, da się

Wstępną instalację maszyny przeprowadzamy z drugiego wpisu. Czyli instalujemy aktualizacje, włączamy Remote Management, nadajemy nazwę jak i ustawiamy konfigurację IP.

Jeżeli już to zrobiliśmy, odpalamy lokalną instancję WAC, dodajemy nasze urządzenie poprzez wpisanie adresu IP oraz użycie lokalnego użytkownika i hasła:

![WAC + Hyper-V Server
]({{ site.url }}{{ site.baseurl }}/assets/images/posts/wac-hyper-v-server/1.png)

I to wszystko.

![WAC + Hyper-V Server
]({{ site.url }}{{ site.baseurl }}/assets/images/posts/wac-hyper-v-server/2.png)

I już możemy tworzyć wirtualne maszyny, zarządzać switchami, grupami oraz robić wiele, wiele fajnych rzeczy.

Have fun Ziema!
