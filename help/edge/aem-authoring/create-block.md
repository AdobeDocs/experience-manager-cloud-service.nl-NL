---
title: Blokken maken met een instrument voor gebruik met de universele editor
description: Leer hoe te om blokken tot stand te brengen van instrumenten voor gebruik met de Universele Redacteur in AEM creatie met Edge Delivery Services projecten.
exl-id: 65a5600a-8d16-4943-b3cd-fe2eee1b4abf
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 72949b36e7e7f8689365e7cb76a8c491edf23825
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 0%

---


# Blokken maken met een instrument voor gebruik met de universele editor {#create-block}

Leer hoe te om blokken tot stand te brengen van instrumenten voor gebruik met de Universele Redacteur in AEM creatie met Edge Delivery Services projecten.

## Vereisten {#prerequisites}

Deze gids verstrekt geleidelijke instructies voor hoe te om blokken tot stand te brengen van instrumenten voor de Universele Redacteur in AEM creatie met Edge Delivery Services projecten. Het omvat het toevoegen van componenten, het laden van componentendefinities in de Universele Redacteur, het publiceren pagina&#39;s, het uitvoeren van blokdecoratie en stijlen, het brengen van de veranderingen in productie, en het verifiëren van hen. Op de voltooiing van deze gids, kunt u een nieuw blok voor uw eigen project tot stand brengen en opstellen.

Deze gids vereist noodzakelijk bestaande kennis van AEM creatie met Edge Delivery Services projecten evenals de Universele Redacteur. Voordat u met deze handleiding begint, moet u al toegang hebben tot Edge Delivery Services en vertrouwd zijn met de basisbeginselen, zoals:

U hebt de [Zelfstudie over Edge Delivery Service.](/help/edge/developer/tutorial.md)
* U hebt toegang tot [AEM Cloud Service-sandbox.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)
* U hebt [heeft de Universal Editor ingeschakeld in dezelfde sandboxomgeving.](/help/implementing/universal-editor/getting-started.md)
* U hebt de [Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) hulplijn.

Deze gids bouwt op het werk voort dat in [Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) hulplijn.

## Een nieuw blok toevoegen aan uw project {#add-block}

In deze handleiding gaat u een blok maken om een gedenkwaardig citaat op uw pagina weer te geven.

