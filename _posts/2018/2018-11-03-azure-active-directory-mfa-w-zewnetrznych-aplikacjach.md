---
title: "[PL] Azure Active Directory – MFA w zewnętrznych aplikacjach"
categories:
    - Poradniki
tags:
    - Poradniki
    - PL Post
---

!["[PL] Azure Active Directory – MFA w zewnętrznych aplikacjach"](/assets/images/posts/azure-active-directory-mfa-w-zewnetrznych-aplikacjach/top.jpg)Azure Active Directory – MFA w zewnętrznych aplikacjach

O dwustopniowej weryfikacji w Azure, Office365 pisałem już kilkanaście razy. Ostatni mój wpis tego typu poruszyłem w momencie, gdy Microsoft dodał „bezhasłowe” logowanie do konta, o czym możecie przeczytać pod tym linkiem.

A co jeżeli użytkownik nie chce używać oficjalnej aplikacji Microsoft Authenticator, tylko używa oddzielnej aplikacji do generowania tokenów potrzebnych do zalogowania?

Jestem idealnym przykładem. Do dwustopniowej weryfikacji używam zewnętrznej aplikacji – nazwanej Authy, w której mam dodane kilka kont.

Aby ustawić taką dwustopniową weryfikację udajemy się na stronę pod adresem: https://account.activedirectory.windowsazure.com/Proofup.aspx i rozpoczynamy dodawanie aplikacji mobilnej:

!["[PL] Azure Active Directory – MFA w zewnętrznych aplikacjach"](/assets/images/posts/azure-active-directory-mfa-w-zewnetrznych-aplikacjach/01.png)

Wszystko jest po staremu, prawda? Ale w momencie jak spróbujecie dodać taki qr code do aplikacji, nie zostanie on zaakceptowany.

Musimy wybrać opcję: Configure app without notifications przez co kod QR się trochę zmieni i dopiero teraz będzie można dodać go do aplikacji.

!["[PL] Azure Active Directory – MFA w zewnętrznych aplikacjach"](/assets/images/posts/azure-active-directory-mfa-w-zewnetrznych-aplikacjach/02.png)

Tadam!

Nasze konto jest bezpieczne, a nie musimy używać do tego dodatkowej aplikacji. Polecam ten styl życia 😉
