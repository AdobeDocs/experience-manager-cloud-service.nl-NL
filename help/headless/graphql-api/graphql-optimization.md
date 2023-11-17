---
title: GraphQL-query's optimaliseren
description: Leer hoe u uw GraphQL-query's kunt optimaliseren tijdens het filteren, pagineren en sorteren van uw Content Fragments in Adobe Experience Manager as a Cloud Service voor levering van inhoud zonder kop.
exl-id: 67aec373-4e1c-4afb-9c3f-a70e463118de
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 0%

---

# GraphQL-query&#39;s optimaliseren {#optimizing-graphql-queries}

>[!NOTE]
>
>Overweeg voordat u deze optimaliseringsaanbevelingen toepast [Inhoudsfragmenten bijwerken voor pagineren en sorteren in GraphQL-filters](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md) voor de beste prestaties.

Deze richtlijnen zijn bedoeld om prestatieproblemen met uw GraphQL-query&#39;s te voorkomen.

## GraphQL Checklist {#graphql-checklist}

De volgende controlelijst is bedoeld om u te helpen de configuratie en het gebruik van GraphQL in as a Cloud Service Adobe Experience Manager (AEM) te optimaliseren.

### Eerste beginselen {#first-principles}

#### Gebruik doorlopende GraphQL-query&#39;s {#use-persisted-graphql-queries}

**Aanbeveling**

Het gebruik van doorlopende GraphQL-query&#39;s wordt sterk aanbevolen.

Blijvende GraphQL-query&#39;s helpen de prestaties van de query te verminderen door gebruik te maken van CDN (Content Delivery Network). Clienttoepassingen hebben doorlopende query&#39;s aangevraagd met GET-aanvragen voor snelle uitvoering met randfunctionaliteit.

**Verdere verwijzing**

Zie:

