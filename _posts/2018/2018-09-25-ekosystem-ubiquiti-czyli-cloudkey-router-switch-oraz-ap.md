---
title: "[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!
"
categories:
    - Krótko
tags:
    - Krótko
    - PL Post
---

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/top.jpg)Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!

## Ekosystemy są dobre

Pokazał to Apple zamykając się na niemożność dostarczania swoich rozwiązań na urządzenia innych producentów.

Idea ta sprawdziła się bardzo dobrze i do teraz użytkownicy systemów spod znaku jabłuszka mogą pracować na spójnym oprogramowaniu. Tę samą drogę obrał producent sprzętu sieciowego – Ubiquiti, produkując, swoje urządzenia dla konsumentów domowych, małych i dużo większych firm. W ich ofercie znajdziemy wiele urządzeń, które swoim zastosowaniem pokryją najbardziej wymagające firmy.

## Dlaczego Ubiquiti?

Ostatnimi czasy udało mi się nawiązać współpracę z firmą Senetic, która dostarczyła mi nie jednego, ale czterech bohaterów dzisiejszej recenzji:

* Ubiquiti UniFi Security Gateway, model USG
* Ubiquiti UniFi Switch, model US-8-60W
* Ubiquiti UniFi AP AC PRO, model UAP-AC-PRO
* Ubiquiti UniFi Controller Cloud Key, model UC-CK

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/01.jpg)

Ten tekst nie będzie konkretną recenzją każdego urządzenia po kolei. Ten tekst będzie opisem mojego doświadczenia w początkowej konfiguracji, używaniu, jak i dopieszczaniu działania mojej domowej sieci. Nie znajdziecie tutaj setek testów przepustowości pomiędzy danymi portami. Nie znajdziecie tutaj czystych danych technicznych zanalizowanych na setki sposobów – jeżeli będą, to tylko po to, aby wiedzieć, jaki model urządzenia testowałem.

Z oprogramowaniem UniFi pierwszy raz miałem do czynienia w poprzedniej pracy, gdzie stworzyłem sieć opartą na kilku urządzeniach UAP-LR, które umożliwiały komunikację tylko na częstotliwości 2,4GHz. Pamiętam doskonale, jak przemierzałem Internet w poszukiwaniu urządzeń, które obsłużą dwa piętra i kilkadziesiąt podłączonych klientów. Począwszy od komputerów, po tablety i telefony komórkowe, a kończąc na RaspberryPi i kamerach. Postanowiłem zaufać firmie Ubiquiti.

Zachwyciło mnie, że cała konfiguracja przebiega w kilku krokach. To, że jestem w stanie wdrożyć nową testową sieć na wszystkich AP albo tylko kilku wybranych przeze mnie. Podgląd statystyk na bieżąco? Nie ma żadnego problemu. Ustawienie ograniczenia, aby podany użytkownik nie miał transferu większego niż 3Mb/s? Nie widziałem wad w tym systemie, a używałem go z powodzeniem przez prawie 3,5 roku. Widziałem, w jaki sposób rozwija się cały system, testowałem nowe zmiany i nowe wersje oprogramowania. Później producent wprowadzał nowości na rynek, których nie miałem już możliwości przetestować i na tym skończyła się moja przygoda. Po roku jednak postanowiłem do niej wrócić.

UniFi do swojej pracy potrzebuje kontrolera, który możemy zainstalować na systemach Linux, Windows oraz macOS dzięki temu, że jest on oparty na Javie.

W przypadku biura znalezienie jednego komputera, na którym zainstalujemy kontroler nie powinno być problemem. Zawsze możemy do tego użyć wirtualnej maszyny na jednym z serwerów lub dowolnego komputera, który może stać pod biurkiem lub w serwerowni. W domu znalezienie wolnego urządzenia, które będzie chodziło całą dobę może być bardziej problematyczne. Oczywiście, że możemy do tego użyć RaspberryPI. Jednak jest to dodatkowa elektronika, o której musimy pamiętać i o nią dbać. Aktualizacje systemowe, oprogramowania, kwestie zabezpieczeń… Nie zawsze jest na to czas. Ten sprzęt ma po prostu działać poprawnie. Dlatego chciałbym wam przedstawić

