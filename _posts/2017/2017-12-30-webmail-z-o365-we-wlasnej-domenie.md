---
title: "[PL] Webmail z O365 we własnej domenie?"
categories:
    - Krótko
tags:
    - PL Post
---
![[PL] Webmail z O365 we własnej domenie?](/assets/images/posts/podsumowanie-oraz-plany/top.jpg)Webmail z O365 we własnej domenie?

Dziś przyszło mi do głowy, że użytkownikom, którzy używają mojego O365 wolałbym podawać adres w postaci webmail.domena.pl zamiast dłuższego adresu w postaci https://outlook.office365.com/owa/nazwaorganizacji/ 🙂

Przeszukałem całkiem sporo Internetu w jaki sposób mogę rozwiązać tę zagwozdkę – większość kierowała mnie na porady w stylu: utwórz rekord CNAME na adres, który podałem wyżej… No spoko, fajne rozwiązanie, ale cname nie może kierować strony, które mają w adresach „/” 😉

Więc jak to zrobić?

Postanowiłem, że utworzę sobie subdomenę na hostingu, dodam do niej darmowy certyfikat Let’s Encrypt, a do folderu na serwerze z domeną wrzucę tylko jeden plik .htaccess z bardzo krótką zawartością:

Redirect 301 / https://outlook.office365.com/owa/nazwaorganizacji/

I to wszystko.

Bardzo krótka porada, a rozwiązuje bardzo dużo problemów.

Nie wiem tylko jak to się sprawdzi w środowiskach hybrydowych 🙂
