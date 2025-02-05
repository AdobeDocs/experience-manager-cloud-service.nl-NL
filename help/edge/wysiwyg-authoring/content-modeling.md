---
title: Inhoud modelleren voor WYSIWYG Authoring met Edge Delivery Services Projecten
description: Leer hoe contentmodellering werkt voor WYSIWYG Authoring met Edge Delivery Services projecten en hoe u uw eigen inhoud kunt modelleren.
exl-id: e68b09c5-4778-4932-8c40-84693db892fd
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2195'
ht-degree: 0%

---


# Inhoud modelleren voor WYSIWYG Authoring met Edge Delivery Services Projecten {#content-modeling}

Leer hoe contentmodellering werkt voor WYSIWYG Authoring met Edge Delivery Services projecten en hoe u uw eigen inhoud kunt modelleren.

## Vereisten {#prerequisites}

De projecten die WYSIWYG Authoring met Edge Delivery Services gebruiken erven de meerderheid van de mechanica van een ander Edge Delivery Services-project, onafhankelijk van de inhoudsbron of [ auteursmethode ](/help/edge/wysiwyg-authoring/authoring.md).

Voordat u begint met het modelleren van inhoud voor uw project, moet u eerst de volgende documentatie lezen.

* [Aan de slag - Zelfstudie voor ontwikkelaars](/help/edge/developer/tutorial.md)
* [Markeringen, secties, blokken en automatische blokkering](/help/edge/developer/markup-sections-blocks.md)
* [Blokverzameling](/help/edge/developer/block-collection.md)

Het is van essentieel belang dat u deze concepten begrijpt om te komen tot een aansprekend inhoudsmodel dat op een bronagnostische manier werkt. Dit document bevat informatie over de mechanismen die specifiek zijn geïmplementeerd voor WYSIWYG-authoring.

## Standaardinhoud {#default-content}

**Standaard inhoud** is inhoud een auteur intuïtief op een pagina zou zetten zonder extra semantiek toe te voegen. Dit omvat tekst, koppen, koppelingen en afbeeldingen. Deze inhoud spreekt voor zich in zijn functie en doel.

In AEM, wordt deze inhoud uitgevoerd als componenten met zeer eenvoudige, vooraf bepaalde modellen, die alles omvatten die in Prijsvermindering en HTML kan in series worden vervaardigd.

* **Tekst**: Rijke tekst (met inbegrip van lijstelementen en sterke of cursieve tekst)
* **Titel**: Tekst, type (h1-h6)
* **Beeld**: Source, beschrijving
* **Knoop**: Tekst, titel, url, type (gebrek, primair, secundair)

Het model van deze componenten maakt deel uit van [ Boilerplate voor WYSIWYG creatie met Edge Delivery Services ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112).

## Blokken {#blocks}

Blokken worden gebruikt om rijkere inhoud met specifieke stijlen en functionaliteit te maken. In tegenstelling tot de standaardinhoud, vereisen de blokken extra semantiek.

Blokken zijn in wezen stukken inhoud die door JavaScript zijn versierd en met een stijlblad zijn opgemaakt.

### Blokmodeldefinitie {#model-definition}

Wanneer u WYSIWYG-authoring met Edge Delivery Services gebruikt, moet de inhoud van blokken expliciet worden gemodelleerd om de auteur de interface te bieden voor het maken van inhoud. In principe moet u een model maken, zodat de ontwerpgebruikersinterface weet welke opties op basis van het blok aan de auteur moeten worden voorgesteld.

Het [`component-models.json` ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) dossier bepaalt het model van blokken. De velden die in het componentmodel worden gedefinieerd, blijven behouden als eigenschappen in AEM en worden weergegeven als cellen in de tabel waaruit een blok bestaat.

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

