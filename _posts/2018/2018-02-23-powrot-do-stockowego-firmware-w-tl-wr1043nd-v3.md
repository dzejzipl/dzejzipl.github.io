---
title: "[PL] Powrót do stockowego firmware w TL-WR1043ND V3"
categories:
    - Other
tags:
    - TPLink
    - PL Post

header-img: "/assets/images/posts/2018/powrot-do-stockowego-firmware-w-tl-wr1043nd-v3/top.jpg"
subtitle:   "[PL] Powrót do stockowego firmware w TL-WR1043ND V3"
---
![[PL] Powrót do stockowego firmware w TL-WR1043ND V3](/assets/images/posts/2018/powrot-do-stockowego-firmware-w-tl-wr1043nd-v3/top.jpg)Powrót do stockowego firmware w TL-WR1043ND V3

Dziś będzie krótko. Nawet bardzo krótko.

Trafił mi się router do zabawy TL-WR1043ND V3, który jako software miał wgranego Gargoyle… No to postanowiłem go ożywić i wgrać mu stockowego firmware, aby zobaczyć co dalej. Możliwe, że później wrócę do Gargoyle.

Niby prosta sprawa – ściągamy oryginalny soft ze strony producenta, wgrywany za pomocą interfejsu i kończymy pracę… No ale gdyby tak było, nie pisałbym tego wpisu.

Oryginalne oprogramowanie do którego chcemy wrócić zawiera w sobie bootloader, który nie jest „blokowany” przez Gargoyle i uniemożliwia nam to wgranie stockowego softu.

Jak to naprawić? Usuńmy początkową część pliku! 🙂

Ja w swoich walkach z tym tematem użyłem polecenia dd, które znajdziemy w każdym Linuxie (oraz zapewne macOS – nie sprawdzałem), ale też w Windowsie za pomocą WSL (Windows Subsystem for Linux) – polecam zajrzeć do tego wpisu.

Tak więc kontynuując, ściągnąłęm odpowiednią wersję (dla hardware w wersji 3 – co jest ważne), wrzuciłem do folderu, zmieniłem nazwę pliku na or.bin a następnie wydałem polecenie:

dd if=or.bin of=tplink.bin skip=257 bs=512

Przez co skroiliśmy plik o odpowiednią ilość bajtów, aby usunąć bootloader i poprawnie wgrać stockowy firmware.

Także drodzy czytelnicy – robicie to na własną odpowiedzialność i nie biorę odpowiedzialności za uszkodzone routery 😉

Ps – dojście do tego wszystkie zajęło mi kilka godzin, dlatego.. Macie to tutaj jak na tacy.
