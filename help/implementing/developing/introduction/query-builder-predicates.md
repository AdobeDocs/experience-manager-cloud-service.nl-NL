---
title: Voorlopige naslaggids voor Query Builder
description: Predicate reference for the Query Builder API in AEM as a Cloud Service.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2270'
ht-degree: 0%

---

# Voorlopige naslaggids voor Query Builder {#query-builder-predicate-reference}

## Algemeen {#general}

### basis {#root}

De basisgroep voor voorspelling. Het steunt alle eigenschappen van een groep en staat het plaatsen van globale vraagparameters toe.

De naam &quot;wortel&quot;wordt nooit gebruikt in een vraag; het is impliciet.

#### Eigenschappen {#properties-18}

* **`p.offset`** - getal dat het begin van de resultatenpagina aangeeft, dat wil zeggen het aantal items dat moet worden overgeslagen.
* **`p.limit`** - getal dat het paginaformaat aangeeft.
* **`p.guessTotal`** - aanbevolen: het volledige resultaattotaal, dat kostbaar kan zijn, niet berekenen. Of een aantal die op het maximumtotaal om te tellen tot (bijvoorbeeld, 1000, een aantal wijst dat gebruikers genoeg terugkoppelt op de ruwe grootte en nauwkeurige aantallen voor kleinere resultaten). Of, `true` slechts tot het noodzakelijke minimum te tellen `p.offset` + `p.limit`.
* **`p.excerpt`** - indien ingesteld op `true`, neemt u het volledige tekstfragment op in het resultaat.
* **`p.indexTag`** - als de reeks een optie van de indexmarkering in de vraag zal omvatten (zie [Index-tag voor zoekopties](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-option-index-tag)).
* **`p.facetStrategy`** - indien ingesteld op `oak`, zal de Bouwer van de Vraag facetextractie aan Oak (zie [Facetten](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#facets)).
* **`p.hits`** - (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met deze standaardtreffers (uitbreidbaar via de service ResultHitWriter).
   * **`simple`** - minimale objecten zoals `path`, `title`, `lastmodified`, `excerpt` (indien ingesteld).
   * **`full`** - JSON-rendering van het knooppunt met `jcr:path` die het pad van de hit aangeven. Door gebrek, maakt een lijst enkel van de directe eigenschappen van de knoop, omvat een diepere boom met `p.nodedepth=N`, waarbij 0 de gehele, oneindige substructuur betekent. Toevoegen `p.acls=true` om de JCR-machtigingen van de huidige sessie op te nemen voor het opgegeven resultaatitem (toewijzingen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** - alleen eigenschappen die zijn opgegeven in `p.properties`, dat een spatie gescheiden is (gebruik `+` in URLs) lijst van relatieve wegen. Als het relatieve pad een diepte heeft `>1`, worden deze eigenschappen vertegenwoordigd als onderliggende objecten. De bijzondere `jcr:path` Deze eigenschap bevat het pad van de hit.

### groep {#group}

Met deze voorspelling kunnen geneste voorwaarden worden gemaakt. Groepen kunnen geneste groepen bevatten. Alles in een query van de Bouwer van de Vraag is impliciet in een wortelgroep, die kan hebben `p.or` en `p.not` ook parameters.

Hieronder ziet u een voorbeeld voor het afstemmen van een van de twee eigenschappen op een waarde:

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Conceptueel is het `(1_property` OF `2_property)`.

Hieronder ziet u een voorbeeld voor geneste groepen:

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Zoekopdrachten voor de term **Beheer** binnen pagina&#39;s in `/content/wknd/ch/de` of in activa `/content/dam/wknd`.

Conceptueel is het `fulltext AND ( (path AND type) OR (path AND type) )`. Zulke OF toetreedt behoefte goede indexen voor prestatiesredenen.

#### Eigenschappen {#properties-6}

* **`p.or`** - indien ingesteld op `true`, slechts één predikaat in de groep moet aanpassen. Standaardwaarden: `false`, wat betekent dat alles moet overeenkomen
* **`p.not`** - indien ingesteld op `true`, wordt de groep genegeerd (standaard ingesteld op `false`)
* **`<predicate>`** - voegt geneste voorspellingen toe
* **`N_<predicate>`** - voegt meerdere geneste voorspellingen tegelijk toe, zoals `1_property, 2_property, ...`

### ordonneren {#orderby}

Op deze manier kunt u de resultaten sorteren. Als het opdracht geven door veelvoudige eigenschappen wordt vereist, moet dit predikaat veelvoudige tijden toevoegen gebruikend het aantalprefix, zoals `1_orderby=first`, `2_oderby=second`.

#### Eigenschappen {#properties-13}

* **`orderby`** - ofwel de naam van de JCR-eigenschap die wordt aangegeven door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title`of een andere voorspelling in de query, bijvoorbeeld `2_property`, waarop wordt gesorteerd
* **`sort`** - sorteerrichting: `desc` voor aflopende of `asc` voor oplopend (standaard)
* **`case`** - indien ingesteld op `ignore`wordt het sorteren ongevoelig voor hoofdletters en kleine letters `a` komt voor `B`; als de sortering leeg is of wordt weggelaten, is de sortering hoofdlettergevoelig (dus `B` komt voor `a`

## Voorspellen {#predicates}

### boolproperty {#boolproperty}

Dit voorspelt overeenkomsten op booleaanse eigenschappen JCR. Accepteert alleen de waarden `true` en `false`. Als de waarde `false`komt deze overeen als de eigenschap de waarde heeft `false`, of als deze überhaupt niet bestaat. Dit predikaat is nuttig om op booleaanse vlaggen te controleren die slechts wanneer toegelaten worden geplaatst.

De overgeërfde `operation` parameter heeft geen betekenis.

Dit voorspel steunt facetextractie en verstrekt emmers voor elk `true` of `false` waarde, maar alleen voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **`boolproperty`** - relatief pad naar eigenschap, bijvoorbeeld `myFeatureEnabled` of `jcr:content/myFeatureEnabled`
* **`value`** - waarde waarop de eigenschap moet worden gecontroleerd, `true` of `false`

### contentfragment {#contentfragment}

Hierdoor wordt het resultaat beperkt tot inhoudsfragmenten.

* Filteren wordt niet ondersteund.
* Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-1}

* **`contentfragment`** - Het kan met om het even welke waarde worden gebruikt om op inhoudsfragmenten te controleren.

### `dateComparison` {#datecomparison}

In deze voorspelling worden twee JCR-datumeigenschappen met elkaar vergeleken. Kan testen of ze gelijk, ongelijk, groter dan of groter dan of gelijk zijn.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

#### Eigenschappen {#properties-2}

* **`property1`** - pad naar eerste-datumeigenschap
* **`property2`** - pad naar tweede-datumeigenschap
* **`operation`**
   * `=` voor exacte overeenkomst (standaard)
   * `!=` voor ongelijkheidsvergelijking
   * `>` for `property1` groter dan `property2`
   * `>=` for `property1` groter dan of gelijk aan `property2`

### daterange {#daterange}

Deze voorspelling stemt de JCR-datumeigenschappen af op een datum-/tijdinterval. Gebruikt de ISO8601-indeling voor datums en tijden (`YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke vertegenwoordiging toe, zoals `YYYY-MM-DD`. U kunt de tijdstempel ook opgeven als POSIX-tijd.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Het steunt facetextractie en verstrekt emmers `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year`, en `earlier than last year`.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **`property`** - relatief pad naar `DATE` eigenschap, bijvoorbeeld `jcr:lastModified`
* **`lowerBound`** - lagere datum gebonden aan controle eigenschap voor, bijvoorbeeld, `2014-10-01`
* **`lowerOperation`** - `>` (nieuwer) of `>=` (bij of hoger), van toepassing op `lowerBound`. De standaardwaarde is `>`
* **`upperBound`** - bovengrens voor het controleren van eigenschappen, bijvoorbeeld `2014-10-01T12:15:00`
* **`upperOperation`** - `<` (ouder) of `<=` (bij of ouder) `upperBound`. De standaardwaarde is `<`
* **`timeZone`** - Id van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

### exclusief paden {#excludepaths}

In deze voorspelling worden knooppunten uitgesloten van het resultaat wanneer hun pad overeenkomt met een reguliere expressie.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-4}

* **`excludepaths`** - reguliere expressie komt overeen met resultaatpaden, met uitzondering van overeenkomende paden uit het resultaat.

### fulltext {#fulltext}

Zoekt naar termen in de fullText-index.

Filteren wordt niet ondersteund.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-5}

* **`fulltext`** - de volledige zoektermen
* **`relPath`** - het relatieve pad naar de eigenschap of het subknooppunt. Deze eigenschap is optioneel.

### hasPermission {#haspermission}

Dit voorspel beperkt het resultaat tot punten waar de huidige zitting gespecificeerde heeft [JCR-bevoegdheden.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **`hasPermission`** - alle door komma&#39;s gescheiden JCR-bevoegdheden die de huidige gebruikerssessie moet hebben voor het desbetreffende knooppunt. Bijvoorbeeld: `jcr:write`, `jcr:modifyAccessControl`

### taal {#language}

Dit voorspelt vindt AEM pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken. Deze eigenschap bevat vaak de taal of landinstelling in een sitestructuur op hoofdniveau.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het steunt facetextractie en verstrekt emmers voor elke unieke taalcode.

#### Eigenschappen {#properties-8}

* **`language`** - ISO-taalcode, bijvoorbeeld `de`

### hoofdmiddel {#mainasset}

Deze voorspelling controleert of een knooppunt een DAM-hoofdactief is en geen subactief. Het is eigenlijk elk knooppunt dat zich niet binnen een knooppunt sub assets bevindt. Het controleert niet op `dam:Asset` knooppunttype. Als u deze voorspelling wilt gebruiken, stelt u `mainasset=true` of `mainasset=false`. Er zijn geen eigenschappen meer.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Zij ondersteunt facetextractie en voorziet in twee emmers voor hoofd- en subactiva.

#### Eigenschappen {#properties-9}

* **`mainasset`** - Booleaans, `true` voor de hoofdactiva, `false` voor subactiva

### lidOf {#memberof}

Dit voorspelt vindt punten die lid van een specifiek zijn [slingerbronverzameling](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html).

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-10}

* **`memberOf`** - pad naar verzamelen van bronnen voor verkoop

### nodenaam {#nodename}

Deze voorspelling komt overeen met de namen van JCR-knooppunten.

Deze functie ondersteunt facetextractie en biedt emmers voor elke unieke knooppuntnaam (bestandsnaam).

#### Eigenschappen {#properties-11}

* **`nodename`** - Naampatroon van knooppunt waarbij jokertekens zijn toegestaan: `*` = een of geen teken, `?` = een teken, `[abc]` = alleen tekens tussen haakjes

### notexpired {#notexpired}

Dit voorspelt gelijken punten door te controleren als een JCR datumbezit groter of gelijk is dan de huidige servertijd. Het kan worden gebruikt om een `expiresAt` waarde en beperkt de resultaten tot alleen die waarden die nog niet zijn verlopen (`notexpired=true`) of die al zijn verlopen (`notexpired=false`).

Filteren wordt niet ondersteund.

Het ondersteunt facetextractie op dezelfde manier als [`daterange`](#daterange) voorspellen.

#### Eigenschappen {#properties-12}

* **`notexpired`** - Booleaans, `true` nog niet verstreken (datum in de toekomst of gelijk aan), `false` voor verlopen (datum in het verleden) (vereist)
* **`property`** - relatief pad naar de `DATE` te controleren eigenschap (vereist)

### pad {#path}

Dit voorspelt onderzoeken binnen een bepaalde weg.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-14}

* **`path`** - Definieert het padpatroon.
   * Afhankelijk van de `exact` eigenschap, de volledige subboomstructuur komt overeen (zoals bij het toevoegen) `//*` in xpath, maar merk op dat het het basispad niet bevat), of dat alleen een exact pad overeenkomt, wat jokertekens kan bevatten (`*`).
      * Standaardwaarden: `true`.
&lt;!— * Als de `self`eigenschap is ingesteld, wordt de volledige substructuur, inclusief het basisknooppunt, doorzocht.—>
* **`exact`** - als `exact` is `true`, moet het exacte pad overeenkomen, maar het kan eenvoudige jokertekens bevatten (`*`), die gelijke namen, maar niet `/`; als het `false` (standaard) alle afstammingen worden opgenomen (optioneel).
* **`flat`** - alleen de directe kinderen doorzoekt (zoals toevoegen) `/*` in xpath) (alleen gebruikt als `exact` is niet waar (optioneel).
* **`self`** - zoekt in de substructuur, maar neemt het basisknooppunt op dat als pad is opgegeven (geen jokertekens).
   * *Belangrijke opmerking*: Er is een probleem geïdentificeerd met `self` bezit in de huidige implementatie van vraagbouwer en het gebruiken van het in vragen kan correcte onderzoeksresultaten niet veroorzaken. De huidige implementatie van `self` eigenschap is ook niet haalbaar omdat hierdoor de bestaande toepassingen die erop vertrouwen, kunnen worden verbroken. Vanwege deze functionaliteit, `self` eigenschap is nu afgekeurd ; het wordt aangeraden dit te vermijden .

### eigenschap {#property}

Dit voorspelt overeenkomsten op eigenschappen JCR en hun waarden.

Het steunt facetextractie en verstrekt emmers voor elke unieke bezitswaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **`property`** - relatief pad naar eigenschap, bijvoorbeeld `jcr:title`.
* **`value`** - waarde waarop eigenschap moet worden gecontroleerd; volgt het eigenschapstype JCR op tekenreeksconversies.
* **`N_value`** - gebruik `1_value`, `2_value`, ... om te controleren op meerdere waarden (gecombineerd met `OR` standaard, met `AND` indien `and=true`).
* **`and`** - ingesteld op `true` voor het combineren van meerdere waarden (`N_value`) met `AND`
* **`operation`**
   * `equals` voor exacte overeenkomst (standaard).
   * `unequals` voor ongelijkheidsvergelijking.
   * `like` voor het gebruik van de `jcr:like` xpath, functie (optioneel).
   * `not` voor geen overeenkomst (bijvoorbeeld `not(@prop)` in xpath, value param wordt genegeerd).
   * `exists` voor controle op het bestaan.
      * `true` de eigenschap moet bestaan.
      * `false` is gelijk aan `not` en is de standaardwaarde.
* **`depth`** - aantal jokertekenniveaus waaronder de eigenschap/het relatieve pad kan bestaan (bijvoorbeeld `property=size depth=2` controles `node/size`, `node/*/size`, en `node/*/*/size`).

### rangeproperty {#rangeproperty}

Deze voorspelling past een bezit JCR aan een interval aan. Het is van toepassing op eigenschappen met lineaire typen, zoals `LONG`, `DOUBLE`, en `DECIMAL`. Voor `DATE`, zie de [`daterange`](#daterange) voorspellen die geoptimaliseerde invoer voor datumnotatie heeft.

U kunt een ondergrens, een bovengrens of beide definiëren. De bewerking (bijvoorbeeld kleiner dan of kleiner dan of gelijk aan) kan ook afzonderlijk worden opgegeven voor de onderste en bovenste binding.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-16}

* **`property`** - relatief pad naar eigenschap
* **`lowerBound`** - onderaan gebonden om eigenschap te controleren
* **`lowerOperation`** - `>` (standaardwaarde) of `>=`is van toepassing op de `lowerValue`
* **`upperBound`** - bovenaan gebonden om eigenschap te controleren
* **`upperOperation`** - `<` (standaardwaarde) of `<=`is van toepassing op de `lowerValue`
* **`decimal`** - `true` als de gecontroleerde eigenschap van het type Decimaal is

### relativedaterange {#relativedaterange}

Deze voorspelling komt overeen `JCR DATE` eigenschappen op basis van een datum-/tijdinterval waarbij tijdverschuivingen ten opzichte van de huidige servertijd worden gebruikt. U kunt `lowerBound` en `upperBound` met een millisecondenwaarde of de Bugzilla-syntaxis `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met `-` om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound`de andere standaard: `0`, die de huidige tijd vertegenwoordigt.

Bijvoorbeeld:

* `upperBound=1h` (en `lowerBound`) selecteert alles in het volgende uur
* `lowerBound=-1d` (en `upperBound`) selecteert alles in de afgelopen 24 uur
* `lowerBound=-6M` en `upperBound=-3M` selecteert alles in de laatste 3 tot 6 maanden
* `lowerBound=-1500` en `upperBound=5500` selecteert alles tussen 1500 milliseconden oud en 5500 milliseconden in de toekomst
* `lowerBound=1d` en `upperBound=2d` selecteert om het even wat overmorgen

Het neemt schrikkeljaren niet in overweging en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Het ondersteunt facetextractie op dezelfde manier als [`daterange`](#daterange) voorspellen.

#### Eigenschappen {#properties-17}

* **`upperBound`** - bovenste datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik `-` voor negatieve verschuiving
* **`lowerBound`** - lagere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik `-` voor negatieve verschuiving

### opgeslagen query {#savedquery}

Dit predikaat omvat alle predikaten van een voortgezette vraag van de Bouwer van de Vraag in de huidige vraag aangezien een subgroup predikaat.

Er wordt geen extra query uitgevoerd, maar de huidige query wordt uitgebreid.

De vragen kunnen programmatically worden voortgeduurd gebruikend `QueryBuilder#storeQuery()`. De notatie kan uit meerdere regels bestaan `String` eigenschap of een `nt:file` knooppunt dat de query als een tekstbestand in Java™-eigenschappenindeling bevat.

Het steunt facetextractie voor de predikaten van de bewaarde vraag niet.

#### Eigenschappen {#properties-19}

* **`savedquery`** - pad naar de opgeslagen query (`String` eigendom of `nt:file` node)

### gelijkaardig {#similar}

Deze voorspelling is een zoekopdracht op basis van gelijkenis met JCR XPath `rep:similar()`.

Filteren wordt niet ondersteund en het ophalen van facetten wordt niet ondersteund.

#### Eigenschappen {#properties-20}

* **`similar`** - absoluut pad naar het knooppunt waarvoor vergelijkbare knooppunten moeten worden gevonden
* **`local`** - een relatief pad naar een afstammend knooppunt of `.` voor het huidige knooppunt (optioneel, standaard is `.`)

### tag {#tag}

Op deze manier kunt u zoeken naar inhoud die is gelabeld met een of meer tags door titelpaden voor tags op te geven.

Deze biedt ondersteuning voor het extraheren van facetten en biedt emmers voor elke unieke tag, waarbij het huidige pad voor de tagtitel wordt gebruikt.

#### Eigenschappen {#properties-21}

* **`tag`** - het pad naar de codetitel, bijvoorbeeld `properties:orientation/landscape`
* **`N_value`** - gebruik `1_value`, `2_value`, ... om te controleren op meerdere tags (gecombineerd met `OR` standaard, met `AND` indien `and=true`)
* **`property`** - eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard `cq:tags`)

### gelabeld {#tagid}

Op deze manier kunt u zoeken naar inhoud die is gelabeld met een of meer tags, door tags-id&#39;s op te geven.

De tag ondersteunt facetextractie en biedt emmers voor elke unieke tag, waarbij de huidige tag-id wordt gebruikt.

#### Eigenschappen {#properties-22}

* **`tagid`** - tag-id om bijvoorbeeld naar te zoeken `properties:orientation/landscape`
* **`N_value`** - gebruik `1_value`, `2_value`, ... om te controleren op meerdere tag-id&#39;s (gecombineerd met `OR` standaard, met `AND` indien `and=true`)
* **`property`** - eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard `cq:tags`)

