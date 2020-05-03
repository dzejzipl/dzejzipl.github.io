---
title: "[PL] Komenda /runas jako ratownik w pomocy zdalnej"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Komenda /runas jako ratownik w pomocy zdalnej](/assets/images/posts/komenda-runas-jako-ratownik-w-pomocy-zdalnej/top.jpg)Korzystamy z komendy RunAs

Ostatnio zacząłem używać  programu Windows Remote Asistance jako zamiennika dla TeamViewer. Zasadną różnicą przy korzystaniu z tego pierwszego jest to, że użytkownik doskonale wie kiedy się łączę i musi mi udzielić stosownego zezwolenia na działanie na jego komputerze.

W tym wpisie przybliżę wam krótko działanie komendy runas, która ratuje nam tyłek, ponieważ w Windows Remote Assistance (WRA) nie wyskakuje okno z poświadczeniami i użytkownik sam musiałby wpisać takie dane.

Pokażę wam teraz sposób w jaki sposób uruchomić konsolę z prawami administratora, a później np.: zarządzanie użytkownikami.

W pierwszym kroku otwieramy zwykłą konsolę i następnie wpisujemy:

runas /user:domena\uzytkownik cmd

Potem zostaniemy poproszeni o wpisanie hasła dla danego użytkownika. Jeżeli logujemy się na konto lokalnego użytkownika nie wpisujemy domeny, a tylko nazwę lokalnego usera, czyli:

runas /user:uzytkownik cmd

Na podglądzie można zobaczyć jak to wygląda:

![[PL] Komenda /runas jako ratownik w pomocy zdalnej](/assets/images/posts/komenda-runas-jako-ratownik-w-pomocy-zdalnej/01.png)

Potem wyskoczy Wam okienko, którego góra będzie prezentowała się w taki sposób:

![[PL] Komenda /runas jako ratownik w pomocy zdalnej](/assets/images/posts/komenda-runas-jako-ratownik-w-pomocy-zdalnej/02.png)
