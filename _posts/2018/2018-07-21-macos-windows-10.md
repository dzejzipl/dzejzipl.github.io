---
title: "[PL] MacOS @ Windows 10"
categories:
    - Other
tags:
    - MacOS
    - PL Post

header-img: "/assets/images/posts/2018/macos-windows-10/top.png"
subtitle:   "[PL] MacOS @ Windows 10"
---
![[PL] MacOS @ Windows 10](/assets/images/posts/2018/macos-windows-10/top.png)MacOS @ Windows 10

Czasem trzeba zrobić coś sprzecznego ze swoim Informatycznym sumieniem.

Dla mnie jest to akurat odpalenie systemu macOS na sprzęcie nie przeznaczonym pod ten system, czyli np. mój domowy komputer.

Skoro mus to mus – są sytuacje, które od nas tego wymagają i trzeba się poświęcić, aby móc przetestować jedno rozwiązanie w pełni.

Ale jak to zrobić?

Potrzebujecie do tego trzech rzeczy:

* Płytę + procesor, które obsługują wirtualizacje (czyli praktycznie każda najnowsza płyta z procesorem Intel – nie sprawdzałem na AMD)
* Plik vmdk  z czystym systemem macOS do pobrania z Internetu (poogoglujcie trochę a znajdziecie bez problemu)
* VirtualBox jako nasze środowisko do wirtualizacji – do pobrania np. [https://www.virtualbox.org/wiki/Downloads]

To tyle.

Instalacja VirtualBoxa nie powinna sprawić żadnych problemów.

Już po uruchomieniu zacznijcie tworzyć nową maszynę klikając na: New. Nazwa jest zależna od was, ale zapamiętajcie ją – przyda się za chwilę.

Musicie również wybrać odpowiedni typ systemu. U mnie to wygląda tak:

![[PL] MacOS @ Windows 10](/assets/images/posts/2018/macos-windows-10/01.png)

Ps. jeżeli będzie wam się wyświetlał tylko system w wersji 32bitowej to oznacza to, że macie zainstalowanego innego wirtualizatora. W moim przypadku był to hyper-v.

Przydzielamy odpowiednią ilość ramu – np. 8096MB, wybieramy, aby nasz system użył już istniejącego dysku twardego, którego chwilę wcześniej pobraliśmy z Internetu i swój system mamy już utworzony.

Teraz musimy wprowadzić jeszcze niezbędne modyfikacje, aby macOS wiedział, że pracuje na certyfikowanym sprzęcie.

Najpierw zeedytujmy ustawienia w VirtualBoxie klikając na maszynę prawym > Setttings.

Przechodzimy do zakładki System i w polu Boot Order musimy mieć wybrane tylko Optical oraz Hard Disk

U mnie wygląda to tak:

![[PL] MacOS @ Windows 10](/assets/images/posts/2018/macos-windows-10/02.png)

Kolejna zakładka Processor  i ustawiamy ilość rdzeni, którą chcemy przekazać na nasz system. Ja dałem 4.

W ostatniej zakładce Display ustawiamy, aby system miał do dyspozycji 128MB ramu. Mało, nawet bardzo mało, ale niestety więcej się nie da.

Wyłaczamy Oracle VirtualBox i przechodzimy do punktu kolejnego.

Macie zapisaną gdzieś nazwę swojego systemu z punktu pierwszego? To teraz musicie uruchomić linię komend (CMD) z uprawnieniami Administratora i wykonać następujące komendy:

```cmd
cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage.exe modifyvm NazwaMaszyny –cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata NazwaMaszyny „VBoxInternal/Devices/efi/0/Config/DmiSystemProduct” „iMac11,3”
VBoxManage setextradata NazwaMaszyny „VBoxInternal/Devices/efi/0/Config/DmiSystemVersion” „1.0”
VBoxManage setextradata NazwaMaszyny „VBoxInternal/Devices/efi/0/Config/DmiBoardProduct” „Iloveapple”
VBoxManage setextradata NazwaMaszyny „VBoxInternal/Devices/smc/0/Config/DeviceKey” „ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc”
VBoxManage setextradata NazwaMaszyny „VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC” 1
```

Nie zapomnijcie zmienić NazwaMaszyny na swoją nazwę.

Wszystko fajnie, ale nadal na tej maszynie nie będzie żadnego połączenia z Internetem więc.. Nic na niej nie zrobimy. Musimy więc ustawić z jakiej sieci ma korzystać podczas pracy.  Wchodzimy w Settings > Network > Adapter 1 > Attached to: Bridged Adapter.

![[PL] MacOS @ Windows 10](/assets/images/posts/2018/macos-windows-10/03.png)

Uruchamiacie maszynę i macie macOS gotowego do pracy!

Serdeczne podziękowania autorowi poradnika z [https://techsviewer.com/install-macos-high-sierra-virtualbox-windows/] – dzięki niemu wszystko poszło tak gładko.
