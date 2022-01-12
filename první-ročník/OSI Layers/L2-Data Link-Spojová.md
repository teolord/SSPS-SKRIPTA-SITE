### Spadá v TCP/IP pod Vrstvu síťového rozhraní.

## Topika: Účel Data Link vrstvy, Komponenty v síti, Protokoly, Protokolová datová jednotka, Full/Half Duplex komunikace

## Účel: 
- Zodpovídá za komunikaci mezi koncovými zařízeními. 
- Umožňuje přístup protokolům vyšší vrstvy k médiúm z fyzické vrstvy a enkapsuluje pakety z L3 (IPv4 a IPv6) do frame-rámců L2.
- Provádí detekci chybných rámců.

### Data Link Layer je često rozdělováná do dvou podvrstev Media Access Control Layer a Logical link control Layer.
**Media Access Control Layer**: Je zodpovědná za řízení, jak zařízení v síti získá přístup k síti a povoluje přenos dat.

**Logical Link Control Layer**: Tato podvrstva je zodpovědná za identitu a enkapsulaci protokolů síťové vrstvy a umožňuje vám najít chybný rámec.

## Komponenty v síti:
L2 Switch, Bridge, NIC(Síťová karta (u hostů)), Wireless Access Points

## Protokoly:
- **802.11(WLAN)**
- **WiFi**
- **Ethernet**
- **Token Ring**
- **PPTP (Point to Point Tunneling Protocol)** Pužíval se na VPN, v dnešní době není bezpečný.
- **PPP (Point to Point Protocol)** poskytuje stejné služby jako Serial line interface protocol. Je to robustní protokol, který přenáší ostatní typy packetů také s IP pakety. Poskytuje dva protokoly – LCP a NCP. PPP používá metody rámování, které popisují rámce. PPP se také nazývá znakově orientovaný protokol, který se používá k detekci chyb. PPC poskytuje ověřování připojení, kompresi dat, šifrování a přenos. Používá se v různých sítích, jako jsou telefonní linky, mobilní telefony, sériové kabely, dálkové linky, ISDN, specializované rádiové linky atd.
- **LCP (Link Control Protocol)** je součástí řídicího protokolu point-to-point. Pakety LCP určují standardy přenosu dat. Protokol LCP se používá k určení identity propojených zařízení, pokud je zařízení správné, akceptuje jej, jinak zařízení odmítne. Také určuje, zda je velikost paketu přijata nebo ne. Pokud požadavky překročí parametry, protokol řízení linky toto spojení ukončí.
- **NCP (Network Control Protocol)** je součástí PPP. Tento protokol se používá k vyjednávání parametrů a zařízení pro síťovou vrstvu. Pro každý protokol vyšší vrstvy podporovaný PPP existuje jeden NCP. IPCP ( Internet Protocol control protocol), DNCP (DECnet Phase IV Control Protocol), OSINLCP OSI Network Layer Control Protocol), IPXCP (Internetwork Packet Exchange Control Protocol), NBFCP (NetBIOS Frames Control Protocol), IPV6CP (IPv6 Control Protocol) jsou některá z NCP.


## Protokolová datová jednotka:
frame-rámec

## Full/Half Duplex komunikace:
### Full Duplex:
- Umožňuje oběma zařízením současně vysílat a přijímat na sdíleném médiu.
- Switche pracují ve full duplex režimu.

### Half Duplex: 
- Umožňuje pouze jednomu zařízení současně odesílat nebo přijímat na sdíleném médiu.
- Pužívá se u WLAN a BUS topologií

