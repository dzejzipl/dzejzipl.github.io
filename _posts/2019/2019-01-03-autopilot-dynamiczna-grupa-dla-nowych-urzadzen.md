---
title: "[PL] AutoPilot – Dynamiczna grupa dla nowych urządzeń"
categories:
    - Intune
tags:
    - PL Post
---
![[PL] AutoPilot – Dynamiczna grupa dla nowych urządzeń](/assets/images/posts/autopilot-dynamiczna-grupa-dla-nowych-urzadzen/top.png)AutoPilot – Dynamiczna grupa dla nowych urządzeń

Dziś krótko.

W jaki sposób stworzyć grupę dynamiczną dla wszystkich urządzeń, które mają używać AutoPilota?

Takie urządzenia wyróżniają się, że parametr zawierają wartość **[ZTDId]**

Stwórzmy więc dynamiczną grupę zawierającą wszystkie takie urządzenia:

![[PL] AutoPilot – Dynamiczna grupa dla nowych urządzeń](/assets/images/posts/autopilot-dynamiczna-grupa-dla-nowych-urzadzen/01.png)

Gdzie w treści reguły *(1)* wpiszemy wartość:

**(device.devicePhysicalIDs -any _ -contains „[ZTDId]”)**

Już po kilku minutach powinno pojawić nam się urządzenia przypisane do tej grupy.