## Bohatera numer jeden: UniFi Cloud Key

Cloud Key jest niewielkim urządzeniem, które jest sercem całego systemu. Jest po prostu kontrolerem, który wpinamy bezpośrednio do naszego switcha i zasilamy technologią PoE lub za pomocą kabla microUSB. Pierwszą konfigurację przeprowadzamy za pomocą przeglądarki. Jedyne co na początku potrzebujemy, to adres IP naszego nowego kontrolera. Znajdziemy go na serwerze DHCP lub wyszukamy za pomocą dodatku Ubiquiti Device Discovery Tool, który znajdziemy w sklepie Google Web Store. Po zalogowaniu możemy przystąpić do konfiguracji urządzenia lub naszego kontrolera.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/02.jpg)

Inicjalizacja jest prosta i poradzi sobie z nią każdy bez żadnego problemu. Polega na przejściu kilku kroków, w których odpowiemy między innymi na pytania:

* kraj oraz strefę czasową
* dodanie naszych urządzeń, które są już wpięte do sieci
* wstępne skonfigurowanie sieci Wi-Fi
* wstawienie nazwy administratora dla kontrolera, jak i urządzeń
* połączenie z kontem w serwisie ubnt.com, który da nam zdalny dostęp do urządzeń.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/03.jpg)

Po tak krótkiej konfiguracji nasze urządzenie jest gotowe do pracy.

UniFi CloudKey posiada także swoje opcje konfiguracyjne. W pierwszej zakładce zobaczymy przydatne informacje o czasie pracy, zajętości miejsca, MAC adresie i wersji oprogramowania. W części Configuration możemy skonfigurować adresację IP, nazwę hosta oraz strefę czasową. W ostatniej zakładce znajdziemy opcję pozwalającą na aktualizację firmware kontrolera, zmianę loginu, jak i hasła oraz zrobienie backupów.

Urządzenie możemy kupić w Senetic za kwotę około 350 zł, natomiast w pudełku prócz urządzenia znajdziemy kabel LAN, kartę microSD o wielkości 8GB oraz instrukcję szybkiej konfiguracji.

## Bohater numer dwa: UniFi Security Gateway, model USG

Po podstawowym skonfigurowaniu CloudKey przychodzi kolej na router. Wybór padł na UniFi Security Gateway, w skrócie zwany USG z 4 portami. W ofercie znajdziecie modele z większą liczbą portów.

U mnie fizyczna konfiguracja urządzenia ograniczyła się do wpięcia dwóch kabli RJ-45 oraz zasilania.

Do portu oznaczonego WAN 1 wpinamy nasze łącze operatorskie. Ja dostarczyłem internet od UPC o przepustowości 120Mb/s z uploadem 10Mb/s.

W port LAN 1 wpinany switcha lub bezpośrednio inne urządzenie. Na tym porcie domyślnie jest skonfigurowany DHCP z sieci 192.168.1.0/24, natomiast do USG możemy się dostać, wpisując adres 192.168.1.1.

Do portu opisanego WAN 2 / LAN 2 możemy dostarczyć drugie łącze, które przejmie ruch w przypadku awarii głównego albo kolejnego urządzenia.

W USG znajdziemy również złącze Console, które pozwoli nam na konfigurację za pomocą CLI, czyli linii komend. Nie wykorzystałem go ze względu na to, że czasem jestem zwolennikiem interfejsu graficznego.

Blisko portów znajdziemy przycisk „reset”, który jak sama nazwa wskazuje służy do resetowania urządzenia w przypadku utracenia dostępu do niego.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/04.jpg)

Jeżeli chodzi o wygląd urządzenia, to jest ono niewielkie, wprost powiedziałbym skromne. Na górze prócz logotypu posiada także podświetlenie, które pokazuje nam aktualny status.

Boki urządzenia są pokryte metalową siatką, która służy do odprowadzania ciepła. Dzięki temu w USG nie ma zamontowanych wentylatorów i jest to urządzenie bezgłośne. Z tyłu znajdziemy ładnie wkomponowane złącze zasilania na 12V.

