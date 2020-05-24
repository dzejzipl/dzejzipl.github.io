---
title: "[PL] Remote Desktop Connection Manager – przyjemna praca na RDP"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Remote Desktop Connection Manager – przyjemna praca na RDP](/assets/images/posts/remote-desktop-connection-manager-przyjemna-praca-na-rdp/top.jpg)Praca z RDP nie musi być trudna.

Pracując zdalnie na systemach Windows do każdego musimy się podłączyć. Jeden serwer – jedno okienko Remote Connection Manager. Każde takie okienko otwiera się na pełnym ekranie, zawsze trzeba wpisywać adres IP no i ogólnie mocna upierdliwość korzystania z tego narzędzia.

Długi czas temu oglądając sesję online któregoż z Polskich prelegentów zauważyłem, że używa nieznane mi wcześniej oprogramowanie do łączenia się z serwerami. Wylistowane serwery w grupie po lewej stronie, nie podaje danych do logowania, automatyczne skalowanie obrazu… I tak sobie pomyślałem – co to za magia?

Dlatego przedstawię wam dziś magię, którą ułatwiła mi życie kilkanaście miesięcy temu.

Magicznym oprogramowaniem okazał się Remote Desktop Connection Manager, którego każdy z nas może ściągnąć BEZPŁATNIE ze strony Microsoft: https://www.microsoft.com/en-us/download/details.aspx?id=44989

Instalacja jest bezproblemowa, zajmuje tylko chwilę i nie powinna narobić wam problemów.

Jeżeli odpalamy bazę po raz pierwszy to musimy utworzyć swój plik RDCM z grupami, w którym zapiszemy wszystkie dane do serwerów. Ja dla przykładu nazwę go LAB

![[PL] Remote Desktop Connection Manager – przyjemna praca na RDP](/assets/images/posts/remote-desktop-connection-manager-przyjemna-praca-na-rdp/01.png)

Dalej, możemy albo dodać swój serwer, albo utworzyć grupę. Ja dla testów utworzę najpierw grupę, a później pojedyńczy serwer w każdej grupie i pokażę wam jak to wygląda w praktyce:

![[PL] Remote Desktop Connection Manager – przyjemna praca na RDP](/assets/images/posts/remote-desktop-connection-manager-przyjemna-praca-na-rdp/02.png)

Jak możecie zobaczyć mam utworzone 3 grupy: Serwery, która jest grupą dynamiczną. W niej pokazują się wszystkie RDP, które mają w nazwie wyświetlanej „ws”. Druga grupa jest nazwana W10 – w niej mam swoje Windowsy 10, natomiast w kolejnej – WS2016, gdzie trzymam swoje Windows Servery.

Oczywiście – nie jest to produkcyjna grupa, tylko pokazana do testów. 😉

Teraz aby dodać taki serwer do grupy, klikamy na nią prawym przyciskiem > Add Server i wypełniamy następujące opcje:

![[PL] Remote Desktop Connection Manager – przyjemna praca na RDP](/assets/images/posts/remote-desktop-connection-manager-przyjemna-praca-na-rdp/03.png)

Z podstawowych rzeczy, które potrzebujecie wykonać, aby bezproblemowo korzystać z RDP to jest wszystko. Ja jednak pokażę wam kilka trików, które uprzyjemniły mi prace:

Dla głównej grupy LAB ustawiłem:

Remote Desktop Settings – pole Remote Desktop Size: Same as client area. Dlaczego tak? Ponieważ nawet jeżeli przeniosę RDCMa na inny ekran z inną rozdzielczością to sesja mi się dopasuje i wszystko będzie dopasowane.

![[PL] Remote Desktop Connection Manager – przyjemna praca na RDP](/assets/images/posts/remote-desktop-connection-manager-przyjemna-praca-na-rdp/04.png)

Local Resources – pole Remote Sounds: do not play
pole Windows key combos: On the remote computer
pole Redirect options: Clipboard, Drivers

W pierwszym polu wyłączam dzwięk z urządzenia zdalnego – uwierzcie mi, czasem człowiek może się przestraszyć jak jakiś error wyskoczy, a wy nie jesteście przygotowani, aby go usłyszeć. Drugie pole pozwala nam na przekierowanie kombinacji klawiszy na komputer zdalny, czyli np. ALT+TAB i tak dalej. A w trzecim polu zaznaczam, aby urządzenie zdalne miało dostęp do schowka jak i dysków lokalnych na hoście, na którym aktualnie pracuję. O tak, często mi to ratuje tyłek.

Dla pewności – ostatnią opcję możecie zaznaczyć tylko jeżeli wiecie, że będziecie z niej korzystać.

Fajną opcją jest także: Profile Managment, dzięki której stworzymy różne profile do logowania, w których możemy zapisać nawet i hasło, aby nie męczyć się z wpisywaniem. Np. tworzycie profil dla Administratora, Usera, wdrożeniowca itp. itd. a następnie przypisujecie go za pomocą Logon Credentials do odpowiedniej maszyny (NIE dla grupy).

UWAGA: zapisywanie swoich haseł – nie jest dobrą idea, pamiętajcie. Dlatego też polecam zapisać taki profil, ale bez hasła. W takim wypadku RDCM będzie nas prosił o wpisanie hasła.

![[PL] Remote Desktop Connection Manager – przyjemna praca na RDP](/assets/images/posts/remote-desktop-connection-manager-przyjemna-praca-na-rdp/05.png)

Jeżeli chodzi o te bardziej zaawasowane opcje to ja korzystam właśnie w taki sposób.

Może wy korzystacie z bardziej zaawansowanych opcji? Dajcie znać w komentarzu!