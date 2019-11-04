---
title: "[PL] Azure AD Connect - Password Writeback"
categories:
    - Windows Server
    - Azure
tags:
    - Azure AD
    - Azure AD Connect
    - PL post
---
!["[PL] Azure AD Connect"](/assets/images/top_images/AzureADTOP.jpg)Synchronizacja hashów haseł z Azure AD do lokalnego AD.

Domyślnie, synchronizacja hashów haseł w Azure AD Connect jest od lokalnego Active Directory do Azure Active Directory. A co, gdyby zrobić także synchronizację haseł w drugą stronę? Czyli reset hasła z Azure AD i replikacja do lokalnego AD?

Na samym początku musimy mieć wstępnie skonfigurowanego AAD Connect oraz znać konto, które dokonuje synchronizacji:

!["[PL] Azure AD Connect - Password Writeback"](/assets/images/posts/AzureAD-Connect-Password-Writeback/01.png)

Drugim wymaganiem jest skonfigurowane **SSPR**, które opisałem [w tym poście](https://www.piesik.me/2019/11/03/AzureAD-SSPR/).

Wstępna konfiguracja wygląda w taki sposób, że otwieramy Azure AD Connect na serwerze, gdzie jest on zainstalowany, przechodzimy do opcji: **Customize Synchronization Options**, logujemy się odpowiednimi danymi i w dodatkowych opcjach zaznaczamy **Password writeback**

!["[PL] Azure AD Connect - Password Writeback"](/assets/images/posts/AzureAD-Connect-Password-Writeback/02.png)

Zatwierdzamy konfigurację, przechodzimy do przystawki **Active Directory Users and Computers**

Klikamy prawym przyciskiem na naszą domenę, wybieramy **Delegate Control**, w drugim kroku wybieramy użytkownika **MSOL**, którego znaleźliśmy wcześniej, w polu: *Tasks to delegate* zaznaczamy **Create a custom task to delegate**, natomiast w *Delegate Control of:* wybieramy **Users objects**

!["[PL] Azure AD Connect - Password Writeback"](/assets/images/posts/AzureAD-Connect-Password-Writeback/03.png)

W kroku **Select the permissions you want to delegate** zaznaczamy dwie pierwsze opcje czyli:

* General
* Property-specific

A z listy musimy wybrać:

* Change password
* Reset password
* Write lockoutTime
* Write pwdLastSet

!["[PL] Azure AD Connect - Password Writeback"](/assets/images/posts/AzureAD-Connect-Password-Writeback/04.png)

Ostatnim krokiem, który musimy wykonać jest skonfigurowanie GPO, aby hasło nie musiało być starsze niż jeden dzień zanim zostanie zmienione.
> Źródło: [Microsoft Docs](https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-sspr-writeback)

Dokonujemy tego w sposób:

1) Otwieramy **Group Policy Management Editor**
2) Edytujemy odpowiednią politykę GPO, ja edytuję domyślną
3) Przechodzimy do: *Computer Configuration* > *Policies* > *Windows Settings* > *Security Settings* > *Account Policies* > **Password Policy** i edytujemy ustawienie: **Minimum password age** zgodnie z tym co na screenie:

!["[PL] Azure AD Connect - Password Writeback"](/assets/images/posts/AzureAD-Connect-Password-Writeback/05.png)

Co ważne - polityka haseł dla użytkowników z on-prem jest teraz sterowana przez lokalne AD, w związku z czym polecam przejrzeć pozostałe ustawienia w **Password Policy**, abyście się nie nacieli na to, że nagle reset hasła dla użytkownika nie działa poprawnie.

Pytania? Standardowo zapraszam do komentarzy.
