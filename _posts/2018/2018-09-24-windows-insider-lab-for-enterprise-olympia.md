---
title: "[PL] Windows Insider Lab for Enterprise – Olympia"
categories:
    - Krótko
tags:
    - Krótko
    - PL Post
---

!["[PL] Windows Insider Lab for Enterprise – Olympia"](/assets/images/posts/windows-insider-lab-for-enterprise-olympia/top.jpg)Windows Insider Lab for Enterprise – Olympia

Jakiś czas temu przeglądając Twittera wyświetlił się tweet, który zawierał nazwę tajemniczego produktu firmy Microsoft – Olympia. Nie słyszałem o takim czymś w związku z czym postanowiłem się bliżej przyjrzeć nowemu projektowi tej firmy.

Zaciekawiony udałem się na stronę projektu, gdzie dowiedziałem się między innymi, że jest to projekt dla Windows Insiderów, którzy chcą mieć możliwość używania zaawansowanych opcji przeznaczonych dla przedsiębiorstw, np:

WIP (Windows Information Protection), ATP (Advanced Threat Protection), WDAG (Windows Defender Application Guard), APP-V (Application virtualization) oraz  Device Guard
Oprócz tego mamy możliwość testowania wczesnych wersji oprogramowania jak i kontaktu z Inżynierami w różnych kanałach oraz przekazywanie pozytywnego i negatywnego feedbacku.

Aby dołączyć do programu wymagane jest bycie Windows Insiderem i należało wypełnić krótką ankietę, w której odpowiedziałem na kilkanaście pytań. Po jakimś czasie otrzymałem wiadomość e-mail, z informacją, że zostałem przyjęty do programu.

!["[PL] Windows Insider Lab for Enterprise – Olympia"](/assets/images/posts/windows-insider-lab-for-enterprise-olympia/01.png)

I do tych zabaw należało się przygotować.

Zacząłem od utworzenia pierwszej nowej wirtualnej maszyny z Windows 10 Professional Insider w wersji 17758 w języku en-US z dodanym kontem Microsoft Account oraz późniejszym zaktualizowaniu systemu do najnowszej obecnej wersji Insidera, czyli 17763 bez Skip Ahead do RS5.

!["[PL] Windows Insider Lab for Enterprise – Olympia"](/assets/images/posts/windows-insider-lab-for-enterprise-olympia/02.png)

Oraz drugiej, gdzie konfiguracja systemu była idealnie ta sama, lecz z dodanym tylko kontem lokalnym, gdzie była zainstalowana taka sama wersja systemu

Dlaczego? Ponieważ Olympia umożliwia dołączenie do swojego przedsiębiorstwa w dwóch modelach:

Jako urządzenie BYOD (Bring-Your-Own-Devide), czyli urządzenie, do którego będziemy się logować swoim kontem Outlook, ale z politykami Olympia
Jako urządzenie korporacyjne, czyli zamiast konta lokalnego użyjemy konto korporacyjne. W tej opcji wersja naszego Windowsa zostaje zaktualizowana z PRO do Enterprise.
Rozpocząłem od dodania drugiej maszyny do Azure AD zgodnie z tym co jest jest napisane w instrukcji: [https://docs.microsoft.com/en-us/windows/deployment/update/olympia/olympia-enrollment-guidelines#set-up-azure-active-directory-joined-windows-10-device] i po chwili otrzymałem komunikat z zapytaniem czy na pewno chcę dołączyć do organizacji:

!["[PL] Windows Insider Lab for Enterprise – Olympia"](/assets/images/posts/windows-insider-lab-for-enterprise-olympia/03.png)

W momencie pierwszego logowania następuje konfiguracja naszego urządzenia:

!["[PL] Windows Insider Lab for Enterprise – Olympia"](/assets/images/posts/windows-insider-lab-for-enterprise-olympia/04.png)

I po tym kroku mogłem już się logować na swoje konto.

Po skonfigurowaniu drugiej maszyny postanowiłem wrócić do pierwszej i skonfigurowałem dostęp do zasobów firmy za pomocą tego samego konta, ale dzięki temu będę mógł się logować kontem Microsoft. Polityki zadziałały od razu i otrzymałem komunikat, że należy zaszyfrować swoje urządzenie.

!["[PL] Windows Insider Lab for Enterprise – Olympia"](/assets/images/posts/windows-insider-lab-for-enterprise-olympia/05.png)

A z racji tego, że dla uczestników tego programu jest dostępny Office 365 w wersji E5 to w końcu będę miał możliwość zapoznania się z nową wersją Skype i dzwonieniem z telefonu komórkowego 😉

A w wolnej chwili, postaram się opisać technologie wykorzystywane w tym labie.
