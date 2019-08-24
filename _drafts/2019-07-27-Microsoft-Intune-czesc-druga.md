---
title: "[PL] „Microsoft Intune - część druga"
categories:
    - Intune
tags:
    - Intune
    - Wprowadzenie
    - PL post
---
![„Microsoft Intune - część druga"](/assets/images/top_images/IntuneTOP.png)Skoro napisało się pierwszą część, napiszmy również drugą część o usłudze Microsoft Intune

Co zostało napisane w pierwszym poście, możecie przeczytać [pod tym linkiem](https://www.piesik.me/2019/07/09/Microsoft-Intune-czesc-pierwsza) do czego was serdecznie mocno zapraszam, ponieważ daje nam to solidne wprowadzenie co należy zrobić, aby móc rozpocząć pracę.

Pokrótce to wszystko podsumuję:
* Wiemy jakie są potrzebne licencje
* Wiemy jak skonfigurować rejestrację urządzeń
* Wiemy jak skonfigurować Branding

Natomiast w drugiej części chciałbym wam pokazać w jaki sposób dodawać użytkowników oraz bawić się z grupami.

## Rozpocznijmy zabawę

### Użytkownicy

Użytkowników możemy dodać za pomocą portalu Office Admin, portalu Azure Active Directory, za pomocą CLI, Grapha jak i PowerShella. Ja chciałbym się skupić na tym, aby pokazać wam w jaki sposób dodać użytkownika za pomocą portalu

Przechodzimy do **Microsoft Intune** lub **Azure Active Directory** > **Users** > **New User**

![„Microsoft Intune - część druga"](/assets/images/posts/Microsoft-Intune-czesc-druga/1.png)

1. W tym polu wpisujemy nazwę wyświetlaną danego użytkownika, np. Jan Kowalski
2. Natomiast tutaj musimy podać nazwę użytkownika, dla przykładu **jkowalski**, ale z naszą domeną. Jeżeli nasza domena to **piesik.xyz**, to nazwa naszego użytkownika będzie wyglądać tak: ***jkowalski@piesik.xyz***
3. Klikając na **Configure** jesteśmy w stanie uzupełnić dodatkowe parametry danego użytkownika
4. Dla przykładu imię, nazwisko, departament jak i nazwę stanowiska
5. Domyślna rola dla każdego użytkownika to **User**, my natomiast możemy ustawić nowego użytkownika z rolą **globalnego administratora** lub administratora o innych rolach - jest ich całkiem sporo. Możecie przeczytać o nich tutaj: [Azure Roles](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles)

Po wypełnieniu wszystkich niezbędnych pól, poniżej roli użytkownika pojawi nam się hasło pierwszego logowania.

### Grupy

W Azure Active Directory wyróżniamy dwie główne grupy oraz podgrupy

* Security

    * Dynamic User
    * Dynamic Device
    * Assigned

* Office 365

    * Dynamic User
    * Assigned

Czym się różnią poszczególne typy grup?

* Dynamic User - pozwala nam na stworzenie grupy użytkowników, która będzie się aktualizowała automatycznie w momencie wykrycia zmian w naszej bazie użytkowników pod względem danego parametru. Dla przykładu, przyda się to do stworzenia grup działowych.

* Dynamid Device - pozwala nam na stworzenie grupy urządzeń posortowanych według wskazanych przez nas parametrów. Najbardziej prosty przykład - grupa urządzeń tylko z systemem Windows

* Assigned - a to jak sama nazwa mówi, sami dodajemy użytkowników / urządzenia do tej grupy.

Najbardziej lubię dynamiczne oraz możliwość zabawy parametrami. Dzięki temu, że Microsoft dosyć dobrze je opisał na [swojej stronie](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership) jesteśmy w stanie stworzyć na prawdę zaawansowane grupy - zarówno użytkowników jak i urządzeń.

Przejdźmy do kolejnego testu, czyli stworzenie testowej grupy urządzeń tylko z Windows 10 oraz grupy użytkowników, którzy mają wpisane **cokolwiek** w Department.

Przechodzimy do **Microsoft Intune** lub **Azure Active Directory** > **Groups** > **New Group**

![„Microsoft Intune - część druga"](/assets/images/posts/Microsoft-Intune-czesc-druga/2.png)

1. Wybieramy typ grupy. Wybrałem **Security**

2. Uzupełniamy nazwę oraz opis

3. Rozpoczynamy tworzenie dynamicznego zapytania

4. Wybieramy typ: **Simple Rule** gdzie możemy wybrać jedno z predefiniowanych pól

5. Lub też zaczynamy tworzyć swoje bardziej zaawansowane zapytania. 

Jednkaże na potrzeby tej grupy wystarczy nam prosty edytor.

Po utworzeniu grupy, odczekaniu kilku minut możemy zobaczyć kto lub jakie urządzenie jest członkiem tej grupy:

![„Microsoft Intune - część druga"](/assets/images/posts/Microsoft-Intune-czesc-druga/3.png)

Ok, ale może teraz warto by było zrobić grupę dla naszych wszystkich użytkowników, którzy mają wpisane **cokolwiek** w polu Department. Po co nam to? Aby później przypisać do tej grupy użytkowników licencje.

Rozpoczynamy więc tworzenie nowej grupy, tym razem wybieramy **Dynamic User** oraz wybierzemy sobie zaawansowany edytor, a jako zapytanie wpiszemy:
```
(user.department -ne $null)
```

![„Microsoft Intune - część druga"](/assets/images/posts/Microsoft-Intune-czesc-druga/4.png)

I już po chwili pojawią się użytkownicy, którzy **mają** uzupełnione pole Department

![„Microsoft Intune - część druga"](/assets/images/posts/Microsoft-Intune-czesc-druga/5.png)