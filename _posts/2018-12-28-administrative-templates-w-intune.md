---
title: "[PL] Administrative Templates w Intune!"
categories:
    - Intune
tags:
    - PL Post
---
![[PL] Administrative Templates w Intune!](/assets/images/posts/administrative-templates-w-intune/top.png)Administrative Templates w Intune!

W dniu wczorajszym świat obiegła informacja o wprowadzeniu Administrative Templates w Intune.  Może nie tyle co świat, ale nasze małe międzynarodowe środowisko entuzjastów jak i osoby pracujące z Intune / Azure AD / Office 365.

Moment, moment, nie kojarzy wam się z czymś pojęcie Administrative Templates? Tak, z Windows Server. Szablony Administracyjne są używane dosyć mocno w pracy z lokalnym Active Directory. Dzięki nim możemy tworzyć zasady, konfigurować ustawienia a nawet ustawić tekst podczas Remote Sessions, co serdecznie polecam 😉

Ale, co by się tak nie cieszyć – to nie jest kopia 1:1 tego co znamy z Windows Server, do tego jeszcze bardzo długa droga. 

Udało mi się dowiedzieć, że na sam początek znajdziemy tam ustawienia głównie z Office, natomiast Windows jak i Internet Explorer / Edge przejdą do Security Baseline o którym kiedyś wam opowiem. 

Ale, co by nie przedłużać – na sam początek i tak wygląda to imponująco.  Lista zawiera 277 pozycji. Wow! 

Pełna lista na dzień dzisiejszy jest w poniższej tabelce, ale, żeby nie przedłużając wdróżmy politykę i spróbujmy zaszaleć – wdrażając ustawienie do Remote Sessions.

Przechodzimy do Intune, następnie do Device configuration – Profiles, tworzymy nowy profil wybierając z opcji „Adminstrative Templates”

![[PL] Administrative Templates w Intune!](/assets/images/posts/administrative-templates-w-intune/01.png)

Wyszukajmy Remote Assistance i ustawmy konfigurację Customize warning messages

![[PL] Administrative Templates w Intune!](/assets/images/posts/administrative-templates-w-intune/02.png)

Po wejściu w opcje konfiguracyjne ustawiłem dwa komunikaty, które zostaną wyświetlone u użytkownika.

![[PL] Administrative Templates w Intune!](/assets/images/posts/administrative-templates-w-intune/03.png)

Konfiguracja tych ustawień jest bardzo prosta, jednak pamiętajcie, aby najpierw je wdrażać na odpowiednich grupach testowych.
