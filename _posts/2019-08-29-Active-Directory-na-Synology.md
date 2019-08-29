---
title: "[PL] "Active Directory" na Synology NAS"
categories:
    - Synology
tags:
    - Synology
    - Active Directory
    - Samba
    - PL post
---
!["[PL] "Active Directory" na Synology NAS"](/assets/images/top_images/SynologyTOP.jpg)

Znam bardzo dużą ilość firm, które dając komputer swojemu pracownikowi dają mu pełne prawa administratora, możliwość instalowania wszystkiego co chce, a także - brak backupu, bo ufają, że pracownik sam zadba o backup i bezpieczeństwo.

Sama idea **Active Directory** jest dla mnie bardzo ważna. Mamy pewną władzę nad urządzeniami, mamy możliwość personalizacji danego urządzenia. Mamy również możliwość zadbania o backup danych.

Jednakże dlaczego tak mało firm zechce wprowadzić to do swojej struktury IT? Dlatego, że są to gigantyczne koszty. Często takie, których nie da się przeskoczyć. Bo skoro działa, to dlaczego to ruszać?

Idealnie się tutaj nada mem:

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/meme.png)

> Źródło: https://me.me/i/everything-worksfine-what-doweevenpavnou-for-something-isntworking-what-do-we-even-pay-20383749

Tak więc, aby uniknąć tego problemu chciałbym wam przedstawić alternatywę w postaci **Synology Directory Server** opartej na protokole **Samba**, którą możemy wdrozyć na naszym urządzeniu.

Jak w poprzednim poście pisałem, wszystko oprę na Synology DS620 Slim.

Założenia są proste:
* Mamy posiadać Active Directory oparte na Sambie. Dla uproszczenia będę pisał **AD**
* Użytkownicy co 180 dni mają zmieniać hasła
* Dzięki wdrożeniu grup oraz użytkowników będę mógł łatwiej zarządzać dostępem do folderów

## A więc rozpocznijmy Instalację

Wszystko należy rozpocząć od zainstalowania dwóch pakietów - **Synology Directory Server** oraz **DNS Server**, który wskoczy nam jako zależny pakiet.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/01.png)

Po zainstalowaniu znajdziemy je w górnym menu - polecam także wyciągnąć je sobie na pulpit.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/02.png)

Naszym oczom ukaże się kreator, który poprowadzi nas przez niezbędne kroki konfiguracyjne. Postawiłem sobie domenę pod adresem: **Piesik.online**, tak jak widać na screenie:

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/03.png)

Ustawiamy hasło dla Administratora domeny, klikamy Finish i czekamy na zakończenie kreatora.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/04.png)

## Dodawanie komputera do domeny

Skoro stworzyliśmy taką swoją domenę, to warto by było dodać do niej pierwsze urządzenie, aby móc rozpocząć zabawę, prawda?

Należy to zrobić w dokładnie taki sam sposób jak dodawanie komputera do domeny Windowsowej, czyli dokładne informacje są na screenie:

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/05.png)

## Tworzenie użytkownika w domenie

Jeżeli już dodaliśmy nasz komputer do domeny, można by zrobić pierwszego użytkownika, który się zaloguje na swoją stację roboczą.

Przechodzimy do Synology Directory Services, następnie do zakładki **Users and Computers**, wybieramy **Add** > **User**, gdzie na pierwszej stronie uzupełniamy wszystkie niezbędne informacje.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/06.png)

Jeżeli wcześniej stworzyliśmy jakieś grupy użytkowników, to na drugim oknie możemy od razu dodać użytkownika do tych grup, albo przejść dalej jeżeli nie chcemy go dodawać do innych grup niż domyślna - **Domain Users**


## Praca z grupami użytkowników

W Active Directory zarządzanie dostępami działa na zasadzie grup dostępowych. Nie masz grupy? Nie masz dostępu. Poproś odpowiednią osobę o dodanie do grupy. 

### Nie powinno się dodawać pojedyńczych użytkowników do folderów sieciowych

Ponieważ jest to niewygodne. Musimy przeklikać 50 folderów i sprawdzić do czego taki użytkownik ma mieć nadal dostęp. A tak, to tylko wyrzucamy z grupy i to wszystko.

Także na potrzeby tego tekstu utworzymy teraz grupę nazwaną: "**HR Team**"

Ponownie przechodzimy do Synology Directory Services > **Users and Computers**, wybieramy **Add** > **Group** i uzupełniamy niezbędne informacje.

#### Co ważne, starajmy się unikać polskich znaków jak i spacji. Będzie później się wygodniej pracowało

W przypadku, gdy **nie jest** to grupa dystrybucyjna, nie musimy tworzyć adresu email do niej.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/07.png)

Stworzyliśmy grupę? Świetnie, dodajmy teraz do niej użytkownika. Robimy to poprzez dwuklik na nowo stworzoną grupę i przejście do zakładki **Members**, gdzie zaznaczamy, który użytkownik ma mieć dostęp do grupy.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/08.png)

Świetnie! Mamy stworzonego użytkownika, dodaliśmy go do grupy, to teraz stwórzmy nowy folder gdzie tylko ta grupa dostępowa będzie miała dostęp, a cała reszta będzie miała brak dostępu.

## Tworzenie nowego udziału dla specyficznej grupy

Nowy udział robimy tak jak napisałem to w pierwszym poradniku. O, [tym tutaj](https://www.piesik.me/2019/08/26/Rozpoczynamy-prace-z-Synology/)

Czyli przechodzimy do Control Panel > **Shared folders** > **Create** > **New**

Jedyne co nam się zmienia, to... Wybór grupy, która ma mieć dostęp do tego folderu. Zobaczcie:

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/09.png)

Z górnego menu musiałem wybrać **Domain group** i potem nowo utworzoną grupę.

### A co, jeżeli część użytkowników ma mieć dostęp *Read*, a część *Read-Write* ?

Polecam od razu w sobie wyrobić nawyk tworzenia dwóch grup dla danego zadania. Z dopiskiem na końcu **RO** - dla *Read Only** oraz **RW** - dla *Read-Write*.

Zaznaczamy odpowiednie uprawnienia i klikamy OK.

Po tej operacji użytkownik powininen się dostać bez problemu do folderu.

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/10.png)

## A co z regułami haseł?

Chciałbym, aby użytkownicy musieli zmienić hasła co 180 dni oraz była historia haseł.

Jak to zrobić?

Należy przejść do **Synology Directory Server** > **Domain Policy**. Tam mamy możliwość skonfigurowania odpowiednich reguł. 

Jak widzicie, ustawiłem w sposób następujący:

![„[PL] "Active Directory" na Synology NAS"](/assets/images/posts/Active-Directory-na-Synology/11.png)

* Maksymalny czas ważności hasła to 180 dni
* Minimum 7 znaków
* Hasło nie może się powtarzać z poprzednimi dwunastoma hasłami

### A co dodatkowo ustawiłem to blokowanie konta

Dlaczego tak? Kwestia bezpieczeństwa. U mnie konta mają zostać zablokowane po pięciu próbach na 60 minut, ale licznik ma się restartować już po 30 minutach.

Warto taką opcję także zaznaczyć.

## Co dalej?

W kolejnym poście pokażę wam w jaki sposób ustawić profile mobilne dla użytkowników, którzy pracują w Synology Directory Server