---
title: "[PL] Azure Nano Server - Enter-PSSession – Cannot connect"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] Azure Nano Server Enter-PSSession – Cannot connect](/assets/images/posts/azure-nano-server-enter-pssession-cannot-connect/top.png)Azure Nano Server Enter-PSSession – Cannot connect

Cześć.

Dziś na bardzo krótko.

Miałem potrzebę wypuścić nano-server w Azure do krótkiego testu. Standardowy deployment poprzez Azure, 20 minut później serwer gotowy.. Ale jak się do niego podłączyć? Przecież on nie posiada RPD wbudowanego..

Więc z pomocą przychodzi do nas PowerShell i słynne Enter-PSSession.

Więc zapisuję adres IP swojego serwera, uruchamiam konsolę z prawami Administratora i….

**Enter-PSSession : Connecting to remote server….**

Co się stało? Co źle zrobiłem?

Spróbowałem z parametrem -Credential mojanazwauseradlamaszyny i nadal nic… Ciągle ten sam błąd.

Może z parametrem -UseSSL ? Nie, niestety też nie.

No to sprawdźmy Firewall dla tej maszyny.

Szybkie sprawdzenie i reguły przychodzące są puste. Może dlatego połączenia są blokowane? Krótka chwila na google i już wiem, że WinRM używa dwóch portów:

* TCP/5985 = HTTP
* TCP/5986 = HTTPS

Dodałem te porty jako dozwolone co widać na screenie:

![[PL] Azure Nano Server Enter-PSSession – Cannot connect](/assets/images/posts/azure-nano-server-enter-pssession-cannot-connect/01.png)

No i spróbowałem się podłączyć.

Nadal błąd…

Ostatnie szukanie opisu błędu w wyszukiwarce naprowadził mnie na informację o tym, że komputery niepodłączone do domeny AD mogą posiadać taki błąd i rozwiązaniem jest ustawienie tego hosta jako zaufanego.

Robimy to następującą komendą (uruchomienie tej komendy nadpisze zaufane hosty, dlatego jeżeli chcemy już ją używać, lepiej jest dopisać host do istniejącej listy, którą gdzieś już sobie prowadzimy)

```powershell
Set-Item wsman:localhost\Client\TrustedHosts ‚adresIPmaszyny’
```

 w konsoli PowerShell

Po tym zabiegu wykonujemy komendę:

```powershell
Enter-PSSession adresIPmaszyny -Credential nazwauzytkownika
```

i powinno już wszystko działać…

W razie pytań – standardowo zapraszam.

Ps – pisane wieczorem, więc gdybym się pomylił  czymś – to dajcie znać!
