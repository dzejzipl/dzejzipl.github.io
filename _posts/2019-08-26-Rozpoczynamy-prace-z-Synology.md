---
title: "[PL] Rozpoczynamy pracę z Synology"
categories:
    - Synology
tags:
    - Synology
    - Wprowadzenie
    - PL post
---
![„Rozpoczynamy pracę z Synology"](/assets/images/top_images/SynologyTOP.jpg)Jakiś czas temu wpadł w moje rączki jeden z najnowszych produktów firmy Synology, model **DS620 Slim**, o którym chciałbym wam dziś opowiedzieć. O moich planach co do tego urządzenia i co, wy - drodzy czytelnicy będziecie mieli z tej serii postów. Bo to tak właściwie będzie seria artykułów.

W pierwszym wpisie chciałbym poruszyć w jaki sposób rozpocząć pracę z urządzeniami tej marki.

Pokrótce chciałbym wam jednak opowiedzieć o bohaterze dzisiejszego tekstu.

## DS620 Slim

Może zacznę inaczej - moje pierwsze wypakowanie tego urządzenia to było duże zdziwienie. Dlaczego to takie małe i czy ja u licha posiadam dyski 2,5', które mogę zamontować do tego NASa?

Wcześniejszy testowany przeze mnie produkt DS918+ był pełnowymiarowy, czyli posiadał możliwość zamontowania dysków 2,5' jak i 3,5', tutaj natomiast możemy montować tylko dyski o mniejszej średnicy, co jak by nie patrzeć z początku mnie zatrzymało i musiałem zajrzeć do swoich archiwów sprzętowych w celu wygrzebania działających dysków, ale się udało.

Co ważne, mamy do użycia **6** zatok, w któych możemy zamontować dyski o maksymalnej wspólnej pojemności - **30TB**. Czy to dużo? Niezbyt, ale pamiętajmy, że jest to sprzęt domowy, a nie korporacyjny.

Co zostało przeniesienione z segmentu korporacjnego to możliwość wymiany dysków bez wyłączania urządzenia - czyli Hot swap. Musimy pamiętać także o tym, że wszystkich dysków od razu nie wymienimy, a jest to zależne do typu RAIDu, który wybierzemy.

A jest w czym wybierać.

- RAID 0
- RAID 1
- RAID 5
- Basic
- JBOD
- Synology Hybrid RAID

W moim rozwiąziu skupimy się nad użyciem Synology Hybrid RAID. Czym jest **SHR**?

> (..) to automatyczny system zarządzania macierzą RAID, który pozwala uprościć zarządzanie pamięcią masową i korzystać z zalet macierzy RAID przez początkujących użytkowników bez wiedzy o dostępnych typach macierzy RAID.
Rozwiązanie SHR pozwala łączyć dyski o różnych pojemnościach w celu utworzenia wolumenu o zoptymalizowanej pojemności i wydajności, ograniczając marnowanie miejsca dysków i zapewniając większą elastyczność. Jeżeli macierz składa się z odpowiedniej liczby dysków, system SHR zapewnia nadmiarowość danych na poziomie 1 lub 2 dysków, co oznacza, że awaria jednego lub dwóch dysków w wolumenie nie powoduje utraty danych.

Brzmi całkiem przyjmenie, prawda? Wkładam wszystkie dyski jakie obecnie posiadam, a sam NAS decyduje o moim bezpieczeństwie. Wybiorę ten wariant.

Aby podłączyć nasze urządzenie do sieci, mamy dostępne dwa porty LAN o przepustowości każdy do 1Gb/s, co zadowoli nawet najbardziej wymagających użytkowników domowych. Ja to skonfiguruję na tę chwilę z jednym portem. Później podłączę do nowego switcha, to już będzie korzystało z dwóch portów RJ-45. Oprócz tego, mamy dostępne dwa złącza USB 3.0, pod które możemy podłączyć dodatkowe dyski albo inne peryferia.

W podstawowej wersji urządzenie posiada tylko 2GB pamięci RAM, które można rozbudować do 6GB. Plotki na Internecie mówią, że ludzie rozbudowali do 8GB. Czy to prawda? Cóż, przekonamy się za jakiś czas. Obecnie dołożyłem nową kość 4GB, co daje mi łącznie 6GB a to powinno wystarczyć to na długi czas.

To przejdźmy teraz do tej lepszej części, czyli na czym się skupimy w dzisiejszym poście.

## Wstępna konfiguracja urządzenia Synology DS620 Slim

Po zainstalowaniu dysku(ów) oraz podłączeniu urządzenia do sieci LAN oraz elektrycznej należy rozpocząć konfigurację, która jest bajecznie prosta.

Jeżeli nie znamy adresu IP naszego urządzenia możemy wejść na stronę [find.synology.com](https://find.synology.com), a ta w magiczny sposób pokaże nam urządzenia Synology w naszej sieci.

Zresztą, zobaczcie sami jak to wygląda na screenie:

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/01.png)

Szybki klik na Connect, i rozpoczynmamy konfigurację, która jest banalnie prosta.

1. W pierwszym kroku musimy zainstalować system operacyjny **DSM** w naszym urządzeniu. Albo instalujemy manualnie z sieci, albo automatycznie. Ja wybieram opcję automatyczną. Przed instalacją pojawi się monit, że wszystkie dane, które są zapisane na naszych dyskach zostaną usunięte.

2. W drugim kroku musimy utworzyć konto Administratora, który będzie konfigurował urządzenie oraz ustawić odpowiednią nazwę urządzenia.

3. W kroku trzecim natomiast ustawiamy, czy nasze urządzenie ma używać **QuickConnect**. Dla osób, które nie wiedzą czym jest ta funkcja to w skrócie powiem, że umożliwa dostęp do naszego urządzenia z sieci zewnętrznej bez przekierowywania portów. A tak, ustawię sobie taką opcję. Zawsze się przyda jak pojadę na urlop, albo nie będę miał dostępu do VPNa.

4. I... To wszystko. Całe nasze urządzenie jest już skonfigurowane. Nie pozostało nam nic innego jak rozpocząć coś więcej niżeli wstępną konfigurację.

## Pulpit naszego urządzenia

Tak właściwie logując się po raz pierwszy mozna mieć wrażenie, że skądś już to znamy. Są ikony, jest menu, jest menu kontekstowe. Tak właśnie wygląda pulpit tego urządzenia - jak dla mnie jest bardzo intuicyjny na sam początek.

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/02.png)

