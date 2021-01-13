---
title: "[PL] Synology NAS - Virtual Machine Manager"
categories:
    - Synology
tags:
    - Synology
    - VMM
    - PL post
---
!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/top_images/SynologyTOP.jpg)Wirtualizacja jest bardzo przydatna w wielu zastosowaniach, dlaczego wiec by jej nie wykorzystać na Synology NAS za pomocą Virtual Machine Manager?

O zaletach wirtualizacji człowiek nie musi się zbytnio rozpisywać. Dzięki niej mamy możliwość odpalania innych maszyn na maszynie, która jest nazywana "hostem". Wirtualizacjocepcja? Być może.

Jeżeli chcecie się więcej dowiedzieć jak to wszystko wygląda w teorii zapraszam na stronę [Wikipedi](https://pl.wikipedia.org/wiki/Wirtualizacja), gdzie wszystko jest bardzo dobrze opisane.

W swoim domowym labie używam Hyper-V jako hypervisora, natomiast chciałbym dziś wspomnieć o istotnej funkcji, którą posiada spora część NASów firmy Synology, czyli obsługa Virtual Machine Manager.

Jest to dodatek, który jak inne ściągamy ze sklepu, instalujemy z zależnością (używany do replikacji) a następnie dokonujemy wstępnej konfiguracji, która jest bajecznie prosta. Zobaczcie na poszczególne kroki.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/01.png)

Jedyną rzeczą, którą musicie wybrać to miejsce, gdzie będą składowane nasze maszyny:

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/02.png)

Po zakończeniu kreatora naszym oczom pojawi się następujący widok:

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/03.png)

Jak widzicie, mamy dodanego jednego hosta, zero maszyn jak i jedną przestrzeń dyskową. Przechodząc przez poszczególne zakładki znajdziemy informacje o:

* Maszynach wirtualnych na naszym urządzeniu (lub urządzeniach)
* Budowanie klastra z użyciem innych NASów Synology w naszej sieci
* Zarządzanie przestrzenią dyskową
* Zarządzanie siecią i wirtualnymi switchami
* Zarządzanie repozytorium obrazów instalacyjnych, dysków oraz DSM
* Migawki dla naszych maszyn
* Ustawienia, logi, oraz licencjonowanie

Co do ostatniego ustawienia - ja się skupię na darmowej licencji, która pozwala nam na wirtualizowanie maksymalnie czterech maszyn maszyny. Może kiedyś w moje rączki wpadnie coś lepszego to potestuję i dam znać bardzo znaczące są różnice w porównaniu do darmowej wersji.

Więcej o licencjach możecie przeczytać pod tym [linkiem](https://www.synology.com/en-global/products/VMMPro_License_Pack)

Teoria teoria, ale dobrze by było rozpocząć pracę na żywym przykładzie, dlatego chciałbym pokazać wam, w jaki sposób stworzyć maszynę z Windows 10 na moim DS620Slim.

### Rozpoczynamy od przejścia do zakładki **Virtual Machine** oraz kliknięciu przycisku **Create**

Wybieramy docelowy system operacyjny, dla mnie to będzie Microsoft Windows i przechodzimy do kolejnego etapu.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/04.png)

W tym miejscu wybieramy dostępne miejsce, gdzie zostaną zapisane pliki. Jako, że mam tylko jedno urządzenie, które nie pracuje w klastrze to wybieram właśnie tego NASa.

Na trzecim etapie musimy skonfigurować nazwę maszyny, ilość przypisanych procesorów, pamięci RAM oraz typ emulowania karty graficznej.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/05.png)

Kolejny etap to praca z dyskami, które ma mieć przypięte maszyna. Ja chcę, aby był dostępny dla niej nowy wirtualny dysk o pojemności 127GB.

Później przypisujemy dostępne adaptery sieciowe, ja wykorzystam domyślny i przechodzimy do kolejnego kroku, gdzie wybieramy plik ISO z systemem Widowss oraz ściągamy i wybieramy **VMM Guest Tool**. ustawiamy również, czy chcemy, aby maszyna była automatycznie włączana na starcie hosta czy chcemy ją uruchamiać manualnie, jak i też ustawiamy wstępne opcje językowe.

