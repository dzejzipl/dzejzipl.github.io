---
title: "[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"
categories:
    - Krótko
tags:
    - Krótko
    - PL Post
---

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/top.jpg) [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu

Geneza tej serii postów jest prosta.

Z racji tego, że muszę coraz częściej instalować nowe wersje Windows Server / Windows 10, denerwuje mnie ciągłe klikanie Next, Next podczas instalacji. Biorąc pod uwagę, że jestem świeżo po reinstalacji to nie miałem czasu postawić od nowa środowiska do Deploymentu.

Co chcę przedstawić? Jak wygląda moje środowisko pracy. W pierwszym poście opiszę w jaki sposób instaluję rolę Windows Deployment Services na Windows Server 2016 oraz co najważniejsze – dodamy czysty obraz systemu do pierwszej, testowej instalacji.

Jako podstawę użyłem Windows Server 2016 Standard, który działa nie jest wpięty do domeny i będzie działał jako serwer standalone. Posiada dwie partycje – C oraz D. Na pierwszej standardowo zainstalowany jest system natomiast na drugiej będzie znajdowała się baza obrazów.

W pierwszym kroku należy zainstalować usługę Windows Deployment Services na naszym serwerze. Możemy to wykonać z poziomu GUI jak i PowerShella. Na potrzeby tego wpisu przejdźmy przez ten krok używając GUI.

Instalujemy rolę WDS z Server Roles przechodząc przez domyślną konfigurację:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/01.png)

Po poprawnym zainstalowaniu roli należy ją skonfigurować, dlatego znajdźmy w menu Server Manager > WDS > a następnie nasz serwer > Windows Deployment Services Management Console

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/02.png)

W nowo otwartym oknie jeszcze raz znajdźmy swój serwer i rozpocznijmy jego konfigurację:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/03.png)

W pierwszym kroku klikamy Next, natomiast w drugim musimy zdecydować jaki typ serwera wybieramy. Z racji tego, że to ma być wersja Standalone to zaznaczam tę opcję:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/04.png)

W kroku trzecim wybieramy gdzie mają znajdować się pliki konfiguracyjne oraz wszystkie obrazy naszej usługi. Ja przeznaczę na to dysk D z folderem RemoteInstall

Krok czwarty jest dosyć ważny, musimy wybrać czy nasz serwer będzie odpowiadał na próby pobrania obrazu bootowania do instalacji:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/05.png)

Skoro jest to moje własne środowisko, oddzielone od domowego to ustawiłem opcję, aby WDS odpowiadał na wszystkie zapytania – zarówno „znanych jak i nieznanych” komputerów. Nie chce mi się ich akceptować ręcznie.

W ostatnim kroku otrzymamy informację, że nasz serwer został skonfigurowany  i czy chcemy dodać teraz obraz do serwera. Odznaczcie opcję i zakończcie konfigurację serwera.

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/06.png)

Na początku musimy mieć obraz bootowania, czyli możliwość uruchamiania całego środowiska z sieci. Taki plik znajduje się na każdym pliku ISO z Windows. Zarówno Server jak i Client w folderze Sources. Taki plik boot.wim musi zostać dodany do folderu Boot Images, więc dodajmy go tam:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/07.png)

Możemy przejść przez konfigurator zachowując domyślnie opcje i już po chwili nasz pierwszy obraz zostanie dodany:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/08.png)

I zróbmy teraz test czy wszystko działa poprawnie. Utworzyłem nową maszynę wirtualną w tej samej sieci co WDS, uruchomiłem bootowanie z sieci….

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/09.png)

I jak widać wszystko działa poprawnie. Jeżeli wciśniemy klawisz Enter to automatycznie zacznie się ładować obraz bootowania.

Ale co nam po samym obrazie systemu skoro przydało by się w ogóle zainstalować jakiś system z sieci, choćby klikając Next, Next, Next…..

Na początku utwórzmy grupę obrazów nazwaną Windows Server 2016

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/10.png)

I dodajmy do niej pierwszy obraz instalacyjny:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/11.png)

Tym razem musimy skorzystać z pliku install.wim, który również znajduje się w folderze Sources.

Jeżeli plik install.wim posiada więcej  niż jeden system do zainstalowania zobaczymy taki widok:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/12.png)

Z racji tego, że ja potrzebuję mieć zawsze instalowaną opcję Standard z GUI, odznaczam pozostałe trzy i zostawiam zaznaczoną tylko drugą i klikam NEXT.  W kolejnym oknie należy potwierdzić import obrazu, kliknąć Next i poczekać chwilę na zakończenie importu. Poprawnie dodany obraz będzie wyświetlał się nam w programie:

!["[PL] [MDT] Instalacja WDS na Windows Server 2016 oraz dodanie pierwszego obrazu"](/assets/images/posts/mdt-instalacja-wds-na-windows-server-2016-oraz-dodanie-pierwszego-obrazu/13.png)

Tak samo teraz jak odpalimy instalację na dowolnym kliencie, będziemy mieli do wyboru nowo dodany obraz instalacji:

Co prawda nadal podczas instalacji trzeba klikać Next, Next… Ale od czegoś trzeba rozpocząć, prawda?
