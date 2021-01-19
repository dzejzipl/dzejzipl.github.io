---
title: "[PL] Azure AD – dodajemy komputer do AAD oraz Intune"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/top.jpg"
subtitle:   "[PL] Azure AD – dodajemy komputer do AAD oraz Intune"
---
![[PL] Azure AD – dodajemy komputer do AAD oraz Intune](/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/top.jpg)Azure AD – dodajemy komputer do AAD oraz Intune

Ostatnio opisywałem w jaki sposób możecie dodać swoje urządzenie mobilne do usługi Azure AD i Intune . Dziś zajmiemy się tematem w jaki sposób możemy dodać nasze urządzenie z Windows 10 do Azure AD i Intune dzięki czemu uzyskamy pełną możliwość zarządzania takim komputerem – w kolejnym wpisie przeczytacie jak wykorzystać dzisiejszą poradę.

Zaczynamy od tego, że będąc na lokalnym koncie użytkownika wchodzimy w Settings, następnie Accounts > Access work or school.

![[PL] Azure AD – dodajemy komputer do AAD oraz Intune](/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/01.png)

Po kliknięciu Connect pojawi nam się opcja dołączenia – wybieramy z dolnego menu Join this device to Azure Active Directory, aby dołączyć do naszej organizacji. Uzupełniamy dane logowania i pojawia nam się potwierdzenie czy na pewno chcemy dołączyć.

![[PL] Azure AD – dodajemy komputer do AAD oraz Intune](/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/02.png)

Jeżeli tak to nie pozostało nic innego niżeli kliknięcie na Join i ponowne uruchomienie komputera.

Po restarcie należy się zalogować do nowego konta poprzez wybranie Switch user i wpisaniu danych logowania z naszej organizacji jak na screenie:

![[PL] Azure AD – dodajemy komputer do AAD oraz Intune](/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/03.png)

Na samym końcu możemy sprawdzić poprawność zalogowania się do Azure Active Directory poprzez odwiedzenie Settings > Accounts > Access work or school. Tam powinno być dodane nasze konto.

Teraz jeżeli wejdziemy w portal AAD > Azure AD Devices znajdziemy dodane przez nas urządzenie:

![[PL] Azure AD – dodajemy komputer do AAD oraz Intune](/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/04.png)

Takie urządzenie zostanie dodane tylko do Azure AD i będzie możliwe tylko w przypadku wersji systemu Professional i wyżej. Nadal, aby np. wdrożyć automatycznie oprogramowanie na komputerze musimy dodać dostęp do aplikacji firmowych za pomocą okienka: Settings > Accounts > Connect > i uzupełniamy wszystkie nasze dane logowania.

Po chwili możemy udać się do sklepu Microsoft i ściągnąć aplikację Company Portal – dokładnie tak jak zostało to opisane w przypadku telefonów komórkowych.

Jeżeli wszystko zostanie poprawnie dodane status w Work and School access powinno wyglądać tak:

![[PL] Azure AD – dodajemy komputer do AAD oraz Intune](/assets/images/posts/2018/azure-ad-dodajemy-komputer-do-aad-oraz-intune/05.png)

Co nam to da? Np. automatyczną instalację oprogramowania! 🙂
