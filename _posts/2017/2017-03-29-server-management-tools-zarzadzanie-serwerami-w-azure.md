---
title: "[PL] Server management tools – zarządzanie serwerami w Azure"
categories:
    - Azure
tags:
    - PL Post
---
![[PL] Server management tools – zarządzanie serwerami w Azure](/assets/images/posts/server-management-tools-zarzadzanie-serwerami-w-azure/top.png)Server management tools – zarządzanie serwerami w Azure

Cześć!

Ostatnio widziałem wiele wzmianek o Server management tools i postanowiłem to przetestować na żywym organizmie.

Czym jest Server Managment Tools? Jest to usługa w Azure, która pozwala nam monitorować jak i zarządzać daną maszynę. Dzięki niej jesteśmy w stanie sprawdzić od obciążenia procesora, po pamięć, dyski jak i sprawdzić reguły firewalla i przejrzeć jakie pliki są na dyskach. Jesteśmy w stanie sprawdzić jakie procesy są odpalone, maszyny wirtualne, a nawet przejrzeć zainstalowane role i usługi. Co jest najlepsze – mamy zdalnego klienta Powershell z przeglądarki do takiego serwera.

Na początek musimy skonfigurować usługę w portalu, przechodząc do: Tworzenie połączenia narzędzi do zarządzania serwerem.

![[PL] Server management tools – zarządzanie serwerami w Azure](/assets/images/posts/server-management-tools-zarzadzanie-serwerami-w-azure/01.png)

Uzupełniamy dwa parametry:

* Nazwa komputera – w tym polu wpisujemy nazwę komputera, jaka jest ustawiona w systemie, w moim przypadku: SRV003
* Utwórz nową bramę – w tym polu wpisujemy nazwę swojej bramy – ja użyłem: BramaSRV003

Po uzupełnieniu klikamy na: Create i po chwili ujrzymy panel administracyjny naszego połączenia, który będzie wyglądał w taki sposób:

![[PL] Server management tools – zarządzanie serwerami w Azure](/assets/images/posts/server-management-tools-zarzadzanie-serwerami-w-azure/02.png)

Aby rozpocząć konfigurowanie bramy, klikamy na:

**Gateway not detected. Click here to configure the gateway** i rozpoczynamy generowanie paczki instalacyjnej. Pozostawiłem zaznaczoną domyślną opcję – automatycznego aktualizowania oprogramowania. Przechodzimy niżej, klikamy na: Generate a package link, po chwili mamy indywidualny link do ściągnięcia na swojej maszynie.

Pobieramy, rozpakowujemy i ukazują nam się dwa pliki:

![[PL] Server management tools – zarządzanie serwerami w Azure](/assets/images/posts/server-management-tools-zarzadzanie-serwerami-w-azure/03.png)

Odpalamy Instalator, pozostawiłem opcję wygenerowania certyfikatu, bo żadnego nie posiadałem i po chwili klikamy Finish.

Po odświeżeniu naszej bramy w Azure pojawi nam się komunikat:

![[PL] Server management tools – zarządzanie serwerami w Azure](/assets/images/posts/server-management-tools-zarzadzanie-serwerami-w-azure/04.png)

Aby kontynuować, klikamy Manage as, aby wprowadzić login i hasło naszego administratora, którego użyjemy do monitorowania.

I niby to powinno być na tyle, prawda?

Nic z tego.

Pojawił mi się problem z podłączeniem – WinRM i te sprawy. Wystarczyło przewinąć trochę niżej stronę https://blogs.technet.microsoft.com/servermanagement/2016/02/09/introducing-server-management-tools/ aby przeczytać, że serwery nie będące w domenie mogą posiadać problemy z podłączeniem.

Co w takim wypadku?

Uruchomiłem linię komend z poziomu konta administratora i wklepałem poniższą komendę:

```powershell
winrm set winrm/config/client @{ TrustedHosts=”TargetMachineNameOrAddress” } 
```
gdzie jako TargetMachineNameOrAddress wpisałem srv003 – ponieważ tak moja maszyna się nazywała i taką nazwę nadałem w portalu Azure

Po chwili wprowadziłem jeszcze raz dane do konta administratora urządzenia i mój monitoring zaczął działać…

![[PL] Server management tools – zarządzanie serwerami w Azure](/assets/images/posts/server-management-tools-zarzadzanie-serwerami-w-azure/05.png)

Jest to dla mnie bardzo przydatne narzędzie. Już niedługo dodam do niego wszystkie moje nano serwery, ale to już w kolejnym wpisie…

Pozdrawiam!
