---
title: "[PL] Azure AD - Yubico i YubiKey"
categories:
    - Azure AD
tags:
    - Azure AD
    - Security
    - 2FA
    - Yubico
    - Yubikey
    - PL post
---
!["[PL] Azure AD - Yubico i Yubikey"](/assets/images/top_images/AzureADTOP.jpg)Bezpieczeństwo ponad wszystko, czyli rozpoczynamy pracę z Yubikey oraz Azure AD.

Dłuższy czas temu dotarł do mnie zestaw startowy z Yubico, w którym były dostępne dwa klucze **Yubikey5C oraz 5 NFC**. Zamówiłem je głównie dlatego, żeby polepszyć bezpieczeństwo mojej testowej organizacji, a także zobaczyć, w jaki sposób dowolna organizacja może wdrożyć Yubikey, aby uwolnić użytkowników od haseł. 

Dziś chciałbym wam pokazać, w jaki sposób skonfigurować Azure AD oraz Intune, aby wdrożyć opcję logowania w naszej organizacji oraz to, co końcowy użytkownik musi zrobić, aby móc używać tej metody logowania.


Rozpoczynamy od przejścia do **Microsoft Endpoint Manager**, który znajdziemy pod adresem https://devicemanagement.portal.azure.com/, potem do zakładki *Devices* > *Windows* > *Windows enrollment*, wybieramy **Windows Hello for Business**, gdzie zaznaczymy opcję: **Use security keys for sign-in** z ***Enabled***

!["[PL] Azure AD - Yubico i Yubikey"](/assets/images/posts/AzureAD-YubiKey/01.png)

Kolejnym krokiem jest włączenie tzw. preview features w Users Settings, dokonujemy tego w tym samym panelu, przechodząc do zakładki *Users* > *User settings* > z dołu wybierając **Manage user feature preview settings** > oraz odpowiednio zaznaczając opcję: **Users can use preview features for registering and managing security info – enhanced** 

!["[PL] Azure AD - Yubico i Yubikey"](/assets/images/posts/AzureAD-YubiKey/02.png)

Trzecim krokiem jest włączenie FIDO2 jako standardu autentyfikacji w naszej organizacji. Przechodzimy do portalu Azure > *Azure AD* > *Security* > **Authentication methods**, wybieramy **FIDO2 Security Key**, ustawiamy Enabled na Yes, zaznaczamy, którzy użytkownicy mogą używać tej metody oraz pozwalamy na Self-Service. Ja również pozwolę na używanie wszystkich kluczy zgodnych z FIDO2.

!["[PL] Azure AD - Yubico i Yubikey"](/assets/images/posts/AzureAD-YubiKey/03.png)

Ostatnim krokiem od strony administracyjnej jest stworzenie dwóch profili, które pozwolą nam na logowanie do stacji roboczej za pomocą klucza. 

Drobna uwaga. Niektóre źródła mówią o potrzebie stworzenia tylko pierwszego profilu, niektóre o dwóch. Ja mogę potwierdzić, że u mnie zadziałała opcja z dwoma profilami.

Przechodzimy do portalu *Microsoft Endopoint Manager* > *Devices* > **Configuration Profiles** > *Add new*.
Jako platformę wybieramy **Windows 10 and later**, a jako typ: **Identify Protection**. Włączamy ustawienie **Use security keys for sign-in** tak jak na screenie oraz przypisujemy do grupy urządzeń.

!["[PL] Azure AD - Yubico i Yubikey"](/assets/images/posts/AzureAD-YubiKey/04.png)

Drugi profil, który dodamy będzie typu **Custom**, czyli manualnie podamy OMA-URI zgodnie z tym co na screenie:

!["[PL] Azure AD - Yubico i Yubikey"](/assets/images/posts/AzureAD-YubiKey/05.png)

* Pod name wpisujemy naszą nazwę
* OMA-URI wygląda w sposób następujący: **./Device/Vendor/MSFT/PassportForWork/SecurityKey/UseSecurityKeyForSignin**
* Data type to *Integer* z value *1*

Ten profil również musi zostać przypisany do odpowiedniej grupy.

Jak wygląda procedura z strony końcowego użytkownika? 

Wpierw taki klucz musi zostać dodany, poprzez przejście na stronę https://myprofile.microsoft.com/, następnie **Security Info** > *Add Method* > **Security Key** i końcowy użytkownik musi postępować zgodnie z kreatorem, który jest bardzo intuicyjny. 

Logowanie natomiast jest jeszcze łatwiejsze. Zamiast wpisywać hasło, użytkownik klika na **Sign-in options**, wybiera klucz, wpisuje pin do klucza, dotyka klucz co powoduje zatwierdzenie logowania. 

Jak widzicie, takie rozwiązanie pozwala nam na uniknięcie podawania hasła do naszego konta.
