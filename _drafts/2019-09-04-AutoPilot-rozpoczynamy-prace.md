---
title: "[PL] Rozpoczynamy pracę z AutoPilot"
categories:
    - AutoPilot
    - Intune
tags:
    - Intune
    - Azure Active Directory
    - AutoPilot
    - PL post
---
!["[PL] Rozpoczynamy pracę z AutoPilot"](/assets/images/top_images/AutoPilotTOP.jpg) A gdyby rozpocząć wdrażać bezobsługowo komputery w swojej organizacji?

Zawsze mnie interesowało wdrażanie urządzeń, a im mniej bezobsługowe było tym dla mnnie lepiej. Pamiętam, że w mojej wcześniejszej pracy należało przenieść ponad 100 użytkowników na nowe urządzenia. A jak to najlepiej robić? Cóż.. Instalując system i przenosząc dane - folder po folderze. Sporo czasu mi to zajęło, a z perspektywy czasu uważam, że nawet na tamte czasy można to było zrobić dużo, dużo lepiej. Nie narzekajmy jednak, człowiek się uczy całe życie. 

Jakiś czas temu, firma Microsoft postanowiła wydać nowy produkt działający na platformie Azure, ściśle współpracujący z Intune. Nazwali go....

## Windows AutoPilot

Od razu zapałałem do niego sporą miłością, właśnie ze względu na to, że lubię się bawić masowym deploymentem urządzeń. Może jednak przejdźmy do rzeczy i spróbuję Wam wytłumaczyć czym jest ta funkcja:

Pomyślmy, że otrzymujemy od naszego dostawcy 300 komputerów i wymieniamy całą naszą flotę. Te 300 komputerów trzeba wpiąć do sieci, puścić na nich instalację Windows, zainstalować odpowiednie oprogramowanie, zrzucić dane użytkowników jak i poczynić bardzo wiele kroków, aby takie urządzenie było przygotowane dla końcowego użytkownika.

A co, gdyby tych kroków nie trzeba było zrobić? Co, gdyby użytkownik końcowy odpalając po raz pierwszy komputer mógł przejść całą konfigurację bezboleśnie i samodzielnie?

Wygląda to w taki sposób, że dostawca tych urządzeń dostarcza nam 300 numerów seryjnych, my je wrzucamy do swojego tenanta, tworzymy i dostosowujemy odpowiednio profil a następnie końcowy użytkownik odpala nowe urządzenie i zaczyna sie dziać magia...

## Taka magia, że end-user po jakimś czasie ma zainstalowane całe niezbędne oprogramowanie bez żadnej jego ingerencji

Jeżeli już teoretyczny opis mamy za sobą, to przejdźmy do bardziej realnego świata, czyli:

## Jak rozpocząć pracę z **AutoPilot** w domowym zaciszu?

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

Uzyskać numer seryjny możemy albo bezpośrednio od naszego relesellera, albo samodzielnie - za pomocą Powershell. Jako, że ja pracuję na jednym urządzeniu to chciałbym wyciągnąć wszystkie niezbędne dane za pomocą PowerShella.

Rozpoczynamy od instalacji modułu oraz wyeksportowaniu niezbędnych danych do pliku CSV, następnie ustawiamy *execution policy* na Unrestricted, instalujemy skrypt **GetWindowsAutoPilotInfo** na samym końcu pobieramy niezbędne dane i zapisujemy je do pliku *AutoPilotHWID.csv*

```powershell
md c:\\HWID
Set-Location c:\\HWID
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted
Install-Script -Name Get-WindowsAutoPilotInfo
Get-WindowsAutoPilotInfo.ps1 -OutputFile AutoPilotHWID.csv
```

Logujemy się do portalu Device Management pod adresem: https://devicemanagement.portal.azure.com/ kontem, które ma odpowiednie uprawnienia, przechodzimy do zakładki **Device Enrollment** > **Windows Enrollment** > **Devices**

!["[PL] Rozpoczynamy pracę z AutoPilot"](/assets/images/posts/AutoPilot-rozpoczynamy-prace/01.png)

W nowym oknie musimy dodać nowe urządzenie za pomocą przycisku **Import**, następnie po zakończonym imporcie klikamy **Sync** oraz **Refresh**.

Po tym, jak 