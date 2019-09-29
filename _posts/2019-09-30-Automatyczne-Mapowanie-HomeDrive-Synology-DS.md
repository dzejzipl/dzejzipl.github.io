---
title: "[PL] Automatyczne mapowanie HomeDrive w Synology Directory Services"
categories:
    - Synology
tags:
    - Synology
    - Active Directory
    - Samba
    - PL post
---
!["[PL] Automatyczne mapowanie HomeDrive w Synology Directory Services"](/assets/images/top_images/SynologyTOP.jpg)W poprzednim poście [link](https://www.piesik.me/2019/09/29/Synology-AD-HomeDrives/#) pokazałem wam, w jaki sposób stworzyć HomeDrives dla naszych użytkowników.

A teraz chciałbym wam pokrótce pokazać w jaki sposób automatycznie zamapować taki dysk, aby użytkownicy mogli się do niego dostać bez potrzeby wpisania nazwy hosta / adresu IP i folderu.

Tak jak poprzednio, wykorzystam do tego domyślną regułę GPO, następnie przejdę do: **User Configuration** > **Preferences** > **Windows Settings** > **Drive Maps**

!["[PL] Automatyczne mapowanie HomeDrive w Synology Directory Services"](/assets/images/posts/Automatyczne-Mapowanie-HomeDrive-Synology-DS/01.png)

Jak widzicie na powyższym screenie, ja już stworzyłem taki dysk, który się automatycznie mapuje, ale zobaczcie jak to wygląda od strony ustawień tego dysku:

!["[PL] Automatyczne mapowanie HomeDrive w Synology Directory Services"](/assets/images/posts/Automatyczne-Mapowanie-HomeDrive-Synology-DS/02.png)

W polu: Location wpisujemy naszą lokalizację dysków, pamiętajmy tylko, aby na samym końcu dodać zmienną *%username%*, która identyfikuje aktualnie zalogowanego użytkownika. 

Przypisałem mu stałą literkę w systemie, tak samo jak odpowiednio nazwałem, aby użytkownik nie miał wątpliwości co to jest za dysk.

Po odświeżeniu polityk GPO na komputerze pojawi się nowy dysk:

!["[PL] Automatyczne mapowanie HomeDrive w Synology Directory Services"](/assets/images/posts/Automatyczne-Mapowanie-HomeDrive-Synology-DS/03.png)

Zrobiłem to tak, dlatego, że nie każdy użytkownik chce trzymać swoje pliki na Pulpicie lub Dokumentach. Niektórzy wolą po prostu trzymać na dysku sieciowym, bez potrzeby synchronizacji z lokalnym urządzeniem.
