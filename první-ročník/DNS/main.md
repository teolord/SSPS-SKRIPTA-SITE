# Domain Name System

|Protocol|Port|
|---|---|
|TCP|53|
|UDP|53|

- protocol na aplikační vrstvě

- Lidé přistupují k informacím online prostřednictvím názvů domén, jako ssps.cz. Webové prohlížeče komunikují prostřednictvím IP adres. DNS překládá názvy domén na IP adresy.

- Proces překladu DNS zahrnuje převod názvu cíle (např. ssps.cz) na počítačově vhodnou IP adresu (např. 185.99.71.99). Když chce uživatel načíst webovou stránku, musí dojít k překladu mezi tím, co uživatel zadá do svého webového prohlížeče (ssps.cz) a strojově přívětivou IP adresou nezbytnou k nalezení webové stránky.

- Abychom porozuměli procesu, který stojí za DNS, je důležité dozvědět se o různých hardwarových komponentách, mezi kterými musí DNS dotaz projít. U webového prohlížeče probíhá vyhledávání DNS "na pozai" a nevyžaduje žádnou interakci z počítače uživatele kromě počátečního dotazu.

## Pro načtení domény se využívají 4 servery

#### DNS recursor

- DNS rekurzor si lze představit jako knihovníka, který je požádán, aby šel najít konkrétní knihu. DNS rekurzor je server navržený pro příjem dotazů z klientských počítačů prostřednictvím aplikací, jako jsou webové prohlížeče. Rekurzor je pak obvykle odpovědný za vytváření dalších požadavků, aby odpověděl na DNS dotaz klienta.

#### Root nameserver

- Root nameserver je prvním krokem při překladu domén na IP adresy. Lze si to představit jako rejstřík v knihovně, který registruje regály s knihami – obvykle slouží jako odkaz na další specifičtější servery.

#### TLD nameserver

- TLD nameserver (TLD - Top Level Domain) si lze představit jako konkrétní regál s knihami v knihovně. Tento jmenný server je dalším krokem při hledání konkrétní IP adresy a je hostitelem poslední části názvu hostitele (Na ssps.cz je server TLD „cz“).

#### Authoritative nameserver

- Tento konečný jmenný server si lze představit jako slovník na polici s knihami, ve kterém lze konkrétní jméno přeložit do jeho definice. Autoritativní jmenný server je poslední zastávkou v dotazu na jmenný server. Pokud má autoritativní jmenný server přístup k požadovanému záznamu, vrátí IP adresu pro požadovaný název cíle zpět DNS rekurzoru, který provedl počáteční požadavek.

## DNS queries

- Při typickém vyhledávání DNS se vyskytují tři typy dotazů. Použitím kombinace těchto dotazů může optimalizovaný proces pro překlad DNS vést ke snížení uběhlé cesty dat. V ideální situaci budou k dispozici data záznamů uložených v mezipaměti, což umožní jmennému serveru DNS vrátit nerekurzivní dotaz.

#### Recursive query

- V rekurzivním dotazu klient DNS vyžaduje, aby DNS server (obvykle rekurzivní překladač DNS) klientovi odpověděl buď požadovaným záznamem prostředku, nebo chybovou zprávou, pokud překladač nemůže záznam najít.

#### Iterative query

- V této situaci klient DNS umožní DNS serveru vrátit nejlepší možnou odpověď. Pokud dotazovaný DNS server nemá shodu s názvem dotazu, vrátí odkaz na server DNS autoritativní pro nižší úroveň oboru názvů domény. DNS klient poté zadá dotaz na adresu doporučení. Tento proces pokračuje s dalšími servery DNS v řetězci dotazů, dokud nenastane chyba nebo časový limit.

#### Non-recursive query

- Obvykle k tomuto dochází, když klient požádá překladače o záznam, ke kterému má přístup DNS server, buď protože je autoritativní pro záznam, nebo záznam existuje uvnitř jeho mezipaměti. DNS server obvykle ukládá záznamy do mezipaměti, aby se zabránilo další spotřebě bandwithu a zatížení na nadřazených serverech.
