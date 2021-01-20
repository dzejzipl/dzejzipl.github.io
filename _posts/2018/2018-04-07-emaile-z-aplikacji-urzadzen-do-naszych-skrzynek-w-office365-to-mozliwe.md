---
title: "[PL] Emaile z aplikacji / urządzeń do naszych skrzynek w Office365? To możliwe!"
categories:
    - Other
tags:
    - Office 365
    - PL Post

header-img: "/assets/images/posts/2018/emaile-z-aplikacji-urzadzen-do-naszych-skrzynek-w-office365-to-mozliwe/top.jpg"
subtitle:   "[PL] Emaile z aplikacji / urządzeń do naszych skrzynek w Office365? To możliwe!"
---
![[PL] Emaile z aplikacji / urządzeń do naszych skrzynek w Office365? To możliwe!](/assets/images/posts/2018/emaile-z-aplikacji-urzadzen-do-naszych-skrzynek-w-office365-to-mozliwe/top.jpg)Emaile z aplikacji / urządzeń do naszych skrzynek w Office365? To możliwe!

W dzisiejszym wpisie pokażę wam w jaki sposób możemy utworzyć bramkę do wysyłania wiadomości w naszej organizacji Office365.

Początek wpisu brzmi całkiem poważnie prawda? A chodzi tu tylko o np. urządzenia wielofunkcyjne, które wysyłają nam skany dokumentów. Albo dowolna aplikacja wysyła powiadomienie o wykonaniu czynności. Do tego właśnie przyda nam się taka bramka.

Istnieje kilka możliwości na wysyłanie wiadomości w Office365. Możemy używać serwera Exchange, możemy użyć do tego celu SMTP. Ale do tych dwóch sposobów potrzebujemy nazwy użytkownika oraz hasła. No i oczywiście przypisanej licencji do konta. Marnować licencję na użytek skanera?

Dlatego postanowiłem dla was przetestować rozwiązanie – w jaki sposób wysyłać wiadomości do naszej organizacji za pomocą dowolnego adresu w taki sposób, aby była w pełni akceptowalna przez filtry antyspamowe oraz przechodziła testy zabezpieczeń.

Zabierzmy się do pracy.

1) W kroku pierwszym musimy poznać adres naszego serwera Exchange w usłudze. Najprościej zrobimy to wchodząc w Office365 Admin Center > Domains > nasza domena > Rekordy od Exchange Online > rekord MX oraz TXT. Zapiszmy sobie gdzieś te rekordy, przydadzą nam się do konfigurowania bramki.

    ![[PL] Emaile z aplikacji / urządzeń do naszych skrzynek w Office365? To możliwe!](/assets/images/posts/2018/emaile-z-aplikacji-urzadzen-do-naszych-skrzynek-w-office365-to-mozliwe/01.png)

2) W kroku drugim musimy znać publiczny adres IP z którego będą wychodzić wiadomości. W przypadku naszego biura to raczej nie będzie problemem. Ja dla przykładu użyłem hosting myDevil.net. Znając adres IP robimy sobie z niego notatkę.
3) W kroku trzecim musimy udać się do naszego usługodawcy gdzie trzymamy swoją domenę w celu modyfikacji ustawień DNS. Pamiętacie rekord TXT z naszego pierwszego wpisu? U mnie wygląda on tak:
v=spf1 include:spf.protection.outlook.com -all
Trzeba go zmodyfikować, aby wiadomości wychodzące z danego adresu IP nie były traktowane jako SPAM, więc do boju.
Weźcie adres IP z drugiego kroku, i wpiszcie go zamiast ciągów znaków xxx.xxx.xxx.xxx
v=spf1 ipv4:xxx.xxx.xxx.xxx include:spf.protection.outlook.com -all
4) Wracamy do Office365 Admin Center. Z lewej strony rozwińmy menu Admin centers, następnie Exchange. Skrót ten otworzy nam kosolę Exchange.
5) Przejdźmy do zakładki: mail flow > connectors. W kroku tym ustalimy, że wszystkie wiadomości przychodzące z adresu IP podanego w drugim punkcje będą przepuszczane do naszych skrzynek odbiorczych.
Tworzymy nową regułę. Z pola From wybieramy: Your organization’s email server, w polu To wybieramy Office 365.
Uzupełniamy nazwę oraz opis reguły, zostawiamy włączone dwie opcje i przechodzimy dalej gdzie będziemy uzupełniać najciekawszą rzecz, czyli adres IP.
Zaznaczcie opcję drugą i dodajcie adres IP, potem Next i Finish.
Gotowa reguła u mnie wygląda w taki sposób:

    ![[PL] Emaile z aplikacji / urządzeń do naszych skrzynek w Office365? To możliwe!](/assets/images/posts/2018/emaile-z-aplikacji-urzadzen-do-naszych-skrzynek-w-office365-to-mozliwe/02.png)

I… To by było na tyle jeżeli chodzi o całą konfigurację po stronie naszego dostawcy poczty.

Ale w jaki sposób użyć tego w naszych skryptach? Albo jak skonfigurować taki skaner?

Przypomnijcie sobie rekord MX z pierwszego punktu.
Macie? To dobrze.

Jako adres serwera SMTP wpisujecie właśnie treść tego rekordu MX.

Do wysyłki użyjemy portu 25 oraz zabezpieczenia SSL/TLS bez uwierzytelniania. Dlaczego bez? Bo gdybyśmy chcieli użyć z to musimy przypisać temu skanerowi konkretną licencję czego chcieliśmy uniknąć.

Jeżeli będziecie potrzebować gotowego przykładu np. dla PHP, dajcie znać! Jest zawsze gdzieś pod ręką!