W pudełku oprócz urządzenia znajdują się zasilacz, kabel zasilający „koniczynka”, kołki do montażu na ścianie oraz instrukcja konfiguracji. Gdyby ktoś z was zastanawiał się dlaczego na ścianę – śpieszę z odpowiedzią, że to urządzenie jest po prostu ładne i bardzo ładnie by się komponowało zawieszone w widocznym miejscu.

Po podłączeniu łącza od operatora i naszego urządzenia wszystko z domysłu powinno już działać, jeżeli operator dostarcza nam adresację po DHCP. Jeżeli nie, to musimy dokonać niezbędnej konfiguracji w panelu.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/05.jpg)

Sam router nie zachwyca ceną – około 470 zł w Senetic, nie zachęca do kupna, prawda? Jako domowy użytkownik za taką kwotę miałbym już w tej cenie router z 4 portami dla użytkownika, jak i punkt Wi-Fi na 5GHz, ale nie stawiajmy wyroku tak szybko.

## Bohater numer trzy: UniFi Switch US-8-60W

Cóż nam z dwóch portów dostępnych w USG, skoro w domu mam minimum dwa urządzenia, które są wpięte do internetu kablem oraz kilka innych, które komunikują się po Wi-Fi? Priorytetem pod względem połączenia kablowego są konsola i komputer stacjonarny. Do tego zdarzają się serwery lub inne komputery, które służą swoim celom – najczęściej testowanie deploymentów. Do rozbudowy mojej sieci posłużył mi US-8-60W, który kosztuje ponad 600 zł oraz posiada 8 portów dostępnych dla użytkownika.

Switch, tak jak router, jest bezgłośny, co zawdzięcza swojej masywnej obudowie, która oddaje ciepło przez otwory w bocznych ściankach. Z przodu znajdziemy osiem portów, z których cztery są w standardzie PoE (Power over Ethernet) i pozwolą nam zasilić inne urządzenia, które obsługują taką technologię. Na górze widzimy szereg diod, które sygnalizują pracę. Na tyle obudowy znajduje się wejście do zasilacza 48V oraz przycisk resetu przywracający urządzenie do ustawień domyślnych.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/06.jpg)

US-8-60W nagrzewa się bardzo mocno. Metalowa obudowa była bardzo ciepła podczas użytkowania, a miałem podłączone tylko dwa urządzenia, które były zasilane za pomocą PoE. Zastanawiam się, jak długo to urządzenie może wytrzymać w przypadku zasilania czterech punktów Wi-Fi i braku aktywnego chłodzenia za pomocą wentylatorów.

Rodzina Switchy UniFi nie ogranicza się oczywiście tylko do tego jednego modelu. Znajdziemy tam również urządzenia 8-portowe w wersji bez PoE oraz wersję, która będzie nam w stanie dostarczyć 150W zamiast 60W, które daje nam ten model. Co w przypadku, gdy potrzebujemy wykorzystać więcej niż 8 portów? Polecam sprawdzić wersje 16, 24 albo nawet 48-portowe. Dla każdego coś dobrego. Zarówno z PoE lub bez. Zależy od potrzeby zastosowania i zasobności portfela.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/07.jpg)

US-8-60W posiada dokładnie takie samo dodatkowe wyposażenie jak USG, czyli kołki do montażu na ścianę, zasilacz, kabel zasilający „koniczynka” oraz instrukcję szybkiej instalacji w języku angielskim.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/08.jpg)

## Bohater numer cztery: UniFi AP AC PRO

Internet już jest, kilka urządzeń mogę podłączyć, ale nadal nie mogę używać Alexy albo inteligentnej żarówki i drukarki, ponieważ używają połączenia Wi-Fi. Do tego celu użyłem punktu dostępowego AP AC PRO, który był zasilany za pomocą PoE dzięki bohaterowi numer trzy. Możemy również kupić wersję, która ma w pudełku adapter do zasilania, poprowadzi nam zasilanie poprzez kabel LAN jeżeli nie mamy urządzenia wspierającego PoE.

Tak jak w przypadku switchy, rodzina Acess Point’ów jest również całkiem spora. Od różnych przepustowości po różne zastosowania i środowiska pracy. Ja wybrałem punkt z jednymi z najwyższych przepustowości, który działał zarówno na falach 2,4GHz z prędkością do 450Mbsps oraz 5GHz z prędkością do 1300Mbps.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/09.jpg)

