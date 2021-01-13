---
title: "[PL] Mikrotik – wykresy i statystyki"
categories:
    - Random
tags:
    - mikrotik
    - statyski
    - PL post
---
![Mikrotik – wykresy i statystyki]({{ site.url }}{{ site.baseurl }}/assets/images/posts/top_images/mikrotikTOP.png)
Ostatnio w moje rączki wpadło nowe urządzenie – **Mikrotik hap AC2**, o którym chciałbym wam trochę opowiedzieć w kilku wpisach.

Na sam początek chciałbym wrzucić informację o wykresach, które może nam Mikrotik generować w celu rozpoznania, jakie obciążenie łącza, procesora, wykorzystanie pamięci i tym podobne generuje nasze urządzenie. Często w celach statystycznych, ale warto takie coś mieć w zapasie.

Logujemy się do Winboxa, przechodzimy do **Tools** > **Graphing** i rozpoczynamy od dodania reguły do rysowania wykresów na interfejsach. Wybieramy interfejs, który chcemy monitorować – ja wybiorę z listy wszystkie i pozwalam na dostęp dla wszystkich adresów, bo i tak dostęp do Mikrotika jest tylko z wewnętrznej sieci.

![[PL] Mikrotik – wykresy i statystyki]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-wykresy-i-statystyki/1.png)

Jeżeli już dodamy taką regułę, wchodzimy na adres IP routera/graphs w celu zobaczenia wykresów:

![[PL] Mikrotik – wykresy i statystyki]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-wykresy-i-statystyki/2.png)

A co z tymi wykresami na procesor / dysk jak i użycie pamięci? Musimy przejść do **Tools** > **Graphing** > **Resource Rules** i stworzyć nową regułę. Tak jak w poprzednim punkcie, jest to otwarte dla wszystkich z wewnętrznej sieci.

![[PL] Mikrotik – wykresy i statystyki]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-wykresy-i-statystyki/3.png)

Po odświeżeniu strony z wykresami będziemy mieli taki widok:

![[PL] Mikrotik – wykresy i statystyki]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-wykresy-i-statystyki/4.png)

A finalnie statystyki wyglądają własnie w taki sposób:

![[PL] Mikrotik – wykresy i statystyki]({{ site.url }}{{ site.baseurl }}/assets/images/posts/mikrotik-wykresy-i-statystyki/5.png)
