---
title: Een externe SPA bewerken in AEM
description: In dit document worden de aanbevolen stappen beschreven voor het uploaden van een zelfstandige SPA naar een AEM-instantie, het toevoegen van bewerkbare gedeelten van inhoud en het inschakelen van ontwerpen.
exl-id: 7978208d-4a6e-4b3a-9f51-56d159ead385
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '2127'
ht-degree: 0%

---

# Een externe SPA bewerken in AEM {#editing-external-spa-within-aem}

Bij het bepalen van [welk integratieniveau](/help/implementing/developing/headful-headless.md) Als u tussen uw externe SPA en AEM wilt, moet u vaak de SPA binnen AEM kunnen bewerken en bekijken.

## Overzicht {#overview}

In dit document worden de aanbevolen stappen beschreven voor het uploaden van een zelfstandige SPA naar een AEM-instantie, het toevoegen van bewerkbare gedeelten van inhoud en het inschakelen van ontwerpen.

## Vereisten {#prerequisites}

De voorwaarden zijn eenvoudig.

* Zorg ervoor dat een instantie van AEM lokaal wordt uitgevoerd.
* Een basis AEM SPA project maken met [het AEM Project Archetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?#available-properties)
   * Dit zal de basis vormen van het AEM project dat zal worden bijgewerkt met de externe SPA.
   * Voor de voorbeelden in dit document gebruiken we het beginpunt van [het WKND-SPA-project.](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html#spa-editor)
* Heb de werkende, externe Reactie SPA die u bij hand wilt integreren.

## SPA uploaden naar AEM project {#upload-spa-to-aem-project}

Eerst moet u de externe SPA uploaden naar uw AEM project.

1. Vervangen `src` in de `/ui.frontend` projectmap met de React-toepassing `src` map.
1. Eventuele extra afhankelijkheden opnemen in de app `package.json` in de `/ui.frontend/package.json` bestand.
   * Zorg ervoor dat de SPA SDK-afhankelijkheden [aanbevolen versies.](/help/implementing/developing/hybrid/getting-started-react.md#dependencies)
1. Alle aanpassingen opnemen in het dialoogvenster `/public` map.
1. Inclusief inline scripts of stijlen die zijn toegevoegd in het dialoogvenster `/public/index.html` bestand.

## De externe SPA configureren {#configure-remote-spa}

Nu de externe SPA deel uitmaakt van uw AEM project, moet deze binnen AEM worden geconfigureerd.

### Inclusief Adobe SPA SDK-pakketten {#include-spa-sdk-packages}

Om uit AEM SPA eigenschappen voordeel te halen, zijn er gebiedsdelen op de volgende drie pakketten.

* [`@adobe/aem-react-editable-components`](https://github.com/adobe/aem-react-editable-components)
* [`@adobe/aem-spa-component-mapping`](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)
* [`@adobe/aem-spa-page-model-manager`](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)

`@adobe/aem-spa-page-model-manager` verstrekt API voor het initialiseren van een ModelManager en het terugwinnen van het model van de AEM instantie. Dit model kan vervolgens worden gebruikt om AEM componenten te renderen met behulp van API&#39;s van `@adobe/aem-react-editable-components` en `@adobe/aem-spa-component-mapping`.

#### Installatie {#installation}

Voer de volgende npm-opdracht uit om de vereiste pakketten te installeren.

```shell
npm install --save @adobe/aem-spa-component-mapping @adobe/aem-spa-page-model-manager @adobe/aem-react-editable-components
```

### ModelManager-initialisatie {#model-manager-initialization}

Voordat de app wordt gerenderd, wordt de [`ModelManager`](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager) moet worden geïnitialiseerd om de oprichting van de AEM af te handelen `ModelStore`.

Dit moet gebeuren binnen de `src/index.js` van uw toepassing of waar de hoofdmap van de toepassing wordt weergegeven.

Hiervoor kunnen we `initializationAsync` API van de `ModelManager`.

De volgende schermafbeelding laat zien hoe u initialisatie van de `ModelManager` in een eenvoudige React-toepassing. De enige beperking is dat `initializationAsync` vóór `ReactDOM.render()`.

![Modelbeheer initialiseren](assets/external-spa-initialize-modelmanager.png)

In dit voorbeeld wordt `ModelManager` is geïnitialiseerd en is leeg `ModelStore` wordt gemaakt.

`initializationAsync` kan optioneel een `options` object als parameter:

* `path` - Bij initialisatie wordt het model op het gedefinieerde pad opgehaald en opgeslagen in het dialoogvenster `ModelStore`. Dit kan worden gebruikt om `rootModel` bij initialisatie, indien nodig.
* `modelClient` - Hiermee kunt u een aangepaste client opgeven die verantwoordelijk is voor het ophalen van het model.
* `model` - A `model` object dat wordt doorgegeven als een parameter die doorgaans wordt gevuld [SSR gebruiken.](/help/implementing/developing/hybrid/ssr.md)

### AEM authorable Leaf Components {#authorable-leaf-components}

1. Maak/identificeer een AEM component waarvoor een authorable React component zal worden gecreeerd. In dit voorbeeld, gebruiken wij de de tekstcomponent van het WKND-project.

   ![WKND-tekstcomponent](assets/external-spa-text-component.png)

1. Maak een eenvoudige React-tekstcomponent in de SPA. In dit voorbeeld wordt een nieuw bestand `Text.js` is gemaakt met de volgende inhoud.

   ![Text.js](assets/external-spa-textjs.png)

1. Maak een configuratieobject om de kenmerken op te geven die nodig zijn voor AEM bewerken.

   ![config-object maken](assets/external-spa-config-object.png)

   * `resourceType` is verplicht om de component React aan de AEM component in kaart te brengen en het uitgeven toe te laten wanneer het openen in de AEM redacteur.

1. De wrapperfunctie gebruiken `withMappable`.

   ![Gebruiken met Mappable](assets/external-spa-withmappable.png)

   Deze omslagfunctie wijst de React component aan de AEM toe `resourceType` gespecificeerd in config en laat het uitgeven mogelijkheden toe wanneer geopend in de AEM redacteur. Voor standalone componenten, zal het ook de modelinhoud voor de specifieke knoop halen.

   >[!NOTE]
   >
   >In dit voorbeeld zijn er afzonderlijke versies van de component: AEM omwikkelde en losgekoppelde React componenten. De omgelopen versie moet worden gebruikt wanneer expliciet de component wordt gebruikt. Wanneer de component deel uitmaakt van een pagina, kunt u de standaardcomponent blijven gebruiken zoals momenteel gedaan in de SPA editor.

1. Inhoud in de component renderen.

   De JCR-eigenschappen van de tekstcomponent worden als volgt AEM weergegeven.

   ![Eigenschappen van tekstcomponent](assets/external-spa-text-properties.png)

   Deze waarden worden als eigenschappen doorgegeven aan het nieuwe object `AEMText` React-component en kan worden gebruikt om de inhoud te renderen.

   ```javascript
   import React from 'react';
   import { withMappable } from '@adobe/aem-react-editable-components';
   
   export const TextEditConfig = {
       // Empty component placeholder label
       emptyLabel:'Text', 
       isEmpty:function(props) {
          return !props || !props.text || props.text.trim().length < 1;
       },
       // resourcetype of the AEM counterpart component
       resourceType:'wknd-spa-react/components/text'
   };
   
   const Text = ({ text }) => (<div>{text}</div>);
   
   export default Text;
   
   export const AEMText = withMappable(Text, TextEditConfig);
   ```

   Dit is hoe de component zal verschijnen wanneer de AEM configuraties volledig zijn.

   ```javascript
   const Text = ({ cqPath, richText, text }) => {
      const richTextContent = () => (
         <div className="aem_text" id={cqPath.substr(cqPath.lastIndexOf('/') + 1)} data-rte-editelement dangerouslySetInnerHTML={{__html: text}}/>
      );
      return richText ? richTextContent() : (<div className="aem_text">{text}</div>);
   };
   ```

   >[!NOTE]
   >
   >In dit voorbeeld hebben wij verdere aanpassingen aangebracht aan de teruggegeven component om de bestaande tekstcomponent aan te passen. Dit houdt echter geen verband met het schrijven in AEM.

#### Authorable Components toevoegen aan de pagina {#add-authorable-component-to-page}

Zodra authorable React componenten worden gecreeerd, kunnen wij hen door de toepassing gebruiken.

Neem een voorbeeldpagina waar wij een tekst van het WKND SPA project moeten toevoegen. In dit voorbeeld willen we de tekst &quot;Hello World!&quot; weergeven on `/content/wknd-spa-react/us/en/home.html`.

1. Bepaal het pad van het knooppunt dat moet worden weergegeven.

   * `pagePath`: De pagina die het knooppunt bevat, in ons voorbeeld `/content/wknd-spa-react/us/en/home`
   * `itemPath`: Pad naar het knooppunt binnen de pagina, in ons voorbeeld `root/responsivegrid/text`
      * Dit bestaat uit de namen van de bevattende items op de pagina.

   ![Pad van het knooppunt](assets/external-spa-path.png)

1. Component toevoegen op de gewenste positie op de pagina.

   ![Component toevoegen aan pagina](assets/external-spa-add-component.png)

   De `AEMText` kan op de gewenste positie op de pagina worden toegevoegd met `pagePath` en `itemPath` waarden ingesteld als eigenschappen. `pagePath` is een verplichte eigenschap.

#### Bewerken van tekstinhoud op AEM controleren {#verify-text-edit}

We kunnen nu de component testen op onze actieve AEM-instantie.

1. Voer de volgende Maven-opdracht uit vanuit de `aem-guides-wknd-spa` directory om het project te bouwen en op te stellen aan AEM.

```shell
mvn clean install -PautoInstallSinglePackage
```

1. Navigeer in uw AEM naar `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`.

![De SPA bewerken in AEM](assets/external-spa-edit-aem.png)

De `AEMText` -component kan nu worden AEM.

### AEM Authorable Pages {#aem-authorable-pages}

1. Identificeer een pagina die voor creatie in de SPA moet worden toegevoegd. Dit voorbeeld gebruikt `/content/wknd-spa-react/us/en/home.html`.
1. Een nieuw bestand maken (bijvoorbeeld `Page.js`) voor de authorable Page Component. Hier kunt u de pagina-component hergebruiken die is opgegeven in `@adobe/cq-react-editable-components`.
1. Stap vier in de sectie herhalen [AEM authorable leaf components.](#authorable-leaf-components) De wrapperfunctie gebruiken `withMappable` op de component.
1. Zoals eerder is gebeurd, is het van toepassing `MapTo` aan de AEM middeltypes voor alle kindcomponenten binnen de pagina.

   ```javascript
   import { Page, MapTo, withMappable } from '@adobe/aem-react-editable-components';
   import Text, { TextEditConfig } from './Text';
   
   export default withMappable(Page);
   
   MapTo('wknd-spa-react/components/text')(Text, TextEditConfig);
   ```

   >[!NOTE]
   >
   >In dit voorbeeld gebruiken we de tekstcomponent React zonder omloop in plaats van de omloop `AEMText` eerder gemaakt. Wanneer de component deel uitmaakt van een pagina/container en niet zelfstandig is, zorgt de container ervoor dat de component recursief in kaart wordt gebracht en dat ontwerpmogelijkheden worden ingeschakeld en dat de extra omloop niet nodig is voor elk onderliggend element.

1. Voer dezelfde stappen uit in de sectie om een pagina die u kunt schrijven, aan de SPA toe te voegen [Voeg authorable Componenten aan de Pagina toe.](#add-authorable-component-to-page) Hier kunnen we de `itemPath` eigenschap.

#### Pagina-inhoud controleren op AEM {#verify-page-content}

Volg dezelfde stappen in de sectie om te controleren of de pagina kan worden bewerkt [Verifieer het uitgeven van de Inhoud van de Tekst op AEM.](#verify-text-edit)

![Een pagina bewerken in AEM](assets/external-spa-edit-page.png)

De pagina kan nu worden bewerkt op AEM met een lay-outcontainer en onderliggende tekstcomponent.

### Virtuele bladonderdelen {#virtual-leaf-components}

In de vorige voorbeelden hebben we componenten aan de SPA toegevoegd met bestaande AEM inhoud. Er zijn echter gevallen waarin inhoud nog niet in AEM is gemaakt, maar later moet worden toegevoegd door de auteur van de inhoud. Hiervoor kan de front-end ontwikkelaar componenten toevoegen op de juiste locaties in de SPA. Deze componenten zullen placeholders tonen wanneer geopend in de redacteur in AEM. Nadat de inhoud door de auteur van de inhoud in deze plaatsaanduidingen is toegevoegd, worden knooppunten gemaakt in de JCR-structuur en wordt de inhoud voortgezet. De gemaakte component staat dezelfde set bewerkingen toe als de zelfstandige bladcomponenten.

In dit voorbeeld gebruiken we de `AEMText` eerder gemaakte component. Wij willen dat nieuwe tekst onder de bestaande tekstcomponent op de WKND homepage wordt toegevoegd. De toevoeging van componenten is hetzelfde als voor normale bladcomponenten. De `itemPath` kan worden bijgewerkt naar het pad waar de nieuwe component moet worden toegevoegd.

Aangezien de nieuwe component onder de bestaande tekst moet worden toegevoegd op `root/responsivegrid/text`de nieuwe weg `root/responsivegrid/{itemName}`.

```html
<AEMText
 pagePath='/content/wknd-spa-react/us/en/home'
 itemPath='root/responsivegrid/text_20' />
```

De `TestPage` ziet er als volgt uit na het toevoegen van de virtuele component.

![De virtuele component testen](assets/external-spa-virtual-component.png)

>[!NOTE]
>
>Zorg ervoor dat de `AEMText` component heeft `resourceType` in de configuratie instellen om deze functie in te schakelen.

U kunt de wijzigingen nu implementeren in AEM volgende stappen in de sectie [Verifieer het uitgeven van de Inhoud van de Tekst op AEM.](#verify-text-edit) Er wordt een tijdelijke aanduiding weergegeven voor de momenteel niet bestaande `text_20` knooppunt.

![The text_20 node in name](assets/external-spa-text20-aem.png)

Wanneer de auteur van de inhoud deze component bijwerkt, wordt een nieuwe `text_20` node wordt gemaakt op `root/responsivegrid/text_20` in `/content/wknd-spa-react/us/en/home`.

![The text20 node](assets/external-spa-text20-node.png)

#### Eisen en beperkingen {#limitations}

Er zijn een aantal vereisten om virtuele bladcomponenten en enkele beperkingen toe te voegen.

* De `pagePath` eigenschap is verplicht voor het maken van een virtuele component.
* Het paginaknooppunt dat is opgegeven op het pad in `pagePath` moet in het AEM-project bestaan.
* De naam van het knooppunt dat moet worden gemaakt, moet worden opgegeven in het dialoogvenster `itemPath`.
* De component kan op elk niveau worden gemaakt.
   * Als wij een `itemPath='text_20'` in het vorige voorbeeld wordt het nieuwe knooppunt direct onder de pagina gemaakt, dus `/content/wknd-spa-react/us/en/home/jcr:content/text_20`
* Het pad naar het knooppunt waar een nieuw knooppunt wordt gemaakt, moet geldig zijn als het wordt opgegeven via `itemPath`.
   * In dit voorbeeld: `root/responsivegrid` moet bestaan zodat de nieuwe knoop `text_20` kan daar worden gecreëerd.
* Alleen het maken van bladcomponenten wordt ondersteund. Virtuele container en pagina worden in toekomstige versies ondersteund.

## Aanvullende aanpassingen {#additional-customizations}

Als u de vorige voorbeelden hebt gevolgd, kunt u uw externe SPA nu bewerken in AEM. Er zijn echter aanvullende aspecten van uw externe SPA die u verder kunt aanpassen.

### Hoofdknooppunt-id {#root-node-id}

Standaard gaan we ervan uit dat de React-toepassing wordt gerenderd in een `div` van element-id `spa-root`. Indien nodig, kan dit worden aangepast.

Stel dat we een SPA hebben waarin de toepassing wordt gerenderd in een `div` van element-id `root`. Dit moet worden weerspiegeld in drie bestanden.

1. In de `index.js` van het React-verzoek (of `ReactDOM.render()` wordt aangeroepen)

   ![ReactDOM.render() in het bestand index.js](assets/external-spa-root-index.png)

1. In de `index.html` van de React-toepassing

   ![De index.html van de toepassing](assets/external-spa-index.png)

1. Voer twee stappen uit in de hoofdtekst van de paginacomponent van de AEM-app:

   1. Een nieuwe `body.html` voor de paginacomponent.

   ![Een nieuw bestand body.html maken](assets/external-spa-update-body.gif)

   1. Het nieuwe basiselement toevoegen aan het nieuwe `body.html` bestand.

   ![Het hoofdelement toevoegen aan body.html](assets/external-spa-add-root.png)

### Het uitgeven van React SPA met het Verpletteren {#editing-react-spa-with-routing}

Als de externe SPA toepassing Reageren meerdere pagina&#39;s heeft, [het kan het verpletteren gebruiken om de pagina/component te bepalen om terug te geven.](/help/implementing/developing/hybrid/routing.md) Het basisgebruiksgeval moet momenteel - actieve URL met de weg aanpassen die voor een route wordt verstrekt. Om het uitgeven op zulk toe te laten verpletterend toegelaten toepassingen, de weg aan te passen tegen moet worden getransformeerd om AEM-specifieke info aan te passen.

In het volgende voorbeeld hebben we een eenvoudige React-toepassing met twee pagina&#39;s. De pagina die moet worden teruggegeven wordt bepaald door de weg aan de router tegen actieve URL wordt verstrekt aan te passen. Bijvoorbeeld als we aan zijn `mydomain.com/test`, `TestPage` wordt weergegeven.

![Het verpletteren in een externe SPA](assets/external-spa-routing.png)

Om het uitgeven binnen AEM voor dit SPA toe te laten, zijn de volgende stappen vereist.

1. Identificeer het niveau dat als wortel op AEM zou dienst doen.

   * Voor ons voorbeeld overwegen we wknd-spa-response/us/en als de basis van de SPA. Dit betekent dat alles vóór dat pad AEM alleen pagina&#39;s/inhoud is.

1. Maak een nieuwe pagina op het vereiste niveau.

   * In dit voorbeeld is de pagina die moet worden bewerkt `mydomain.com/test`. `test` bevindt zich in het hoofdpad van de app. Dit moet ook worden behouden bij het maken van de pagina in AEM. Daarom kunnen wij een nieuwe pagina op het wortelniveau tot stand brengen dat in de vorige stap wordt bepaald.
   * De nieuwe pagina die u maakt, moet dezelfde naam hebben als de pagina die u wilt bewerken. In dit voorbeeld voor `mydomain.com/test`moet de nieuwe pagina worden gemaakt `/path/to/aem/root/test`.

1. Voeg helpers binnen SPA het verpletteren toe.

   * De nieuwe pagina geeft de verwachte inhoud nog niet in AEM weer. Dit is omdat de router een weg van verwacht `/test` overwegende dat het AEM actieve pad `/wknd-spa-react/us/en/test`. Om het AEM-specifieke gedeelte van URL aan te passen, moeten wij sommige helpers aan de SPA kant toevoegen.

   ![Routeringshelper](assets/external-spa-router-helper.png)

   * De `toAEMPath` helper verstrekt door `@adobe/cq-spa-page-model-manager` kan hiervoor worden gebruikt. Het transformeert de weg die voor het verpletteren wordt verstrekt om AEM-specifieke gedeelten te omvatten wanneer de toepassing op een AEM instantie open is. Er worden drie parameters geaccepteerd:
      * De weg die voor het verpletteren wordt vereist
      * De oorsprong-URL van de AEM instantie waar de SPA wordt bewerkt
      * De projectwortel op AEM zoals bepaald in eerste stap
   * Deze waarden kunnen worden ingesteld als omgevingsvariabelen voor meer flexibiliteit.



1. Verifieer het uitgeven van de pagina in AEM.

   * Implementeer het project en navigeer naar het nieuwe project `test` pagina. De pagina-inhoud wordt nu gerenderd en AEM componenten kunnen worden bewerkt.

## Aanvullende bronnen {#additional-resources}

Het volgende referentiemateriaal kan nuttig zijn om SPA in de context van AEM te begrijpen.

* [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md)
* [Het AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)
* [Het WKND-SPA-project](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html)
* [Aan de slag met SPA in AEM Reageren gebruiken](/help/implementing/developing/hybrid/getting-started-react.md)
* [Referentiematerialen SPA (API-referenties)](/help/implementing/developing/hybrid/reference-materials.md)
* [SPA Bladeren en PageModelManager](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager)
* [SPA](/help/implementing/developing/hybrid/routing.md)
* [SPA en rendering op de server](/help/implementing/developing/hybrid/ssr.md)
