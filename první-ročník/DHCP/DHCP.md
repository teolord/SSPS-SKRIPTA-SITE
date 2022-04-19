# DHCP - Dynamic Host Configuration Protocol

## Topika: Úvod, nastavení v IOS, nastavení dedikovaného serveru, security

### Úvod

67 - HOST

68 - SERVER

*DHCP* je protokol nacházející se na Síťové vrstvě. Zajišťuje nám aby nové zařízení v síti mohli fungovat. Jeho předchůdci jsou Reverse ARP a Bootstrap protokol. 

#### Přiřazení adresy
- probíhá 4 way handshakem.

> Host pošle DHCPDISCOVER na portu 68 na broadcast aby našel DHCP server
> Server odpoví DHCPOFFER na portu 67 a nabídne adresu, hosta najde pomocí MAC adresy
> Host pošle DHCPREQUEST na portu 68, žádá o nabídnutou IP adresu
> Server odpoví DHCPACKNOWLEDGE na portu 67, server potvrzuje přiřazení adresy a zapisuje si ho do "poolu"

Přiřazuje hostům:
- IPv4 adresu
- NTP (Network Time Protocol (pro analýzu))
- Gateway
- DNS server (například Cloudflare - 1.1.1.1 nebo Google - 8.8.8.8)

##### Chování serveru

Server může vyslat následující typy zpráv

|Typ|Popis
|---|---|
|DHCPOFFER|Nabídka adresy spolu s konfigurací sítě|
|DHCPACK|Potvrdí žádost|
|DHCPNAK|Odmítne žádost|

##### Chování klienta

Klient může serveru vyslat následující typy zpráv

|Typ|Popis
|---|---|
|DHCPDISCOVER|Zažádá o adresu|
|DHCPREQUEST|
|DHCPDECLINE|Klient odmítá nabízenou adresu, zjistil, že je již použita|
|DHCPRELEASE|Klient se zbavuje adresy, je možné ji zase půjčovat|
|DHCPINFORM|
