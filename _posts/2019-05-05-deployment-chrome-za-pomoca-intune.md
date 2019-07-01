---
title: "[PL] Deployment Chrome za pomocą Intune"
categories:
    - Intune
tags:
    - Intune
    - Win32 Apps
    - PL post
---
![Deployment Chrome za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/IntuneTOP.jpg)
Długi czas temu do Intune weszła nowość, którą chciałbym dziś pokazać wam w praktyce, czyli deployment aplikacji Win32 za pomocą Intune.

W poście tym chciałbym wam pokazać w jaki sposób dodać aplikację Google Chrome w pliku *.msi do naszej organizacji w taki sposób, aby była do zainstalowania przez Company Portal.

Rozpoczynamy od ściągnięcia konwentera ze strony
[https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool) i wrzucenia go do folderu, do którego przejdziemy za pomocą CMD lub Powershella. Niech to będzie dla mnie: ***C:\Intune***.

Ściągnięty instalator – w samej paczce MSI wrzucam do ***C:\Intune\GoogleChrome\Installer***

Tak wygląda struktura folderów – prosta i szybka. Dlatego teraz pokrótce opiszmy w jaki sposób działa **Microsoft Win32 Content Prep Tool**.

Jest to plik exe, który posiada trzy parametry:

- -c, czyli folder w którym są pliki instalacyjne
- -s, czyli nasz plik instalacyjny
- -o, czyli nasz folder, do którego ma zostać wrzucony gotowy plik .intunewin
- Jest dostępny jeszcze parametr -h, który wyświetla pomoc.

Także po przejściu do folderu ***C:\Intune*** komenda do spakowania Google Chrome do pliku intunewin będzie wyglądać następująco:

```powershell
.\IntuneWinAppUtil.exe -c "C:\Intune\GoogleChrome" -s "C:\Intune\GoogleChrome\Installer\GoogleChromeStandaloneEnterprise64.msi" -o "C:\Intune\GoogleChrome"
```

Po kliknięciu Enter pojawi nam się pasek postępu jak i logi:

![Deployment Chrome za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deployment-chrome-za-pomoca-intune/1.png)

Posiadając teraz taki plik, przechodzimy do portalu Intune, Apps i rozpoczynamy od stworzenia nowej aplikacji Win32

Dodajemy plik stworzony wcześniej przez konwenter, ustawiamy niezbędne informacje i zaczyna się najlepsza zabawa.

W zakładce „Program” ustawiamy komendę instalacyjną jak i taką, która umożliwi odinstalowanie tego oprogramowania. W przypadku Chrome, zostało to automatycznie wykryte tak jak widać na screenie:

![Deployment Chrome za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deployment-chrome-za-pomoca-intune/2.png)

W zakładce Requirements ustawiamy dodatkowe opcje takie jak wersja systemu operacyjnego, minimalna ilość pamięci, dysku jak i jaka jest minimalna wersja systemu. Możemy ustawić również skonfigurować dodatkowe opcje o których w kolejnych postach.

Trzeba także ustawić reguły wykrywania, czy program jest poprawnie zainstalowany. Ja zrobiłem to w taki sposób, że sprawdzam czy w katalogu: ***%programfiles(x86)%\Google\Chrome\Application*** jest plik chrome.exe

![Deployment Chrome za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deployment-chrome-za-pomoca-intune/3.png)

Dla celów diagnostycznych możemy również ustawić informacje zwrotne, które ma zwracać instalator. W tym wypadku nie trzeba tego ruszać.

Po kliknięciu OK, aplikacja po uploadzie zostanie dodana, należy ją przypisać do grupy użytkowników i pojawi się ona w Company Portal

![Deployment Chrome za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deployment-chrome-za-pomoca-intune/4.png)

Po kliknięciu Install pojawi się komunikat….

![Deployment Chrome za pomocą Intune]({{ site.url }}{{ site.baseurl }}/assets/images/posts/deployment-chrome-za-pomoca-intune/5.png)

I wszystko.

W ten oto sposób możemy wrzucać paczki Win32 do naszego tenanta.
