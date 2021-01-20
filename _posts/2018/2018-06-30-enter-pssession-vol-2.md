---
title: "[PL] Enter-PSSession – vol 2"
categories:
    - PowerShell
tags:
    - Enter-PSSession
    - PL Post

header-img: "/assets/images/posts/2018/enter-pssession-vol-2/top.jpg"
subtitle:   "[PL] Enter-PSSession – vol 2"
---
![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/top.jpg)Enter-PSSession – vol 2

Długi czas temu popełniłem wpis, który pomógł mi rozwiązać wiele problemów z zdalnym łączeniem do Windows Server.

Możecie go przeczytać pod tym linkiem. W skrócie mówiąc, przy próbie połączenia za pomocą Enter-PSSession otrzymywałem błąd: **Enter-PSSession : Connecting to remote server ….. failed with the following error message**… i tak dalej…

Możecie go zobaczyć na screenie poniżej:

![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/01.png)

Zawsze to naprawiałem dodawając hosta i robiąc spis takich hostów w jakimś pliku tekstowym. Słabe rozwiązanie i w końcu trzeba było znaleźć nowe.

Możemy zarządzać tymi wpisami za pomocą samego Powershella.

Na początek w jaki sposób wyswietlić istniejące zaufane hosty:

```powershell
Get-Item WSMan:\localhost\Client\TrustedHosts
```

Jeżeli nie mamy żadnych dodanych to zwróci nam to taki wynik:

![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/02.png)

Dobrze by było dodać pierwszy. Wykorzystajmy do tego komendę:

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value 'nazwaMaszyny'
```

![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/03.png)

I w momencie jak wylistujemy znów listę hostów otrzymamy już taki wynik:

![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/04.png)

Zawsze mozemy skopiować sobie nazwy hostów z pola value wykonując polecenie:

```powershell
Get-Item WSMan:\localhost\Client\TrustedHosts | select value 
```

i dodając na końcu nowego hosta, dla przykładu takie polecenie będzie wyglądać tak:

![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/05.png)

Ale to będzie trochę upierdliwe, ponieważ za każdym razem musimy pamiętać, aby kopiować całą wartość z hostami.

Dlaczego by nie dodać po prostu nowego hosta przerobionym poleceniem?

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value 'nazwaHosta2′ -Concatenate
```

Spójrzcie na wynik – jest o wiele szybciej.

![[PL] Enter-PSSession – vol 2](/assets/images/posts/2018/enter-pssession-vol-2/06.png)

I tyle – zarządzanie hostami zaufanymi jest o wiele łatwiejsze!
