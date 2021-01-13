---
title: "[PL] Hyper-V na Azure VM – Połączenie z Internetem"
categories:
    - Hyper-V
    - Azure
tags:
    - Azure
    - Hyper-V
    - Nested virtualization
    - PL post
---
![Hyper-V na Azure VM – Połączenie z Internetem]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WindowsServerTOP.jpg)
Nadszedł czas, gdy musiałem wykorzystać Azurowe maszyny do mojej pracy. TL;DR jest takie, że mam maszynę z Windows Server 2019, a na niej postawione inne maszyny. Dla przykładu Windows Server 2019, które będą mi służyć do Remote Desktop Services.

Rolę możemy zainstalować albo ***Add Roles and Features*** lub też za pomocą PowerShella:

```powershell
Install-WindowsFeature -Name Hyper-V -IncludeManagementTools -Restart
```

To wypadało by również ogarnąć sieć na tym serwerze, prawda? Doskonale wiemy o tym, że sieć jest tam zupełnie inaczej skonstruowana, dlatego musimy wykorzystać do tego "**NAT Network**".

Poradnik będzie dosyć krótki, bo nie ma tu zbytnio o czym pisać. Musicie jednak pamiętać, aby na każdej maszynie ustawić statyczny adres IP z odpowiedniej klasy, którą za chwilę stworzymy. Dla przykładu, ja wykorzystam sieć 192.168.0.0/24

Najpierw tworzymy switcha:

```powershell
New-VMSwitch –SwitchName “NATSwitch” –SwitchType Internal
```

![Hyper-V na Azure VM – Połączenie z Internetem]({{ site.url }}{{ site.baseurl }}/assets/images/posts/hyper-v-na-azure-vm-polaczenie-z-internetem/1.png)

Następnie tworzymy nową adresację

```powershell
New-NetIPAddress –IPAddress 192.168.0.1 -PrefixLength 24 -InterfaceAlias „vEthernet (NATSwitch)”
```

![Hyper-V na Azure VM – Połączenie z Internetem]({{ site.url }}{{ site.baseurl }}/assets/images/posts/hyper-v-na-azure-vm-polaczenie-z-internetem/2.png)

A na końcu tworzymy NAT:

```powershell
New-NetNat –Name NatNetworkRDS –InternalIPInterfaceAddressPrefix 192.168.0.0/24
```

![Hyper-V na Azure VM – Połączenie z Internetem]({{ site.url }}{{ site.baseurl }}/assets/images/posts/hyper-v-na-azure-vm-polaczenie-z-internetem/3.png)

Na maszynie, która jest wizualizowana ustawiamy adres IP z powyższej puli jak na screenie:

![Hyper-V na Azure VM – Połączenie z Internetem]({{ site.url }}{{ site.baseurl }}/assets/images/posts/hyper-v-na-azure-vm-polaczenie-z-internetem/4.png)

I w ten sposób kończymy konfigurację sieci na dodatkowych maszynach.