Powiem wam tylko, że wykorzystanie takich prędkości w domu jest praktycznie nierealne. Co innego w firmie, gdzie podłączonych urządzeń jest kilkanaście. W takim wypadku kupno tak drogiego urządzania ma sens. Po testach stwierdziłem, że o wiele lepiej w moich domowych zastosowaniach sprawdziłby się podstawowy model, czyli UAP-AC-Lite, który oferuje prędkości do 300Mbps oraz do 876Mbps w nowszym standardzie.

Produkty różnią się także ilością zamontowanych anten – czasem są to dwie anteny na każdą częstotliwość, czasem trzy.

Jeżeli chodzi o model, czyli AP AC PRO, który wpadł w moje ręce, to posiadał dwa porty RJ45, każdy o prędkości 1Gb/s, natomiast modele niższe posiadają jeden port o takiej samej przepustowości oraz przycisk pozwalający na reset urządzenia.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/10.jpg)

W kartonie znajdziemy cztery śruby, uchwyty montażowe, poradnik szybkiej instalacji i sam Access Point. W niektórych modelach znajdzie się również adapter PoE.

Punkty są w taki sposób skonstruowane, że mogą być powieszone zarówno na suficie, jak i na ścianie. Mają bardzo uniwersalny, przez co nierzucający się w oczy wygląd przypominający spodek UFO w białym kolorze. Na górze znajdziemy logotyp oraz diody LED, które poprzez odpowiedni kolor sygnalizują nam pracę urządzenia.

Początkowo wybranie urządzenia może wydawać się ciężkie. Wszystko zależy od potrzeb, które posiadamy. Do małego mieszkania kupimy UAP AC Lite, jeżeli potrzebujemy dużo większych prędkości zainwestujemy w testowany przeze mnie model UAP AC Pro, a jeżeli mamy do pokrycia sporą powierzchnię, wybierzemy UAP AC LR, który posiada mocniejsze anteny. Dla osiągnięcia największych prędkości wybierzemy UAP HD, który na 5GHz może osiągnąć prędkość do 1733MBbps.

Plusem jest natomiast to, że wszystkimi punktami zarządzamy z jednego miejsca.

## Wszyscy bohaterowie na raz, czyli ekosystem UniFi

Na początku wspomniałem, że doceniam ekosystem Apple. Wszystko jest z sobą spójne i ze sobą współgra. Tak samo firma Ubiquiti postanowiła stworzyć system, który pozwoli na zarządzanie wszystkimi urządzeniami z serii UniFi.

Pierwszy etap instalacji polegał na konfiguracji kontrolera na urządzeniu CloudKey, co opisałem w jednym z pierwszych akapitów.

Drugi etap w moich testach polegał na spięciu wszystkich urządzeń w jedną całość. Począwszy od poprawnego połączenia przewodami po zaadaptowaniu urządzeń i ich odpowiednim nazwaniu.

Tak właściwie w tym etapie wszystkie nasze urządzenia już pracują poprawnie i moglibyśmy o nich zapomnieć. Mamy dostęp do sieci po kablu, jak i po Wi-Fi. Ale nie po to kupuje się zaawansowany zestaw, aby nie skorzystać z jego dobroci, prawda?

## Statystyki

Statystyki w życiu każdego administratora są bardzo ważne. Na ich podstawie jest w stanie zareagować na obciążenia sieci i przygotować plany rozbudowy.

Możliwe, że w swoim IT życiu widziałem mało, ale nigdy nie widziałem większej ilości statystyk niżeli UniFi było mi w stanie dostarczyć. Począwszy od liczby podłączonych urządzeń, które są pod kontrolą naszego kontrolera, po podpiętych klientów, jak i ilość danych, które zostały przesłane przez naszych użytkowników.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/11.png)

Nie zapominajmy również o dokładnych informacjach, o której godzinie mieliśmy największe obciążenie Internetu i jakie były czasy dostępów.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/12.png)

Posiadając więcej niż jedną sieć Wi-Fi możemy podejrzeć sobie statystyki związane z ruchem na falach radiowych:

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/13.png)

