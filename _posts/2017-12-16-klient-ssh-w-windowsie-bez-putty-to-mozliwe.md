---
title: "[PL] Klient SSH w Windowsie? Bez Putty? To możliwe!"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Klient SSH w Windowsie? Bez Putty? To możliwe!](/assets/images/posts/klient-ssh-w-windowsie-bez-putty-to-mozliwe/01.jpg)Klient SSH w Windowsie? Bez Putty? To możliwe!

Ostatnio Microsoft nas rozpieszcza. Najpierw był Windows Subsystem for Linux, którego opisywałem tu oraz tu, a teraz otrzymujemy kolejną funkcjonalnośc, której bardzo mi brakowało, a używałem do niej zewnętrznego programu, czyli Putty.

Czym jest Putty? W najprostszym zastosowaniu jest to klient, który służy nam do połączenia poprzez protokół SSH do innych serwerów. Ma kilka zalet, np. zapisywanie serwerów do których się łączymy, logowanie wpisywanych danych oraz np. łączenie za pomocą serial portu zamiast SSH. Jednak ja używałem go tylko do połączeń administracyjnych z innymi Linuxami. I to nie były jakieś mega zaawansowane sprawy, więc wykorzystywałem go w bardzo podstawowy sposób.

Więc… Co nam daje nowa funkcjonalność, która jest na tą chwilę w wersji beta? W skrócie mówiąc: właśnie łączenie do innych serwerów poprzez SSH.

Przystąpmy do szybkiej pracy, aby móc używać tej nowej funkcji.

Z menu start wybieramy Settings > Apps > Apps & features i klikamy w Manage optional features

![[PL] Klient SSH w Windowsie? Bez Putty? To możliwe!](/assets/images/posts/klient-ssh-w-windowsie-bez-putty-to-mozliwe/02.png)

Dalej musimy wybrać Add a feature

![[PL] Klient SSH w Windowsie? Bez Putty? To możliwe!](/assets/images/posts/klient-ssh-w-windowsie-bez-putty-to-mozliwe/03.png)

I z listy instalujemy OpenSSH Client (Beta)

![[PL] Klient SSH w Windowsie? Bez Putty? To możliwe!](/assets/images/posts/klient-ssh-w-windowsie-bez-putty-to-mozliwe/03.png)

Po restarcie komputera otwieramy PowerShella lub linie komend i wpisujemy komendę połączenia z serwerem SSH… I finito!

Mała funkcjonalność, ale jak bardzo mocno cieszy. Szczególnie, jeżeli ktoś nie używa WSLa. W takim wypadku nie trzeba doinstalowywać żadnego pakietu tylko korzystajmy z tego, który znajdziemy w Windows Subsystem for Linux.