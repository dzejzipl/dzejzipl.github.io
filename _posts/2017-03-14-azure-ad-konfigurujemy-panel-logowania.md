---
title: "[PL] Azure AD – konfigurujemy panel logowania"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] Azure AD – konfigurujemy panel logowania](/assets/images/posts/azure-ad-konfigurujemy-panel-logowania/top.jpg)Konfigurujemy Branding w Azure AD

Cześć!

Drugi z wpisów poświęcę mało ważnej rzeczy z widzenia technicznego, ale ważnej dla użytkownika, czyli skonfigurujemy swój panel logowania do Azure AD / Office 365, dzieki czemu użytkownik będzie wiedział, że jest to „nasz” portal i szybciej się dowie jakie dane ma tam wpisać.

Na początek logujemy się do swojego Azure i wchodzimy w Azure Active Directory. Z lewego menu wybieramy Znakowanie firmowe, dzięki czemu możemy rozpocząć dostosowywanie poprzez kliknięcie przycisku: Konfiguruj znakowanie firmowe teraz.

![[PL] Azure AD – konfigurujemy panel logowania](/assets/images/posts/azure-ad-konfigurujemy-panel-logowania/01.png)

Następnie przygotowujemy 4 obrazy, które będą identyfikowały naszą stronę logowania:

* Obraz strony logowania o wymiarach 1420x1200px
* Obraz transparetny o wymiarach 280x60px (jest to nasze logo)
* Kwadratowe logo o rozmiarze 240x240px
* Kwadratowe logo o rozmiarze 240x240px, które zostanie wykorzystane w ciemnym motywie

Musimy również uzupełnić następujące pola:

* Podpowiedź dotycząca nazwy użytkownika – ten tekst pojawi się w polu nazwa użytkownika
* Tekst strony logowania – tutaj mamy pole o wielkości do 256 znaków. W nim wpisujemy wszystko, co chcemy przekazać użytkownikowi podczas logowania, np. gdzie zgłaszać się po pomoc lub warunki użytkowania
* Kolor tła strony logowania – jest to konieczne do wybrania, ponieważ czasem obrazek logowania, który zdefiniowaliśmy wyżej może się nie załadować i w takim wypadku jest wykorzystywany ten kolor
* Nie wylogowuj mnie – możemy zaznaczyć tą opcję, aby zostawić użytkowników zalogowanych do serwisów O365 – np klienta Outlook.

Po tym wszystkim klikamy przycisk Zapisz i czekamy, aż takie wdrożenie zostanie przeprowadzone.

Po tym wszystkim możemy otworzyć sesję incognito w dowolnej przeglądarce, spróbować się zalogować na swoje konto i po chwili przeniesie nas do portalu logowania już z naszym spersonalizowanym wyglądem.

Poniżej możecie zobaczyć screen jak to wygląda w moim przypadku:

![[PL] Azure AD – konfigurujemy panel logowania](/assets/images/posts/azure-ad-konfigurujemy-panel-logowania/02.png)

oraz na telefonie komórkowym:

![[PL] Azure AD – konfigurujemy panel logowania](/assets/images/posts/azure-ad-konfigurujemy-panel-logowania/03.jpg)