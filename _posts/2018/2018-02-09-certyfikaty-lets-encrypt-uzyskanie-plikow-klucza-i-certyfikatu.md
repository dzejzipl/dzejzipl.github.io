---
title: "[PL] Certyfikaty Let’s Encrypt – uzyskanie plików klucza i certyfikatu"
categories:
    - Other
tags:
    - Lets Encrypt
    - PL Post

header-img: "/assets/images/posts/2018/certyfikaty-lets-encrypt-uzyskanie-plikow-klucza-i-certyfikatu/top.jpg"
subtitle:   "[PL] Certyfikaty Let’s Encrypt – uzyskanie plików klucza i certyfikatu"
---
![[PL] Certyfikaty Let’s Encrypt – uzyskanie plików klucza i certyfikatu](/assets/images/posts/2018/certyfikaty-lets-encrypt-uzyskanie-plikow-klucza-i-certyfikatu/top.jpg)Certyfikaty Let’s Encrypt – uzyskanie plików klucza i certyfikatu

Zapewne wiecie, że certyfikaty SSL są potrzebne praktycznie na każdej stronie, którą odwiedzacie, prawda?

Szczególnie na tych, gdzie przesyłacie swoje loginy, hasła albo inne wrażliwe dane.

Tak właściwie to SSL powinno być juz standardem na każdej stronie. Nawet na blogu mam zainstalowane od dłuższego czasu.

W dawnych czasach dowolne certyfikaty były drogie w sumie to nadal są. Najtańsze kosztują po 10 zł, które są wydawane przez lokalnych dostawców domen (np. home.pl), trochę droższe kosztują już około 150 zł, a jeżeli chcemy kupić taki, który prócz głównej domeny „ochroni” nam także nasze subdomeny to musimy wysłupać około 700 zł rocznie.

Sporo, prawda?

Podpowiem tylko, że to nie są najdroższe certyfikaty. Są jeszcze dużo droższe.

Do amatorskich zastosowań takich jak np. mój blog możemy użyć darmowego certyfikatu od Let’s Encrypt, który należy odnawiać co pół roku.

Nie jest to dużym problelem, ponieważ… Większosć porządnych firm hostingowych już oferuje automatyczne dodawanie certyfikatów do naszych stron. Z mojej strony mogę się wypowiedzieć, że dobrze to działa na TheCamels.org oraz mydevil.net gdzie obecnie posiadam hosting. O nic nie musimy się martwić, wszystko za nas robią automaty.

Ale… Nie o tym miał być ten wpis.

Przydarzyła mi się sytuacja, gdzie musiałem uzyskać certyfikat do testów jednego rozwiązania w Azure. Niby nic trudnego, kupuję najtańszy za 11 zł w Home.pl, generuję go dla danej subdomeny, ściągam pliki, wrzucam w chmurę, kończę testy.

Tylko po co? Skoro są darmowe certyfikaty a to pół roku w zupełności mi wystarczy na przetestowanie?

Natychmiast po tym pomyśle pojawiło się pytanie w jaki sposób wygenerować taki cert oraz pobrać niezbędne pliki *.key, *.cert ?

Trochę niżej znajdziecie odpowiedź kolegi @jnowwwak z informacją, że możemu użyć do tego portalu sslforfree.com o którym właśnie chcę dzis napisać.

Obsługa strony nie powinna nastręczyć nam żadnych problemów. Na początku polecam stworzyć swoje konto, dzięki czemu automatycznie dostaniemy wiadomość mailową w momencie gdy nasz certyfikat będzie się kończył. Jest to bardzo dobra opcja.

Samo generowanie nie sprawia żadnych trudności – wpisujemy adres, klikamy generuj i otrzymujemy trzy możliwości zweryfikowania się jako właściciel danego adresu:

![[PL] Certyfikaty Let’s Encrypt – uzyskanie plików klucza i certyfikatu](/assets/images/posts/2018/certyfikaty-lets-encrypt-uzyskanie-plikow-klucza-i-certyfikatu/01.png)

Dla mnie opcja trzecia jest zawsze najszybsza, jednak wy możecie wybrać każdą inną.

Po poprawnej weryfikacji otrzymujemy możliwość albo skopiowania plików, albo ich ściagnięcia na dysk w formie jednego pliku *.zip.

Co dalej?

To już zależy od was do czego wykorzystacie takie certyfikaty.

A ja polecam – szyfrujcie wszystko co możliwe.
