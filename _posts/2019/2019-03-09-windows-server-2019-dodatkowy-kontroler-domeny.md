---
title: "[PL] Windows Server 2019 – dodatkowy kontroler domeny"
categories:
    - Windows Server
tags:
    - Windows Server
    - Active Directory
    - PL post
---
![Windows Server 2019 – dodatkowy kontroler domeny]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/WindowsServerTOP.jpg)No więc postanowiłem się trochę pobawić w Windows Server 2019. Na samym początku postawiłem domenę AD o nazwie: ITCNS.pl wraz z jednym kontrolerem domeny. O tym będzie post później. Chciałbym teraz dodać drugi serwer, który będzie zapasowym kontrolerem domeny i na niego pójdzie replikacja jak i będzie do użytku w razie awarii tego pierwszego.

Konfiguracja IP pierwszego kontrolera, który został już wcześniej skonfigurowany wygląda w taki sposób:

![Windows Server 2019 – dodatkowy kontroler domeny]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-server-2019-dodatkowy-kontroler-domeny/1.png)

Pod jedynką mam aktualny adres IP pierwszego AD, pod dwójką DNS na tym samym urządzeniu, natomiast pod trójką ustawiłem adres IP nowego kontrolera, na którym również będzie serwer DNS postawiony.

Rozpoczynamy od instalacji ról AD DS i DNS jak na screenie:

![Windows Server 2019 – dodatkowy kontroler domeny]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-server-2019-dodatkowy-kontroler-domeny/2.png)

Nastepnie dodajemy nasz kontroler do istniejącej już domeny wraz z loginem i hasłem konta administratora domeny:

![Windows Server 2019 – dodatkowy kontroler domeny]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-server-2019-dodatkowy-kontroler-domeny/3.png)

W kolejnym kroku wybieramy skąd mają być replikowane dane. Powinniśmy wybrać główny kontroler.

![Windows Server 2019 – dodatkowy kontroler domeny]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-server-2019-dodatkowy-kontroler-domeny/4.png)

Klikamy next kilka razy, instalujemy.. Restartujemy i na naszym zapasowym AD DS konfigurujemy IP według opcji:

![Windows Server 2019 – dodatkowy kontroler domeny]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-server-2019-dodatkowy-kontroler-domeny/5.png)

Pod jedynką mamy adres IP maszyny, pod preferowanym DNS ustawiam główny kontroler, natomiast pod zapasowy – maszyna, na której mamy backup.

W kolejnym wpisie utworzymy replikację DNS.
