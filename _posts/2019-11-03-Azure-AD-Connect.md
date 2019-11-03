---
title: "[PL] Azure AD Connect"
categories:
    - Windows Server
    - Azure
tags:
    - Azure AD
    - Azure AD Connect
    - PL post
---
!["[PL] Azure AD Connect"](/assets/images/top_images/AzureADTOP.jpg)A gdyby tak połączyć nasze środowisko lokalne z Azure AD?

W poście tym chciałbym pokazać jak połączyć AAD z lokalnym AD, dzięki czemu będziemy mogli mieć jedno środowisko.

Pierwszy przykłąd to taki, że tworzymy konto użytkownika lokalnie, jest ono synchronizowane do chmury, dzięki temu taki użtkownik będzie mógł się zalogować do portalu Office swoimi danymi.

Kolejny przykład - synchronizacja haseł. Użytkownicy logują się do chmury hasłem, które używają w on premise. Jeżeli zmienimy hasło lokalnie, hash tego hasła jest replikowany do chmury (automatycznie co dwie minuty)

Jest sporo innych zastosowań, jednak na początku chciałbym się skupić na tych dwóch.

### Rozpocznijmy pracę

Logujemy się do naszego kontrolera domeny, ściągamy Azure AD Connect i rozpoczynamy instalację

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/01.png)

W pierwszym kroku wybieram instalację ekspresową, ponieważ nie chcę zmieniać konta, które będzie użyte do synchronizacji oraz nie chcę ustawiać innego serwera SQL, ponieważ jest to moje środowisko testowe.

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/02.png)

Loguję się do konta Azure z danymi użytkownika o uprawnieniach globalnego administratora oraz wpisuję poświadczenia dla administratora domeny:

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/03.png)

Jeżeli już się zalogujemy, otrzymamy informację o domenach. U mnie jest sytuacja, że domena lokalna **piesik.online** jest juz dodana w Azure AD jak i zweryfikowana. W przypadku posiadania nazwy domeny lokalnej, która nie jest dodana do AAD, należy poczynić dodatkowe kroki i skonfigurować ją w **Active Directory Domains and Trust**.

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/04.png)

Rozpoczynamy instalację, czekamy na wykonanie konfiguracji i naszym oczom pojawi się następujący komunikat:

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/05.png)

Jak widać na załączonym screenie, nie mam ustawionego kosza dla mojego AD, dlatego też zrobię to poleceniem powershell:

```powershell
Enable-ADOptionalFeature 'Recycle Bin Feature' -Scope ForestOrConfigurationSet -Target nazwadomeny
```

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/06.png)

Ten krok oczywiście jest dodatkowy, z racji tego, że moja domena jest dosyć świeża i dopiero ją zaczynam budować to kosz był wyłączony.

Po wstępnej konfiguracji możemy przejść do portalu Azure > Azure AD > **Azure AD Connect** gdzie naszym oczom powinien pojawić się następujący widok:

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/07.png)

Jeżeli przejdziemy do zakładki Users, zobaczymy naszych użytkowników z lokalnego AD:

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/08.png)

Tak samo grupy:

!["[PL] Azure AD Connect"](/assets/images/posts/Azure-AD-Connect/09.png)

To na tyle jeżeli chodzi o wstępną konfigurację

W kolejnych wpisach postaram się pokazać więcej potencjału tego rozwiązania.
