---
title: "[PL] OSX, PowerShell… I zło konieczne."
categories:
    - Krótko
    - Azure
tags:
    - PL Post
---
![[PL] OSX, PowerShell… I zło konieczne!](/assets/images/posts/osx-powershell-i-zlo-konieczne/top.jpg)Azure AD, O365, zła kolejność… I frytki do tego!

Cóż, zło konieczne nastąpiło.

Przesiadłem się na system OSX. Mac OSX. Mac OS. Zwał jak zwał.  Od dziś, będę go używał do codziennej pracy. Blogowania, pisania stron w WordPressie jak i uwaga… Zarządzania Azurem przez Powershella. Ogólnie postaram się wykonywać wszystkie niezbędne prace już tylko na nim.

A tymczasem chciałem napisać, że miałem potrzebę zalogować się do swojego AAD za pomocą PowerShella i dokonać jednej modyfikacji. Ale… Jak to zrobić na OSX?

Z pomocą przychodzi nam wujek Google, który podaje nam link: https://github.com/PowerShell/PowerShell pod który wchodzimy i ściągamy odpowiedni pakiet dla naszego systemu, np. mnie interesuje ten link: https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-beta.3/powershell-6.0.0-beta.3-osx.10.12-x64.pkg

Instalujemy normalnie jak każdy inny pakiet.

Następnie ściągamy Azure CLI tym poleceniem:

```
curl -L https://aka.ms/InstallAzureCli | bash
```

Po zainstalowaniu dużej ilości dodatkowych pakietów, możemy odpalić naszą pierwszą sesję w AzureCLI.

![[PL] OSX, PowerShell… I zło konieczne!](/assets/images/posts/osx-powershell-i-zlo-konieczne/01.png)

Do zalogowania się użyjemy komendy az login, po chwili wyskoczy nam komunikat, że musimy się autoryzować poprzez wpisanie kodu na stronie https://aka.ms/devicelogin.

Po poprawnej autoryzacji pojawią się dostępne dla naszego konta subskrypcje.
