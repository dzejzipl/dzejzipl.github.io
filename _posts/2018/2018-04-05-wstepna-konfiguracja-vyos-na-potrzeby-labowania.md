---
title: "[PL] Wstępna konfiguracja vyOS na potrzeby labowania"
categories:
    - Other
tags:
    - vyOS
    - PL Post

header-img: "/assets/images/top_images/vyosTOP.jpg"
subtitle:   "[PL] Wstępna konfiguracja vyOS na potrzeby labowania"
---
![[PL] Wstępna konfiguracja vyOS na potrzeby labowania](/assets/images/top_images/vyosTOP.jpg)Wstępna konfiguracja vyOS na potrzeby labowania

Moja ostatnia nauka koncentrowała się na Windows Server, deploymentach i ogólnej obsłudze sieci w systemach Windows. Nie chciałem tego robić na istniejącej infrastrukturze, dlatego postanowiłem na moim domowym serwerze zainstalować wirtualny router o nazwie vyOS. Jest to oprogramowanie oparte na dystrybucji Linuxa dostosowane, aby zarządzać naszą siecią. Więcej możecie przeczytać pod tym linkiem.

Ten artykuł, który właśnie czytacie jest wstępniakiem do konfiguracji naszej sieci pod Windows Server właśnie. Główne założenie jest takie, aby nasza maszyna z vyOS miała dwie karty sieciowe. Jedna, która dostarcza nam Internet od Providera nazwana WAN oraz druga, która będzie odpowiadała za zarządzanie ruchem w naszej głównej sieci nazwana LAN.

Parametry maszyny nie muszą być duże – jeden rdzeń, 512MB ramu, partycja 10GB… Oczywiście możecie do tego wykorzystać maszynę fizyczną. Jednak nie miałem takiej pod ręką, więc bawię się na wirtualnych.
Adresacja na interfejsie WAN będzie pobierana przez DHCP, natomiast na LAN postawimy nasz własny serwer DHCP, który będzie działał w klasie 192.168.11.0/24. Tak samo dla początkowej konfiguracji ustawimy, aby nasze zapytania DNS były kierowane do routera głównego albo np. do Google. W późniejszych wpisach dowiecie się w jaki sposób zmienić ustawienie, aby nasz Windows Server był serwerem DNS i DHCP dla ułatwienia naszej pracy.
Poniżej znajdziecie kompletną konfigurację.

<script src="https://gist.github.com/dzejzipl/7e8023a7394f6fe7e8c9da06eaefd84f.js"></script>

Jak widzicie, pierwsza konfiguracja jest bardzo intuicyjna. Zamierzam poświęcić trochę więcej czasu na naukę tego systemu, bo taka wiedza może być bardzo przydatna.
Oczekujcie na kolejne wpisy związane z tym systemem!
