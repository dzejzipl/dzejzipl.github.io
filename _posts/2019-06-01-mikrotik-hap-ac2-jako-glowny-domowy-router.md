---
title: "[PL] Mikrotik hap ac2 jako główny domowy router"
categories:
    - Random
tags:
    - Mikrotik
    - konfiguracja
    - PL post
---
![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/MikrotikTOP.jpg)Post ten jest nową wersją wpisu o [podstawowej konfiguracji Mikrotika](https://piesik.me/2017/05/14/podstawowa-konfiguracja-mikrotika/). Więc jeżeli przychodzicie z tamtego posta, to łapcie ulepszoną werję.

W moje ręce wpadło nowe urządzenie, **Mikrotik hap ac2**, który ma posłużyć za domowy router o rozbudowanych funkcjach. Cena tego urządzenia patrząc na możliwości jest po prostu śmieszna, ponieważ udało mi się go kupić za około 280zł.

A co otrzymamy za te pieniądze?

5 portów LAN, każdy o przepustowości 1gbit oraz sieć WiFi 2,4GHz jak i 5GHz jak i jeden port USB, który na tą chwilę jest niewykorzystany przeze mnie.. Całą specyfikację możecie zobaczyć na [stronie producenta](https://mikrotik.com/product/hap_ac2).

Demonem szybkości w wykorzystaniach korporacyjnych on nie będzie, ale wszystkie urządzenia, które mam w domu spokojnie obsłuży, a na dodatkowe laby i inne zabawy mu tej mocy nie zabraknie, więc możecie spodziewać się luźno powiązanych z sobą wpisów. Zresztą już jeden poszedł online wcześniej – ten o statystykach, które są ważne, bo jednak warto mieć podląd na to ile łącza zużywamy w trakcie codziennego użytku.

Dosyć lania wody, przejdźmy do konfiguracji!

Pokrótce tylko napisze, że nie uważam się za specjalistę od tych urządzeń. Jestem osobą, która się uczy metodą prób i błędów. Drogi czytelniku, gdybyś znalazł jakiegoś buga, koniecznie daj znać w komentarzu.

Założenia tego wpisu są następujące:

- Wstępna konfiguracja
- Konfiguracja dostępu do Internetu
- Konfiguracja LANu + serwera DHCP
- Port 1 będzie portem gdzie będzie dostarczany Internet bezpośrednio od mojego providera UPC, czyli ichniejszy ConnectBox będzie działał tylko w trybie modemu, reszta portów będzie wspólna dla wszystkich urządzeń w domu
- Konfiguracja firewalla
- Konfiguracja Wi-Fi

Wszystko się rozpoczyna od pobrania programu Winbox ze strony producenta. Winbox jest programem do zarządzania urządzeniami Mikrotik w trybie GUI. Bo ja wiecie, albo i nie wiecie możecie tymi urządzeniami zarządzać z poziomu telnetu, SSH albo i GUI. Podłączamy urządzenie do prądu, podpinamy się do niego bezpośrednio kablem LAN (aczkolwiek wybierzcie inny port niżeli ten, na którym będzie sieć od waszego providera) i uruchomcie program. Waszym oczom powinien się pojawić taki widok:

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/1.png)

Łączymy się do naszego nowego routera z loginem **admin** oraz bez hasła. W pierwszym oknie pojawia się pytanie – co chcemy zrobić z wgraną konfiguracją. Usunąć, co znaczy tyle, że musimy wszystko sami skonfigurować czy też zostawić przedefiniowane ustawienia. Ja na potrzeby tego wpisu wszystkie usuwam.

Ważne jest to, aby nie pracować na domyślnym użytkowniku. Przejdźmy więc do menu ***System*** > ***Users*** > dodajmy naszego użytkownika na ***Full Permission***, wylogujmy się z Winboxa, zalogujmy jeszcze raz, ale na nowym użytkowniku, a tego domyślnego usuniemy. Tak dla bezpieczeństwa.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/2.png)

Kolejnym krokiem jest dla mnie nazwanie i zarządzanie Interfejsami. Chciałbym wiedzieć co jest podłączone do danego interfejsu, bo jednak ETH4 nic mi nie mówi. Dlatego też rozpocznę od nazwania jak i ustawienia poprawnych komentarzy. Robimy to poprzez wejście do ***Interfaces***.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/3.png)

Po zmianie wygląda to trochę ładniej, prawda?

Kolejną rzeczą, którą chcę wykonać to mieć możliwość widoczności wszystkich urządzeń w jednej sieci, czyli zrobię Bridge ze wszystkich portów, przechodząc do ***Bridge*** > ***add new*** i tworzymy nowy bridge:

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/4.png)

Później dodajemy odpowiednie porty poprzez wejście w ***Bridge*** > ***Ports*** > ***add*** i przypisanie go odpowiedniego Bridge. Czynność tą powtarzamy dla każdego portu, który chcemy używać w naszej sieci.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/5.png)

Jeżeli już mamy ustawione te kilka podstawowych rzeczy to rozpocznijmy od stworzenia adresacji i ustawienia lokalnego serwera DHCP oraz włączenia klienta DHCP dla mojego providera.

