---
title: "[PL] Instalacja RSAT na Windows 10 - 1809 i późniejsze"
categories:
    - Windows 
tags:
    - Synology
    - Active Directory
    - Samba
    - PL post
---
1. Sprawdzamy jakie role są dostepne:
```powershell
Get-WindowsCapability -Name "RSAT*" -Online
```

Instalujemy odpowiednie role:
```powershell
Add-WindowsCapability –online –Name “Rsat.GroupPolicy.Management.Tools~~~~0.0.1.0”
```
