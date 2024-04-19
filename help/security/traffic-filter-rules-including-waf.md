---
title: Verkeersfilterregels inclusief WAF-regels
description: Het vormen de Regels van de Filter van het Verkeer met inbegrip van de Regels van de Firewall van de Toepassing van het Web (WAF)
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: d210fed56667b307a7a816fcc4e52781dc3a792d
workflow-type: tm+mt
source-wordcount: '3788'
ht-degree: 0%

---


# Regels voor verkeersfilters, inclusief WAF-regels {#traffic-filter-rules-including-waf-rules}

De filterregels van het verkeer kunnen worden gebruikt om verzoeken bij de laag te blokkeren of toe te staan CDN, die in scenario&#39;s zoals nuttig kan zijn:

* Toegang tot specifieke domeinen beperken tot intern bedrijfsverkeer, voordat een nieuwe site live gaat
* Vaststelling van tariefgrenzen zodat minder vatbaar voor volumetrische aanvallen van Dos zijn
* Voorkomen dat IP-adressen waarvan bekend is dat ze kwaadaardig zijn, zich richten op uw pagina&#39;s

De meeste van deze regels van de verkeersfilter zijn beschikbaar aan alle AEM as a Cloud Service Plaatsen en klanten van Forms. Zij werken hoofdzakelijk op verzoekeigenschappen en verzoekkopballen, met inbegrip van IP, hostname, weg, en gebruikersagent.

