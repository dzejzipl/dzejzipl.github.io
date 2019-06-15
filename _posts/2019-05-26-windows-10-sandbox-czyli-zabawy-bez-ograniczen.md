---
title: "[PL] Windows 10 Sandbox, czyli zabawy bez ograniczeń."
categories:
    - Random
tags:
    - Windows 10
    - Sandbox
    - PL post
---
![Windows 10 Sandbox, czyli zabawy bez ograniczeń.]({{ site.url }}{{ site.baseurl }}/assets/images/top_images/SandboxTOP.jpg)
Testowanie wprowadzonych przez nas zmian może być dosyć kłopotliwe, szczególnie jeżeli są to zmiany, które polegają na instalacji oprogramowania.

Niby możemy zainstalować Hyper-V lub innego hypervisiora, ale czy nie lepsze było by wykorzystanie natywnej funkcji, która została zaprezentowana w Windows Insider, a kilka dni temu przeniesionej do Windows 10 1903?

Przedstawiam wam – Windows Sandbox, czyli miejsce, gdzie możemy sobie dowolnie modyfikować ustawienia systemu, a całość wróci do swojego pierwotnego stanu po ponownym uruchomieniu tego środowiska.

Wymagania są takie, że nasz procesor musi obsługiwać wirtualizację jak i posiadać tak z 2-4GB wolnej pamięci, trochę dysku jak i sprawny procesor. Sprawdzamy to w Task Manager:

![Windows 10 Sandbox, czyli zabawy bez ograniczeń.]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-10-sandbox-czyli-zabawy-bez-ograniczen/1.png)

Jeżeli wirtualizacja nie jest dostępna, sprawdźcie BIOS, może tam jest wyłączona.

Kolejnym wymaganiem jest wersja systemu > Pro lub wyżej. Niestety, na Windows 10 Home tym się nie pobawimy.

Rozpoczynamy od zainstalowania Sandboxa z Windows Features i restartujemy urządzenie.

![Windows 10 Sandbox, czyli zabawy bez ograniczeń.]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-10-sandbox-czyli-zabawy-bez-ograniczen/2.png)

Po restacie naszego komputera w menu start zobaczymy nową pozycję: Windows Sandbox.

![Windows 10 Sandbox, czyli zabawy bez ograniczeń.]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-10-sandbox-czyli-zabawy-bez-ograniczen/3.png)

Natomiast po jej uruchomieniu zobaczymy gotowe środowisko do pracy.

![Windows 10 Sandbox, czyli zabawy bez ograniczeń.]({{ site.url }}{{ site.baseurl }}/assets/images/posts/windows-10-sandbox-czyli-zabawy-bez-ograniczen/4.png)

Oczywiście – nie jest to tak rozbudowane jak nasza maszyna, nie wszystko działa poprawnie. Nie można dla przykładu instalować Windows Features, co jest mi ostatnio bardzo mocno przydatne. Ale wierzę w to, że produkt ten się bardzo mocno rozwinie.

No dobrze, ale co ? To wszystko? Może można to skonfigurować w jakiś sposób, aby wygodniej się pracowało? Ano można, dla przykładu zablokować dostęp do Internetu, albo udostępnić folder w trybie read only lub też do zapisu. Można wyłączyć VGPU albo też sprawić, że przy starcie będzie uruchamiał się określony program.

Moja testowa konfiguracja wygląda w taki sposób:

```xml
<Configuration>
<VGpu>Enable</VGpu>
<Networking>Enable</Networking>
<MappedFolders>
   <MappedFolder>
     <HostFolder>C:\Users\jakub\Downloads\Sandbox</HostFolder>
     <ReadOnly>false</ReadOnly>
   </MappedFolder>
   <MappedFolder>
     <HostFolder>C:\Users\jakub\Downloads\SandboxReadOnly</HostFolder>
     <ReadOnly>true</ReadOnly>
   </MappedFolder>
</MappedFolders>
<LogonCommand>
   <Command>explorer.exe C:\users\WDAGUtilityAccount\Documents</Command>
</LogonCommand>
</Configuration>
```

Jak używać takiego pliku? Tworzymy plik z rozszerzeniem *.**wsb** i pracujemy na nim jak na zwykłym pliku XML. W związku czym rozpoczynamy od <configuration> i dalej:

- VGPU – Bez podania tego parametru domyślnie VGPU zostanie włączone. Jeżeli ustawimy False – zostanie wyłączone.
- Networking – jak wyżej, jeżeli nie ustawimy na False sieć będzie włączona.
- MappedFolders – trochę lepsza zabawa, polegająca na mapowaniu folderów z hosta.
  - Parametr ReadOnly- true. Zamapowany folder będzie tylko w trybie do odczytu
  - Parametr ReadOnly – false. Zamapowany folder będzie także w trybie do zapisu. **UWAŻAJCIE Z TYM!**
- LogonCommand – podajemy, które komendy mają się odpalić na starcie. Może być to nawet IE 😉

Ogólnie – to rozwiązanie ma przyszłość, tylko przydało by się więcej opcji konfiguracyjnych.

Pamiętajcie też o tym, że po zamknięciu takiego Sandboxa – **danych z niego już nie odzyskacie**.
