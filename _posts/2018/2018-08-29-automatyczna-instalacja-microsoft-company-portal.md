---
title: "[PL] Automatyczna instalacja Microsoft Company Portal"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/top.jpg"
subtitle:   "[PL] Automatyczna instalacja Microsoft Company Portal"
---
![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/top.png)Automatyczna instalacja Microsoft Company Portal

Wcześniej w postach opisywałem np. w jaki sposób wymusić automatyczną instalację Microsoft Office na komputerach. Dziś pokażę wam w jaki sposób sposób dodać aplikację jako „Required” w Intune.

Jako, że jest to aplikacja, której nie można dodać w sposób łatwy musimy dodać ją pobrać jako oddzielne komponenty z Microsoft Store for Business, a później ją wrzucić do Intune.

Rozpoczynamy od przejścia do Microsoft Store for Business, wyszukaniu aplikacji Company Portal, dodaniu jej do naszych zasobów, a następnie musimy otworzyć Manage > Settings > Shopping experience i zaznaczyć checkboxa nazwanego: Show offline apps: Show offline licensed apps to people shopping in the Microsoft Store.

![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/01.png)

Po zaznaczeniu powyższej opcji jeszcze raz wyszukujemy aplikację Company Portal w sklepie i zmieniamy typ licencjonowania na Offline i klikamy Manage.

![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/02.png)

Po zaznaczeniu powyższej opcji jeszcze raz wyszukujemy aplikację Company Portal w sklepie i zmieniamy typ licencjonowania na Offline i klikamy Manage.

![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/02.png)

Ściągamy paczkę Offline + wszystkie zależności do trzech platform (x64, x86, ARM). Wagowo to wychodziło około 49Mb.

Kolejnym krokiem jest dodanie aplikacji.

Rozpoczynamy od przejścia do panelu Intune, Mobile apps > Apps > Add. Jako Typ aplikacji wybieramy Line-of-business app, w opcjach App package file wrzucamy wszystkie pliki, które są wymagane przez plik appxbundle. W zakładce App information wypisujemy wszystkie dodatkowe informacje, które mają się wyświetlić na stronie aplikacji. Jest to co prawda nie potrzebne, ponieważ ta aplikacja i tak się zainstaluje w tle, ale..

Po wrzuceniu plików na serwery należy skonfigurować przypisanie aplikacji do urządzeń.

Jak już pisałem wcześniej – będzie ustawiona jako required dla wszystkich użytkowników, którzy mają licencję Intune.

Finalnie wygląda to w taki sposób:

![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/03.png)

Po poprawnym rozpropagowaniu zasad – aplikacja pojawi się w Start menu jako zainstalowana. Po odpaleniu powinniśmy otrzymać wynik podobny do tego:

![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/04.png)

W portalu Intune również będą podane statystyki:

![[PL] Automatyczna instalacja Microsoft Company Portal](/assets/images/posts/2018/automatyczna-instalacja-microsoft-company-portal/05.png)
