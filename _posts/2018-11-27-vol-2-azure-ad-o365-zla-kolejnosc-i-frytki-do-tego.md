---
title: "[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/top.jpg)vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!

Jakiś czas temu popełniłem wpis w którym udało mi się naprawić swój błąd jeżeli chodzi o zakładanie subskrypcji Azure..

Całość możecie przeczytać pod tym linkiem: https://dzejzibloguje.pl/2017/07/05/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/

TL;DR: W tamtym wpisie opisałem  łączenie subskrypcji Azure i O365 ponieważ nie miały one dostępu do jednego wspólnego do katalogu, tylko każda usługa miała inny. Jak to naprawić?

No i znów mam taką samą sytuację. Dwa oddzielne katalogi i trzeba je połączyć. Niestety, sposób podany w pierwszym poście już jest nieaktualny, ponieważ stary portal nie istnieje.

Jak zwykle z pomocą przyszła grupa Microsoft Azure User Group Poland , a krótką dyskusję możecie przeczytać pod tym linkiem.

Założenia są takie:

1) Darmowe konto na Azure, które posiada przez rok limit dolarów / euro do wykorzystania, które ma konto xyz@gmail.com
2) Subskrypcja Office 365 Developer w wersji na rok z kontem azureadmin@blabla.onmicrosoft.com

Więc w jaki sposób rozwiązałem mój problem

Przeszedłem do ustawień subskrypcji na koncie gdzie jest ona jest aktywna i dodałem nowego użytkownika jako Ownera tak jak na screenie:

![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/01.png)

Następnie przyjąłem zaproszenie do katalogu:

![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/02.png)

Teraz nastąpi ważna rzecz, mianowicie zalogowanie się do portalu Azure kontem azureadmin@blabla.onmicrosoft.com oraz wybranie z górnego rogu nowo przydzielonej subskrypcji:

![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/03.png)

Jeżeli przełączymy się na nowy katalog, przechodzimy do opcji Cost Management + Billing z lewego menu > Other Subscriptions > wybieramy tą, którą została nam przydzielona z poprzedniego konta.

![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/04.png)

Klikamy Change Directory

![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/05.png)

Change…..

I mamy komunikat potwierdzający przeniesienie subskrypcji do nowego, już właściwego tenanta.

![[PL] vol 2 | Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/vol-2-azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/06.png)

Dzięki wykonaniu tej instrukcji możemy rozpocząć właściwą pracę.
