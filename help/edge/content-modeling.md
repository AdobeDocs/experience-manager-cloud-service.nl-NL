---
title: Inhoud modelleren voor AEM ontwerpen met projecten voor Edge Delivery Services
description: Leer hoe het modelleren van inhoud voor AEM creatie met Edge Delivery Services projecten en hoe te om uw eigen inhoud te modelleren werkt.
source-git-commit: 8f3c7524ae8ee642a9aee5989e03e6584a664eba
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---


# Inhoud modelleren voor AEM ontwerpen met projecten voor Edge Delivery Services {#content-modeling}

Leer hoe het modelleren van inhoud voor AEM creatie met Edge Delivery Services projecten en hoe te om uw eigen inhoud te modelleren werkt.

{{aem-authoring-edge-early-access}}

## Vereisten {#prerequisites}

Projecten waarbij gebruik wordt gemaakt van AEM ontwerpen met Edge Delivery Services nemen het grootste deel van de mechanica van elk ander Edge Delivery Services-project over, onafhankelijk van de inhoudsbron of [ontwerpmethode.](/help/edge/authoring.md)

Voordat u begint met het modelleren van inhoud voor uw project, moet u eerst de volgende documentatie lezen.

* [Aan de slag - Zelfstudie voor ontwikkelaars](/help/edge/developer/tutorial.md)
* [Markeringen, secties, blokken en automatische blokkering](/help/edge/developer/markup-sections-blocks.md)
* [Blokverzameling](/help/edge/developer/block-collection.md)

Het is van essentieel belang dat u deze concepten begrijpt om te komen tot een aansprekend inhoudsmodel dat op een bronagnostische manier werkt. Dit document bevat details over de mechanismen die specifiek zijn geïmplementeerd voor AEM ontwerpen.

## Standaardinhoud {#default-content}

**Standaardinhoud** is inhoud die een auteur intuïtief op een pagina zou plaatsen zonder extra semantiek toe te voegen. Dit omvat tekst, koppen, koppelingen en afbeeldingen. Deze inhoud spreekt voor zich in zijn functie en doel.

In AEM, wordt deze inhoud uitgevoerd als componenten met zeer eenvoudige, vooraf bepaalde modellen, die alles omvatten die in Prijsvermindering en HTML kan in series worden vervaardigd.

* **Tekst**: RTF-tekst (inclusief lijstelementen en sterke of cursieve tekst)
* **Titel**: Tekst, type (h1-h6)
* **Afbeelding**: Bron, beschrijving
* **Knop**: Tekst, titel, url, type (standaard, primair, secundair)

Het model van deze componenten maakt deel uit van het [Boilerplate voor AEM Authoring met Edge Delivery Services.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112)

## Blokken {#blocks}

Blokken worden gebruikt om rijkere inhoud met specifieke stijlen en functionaliteit te maken. In tegenstelling tot de standaardinhoud, vereisen de blokken extra semantiek. Blokken kunnen worden vergeleken met [in de AEM paginaeditor.](/help/implementing/developing/components/overview.md)

Blokken zijn in wezen stukken inhoud die door JavaScript zijn versierd en die met een stijlpagina zijn opgemaakt.

### Blokmodeldefinitie {#model-definition}

Wanneer het gebruiken van AEM creatie met Edge Delivery Services, moet de inhoud van blokken uitdrukkelijk worden gemodelleerd om de auteur de interface te verstrekken om inhoud tot stand te brengen. In principe moet u een model maken, zodat de ontwerpgebruikersinterface weet welke opties op basis van het blok aan de auteur moeten worden voorgesteld.

