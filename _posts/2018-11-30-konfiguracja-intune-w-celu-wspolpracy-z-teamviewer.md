---
title: "[PL] Konfiguracja Intune w celu współpracy z TeamViewer"
categories:
    - Intune
tags:
    - PL Post
    - TeamViewer
---
![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/top.jpg)Konfiguracja Intune w celu współpracy z TeamViewer

W moim [pierwszym poście](https://piesik.me/2018/11/09/intune-teamviewer-remote-support-w-akcji/) z tej serii przedstawiłem wam informację o współpracy TeamViewer z Intune. W drugim poście chciałem was poinstruować w jaki sposób dodać aplikację TeamViewer do Intune, aby wymusić zainstalowanie na telefonach komórkowych. Zapomniałem tylko o jednej, bardzo ważnej rzeczy. Skonfigurowaniu samego portalu, aby taka współpraca w ogóle mogła dojść do skutku.

Nadróbmy więc ten problem i do boju.

Pierwszy krok to dodanie do grupy Intune Role Administrator odpowiedniej grupy, która będzie zawierała w sobie grupę z dostępem Administracyjnym. Grupocepcja.

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/01.png)

Musimy również wybrać zakres do czego nasza grupa ma mieć dostęp. Ja wybrałem dostęp do wszystkich urządzeń i użytkowników:

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/02.png)

Pamiętacie grupę, którą dodaliście do roli Intune Role Administrator? Musicie jej również nadać uprawnienia do:

* Remote assistance
* Remote Tasks

Jak wygląda to w praktyce?

Remote assistance:

* Read > Yes
* Update > Yes

Remote Tasks:

* Request Remote assistance > YES

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/03.png)

W oficjalnym poradniku na stronie TeamViewer mamy informację, że musimy także ustawić odpowiednie uprawnienia dla Roli Intune Role Administrator, jednak nie możemy tego zrobić dopóki Intune nie będzie połączony z TeamViewer. Dlatego połączmy go według podanych niżej kroków.

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/04.png)

Aby rozpocząć konfigurację musimy kliknąć Connect, następnie OK

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/05.png)

Oraz połączyć konta:

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/06.png)

Po uzyskaniu komunikatu: *TeamViewer has been successfully connected. You can now close this window* możemy odświeżyć status połączenia i powinniśmy zobaczyć:

![[PL] Konfiguracja Intune w celu współpracy z TeamViewer](/assets/images/posts/konfiguracja-intune-w-celu-wspolpracy-z-teamviewer/07.png)

To wszystko!
