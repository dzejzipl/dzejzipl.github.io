---
title: "[PL] Deploy aplikacji TeamViewer przez Intune dla Androida"
categories:
    - Intune
tags:
    - PL Post
    - TeamViewer
---
![[PL] Deploy aplikacji TeamViewer przez Intune dla Androida](/assets/images/posts/deploy-aplikacji-teamviewer-przez-intune-dla-androida/top.jpg)Deploy aplikacji TeamViewer przez Intune dla Androida

W [moim poprzednim wpisie](https://piesik.me/2018/11/09/intune-teamviewer-remote-support-w-akcji/) przekazałem wam informację, że jest możliwość zintegrowania Intune oraz aplikacji TeamViewer, aby móc udzielać pomocy zdalnej naszym pracownikom.

Dziś natomiast chciałbym wam pokazać w jaki sposób możemy dodać aplikację TeamViewer QuickSupport, aby była dostępna poprzez portal Firmy – Intune do zainstalowania oraz w jaki sposób ją skonfigurować, aby móc ją użyć z naszą organizacją.

Dodawanie aplikacji, aby była dostępna na telefonie komórkowym opisywałem już w tym wpisie, ale zróbmy to jeszcze jeden raz na potrzeby tego wpisu.

Na początku potrzebujemy posiadać adres Google Play do aplikacji, którą chcemy dodać do Company Portal. Dla aplikacji TeamViewer Quick Support jest to adres: https://play.google.com/store/apps/details?id=com.teamviewer.quicksupport.market

Jeżeli już znamy ten adres, przechodzi do ustawień naszego Intune, następnie do zakładki Client apps > Apps i dodajemy nową aplikację za pomocą przycisku Add

![[PL] Deploy aplikacji TeamViewer przez Intune dla Androida](/assets/images/posts/deploy-aplikacji-teamviewer-przez-intune-dla-androida/01.png)

Ja ustawiłem całą konfigurację dla aplikacji Androida w sposób następujący:

![[PL] Deploy aplikacji TeamViewer przez Intune dla Androida](/assets/images/posts/deploy-aplikacji-teamviewer-przez-intune-dla-androida/02.png)

Jeżeli już dodamy naszą aplikację należy ją przypisać do grupy:

![[PL] Deploy aplikacji TeamViewer przez Intune dla Androida](/assets/images/posts/deploy-aplikacji-teamviewer-przez-intune-dla-androida/03.png)

Ja ustawiłem aplikację jako Required dla danej grupy użytkowników i po zaaktualizowaniu polity na Intune na moim urządzeniu pojawił mi się komunikat:

![[PL] Deploy aplikacji TeamViewer przez Intune dla Androida](/assets/images/posts/deploy-aplikacji-teamviewer-przez-intune-dla-androida/04.png)

I jeżeli chodzi o wdrożenie dla Androida, to już wszystko.
