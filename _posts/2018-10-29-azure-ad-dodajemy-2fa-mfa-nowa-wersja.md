---
title: "[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"
categories:
    - Azure AD
tags:
    - Azure AD
    - MFA
    - PL Post
---

!["[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"](/assets/images/posts/azure-ad-dodajemy-2fa-mfa-nowa-wersja/top.jpg)Azure AD – dodajemy 2FA (MFA) – nowa wersja

Ponad półtora roku temu powstał [wpis o włączaniu MFA](https://www.piesik.me/2017/03/15/azure-ad-dodajemy-2fa-mfa/) w Microsoft Azure dla poszczególnych kont użytkowników. Z racji tego, że się trochę zdezaktualizował chciałbym wam przedstawić nową wersję.
Rozpoczynamy od ustawienia niezbędnych opcji na stronie: [https://account.activedirectory.windowsazure.com/UserManagement/MfaSettings.aspx] dla przykładu zaufane adresy IP oraz sposoby weryfikacji.

!["[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"](/assets/images/posts/azure-ad-dodajemy-2fa-mfa-nowa-wersja/01.png)

Następnie z listy naszych użytkowników wybieramy tych, którym chcemy włączyć MFA. Jeżeli zaznaczymy jednego użytkownika możemy użyć bezpośrednio opcji Enable w Quick steps lub też użyć Bulk update jeżeli chcemy włączyć dla większej ilości użytkowników.

!["[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"](/assets/images/posts/azure-ad-dodajemy-2fa-mfa-nowa-wersja/02.png)

W momencie gdy użytkownik jkowalski będzie chciał się zalogować na swoją pocztę będzie musiał włączyć dwustopniową weryfikację:

!["[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"](/assets/images/posts/azure-ad-dodajemy-2fa-mfa-nowa-wersja/03.png)

Aczkolwiek Jan Kowalski nie zawsze nosi przy sobie telefon służbowy i chciałby jednak, aby w ramach potrzeby pilnego zalogowania się system do niego zadzwonił na prywatny numer.

Przydatny link dla użytkowników: [https://account.activedirectory.windowsazure.com/Proofup.aspx] gdzie taki użytkownik może dodać dodatkowe informacje:

!["[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"](/assets/images/posts/azure-ad-dodajemy-2fa-mfa-nowa-wersja/04.png)

Dla testów dodajmy użytkownikowi Jan Kowalski aplikację mobilną:

!["[PL] Azure AD – dodajemy 2FA (MFA) – nowa wersja"](/assets/images/posts/azure-ad-dodajemy-2fa-mfa-nowa-wersja/05.png)

Jeżeli Jan będzie próbował się zalogować do aplikacji / poczty / cokolwiek innego – zostanie o tym powiadomiony.

Jest to jedna z podstawowych rzeczy, którą musimy wykonać w naszej organizacji, aby utrzymać bezpieczeństwo.