Co ważne, pamiętajcie proszę o tych **VMM Guest Tool**, ponieważ jak jest napisane na stronie Supportu oferują one:
> This tool improves the compatibility of Windows virtual machines running on Synology NAS. It includes VirtIO drivers required for Windows and Synology Guest Agent, optimizing snapshots and other functions of virtual machines. [Źródło](https://www.synology.com/pl-pl/releaseNote/WinVirtioDriver)

Na samym końcu wybieramy użytkowników / grupy, które mają mieć możliwość włączania / wyłączania oraz restartowania maszyny, którą właśnie tworzymy.

Po zakończenia kreatora, naszym oczom pojawi się uaktualniona zakładka z nowo utworzoną maszyną na liście:

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/06.png)

Jeżeli chcemy się połączyć maszyną, klikamy na przycisk **Connect** (1), natomiast tak jak widzicie, u mnie ona już jest w trybie "Running", czyli uruchomiona, dlatego nie widać przycisku Start. Pod przyciskiem Shutdown znajdziemy różne opcje, np. restartu maszyny.

Po uruchomieniu oraz połączeniu naszym oczom pojawi się instalator Windowsa.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/07.png)

Jak widzicie, na screenie z lewej strony rozwinąłem menu, pod którym mamy dostępne klawisze, np. CTRL + ALT + DEL, które mają zostać przekazane na naszą maszynę.

Mamy już stworzoną maszynę wirtualną, która nam działa, ale warto było by powiedzieć słów kilka o pozostałych opcjach, które są przydatne podczas pracy z Virtual Machine Manager.

### Zaczniemy od zakładki "**Network**"

Wyróżniamy dwa typy switchy w DSM:

* External, czyli takie, które mają dostęp do naszej domowej sieci
* Private, czyli takie, które nie mają dostępu do naszej domowej sieci.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/08.png)

### W zakładce "**Image**" zarządzamy naszym repozytorium plików z różnego rodzaju obrazami systemów

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/09.png)

W miejscu tym możemy dodać obrazy ISO, obrazy dysków oraz obrazy systemu Synology w celach testowych.

Rozwiązanie to sprawdzi się gdy chcemy mieć uporządkowaną listę obrazów oraz pozwoli nam to również na wybór odpowiedniego ISO podczas tworzenia maszyny.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/10.png)

### Zakladka: Protection pozwala nam na konfigurowanie automatycznych migawek

Dzięki tej opcji jesteśmy w stanie robić automatyczne zrzuty całego naszego systemu i łatwo je przywracać w razie awarii. Niestety, wersja BASIC mojej licencji jest bardzo mocno ograniczona i nie ma nawet możliwości ustawienia po ilu dniach stare migawki mają być usuwane. Maksymalna ilość migawek dla wersji BASIC to 32.

!["[PL] Synology NAS - Virtual Machine Manager"](/assets/images/posts/Synology-Virtual-Machine-Manager/11.png)

Jak widzicie, **VMM** na domowe zastosowania w zupełności wystarczy, jednakże firmy, które mają więcej niż jedno urządzenie niech wybiorą wersję PRO, która da im choćby możliwość live migracji, replikacji danych, tworzenia klastra wysokiej dostępności i kilku innych funkcji.

A jeżeli ktoś w domowych zastosowaniach posiada mocniejszego NASa niżeli ten mój DS620Slim i chce wykorzystywac go jako wirtualizator - także powinien zainwestować w wersję PRO choćby ze względu na obsługę migawek.

Moim zdaniem, rozwiązanie jest bardzo fajne, sprawdzi się w wielu firmach (które mają bardziej zaawansowane urządzenia Synology), a także pozwoli zaoszczędzić sporo pieniędzy pozwalając uniknąć zakupu nowego serwera do wirtualizacji.

Powodzenia z testowaniem, a w razie pytań zapraszam do komentarzy!