Een subcategorie van de regels van het verkeersfilter vereist of een vergunning van de Beveiliging van Uitgebreide Veiligheid of van de Bescherming WAF-DDoS. Deze krachtige regels zijn gekend als het verkeersfilterregels van het WAF (de Firewall van de Toepassing van het Web) (of de regels van WAF voor kort) en hebben toegang tot [WAF-vlaggen](#waf-flags-list) wordt verderop in dit artikel beschreven.

De filterregels van het verkeer kunnen via de configuratiepijpleidingen van de Manager van de Wolk worden opgesteld om, stadium, en de types van productiemilieu in productie (niet zandbak) programma&#39;s te ontwikkelen. Steun voor RDEs zal in de toekomst komen.

[Een zelfstudie doorlopen](#tutorial) snel concrete expertise op dit gebied op te bouwen.

>[!NOTE]
>Geïnteresseerd in andere opties om verkeer bij CDN te vormen, met inbegrip van het wijzigen van het verzoek/de reactie, het verklaren van omleiding, en het proxying aan een niet-AEM oorsprong? [Meer informatie en probeer het uit](/help/implementing/dispatcher/cdn-configuring-traffic.md) door zich aan te sluiten bij het programma voor vroegtijdige adoptie .


## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is onderverdeeld in de volgende secties:

* **Overzicht verkeersbeveiliging:** Leer hoe u tegen kwaadwillig verkeer wordt beschermd.
* **Voorgesteld proces voor het configureren van regels:** Lees meer over een methode op hoog niveau voor het beschermen van uw website.
* **Instellen:** Ontdek hoe te opstelling, vorm, en stel de regels van de verkeersfilter, met inbegrip van de geavanceerde regels van WAF op.
* **Syntaxis regels:** Lees over hoe te om de regels van de verkeersfilter in te verklaren `cdn.yaml` configuratiebestand. Dit omvat zowel de regels van de verkeersfilter beschikbaar aan alle klanten van Plaatsen en van Forms, als de subcategorie van de regels van WAF voor degenen die van dat vermogen vergunning geven.
* **Voorbeelden van regels:** Bekijk voorbeelden van gedeclareerde regels om u op weg te helpen.
* **Regels voor tarieflimieten:** Leer hoe u regels voor snelheidsbeperking gebruikt om uw site te beschermen tegen aanvallen met een hoog volume.
* **CDN-logbestanden:** Zie welke verklaarde regels en de Vlaggen van WAF uw verkeer aanpassen.
* **Dashboard-gereedschappen:** Analyseer uw CDN logboeken om nieuwe regels van de verkeersfilter omhoog te komen.
* **Aanbevolen starterregels:** Een set regels om mee aan de slag te gaan.
* **Zelfstudie:** Praktische kennis over de eigenschap, met inbegrip van hoe te om dashboardtooling te gebruiken om de juiste regels te verklaren.

We nodigen u uit feedback te geven of vragen te stellen over regels voor het filter van het verkeer via e-mail **aemcs-waf-adopter@adobe.com**.

## Overzicht van verkeersbeveiliging {#traffic-protection-overview}

In het huidige digitale landschap is kwaadwillig verkeer een steeds grotere bedreiging. Wij erkennen de ernst van het risico en bieden verscheidene benaderingen aan om klantentoepassingen te beschermen en aanvallen te verlichten wanneer zij voorkomen.

Bij de rand, absorbeert de Adobe Beheerde CDN de aanvallen van Dos bij de netwerklaag (lagen 3 en 4), met inbegrip van vloed en bezinning/versterkingsaanvallen.

Door gebrek, neemt de Adobe maatregelen om prestatiesverslechtering te verhinderen toe te schrijven aan barsten van onverwacht hoog verkeer boven een bepaalde drempel. In het geval van een aanval van Dos die plaatsbeschikbaarheid beïnvloeden, worden de verrichtingenteams van de Adobe gealarmeerd en nemen stappen om te verlichten.

De klanten kunnen pro-actieve maatregelen nemen om de aanvallen van de toepassingslaag (laag 7) te verlichten door regels bij diverse lagen van de stroom van de inhoudslevering te vormen.

Op de Apache-laag kunnen klanten bijvoorbeeld de [verzendingsmodule](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter) of [ModSecurity](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection.html) om de toegang tot bepaalde inhoud te beperken.

En aangezien dit artikel beschrijft, kunnen de regels van de verkeersfilter aan de Adobe Geleide CDN worden opgesteld, gebruikend de configuratiepijplijn van de Manager van de Wolk. Naast de regels van de verkeersfilter die op eigenschappen zoals IP adres, weg, en kopballen, of regels worden gebaseerd die op het plaatsen van tariefgrenzen worden gebaseerd, kunnen de klanten een krachtige subcategorie van de regels van de verkeersfilter ook vergunning geven genoemd de regels van WAF.

## Voorgesteld proces {#suggested-process}

Het volgende is een geadviseerd proces op hoog niveau van begin tot eind voor het komen met de juiste regels van de verkeersfilter:

1. Niet-productie- en productieconfiguratiepijpleidingen configureren, zoals beschreven in de [Instellen](#setup) sectie.
1. Klanten die een licentie voor de subcategorie WAF-regels voor verkeersfilters hebben, dienen deze in te schakelen in Cloud Manager.
1. Lees en probeer uit het leerprogramma om concreet te begrijpen hoe te om de regels van de verkeersfilter, met inbegrip van de regels van WAF te gebruiken als zij vergunning hebben gekregen. Het leerprogramma begeleidt u door het opstellen van regels aan een dev milieu, simulerend kwaadwillig verkeer, downloadend [CDN-logbestanden](#cdn-logs)en deze in [dashboardgereedschap](#dashboard-tooling).
1. De aanbevolen startregels kopiëren naar `cdn.yaml` en stel de configuratie aan het productiemilieu op logboekwijze op.
1. Na het verzamelen van wat verkeer, analyseer de resultaten gebruikend [dashboardgereedschap](#dashboard-tooling) om na te gaan of er wedstrijden zijn. Lookout voor valse positieven, en maak om het even welke noodzakelijke aanpassingen, uiteindelijk toelatend de starterregels op blokwijze.
1. Voeg douaneregels toe die op analyse van de logboeken CDN worden gebaseerd, eerst het testen met gesimuleerd verkeer op ontwikkelmilieu&#39;s alvorens aan stadium en productiemilieu&#39;s op logboekwijze, dan blokwijze op te stellen.
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


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (for example, "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Als voor WAF-regels een licentie wordt verleend, moet u de functie inschakelen in Cloud Manager, zoals hieronder wordt beschreven voor zowel de nieuwe als de bestaande programmascenario&#39;s.

   1. Om WAF op een nieuw programma te vormen, controleer **WAF-DDOS-beveiliging** selectievakje op de **Beveiliging** als u [een productieprogramma toevoegen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

   1. WAF op een bestaand programma vormen, [uw programma bewerken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) en op de **Beveiliging** of controleer de **WAF-DDOS** op elk gewenst moment.

1. Voor milieutypes buiten RDE, creeer een gerichte plaatsing config pijpleiding in de Manager van de Wolk.

   * [Zie productiepijpleidingen configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).
   * [Zie niet-productiepijpleidingen configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

Voor RDEs, zal de bevellijn worden gebruikt, maar RDE wordt niet gesteund op dit ogenblik.

**Notities**

* U kunt `yq` om de opmaak van uw configuratiebestand lokaal te valideren (bijvoorbeeld `yq cdn.yaml`).

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

Het formaat van de regels van de verkeersfilter in `cdn.yaml` wordt hieronder beschreven. Zie sommige [andere voorbeelden](#examples) in een latere sectie en een afzonderlijke sectie over [Regels voor tarieflimieten](#rate-limit-rules).


| **Eigenschap** | **De meeste regels van de verkeersfilter** | **Regels voor WAF-verkeersfilters** | **Type** | **Standaardwaarde** | **Beschrijving** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelnaam (64 tekens lang, alleen alfanumerieke tekens en -) |
| wanneer | X | X | `Condition` | - | De basisstructuur is:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[Zie Syntaxis van Condition Structure](#condition-structure) Hieronder vindt u een beschrijving van de getters, voorspellingen en hoe u meerdere voorwaarden kunt combineren. |
| action | X | X | `Action` | log | log, allow, block of Action-object. Standaard is log |
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
| reqProperty | `string` | Request-eigenschap.<br><br>Een van:<br><ul><li>`path`: Retourneert het volledige pad van een URL zonder de queryparameters.</li><li>`queryString`: Retourneert het querygedeelte van een URL</li><li>`method`: Retourneert de HTTP-methode die in de aanvraag wordt gebruikt.</li><li>`tier`: Retourneert een van `author`, `preview` of `publish`.</li><li>`domain`: Hiermee wordt de eigenschap domain geretourneerd (zoals gedefinieerd in het dialoogvenster `Host` header) in kleine letters</li><li>`clientIp`: Retourneert de client-IP.</li><li>`clientCountry`: Retourneert een tweelettercode ([https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) die aangeven in welk land de cliënt zich bevindt.</li></ul> |
| reqHeader | `string` | Hiermee wordt aanvraagheader met de opgegeven naam geretourneerd |
| queryParam | `string` | Hiermee wordt de query-parameter met de opgegeven naam geretourneerd |
| reqCookie | `string` | Retourneert cookie met opgegeven naam |
| postParam | `string` | Keert de Parameter van het Post met gespecificeerde naam van het lichaam van het Verzoek terug. Werkt alleen als de hoofdtekst van het inhoudstype is `application/x-www-form-urlencoded` |

**Voorspelend**

| **Eigenschap** | **Type** | **Betekenis** |
|---|---|---|
| **equals** | `string` | true als het resultaat van de getter gelijk is aan de opgegeven waarde |
| **doesNotEqual** | `string` | true als het resultaat van de getter niet gelijk is aan de opgegeven waarde |
| **leuk** | `string` | true als het resultaat van de getter overeenkomt met het opgegeven patroon |
| **notlike** | `string` | true als het resultaat van de getter niet overeenkomt met het opgegeven patroon |
| **overeenkomsten** | `string` | true als het resultaat van de getter overeenkomt met opgegeven regex |
| **doesNotMatch** | `string` | true als het resultaat van de getter niet overeenkomt met opgegeven regex |
| **in** | `array[string]` | true als de opgegeven lijst het resultaat getter bevat |
| **notIn** | `array[string]` | true als de opgegeven lijst geen resultaat voor getter bevat |
| **exists** | `boolean` | true wanneer ingesteld op true en eigenschap bestaat of wanneer ingesteld op false en eigenschap niet bestaat |

**Notities**

* De eigenschap request `clientIp` kan alleen worden gebruikt met de volgende voorspelling: `equals`, `doesNotEqual`, `in`, `notIn`. `clientIp` kan ook tegen IP waaiers worden vergeleken wanneer het gebruiken `in` en `notIn` voorspelt. In het volgende voorbeeld wordt een voorwaarde geïmplementeerd om te beoordelen of een client-IP zich in het IP-bereik van 192.168.0.0/24 bevindt (dus van 192.168.0.0 tot 192.168.0.255):

```
when:
  reqProperty: clientIp
  in: [ "192.168.0.0/24" ]
```

* We raden het gebruik aan van [regex101](https://regex101.com/) en [Fastly Fiddle](https://fiddle.fastly.dev/) wanneer u met regex werkt. U kunt ook meer leren over hoe snel regex in dit [artikel](https://developer.fastly.com/reference/vcl/regex/#best-practices-and-common-mistakes).


### Handelingsstructuur {#action-structure}

An `action` Dit kan een tekenreeks zijn die de handeling opgeeft (toestaan, blokkeren of vastleggen), of een object dat bestaat uit zowel het handelingstype (toestaan, blokkeren of vastleggen) als opties zoals wafFlags en/of status.

**Typen handelingen**

De acties worden geprioriteerd volgens hun types in de volgende lijst, die wordt bevolen om op de ordeacties te wijzen wordt uitgevoerd:

| **Naam** | **Toegestane eigenschappen** | **Betekenis** |
|---|---|---|
| **toestaan** | `wafFlags` (facultatief), `alert` (optioneel, nog niet vrijgegeven) | als wafFlags niet aanwezig is, houdt verdere regelverwerking tegen en gaat aan het dienen van reactie te werk. Als wafFlags aanwezig is, maakt het gespecificeerde bescherming van WAF onbruikbaar en gaat aan verdere regelverwerking te werk. <br>Als het alarm wordt gespecificeerd, wordt een bericht van het Centrum van Acties verzonden als de regel 10 keer in een 5 minieme venster wordt teweeggebracht. Deze functie wordt nog niet vrijgegeven. Zie de [Waarschuwing verkeersfilterregels](#traffic-filter-rules-alerts) voor meer informatie over de deelname aan het programma voor vroegtijdige adoptie . |
| **blok** | `status, wafFlags` (facultatief en wederzijds exclusief), `alert` (optioneel, nog niet vrijgegeven) | als wafFlags niet aanwezig is, retourneert de HTTP-fout waarbij alle andere eigenschappen worden overgeslagen, wordt de foutcode gedefinieerd door de status-eigenschap of is de standaardwaarde 406. Als wafFlags aanwezig is, laat het gespecificeerde bescherming van WAF toe en gaat aan verdere regelverwerking te werk. <br>Als het alarm wordt gespecificeerd, wordt een bericht van het Centrum van Acties verzonden als de regel 10 keer in een 5 minieme venster wordt teweeggebracht. Deze functie wordt nog niet vrijgegeven. Zie de [Waarschuwing verkeersfilterregels](#traffic-filter-rules-alerts) voor meer informatie over de deelname aan het programma voor vroegtijdige adoptie . |
| **log** | `wafFlags` (facultatief), `alert` (optioneel, nog niet vrijgegeven) | registreert het feit dat de regel werd teweeggebracht, anders beïnvloedt niet de verwerking. wafFlags heeft geen effect. <br>Als het alarm wordt gespecificeerd, wordt een bericht van het Centrum van Acties verzonden als de regel 10 keer in een 5 minieme venster wordt teweeggebracht. Deze functie wordt nog niet vrijgegeven. Zie de [Waarschuwing verkeersfilterregels](#traffic-filter-rules-alerts) voor meer informatie over de deelname aan het programma voor vroegtijdige adoptie . |

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
| CODEINJECTIE | Code-injectie | De Injectie van de code is de poging om controle te verkrijgen of een doelsysteem door willekeurige bevelen van de toepassingscode door gebruikersinput te beschadigen. |
| ABNORMALPATH | Abnormaal pad | Met Abnormal Path wordt aangegeven dat het oorspronkelijke pad afwijkt van het genormaliseerde pad (bijvoorbeeld `/foo/./bar` is genormaliseerd naar `/foo/bar`) |
| DOUBLEENCODERING | Dubbele codering | De dubbele Codering controleert de ontduikingstechniek van het tweemaal coderen van HTML- karakters |
| NOTUTF8 | Ongeldige codering | Ongeldige codering kan ertoe leiden dat de server schadelijke tekens van een verzoek in een reactie omzet, wat of een ontkenning van de dienst of XSS veroorzaakt |
| JSON-ERROR | JSON-coderingsfout | Een POST, PUT, of PATCH- verzoeklichaam dat als bevattende JSON binnen de &quot;Content-Type&quot;verzoekkopbal wordt gespecificeerd maar JSON het ontleden fouten bevat. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |
| MALFORMED-DATA | Onjuiste gegevens in de aanvraaginstantie | Een POST, een PUT, of PATCH verzoeken lichaam dat volgens de &quot;Inhoud-Type&quot;verzoekkopbal misvormd is. Bijvoorbeeld, als een &quot;Content-Type: application/x-www-form-urlencoded&quot;verzoekkopbal wordt gespecificeerd en een POST bevat die json is. Dit is vaak een programmeerfout, een geautomatiseerd of een kwaadwillig verzoek. Vereist agent 3.2 of hoger. |
| SANS | Verkeer van kwaadwillige IP | [SANS Internet Storm Center](https://isc.sans.edu/) lijst van IP adressen die om aan kwaadwillige activiteit zijn gemeld te hebben betrokken |
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

* IP de Lijsten van gewenste personen die in de Manager van de Wolk worden bepaald hebben belangrijkheid over de Regels van de Filters van het Verkeer.

* De de regelovereenkomsten van WAF verschijnen slechts in CDN- logboeken voor CDN mist en passen, niet klappen.

## Voorbeelden van regels {#examples}

Hier volgen enkele regelvoorbeelden. Zie de [tarieflimiteringssectie](#rules-with-rate-limits) verder voor voorbeelden van tarieflimietregels.

**Voorbeeld 1**

Deze regel blokkeert aanvragen afkomstig van **IP 192.168.1.1**:

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

Deze regel blokkeert aanvragen om paden `/block-me`en blokkeert elke aanvraag die overeenkomt met een `SQLI` of `XSS` patroon. Dit voorbeeld omvat een het verkeersfilterregels van WAF, die verwijzingen `SQLI` en `XSS` [WAF-vlaggen](#waf-flags-list)en dus een aparte vergunning vereist.

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

Soms is het wenselijk om verkeer te blokkeren als het een bepaald tarief van inkomende verzoeken overschrijdt, misschien gebaseerd op een specifieke voorwaarde. Een waarde instellen voor de `rateLimit` eigenschap beperkt de snelheid van die aanvragen die overeenkomen met de regelvoorwaarde.

Regels voor tarieflimieten kunnen niet verwijzen naar WAF-vlaggen. Ze zijn beschikbaar voor alle klanten van Sites en Forms.

Snelheidslimieten worden berekend per CDN POP. Als voorbeeld, veronderstel dat POPs in Montreal, Miami, en Dublin verkeerstarieven van 80, 90, en 120 verzoek per seconde ervaren, en dat de tariefgrensregel wordt geplaatst aan een grens van 100. In dat geval zou alleen het verkeer naar Dublin beperkt zijn.

De grenzen van het tarief worden geëvalueerd gebaseerd op of verkeer dat de rand raakt, verkeer dat de rand raakt, of het aantal fouten.

### rateLimit-structuur {#ratelimit-structure}

| **Eigenschap** | **Type** | **Standaard** | **BETEKENEN** |
|---|---|---|---|
| limiet | geheel getal van 10 tot en met 10000 | vereist | Het tarief van het verzoek (per CDN POP) in verzoeken per seconde waarvoor de regel wordt teweeggebracht. |
| venster | geheel getal: 1, 10 of 60 | 10 | Samplingvenster in seconden waarvoor de aanvraagsnelheid wordt berekend. De nauwkeurigheid van de tellers hangt af van de grootte van het venster (grotere vensternauwkeurigheid). U kunt bijvoorbeeld een nauwkeurigheid van 50% verwachten voor het tweede venster en een nauwkeurigheid van 90% voor het tweede venster van 60 seconden. |
| straf | geheel getal van 60 tot 3600 | 300 | Een periode in seconden waarvoor overeenkomstige verzoeken worden geblokkeerd (afgerond naar de dichtstbijzijnde minuut). |
| aantal | all, fetch, error | alles | evalueert gebaseerd op randverkeer (allen), oorsprongverkeer (haal), of het aantal fouten. |
| groupBy | array[Getter] | none | De teller van de snelheidsbegrenzer zal door een reeks verzoekeigenschappen (bijvoorbeeld, clientIp) worden bijeengevoegd. |


### Voorbeelden {#ratelimiting-examples}

**Voorbeeld 1**

Deze regel blokkeert een cliënt voor 5m wanneer het een gemiddelde van 60 req/sec (per KNP CDN) in de laatste 10 sec overschrijdt:

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
        count: all
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Voorbeeld 2**

De verzoeken van het blok op weg /kritiek/middel voor 60s wanneer het een gemiddelde van 100 req/sec (per CDN POP) in de laatste 60 sec overschrijdt:

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
        rateLimit: { limit: 100, window: 60, penalty: 60, count: all }
```

## Waarschuwing verkeersfilterregels {#traffic-filter-rules-alerts}

>[!NOTE]
>
>Deze functie wordt nog niet vrijgegeven. Voor toegang via het programma voor vroege adoptie kunt u e-mail **aemcs-waf-adopter@adobe.com**.

Een regel kan worden gevormd om een bericht van het Centrum van Acties te verzenden als het 10 keer binnen een 5 minieme venster wordt teweeggebracht, daardoor alarmerend u wanneer bepaalde verkeerspatronen voorkomen zodat kunt u om het even welke noodzakelijke maatregelen nemen. Meer informatie over [Handelingencentrum](/help/operations/actions-center.md), inclusief hoe u de vereiste meldingsprofielen kunt instellen voor het ontvangen van e-mailberichten.

![Melding van actiecentra](/help/security/assets/traffic-filter-rules-actions-center-alert.png)


De eigenschap alert (momenteel voorafgegaan door *experimenteel* aangezien de eigenschap nog niet wordt vrijgegeven) kan op de actieknooppunt voor alle actietypes (toestaan, blok, logboek) worden toegepast.

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
          experimental_alert: true
```

## CDN-logs {#cdn-logs}

AEM as a Cloud Service verleent toegang tot CDN logboeken, die voor gebruiksgevallen met inbegrip van de optimalisering van de geheim voorgeheugenklapverhouding, en het vormen van de regels van de verkeersfilter nuttig zijn. CDN-logboeken worden weergegeven in Cloud Manager **Logbestanden downloaden** wanneer u de service Auteur of Publiceren selecteert.

CDN-logbestanden kunnen maximaal vijf minuten worden vertraagd.

De `rules` De eigenschap beschrijft welke regels voor verkeersfilters worden aangepast en heeft het volgende patroon:

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Bijvoorbeeld:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

De regels gedragen zich als volgt:

* De klant-verklaarde regelnaam van om het even welke passende regels zal in worden vermeld `match` kenmerk.
* De `action` het attribuut bepaalt of de regels het effect van het blokkeren, het toestaan, of het registreren hadden.
* Als WAF vergunning en toegelaten is, `waf` in dit kenmerk worden alle WAF-markeringen (bijvoorbeeld SQLI) weergegeven die zijn gedetecteerd, ongeacht of de WAF-markeringen in een regel zijn vermeld. Dit moet inzicht verschaffen in mogelijke nieuwe regels die moeten worden gedeclareerd.
* Als er geen door de klant gedeclareerde regels overeenkomen en er geen waf-regels overeenkomen, wordt de `rules` eigenschap is leeg.

Zoals eerder vermeld, verschijnen de de regelovereenkomsten van WAF slechts in CDN- logboeken voor CDN missen en overgaan, niet klappen.

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

[Tutorials](#tutorial) zijn beschikbaar voor concrete instructies over het gebruik van de dashboardgereedschappen.

## Aanbevolen startregels {#recommended-starter-rules}

U kunt de aanbevolen regels hieronder kopiëren naar uw `cdn.yaml` aan de slag. Begin op logboekwijze, analyseer uw verkeer, en wanneer tevreden, verandering in blokwijze. Mogelijk wilt u de regels wijzigen op basis van de unieke kenmerken van het live verkeer van uw website.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
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
    # Enable recommended WAF protections (only works if WAF is licensed enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        matches: "author|publish"
      action:
        type: log
        wafFlags:
          - SANS
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
    # Disable protection against CMDEXE on /bin (only works if WAF is licensed enabled for your environment)
    - name: allow-cdmexe-on-root-bin
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            matches: "^/bin/.*"
      action:
        type: allow
        wafFlags:
          - CMDEXE
```

## Tutorials {#tutorial}

Er zijn twee zelfstudies beschikbaar.

### Websites beschermen met verkeersfilterregels (inclusief WAF-regels)

[Een zelfstudie gebruiken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html) algemene, praktische kennis en ervaring op te doen met verkeersfilterregels, met inbegrip van WAF-regels.

De zelfstudie begeleidt u door:

* De configuratiepijplijn van Cloud Manager instellen
* Het gebruiken van hulpmiddelen om kwaadwillig verkeer te simuleren
* Regels voor het declareren van verkeersfilters, inclusief WAF-regels
* Resultaten analyseren met dashboardgereedschappen
* Aanbevolen procedures

### Het blokkeren Dos en de aanvallen van DDoS gebruikend de regels van de verkeersfilter

[Diep duiken op hoe te om te blokkeren](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/security/blocking-dos-attack-using-traffic-filter-rules) Ontkenning van de (Dos) van de Dienst en Verdeelde Ontkenning van de (DDoS) aanvallen van de Dienst gebruikend de regels van de het verkeersfilter van de tariefgrens en andere strategieën.

De zelfstudie begeleidt u door:

* begrijpen, beveiliging
* ontvangen van waarschuwingen wanneer tarieflimieten worden overschreden
* het analyseren van verkeerspatronen gebruikend dashboardtooling om drempels voor de regels van de snelheidsgrensfilter te vormen



