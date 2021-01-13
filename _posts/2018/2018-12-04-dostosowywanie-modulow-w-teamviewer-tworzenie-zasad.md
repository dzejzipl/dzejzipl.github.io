---
title: "[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad"
categories:
    - Intune
tags:
    - PL Post
    - TeamViewer
---
![[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad](/assets/images/posts/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/top.jpg)Dostosowywanie modułów w TeamViewer + tworzenie zasad

TeamViewer to zapewne program, który znacie tylko pod jedną postacią – aby móc sterować własnym komputerem z dala od domu. Jednak cały TW – to jest zbiór sporej ilości wersji oprogramowania, które możemy podzielić między innymi na:

* TeamViewer
* TeamViewer QuickSupport
* TeamViewer Host
* TeamViewer QuickJoin

A co najlepsze – każda z powyższych pozycji występuje na różne platformy, więc mamy bardzo, ale to bardzo wiele możliwości, aby móc sterować urządzeniami naszych użytkowników.

W dzisiejszym wpisie chciałbym się skupić na tym, aby wdrożyć moduł o nazwie Host, który pozwala tylko na podłączenie się do danego urządzenia. Nie umożliwia kontrolowania innego urządzenia, które jest np. dodane do naszego konta. Dla mnie, to co jest najważniejsze to możliwość brandowania oraz przypisywania do odpowiednich grup takiego urządzenia, gdzie uruchomimy instalację. Pokażę wam dwa screeny – po lewej stronie widzicie zwykły moduł Host, natomiast po prawej – ze zmienionym wyglądem. 

![[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad](/assets/images/posts/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/01.png)

Spora różnica, prawda? Dodajemy indywidualne tło, logo, tekst – wszystko to, co pozwoli zidentyfikować naszą firmę. 

W jaki sposób tego dokonałem? Do modyfikowania instalacji należy mieć minimum licencję Premium lub Corporate. Jeżeli będziecie mieli tą drugą – będzie także możliwość ściągania plików .msi, które bardzo się przydadzą. 

Musimy utworzyć grupę do której będą dodawane nasze urządzenia. Ja utworzyłem sobie grupę nazwaną „Remote Support”

![[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad](/assets/images/posts/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/02.png)

Następnie stworzyłem nową „Zasadę” z odpowiednimi ustawieniami

![[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad](/assets/images/posts/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/03.png)

Jako kolejny krok utworzyłem nowy moduł kliencki, który będzie automatycznie dodawał urządzenia do grupy „Remote Support” oraz przypisywał zasady „Remote Support – Rules”. Tak samo zmienię jego wygląd na trochę inny.

![[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad](/assets/images/posts/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/04.png)

W momencie kliknięcia na „Host” pojawi nam się okienko z możliwością edytowania klienta. Zobaczcie jak to u mnie wygląda:

![[PL] Dostosowywanie modułów w TeamViewer + tworzenie zasad](/assets/images/posts/dostosowywanie-modulow-w-teamviewer-tworzenie-zasad/05.png)

Tak stworzony moduł posiada swój link, który możemy przekazać naszemu użytkownikowi, aby ściągnął plik instalacyjny, który pozwoli nam na dodanie jego urządzenia do grupy urządzeń. 

Jak sami widzicie, tworzenie zasad jest bajecznie proste. Możemy utworzyć różne grupy zasad, zależnie od typu urządzeń jak i pracowników, a praca z tym programem jest mega wygodna. 
