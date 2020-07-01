---
title: "[PL] Synology DS918+ NAS do domu jak i małej firmy"
categories:
    - Recenzje
tags:
    - PL Post
---
![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/top.jpg)Synology DS918+ NAS do domu jak i małej firmy

Backup naszych danych jest ważny. A jeszcze ważniejsze jest dbanie o jego regularność jak i sprawdzanie czy te dane będą mogły zostać bez problemu przywrócone.

Najważniejsze swoje dane trzymam w dwóch niezależnych lokalizacjach, natomiast mam bardzo dużo danych, które używam do codziennej pracy na blogu. Są to przeróżne pliki – począwszy od instalatorów różnych programów, pliki ISO z systemami, kończąc na plikach VHD z dyskami maszyn na których pracowałem. Ilościowo tego jest sporo, bo około 500GB. Obecnie jest to trzymane na jednym dysku, który jest podłączony bezpośrednio pod mój domowy serwer z Hyper-V, ale… Boli mnie trochę sytuacja, że jak to stracę to sporo czasu upłynie zanim odzyskam wszystkie pliki.

Firma Synology. Możecie ją znać jako producenta dysków sieciowych dla domowych użytkowników, małych firm jak i tych dużo większych, gdzie wymagana jest bardzo duża wydajność. W mojej poprzedniej firmie używałem model DS1817, którego pokochałem za możliwość rozbudowy, wydajność jak i ogólne działanie. Przetrzymywał około 30TB danych, a przy większym obciążeniu nawet się nie zmęczył…  Potwierdzone działaniem jak i statystykami.

Jako, że ja jestem użytkownikiem domowym to pod moje strzechy dotarł model DS918+, który posiada przyzwoitą konfigurację, bo w standardzie dostajemy 6 slotów na dyski, dwa złącza LAN oraz porty USB.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/01.jpg)

Zabawę rozpocząłem od odpakowania urządzenia, które wykonane jest z ciemnego, proszkowanego materiału z widocznymi czterema ramkami na dyski, diodami, które mówią nam o statusie urządzenia oraz portem USB 3.0 na przednim panelu do podłączenia dodatkowego urządzenia.

Jeżeli chodzi o konfigurację dyskową to niewiele rzeczy nas ogranicza. W slotach na dyski z przedniego panelu możemy zamontować nawet do 56TB w czterech dyskach (obecny Firmware urządzenia wspiera pojedynczy dysk do 14TB) oraz dwa dodatkowe dyski w standardzie m.2, które mogą nam posłużyć jako dyski cache albo jako po prostu dodatkowe miejsce na przechowywanie. Mnogość rozwiązań, drodzy Państwo.

Montaż dysków jest banalnie prosty. W przypadku dysków 3,5’wykorzystujemy tylko boczne szyny, które zastępują nam śrubki, natomiast dla dysków 2,5′ musimy użyć dołączonych śrubek z zestawu. Do tego otrzymujemy również zasilacz, kabel IEC oraz RJ45 jak i niezbędne dla nas wszystkich ulotki.

Testowa konfiguracja składała się z dwóch dysków ADATA SP550 jak i mojego najnowszego nabytku Samsung EVO 860 o pojemności 240GB.

Konfigurację rozpoczynamy w dwojaki sposób:

* Jeżeli znamy adres IP urządzenia to przechodzimy od razu na stronę konfiguracji
* Lub poprzez wyszukanie urządzenia za pomocą specjalnej strony: find.synology.com

Dla domowych użytkowników idealnym rozwiązaniem jest drugie rozwiązanie, ponieważ nie mamy potrzeby zaglądania w konfigurację routera i szukania właściwego adresu. Zobaczcie jak to wygląda w praktyce:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/02.png)

Wstępna konfiguracja nie sprawi problemów nawet laikowi, musimy podać tylko kilka niezbędnych danych i już możemy rozpocząć pracę na naszym urządzeniu. Na potrzeby testów utworzyłem pierwszy wolumen składający się z dwóch dysków ADATA w RAID oraz drugi wolumen, który ma tylko jeden dysk w sobie: Samsung EVO. Cała konfiguracja jest tak prosta jak wstępna konfiguracja urządzenia i przeprowadza ją z nami konfigurator:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/04.png)

Utworzyłem RAID 1 z dwóch pierwszych dysków oraz konfigurację JBOD z trzeciego dysku:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/05.png)


