---
title: "[PL] „Password-less” w Azure AD!"
categories:
    - Intune
tags:
    - Intune
    - PL Post
---

!["[PL] „Password-less” w Azure AD!"](/assets/images/posts/password-less-w-azure-ad/top.png)„Password-less” w Azure AD!

Kilka dni temu wyszła nowa funkcja, która pozwala naszym użytkownikom na większe dbanie o bezpieczeństwo. Została nazwana przez Microsoft jako „Password-less”.

Co w skrócie robi ta funkcja? Pozwala na zalogowanie użytkownika za pomocą odpowiedniego kliknięcia w aplikacji w naszym telefonie zamiast wpisywania hasła. Pozornie może się to wydawać mniej bezpieczne, ale…. Ma to dość duży sens. Gdyby haker miał dostęp do tego co wpisujemy od razu zobaczy nasze hasło. A tak? Tylko login.

Jako, że funkcja jest obecnie w funkcji public preview to zobaczymy jak się ją instaluje.

Rozpoczynamy od zainstalowania modułu Azure-ADPReview używając komendy: Install-Module -Name AzureADPreview

Kolejnym krokiem jest zalogowanie się za pomocą komendy: connect-azureAD

i wykonanie polecenia:

```powershell
New-AzureADPolicy -Type AuthenticatorAppSignInPolicy -Definition '{„AuthenticatorAppSignInPolicy”:{„Enabled”:true}}' -isOrganizationDefault $true -DisplayName AuthenticatorAppSignIn
```

!["[PL] „Password-less” w Azure AD!"](/assets/images/posts/password-less-w-azure-ad/01.png)

I teraz następuje najlepsza rzecz.
Aby użytkownik mógł się zalogować bez podania hasła, ale z wybraniem numeru, który się wyświetlił na ekranie, to musimy dokonać kilku modyfikacji w aplikacji. Zajrzycie proszę do poprzedniego wpisu gdzie dodaliśmy aplikację do uwierzytelniania za pomocą kodu generowanego co 60 sekund.

Rozwijając menu, które jest przypisane do konta musimy wybrać **Enable phone sign-in**

!["[PL] „Password-less” w Azure AD!"](/assets/images/posts/password-less-w-azure-ad/02.png)

oraz spełnić kilka warunków:

!["[PL] „Password-less” w Azure AD!"](/assets/images/posts/password-less-w-azure-ad/03.png)

* Aplikacja musi mieć dostęp do kontaktów
* Nasz telefon musi być zarejestrowany w Intune oraz przypisany tylko do tego konta
* Muszą być ustawione dodatkowe opcje odblokowywania telefonu

Jeżeli spełnimy te 3 wymagania, będziemy mogli ustawić autentyfikację bez użycia hasła.

Jak to wygląda z poziomu end-usera? Spójrzmy:

!["[PL] „Password-less” w Azure AD!"](/assets/images/posts/password-less-w-azure-ad/04.png)

Natomiast powiadomienie na telefonie wygląda w sposób następujący:

!["[PL] „Password-less” w Azure AD!"](/assets/images/posts/password-less-w-azure-ad/05.png)

Prawda, że fajne? 😀