A co jeżeli chcemy przejrzeć statystyki z podziałem na różne kategorie? Producent stworzył predefiniowane filtry, które muszę przyznać, że się sprawdzają całkiem porządnie. Sprawdźcie zresztą sami:

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/14.png)

Dla bardziej wymagających użytkowników mamy możliwość podejrzenia jeszcze dokładniejszych statystyk danej kategorii wraz z podziałem na hosty:

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/15.png)

Same statystyki pozwalające nam kontrolować naszych użytkowników to nie wszystko. Ważniejsze dla administratorów są informacje o obciążeniu urządzenia.

Jak widzieliście na powyższych zrzutach ekranu, takie statystyki są bardzo rozbudowane, a gdyby podobne otrzymać o obciążeniu routera podczas pracy?

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/16.png)

Informacje możemy podejrzeć z danego zakresu czasu, który jest konfigurowalny i zależny od retencji danych, które ustawimy w opcjach. Możemy trzymać tydzień statystyk, a możemy mieć je także od czasu pierwszej konfiguracji.

Posiadając w domu switcha US-8-60W, miałem możliwość podejrzenia informacji o portach i ich przepustowości:

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/17.png)

Jak widzicie – możemy wybrać, aby wyświetlało się kilka urządzeń lub jedno – wszystko zależy od naszych potrzeb.

Krótko mówiąc – możliwości tych urządzeń, jeżeli chodzi o raportowania, są niesamowite – a jeszcze bardzo wielu rzeczy nie opisałem!

## Mapa sieci

Posiadając infrastrukturę opartą tylko na urządzenia UBNT, mamy możliwość stworzenia mapy sieci, która może być bardzo przydatna w momencie szukania awarii, bo dzięki temu wiemy, który host/urządzenie nie odpowiada.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/18.png)

Funkcja bardzo przydatna – nie każdy ma oprogramowanie, w którym na bieżąco spisuje ustawienia swojej sieci.

## Notyfikacje oraz alerty

UniFi posiada bardzo zaawansowane funkcje pozwalające na informowanie nas o bardzo wielu eventach, które dzieją się na naszym kontrolerze. Możemy wybierać pomiędzy alertami na stronie lub powiadomieniami e-mail, zarówno o akcjach związanych z naszymi urządzeniami, jak i informacjami, że do sieci podłączył się nowy użytkownik. Nie ma kontaktu z urządzeniem? Za chwilę dostaniesz o tym wiadomość e-mail. Zalogował się administrator? Wystarczy ustawić odpowiednie powiadomienie.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/19.png)

Cały ekosystem możemy również monitorować za pomocą SNMP w trzech wersjach, dzięki czemu z łatwością podłączymy urządzenia np. pod cacti.

## Cykliczne testy prędkości

W opcjach mamy możliwość ustawienia cyklicznych testów prędkości łącza dostarczanego przez operatora. Dla przykładu ustawienie codziennego testu da nam pogląd na to, czy otrzymujemy taką przepustowość, którą zamówiliśmy, bo jak by nie patrzeć, operatorzy często nas ograniczają.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/20.png)

Oczywiście później jesteśmy w stanie wygenerować sobie raport z takich testów i zobaczyć jak nasza sieć działała.

## Konfiguracja portów

VLANy wszędzie. W przypadku firm sprawdzi się to idealnie. VLAN dla serwerów, VLAN dla gniazdek RJ45, dla określonej grupy pracowników z grupy wysokiego ryzyka…. Wszystko zależy od naszej inwencji twórczej. Szczęście takie, że producenci utworzyli pełną możliwość tworzenia nowych sieci w panelu, gdzie możemy ustawić wiele opcji konfiguracyjnych, które powinny wystarczyć nawet najbardziej wymagającym użytkownikom. A samo przypisanie właściwego portu to dwa kliknięcia!

## Dodatkowe sieci Wi-Fi

Hipotetyczna sytuacja: Mamy 3 punkty dostępowe na terenie naszej firmy. Dwa mają być wewnątrz z siecią firmową, ale jeden na zewnątrz – ma być tylko z siecią, która jest odseparowana od pozostałych urządzeń. I da się to zrobić bez problemu – wystarczy utworzyć nową grupę sieci Wi-Fi, którą przypiszemy tylko do danego AP i będzie to współgrało z całym naszym systemem.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/21.png)

