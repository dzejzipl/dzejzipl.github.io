---
title: "[PL] Łączymy się do O365 z poziomu PS przy włączonym MFA"
categories:
    - PowerShell
tags:
    - Enter-PSSession
    - PL Post

header-img: "/assets/images/posts/2018/laczymy-sie-do-o365-z-poziomu-ps-przy-wlaczonym-mfa/top.jpg"
subtitle:   "[PL] Łączymy się do O365 z poziomu PS przy włączonym MFA"
---
![[PL] Łączymy się do O365 z poziomu PS przy włączonym MFA](/assets/images/posts/2018/laczymy-sie-do-o365-z-poziomu-ps-przy-wlaczonym-mfa/top.jpg)Łączymy się do O365 z poziomu PS przy włączonym MFA

Ostatnio pisałem o możliwości łączenia się do panelu zarządzania Office365 przez PowerShell, co możecie zaobserwować pod [tym linkiem: Edytujemy usługe O365 z poziomu PowerShella](https://www.piesik.me/2018/01/09/edytujemy-nasza-usluge-o365-z-poziomu-powershell/)

Jednak dzis chciałbym pokazać wam w jaki sposób możemy się łączyć przez PS jeżeli mamy uaktywnione MFA na danym koncie.

Czym jest MFA oraz jak je wprowadzić możecie przeczytać [pod tym linkiem](https://www.piesik.me/2017/03/15/azure-ad-dodajemy-2fa-mfa/)

Wracając do tematu – bezpieczeństwo ponad wszystko i jednak każdy Global Administrator musi mieć włączone MFA.

1) Na początku musimy zalogować się do panelu Office365 i wejsć do panelu Exchange, który jest dostępny pod tym linkiem z poziomu przeglądarki Microsoft Edge. Niestety, z każdej innej przeglądrki otrzymamy błąd.
2) Z lewej strony wybieramy hybrid > The Exchange Online PowerShell Module supports multi-factor authentication. Download the module to manage Exchange Online more securely.

    ![[PL] Łączymy się do O365 z poziomu PS przy włączonym MFA](/assets/images/posts/2018/laczymy-sie-do-o365-z-poziomu-ps-przy-wlaczonym-mfa/01.png)

3) Pobieramy oraz instalujemy moduł do obsługi Microsoft Exchange

    ![[PL] Łączymy się do O365 z poziomu PS przy włączonym MFA](/assets/images/posts/2018/laczymy-sie-do-o365-z-poziomu-ps-przy-wlaczonym-mfa/02.png)

4) Po chwili wyskoczy nam nowe okno PowerShella wyglądające w taki sposób:

    ![[PL] Łączymy się do O365 z poziomu PS przy włączonym MFA](/assets/images/posts/2018/laczymy-sie-do-o365-z-poziomu-ps-przy-wlaczonym-mfa/03.png)

5) Aby się połączyć wpisujemy polecenie: **Connect-EXOPSSession**, nasz login / hasło oraz weryfikujemy MFA.
6) Po wykonaniu komendy mamy pełen dostęp do obsługi O365 za pomocą PS.

No dobrze, ale czy teraz za każdym razem jak będę chciał się logować przez PS to mam wykonywać kroki od 1 do 6? No niezbyt.

Wystarczy, że z pulpitu uruchomisz ikonę Microsoft Exchange Online Powershell Module i wykonasz komendę: Connect-EXOPSSession

To by było na tyle.

I pamietajcie – bezpieczeństwo ponad wszystko!
