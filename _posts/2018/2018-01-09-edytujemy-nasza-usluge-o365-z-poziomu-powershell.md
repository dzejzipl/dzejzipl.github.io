---
title: "[PL] Edytujemy naszą usługę O365 z poziomu PowerShell"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Edytujemy naszą usługę O365 z poziomu PowerShell](/assets/images/posts/edytujemy-nasza-usluge-o365-z-poziomu-powershell/top.jpg)Edytujemy naszą usługę O365 z poziomu PowerShell

Cześć.

Miałem dziś potrzebę wylistować użytkowników mojego tenanta (aż czterech!)  z określonymi kolumnami a następnie wprowadzić aktualizację ich parametrów (dla przykładu użyję Dział oraz Miasto).

Mogłem to zrobić z poziomu ECP, ale… Niby to tylko czterech użytkowników, zrobie to szybciej niżeli instalowanie addonów, łączenie się za pomocą PowerShella i tak dalej.. A co jeżeli takich użytkowników mamy juz 100? Też to zrobimy z poziomu ECP? Oczywiście. Tylko, że o w wiele, wiele dłuższym czasie.

Na potrzeby wpisu przyjmiemy, że jest to system Windows 10, bez zainstalowanych modułów Powershell.

Aby rozpocząć pracę z O365 w PS potrzebujemy modułów z galerii:

MSOnline  z linku: https://www.powershellgallery.com/packages/MSOnline/
Azure AD PowerShell z linku https://www.powershellgallery.com/packages/AzureAD/
Oba moduły instalujemy w bardzo łatwny sposób:

```powershell
Install-Module -Name MSOnline
Install-Module -Name AzureAD
```

Kolejnym krokiem będzie zalogowanie się do swoich usług

```powershell
Connect-AzureAD
$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential (Get-Credential) -Authentication Basic -AllowRedirection
Import-PSSession $Session
Connect-MsolService
```

Po poprawnym zalogowaniu możemy wylistować np. swoje skrzynki mailowe poleceniem:

```powershell
Get-mailbox
```

Ja potrzebowałem wyeksportować wszystkie dane moich użytkowników do pliku csv. W tym celu użyłem polecenia:

```powershell
get-user -resultsize unlimited |select * |export-csv c:\dane_ps\uzytkownicy.csv
```

Dzięki temu uzyskałem kompletny plik csv z każdą możliwą komórką do uzupełnienia. Po uzupełnieniu wszystkich niezbędnych danych musimy w jakiś sposób dodać te dane, prawda?
Zrobimy to w taki sposób:

```powershell
Import-Csv „c:\dane_ps\uzytkownicy.csv” | foreach{Set-MsolUser -UserPrincipalName $_.UserPrincipalName -Department $_.Department -City $_.City }
```

Dlaczego to polecenie wygląda w taki sposób? Najpierw importujemy plik cvs, potem dla każdego rekordu z tego pliku wykonujemy polecenie Set-MsolUser z parametrem, który identyfikuje naszego użytkownika: UserPrincipalName, a każdy kolejny parametr wskazuje wartość, którą modyfikujemy. Możemy dodać tych parametrów nawet 30 jeżeli mamy taką ochotę. 

Po chwili nasze wartości powinny być widoczne poprawnie w ECP.

Jak dla mnie – ułatwia to bardzo pracę.

Have fun!
