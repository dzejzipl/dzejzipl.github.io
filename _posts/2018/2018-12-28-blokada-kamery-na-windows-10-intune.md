---
title: "[PL] Blokada Kamery na Windows 10 – Intune"
categories:
    - Intune
tags:
    - PL Post
---
![[PL] Blokada Kamery na Windows 10 – Intune](/assets/images/posts/blokada-kamery-na-windows-10-intune/top.png)Blokada Kamery na Windows 10 – Intune

Robiąc laba uświadomiłem sobie, że warto było by się pochwalić rzeczami, którymi się nauczyłem, prawda? W końcu po to one służą.

No to dla przykładu nauczyłem się w jaki sposób stworzyć dynamiczną politykę, która zablokuje nam kamerę w momencie, gdy będziemy podłączeni pod daną sieć. Jest rozpoznawane to poprzez adresu IP bramy sieciowej, lokalizacji i innych składowych. Z tego co mówi nam dokumentacja to możemy również zablokować kamerę w określonych godzinach.

Nie wiem czy tworzyliśmy już polityki, ale jeżeli nie to rozpocznijmy i stwórzmy opisującą właśnie ten przykład.

Otwieramy portal Intune, rozpoczynamy od przejścia do Device Configuration > Profiles > Create Profile
Platform: Windows 10 and later
Profile type: Custom
Jak na poniższym screenie:

![[PL] Blokada Kamery na Windows 10 – Intune](/assets/images/posts/blokada-kamery-na-windows-10-intune/01.png)

Musimy stworzyć trzy wpisy od OMA-URI, które mają treść następującą:

1) Name: SettingsPack
2) OMA-URI:
```
./Vendor/MSFT/DynamicManagement/Contexts/NetworkBased/SettingsPack.
```
3) Data-Type: String
4) Value:
```<SyncML>
<SyncBody>
<Replace>
<CmdID>1331</CmdID>
<Item>
<Target>
<LocURI>./Vendor/MSFT/Policy/Config/Camera/AllowCamera</LocURI>
</Target>
<Meta>
<Format xmlns="syncml:metinf">int</Format>
</Meta>
<Data>0</Data>
</Item>
</Replace>
<Final/>
</SyncBody>
</SyncML>
```

1) Name: SignalDefinition
2) OMA-URI: 
```
./Vendor/MSFT/DynamicManagement/Contexts/NetworkBased/SignalDefinition
```
3) Data-Type: String
4) Value:
```
<rule schemaVersion="1.0">
<signal type="ipConfig">
<ipv4Gateway>10.0.0.254</ipv4Gateway>
</signal>
</rule>
// Pamiętajmy, aby ustawić poprawnie bramkę.
```

1) Name: NotificationsEnabled
2) OMA-URI: ./Vendor/MSFT/DynamicManagement/NotificationsEnabled
3) Data-Type: Boolean
4) Value: True

![[PL] Blokada Kamery na Windows 10 – Intune](/assets/images/posts/blokada-kamery-na-windows-10-intune/02.png)

Po przypisaniu polityki do odpowiedniej grupy możemy rozpocząć testowanie.

Tak wygląda gdy polityka nie jest aktywna i jesteśmy w sieci innej niż wpisana powyżej:

![[PL] Blokada Kamery na Windows 10 – Intune](/assets/images/posts/blokada-kamery-na-windows-10-intune/03.png)

Natomiast tak wygląda gdy polityka jest aktywna:

![[PL] Blokada Kamery na Windows 10 – Intune](/assets/images/posts/blokada-kamery-na-windows-10-intune/04.png)
