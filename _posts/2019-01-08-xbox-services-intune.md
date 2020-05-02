---
title: "[PL] Xbox Services – Intune"
categories:
    - Intune
tags:
    - Intune
    - PL Post
---
!["[PL] Xbox Services – Intune"](/assets/images/top_images/IntuneTOP.png)Wyłączamy usługi Xboxowe za pomocą Intune

W systemie Windows istnieje bardzo wiele różnych serwisów, które odpalają się przy starcie systemu. Całkiem spora ilość z nich jest w ogóle nie potrzebna na komputerach służbowych. No zapytajmy się sami siebie – czy naprawdę potrzebujemy, aby usługa odpowiadająca za XBOXa była uruchomiona i możliwa do zarządzania przez użytkownika?

No chyba troszkę nie.

W dzisiejszym poście pokażę wam w jaki sposób utworzyć profil, który zostanie wdrożony na urządzenia z Windows 10 i zablokuje usługi Xboxowe.

Do boju!

Przechodzimy do Device Management > Device configuration > Profiles > Create Profile i tworzymy nowy profil.

!["[PL] Xbox Services – Intune"](/assets/images/posts/xbox-services-intune/01.png)

Nazywamy go odpowiednio, jako Platform wybieramy „Windows 10 and later” a jako typ ustawiamy „Endopoint protection”

Przechodzimy do Configure > Xbox Services i konfigurujemy według opcji jak na obrazku, aby wyłączyć wszystkie usługi:

!["[PL] Xbox Services – Intune"](/assets/images/posts/xbox-services-intune/02.png)

Następnie przypisujemy do odpowiedniej grupy i zobaczmy jak to wygląda z perspektywy końcowego użytkownika:

!["[PL] Xbox Services – Intune"](/assets/images/posts/xbox-services-intune/03.png)
