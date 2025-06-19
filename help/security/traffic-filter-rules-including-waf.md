---
title: Verkeersfilterregels inclusief WAF-regels
description: Het vormen de Regels van de Filter van het Verkeer met inbegrip van de Regels van de Firewall van de Toepassing van het Web (WAF).
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
feature: Security
role: Admin
source-git-commit: 70ba91e83ce2395e748ff8bdbecfc4d4fc04250b
workflow-type: tm+mt
source-wordcount: '4262'
ht-degree: 0%

---


# Regels voor verkeersfilters, inclusief WAF-regels {#traffic-filter-rules-including-waf-rules}

De filterregels van het verkeer kunnen worden gebruikt om verzoeken bij de laag te blokkeren of toe te staan CDN, die in scenario&#39;s zoals nuttig kan zijn:

* Toegang tot specifieke domeinen beperken tot intern bedrijfsverkeer, voordat een nieuwe site live gaat
* Het vestigen van tariefgrenzen om minder vatbaar voor volumetrische aanvallen van Dos te zijn
* Voorkomen dat IP-adressen waarvan bekend is dat ze kwaadaardig zijn, zich richten op uw pagina&#39;s

De meeste van deze verkeersfilterregels zijn beschikbaar aan alle klanten van AEM as a Cloud Service Sites en van Forms. Zij werken hoofdzakelijk op verzoekeigenschappen en verzoekkopballen, met inbegrip van IP, hostname, weg, en gebruikersagent.

