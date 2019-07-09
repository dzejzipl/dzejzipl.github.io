---
title: "[PL] „Microsoft Intune - część pierwsza"
categories:
    - Intune
tags:
    - Intune
    - Wprowadzenie
    - PL post
---
![„Microsoft Intune - część pierwsza"](/assets/images/top_images/IntuneTOP.png)Seria ta będzie swoistym wprowadzeniem w świat Intune jak i całego pakietu Microsoft 365.  

Cóż, trzeba w końcu to poczynić i napisać wszystko od podstaw, bo jednak od poprzednich wpisów człowiek się sporo nauczył.

Chciałbym specjalnie dla Was poruszyć konfigurację tej usługi dla celów firmowych. W jaki sposób móc zarządzać urządzeniami, wrzucać aplikacje, wdrażać polityki i ogólnie - dobrze się bawić powoli rozwijając swoją wiedzę.

Sam nie jestem w tym mistrzem, ale.. Uczę się. Więc do boju!
## Czego się spodziewać w części pierwszej?

W części pierwszej poruszmy czego potrzebujemy, aby móc używać Intune, jakie są różnice pomiędzy licencjami i jakie są inne wymagania, by móc wprowadzić Intune jako MDM w swojej organizacji.

### Licencjonowanie

Aby móc używać Intune w swojej organizacji potrzebujemy odpowiedniej licencji. Nie jest tak, że kupimy sobie Office 365 E3 i mamy wszystko. Niestety, przy kupowaniu licencji trzeba dosyć mocno rozważnie czytać to, co otrzymujemy oraz tego, co będziemy musieli dokupić.

Obecnie licencja Intune dostępna jest tylko w:

* Enterprise Mobility + Security E3
* Enterprise Mobility + Security E5
* Microsoft 365 E3
* Microsoft 365 E5
* Microsoft 365 F1
* Microsoft 365 Business
* Oraz jako oddzielna licencja Intune oczywiście

Do wyboru mamy również dla sektora edukacji, czyli:

* Microsoft 365 Education A1
* Microsoft 365 Education A3
* Microsoft 365 Education A5

Nigdy nie pracowałem z wersjami edukacyjnymi, dlatego też nie będę ich opisywał, jednak mam to na "kiedyś" w planach.

#### Co kupić?

Jeżeli chodzi o licencje dla małych firm to obecnie najbardziej opłaca się kupić Microsoft 365, ponieważ mamy tam wszystko co jest wymagane do pracy. Począwszy od poczty, po komunikację, bezpieczeństwo, Intune oraz możliwość aktualizacji do Windows 10 Enterprise. Możemy również kupować oddzielnie licencje na każdą usługę, ale może spowodować to, że powoli zrobi się tam bałagan nie do ogarnięcia.

#### Ceny

Koszt wdrożenia oprogramowania Microsoftu w naszej firmie - jest całkiem spory szczególnie jeżeli zaczynamy od samego początku. Dla przykładu, polecana przeze mnie licencja na Microsoft 365 E3 kosztuje około 140 zł brutto. Za **JEDNEGO** użytkownika. Mnożąc to przez 12 miesięcy razy ilość użytkowników wychodzą gigantyczne kwoty. Ale cóż - coś za coś i dzięki wydaniu tych pieniędzy mamy dostęp do wszystkich najnowszych funkcji.

Ostatnia informacja o cenach - pytajcie u różnych dostawców. Jeden powie, że chce za to 140 zł, a drugi się spyta o liczbę licencji, którą chciecie kupić i cena nagle spadnie do 120 zł. Warto negocjować.

### Dodatkowe licencje

Ten akapit przyda Ci się drogi czytelniku tylko w momencie, jeżeli kupujesz oddzielnie licencje na różne produkty. Dla przykładu - jeżeli masz już kupione licencje Office 365 w wersji E3, nie oznacza to, że będziesz mógł robić wszystko to, co będę tutaj opisywał.

Najlepiej by było, aby po prostu nasi testowi użytkownicy mieli licencje Enterprise + Mobility Suite w wersji E3, która już w sobie zawiera Azure AD Premium jak i Intune. Patrz akapit wyżej - może lepiej dla testow będzie kupić EMS + Office 365?

### Azure AD

Intune to nie wszystko, jakąś część poradników będziemy wykonywać za pomocą Azure Active Directory. Czym jest ta usługa? Jest to nowa wersja Active Directory, która działa na serwerach Azure, bez lokalnego serwera, dzięki czemu cała toższamość naszej organizacji jest trzymana w chmurze. Jest to swoisty katalog, ale niestety jeszcze bez wielu funkcji, które mamy w on-premise Active Directory.

Oczywiście mamy możliwość synchronizacji naszego AAD z lokalnym AD, co będziemy czynić w celu uzyskania dodatkowych funkcjonalności.

## Pokrótce już wiecie wszystko co na początek jest potrzebne

Więc dlaczego by nie rozpocząć zabawy?

## Rozpocznijmy zabawę!

### Konfiguracja rejestracji urządzeń

Pierwsze co musimy poczynić to umożliwić naszym wszystkim lub też określonej grupie użytkowników możliwość rejestracji urządzeń w naszej organizacji. Robimy to w ustawieniach **Azure Active Directory** > **Mobility (MDM and MAM)**, następnie wybieramy **Microsoft Intune**:

![„Microsoft Intune - część pierwsza"](/assets/images/posts/Microsoft-Intune-czesc-pierwsza/1.png)

Gdzie pod jedynką wybieramy zakres użytkowników dla MDM, a pod dwójką zakres pod MAM.

Dla testów polecam stworzyć małą grupę testowych użytkowników, a dopiero później wdrożyć Intune dla całej organizacji. Na potrzebny wstępnych artykułów, będziemy się bawić tylko MDM, natomiast MAM wpadnie na bębęn trochę później.

### Konfiguracja Brandingu

Po poprawnym skonfigurowaniu rejestracji urządzeń przez naszych użytkowników należy skonfigurować branding.

Czym jest branding? Tym, co widzimy podczas logowania się do usług w naszym tenancie. Tekstem pomocy, logotypem, tłem.

Jest to wymagane, aby móc pracować z AutoPilotem o którym opowiem później, ale ważne jest to, aby nasz końcowy użytkownik wiedział do czego się loguje oraz w jaki sposób może się skontaktować z naszym HelpDeskiem.

Rozpoczynamy od przejścia do **Azure Active Directory** > **Company Branding** oraz kliknięcia na **Configure**.  Pierwsza konfiguracja polega na dodaniu odpowiednich logotypów oraz dodaniu tekstów pomocy.

Wymagane obrazki, które musimy dodać to:

* Tło do panelu logownia o rozmiarze: 1920x1080px
* Banner o wymiarze 280x60px

Możemy również dodac kwadratowy logotyp (240x240px), który zostanie pokazany podczas enrollmentu nowych urządzeń do usługi Microsoft Intune. Używamy tutaj dwóch wersji - z jasnym tłem jak i ciemnym.

Z opcji, które możemy skonfigurować to:

* Username hint - czyli podpowiedź dla końcowego użytkownika, w jaki sposób ma wpisywać swoją nazwę użytkownika
* Sign-in page text, czyli tekst, który pojawia się podczas logowania. Może być to np. jakiś disclammer.

Możemy również wybrać kolor tła na stronie logownia, który zostanie wyświetlony w momencie, gdy obrazek się nie załadował (najczęściej w przypadku połączeń słabej jakości)

Po poprawnym dodaniu pierwszego języka możemy przystąpić do konfiguracji kolejnych, które wyświetlą się zgodnie z lokalizacją, którą ma ustawiony użytkownik w swoim systemie.

![„Microsoft Intune - część pierwsza"](/assets/images/posts/Microsoft-Intune-czesc-pierwsza/2.png)

## Co dalej?

W pierwszej części to by było na tyle, w drugiej natomiast zajmiemy się stworzeniem użytkowników, spojrzeniem jakie mamy dostępne atrybuty, jak możemy nimi zarządzać oraz zaczniemy pracować z grupami. Zarówno statycznymi jak i dynamicznymi.

Później rozpoczniemy pracę z aplikacjami.