Merk op dat niet elk blok een model moet hebben. Sommige blokken zijn eenvoudig [ containers ](#container) voor een lijst van kinderen, waar elk kind zijn eigen model heeft.

Het is ook nodig om te bepalen welke blokken bestaan en aan een pagina kunnen worden toegevoegd gebruikend de Universele Redacteur. In het bestand [`component-definitions.json`](/help/implementing/universal-editor/component-definition.md) worden de componenten weergegeven zoals deze door de Universal Editor beschikbaar worden gesteld.

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

* Moet het `core/franklin/components/block/v1/block` middeltype, de generische implementatie van de bloklogica in AEM gebruiken.
* U moet de bloknaam definiëren. Deze wordt weergegeven in de tabelkoptekst van het blok.
   * De bloknaam wordt gebruikt om de juiste stijl en het script op te halen om het blok te versieren.
* Kan a [ modelidentiteitskaart ](/help/implementing/universal-editor/field-types.md#model-structure) bepalen.
   * De model-id is een verwijzing naar het model van de component, dat de velden definieert die beschikbaar zijn voor de auteur in het deelvenster Eigenschappen.
* Kan a [ filteridentiteitskaart ](/help/implementing/universal-editor/filtering.md) bepalen.
   * De filterID is een verwijzing naar het filter van de component, dat toestaat om het auteursgedrag te veranderen, bijvoorbeeld door te beperken welke kinderen aan het blok of de sectie kunnen worden toegevoegd, of welke eigenschappen RTE worden toegelaten.

Al deze informatie wordt opgeslagen in AEM wanneer een blok aan een pagina wordt toegevoegd. Als het middeltype of de bloknaam ontbreken, zal het blok niet op de pagina teruggeven.

>[!WARNING]
>
>Hoewel mogelijk is het niet nodig of aanbevolen om aangepaste AEM te implementeren. De door AEM geleverde onderdelen voor Edge Delivery Services zijn voldoende en bieden bepaalde relingen om de ontwikkeling te vergemakkelijken.
>
>De componenten die door AEM worden verstrekt geven een prijsverhoging terug die door [ helix-html2md ](https://github.com/adobe/helix-html2md) kan worden verbruikt wanneer het publiceren aan Edge Delivery Services en door [ aem.js ](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js) wanneer het laden van een pagina in de Universele Redacteur. De prijsverhoging is het stabiele contract tussen AEM en de andere delen van het systeem, en staat geen aanpassingen toe. Daarom moeten de projecten de componenten niet veranderen en moeten geen douanecomponenten gebruiken.

### Blokstructuur {#block-structure}

De eigenschappen van blokken worden [ bepaald in de componentenmodellen ](#model-definition) en als dusdanig voortgeduurd in AEM. Eigenschappen worden als cellen gerenderd in de tabelachtige structuur van het blok.

#### Eenvoudige blokken {#simple}

In de eenvoudigste vorm geeft een blok elke eigenschap weer in één rij/kolom in de volgorde waarin de eigenschappen in het model zijn gedefinieerd.

In het volgende voorbeeld wordt de afbeelding eerst in het model gedefinieerd en vervolgens de tekst. Ze worden dus eerst met de afbeelding en vervolgens met de tekst gerenderd.

>[!BEGINTABS]

>[!TAB  Gegevens ]

```json
{
  "name": "Hero",
  "model": "hero",
  "image": "/content/dam/image.png",
  "imageAlt": "Helix - a shape like a corkscrew",
  "text": "<h1>Welcome to AEM</h1>"
}
```

>[!TAB  Prijsverhoging ]

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

>[!TAB  Lijst ]

```text
+---------------------------------------------+
| Hero                                        |
+=============================================+
| ![Helix - a shape like a corkscrew][image0] |
+---------------------------------------------+
| # Welcome to AEM                            |
+---------------------------------------------+
```

>[!ENDTABS]

Het kan opvallen dat bepaalde typen waarden het afleiden van semantiek in de opmaak toestaan en dat eigenschappen in één cel worden gecombineerd. Dit gedrag wordt beschreven in de sectie [ Inferentie van het Type ](#type-inference).

#### Key-Value-blok {#key-value}

In veel gevallen is het raadzaam de gerenderde semantische opmaakcode te decoreren, CSS-klassennamen toe te voegen, nieuwe knooppunten toe te voegen of deze in de DOM te verplaatsen en stijlen toe te passen.

In andere gevallen echter, wordt het blok gelezen als sleutel-waarde paar-als configuratie.

Een voorbeeld van dit is de [ sectiemetagegevens ](/help/edge/developer/markup-sections-blocks.md#sections). In dit gebruiksgeval, kan het blok worden gevormd om als sleutel-waarde paarlijst terug te geven. Gelieve te zien de sectie [ Secties en Metagegevens van de Sectie ](#sections-metadata) voor meer informatie.

>[!BEGINTABS]

>[!TAB  Gegevens ]

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

>[!TAB  Prijsverhoging ]

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

>[!TAB  Lijst ]

```text
+-----------------------------------------------------------------------+
| Featured Articles                                                     |
+=======================================================================+
| source   | [/content/site/articles.json](/content/site/articles.json) |
+-----------------------------------------------------------------------+
| keywords | Developer,Courses                                          |
+-----------------------------------------------------------------------+
| limit    | 4                                                          |
+-----------------------------------------------------------------------+
```

>[!ENDTABS]

#### Containerblokken {#container}

Beide structuren hebben één dimensie: de lijst met eigenschappen. Met behulp van containerblokken kunnen onderliggende elementen worden toegevoegd (meestal van hetzelfde type of model) en zijn deze dus tweedimensionaal. Deze blokken ondersteunen nog steeds hun eigen eigenschappen die worden gerenderd als rijen met eerst één kolom. Maar zij staan ook toe toevoegend kinderen, waarvoor elk punt als rij en elk bezit als kolom binnen die rij wordt teruggegeven.

In het volgende voorbeeld accepteert een blok een lijst met gekoppelde pictogrammen als onderliggende pictogrammen, waarbij elk gekoppeld pictogram een afbeelding en een koppeling heeft. Merk [ filteridentiteitskaart ](/help/implementing/universal-editor/filtering.md) op die in de gegevens van het blok wordt geplaatst om de filterconfiguratie van verwijzingen te voorzien.

>[!BEGINTABS]

>[!TAB  Gegevens ]

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

>[!TAB  Prijsverhoging ]

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

>[!TAB  Lijst ]

```text
+------------------------------------------------------------ +
| Our Partners                                                |
+=============================================================+
| Our community of partners is ...                            |
+-------------------------------------------------------------+
| ![Icon of Foo][image0] | [https://foo.com](https://foo.com) |
+-------------------------------------------------------------+
| ![Icon of Bar][image1] | [https://bar.com](https://bar.com) |
+-------------------------------------------------------------+
```

>[!ENDTABS]

### Semantische inhoudsmodellen maken voor blokken {#creating-content-models}

Met de [ mechanica van verklaarde blokstructuur ](#block-structure), is het mogelijk om een inhoudsmodel tot stand te brengen dat inhoud in AEM één-aan-één aan de leveringsrij voortzette in kaart brengt.

Vroeg in elk project, moet een inhoudsmodel zorgvuldig worden overwogen voor elk blok. De functie moet niet op de hoogte zijn van de inhoudsbron en de ervaring die u hebt opgedaan om auteurs de mogelijkheid te geven om te schakelen of te combineren terwijl ze blokimplementaties en -stijlen opnieuw gebruiken. Meer details en algemene begeleiding kunnen in [ het Model van David worden gevonden (neem 2) ](https://www.aem.live/docs/davidsmodel). Specifieker, bevat de [ blokinzameling ](/help/edge/developer/block-collection.md) een uitgebreide reeks inhoudsmodellen voor specifieke gebruiksgevallen van gemeenschappelijke gebruikersinterfacepatronen.

Voor WYSIWYG-authoring met Edge Delivery Services roept dit de vraag op hoe een aansprekend semantisch inhoudsmodel kan worden gebruikt wanneer de informatie wordt geschreven met formulieren die uit meerdere velden bestaan, in plaats van semantische opmaak in context te bewerken, zoals RTF-tekst.

U kunt dit probleem oplossen door drie methoden te gebruiken waarmee u een aansprekend inhoudsmodel kunt maken:

* [Type-gevolgtrekking](#type-inference)
* [Veld samenvouwen](#field-collapse)
* [Elementgroepering](#element-grouping)

>[!NOTE]
>
>De implementaties van het blok kunnen de inhoud deconstrueren en het blok met cliënt-zij-teruggegeven DOM vervangen. Hoewel dit mogelijk en intuïtief is voor een ontwikkelaar, is het niet de beste praktijk voor Edge Delivery Services.

#### Type-gevolgtrekking {#type-inference}

Voor sommige waarden kunnen we de semantische betekenis afleiden van de waarden zelf. Deze waarden zijn onder meer:

* **Beelden** - als een verwijzing naar een middel in AEM een activa met een type MIME is dat met `image/` begint, wordt de verwijzing teruggegeven als `<picture><img src="${reference}"></picture>`.
* **Verbindingen** - als een verwijzing in AEM bestaat en geen beeld is, of als de waarde met `https?://` of `#` begint, wordt de verwijzing teruggegeven als `<a href="${reference}">${reference}</a>`.
* **Rijke Tekst** - als een in orde gemaakte waarde met een paragraaf (`p`, `ul`, `ol`, `h1` - `h6`, enz.) begint, wordt de waarde teruggegeven als rijke tekst.
* **Namen van de Klasse** - het `classes` bezit wordt behandeld als [ blokopties ](/help/edge/developer/markup-sections-blocks.md#block-options) en in de lijstkopbal voor [ eenvoudige blokken ](#simple) teruggegeven, of als waardelijst voor punten in a [ containerblok ](#container). Het is nuttig als u een blok ](/help/edge/wysiwyg-authoring/create-block.md#block-options) verschillend wilt [ opmaken, maar te hoeven om geen volledig nieuw blok tot stand te brengen.
* **Lijsten van de Waarde** - als een waarde een multi-waardebezit is en de eerste waarde geen van het vorige is, worden alle waarden samengevoegd als komma-gescheiden lijst.

Alle andere elementen worden weergegeven als onbewerkte tekst.

#### Veld samenvouwen {#field-collapse}

Veld samenvouwen is het mechanisme voor het combineren van meerdere veldwaarden in één semantisch element op basis van een naamgevingsconventie met de achtervoegsels `Title`, `Type`, `MimeType`, `Alt` en `Text` (allemaal hoofdlettergevoelig). Een eigenschap die eindigt met een van deze achtervoegsels wordt niet als een waarde beschouwd, maar als een kenmerk van een andere eigenschap.

##### Afbeeldingen {#image-collapse}

>[!BEGINTABS]

>[!TAB  Gegevens ]

```json
{
  "image": "/content/dam/red-car.png",
  "imageAlt: "A red card on a road"
}
```

>[!TAB  Prijsverhoging ]

```html
<picture>
  <img src="/content/dam/red-car.png" alt="A red car on a road">
</picture>
```

>[!TAB  Lijst ]

```text
![A red car on a road][image0]
```

>[!ENDTABS]

##### Koppelingen en knoppen {#links-buttons-collapse}

>[!BEGINTABS]

>[!TAB  Gegevens ]

```json
{
  "link": "https://www.adobe.com",
  "linkTitle": "Navigate to adobe.com",
  "linkText": "adobe.com",
  "linkType": "primary"
}
```

>[!TAB  Prijsverhoging ]

Geen `linkType` of `linkType=default`

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

>[!TAB  Lijst ]

```text
[adobe.com](https://www.adobe.com "Navigate to adobe.com")
**[adobe.com](https://www.adobe.com "Navigate to adobe.com")**
_[adobe.com](https://www.adobe.com "Navigate to adobe.com")_
```

>[!ENDTABS]

##### Koppen {#headings-collapse}

>[!BEGINTABS]

>[!TAB  Gegevens ]

```json
{
  "heading": "Getting started",
  "headingType": "h2"
}
```

>[!TAB  Prijsverhoging ]

```html
<h2>Getting started</h2>
```

>[!TAB  Lijst ]

```text
## Getting started
```

>[!ENDTABS]

#### Elementgroepering {#element-grouping}

Terwijl [ het gebied samenvouwt ](#field-collapse) over het combineren van veelvoudige eigenschappen in één enkel semantisch element is, element groepering over het aaneenschakelen van veelvoudige semantische elementen in één enkele cel. Dit is met name handig in gevallen waarin de auteur moet worden beperkt in het type en het aantal elementen dat hij kan maken.

Met een teaser-component kan de auteur bijvoorbeeld alleen een ondertitel, titel en een enkele alinealijn maken, gecombineerd met maximaal twee actieknoppen. Als u deze elementen groepeert, levert dit een semantische opmaak op die zonder verdere actie kan worden opgemaakt.

Bij elementgroepering wordt een naamgevingsconventie gebruikt, waarbij de groepsnaam van elke eigenschap in de groep wordt gescheiden door een onderstrepingsteken. Veldsamenvouwen van de eigenschappen in een groep werkt zoals eerder beschreven.

>[!BEGINTABS]

>[!TAB  Gegevens ]

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

>[!TAB  Prijsverhoging ]

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

>[!TAB  Lijst ]

```text
+-------------------------------------------------+
| Teaser                                          |
+=================================================+
| ![A group of people sitting on a stage][image0] |
+-------------------------------------------------+
| Adobe Experience Cloud                          |
| ## Meet the Experts                             |
| Join us in this ask me everything session ...   |
| [More Details](https://link.to/more-details)    |
| [RSVP](https://link.to/sign-up)                 |
+-------------------------------------------------+
```

>[!ENDTABS]

## Secties en sectiemetagegevens {#sections-metadata}

De zelfde manier een ontwikkelaar kan veelvoudige [ blokken ](#blocks) bepalen en modelleren, kunnen zij verschillende secties bepalen.

Het inhoudsmodel van Edge Delivery Services staat opzettelijk slechts één enkel niveau van het nesten toe, dat om het even welke standaardinhoud of een blok bevat door een sectie is. Dit betekent dat, om complexere visuele componenten te hebben die andere componenten kunnen bevatten, zij als secties moeten worden gemodelleerd en samen moeten worden gecombineerd gebruikend auto-blokkerende cliëntkant. Typische voorbeelden hiervan zijn tabbladen en inklapbare secties zoals accordeons.

Een sectie kan op dezelfde manier als een blok worden gedefinieerd, maar met het middeltype van `core/franklin/components/section/v1/section`. De secties kunnen een naam en a [ filteridentiteitskaart ](/help/implementing/universal-editor/filtering.md) hebben, die door de [ Universele Redacteur ](/help/implementing/universal-editor/introduction.md) slechts, evenals a [ modelidentiteitskaart ](/help/implementing/universal-editor/field-types.md#model-structure) wordt gebruikt, die wordt gebruikt om de sectiemetagegevens terug te geven. Het model is op deze manier het model van het blok met sectiemetagegevens, dat automatisch aan een sectie als sleutel-waardeblok zal worden toegevoegd als het niet leeg is.

[ modelidentiteitskaart ](/help/implementing/universal-editor/field-types.md#model-structure) en [ filteridentiteitskaart ](/help/implementing/universal-editor/filtering.md) van de standaardsectie is `section`. Deze kan worden gebruikt om het gedrag van de standaardsectie te wijzigen. In het volgende voorbeeld worden enkele stijlen en een achtergrondafbeelding toegevoegd aan het metagegevensmodel van de sectie.

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

Documenten kunnen een pagina [ meta-gegevensblok ](https://www.aem.live/developer/block-collection/metadata) hebben, dat wordt gebruikt om te bepalen welke `<meta>` elementen in `<head>` van een pagina worden teruggegeven. De pagina-eigenschappen van pagina&#39;s in AEM as a Cloud Service worden toegewezen aan de pagina-eigenschappen die buiten het vak beschikbaar zijn voor Edge Delivery Services, zoals `title` , `description` , `keywords` , enz.

Lees eerst de volgende documenten voordat u gaat onderzoeken hoe u uw eigen metagegevens kunt definiëren. Op deze manier krijgt u meer inzicht in het begrip metagegevens van pagina&#39;s.

* [ Metagegevens ](https://www.aem.live/developer/block-collection/metadata)
* [Bulkmetagegevens](/help/edge/docs/bulk-metadata.md)

Het is ook mogelijk om aanvullende metagegevens voor pagina&#39;s op twee manieren te definiëren.

### Metagegevensspreadsheets {#metadata-spreadsheets}

Het is mogelijk metagegevens per pad of per padpatroonbasis op een tabelachtige manier te definiëren in AEM as a Cloud Service. Er is een ontwerpgebruikersinterface voor tabelachtige gegevens beschikbaar die vergelijkbaar is met Excel- of Google-bladen.

Voor verdere details, te zien gelieve het document [ Gebruikend Spreadsheets om Gegevens in Tabel te beheren ](/help/edge/wysiwyg-authoring/tabular-data.md) voor meer informatie.

### Pagina-eigenschappen {#page-properties}

Veel van de standaardpagina-eigenschappen die beschikbaar zijn in AEM, worden toegewezen aan de desbetreffende pagina-metagegevens in een document. Dit geldt bijvoorbeeld voor `title` , `description` , `robots` , `canonical url` of `keywords` . Er zijn ook enkele AEM-specifieke eigenschappen beschikbaar:

* `cq:lastModified` als `modified-time` in de ISO8601-indeling
* De tijd waarop het document voor het laatst is gepubliceerd als `published-time` in de ISO8601-indeling
* `cq:tags` als `cq-tags` als een door komma&#39;s gescheiden lijst met de tag-id&#39;s.

Het is ook mogelijk om een componentenmodel voor meta-gegevens van de douanepagina te bepalen, die aan de auteur in de Universele Redacteur ter beschikking zullen worden gesteld.

Hiertoe maakt u een componentmodel met de id `page-metadata` .

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```

## Volgende stappen {#next-steps}

Nu u weet hoe te om inhoud te modelleren, kunt u blokken voor uw eigen Edge Delivery Services met het auteursproject van WYSIWYG tot stand brengen.

Zie het document [ Creërend Blokken Instrumented voor gebruik met de Universele Redacteur ](/help/edge/wysiwyg-authoring/create-block.md) om te leren hoe te tot blokken die voor gebruik met de Universele Redacteur in WYSIWYG authoring met de projecten van Edge Delivery Services tot stand brengen.

Als u reeds vertrouwd met het creëren van blokken bent, te zien gelieve de document [ Begonnen Gids van de Ontwikkelaar Begonnen voor het auteursrecht van WYSIWYG met Edge Delivery Services ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) om u aan de slag te krijgen met een nieuwe plaats van Adobe Experience Manager gebruikend Edge Delivery Services en de Universele Redacteur voor inhoud authoring.

>[!TIP]
>
>Voor een analyse van begin tot eind van het creëren van een nieuw project van Edge Delivery Services dat voor WYSIWYG creatie met AEM as a Cloud Service als inhoudsbron wordt toegelaten, gelieve te bekijken [ dit AEM webinar GEMs ](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/wysiwyg-authoring-and-edge-delivery).

