---
title: Het vormen de Regels van de Filter van het Verkeer (met de Regels van WAF)
description: De Regels van de Filter van het Verkeer van het Gebruik (met de Regels van WAF) aan het Verkeer van de Filter
source-git-commit: dc0c7e77bb4bc5423040364202ecac3c59adced0
workflow-type: tm+mt
source-wordcount: '2690'
ht-degree: 0%

---


# Het vormen van de Regels van de Filter van het Verkeer (met de Regels van WAF) aan het Verkeer van de Filter {#configuring-cdn-and-waf-rules-to-filter-traffic}

>[!NOTE]
>
>Deze functie is nog niet algemeen beschikbaar. E-mail voor deelname aan het lopende programma voor vroegtijdige adoptie **aemcs-waf-adopter@adobe.com**, inclusief de naam van uw organisatie en context over uw interesse in de functie.

De Adobe probeert om aanvallen tegen klantenwebsites te verlichten, maar het kan nuttig zijn om verkeer pro-actief te filtreren die bepaalde patronen aanpassen zodat het kwaadwillige verkeer uw toepassing niet bereikt. Mogelijke benaderingen zijn:

* Apache-laagmodules zoals `mod_security`
* Het vormen de regels van de verkeersfilter die aan CDN via de configuratiepijplijn van de Manager van de Wolk worden opgesteld

Dit artikel beschrijft de benadering van de regels van de verkeersfilter. De meeste van deze regels blokkeren of staan verzoeken toe die op verzoekeigenschappen en verzoekkopballen, met inbegrip van IP, wegen, en gebruikersagent worden gebaseerd. Deze regels kunnen door alle AEM as a Cloud Service Plaatsen en klanten van Forms worden gevormd.

De klanten die van WAF (de Firewall van de Toepassing van het Web) toe:voegen-op vergunning geven kunnen een extra categorie van regels ook vormen genoemd &quot;de regels van de het verkeersfilter van WAF&quot; (of de regels van WAF voor kort). Deze regels van WAF blokkeren verzoeken die diverse patronen aanpassen gekend om met kwaadwillig verkeer worden geassocieerd. Neem contact op met het accountteam van de Adobe voor meer informatie over het verlenen van licenties voor deze toekomstige mogelijkheid. Let op: er is geen extra licentie vereist tijdens het programma voor vroege adoptie.

De filterregels van het verkeer kunnen aan alle types van het wolkenmilieu (RDE, dev, stadium, prod) in productie (niet zandbak) programma&#39;s worden opgesteld.

## Instellen {#setup}

1. Maak eerst de volgende map en bestandsstructuur in de map op hoofdniveau in de map it:

   ```
   config/
        cdn/
           cdn.yaml
   ```

1. `cdn.yaml` moeten metagegevens en een lijst met verkeersfilterregels en WAF-regels bevatten.

   ```
   kind: "CDN"
   version: "1"
   envType: "dev"
   data:
     trafficFilters:
       rules:
         ...
   ```