### tagzoeken {#tagsearch}

Op deze manier kunt u zoeken naar inhoud die is gecodeerd met een of meer tags door trefwoorden op te geven. Het zoekt eerst naar tags die deze trefwoorden bevatten in hun titels en beperkt het resultaat vervolgens tot alleen items die met deze trefwoorden zijn getagd.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#Properties-1}

* **`tagsearch`** - trefwoord dat moet worden gezocht in titels van tags
* **`property`** - eigenschap (of relatief pad naar eigenschap) die in overweging moet worden genomen (standaard `cq:tags`)
* **`lang`** - alleen in een bepaalde gelokaliseerde tagtitel zoeken (bijvoorbeeld `de`)
* **`all`** - Booleaanse waarde voor het doorzoeken van volledige labeltekst, dus alle titels, beschrijvingen enzovoort (heeft voorrang op `lang`)

### type {#type}

Dit voorspel beperkt resultaten tot een specifiek JCR knooptype, zowel primaire knooptypes als `mixin` typen. Het vindt ook subtypes van dat knooptype. In de zoekindexen van de opslagplaats moeten de knooppunttypen worden opgenomen voor een efficiënte uitvoering.

Het steunt facetextractie en verstrekt emmers voor elk uniek type in de resultaten.

#### Eigenschappen {#Properties-2}

* **`type`** - knooppunttype of `mixin` naam waarnaar moet worden gezocht, bijvoorbeeld `cq:Page`
