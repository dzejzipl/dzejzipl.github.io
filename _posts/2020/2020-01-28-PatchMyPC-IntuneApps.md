---
title: "[PL] PatchMyPC + Intune = <3"
categories:
    - Intune
tags:
    - Software Management
    - Intune
    - PatchMyPC
    - PL post
---
!["[PL] PatchMyPC + Intune = <3"](/assets/images/top_images/IntuneTOP.png)Deployment aplikacji Win32 za pomocą PatchMyPC.

Na rynku od dłuższego czasu istnieje oprogramowanie nazwane PatchMyPC. Wcześniejsza jego historia opierała się na współpracy z WSUSem jak i SCCMem, jednakże ostatnio spojrzałem na niego bardziej przychylnym okiem, ponieważ producent postanowił dodać obsługę aplikacji Win32 w Intune.

Tak jak samo w sobie tworzenie aplikacji Win32 jest bardzo proste, tak już zarządzanie aktualizacjami już niezbyt. A tutaj mamy wszystko podane na tacy przez producenta.

Program ma jeszcze jedną zaletę - zobaczcie na ilość oprogramowania, które wspiera. Całą listę możecie zobaczyć pod [tym adresem](https://patchmypc.com/supported-products-scup-catalog).

Skoro mamy wstęp za sobą, rozpocznijmy pracę. 

Aby program mógł dziać, muszą być spełnione trzy zależności:
* Skonfigurowana rola WSUSa (po prostu zainstalowana na serwerze oraz dokończona konfiguracja)
* Certyfikaty - wygenerowane na potrzeby laba, te z SCCMa lub zaimportowane własne, które posiadamy do użycia
* Licencja na program. Jest licencja Trial, ja korzystam z licencji NRF.

Zgodnie z pierwszym krokiem musimy zainstalować rolę WSUSa oraz dokończyć konfigurację. 

W kroku drugim ściągamy aplikację z strony https://patchmypc.com/publishing-service-setup-documentation oraz ją instalujemy.

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/01.png)

Po zainstalowaniu, albo aktywujemy własną licencję albo używamy licencji Trial

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/02.png)

Krok trzeci to wygenerowanie certyfikatu / zaimportowanie istniejącego / albo użycie generowanego z SCCMa. Z racji tego, że to mój mały, skromny domowy lab to wybiorę pierwszą opcję. Klikamy na **Generate a Self-Signed Certificate**, uzupełniamy niezbędne dane oraz potwierdzamy wygenerowanie certyfikatu za pomocą **Generate Certificate**

Krok czwarty to instalacja wersji *preview* aplikacji. W tym celu przechodzimy do zakładki *About* i zaznaczamy **Install preview builds** > następnie **Upgrade Now**. 

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/03.png)

Po wstępnej konfiguracji jesteśmy gotów, aby rozpocząć główną konfigurację, czyli na przykład konfigurację Graph API, która jest używana do publikacji aplikacji.

Logujemy się do portalu Azure, przechodzimy do *Azure Active Directory* > *App Registration* > **New Registration**, uzupełniamy nazwę i klikamy **Register**.

Otwieramy nowo stworzoną aplikację, przechodzimy do zakładki **API permissions** i klikamy na **Add a permission**

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/04.png)

Z dostępnych opcji wybieramy *Microsoft Graph* oraz *Application Permissions*. Wyszukujemy po słowie kluczowym: **DeviceManagementApps.Read** i dodajemy dwa uprawnienia, które się nam wyświetlą:

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/05.png)

Po chwili klikamy na **Grant admin consent for {Domain}** i zatwierdzamy operację logując się na konto Administratora.

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/06.png)

Generujemy nowy klucz API, przechodząc do zakładki **Certificates & secrets** > *New Client Secret* i zapisujemy klucz.

Teraz wracamy do aplikacji i przechodzimy do zakładki **Advanced** i uzupełniamy dane. W polu Authority należy dodać naszą domenę, a pozostałe pola uzupełnić z spisanymi wcześniej danymi. Dla pewności możemy kliknąć *Test*, aby zobaczyć czy zostało poprawnie nawiązane połączenie z Intune.

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/08.png)

Jeżeli zaznaczymy dwie ostatnie opcje, wyłączymy niepotrzebne dla nas zakładki - dla SCCMa jak i WSUSa. Z racji tego, że w tym wpisie mnie interesuje tylko deployment do Intune, zostaną u mnie zaznaczone.

Aby wrzucić interesującą nas aplikację przechodzimy do zakładki **Intune (Preview)** > zaznaczamy programy, które nas interesują i klikamy **Apply**.

Z racji tego, że domyślnie synchronizacja jest raz dziennie, co możemy zobaczyć w zakładce *Sync Schedule*, polecam kliknąć **Run Publishing Service Sync** co wymusi natychmiastową synchronizację. Na przyszłość, możemy ustawić automatyczną synchronizację co np. 12 godzin.

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/09.png)

Po chwili przechodzimy do Intune > Apps i znajdziemy tam oprogramowanie, które zaznaczyliśmy w PatchMyPC

!["[PL] PatchMyPC + Intune = <3"](/assets/images/posts/PatchMyPC-IntuneApps/10.png)

Nie pozostało nam nic innego jak przypisać oprogramowanie do grup i rozpocząć deployment!

Jak widzicie, aplikacja jest bajecznie prosta w użyciu i uważam, że na prawdę warto jej się przyjrzeć. Szczególnie, że bezpieczeństwo naszego oprogramowania jest bardzo ważne.
