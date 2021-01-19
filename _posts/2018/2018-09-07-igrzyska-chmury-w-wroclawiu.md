---
title: "[PL] Igrzyska Chmury w Wrocławiu"
categories:
    - Other
tags:
    - Igrzyska Chmury
    - PL Post

header-img: "/assets/images/posts/2018/igrzyska-chmury-w-wroclawiu/top.jpg"
subtitle:   "[PL] Igrzyska Chmury w Wrocławiu"
---
![[PL] Igrzyska Chmury w Wrocławiu](/assets/images/posts/2018/igrzyska-chmury-w-wroclawiu/top.jpg)Igrzyska Chmury w Wrocławiu

W dniu wczorajszym wziąłem udział w Igrzyskach Chmury w Wrocławiu. Były to kwalifikacje do głównego konkursu, który odbędzie się w Warszawie – 22 września.

I powiem wam tak:

Pomimo to, że zająłem 6 miejsce – wspólnie z innym kolegą, to uwaga… Nie żałuję, że wziąłem udział.

Byłem negatywnie nastawiony do tego wydarzenia. Dlaczego ja, osoba, która na co dzień używa tylko Azure i to w małych ilościach ma konkurować z innymi osobami, które zapewne używają kilku chmur. A jeżeli ich nie używają na co dzień to na pewno wiedzą jak wyglądają takie chmury i w jaki sposób się w nich obracać.

![[PL] Igrzyska Chmury w Wrocławiu](/assets/images/posts/2018/igrzyska-chmury-w-wroclawiu/01.jpg)

Wiecie, że istnieje chmura od Orange?

Wiedziałem, że istnieją chmury od: Azure, AWS, Google Cloud, Aruba, OVH… Ale, że istnieje Orange i przyjdzie mi się na niej pracować, to nigdy bym się nie spodziewał.

Kwalifikacje odbywały się Wrocławskim Parku Technologicznym na ulicy Duńskiej 9. Typowe zagłębie korporacyjne jakich dużo, nawet z przedszkolem dla dzieci pracowników.

Organizacyjnie nie mam się tak naprawdę do czego przyczepić. Jedzenie, kawa, napoje, przekąski – wszystko zapewnione od samego początku. Listy zasilające – były! Profesjonalne nagłośnienie – było! Profesjonalne przygotowanie zadań dla zawodników – było! Muzyka w tle? Była, Britney Spears na głośnikach, co mnie zdziwiło, ale wbrew pozorom w ogóle nie przeszkadzało i przyjemnie się tego słuchało.

Podsumowując – organizacyjnie 100/10. Widać, że Chmurowisko, to porządna firma, która przykłada się do swojej pracy.

Na samym początku nie byłem przekonany, że mogę tam iść. A jeżeli się zbłaźnię i nie wykonam żadnego zadania? Jeżeli nie będę wiedział o czym będzie dane zadanie? Bałem się, że po prostu z samego początku wykonam taką akcję:

![[PL] Igrzyska Chmury w Wrocławiu](/assets/images/posts/2018/igrzyska-chmury-w-wroclawiu/02.jpg)

Oczywiście, że był stres. Oczywiście, że nie zakończyłem ani jednego zadania jako pierwszy. Oczywiście, że nie udało mi się w ogóle rozpocząć jednego zadania, bo nagle komputer postanowił odmówić mi posłuszeństwa i portal Azure nie działał na żadnej przeglądarce.

A co mi się udało? Dobrze się bawić, nauczyć się kilku rzeczy. Dowiedzieć się, że jedno zadanie można zrobić na kilku chmurach na różne sposoby.

Dowiedziałem się również jednej, ale to bardzo ważnej rzeczy. Należy bardzo dokładnie, ale to baaardzo dokładnie czytać specyfikację zadania, np. w pierwszym zadaniu od organizatorów należało stworzyć zasób, gdzie będziemy trzymać pliki i podmontować je na dwóch maszynach oraz dokonać w nim zmiany. Wydaje się bardzo proste, prawda? Wykorzystałem do tego Windows Server 2016 w dwóch kopiach, Azure File Storage i gotowe.

