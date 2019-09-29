---
title: "[PL] Instalacja RSAT na Windows 10 - 1809 i wersje późniejsze"
categories:
    - Windows 
tags:
    - Synology
    - Active Directory
    - Samba
    - PL post
---
!["[PL] Instalacja RSAT na Windows 10 - 1809 i wersje późniejsze"](/assets/images/top_images/Windows10TOP.jpg)Wraz z wersją 1809 Microsoft postanowił zmienić sposób instalacji narzędzi RSAT - **Remote Server Administrator Tools** na taki, z użyciem Powershella.

W poście tym chciałbym wam pokazać jak wpierw wyświetlić dostępne role do zainstalowania, a następnie jak je łatwo zainstalować.

1. Sprawdzamy jakie role są dostepne do zainstalowania:

```powershell
Get-WindowsCapability -Name "RSAT*" -Online | Select-object Name, DisplayName
```

!["[PL] Instalacja RSAT na Windows 10 - 1809 i wersje późniejsze"](/assets/images/posts/RSAT-Windows10/01.png)

Wybieramy rolę, która nas interesuje i kopiujemy jej nazwę z pola **Name**

1. Instalujemy odpowiednią rolę wykonując komendę:

```powershell
Add-WindowsCapability –online –Name “Rsat.GroupPolicy.Management.Tools~~~~0.0.1.0”
```

!["[PL] Instalacja RSAT na Windows 10 - 1809 i wersje późniejsze"](/assets/images/posts/RSAT-Windows10/02.png)

Oczywiście, zmieniacie nazwy ról według swoich potrzeb.

A jak wyświetlić już zainstalowane role?

```powershell
Get-WindowsCapability -online | Where-Object {$_.State -eq "Installed" -and $_.Name -like "*RSAT*"}
```

Zwróci nam to wynik:
!["[PL] Instalacja RSAT na Windows 10 - 1809 i wersje późniejsze"](/assets/images/posts/RSAT-Windows10/03.png)

W ten sposób zobaczymy wszystkie zainstalowane dodatkowe role, **ale** tylko te, które mają w nazwie RSAT, czyli te do zarządzania Windows Server.
