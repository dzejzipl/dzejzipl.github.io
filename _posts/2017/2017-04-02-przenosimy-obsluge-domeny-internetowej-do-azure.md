---
title: "[PL] Przenosimy obsługę domeny Internetowej do Azure"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] Przenosimy obsługę domeny Internetowej do Azure](/assets/images/posts/przenosimy-obsluge-domeny-internetowej-do-azure/top.png)Przenosimy obsługę domeny Internetowej do Azure

Ostatnio zacząłem przenosić swoje usługi do chmury Azure – tym razem padło na adresy www, czyli domeny.

Dzięki tej operacji mam dostęp do szybkiej modyfikacji rekordów DNS bez konieczności logowania się do innych stron.

Utrzymanie jednej domeny miesięcznie kosztuje nas około 0.42 euro, jednak jest to zalezne od wykorzystego ruchu.

Pokrótce opiszę jak takiej operacji dokonać.

Logujemy się do panelu i wybieramy New > Dns Zone

![[PL] Przenosimy obsługę domeny Internetowej do Azure](/assets/images/posts/przenosimy-obsluge-domeny-internetowej-do-azure/01.png)

Wpisujemy nazwę swojej domeny, w moim przypadku to będzie: contoso.ovh, wybieramy subskrypcję oraz grupę do której ma należeć ta strefa. Ja np. dla samych stref mam oddzielną grupę, dzięki czemu jest mi łatwiej wszystkim zarządzać. Po chwili domena zostanie poprawnie zaparkowana.

Kolejnym krokiem, który należy wykonać to przekierować naszą domenę na odpowiednie serwery Azure, które widzicie poniżej:

![[PL] Przenosimy obsługę domeny Internetowej do Azure](/assets/images/posts/przenosimy-obsluge-domeny-internetowej-do-azure/02.png)

W moim przykładzie pokażę jak to zrobić w panelu ovh.pl gdzie mam wykupione swoje usługi.

Wchodzimy w edycję swojego adresu, następnie w DNS Servers i mamy widok domyślnych serwerów, który u mnie wygląda tak:

![[PL] Przenosimy obsługę domeny Internetowej do Azure](/assets/images/posts/przenosimy-obsluge-domeny-internetowej-do-azure/03.png)

Dlatego teraz zaczniemy dodawać swoje serwery, które są przypisane do Azure a te z OVH usuniemy.

Finalny widok będzie wyglądał podobnie do tego:

![[PL] Przenosimy obsługę domeny Internetowej do Azure](/assets/images/posts/przenosimy-obsluge-domeny-internetowej-do-azure/04.png)

To była ta najłatwiejsza część, teraz będziemy mogli już modyfikować rekordy bezpośrednio w Azure.

W kolejnych wpisach przybliżę w jaki sposób przypisać domenę O365 nie w OVH jak kiedyś opisywałem, a w Microsofcie.

Have fun!
