---
title: Verkeersfilterregels inclusief WAF-regels
description: Het vormen de Regels van de Filter van het Verkeer met inbegrip van de Regels van de Firewall van de Toepassing van het Web (WAF)
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: 221f6df73fe660c6f8dbf79affdccdd081ad3906
workflow-type: tm+mt
source-wordcount: '4210'
ht-degree: 0%

---


# Regels voor verkeersfilters, inclusief WAF-regels {#traffic-filter-rules-including-waf-rules}

>[!NOTE]
>
>Deze functie is nog niet algemeen beschikbaar. E-mail voor deelname aan het lopende programma voor vroegtijdige adoptie **aemcs-waf-adopter@adobe.com**, inclusief de naam van uw organisatie en context over uw interesse in de functie.

De filterregels van het verkeer kunnen worden gebruikt om verzoeken bij de laag te blokkeren of toe te staan CDN, die in scenario&#39;s zoals nuttig kan zijn:

* Toegang tot specifieke domeinen beperken tot intern bedrijfsverkeer, voordat een nieuwe site live gaat
* Vaststelling van tariefgrenzen zodat deze minder gevoelig zijn voor volumetrische aanvallen van DDoS
* Voorkomen dat IP-adressen waarvan bekend is dat ze kwaadaardig zijn, zich richten op uw pagina&#39;s

Sommige van deze regels van de verkeersfilter zijn beschikbaar aan alle AEM as a Cloud Service Plaatsen en klanten van Forms. Zij werken hoofdzakelijk op verzoekeigenschappen en verzoekkopballen, met inbegrip van IP, hostname, weg, en gebruikersagent.

