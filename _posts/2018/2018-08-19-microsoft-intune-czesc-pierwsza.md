---
title: "[PL] Microsoft Intune – część pierwsza"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/top.jpg"
subtitle:   "[PL] Microsoft Intune – część pierwsza"
---
![[PL] Microsoft Intune – część pierwsza](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/top.png)Microsoft Intune – część pierwsza

Zawsze marzyło mi się, aby móc napisać dla was artykuł o Intune.

Wpisem tym rozpocznę serię o Intune w połączeniu z Azure Active Directory i Office365. Kto wie czy też nie zahaczę również o Windows Small Business Server – ponieważ nikt o nim dobrze nawet nie pisze, a uważam, że jest to całkiem ciekawy produkt dla małych firm.

Tak właściwie to nie mam dokładnego planu o czym będę pisał, jest jedynie spora ilość gotowych notatek, które muszę przelać na bloga – zobaczymy czy mi się to uda.

Na początku postanowiłem rozpocząć od skonfigurowania brandingu naszej firmy. Całość opisałem już w poście Azure AD – konfigurujemy panel logowania. Wiele się od tamtego czasu nie zmieniło, więc post jest nadal aktualny. Polecam przeczytać i wrzucić te kilka obrazków, aby wszystko wyglądało profesjonalnie.

Drugim krokiem jest rozpoczęcie pracy z naszym tenantem – czyli rozpoczynamy od zalogowania się do portalu Azure, następnie z listy dostępnych usług wybieramy Intune i powinno pokazać nam się okno podobne do mojego:

![[PL] Microsoft Intune – część pierwsza](/assets/images/posts/2018/microsoft-intune-czesc-pierwsza/01.png)

To by oznaczało, że nie mamy skonfigurowanych naszych opcji i możemy rozpocząć od nowa. Kliknijmy więc na na napis: You haven’t enabled device management yet. Click here to start, aby rozpocząć.

Powinniście otrzymać informację o potrzebie wyboru sposobu działania Intune:

* Intune MDM Authority, które jest całkowicie w chmurze
* Configuration Manager MDM Authority, które może działać w połączeniu z Microsoft Configuration Manager

Dla mojego zastosowania wybiorę pierwszą opcję, ponieważ nie planuję stawiać żadnych rozwiązań on-premise na tę chwilę. I gdybyście się jednak kiedyś rozmyślili i chcieli zmienić sposób działania – to jest to możliwe do zrobienia bez potrzeby kontaktowania się z supportem Microsoftu i utracenia dostępu do zarządzanych urządzeń.

Już po chwili od wybrania otrzymacie komunikat:

![[PL] Microsoft Intune – część pierwsza](/assets/images/posts/2018/microsoft-intune-czesc-pierwsza/02.png)

Kolejną kwestią jest poprawna konfiguracja naszej domeny – muszą zostać dodane rekordy. O konfiguracji domeny przeczytacie w wpisie: [OVH, Office365 i własna domena](https://www.piesik.me/2016/11/15/ovh-office365-i-wlasna-domena/).

Jest jedna ważna aplikacja, którą będę używał na urządzeniach z Androidem, który będę używał do testów, mianowicie: Intune – company portal. Ta sama aplikacja jest dostępna również na komputery z systemem Windows 10, ale tutaj postaram się wykorzystać dodawanie do Azure Active Directory o czym trochę później.

W kolejnym wpisie będziecie mogli przeczytać o tym w jaki sposób dodamy testowego użytkownika, następnie utworzymy kilka grup oraz ustawimy, że dla danej grupy pojawią się opcje zainstalowania dodatkowych aplikacji z aplikacji Intune w telefonie / komputerze.
