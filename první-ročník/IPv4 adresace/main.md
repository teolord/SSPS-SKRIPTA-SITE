# IPv4 adresace

- IPv4 adresy se dělí na dva základí typy, veřejné a privátní.

## Veřejné

## Privátní

- používají se v LAN a VPN

- jsou schované od WAN pomocí NAT

- jsou tři rozsahy sítě

|Class|Rozsah|Maska|Počet adres|
|---|---|---|---|
|A|10.0.0.0 - 10.255.255.255|8 - 255.0.0.0|16 777 216|
|B|172.16.0.0 - 172.31.255.255|12 - 255.240.0.0|1 048 576|
|C|192.168.0.0 - 192.168.255.255|16 - 255.255.0.0|65 536|
|local|127.0.0.0 - 127.255.255.255|8 - 255.0.0.0|16 777 216|

### Naši privátní adresu můžeme zjistit pomocí příkazu:

|OS|Příkaz|
|---|---|
|Windows| ipconfig|
|Linux| ip a|
|MacOS| (nikdo nepoužívá)|
