---
title: "[PL] Wdrażamy zdalnie aplikację Office365 na komputerach za pomocą Intune"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/wdrazamy-zdalnie-aplikacje-office365-na-komputerach-za-pomoca-intune/top.jpg"
subtitle:   "[PL] Wdrażamy zdalnie aplikację Office365 na komputerach za pomocą Intune"
---
![[PL] Wdrażamy zdalnie aplikację Office365 na komputerach za pomocą Intune](/assets/images/posts/2018/wdrazamy-zdalnie-aplikacje-office365-na-komputerach-za-pomoca-intune/top.png)Automatyczna instalacja Microsoft Company Portal

Pamiętacie [wpis z 23.08.2018 o dodawaniu komputera z systemem Windows 10 do Azure AD](https://www.piesik.me/2018/08/23/azure-ad-dodajemy-komputer-do-aad/)? W połączeniu z automatycznym utworzeniem [dynamicznej grupy](https://www.piesik.me/2018/08/24/automatyczne-przydzielanie-licencji-office-365-dla-pracownikow/) zabezpieczeń w AAD wdrożymy odpowiednią wersję oprogramowania na dane urządzenie bez ingerencji końcowego użytkownika.

Przejdźmy więc do głównego zadania. Główne założenie jest takie, żeby użytkownik, który zalogował się do komputera swoim kontem, np. jkowalski@itcns.pl miał zainstalowany automatycznie pakiet Office365 ProPlus, który jest w pakiecie E3.

Rozpoczynamy od zalogowania się do portalu Azure oraz przejścia do zakładki Intune oraz Mobile apps, która nas najbardziej interesuje.

W górnej części panelu powinniśmy mieć magiczny przycisk Add, który przeniesie nas do opcji, które należy skonfigurować.

* Wybieramy jako App Type Office 365 Suite > Windows 10
* Configure App Suite > Select Office apps to be assigned – zaznaczamy, które aplikacje  maja zostać zainstalowane
* App Suite Information – wypełniamy informacje, które zostaną wyświetlone w Portalu Firmy
* App Suite Settings – wybieramy odpowiednie opcje instalacyjne, aktualizacyjne oraz wersję pakietu, która zostanie zainstalowana, język oraz kilka innych opcji.

Po wszystkim należy kliknąć OK i aplikacja zostanie dodana, teraz musimy przypisać ją do odpowiedniej grupy.

Wykorzystam do tego wcześniej stworzoną grupę: O365_E3_Licences.

W zakładce, która zostanie otworzona przechodzimy do grupy: Assignments > Add group, wybieramy typ przypisania:

* Wymagana
* Dostępna do zainstalowania
* Do usunięcia

Ja chcę zrobić, aby ta aplikacja była ustawiona jako „Required”, następnie dodaję grupę jako Included, nie wyłączając żadnej innej grupy i klikam OK.

I już po chwili na naszym komputerze z Windows 10, gdzie jesteśmy zalogowani na użytkownika, który jest dodany do grupy rozpocznie się instalacja Office 365 co widzimy na screenie z Task Managera:

![[PL] Wdrażamy zdalnie aplikację Office365 na komputerach za pomocą Intune](/assets/images/posts/2018/wdrazamy-zdalnie-aplikacje-office365-na-komputerach-za-pomoca-intune/01.png)

Proste, szybkie i bez problemowe, prawda? Dzięki temu każdy z pracowników będzie miał wymuszoną instalację pakietu Office.

Jeżeli chcemy sprawdzić status instalacji – musimy wejść w detale naszej aplikacji, a następnie przejść do zakładki > Device install status. Dla przykładu użytkownik Jak Kowalski aktualnie instaluje aplikację:

![[PL] Wdrażamy zdalnie aplikację Office365 na komputerach za pomocą Intune](/assets/images/posts/2018/wdrazamy-zdalnie-aplikacje-office365-na-komputerach-za-pomoca-intune/02.png)

Miłego tworzenia automatycznego wdrażania aplikacji! 🙂
