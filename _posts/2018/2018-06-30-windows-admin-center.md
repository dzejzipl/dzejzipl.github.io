---
title: "[PL] Windows Admin Center"
categories:
    - Other
tags:
    - WAC
    - Windows Admin Center
    - PL Post

header-img: "/assets/images/posts/2018/windows-admin-center/top.png"
subtitle:   "[PL] Windows Admin Center"
---
![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/top.png)Windows Admin Center

Zarządzanie wieloma systemami, które są oparte na Windows Server lub Windows 10 (tak, też takie widziałem) może nastręczyć wielu różnych problemów. Aby się do nich podłączyc trzeba pamiętać adresy, loginy, hasła… No i uruchamiać pulpit zdalny. W skrócie mówiąc – wychodzi to trochę więcej czasu niżeli byśmy chcieli na to poświęcić.

Dlatego wcześniej korzystałem z Microsoft Remote Desktop Manager, którego opisałem w [tym wpisie](https://www.piesik.me/2017/07/16/remote-desktop-connection-manager-przyjemna-praca-na-rdp/) i sprawdzał się całkiem przyjemnie.

Jednak nadszedł czas na coś lepszego – usługę a właściwie program nazwany Windows Admin Center, wcześniej znany jako Microsoft Honolulu.

Aplikacja ta służy nam do zarządzania różnymi usługami na systemach Windows. Pozwoli nam na zainstalowanie Windows Update, sprawdzenie stanu usług, skonfigurowanie ról i usług i wielu, wielu innych akcji.

Zaraz, zaraz czy kiedyś nie było czegoś podobnego? A było, nawet opisywana wcześniej przeze mnie usługa [Server Managment Tools](https://www.piesik.me/2017/03/29/server-management-tools-zarzadzanie-serwerami-w-azure/), która pozwalała nam na zarządzanie serwerami w Azure. I muszę przyznać, że to była całkiem ciekawa usługa.

Przenieśmy się jednak do środowiska on-premise.

W jaki sposób możemy zacząć pracę z naszymi systemami?

Najłatwiej będzie rozpocząć od ściągnięcia najnowszej wersji WAC (Windows Admin Center) z strony [https://aka.ms/WACDownload], a następnie zainstalowanie z wybranym przez nas portem. Instalacja nie nastręcza żadnych problemów, dlatego nie będę jej opisywał.

Po chwili wyszukujemy nasze oprogramowanie:

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/01.png)

Program przywita nas podglądem wszystkich połaczeń – na tą chwilę znajdziecie tam tylko jedno, to z waszym komputerem:

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/02.png)

Czas będzie dodać swoje pierwsze połączenie. Jednak przed tym jeżeli nie używacie środowiska domenowego koniecznie zapoznajcie się z tym wpisem – uratuje wam wiele nerwów.

Klikamy Add > Add Server Connection, uzupełniamy tagi jeżeli jest potrzeba, wpisujemy nazwę serwera, klikamy Submit…

I jeżeli teraz spróbujemy się podłączyć niestety nie uda się. Musimy manualnie ustawić do niego domenę / login / hasło.

Zaznaczamy go z listy, klikamy Manage As i wpisujemy odpowienie dane do logowania.

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/03.png)

Drobna uwaga do was – jeżeli nie jest to komputer w środowisku domenowym, trzeba poprzedzić nazwę użytkownika nazwą komputera.

Na screenie niżej jak to wygląda do mojego testowego serwera WDS.

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/04.png)

Po tym pozostało nam już kliknąć Connect i cieszyć wzrok bardzo rozwijanym narzędziem.

Spójrzcie na tą gigantyczną ilość opcji, którą możecie wykorzystać pracując tylko na przeglądarce!

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/05.png)

Dla przykładu możecie sprawdzić status Windows Update

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/06.png)

Stworzyć użytkownika i dodać go do odpowiedniej grupy

![[PL] Windows Admin Center](/assets/images/posts/2018/windows-admin-center/06.png)

Oraz wykonać, wiele, wiele innych działań, które normalnie byście robili za pomocą PowerShella, a tak to można szybko wyklikać w GUI.

Muszę przyznać, że będzie to moje narzędzie: must have do codziennej pracy.
