---
title: Voorlopige naslaggids voor Query Builder
description: Predicate reference for the Query Builder API.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
source-git-commit: a446efacb91f1a620d227b9413761dd857089c96
workflow-type: tm+mt
source-wordcount: '2219'
ht-degree: 1%

---

# Predicate Reference {#query-builder-predicate-reference} van de Bouwer van de vraag

## Algemeen {#general}

### basis {#root}

Dit is de basisgroep voor voorspelling. Het steunt alle eigenschappen van een groep en staat het plaatsen van globale vraagparameters toe.

De naam &quot;wortel&quot;wordt nooit gebruikt in een vraag, het is impliciet.

#### Eigenschappen {#properties-18}

* **`p.offset`** - getal dat het begin van de resultatenpagina aangeeft, d.w.z. hoeveel items moeten worden overgeslagen
* **`p.limit`** - getal dat het paginaformaat aangeeft
* **`p.guessTotal`** - aanbevolen: niet het volledige resultaattotaal berekenen dat kostbaar kan zijn; hetzij een getal dat het maximale totaal aangeeft tot (bijvoorbeeld 1000, een getal dat gebruikers voldoende feedback geeft over de ruwe grootte en exacte getallen voor kleinere resultaten) of  `true` om alleen tot het noodzakelijke minimum te tellen  `p.offset` +  `p.limit`
* **`p.excerpt`** - indien ingesteld op  `true`, het volledige tekstfragment in het resultaat opnemen
* **`p.hits`** - (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met de volgende standaardtreffers (uitbreidbaar via de service ResultHitWriter):
   * **`simple`** - minimale objecten zoals  `path`,  `title`,  `lastmodified`,  `excerpt` (indien ingesteld)
   * **`full`** - JSON-rendering van het knooppunt met  `jcr:path` het pad van de hit: door gebrek enkel maakt een lijst van de directe eigenschappen van de knoop, omvat een diepere boom met  `p.nodedepth=N`, met 0 die de volledige, oneindige subboom betekenen; Voeg toe  `p.acls=true` om de toestemmingen van het JCR van de huidige zitting op het bepaalde resultaatpunt (afbeeldingen te omvatten:  `create` =  `add_node`,  `modify` =  `set_property`,  `delete` =  `remove`)
   * **`selective`** - alleen de eigenschappen die zijn opgegeven in,  `p.properties`dat wil zeggen een lijst met relatieve paden, gescheiden door spaties (gebruik  `+` in URL&#39;s); als het relatieve pad een diepte heeft, worden  `>1` deze weergegeven als onderliggende objecten; de speciale  `jcr:path` eigenschap bevat het pad van de hit

### groep {#group}

Met deze voorspelling kunnen geneste voorwaarden worden gemaakt. Groepen kunnen geneste groepen bevatten. Alles in een query van de Bouwer van de Vraag is impliciet in een wortelgroep, die `p.or` en `p.not` ook parameters kan hebben.

Hieronder ziet u een voorbeeld voor het afstemmen van een van de twee eigenschappen op een waarde:

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Dit is conceptueel `(1_property` OF `2_property)`.

Hieronder ziet u een voorbeeld voor geneste groepen:

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Hiermee wordt gezocht naar de term **Beheer** binnen pagina&#39;s in `/content/wknd/ch/de` of in elementen in `/content/dam/wknd`.

Dit is conceptueel `fulltext AND ( (path AND type) OR (path AND type) )`. Houd er rekening mee dat dergelijke OR-verbindingen goede indexen nodig hebben voor de prestaties.

#### Eigenschappen {#properties-6}

* **`p.or`** - bij een waarde  `true`moet slechts één voorspelling in de groep overeenkomen. Dit is standaard `false`, wat betekent dat alles moet overeenkomen
* **`p.not`** - indien ingesteld op  `true`, wordt de groep genegeerd (standaard ingesteld op  `false`)
* **`<predicate>`** - voegt geneste voorspellingen toe
* **`N_<predicate>`** - voegt meerdere geneste voorspellingen tegelijk toe, zoals  `1_property, 2_property, ...`

### ordonneren {#orderby}

Op deze manier kunt u de resultaten sorteren. Als het opdracht geven door veelvoudige eigenschappen wordt vereist, moet dit predikaat veelvoudige tijden worden toegevoegd gebruikend het aantalprefix, zoals `1_orderby=first`, `2_oderby=second`.

#### Eigenschappen {#properties-13}

* **`orderby`** - JCR-eigenschapsnaam die wordt aangegeven door een regelafstand @, bijvoorbeeld  `@jcr:lastModified` of  `@jcr:content/jcr:title`, of een andere voorspelling in de query, bijvoorbeeld  `2_property`waarop moet worden gesorteerd
* **`sort`** - sorteerrichting,  `desc` voor aflopend of  `asc` voor oplopend (standaard)
* **`case`** - indien het  `ignore` wordt ingesteld om het sorteren ongevoelig te maken, hetgeen  `a` eerder wordt bedoeld  `B`; als de waarde leeg of weggelaten is, is de sortering hoofdlettergevoelig, wat betekent dat de waarde  `B` eerder komt  `a`

## Voorspellen {#predicates}

### boolproperty {#boolproperty}

Dit voorspelt overeenkomsten op booleaanse eigenschappen JCR. Accepteert alleen de waarden `true` en `false`. In het geval van `false`, zal het aanpassen als het bezit de waarde `false` heeft of als het helemaal niet bestaat. Dit kan handig zijn om te controleren op Booleaanse markeringen die alleen zijn ingesteld wanneer deze zijn ingeschakeld.

De overgeërfde parameter `operation` heeft geen betekenis.

Deze voorspelling ondersteunt facetextractie en biedt emmers voor elke `true`- of `false`-waarde, maar alleen voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **`boolproperty`** - relatief pad naar eigenschap, bijvoorbeeld  `myFeatureEnabled` of  `jcr:content/myFeatureEnabled`
* **`value`** - de waarde waarop de eigenschap moet worden gecontroleerd,  `true` of  `false`

### contentfragment {#contentfragment}

Hierdoor wordt het resultaat beperkt tot inhoudsfragmenten.

* Filteren wordt niet ondersteund.
* Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-1}

* **`contentfragment`** - Het kan met om het even welke waarde worden gebruikt om op inhoudsfragmenten te controleren.

### `dateComparison` {#datecomparison}

In deze voorspelling worden twee JCR-datumeigenschappen met elkaar vergeleken. Kan testen of ze gelijk, ongelijk, groter dan of groter dan of gelijk zijn.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

#### Eigenschappen {#properties-2}

* **`property1`** - pad naar eerste-datumeigenschap
* **`property2`** - pad naar tweede-datumeigenschap
* **`operation`**
   * `=` voor exacte overeenkomst (standaard)
   * `!=` voor ongelijkheidsvergelijking
   * `>` voor  `property1` meer dan  `property2`
   * `>=` voor  `property1` groter dan of gelijk aan  `property2`

### daterange {#daterange}

Deze voorspelling stemt de JCR-datumeigenschappen af op een datum-/tijdinterval. Dit gebruikt ISO8601
formaat voor data en tijden (`YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke vertegenwoordiging, zoals `YYYY-MM-DD` toe. U kunt de tijdstempel ook opgeven als POSIX-tijd.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Deze biedt ondersteuning voor facetextractie en biedt emmers `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` en `earlier than last year`.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **`property`** - relatief pad naar een  `DATE` eigenschap, bijvoorbeeld  `jcr:lastModified`
* **`lowerBound`** - lagere datum gebonden aan controlebezit voor, bijvoorbeeld  `2014-10-01`
* **`lowerOperation`** -  `>` (nieuwer) of  `>=` (nieuwer of nieuwer) is van toepassing op de  `lowerBound`. De standaardwaarde is `>`
* **`upperBound`** - bovengrens voor het controleren van eigenschappen, bijvoorbeeld  `2014-10-01T12:15:00`
* **`upperOperation`** -  `<` (ouder) of  `<=` (ouder), van toepassing op de  `upperBound`. De standaardwaarde is `<`
* **`timeZone`** - Id van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

### exclusief paden {#excludepaths}

In deze voorspelling worden knooppunten uitgesloten van het resultaat wanneer hun pad overeenkomt met een reguliere expressie.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-4}

* **`excludepaths`** - reguliere expressie komt overeen met resultaatpaden, met uitzondering van overeenkomende paden uit het resultaat.

### fulltext {#fulltext}

Dit voorspelt onderzoeken naar termijnen in de fulltext index.

Filteren wordt niet ondersteund.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-5}

* **`fulltext`** - de fulltext zoekterm(en)
* **`relPath`** - het relatieve pad dat moet worden gezocht in de eigenschap of het subknooppunt. Deze eigenschap is optioneel.

### hasPermission {#haspermission}

In deze voorspelling wordt het resultaat beperkt tot items waarvoor de huidige sessie de opgegeven [JCR-bevoegdheden heeft.](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **`hasPermission`** - door komma&#39;s gescheiden JCR-bevoegdheden die de huidige gebruikerssessie ALLE moet hebben voor het desbetreffende knooppunt; bijvoorbeeld  `jcr:write`,  `jcr:modifyAccessControl`

### language {#language}

Dit voorspelt vindt AEM pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken, dat vaak de taal of landinstelling in een sitestructuur op hoofdniveau bevat.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Het steunt facetextractie en verstrekt emmers voor elke unieke taalcode.

#### Eigenschappen {#properties-8}

* **`language`** - ISO-taalcode, bijvoorbeeld  `de`

### hoofdmiddel {#mainasset}

Deze voorspelling controleert of een knooppunt een DAM-hoofdactief is en geen subactief. Dit is eigenlijk elk knooppunt dat zich niet binnen een knooppunt sub assets bevindt. Merk op dat dit niet het `dam:Asset` knooptype controleert. U kunt deze voorspelling gebruiken door `mainasset=true` of `mainasset=false` in te stellen. Er zijn geen eigenschappen meer.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Zij ondersteunt facetextractie en voorziet in twee emmers voor hoofd- en subactiva.

#### Eigenschappen {#properties-9}

* **`mainasset`** - booleaanse waarde,  `true` voor hoofdactiva,  `false` voor subactiva

### lidOf {#memberof}

Dit voorspelt vondsten punten die lid van een specifieke [sling middelinzameling](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/resource/collection/ResourceCollection.html) zijn.

Dit is een voorspelling die alleen kan worden gefilterd en kan geen zoekindex gebruiken.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-10}

* **`memberOf`** - pad naar verzamelen van bronnen voor verkoop

### nodenaam {#nodename}

Deze voorspelling komt overeen met de namen van JCR-knooppunten.

Deze functie ondersteunt facetextractie en biedt emmers voor elke unieke knooppuntnaam (bestandsnaam).

#### Eigenschappen {#properties-11}

* **`nodename`** - Naampatroon van knooppunt waarbij jokertekens zijn toegestaan:  `*` = een of geen teken,  `?` = een teken,  `[abc]` = alleen tekens tussen haakjes

### notexpired {#notexpired}

Dit voorspelt gelijken punten door te controleren als een JCR datumbezit groter of gelijk is dan de huidige servertijd. Dit kan worden gebruikt om een `expiresAt` waarde te controleren en resultaten te beperken tot slechts die die nog niet (`notexpired=true`) zijn verlopen of die reeds (`notexpired=false`) zijn verlopen.

Filteren wordt niet ondersteund.

Het steunt facetextractie op de zelfde manier zoals [`daterange`](#daterange) voorspelt.

#### Eigenschappen {#properties-12}

* **`notexpired`** - Booleaans,  `true` voor nog niet verstreken (datum in de toekomst of gelijk aan),  `false` voor verlopen (datum in het verleden) (vereist)
* **`property`** - relatief pad naar de te controleren  `DATE` eigenschap (vereist)

### path {#path}

Dit voorspelt onderzoeken binnen een bepaalde weg.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-14}

* **`path`** - Hiermee definieert u het padpatroon.
   * Afhankelijk van de eigenschap `exact` komt ofwel de volledige substructuur overeen (zoals het toevoegen van `//*` in xpath, maar let erop dat dit het basispad niet bevat) of alleen een exacte padovereenkomst, die jokertekens (`*`) kan bevatten.
      * Heeft als standaardwaarde `true`
   * Als de eigenschap `self`wordt ingesteld, wordt de gehele substructuur, inclusief het basisknooppunt, doorzocht.
* **`exact`** - als  `exact` dat  `true`is, moet het nauwkeurige weg aanpassen, maar het kan eenvoudige vervangingen (`*`) bevatten, die namen aanpassen, maar niet  `/`; als het  `false` (gebrek) is zijn alle nakomelingen inbegrepen (facultatief)
* **`flat`** - alleen de directe onderliggende items wordt gezocht (zoals  `/*` in xpath) (wordt alleen gebruikt als dit niet waar  `exact` is, optioneel)
* **`self`** - de substructuur doorzoekt, maar het basisknooppunt bevat dat als pad is opgegeven (geen jokertekens)

### eigenschap {#property}

Dit voorspelt overeenkomsten op eigenschappen JCR en hun waarden.

Het steunt facetextractie en verstrekt emmers voor elke unieke bezitswaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **`property`** - relatief pad naar eigenschap, bijvoorbeeld  `jcr:title`
* **`value`** - waarde waarop eigenschap moet worden gecontroleerd; volgt het JCR-eigenschapstype op tekenreeksconversies
* **`N_value`** - gebruik  `1_value`,  `2_value`... controleren op meerdere waarden (standaard gecombineerd met  `OR` , met  `AND` if  `and=true`)
* **`and`** - instellen op  `true` voor het combineren van meerdere waarden (`N_value`) met  `AND`
* **`operation`**
   * `equals` voor exacte overeenkomst (standaard)
   * `unequals` voor ongelijkheidsvergelijking
   * `like` voor gebruik van de functie  `jcr:like` xpath (optioneel)
   * `not` voor geen overeenkomst (bijvoorbeeld  `not(@prop)` in xpath, value param zal worden genegeerd)
   * `exists` Bestaande controle
      * `true` de eigenschap moet bestaan
      * `false` is gelijk aan  `not` en is de standaardwaarde
* **`depth`** - aantal jokertekenniveaus waaronder de eigenschap/het relatieve pad kan bestaan ( `property=size depth=2` wordt bijvoorbeeld gecontroleerd  `node/size`,  `node/*/size` en  `node/*/*/size`)

### rangeproperty {#rangeproperty}

Deze voorspelling past een bezit JCR aan een interval aan. Dit is van toepassing op eigenschappen met lineaire typen, zoals `LONG`, `DOUBLE` en `DECIMAL`. Voor `DATE` gelieve te zien [`daterange`](#daterange) voorspellen dat geoptimaliseerde gegeven van het datumformaat heeft.

U kunt een ondergrens, een bovengrens of beide definiëren. De bewerking (bijvoorbeeld kleiner dan of kleiner dan of gelijk aan) kan ook afzonderlijk worden opgegeven voor de ondergrens en de bovengrens.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-16}

* **`property`** - relatief pad naar eigenschap
* **`lowerBound`** - onderaan gebonden om eigenschap te controleren
* **`lowerOperation`** -  `>` (standaard) of  `>=`, van toepassing op de  `lowerValue`
* **`upperBound`** - bovenaan gebonden om eigenschap te controleren
* **`upperOperation`** -  `<` (standaard) of  `<=`, van toepassing op de  `lowerValue`
* **`decimal`** -  `true` als de gecontroleerde eigenschap van het type Decimaal is

### relativedaterange {#relativedaterange}

Deze voorspelling stemt `JCR DATE`-eigenschappen af op een datum-/tijdinterval waarbij tijdverschuivingen worden gebruikt ten opzichte van de huidige servertijd. U kunt `lowerBound` en `upperBound` specificeren gebruikend of een millisecondenwaarde of de syntaxis `1s 2m 3h 4d 5w 6M 7y` van Bugzilla (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar). Voorvoegsel met `-` om op een negatieve compensatie vóór de huidige tijd te wijzen. Als u alleen `lowerBound` of `upperBound` opgeeft, wordt de andere `0` standaard ingesteld als de huidige tijd.

Bijvoorbeeld:

* `upperBound=1h` (en geen  `lowerBound`) selecteert iets in het volgende uur
* `lowerBound=-1d` (en geen  `upperBound`) selecteert iets in de afgelopen 24 uur
* `lowerBound=-6M` en  `upperBound=-3M` selecteert in de laatste 3 tot 6 maanden
* `lowerBound=-1500` en  `upperBound=5500` selecteert u in de toekomst alles tussen 1500 milliseconden en 5500 milliseconden
* `lowerBound=1d` en  `upperBound=2d` selecteert de overdag om het even wat

Er wordt geen rekening gehouden met schrikkeljaren en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Het steunt facetextractie op de zelfde manier zoals [`daterange`](#daterange) voorspelt.

#### Eigenschappen {#properties-17}

* **`upperBound`** - bovenste datum gebonden in milliseconden of  `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik  `-` voor negatieve compensatie
* **`lowerBound`** - lagere datum gebonden in milliseconden of  `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik  `-` voor negatieve compensatie

### opgeslagen query {#savedquery}

Dit predikaat omvat alle predikaten van een voortgezette vraag van de Bouwer van de Vraag in de huidige vraag aangezien een subgroup predikaat.

Hiermee wordt geen extra query uitgevoerd, maar wordt de huidige query uitgebreid.

De vragen kunnen programmatically worden voortgeduurd gebruikend `QueryBuilder#storeQuery()`. De indeling kan een eigenschap `String` met meerdere regels of een `nt:file`-knooppunt zijn dat de query als een tekstbestand in de Java-eigenschappenindeling bevat.

Het steunt facetextractie voor de predikaten van de bewaarde vraag niet.

#### Eigenschappen {#properties-19}

* **`savedquery`** - pad naar de opgeslagen query (`String` eigenschap of  `nt:file` knooppunt)

### gelijkaardig {#similar}

Deze voorspelling is een zoekopdracht op basis van gelijkenis met de `rep:similar()` van JCR XPath.

Filteren wordt niet ondersteund en het ophalen van facetten wordt niet ondersteund.

#### Eigenschappen {#properties-20}

* **`similar`** - absoluut pad naar het knooppunt waarvoor vergelijkbare knooppunten moeten worden gevonden
* **`local`** - een relatief pad naar een afstammend knooppunt of  `.` voor het huidige knooppunt (optioneel, standaard is  `.`)

### tag {#tag}

Op deze manier kunt u zoeken naar inhoud die is gelabeld met een of meer tags door titelpaden voor tags op te geven.

Deze biedt ondersteuning voor het extraheren van facetten en biedt emmers voor elke unieke tag, waarbij het huidige pad voor de tagtitel wordt gebruikt.

#### Eigenschappen {#properties-21}

* **`tag`** - pad naar labeltitel, bijvoorbeeld  `properties:orientation/landscape`
* **`N_value`** - gebruik  `1_value`,  `2_value`... controleren op meerdere tags (standaard gecombineerd met  `OR` , met  `AND` als  `and=true`)
* **`property`** - eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard  `cq:tags`)

### tagid {#tagid}

Op deze manier kunt u zoeken naar inhoud die is gelabeld met een of meer tags, door tags-id&#39;s op te geven.

De tag ondersteunt facetextractie en biedt emmers voor elke unieke tag, waarbij de huidige tag-id wordt gebruikt.

#### Eigenschappen {#properties-22}

* **`tagid`** - tag-id, bijvoorbeeld  `properties:orientation/landscape`
* **`N_value`** - gebruik  `1_value`,  `2_value`... controleren op meerdere tag-id&#39;s (standaard gecombineerd met  `OR` , met  `AND` als  `and=true`)
* **`property`** - eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard  `cq:tags`)

### tagzoeken {#tagsearch}

Op deze manier kunt u zoeken naar inhoud die is gecodeerd met een of meer tags door trefwoorden op te geven. Hiermee zoekt u eerst naar tags met deze trefwoorden in de titels en beperkt u het resultaat vervolgens tot alleen items die met deze trefwoorden zijn getagd.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#Properties-1}

* **`tagsearch`** - trefwoord dat moet worden gezocht in titels van tags
* **`property`** - eigenschap (of relatief pad naar eigenschap) die moet worden overwogen (standaardwaarde  `cq:tags`)
* **`lang`** - alleen zoeken in een bepaalde gelokaliseerde tagtitel (bijvoorbeeld  `de`)
* **`all`** - Booleaanse waarde om volledige labeltekst te doorzoeken, d.w.z. alle titels, beschrijving enz. (heeft voorrang op `lang`)

### type {#type}

Dit voorspel beperkt resultaten tot een specifiek JCR knooptype, zowel primaire knooptypes als mixintypes. Dit zal ook subtypes van dat knooptype vinden. Merk op dat de gegevensopslagplaats onderzoeksindexen de knooppunttypes voor efficiënte uitvoering moeten behandelen.

Het steunt facetextractie en verstrekt emmers voor elk uniek type in de resultaten.

#### Eigenschappen {#Properties-2}

* **`type`** - knooppunttype of mixnaam om naar te zoeken, bijvoorbeeld  `cq:Page`
