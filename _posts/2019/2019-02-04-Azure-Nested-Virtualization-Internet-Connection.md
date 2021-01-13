---
title: Azure Nested Virtualization - Internet Connection
categories:
    - Azure
    - Windows Server
tags:
    - azure
    - nested virtualization
    - powershell
    - switch
    - windows server
---
![Azure Nested Virtualization - Internet Connection]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Nested-Virtualization-Internet-Connection/top.jpg)
Yesterday I created new machine on Azure with Windows on board –
Standard D8s v3 (8 vcpus, 32 GB memory). It’s something big for me – previous I was used smaller machines. So, main target of that machine is virtualization. I’m preparing posts about Remote Desktop Services, so I needed one host where I install Hyper-V role, and on that Hyper-V I install 5 x Windows Server 2019.

Sharing network on Azure is not easy like in our home environment and we need to create second switch, create network and set up NAT. It’s easy to do with my post.

First, we need to create virtual switch named **NATSwitch** using that PowerShell command:

```powershell
New-VMSwitch –SwitchName “NATSwitch” –SwitchType Internal
```

![Azure Nested Virtualization - Internet Connection]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Nested-Virtualization-Internet-Connection/1.png)

After that we need to create new address with that command ( I will use space **192.168.0.0/24**) and assign it to previously created Switch

```powershell
New-NetIPAddress –IPAddress 192.168.0.1 -PrefixLength 24 -InterfaceAlias „vEthernet (NATSwitch)”
```

![Azure Nested Virtualization - Internet Connection]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Nested-Virtualization-Internet-Connection/2.png)

On the end we need to create NAT on our switch which we created:

```powershell
New-NetNat –Name NatNetworkRDS –InternalIPInterfaceAddressPrefix 192.168.0.0/24
```

![Azure Nested Virtualization - Internet Connection]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Nested-Virtualization-Internet-Connection/3.png)

Now, you need use that **NATSwitch** and assign manually IP address like on below screen. After that you should have Internet connection.

![Azure Nested Virtualization - Internet Connection]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Azure-Nested-Virtualization-Internet-Connection/4.png)

You can see that I have IPv4 address from 192.168.0.0/24, but as DNS server i’m using Google servers. Why? Because on host machine I don’t have installed dns role.