Pierwsze co należy zrobić to zainstalować dostępne aktualizacje z Package Center.

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/03.png)

Po drugie, to wypada skonfigurować automatyczne aktualizacje, aby uchronić się przed znanymi zagrożeniami. Przechodzimy do **Control Panel** > **Update & Restore** > **Update Settings** i wybieramy w jakie dni mają być automatycznie instalowane **LUB** ma wyskakiwać powiadomienie, że jest nowa aktualizacja do zainstalowania.

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/04.png)

Ja wybrałem opcję codziennego sprawdzania i instalowania krótko po północy.

Jeżeli już mamy ustawione aktualizacje, wypadało by zrobić pierwszego share'a, gdzie wrzucimy swoje pliki.

Rozpocznynamy od przejścia z menu głównego > **Storage Manager**

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/05.png)

Przechodzimy do **Volume**, klikamy na **Create** i dla naszego domowego zastosowania, gdzie wszystko ma być trzymane w jednym **SHR**, wybieram opcję **Quick**

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/06.png)

A z racji tego, że ten NAS posiada tylko 6 zatok na dyski, a zależy mi trochę na pojemności to wybiorę SHR 1, który pozwoli na awarię jednego dysku. Jeżeli byśmy wybrali SHR 2, to "bezpieczne" są te dwa dyski, które mogą się w jednym momencie zepsuć.

Wybieramy nasze dyski, które chcemy wykorzystać i przechodzimy do wyboru systemu plików. Tak jak kreator zaleca, wybieram **Btrfs**.

Po zakończeniu tego kreatora mogę przejść do utworzenia pierwszego share'a.

Idziemy do **Control Panel** > **Shared Folder** i rozpoczynamy tworzenie nowego folderu za pomocą przycisku **Create**

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/07.png)

Utworzymy sobie pierwszy folder o nazwie Rozrywka oraz włączymy **kosz**, który będzie dostępny tylko dla grupy Administratorów.

Z racji tego, że ten folder będzie publiczny, nie mamy potrzeby go szyfrować, jak i będziemy sprawdzać integralności danych jak i włączać *quoty*, czyli kto i ile może wrzucić danych.

Klikamy Apply i folder został stworzony.

Teraz dodam uprawnienia dla użytkownika, któremu stworzyłem konto na samym początku, natomiast później stworzymy dedykowanego użytkownika(ów) do codziennej pracy.

Nie wiem czy pamiętacie, ale jakiś czas temu szalał wirus, który powodował całkiem spore spustoszenie dzięki włączonemu protokołowi SMBv1. Microsoft wtedy wyłączył dokładnie tę wersję protokołu w systemie Windows, dlatego też my ją wyłączymy w naszym urządzeniu.

Przechodzimy do **Control Panel** > **File Services** > SMB > **Advanced Settings** i włączamy minimalną wersję protokołu SMB v2, a jako maksymalną wersję SMBv3.

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/08.png)

Jeżeli już ustawiliśmy protokoły, dobrze by było stworzyć użytkownika, który ma trochę mniejsze uprawnienia niż Administrator, ale będzie mógł zapisywać / odczytywać foldery.

Przechodzimy do **Control Panel** > **User** > **Create** i uzupełniamy odpowiednie dane. W kolejnym kroku zamiast dodawać go do grupy Administratorów, zostawmy go w grupie *Users*. Jak widzimy, domyślnie nie musimy nadać uprawnienia do odpowiednich folderów, ponieważ stosujemy uprawnienia dziedzicone. Dla przykładu, gdybyśmy na folder **Rozrywka** ustawili, że grupa *User* nie ma mieć dostępu do tego folderu, użytkownik miałby teraz *No access*.

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/09.png)

W kolejnych krokach możemy mu nadać dostęp do panelu webowego Synology, FTP, SMB oraz kilka inncyh, obecnie nie potrzebnych nam rzeczy.

Gotowi do podłączenia dysku w systemie Windows? Zobaczcie jak ja to zrobiłem na poniższym screenie:

![„Rozpoczynamy pracę z Synology"](/assets/images/posts/Rozpoczynamy-prace-z-Synology/10.png)

### A teraz pytanie do Was

Dlaczego użyłem z loginem i hasłem użytkownika, zamiast spróbować wlączyć konto Gościa? Tak dla bezpieczeństwa. Po prostu - krótki trik, a będzie większe bezpieczeństwo Twoich danych.

Krótko, ale na temat.

Uważam, że tym wpisem wyczerpałem pierwszą, wstępną konfigurację naszego urządzenia.

W kolejnym wpisie chciałbym pokazać wam, w jaki sposób użyć tak skonfigurowane urządzenie do postawienia "małej" firmy. Czyli namiastka Active Directory.

Kolejne wpisy będą się skupiać bardziej na zastosowaniu biznesowym, ale postaram się także wam pokazać jak możemy go wykorzystać w naszym domu.