Een subcategorie van de regels van de verkeersfilter vereist of een vergunning van de Veiligheid van de Bescherming WAF-DDoS. Deze krachtige regels zijn gekend als het verkeersfilterregels van het WAF (de Firewall van de Toepassing van het Web) (of de regels van WAF voor kort) en hebben toegang tot [WAF-vlaggen](#waf-flags-list) wordt verderop in dit artikel beschreven. Sites en Forms-klanten kunnen contact opnemen met hun accountteam voor Adoben voor meer informatie over het verlenen van licenties voor deze geavanceerde functionaliteit.

De filterregels van het verkeer kunnen via de configuratiepijpleidingen van de Manager van de Wolk worden opgesteld om, stadium, en de types van productiemilieu in productie (niet zandbak) programma&#39;s te ontwikkelen. Steun voor RDEs zal in de toekomst komen.

## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is onderverdeeld in de volgende secties:

* **Overzicht verkeersbeveiliging:** Leer hoe u tegen kwaadwillig verkeer wordt beschermd.
* **Voorgesteld proces voor het configureren van regels:** Lees meer over een methode op hoog niveau voor het beschermen van uw website.
* **Instellen:** Ontdek hoe te opstelling, vorm, en stel de regels van de verkeersfilter, met inbegrip van de geavanceerde regels van WAF op.
* **Syntaxis regels:** Lees over hoe te om de regels van de verkeersfilter in te verklaren `cdn.yaml` configuratiebestand. Dit omvat zowel de regels van de verkeersfilter beschikbaar aan alle Sites en klanten van Forms, als de subcategorie van de regels van WAF voor degenen die van dat vermogen vergunning geven.
* **Voorbeelden van regels:** Bekijk voorbeelden van gedeclareerde regels om u op weg te helpen.
* **Regels voor tarieflimieten:** Leer hoe u regels voor snelheidsbeperking gebruikt om uw site te beschermen tegen aanvallen met een hoog volume.
* **CDN-logbestanden:** Zie welke verklaarde regels en de Vlaggen van WAF uw verkeer aanpassen.
* **Dashboard-gereedschappen:** Analyseer uw CDN logboeken om nieuwe regels van de verkeersfilter omhoog te komen.
* **Zelfstudie:** Praktische kennis over de eigenschap, met inbegrip van hoe te om dashboardtooling te gebruiken om de juiste regels te verklaren.
<!-- About the tutorial: sets the context for a linked tutorial, which gives you practical knowledge about the feature, including how to use dashboard tooling to declare the right rules. -->

## Overzicht van verkeersbeveiliging {#traffic-protection-overview}

In het huidige digitale landschap is kwaadwillig verkeer een steeds grotere bedreiging. Wij erkennen de ernst van het risico en bieden verscheidene benaderingen aan om klantentoepassingen te beschermen en aanvallen te verlichten wanneer zij voorkomen.

Bij de rand, absorbeert de Adobe Beheerde CDN aanvallen DDoS bij de netwerklaag (lagen 3 en 4), met inbegrip van vloed en bezinning/versterkingsaanvallen.

Door gebrek, neemt de Adobe maatregelen om prestatiesverslechtering te verhinderen toe te schrijven aan barsten van onverwacht hoog verkeer boven een bepaalde drempel. In het geval van een aanval DDoS die plaatsbeschikbaarheid beïnvloeden, worden de verrichtingenteams van de Adobe gealarmeerd en nemen stappen om te verlichten.

De klanten kunnen pro-actieve maatregelen nemen om de aanvallen van de toepassingslaag (laag 7) te verlichten door regels bij diverse lagen van de stroom van de inhoudslevering te vormen.

Op de Apache-laag kunnen klanten bijvoorbeeld de [verzendingsmodule](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#configuring-access-to-content-filter) of [ModSecurity](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection.html?lang=en) om de toegang tot bepaalde inhoud te beperken.

En aangezien dit artikel beschrijft, kunnen de regels van de verkeersfilter aan CDN worden opgesteld, gebruikend de configuratiepijpleiding van de Manager van de Wolk. Naast op verzoek-Gebaseerde verkeersfilterregels die op eigenschappen zoals IP adres, weg, en kopballen worden gebaseerd, kunnen de klanten een krachtige subcategorie van de regels van de verkeersfilter ook vergunning geven genoemd de regels van WAF.

## Voorgesteld proces {#suggested-process}

Het volgende is een geadviseerd proces op hoog niveau van begin tot eind voor het komen met de juiste regels van de verkeersfilter:

1. Een niet-productie- en productieconfiguratiepijplijn configureren, zoals beschreven in de [Instellen](#setup) sectie.
1. Klanten die een licentie voor de subcategorie WAF-regels voor verkeersfilters hebben, dienen deze in te schakelen in Cloud Manager.
1. Lees en probeer uit het leerprogramma om concreet te begrijpen hoe te om de regels van de verkeersfilter, met inbegrip van de regels van WAF te gebruiken als zij vergunning hebben gekregen. Het leerprogramma begeleidt u door het opstellen van regels aan een dev milieu, simulerend kwaadwillig verkeer, downloadend [CDN-logbestanden](#cdn-logs)en deze in [dashboardgereedschap](#dashboard-tooling).
1. De aanbevolen initiële regels kopiëren naar `cdn.yaml` en stel de configuratie aan productie op logboekwijze op.
1. Na het verzamelen van wat verkeer, analyseer de resultaten gebruikend [dashboardgereedschap](#dashboard-tooling) om na te gaan of er wedstrijden zijn. Zoek naar vals positieven, en maak om het even welke noodzakelijke aanpassingen, uiteindelijk toelatend de standaardregels op blokwijze.
1. Voeg douaneregels toe die op analyse van de logboeken CDN worden gebaseerd, eerst het testen met gesimuleerd verkeer op ontwikkelomgevingen, alvorens aan stadium en productie op logboekwijze, dan blokwijze op te stellen.
1. Het verkeer van de controle op een voortdurende basis, die veranderingen in de regels aanbrengen aangezien het bedreigingslandschap evolueert.

## Instellen {#setup}

1. Maak eerst de volgende map en bestandsstructuur in de map op hoofdniveau in uw project in Git:

   ```
   config/
        cdn.yaml
   ```

1. `cdn.yaml` moeten metagegevens en een lijst met verkeersfilterregels en WAF-regels bevatten.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
       # Block simple path
       - name: block-path
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/block/me'
         action: block
   ```

De `kind` parameter moet worden ingesteld op `CDN` en de versie moet worden ingesteld op de schemaversie die momenteel is `1`. Zie onderstaande voorbeelden.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Om de regels van WAF te vormen, moet WAF in de Manager van de Wolk worden toegelaten, zoals hieronder voor zowel de nieuwe als bestaande programmascenario&#39;s wordt beschreven. Voor WAF moet een aparte vergunning worden aangeschaft.

   1. Om WAF op een nieuw programma te vormen, controleer **WAF-DDOS-beveiliging** selectievakje op de **Beveiliging** als u [een productieprogramma toevoegen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

   1. WAF op een bestaand programma vormen, [uw programma bewerken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) en op de **Beveiliging** of controleer de **WAF-DDOS** op elk gewenst moment.

1. Voor milieutypes buiten RDE, creeer een gerichte plaatsing config pijpleiding in de Manager van de Wolk.

   * [Zie dit document voor productiepijpleidingen.](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Zie dit document voor niet-productiepijpleidingen.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

Voor RDEs, zal de bevellijn worden gebruikt, maar RDE wordt niet gesteund op dit ogenblik.

## Syntaxis verkeersfilterregels {#rules-syntax}

U kunt `traffic filter rules` om op patronen zoals IPs, gebruikersagent, verzoekkopballen, hostname, geo, en url aan te passen.

Klanten die een licentie verlenen voor het aanbod Uitgebreide beveiliging of WAF-DDoS-beveiliging, kunnen ook een speciale categorie regels voor het filter configureren, genaamd `WAF traffic filter rules` (of WAF-regels voor kort) die verwijzen naar een of meer [WAF-vlaggen](#waf-flags-list).

Hier is een voorbeeld van een reeks regels van de verkeersfilter, die ook een regel van WAF omvat.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
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

Het formaat van de regels van de verkeersfilter in `cdn.yaml` wordt hieronder beschreven. Zie sommige [andere voorbeelden](#examples) in een later gedeelte, alsmede in een apart gedeelte over [Regels voor tarieflimieten](#rate-limit-rules).


| **Eigenschap** | **De meeste regels van de verkeersfilter** | **Regels voor WAF-verkeersfilters** | **Type** | **Standaardwaarde** | **Beschrijving** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelnaam (64 tekens lang, alleen alfanumerieke tekens en -) |
| wanneer | X | X | `Condition` | - | De basisstructuur is:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[Zie Syntaxis van Condition Structure](#condition-structure) Hieronder vindt u een beschrijving van de getters, voorspellingen en hoe u meerdere voorwaarden kunt combineren. |
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
| reqCookie | `string` | Retourneert cookie met opgegeven naam |
| postParam | `string` | Retourneert parameter met de opgegeven naam van de hoofdtekst. Alleen werken als de hoofdtekst van het inhoudstype is `application/x-www-form-urlencoded` |

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
| **exists** | `boolean` | true wanneer ingesteld op true en eigenschap bestaat of wanneer ingesteld op false en eigenschap niet bestaat |

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

De `wafFlags` eigenschap, die kan worden gebruikt in de licentiebare WAF-regels voor verkeersfilters, kan verwijzen naar het volgende:

| **Markering-id** | **Vlagnaam** | **Beschrijving** |
|---|---|---|
| SQLI | SQL-injectie | SQL de Injectie is de poging om toegang tot een toepassing te verkrijgen of bevoorrechte informatie te verkrijgen door willekeurige gegevensbestandvragen uit te voeren. |
| BACKEUR | Achterkant | Een achterdeursignaal is een verzoek dat probeert te bepalen als een gemeenschappelijk achterdeurdossier op het systeem aanwezig is. |
| CMDEXE | Opdracht uitvoeren | De Uitvoering van het bevel is de poging om controle te verkrijgen of een doelsysteem door willekeurige systeembevelen door middel van gebruikersinput te beschadigen. |
| XSS | Scripts voor meerdere sites | Met scripts die verwijzen naar andere sites wordt geprobeerd een gebruikersaccount of een webbrowsersessie te kapen via kwaadaardige JavaScript-code. |
| TRAVERSAL | Directorytraversal | Directorytraversal is de poging om bevoorrechte omslagen door een systeem in hoop te navigeren om gevoelige informatie te verkrijgen. |
| GEBRUIKER | Gereedschap Bijsluiten | De Tooling van de aanval is het gebruik van geautomatiseerde software om veiligheidskwetsbaarheid te identificeren of te proberen om een ontdekte kwetsbaarheid te exploiteren. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI-aanvallen proberen de [Log4Shell-kwetsbaarheid](https://en.wikipedia.org/wiki/Log4Shell) aanwezig in eerdere versies van Log4J dan 2.16.0 |
| BHH | Onjuiste koppen | De slechte Kopballen van de Hop wijzen op een HTTP het smokkelen poging door of een misvormde overdracht-Codering (TE) of een inhoud-Lengte (CL) kopbal, of een goed gevormde TE en kopbal CL |
| ABNORMALPATH | Abnormaal pad | Met Abnormal Path wordt aangegeven dat het oorspronkelijke pad afwijkt van het genormaliseerde pad (bijvoorbeeld `/foo/./bar` is genormaliseerd naar `/foo/bar`) |
| DOUBLEENCODERING | Dubbele codering | De dubbele Codering controleert de ontduikingstechniek van het tweemaal coderen van HTML- karakters |
| NOTUTF8 | Ongeldige codering | Ongeldige codering kan ertoe leiden dat de server schadelijke tekens van een verzoek in een reactie omzet, wat of een ontkenning van de dienst of XSS veroorzaakt |
| JSON-ERROR | JSON-coderingsfout | Een POST, PUT, of PATCH- verzoeklichaam dat als bevattende JSON binnen de &quot;Content-Type&quot;verzoekkopbal wordt gespecificeerd maar JSON het ontleden fouten bevat. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |
| MALFORMED-DATA | Onjuiste gegevens in de aanvraaginstantie | Een POST, een PUT, of PATCH verzoeken lichaam dat volgens de &quot;Inhoud-Type&quot;verzoekkopbal misvormd is. Bijvoorbeeld, als een &quot;Content-Type: application/x-www-form-urlencoded&quot;verzoekkopbal wordt gespecificeerd en een POST bevat die json is. Dit is vaak een programmeerfout, een geautomatiseerd of een kwaadwillig verzoek. Vereist agent 3.2 of hoger. |
| SANS | Verkeer van kwaadwillige IP | [SANS Internet Storm Center](https://isc.sans.edu/) lijst van IP adressen die om aan kwaadwillige activiteit zijn gemeld te hebben betrokken |
| SIGSCI-IP | Netwerkeffect | IP die door SignalSciences wordt gemarkeerd: Wanneer IP wegens een kwaadwillig signaal door de besluitvormingsmotor wordt gemarkeerd, zal dat IP aan alle klanten worden verspreid. De verdere verzoeken van die IP adressen die om het even welk extra signaal voor de duur van de vlag bevatten worden dan geregistreerd |
| NO-CONTENT-TYPE | Ontbrekende aanvraagheader &quot;Content-Type&quot; | Een POST-, PUT- of PATCH-aanvraag die geen aanvraagheader &quot;Content-Type&quot; heeft. Standaard moeten toepassingsservers in dit geval &#39;Content-Type: text/plain; charset=us-ascii&#39; aannemen. Bij veel geautomatiseerde en kwaadaardige verzoeken ontbreekt mogelijk het type inhoud. |
| NOUA | Geen gebruikersagent | Vele geautomatiseerde en kwaadwillige verzoeken gebruiken vals of ontbrekende Gebruiker-Agenten om het moeilijk te maken om het type van apparaat te identificeren dat de verzoeken maakt. |
| TORNODE | Teerverkeer | Tor is software die de identiteit van een gebruiker verbergt. Een piek in het verkeer van de Tor kan op een aanvaller wijzen die probeert om hun plaats te maskeren. |
| NULLBYTE | Null Byte | Null-bytes worden normaal gesproken niet weergegeven in een verzoek en geven aan dat het verzoek onjuist is geformuleerd en mogelijk kwaadaardig is. |
| PRIVATEFIEL | Persoonlijke bestanden | Persoonlijke bestanden zijn doorgaans vertrouwelijk, zoals een Apache `.htaccess` bestand of een configuratiebestand dat vertrouwelijke informatie kan lekken |
| SCANNER | Scanner | Identificeert populaire scanservices en -gereedschappen |
| RESPONSESPLIT | HTTP-antwoordsplitsing | Identificeert wanneer CRLF-tekens als invoer naar de toepassing worden verzonden om headers in de HTTP-reactie te injecteren |
| XML-ERROR | XML-coderingsfout | Een POST, PUT, of PATCH aanvraaglichaam dat als bevattende XML binnen de &quot;Inhoud-Type&quot;verzoekkopbal wordt gespecificeerd maar XML het ontleden fouten bevat. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |

## Overwegingen {#considerations}

* Wanneer twee conflicterende regels worden gecreeerd, zullen de allow regels altijd belangrijkheid over de blokregels nemen. Bijvoorbeeld, als u een regel creeert om een specifieke weg en een regel te blokkeren om één specifiek IP adres toe te staan, zullen de verzoeken van dat IP adres op de geblokkeerde weg worden toegestaan.

* Als een regel wordt aangepast en geblokkeerd, reageert CDN met een `406` retourcode.

* De configuratiedossiers zouden geen geheimen moeten bevatten aangezien zij door iedereen leesbaar zouden zijn die toegang tot de git bewaarplaats heeft.

## Voorbeelden van regels {#examples}

Hier volgen enkele regelvoorbeelden. Zie de [tarieflimiteringssectie](#rules-with-rate-limits) verder voor voorbeelden van tarieflimietregels.

**Voorbeeld 1**

Deze regel blokkeert verzoeken die van IP 192.168.1.1 komen:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
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
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
        when:
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
metadata:
  envTypes: ["dev"]
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

Deze regel blokkeert aanvragen om paden `/block-me`en blokkeert elke aanvraag die overeenkomt met een `SQLI` of `XSS` patroon. Dit voorbeeld omvat een het verkeersfilterregels van WAF, die verwijzingen `SQLI` en `XSS` [WAF-vlaggen](#waf-flags-list), waarvoor een aparte vergunning vereist is.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
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

**Voorbeeld 5**

Deze regel blokkeert de toegang tot OFAC-landen:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - reqProperty: tier
              matches: "author|publish"
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

## Regels voor tarieflimieten {#rate-limits-rules}

Soms is het wenselijk om verkeer te blokkeren die een regel aanpassen slechts als de gelijke een bepaald tarief in tijd overschrijdt. Een waarde instellen voor de `rateLimit` eigenschap beperkt de snelheid van die aanvragen die overeenkomen met de regelvoorwaarde.

Regels voor tarieflimieten kunnen niet verwijzen naar WAF-vlaggen. Ze zijn beschikbaar voor alle klanten van Sites en Forms.

### rateLimit-structuur {#ratelimit-structure}

| **Eigenschap** | **Type** | **Standaard** | **BETEKENEN** |
|---|---|---|---|
| limiet | geheel getal van 10 tot en met 10000 | vereist | Het tarief van het verzoek (per CDN POP) in verzoeken per seconde waarvoor de regel wordt teweeggebracht. |
| venster | geheel getal: 1, 10 of 60 | 10 | Samplingvenster in seconden waarvoor de aanvraagsnelheid wordt berekend. |
| straf | geheel getal van 60 tot 3600 | 300 | Een periode in seconden waarvoor overeenkomstige verzoeken worden geblokkeerd (afgerond naar de dichtstbijzijnde minuut). |
| groupBy | array[Getter] | none | De teller van de snelheidsbegrenzer zal door een reeks verzoekeigenschappen (bijvoorbeeld clientIp) worden bijeengevoegd. |

### Voorbeelden {#ratelimiting-examples}

**Voorbeeld 1**

Deze regel blokkeert een cliënt voor 5m wanneer het 100 req/sec (per CDN POP) in de laatste 60 sec overschrijdt:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Voorbeeld 2**

De verzoeken van het blok voor 60s op weg /kritiek/middel wanneer het 100 req/sec (per CDN POP) in de laatste 60 sec overschrijdt:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
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

CDN-logbestanden kunnen maximaal 5 minuten worden vertraagd.

De `rules` De eigenschap beschrijft welke regels voor verkeersfilters worden aangepast en heeft het volgende patroon:

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Bijvoorbeeld:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

De regels gedragen zich als volgt:

* De klant-verklaarde regelnaam van om het even welke passende regels zal in de gelijkenattributen worden vermeld.
* Het actiekenmerk bepaalt of de regels het effect van het blokkeren, toestaan of registreren hadden.
* Als WAF vergunning en toegelaten is, zal het wafattribuut van om het even welke golfregels (b.v., SQLI een lijst maken; merk op dat dit van de klant-verklaarde naam) onafhankelijk is die werden ontdekt, ongeacht of de waf regels in de configuratie werden vermeld.
* Als geen klant-verklaarde regels aanpassen en geen golfregels aanpassen, zal het bezit van regelattributen leeg zijn.

In het algemeen, verschijnen de passende regels in de logboekingang voor alle verzoeken aan CDN, ongeacht of het een CDN hit, pas, of mis is. Nochtans, verschijnen de regels van WAF in de logboekingang slechts voor verzoeken aan CDN die als CDN missen of overgaan, maar niet CDN- klappen worden beschouwd.

In het onderstaande voorbeeld ziet u een voorbeeld `cdn.yaml` en twee CDN-logitems:


```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
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
| *tijdstempel* | De tijd waarop de aanvraag is gestart, na beëindiging van TLS. |
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

## Dashboard Tooling {#dashboard-tooling}

Adobe biedt een mechanisme voor het downloaden van dashboardgereedschappen naar uw computer voor het invoeren van CDN-logbestanden die zijn gedownload via Cloud Manager. Met dit tooling, kunt u uw verkeer analyseren om omhoog met de aangewezen regels van de verkeersfilter te komen om te verklaren, met inbegrip van de regels van WAF.

Gereedschap Dashboard kan rechtstreeks worden gekloond vanuit het dialoogvenster [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) Github repository.

[Zie de zelfstudie](#tutorial) voor concrete instructies over het gebruik van de dashboardgereedschappen.

## Zelfstudie {#tutorial}

Adobe biedt een mechanisme voor het downloaden van dashboardgereedschappen naar uw computer voor het invoeren van CDN-logbestanden die zijn gedownload via Cloud Manager. Met dit tooling, kunt u uw verkeer analyseren om omhoog met de aangewezen regels van de verkeersfilter te komen om te verklaren, met inbegrip van de regels van WAF. In deze sectie worden eerst enkele instructies gegeven om vertrouwd te raken met het dashboard-gereedschap in een ontwikkelomgeving, gevolgd door richtlijnen over hoe u die kennis kunt gebruiken om regels voor een testomgeving te maken.

Gereedschap Dashboard kan rechtstreeks worden gekloond vanuit het dialoogvenster [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) GitHub-opslagplaats.


### Kennis krijgen van de dashboardgereedschappen {#dashboard-getting-familiar}

1. Creeer een pijpleiding van de niet-productieconfiguratie van de Manager van de Wolk, verbonden aan een ontwikkelomgeving. Selecteer eerst de optie **Implementatiepijp** -optie. Selecteer vervolgens **Gerichte implementatie**, Config, uw bewaarplaats, de git tak, en plaats de codeplaats aan /config.

   ![Niet-productiepijpleiding toevoegen selecteert plaatsing](/help/security/assets/waf-select-pipeline1.png)

   ![Niet-productiepijplijn toevoegen, selecteer doel](/help/security/assets/waf-select-pipeline2.png)

[Zie dit document voor meer informatie over het opzetten van niet-productiepijpleidingen.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

1. In uw werkruimte, creeer een omslag config op het wortelniveau en voeg een dossier toe genoemd `cdn.yaml`, waar u een eenvoudige regel zult verklaren, plaatsend het op logboekwijze eerder dan op het blokkeren wijze.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    # Log request on simple path
    - name: log-rule-example
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            equals: '/log/me'
      action: log
```

1. Leg uw veranderingen vast en duw, en stel uw configuratie op gebruikend de configuratiepijplijn.

   ![Configuratiepijplijn uitvoeren](/help/security/assets/waf-run-pipeline.png)

1. Zodra uw configuratie is opgesteld, probeer om tot toegang te hebben `https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me` met behulp van uw webbrowser of met de onderstaande curl-opdracht. U moet een 404-foutpagina krijgen omdat die pagina niet bestaat.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Download de CDN-logboeken van Cloud Manager en bevestig dat de regels overeenkomen met de verwachte waarden, met een regeleigenschap die overeenkomt met de regelnaam:

   ```
   "rules": "match=log-rule-example"
   ```

   ![Logbestanden downloaden selecteren](/help/security/assets/waf-download-logs1.png)

   ![Logbestanden downloaden](/help/security/assets/waf-download-logs2.png)

1. Laad de Docker-afbeelding met het dashboard-gereedschap en volg de README om de CDN-logboeken in te voeren. Zoals in de volgende schermafbeeldingen wordt getoond, selecteer de juiste tijdsperiode, de juiste omgeving, en de juiste filters.

   ![Tijd selecteren vanuit dashboard](/help/security/assets/dashboard-select-time.png)

   ![Omgeving van dashboard selecteren](/help/security/assets/dashboard-select-env.png)

1. Nadat de juiste filters zijn toegepast, ziet u een dashboard dat met de verwachte gegevens is geladen. In het schermafbeelding hieronder, is het regel log-rule-example 3 keer geactiveerd in de laatste 2 uren, door zelfde IP die in Ierland wordt gevestigd, gebruikend Webbrowser en krullen.

   ![Gegevens van het ontwikkeldashboard weergeven](/help/security/assets/dashboard-see-data-logmode.png)
   ![Widgets dev-dashboardgegevens weergeven](/help/security/assets/dashboard-see-data-logmode2.png)

1. Wijzig nu cdn.yaml om de regel in blokmodus te zetten, zodat de pagina&#39;s worden geblokkeerd, zoals u had verwacht. Dan begaat, duw en teweegbrengt de configuratiepijplijn zoals vroeger gedaan.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    # Log request on simple path
    - name: log-rule-example
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            equals: '/log/me'
      action: block
```

1. Zodra uw configuratie is opgesteld, probeer om tot toegang te hebben `https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me` met behulp van uw webbrowser of met de onderstaande curl-opdracht. Er moet een pagina met 406 fouten worden weergegeven om aan te geven dat het verzoek is geblokkeerd.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Download opnieuw uw CDN-logbestanden in Cloud Manager (Opmerking: het kan tot 5 minuten duren voordat de nieuwe aanvragen in uw CDN-logbestanden worden weergegeven) en importeer ze in de dashboardwerkset, zoals we dat eerder deden. Vernieuw het dashboard als het gereed is. Zoals u kunt zien in de onderstaande schermafbeelding, kunt u verzoeken om `/log/me` worden geblokkeerd door onze regels.

   ![Gegevens in het dashboard van een pod weergeven](/help/security/assets/dashboard-see-data-blockmode.png)
   ![Gegevens in het dashboard van een pod weergeven](/help/security/assets/dashboard-see-data-blockmode2.png)

1. Als u WAF verkeersfilters hebt toegelaten (dit zal een extra vergunning vereisen nadat de eigenschap GA is), herhaal met een regel van de het verkeersfilter van WAF, op logboekwijze, en stel de regels op.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: log-waf-flags
        when:
          reqProperty: tier
          matches: "author|publish"
        action:
          type: log
          wafFlags:
              - SANS
              - SIGSCI-IP
              - TORNODE
              - NOUA
              - SCANNER
              - USERAGENT
              - PRIVATEFILE
              - ABNORMALPATH
              - TRAVERSAL
              - NULLBYTE
              - BACKDOOR
              - LOG4J-JNDI
              - SQLI
              - XSS
              - CODEINJECTION
              - CMDEXE
              - NO-CONTENT-TYPE
              - UTF8
```

1. Een gereedschap gebruiken als [nikto](https://github.com/sullo/nikto/tree/master) om overeenkomstige verzoeken te produceren. Met de onderstaande opdracht worden ongeveer 550 kwaadaardige verzoeken binnen 1 minuut verzonden.

   ```
   ./nikto.pl -useragent "MyAgent (Demo/1.0)" -D V -Tuning 9 -ssl -h https://publish-pXXXXX-eYYYYY.adobeaemcloud.com
   ```

1. Download de CDN-logbestanden van Cloud Manager (houd er rekening mee dat het maximaal 5 minuten kan duren om te worden weergegeven) en controleer of zowel de overeenkomende gedeclareerde regels als de WAF-markeringen worden weergegeven.

   Zoals u kunt zien, worden verschillende verzoeken van Nikto door de WAF gemarkeerd als kwaadaardig. We kunnen zien dat Nikto heeft geprobeerd CMDEXE, SQLI en NULLBYTE te misbruiken. Als u nu de handeling wijzigt van log naar block en re-trigger voor een scan met Nikto, worden alle aanvragen die eerder waren gemarkeerd deze keer geblokkeerd.

   ![WAF-gegevens weergeven](/help/security/assets/dashboard-see-data-waf.png)


   Merk op dat wanneer een verzoek om om het even welke vlaggen van WAF aanpast, die vlaggen van WAF zullen verschijnen, zelfs als geen deel van de verklaarde regel; dit is zodat bent u altijd bewust van potentieel nieuw kwaadwillig verkeer, waarvoor u nog geen passende regels hebt verklaard. Als voorbeeld:

   ```
   "rules": "match=log-waf-flags,waf=SQLI,action=blocked"
   ```

1. Herhaal deze bewerking met een regel waarbij snelheidsbeperking wordt gebruikt in de logmodus. Zoals altijd, begaat, duw en brengt de configuratiepijplijn teweeg om uw configuratie toe te passen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: limit-requests-client-ip
        when:
          reqProperty: tier
          matches: "author|publish"
        rateLimit:
          limit: 10
          window: 1
          penalty: 60
          groupBy:
            - reqProperty: clientIp
        action: log
```

1. Een gereedschap gebruiken als [Vegeta](https://github.com/tsenart/vegeta) om verkeer te produceren.

   ```
   echo "GET https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com" | vegeta attack -duration=5s | tee results.bin | vegeta report
   ```

1. Nadat u het gereedschap hebt uitgevoerd, kunt u CDN-logboeken downloaden en deze in het dashboard invoeren om te controleren of de regel voor snelheidsbegrenzer is geactiveerd

   ![WAF-gegevens weergeven](/help/security/assets/waf-dashboard-ratelimiter-1.png)

   ![WAF-gegevens weergeven](/help/security/assets/waf-dashboard-ratelimiter-2.png)

   Zoals je onze regel ziet **limit-request-client-ip** is geactiveerd.

   Nu u vertrouwd bent met hoe de regels van de verkeersfilter werken, kunt u zich op het prodmilieu bewegen.

### Regels implementeren in de profielomgeving {#dashboard-prod-env}

Zorg ervoor om regels op logboekwijze aanvankelijk te verklaren om te bevestigen dat er geen valse positieven zijn, wat wettig verkeer betekent dat verkeerd zou worden geblokkeerd.

1. Creeer een pijpleiding van de productieconfiguratie verbonden aan uw productiemilieu.

1. Kopieer de aanbevolen regels hieronder naar cdn.yaml. Mogelijk wilt u de regels wijzigen op basis van de unieke kenmerken van het live verkeer van uw website. Leg uw configuratiepijplijn vast, duw en activeer deze. Zorg ervoor dat de regels in de logmodus staan.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds 100 req/sec on a time window of 1sec
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 100
        window: 1
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    # Block requests coming from OFAC countries
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
      action: log
    # Enable recommended WAF protections (only works if WAF is enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        matches: "author|publish"
      action:
        type: log
        wafFlags:
          - SANS
          - SIGSCI-IP
          - TORNODE
          - NOUA
          - SCANNER
          - USERAGENT
          - PRIVATEFILE
          - ABNORMALPATH
          - TRAVERSAL
          - NULLBYTE
          - BACKDOOR
          - LOG4J-JNDI
          - SQLI
          - XSS
          - CODEINJECTION
          - CMDEXE
          - NO-CONTENT-TYPE
          - UTF8
    # Disable protection against CMDEXE on /bin
    - name: allow-cdmexe-on-root-bin
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            matches: "^/bin/.*"
      action:
        type: log
        wafFlags:
          - CMDEXE
```

1. Voeg om het even welke extra regels toe om kwaadwillig verkeer te blokkeren dat u zich van bewust kunt zijn. Bijvoorbeeld, bepaalde IPs die uw plaats hebben aangevallen.

1. Na een paar minuten, uren of dagen, afhankelijk van het verkeersvolume van uw site, downloadt u CDN-logbestanden van Cloud Manager en analyseert u deze met het dashboard.

1. Hier volgen enkele overwegingen:
   1. Verkeersovereenkomsten tussen gedeclareerde regels worden weergegeven in grafieken en aanvraaglogboeken, zodat u eenvoudig kunt controleren of de gedeclareerde regels worden geactiveerd.
   1. De de passende vlaggen van WAF van het verkeer verschijnen in grafieken en verzoeklogboeken, zelfs als u hen niet in een regel registreerde. Dit is zodat bent u zich altijd bewust van potentieel nieuw kwaadwillig verkeer en kan nieuwe regels tot stand brengen zoals nodig. Bekijk de vlaggen van WAF die niet in de verklaarde regels worden weerspiegeld en denk na verklarend hen.
   1. Voor passende regels, inspecteer de verzoeklogboeken valse positieven en zie of kunt u hen uit de regels filtreren. Misschien zijn ze bijvoorbeeld alleen voor bepaalde paden onwaar positief.

1. Plaats de aangewezen regels aan blokwijze en denk ook na toevoegend extra regels. Misschien zouden sommige regels op logboekwijze moeten blijven aangezien u verder met meer verkeer analyseert.

1. Implementeer de configuratie opnieuw.

1. Herhaal dit, waarbij de dashboards regelmatig worden geanalyseerd.

