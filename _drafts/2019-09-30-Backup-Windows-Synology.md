---
title: "[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"
categories:
    - Synology
tags:
    - Synology
    - Backup
    - Samba
    - PL post

---
!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/top_images/SynologyTOP.jpg)Backup w Twoim domu jak i w małej firmie, czyli kolejny post z serii: wykorzystanie urządzenia Synology NAS w realnym życiu.

W poprzednich postach skupiłem się na wstępnej konfiguracji *Synology Directory Services* oraz profilach mobilnych, natomiast dziś chciałbym pokazać wam, w jaki sposób backupować nasze urządzenia za pomocą:

## Active Backup for Business

Jest to darmowy dodatek lub też usługa, zależy jak to nazwiemy, który możemy ściągnąć ze sklepu, bezpośrednio na nasze urządzenie:

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/01.png)

Po zainstalowaniu i uruchomieniu dodatku pojawi nam się okno wstępnej konfiguracji, gdzie logujemy się na nasze konto Synology i aktywujemy oprogramowanie.

Po wykonaniu wstępnej konfiguracji otworzy nam się Panel Administratora, który na samym początku będzie pusty, jednak już po kilku dniach i po poprawnym skonfigurowaniu będzie wyglądał zupełnie inaczej.

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/02.png)

Co znajdziemy na ekranie?

Z lewej strony znajdziemy menu z naszymi urządzeniami, które możemy obsługować:

* PC - czyli komputery z Windows
* Physical Server - czyli backup Windows Server
* File Server, czyli zasoby montowane po SMB lub rsync 3.0
* Virtual Machine, czyli maszyny wirtualne. **Niestety**, tylko te z VMWare, nie jest obsługiwane Hyper-V lub inne platformy.

W zakładce **Storage** znajdziemy foldery, do których backupujemy dane, w kolejnej zakładce **Restore Status** będą wyświetlane aktualne zadania przywracania danych. Natomiast w **Activities** znajdziemy wszystkie logi z naszych maszyn dotyczące backupu.

Na samym końcu jest zakładka **Settings**, w której są niezbędne opcje do ustawienia.

Tak jak mówiłem, po kilku dniach panel może wyglądać np. w taki sposób jak na screenie:

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/03.png)

Pokrótce wam wytłumaczę co widać na głównej stronie:

1) Informacje o ilości maszyn, które obecnie backupujemy
2) Krótkie podsumowanie zadań na dany dzień. Czy było wszystko dobrze, czy jakieś ostrzeżenia, a może błędy
3) Aktualnie wykonywane zadania
4) Ostatnie zadania backupu
5) Ilość wykorzystanego miejsca **oraz co ważne** ilość miejsca wykorzystywanego po deduplikacji danych. Co to znaczy? Znaczy, że z trzech plików, które mają taką samą sumę kontrolną tylko jeden będzie fizycznie zapisany na naszym urządzeniu, pozostałe będą linkować do tego jednego. Jest to spora oszczędność miejsca
6) Logi z naszych zadań
7) Oraz wykres podsumowujący zadania

Jak widzicie, cały panel wygląda dość intuicyjnie i mamy podgląd na wszystkie aktywne zadania.

Przejdźmy z teorii do praktyki oraz dodajmy pierwsze zadanie backupujące dla naszego komputera.

Przechodzimy do zakładki **Settings** w której skonfigurujemy szablony zadań. Klikamy na **Templates** > **Create** i uzupełniamy nazwę, grupę użytkowników, którzy mają możliwość robienia tego backupu oraz typ. Jako typ wybrałem **PC**.

!["[PL] Backup dla Twoich maszyn za pomocą Active Backup for Business"](/assets/images/posts/Backup-Windows-Synology/04.png)

W kolejnym kroku definiujemy miejsce, gdzie będą zapisywane backupy