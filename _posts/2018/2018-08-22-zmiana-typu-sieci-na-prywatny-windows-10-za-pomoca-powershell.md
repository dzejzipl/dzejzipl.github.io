---
title: "[PL] Zmiana typu sieci na prywatny – Windows 10 za pomocą PowerShell"
categories:
    - PowerShell
tags:
    - PowerShell
    - PL Post

header-img: "/assets/images/posts/2018/zmiana-typu-sieci-na-prywatny-windows-10-za-pomoca-powershell/top.jpg"
subtitle:   "[PL] Zmiana typu sieci na prywatny – Windows 10 za pomocą PowerShell"
---
![[PL] Zmiana typu sieci na prywatny – Windows 10 za pomocą PowerShell](/assets/images/posts/2018/zmiana-typu-sieci-na-prywatny-windows-10-za-pomoca-powershell/top.jpg)Zmiana typu sieci na prywatny – Windows 10 za pomocą PowerShell

Krótki wpis o tym jak zmienić typ połączenia na prywatny w Windows 10, bo to jest jeden z najczęściej spotykanych problemów przy pracy ze zdalnym Powershellem.

Dziś, po raz kolejny łącząc się przez enter-pssession otrzymałem znany komunikat:

```powershell
Message = WinRM firewall exception will not work since one of the network connection types on this machine is set to Public. Change the network connection type to either Domain or Private and try again.

Error number: -2144108183 0x80338169
WinRM firewall exception will not work since one of the network connection types on this machine is set to Public. Change the network connection type to either Domain or Private and try again.
```

Znów kochany Windows ustawił sieć na publiczną pomimo kliknięcia, że ma być prywatna. No zdarza mu się.

Pokażę wam szybki fix jak to naprawić.

Odpalamy PowerShella z uprawnieniami Administratora. Listujemy wszystkie sieci poleceniem: **Get-NetConnectionProfile** i otrzymujemy wynik:

![[PL] Zmiana typu sieci na prywatny – Windows 10 za pomocą PowerShell](/assets/images/posts/2018/zmiana-typu-sieci-na-prywatny-windows-10-za-pomoca-powershell/01.png)

Najważniejsze co musimy zobaczyć na screenie to: InterfaceIndex oraz NetworkCategory. Jeżeli drugi parametr jest Public to zapamiętajmy Index i przystąpmy to działania.

Aby to naprawić musimy wykonać jedną komendę:

```powershell
Set-NetConnectionProfile -InterfaceIndex IndexIntefejsu -NetworkCategory Private
```

gdzie pod IndexInterfejsu podstawiamy numer, który mamy z poprzedniego polecenia.

I tak czynimy dla wszystkich połączeń.

Krótko, ale na temat i przydatnie.
