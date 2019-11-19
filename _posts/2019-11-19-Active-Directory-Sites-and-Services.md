---
title: "[PL] Active Directory Sites and Services"
categories:
    - Windows Server
    - Active Directory
tags:
    - Windows Server
    - Active Directory
    - PL post
---
!["[PL] Active Directory Sites and Services"]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WindowsServerTOP.jpg)Sites and Services w akcji - czym jest i jak używać?

**Active Directory Sites and Services** jest funkcją w Windows Server, która pozwala nam na logiczny podział naszej sieci. W moim domowym labie mam 3 kontrolery domeny w trzech różnych subnetach z następującymi adresami IP:

* S01-M01 - 192.168.110.2/24
* S02-M01- 192.168.120.2/24
* S03-M01 - 192.168.130.2/24

Jak widzimy, są to trzy różne sieci, które reprezentują mi trzy siedziby. Wrocław, Londyn i Warszawę. 

W momencie poprawnego skonfigurowania **Site and Services** użytkownicy, a zarazem komputery będą się logowały do najbliższego kontrolera AD, nie natomiast do losowo wybranego. Dla przykładu, użytkownicy z Londynu nie będą się logować do Warszawy. 

U mnie będzie jeszcze coś takiego zrobione, że site - Londyn będzie oddzielną subdomeną w AD, czyli london.piesik.online.

Skoro już znamy teorię, czas przystąpić po praktyki.

Otwieramy na naszym jednych z kontrolerów domeny przystawkę Site and Services i przyjrzyjmy się wpierw strukturze:

!["[PL] Active Directory Sites and Services"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Active-Directory-Sites-and-Services
/01.png)

Jak widzimy, mamy domyślnie stworzonego pierwszego site'a. Dla przypomnienia dodam tylko, że u mnie mają być trzy site: Warsaw, London, Wroclaw.

Mamy także pustą tabelkę subnets. Po co nam ona? Dzięki niej serwery będą automatycznie trafiać do odpowiedniego site.

Wpierw należy utworzyć site - robimy to za pomocą kliknięcia prawym na *Sites* > New site. Zostawiamy domyślny link, na razie nie potrzebujemy nic modyfikować i nazywamy odpowiednio site. Powtarzamy czynność tyle razy, ile chcemy mieć site.

!["[PL] Active Directory Sites and Services"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Active-Directory-Sites-and-Services
/02.png)

Następnie rozpoczynamy konfigurację subnetów. Klikamy prawym na Subnets > New Subnet i tworzymy według schematu: 192.168.110.**0**/24, tak jak napisałem przy rozpisaniu struktury i dodajemy do odpowiedniego site.

!["[PL] Active Directory Sites and Services"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Active-Directory-Sites-and-Services
/03.png)

Wszystko fajnie, trzy site utworzone, ale nasze serwery są nadal w **Default-First-Site-Name**, jak je teraz przenieść? Klikamy prawym przyciskiem na jeden z serwerów, wybieramy *All tasks* > **Move** i zaznaczamy do którego site przenosimy.

Jak to wygląda finalnie? Tak jak na screenie.

!["[PL] Active Directory Sites and Services"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Active-Directory-Sites-and-Services
/04.png)
