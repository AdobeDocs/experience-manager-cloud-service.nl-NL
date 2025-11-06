---
title: Voorlopige naslaggids voor Query Builder
description: Predicate reference for the Query Builder API in AEM as a Cloud Service.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
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
* **`p.guessTotal`** - aanbevolen: u kunt het volledige resultaattotaal niet berekenen, wat kostbaar kan zijn. Of een aantal die op het maximumtotaal om te tellen tot (bijvoorbeeld, 1000, een aantal wijst dat gebruikers genoeg terugkoppelt op de ruwe grootte en nauwkeurige aantallen voor kleinere resultaten). Of `true` om alleen tot het minimaal vereiste aantal `p.offset` + `p.limit` te tellen.
* **`p.excerpt`** - als de waarde is ingesteld op `true` , neemt u het volledige tekstfragment op in het resultaat.
* **`p.indexTag`** - als de reeks een optie van de indexmarkering in de vraag zal omvatten (zie {de Markering van de Index van de Optie van de 1} Vraag [).](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-option-index-tag)
* **`p.facetStrategy`** - als reeks aan `oak`, zal de Bouwer van de Vraag facetextractie aan Oak (zie [&#x200B; Facetten &#x200B;](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#facets)) afvaardigen.
* **`p.hits`** - (alleen voor het JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met deze standaardresultaten (uitbreidbaar via de service ResultHitWriter).
   * **`simple`** - minimale items zoals `path` , `title` , `lastmodified` en `excerpt` (indien ingesteld).
   * **`full`** - hiermee wordt JSON-rendering van het knooppunt weergegeven, waarbij `jcr:path` het pad van de hit aangeeft. Standaard worden alleen de directe eigenschappen van het knooppunt weergegeven. Neem een diepere structuur met `p.nodedepth=N` op, waarbij 0 de volledige, oneindige substructuur betekent. Voeg `p.acls=true` toe om de JCR-machtigingen van de huidige sessie voor het opgegeven resultaatitem op te nemen (toewijzingen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** - alleen de eigenschappen die zijn opgegeven in `p.properties` . Dit is een spatie gescheiden (gebruik `+` in URL&#39;s) lijst met relatieve paden. Als het relatieve pad een diepte `>1` heeft, worden deze eigenschappen weergegeven als onderliggende objecten. De speciale eigenschap `jcr:path` bevat het pad van de hit.

### groep {#group}

Met deze voorspelling kunnen geneste voorwaarden worden gemaakt. Groepen kunnen geneste groepen bevatten. Alles in een query voor Query Builder bevindt zich impliciet in een hoofdgroep, die ook parameters `p.or` en `p.not` kan hebben.

Hieronder ziet u een voorbeeld voor het afstemmen van een van de twee eigenschappen op een waarde:

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Conceptueel is dit `(1_property` OR `2_property)` .

Hieronder ziet u een voorbeeld voor geneste groepen:

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Zoekt naar de term **Beheer** binnen pagina&#39;s in `/content/wknd/ch/de` of in activa in `/content/dam/wknd`.

Conceptueel is het `fulltext AND ( (path AND type) OR (path AND type) )` . Zulke OF toetreedt behoefte goede indexen voor prestatiesredenen.

#### Eigenschappen {#properties-6}

* **`p.or`** - bij `true` hoeft slechts één voorspelling in de groep overeen te komen. Heeft als standaardwaarde `false` , wat betekent dat alles moet overeenkomen
* **`p.not`** - bij `true` wordt de groep genegeerd (standaardwaarde `false` )
* **`<predicate>`** - voegt geneste voorspellingen toe
* **`N_<predicate>`** - voegt meerdere geneste voorspellingen tegelijk toe, zoals `1_property, 2_property, ...`

### ordonneren {#orderby}

Op deze manier kunt u de resultaten sorteren. Als de volgorde door meerdere eigenschappen vereist is, moet deze voorspelling meerdere keren worden toegevoegd met behulp van het voorvoegsel number, zoals `1_orderby=first`, `2_oderby=second` .

#### Eigenschappen {#properties-13}

* **`orderby`** - JCR-eigenschapsnaam die wordt aangegeven door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title` , of een andere voorspelling in de query, bijvoorbeeld `2_property` , waarop moet worden gesorteerd
* **`sort`** - sorteerrichting, `desc` voor aflopend of `asc` voor oplopend (standaard)
* **`case`** - als de waarde is ingesteld op `ignore` , wordt het sorteren van hoofdletters en kleine letters ongevoelig. Dit betekent dat `a` voor `B` komt. Als de waarde leeg of weggelaten is, wordt het sorteren hoofdlettergevoelig. Dit betekent dat `B` voor `a` komt

## Voorspellen {#predicates}

### boolproperty {#boolproperty}

Dit voorspelt overeenkomsten op booleaanse eigenschappen JCR. Accepteert alleen de waarden `true` en `false` . Als de waarde `false` is, komt deze overeen als de eigenschap de waarde `false` heeft of als deze helemaal niet bestaat. Dit predikaat is nuttig om op booleaanse vlaggen te controleren die slechts wanneer toegelaten worden geplaatst.

De overgeërfde parameter `operation` heeft geen betekenis.

Deze voorspelling ondersteunt facetextractie en biedt emmers voor elke `true` - of `false` -waarde, maar alleen voor bestaande eigenschappen.

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

* **`property1`** - pad naar eigenschap first date
* **`property2`** - pad naar tweede-datumeigenschap
* **`operation`**
   * `=` voor exacte overeenkomst (standaardwaarde)
   * `!=` voor vergelijking van ongelijkheid
   * `>` voor `property1` groter dan `property2`
   * `>=` voor `property1` groter dan of gelijk aan `property2`

### daterange {#daterange}

Deze voorspelling stemt de JCR-datumeigenschappen af op een datum-/tijdinterval. Gebruikt ISO8601
notatie voor datums en tijden (`YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke vertegenwoordiging, zoals `YYYY-MM-DD` toe. U kunt de tijdstempel ook opgeven als POSIX-tijd.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Deze biedt ondersteuning voor het extraheren van facetten en biedt emmers `today` , `this week` , `this month` , `last 3 months` , `this year` , `last year` en `earlier than last year` .

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **`property`** - relatief pad naar een eigenschap `DATE` , bijvoorbeeld `jcr:lastModified`
* **`lowerBound`** - lagere datum is gebonden aan check-eigenschap voor, bijvoorbeeld, `2014-10-01`
* **`lowerOperation`** - `>` (nieuwer) of `>=` (hoger of hoger) is van toepassing op de `lowerBound` . De standaardwaarde is `>`
* **`upperBound`** - Bovengrens om de eigenschap te controleren voor, bijvoorbeeld, `2014-10-01T12:15:00`
* **`upperOperation`** - `<` (ouder) of `<=` (ouder of ouder) is van toepassing op `upperBound` . De standaardwaarde is `<`
* **`timeZone`** - ID van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

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

* **`fulltext`** - de zoektermen met volledige tekst
* **`relPath`** - het relatieve pad naar de eigenschap of het subknooppunt. Deze eigenschap is optioneel.

### hasPermission {#haspermission}

Dit voorspelt beperkt het resultaat tot punten waar de huidige zitting de gespecificeerde [&#x200B; voorrechten JCR &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) heeft.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **`hasPermission`** - alle door komma&#39;s gescheiden JCR-bevoegdheden die de huidige gebruikerssessie moet hebben voor het desbetreffende knooppunt. Bijvoorbeeld `jcr:write` , `jcr:modifyAccessControl`

### taal {#language}

Met deze voorspelling worden AEM-pagina&#39;s in een specifieke taal gevonden. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken. Deze eigenschap bevat vaak de taal of landinstelling in een sitestructuur op hoofdniveau.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het steunt facetextractie en verstrekt emmers voor elke unieke taalcode.

#### Eigenschappen {#properties-8}

* **`language`** - ISO-taalcode, bijvoorbeeld `de`

### hoofdmiddel {#mainasset}

Deze voorspelling controleert of een knooppunt een DAM-hoofdactief is en geen subactief. Het is eigenlijk elk knooppunt dat zich niet binnen een knooppunt sub assets bevindt. Er wordt niet gecontroleerd op het knooppunttype `dam:Asset` . Stel `mainasset=true` of `mainasset=false` in om deze voorspelling te gebruiken. Er zijn geen eigenschappen meer.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Zij ondersteunt facetextractie en voorziet in twee emmers voor hoofd- en subactiva.

#### Eigenschappen {#properties-9}

* **`mainasset`** - boolean, `true` voor hoofdelementen, `false` voor subelementen

### lidOf {#memberof}

Dit voorspelt vondsten punten die lid van een specifieke [&#x200B; sling middelinzameling &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) zijn.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-10}

* **`memberOf`** - pad van verzamelen van bronnen voor verschuiven

### nodenaam {#nodename}

Deze voorspelling komt overeen met de namen van JCR-knooppunten.

Deze functie ondersteunt facetextractie en biedt emmers voor elke unieke knooppuntnaam (bestandsnaam).

#### Eigenschappen {#properties-11}

* **`nodename`** - naampatroon van knooppunt dat jokertekens toestaat: `*` = een willekeurig teken of geen teken, `?` = een willekeurig teken, `[abc]` = alleen tekens tussen haakjes

### notexpired {#notexpired}

Dit voorspelt gelijken punten door te controleren als een JCR datumbezit groter of gelijk is dan de huidige servertijd. Het kan worden gebruikt om een `expiresAt` waarde te controleren en resultaten tot slechts die waarden te beperken die nog niet zijn verlopen (`notexpired=true`), of die reeds (`notexpired=false`) zijn verlopen.

Filteren wordt niet ondersteund.

Deze functie ondersteunt facetextractie op dezelfde manier als de [`daterange`](#daterange) predikaat.

#### Eigenschappen {#properties-12}

* **`notexpired`** - boolean, `true` for not yet expired (date in the future or equal), `false` for expired (date in the past) (required)
* **`property`** - relatief pad naar de eigenschap `DATE` die moet worden gecontroleerd (vereist)

### pad {#path}

Dit voorspelt onderzoeken binnen een bepaalde weg.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-14}

* **`path`** - Definieert het padpatroon.
   * Afhankelijk van de eigenschap `exact` komt de volledige substructuur overeen (zoals bij het toevoegen van `//*` in xpath, maar houd er rekening mee dat dit niet het basispad bevat), of wordt alleen een exact pad gevonden, dat jokertekens kan bevatten (`*`).
      * Wordt standaard ingesteld op `true` .
&lt;!—   * Als het `self` bezit wordt geplaatst, wordt de volledige subboom met inbegrip van de basisknoop gezocht.—>
* **`exact`** - als `exact` is `true` , moet het exacte pad overeenkomen, maar het kan eenvoudige jokertekens ( `*` ) bevatten, die identieke namen, maar niet `/` ; als het `false` (standaard) is, worden alle afstammingen opgenomen (optioneel).
* **`flat`** - hiermee wordt alleen gezocht naar de directe onderliggende elementen (zoals het toevoegen van `/*` in xpath) (alleen wordt gebruikt als `exact` niet true is, optioneel).
* **`self`** - hiermee wordt gezocht in de substructuur, maar wordt het basisknooppunt opgenomen dat als pad is opgegeven (geen jokertekens).
   * *Belangrijke Nota*: Een kwestie is geïdentificeerd met `self` bezit in de huidige implementatie van vraagbouwer en het gebruiken van het in vragen kan correcte onderzoeksresultaten niet veroorzaken. Het is ook niet mogelijk de huidige implementatie van de eigenschap `self` te wijzigen omdat hierdoor de bestaande toepassingen die erop vertrouwen, kunnen worden verbroken. Vanwege deze functionaliteit is de eigenschap `self` nu afgekeurd en wordt aangeraden dit te vermijden.

### eigenschap {#property}

Dit voorspelt overeenkomsten op eigenschappen JCR en hun waarden.

Het steunt facetextractie en verstrekt emmers voor elke unieke bezitswaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **`property`** - relatief pad naar eigenschap, bijvoorbeeld `jcr:title` .
* **`value`** - waarde waarop de eigenschap moet worden gecontroleerd; volgt het eigenschapstype JCR op tekenreeksconversies.
* **`N_value`** - gebruik `1_value` , `2_value` ... om te controleren op meerdere waarden (standaard gecombineerd met `OR` , met `AND` if `and=true` ).
* **`and`** - ingesteld op `true` voor het combineren van meerdere waarden ( `N_value` ) met `AND`
* **`operation`**
   * `equals` voor exacte overeenkomst (standaardwaarde).
   * `unequals` voor ongelijkheidsvergelijking.
   * `like` voor het gebruik van de functie `jcr:like` xpath (optioneel).
   * `not` voor geen overeenkomst (waardeparam wordt bijvoorbeeld genegeerd in `not(@prop)` in xpath).
   * `exists` voor existentiecontrole.
      * `true` de eigenschap moet bestaan.
      * `false` is hetzelfde als `not` en is de standaardinstelling.
* **`depth`** - aantal jokertekenniveaus waaronder de eigenschap/het relatieve pad kan bestaan (bijvoorbeeld `property=size depth=2` checks `node/size` , `node/*/size` en `node/*/*/size` ).

### rangeproperty {#rangeproperty}

Deze voorspelling past een bezit JCR aan een interval aan. Deze is van toepassing op eigenschappen met lineaire typen, zoals `LONG` , `DOUBLE` en `DECIMAL` . Zie voor `DATE` de [`daterange`](#daterange) -voorspelling die geoptimaliseerde invoer voor de datumnotatie heeft.

U kunt een ondergrens, een bovengrens of beide definiëren. De bewerking (bijvoorbeeld kleiner dan of kleiner dan of gelijk aan) kan ook afzonderlijk worden opgegeven voor de onderste en bovenste binding.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-16}

* **`property`** - relatief pad naar eigenschap
* **`lowerBound`** - ondergrens voor controle-eigenschap
* **`lowerOperation`** - `>` (standaardwaarde) of `>=` , is van toepassing op `lowerValue`
* **`upperBound`** - Bovengrens voor controle-eigenschap
* **`upperOperation`** - `<` (standaardwaarde) of `<=` , is van toepassing op `lowerValue`
* **`decimal`** - `true` als de gecontroleerde eigenschap van het type Decimaal is

### relativedaterange {#relativedaterange}

Deze voorspelling stemt `JCR DATE` -eigenschappen af op een datum-/tijdinterval waarbij tijdverschuivingen worden gebruikt ten opzichte van de huidige servertijd. U kunt `lowerBound` en `upperBound` opgeven met een millisecondenwaarde of de Bugzilla-syntaxis `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uur, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met `-` om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound` opgeeft, wordt de andere standaard ingesteld op `0` , die de huidige tijd vertegenwoordigt.

Bijvoorbeeld:

* `upperBound=1h` (en geen `lowerBound` ) selecteert iets in het volgende uur
* `lowerBound=-1d` (en geen `upperBound` ) selecteert iets in de afgelopen 24 uur
* `lowerBound=-6M` en `upperBound=-3M` selecteert iets in de laatste 3 tot 6 maanden
* `lowerBound=-1500` en `upperBound=5500` selecteert alles tussen 1500 milliseconden en 5500 milliseconden in de toekomst
* `lowerBound=1d` en `upperBound=2d` selecteert de dag na morgen iets

Het neemt schrikkeljaren niet in overweging en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Deze functie ondersteunt facetextractie op dezelfde manier als de [`daterange`](#daterange) predikaat.

#### Eigenschappen {#properties-17}

* **`upperBound`** - bovenste datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik `-` voor negatieve compensatie
* **`lowerBound`** - lagere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik `-` voor negatieve compensatie

### opgeslagen query {#savedquery}

Dit predikaat omvat alle predikaten van een voortgezette vraag van de Bouwer van de Vraag in de huidige vraag aangezien een subgroup predikaat.

Er wordt geen extra query uitgevoerd, maar de huidige query wordt uitgebreid.

Query&#39;s kunnen met programmacode worden voortgezet met `QueryBuilder#storeQuery()` . De indeling kan ofwel een eigenschap van meerdere regels `String` zijn, ofwel een knooppunt `nt:file` dat de query als een tekstbestand in de Java™-eigenschappenindeling bevat.

Het steunt facetextractie voor de predikaten van de bewaarde vraag niet.

#### Eigenschappen {#properties-19}

* **`savedquery`** - pad naar de opgeslagen query (`String` eigenschap of `nt:file` node)

### gelijkaardig {#similar}

Deze voorspelling is een zoekopdracht op basis van gelijkenis met JCR XPath `rep:similar()` .

Filteren wordt niet ondersteund en het ophalen van facetten wordt niet ondersteund.

#### Eigenschappen {#properties-20}

* **`similar`** - absoluut pad naar het knooppunt waarvoor vergelijkbare knooppunten moeten worden gevonden
* **`local`** - een relatief pad naar een afstammend knooppunt of `.` voor het huidige knooppunt (optioneel, standaard is de waarde `.` )

### tag {#tag}

Op deze manier kunt u zoeken naar inhoud die is gelabeld met een of meer tags door titelpaden voor tags op te geven.

Deze biedt ondersteuning voor het extraheren van facetten en biedt emmers voor elke unieke tag, waarbij het huidige pad voor de tagtitel wordt gebruikt.

#### Eigenschappen {#properties-21}

* **`tag`** - typ het titelpad van de tag om naar te zoeken, bijvoorbeeld `properties:orientation/landscape`
* **`N_value`** - gebruik `1_value` , `2_value` ... om te controleren op meerdere tags (standaard gecombineerd met `OR` , met `AND` if `and=true` )
* **`property`** - eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard `cq:tags`)

### gelabeld {#tagid}

Op deze manier kunt u zoeken naar inhoud die is gelabeld met een of meer tags, door tags-id&#39;s op te geven.

De tag ondersteunt facetextractie en biedt emmers voor elke unieke tag, waarbij de huidige tag-id wordt gebruikt.

#### Eigenschappen {#properties-22}

* **`tagid`** - tag-id die u wilt opzoeken, bijvoorbeeld `properties:orientation/landscape`
* **`N_value`** - gebruik `1_value` , `2_value` ... om te controleren op meerdere tag-id&#39;s (standaard gecombineerd met `OR` , met `AND` if `and=true` )
* **`property`** - eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard `cq:tags`)

### tagzoeken {#tagsearch}

Op deze manier kunt u zoeken naar inhoud die is gecodeerd met een of meer tags door trefwoorden op te geven. Het zoekt eerst naar tags die deze trefwoorden bevatten in hun titels en beperkt het resultaat vervolgens tot alleen items die met deze trefwoorden zijn getagd.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#Properties-1}

* **`tagsearch`** - trefwoord dat u wilt zoeken in titels van tags
* **`property`** - eigenschap (of relatief pad naar eigenschap) die moet worden overwogen (standaard `cq:tags` )
* **`lang`** - alleen in een bepaalde gelokaliseerde tagtitel zoeken (bijvoorbeeld `de` )
* **`all`** - Booleaanse waarde om volledige labeltekst te doorzoeken, dat wil zeggen alle titels, beschrijvingen enzovoort (heeft voorrang op `lang` )

### type {#type}

Dit voorspel beperkt resultaten tot een specifiek JCR knooptype, zowel primaire knooptypes als `mixin` types. Het vindt ook subtypes van dat knooptype. In de zoekindexen van de opslagplaats moeten de knooppunttypen worden opgenomen voor een efficiënte uitvoering.

Het steunt facetextractie en verstrekt emmers voor elk uniek type in de resultaten.

#### Eigenschappen {#Properties-2}

* **`type`** - nodetype of `mixin` naam om naar, bijvoorbeeld, te zoeken `cq:Page`
