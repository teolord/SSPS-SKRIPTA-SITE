# DHCP - Dynamic Host Configuration Protocol

## Topika: Úvod, nastavení v IOS, nastavení dedikovaného serveru, security

### Úvod

67 - HOST

68 - SERVER

*DHCP* je protokol nacházející se na Síťové vrstvě. Zajišťuje nám aby nové zařízení v síti mohli fungovat. Jeho předchůdci jsou Reverse ARP a Bootstrap protokol. 

#### Přiřazení adresy
- probíhá 4 way handshakem.

> Host pošle DHCPDISCOVER na portu 68 na broadcast aby našel DHCP server
> 
> Server odpoví DHCPOFFER na portu 67 a nabídne adresu, hosta najde pomocí MAC adresy
> 
> Host pošle DHCPREQUEST na portu 68, žádá o nabídnutou IP adresu
> 
> Server odpoví DHCPACKNOWLEDGE na portu 67, server potvrzuje přiřazení adresy a zapisuje si ho do "poolu"

Přiřazuje hostům:
- IPv4 adresu
- NTP (pro analýzu)
- Gateway
- DNS server (například Cloudflare - 1.1.1.1 nebo Google - 8.8.8.8)

### Nastavení DHCP na Switchi nabo Routeru s IOS

#### Základní konfigurace
```
SW(config)#ip dhcp pool NETWORK1                          //vytvoří pool se jménem 
SW(dhcp-config)#network 192.168.190.0 255.255.255.0       //nastaví adresní rozsah
SW(dhcp-config)#default-router 192.168.190.1              //Gateway adresa
SW(dhcp-config)#dns-server 1.1.1.1 8.8.8.8                //adresy DNS serverů (můžeme nastavit až 8 adres)
SW(dhcp-config)#lease 30                                  //pronájem adresy na 30 dní, formátje den hodina minuta (tedy třeba 0 0 10 = 10 minut)
```
