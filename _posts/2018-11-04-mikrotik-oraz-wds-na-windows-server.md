---
title: "[PL] - Mikrotik oraz WDS na Windows Server"
categories:
    - Windows Server
    - Mikrotik
tags:
    - Mikrotik
    - Windows Server
    - WDS
    - PL Post
---
!["[PL] - Mikrotik oraz WDS na Windows Server"](/assets/images/top_images/mikrotikTOP.jpg)Konfigurujemy Mikrotika z rolą WDS na Windows Server

Czasem jest tak, że człowiek sobie wymyśli, że chciałby mieć wdrożone jakieś rozwiązanie w domu. I to zrobi.

Ja wczoraj sobie wymyśliłem, że chciałbym wdrożyć z powrotem Mikrotika do swojej domowej sieci jako główny router, a przy okazji zrobić działającego WDSa na poziomie lokalnej sieci. W Hyper-V zawsze to robiłem bez żadnego problemu, ponieważ tam był wystawiony vyOS jako router i cały ruch przechodził przez niego, więc… Postanowiłem to zrobić i nagle się okazało, że na sieci są setki różnych wersji jak to zrobić, a praktycznie żadna z nich nie jest do końca poprawna.

Wpis ten będzie się łączył z nową wersją poradnika do Mikrotika, która powstanie na dniach.

A więc zaczynamy.

Konfiguracja mojej sieci wygląda tak. Router > Hyper-V server i na nim postawione maszyny. Windows Server z skonfigurowana usługa WDS posiada adres 192.168.11.4 oraz DNS na 127.0.0.1, ponieważ posiada również zainstalowana usługę DNS, jako, że jest kontrolerem domeny dla lokalnej grupy testowej. Ten adres jest dla nas ważny.

Aby ustawić bootowanie z sieci przechodzimy do DHCP Server Boot options i dodajemy trzy nowe opcje DHCP.

Boot Options **60** z wartością: '***PXEClient***'

Boot Options **66** z wartością: '***adresIPWDS***'

Boot Options **67** z wartością: '***\boot\x64\wdsnbp.com***'

![[PL] - Mikrotik oraz WDS na Windows Server](/assets/images/posts/WDS-WindowsServer-Mikrotik/01.png)

U mnie to działa w dokładnie takiej konfiguracji. Widziałem sporo innych, ale żadna z nich mi nie działała poprawnie.

Gdyby wam nie działało, to pamiętajcie proszę o odblokowaniu portów na serwerze z zainstalowaną usługa WDS:

UDP – 67, 68, 69, 4011
TCP – 135, 137, 138, 139, 5040