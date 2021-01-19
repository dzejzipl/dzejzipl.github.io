---
title: "[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune"
categories:
    - Intune
tags:
    - Company Portal
    - PL Post

header-img: "/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/top.jpg"
subtitle:   "[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune"
---
![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/top.png)Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune

W wpisie tym opowiem trochę o aplikacji mobilnej firmy Microsoft – Company Portal.

Dzięki tej aplikacji mamy możliwość dodania naszego urządzenia – począwszy od telefonu komórkowego, po tablet jak i komputer do Azure Active Directory. Pozwoli ona na wdrożenie odpowiednich reguł, które umożliwią dostęp do zasobów firmowych.

Dla przypomnienia dodam tylko, że wcześniej napisałem dwa wpisy:

* [Microsoft Intune – część pierwsza](https://www.piesik.me/2018/08/19/microsoft-intune-czesc-pierwsza/), w której opisałem podstawy związane z Intune
* [Microsoft Intune – cześć druga](https://www.piesik.me/2018/08/19/microsoft-intune-czesc-druga/), w której opisałem tworzenie użytkowników oraz grup

Nadszedł czas na trochę mięska czyli dodanie naszego pierwszego urządzenia do Azure Active Directory.

Testy przeprowadzę na aplikacji Company Portal ze sklepu Google Play oraz Honorze 8.

Przejdźmy krok po kroku z aktywacją. Po zainstalowaniu uruchamiamy aplikację i należy się zalogować swoimi danymi do organizacji:

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/01.png)

Po zalogowaniu musimy zezwolić naszemu tenantowi na zarządzanie naszym urządzeniem tak jak na screenie poniżej:

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/02.png)

Teraz krok najbardziej najcięższy dla każdego pracownika, który pomaga przy takich wdrożeniach, czyli tłumaczenie co my – jako IT możemy zrobić z Twoim urządzeniem i jakie dane zostaną do nas dostarczone.

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/03.png)

W kolejnym kroku dowiemy się jakie możliwości ma IT w związku z dodaniem Intune jako Administratora urządzenia i co możemy zrobić z takim urządzeniem.

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/04.png)

Po przejściu do kolejnego kroku jeżeli całe dodanie do Intune przejdzie poprawnie powinniśmy otrzymać komunikat jak poniżej:

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/05.png)

A to oznacza, że nasze urządzenie jest już zarządzane przez organizację. W momencie przejścia do zakładki Urządzenia / Devices powinniśmy zobaczyć nasze urządzenie (lub urządzenia, jeżeli używamy więcej niż jedno)

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/06.png)

Co nam to daje – skoro to tylko zainstalowana aplikacja na telefonie? Wejdźmy zatem do portalu Intune i już po chwili nasz telefon zostanie wyświetlony w menu Devices:

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/08.png)

Po wejściu w detale urządzenia zobaczymy wiele innych szczegółów:

![[PL] Microsoft Intune – część trzecia. Dodajemy urządzenie do Intune”](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/07.png)

Tak samo proces enrollmentu wygląda w urządzenia Apple, tabletach z Androidem – trochę inaczej w telefonach z Windows Phone, ale o tym już nie będę pisał, bo przecież nikt nie używa tej platformy.

W kolejnym wpisie poruszę dodanie komputera do Azure Active Directory, aby również mieć możliwość zarządzania nimi jak i przypisywania aplikacji.