Kolejnym krokiem, który musimy dokonać jest utworzenie folderów współdzielonych, które tworzymy również za pomocą… A jakże, bardzo prostego i przyjaznego kreatora. Możemy włączyć kosz sieciowy, ukryć katalog przed użytkownikami, którzy nie mają dostępu oraz zaszyfrować katalog za pomocą hasła. Po utworzeniu takiego folderu należy nadać uprawnienia, natomiast w domowym zastosowaniu wystarczy użyć takich opcji:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/06.png)

Po chwili możemy cieszyć się widokiem poprawnie udostępnionego folderu:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/07.png)

Tak skonfigurowane urządzenie jest już w pełni gotowe do użytku. Możemy wrzucać pliki, kopiować jak i udostępniać dane .. NAS może zostać schowany pod półkę. Co jakiś czas możemy się do niego zalogować, aby sprawdzać aktualizacje, lub też ustawić, aby każda aktualizacja instalowała się samoczynnie. Jest to urządzenie bezobsługowe.

Dla osób, które trochę bardziej chcą zajrzeć w ustawienia dysku sieciowego lub też sprawdzić podstawowe statystyki to w rogu „pulpitu” znajdziemy wykres, który pokaże nam obecne obciążenie:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/08.png)

A jeżeli potrzebujecie bardziej zaawansowanych statystyk to użyjcie skrótu prowadzącego do Monitor Zasobów

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/09.png)

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/10.jpg)

Coraz więcej firm tworzy swoje wewnętrzne sklepy z aplikacjami – Synology nie jest tutaj wyjątkiem. Dzięki Centrum pakietów możemy dodać do swojego NASa nowe funkcjonalności, dzięki którym nasze urządzenie uzyska drugie życie.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/11.png)

Mi najbardziej spodobał się dodatek nazwany Active Directory Server, która pozwoli stworzyć namiastkę AD opartą na Sambie. Nie jest to oczywiście pełne Active Directory, które znamy z Windows, lecz daje nam sporo możliwości. Sprawdźmy jak to wygląda w praktyce. Rozpoczynamy od instalacji pakietu wraz z zależnościami:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/12.png)

Po zainstalowaniu przechodzimy do kreatora, w którym należy ustawić hasło do AD oraz nazwę domeny:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/13.png)

No i możemy dodać nasz komputer do domeny.

Standardowa podczas dodawania do domeny musimy się zalogować kontem administratora: nazwadomeny\kontoAdministratora, moja domena nazywa się DZEJZIHOME.LOCAL więc konto Administratora to będzie: DZEJZIHOME.LOCAL\Administrator, prawda? Nie w przypadku Synology. Tutaj musiałem wykorzystać login HomeNAS\Administrator, gdzie jako HomeNas wstawiłem nazwę mojego urządzenia.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/14.png)

Dziwne, ale działa.

Największa zaleta Synology Active Directory? To, że jest namiastką do Windowsowego AD. Mamy możliwość używania profili mobilnych. Dzięki temu użytkownicy nie korzystają z swoich dysków twardych do przechowywania danych, a równocześnie te dane są bezpieczne dzięki kilkom dyskom twardym w naszym urządzeniu. Dzięki temu dodatkowi jesteśmy nawet w stanie wymusić na użytkownikach odpowiednie reguły haseł.

Kolejnym dodatkiem na który chciałem zwrócić uwagę jest Download Station. Oprócz tego, że może służyć do mniej legalnych celów to ja go wykorzystałem akurat do pobierania obrazów bezpośrednio na specjalnego katalogu. Owszem, mogłem to zrobić z poziomu, zapisując do mojego komputera albo do podmapowanego folderu, ale… Właśnie w taki oto sposób staram się trzymać porządek.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/15.png)

Gdybyśmy jednak chcieli bawić się w dodatkowe backupy naszych użytkowników to polecam użyć dodatek Active Backup for Business. Pozwoli on nam na robienie kopii zapasowej jak i zarządzanie nimi. Pakiety instalacyjne są do ściągnięcia w pliku MSI, dzięki czemu bardzo łatwo wdrożymy je za pomocą Intune lub SCCM. Dzięki kreatorowi mamy możliwość wyboru jakie dane mają być chronione. Wybieramy odpowiednie foldery. Cała obsługa kreatora jest bardzo łatwa, a przywracanie – jeszcze łatwiejsze.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/16.png)

