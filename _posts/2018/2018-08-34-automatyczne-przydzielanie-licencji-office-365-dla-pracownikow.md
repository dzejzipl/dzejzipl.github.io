---
title: "[PL] Automatyczne przydzielanie licencji Office 365 dla pracowników"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/automatyczne-przydzielanie-licencji-office-365-dla-pracownikow/top.jpg"
subtitle:   "[PL] Automatyczne przydzielanie licencji Office 365 dla pracowników"
---
![[PL] Automatyczne przydzielanie licencji Office 365 dla pracowników](/assets/images/posts/2018/automatyczne-przydzielanie-licencji-office-365-dla-pracownikow/top.jpg)Automatyczne przydzielanie licencji Office 365 dla pracowników

Mamy w planach zatrudnienie kolejnych 15 osób, więc kupujemy odpowiednią ilość licencji i podpinamy je do swojego konta. Tworzymy konta dla tych osób i możemy podpiąć manualnie do każdego licencję. To by się sprawdziło w przypadku 4-5 osób. Powyżej tej liczby po pierwsze dodawałbym konta za pomocą PowerShella i plików CSV a po drugie – nie chce mi się pamiętać, aby dla każdej osoby dodać odpowiednią licencję. To po prostu ma działać.

W jaki sposób to rozwiązać? Zacząłbym od stworzenia grupy zabezpieczeń, która będzie dynamiczna i brała wartość parametru. U mnie ten parametr będzie sprawdzany na podstawie Department. Jeżeli jego wartość będzie inna niż FrontLine – przypiszę odpowiednią licencję E3. Jeżeli będzie to FrontLine – przypiszę licencje F1. Na potrzeby testów stworzyłem sześciu użytkowników: czterech do E3 oraz dwóch do F1.

O dynamicznych grupach użytkowników pisałem już w tym poście, ale dla przypomnienia utworzymy jeszcze grupę dla FrontLine. W tym celu otwieramy portal Azure AD, przechodzimy do zakładki Groups, New Group, wypełniamy odpowiednie pola a jako Membership type wybieramy Dynamic user. W tym przypadku Dynamic Query wygląda tak:

```powershell
(user.department -eq „FrontLine”)
```

Taka ciekawostka – w jaki sposób wyszukać wszystkich pracowników, którzy mają wpisane w Departament cokolwiek innego niżeli FrontLine oraz nie mają pustego pola jak jest domyślnie ustawione?

```powershell
(user.department -notMatch „FrontLine”) -and (user.department -ne $null)
```

W ten oto sposób stworzyłem grupę dla licencji E3.

Jeżeli już stworzyliśmy takową grupę, pojawili się w niej odpowiedni członkowie to wypadało by przypisać odpowiednią licencję Office365.

Zaczynamy od wejścia do naszej grupy – zacznę od grupy nazwanej: O365_E3_Licences gdzie mam swoich użytkowników, następnie przejdę do okienka: Licenses > **Assign**

![[PL] Automatyczne przydzielanie licencji Office 365 dla pracowników](/assets/images/posts/2018/automatyczne-przydzielanie-licencji-office-365-dla-pracownikow/01.png)

Nie pozostało nam nic innego jak przy kliknięciu na Products > Configure required settings wybrać odpowiednią licencję (dla mnie to będzie Office E3) a w zakładce: Assignment options zaznaczyć, które programy maja być dostępne dla użytkowników i potwierdzić wszystko przyciskiem Assign.

Nasze okno powinno wyglądać teraz następująco:

![[PL] Automatyczne przydzielanie licencji Office 365 dla pracowników](/assets/images/posts/2018/automatyczne-przydzielanie-licencji-office-365-dla-pracownikow/02.png)

Krótko i na temat – dzięki dynamicznym grupom jesteście w stanie zapanować nad licencjami. W momencie jak dodacie użytkownika do Azure Active Directory i będzie miał ustawiony odpowiedni Departament – będzie miał dostęp do Office365.
