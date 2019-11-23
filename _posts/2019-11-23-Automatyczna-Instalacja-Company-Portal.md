---
title: "[PL] Automatyczna instalacja Company Portal"
categories:
    - Intune
tags:
    - Intune
    - App Deployment
    - PL post
---
!["[PL] Automatyczna instalacja Company Portal"]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/IntuneTOP.png)
Dlaczego by nie wymusić automatycznej instalacji Company Portal na wszystkich urządzeniach, które są zarządzane za pomocą Intune?

W poprzednich artykułach związanych z Azure AD napisałem o tym, że komputery, które są dodane do lokalnego AD mogą być dodane do Azure AD, dzięki czemu będą zarządzane za pomocą Intune. Całość możecie przeczytać [tutaj](https://www.piesik.me/2019/11/17/AzureAD-Hybrid-Join/)

W nowoczesnym środowisku komputery są zarządzane za pomocą SCCMa, jednak nie wszystkie firmy posiadają go wdrożonego. Ja natomiast bardziej się skupiam na małych firmach, dlatego chciałbym wam pokazać dziś, w jaki sposób wymusić automatyczną instalację oprogramowania **Company Portal** na tych urządzeniach, które są dodane do lokalnego AD.

Rozpoczynamy od stworzenia grupy z urządzeniami, dla przykładu tak wygląda moja:

!["[PL] Automatyczna instalacja Company Portal"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Automatyczna-Instalacja-Company-Portal/01.png)

Następnie przechodzimy do *Intune* > *Client apps* > **Apps** i wyszukujemy aplikację o nazwie *Company Portal (online). Otwieramy ją i przechodzimy do zakładki *Assignments*

* Assignment type: **Required**
* Included Groups: nasza wcześniej stworzona grupa

Finalnie to wygląda w taki sposób:

!["[PL] Automatyczna instalacja Company Portal"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Automatyczna-Instalacja-Company-Portal/02.png)

Po chwili instalacja się rozpocznie, a raport z instalacji powinien wyglądać w taki sposób:

!["[PL] Automatyczna instalacja Company Portal"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Automatyczna-Instalacja-Company-Portal/03.png)

Oczywiście, sposób ten nie ogranicza się tylko do komputerów z lokalnego AD, jak widzicie na screenach, ta aplikacja jest też instalowana na komputerach, które przechodzą przez AutoPilota.
