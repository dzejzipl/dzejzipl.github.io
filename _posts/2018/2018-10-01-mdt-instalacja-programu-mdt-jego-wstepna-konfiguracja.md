---
title: "[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"
categories:
    - Krótko
tags:
    - Krótko
    - PL Post
---

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/top.jpg) [MDT] Instalacja programu MDT jego wstępna konfiguracja

W pierwszym poście z tej serii dodaliśmy do naszego Windows Server rolę WDS – Windows Deployment Services oraz dodaliśmy obraz bootowania i pierwszy obraz do instalacji Windows Server 2016. Wszystko standardowo, z kliknięciem Next, Next i tym podobne.

Natomiast w tym wpisie chciałbym poruszyć tematykę programu Microsoft Deployment Toolkit, czyli popularnie zwanego MDT. Jest to darmowy program do tworzenia jak i modyfikowania instalacji systemu Windows. Dzięki niemu możemy zrobić obraz, który po uruchomieniu z sieci sam uruchomi instalację a na samym końcu wyśle nam wiadomość e-mail z adresem IP komputera. Jest wiele możliwości konfiguracyjnych w tym programie. Domyślam się, że większości nawet nie znam, ale dzięki tej serii postów chciałbym wam przedstawić te, które znam.

Co ciekawe, sam program jest darmowy oraz jest ciągle rozwijalny. Znam kilka na prawdę bardzo dużych firm, które z niego korzystają jako, że jest to podstawowe narzędzie do pracy.

Naszą zabawę rozpoczniemy od ściągnięcia MDT ze strony [https://www.microsoft.com/en-us/download/details.aspx?id=54259] i przejścia przez standardową instalację.

Drugim krokiem jest zainstalowanie Windows ADK (Assessment and Deployment Kit), który jest zestawem oprogramowania do modyfikowania instalacji Windowsa. Na potrzeby tekstów pobieramy go z linku [https://go.microsoft.com/fwlink/?linkid=873065] i instalujemy z ustawieniami jak na poniższym screenie:

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/01.png)

Po poprawnym zainstalowaniu dwóch programów zacznijmy od stworzenia Deployment Share, czyli miejsca, gdzie będzie trzymana cała konfiguracja naszego MDT. Wykorzystam do tego dysk D, ale już inny folder niżeli ten z WDS. Aby to zrobić, uruchamiamy program Deployment Workbench i klikamy prawym na Deployment Share > New Deployment Share

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/02.png)

Zostawiam domyślną nazwę folderu, natomiast w drugim kroku ustawiamy nazwę udostępnionego folderu:

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/03.png)

Jak widzicie, będzie można się do niego dostać za pomocą ścieżki \\WDS\DeploymentShare$ – dolar na końcu ponieważ będzie to folder ukryty. Ustawiamy opis, pozostawiamy zaznaczone opcje tak jak są domyślnie i już po chwili powinien ukazać się naszym oczom taki komunikat:

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/04.png)

Po utworzeniu takiego Deployment Share należy dodać nasz system, który poddamy modyfikacji. Ja wykorzystam do tego celu – Microsoft Windows Server 2016, ale jeszcze wcześniej tworząc nowy folder wewnątrz, aby nie mieć bałaganu jeżeli dodam Windows 10.

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/05.png)

Po utworzeniu folderu rozpoczynamy poprzez klik prawym > Import Operating System, z wybraną pierwszą opcją, czyli: „Full set of source files”

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/06.png)

W polu Destination ustawię Windows Server 2016, w kolejnym kroku Next i rozpocznijmy import, który potrwa chwilę.

!["[PL] [MDT] Instalacja programu MDT jego wstępna konfiguracja"](/assets/images/posts/mdt-instalacja-programu-mdt-jego-wstepna-konfiguracja/07.png)

Ten sam krok powtórzę dla Windows 10
