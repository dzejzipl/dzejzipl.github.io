---
title: "[PL] Dynamiczne grupy użytkowników w AAD"
categories:
    - Azure
tags:
    - AAD
    - PL Post

header-img: "/assets/images/posts/2018/dynamiczne-grupy-uzytkownikow-w-aad/top.jpg"
subtitle:   "[PL] Dynamiczne grupy użytkowników w AAD"
---
![[PL] Dynamiczne grupy użytkowników w AAD](/assets/images/posts/2018/dynamiczne-grupy-uzytkownikow-w-aad/top.jpg)Dynamiczne grupy użytkowników w AAD

Praktycznie w każdej firmie istnieje alias, dzięki któremu będziemy mogli wysłać wiadomość do wszystkich użytkowników. O praktyczności zastosowania takiego aliasu nie muszę nikogo przekonywać – dzięki temu komunikacja wewnętrzna przebiega o wiele sprawniej.

Stworzenie aliasu nie jest problemem. Dodajemy użytkowników, pamiętamy o aktualizacji jeżeli któryś z pracowników odchodzi lub nowy przychodzi.. I wszystko działa.

A gdyby tak zaatomatyzować taką listę dystrybucyjną? Niech każdy nowo zatrudniony pracownik będzie automatycznie dodawany do tej listy. A może mamy oddzielne listy dla odpowiednich działów i chcemy też to zautomatyzować?

Parametry użytkownika są bardzo fajna funkcją w Active Directory. Job TItle, Department, City… Na podstawie odpowiednio wybranych parametrów tworzymy automatyczne listy dystrybucyjne.

W moim przykładzie utworzę grupę dystrybucyjną (DG) dla kilku użytkowników, którzy mają w polu City: Lodz oraz Country : Poland. Taka DG będzie się nazywała: PLLodz@dzejzibloguje.pl

Na początek wchodzimy w nasz katalog Azure AD > Groups > New Group

![[PL] Dynamiczne grupy użytkowników w AAD](/assets/images/posts/2018/dynamiczne-grupy-uzytkownikow-w-aad/01.png)

Kolejnym krokiem będzie wybranie typu grupy, w tym przypadku: Office 365. Jako nazwę: PLLodz co napisałem kilka linijek wyżej. Opis jest naszą dowolnością. Najważniesze jest dla nas wybranie zasad przypisania użytkowników do grupy. Dla tego przykładu: Dynamic User.

I dopiero teraz zaczyna się najlepsza zabawa. Musimy stworzyć swoje zapytanie na podstawie którego będziemy automatycznie wybierać użytkowników.

W podstawowym edytorze wybieramy jeden parametr, ale przecież chcemy użyć dwóch, dlatego „Advanced rule” i tworzymy swoje zapytanie.

Przypomnę, interesują nas dwa parametry:

City = Lodz

Country = Poland

Zapytania tworzymy w sposób następujący:

user.parametr –operator2 „Wartosc” –operator1 user.parametr –operator2 „Wartosc” i tak dalej i tak dalej…

Gdzie pod:

operator1 podstawiamy: -and, -or, -not oraz inne parametry, które pozwolą na stworzenie wyrażenia regularnego. Dokładna lista pod tym linkiem

operator2 podstawiamy wartość, która pozwoli nam na odpowiednie sprawdzenie zawartości atrybytu. Dokładną listę poznacie pod tym linkiem.

Jeżeli już wiemy w jaki sposób tworzyć zapytania, stwórzmy takie, które będzie odpowiednie na nasze potrzeby.

user.city -eq „Lodz” -and user.country -eq „Poland”

Tak skonstruowane zapytanie zapisujemy klikając na „Add query” i Create.

![[PL] Dynamiczne grupy użytkowników w AAD](/assets/images/posts/2018/dynamiczne-grupy-uzytkownikow-w-aad/02.png)

W momencie jak grupa zostanie stworzona, możemy wejść w Groups > PLLodz i wyświetlic detale. U mnie wygląda to tak:

![[PL] Dynamiczne grupy użytkowników w AAD](/assets/images/posts/2018/dynamiczne-grupy-uzytkownikow-w-aad/03.png)

Działa!

Po dodaniu użytkownika oraz ustawieniu odpowiednich parametrów użytkownik zostanie automatycznie dodany do grupy, którą przed chwilą stworzyliśmy.

To wszystko.

Nie było to mega trudne, prawda? A bardzo ułatwia życie pracownikom, którzy zajmują się skrzynkami mailowymi
