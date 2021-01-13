---
title: "[PL] Dodajemy NASa Synology do Active Directory"
categories:
    - Synology
tags:
    - Synology
    - Active Directory
    - PL post
---
!["[PL] Dodajemy NASa Synology do Active Directory"](/assets/images/top_images/SynologyTOP.jpg)Krótki post na temat dodania NASa Synology do usług Active Directory

W poprzednim [wpisie](https://www.piesik.me/2019/12/27/Backup-Windows-Synology/#) pokazałem wam w jaki sposób skonfigurować Synology Active Backup for Business z pojedyńczym urządzeniem. Dziś chciałbym trochę nawiązać do tego wpisu oraz dodać nasze urządzenie do usług Active Directory w systemie Windows, aby móc zarządzać np. uprawnieniami do folderów grupami, które są stworzone bezpośrednio w usługach katalogowych. 

W celu dołączenia do domeny przechodzimy do Control Panel > Domain/LDAP i wybieramy zakładkę **Domain**. Zaznaczamy checkboxa: *Join domain* i wpisujemy niezbędne dane.

!["[PL] Dodajemy NASa Synology do Active Directory"](/assets/images/posts/Dodajemy-Synology-do-AD/01.png)

Jeżeli zaznaczymy opcję: **Advanced domain options** będziemy mogli skonfigurować choćby adresy IP / nazwy hostów od naszych kontrolerów domeny oraz ustawić jak często mają się aktualizować grupy / użytkownicy. Tutaj polecam aktualizację automatyczną co godzinę, a jeżeli chcemu manualnie zaaktualizować listy, przechodzimy do zakładki Domain Users / Domain Group i klikamy **Update domain data**.

Po kliknięciu na Apply urządzenie zostanie skonfigurowane, a ekran końcowy powinien wyglądać w taki sposób:

!["[PL] Dodajemy NASa Synology do Active Directory"](/assets/images/posts/Dodajemy-Synology-do-AD/02.png)

Finalnie, urządzenie pojawi się w Active Directory:

!["[PL] Dodajemy NASa Synology do Active Directory"](/assets/images/posts/Dodajemy-Synology-do-AD/03.png)

Z problemów, które się u mnie pojawiły to MTU na Mikrotiku, które należało ustawić statycznie oraz musiałem ustawić manualnie VLANy na karcie sieciowej.

Krótko i na temat, ale post jest powiązany z przyszłymi rozwiązaniami nad którymi dla was pracuję.
