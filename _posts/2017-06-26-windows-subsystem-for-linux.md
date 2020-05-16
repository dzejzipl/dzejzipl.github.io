---
title: "[PL] Windows Subsystem for Linux"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/top.jpg)Windows Subsystem for Linux

Windows ❤ Linux…

Tak, ostatnio bardzo często można zobaczyć taki slogan we wszelkich prezentacjach Microsoftu.

Tak, jest to bardzo dziwne, nawet dla mnie.

Ale co jest dla mnie o wiele wygodniejsze to to, że jakis czas temu dostaliśmy możliwość odpalenia Ubuntu bezpośrednio wewnątrz Windowsa.

Oczywiście, nie jest to pełnoprawne Ubuntu, bo nie ma np. środowiska graficznego, ale kto potrzebuje GUI jak mamy w bardzo mocno rozbudowane komendy?

Dzięki temu rozwiązaniu możemy bez problemu wychodzić z VIMa mając uruchomionego PowerShella.. A może z problemami wychodzić z VIMa? Dla przypomnienia, wychodzimy poprzez ESC > :q 😉

Tak czy siak – dla mnie o wiele szybciej jest uruchomić taki WSL (Windows Subsystem for Linux) niżeli wejść na stronę NASKu i np. sprawdzić ważność domeny.

Tak samo – do szybkich prac mam wystawionego LAMPa i tam sobie wrzucam np. WordPressa i coś testuję.

Kolejnym przykładem będzie Docker o którym też będzie kiedyś artykuł.

Przykłady można mnożyć, a jeżeli ktoś używa Linuxa w codziennym zastowaniu to myślę, że spokojnie może się przestawić na WSL.

A teraz… Przejdźmy trochę do rzeczy technicznych, czyli instalacji.

Na początek musimy zainstalować WSL na naszym komputerze, w tym celu wchodzimy w Control Panel > Programs and features > Turn Windows features on or off i w okienku, które nam wyskoczy zaznaczamy Windows Subsystem for Linux (Beta) tak jak na screenie poniżej:

![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/01.png)

Po tej operacji musimy zrestartować komputer.

Kolejnym krokiem jest uruchomienie Settings > Update and Security> For Developers > i tutaj zaznaczamy opcję Developer mode i potwierdzamy instalację:

![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/02.png)

Ostatnim krokiem będzie włączenie konsoli PowerShell i wpisanie tajemniczego polecenie bash, które pozwoli nam na zainstalowanie WSL na naszym komputerze.

![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/03.png)

Teraz nadszedł czas na konfigurację:

Wpisujemy nazwę swojego użytkownika oraz hasło:

![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/04.png)

Po stworzeniu swojego użytkownika nadszedł czas na zmianę hasła do konta roota, ponieważ konto główne nie ma hasła. W tym celu wpisujemy: sudo su, następnie wpisujemy passwd i ustawiamy hasło roota tak jak widać na poniższym screenie.

![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/05.png)

Po tej czynności możemy już bez problemu aktualizować subsystem i na nim pracować.

![[PL] Windows Subsystem for Linux](/assets/images/posts/windows-subsystem-for-linux/05.png)

Po wyjściu z konsoli PowerShella możemy ponownie wejść w WSL poprzez wpisanie polecenia bash

Miłej zabawy! 🙂
