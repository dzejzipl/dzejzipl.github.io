title: "[PL] „Rozpoczynamy pracę z AutoPilot"
categories:
    - Intune
tags:
    - Intune
    - autopilot
    - PL post
---
![„[PL] Rozpoczynamy pracę z AutoPilot"](/assets/images/top_images/IntuneTOP.png)Jeżeli juz mamy skonfigurowany branding naszej organizacji, mamy stworzone odpowiednie grupy oraz użytkowników to dobrze by było rozpocząć pracę z **Windows AutoPilot**

Czym jest to słynne słowo? 

Przedstawie Wam realne zastosowanie tego rozwiązania. 

Pomyślmy, że otrzymujemy od naszego dostawcy 300 komputerów i wymieniamy całą naszą flotę. Te 300 komputerów trzeba wpiąć do sieci, puścić na nich instalację Windows, zainstalować odpowiednie oprogramowanie, zrzucić dane użytkowników jak i poczynić bardzo wiele kroków, aby takie urządzenie było przygotowane dla końcowego użytkownika.

A co, gdyby tych kroków nie trzeba było zrobić? Co, gdyby użytkownik końcowy odpalając po raz pierwszy komputer mógł przejść całą konfigurację bezboleśnie i samodzielnie?

Wygląda to w taki sposób, że dostawca tych urządzeń dostarcza nam 300 numerów seryjnych, my je wrzucamy do swojego tenanta, tworzymy i dostosowujemy odpowiednio profil a następnie końcowy użytkownik odpala nowe urządzenie i zaczyna sie dziać magia...

## Taka magia, że end-user po jakimś czasie ma zainstalowane całe niezbędne oprogramowanie bez żadnej jego ingerencji

Jeżeli już teoretyczny opis mamy za sobą, to przejdźmy do bardziej realnego świata, czyli domowego laba. 

## W jaki sposób pracować z **AutoPilot** w domowym zaciszu?

Plan jest prosty, potrzebujemy wykonać kilkanaście kroków.

1. Musimy uzyskać numer seryjny naszego urządzenia
2. Odpowiedni plik *.csv wrzucamy do Intune
3. Tworzymy profil AutoPilot
4. Przypisujemy do odpowiedniej grupy
5. Resetujemy komputer do trybu OOBE
6. Logujemy się do konta użytkownika i cieszymy się działającym systemem.

Wszystko to, co napisałem jest w bardzo wielkim skrócie dlatego rozpoczniemy wszystko od początku.

## Praca, praca, praca!

### Uzyskiwanie numeru seryjnego.

Uzyskać numer seryjny możemy albo bezpośrednio od naszego dostawcy, albo samodzielnie - za pomocą Powershell. Jako, że dostawcy nie mamy podziałajmy z magią. 

Rozpoczynamy od instalacji modułu oraz wyeksportowaniu niezbędnych danych do pliku CSV

```powershell
md c:\\HWID
Set-Location c:\\HWID
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted
Install-Script -Name Get-WindowsAutoPilotInfo
Get-WindowsAutoPilotInfo.ps1 -OutputFile AutoPilotHWID.csv
```


Wybieramy region, klawiaturę