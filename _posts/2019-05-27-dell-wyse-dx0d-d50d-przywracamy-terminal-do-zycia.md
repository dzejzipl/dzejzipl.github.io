---
title: "[PL] Dell Wyse Dx0D D50D – przywracamy terminal do życia"
categories:
    - Remote Desktop Services
tags:
    - Windows Server
    - Wyse
    - Remote Desktop Services
    - ThinLinux
    - PL post
---
![Dell Wyse Dx0D D50D – przywracamy terminal do życia]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WyseTOP.jpg)Stało się.

W moje rączki finalnie trafił terminal Wyse. W sumie to marzyłem o tym zakupie od ponad roku, gdy zobaczyłem jakie jest realne zastosowanie takich terminali.

A sam terminal nie jest modelem najmłodszym, jest jednym z starszych, które można dostać na rynku, aczkolwiek na sam początek moich zabaw z RDS powinien wystarczyć. Późiej kupię nowy, z ulepszoną konfiguracją, jednak pierwsze wpisy powstaną na podstawie pracy z tymże modelem, który posiada 2GB ramu jak i 2GB flash Disk.

Problem po zakupie był jeden – nie posiadał on żadnego systemu operacyjnego. Niby wiem w jaki sposób powinno to wszystko działać, jednak musiałem poświęcić calkiem sporo czasu na przygotowanie czystej, podstawowej konfiguracji. Czyli takiej, którą otrzymujecie po zakupie.

W tym wpisie chciałbym wam przedstawić część pierwszą – czyli resetujemy nasz terminal do ustawień domyślnych..

Rozpoczynamy od przejścia na stronę Dell Download i wpisania Serial Number naszego urządzenia, które zostanie przekonwertowane na Service Tag, następnie przechodzimy do zakładki **Sterowniki i pliki do pobrania​.**

To, co mnie najbardziej interesuje to: **ThinOS 8.5_009 English Merlin Image file for Dell Wyse 5010 and 5040 AIO thin clients with 2 GB flash**

![Dell Wyse Dx0D D50D – przywracamy terminal do życia]({{ site.url }}{{ site.baseurl }}/assets/images/posts/dell-wyse-dx0d-d50d-przywracamy-terminal-do-zycia/1.png)

System, który pobierzemy jest z grudnia zeszłego roku co jest niezłym wynikem biorąc pod uwagę, że terminal jest wyprodukowany w 2013 roku.

Pobranie systemu bazowego to pierwszy krok, drugim jest pobranie **Wyse USB Firmware Tool**, który zrobi nam bootowalnego pendrive z tymże systemem. Polecam najnowszą wersję, działała bez żadnego problemu.

Rozpoczynamy od instalacji oraz uruchomienia programu. W pierwszym kroku wybieramy dysk na którym chcemy pracować (najlepiej będzie jeżeli to będzie czysty pendrive), następnie przechodzimy do zakładki **Image Push**, gdzie dodajemy nasz obraz.

![Dell Wyse Dx0D D50D – przywracamy terminal do życia]({{ site.url }}{{ site.baseurl }}/assets/images/posts/dell-wyse-dx0d-d50d-przywracamy-terminal-do-zycia/2.png)

Pamiętajcie o wybraniu poprawnej ścieżki jak i rozszerzenia plików:

![Dell Wyse Dx0D D50D – przywracamy terminal do życia]({{ site.url }}{{ site.baseurl }}/assets/images/posts/dell-wyse-dx0d-d50d-przywracamy-terminal-do-zycia/3.png)

Jeżeli zobaczymy ten komunikat po chwili, to znaczy, że pendrive został przygotowany poprawnie i możemy go włożyć do Wyse.

![Dell Wyse Dx0D D50D – przywracamy terminal do życia]({{ site.url }}{{ site.baseurl }}/assets/images/posts/dell-wyse-dx0d-d50d-przywracamy-terminal-do-zycia/4.png)

Uruchamiamy nasz terminal, na klawiaturze wciskamy „P” w celu przejścia do Boot Menu i wybieramy nasz pendrive.

A tak w ogóle to domyślne hasło do bios w tej Wyse to: ***Fireport***. I ważna jest wielkość liter, czyli pierwsza litera jest duża.

Na dziś to będzie wszystko, w kolejnych wpisach stworzymy prosty serwer z plikami konfiguracyjnymi Wyse jak i skonfigurujemy Remote Sessions dla Windows RDS.
