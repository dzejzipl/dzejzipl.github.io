---
title: "[PL] Synology NAS - Docker"
categories:
    - Synology
tags:
    - Synology
    - Docker
    - PL post
---
!["[PL] Synology NAS - Docker"](/assets/images/top_images/SynologyTOP.jpg)A może tak słów kilka na temat kontenerów w Synology?

Z racji tego, że lubię pracować z wirtualnymi maszynami poczułem potrzebę postawienia kilku maszyn linuxowych do celów prywatnych. Czyli w skrócie mówiąc - użyciu kontenerów.

Dlatego też od razu skierowałem się do sklepu z elektroniką, wyszukałem Rasperry Pi (najlepiej w wersji czwartej, tej najbardziej wypasionej) i chciałem już kupować, jednak wtem pomyślałem, że moje Synology posiada wbudowaną obsługę Dockera. Dlaczego by tego nie użyć? 

Więc zabierzmy się za stworzenie pierwszego kontenera z użyciem addina o magicznej nazwie Docker, którego ściągniemy z *Package Center*. 

To nie będzie zaawansowany poradnik, bo sam też nie jestem zaaawansowany. Po prostu chcę tego używać w domowym zastosowaniu i opiszę wam realny przykład jak tego użyć.

Dla przykładu, jestem osobą, której zdarza się czytać ebooki. Mam już trochę ich w swojej kolekcji, jednak zawsze były one wrzucone do folderu w stylu "gdzieś i kiedyś posortuję". Po długim czasie udało mi się je posortować na OneDrive, jednak każda reinstalacja systemu polegała na ściągnięciu kilku GB z ebookami, instalacją programu Calibre do zarządzania książkami i tak dalej... Za dużo nikomu nie potrzebnej roboty.

Gdzieś w Internecie zobaczyłem, że istnieje gotowy obraz, który nam robi interfejs webowy dla naszej bazy danych utworzonej w Calibre. Wygląda on dokładnie w taki sposób:

!["[PL] Synology NAS - Docker"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Synology-NAS-Docker/01.png)

Ładnie, prawda? Mamy możliwość czytania książek online, ściągania, wrzucania - w skrócie... Wszystko działa tak samo jak na Calibre, przynajmniej dla moich potrzeb. 

Przejdźmy do praktyki.

Po zainstalowaniu dodatku, uruchamiamy go i naszym oczom powinien pojawić się widok podobny do tego:

!["[PL] Synology NAS - Docker"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Synology-NAS-Docker/02.png)

Jak widzimy, mamy kilka zakładek:

* Container, gdzie są stworzone kontenery
* Registry, gdzie możemy przeszukać całą bazę z obrazami
* Image to miejsce, gdzie są zapisane ściągnięte przez nas obrazy
* Network, czyli ustawienia sieci
* A w Log znajdziemy wszystkie logi z wykonywanych przez nas akcji

Wpierw należy ściągnąć obraz z repozytorium, czyli przechodzimy do *Registry* wpisujemy odpowiednią frazę i klikamy dwa razy na obraz. Na potrzeby postu niech ta fraza będzie: **calibre-web**

!["[PL] Synology NAS - Docker"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Synology-NAS-Docker/03.png)

Po kliknęciu Download lub dwukliku pojawia nam się popup z pytaniem jaką wersję (tag) chcemy pobrać. Mnie zawsze interesuje najnowsza. Czekamy na pobranie...

Po pobraniu przechodzimy do **Image**, klikamy na nasz obraz dwukrotnie i otrzymamy popup, w którym będziemy mogli rozpocząć tworzenie kontenera. 

Ustawiamy mu nazwę, możemy skonfigurować, aby nie zużywał więcej pamięci niż określona przez nas ilość. Nas jednak interesuje **Advanced Settings**
