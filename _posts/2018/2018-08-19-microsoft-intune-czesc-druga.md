---
title: "[PL] Microsoft Intune – część druga"
categories:
    - Intune
tags:
    - Intune
    - PL Post

header-img: "/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/top.jpg"
subtitle:   "[PL] Microsoft Intune – część druga
"
---
![[PL] Microsoft Intune – część druga](/assets/images/posts/2018/microsoft-intune-czesc-trzecia-dodajemy-urzadzenie-do-intune/top.png)Microsoft Intune – część druga

W [pierwszym poście](https://www.piesik.me/2018/08/19/microsoft-intune-czesc-pierwsza/) dowiedzieliście się dwóch z trzech podstawowych rzeczy o Intune.

* O tym jak skonfigurować branding, czyli wygląd naszej organizacji
* O tym jak skonfigurować ustawienia rekordów DNS naszej domeny
* I w jaki sposób wybrać sposób działania pracy Intune

Dziś zajmiemy się tworzeniem użytkowników i grup. Spróbujemy stworzyć użytkownika, grupę, a następnie dodać go do tej grupy w trzy różne sposoby:

* Azure CLI
* PowerShell
* Portal Azure

W jaki sposób używać Azure CLI – mogliście przeczytać już w poście Azure CLI vol 2 | Strefy DNS. Natomiast PowerShella do zarządzania Azure jak i Office365 opisywałem natomiast w poście: Edytujemy naszą usługę O365 z poziomu PowerShell.  Zanim zaczniemy pracę zachęcam do zapoznania się z tymi dwoma postami.

Na początku opiszę proces dodawania grupy i użytkowników za pomocą PowerShell:

Użytkownik:

1) Logujemy się za pomocą polecenia Connect-AzureAD
2) Do sprawdzenia poprawności działania wylistujemy sobie 10 użytkowników poleceniem: Get-AzureADUser -top 10
3) W kroku trzecim musimy zdefiniować hasło dla użytkownika:

    ```powershell
    $PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
    $PasswordProfile.Password = „NaszeHasloDlaUzytkownika„
    ```

4) I pozostała nam już tylko jedna komenda do wykonania:

    ```powershell
    New-AzureADUser -DisplayName „Jan Kowalski PS” -PasswordProfile $PasswordProfile -UserPrincipalName „adres@email.pl” -AccountEnabled $true
    ```

Grupa:

1) Tak jak w poprzednim kroku do zalogowania się używamy polecenia **Connect-AzureAD**
Dla sprawdzenia poprawności działania wylistujemy 10 grup poleceniem: Get-AzureADGroup -top 10
Poleceniem:  N**ew-AzureADGroup -DisplayName „Grupa z PS” -MailEnabled $false -SecurityEnabled $true -MailNickName „GrupazPS”**
W tym wypadku nazwałem grupę *„Grupa z PS”*, która nie jest grupą dystrybucyjną tylko grupą zabezpieczeń.
Jeżeli teraz wylistujemy jeszcze raz grupy powinna się ona pojawić na liście
Dodajmy nowo stworzonego użytkownika do grupy:

Wykonujemy polecenie:  **Add-AzureADGroupMember -ObjectId „IDNaszejGrupy” -RefObjectId „IDNaszegoUsera„**
Jeżeli teraz wylistujemy użytkowników należących do naszej grupy poleceniem:
**Get-AzureADGroupMember -ObjectId „IDNaszejGrupy”** nowo dodany użytkownik powinien zostać wyświetlony

Usunięcie użytkownika z grupy:

Usunięcie użytkownika z grupy polega na wykonaniu polecenia:
**Remove-AzureADGroupMember -ObjectId „IDNaszejGrupy” -MemberId „IDNaszegoUsera„**
Zauważyliście, że w przypadku dodawania użytkownika drugi parametr ma nazwę RefObjectID a przy usuwaniu to MemberId? 🙂
Teraz możemy to wszystko powtórzyć w przypadku Azure CLI – zobaczmy co uda nam się zrobić.

Tworzenie użytkownika:

Logujemy się do swojego tenanta za pomocą polecenia: **az login**
Następnie tworzymy użytkownika za pomocą polecenia:
**az ad user create –display-name „Jan Kowalski CLI” –password „HasloNaszegoUzytkownika” –user-principal-name „NazwaNaszegoUzytkownika@domena.pl„**
Jeżeli dodamy na końcu polecenia **–force-change-password-next-login true** ustawimy, aby użytkownik przy następnym zalogowaniu musiał zmienić hasło na swoje co jest polecane.
Tworzenie grupy:

Wykonujemy polecenie:
**az ad group create –display-name „Nazwa grupy” –mail-nickname „Identyfikator”**
Domyślnie jest tworzona grupa zabezpieczeń, nie znalazłem niestety przełącznika odpowiadającego za stworzenie grupy dystrybucyjnej.

Wylistowanie grup:

Wszystkie grupy możemy wylistować poleceniem: **az ad group list**

Dodanie nowo stworzonego użytkownika do grupy

Stworzyliśmy użytkownika i teraz chcieli byśmy dodać go do nowo stworzonej grupy. Robimy to poleceniem:
**az ad group member add –group „IDNaszejGrupy” –member-id „IDNaszegoUsera„**

Wyświetlenie członków danej grupy:

Polecenie: **az ad group member list –group „IDNaszejGrupy”**

Usunięcie użytkownika z grupy

Polecenie: **az ad group member remove –group „IDNaszejGrupy” –member-id „IDNaszegoUzytkownika”**

Jeżeli już wiemy w jaki sposób to wszystko wykonać z poziomu CLI oraz PowerShella – to stwórzmy teraz użytkownika w najłatwiejszy sposób, czyli za pomocą portalu Azure.

1) Logujemy się do portalu, przechodzimy do sekcji Azure Active Directory
2) Z lewej strony wybieramy Users > New User
3) Wypełniamy niezbędne pola
4_ Klikamy Create

Tworzenie grupy za pomocą portalu Azure

1) Z naszego tenanta wybieramy zakładkę Groups > New Group
2) Wybieramy typ grupy: dla mojego przykładu niech jest to Security
3) Nazwa jak i opis jest do wymyślenia przez was
4) Membership type: Assigned. Później stworzymy grupę urządzeń z Androidem poniżej jakiejś wersji.
5) Od razu za jednym razem możemy dodać odpowiednich użytkowników do grupy klikając na pole Members
J
eżeli chcecie poczytać trochę o dynamicznych grupach użytkowników to zapraszam was do artykułu, który niedawno popełniłem czyli: [Dynamiczne grupy użytkowników w AAD](https://www.piesik.me/2018/03/10/dynamiczne-grupy-uzytkownikow-w-aad/)

Z podstaw tworzenia grup i użytkowników to na tyle.

W kolejnym artykule dodamy sobie pierwsze urządzenia do Intune i stworzymy dynamiczne grupy urządzeń.