## Sieć gościnna

A może zamiast powyższej sytuacji chcecie mieć sieć gościnną w całym budynku? UniFi wspiera tworzenie sieci gościnnych, które są w pełni odcięte od wewnętrznych zasobów. Dzięki możliwości zarządzania taką siecią ustawimy branding, informacje, sposoby logowania (Google+, Facebook oraz inne!), jednorazowe vouchery, hasła… Co tylko chcecie.

## PoE – rzecz przydatna?

Czy PoE może być przydatne w małych domowych sieciach? Oczywiście, że tak. Najczęściej jest tak, że w nowo budowanych lub remontowanych domach prowadzimy określoną ilość kabli LAN do pomieszczenia, aby mieć wolne gniazdko na przyszłe użytkowanie. W przypadku gdybyśmy chcieli zamontować w tym miejscu dodatkowy punkt Wi-Fi musimy użyć dodatkowego zasilacza, a dzięki tej technologii zasilanie i internet dostarczymy jednym okablowaniem, które już istnieje. A do takiego rozwiązania idealnie sprawdzą się punkty ścienne typu: UniFi AP In-Wall. W testowanym przeze mnie switchu dostępne miałem cztery porty, które mogły przekazać maksymalnie 60W zasilania. W zupełności wystarczające, aby zasilić cztery punkty AP w najbardziej rozbudowanej wersji.

## Zarządzanie firmware

Dbanie o bezpieczeństwo sieci nie odbędzie się tylko na poziomie blokady niepotrzebnych usług oraz portów. Często wychodzą tak zwane 0-Day’e, które producenci muszą szybko naprawiać. A czym są te 0-Day’e? Są to luki odkryte przez niezależne osoby, o których informacje zostały przekazane producentom w celu naprawy. Twórca oprogramowania ma określony czas na reakcję. A jak najszybciej zareagować na taką dziurę? Wypuszczając aktualizację swojego oprogramowania. Akurat w przypadku UniFi jest to bardzo dobrze rozwiązane, ponieważ możemy ustalić, aby wszelkie aktualizacje instalowały się same w określonym czasie (np. jak nikogo nie ma w firmie). Możemy dostać informację o tym, że dane urządzenie posiada nowszą wersję i sami zdecydować, kiedy je uaktualnimy. Najważniejsze dla mnie jest to, że wszystko robimy z poziomu właśnie jednego portalu, gdzie zarządzamy urządzeniami i informacja o nowej wersji oprogramowania jest doskonale widoczna w panelu.

## Bezpieczeństwo naszej sieci

A propos bezpieczeństwa i blokowania portów – ekosystem sam w sobie posiada bardzo zaawansowane opcje do zarządzania regułami bezpieczeństwa. Nie chcemy, aby port 8080 dostępny był dla sieci gościnnej, ale dla naszej już tak? Da się to zrobić. A może nie chcemy, aby ruch przychodzący na powyższy port był zablokowany, ale wychodzący już nie? Da się to zrobić od ręki. Kilkoma kliknięciami. GUI jest bardzo rozbudowane.

!["[PL] Ekosystem Ubiquiti – czyli CloudKey, Router, Switch oraz AP!"](/assets/images/posts/2018/ekosystem-ubiquiti-czyli-cloudkey-router-switch-oraz-ap/22.png)

## GUI

Większość administratorów powie, że GUI (graficzny interfejs użytkownika) jest zbędny. Oczywiście, że sporo rzeczy można o wiele szybciej „ogarnąć” komendami – w końcu automatyzacja jest fajna. Ale w przypadku UniFi wyklikiwanie wszystkich funkcji jest po prostu szybkie i przyjemne. Większość funkcji, które wykorzystujemy, uzyskujemy za pomocą kilku kliknięć. Widać, że zespół przyłożył się do stworzenia tego oprogramowania.

## Zdalny dostęp do naszego ekosystemu

