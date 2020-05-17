---
title: "[PL] Windows Subsystem for Linux – wersja dla Insiderów"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Windows Subsystem for Linux – wersja dla Insiderów](/assets/images/posts/windows-subsystem-for-linux-wersja-dla-insiderow/top.jpg)Windows Subsystem for Linux – wersja dla Insiderów

Cześć.

Jakiś czas temu wyszła nowa wersja Windows 10 dla Insiderów, która wprowadziła jedną, aczkolwiek dużą poprawkę w instalacji WSL ❤

Mianowicie – nie musimy już włączać trybu developerskiego, aby móc zainstalować WSL.

Dlatego też, najpierw wykonujemy krok pierwszy z poprzedniego postu ( link ), możemy również to zrobić za pomocą komendy:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

następnie w Powershellu wpisujemy polecenie:

**lxrun /install**

I.. To wszystko!

Jedna nowość, która może trochę nam uprzyjemnić pracę jeżeli nie chcemy mieć trybu developerskiego na swoim komputerze.

Have fun!
