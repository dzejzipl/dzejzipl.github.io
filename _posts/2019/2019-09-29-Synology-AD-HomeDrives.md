---
title: "[PL] HomeDrives na Synology Directory Services"
categories:
    - Synology
tags:
    - Synology
    - Active Directory
    - Samba
    - PL post
---
!["[PL] HomeDrives na Synology Directory Services"](/assets/images/top_images/SynologyTOP.jpg)A gdyby tak przenieść dane naszych użytkowników z dysków lokalnych na jedną, wspólną przestrzeń? 

Taką, która będzie regularnie przez nas backupowana, zarządzana, a zarazem przy logowaniu na inny komputer dane użytkownika pomigrują za nim? Czyż by to nie było ciekawe rozwiązanie? 

Synology Directory Services pozwala nam na stworzenie miejsca, gdzie będą trzymane pliki naszych użytkowników, tzw. **homedrive**. Jest to bardzo dobre rozwiązanie, ponieważ pliki wędrują za użytkownikiem, a poza tym są one regularnie backupowane przez odpowiednie osoby. 

### Dlaczego więc by tego nie wprowadzić u siebie?

Proces ten jest bardzo prosty, wpierw musimy utworzyć odpowiedni share folder:

!["[PL] HomeDrives na Synology Directory Services"](/assets/images/posts/Synology-AD-HomeDrives/01.png)

Z opcji dodatkowych to go nie szyfrujemy, nie włączamy quoty, możemy włączyć natomiast sprawdzanie poprawności plików.

Jeżeli już stworzyliśmy nowy folder, automatycznie otworzą nam się opcje udostępniania folderów. W przypadku dysków dla użytkowników uprawnienia muszą być specyficzne i dobrze dobrane, bo przecież nie chcielibyśmy, aby użytkownik a miał dostęp do danych użytkownika B.

Pozwoliłem sobie skorzystać z tabelki, która została przygotowana przez Synolology, ja natomiast dodam jeszcze jedną grupę, w której będą osoby, które mogą pracować z danymi użytkowników, nazwaną **DataAdmins** i dodam do niej konta domenowe administratorów.

A jak ustawić główne uprawnienia? Zobaczcie na poniższą tabelkę:

| Konto / Grupa | Apply to | Permission |
|:-------------:|:--------------------------------------------------------:|:------------------------------------------------------------------------------------:|
| Owner | Check  Child folders,  Child files, and  All descendants | Check Administration, Read, and Write for Full Control |
| Domain Admins | Select All | Check Administration, Read, and Write for Full Control |
| Domain Users | Select All | Check Read for full Read permissions and only Create folders/Append data under Write |
| Data Admins | Select All | Check Administration, Read, and Write for Full Control |

> Podziękowania dla firmy Synology za wstępną tabelkę. Ja dodałem do niej grupę DataAdmins.

!["[PL] HomeDrives na Synology Directory Services"](/assets/images/posts/Synology-AD-HomeDrives/02.png)

Tak będzie wyglądała opcja dla DataAdmins.

#### Co ważne, pamiętajcie, aby proszę to robić z poziomu grup Directory Services, a nie grup lokalnych

Według poradnika bezpośrednio na stronie producenta należy teraz dodać homedrive dla każdego użytkownika. Nie uśmiecha mi się tego robić więcej niż raz, więc dlaczego by nie zaprząc do tego polityk **GPO**.

Wykorzystam do tego podłączony do naszej domeny system Windows 10 i skonfiguruję domyślną politykę, która obejmuje **wszystkich** użytkowników z grupy **authenticated users**

Aby to zrobić, przechodzę do **User Configuration** > **Windows Settings** > **Folder Redirection**

!["[PL] HomeDrives na Synology Directory Services"](/assets/images/posts/Synology-AD-HomeDrives/03.png)

I tam ustawiam każdy folder, który chcę, aby był przekierowywany. Ja np. chciałbym, aby był przekierowywany **Desktop**, dlatego klikam na nim prawym przyciskiem myszy i wybieram **Properties**

!["[PL] HomeDrives na Synology Directory Services"](/assets/images/posts/Synology-AD-HomeDrives/04.png)

Jak widzicie, w polu **Root Path** mam wpisaną ścieżkę, którą utworzyłem na początku tego wpisu.

A, żeby ładniejsze polecam jednak użyć nazwy DNS niżeli adresu IP, który może się zmienić.

Po restarcie komputera u użytkownika i zaaktualizowaniu polityk GPO, na naszym NASie powinien pojawić się nowy folder:

!["[PL] HomeDrives na Synology Directory Services"](/assets/images/posts/Synology-AD-HomeDrives/05.png)

Dzięki tym prostym krokom stworzyliśmy profil mobilny dla naszego użytkownika, a jego dane będą zarówno backupowane jak i przenoszone na nowy komputer w przypadku wymiany urządzenia.
