---
title: "[PL] Azure AD - Hybrid Join"
categories:
    - Windows Server
    - Azure
tags:
    - Azure AD
    - Azure AD Connect
    - Hybrid Join
    - PL post
---
!["[PL] Azure AD - Hybrid Join"](/assets/images/top_images/AzureADTOP.jpg)Dodajmy komputery z lokalnego AD do Azure AD <3

Ostatnimi czasy zacząłem się bawić Azure AD i jego połączeniem z lokalnym AD, które mam u siebie stworzone. Powstały już trzy wpisy na ten temat:

* [Wstępna konfiguracja Azure AD Connect](https://www.piesik.me/2019/11/03/Azure-AD-Connect/)
* [Azure AD Self-Service Password Reset](https://www.piesik.me/2019/11/03/AzureAD-SSPR/)
* oraz [Azure AD Connect - Password Writeback](https://www.piesik.me/2019/11/05/AzureAD-Connect-Password-Writeback/)

W pierwszym wpisie skupiłem się na konfiguracji, natomiast w pozostałych dwóch już na użytkownikach. Dziś natomiast chciałbym się skupić na urządzeniach, które są dodane do mojego lokalnego Active Directory. Dlaczego by nie zarządzać nimi z poziomu Intune? 

Dlatego dziś skupimy się nad konfiguracją Azure AD Connect Hybrid Join.

Jest sobie urządzenie, które jest dodane do lokalnego AD tak jak na screenie:

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/03.png)

I chciałbym teraz nim zarządzać z Azure AD, więc...

Uruchamiamy AAD Connect, wybieramy Configure > **Configure Device Options**

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/01.png)

Logujemy się do Azure AD, zaznaczamy opcję **Configure Hybird Azure AD join**

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/02.png)

Wybieramy odpowiednie opcje w *Device operating systems*, przechodzimy krok dalej, wybieramy naszą domenę, wpisujemy dane do Ekonta Enterprise Admin, przechodzimy krok dalej i czekamy....

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/04.png)

Po chwili powinien pojawić nam się ekran z informacją, że konfiguracja zakończona, ale należy poczynić jeszcze kilka innych modyfikacji, więc do boju!

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/05.png)

Wpierw musimy edytować politykę GPO, która będzie wdrożona na nasze komputery. Odpalamy GPO Editor, przechodzimy do: *Computer Configuration* > *Policies* > *Administrative Templates* > *Windows Components* > *Internet Explorer* > *Security Page* > *Site to Zone Assigment List* oraz dodajemy dwie strony:

* https://autologon.microsoftazuread-sso.com
* https://device.login.microsoftonline.com
  
!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/06.png)

Następnie przechodzimy katalog niżej, do **Intranet Zone** i włączamy opcję nazwaną ***Allow updates to status bar via script***

Odświeżamy GPO za pomocą gpupdate na serwerze, wracamy na komputer kliencki, tam też odświeżamy politykę GPO i po dwóch restarach nasze urządzenie powinno pojawić się w Azure AD Devices:

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/07.png)

Jednak co mnie bardziej martwi to to, że typ **MDM** jest z domysłu ustawione na None. No niezbyt, moim MDMem jest Intune i skupmy się na tym, aby go ustawić.


Wracamy do ustawień GPO na serwerze, przechodzimy do: **Computer Configuration** > *Administrative Templates* > *Windows Components* > *MDM* i konfigurujemy **Enable automatic MDM enrollment using default Azure AD Credentials** z ustawieniem **User Credentials**

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/08.png)

Po kolejnym restarcie urządzenia, urządzenie zostanie skonfigurowane jako MDM Intune, dzięki czemu będziemy mogli nimi zarządzać z poziomu tejże usługi.

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/10.png)

### Co ważne, pamiętajmy proszę o licencjach

Dlaczego? Ponieważ sam się złapałem na tym, że logowałem się użytkownkiem, który był w lokalnym AD a komputer nie rejestrował się do MDMa. Wyjaśnienie było proste - użytkownik synchronizowany nie miał przypisanej licencji Intune pozwalającej na enrollment.

Finalnie to wygląda w taki sposób:

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/11.png)

A taki widok uzyskamy, gdy klikniemy Info.

!["[PL] Azure AD - Hybrid Join"](/assets/images/posts/AzureAD-Hybrid-Join/12.png)

I przypominam, że jest to urządzenie, które jest wpięte do lokalnego AD! :)
