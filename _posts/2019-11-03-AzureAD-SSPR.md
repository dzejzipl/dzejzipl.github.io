---
title: "[PL] Azure AD Self-Service Password Reset"
categories:
    - Windows Server
    - Azure
tags:
    - Azure
    - Azure AD
    - Azure AD Connect
    - PL post
---
!["[PL] Azure AD Connect"](/assets/images/top_images/AzureADTOP.jpg)Słów kilka o Azure AD SSPR, czyli Self-Service Password Reset.

W przypadku, gdy użytkownik zapomni hasła, to musi dzwonić do HelpDesku, prosić innych użytkowników o kontakt z działem technicznym lub w inny sposób resetować swoje hasło. A co, gdyby przyśpieszyć to działanie i pozwolić użytkownikom na resetowanie haseł za pomocą samoobsługowego portalu?

Na samym początku musimy wprowadzić niezbędne ustawienia w portalu Azure AD. Przechodzimy do Azure AD > **Password Reset** z lewego strony i w menu Propeties wybieramy czy chcemy wdrożyć możliwość resetowania haseł dla całej organizacji czy też dla określonej grupy.

!["[PL] Azure AD Self-Service Password Reset"](/assets/images/posts/AzureAD-SSPR/01.png)

Następnie przechodzimy do zakładki **Authentication methods**, gdzie wybieramy ile metod uwierzytelniania ma być użyte do zweryfikowania użytkownika. Ja zaznaczę dwie wymagane metody oraz ustawię pytania. Jak widzicie na screenie, użytkownicy muszą podać odpowiedź na minimum cztery pytania przy konfiguracji MFA, a podczas odzyskiwania hasła muszą odpowiedzieć na minimum trzy pytania.

!["[PL] Azure AD Self-Service Password Reset"](/assets/images/posts/AzureAD-SSPR/02.png)

W zakładce **Notifications** ustawiamy odpowiednio opcje, natomiast w **Customization** możemy wskazać stronę z pomocą w jaki sposób używać SSPR.

## Z perspektywy end-usera

### Konfiguracja metod autentyfikacji

A jak końcowy użytkownik ma ustawić metody autentyfikacji?

Użytkownik loguje się na stronie [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup) i ustawia wymagane opcje.

!["[PL] Azure AD Self-Service Password Reset"](/assets/images/posts/AzureAD-SSPR/03.png)

### Odzyskiwanie hasła

Użytkownik otwiera stronę: [https://aka.ms/sspr](https://aka.ms/sspr), wpisuje swój login (adres email), uzupełnia captchę i odzyskuje hasło w dwóch prostych krokach.

!["[PL] Azure AD Self-Service Password Reset"](/assets/images/posts/AzureAD-SSPR/04.png)

Ustawienie **SSPR** jest wymagane do kolejnego poradnika, czyli Password-Writeback w AzureAD Connect.
