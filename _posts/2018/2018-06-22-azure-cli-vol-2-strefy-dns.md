---
title: "[PL] Azure CLI vol 2 Strefy DNS"
categories:
    - Azure
tags:
    - CLI
    - PL Post

header-img: "/assets/images/posts/2018/azure-cli-vol-2-strefy-dns/top.jpg"
subtitle:   "[PL] Azure CLI vol 2 Strefy DNS"
---
![[PL] Azure CLI vol 2 Strefy DNS](/assets/images/posts/2018/azure-cli-vol-2-strefy-dns/top.jpg)Azure CLI vol 2 - Strefy DNS

Stało się.

Nadszedł czas, kiedy muszę się przenieść z jednej subkrypcji Azure na drugą. W zupełnie innych tenatach… I muszę przenieść wszystkie moje zasoby. Na szczeście ostatnimi czasy jest ich mało, bo tylko strefy DNS, ale… Ze sporą ilością rekordów jednak. Mógłbym przenieść je jeden do jednego, ale.. Nie chce mi się. Po prostu mi się nie chce 😉

Szukałem eksportu i importu plików stref w Azure, nie znalazłem. Ale potem sobie przypomniałem, że jest coś takiego jak Azure CLI.

O którym pisałem kiedy tutaj: [OSX, PowerShell… I zło konieczne](https://www.piesik.me/2017/07/12/osx-powershell-i-zlo-konieczne/)

Więc wróćmy do podstaw. Czym jest CLI popularnie zwane? Krótko mówiąc – interfejs linii poleceń.

Ale, żeby tak jak zwierzę się logować do Azure i wpisywać komendy zamiast klikać w GUI? No czasem trzeba. Nie bez powodu automatyzacja w PowerShellu jest tak piękna :3

Co potrzebujemy, aby przenieść nasze strefy DNS ?

Na początek polecam zainstalować aktualną wersję Azure CLI, którą znajdziecie pod tym linkiem.

Jak juz wam się zainstaluje, odpalcie wasz ulubiony terminal. Ja do tego używam Powershella, bo.. mam go praktycznie ciągle odpalonego.

Wpiszcie **az login** i wejdźcie na podaną stronę, podajcie kod, kliknijcie log in… I w ten sposób otrzymaliście dostęp do waszej subskrypcji Azure.

![[PL] Azure CLI vol 2 Strefy DNS](/assets/images/posts/2018/azure-cli-vol-2-strefy-dns/01.png)

Bajka, prawda?

To jak już się zalogowaliśmy, wylistujemy strefę DNS swojej domeny.

```cmd
az network dns record-set list -g nazwaGrupyZasobow -z nazwaDomeny
```

W ten sposób uzyskamy wszystkie rekordy.

Ale zaraz – może potrzebuję tylko rekordy srv ?

Ok, to lecimy poleceniem:

```cmd
az network dns record-set srv list -g nazwaGrupyZasobow -z nazwaDomeny
```

Zestaw najważniejszych linków znajdziecie pod tym linkiem

Przejdźmy do mięska głównego czyli najpierw eksportu strefy:

```cmd
az network dns zone export -g nazwaGrupyZasobow  -n nazwaDomeny -f nazwaPliku
```

Następnie zalogujmy się do nowego tenanta i wrzućmy swoją strefę do Azure:

```cmd
az network dns zone import -g nazwaGrupyZasobow  -n nazwaDomeny  -f nazwaPliku
```

Enter i… Voila! Waszastrefa jest importowana. Tak to wygląda:

![[PL] Azure CLI vol 2 Strefy DNS](/assets/images/posts/2018/azure-cli-vol-2-strefy-dns/02.png)

Nie pozostało wam teraz nic innego jak już zmienić adresy serwerów DNS u waszego hostingodawcy.

Cała operacja zajęła z 2-3 minuty zamiast 10 na żmudne przepisywanie i przeklikiwanie się przez portal.

Oczywiście oprócz importu, eksportu, wyświetlania mamy pełną możliwość zarządzania rekordami.

Kompletną instrukcję znajdziecie pod [tym linkiem](https://docs.microsoft.com/en-us/azure/dns/dns-getstarted-cli)
