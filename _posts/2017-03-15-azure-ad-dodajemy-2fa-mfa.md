---
title: "[PL] Azure AD – dodajemy 2FA (MFA)"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/top.jpg)Azure AD – dodajemy 2FA (MFA)

Cześć,
w dzisiejszym wpisie chcę poruszyć kwestię bezpieczeństwa.

Zabezpieczanie swoich kont w różnych serwisach to nie tylko hasła. Oczywiście, każde z kont powinno mieć je inne, a jeżeli już nie chcecie tak robić, to możecie ustalić jedno hasło „bazowe”, które później modyfikujecie pod daną witrynę. Nie jest to najbezpieczniejsze, ale o wiele lepsze niż posiadanie jednego lub dwóch haseł do wielu witryn w tym waszych skrzynek pocztowych oraz banków.

Jeszcze bezpieczniejszą opcją jest włączenie 2FA, czyli 2 Factor Authentication, w języku polskim popularnie zwane jest to dwustopniową weryfikacją. W jaki sposób może się to odbywać? Najpopularniejszym przykładem są kody SMS oraz z kody z aplikacji mobilnych.

Przypomnijcie sobie proszę w jaki sposób autoryzowało się przelewy w bankach. Aby takowy wykonać, należało podać jednorazowy kod, który znajdował się na karcie. W późniejszym czasie przeszliśmy na potwierdzenia przelewów za pomocą SMS, co było o wiele wygodniejszą opcją.

A jakie opcje my możemy wprowadzić dla swojej organizacji? Będziemy potrzebować nie tylko loginu oraz hasła, ale także kodu, który zostanie dla nas wygenerowany i wysłany w wiadomości tekstowej. Do wyboru mamy także możliwość otrzymania połączenia telefonicznego.

W wpisie tym chciałbym przedstawić w jaki sposób możemy uaktywnić dwustopniową weryfikację do naszych kont w Azure Active Directory. Wpis jest o wiele bardziej techniczny niż poprzednie, aczkolwiek pojawiła się szansa na wykorzystanie tego dlatego postanowiłem podzielić się z wami tą wiedzą.

Niestety, zobaczycie tylko jak włączyć MFA za pomocą wiadomości SMS i połączeń, w planach jest także uaktywnienie takich autoryzacji używając aplikacji mobilnej.

Na początek musimy zalogować się do starego portalu, którego znajdziemy pod tym adresem: https://manage.windowsazure.com/ następnie przechodzimy do naszego AD wybierając: Active Directory > nasza domena > Configure > oraz klikamy w: Manage service settings

![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/01.png)

Otworzy nam się okno, w którym konfigurujemy wszystkie niezbędne opcje. Dla mnie najważniejszą była verification options, gdzie zaznaczamy w jaki sposób możemy się uwierzytelnić. Ja pozostawiłem zaznaczone u siebie tylko dwie pierwsze opcje (SMS oraz Phone), ponieważ jak już wcześniej pisałem plany wdrożenia aplikacji są – na kiedyś.

Zaznaczyłem również opcję, aby urządzenia były uwierzytelnione przez 30 dni, dzięki tej właściwości użytkownik nie musi wpisywać codziennie kodu autoryzacyjnego.

![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/02.png)

Kolejnym krokiem, który wykonujemy jest wybranie z zakładki: users naszych „pracowników”, którym włączamy dwuskładnikowe uwierzytelnianie. Włączyłem dla przykładu dla użytkownika: Marek Rolecki.

![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/03.png)

Z podstawowej konfiguracji jest to wszystko co musimy wykonać, dalsze kroki robimy z poziomu profilu danego użytkownika.

W momencie gdy Marek zaloguje się po raz pierwszy po takiej zmianie na portal.office.com ujrzy komunikat podobny do tego:

![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/04.png)

Po kliknięciu **skonfiguruj je teraz** Marek będzie musiał podać numer telefonu gdzie otrzymam wiadomość SMS z kodem lub rozmowę z automatem, który mu go przekaże.

![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/05.png)

W kroku drugim jest generowane hasło do aplikacji. Możecie spytać – po co? Nie wszystkie aplikacje obsługują poprawnie dwustopniową weryfikację, w takim przypadku podajemy właśnie wygenerowany ciąg znaków. Jest to także bezpieczne – jeden ciąg – jedna aplikacja. W przypadku wycieku blokujemy tylko tymczasowe hasło. Dobrą stroną jest także to, że dany program nie posiada naszych głównych danych.

Klikamy gotowe… I po chwili nasze konto jest już zweryfikowane.

Podczas kolejnego logowania (po czasie ustawionym przez nas podczas konfiguracji) Marek otrzyma komunikat, że należy zweryfikować „własność” konta. Pokazuje to poniższy komunikat.

![[PL] Azure AD – dodajemy 2FA (MFA)](/assets/images/posts/azure-ad-dodajemy-2fa-mfa/06.png)

To wszystko co musimy zrobić, aby uzyskać F2A dla kont w naszej organizacji za pomocą połączeń głosowych lub wiadomości SMS.
