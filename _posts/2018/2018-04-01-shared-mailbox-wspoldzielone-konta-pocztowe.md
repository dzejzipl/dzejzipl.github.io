---
title: "[PL] Shared Mailbox – współdzielone konta pocztowe"
categories:
    - Other
tags:
    - Office 365
    - PL Post

header-img: "/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/top.jpg"
subtitle:   "[PL] Shared Mailbox – współdzielone konta pocztowe"
---
![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/top.jpg)Shared Mailbox – współdzielone konta pocztowe

Ostatnio zainteresowała mnie tematyka kont pocztowych w różnych wielkościach organizacjach. Czy w  firmie, w której pracuje kilka recepcjonistek każda ma mieć swoją oddzielna skrzynkę? I do każdej z niej należy podać adres mailowy jako kontakt na stronie? Słabe rozwiązanie. Możemy to załatwić listą dystrybucyjną – tworzymy alias recepcja@nazwanaszejorganizacji dzięki czemu wiadomości spływają do każdego użytkownika, który pod dany alias jest podpięty.

Wydaje się idealne rozwiązaniem, prócz tego, że nie wiemy czy ktoś odpisał na taką wiadomość. A jeżeli odpisał to nadawca zna dokładne namiary na takiego pracownika. Nie ten efekt chcieliśmy osiągnąć.

Możemy jednak rozwiązać to inaczej: Shared Mailbox – czyli współdzielona skrzynka pocztowa. Czym wyróżnia się w Office365?

* Nie tracimy licencji, jeżeli jej objętość nie jest większa niż 50GB
* Odpowiedzi są wysyłane bezpośrednio z tej skrzynki, bez „behalf of” (czyli nie ujawniamy toższamości pracownika, który odpowiada)
* Możemy ustawić, że wszystkie wysyłane wiadomości są kopiowane do folderu wysłane w tej skrzynce, a nie skrzynce danego pracownika
* Mamy możliwość ustawienia uprawnień tylko do czytania skrzynki, bez możliwości odpowiadania
* Oraz co najlepsze – ustawienie automatycznej odpowiedzi w celu np. poinformowania, że otrzymaliśmy takiego maila
* Oraz kilka innych plusów o których przeczytacie poniżej podczas tworzenia skrzynki

Pokrótce przekażę wam instrukcję jak taką skrzynkę utworzyć.

Na początku logujemy się do panelu Administratora O365, gdzie z lewego menu wybieramy Groups > Shared Mailbox, następnie klikamy na: Add a mailbox

![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/01.png)

W okienku, które sie otworzy tworzymy konto ustawiając opis oraz adres, klikamy Add i czekamy kilka minut na stworzenie skrzynki.

Głównym krokiem, który musimy wykonać jest dodanie użytkowników konta. Robimy to poprzez wybranie skrzynki, z sekcji Members klikamy na Edit

![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/02.png)

W polu Edit mailbox permissions, ustawiamy następujące uprawnienia:

![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/03.png)

* Czytaj i zarządzaj *Wymagana opcja, aby uzyskać dostęp do Shared Mailbox – czytaj i zarządzaj mailami*
* Wyślij jako
* Wyślij jako Shared Mailbox
* Wyślij w imieniu
* Wyślij jako xyz w imieniu naszego Shared Mailbox

Jak to wygląda w praktyce?

Opcji pierwszej nie trzeba wyjaśniać, natomiast druga jest już całkiem ciekawa na nasze zastosowanie, gdyż całkowicie ukrywa nadawcę wiadomości. Tutaj zawsze jest widoczna wyżej utworzona recepcja, co mozecie zobaczyć na poniższym screenie:

![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/04.png)

Natomiast trzecia opcja wygląda następująco:

![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/05.png)

To by było na tyle, jeżeli chodzi o wysyłane wiadomości.

Co się natomiast dzieje z wiadomościami, które są wysyłane ze skrzynki? Domyślne ustawienie jest takie, że każda wiadomość wysyłana z sharedmailbox – trafia do elementów wysłanych osoby wysyłającej. Trochę złe rozwiązanie, bo jednak warto zachować ciągłość korespondencji jeżeli ma na nią odpowiedzieć inna osoba.

Do tego wykorzystamy opcję: Sent items z zaznaczonymi dwoma checkboxami:

![[PL] Shared Mailbox – współdzielone konta pocztowe](/assets/images/posts/2018/shared-mailbox-wspoldzielone-konta-pocztowe/06.png)

Dzięki zaznaczeniu tych dwóch pól – będziemy mieli pełną przejrzystość działania na tej skrzynce.

Ostatnią opcją o której chciałem wspomieć to automatyczna odpowiedź – dzięki temu możemy poinfomować użytkownika o tym, że otrzymaliśmy taką wiadomość i zaczynamy ją procesować.

Dla waszej pamięci – jeżeli chcecie, aby taka skrzynka w pełni działała, to musi być ona widoczna w książce adresowej.

To by było na tyle z tematyki Shared Mailbox. Jak byście mieli jakieś pytania, serdecznie zapraszam!
