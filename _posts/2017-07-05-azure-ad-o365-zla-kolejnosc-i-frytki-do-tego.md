---
title: "[PL] Azure AD, O365, zła kolejność… I frytki do tego!"
categories:
    - Krótko
    - Azure
tags:
    - PL Post
---
![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/top.png)Azure AD, O365, zła kolejność… I frytki do tego!

Cześć i czołem.

Dziś miałem jeden problem. Dosyć duży problem, mianowicie:

Stworzyłem subskrypcję Azure, dodałem usera i…

Pomyślałem, że do tego scenariusza potrzebuję subskrypcji Office 365 dla Developerów (którą możecie zdobyć za darmo!).

Nie pytajcie co to za rozwiązanie, kiedyś na blogu 😉

Wracając do tematu.

W momencie tworzenia subskrypcji O365 chciałem dodać ją do istniejącej subskrypcji Azure AD, co by mieć jeden katalog użytkowników. Wiecie – takie bardzo wielkie ułatwienie na kolejne projekty.

Więc wchodzę na stronę rejestracji, klikam dodaj do istniejącej subskrypcji, loguję się na dane administratora… I nie znaleziono takiego użytkownika.

Próbuję się zalogować z nazwą AD.onmicrosoft.com…

I nic.

Próba 35 i nadal nic.

Ok, więc czas na poszukanie na Google. Po odpowiednim zapytaniu trafiłem na informację, że.. Jest to znany problem a nasz Kochany Microsoft™ jeszcze nic z nim nie zrobił… No trudno, musimy jakoś przejść przez ten problem. W międzyczasie napisałem zapytanie na grupie Microsoft Azure User Group Poland ( https://www.facebook.com/groups/azureugpl/ ) gdzie kolega Kamil Brzeziński podpowiedział, że takie rzeczy już wykonywał. Ok, to nie ma co czekać tylko wykonujemy porady, które zostały podrzucone na tejże stronie ( https://docs.microsoft.com/en-us/azure/billing/billing-add-office-365-tenant-to-azure-subscription )

Podpowiem tylko, że ja będę wykonywał tę operację posiadając dwa główne założenia:

* Jest założona subskrypcja Azure, które ma przypisane konto do logowania aaa@cos.pl
* Jest już stworzony subskrypcja Office365, które ma przypisane konto bbb@cos.onmicrosoft.com
 

Logujemy się na stary portal: https://manage.windowsazure.com/ z adresem aaa@cos.pl

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/01.jpg)

Wchodzimy w Active Directory, tworzymy nowy katalog z dolnego menu wybierając New > Directory > Custom Create jak na screenie:

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/02.jpg)

W polu dodawania katalogu wybieramy, że chcemy użyć istniejącego katalogu i zaznaczamy, że możemy się wylogować i zalogować nowymi danymi:

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/03.jpg)

Teraz nadszedł czas, gdy musimy się zalogować do Azure damymi, które mamy przypisane do konta Office 365, czyli w moim przypadku to będzie: bbb@cos.onmicrosoft.com

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/04.jpg)

Wyskoczy nam informacja czy chcemy użyć katalogu z O365 z naszym Azure AD. Klikamy Continue.

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/05.jpg)

Po tym jak automatycznie zostaniemy wylogowani z starego portalu, możemy już się zalogować do niego z powrotem i sprawdzić czy mamy dostępne dwa katalogi.

Jeżeli mamy, możemy przejść do kolejnej części czyli do zmiany katalogu używanego w subskrypcji Azure.

Logujemy się na stary portal, z menu po lewej stronie wybieramy Settings > następnie naszą subskrypcję i musimy ją zeedytować poprzez wybranie Edit Directory z dolnego menu jak na screenie.

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/06.jpg)

Edytujemy przypisany katalog wybierając ten z O365, w moim przypadku jak na screenie:

![[PL] Azure AD, O365, zła kolejność… I frytki do tego!](/assets/images/posts/azure-ad-o365-zla-kolejnosc-i-frytki-do-tego/07.jpg)

Pojawi nam się informacja o tym, że przypisani administratorzy tracą dostęp (muszą, bo nie mają dostępu w katalogu O365), klikamy next
Następnie wybieramy Complete.
To by było na tyle.

Na koniec możemy dodać jeszcze administratora Azure z katalogu O365, więc wpisujemy jego adres: cos@bbb.onmicrosoft.com i przypisujemy do której subskrypcji ma dostęp.

Wybaczcie za słabej jakości screeny, wycinałem z filmiku, który nagrywałem podczas prac i wklejałem ręcznie napisy 😀
