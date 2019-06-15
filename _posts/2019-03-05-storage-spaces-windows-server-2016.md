---
title: [PL] Storage Spaces – Windows Server 2016
categories:
    - Windows Server
tags:
    - Windows Server
    - Storage spaces
    - PL post
---
![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WindowsServerTOP.jpg)
Zawsze miałem problemy z partycjami, dyskami jak i ogólnym partycjonowaniem dysków. Denerwowało mnie to, że nie mogę mieć jednej wielkiej partycji, gdzie trzymałbym wszystkie dane, na którą składało by się kilka dysków.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/1.png)

Oczywiście, że mógłbym użyć do tego RAIDów i innych takich, ale nie mam serwera w domu ani też kontrolera RAID w moim domowym komputerze, który mi służy za serwer.

Dlatego też muszę sobie radzić inaczej.

Z racji tego, że moja bazowa konfiguracja to dwa dyski ADATA SP550 oraz najnowszy Samsung Evo 860, a za dwa tygodnie Kingston o pojemności 480GB to postanowiłem poświęcić trochę czasu na zagłębienie jak mogę to wszystko połączyć w jedną przestrzeń.

I jest tylko jedna odpowiedź, która pasuje idealnie do mojego scenariusza.

**Storage spaces**

Dla ułatwienia mojego dzisiejszego posta, chciałbym napisać, że mam sobie dwa dyski SSD, które chciałbym połączyć w jeden i na nim utworzyć jedną, dużą partycję, na której będę trzymał wszystkie dane.

Zaczynamy więc od zrozumienia tego, że najpierw tworzymy **Storage pools**, potem **Virtual disk** na tych storage poolach, natomiast na sam koniec – partycje.

Mając zamontowanych kilka dysków w swoim komputerze możemy zrobić albo jedną pulę, albo kilka. To wszystko zależy od naszych potrzeb. Ja stworzę jedną pulę, jeden dysk i jedną partycję. Może później, jak będę dodawał nowe dyski pomyślę o innym setupie.

Tak więc zaczynamy od potwierdzenia, że mamy dwa czyste dyski bez żadnych partycji. Dla przykładu zobaczymy to w **Create and Format hard disk Partition**

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/1.png)

Z dodatkowych ról nie musimy nic instalować, funkcja jest ta do użycia od razu po zainstalowaniu Windows Server.

Jeżeli już mamy pewność, że te dwa dyski są czyste, przechodzimy do Server Manager > File and Storage > Volumes > **Storage Pools**. Po prawej na dole widzimy swoje dwa fizyczne dyski, które przeznaczymy na potrzeby tego projektu.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/2.png)

Rozpoczynamy od stworzenia nowego Storage Pool, wybierając New Storage Pool

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/3.png)

Wybieramy serwer, na którym tworzymy pulę, ustawiamy nazwę:

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/4.png)

Następnie wybieramy dyski, które chcemy użyć (ja wybrałem dwa)

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/5.png)

Klikamy Next, Create i czekamy na stworzenie.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/6.png)

Jeżeli już mamy stworzoną pulę, przejdźmy do stworzenia wirtualnego dysku. Mnie interesuje tylko jeden dysk, nie potrzebuję dwóch albo i więcej. Klikamy więc New virtual Disk i wybieramy stworzona przez siebie pulę.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/7.png)

Ustawiamy nazwę, opis, klikamy Next i przechodzimy do kolejnego etapu, gdzie wybieramy typ.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/8.png)

- Simple. W tym wariancie nie będziemy mieli żadnego backupu. Mając trzy dyski po 100GB otrzymamy pojemność wspólną 300GB, ale jak jeden dysk nam padnie, to stracimy 100GB danych.
- Mirror. W tym wariancie dane są kopiowane na dwa dysk (lub trzy, w przypadku klastrów, których tu nie wykorzystujemy). Czyli dla przykładu używam dwóch dysków 100GB, pojemność końcowa wynosi 100GB, ale jeden dysk może zostać uszkodzony i nasze dane zostaną w pełni funkcjonalne.
- Parity. Tutaj jak samo jak w Mirror, ale informacje o danych są przerzucane na trzy dyski. Aby mieć 100GB miejsca, używamy trzech dysków 100GB.

Jak widać, mi najbardziej zależy na pojemności, nie na backupie więc wybieram opcję Simple. W kolejnym kroku wybieramy typ partycji: Thin lub Fixed.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/9.png)

Ja wybieram opcję Fixed, ponieważ chcę mieć pewność, że całość miejsca zostanie zaalokowana od razu.

W kroku „Size” wybieramy wielkość virtualnego dysku, ja wybieram „Maximum Size”. Potwierdzamy wszystkie parametry, czekamy na utworzenie wirtualnego dysku i po chwili możemy zobaczyć komunikat:

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/10.png)

Jeżeli zostawimy zaznaczonego checkboxa na dole po zamknięciu tego kreatora od razu pojawi nam się kreator nowej partycji.

![[PL] Storage Spaces – Windows Server 2016]({{ site.url }}{{ site.baseurl }}/assets/images/posts/storage-spaces-windows-server-2016/11.png)

Kreator jest bardzo intuicyjny w obsłudze, więc nie będę robił jego screenshotów.

Po jego zakończeniu mamy połączone dyski, możemy rozbudowywać i zmniejszać nasze storage pool. Mi się to akurat bardzo mocno przyda w moim domowym labie.