Rozpoczynam od tej ostatniej rzeczy. Wchodzę w zakładkę ***IP*** > ***DHCP client*** i rozpoczynam tworzenie nowego klienta. Zostawiam domyślnie ustawione opcje.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/6.png)

I już po chwili widzę, że otrzymałem adres IP dla mojego klienta DHCP.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/7.png)

DNSów nie będziemy ustawiać, ponieważ UPC dostarcza swoje serwery DNS, które są w zupełności wystarczające. Może później postawię swój serwer DNS w domu i wtedy się zainteresuję, aby to ustawić.

Przystąpimy teraz do konfiguracji DHCP w naszej sieci lokalnej. Pierwsze co musimy zrobić, to stworzenie adresu, który będzie miał nasz Mikrotik w sieci.

Z lewej strony wybieramy ***IP*** > ***Addresses*** i dodajemy nowy adres. Ja w domowej sieci wykorzystam klasę **192.168.35.0/24**, z czego adres **192.168.35.254** przeznaczę na Mikrotika i przypisałem go do nowo utworzonego bridge.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/8.png)

Jeżeli już utworzyliśmy adres naszego urządzenia, skonfigurujmy serwer DHCP, aby rozdawał adresy hostom. Założenie jest takie, że wykorzystuję pulę **192.168.35.0/24**, z czego do wykorzystania będą tylko adresy ***192.168.35.30*** – ***192.168.35.250***, a pozostałe będą przeznaczone na inne cele.

Przechodzimy więc do ***IP*** > ***DHCP Server*** i klikamy na **DHCP Setup**

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/9.png)

- Wybieramy utworzony Bridge
- Wybieramy adresację, którą stworzyliśmy w poprzednim kroku
- Wybieramy adres routera
- Ustawiamy zakres adresów: ***192.168.35.30*** – ***192.168.35.250***
- Ustawiamy serwery DNS. Informacja dla was: ja korzystam z serwerów DNS od UPC, więc zostawiam domyślne
- Ustawiamy czas dzierżawy DNS, polecam zmienić na 24:00:00,co będzie równe 24 godzinom.

Teraz po restarcie urządzenia i ponownym podłączeniu się powinniśmy otrzymać IP z nowo utworzonej sieci:

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/10.png)

Mamy skonfigurowany DHCP, teraz wypadało by skonfigurować NAT, aby mieć dostęp do Internetu. Czym jest NAT przeczytacie np. [tutaj](https://pl.wikipedia.org/wiki/Network_Address_Translation).

Przechodzimy do ***IP*** > ***Firewall*** > ***NAT*** i rozpoczynamy dodawanie nowego NATu

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/11.png)

- Zakładka General, pole ***Chain*** wybieramy **scrnat**
- Zakładka General, pole ***Src***. Address wpisujemy swoją adresację, czyli **192.168.35.0/24**
- Zakładka Action, pole ***Action*** wybieramy **masquearde**

Po zapisaniu tych ustawień na naszym komputerze powinien pojawić się dostęp do Internetu.

Po tym jak już mamy Internet zaaktualizujmy urządzenie do najnowszej wersji. Przechodzimy do ***System*** > ***Packages*** i klikamy na „**Check for Updates**” i jeżeli pojawią się jakieś aktualizacje, koniecznie je zainstalujmy.

Teraz zrobimy backup tego wszystkiego co zrobiliśmy wcześniej, przechodząc do ***Files*** > ****Backup**** i tworząc backup. Możemy go pobrać do siebie na komputer, po prostu przeciągając do go folderu.

Jeżeli już zrobiliśmy ten backup, to przejrzyjcie koniecznie tej strony: [https://wiki.mikrotik.com/wiki/Basic_universal_firewall_script](https://wiki.mikrotik.com/wiki/Basic_universal_firewall_script) na której znajdziecie wszystkie informacje, w jaki sposób zabezpieczyć waszą sieć z zewnątrz. **KONIECZNIE TO ZRÓBCIE!**

A co z siecią Wi-Fi ? Przecież ten model posiada wbudowane 2,4GHz jak i 5GHz więc skonfigurujmy również i te opcje. Pierwsze co musimy zrobić to stworzyć „Security profile” z menu ***Wireless*** > ***Security Profiles***. W polu czwartym wpisujemy hasło, w polu piątym wybieramy poprawne ustawienia.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/12.png)

Teraz musimy zobaczyć, czy nasze dwa interfejsy są dodane do bridge. Jak to zrobić, pisałem wcześniej. Po dodaniu interfejsów do bridge, nalezy przypisać stworzony profil do naszych kart wifi.

Aby to zrobić przechodzimy do ***Wireless*** > ***Wifi Interfaces*** > nasza karta wifi, klikamy na przycisk: Advanced mode i konfigurujemy wszystkie ustawienia zgodnie z naszymi potrzebami.

![Mikrotik hap ac2 jako główny domowy router]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-hap-ac2-jako-glowny-domowy-router/13.png)

To samo powtarzamy dla Wifi 5,4GHz.

Powodzenia!
