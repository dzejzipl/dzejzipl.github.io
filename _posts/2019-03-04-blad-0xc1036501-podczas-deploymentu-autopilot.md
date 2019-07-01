---
title: [PL] Błąd 0xc1036501 podczas deploymentu AutoPilot
categories:
    - Intune
tags:
    - autopilot
    - deployment
    - intune
    - self service
---
![Błąd 0xc1036501 podczas deploymentu AutoPilot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploying-wi-fi-profile-connection-using-intune/top.png)
Bawiąc się Self-Service autopilotem natrafiłem na błąd, który uniemożliwiał mi poprawne wdrożenie komputera z takim profilem. Za każdym razem pojawiał mi się ten błąd. Jedyne co w Internetach znalazłem prowadziło mnie na strone [More Than just ConfigMgr](https://www.petervanderwoude.nl/post/windows-autopilot-self-deploying-mode/), ale bez wyraźnej wskazówki co może być nie tak.

0xc1036501

Postanowiłem rozwiązać ten problem, ponieważ chciałem w końcu przejść przez self deployment profile.

Rozpocząłem od pobrania logów z maszyny, wrzucenia ich na pendrive i otworzenia na komputerze, na którym pracuję.

Moim oczom ukazał się błąd jak na screenie:

![Błąd 0xc1036501 podczas deploymentu AutoPilot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/error-0xc1036501-while-self-service-at-autopilot/1.png)

No dobra, ale to nadal nic nie mówi, prawda?

Szukając informacji na Internecie w końcu doszedłem do tego, że błędem jest to, że ma się więcej niż jedną usługę pozwalającą na enrollment. W moim wypadku, był to Intune jak i Intune. Nie wiem skąd się wziął ten drugi, ale tam był.

![Błąd 0xc1036501 podczas deploymentu AutoPilot]({{ site.url }}{{ site.baseurl }}/assets/images/posts/error-0xc1036501-while-self-service-at-autopilot/2.png)

Usunąłem to z **Azure AD** > **Mobility (MDM and MAM)**, restart urządzenia i wszystko zaczęło działać jak złoto.
