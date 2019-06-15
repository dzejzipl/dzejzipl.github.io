---
title: "[PL] Instalacja Windows Admin Center na Windows Server Core"
categories:
    - Windows Server
tags:
    - Windows Server
    - WAC
    - Windows Server Core
    - PL post
---
![Instalacja Windows Admin Center na Windows Server Core]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WACTOP.jpg)
Ostatnio musiałem zainstalować na Windows Server 2019 w wersji CORE, Windows Admin Center. Jak wiemy, wersja CORE nie posiada GUI, więc musiałem to zrobić z linii komend co okazało się banalnie prostym zadaniem. Prawie tak samo prostym jak instalacja na zwykłym Windows Server.

Tworzymy nowy katalog na dysku C, np. Temp, przechodzimy do niego i wykonujemy polecenie ( z powershella)

```powershell
Invoke-WebRequest -uri ” https://aka.ms/WACDownload” -OutFile „C:\temp\WAC.msi”
```

Dzięki tej komendzie pobierzemy do C:\temp plik instalacyjny z nazwą WAC.msi

Aby zainstalować, wykonujemy polecenie:

```cmd
msiexec /i .msi /qn /L*v log.txt SME_PORT= 8080 SSL_CERTIFICATE_OPTION=generate
```

Gdzie pod port 8080 wstawiamy swój port. Ta komenda wygeneruje certyfikat automatycznie, a co jeżeli mamy już certyfikaty w swojej infrastrukturze? Wtedy należy użyć polecenia:

```cmd
msiexec /i .msi /qn /L*v log.txt SME_PORT=<PORT> SME_THUMBPRINT= <THUBMPRINT> SSL_CERTIFICATE_OPTION=installed
```

Aby odpalić aplikację wpisujemy w przeglądarce: https://nazwahosta:naszport

Sposób prosty i bez problemowy, a co najważniejsze – przetestowany.
