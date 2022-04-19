# DHCP - Dynamic Host Configuration Protocol

## Topika: Úvod, nastavení v IOS, nastavení dedikovaného serveru, security

#### Úvod

UDP port - 67/68

|  |  
|---|---|
|67|HOST|
|68|SERVER/KLIENT|

*DHCP* je protokol nacházející se na Síťové vrstvě. Zajišťuje nám aby nové zařízení v síti mohli fungovat. Jeho předchůudci byli Reverse ARP a Bootstrap Portocol

Přiřazuje hostům:
- IP adresu
- NTP (Network Time Protocol (je to dobrý pro analýzu))
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
