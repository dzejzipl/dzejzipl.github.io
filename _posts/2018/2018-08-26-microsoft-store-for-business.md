---
title: "[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/microsoft-store-for-business/top.jpg"
subtitle:   "[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji"
---
![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/top.png)Automatyczna instalacja Microsoft Company Portal

W Windows 10 mamy Windows Store, z którego pobieramy wszystkie aplikacje będąc końcowym użytkownikiem. W przypadku organizacji może się to trochę nie sprawdzić, ponieważ dajemy użytkownik możliwość instalowania wszystkiego ze sklepu, a niektóre aplikacje nie powinny być w ogóle dozwolone, prawda?

Na przeciw wychodzi nam Microsoft Store for Business, którego możemy skonfigurować według podanych przez nas reguł, udostępnić tylko kilka aplikacji dla końcowych użytkowników. Wszystko jest pod naszą kontrolą.

Zaczynamy od pierwszego, ale najważniejszego kroku czyli włączenia sklepu. Udajemy się na stronę: [https://businessstore.microsoft.com/] logujemy się kontem Global Administratora, akceptujemy warunki, które zostają nam narzucone oraz  wybieramy zakładkę Manage > Settings > Distribute i znajdujemy część: Management tools. Uaktywniamy Microsoft Intune oraz Microsoft Intune Enrollment klikając Activate.

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/01.png)

Kolejnym krokiem, który wykonamy jest synchronizacja naszego sklepu z portalem Intune. W tym celu przechodzimy do konsoli Intune w Azure, Apps > Microsoft Store for Business oraz wybieramy opcję Enabled, odpowiedni język, Sync oraz klikamy na przycisk Save. Konfiguracja powinna zakończyć się bez problemu.

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/02.png)

W taki oto sposób dokonaliśmy wstępnej konfiguracji. Dla przykładu możemy również sobie zmienić nazwę naszego firmowego sklepu z nazwy domeny na coś bardziej przyjaznego. Robimy to z linku: [Windows Store for Business](https://businessstore.microsoft.com/en-gb/store) w zakładce Settings > Distribute > Private store

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/03.png)

Dla przykładu dodajmy nową aplikację, która będzie wyświetlała się w sklepie i będzie dostępna do ściągnięcia. Wykorzystam do tego aplikację o nazwie: Microsoft Remote Desktop, która jest dostępna pod tym linkiem.

Klikamy więc na przycisk Get the App

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/04.png)

I już po chwili mamy informację, że została poprawnie dodana do listy dostępnych aplikacji.

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/05.png)

Taka aplikacja nie jest jeszcze dostępna dla naszych użytkowników, należy ją uaktywnić w panelu Intune o czym za chwilę, ale na tą chwilę możemy ją dodać do kolekcji aplikacji. Przejdźmy więc do trzech kropek w oknie aplikacji oraz do Manage

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/06.png)

W zakładce Private Store Collections utwórzmy nową kolekcję: Productivity, dzięki czemu będziemy mieli odpowiednie kategorie.

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/07.png)

Ostatnim krokiem, który należy przypisać jest znane już Wam przypisanie aplikacji do odpowiedniej grupy użytkowników co opisałem już w tym poście.

Przejdźmy więc do portalu Intune, Mobile Apps > Apps, wyszukujemy naszą aplikację na liście:

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/08.png)

I ustawiamy, aby była dostępna dla wszystkich poprawnie dodanych urządzeń do naszej organizacji.

Po jakimś czasie taka aplikacja zostanie poprawnie wyświetlona w sklepie (tutaj dla przykładu kolejna aplikacja, którą dodałem, czyli Arduino IDE)

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/09.png)

Co prawda – nadal istnieje podstawowy sklep w którym dostępne są wszystkie aplikacje, ale w kolejnych wpisach zablokujemy go przez co użytkownicy będą mogli instalować tylko aplikacje dozwolone przez nasz dział IT.

Ostatni screen, który wam przedstawię pokazuje, że możemy zainstalować Microsoft Remote Desktop bezpośrednio z aplikacji Intune

![[PL] Microsoft Store for Business – konfiguracja oraz dodawanie aplikacji](/assets/images/posts/2018/microsoft-store-for-business/10.png)
