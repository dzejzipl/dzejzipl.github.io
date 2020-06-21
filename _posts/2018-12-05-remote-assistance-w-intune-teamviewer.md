---
title: "[PL] Remote Assistance w Intune + TeamViewer"
categories:
    - Intune
tags:
    - PL Post
    - TeamViewer
---
![[PL] Remote Assistance w Intune + TeamViewer](/assets/images/posts/remote-assistance-w-intune-teamviewer/top.jpg)Remote Assistance w Intune + TeamViewer

I o to właśnie wisienka na torcie jeżeli chodzi o Remote Assistance w połączeniu Intune + TeamViewer. 

Mogliście przeczytać już kilka wpisów, jeszcze jeden jest w przygotowaniu – chodzi o deploy aplikacji TeamViewer na Windows 10, ale to „soon”, więc przejdźmy do ostatniego – w sumie najważniejszego wpisu. 

W jaki sposób udzielać pomocy zdalnej używając Intune?

Dla przykładu dodam, że będę korzystał z aplikacji TeamViewer na komputerze, który dodany jest do Azure AD. Na tym urządzeniu nie przeprowadzałem żadnej konfiguracji, jest po prostu zainstalowany program TeamViewer w najzwyklejszym setupie, czyli next, next, next…. Możemy do tego wykorzystać również moduł [Host](https://piesik.me/2018/12/04/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/), który opisałem wam w poprzednim wpisie. 

Przechodzimy do portalu Device Management, następnie do Devices > All Devices > nasze urządzenie, do którego chcemy się podłączyć

![[PL] Remote Assistance w Intune + TeamViewer](/assets/images/posts/remote-assistance-w-intune-teamviewer/01.png)

Jeżeli już wybierzemy poprawne urządzenie, przechodzimy do More, klikamy na New Remote Assistance Session, po chwili na dole pojawia nam się informacja: Start Remote Assistance, która pozwoli nam na otworzenie okienka w TeamViewer w oczekiwaniu na partnera

![[PL] Remote Assistance w Intune + TeamViewer](/assets/images/posts/remote-assistance-w-intune-teamviewer/02.png)

A jak to wygląda u naszego partnera ? Musi otworzyć Company Portal, w której wyskoczy mu powiadomienie:

![[PL] Remote Assistance w Intune + TeamViewer](/assets/images/posts/remote-assistance-w-intune-teamviewer/03.png)

I jeżeli chodzi o TeamViewer, to by w sumie było już wszystko. Postaram się dla was jeszcze opisać deployment aplikacji na Win10, ale na to potrzebuję trochę więcej czasu, więc… Stay tunned! 

I w razie gdyby były jakieś pytania, zapraszam do komentarzy. Z miłą chęcią pomogę. 
