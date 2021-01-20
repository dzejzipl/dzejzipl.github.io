---
title: "[PL] Windows 10 Insider Preview – brak miejsca na partycji systemowej"
categories:
    - Other
tags:
    - Windows 10
    - PL Post

header-img: "/assets/images/posts/2018/windows-10-insider-preview-brak-miejsca-na-partycji-systemowej/top.jpg"
subtitle:   "[PL] Windows 10 Insider Preview – brak miejsca na partycji systemowej"
---
![[PL] Windows 10 Insider Preview – brak miejsca na partycji systemowej](/assets/images/posts/2018/windows-10-insider-preview-brak-miejsca-na-partycji-systemowej/top.jpg)Windows 10 Insider Preview – brak miejsca na partycji systemowej

Tak to czasem bywa, że będąc Insiderem najnowszych wersji Windows pojawia się błąd, który nie jest opisany w żadnych fix logach ani też w error logach i trzeba szukać samodzielnie rozwiązania danego problemu.

Jakieś trzy wersje temu pojawiła mi się w systemie dodatkowa partycja, oznaczona literką D:, jednak to nie była moja partycja na dane, ale… wcześniej ukryta systemowa partycja. Nie ma problemu, ona może sobie tam być, ale bardzo, ale to bardzo często wyskakiwał komunikat jak na poniższym screenie.

![[PL] Windows 10 Insider Preview – brak miejsca na partycji systemowej](/assets/images/posts/2018/windows-10-insider-preview-brak-miejsca-na-partycji-systemowej/01.png)

No tego akurat to nie lubię jak coś mnie rozprasza w pracy.

W takich sytuacjach zajrzałbym do standardowego Create and format hard disk partitions, ale jak zdążyłem się przekonać – Windows na swoich volumenach nie pozwala na modyfikację literek 😉

Jak więc to naprawić? Z pomocą przychodzi dosyć stare narzędzie – DiskPart, które używam do tworzenia bootowalnych penów z systemami.

Polecam najpierw odpalić linię komend, następnie z jej poziomu uruchomić polecenie diskpart (koniecznie z uprawnieniami administratora!)

Następnie musimy wykonać kilka komend:

list disk // listujemy dyski

select disk // wybieramy dany dysk

list volume // listujemy volumeny na wybranych dysku

select volume // wybieramy dany volumen

remove letter=x // usuwamy przypisaną literę

![[PL] Windows 10 Insider Preview – brak miejsca na partycji systemowej](/assets/images/posts/2018/windows-10-insider-preview-brak-miejsca-na-partycji-systemowej/02.png)

W moim przykładzie pojawia się literka D:, więc po prostu usunąłęm ten punkt przypisania.

Wszystko? Wszystko. W tak krótki sposób usunąłem wyskakujący co 2-3 minuty komunikat.

Have fun.