Posiadając system w firmie UniFi zawsze istnieje szansa, że coś może nie działać. W końcu jest to tylko oprogramowanie. Nie zawsze jesteśmy też w biurze, aby móc zareagować. Dlatego posiadając CloudKey mamy dostęp do panelu UniFi z dowolnego miejsca na świecie. Wszystko opiera się tylko na stworzeniu konta w serwisie ubnt.com i dodaniu go w na naszym kontrolerze. Wszystko działa w taki sposób, jakbyśmy pracowali lokalnie… Jedyny moment, w którym to rozwiązanie nas nie uratuje to czas, w którym mamy przerwę świadczenia usług przez naszego providera.

## Możliwość rozbudowy

Co w przypadku, gdy nasza mała firma staje się większą firmą i zatrudniamy dodatkowo 20 osób? Co w przypadku, gdy posiadamy określoną ilość sprzętu, ale się przeprowadzamy i musimy rozbudować naszą infrastrukturę? Czy musimy kupować wszystko od nowa? Absolutnie nie. UniFi jest systemem skalowalnym – obsłuży bardzo wiele urządzeń w naszej sieci. Cała rozbudowa opiera się na wpięciu do sieci nowego urządzenia, zaadaptowaniu go, nazwaniu… I nic więcej nie musimy z nim robić. Ono po prostu działa. Oczywiście możemy dokonać niezbędnych dla nas zmian typu ustawienie vlanów, portów, ale to już są opcje dla bardziej zaawansowanych użytkowników.

## Cena

Cóż, testowany przeze mnie zestaw nie był najtańszy. Całość kosztowała około 2 tysięcy brutto, czyli jak by nie patrzeć – prawie cztery razy droższy niż testowane przeze mnie routery (dla porównania TP-Linki, które testowałem kosztowały około 500 zł)

Jest to sporo – szczególnie, jeżeli mieszkamy w bloku. W przypadku domu jednorodzinnego już bym mógł się zastanowić. Powierzchnia, jak i liczba kabli, które możemy poprowadzić, sprawia, że nasza sieć robi się bardziej skomplikowana.

Nie da się ukryć – wiemy za co płacimy. Za jakość wykonania, za oprogramowanie i możliwości. Możemy kupić pojedynczy router, tak jak mam to teraz zrobione w domu, ale nie dostaniemy tych wszystkich opcji, które mamy w UniFi. Ale czy do małego mieszkania potrzebuję takich możliwości?

## Idealny dla małych firm, jak i dla wymagających pojedynczych użytkowników

Znam firmy, które używają tylko sprzętów Cisco w swoich oddziałach, ponieważ mają już wdrożone swoje systemy i to się sprawdza. Znam firmy, które pracują na Mikrotikach, jak i firmy, które mają w swoich serwerowniach sprzęty HP i Dell do obsługi sieci. A co z Ubiquiti? Czy da się zbudować funkcjonalną sieć dla kilku pięter i kilkuset urządzeń? Oczywiście, że się da. Routery, które mają DualWan w przypadku potrzeby stworzenia failover, switche z nawet 48 portami – zarówno w wersji PoE lub bez, punkty Wi-Fi, o których wam wspominałem wcześniej. A jeżeli dołączymy do tego opcję kamer i możliwości nagrywania obrazu z nich, to mamy całkiem sporą możliwość otrzymania kompletnego środowiska od jednego producenta.

Z tego co zauważyłem, w portfolio znajdziemy również produkty z serii VoIP, czyli telefonii stacjonarnej. Ostatnia aktualizacja oprogramowania jest z listopada 2016 roku, co sugeruje, że te produkty nie są już rozwijane.

## Przerost formy nad treścią?

W przypadku wyboru urządzeń do firmy – nie wahałbym się ani chwili dłużej i wiem, jaki system bym wybrał. Skalowalność, stabilność, oprogramowanie przemawia za Ubiquiti. Wymagający domowy użytkownik znajdzie również dla siebie sporo dobrego w tym systemie. A co z typowym Janem Kowalskim, który chce mieć dobrze działającą sieć w domu? W tym wypadku polecam spojrzeć w inny segment – domowy. Jest wiele dobrych routerów w cenie do 500 lub nawet 1000 zł, które oferują bardzo dużą wydajność oraz mają sporo funkcji.

Jeżeli jednak już chcecie przejść na UniFi, ale przeraża was ilość urządzeń, które musicie kupić, to może skusicie się na AmpliFi HD Home Wi-Fi Router? Postaram się go dla was zrecenzować!
