# Hrozby a bezpečnost v počítačových sítích

## Zabezpečení

### Konfigurace
- Dáváme si pozor aby důležité služby např. SSH a SFTP nebyly vystrčené do Internetu. Pokud k nim potřebujeme přistoupit můžeme využít VPN tunelování. Také si u těchto služeb dáváme pozor aby nebyli na větším portu než 1024. Jelikož v UNIXových systémech má ke konfiguračním souborům těchto služeb běžící na větším portu než 1024 každý uživatel přístup. 

### SOC (Security Operations Centre) a NOC (Network Operations Centre)

#### SOC

- vyskytuje se ve velkých infrastrukturách kde je zapotřebí monitorovat bezpečnost

- K monitorování se používá SIEM (Security Information and Event Management)

#### NOC

### IDS a IPS

#### Systém prevence a detekce průniku (Intrusion Prevention Systems)

- Slouží k chytré analýze provozu na síti, nečeká se na něj (jako např. u firewallu), sbírají se data do nějakého GUI, kde je mohou lidé nějak analyzovat. Bývají spíše u větších firem.

- NIC Promiscious mode - Jakýkoliv provoz na síti zaznamenán, ihned zasílán dál

- Nedílná součást středních a větších firem - v případě korporátů existence SOC - vyhodnocování bezpečnostních incidentů člověkem v reálném čase

- Nejedná se o automatická pravidla, která pak sama něco dělají, spíše jen podle nějakých pravidel se filtrují data, které pak analyzuje konkrétně člověk. (Platí především u IDS, jelikož IPS již umí na určité hrozby reagovat, kooperovat s Firewallem apod.)

- **IDS** - <u>pasivní systém!</u>

- **IPS** - Rozšíření IDS, umí jak provoz na síti, tak aktivity OS. Zároveň již může komunikovat s Firewallem a může na něco reagovat. Umí také opravovat chybný CRC, chybné řazení TCP paketů apod. - jedná se o <u>aktivní systém!</u>

  

#### Popis druhů a jejich využití

-   **Network-based Intrusion Prevention (NIPS):**

    -   Monitoruje celou síť na podezřelou aktivitu analyzováním síťového provozu.

    -   Např.: Snort

-   **Wireless Intrusion Prevention System (WIPS):**

    -   Monitoruje bezdrátovou síť na podezřelou aktivitu analyzováním síťových **protokolů** bezdrátových sítí.

-   **Network Behavior Analysis (NBA):**

    -   Zkoumá síťový provoz kvůli identifikaci hrozeb, které generují neobvyklý provoz na síti, jako například útoky DDoS (odmítnutí služby), určité formy malware a porušení zásad.

-   **Host-based Intrusion Prevention (HIPS):**

    -   Instalovaný softwarový balíček, který monitoruje jediný počítač na podezřelou aktivitu analyzováním událostí, které se na tomto počítači právě provádí včetně integrity souborů

    - Např.: OSSE
    
      

####  IDS Solution -- Jak to funguje

-   **Signature detection**

    -   Kontrola podpisů podle seznamu podpisů určitých útoků

    -   **Malý počet false positives** - Upozornění systému, na něco, co si myslí, že je hrozba, ale ve skutečnosti není

    -   **Větší počet false negatives** - Upozornění, co jsou reálnou hrozbou, ale systém je nezachytí

    -   Snort

-   **Anomaly Detection**

    - Zjištění normálního provozu - zjišťuje normální chování sítě, podle kterého se učí

    - Upozornění při neobvyklých událostech

    - **Větší počet false positives**

    - **Menší počet false negatives**
    
      ![](20-output.png)
    
    - Output vypadá jako typický LOG - Čas, source, destination, popis útoku a jeho priorita
    
      

#### Nastavení nástrojů

-   **<https://github.com/StamusNetworks/SELKS> - kombinace různých nástroju (Surikata, elastic, logstash atd.)**
    -   Instalace podobná jako když člověk instaluje čistě Debian
    
    -   Vše pod jednou aplikací
    
-   **Surikata**

    -   Pravidla (sources) si nepíše člověk sám, spíše se někde stahují nebo kupují

    -   Snort pravidla jdou konvertovat na surikatu

-   **Snort**
    -   Pravidla - pokud si platíte, tak je máte o měsíc dříve, za 30 dní od vydání již vychází pro všechny zadarmo
    
    -   Existuje jak pro Linux, tak pro Windows, ale je to napsané spíše pro Linux - pro Windows potřeba změnit některé defaultní konfigurace
    
    -   **Snort.conf** - Soubor pro hlavní konfiguraci snortu, povolování portů, cesty k pravidlům
    
    -   **Local.rules** -- Soubor pro vlastní pravidla pokud nám něco v zakoupených pravidlech chybí (ID 1 000 000 a více je pro vlastní pravidla)
    
    -   `Snort -w` - Všechny interface
    
    -   `-T` pro test `-A` zapnutí, poté následuje otázka, kam vypsat výstup
    
    -   Typický syntax: `snort -i 2 -c c:\Snort\etc\snort.conf -A console`
    
    -   Po ukončení následuje velké shrnutí
    
-   **Elastic search**
    -   Indexovaná databáze - díky indexům dokáže program velmi rychle pracovat s databází
    
-   **Kibana**
    -   Webové rozhraní nad elastic search
    
    -   Vytváří rozhraní, kde jsou zajímavé grafy a informace z elastic searche
    
-   **Kismet**

    -   Bohatý nástroj pro práci s bezdrátovými sítěmi

    -   Součást nástrojové sady je také IDS pro bezdrátové sítě


### Firewall

- Softwarové programy nebo hardwarová zařízení, která filtrují a zkoumají informace přicházející prostřednictvím připojení k internetu (z vnějšího světa do sítě)

-   **Hardwarový** (personální) firewall = samostatné hardwarové řešení pro ochranu počítačové sítě

    -   Malá nebo žádná konfigurace (zabudovány do hardwaru)

    -   Umístěn před vstupem do lokální sítě a tedy filtruje přístup ke všem prostředkům v dané síti

    -   Hardwarové brány firewall poskytují základní zabezpečení pro IoT, např.: chytré žárovky (často slabé funkce zabezpečení)

-   **Softwarový** (síťový) firewall = realizován na koncových stanicích (počítačích)

    -   Umístěn na samostatných počítačích

    -   Filtruje příchozí a odchozí komunikaci mezi počítačem a vnějším internetem(WAN)

    -   Více konfigurace než hardwarový firewall

    -   **Windows:** Windows Firewall, Norton 360, Avast Internet Security

    -   **Linux:** `iptables`, `nftables`

- **Bezpečnostní politika firewallu** = Nastavení pravidel pro komunikaci přes firewall (dnes už nemusí být pouze pravidla, ale i překlady adres (NAT) atd.)

- Při nastavování pravidel je dobré si určit, jak moc je síť vystavena útokům a jak moc je třeba dbát na bezpečnost. Např.: U vás doma je síť vystavena mnohem menšímu riziku, než datový server s citlivými informacemi
