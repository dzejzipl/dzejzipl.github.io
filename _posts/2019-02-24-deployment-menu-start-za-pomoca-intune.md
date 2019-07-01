---
title: "[PL] Deployment Menu Start za pomocą Intune"
categories:
    - Intune
tags:
    - Intune
    - deployment
    - PL post
---
![Błąd Deployment Menu Start za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/IntuneTOP.png)Menu Start jakie jest – każdy widzi. Obrzydliwe.

Zobaczcie zresztą na screen jak to wygląda po domyślnej instalacji Windowsa:

![Deployment Menu Start za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploy-start-menu-using-intune/1.png)

Obrzydliwie, prawda? Dlaczego by nie dać w menu start tego co rzeczywiście potrzebują nasi końcowi użytkownicy? Np. tylko samych aplikacji Office?

Możemy to wszystko osiągnąć wprowadzając prosty profil a pomocą Intune.

Wpierw jednak musimy mieć dawcę tego ładnego start menu, prawda? Tworzymy więc odpowiednie menu na komputerze wzorcowym i eksportujemy je za pomocą prostej komendy w PowerShell bez uprawnień administratora

```powershell
Export-StartLayout -Path menu.xml
```

Jeżeli już wyeksportujemy to menu to przechodzimy do Intune i tworzymy nowy profil:

![Deployment Menu Start za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploy-start-menu-using-intune/3.png)

- Platform: **Windows 10 and later**
- Profile type: **Device restrictions**
- Scope: **Start**

W miejscu **Start menu layout** (4) wrzucamy swój plik XML, dostosowujemy pozostałe ustawienia, klikamy Save przypisujemy politykę do grupy….

Po chwili nasze menu będzie wyglądało w taki sposób:

![Deployment Menu Start za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deploy-start-menu-using-intune/2.png)

Schludniej, prawda?
