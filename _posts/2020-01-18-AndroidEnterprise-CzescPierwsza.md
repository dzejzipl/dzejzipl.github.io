---
title: "[PL] Intune + Android Enterprise - część pierwsza"
categories:
    - Intune
    - Android Enterprise
tags:
    - Azure AD
    - Intune
    - Android Enterprise
    - Google Play
    - PL post
---
!["[PL] Intune + Android Enterprise - część pierwsza"](/assets/images/top_images/AndroidEnterpriseTOP.jpg)Zarządzanie Windowsami z poziomu Intune jest bajecznie proste, a co z Androidami? Na pomoc nadchodzi Android Enterprise!

Długi czas temu zamarzyła mi się praca z Intune, głównie po to, aby móc zarządzać urządzeniami opartymi na Windowsie. Skoro to mi poszło całkiem dobrze, to dlaczego by nie pójść kawałek dalej i nauczyć się w jaki sposób zarządzać urządzeniami oparatymi na platformie Android?

Dziś chciałbym pokazać Wam, w jaki sposób połączyć nasze konto w Intune z Android Enterprise, co możemy dzięki temu osiągnąć oraz pokrótce - jak to osiągnąć.

Na wstępie chciałbym podziękować firmie HMD Global za dostarczenie do testów smartfona Nokia 7.1 który jest moim samplem testowym. Więcej o tym telefonie napiszę w późniejszym czasie, na początek jednak mięsko techniczne.

Android Enterprise pozwala nam na stworzenie trzech różnych profili zarządzanych urządzeń:

* Personal devices with work profile, czyli w skrócie mówiąc urządzenia prywatne, które posiadają profil z aplikacjami firmowymi oraz ustawieniami. Najczęstsze rozwiązanie w małych firmach, gdzie pracownicy nie posiadają służbowych telefonów, a chcą mieć dostęp do zasobów firmowych.
* Corporate-owned dedicated devices, czyli w skrócie urządzenia kupione przez firmę, nie do użytku prywatnego. Są to telefony / tablety używane w konkretnym celu, którym najbardziej popularnym będzie urządzenie typu Kiosk.
* Corporate-owned, fully managed devices, czyli w skrócie urządzenia, które są użytkowane przez użytkownika końcowego i w pełni zarządzane przez firmę, bez możliwości użycia w prywatnym celach.

Jak widzimy, dla każdego coś dobrego. W serii postów postaram się opisać każdy z możliwych profili - głównie dlaczego i w jaki sposób go wykorzystać.

Połączymy więc te dwie usługi!

1. Otwieramy Intune, przechodzimy do Device Enrollment > Android Enrollment
2. Otwieramy zakładkę na Managed Google Play, zgadzamy się na przesyłanie danych pomiędzy Microsoft <> Google i rozpoczynamy konfigurację za pomocą przycisku *Launch Google to connect now.*

    !["[PL] Intune + Android Enterprise - część pierwsza"](/assets/images/posts/AndroidEnterprise-CzescPierwsza/01.png)

3. Cała konfiguracja jest bajecznie prosta, wypełniamy najważniejsze dane kontaktowe i już po chwili mamy dostępne profile do skonfigurowania.

    !["[PL] Intune + Android Enterprise - część pierwsza"](/assets/images/posts/AndroidEnterprise-CzescPierwsza/02.png)

Jak widzicie, wstępna konfiguracja opiera się tylko na połączeniu dwóch usług. Dzięki temu możemy przejść do kolejnego posta w którym wykorzystamy **Personal devices with work profile**
