---
title: "[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"
categories:
    - Synology
tags:
    - Synology
    - Backup
    - PL post
---
!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/top_images/SynologyTOP.jpg)Kopia zapasowa jest bardzo ważna, dlatego chciałbym wam pokazać w jaki sposób skonfigurować Active Backup for Business.

W poprzednich dwóch postach skupiłem się na wstępnej konfiguracji *Synology Directory Services*, czyli linuxowym odpowiedniku Active Directory oraz profilach mobilnych, które pozwalały na trzymanie danych na serwerze, natomiast dziś chciałbym pokazać wam, w jaki sposób backupować nasze urządzenia za pomocą:

## Active Backup for Business

Jest to dodatek, który instalujemy z Package Center i wymaga on aktywacji na stronie Synology bezpośrednio po instalacji.

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/01.png)

Domyślnie konsola Administracyjna jest całkowicie pusta, ponieważ nie mamy skonfigurowanego żadnego urządzenia.

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/02.png)

Co znajdziemy na ekranie?

Z lewej strony znajduje się menu w którym możemy konfigurować:

* PC - komputery z Windows
* Physical Server - fizyczne urządzenia typu Windows Server
* File Server - zasoby montowane po SMB lub rsync 3.0
* Virtual Machiny - maszyny wirtualne z platform Hyper-V lub vSphere.

W zakładce **Storage** znajdziemy skonfigurowane foldery, do których backupujemy dane, w **Restore Status** będą wyświetlane aktualne zadania przywracania danych. Natomiast w **Activities** znajdziemy logi z skonfigurowanych maszyn dotyczące stworzonych zadań.

Na samym końcu jest zakładka **Settings**, w której znajdziemy opcje konfiguracyjne oraz szablony.

Po kilku dniach i dodaniu nowych urządzeń nasz panel będzie wyglądał zupełnie inaczej.

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/03.png)

Pokrótce wam wytłumaczę co widać na głównej stronie:

1) Informacje o ilości maszyn, którymi obecnie zarządzamy
2) Informacje o zadaniach na dany dzień
3) Aktualnie wykonywane zadania
4) Ostatnie zadania backupu
5) Ilość wykorzystanego miejsca **oraz co ważne** ilość miejsca wykorzystywanego po deduplikacji danych. Jeżeli pliki z trzech urządzeń posiadają taką samą sumę kontrolną, na naszym NASie będzie zapisana fizycznie tylko jedna kopia, co daje nam sporą oszczędność miejsca.
6) Logi z naszych zadań
7) Oraz wykres podsumowujący zadania

Przejdźmy z teorii do praktyki oraz dodajmy pierwsze zadanie backupujące dla naszego komputera.

Przechodzimy do zakładki **Settings** w której skonfigurujemy szablony zadań. Klikamy na **Templates** > **Create** i uzupełniamy nazwę, grupę użytkowników, którzy mają możliwość robienia tego backupu oraz typ **PC**.

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/04.png)

W kolejnym krokach definiujemy miejsce, gdzie będą zapisywane backupy oraz co ma być archiwizowane - całe urządzenie (włącznie z zewnętrznymi urządzeniami) lub tylko wolumen systemowy oraz czy chcemy kompresować i szyfrować transfer. Oczywiście, że chcemy, trochę bezpieczeństwa jeszcze nikomu nie zaszkodziło.

Ważne jest także poprawne ustawienie kiedy ma następować archiwizacja. Czy dziennie, czy na określoną akcję - te ustawienia zależą już od waszych potrzeb.

W ostatnim kroku konfigurujemy jak długo chcemy trzymać kopie zapasowe. Poprawna polityka trzymania kopii zapasowych może uratować nam życie, ale także generować sporą zajętość dysków, dlatego należy dobrze przemyśleć politykę trzymania kopii zapasowych. 

Po stworzeniu szablonu należy zainstalować klienta na urządzeniu końcowym oraz zalogować się danymi użytkownika, który ma uprawieniania do wykonania tej operacji. Czyli każdy użytkownik, który został przypisany do wcześniej utworzonego szablonu. O cichcej instalacji napiszę w którymś z kolejnych postów.

Po poprawnym zalogowaniu się szablon, który stworzyliśmy wcześniej zostanie zaaplikowany, nastąpi rozpoczęcie procesu backupowania a komputer użytkownika pojawi się w zakładce **PC** w naszym panelu tak jak na screenie:

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/05.png)

Jeżeli chcieli byśmy teraz przywrócić dane użytkownikowi, bo np. skasował sobie jakiś plik przechodzimy do **Active Backup for Business Portal**, którego znajdziemy w menu aplikacji. Otworzy nam to nową stronę, która domyślnie wygląda w taki sposób:

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/06.png)

Cały portal jest bardzo intuicyjny. Po lewej stronie mamy dyski / foldery, na środku mamy eksplorator plików, natomiast góra jest przeznaczona na wybór użytkownika / zadania, czyli w skrócie wybór urządzenia z którym chcemy pracować. 

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/07.png)

Pozostał nam dolny pasek, czyli timeline. Stamtąd wybieramy okres z którego chcemy przywrócić pliki. 

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/08.png)

Po wybraniu pliki / katalogu możemy go albo ściągnąć, albo przywrócić do określonej lokalizacji bezpośrednio na maszynę użytkownika. 

To by było na tyle co chciałbym wstępnie napisać o tym oprogramowaniu. Jest to tylko dla mnie pierwsza część wpisu, która będzie powiązana z kolejnymi, jednakże wpierw trzeba dodać nasze urządzenie do domeny Active Directory.