![[PL] Igrzyska Chmury w Wrocławiu](/assets/images/posts/2018/igrzyska-chmury-w-wroclawiu/03.jpg)

Szkoda tylko, że na początku zadania było napisane jeszcze jedno wymaganie. Do serwerów należy móc się także zalogować przez SSH. Do Windows Server mógłbym doinstalować rolę, ale na to już nie było wystarczająco dużo czasu, ponieważ wybrałem mało wydajne maszyny. Postawiłem szybko Ubuntu, jednakże tam miałem problemy z użyciem komendy mount do zdalnego zamontowania zasobów sieciowych.

No zdarza się…

![[PL] Igrzyska Chmury w Wrocławiu](/assets/images/posts/2018/igrzyska-chmury-w-wroclawiu/04.jpg)

Powiem wam kolejną rzecz. Nie znając jednej chmury jesteśmy w stanie zacząć szybko na niej pracę. Mowa tutaj o Flexible Engine od Orange. Było jedno zadanie, dosyć proste. Postawić dwa serwery w tej chmurze, load ballancer, ustawić nazwę hosta w index.html dla dwóch serwerów i zadanie wykonane. Tak jak postawienie dwóch serwerów poszło mi błyskawicznie to z load ballancerem już miałem problem. Żaden z tych serwerów nie miał publicznego adresu IP. Musiałem więc kupić dodatkowe adresy, przydzielić je serwerom, skonfigurować odpowiednio load ballancer i teoretycznie wszystko działa, prawda? Oprócz tego, że nie można było się zalogować do SSH, bo port był domyślnie zablokowany i należało zmienić reguły to… W Flexible Engine nie ma logowania poprzez: login + hasło za pomocą SSH, logujemy się kluczem publicznym.

Ktoś, kto jest obeznany w Linuxie czy serwerach na pewno takie klucze posiada. Ja niestety nie miałem i kolejne 5 minut musiałem poświęcić na naukę jak się tego używa.

Gdybym tylko przeczytał dokładnie FAQ, to mógłbym wiedzieć, że logując się do SSH kluczem publicznym, nie używam użytkownika root. Tylko specjalnego konta nazwanego cloud i nie straciłbym kolejnych 5 minut na próbę logowania się. Koniec czasu, odkładamy komputery jak krzyknął akurat w tej chwili Mirek. Ja natomiast zakończyłem na zainstalowanych dwóch Linuxach, gdzie tylko jeden miał zainstalowanego LAMPa…

Były jeszcze trzy inne zadania, między innymi:

* Serverless, czyli połączenie dwóch chmur i funkcji. Jedna ma wyzwalać drugą.
* Azure Stack – po raz pierwszy widziany na żywo! Gdzie mieliśmy postawić dwa serwery w Availability Sets i z na nich mieliśmy postawić dowolną stronę WWW i zabezpieczyć ruch w taki sposób, aby był serwery były dostępne tylko po portach 80 + 22 + 3389
* I jako trzecie – stworzenie backupu w Aruba Cloud.

Tak jak się bałem z początku wziąć w tym wydarzeniu udział, o czym już kilkakrotnie wspomniałem – to zrobiłbym to drugi raz. I trzeci. Bo uwierzcie mi, nic tak nie podnosi samooceny, jak możliwość realizacji z lepszymi osobami od nas wiedząc, że na przerwie ta osoba ci pomoże i powie jak to zrobiła i co ty mogłeś zrobić źle.

Mam nadzieję, że za rok będą znów kwalifikacje i już teraz wiem, że się na nie zgłoszę.

W tym miejscu chciałbym serdecznie pogratulować Karolowi, który „uciekł” się z lekcji języka polskiego, aby móc wygrać wrocławską eliminację i powodzenia w Warszawie!

Jeszcze większe podziękowania należą się organizatorowi – Chmurowisko oraz wszystkim partnerom, którzy dołożyli swoją cegiełkę do tego, aby takie osoby jak ja, mogły się rozwijać.
