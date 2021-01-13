---
title: "[PL] Automatyczne usuwanie nieaktywnych urządzeń z Intune"
categories:
    - Intune
tags:
    - PL Post
---
![[PL] Automatyczne usuwanie nieaktywnych urządzeń z Intune](/assets/images/posts/automatyczne-usuwanie-nieaktywnych-urzadzen-z-intune/top.png)Automatyczne usuwanie nieaktywnych urządzeń z Intune

Testując Intune wdrażam kilka urządzeń tygodniowo do mojego Tenanta. Po jakimś czasie robi się tam całkiem duży burdel jeżeli chodzi o urządzenia. Większość jest nazwanych domyślnie, czyli Desktop-XXXXX, co powoduje zamieszanie. Telefony, tablety.. Urządzenia, które są już sformatowane dwukrotnie od długiego czasu. 

Denerwuje mnie to, że muszę scrollować takową listę, aby dotrzeć do tych urządzeń, które potrzebuję. 

Oczywiście, że mogę użyć wyszukiwania, ale czasem też należy posprzątać.

Logujemy się do https://devicemanagement.portal.azure.com (jest to bezpośredni link do zarządzania Intune) i wybieramy Devices, a następnie: Device cleanup rules

W nowo wybranej zakładce musimy zaznaczyć, że chcemy włączyć czyszczenie nieaktywnych urządzeń oraz wybrać zakres czasowy. Ja dla przykładu usunę urządzenia, które są nieaktywne 90 dni. 

![[PL] Automatyczne usuwanie nieaktywnych urządzeń z Intune](/assets/images/posts/automatyczne-usuwanie-nieaktywnych-urzadzen-z-intune/01.png)

Po kliknięciu na View affected devices zobaczymy listę urządzeń, które zostaną usunięte:

![[PL] Automatyczne usuwanie nieaktywnych urządzeń z Intune](/assets/images/posts/automatyczne-usuwanie-nieaktywnych-urzadzen-z-intune/02.png)

Szybki klik na Save, potwierdzamy usuniecie urządzeń i praca w naszym Intune będzie wygodniejsza.

Od teraz każde urządzenie, które ma status inactive, stale lub unresponsive będzie automatycznie usuwane po 90 dniach.

Have fun! 