Een subcategorie van verkeersfilterregels vereist of een vergunning van Uitgebreide Veiligheid of van de Bescherming WAF-DDoS. Deze krachtige regels zijn gekend als het verkeersfilterregels van het het verkeersfilter van WAF (of de regels van WAF voor kort) en hebben toegang tot de [ Vlaggen van WAF ](#waf-flags-list) die later in dit artikel worden beschreven.

De filterregels van het verkeer kunnen via Cloud Manager config pijpleidingen worden opgesteld om, stadium, en de types van productiemilieu te ontwikkelen. Het configuratiedossier kan aan de Milieu&#39;s van de Snelle Ontwikkeling (RDEs) worden opgesteld gebruikend bevellijn tooling.

[ volg door een leerprogramma ](#tutorial) om concrete deskundigheid op deze eigenschap snel te bouwen.

>[!NOTE]
>Voor extra opties met betrekking tot het vormen van verkeer bij CDN, met inbegrip van het uitgeven van het verzoek/de reactie, het verklaren van opnieuw richt, en het proxying aan een niet-AEM oorsprong, zie [ het Vormen Verkeer bij het CDN ](/help/implementing/dispatcher/cdn-configuring-traffic.md) artikel.


## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is onderverdeeld in de volgende secties:

* **overzicht van de bescherming van het Verkeer:** leer hoe u tegen kwaadwillig verkeer wordt beschermd.
* **Voorgesteld proces om regels te vormen:** las over een methodologie op hoog niveau voor het beschermen van uw website.
* **Opstelling:** ontdekt hoe te opstelling, vorm, en stel de regels van de verkeersfilter, met inbegrip van de geavanceerde regels van WAF op.
* **syntaxis van Regels:** las over hoe te om de regels van de verkeersfilter in het `cdn.yaml` configuratiedossier te verklaren. Dit omvat zowel de regels van de verkeersfilter beschikbaar aan alle Sites en klanten van Forms, als de subcategorie van de regels van WAF voor degenen die van dat vermogen vergunning geven.
* **de voorbeelden van Regels:** zie voorbeelden van verklaarde regels om u op uw manier te krijgen.
* **de grensregels van het Tarief:** leer hoe te om tarief te gebruiken die regels beperken om uw plaats tegen hoge volumeaanvallen te beschermen.
* **de Regels van de Filter van het Verkeer Alarm** vormt alarm om op de hoogte te worden gebracht wanneer uw regels worden teweeggebracht.
* **StandaardSpiek van het Verkeer bij Herinnering van de Oorsprong** wordt op de hoogte gebracht wanneer er een toename van verkeer bij de oorsprong wijzend op een aanval DDoS is.
* **CDN logboeken:** zie welke verklaarde regels en de Vlaggen van WAF uw verkeer aanpassen.
* **Tooling van het Dashboard:** Analyseer uw CDN- logboeken om omhoog met nieuwe regels van de verkeersfilter te komen.
* **geadviseerde Regels van de Aanzet:** Een reeks regels om met te beginnen.
* **Leerprogramma:** Praktische kennis over de eigenschap, met inbegrip van hoe te om dashboardtoolings te gebruiken om de juiste regels te verklaren.

## Overzicht van verkeersbeveiliging {#traffic-protection-overview}

In het huidige digitale landschap is kwaadwillig verkeer een steeds grotere bedreiging. Adobe erkent de ernst van het risico en biedt verschillende manieren om klanttoepassingen te beschermen en aanvallen te beperken wanneer deze zich voordoen.

Aan de rand absorbeert de door Adobe beheerde CDN DoS-aanvallen op de netwerklaag (lagen 3 en 4), inclusief overstroming en reflectie-/versterkingsaanvallen.

Adobe neemt standaard maatregelen om te voorkomen dat de prestaties achteruitgaan als gevolg van uitbarstingen van onverwacht hoog verkeer boven een bepaalde drempel. Als er een aanval van Dos is die plaatsbeschikbaarheid beïnvloedt, worden de verrichtingenteams van Adobe gewaarschuwd en nemen stappen om te verlichten.

De klanten kunnen pro-actieve maatregelen nemen om de aanvallen van de toepassingslaag (laag 7) te verlichten door regels bij diverse lagen van de stroom van de inhoudslevering te vormen.

Bijvoorbeeld, bij de laag Apache, kunnen de klanten of de [ module van Dispatcher ](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#configuring-access-to-content-filter) of [ ModSecurity ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection) vormen om toegang tot bepaalde inhoud te beperken.

Aangezien dit artikel beschrijft, kunnen de regels van de verkeersfilter aan Adobe Geleide CDN worden opgesteld, gebruikend Cloud Manager [ config pijpleidingen ](/help/operations/config-pipeline.md). Naast de regels van de verkeersfilter die op eigenschappen zoals IP adres, weg, en kopballen, of regels worden gebaseerd die op het plaatsen van tariefgrenzen worden gebaseerd, kunnen de klanten een krachtige subcategorie van de regels van de verkeersfilter ook vergunning geven genoemd de regels van WAF.

## Voorgesteld proces {#suggested-process}

Het volgende is een geadviseerd proces op hoog niveau van begin tot eind voor het komen met de juiste regels van de verkeersfilter:

1. Vorm niet-productie en productie config pijpleidingen, zoals die in de [ sectie van de Opstelling ](#setup) worden beschreven.
1. Klanten die een licentie voor de subcategorie van WAF-verkeersfilterregels hebben, moeten deze in Cloud Manager inschakelen.
1. Lees en probeer uit het leerprogramma om concreet te begrijpen hoe te om de regels van de verkeersfilter, met inbegrip van de regels van WAF te gebruiken als zij vergunning hebben gekregen. Het leerprogramma begeleidt u door het opstellen van regels aan een dev milieu, dat kwaadwillig verkeer simuleert, de [ CDN- logboeken ](#cdn-logs) downloadt, en hen analyseert in [ dashboard tooling ](#dashboard-tooling).
1. Kopieer de aanbevolen startregels naar `cdn.yaml` en implementeer de configuratie in de logmodus in de productieomgeving.
1. Na het verzamelen van wat verkeer, analyseer de resultaten gebruikend [ dashboard tooling ](#dashboard-tooling) om te zien of waren er om het even welke gelijken. Lookout voor valse positieven, en maak om het even welke noodzakelijke aanpassingen, uiteindelijk toelatend de starterregels op blokwijze.
1. Voeg douaneregels toe die op analyse van de logboeken CDN worden gebaseerd, eerst het testen met gesimuleerd verkeer op ontwikkelmilieu&#39;s alvorens aan stadium en productiemilieu&#39;s op logboekwijze, dan blokwijze op te stellen.
1. Het verkeer van de controle voortdurend, veranderend de regels aangezien het bedreigingslandschap evolueert.

## Instellen {#setup}

1. Maak een bestand `cdn.yaml` met een set verkeersfilterregels, waaronder WAF-regels.

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

   Zie [ Gebruikend Pijpleidingen Config ](/help/operations/config-pipeline.md#common-syntax) voor een beschrijving van de eigenschappen boven de `data` knoop. De `kind` bezitswaarde zou aan *CDN* moeten worden geplaatst en de versie zou aan `1` moeten worden geplaatst.


1. Als WAF-regels een licentie hebben, moet u de functie in Cloud Manager inschakelen, zoals hieronder wordt beschreven voor zowel de nieuwe als de bestaande programmascenario&#39;s.

   1. Om WAF op een nieuw programma te vormen, controleer de **controle-doos van de Bescherming WAF-DDOS op het** 3&rbrace; lusje van de Veiligheid [ een productieprogramma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) toevoegen.**&#x200B;**

   1. Om WAF op een bestaand programma te vormen, [ geef uw programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) en op het **3&rbrace; lusje van de Veiligheid &lbrace;uit uncheck of controleer op elk ogenblik de** WAF-DDOS **optie.**

1. Creeer een config pijpleiding in Cloud Manager, zoals die in [ wordt beschreven config pijpleidingsartikel ](/help/operations/config-pipeline.md#managing-in-cloud-manager). De pijpleiding zal een hoogste niveau `config` omslag met het `cdn.yaml` dossier van verwijzingen voorzien dat ergens onder wordt geplaatst, zie [ Gebruikend Pijpleidingen Config ](/help/operations/config-pipeline.md#folder-structure).

## Syntaxis verkeersfilterregels {#rules-syntax}

U kunt *regels van de verkeersfilter* vormen om op patronen zoals IPs, gebruikersagent, verzoekkopballen, hostname, geo, en url aan te passen.

De klanten die van Verbeterde Veiligheid of WAF-DDoS het aanbieden van de Veiligheid van de Bescherming ook vergunning geven kunnen een speciale categorie van de regels van de verkeersfilter vormen genoemd *de regels van de het verkeersfilter van 0&rbrace; WAF (of de regels van WAF voor kort) die één of meer [ vlaggen van WAF ](#waf-flags-list) van verwijzingen voorzien.*

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
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

De indeling van de verkeersfilterregels in het `cdn.yaml` -bestand wordt hieronder beschreven. Zie sommige [ andere voorbeelden ](#examples) in een recentere sectie, en een afzonderlijke sectie over [ Regels van de Grens van het Tarief ](#rate-limit-rules).


| **Bezit** | **de Meeste regels van de verkeersfilter** | **de regels van de het verkeersfilter van WAF** | **Type** | **Standaardwaarde** | **Beschrijving** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelnaam (64 tekens lang, alleen alfanumerieke tekens en -) |
| wanneer | X | X | `Condition` | - | De basisstructuur is:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[ zie de syntaxis van de Structuur van de Voorwaarde ](#condition-structure) hieronder, die de getters, voorspelt, en hoe te om veelvoudige voorwaarden te combineren. |
| action | X | X | `Action` | log | log, allow, block of Action-object. Standaard is log |
| rateLimit | X |   | `RateLimit` | niet gedefinieerd | Snelheidsbeperkende configuratie. Snelheidsbeperking is uitgeschakeld als deze niet is gedefinieerd.<br><br> Er is een afzonderlijke sectie verder onder beschrijvend de rateLimit syntaxis, samen met voorbeelden. |

### Voorwaardestructuur {#condition-structure}

Een voorwaarde kan een eenvoudige Voorwaarde of een groep Voorwaarden zijn.

**Eenvoudige Voorwaarde**

Een eenvoudige voorwaarde bestaat uit een getter en een voorspelling.

```
{ <getter>: <value>, <predicate>: <value> }
```

**Voorwaarden van de Groep**

Een groep Voorwaarden bestaat uit meerdere Eenvoudige en/of Groepsvoorwaarden.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **Bezit** | **Type** | **Betekenis** |
|---|---|---|
| **allOf** | `array[Condition]` | **en** verrichting. true als alle vermelde voorwaarden true retourneren |
| **anyOf** | `array[Condition]` | **of** verrichting. true als een van de vermelde voorwaarden true retourneert |

**Getter**

| **Bezit** | **Type** | **Beschrijving** |
|---|---|---|
| reqProperty | `string` | Request-eigenschap.<br><br> Één van:<br><ul><li>`path`: retourneert het volledige pad van een URL zonder de queryparameters. (gebruik `pathRaw` voor de niet-beschermde variant)</li><li>`url`: retourneert de volledige URL inclusief de queryparameters. (gebruik `urlRaw` voor de niet-beschermde variant)</li><li>`queryString`: retourneert het querygedeelte van een URL</li><li>`method`: retourneert de HTTP-methode die in de aanvraag wordt gebruikt.</li><li>`tier`: retourneert een van `author` , `preview` of `publish` .</li><li>`domain`: retourneert de eigenschap domain (zoals gedefinieerd in de `Host` -header) in kleine letters</li><li>`clientIp`: retourneert de client-IP.</li><li>`forwardedDomain`: retourneert het eerste domein dat in kleine letters is gedefinieerd in de `X-Forwarded-Host` -header</li><li>`forwardedIp`: retourneert het eerste IP in de `X-Forwarded-For` header.</li><li>`clientRegion`: Keert de code van de landonderverdeling terug die identificeert waarin het gebied de cliënt zoals die in [ wordt beschreven ISO 3166-2 ](https://en.wikipedia.org/wiki/ISO_3166-2) wordt gevestigd.</li><li>`clientCountry`: Keert een twee brievencode ([ Regionaal indicatorsymbool ](https://en.wikipedia.org/wiki/Regional_indicator_symbol)) terug die zich identificeert in welk land de cliënt wordt gevestigd.</li><li>`clientContinent`: Geeft een tweelettercode (AF, AN, AS, EU, NA, OC, SA) die aangeeft op welk continent de client zich bevindt.</li><li>`clientAsNumber`: Keert het [ Autonoom aantal van het Systeem ](https://en.wikipedia.org/wiki/Autonomous_system_(Internet)) verbonden aan de cliëntIP terug.</li><li>`clientAsName`: retourneert de naam die is gekoppeld aan het autonome systeemnummer.</li></ul> |
| reqHeader | `string` | Hiermee wordt aanvraagheader met de opgegeven naam geretourneerd |
| queryParam | `string` | Hiermee wordt de query-parameter met de opgegeven naam geretourneerd |
| reqCookie | `string` | Retourneert cookie met opgegeven naam |
| postParam | `string` | Keert de Parameter van het Post met gespecificeerde naam van het lichaam van het Verzoek terug. Werkt alleen als de hoofdtekst van het inhoudstype is `application/x-www-form-urlencoded` |

**Predicate**

| **Bezit** | **Type** | **Betekenis** |
|---|---|---|
| **evenaart** | `string` | true als het resultaat van de getter gelijk is aan de opgegeven waarde |
| **doesNotEqual** | `string` | true als het resultaat van de getter niet gelijk is aan de opgegeven waarde |
| **als** | `string` | true als het resultaat van de getter overeenkomt met het opgegeven patroon |
| **notLike** | `string` | true als het resultaat van de getter niet overeenkomt met het opgegeven patroon |
| **gelijken** | `string` | true als het resultaat van de getter overeenkomt met opgegeven regex |
| **doesNotMatch** | `string` | true als het resultaat van de getter niet overeenkomt met opgegeven regex |
| **in** | `array[string]` | true als de opgegeven lijst het resultaat getter bevat |
| **notIn** | `array[string]` | true als de opgegeven lijst geen resultaat voor getter bevat |
| **bestaat** | `boolean` | true wanneer ingesteld op true en eigenschap bestaat of wanneer ingesteld op false en eigenschap niet bestaat |

**Nota&#39;s**

* De request-eigenschap `clientIp` kan alleen worden gebruikt met de volgende voorspellingen: `equals`, `doesNotEqual`, `in`, `notIn` . `clientIp` kan ook worden vergeleken met IP-bereiken wanneer `in` en `notIn` voorspellingen worden gebruikt. In het volgende voorbeeld wordt een voorwaarde geïmplementeerd om te bepalen of een client-IP zich binnen het IP-bereik van 192.168.0.0/24 bevindt (dus van 192.168.0.0 tot 192.168.0.255 ):

```
when:
  reqProperty: clientIp
  in: [ "192.168.0.0/24" ]
```

* Adobe adviseert het gebruik van [ regex101 ](https://regex101.com/) en [ snelst verdwijnt ](https://fiddle.fastly.dev/) wanneer het werken met regex. U kunt meer over leren hoe de Snelle handvatten regex van [ dure documentatie - Reguliere uitdrukkingen in VCL van de Snelheid &lbrace;](https://www.fastly.com/documentation/reference/vcl/regex/#best-practices-and-common-mistakes).


### Handelingsstructuur {#action-structure}

Een `action` kan een tekenreeks zijn die de handeling opgeeft (toestaan, blokkeren of vastleggen), of een object dat is samengesteld uit zowel het handelingstype (toestaan, blokkeren of vastleggen) als opties zoals wafFlags en/of status.

**Types van Acties**

De acties worden geprioriteerd volgens hun types in de volgende lijst, die wordt bevolen om op de ordeacties te wijzen wordt uitgevoerd:

| **Naam** | **Toegestane Eigenschappen** | **Betekenis** |
|---|---|---|
| **toestaan** | `wafFlags` (optioneel), `alert` (optioneel) | als wafFlags niet aanwezig is, houdt verdere regelverwerking tegen en gaat aan het dienen van reactie te werk. Als wafFlags aanwezig is, maakt het gespecificeerde bescherming van WAF onbruikbaar en gaat aan verdere regelverwerking te werk. <br> als het alarm wordt gespecificeerd, wordt een bericht van het Centrum van Acties verzonden als de regel 10 keer in een 5 minieme venster wordt teweeggebracht. Zodra een alarm voor een bepaalde regel in werking wordt gesteld, zal het niet opnieuw weg tot de volgende dag (UTC). |
| **blok** | `status, wafFlags` (optioneel en wederzijds exclusief), `alert` (optioneel) | als wafFlags niet aanwezig is, retourneert de HTTP-fout waarbij alle andere eigenschappen worden overgeslagen, wordt de foutcode gedefinieerd door de status-eigenschap of is de standaardwaarde 406. Als wafFlags aanwezig is, laat het gespecificeerde bescherming van WAF toe en gaat aan verdere regelverwerking te werk. <br> als het alarm wordt gespecificeerd, wordt een bericht van het Centrum van Acties verzonden als de regel 10 keer in een 5 minieme venster wordt teweeggebracht. Zodra een alarm voor een bepaalde regel in werking wordt gesteld, zal het niet opnieuw weg tot de volgende dag (UTC). |
| **logboek** | `wafFlags` (optioneel), `alert` (optioneel) | registreert het feit dat de regel werd teweeggebracht, anders beïnvloedt niet de verwerking. wafFlags heeft geen effect. <br> als het alarm wordt gespecificeerd, wordt een bericht van het Centrum van Acties verzonden als de regel 10 keer in een 5 minieme venster wordt teweeggebracht. Zodra een alarm voor een bepaalde regel in werking wordt gesteld, zal het niet opnieuw weg tot de volgende dag (UTC). |

### Lijst met WAF-markeringen {#waf-flags-list}

De eigenschap `wafFlags` , die kan worden gebruikt in de licentieable WAF-regels voor verkeersfilters, kan naar het volgende verwijzen:

#### Verkeer

| **identiteitskaart van de Vlag** | **de Naam van de Vlag** | **Beschrijving** |
|---|---|---|
| AANVALLEN | Aanvallen | Markering om verzoeken te identificeren die een of meer van de aanvalstypen bevatten die in die tabel worden vermeld |
| AANVALLEN VANUIT BAD-IP | Aanval van slechte IP | Markering voor het identificeren van aanvragen afkomstig uit `BAD-IP` en die een of meer van de aanvalstypen bevatten die in die tabel worden vermeld |
| SQLI | SQL-injectie | SQL de Injectie is de poging om toegang tot een toepassing te verkrijgen of bevoorrechte informatie te verkrijgen door willekeurige gegevensbestandvragen uit te voeren. |
| BACKEUR | Achterkant | Een achterdeursignaal is een verzoek dat probeert te bepalen als een gemeenschappelijk achterdeurdossier op het systeem aanwezig is. |
| CMDEXE | Opdracht uitvoeren | De Uitvoering van het bevel is de poging om controle te verkrijgen of een doelsysteem door willekeurige systeembevelen door middel van gebruikersinput te beschadigen. |
| CMDEXE-NO-BIN | Opdracht uitvoeren, behalve op `/bin/` | Zorg voor hetzelfde beschermingsniveau als `CMDEXE` en schakel false-positive in `/bin` uit vanwege AEM-architectuur. |
| XSS | Scripts voor meerdere sites | Met scripts die verwijzen naar andere sites wordt geprobeerd een gebruikersaccount of een webbrowsersessie te kapen via kwaadaardige JavaScript-code. |
| TRAVERSAL | Directorytraversal | Directorytraversal is de poging om bevoorrechte omslagen door een systeem in hoop te navigeren om gevoelige informatie te verkrijgen. |
| GEBRUIKER | Gereedschap Bijsluiten | De Tooling van de aanval is het gebruik van geautomatiseerde software om veiligheidskwetsbaarheid te identificeren of te proberen om een ontdekte kwetsbaarheid te exploiteren. |
| LOG4J-JNDI | Log4J JNDI | De aanvallen van Log4J JNDI proberen om de [ kwetsbaarheid Log4Shell ](https://en.wikipedia.org/wiki/Log4Shell) huidig in versies Log4J vroeger dan 2.16.0 te exploiteren |
| CVE | CVE | Markering om een CVE te identificeren. Wordt altijd gecombineerd met een markering `CVE-<CVE Number>` . Neem contact op met Adobe voor meer informatie over welke CVE&#39;s Adobe u beschermt. |

#### Verdacht verkeer

| **identiteitskaart van de Vlag** | **de Naam van de Vlag** | **Beschrijving** |
|---|---|---|
| ABNORMALPATH | Abnormaal pad | Abnormaal pad geeft aan dat het oorspronkelijke pad afwijkt van het genormaliseerde pad (`/foo/./bar` is bijvoorbeeld genormaliseerd naar `/foo/bar`) |
| BAD-IP | Onjuiste IP | De vlag om verzoek te identificeren dat van IPs komt identificeert zich slecht, of omdat er als kwaadwillige bronnen (`SANS`, `TORNODE`) geïdentificeerd zijn of omdat zij door WAF slecht zijn geïdentificeerd nadat zij teveel kwaadwillige verzoeken verzonden |
| BHH | Onjuiste koppen | De slechte Kopballen van de Hop wijzen op een HTTP het smokkelen poging door of een misvormde overdracht-Codering (TE) of een inhoud-Lengte (CL) kopbal, of een goed gevormde TE en kopbal CL |
| CODEINJECTIE | Code-injectie | De Injectie van de code is de poging om controle te verkrijgen of een doelsysteem door arbitraire bevelen van de toepassingscode door gebruikersinput te beschadigen. |
| GECOMPRIMEERD | Compressie gedetecteerd | De POST-aanvraaginstantie is gecomprimeerd en kan niet worden gecontroleerd. Als bijvoorbeeld een aanvraagheader `Content-Encoding: gzip` is opgegeven en de hoofdtekst van de POST geen onbewerkte tekst is. |
| RESPONSESPLIT | HTTP-antwoordsplitsing | Identificeert wanneer CRLF-tekens als invoer naar de toepassing worden verzonden om headers in de HTTP-reactie te injecteren |
| NOTUTF8 | Ongeldige codering | Ongeldige codering kan ertoe leiden dat de server schadelijke tekens van een verzoek in een reactie omzet, wat of een ontkenning van de dienst of XSS veroorzaakt |
| MALFORMED-DATA | Onjuiste gegevens in de aanvraaginstantie | Een POST-, PUT- of PATCH-aanvraaginstantie die onjuist is samengesteld volgens de aanvraagheader &quot;Content-Type&quot;. Bijvoorbeeld, als een &quot;Content-Type: application/x-www-form-urlencoded&quot;verzoekkopbal wordt gespecificeerd en een POST lichaam bevat dat json is. Dit is vaak een programmeerfout, een geautomatiseerd of een kwaadwillig verzoek. Vereist agent 3.2 of hoger. |
| SANS | Verkeer van kwaadwillige IP | [ SANS Internet Storm Center ](https://isc.sans.edu/) lijst van gemelde IP adressen die in kwaadwillige activiteit betrokken waren. |
| NO-CONTENT-TYPE | Ontbrekende aanvraagheader &quot;Content-Type&quot; | A POST, PUT, or PATCH request that does not have a &quot;Content-Type&quot; request header. Standaard moeten toepassingsservers in dit geval &#39;Content-Type: text/plain; charset=us-ascii&#39; aannemen. Bij veel geautomatiseerde en kwaadaardige verzoeken ontbreekt mogelijk het type inhoud. |
| NOUA | Geen gebruikersagent | Geeft aan dat een aanvraag geen header &quot;User-Agent&quot; bevat of dat de headerwaarde niet is ingesteld. |
| NULLBYTE | Null Byte | Null-bytes worden normaal gesproken niet weergegeven in een verzoek en geven aan dat het verzoek onjuist is geformuleerd en mogelijk kwaadaardig is. |
| OOB-DOMAIN | Buiten-banddomein | Buiten-de-banddomeinen worden over het algemeen gebruikt tijdens penetratie het testen om kwetsbaarheid te identificeren waarin de netwerktoegang wordt toegestaan. |
| PRIVATEFIEL | Persoonlijke bestanden | Persoonlijke bestanden zijn vertrouwelijk, zoals een Apache `.htaccess` -bestand of een configuratiebestand dat vertrouwelijke informatie kan lekken |
| SCANNER | Scanner | Identificeert populaire scanservices en -gereedschappen |

#### Diversen verkeer

| **identiteitskaart van de Vlag** | **de Naam van de Vlag** | **Beschrijving** |
|---|---|---|
| DATACENTER | Datacenter | Identificeert de aanvraag als afkomstig van een bekende hostingprovider. Dit type van verkeer wordt niet algemeen geassocieerd met een echt eind - gebruiker. |
| DOUBLEENCODERING | Dubbele codering | De dubbele Codering controleert de ontduikingstechniek van het tweemaal coderen van HTML- karakters |
| JSON-ERROR | JSON-coderingsfout | A POST, PUT, or PATCH request body that is specified as containing JSON within the &quot;Content-Type&quot; request header but contains JSON parsing errors. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |
| TORNODE | Teerverkeer | Tor is software die de identiteit van een gebruiker verbergt. Een piek in het verkeer van de Tor kan op een aanvaller wijzen die probeert om hun plaats te maskeren. |
| XML-ERROR | XML-coderingsfout | A POST, PUT, or PATCH request body that is specified as containing XML within the &quot;Content-Type&quot; request header but contains XML parsing errors. Dit heeft vaak te maken met een programmeerfout of een geautomatiseerd of kwaadaardig verzoek. |

## Overwegingen {#considerations}

* Wanneer twee conflicterende regels worden gecreeerd, nemen de toegestane regels altijd belangrijkheid over de blokregels. Bijvoorbeeld, als u een regel creeert om een specifieke weg en een regel te blokkeren om één specifiek IP adres toe te staan, worden de verzoeken van dat IP adres op de geblokkeerde weg toegestaan.

* Als een regel wordt aangepast en geblokkeerd, reageert de CDN met een `406` retourcode.

* De configuratiedossiers zouden geen geheimen moeten bevatten aangezien zij door iedereen leesbaar zouden zijn die toegang tot de git bewaarplaats heeft.

* IP de lijsten van gewenste personen die in Cloud Manager worden bepaald hebben voorrang op de Regels van de Filters van het Verkeer.

* WAF-regelovereenkomsten worden alleen weergegeven in CDN-logboeken voor CDN-fouten en -controles, niet-treffers.

## Voorbeelden van regels {#examples}

Hier volgen enkele regelvoorbeelden. Zie de [ sectie van de tariefgrens ](#rate-limit-rules) verder neer voor voorbeelden van de regels van de tariefgrens.

**Voorbeeld 1**

Deze regel blokkeert aanvragen die afkomstig zijn van **IP192.168.1.1** :

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

Deze regel blokkeert een aanvraag op pad `/helloworld` bij publicatie met een gebruikersagent die Chrome bevat:

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

Deze regel blokkeert verzoeken om publicatie die de vraagparameter `foo` bevatten, maar staat elke aanvraag toe die uit IP 192.168.1.1 komt:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when:
          allOf:
            - { queryParam: url-param, equals: foo }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action:
          type: allow
```

**Voorbeeld 4**

Deze regel blokkeert aanvragen om een pad `/block-me` bij publicatie en blokkeert elke aanvraag die overeenkomt met een patroon `SQLI` of `XSS` . Dit voorbeeld omvat een het verkeersfilterregels van WAF, die `SQLI` en `XSS` [ Vlaggen van WAF ](#waf-flags-list) van verwijzingen voorzien, en zo een afzonderlijke vergunning vereist.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
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

## Regels voor tarieflimieten

Soms is het wenselijk om verkeer te blokkeren als het een bepaald tarief van inkomende verzoeken, gebaseerd op een specifieke voorwaarde overschrijdt. Als u een waarde voor de eigenschap `rateLimit` instelt, wordt de frequentie van die aanvragen beperkt die overeenkomen met de regelvoorwaarde.

Regels voor tarieflimieten kunnen niet verwijzen naar WAF-vlaggen. Ze zijn beschikbaar voor alle klanten van Sites en Forms.

Snelheidslimieten worden berekend per CDN POP. Als voorbeeld, veronderstel dat POPs in Montreal, Miami, en Dublin verkeerstarieven van 80, 90, respectievelijk 120 verzoeken per seconde ervaren. En de tarieflimietregel is ingesteld op een limiet van 100. In dat geval zou alleen het verkeer naar Dublin beperkt zijn.

De grenzen van het tarief worden geëvalueerd gebaseerd op of verkeer dat de rand raakt, verkeer dat de oorsprong raakt, of het aantal fouten.

### rateLimit-structuur {#ratelimit-structure}

| **Bezit** | **Type** | **Gebrek** | **BETEKENEN** |
|---|---|---|---|
| limiet | geheel getal van 10 tot en met 10000 | vereist | Het tarief van het verzoek (per CDN POP) in verzoeken per seconde waarvoor de regel wordt teweeggebracht. |
| venster | geheel getal: 1, 10 of 60 | 10 | Samplingvenster in seconden waarvoor de aanvraagsnelheid wordt berekend. De nauwkeurigheid van tellers hangt van de grootte van het venster (grotere vensternauwkeurigheid) af. U kunt bijvoorbeeld 50% nauwkeurigheid verwachten voor het venster van 1 seconde en 90% nauwkeurigheid voor het venster van 60 seconden. |
| straf | geheel getal van 60 tot 3600 | 300 | Een periode in seconden waarvoor overeenkomstige verzoeken worden geblokkeerd (afgerond naar de dichtstbijzijnde minuut). |
| aantal | all, fetches, fouten | alles | evalueert gebaseerd op randverkeer (allen), oorsprongverkeer (halen), of het aantal fouten (fouten). |
| groupBy | serie [ Getter ] | none | De teller van de snelheidsbegrenzer zal door een reeks verzoekeigenschappen (bijvoorbeeld, clientIp) worden bijeengevoegd. |

### Voorbeelden {#ratelimiting-examples}

**Voorbeeld 1**

Deze regel blokkeert een cliënt voor 5 milliseconden wanneer het een gemiddelde van 60 req/sec (per KNP CDN) in de laatste 10 sec overschrijdt:

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

De verzoeken van het blok op weg /kritiek/middel voor 60 seconden wanneer het een gemiddelde van 100 verzoeken aan oorsprong per seconde (per CDN POP) op een tijdvenster van tien seconden overschrijdt:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when:
          allOf:
            - { reqProperty: path, equals: /critical/resource }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
        rateLimit: { limit: 100, window: 10, penalty: 60, count: fetches }
```

## CVE-regels {#cve-rules}

Als WAF een licentie heeft, past Adobe automatisch blokkeringsregels toe ter bescherming tegen veel bekende CVE&#39;s (Common Vulnerabilities and Exposure) en kunnen er snel na de ontdekking nieuwe CVE&#39;s worden toegevoegd. Klanten moeten de CVE-regels zelf niet configureren en hoeven dat ook niet te doen.

Als een verkeersverzoek een CVE aanpast, zal het in de overeenkomstige CDN logboekingang verschijnen.

Neem contact op met de ondersteuning van Adobe als er vragen zijn over een bepaalde CVE of als er een bepaalde CVE-regel is die uw organisatie wil uitschakelen.

## Waarschuwing verkeersfilterregels {#traffic-filter-rules-alerts}

Een regel kan worden gevormd om een bericht van het Centrum van Acties te verzenden als het tien keer binnen een 5 minieme venster wordt teweeggebracht. Een dergelijke regel waarschuwt u wanneer bepaalde verkeerspatronen voorkomen zodat u om het even welke noodzakelijke maatregelen kunt nemen. Zodra een alarm voor een bepaalde regel in werking wordt gesteld, zal het niet opnieuw weg tot de volgende dag (UTC).

Leer meer over [ Centrum van Acties ](/help/operations/actions-center.md), met inbegrip van hoe te opstelling de vereiste Profielen van het Bericht om e-mails te ontvangen.

![ het Bericht van het Centrum van Acties ](/help/security/assets/traffic-filter-rules-actions-center-alert.png)


De waakzame eigenschap kan worden toegepast op het actieknooppunt voor alle handelingstypen (toestaan, blokkeren, vastleggen).

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
          alert: true
```

## Standaardverkeersspiegel bij oorspronkelijke waarschuwing {#traffic-spike-at-origin-alert}

Een [&#128279;](/help/operations/actions-center.md) e-mailbericht van het Centrum van Acties 1&rbrace; zal worden verzonden wanneer er een significante hoeveelheid verkeer is dat naar de oorsprong wordt verzonden, waar een hoge drempel van verzoeken uit het zelfde IP adres komt, zo wijzend op een aanval DDoS.

Als deze greep wordt ontmoet, zal Adobe verkeer van dat IP adres blokkeren, maar het wordt geadviseerd om extra maatregelen te nemen om uw oorsprong te beschermen, met inbegrip van het vormen van de regels van de de filterfilter van de tariefgrens om verkeerspikes bij lagere drempels te blokkeren. Zie [ het Blokkeren Dos en aanvallen DDoS gebruikend het leerprogramma van verkeersregels ](#tutorial-blocking-DDoS-with-rules) voor een geleide looppas-door.

Dit alarm wordt toegelaten door gebrek, maar het kan worden onbruikbaar gemaakt gebruikend het *defaultTrafficAlerts* bezit, dat aan vals wordt geplaatst. Zodra de waarschuwing in werking wordt gesteld, zal het niet opnieuw weg tot de volgende dag (UTC).

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
   defaultTrafficAlerts: false
```

## CDN-logs {#cdn-logs}

AEM as a Cloud Service verleent toegang tot CDN logboeken, die voor gebruiksgevallen met inbegrip van de optimalisering van de geheim voorgeheugenklapverhouding, en het vormen van de regels van de verkeersfilter nuttig zijn. CDN- logboeken verschijnen in de dialoog van de Logboeken van de Download van Cloud Manager **&#x200B;**, wanneer het selecteren van de Auteur of de Publish dienst.

CDN-logbestanden kunnen maximaal vijf minuten worden vertraagd.

De eigenschap `rules` beschrijft welke regels voor verkeersfilters worden aangepast en heeft het volgende patroon:

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Bijvoorbeeld:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

De regels gedragen zich als volgt:

* De door de klant gedeclareerde regelnaam van overeenkomende regels wordt vermeld in het kenmerk `match` .
* Het attribuut `action` bepaalt of de regels blokkeren, toestaan, of logboek.
* Als de WAF een licentie heeft en is ingeschakeld, geeft het kenmerk `waf` alle eventuele WAF-markeringen weer (bijvoorbeeld SQLI) die zijn gedetecteerd. Dit geldt ongeacht of de WAF-vlaggen in enige regelgeving zijn vermeld. Dit moet insight in staat stellen nieuwe regels op te stellen.
* Als er geen door de klant gedeclareerde regels overeenkomen en er geen waf-regels overeenkomen, is de eigenschap `rules` leeg.

Zoals eerder vermeld, verschijnen de regelovereenkomsten van WAF slechts in CDN- logboeken voor CDN missen en overgaan, niet klappen.

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

| **Naam van het Gebied** | **Beschrijving** |
|---|---|
| *timestamp* | De tijd waarop de aanvraag is gestart, na beëindiging van TLS. |
| *ttfb* | Afkorting voor *Tijd aan Eerste Byte*. Het tijdinterval tussen het verzoek begon tot het punt alvorens het reactiekarakter begon te worden gestroomd. |
| *cli_ip* | Het client-IP-adres. |
| *cli_country* | Twee-brief [ ISO 3166-1 ](https://en.wikipedia.org/wiki/ISO_3166-1) alpha-2 landcode voor het cliëntland. |
| *rid* | De waarde van de verzoekkopbal die wordt gebruikt om het verzoek uniek te identificeren. |
| *req_ua* | De gebruikersagent die verantwoordelijk is voor het indienen van een bepaalde HTTP-aanvraag. |
| *gastheer* | De autoriteit waarvoor het verzoek is bestemd. |
| *url* | Het volledige pad, inclusief queryparameters. |
| *methode* | HTTP-methode die door de client wordt verzonden, zoals &quot;GET&quot; of &quot;POST&quot;. |
| *res_ctype* | Het Content-Type dat wordt gebruikt om het oorspronkelijke mediatype van de bron aan te geven. |
| *geheime voorgeheugen* | Status van de cache. Mogelijke waarden zijn HIT, MISS of PASS |
| *status* | De HTTP-statuscode als een geheel getal. |
| *res_age* | De hoeveelheid tijd (in seconden) dat een reactie in de cache is geplaatst (in alle knooppunten). |
| *pop* | Datacenter van de CDN-cacheserver. |
| *regels* | De naam van eventuele overeenkomende regels.<br><br> wijst ook op als de gelijke in een blok resulteerde. <br><br> Bijvoorbeeld, &quot;`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`&quot;<br><br> Leeg als geen regels aankwamen. |

## Dashboard Tooling {#dashboard-tooling}

Adobe biedt een mechanisme voor het downloaden van dashboardgereedschappen naar uw computer om CDN-logbestanden in te voegen die via Cloud Manager zijn gedownload. Met dit hulpmiddel, kunt u uw verkeer analyseren om omhoog met de aangewezen regels van de verkeersfilter te komen om te verklaren, met inbegrip van de regels van WAF.

Het tooling van het dashboard kan direct van de [ worden gekloond AEMCS-CDN-Logboek-Analyse-Tooling ](https://github.com/adobe/AEMCS-CDN-Log-Analysis-Tooling) bewaarplaats GitHub.

[ Leerprogramma&#39;s ](#tutorial) zijn beschikbaar voor concrete instructies op hoe te om het dashboardhulpmiddel te gebruiken.

## Aanbevolen startregels {#recommended-starter-rules}

U kunt de aanbevolen regels hieronder naar uw `cdn.yaml` kopiëren om aan de slag te gaan. Begin op logboekwijze, analyseer uw verkeer, en wanneer tevreden, verandering in blokwijze. Mogelijk wilt u de regels wijzigen op basis van de unieke kenmerken van het live verkeer van uw website.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds an average of 100 req/sec to origin on a time window of 10sec
    - name: limit-origin-requests-client-ip
      when:
        reqProperty: tier
        equals: 'publish'
      rateLimit:
        limit: 100
        window: 10
        count: fetches
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    #  Block client for 5m when it exceeds an average of 500 req/sec on a time window of 10sec
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        equals: 'publish'
      rateLimit:
        limit: 500
        window: 10
        count: all
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    # Block requests coming from OFAC countries
    - name: block-ofac-countries
      when:
        allOf:
          - { reqProperty: tier, in: ["author", "publish"] }
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
        in: ["author", "publish"]
      action:
        type: log
        wafFlags:
          - TRAVERSAL
          - CMDEXE-NO-BIN
          - XSS
          - LOG4J-JNDI
          - BACKDOOR
          - USERAGENT
          - SQLI
          - SANS
          - TORNODE
          - NOUA
          - SCANNER
          - PRIVATEFILE
          - NULLBYTE
```

## Tutorials {#tutorial}

Er zijn twee zelfstudies beschikbaar.

### Websites beschermen met verkeersfilterregels (inclusief WAF-regels) {#tutorial-protecting-websites}

[ het Werk door een leerprogramma ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview) om algemene, praktische kennis en ervaring rond de regels van de verkeersfilter, met inbegrip van de regels van WAF te bereiken.

De zelfstudie begeleidt u door:

* De Cloud Manager config-pijplijn instellen
* Het gebruiken van hulpmiddelen om kwaadwillig verkeer te simuleren
* Regels voor het declareren van verkeersfilters, inclusief WAF-regels
* Resultaten analyseren met dashboardgereedschappen
* Aanbevolen procedures

### Het blokkeren Dos en de aanvallen van DDoS gebruikend de regels van de verkeersfilter {#tutorial-blocking-DDoS-with-rules}

[ diepte-duik op hoe te om ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/security/blocking-dos-attack-using-traffic-filter-rules) Ontkenning van de Dienst (Dos) en Verspreid Ontkenning van de aanvallen van de Dienst (DDoS) te blokkeren gebruikend de regels van de het verkeersfilter van de snelheidsbeperking en andere strategieën.

De zelfstudie begeleidt u door:

* begrijpen, beveiliging
* ontvangen van waarschuwingen wanneer tarieflimieten worden overschreden
* het analyseren van verkeerspatronen gebruikend dashboardtooling om drempels voor de regels van de snelheidsgrensfilter te vormen