De [`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) Het bestand definieert het model van blokken. De velden die in het componentmodel worden gedefinieerd, blijven behouden als eigenschappen in AEM en worden weergegeven als cellen in de tabel waaruit een blok bestaat.

```json
{
  "id": "hero",
  "fields": [
    {
      "component": "reference",
      "valueType": "string",
      "name": "image",
      "label": "Image",
      "multi": false
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "imageAlt",
      "label": "Alt",
      "value": ""
    },
    {
      "component": "text-area",
      "name": "text",
      "value": "",
      "label": "Text",
      "valueType": "string"
    }
  ]
}
```

Merk op dat niet elk blok een model moet hebben. Sommige blokken zijn gewoon [containers](#container) voor een lijst van kinderen, waarbij elk kind zijn eigen model heeft.

Het is ook nodig om te bepalen welke blokken bestaan en aan een pagina kunnen worden toegevoegd gebruikend de Universele Redacteur. De [`component-definitions.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) In dit bestand worden de componenten weergegeven zoals deze door de Universal Editor beschikbaar worden gesteld.

```json
{
  "title": "Hero",
  "id": "hero",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "Hero",
          "model": "hero"
        }
      }
    }
  }
}
```

Het is mogelijk om één model voor vele blokken te gebruiken. Sommige blokken kunnen bijvoorbeeld een model delen dat een tekst en afbeelding definieert.

Voor elk blok:

