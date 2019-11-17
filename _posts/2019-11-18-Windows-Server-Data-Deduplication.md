---
title: "[PL] Windows Server Data Deduplication"
categories:
    - Windows Server
tags:
    - Windows Server
    - PL post
---
!["[PL] Windows Server Data Deduplication"]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WindowsServerTOP.jpg)Pojemność dysków może być problemem przy pracy z obrazami. A dlaczego by nie oszczędzić trochę miejsca?

Obecnie najwięcej pracuję na swoim najnowszym nabytku, czyli HP Prodesk G2 Mini, w którym mam zainstalowane dwa dyski. 120GB na system oraz 250 M2 NVME na maszyny wirtualne. Jak by nie patrzeć, te 250GB to jest całkiem mało.

!["[PL] Windows Server Data Deduplication"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Windows-Server-Data-Deduplication/01.png)

Dobrze jeszcze nie zacząłem instalować maszyn do zabaw jak widać na powyższym screenie a już mi zostało tylko 60GB wolnego miejsca. 

W Windows Server 2012 została zaprezentowana taka fajna funkcja jak **Data Deduplication**, ltóra pozawala na rozpoczęcie oszczędzania miejsca na naszym dysku. A ile tego miejsca zostanie oszczędzone, zależy już od naszej specyfiki pracy.

Instalacja jest prosta - dodajemy dodatkową rolę do serwera, który ma obsługiwać tę funkcję:

!["[PL] Windows Server Data Deduplication"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Windows-Server-Data-Deduplication/02.png)

Następnie przechodzimy do *File and Storage Servies* > *Volumes* > *Disk*, wybieramy nasz wolumen, klikamy prawym i wybieramy **Configure Data Deduplication**

!["[PL] Windows Server Data Deduplication"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Windows-Server-Data-Deduplication/03.png)

Wybieramy zastosowanie - dla mnie będzie to *General purpose file server*, określamy jak długo mają być nieużywane pliki do deduplikacji, czyli **starsze** niż x dni, na samym końcu możemy wykluczyć określone rozszerzenia oraz ustawić wykonywanie zadania w określonym czasie. Jasne, ustawmy to. Nie chcę, aby to się działo w momencie, gdy mogę robić jakieś laby czyli poniedziałek - piątek od 15:30 oraz w sobotę - niedzielę całe dnie.

!["[PL] Windows Server Data Deduplication"]({{ site.url }}{{ site.baseurl }}/assets/images/posts/Windows-Server-Data-Deduplication/04.png)

I to by było na tyle. Zadanie zostało skonfigurowane, teraz już tylko poczekać na efekty i zobaczymy, ile miejsca oszczędzimy.
