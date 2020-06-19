---
title: "[PL] Intune – Enrollment Page"
categories:
    - Intune
tags:
    - PL Post
---
![[PL] Intune – Enrollment Page](/assets/images/posts/intune-enrollment-page/top.png)Intune – Enrollment Page

Podczas wdrażania urządzenia dobrze by było przekazać użytkownikowi informację co się aktualnie dzieje na jego komputerze i dlaczego ciągle nie może pracować.

A szczególnie dobrze by było go poinformować, co należy zrobić jeżeli AutoPilot się wywalił. Albo w jaki sposób ma się skontaktować z HelpDeskiem.

Enrollment Page. Strona, która pokazuje się użytkownikowi kiedy urządzenie ściąga wszystkie ustawienia z Azure AD.

Domyślnie użytkownik wpisuje swój login / hasło i przechodzi do pulpitu Windows a w tle się instalują wszystkie programy. Lepiej by było, aby wszystkie polityki zostały wdrożone przed używaniem komputera.

Przejdźmy więc do zabawy.

![[PL] Intune – Enrollment Page](/assets/images/posts/intune-enrollment-page/01.png)

Windows enrollment > Enrollment Status Page > Create Profile i tworzymy nowy profil, a następnie go konfigurujemy.

![[PL] Intune – Enrollment Page](/assets/images/posts/intune-enrollment-page/02.png)

1) Show apps and profile installation progress > Yes
2) Show custom message when an error occurs > Yes, następnie skonfigurujmy treść błędu
3) Block device use until all apps and profiles are installed > Yes
4) Allow users to reset device if installation error occurs > Yes
5) Allow users to use device if installation error occurs > No
6) Block device use until these required apps are installed if they are assigned to the user/device > Selected Tutaj dla przykładu wrzuciłem Office 365.

Zapisujemy ustawienia i następuje proces przypisania do odpowiedniej grupy urządzeń.

![[PL] Intune – Enrollment Page](/assets/images/posts/intune-enrollment-page/03.png)

Ja dla przykładu przypisałem do do grupy, którą utworzyłem w poprzednim wpisie, [o tutaj!](https://piesik.me/2019/01/03/autopilot-dynamiczna-grupa-dla-nowych-urzadzen/)

Po przypisaniu do odpowiedniej grupy, rozpoczynamy od uruchomienia takiej maszyny. Logujemy się na konto użytkownika i… Mamy piękny komunikat o tym, co się obecnie dzieje!

Ogólny pogląd na status enrollmentu

![[PL] Intune – Enrollment Page](/assets/images/posts/intune-enrollment-page/04.png)

Szczegółowe informacje

![[PL] Intune – Enrollment Page](/assets/images/posts/intune-enrollment-page/05.png)

Uważam, że taka strona bardzo pomoże końcowemu użytkownikowi w orientowaniu się co się dzieje na jego urządzeniu.