* Moet de `core/franklin/components/block/v1/block` middeltype, de generische implementatie van de bloklogica in AEM.
* U moet de bloknaam definiëren. Deze wordt weergegeven in de tabelkoptekst van het blok.
* Kan een [model-id.](/help/implementing/universal-editor/field-types.md#model-structure)
* Kan een [filter-id.](/help/implementing/universal-editor/customizing.md#filtering-components)

Al deze informatie wordt opgeslagen in AEM wanneer een blok aan een pagina wordt toegevoegd.

>[!WARNING]
>
>Hoewel mogelijk, is het niet noodzakelijk om de componenten van de douane AEM uit te voeren. De door AEM geleverde onderdelen voor Edge Delivery Services zijn voldoende en bieden bepaalde relingen om de ontwikkeling te vergemakkelijken.
>
>Om deze reden, adviseert de Adobe niet gebruikend douane AEM middeltypes.

### Blokstructuur {#block-structure}

De eigenschappen van blokken zijn [gedefinieerd in de componentmodellen](#model-definition) en blijft als zodanig in AEM. Eigenschappen worden als cellen gerenderd in de tabelachtige structuur van het blok.

#### Eenvoudige blokken {#simple}

In de eenvoudigste vorm geeft een blok elke eigenschap weer in één rij/kolom in de volgorde waarin de eigenschappen in het model zijn gedefinieerd.

In het volgende voorbeeld wordt de afbeelding eerst in het model gedefinieerd en vervolgens de tekst. Ze worden dus eerst met de afbeelding en vervolgens met de tekst gerenderd.

##### Gegevens {#data-simple}

```json
{
  "name": "Hero",
  "model": "hero",
  "image": "/content/dam/image.png",
  "imageAlt": "Helix - a shape like a corkscrew",
  "text": "<h1>Welcome to AEM</h1>"
}
```

##### Opmaak {#markup-simple}

```html
<div class="hero">
  <div>
    <div>
      <picture>
        <img src="/content/dam/image.png" alt="Helix - a shape like a corkscrew">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <h1>Welcome to AEM</h1>
    </div>
  </div>
</div>
```

Het kan opvallen dat bepaalde typen waarden het afleiden van semantiek in de opmaak toestaan en dat eigenschappen in één cel worden gecombineerd. Dit gedrag wordt beschreven in de sectie [Type-gevolgtrekking.](#type-inference)

#### Key-Value-blok {#key-value}

In veel gevallen is het raadzaam de gerenderde semantische opmaakcode te decoreren, CSS-klassennamen toe te voegen, nieuwe knooppunten toe te voegen of deze in de DOM te verplaatsen en stijlen toe te passen.

In andere gevallen echter, wordt het blok gelezen als sleutel-waarde paar-als configuratie.

Een voorbeeld hiervan is het [metagegevens van de sectie.](/help/edge/developer/markup-sections-blocks.md#sections) In dit gebruiksgeval, kan het blok worden gevormd om als sleutel-waarde paarlijst terug te geven. Zie de sectie [Secties en sectiemetagegevens](#sections-metadata) voor meer informatie .

##### Gegevens {#data-key-value}

```json
{
  "name": "Featured Articles",
  "model": "spreadsheet-input",
  "key-value": true,
  "source": "/content/site/articles.json",
  "keywords": ['Developer','Courses'],
  "limit": 4
}
```

##### Opmaak {#markup-key-value}

```html
<div class="featured-articles">
  <div>
    <div>source</div>
    <div><a href="/content/site/articles.json">/content/site/articles.json</a></div>
  </div>
  <div>
    <div>keywords</div>
    <div>Developer,Courses</div>
  <div>
  <div>
    <div>limit</div>
    <div>4</div>
  </div>
</div>
```

#### Containerblokken {#container}

Beide structuren hebben één dimensie: de lijst met eigenschappen. Met behulp van containerblokken kunnen onderliggende elementen worden toegevoegd (meestal van hetzelfde type of model) en zijn deze dus tweedimensionaal. Deze blokken ondersteunen nog steeds hun eigen eigenschappen die worden gerenderd als rijen met eerst één kolom. Maar zij staan ook toe toevoegend kinderen, waarvoor elk punt als rij en elk bezit als kolom binnen die rij wordt teruggegeven.

In het volgende voorbeeld accepteert een blok een lijst met gekoppelde pictogrammen als onderliggende pictogrammen, waarbij elk gekoppeld pictogram een afbeelding en een koppeling heeft. Let op: [filter-id](/help/implementing/universal-editor/customizing.md#filtering-components) in de gegevens van het blok worden ingesteld om naar de filterconfiguratie te verwijzen.

##### Gegevens {#data-container}

```json
{
  "name": "Our Partners",
  "model": "text-only",
  "filter": "our-partners",
  "text": "<p>Our community of partners is ...</p>",
  "item_0": {
    "model": "linked-icon",
    "image": "/content/dam/partners/foo.png",
    "imageAlt": "Icon of Foo",
    "link": "https://foo.com/"
  },
  "item_1": {
    "model": "linked-icon"
    "image": "/content/dam/partners/bar.png",
    "imageAlt": "Icon of Bar",
    "link": "https://bar.com"
  }
}
```

##### Opmaak {#markup-container}

```html
<div class="our-partners">
  <div>
    <div>
        Our community of partners is ...
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/foo.png" alt="Icon of Foo">
      </picture>
    </div>
    <div>
      <a href="https://foo.com">https://foo.com</a>
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/bar.png" alt="Icon of Bar">
      </picture>
    </div>
    <div>
      <a href="https://bar.com">https://bar.com</a>
    </div>
  </div>
</div>
```

### Semantische inhoudsmodellen maken voor blokken {#creating-content-models}

Met de [uitleg over de mechanismen van de blokstructuur;](#block-structure) het is mogelijk om een inhoudsmodel te maken waarmee inhoud die in AEM een-op-een wordt gepresteerd, wordt toegewezen aan de leveringslaag.

Vroeg in elk project, moet een inhoudsmodel zorgvuldig worden overwogen voor elk blok. De functie moet niet op de hoogte zijn van de inhoudsbron en de ervaring die u hebt opgedaan om auteurs de mogelijkheid te geven om te schakelen of te combineren terwijl ze blokimplementaties en -stijlen opnieuw gebruiken. Meer details en algemene richtlijnen zijn te vinden in [David&#39;s Model (neem 2).](https://www.aem.live/docs/davidsmodel) Meer in het bijzonder [blokverzameling](/help/edge/developer/block-collection.md) Bevat een uitgebreide reeks inhoudsmodellen voor specifieke gebruiksgevallen van gemeenschappelijke gebruikersinterfacepatronen.

Voor AEM creatie met Edge Delivery Services, roept dit de vraag op hoe te om een dwingende semantische inhoudsmodel te dienen wanneer de informatie met vormen wordt authored die uit veelvoudige gebieden in plaats van het uitgeven semantische prijsverhoging in-context zoals rijke teksten worden samengesteld.

U kunt dit probleem oplossen door drie methoden te gebruiken waarmee u een aansprekend inhoudsmodel kunt maken:

* [Type-gevolgtrekking](#type-inference)
* [Veld samenvouwen](#field-collapse)
* [Elementgroepering](#element-grouping)

>[!NOTE]
>
>De implementaties van het blok kunnen de inhoud deconstrueren en het blok met cliënt-zij-teruggegeven DOM vervangen. Hoewel dit mogelijk en intuïtief is voor een ontwikkelaar, is het niet de beste praktijk voor Edge Delivery Services.

#### Type-gevolgtrekking {#type-inference}

Voor sommige waarden kunnen we de semantische betekenis afleiden van de waarden zelf. Deze waarden zijn onder meer:

* **Afbeeldingen** - Als een verwijzing naar een bron in AEM een element is met een MIME-type dat begint met `image/`wordt de verwijzing weergegeven als `<picture><img src="${reference}"></picture>`.
* **Koppelingen** - Als een verwijzing voorkomt in AEM en geen afbeelding is, of als de waarde begint met `https?://`  of `#`wordt de verwijzing weergegeven als `<a href="${reference}">${reference}</a>` .
* **RTF** - Als een bijgesneden waarde begint met een alinea (`p`, `ul`, `ol`, `h1`-`h6`, enz.), wordt de waarde weergegeven als RTF-tekst.
* **Klassenamen** - de `classes` eigenschap wordt behandeld als blokopties en in de tabelkoptekst weergegeven voor [eenvoudige blokken,](#simple) of als waardelijst voor items in een [containerblok.](#container)
* **Waardelijsten** - Wanneer een waarde een eigenschap met meerdere waarden is en de eerste waarde geen van de vorige waarden is, worden alle waarden samengevoegd tot een lijst met door komma&#39;s gescheiden waarden.

Alle andere elementen worden weergegeven als onbewerkte tekst.

#### Veld samenvouwen {#field-collapse}

Veld samenvouwen is het mechanisme voor het combineren van meerdere veldwaarden in één semantisch element op basis van een naamgevingsconventie met de achtervoegsels `Title`, `Type`, `Alt`, en `Text` (alle hoofdletters/kleine letters). Een eigenschap die eindigt met een van deze achtervoegsels wordt niet als een waarde beschouwd, maar als een kenmerk van een andere eigenschap.

##### Afbeeldingen {#image-collapse}

###### Gegevens {#data-image}

```json
{
  "image": "/content/dam/red-car.png",
  "imageAlt: "A red card on a road"
}
```

###### Opmaak {#markup-image}

```html
<picture>
  <img src="/content/dam/red-car.png" alt="A red car on a road">
</picture>
```

##### Koppelingen en knoppen {#links-buttons-collapse}

###### Gegevens {#data-links-buttons}

```json
{
  "link": "https://www.adobe.com",
  "linkTitle": "Navigate to adobe.com",
  "linkText": "adobe.com",
  "linkType": "primary"
}
```

###### Opmaak {#markup-links-buttons}

Nee `linkType`, of `linkType=default`

```html
<a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
```

`linkType=primary`

```html
<strong>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</strong>
```

`linkType=secondary`

```html
<em>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</em>
```

##### Koppen {#headings-collapse}

###### Gegevens {#data-headings}

```json
{
  "heading": "Getting started",
  "headingType": "h2"
}
```

###### Opmaak {#markup-headings}

```html
<h2>Getting started</h2>
```

#### Elementgroepering {#element-grouping}

while [veld samenvouwen](#field-collapse) Als u meerdere eigenschappen wilt combineren tot één semantisch element, gaat het bij het groeperen van elementen om het samenvoegen van meerdere semantische elementen in één cel. Dit is met name handig in gevallen waarin de auteur moet worden beperkt in het type en het aantal elementen dat hij kan maken.

De auteur moet bijvoorbeeld alleen een ondertitel, titel en één alinea-beschrijving maken in combinatie met maximaal twee actieknoppen. Als u deze elementen groepeert, levert dit een semantische opmaak op die zonder verdere actie kan worden opgemaakt.

##### Gegevens {#data-grouping}

```json
{
  "name": "teaser",
  "model": "teaser",
  "image": "/content/dam/teaser-background.png",
  "imageAlt": "A group of people sitting on a stage",
  "teaserText_subtitle": "Adobe Experience Cloud"
  "teaserText_title": "Meet the Experts"
  "teaserText_titleType": "h2"
  "teaserText_description": "<p>Join us in this ask me everything session...</p>"
  "teaserText_cta1": "https://link.to/more-details",
  "teaserText_cta1Text": "More Details"
  "teaserText_cta2": "https://link.to/sign-up",
  "teaserText_cta2Text": "RSVP",
  "teaserText_cta2Type": "primary"
}
```

##### Opmaak {#markup-grouping}

```html
<div class="teaser">
  <div>
    <div>
      <picture>
        <img src="/content/dam/teaser-background.png" alt="A group of people sitting on a stage">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <p>Adobe Experience Cloud</p>
      <h2>Meet the Experts</h2>
      <p>Join us in this ask me everything session ...</p>
      <p><a href="https://link.to/more-details">More Details</a></p>
      <p><strong><a href="https://link.to/sign-up">RSVP</a></strong></p>
    </div>
  </div>
</div>
```

## Secties en sectiemetagegevens {#sections-metadata}

Op dezelfde manier als een ontwikkelaar meerdere objecten kan definiëren en modelleren [blokken,](#blocks) ze kunnen verschillende secties definiëren .

Het inhoudsmodel van Edge Delivery Services staat opzettelijk slechts één enkel niveau van het nesten toe, dat om het even welke standaardinhoud of een blok bevat door een sectie is. Dit betekent dat, om complexere visuele componenten te hebben die andere componenten kunnen bevatten, zij als secties moeten worden gemodelleerd en samen moeten worden gecombineerd gebruikend auto-blokkerende cliëntkant. Typische voorbeelden hiervan zijn tabbladen en inklapbare secties zoals accordeons.

Een sectie kan op dezelfde manier als een blok worden gedefinieerd, maar met het middeltype van `core/franklin/components/section/v1/section`. Secties kunnen een naam en een [filter-ID,](/help/implementing/universal-editor/customizing.md#filtering-components) die door de [Universele editor](/help/implementing/universal-editor/introduction.md) en [model-id;](/help/implementing/universal-editor/field-types.md#model-structure) wordt gebruikt om de sectiemetagegevens weer te geven. Het model is op deze manier het model van het blok met sectiemetagegevens, dat automatisch aan een sectie als sleutel-waardeblok zal worden toegevoegd als het niet leeg is.

De [model-id](/help/implementing/universal-editor/field-types.md#model-structure) en [filter-id](/help/implementing/universal-editor/customizing.md#filtering-components) van de standaardsectie is `section`. Deze kan worden gebruikt om het gedrag van de standaardsectie te wijzigen. In het volgende voorbeeld worden enkele stijlen en een achtergrondafbeelding toegevoegd aan het metagegevensmodel van de sectie.

```json
{
  "id": "section",
  "fields": [
    {
      "component": "multiselect",
      "name": "style",
      "value": "",
      "label": "Style",
      "valueType": "string",
      "options": [
        {
          "name": "Fade in Background",
          "value": "fade-in"
        },
        {
          "name": "Highlight",
          "value": "highlight"
        }
      ]
    },
    {
      "component": "reference",
      "valueType": "string",
      "name": "background",
      "label": "Image",
      "multi": false
    }
  ]
}
```

In het volgende voorbeeld wordt een tabsectie gedefinieerd die kan worden gebruikt om een tabblok te maken door opeenvolgende secties te combineren met een kenmerk voor tabtitelgegevens in een tabblok tijdens automatische blokkering.

```json
{
  "title": "Tab",
  "id": "tab",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/section/v1/section",
        "template": {
          "name": "Tab",
          "model": "tab",
          "filter": "section"
        }
      }
    }
  }
}
```

## Metagegevens pagina {#page-metadata}

Documenten kunnen een pagina hebben [metagegevensblok,](/help/edge/authoring.md#metadata--seo) die wordt gebruikt om te bepalen welke `<meta>` elementen worden gerenderd in de `<head>` van een pagina. De pagina-eigenschappen van pagina&#39;s in AEM as a Cloud Service kaart voor pagina&#39;s die buiten het vak beschikbaar zijn voor Edge Delivery Services, zoals `title`, `description`, `keywords`, enz.

Lees eerst de volgende documenten voordat u gaat onderzoeken hoe u uw eigen metagegevens kunt definiëren. Op deze manier krijgt u meer inzicht in het begrip metagegevens van pagina&#39;s.

* [Metagegevens](https://www.aem.live/developer/block-collection/metadata)
* [Bulkmetagegevens](/help/edge/docs/bulk-metadata.md)

Het is ook mogelijk om aanvullende metagegevens voor pagina&#39;s op twee manieren te definiëren.

### Metagegevensspreadsheets {#metadata-spreadsheets}

Het is mogelijk metagegevens per pad of per padpatroonbasis op een tabelachtige manier te definiëren in AEM as a Cloud Service. Er is een ontwerpgebruikersinterface voor tabelachtige gegevens beschikbaar die vergelijkbaar is met Excel- of Google-bladen.

U maakt een dergelijke tabel door een pagina te maken en de sjabloon Metagegevens in de Sites-console te gebruiken.

>[!NOTE]
>
>Zorg ervoor dat u bij het bewerken van de spreadsheet met metagegevens schakelt naar **Voorvertoning** modus sinds het ontwerpen plaatsvindt op de pagina zelf, niet in de editor.

Definieer in de pagina-eigenschappen van het werkblad de metagegevensvelden die u samen met de URL nodig hebt. Voeg vervolgens metagegevens toe per paginapad of paginapad, waarbij het URL-veld betrekking heeft op de toegewezen, openbare paden en niet op het inhoudspad in AEM.

Zorg ervoor dat het werkblad ook aan de padtoewijzing is toegevoegd voordat u het publiceert.

```text
mappings:
  - /content/site/:/
  - /content/site/metadata:/metadata.json
```

### Pagina-eigenschappen {#page-properties}

Het is ook mogelijk om een componentenmodel voor paginametagegevens te bepalen, die aan de auteur als lusje van het de paginaeigenschappen van AEM Sites ter beschikking zullen worden gesteld.

Hiertoe maakt u een componentmodel met de id `page-metadata`.

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text-input",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```

Er zijn een paar gebiedsnamen die een speciale betekenis hebben en zullen worden overgeslagen wanneer het dienen van de auteursdialoog UI:

* **`cq:tags`** - Standaard, `cq:tags` niet aan de metagegevens worden toegevoegd. Deze toevoegen aan de `page-metadata` model voegt de tag-id&#39;s toe als een door komma&#39;s gescheiden lijst als een `tags` meta-tag naar de kop.
* **`cq:lastModified`** - `cq:lastModified` voegt de gegevens toe zoals `last-modified` aan het hoofd.
