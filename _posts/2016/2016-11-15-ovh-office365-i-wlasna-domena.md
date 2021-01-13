---
title: "[PL] OVH, Office365 i własna domena"
categories:
    - Office
tags:
    - Office 365
    - PL Post
---
![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/top.jpg)Konfigurujemy naszą domenę dla Office 365 w OVH

Hej,
w pierwszym wpisie tej serii chciałbym przedstawić Wam w jaki sposób możecie dodać własną domenę (w moim wypadku zarejestrowaną w http://ovh.pl ) do obsługi w panelu administracyjnym Office365.

Wyjaśnienie na początek – ja swoją domenę mam w całości zaparkowaną na serwerach http://ovh.pl – i tam zarządzam wpisami DNS. Jeżeli w #ovh masz tylko wykupioną domenę, a zaparkowaną gdzie indziej – analogicznie udajesz się do swojego „usługodawcy”.

Pierwszym krokiem, który musimy wykonać będzie zalogowanie się do panelu administracyjnego Office365 danymi, które otrzymaliśmy podczas pierwszej konfiguracji usługi (dostajemy tam adres emailowy z końcówką *.onmicrosoft.com) lub takimi, które już mamy. Panel zajdziemy tu: http://portal.office.com.

Następnie wybieramy z lewego menu: Settings > Domains

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/01.png)

Wybieramy Add domain dzięki czemu otworzy nam się okno, w którym możemy wpisać nazwę domeny, której jesteśmy właścicielem. U mnie wygląda to tak:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/02.png)

Po dodaniu swojej domeny, będziemy musieli ją zweryfikować.

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/03.png)

Z dwóch dostępnych opcji weryfikacji, wybieram metodę poprzez rekord TXT. Gdyby ktoś miał problem z chęcią pokażę drugi sposób czyli poprzez rekord MX.

Kolejnym krokiem będzie zalogowanie się do panelu OVH i wybieramy swoją domenę z lewej strony.

W kolejnym oknie wybieramy zakładkę DNS Zone, klikamy button Add an entry, z kolejnych opcji – rekord TXT, bo taki wybraliśmy do weryfikacji domeny.
Uwaga: jeżeli na potrzeby Office chcemy przeznaczyć całą domenę, a później przekierować odpowiednie subdomeny lub rekordy gdzie indziej – w pole subdomeny nie wpisujemy nic. Jeżeli na potrzeby Office chcemy przekazać jakąś np. office.mojadres.pl; to zawsze w jej polu wpisujemy office.

Wrzucamy swój rekord TXT, który uzyskaliśmy ze strony Microsoftu w pole i klikamy Next. Finalny ekran powinien wyglądać w taki sposób:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/04.png)

Później na stronie Microsoftu klikamy Verify. System nas przeniesienie do kolejnego kroku nazwanego  Set up your online services. Oznacza to, że poprawnie zweryfikował własność naszej domeny. Gdy tak się nie stanie – poczekajmy 10-15 minut, czasem nawet do godziny. U mnie trwało to akurat 2 minuty.

W kroku drugim na stronie Microsoftu musimy dokonać ważnego wyboru – w jaki sposób będziemy dodawać usługę. Czy „oddajemy” całą domenę na potrzeby Microsoftu czy też chcemy robić wszystko ręcznie. Ja wybrałem zarządzanie ręczne dlatego, że sam przekierowuję subdomeny na inne serwery lub adresy IP zależnie od moich potrzeb.
Drobna uwaga: jeżeli wybierzemy pierwszą opcję – czyli przekierowanie DNSów do Microsoftu – cała konfiguracja zostanie wykonana „ręcznie” przez serwey Microsoftu i nie będziemy musieli nic zrobić prócz ustawienia 4 serwerów DNS.

Ja wybrałem opcję: I’ll manage my own DNS records. dzięki czemu mam możliwość zarządzania tą domeną – o czym wspominałem wcześniej. Klikamy Next i pokaże nam się przepiękne okienko z dziesięcioma, różnych typów rekordami do dodania. Zaczynamy od pierwszego MX, który opowiada za usługę e-mailową.

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/05.png)

Wchodzimy w edycję swojej domeny w panelu OVH > DNS Zone > Add an entry > i wypełniamy według wzoru:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/06.png)

W razie wątpliwości wytłumaczę co i jak:

Subdomain – tu wpisujemy nazwę swojej subdomeny, którą chcemy przeznaczyć na rzecz Office. Jeżeli wykorzystujemy główną domene tak jak ja – nie wpisujemy niczego.
TTL – zostawiamy domyślny, jest zgodny z wymaganiami MSu.
Priority – tu wpisujemy priorytet, który nadał Microsoft.
Target – najważniejsze pole – w nim wpisujemy adres, który pokazał nam Microsoft w panelu administratora. Z kropką na końcu. Tak, to jest bardzo ważne, aby ta kropka na końcu pola target się znajdowała, inaczej nie przejdzie Wam konfiguracja.
Klikamy Next > Confirm i udajemy się do kroku Add an entry aby dodać kolejny rekord…
Rekordów CNAME musimy dodać aż 6, ja pokażę tylko jeden, cała reszta analogicznie:

W panelu OVH > DNS Zone > Add an entry > Cname i uzupełniamy w taki sposób:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/07.png)

*Subdomain – jeżeli przeznaczany główną domenę, bierzemy host name z panelu Office i wklejamy go w to pole, czyli w naszym przypadku: autodiscover. Jeżeli posiadamy subdomenę: mojoffice to subdomain będzie wyglądało tak: autodiscover.mojoffice
* TTL – Default – zgodne z MS
* Target – tutaj wpisujemy to co uzyskujemy od Microsoftu z panelu Office ( Points to address or value ) z kropką na końcu! Będzie to wyglądać tak: autodiscover.outlook.com.

Next, Confirm i powtarzamy krok dla kolejnych pięciu rekordów.*

Nie będę ponownie pokazywał jak zrobić Rekord TXT, ponieważ omówiłem to podczas sprawdzania czy domena należy do nas.

Zostały nam jeszcze do dodania dwa rekordy: SRV, które odpowiadają za rekordy usługi: w tym wypadku będą odpowiadać za działanie programy Lync (Skype for Business)

Czyli po kolei: Wchodzimy w panel OVH, DNS Zone > Add entry > SRV > i po poprawnym wpisaniu powinno wyglądać to tak:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/08.png)

Po kolei tłumaczę co i jak, bo mamy tu trochę zawiłości.

Na początek wrzucam obrazek, który jest w panelu Microsoftu:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/09.png)

* Subdomain – musimy z tego zrobić ładny miks. I znów zależy czy robimy to na subdomenie lub nie.
  * Pokażę najpierw bez:
    * bierzemy usługę i dodajemy kropkę
    *bierzemy protokół
    * finalnie wygląda to tak: _sip._tls
  * Wersja z subdomeną ( mojoffice )
    * bierzemy usługę i dodajemy kropkę
    * bierzemy protokół i dodajemy kropkę
    * wpisujemy nazwę swojej subdomeny, czyli np. mojoffice
    * finalnie to wygląda tak: _sip._tls.mojoffice
* TTL – znów zostawiamy bez zmian
* Priority : wpisujemy priorytet, który jest wpisany w panelu Office
* Weight – tak samo
* Port – dosyć ważna rzecz, musi się zgadzać z tym co w panelu Office
* Target – również jest wypisany w panelu Office. I znów dodajemy na końcu kropkę!
  
Klikamy Next > Confirm i w panelu OVH mamy wszystko. Przechodzimy do panelu Office i klikamy piękny, duży przycisk: Verify i czekamy….
Jeżeli zrobiliśmy wszystko poprawnie, zostaniemy przekierowani do kolejnego okienka i zostanie nam wyświetlony taki komunikat:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/10.png)

Jeżeli zrobiliśmy jakiś błąd, wyskoczy nam podsumowanie wszystkich rekordów. Znajdźmy ten na czerwono i zobaczmy gdzie zrobiliśmy błąd. Następnie poprawmy go w panelu OVH.

Na sam koniec możemy ustawić domenę jako domyślną. Robimy to w sposób następujący:
Wybieramy swoją domenę w panelu Office, klikamy na nią, co spowoduje wyświetlenie okienka:

![[PL] OVH, Office365 i własna domena](/assets/images/posts/ovh-office365-i-wlasna-domena/11.png)

Klikamy: Set as default.

To wszystko!

Właśnie dodaliśmy swoją pierwszą domenę do usługi Office365. Powodzenia!