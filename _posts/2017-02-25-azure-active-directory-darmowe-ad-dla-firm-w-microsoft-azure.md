---
title: "[PL] Azure Active Directory – darmowe AD dla firm w Microsoft Azure"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] Azure Active Directory – darmowe AD dla firm w Microsoft Azure](/assets/images/posts/azure-active-directory-darmowe-ad-dla-firm-w-microsoft-azure/top.jpg)Azure Active Directory – darmowe AD dla firm w Microsoft Azure

Na 4 spotkaniu Azure Group w Łodzi Dariusz Porowski opowiadał o rozpoczęciu pracy w Azure Active Directory. Dowiedziałem się, że źle zacząłem pracę i tworzenie „testowej” organizacji, dlatego postanowiłem napisać poradnik jak zacząć, aby nie popełnić moich błędów.

Co zrobiłem źle? Wdrożyłem pakiet O365 dla developerów bez wprowadzenia AAD, próbowałem podłączyć własny portal logowania bez podstawowej konfiguracji, no i najważniejsze – próbowałem wdrożenia Exchange bez najbardziej podstawowej rzeczy – zdefiniowania administratorów oraz osób odpowiedzialnych za „finanse” w naszej fikcyjnej organizacji. Może się to wydawać śmieszne, ale takie konta i role też muszą być założone, bo dlaczego osoba od finansów ma mieć możliwość kasowania kont użytkowników?

Po co to robię? Może uda mi się wykorzystać tę wiedzę w przyszłości do wdrożenia przedsiębiorstwa w Azure AD i całkowitego zarządzania nim za pomocą oprogramowania Microsoftu w tym Exchange jako serwer poczty.

Czym jest Azure AD? Jest to „chmurowa” wersja Active Directory, która umożliwia nam tworzenie obiektów, czyli użytkowników oraz grup. Z poziomu AAD (Azure Active Directory) możemy nimi np. zarządzać, nadawać uprawnienia, przypisywać licencje.

Pierwszym krokiem jest założenie darmowego konta, które tworzymy pod tym linkiem: https://account.windowsazure.com/organization. Jak widzimy na screenie, musimy uzupełnić podstawowe dane: imię,  nazwisko, adres e-mail.  Piątym, najważniejszym dla nas parametrem będzie nazwa organizacji, która z początku będzie w domenie onmicrosoft.com, a później podepniemy pod AAD własny adres.  Ja użyję: dzejzi.ovh.

![[PL] Azure Active Directory – darmowe AD dla firm w Microsoft Azure](/assets/images/posts/azure-active-directory-darmowe-ad-dla-firm-w-microsoft-azure/01.png)

Po kliknięciu sprawdź dostępność pojawią się dodatkowe pola:

![[PL] Azure Active Directory – darmowe AD dla firm w Microsoft Azure](/assets/images/posts/azure-active-directory-darmowe-ad-dla-firm-w-microsoft-azure/02.png)

W tym kroku uzupełniamy:

* Nowy ID użytkownika, czyli nazwa naszego administratora. W moim przypadku będzie to np. mój login, czyli jpiesik.
* Hasło i powtórzenie hasła – nie muszę się wiele wypowiadać, aczkolwiek radzę użyć bardzo mocnego hasła. Dlaczego? Bo będzie to główne konto administratora, który ma dostęp do całej organizacji.
* Weryfikacja numeru telefonu.

Po poprawnej weryfikacji przenosimy się do strony logowania portalu Microsoft, wpisujemy swój login, który jest w formacie: nazwauzytkownika@nazwadomeny.onmicrosoft.com oraz ustalone wcześniej hasło. Po weryfikacji – czeka nas do uzupełnienia jeszcze więcej pól, w tym kolejna, dwukrotna weryfikacja za pomocą telefonu oraz karty kredytowej. Drobna informacja – żadne fundusze nie zostaną pobrane,  dostaniemy 170 euro do wykorzystania na testowe potrzeby. Po uzupełnieniu danych i akceptowaniu regulaminu pojawi się upragniona informacja:

![[PL] Azure Active Directory – darmowe AD dla firm w Microsoft Azure](/assets/images/posts/azure-active-directory-darmowe-ad-dla-firm-w-microsoft-azure/03.png)

Po takiej operacji możemy z lewego menu wybrać Azure Active Directory i dodać kilku testowych użytkowników, ponieważ na początku nasze AAD wygląda w tak:

![[PL] Azure Active Directory – darmowe AD dla firm w Microsoft Azure](/assets/images/posts/azure-active-directory-darmowe-ad-dla-firm-w-microsoft-azure/04.png)

Po wszystkim możemy dodać własną domenę np używając poradnika z tego linku: https://www.piesik.me/2016/11/15/ovh-office365-i-wlasna-domena/

Życzę powodzenia w tworzeniu własnego AAD. W kolejnych wpisach pokażę co możemy z taką Azure AD zrobić, jak włączyć dwuetapową weryfikację i jak zrobić synchronizację z lokalnym AD, czyli w skrócie mówiąc: wiele dobrego mięsa!

Dzięki!
