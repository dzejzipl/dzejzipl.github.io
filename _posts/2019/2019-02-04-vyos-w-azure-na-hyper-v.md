---
title: "[PL] vyOS w Azure na Hyper-V"
categories:
    - Hyper-V
    - Azure
tags:
    - Azure
    - Hyper-V
    - Nested virtualization
    - PL post
---
![vyOS w Azure na Hyper-V]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/vyosTOP.jpg)[Wczoraj stworzyłem posta](https://www.piesik.me/2019/02/03/hyper-v-na-azure-vm-polaczenie-z-internetem/) w jaki sposób mogę skonfigurować NAT w taki sposób, aby mieć Internet na maszynach zainstalowanych na Hyper-V na mojej maszynie w Azure.

Maszynocepcja? Być może.

Sposób miał jedną dużą wadę – każda maszyna musiała mieć skonfigurowany manualnie adres IP. Nie mam na to czasu. Po prostu nie mam. Maszyny mają pobierać adresację za pomocą DHCP, a nie chciałem konfigurować usług Routera na Windows, bo nic dobrego z tego by nie wyszło.

TL;DR jest takie, że wykorzystałem nowego switcha, stworzyłem wirtualną maszynę z vyOS i na niej skonfigurowałem DHCP na kolejnym nowym switchu.

Switchocepcja? Definitywnie, ale dzięki temu moja praca jest obecnie łatwiejsza. Jeżeli ktoś ma trochę inny pomysł, z miłą chęcią poczytam.

Jak już wcześniej napisałem, wykorzystamy do tego system vyOS oraz wcześniejszy post. Konfigurację vyOS na potrzeby labowania już opisywałem i całość możecie przeczytać tutaj, polecam to zrobić, bo z tej konfiguracji będę korzystał

1. Rozpoczynamy od stworzenia konfiguracji, która jest opisana w wcześniejszym wpisie.
2. Tworzymy kolejny wirtualny switch, który będzie miał włączone DHCP z vyOS
3. Następnie stawiamy wirtualną maszynę vyOS z dwoma kartami sieciowymi – pierwsza to wirtualny switch, który postawiliśmy w poprzednim poście, druga będzie podłączona do switcha, który utworzyliśmy chwilę temu
4. Instalujemy vyOS zgodnie z konfiguracją [w tym poście](https://www.piesik.me/2018/04/05/wstepna-konfiguracja-vyos-na-potrzeby-labowania/)
5. Zmieniamy konfigurację, która jest opisana w tym punkcie: Konfiguracja interfejsu WAN na następującą:
    1. **set interfaces ethernet eth1 address *192.168.0.X/24***
    2. **set system gateway-address *192.168.0.1***
    3. **set system name-server *8.8.8.8***
6. W miejsce adresacji z kursywą wpisujecie swoje adresy.
I to wszystko.

W momencie przypisania switcha, który jest jako drugi w vyOS na wirtualnych maszynach będziemy mieli Internet bez potrzeby manualnej konfiguracji.
