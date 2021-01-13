---
title: "[PL] Intune – Bitlocker Windows 10"
categories:
    - Intune
tags:
    - PL Post
---
![[PL] Intune – Bitlocker Windows 10](/assets/images/posts/intune-bitlocker-windows-10/01.png)Intune – Bitlocker Windows 10

Czasem jest tak, że człowiek chciałby wymusić większe bezpieczeństwo na komputerach w swojej organizacji. Dwustopniowe logowanie, zmiany haseł lub inne zabezpieczenia. Ale to wszystko chroni przed możliwością do zalogowania się do system. A co w przypadku, gdy ktoś taki komputer ukradnie, wyciągnie dysk, podłączy do swojego urządzenia? Cóż, ma natychmiastowy dostęp do dysku i wszystkich danych.

Technologia Bitlockera w Windows 10 działa bardzo dobrze, nie spotkałem się jeszcze z żadnymi problemami w jej działaniu, a konfiguracja z poziomu Azure AD / Intune jest bajecznie prosta, co chciałbym wam pokazać w tym wpisie.

Proces rozpoczynamy od stworzenia grupy, która będzie przypięta do odpowiedniej polityki, która pozwoli na włączenie Bitlockera. Stosuję zasadę – jedna grupa, jedno ważne ustawienie systemu. Dlaczego miałbym włączać bitlockera na wirtualnych maszynach w moim środowisku? No dla testów oczywiście, że tak, ale na stałe?
Na moje potrzeby grupa została nazwana: SG-Win10-BitlockerEnabled

Następnie stworzymy politykę, która zostanie podpięta pod grupę
SG-Win10-BitlockerEnabled. Do boju więc!
**Device Configuration > Profiles > Create Profile**
Platform: **Windows 10 and later**
Profile type: **Endpoint protection**

![[PL] Intune – Bitlocker Windows 10](/assets/images/posts/intune-bitlocker-windows-10/02.png)

Przechodzimy do zakładki: *Windows Encryption* i tam konfigurujemy następujące opcje:

* Encrypt devices > Required
* BitLocker base settings > Configure encryption methods > Enable
* OS drive recovery > Enable
* Os drive recovery > Recovery options in the BitLocker setup wizard > Block
* Os drive recovery > Save BitLocker recovery information to Azure Active Directory > Enable
* Os drive recovery > BitLocker recovery Information stored to Azure Active Directory
* Backup recovery passwords and key packages > Backup recovery passwords and key packages
* Os drive recovery > Store recovery information in Azure Active Directory before enabling BitLocker > Require

Domyślnie konfiguracja sprowadza się tylko do włączenia dwóch opcji. Ja natomiast postanowiłem zaszaleć i wrzucić więcej opcji, które zrobią nam taką procedurę mniej stresową dla końcowego użytkownika. Po prostu klucz odzyskiwania zostanie zapisany bezpośrednio w Azure AD! 😉

Po odświeżeniu polityk na urządzeniu użytkownika pojawi mu się piękny komunikat o wymuszeniu Bitlockera na urządzeniu:

![[PL] Intune – Bitlocker Windows 10](/assets/images/posts/intune-bitlocker-windows-10/03.png)

![[PL] Intune – Bitlocker Windows 10](/assets/images/posts/intune-bitlocker-windows-10/04.png)

Domyślnie jest możliwość wybrania informacji, gdzie chcemy zapisać klucze odzyskiwania., jednak ta opcja została przez nas zablokowana i klucz znajdziemy na portalu Azure AD, tak jak na screenie:

![[PL] Intune – Bitlocker Windows 10](/assets/images/posts/intune-bitlocker-windows-10/05.png)

W ten sposób możemy zaszyfrować nasze urządzenia. Wcześniej wymagany to tego był Windows 10 Enterprise, teraz możemy używać do tego Windows 10 w wersji Professional.
