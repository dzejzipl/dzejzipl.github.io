---
title: "[PL] Intune + TeamViewer = Remote Support w akcji!"
categories:
    - TeamViewer
tags:
    - TeamViewer
    - PL Post
---

!["[PL] Intune + TeamViewer = Remote Support w akcji!"](/assets/images/top_images/TeamViewerTOP.jpg)Intune + TeamViewer = Remote Support w akcji!

Remote Support w naszej organizacji jest bardzo ważny. Często zdarza się tak, że komputery są rozrzucone po piętrach, po siedzibach, a część użytkowników w ogóle pracuje z domu. Jak się wtedy łączyć? Jeżeli użytkownik jest wpięty do naszej sieci – nie ma żadnego problemu – jesteśmy w tej samej adresacji IP. Jeżeli pracuje z domu i jest podłączony do VPNa – także nie ma żadnego problemu, bo będziemy się w stanie podłączyć do takiego użytkownika. Ale co w sytuacji gdy mamy środowisko bez Active Directory ?

W poprzedniej pracy udało mi się wdrożyć Team Viewer na każdym komputerze – dzięki temu moja praca stała się dużo łatwiejsza i nie musiałem robić wycieczek pomiędzy biurami oraz mogłem supportować użytkowników, którzy pracowali z domu.

Poprzednio opisałem sporo funkcji z Intune – dziś natomiast chciałbym wam przedstawić jedną integrację – TeamViewer w współpracy z Azure AD.

Seria ta będzie składała się z kilku postów, które będę na bieżąco pisał i wrzucał. Cały spis treści znajdzie się właśnie poniżej:

* [Wprowadzenie oraz wymagania](https://www.piesik.me/2018/11/09/intune-teamviewer-remote-support-w-akcji/)
* [Deploy aplikacji TeamViewer przez Intune dla Androida / iOS](https://www.piesik.me/2018/11/26/deploy-aplikacji-teamviewer-przez-intune-dla-androida/)
* Deploy aplikacji TeamViewer przez Intune dla Windowsa
* [Konfiguracja Intune do współpracy z TeamViewer](https://www.piesik.me/2018/11/30/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/)
* [Dostosowywanie modułu „Host”](https://www.piesik.me/2018/12/04/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/)
* [Pomoc zdalna dla użytkowników z poziomu Portalu Intune](https://www.piesik.me/2018/12/05/remote-assistance-w-intune-teamviewer/)

Główne założenie tej serii jest takie, aby przedstawić wam w jaki sposób skonfigurować Azure AD, wdrożyć aplikację na komputery naszych pracowników oraz umożliwić szybszą pracę osobom z HelpDesku.

Jedyne wymaganie, które jest ciężko spełnić to licencja minimum premium lub corporate w celu rozpoczęcia pracy.

Pozostałe kroki zostaną wam przedstawione wam krok po kroku – have fun! 😉