De &quot;kind&quot;parameter zou aan &quot;CDN&quot;moeten worden geplaatst en de versie zou aan de schemaversie moeten worden geplaatst, die momenteel &quot;1&quot;is. Zie onderstaande voorbeelden.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Om de regels van WAF te vormen, moet WAF in de Manager van de Wolk worden toegelaten, zoals hieronder voor zowel de nieuwe als bestaande programmascenario&#39;s wordt beschreven. Voor WAF moet een aparte vergunning worden aangeschaft.

   1. Om WAF op een nieuw Programma te vormen, controleer **WAF-DDOS-beveiliging** in het dialoogvenster **Beveiliging** zoals hieronder weergegeven. Ga door met het volgen van de stappen beschreven in [Productieprogramma toevoegen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) om uw programma te maken

   1. Om WAF op een bestaand programma te vormen, selecteer **Programma bewerken** door de in de [Programma&#39;s bewerken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) documentatie. Dan, in **Beveiliging** kunt u de optie WAF-DDOS op elk gewenst moment uitschakelen of controleren

1. Voor milieutypes buiten RDE, voer de configuratiepijplijn van de Manager van de Wolk uit, die zoals hieronder beschreven kan worden gevormd.

   1. Selecteer op de pijplijnkaart op de startpagina van Cloud Manager de optie **Productiepijpleiding toevoegen** of **Niet-productiepijpleiding toevoegen** om add pijpleidingstovenaar te lanceren
   1. Selecteren **Implementatiepijp** op het tabblad Configuratie

      ![Selecteer de optie van de Pijl van de Plaatsing](/help/security/assets/deployment.png)

   1. Geef uw pijpleiding een naam en selecteer plaatsingstrekkers, dan uitgezocht **Doorgaan**
   1. In de **Broncode** tab, selecteert u **Gerichte implementatie** selecteert u vervolgens **Config**

      ![Gerichte implementatie selecteren](/help/security/assets/target-deployment.png)

   1. Selecteer de opslagplaats en vertakking zoals nodig. Als er een Config-pijplijn voor de geselecteerde omgeving bestaat, is deze selectie uitgeschakeld.

      ![Overzicht van een Pijpleiding Config](/help/security/assets/config-pipeline.png)

      >[!NOTE]
      >
      > De gebruikers moeten als Manager van de Plaatsing worden het programma geopend om deze pijpleidingen te vormen of in werking te stellen.
      > Ook, kunt u slechts één pijpleiding Config per milieu vormen en in werking stellen.

   1. Selecteren **Opslaan**. Uw nieuwe pijpleiding zal in de pijpleidingskaart verschijnen en kan worden in werking gesteld wanneer u klaar bent.
   1. Voor RDEs, zal de bevellijn worden gebruikt, maar RDE wordt niet gesteund op dit ogenblik.

## Syntaxis verkeersfilterregels {#rules-syntax}

U kunt `traffic filter rules` om op patronen zoals IPs, gebruikersagent, verzoekkopballen, hostname, geo, en url aan te passen.

Klanten die een vergunning geven voor het aanbieden van WAF kunnen ook een speciale categorie regels van de verkeersfilter vormen genoemd `WAF traffic filter rules` (of de regels van de WAF voor kort) die één of meerdere vlaggen van de WAF van verwijzingen voorzien, die in zijn eigen sectie hieronder vermeld zijn.

Hier is een voorbeeld van een reeks regels van de verkeersfilter, die ook een regel van WAF omvat.

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: 
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

De indeling van de verkeersfilterregels in het bestand cdn.yaml wordt hieronder beschreven. Zie enkele voorbeelden in een latere sectie.


| **Eigenschap** | **De meeste regels van de verkeersfilter** | **Regels voor WAF-verkeersfilters** | **Type** | **Standaardwaarde** | **Beschrijving** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelnaam (64 tekens lang, alleen alfanumerieke tekens en -) |
| wanneer | X | X | `Condition` | - | De basisstructuur is:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>Zie Hieronder de syntaxis van de Condition Structure, die de getters, voorspellingen en hoe u meerdere voorwaarden kunt combineren beschrijft. |
| action | X | X | `Action` | log | log, allow, block, log of action object Default is log |
| rateLimit | X |   | `RateLimit` | niet gedefinieerd | Snelheidsbeperkende configuratie. Snelheidsbeperking is uitgeschakeld als deze niet is gedefinieerd.<br><br>Hieronder vindt u een aparte sectie waarin de syntaxis rateLimit wordt beschreven, samen met voorbeelden. |

### Voorwaardestructuur {#condition-structure}

Een voorwaarde kan een eenvoudige Voorwaarde of een groep Voorwaarden zijn.

**Eenvoudige voorwaarde**

Een eenvoudige voorwaarde bestaat uit een getter en een voorspelling.

```
{ <getter>: <value>, <predicate>: <value> }
```

**Groepsvoorwaarden**

Een groep Voorwaarden bestaat uit meerdere Eenvoudige en/of Groepsvoorwaarden.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **Eigenschap** | **Type** | **Betekenis** |
|---|---|---|
| **allOf** | `array[Condition]` | **en** -bewerking. true als alle vermelde voorwaarden true retourneren |
| **anyOf** | `array[Condition]` | **of** -bewerking. true als een van de vermelde voorwaarden true retourneert |

**Getter**

| **Eigenschap** | **Type** | **Beschrijving** |
|---|---|---|
| reqProperty | `string` | Request-eigenschap.<br><br>Een van: `path` , `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>De domeineigenschap is een kleine omzetting van de hostheader van de aanvraag. Het is nuttig voor tekenreeksvergelijkingen zodat de gelijken niet wegens hoofdlettergevoeligheid worden gemist.<br><br>De `clientCountry` gebruikt twee lettercodes die worden weergegeven bij [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) |
| reqHeader | `string` | Hiermee wordt aanvraagheader met de opgegeven naam geretourneerd |
| queryParam | `string` | Hiermee wordt de query-parameter met de opgegeven naam geretourneerd |
| koekje | `string` | Retourneert cookie met opgegeven naam |

**Voorspelend**

| **Eigenschap** | **Type** | **Betekenis** |
|---|---|---|
| **equals** | `string` | true als het resultaat van de getter gelijk is aan de opgegeven waarde |
| **doesNotEqual** | `string` | true als het resultaat van de getter niet gelijk is aan de opgegeven waarde |
| **leuk** | `string` | true als het resultaat van de getter overeenkomt met het opgegeven patroon |
| **notlike** | `string` | true als het resultaat van de getter niet overeenkomt met het opgegeven patroon |
| **matches** | `string` | true als het resultaat van de getter overeenkomt met opgegeven regex |
| **doesNotMatch** | `string` | true als het resultaat van de getter niet overeenkomt met opgegeven regex |
| **in** | `array[string]` | true als de opgegeven lijst het resultaat getter bevat |
| **notIn** | `array[string]` | true als de opgegeven lijst geen resultaat voor getter bevat |

### Handelingsstructuur {#action-structure}

Opgegeven door `action` veld dat een tekenreeks kan zijn die het handelingstype opgeeft (toestaan, blokkeren, vastleggen) en standaardwaarden aanneemt voor alle andere opties of een object waarvoor regeltype is gedefinieerd via `type` vereist veld en andere opties die op dat type van toepassing zijn.

**Typen handelingen**

De acties worden geprioriteerd volgens hun types in de volgende lijst, die wordt bevolen om op de ordeacties te wijzen wordt uitgevoerd:

| **Naam** | **Toegestane eigenschappen** | **Betekenis** |
|---|---|---|
| **toestaan** | `wafFlags` (optioneel) | als wafFlags niet aanwezig is, houdt verdere regelverwerking tegen en gaat aan het dienen van reactie te werk. Als wafFlags aanwezig is, maakt het gespecificeerde bescherming van WAF onbruikbaar en gaat aan verdere regelverwerking te werk. |
| **blok** | `status, wafFlags` (facultatief en wederzijds exclusief) | als wafFlags niet aanwezig is, retourneert de HTTP-fout waarbij alle andere eigenschappen worden overgeslagen, wordt de foutcode gedefinieerd door de status-eigenschap of is de standaardwaarde 406. Als wafFlags aanwezig is, laat het gespecificeerde bescherming van WAF toe en gaat aan verdere regelverwerking te werk. |
| **log** | `wafFlags` (optioneel) | registreert het feit dat de regel werd teweeggebracht, anders beïnvloedt niet de verwerking. wafFlags heeft geen effect |

### Lijst met WAF-markeringen {#waf-flags-list}

De `wafFlag` eigenschap kan het volgende omvatten:

| **Markering-id** | **Vlagnaam** | **Beschrijving** |
|---|---|---|
| SQLI | SQL-injectie | SQL de Injectie is de poging om toegang tot een toepassing te verkrijgen of bevoorrechte informatie te verkrijgen door willekeurige gegevensbestandvragen uit te voeren. |
| BACKEUR | Achterkant | Een achterdeursignaal is een verzoek dat probeert te bepalen als een gemeenschappelijk achterdeurdossier op het systeem aanwezig is. |
| CMDEXE | Opdracht uitvoeren | De Uitvoering van het bevel is de poging om controle te verkrijgen of een doelsysteem door willekeurige systeembevelen door middel van gebruikersinput te beschadigen. |
| XSS | Scripts voor meerdere sites | Met scripts die verwijzen naar andere sites wordt geprobeerd een gebruikersaccount of een webbrowsersessie te kapen via kwaadaardige JavaScript-code. |
| TRAVERSAL | Directorytraversal | Directorytraversal is de poging om bevoorrechte omslagen door een systeem in hoop te navigeren om gevoelige informatie te verkrijgen. |
| GEBRUIKER | Gereedschap Bijsluiten | De Tooling van de aanval is het gebruik van geautomatiseerde software om veiligheidskwetsbaarheid te identificeren of te proberen om een ontdekte kwetsbaarheid te exploiteren. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI-aanvallen proberen de [Log4Shell-kwetsbaarheid](https://en.wikipedia.org/wiki/Log4Shell) aanwezig in eerdere versies van Log4J dan 2.16.0 |
| AWS SSRF | AWS-SSRF | SSRF (Server Side Request Smeedery) is een verzoek dat probeert verzoeken te verzenden die door de webtoepassing worden gedaan om interne systemen te richten. De aanvallen van AWS SSRF gebruiken SSRF om de sleutels van Amazon Web Services (AWS) te verkrijgen en toegang tot S3 emmers en hun gegevens te krijgen. |
| BHH | Onjuiste koppen | De slechte Kopballen van de Hop wijzen op een HTTP het smokkelen poging door of een misvormde overdracht-Codering (TE) of een inhoud-Lengte (CL) kopbal, of een goed gevormde TE en kopbal CL |
| ABNORMALPATH | Abnormaal pad | Met Abnormal Path wordt aangegeven dat het oorspronkelijke pad afwijkt van het genormaliseerde pad (bijvoorbeeld `/foo/./bar` is genormaliseerd naar `/foo/bar`) |
| GECOMPRIMEERD | Compressie gedetecteerd | De POST aanvraaginstantie is gecomprimeerd en kan niet worden gecontroleerd. Als bijvoorbeeld een aanvraagheader &quot;Content-Encoding: gzip&quot; wordt opgegeven en de hoofdtekst van de POST geen onbewerkte tekst is. |
| DOUBLEENCODERING | Dubbele codering | De dubbele Codering controleert de ontduikingstechniek van het tweemaal coderen van HTML- karakters |
| FORCEFULBROWSING | Snel bladeren | Snel bladeren is de mislukte poging om beheerpagina&#39;s te openen |
| NOTUTF8 | Ongeldige codering | Ongeldige codering kan ertoe leiden dat de server schadelijke tekens van een verzoek in een reactie omzet, wat of een ontkenning van de dienst of XSS veroorzaakt |
| JSON-ERROR | JSON-coderingsfout | Een POST, PUT, of PATCH- verzoeklichaam dat als bevattende JSON binnen de &quot;Content-Type&quot;verzoekkopbal wordt gespecificeerd maar JSON het ontleden fouten bevat. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |
| MALFORMED-DATA | Onjuiste gegevens in de aanvraaginstantie | Een POST, een PUT, of PATCH verzoeken lichaam dat volgens de &quot;Inhoud-Type&quot;verzoekkopbal misvormd is. Bijvoorbeeld, als een &quot;Content-Type: application/x-www-form-urlencoded&quot;verzoekkopbal wordt gespecificeerd en een POST bevat die json is. Dit is vaak een programmeerfout, een geautomatiseerd of een kwaadwillig verzoek. Vereist agent 3.2 of hoger. |
| SANS | Verkeer van kwaadwillige IP | [SANS Internet Storm Center](https://isc.sans.edu/) lijst van IP adressen die om aan kwaadwillige activiteit zijn gemeld te hebben betrokken |
| SIGSCI-IP | Netwerkeffect | IP die door SignalSciences wordt gemarkeerd: Wanneer IP wegens een kwaadwillig signaal door de besluitvormingsmotor wordt gemarkeerd, zal dat IP aan alle klanten worden verspreid. De verdere verzoeken van die IP adressen die om het even welk extra signaal voor de duur van de vlag bevatten worden dan geregistreerd |
| NO-CONTENT-TYPE | Ontbrekende aanvraagheader &quot;Content-Type&quot; | Een POST-, PUT- of PATCH-aanvraag die geen aanvraagheader &quot;Content-Type&quot; heeft. Standaard moeten toepassingsservers in dit geval &#39;Content-Type: text/plain; charset=us-ascii&#39; aannemen. Bij veel geautomatiseerde en kwaadaardige verzoeken ontbreekt mogelijk het type inhoud. |
| NOUA | Geen gebruikersagent | Vele geautomatiseerde en kwaadwillige verzoeken gebruiken vals of ontbrekende Gebruiker-Agenten om het moeilijk te maken om het type van apparaat te identificeren dat de verzoeken maakt. |
| TORNODE | Teerverkeer | Tor is software die de identiteit van een gebruiker verbergt. Een piek in het verkeer van de Tor kan op een aanvaller wijzen die probeert om hun plaats te maskeren. |
| DATACENTER | Datacenter-verkeer | Datacenterverkeer is niet-biologisch verkeer dat afkomstig is van geïdentificeerde hostingproviders. Dit type van verkeer wordt niet algemeen geassocieerd met een echt eind - gebruiker. |
| NULLBYTE | Null Byte | Null-bytes worden normaal gesproken niet weergegeven in een verzoek en geven aan dat het verzoek onjuist is geformuleerd en mogelijk kwaadaardig is. |
| IMPOSTOR | SearchBot Impostor | Zoekbotweefsel is iemand die doet alsof hij een Google- of Bing-zoekbot is, maar die niet legitiem is. Opmerking: is niet afhankelijk van een reactie op zich, maar moet eerst worden opgelost in de cloud, zodat deze niet mag worden gebruikt in een prerule. |
| PRIVATEFIEL | Persoonlijke bestanden | Persoonlijke bestanden zijn doorgaans vertrouwelijk, zoals een Apache `.htaccess` bestand of een configuratiebestand dat vertrouwelijke informatie kan lekken |
| SCANNER | Scanner | Identificeert populaire scanservices en -gereedschappen |
| RESPONSESPLIT | HTTP-antwoordsplitsing | Identificeert wanneer CRLF-tekens als invoer naar de toepassing worden verzonden om headers in de HTTP-reactie te injecteren |
| XML-ERROR | XML-coderingsfout | Een POST, PUT, of PATCH aanvraaglichaam dat als bevattende XML binnen de &quot;Inhoud-Type&quot;verzoekkopbal wordt gespecificeerd maar XML het ontleden fouten bevat. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |

## Overwegingen {#considerations}

* Wanneer twee conflicterende regels worden gecreeerd, zullen de allow regels altijd belangrijkheid over de blokregels nemen. Bijvoorbeeld, als u een regel creeert om een specifieke weg en een regel te blokkeren om één specifiek IP adres toe te staan, zullen de verzoeken van dat IP adres op de geblokkeerde weg worden toegestaan.

* Als een regel wordt aangepast en geblokkeerd, reageert CDN met een `406` retourcode.

* De configuratiedossiers zouden geen geheimen moeten bevatten aangezien zij door iedereen leesbaar zouden zijn die toegang tot de git bewaarplaats heeft

## Voorbeelden van regels {#examples}

Hier volgen enkele regelvoorbeelden. Zie de [tarieflimiteringssectie](#rules-with-rate-limits) verder worden uitgewerkt voor voorbeelden van tariefbeperkingen.

**Voorbeeld 1**

Deze regel blokkeert verzoeken die van IP 192.168.1.1 komen:

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action: 
           type: block
```

**Voorbeeld 2**

Deze regel blokkeert aanvragen op pad `/helloworld` bij het publiceren met een Gebruiker-Agent die Chrome bevat:

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
     rules:
       - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
           allOf:
            - { reqProperty: path, equals: /helloworld }
            - { reqProperty: tier, equals: publish }
            - { reqHeader: user-agent, matches: '.*Chrome.*'  }
           action: 
             type: block
```

**Voorbeeld 3**

Deze regel blokkeert verzoeken die de vraagparameter bevatten `foo`, maar staat elk verzoek toe dat van IP 192.168.1.1 komt:

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when: { queryParam: url-param, equals: foo }
        action: 
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action: 
          type: allow
```

**Voorbeeld 4**

Deze regel blokkeert verzoeken aan weg /block-me, en blokkeert elk verzoek dat een patroon SQLI of XSS aanpast:

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: 
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

**Voorbeeld 4**

Deze regel blokkeert de toegang tot OFAC-landen:

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - { reqProperty: tier, equals: publish }
            - reqProperty: clientCountry
              in:
                - SY
                - BY
                - MM
                - KP
                - IQ
                - CD
                - SD
                - IR
                - LR
                - ZW
                - CU
                - CI
        action: block
```

## Regels met tarieflimieten {#rules-with-rate-limits}

Soms is het wenselijk om verkeer te blokkeren die een regel aanpassen slechts als de gelijke een bepaald tarief in tijd overschrijdt. Een waarde instellen voor de `rateLimit` eigenschap beperkt de snelheid van die aanvragen die overeenkomen met de regelvoorwaarde.

### rateLimit-structuur {#ratelimit-structure}

| **Eigenschap** | **Type** | **Standaard** | **BETEKENEN** |
|---|---|---|---|
| limiet | geheel getal van 10 tot en met 10000 | vereist | Het tarief van het verzoek in verzoeken per seconde waarvoor de regel wordt teweeggebracht |
| venster | geheel getal: 1, 10 of 60 | 10 | Samplingvenster in seconden waarvoor de aanvraagsnelheid wordt berekend |
| straf | geheel getal van 60 tot 3600 | 300 | Een periode in seconden waarvoor overeenkomstige verzoeken worden geblokkeerd (afgerond naar de dichtstbijzijnde minuut) |

### Voorbeelden {#ratelimiting-examples}

**Voorbeeld 1**

Deze regel blokkeert een client voor 5 m wanneer deze in de laatste 60 sec meer dan 100 req/sec heeft

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Voorbeeld 2**

De verzoeken van het blok voor 60s op weg /kritiek/middel wanneer het 100 req/sec in de laatste 60 sec. overschrijdt

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when: { reqProperty: path, equals: /critical/resource }
        action: 
          type: block
        rateLimit: { limit: 100, window: 60, penalty: 60 }
```

## CDN-logs {#cdn-logs}

AEM as a Cloud Service verleent toegang tot CDN logboeken, die voor gebruiksgevallen met inbegrip van de optimalisering van de geheim voorgeheugenklapverhouding, en het vormen van CDN en de regels van WAF nuttig zijn. CDN-logboeken worden weergegeven in Cloud Manager **Logbestanden downloaden** wanneer u de service Auteur of Publiceren selecteert.

De eigenschap &quot;rules&quot; beschrijft welke regels voor de verkeersfilter worden aangepast en heeft het volgende patroon:

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Bijvoorbeeld:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

De regels gedragen zich als volgt:

* de klant-verklaarde regelnaam van om het even welke passende regels zal in de gelijkenattributen worden vermeld.
* de actiekenmerken detailleert of de regels het effect van het blokkeren, toestaan of registreren hadden
* als WAF vergunning en toegelaten is, zal het waf attribuut van om het even welke wafregels (b.v., SQLI een lijst maken; merk op dat dit van de klant-verklaarde naam) onafhankelijk is die werden ontdekt, ongeacht of de waf regels in de configuratie werden vermeld.
* als geen klant-verklaarde regels aanpassen en geen golfregels aanpassen, zal het bezit van regelattributen leeg zijn.

In het algemeen, verschijnen de passende regels in de logboekingang voor alle verzoeken aan CDN, ongeacht of het een CDN hit, pas, of mis is. Nochtans, verschijnen de regels van WAF in de logboekingang slechts voor verzoeken aan CDN die als CDN missen of overgaan, maar niet CDN- klappen worden beschouwd.

In het onderstaande voorbeeld ziet u een voorbeeld van cdn.yaml en twee CDN-logitems:


```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS ]
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/block-me",
"method": "GET",
"res_ctype": "",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=path-rule,action=blocked"
}
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"rid": "974e67f6",
"host": "example.com",
"url": "/?sqli=%27%29%20UNION%20ALL%20SELECT%20NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL--%20fAPK",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

### Logbestandsindeling {#cdn-log-format}

Hieronder vindt u een lijst met veldnamen die in CDN-logbestanden worden gebruikt, samen met een korte beschrijving.

| **Veldnaam** | **Beschrijving** |
|---|---|
| *tijdstempel* | De tijd waarop de aanvraag is gestart, na beëindiging van TLS |
| *ttfb* | Afkorting van *Tijd naar eerste byte*. Het tijdinterval tussen het verzoek begon tot het punt alvorens het reactiekarakter begon te worden gestroomd. |
| *cli_ip* | Het client-IP-adres. |
| *cli_country* | Twee letters [ISO 3166-1](https://en.wikipedia.org/wiki/ISO_3166-1) alpha-2-landcode voor het land van de cliënt. |
| *afdanken* | De waarde van de verzoekkopbal die wordt gebruikt om het verzoek uniek te identificeren. |
| *req_ua* | De gebruikersagent die verantwoordelijk is voor het indienen van een bepaalde HTTP-aanvraag. |
| *host* | De autoriteit waarvoor het verzoek is bestemd. |
| *url* | Het volledige pad, inclusief queryparameters. |
| *methode* | HTTP-methode die door de client wordt verzonden, zoals &quot;GET&quot; of &quot;POST&quot;. |
| *res_ctype* | Het Content-Type dat wordt gebruikt om het oorspronkelijke mediatype van de bron aan te geven. |
| *cachegeheugen* | Status van de cache. Mogelijke waarden zijn HIT, MISS of PASS |
| *status* | De HTTP-statuscode als een geheel getal. |
| *res_age* | De hoeveelheid tijd (in seconden) dat een reactie in de cache is geplaatst (in alle knooppunten). |
| *pop* | Datacenter van de CDN-cacheserver. |
| *regels* | De naam van eventuele overeenkomende regels.<br><br>Geeft ook aan of de overeenkomst tot een blok heeft geleid. <br><br>Bijvoorbeeld &quot;`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`&quot;<br><br>Leeg als geen regels overeenkomen. |
