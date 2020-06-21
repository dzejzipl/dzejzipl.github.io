title: "[PL] Modern Desktop Deployment and Management Lab Kit"
categories:
    - Intune
tags:
    - PL Post
    - TeamViewer
---
![[PL] Modern Desktop Deployment and Management Lab Kit](/assets/images/posts/modern-desktop-deployment-and-management-lab-kit/top.png)Modern Desktop Deployment and Management Lab Kit

Nauka nowych rzeczy nie jest łatwa. Zawsze istnieją jakieś „ale”, które nie pozwolą nam na wdrożenia testowego rozwiązania u siebie, aby zobaczyć w jaki sposób się je te nowe funkcje w programach lub systemach.

Najczęstszą przyczyną jest właśnie brak czasu na wstępną instalację Windows Server, instalację i konfigurację programów jak i bawienie się w całe tło, które nas totalnie nie obchodzi.

Dla osób, które nie chcą się bawić w takową konfigurację, a chcą się nauczyć w jaki sposób zarządzać Windows 10, Office 365. SCCM, MBAM oraz pokrewnych Microsoft co jakiś czas przygotowuje idealne laby, które możemy użyć na swoim urządzeniu – nazywają się one Modern Desktop Deployment and Management Lab Kit, natomiast wcześniej występowały pod nazwą: Windows 10 Deployment and Management Kit Lab.

Aby nie było tak różowo, to na samym początku muszę wam przedstawić kilka minusów z używania tego laba na domowym komputerze / serwerze.

Jest to bardzo, ale to bardzo RAMożerna konfiguracja. Mając 16GB Ramu – przeznaczonego tylko dla tego labu – dacie radę to zrobić. Ale w sumie o wiele lepiej się pracuje, jeżeli mamy w naszym urządzeniu 32GB – jest to potwierdzone info. A, gdybyście mieli te 64GB to spokojnie można pracować.

Procesor – moje i5-4460 trochę sobie daje radę. Nie jest najlepsze, ale…. Daje radę. Cztery rdzenie, cztery wątki to jest tak zwane must-have. W skrócie to powiem tylko, że im więcej, tym lepiej. A im nowszy – tym jeszcze lepszy! Podczas robienia poprzednich labów, większość czasu procesor pracował na 100% swoich możliwości. 

Dysk twardy, aka dysk SSD. 480-512 GB SSD, które miałem wcześniej u siebie na testach np. Transcend SSD 230S, sprawdziłby się doskonale. A z racji tego, że się go oddałem to muszę się ratować innymi rozwiązaniami.  Obecnie pracuję na trzech dyskach SSD + 1 dysk 1TB na przechowywanie danych. Po tym, jak lab zostanie zbudowany na jednym z dysków przez kreator to ja rozdzielam to na trzy pozostałe. Niestety, trzeba sobie radzić.  Podsumowując – dwa dyski SSD to minimum jak dla mnie do wykonania tych ćwiczeń.

Kolejnym wymaganiem – tenant na Azure AD + licencja Office 365. Wszystko może być wykorzystane za darmo. 

Skoro już przeszliśmy przez gorszą część, czyli wymagań przejdźmy do tej lepszej, czyli zalet takiego laba.

Główna jest taka, że dostajemy przygotowaną paczkę z wirtualnymi maszynami, które są już wstępnie skonfigurowane. Mają zainstalowane w sobie Windows Server 2016, Windows 10, SQL Servery i tym podobne – czyli sporo roboty już za nami.  Poniżej znajdziecie dokładną rozpiskę co znajduje się w paczce:

* Windows 10 Enterprise, wersja 1809 (Windows 10, update z Października 2018)
* Office 365 ProPlus Build 16.0.11121.20000
* System Center Configuration Manager, wersja 1802
* Windows Assessment and Deployment Kit dla Windows 10, wersja 1809
* Microsoft Deployment Toolkit 
* Microsoft BitLocker Administration and Monitoring 2.5 SP1
* Windows Server 2016
* Microsoft SQL Server 2014

Sporo, prawda? A teraz pomyślcie, że należało by to wszystko od samego początku instalować i konfigurować.

Oprócz tego, w środku znajdziecie też pełen poradnik wszystkich kroków, które należy wykonać w danej części laba. Jest tego całkiem sporo, ponieważ aż ponad 200 stron. Czeka was całkiem sporo zabawy.

Aby rozpocząć pracę należy odpalić plik setup.exe, który poprowadzi nas przez bezobsługowe wdrożenie. Całość zajmie około 20 minut, a jest to zależne od szybkości naszego dysku. 

![[PL] Modern Desktop Deployment and Management Lab Kit](/assets/images/posts/modern-desktop-deployment-and-management-lab-kit/01.png)

Po przejściu kreatora w Manadżerze Hyper-V pojawią się nam nowe maszyny wirtualne.

![[PL] Modern Desktop Deployment and Management Lab Kit](/assets/images/posts/modern-desktop-deployment-and-management-lab-kit/02.png)

Ładny zestaw, prawda? 

A co nam da zrobienie tego laba w praktyce? Przejdziemy przez następujące obszary:

* Przygotowania Azure AD + Office 365 do współpracy z naszym labem
* Konfigurację Windows Analytics + Enterprise Mode
* Konfiguracji SCCM, między innymi dla użycia Peer Cache, VPN, Intune Co-management
* Deployment Office 365 ProPlus i jego dostosowanie
* Microsoft Store for Business
* Migrację danych użytkowników
* Bezpieczeństwo w nowym Windows 10
* Czyste instalacje Windows 10, upgrade i update w różnych konfiguracjach
* I wiele, wiele innych.

Powiem tylko tyle, że zrobienie tego laba zajmie naprawdę wiele czasu, ale warto. Sam będę do tego przysiadał już w tym tygodniu i tego wszystkiego co się nauczę, będę wam opisywał.

Miłej zabawy!