* [Blijvende GraphQL-query&#39;s](/help/headless/graphql-api/persisted-queries.md).
* [GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s](/help/headless/graphql-api/sample-queries.md)

### Cachestrategie {#cache-strategy}

Verschillende methoden voor het in cache plaatsen kunnen ook worden gebruikt voor optimalisatie.

#### Opslaan in cache AEM Dispatcher inschakelen {#enable-aem-dispatcher-caching}

**Aanbeveling**

[AEM Dispatcher](/help/implementing/dispatcher/overview.md) is het eerste niveaugeheime voorgeheugen binnen de AEM dienst, vóór CDN geheime voorgeheugen.

**Verdere verwijzing**

Zie:

* [GraphQL Persisted Queries - caching inschakelen in Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Een CDN (Content Delivery Network) gebruiken {#use-cdn}

**Aanbeveling**

GraphQL-query&#39;s en hun JSON-antwoorden kunnen in de cache worden geplaatst als ze worden toegewezen aan `GET` vraagt wanneer het gebruiken van een CDN. Aanvragen zonder cache kunnen daarentegen zeer (bron)duur zijn en traag verlopen, met mogelijk verdere nadelige gevolgen voor de middelen van de oorsprong.

**Verdere verwijzing**

Zie:

* [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### HTTP-cachebeheerkoppen instellen {#set-http-cache-control-headers}

**Aanbeveling**

Wanneer het gebruiken van voortgeduurde vragen van GraphQL met een CDN, wordt het geadviseerd om aangewezen HTTP- geheim voorgeheugencontrolekopballen te plaatsen.

Elke voortgezette vraag kan zijn eigen specifieke reeks kopballen van de geheim voorgeheugencontrole hebben. De koppen kunnen worden ingesteld op de [GRAPHQL API](/help/headless/graphql-api/content-fragments.md) of de [AEM GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md).

**Verdere verwijzing**

Zie:

* [Door uw doorlopende query&#39;s in cache te plaatsen](/help/headless/graphql-api/persisted-queries.md#caching-persisted-queries)
* [Het beheren van geheime voorgeheugen voor uw persistente vragen](/help/headless/graphql-api/graphiql-ide.md#managing-cache)

#### GraphQL-voorcaching gebruiken AEM {#use-aem-graphql-pre-caching}

**Aanbeveling**

Dankzij deze mogelijkheid kan AEM inhoud binnen het bereik van GraphQL-query&#39;s verder in cache plaatsen die vervolgens als blokken in JSON-uitvoer kan worden geassembleerd in plaats van regel voor regel.

**Verdere verwijzing**

Neem contact op met de Adobe om deze mogelijkheid in te schakelen voor uw AEM Cloud Service-programma en -omgevingen.

### GraphQL Query-optimalisatie {#graphql-query-optimization}

Op een AEM instantie met een hoog aantal Inhoudsfragmenten die hetzelfde model delen, kunnen vragen in de GraphQL-lijst kostbaar worden (in termen van bronnen).

Dit komt omdat *alles* fragmenten die een model delen dat wordt gebruikt binnen de GraphQL-query, moeten in het geheugen worden geladen. Dit verbruikt zowel tijd als geheugen. Filteren, waardoor het aantal items in de (uiteindelijke) resultatenset kan worden verminderd, kan alleen worden toegepast **na** het laden van de volledige resultaatset in het geheugen.

Dit kan de indruk wekken dat zelfs kleine resultaatsets (kunnen) tot slechte prestaties leiden. In werkelijkheid wordt de vertraging echter veroorzaakt door de grootte van de oorspronkelijke resultaatset, aangezien deze intern moet worden afgehandeld voordat filters kunnen worden toegepast.

Om de prestaties en het geheugen te verminderen, moet deze aanvankelijke resultaatreeks zo klein mogelijk worden gehouden.

AEM biedt twee manieren om GraphQL-query&#39;s te optimaliseren:

* [Hybride filtering](#use-aem-graphql-hybrid-filtering)
* [Paginering](#use-aem-graphql-pagination) (of paginering)

   * [Sorteren](#use-graphql-sorting) heeft niet rechtstreeks betrekking op optimalisatie, maar heeft wel betrekking op paginering

Elke benadering heeft zijn eigen gebruiksgevallen en beperkingen. In deze sectie vindt u informatie over het filteren en pagineren van hybride foto&#39;s, samen met enkele van de [best practices](#best-practices) voor gebruik bij het optimaliseren van GraphQL-query&#39;s.

#### Hybride filters AEM GraphQL gebruiken {#use-aem-graphql-hybrid-filtering}

**Aanbeveling**

Bij hybride filters wordt JCR-filtering gecombineerd met AEM filtering.

Het past een filter JCR (in de vorm van een vraagbeperking) toe alvorens het resultaat te laden dat in geheugen voor AEM het filtreren wordt geplaatst. Hierdoor wordt de in het geheugen geladen resultatenset verminderd, aangezien het JCR-filter overbodige resultaten verwijdert.

>[!NOTE]
>
>Om technische redenen (bijvoorbeeld flexibiliteit, nesten van fragmenten), kan AEM niet het volledige filtreren aan JCR delegeren.

Met deze techniek blijft de flexibiliteit behouden die GraphQL-filters bieden, terwijl tegelijkertijd zoveel mogelijk filters worden gedelegeerd aan JCR.

>[!NOTE]
>
>AEM voor hybride filters moeten bestaande inhoudsfragmenten worden bijgewerkt

**Verdere verwijzing**

Zie:

* [Inhoudsfragmenten bijwerken voor pagineren en sorteren in GraphQL-filters](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md)
* [Voorbeeldquery met filtering op _tags-id en exclusief variaties](/help/headless/graphql-api/sample-queries.md#sample-filtering-tag-not-variations)

#### GraphQL-paginering gebruiken {#use-aem-graphql-pagination}

**Aanbeveling**

De reactietijd van complexe vragen, met grote resultaatreeksen, kan worden verbeterd door reacties in brokken te segmenteren gebruikend paginering, een norm van GraphQL.

GraphQL in AEM biedt ondersteuning voor twee typen paginering:

* [paginering op basis van limiet/verschuiving](/help/headless/graphql-api/content-fragments.md#list-offset-limit)
Dit wordt gebruikt voor lijstvragen; deze eindigen met `List`; bijvoorbeeld `articleList`.
Als u dit wilt gebruiken, moet u de positie opgeven van het eerste item dat moet worden geretourneerd (de `offset`) en het aantal objecten dat moet worden geretourneerd (de `limit`, of paginaformaat).

* [cursorpaginering](/help/headless/graphql-api/content-fragments.md#paginated-first-after) (vertegenwoordiger `first`en `after`) Dit verstrekt een unieke identiteitskaart voor elk punt; ook gekend als curseur.
In de vraag, specificeert u de curseur van het laatste punt van de vorige pagina, plus de paginagrootte (het maximumaantal punten dat moet worden teruggekeerd).

  Aangezien op curseur-gebaseerde paginering niet binnen de gegevensstructuren van op lijst-gebaseerde vragen past, heeft AEM geïntroduceerd `Paginated` type query; bijvoorbeeld `articlePaginated`. De gebruikte gegevensstructuren en parameters volgen [GraphQL Cursor ConnectionSpecification](https://relay.dev/graphql/connections.htm).

  >[!NOTE]
  >
  >AEM biedt momenteel ondersteuning voor doorsturen van paginering (met `after`/`first` parameters).
  >
  >Achterwaartse paginering (gebruiken `before`/`last` parameters) wordt niet ondersteund.

**Verdere verwijzing**

Zie:

* [Voorbeeld van pagineringsquery met eerste en volgende](/help/headless/graphql-api/sample-queries.md#sample-pagination-first-after)

#### GraphQL-sortering gebruiken {#use-graphql-sorting}

**Aanbeveling**

Bij het sorteren is ook een GraphQL-standaard waarmee clients JSON-inhoud in gesorteerde volgorde kunnen ontvangen. Dit kan de behoefte aan verdere verwerking op de cliënt verminderen.

Sorteren kan alleen efficiënt zijn als alle sorteercriteria betrekking hebben op fragmenten op het hoogste niveau.

Als de sorteervolgorde een of meer velden bevat die zich op een genest fragment bevinden, moeten alle fragmenten die het model op hoofdniveau delen, in het geheugen worden geladen. Dit heeft een negatieve invloed op de prestaties.

>[!NOTE]
>
>Sorteren op velden op het hoogste niveau heeft ook een (zij het kleine) invloed op de prestaties.

**Verdere verwijzing**

Zie:

* [Voorbeeldquery met filtering op _tags-id en exclusief variaties, en sorteren op naam](/help/headless/graphql-api/sample-queries.md#sample-filtering-tag-not-variations)

## Best practices voor {#best-practices}

Het belangrijkste doel van alle optimaliseringsaanbevelingen is het verminderen van de aanvankelijke resultaatreeks. De hier vermelde beste praktijken verstrekken manieren om dit te doen. Zij kunnen (en moeten) worden gecombineerd.

### Alleen op eigenschappen op hoofdniveau filteren {#filter-top-level-properties-only}

Filteren op JCR-niveau werkt momenteel alleen voor fragmenten op hoofdniveau.

Als een filter de velden van een genest fragment aanpakt, moet AEM terugvallen naar het laden (in geheugen) van alle fragmenten die het onderliggende model delen.

U kunt dergelijke GraphQL-query&#39;s nog steeds optimaliseren door filterexpressies te combineren op velden van fragmenten op het hoogste niveau en op velden van geneste fragmenten met de opdracht [AND, operator](#logical-operations-in-filter-expressions).

### De inhoudsstructuur gebruiken {#use-content-structure}

In AEM wordt het over het algemeen als een goede praktijk beschouwd om de gegevensopslagstructuur te gebruiken om het bereik van de te verwerken inhoud te beperken.

Deze aanpak moet ook worden toegepast op GraphQL-query&#39;s.

Dit kan door een filter op toe te passen `_path` veld van het fragment op hoofdniveau:

```graphql
{
  someList(filter: {
    _path: {
      _expressions: [ 
        {
          value: "/content/dam/some/sub/path/",
          _operator: STARTS_WITH
        }
      ]
    }
  }) {
    items {
      # ...
    }
  }
}
```

>[!NOTE]
>
>De navolgende `/` op `value` is vereist om de beste prestaties te behalen.

### Paginering gebruiken {#use-paging}

U kunt ook paginering gebruiken om de oorspronkelijke resultaatset te reduceren, vooral als uw aanvragen geen filters en sortering gebruiken.

Als u filtert of sorteert op geneste fragmenten, kunnen gepagineerde query&#39;s nog steeds traag zijn, omdat AEM mogelijk grotere hoeveelheden fragmenten in het geheugen moet laden. Daarom als u het filtreren en het pagineren combineert, overweeg de regels voor het filtreren (zoals hierboven vermeld).

Voor pagineren is sorteren even belangrijk, omdat gepagineerde resultaten altijd worden gesorteerd - expliciet of impliciet.

Als u in de eerste plaats in slechts het terugwinnen van de eerste paar pagina&#39;s interesseert, is er geen significant verschil tussen het gebruiken van `...List` of `...Paginated` vragen. Als uw toepassing echter meer dan één of twee pagina&#39;s wil lezen, moet u rekening houden met de `...Paginated` query&#39;s uitvoeren, aangezien deze vooral beter presteren bij de latere pagina&#39;s.

### Logische bewerkingen in filterexpressies {#logical-operations-in-filter-expressions}

Als u filtert op geneste fragmenten, kunt u nog steeds JCR-filtering toepassen door een bijbehorend filter op te geven voor een veld op hoofdniveau dat wordt gecombineerd met het `AND` operator.

Een typisch gebruik-geval zou het werkingsgebied van de vraag moeten beperken gebruikend een filter op `_path` van het fragment op het hoogste niveau en filtert vervolgens op aanvullende velden op het hoogste niveau of op een genest fragment.

In dit geval worden de verschillende filterexpressies gecombineerd met `AND`. Het filter op `_path` kan de oorspronkelijke resultaatset effectief beperken. Alle andere filters in velden op het hoogste niveau kunnen helpen om de oorspronkelijke resultaatset ook te reduceren, mits deze worden gecombineerd met `AND`.

Filterexpressies gecombineerd met `OR` kan niet worden geoptimaliseerd als het om geneste fragmenten gaat. `OR` expressies kunnen alleen worden geoptimaliseerd als *nee* geneste fragmenten zijn hierbij betrokken.

### Filteren op tekstvelden met meerdere regels wordt vermeden {#avoid-filtering-multiline-textfields}

De velden van een tekstveld met meerdere regels (html, markdown, plaintext, json) kunnen niet worden gefilterd via een JCR-query, omdat de inhoud van deze velden direct moet worden berekend.

Als u nog steeds op een tekstveld met meerdere regels moet filteren, kunt u de grootte van de oorspronkelijke resultaatset beperken door extra filterexpressies toe te voegen en deze te combineren `AND`. Het bereik beperken door te filteren op de `_path` het terrein is ook een goede aanpak .

### Filteren op virtuele velden vermijden {#avoid-filtering-virtual-fields}

Virtuele velden (de meeste velden beginnen met `_`) worden berekend terwijl een GraphQL-query wordt uitgevoerd en vallen daarom buiten het bereik van op JCR gebaseerde filtering.

Een belangrijke uitzondering is de `_path` veld, dat effectief kan worden gebruikt om de grootte van de oorspronkelijke resultaatset te beperken - als de inhoud dienovereenkomstig is gestructureerd (zie [De inhoudsstructuur gebruiken](#use-content-structure)).

### Filteren: uitsluitingen {#filtering-exclusions}

Er zijn verschillende andere situaties waarin een filterexpressie niet op het JCR-niveau kan worden geëvalueerd (en daarom moet worden vermeden dat de beste prestaties worden bereikt):

* Filterexpressies op een `Float` waarde die de `_sensitiveness` filteroptie en waar `_sensitiveness` is ingesteld op een andere waarde dan `0.0` .

* Filterexpressies op een `String` waarde met behulp van de `_ignoreCase` filteroptie.

* Filteren op `null` waarden.

* Filters op arrays met `_apply: ALL_OR_EMPTY`.

* Filters op arrays met `_apply: INSTANCES`, `_instances: 0`.

* Filterexpressies met de `CONTAINS_NOT` operator.

* Filterexpressies op een `Calendar`, `Date` of `Time` waarde die de `NOT_AT` operator.

### Nesten van inhoudsfragmenten minimaliseren {#minimize-content-fragment-nesting}

Het nesten van Inhoudsfragmenten is een uitstekende manier om aangepaste inhoudsstructuren te modelleren. U kunt zelfs een fragment hebben met een genest fragment, dat een genest fragment bevat, dat ...heeft enzovoort.

Als u echter een structuur met te veel niveaus maakt, kunnen de verwerkingstijden voor een GraphQL-query toenemen, aangezien GraphQL de volledige hiërarchie van alle geneste Content Fragments moet doorlopen.

Diepe nesting kan ook negatieve gevolgen hebben voor het beheer van inhoud. Over het algemeen wordt aanbevolen het nesten van inhoudsfragmenten te beperken tot minder dan vijf of zes niveaus.

### Niet alle indelingen uitvoeren (tekstelementen met meerdere regels) {#do-not-output-all-formats}

AEM GraphQL tekst kan retourneren die is gemaakt in het dialoogvenster **[Tekst met meerdere regels](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** gegevenstype, in meerdere indelingen: RTF, Simple Text en Markdown.

Wanneer u alle drie de indelingen uitvoert, wordt de tekstuitvoer in JSON met een factor drie vergroot. Dat, in combinatie met over het algemeen grote resultaatreeksen van zeer brede vragen, zeer grote JSON reacties kan veroorzaken die daarom lang duurt om te berekenen. Het is beter om de uitvoer te beperken tot alleen de tekstindelingen die nodig zijn voor het renderen van de inhoud.

### Inhoudsfragmenten wijzigen {#modifying-content-fragments}

Wijzig slechts de Fragments van de Inhoud, en hun middelen, gebruikend AEM UI of APIs. Breng geen wijzigingen rechtstreeks aan in de tekenherkenning.

### Uw query&#39;s testen {#test-your-queries}

Het verwerken van GraphQL-query&#39;s is vergelijkbaar met het verwerken van zoekquery&#39;s en is aanzienlijk complexer dan eenvoudige API-aanvragen voor alle GET-inhoud.

Het zorgvuldig plannen, testen, en optimaliseren van uw vragen in een gecontroleerde niet productieomgeving is essentieel voor later succes wanneer gebruikt in productie.