Gdyby ktoś z was nie używał OneDrive do obsługi plików to dzięki Active Backup mamy również opcje wersjonowania plików, dzięki czemu jesteśmy w stanie wrócić do wersji tego samego pliku z kilku dni wcześniej. Tak w razie bezpieczeństwa dla naszych użytkowników.

Dostęp do naszych danych jest ważny w każdym momencie. Zarówno z poziomu telefonu komórkowego jak i komputera. Jeżeli nie mamy wystawionego VPNa do naszego domu lub firmy to posiadając urządzenie Synology nie będziemy mieli z tym żadnego problemu. Wystarczy tylko użyć funkcji nazwanej QuickConnect. Pozwala ona na połączenie z dowolnego miejsca na świecie do naszego urządzenia za pomocą jednego adresu z początkiem: http://quickconnect.to/naszanazwausera Dzięki niej mamy dostęp do zasobów przez panel webowy dokładnie w taki sam sposób jak byśmy byli podłączeni do domowej sieci.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/17.jpg)

Synology jak to Synology – nie próżnuje i mamy dostęp również do sporej ilości aplikacji na telefonach, przez co  nasze dane są dostępne również z poziomu aplikacji na Androida jak i iOS.

Jeżeli jednak nie wystawimy urządzenia przez funkcję QuickConnect a poprzez adres IP oraz naszą domenę to dzięki zintegrowaniu systemu z Let’s Encrypt jest możliwość wygenerowania bezpłatnego certyfikatu SSL. Nie zabrakło również możliwości zaimportowania własnego certyfikatu.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/18.png)

Mógłbym bardzo dużo pisać o dodatkach dostępnych w sklepie Synology, bo jest ich naprawdę sporo. Wielki plus dla producenta, że tak pozwala modyfikować jak i rozbudowywać możliwości własnego systemu.

Możliwość konfiguracji jest sporo, podstawowe opcje prezentują się tak:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/19.png)

Zaawansowane natomiast tak:

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/20.png)

Biorąc pod uwagę, że już wcześniej miałem do czynienia z firmą Synology – nie zawiodłem się na niej poprzednim razem jak i teraz. Jeżeli chodzi o system, jego możliwość rozbudowy, konfiguracji, łatwość obsługi powodują, że jest to zakup dla użytkowników domowych, małych firm jak i tych dużo większych.

Dodatki, które są dostępne w sklepie pozwolą nam na wprowadzenie Active Directory w momencie, gdy nie chcemy stawiać tejże usługi na serwerach Windowsa. Możemy zainstalować Docker, aby emulować obrazy systemu. Nie spotkałem się z usługą, której nie mogłem zainstalować poprzez wbudowany sklep.

![[PL] Synology DS918+ NAS do domu jak i małej firmy](/assets/images/posts/synology-ds918-nas-do-domu-jak-i-malej-firmy/20.jpg)

Wydajnościowo urządzenie mnie nie zawiodło. Pozwoliło odtwarzać filmy bezpośrednio z dysku, kopiować w międzyczasie obraz systemu i gdzieś w tle ściągać kolejny.. Dwa porty LAN o przepustowości 1Gb/s, które możemy ustawić w przeróżnych trybach, możliwość podłączenia adaptera Wi-Fi, użycie dysków m.2 jako cache i 4 dysków jako pamięć masowa…A nawet gdyby zabrakło nam wolnego miejsca to zawsze możemy podłączyć dodatkowe dyski za pomocą szybkich portów USB 3.0.

Cenowo urządzenie do domu wychodzi trochę drogo, ponieważ musimy wydać na samo urządzenie około 2500 zł, dla firmy to nie będzie duży wydatek. Jeżeli doliczymy do tego jeszcze koszt dysków, to… Wychodzi sporo. Jednak patrząc na ceny urządzeń innych producentów, wychodzi standardowa kwota za urządzenie tego typu. Po prostu trzeba się przyzwyczaić, że urządzenie musi tyle kosztować.

A warto wydać te pieniądze.

Gdybym miał się skusić, to jednak w moim rączkach by wylądowało urządzenie z miejscem na dwa dyski, bo nic więcej nie potrzebuję i w zupełności wystarcza na domowe zastosowania.
