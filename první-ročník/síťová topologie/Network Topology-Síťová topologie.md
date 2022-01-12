# Síťová Topologie

## V této kategorii se zabýváme Fyzickou a Logickou síťovou topologií.

## Topika: Úvod, Fyzická Topologie, Logická Topologie

## Úvod:
Topologie sítě charakterizuje strukturu, způsob jakým jsou mezi sebou propojeny jednotlivá koncová zařizení a datové toky mezi nimi.

## Fyzikcá Topologie:
Popisuje jakým způsobem jsou do sebe zařízení připojena. Najdeme zde informace kde se zařízení nachází budova, místnost, rack nebo jakým kabelem jsou zařízení spojena. 

## Logická Topologie: 
Zobrazuje adresy zařízení v síti, porty a názvy zařízení.

## Bus Topology:
(Sběrnicová Topologie)typický znak je přenosové páteřní vedení, které tvoří sběrnici ke které jsou připojeny veškeré prvky sítě. Zařízení se připojují k vedení pomocí tzv. T-konektorů. Jako vedení se používá sdílené přenosové médium koaxiální kabel který je zakončen BNC konektorem. Vedení je vždy nutné zakončit terminátorem, který zabraňuje zpětnému odrazu signálu a následnému útlumu signálu na vedení. 
Hlavním problémem této topologie je kolize. Jedná se o situaci, kdy v síti chtějí vysílat dvě zařízení ve stejnou chvíli. Aby se těmto kolizím předcházelo, je zapotřebí, aby každé připojené zařízení používalo protokol CSMA/CD. Jedná se o protokol (implementovaný síťovému adaptéru) pro přístup ke komunikačnímu kanálu, kdy stanice ověřuje, zdali je přenosová linka volná pro vysílání dat.

### Výhody: 
- jednoduchá realizace sítě a připojování dalších stanic
- malé náklady na stavbu sítě
- není nutný aktivní prvek řídící komunikaci v síti například router nebo switch

### Nevýhody: 
- při poškození (přerušení) vedení vypadne komunikace v celé síti – obtížný toubleshooting
- s přibývajícím počtem stanic, klesá datová propustnost sítě
- vysílanou informaci přijímají všechny stanice v síti – zbytečné zatěžování sítě.

### Tento způsob zapojení LAN se v dnešní době nepoužívá.

## Ring Topology:
je navržena tak, že zařízení tvoří uzavřený okruh. Data v této topologii procházejí pouze v jednom směru od vysílajícího zařízení přes všehna zařízení. 
Pro připojení jednotlivých zařízení k síti se používají stejné pasivní prvky jak u Bus Topology (koaxiální kabel, BNC konektor, T-konektor). Výhodou oproti Bus Topology je, že každá stanice funguje jako opakovač (zesiluje přenášený signál) a posílá ho dál.

### Výhody: 
- jednoduchá realizace sítě a připojování dalších zařízení
- malé náklady na realizaci sítě
- není nutný aktivní prvek řídící komunikaci v síti například router nebo switch

### Nevýhody: 
- při poškození (přerušení) vedení vypadne komunikace v celé síti – obtížně se hledá závada
- omezená délka kabelu i počtu připojených stanic
- s přibývajícím počtem stanic, klesá datová propustnost sítě
- vysílanou informaci přijímají všechny stanice v síti – zbytečné zatěžování sítě.

### Tento způsob zapojení LAN se v dnešní době nepoužívá. Využíval se v ARPanetu.

## Star Topology:
tato topologie připomíná svým zapojením hvězdu. Skládá se ze samostatných drátových pasivních prvků, které vedou od koncového zařízení k aktivním prvkům.

U Star Topology se pro spojení jednotlivých zařízení používá obvykle UTP kabel se 4 páry vodičů, zakončená konektorem RJ45. 

### Výhody:
- selhání jednoho cílového zařízení nezpůsobí výpadek celé sítě – lehký toubleshooting
- snadné vytvoření sítě a připojování zařízení k této síti

### Nevýhody:
- nutnost použití aktivního prvku pro řízení přenosu dat sítí
- větší spotřeba kabeláže 
- porucha či výpadek aktivního prvku způsobí ochromení celé sítě

## Tree Topology: 
je složena z několika sítí hvězdicové topologie. Tree Topology má tedy stejné výhody i nevýhody jako má Star Topology. Využívá se zde takzvaný Subnetting. Tento druh topologie se využívá zejména ve velkých firmách, kdy jednotlivé hvězdicové části sítě, představují například místnost. 

## Mesh Topology: 
jedná se o topologii, u níž je každé zařízení propojené s každým, které je připojeno do sítě (full mesh) nebo může být použita alternativa, kdy se některé spoje vynechají (částečný mesh). Tato topologie se využíva v IoT.

### Výhody: 
- selhání jednoho spoje neochromí celou síť

### Nevýhody:
- obtížná a nákladná instalace sítě
- větší spotřeba kabeláže neplatí u bezdrátových sítí
