---
title: "[PL] Apple macOS Server – zaczynamy!"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/top.jpg)Apple macOS Server – zaczynamy!

Cześć!

Od dłuzszego czasu planowałem ogarnąć umiejętność pracy z macOS Server, czyli takim Active Directory dla systemów z rodziny Appla. Z racji tego, że w końcu nadarzyła się do tego okazja, to chciałbym przedstawić Ci drogi czytelniku, co dokładnie będę robił z tą aplikacją i jak to zrobię….

Założenia, które chciałbym wprowadzić:

Połączenie albo z lokalnym AD albo uwaga.. z Azure AD! 😉
Instalacja z sieci
Foldery domowe
Konfiguracja maila / kontaktów
Oraz inne funkcje, które uda mi się w międzyczasie ogarnąć.
Wiem, że nie jest to tak profesjonalne środowisko jak JAMF… Ale skoro mogę wykorzystać macOS Server na początek, to dlaczego by tego nie zrobić?

Kontynuując, na początek dowiedzmy się co należy zrobić, aby dokonać pierwszej konfiguracji.

Pierwsze co musimy zrobić to zakupić program z tego linku, a następnie zainstalować i skonfigurować swoją kartę sieciową, aby miała statyczną adresację.

Po poprawnym zainstalowaniu w Launchpad pojawi nam się nowa ikona:

![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/01.png)

Po uruchomieniu zobaczymy kreator konfiguracji macOS Server:

![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/02.png)

Akceptujemy regulamin, logujemy się na swoje konto Administratora i czekamy chwilę na zakończenie automatycznej konfiguracji.

Po poprawnym zainstalowaniu program otworzy się automatycznie i zobaczymy wstępną konfigurację naszego serwera. U mnie wygląda ona następująco:

![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/03.png)

Pierwszym krokiem, który należy wykonać jest zmiana nazwy naszego serwera na bardziej przyjazną – ja wybieram nazwę: macoss

![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/04.png)

Potem ustawię w jaki sposób użytkownicy będą mieli się łączyć do mojego urządzenia i jak będzie ono dostępne. Aby dojść do tego menu, z strony startowej wybieramy Edit host name, next i wybieramy daną opcję.

![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/05.png)

W moim przypadku wybiorę opcję Internet (chociaż niewykluczone, że później to zmienię na „VPN”.

Wstępna konfiguracja wygląda tak:

![[PL] Apple macOS Server – zaczynamy!](/assets/images/posts/apple-macos-server-zaczynamy/06.png)

I na początek nam to wystarczy.

Mam nadzieję, że uda mi się wrócić do tego tematu w jak najbliższym czasie!