Om dit voorbeeld te vereenvoudigen, worden alle wijzigingen aangebracht in de `main` tak van de projectbewaarplaats. Natuurlijk voor uw daadwerkelijke project, [u moet best practices voor ontwikkeling volgen](https://www.aem.live/docs/dev-collab-and-good-practices) door zich op een verschillende tak te ontwikkelen en alle veranderingen te herzien via trekvraag alvorens samen te voegen aan `main`.

De Adobe beveelt aan dat u blokken in een driefasenaanpak ontwikkelt:

1. Maak de definitie en het model voor het blok, herzie het, en breng het aan productie.
1. Maak inhoud met het nieuwe blok.
1. Implementeer de decoratie en stijlen voor het nieuwe blok.

Het volgende citaatblokvoorbeeld volgt deze benadering.

### Blokdefinitie en -model maken {#create-block-model}

1. Kloon plaatselijk het project GitHub dat u in het project creeerde [Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) te raadplegen en te openen in een editor van uw keuze.

   * Microsoft-code wordt hier gebruikt ter illustratie.

   ![Het project klonen](assets/create-block/clone.png)

1. Bewerk de `component-definition.json` dossier bij de wortel van het project en voeg de volgende definitie voor uw nieuw citaatblok toe en bewaar het dossier.

>[!BEGINTABS]

>[!TAB JSON-voorbeeld]

```json
{
  "title": "Quote",
  "id": "quote",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "Quote",
          "model": "quote",
          "quote": "<p>Think, McFly! Think!</p>",
          "author": "Biff Tannen"
        }
      }
    }
  }
}
```

>[!TAB Schermafbeelding]

![Het bestand component-definitions.json bewerken om het aanhalingsblok te definiëren](assets/create-block/component-definitions.png)

>[!ENDTABS]

1. Bewerk de `component-models.json` dossier bij de wortel van het project en voeg het volgende toe [modeldefinitie](/help/implementing/universal-editor/field-types.md#model-structure) voor het nieuwe aanhalingsteken en sla het bestand op.

   * Zie het document [Inhoud modelleren voor AEM ontwerpen met projecten voor Edge Delivery Services](/help/edge/aem-authoring/content-modeling.md) voor meer informatie over wat belangrijk is om te overwegen wanneer het creëren van inhoudsmodellen.

>[!BEGINTABS]

>[!TAB JSON-voorbeeld]

```json
{
  "id": "quote",
  "fields": [
     {
       "component": "text-area",
       "name": "quote",
       "value": "",
       "label": "Quote",
       "valueType": "string"
     },
     {
       "component": "text-input",
       "valueType": "string",
       "name": "author",
       "label": "Author",
       "value": ""
     }
   ]
}
```

>[!TAB Schermafbeelding]

![Het bestand component-models.json bewerken om het model van het blok met aanhalingstekens te definiëren](assets/create-block/component-models.png)

>[!ENDTABS]

1. Bewerk de `component-filters.json` dossier bij de wortel van het project en voeg het citaatblok aan toe [filterdefinitie](/help/implementing/universal-editor/customizing.md#filtering-components) om toe te staan dat het blok aan om het even welke sectie wordt toegevoegd en sparen het dossier.

>[!BEGINTABS]

>[!TAB JSON-voorbeeld]

```json
{
  "id": "section",
  "components": [
    "text",
    "image",
    "button",
    "title",
    "hero",
    "cards",
    "columns",
    "quote"
   ]
}
```

>[!TAB Schermafbeelding]

![Het bestand component-filters.json bewerken om de filters voor het aanhalingsblok te definiëren](assets/create-block/component-filters.png)

>[!ENDTABS]

1. Deze wijzigingen doorvoeren met behulp van git `main` vertakking.

   * Toewijzen aan `main` is alleen ter illustratie. [Tips en trucs volgen](https://www.aem.live/docs/dev-collab-and-good-practices) en gebruiken een trekpleisterverzoek voor werkelijk projectwerk.

### Inhoud maken met het blok {#create-content}

Nu uw basiscitaatblok wordt bepaald en aan het steekproefproject geëngageerd, kunt u een citaatblok aan een bestaande pagina toevoegen.

1. Meld u aan bij AEM as a Cloud Service in een browser. [De Sites-console gebruiken](/help/sites-cloud/authoring/basic-handling.md) navigeer naar de site die u in het dialoogvenster [Aan de slag-handleiding voor ontwikkelaars voor AEM ontwerpen met Edge Delivery Services](/help/edge/aem-authoring/edge-dev-getting-started.md) en selecteer een pagina.

   * In dit geval: `index` wordt gebruikt voor illustratieve doeleinden.

   ![De indexpagina selecteren in de Sites-console](assets/create-block/sites-console.png)

1. Tik of klik op **Bewerken** in de toolbar van de console en de Universele Redacteur opent.

   * Als u de pagina wilt laden, moet u mogelijk tikken of klikken **Aanmelden met Adobe** om te verifiëren aan AEM in de Universele Redacteur.

1. Selecteer een sectie in de Universal Editor. Tik of klik op de **Toevoegen** en selecteert u vervolgens uw nieuwe **Offerte** in het menu.

   * De **Toevoegen** is een plusteken.
   * U weet dat u een sectie hebt geselecteerd als de blauwe omtrek van het geselecteerde object een tab heeft met het label **Sectie**.
   * In dit voorbeeld tikt of klikt u iets boven de knop **Lorem Ipsum** Met koptekst selecteert u een sectie met de koptekst en lorem ipsum.

   ![Een sectie selecteren in de Universal Editor](assets/create-block/add-quote-block.png)

1. De pagina wordt opnieuw geladen en het prijsblok wordt toegevoegd aan de onderkant van de geselecteerde sectie met de standaardinhoud die is opgegeven in de sectie `component-definitions.json` bestand.

   * Het aanhalingsteken kan worden geselecteerd en bewerkt zoals elk ander blok op zijn plaats of in de eigenschappenrails.
   * Stijlen wordt in een volgende stap toegepast.

   ![De pagina met het nieuwe prijsblok in de geselecteerde sectie](assets/create-block/quote-added.png)

1. Als u tevreden bent met de inhoud van uw prijsopgave, kunt u de pagina publiceren door op de pagina te tikken of op de **Publiceren** in de werkbalk van de Universele Editor.

1. Controleer of de inhoud is gepubliceerd door naar de gepubliceerde pagina te navigeren. De koppeling is vergelijkbaar met `https://<branch>--<repo>--<owner>.hlx.page`

   ![Het gepubliceerde citaat](assets/create-block/quote-published.png)

### Het blok opmaken {#style-block}

Nu u een werkend citaatblok hebt kunt u het stileren toepassen.

1. Ga terug naar de redacteur voor uw project.

1. Een `quote` map onder de `blocks` map.

   ![Een map met aanhalingstekens maken](assets/create-block/new-folder.png)

1. In het nieuwe `quote` map, een `quote.js` bestand om blokdecoratie te implementeren door het volgende JavaScript toe te voegen en het bestand op te slaan.

>[!BEGINTABS]

>[!TAB JavaScript-voorbeeld]

```javascript
export default function decorate(block) {
  const [quoteWrapper] = block.children;

  const blockquote = document.createElement('blockquote');
  blockquote.textContent = quoteWrapper.textContent.trim();
  quoteWrapper.replaceChildren(blockquote);
}
```

>[!TAB Schermafbeelding]

![JavaScript toevoegen om het blok te versieren](assets/create-block/quote-js.png)

>[!ENDTABS]

1. In de `quote` map, een `quote.css` bestand om de opmaak voor het blok te definiëren door de volgende CSS-code toe te voegen en het bestand op te slaan.

>[!BEGINTABS]

>[!TAB CSS-voorbeeld]

```css
.block.quote {
    background-color: #ccc;
    padding: 0 0 24px;
    display: flex;
    flex-direction: column;
    margin: 1rem 0;
}

.block.quote blockquote {
    margin: 16px;
    text-indent: 0;
}

.block.quote > div:last-child > div {
    margin: 0 16px;
    font-size: small;
    font-style: italic;
    position: relative;
}

.block.quote > div:last-child > div::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    bottom: -8px;
    height: 5px;
    width: 30px;
    background-color: darkgray;
}
```

>[!TAB Schermafbeelding]

![CSS toevoegen om de blokopmaak te definiëren](assets/create-block/quote-css.png)

>[!ENDTABS]

1. Deze wijzigingen doorvoeren met behulp van git `main` vertakking.

   * Toewijzen aan `main` is alleen ter illustratie. [Tips en trucs volgen](https://www.aem.live/docs/dev-collab-and-good-practices) en gebruiken een trekpleisterverzoek voor werkelijk projectwerk.

1. Keer terug naar uw browser lusje van de Universele Redacteur waar u de pagina van uw project uitgeeft en herlaadt de pagina om uw gestileerde blok te bekijken.

1. Zie het nu gestileerde citaatblok op de pagina.

   ![Het gestileerde citaatblok in de Universele Redacteur](assets/create-block/quote-styled.png)

1. Controleer of de wijzigingen naar de productie zijn verplaatst door naar de gepubliceerde pagina te navigeren. De koppeling is vergelijkbaar met `https://<branch>--<repo>--<owner>.hlx.page`

   ![Het gepubliceerde en gestileerde citaatblok](assets/create-block/quote-styled-published.png)

Gefeliciteerd! U hebt nu een volledig werkend en gestileerd citaatblok. U kunt dit voorbeeld gebruiken als basis voor het ontwerpen van uw eigen projectspecifieke blokken.

### Blokopties {#block-options}

Als u een blok nodig hebt om er iets anders uit te zien of zich iets anders te gedragen op basis van bepaalde omstandigheden, maar niet anders genoeg om een nieuw blok op zich te worden, kunt u auteurs de keuze laten [blokopties.](content-modeling.md#type-inference)

Door een `classes` eigenschap aan het blok, de eigenschap die in de tabelkoptekst voor eenvoudige blokken wordt weergegeven, of als een waardelijst voor items in een containerblok.

```json
{
  "id": "simpleMarquee",
  "fields": [
    {
      "component": "text",
      "valueType": "string",
      "name": "marqueeText",
      "value": "",
      "label": "Marquee text",
      "description": "The text you want shown in your marquee"
    },
    {
      "component": "select",
      "name": "classes",
      "value": "",
      "label": "Background Color",
      "description": "The marquee background color",
      "valueType": "string",
      "options": [
        {
          "name": "Red",
          "value": "bg-red"
        },
        {
          "name": "Green",
          "value": "bg-green"
        },
        {
          "name": "Blue",
          "value": "bg-blue"
        }
      ]
    }
  ]
}
```

## Andere werktakken gebruiken {#other-branches}

Deze gids heeft u rechtstreeks aan `main` vertakking voor de eenvoud. Voor experimenteren in een voorbeeldopslagplaats, is dit gewoonlijk geen kwestie. Voor de eigenlijke projectwerkzaamheden [u moet best practices voor ontwikkeling volgen](https://www.aem.live/docs/dev-collab-and-good-practices) door zich op een verschillende tak te ontwikkelen en alle veranderingen te herzien via trekvraag alvorens samen te voegen aan `main`.

Als u zich niet ontwikkelt op de `main` vertakking, kunt u toevoegen `?ref=<branch>` in de Universal Editor-locatiebalk om de pagina vanuit uw vertakking te laden. `<branch>` Dit is de naam van de vertakking die wordt gebruikt voor de voorvertoning van uw project of voor live URL&#39;s, bijvoorbeeld `https://<branch>--<repo>--<owner>.hlx.page`.

Het publiceren van inhoud met een nieuw model wordt slechts gesteund wanneer het model aan wordt samengevoegd `main` vertakking.

## Volgende stappen {#next-steps}

Nu u weet hoe u blokken kunt maken, is het van essentieel belang dat u begrijpt hoe u inhoud op semantische wijze modelleert om een slanke ontwikkelaarservaring te bereiken.

Zie het document [Inhoud modelleren voor AEM ontwerpen met projecten voor Edge Delivery Services](/help/edge/aem-authoring/content-modeling.md) om te leren hoe de inhoud modellering voor AEM creatie met Edge Delivery Services projecten werkt.

>[!TIP]
>
>Voor een analyse van begin tot eind van het creëren van een nieuw project van Edge Delivery Services dat voor AEM creatie met AEM as a Cloud Service als inhoudsbron wordt toegelaten, gelieve te bekijken [deze AEM GEM&#39;s webinar.](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery)

