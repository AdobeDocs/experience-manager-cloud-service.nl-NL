---
title: Een externe SPA bewerken in AEM
description: Dit document beschrijft de geadviseerde stappen om een standalone SPA aan een instantie van AEM te uploaden, editable secties van inhoud toe te voegen, en creatie toe te laten.
exl-id: 7978208d-4a6e-4b3a-9f51-56d159ead385
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '2370'
ht-degree: 0%

---


# Een externe SPA bewerken in AEM {#editing-external-spa-within-aem}

Wanneer het beslissen van [&#x200B; welk niveau van integratie &#x200B;](/help/implementing/developing/headful-headless.md) u tussen uw externe SPA en AEM zou willen hebben, overweeg dat u het KUUROORD binnen AEM moet kunnen uitgeven en bekijken, vaak.

{{ue-over-spa}}

## Overzicht {#overview}

Dit document beschrijft de geadviseerde stappen om een standalone SPA aan een instantie van AEM te uploaden, editable secties van inhoud toe te voegen, en creatie toe te laten.

## Vereisten {#prerequisites}

De voorwaarden zijn eenvoudig.

* Zorg ervoor dat een instantie van AEM lokaal wordt uitgevoerd.
* Creeer een project van basisAEM SPA gebruikend [&#x200B; het Archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL&#available-properties).
   * Forms de basis van het AEM-project dat wordt bijgewerkt met de externe SPA.
   * Voor de steekproeven in dit document, gebruikt Adobe het uitgangspunt van [&#x200B; het project van KND SPA &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=nl-NL#spa-editor).
* Heb het werkende, externe KUUROORD van de Reactie die u bij hand wilt integreren.

## SPA uploaden naar AEM-project {#upload-spa-to-aem-project}

Eerst, moet u externe SPA aan uw project van AEM uploaden.

1. Vervang `src` in de `/ui.frontend` projectmap door de map `src` van de React-toepassing.
1. Neem eventuele extra afhankelijkheden op in het bestand `/ui.frontend/package.json` van de app `package.json` .
   * Zorg ervoor dat de gebiedsdelen van SDK van het KUUROORD van [&#x200B; geadviseerde versies &#x200B;](/help/implementing/developing/hybrid/getting-started-react.md#dependencies) zijn.
1. Neem aanpassingen op in de map `/public` .
1. Neem alle inlinescripts of stijlen op die in het `/public/index.html` -bestand zijn toegevoegd.

## Vorm Verre SPA {#configure-remote-spa}

Nu het externe KUUROORD deel van uw project van AEM uitmaakt, moet het binnen AEM worden gevormd.

### Inclusief Adobe SPA SDK-pakketten {#include-spa-sdk-packages}

Om uit de eigenschappen van AEM SPA voordeel te halen, zijn er gebiedsdelen op de volgende drie pakketten.

* [`@adobe/aem-react-editable-components`](https://github.com/adobe/aem-react-editable-components)
* [`@adobe/aem-spa-component-mapping`](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)
* [`@adobe/aem-spa-page-model-manager`](https://www.npmjs.com/login?next=/package/@adobe/aem-spa-model-manager)

Het `@adobe/aem-spa-page-model-manager` -pakket bevat de API voor het initialiseren van een Modelbeheer en het ophalen van het model uit de AEM-instantie. Dit model kan vervolgens worden gebruikt om AEM-componenten te renderen met API&#39;s van `@adobe/aem-react-editable-components` en `@adobe/aem-spa-component-mapping` .

#### Installatie {#installation}

Voer de volgende `npm` opdracht uit, zodat u de vereiste pakketten kunt installeren.

```shell
npm install --save @adobe/aem-spa-component-mapping @adobe/aem-spa-page-model-manager @adobe/aem-react-editable-components
```

### ModelManager-initialisatie {#model-manager-initialization}

Voordat de app wordt gerenderd, moet [`ModelManager`](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager) worden geïnitialiseerd om het maken van de AEM `ModelStore` af te handelen.

Deze initialisatie moet plaatsvinden in het `src/index.js` -bestand van uw toepassing of op de plaats waar de hoofdmap van de toepassing wordt weergegeven.

Voor deze initialisatie kunt u de `initializationAsync` API van `ModelManager` gebruiken.

De volgende schermafbeelding laat zien hoe u initialisatie van de `ModelManager` in een eenvoudige React-toepassing kunt inschakelen. De enige beperking is dat `initializationAsync` moet worden aangeroepen vóór `ReactDOM.render()` .

![&#x200B; Initialize ModelManager &#x200B;](assets/external-spa-initialize-modelmanager.png)

In dit voorbeeld wordt `ModelManager` geïnitialiseerd en wordt een lege `ModelStore` gemaakt.

De instructie `initializationAsync` kan optioneel een `options` -object als parameter accepteren:

* `path` - Bij initialisatie wordt het model op het gedefinieerde pad opgehaald en opgeslagen in de `ModelStore` . Dit pad kan indien nodig worden gebruikt om de `rootModel` bij initialisatie op te halen.
* `modelClient` - Hiermee kunt u een aangepaste client opgeven die het model ophaalt.
* `model` - Een `model` -object dat wordt doorgegeven als een parameter die doorgaans wordt gevuld bij gebruik van SSR.

### AEM Authorable Leaf Components {#authorable-leaf-components}

1. Een AEM-component maken/identificeren waarvoor een authorable React-component is gemaakt. In dit voorbeeld, gebruikt het de tekstcomponent van het WKND-project.

   ![&#x200B; WKND tekstcomponent &#x200B;](assets/external-spa-text-component.png)

1. Creeer een eenvoudige React tekstcomponent in SPA. In dit voorbeeld is een nieuw bestand `Text.js` gemaakt met de volgende inhoud.

   ![&#x200B; Text.js &#x200B;](assets/external-spa-textjs.png)

1. Maak een configuratieobject zodat u de kenmerken kunt opgeven die vereist zijn voor het inschakelen van AEM-bewerkingen.

   ![&#x200B; creeer config voorwerp &#x200B;](assets/external-spa-config-object.png)

   * `resourceType` is verplicht om de component React toe te wijzen aan de AEM-component en het bewerken in te schakelen wanneer deze wordt geopend in de AEM Editor.

1. Gebruik de wrapper functie `withMappable` .

   ![&#x200B; Gebruik withMappable &#x200B;](assets/external-spa-withmappable.png)

   Deze omsluitende functie wijst de component React toe aan de AEM `resourceType` die in config wordt gespecificeerd en laat het uitgeven mogelijkheden toe wanneer geopend in de Redacteur van AEM. Voor standalone componenten, haalt het ook de modelinhoud voor de specifieke knoop.

   >[!NOTE]
   >
   >In dit voorbeeld zijn er verschillende versies van de component: React-componenten met omloop en los van de omloop van AEM. De omloopversie moet worden gebruikt wanneer uitdrukkelijk het gebruiken van de component. Wanneer de component deel van een pagina uitmaakt, kunt u de standaardcomponent blijven gebruiken zoals momenteel gedaan in de redacteur van het KUUROORD.

1. Inhoud in de component renderen.

   De JCR-eigenschappen van de tekstcomponent worden als volgt weergegeven in AEM.

   ![&#x200B; de componenteneigenschappen van de Tekst &#x200B;](assets/external-spa-text-properties.png)

   Deze waarden worden als eigenschappen doorgegeven aan de gemaakte component `AEMText` React en kunnen worden gebruikt om de inhoud te renderen.

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

   Hieronder ziet u hoe de component wordt weergegeven wanneer de AEM-configuraties zijn voltooid.

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
   >In dit voorbeeld zijn verdere aanpassingen aangebracht aan de gerenderde component, zodat deze overeenkomen met de bestaande tekstcomponent. Het heeft geen betrekking op authoring in AEM.

#### Authorable Components toevoegen aan de pagina {#add-authorable-component-to-page}

Nadat u de authorable React-componenten hebt gemaakt, kunt u deze in de hele toepassing gebruiken.

Neem een voorbeeldpagina waar u een tekst van het project WKND SPA moet toevoegen. In dit voorbeeld wilt u de tekst &quot;Hello World!&quot; weergeven op `/content/wknd-spa-react/us/en/home.html` .

1. Bepaal het pad van het knooppunt dat moet worden weergegeven.

   * `pagePath`: De pagina die het knooppunt bevat, in dit voorbeeld `/content/wknd-spa-react/us/en/home`
   * `itemPath`: pad naar het knooppunt op de pagina, in dit voorbeeld `root/responsivegrid/text`
      * Bestaat uit de namen van de bevattende items op de pagina.

   ![&#x200B; Weg van de knoop &#x200B;](assets/external-spa-path.png)

1. Component toevoegen op de gewenste positie op de pagina.

   ![&#x200B; voeg component aan de pagina &#x200B;](assets/external-spa-add-component.png) toe

   De component `AEMText` kan op de gewenste positie op de pagina worden toegevoegd met `pagePath` - en `itemPath` -waarden ingesteld als eigenschappen. `pagePath` is een verplichte eigenschap.

#### Bewerken van tekstinhoud op AEM controleren {#verify-text-edit}

Test nu de component op de actieve AEM-instantie.

1. Voer de volgende Maven-opdracht uit vanuit de `aem-guides-wknd-spa` -map, zodat u het project kunt bouwen en implementeren in AEM.

```shell
mvn clean install -PautoInstallSinglePackage
```

1. Navigeer in uw AEM-instantie naar `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html` .

![&#x200B; Uitgevend het KUUROORD in AEM &#x200B;](assets/external-spa-edit-aem.png)

De `AEMText` -component kan nu worden geschreven op AEM.

### AEM Authorable Pages {#aem-authorable-pages}

1. Identificeer een pagina die voor creatie in het KUUROORD moet worden toegevoegd. In dit voorbeeld wordt `/content/wknd-spa-react/us/en/home.html` gebruikt.
1. Maak een bestand (bijvoorbeeld `Page.js` ) voor de authorable Page Component. Gebruik de pagina-component in `@adobe/cq-react-editable-components` .
1. Herhaal stap vier in de sectie [&#x200B; AEM authorable bladcomponenten &#x200B;](#authorable-leaf-components). Gebruik de wrapperfunctie `withMappable` op de component.
1. Zoals eerder is gedaan, past u `MapTo` toe op de AEM-brontypen voor alle onderliggende componenten in de pagina.

   ```javascript
   import { Page, MapTo, withMappable } from '@adobe/aem-react-editable-components';
   import Text, { TextEditConfig } from './Text';
   
   export default withMappable(Page);
   
   MapTo('wknd-spa-react/components/text')(Text, TextEditConfig);
   ```

   >[!NOTE]
   >
   >In dit voorbeeld wordt de tekstcomponent React zonder omloop gebruikt in plaats van de omloop `AEMText` die eerder is gemaakt. De reden is dat wanneer de component onderdeel is van een pagina/container en niet zelfstandig is, de container ervoor zorgt dat de component recursief in kaart wordt gebracht. En, toelatend auteursmogelijkheden en de extra omslag is niet nodig voor elk kind.

1. Om een authorable pagina in het KUUROORD toe te voegen, volg de zelfde stappen in de sectie [&#x200B; Voeg Authorable Componenten aan de Pagina &#x200B;](#add-authorable-component-to-page) toe. Hier kunt u de eigenschap `itemPath` overslaan.

#### Pagina-inhoud verifiëren op AEM {#verify-page-content}

Om te verifiëren dat de pagina kan worden uitgegeven, volg de zelfde stappen in de sectie [&#x200B; verifiëren het Uitgeven van de Inhoud van de Tekst op AEM &#x200B;](#verify-text-edit).

![&#x200B; Uitgevend een pagina in AEM &#x200B;](assets/external-spa-edit-page.png)

De pagina kan nu worden bewerkt in AEM met een lay-outcontainer en onderliggende tekstcomponent.

### Virtuele bladonderdelen {#virtual-leaf-components}

In de vorige voorbeelden hebt u componenten met bestaande AEM-inhoud toegevoegd aan de SPA. Er zijn echter gevallen waarin de inhoud nog niet in AEM is gemaakt, maar later door de auteur van de inhoud moet worden toegevoegd. Om dit scenario aan te passen, kan de front-end ontwikkelaar componenten in de aangewezen plaatsen binnen het KUUROORD toevoegen. Deze componenten tonen placeholders wanneer geopend in de redacteur in AEM. Nadat de inhoud door de auteur van de inhoud binnen deze plaatsaanduidingen is toegevoegd, worden knooppunten gemaakt in de JCR-structuur en wordt de inhoud voortgezet. De gemaakte component staat dezelfde set bewerkingen toe als de zelfstandige bladcomponenten.

In dit voorbeeld gebruikt u de component `AEMText` die u eerder hebt gemaakt. U wilt dat nieuwe tekst onder de bestaande tekstcomponent op de WKND-startpagina wordt toegevoegd. De toevoeging van componenten is hetzelfde als voor normale bladcomponenten. De `itemPath` kan echter worden bijgewerkt naar het pad waar de nieuwe component moet worden toegevoegd.

Omdat de nieuwe component onder de bestaande tekst bij `root/responsivegrid/text` moet worden toegevoegd, is het nieuwe pad `root/responsivegrid/{itemName}` .

```html
<AEMText
 pagePath='/content/wknd-spa-react/us/en/home'
 itemPath='root/responsivegrid/text_20' />
```

De component `TestPage` ziet er als volgt uit nadat de virtuele component is toegevoegd.

![&#x200B; het Testen van de virtuele component &#x200B;](assets/external-spa-virtual-component.png)

>[!NOTE]
>
>Zorg ervoor dat de `AEMText` -component in de configuratie is ingesteld op `resourceType` , zodat u deze functie kunt inschakelen.

U kunt de veranderingen in AEM na de stappen in de sectie [&#x200B; nu opstellen verifieert het Uitgeven van de Inhoud van de Tekst op AEM &#x200B;](#verify-text-edit). Er wordt een tijdelijke aanduiding weergegeven voor het knooppunt `text_20` dat momenteel niet bestaat.

![&#x200B; de text_20 knoop in aName &#x200B;](assets/external-spa-text20-aem.png)

Wanneer de auteur van de inhoud deze component bijwerkt, wordt een nieuw knooppunt `text_20` gemaakt op `root/responsivegrid/text_20` in `/content/wknd-spa-react/us/en/home` .

![&#x200B; de text20 knoop &#x200B;](assets/external-spa-text20-node.png)

#### Eisen en beperkingen {#limitations}

Er zijn verschillende vereisten om virtuele bladcomponenten en enkele beperkingen toe te voegen.

* De eigenschap `pagePath` is verplicht voor het maken van een virtuele component.
* Het paginaknooppunt op het pad in `pagePath` moet bestaan in het AEM-project.
* De naam van het knooppunt dat moet worden gemaakt, moet worden opgegeven in de map `itemPath` .
* De component kan op elk niveau worden gemaakt.
   * Als u een `itemPath='text_20'` opgeeft in het vorige voorbeeld, wordt het nieuwe knooppunt direct onder de pagina gemaakt, dat wil zeggen: `/content/wknd-spa-react/us/en/home/jcr:content/text_20`
* Het pad naar het knooppunt waar een nieuw knooppunt wordt gemaakt, moet geldig zijn wanneer dit via `itemPath` wordt opgegeven.
   * In dit voorbeeld moet `root/responsivegrid` bestaan, zodat het nieuwe knooppunt `text_20` daar kan worden gemaakt.
* Alleen het maken van bladcomponenten wordt ondersteund. Virtuele container en pagina worden in toekomstige versies ondersteund.

### Virtuele containers {#virtual-containers}

De mogelijkheid om containers toe te voegen, zelfs als de bijbehorende container nog niet in AEM is gemaakt, wordt ondersteund. Het concept en de benadering zijn gelijkaardig aan [&#x200B; virtuele bladcomponenten &#x200B;](#virtual-leaf-components).

De front-end ontwikkelaar kan de containercomponenten in aangewezen plaatsen binnen SPA toevoegen en deze componenten tonen placeholders wanneer geopend in de redacteur in AEM. De auteur kan vervolgens componenten en de inhoud ervan toevoegen aan de container die de vereiste knooppunten maakt in de JCR-structuur.

Als een container bijvoorbeeld bestaat bij `/root/responsivegrid` en de ontwikkelaar een onderliggende container wil toevoegen:

![&#x200B; plaats van de Container &#x200B;](assets/container-location.png)

`newContainer` bestaat nog niet in de AEM.

Wanneer u de pagina met deze component bewerkt in AEM, wordt een lege plaatsaanduiding voor een container weergegeven waarin de auteur inhoud kan toevoegen.

![&#x200B; placeholder van de Container &#x200B;](assets/container-placeholder.png)

![&#x200B; plaats van de Container in JCR &#x200B;](assets/container-jcr-structure.png)

Nadat de auteur een onderliggende component aan de container heeft toegevoegd, wordt het nieuwe containerknooppunt gemaakt met de corresponderende naam in de JCR-structuur.

![&#x200B; Container met inhoud &#x200B;](assets/container-with-content.png)

![&#x200B; Container met inhoud in JCR &#x200B;](assets/container-with-content-jcr.png)

Meer componenten en inhoud kunnen nu aan de container worden toegevoegd zoals de auteur vereist en de veranderingen worden voortgeduurd.

#### Eisen en beperkingen {#container-limitations}

Er zijn verschillende vereisten om virtuele containers en enkele beperkingen toe te voegen.

* Het beleid om te bepalen welke componenten kunnen worden toegevoegd wordt geërft van de oudercontainer.
* Het directe bovenliggende element van de container die moet worden gemaakt, moet in AEM bestaan.
   * Als de container `root/responsivegrid` in de AEM-container bestaat, kan een nieuwe container worden gemaakt door het pad `root/responsivegrid/newContainer` op te geven.
   * `root/responsivegrid/newContainer/secondNewContainer` is echter niet mogelijk.
* Er kan slechts één nieuw componentniveau tegelijk worden gemaakt.

## Aanvullende aanpassingen {#additional-customizations}

Als u de vorige voorbeelden volgt, is uw externe SPA nu editable binnen AEM. Nochtans zijn er extra aspecten van uw externe SPA die u kunt verder aanpassen.

### Hoofdknooppunt-id {#root-node-id}

Standaard kunt u ervan uitgaan dat de React-toepassing wordt gerenderd in een `div` element-id `spa-root` . Indien nodig, kan deze syntaxis worden aangepast.

Stel dat u een SPA hebt waarin de toepassing wordt gerenderd in een `div` element-id `root` . Deze syntaxis moet worden weerspiegeld in drie bestanden.

1. In de `index.js` van de React-toepassing (of waar `ReactDOM.render()` wordt aangeroepen)

   ![&#x200B; ReactDOM.render () in het index.js- dossier &#x200B;](assets/external-spa-root-index.png)

1. In de `index.html` van de React-toepassing

   ![&#x200B; Index.html van de toepassing &#x200B;](assets/external-spa-index.png)

1. Ga in de hoofdtekst van de paginacomponent van de AEM-app als volgt te werk:

   1. Maak een `body.html` voor de paginacomponent.

   ![&#x200B; creeer een body.html- dossier &#x200B;](assets/external-spa-update-body.gif)

   1. Voeg het basiselement toe aan het nieuwe `body.html` -bestand.

   ![&#x200B; voeg het wortelelement aan body.html toe &#x200B;](assets/external-spa-add-root.png)

### Het uitgeven van React SPA met het Verpletteren {#editing-react-spa-with-routing}

Als de externe toepassing van het KUUROORD Reageren veelvoudige pagina&#39;s heeft, [&#x200B; kan het gebruiken verpletterend om de pagina/component te bepalen om &#x200B;](/help/implementing/developing/hybrid/routing.md) terug te geven. Het basisgebruiksgeval moet momenteel - actieve URL met de weg aanpassen die voor een route wordt verstrekt. Om het uitgeven op dergelijke verpletterende toegelaten toepassingen toe te laten, moet de weg worden aangepast tegen om AEM-specifieke info aan te passen.

In het volgende voorbeeld hebt u een eenvoudige React-toepassing met twee pagina&#39;s. De pagina die moet worden teruggegeven wordt bepaald door de weg aan de router tegen actieve URL wordt verstrekt aan te passen. Als u bijvoorbeeld op `mydomain.com/test` staat, wordt `TestPage` weergegeven.

![&#x200B; Verpletterend in een externe KUUROORD &#x200B;](assets/external-spa-routing.png)

Om het uitgeven binnen AEM voor dit voorbeeldSPA toe te laten, worden de volgende stappen vereist.

1. Identificeer het niveau dat als wortel op AEM zou dienst doen.

   * Voor uw steekproef, overweeg wknd-spa-response/us/en als wortel van SPA. Dit betekent dat alles voor dat pad alleen AEM-pagina&#39;s/inhoud is.

1. Maak een pagina op het vereiste niveau.

   * In dit voorbeeld is de pagina die moet worden bewerkt `mydomain.com/test` . `test` bevindt zich in het hoofdpad van de app. Dit hoofdpad moet ook behouden blijven bij het maken van de pagina in AEM. Daarom kunt u een pagina op het wortelniveau tot stand brengen dat in de vorige stap wordt bepaald.
   * De nieuwe pagina die u maakt, moet dezelfde naam hebben als de pagina die u wilt bewerken. In dit voorbeeld, voor `mydomain.com/test`, moet de nieuwe gemaakte pagina `/path/to/aem/root/test` zijn.

1. Voeg helpers binnen het verpletteren van het KUUROORD toe.

   * De gemaakte pagina kan de verwachte inhoud in AEM nog niet weergeven. De reden is dat de router een weg van `/test` verwacht terwijl de actieve weg van AEM `/wknd-spa-react/us/en/test` is. Om het AEM-specifieke gedeelte van URL aan te passen, moet u sommige helpers op de kant van het KUUROORD toevoegen.

   ![&#x200B; Verpletterend helper &#x200B;](assets/external-spa-router-helper.png)

   * U kunt de `toAEMPath` helper gebruiken die door `@adobe/cq-spa-page-model-manager` wordt geleverd. Het transformeert de weg die voor het verpletteren wordt verstrekt om AEM-specifieke gedeelten te omvatten wanneer de toepassing op een instantie van AEM open is. Er worden drie parameters geaccepteerd:
      * De weg die voor het verpletteren wordt vereist
      * De oorsprong-URL van de instantie AEM waar de SPA wordt bewerkt
      * De projectwortel op AEM zoals die in eerste stap wordt bepaald

   * Deze waarden kunnen worden ingesteld als omgevingsvariabelen voor meer flexibiliteit.

1. Verifieer het uitgeven van de pagina in AEM.

   * Implementeer het project op AEM en navigeer naar de gemaakte `test` pagina. De pagina-inhoud wordt nu gerenderd en AEM-componenten kunnen worden bewerkt.

## Kaderbeperkingen {#framework-limitations}

De component RemotePage verwacht dat de implementatie activa-manifest zoals [&#x200B; webpack-manifest-stop op GitHub &#x200B;](https://github.com/shellscape/webpack-manifest-plugin) verstrekt. De component RemotePage is echter alleen getest om te werken met het React-framework (en Next.js via de component Remote-page-next) en biedt daarom geen ondersteuning voor het extern laden van toepassingen vanuit andere frameworks, zoals Angular.

## Aanvullende bronnen {#additional-resources}

Het volgende referentiemateriaal kan nuttig zijn om SPAs in de context van AEM te begrijpen.

* [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md)
* [&#x200B; The AEM Project Archetype &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL)
* [&#x200B; het project van het KND SPA &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=nl-NL)
* [Begonnen het worden met SPAs in AEM Gebruikend Reageren](/help/implementing/developing/hybrid/getting-started-react.md)
* [SPA Reference Materials (API-referenties)](/help/implementing/developing/hybrid/reference-materials.md)
* [SPA Blueprint en PageModelManager](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager)
* [SPA Model Routing](/help/implementing/developing/hybrid/routing.md)
