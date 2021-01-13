---
title: "[PL] Microsoft Hyper-V Server 2016 – instalacja oraz konfiguracja"
categories:
    - Krótko
    - Windows Server
tags:
    - PL Post
---
![[PL] Microsoft Hyper-V Server 2016 – instalacja oraz konfiguracja
](/assets/images/posts/microsoft-hyper-v-server-2016-instalacja-oraz-konfiguracja/top.jpg)Krótko i na temat w sprawie Hyper-V Server 2016!

Cześć.

Pod moim biurkiem stoi maszyna z Phenom X4 965, 16GB ramu i dyskiem SSD 120GB, czyli dosyć wydajna konfiguracja, która szkoda, aby się marnowała. Dlatego też postanowiłem dla nauki wdrożyć na niej Windows Hyper-V Server w wersji najnowszej, czyli 2016. Dysk SSD 120GB będzie współdzielony z systemem Matką jak i z jednym hostem – Windows 10 w wersji Enterprise do testów wdrożeniowych. W razie potrzeby dołożę dyski 2×500/ 1TB w RAID 1 na kolejne 2-3 maszyny. I tak dalej, i tak dalej. Miejsca mam na 5 dysków. Dość ambitny plan, zobaczymy co z niego wyjdzie.

Na początek może czym jest Hyper-V Server? Jest to bezpłatna edycja Windowsa Server, która GUI posiada jedynie podczas instalacji systemu. A przebiega ona standardowo – wybieramy język oraz ustawienia lokalizacji, sposób partycjonowania i to wszystko. Dopiero po pierwszym restarcie zobaczymy okienka, które nie przypominają typowego GUI z Windows Server Desktop Experience. Dlaczego? Ponieważ z poziomu fizycznego podłączenia do takiego serwera mamy dostęp tylko do kilku opcji:

* Ustawienie przynależność do domeny / grupy
* Nazwy komputera
* Lokalnych administratorów
* Konfigurację zdalnego dostępu
* Ustawienia Windows Update
* Konfigurację pulpitu zdalnego
* Ustawienia sieci oraz daty i godziny
* Oraz opcje wylogowania użytkownika / restartu / wyłączenia serwera oraz wyjścia do zwykłej linii komend.

Jako, że w moim przypadku to jest maszyna, która nie będzie podłączona do domeny (a będzie jedynie podłączona do Azure Server Managment Tools) to zmienię tylko jej nazwę wybierając z Server Configuration opcje drugą i wpisując nową nazwę, akceptując przyciskiem Enter i nie restartując jeszcze komputera, ponieważ chcę ustawić inne opcje.

Dodałem lokalnego Administratora, co by nie korzystać z wbudowanego konta Admina poprzez wybranie z głównego menu opcji pod numerem 3, wpisując nazwę nowego użytkownika oraz hasło.

Kolejną opcją jest skonfgurowanie opcji Windows Update > z menu wybieramy 5 i w moim przypadku wybrałem opcję > Select (A)utomatic, dzięki czemu system Windows codziennie o 3 rano będzie sprawdzał status aktualizacji. Nie jest to maszyna produkcyjna dlatego też nie zrobi mi różnicy  jeżeli się zrestartuje w celu zainstalowania takowych aktualizacji.

Dobrą opcją jest włączenie opcji pod numerem 7, czyli Remote Desktop. Dzięki temu będziemy mogli się łączyć nie tylko za pomocą PowerShella, ale również Remote Desktop pod numer IP naszej maszyny. Tutaj również wybrałem opcję Enabled, ale z zastrzeżeniem, że wpuszczam użytkowników z „Network Level Authentication (more secure)”.

Ostatnimi opcjami, które postanowiłem zmienić były ustawienia sieci Ethernet. Domyślnie jest włączone DHCP dzięki czemu jesteśmy w stanie znaleźć dosyć łatwo taki komputer. W moim przypadku chciałem, aby był on dostępny pod statycznym adresem IP. W tym celu wybieramy z menu: 8) Network Settings, szukamy swoją aktywną kartę sieciową (jeżeli więcej niż jedna), wybieramy jej numer, po raz kolejny wybieramy z menu: Set Network Adapter Address, wpisujemy całą konfigurację, którą chcemy uzyskać i zapisujemy klawiszem Enter. Taką samą operację przeprowadzamy w przypadku 2) Set DNS Servers i powracamy do głównego menu.

Z niego możemy już wybrać opcję Restart Server i spróbować się podłączyć do serwera za pomocą Powershell..

Wpisujemy Enter-PsSession adresIP i otrzymujemy znany już nam komunikat, który opisywałem we wcześniejszym wpisie…

Azure Nano Server | Enter-PSSession – Cannot connect

Czynimy krok, który jest opisany w powyższym wpisie…

I wszystko działa! Spróbujmy wydać polecenie systeminfo, w moim wypadku otrzymałem informacje zwrotne:

[192.168.10.20]: PS C:\Users\Kuba\Documents> systeminfo

Host Name: HYPERV2016
OS Name: Microsoft Hyper-V Server 2016
OS Version: 10.0.14393 N/A Build 14393
OS Manufacturer: Microsoft Corporation
OS Configuration: Standalone Server
OS Build Type: Multiprocessor Free
Registered Owner: Windows User

No dobrze, a co z całą resztą? W jaki sposób zarządzać całym Hyper-V? Jak tworzyć maszyny? Jak tworzyć wirtualne przełączniki? Cokolwiek? Wszystkie kroki już robimy będąc podłączonym maszyny właśnie przez Enter-PsSession. W PowerShellu tworzymy switche, maszyny, zarządzamy przypisanymi zasobami i procesorami. Postaram się jak najszybciej opisać w jaki sposób to robimy i podrzucić kilka przydatnych wpisów na ten temat.

Ps. Gdybyście przypadkiem czasem wyślij z menu Server Configuration do linii komend za pomocą opcji 14, to można je uruchomić za pomocą polecenia: sconfig.cmd

Stay tunned!