---
title: Een externe SPA bewerken in AEM
description: In dit document worden de aanbevolen stappen beschreven voor het uploaden van een zelfstandige SPA naar een AEM-instantie, het toevoegen van bewerkbare gedeelten van inhoud en het inschakelen van ontwerpen.
exl-id: 7978208d-4a6e-4b3a-9f51-56d159ead385
feature: Developing
role: Admin, Architect, Developer
source-git-commit: a69658d5657f4e1a4feed20cf7eda5e9899aaa3d
workflow-type: tm+mt
source-wordcount: '2370'
ht-degree: 0%

---

# Een externe SPA bewerken in AEM {#editing-external-spa-within-aem}

Wanneer het beslissen van [ welk niveau van integratie ](/help/implementing/developing/headful-headless.md) u tussen uw externe SPA en AEM zou willen hebben, overweeg dat u de SPA binnen AEM moet kunnen uitgeven en bekijken, vaak.

{{ue-over-spa}}

## Overzicht {#overview}

In dit document worden de aanbevolen stappen beschreven voor het uploaden van een zelfstandige SPA naar een AEM-instantie, het toevoegen van bewerkbare gedeelten van inhoud en het inschakelen van ontwerpen.

## Vereisten {#prerequisites}

De voorwaarden zijn eenvoudig.

* Zorg ervoor dat een instantie van AEM lokaal wordt uitgevoerd.
* Creeer een basis AEM SPA project gebruikend [ het Archetype van het Project van de AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL&#available-properties).
   * Forms de basis van het AEM project dat wordt bijgewerkt om de externe SPA op te nemen.
   * Voor de steekproeven in dit document, gebruikt de Adobe het uitgangspunt van [ het WKND SPA project ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=nl-NL#spa-editor).
* Heb de werkende, externe Reactie SPA die u bij hand wilt integreren.

## SPA uploaden naar AEM project {#upload-spa-to-aem-project}

Eerst, moet u de externe SPA aan uw AEM project uploaden.

1. Vervang `src` in de `/ui.frontend` projectmap door de map `src` van de React-toepassing.
1. Neem eventuele extra afhankelijkheden op in het bestand `/ui.frontend/package.json` van de app `package.json` .
   * Zorg ervoor dat de SPA SDK gebiedsdelen van [ geadviseerde versies ](/help/implementing/developing/hybrid/getting-started-react.md#dependencies) zijn.
1. Neem aanpassingen op in de map `/public` .
1. Neem alle inlinescripts of stijlen op die in het `/public/index.html` -bestand zijn toegevoegd.

## De externe SPA configureren {#configure-remote-spa}

Nu de externe SPA deel uitmaakt van uw AEM project, moet deze binnen AEM worden geconfigureerd.

### Inclusief Adobe SPA SDK-pakketten {#include-spa-sdk-packages}

Om uit AEM SPA eigenschappen voordeel te halen, zijn er gebiedsdelen op de volgende drie pakketten.

* [`@adobe/aem-react-editable-components`](https://github.com/adobe/aem-react-editable-components)
* [`@adobe/aem-spa-component-mapping`](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)
* [`@adobe/aem-spa-page-model-manager`](https://www.npmjs.com/login?next=/package/@adobe/aem-spa-model-manager)

Het `@adobe/aem-spa-page-model-manager` -pakket bevat de API voor het initialiseren van een Modelbeheer en het ophalen van het model uit de AEM-instantie. Dit model kan vervolgens worden gebruikt om AEM componenten te renderen met behulp van API&#39;s van `@adobe/aem-react-editable-components` en `@adobe/aem-spa-component-mapping` .

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

![ Initialize ModelManager ](assets/external-spa-initialize-modelmanager.png)

In dit voorbeeld wordt `ModelManager` geïnitialiseerd en wordt een lege `ModelStore` gemaakt.

De instructie `initializationAsync` kan optioneel een `options` -object als parameter accepteren:

* `path` - Bij initialisatie wordt het model op het gedefinieerde pad opgehaald en opgeslagen in de `ModelStore` . Dit pad kan indien nodig worden gebruikt om de `rootModel` bij initialisatie op te halen.
* `modelClient` - Hiermee kunt u een aangepaste client opgeven die het model ophaalt.
* `model` - Een `model` -object dat wordt doorgegeven als een parameter die doorgaans wordt gevuld bij gebruik van SSR.

### AEM authorable Leaf Components {#authorable-leaf-components}

1. Maak/identificeer een AEM component waarvoor een authorable React component wordt gecreeerd. In dit voorbeeld, gebruikt het de tekstcomponent van het WKND-project.

   ![ WKND tekstcomponent ](assets/external-spa-text-component.png)

1. Maak een eenvoudige React-tekstcomponent in de SPA. In dit voorbeeld is een nieuw bestand `Text.js` gemaakt met de volgende inhoud.

   ![ Text.js ](assets/external-spa-textjs.png)

1. Maak een configuratieobject zodat u de kenmerken kunt opgeven die nodig zijn voor AEM bewerken.

   ![ creeer config voorwerp ](assets/external-spa-config-object.png)

   * `resourceType` is verplicht om de component React toe te wijzen aan de AEM component en het bewerken in te schakelen bij het openen in de AEM Editor.

1. Gebruik de wrapper functie `withMappable` .

   ![ Gebruik withMappable ](assets/external-spa-withmappable.png)

   Deze omsluitende functie wijst de React component aan de AEM `resourceType` in config in kaart en laat het uitgeven mogelijkheden toe wanneer geopend in de AEM Redacteur. Voor standalone componenten, haalt het ook de modelinhoud voor de specifieke knoop.

   >[!NOTE]
   >
   >In dit voorbeeld zijn er afzonderlijke versies van de component: AEM omwikkelde en losgekoppelde React-componenten. De omloopversie moet worden gebruikt wanneer uitdrukkelijk het gebruiken van de component. Wanneer de component deel uitmaakt van een pagina, kunt u de standaardcomponent blijven gebruiken zoals momenteel gedaan in de SPA editor.

1. Inhoud in de component renderen.

   De JCR-eigenschappen van de tekstcomponent worden als volgt AEM weergegeven.

   ![ de componenteneigenschappen van de Tekst ](assets/external-spa-text-properties.png)

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

   Hieronder ziet u hoe de component wordt weergegeven wanneer de AEM zijn voltooid.

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
   >In dit voorbeeld zijn verdere aanpassingen aangebracht aan de gerenderde component, zodat deze overeenkomen met de bestaande tekstcomponent. Het heeft geen betrekking op ontwerpen in AEM.

#### Authorable Components toevoegen aan de pagina {#add-authorable-component-to-page}

Nadat u de authorable React-componenten hebt gemaakt, kunt u deze in de hele toepassing gebruiken.

Neem een voorbeeldpagina waar u een tekst van het WKND SPA project moet toevoegen. In dit voorbeeld wilt u de tekst &quot;Hello World!&quot; weergeven op `/content/wknd-spa-react/us/en/home.html` .

1. Bepaal het pad van het knooppunt dat moet worden weergegeven.

   * `pagePath`: De pagina die het knooppunt bevat, in dit voorbeeld `/content/wknd-spa-react/us/en/home`
   * `itemPath`: pad naar het knooppunt op de pagina, in dit voorbeeld `root/responsivegrid/text`
      * Bestaat uit de namen van de bevattende items op de pagina.

   ![ Weg van de knoop ](assets/external-spa-path.png)

1. Component toevoegen op de gewenste positie op de pagina.

   ![ voeg component aan de pagina ](assets/external-spa-add-component.png) toe

   De component `AEMText` kan op de gewenste positie op de pagina worden toegevoegd met `pagePath` - en `itemPath` -waarden ingesteld als eigenschappen. `pagePath` is een verplichte eigenschap.

#### Bewerken van tekstinhoud op AEM controleren {#verify-text-edit}

Test nu de component op de actieve AEM.

1. Voer de volgende Maven-opdracht uit vanuit de `aem-guides-wknd-spa` -map, zodat u het project kunt bouwen en implementeren om te AEM.

```shell
mvn clean install -PautoInstallSinglePackage
```

1. Navigeer in de AEM naar `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html` .

![ Uitgevend de SPA in AEM ](assets/external-spa-edit-aem.png)

De component `AEMText` kan nu worden AEM.

### AEM Authorable Pages {#aem-authorable-pages}

1. Identificeer een pagina die voor creatie in de SPA moet worden toegevoegd. In dit voorbeeld wordt `/content/wknd-spa-react/us/en/home.html` gebruikt.
1. Maak een bestand (bijvoorbeeld `Page.js` ) voor de authorable Page Component. Gebruik de pagina-component in `@adobe/cq-react-editable-components` .
1. Herhaal stap vier in de sectie [ AEM authorable bladcomponenten ](#authorable-leaf-components). Gebruik de wrapperfunctie `withMappable` op de component.
1. Zoals eerder is gedaan, past u `MapTo` toe op de AEM-brontypen voor alle onderliggende componenten binnen de pagina.

   ```javascript
   import { Page, MapTo, withMappable } from '@adobe/aem-react-editable-components';
   import Text, { TextEditConfig } from './Text';
   
   export default withMappable(Page);
   
   MapTo('wknd-spa-react/components/text')(Text, TextEditConfig);
   ```

   >[!NOTE]
   >
   >In dit voorbeeld wordt de tekstcomponent React zonder omloop gebruikt in plaats van de omloop `AEMText` die eerder is gemaakt. De reden is dat wanneer de component onderdeel is van een pagina/container en niet zelfstandig is, de container ervoor zorgt dat de component recursief in kaart wordt gebracht. En, toelatend auteursmogelijkheden en de extra omslag is niet nodig voor elk kind.

1. Om een authorable pagina in de SPA toe te voegen, volg de zelfde stappen in de sectie [ Voeg Authorable Componenten aan de Pagina ](#add-authorable-component-to-page) toe. Hier kunt u de eigenschap `itemPath` overslaan.

#### Pagina-inhoud controleren op AEM {#verify-page-content}

Om te verifiëren dat de pagina kan worden uitgegeven, volg de zelfde stappen in de sectie [ verifiëren het Uitgeven van de Inhoud van de Tekst op AEM ](#verify-text-edit).

![ Uitgevend een pagina in AEM ](assets/external-spa-edit-page.png)

De pagina kan nu worden bewerkt op AEM met een lay-outcontainer en onderliggende tekstcomponent.

### Virtuele bladonderdelen {#virtual-leaf-components}

In de vorige voorbeelden hebt u componenten aan de SPA toegevoegd met bestaande AEM inhoud. Er zijn echter gevallen waarin inhoud nog niet in AEM is gemaakt, maar later moet worden toegevoegd door de auteur van de inhoud. Om dit scenario aan te passen, kan de front-end ontwikkelaar componenten in de aangewezen plaatsen binnen de SPA toevoegen. Deze componenten tonen placeholders wanneer geopend in de redacteur in AEM. Nadat de inhoud door de auteur van de inhoud binnen deze plaatsaanduidingen is toegevoegd, worden knooppunten gemaakt in de JCR-structuur en wordt de inhoud voortgezet. De gemaakte component staat dezelfde set bewerkingen toe als de zelfstandige bladcomponenten.

In dit voorbeeld gebruikt u de component `AEMText` die u eerder hebt gemaakt. U wilt dat nieuwe tekst onder de bestaande tekstcomponent op de WKND-startpagina wordt toegevoegd. De toevoeging van componenten is hetzelfde als voor normale bladcomponenten. De `itemPath` kan echter worden bijgewerkt naar het pad waar de nieuwe component moet worden toegevoegd.

Omdat de nieuwe component onder de bestaande tekst bij `root/responsivegrid/text` moet worden toegevoegd, is het nieuwe pad `root/responsivegrid/{itemName}` .

```html
<AEMText
 pagePath='/content/wknd-spa-react/us/en/home'
 itemPath='root/responsivegrid/text_20' />
```

De component `TestPage` ziet er als volgt uit nadat de virtuele component is toegevoegd.

![ het Testen van de virtuele component ](assets/external-spa-virtual-component.png)

>[!NOTE]
>
>Zorg ervoor dat de `AEMText` -component in de configuratie is ingesteld op `resourceType` , zodat u deze functie kunt inschakelen.

U kunt de veranderingen aan AEM na de stappen in de sectie nu opstellen [ verifieert het Uitgeven van de Inhoud van de Tekst op AEM ](#verify-text-edit). Er wordt een tijdelijke aanduiding weergegeven voor het knooppunt `text_20` dat momenteel niet bestaat.

![ de text_20 knoop in aName ](assets/external-spa-text20-aem.png)

Wanneer de auteur van de inhoud deze component bijwerkt, wordt een nieuw knooppunt `text_20` gemaakt op `root/responsivegrid/text_20` in `/content/wknd-spa-react/us/en/home` .

![ de text20 knoop ](assets/external-spa-text20-node.png)

#### Eisen en beperkingen {#limitations}

Er zijn verschillende vereisten om virtuele bladcomponenten en enkele beperkingen toe te voegen.

* De eigenschap `pagePath` is verplicht voor het maken van een virtuele component.
* Het paginaknooppunt op het pad in `pagePath` moet in het AEM project bestaan.
* De naam van het knooppunt dat moet worden gemaakt, moet worden opgegeven in de map `itemPath` .
* De component kan op elk niveau worden gemaakt.
   * Als u een `itemPath='text_20'` opgeeft in het vorige voorbeeld, wordt het nieuwe knooppunt direct onder de pagina gemaakt, dat wil zeggen: `/content/wknd-spa-react/us/en/home/jcr:content/text_20`
* Het pad naar het knooppunt waar een nieuw knooppunt wordt gemaakt, moet geldig zijn wanneer dit via `itemPath` wordt opgegeven.
   * In dit voorbeeld moet `root/responsivegrid` bestaan, zodat het nieuwe knooppunt `text_20` daar kan worden gemaakt.
* Alleen het maken van bladcomponenten wordt ondersteund. Virtuele container en pagina worden in toekomstige versies ondersteund.

### Virtuele containers {#virtual-containers}

De mogelijkheid om containers toe te voegen, zelfs als de bijbehorende container nog niet in AEM is gemaakt, wordt ondersteund. Het concept en de benadering zijn gelijkaardig aan [ virtuele bladcomponenten ](#virtual-leaf-components).

De front-end ontwikkelaar kan de containercomponenten in aangewezen plaatsen binnen de SPA toevoegen en deze componenten tonen placeholders wanneer geopend in de redacteur in AEM. De auteur kan vervolgens componenten en de inhoud ervan toevoegen aan de container die de vereiste knooppunten maakt in de JCR-structuur.

Als een container bijvoorbeeld bestaat bij `/root/responsivegrid` en de ontwikkelaar een onderliggende container wil toevoegen:

![ plaats van de Container ](assets/container-location.png)

`newContainer` bestaat nog niet in de AEM.

Wanneer u de pagina met deze component in AEM bewerkt, wordt een lege plaatsaanduiding voor een container weergegeven waarin de auteur inhoud kan toevoegen.

![ placeholder van de Container ](assets/container-placeholder.png)

![ plaats van de Container in JCR ](assets/container-jcr-structure.png)

Nadat de auteur een onderliggende component aan de container heeft toegevoegd, wordt het nieuwe containerknooppunt gemaakt met de corresponderende naam in de JCR-structuur.

![ Container met inhoud ](assets/container-with-content.png)

![ Container met inhoud in JCR ](assets/container-with-content-jcr.png)

Meer componenten en inhoud kunnen nu aan de container worden toegevoegd zoals de auteur vereist en de veranderingen worden voortgeduurd.

#### Eisen en beperkingen {#container-limitations}

Er zijn verschillende vereisten om virtuele containers en enkele beperkingen toe te voegen.

* Het beleid om te bepalen welke componenten kunnen worden toegevoegd wordt geërft van de oudercontainer.
* De directe bovenliggende container van de container die moet worden gemaakt, moet in AEM bestaan.
   * Als de container `root/responsivegrid` in de AEM container bestaat, kan een nieuwe container worden gemaakt door het pad `root/responsivegrid/newContainer` op te geven.
   * `root/responsivegrid/newContainer/secondNewContainer` is echter niet mogelijk.
* Er kan slechts één nieuw componentniveau tegelijk worden gemaakt.

## Aanvullende aanpassingen {#additional-customizations}

Als u de vorige voorbeelden hebt gevolgd, kunt u uw externe SPA nu bewerken in AEM. Er zijn echter aanvullende aspecten van uw externe SPA die u verder kunt aanpassen.

### Hoofdknooppunt-id {#root-node-id}

Standaard kunt u ervan uitgaan dat de React-toepassing wordt gerenderd in een `div` element-id `spa-root` . Indien nodig, kan deze syntaxis worden aangepast.

Stel dat u een SPA hebt waarin de toepassing wordt gerenderd in een `div` element-id `root` . Deze syntaxis moet worden weerspiegeld in drie bestanden.

1. In de `index.js` van de React-toepassing (of waar `ReactDOM.render()` wordt aangeroepen)

   ![ ReactDOM.render () in het index.js- dossier ](assets/external-spa-root-index.png)

1. In de `index.html` van de React-toepassing

   ![ Index.html van de toepassing ](assets/external-spa-index.png)

1. Voer twee stappen uit in de hoofdtekst van de paginacomponent van de AEM-app:

   1. Maak een `body.html` voor de paginacomponent.

   ![ creeer een body.html- dossier ](assets/external-spa-update-body.gif)

   1. Voeg het basiselement toe aan het nieuwe `body.html` -bestand.

   ![ voeg het wortelelement aan body.html toe ](assets/external-spa-add-root.png)

### Het uitgeven van React SPA met het Verpletteren {#editing-react-spa-with-routing}

Als de externe Reactie SPA toepassing veelvoudige pagina&#39;s heeft, [ kan het gebruiken verpletterend om de pagina/component te bepalen om ](/help/implementing/developing/hybrid/routing.md) terug te geven. Het basisgebruiksgeval moet momenteel - actieve URL met de weg aanpassen die voor een route wordt verstrekt. Om het uitgeven op dergelijke verpletterende toegelaten toepassingen toe te laten, moet de weg worden aangepast tegen moet worden getransformeerd om AEM-specifieke info aan te passen.

In het volgende voorbeeld hebt u een eenvoudige React-toepassing met twee pagina&#39;s. De pagina die moet worden teruggegeven wordt bepaald door de weg aan de router tegen actieve URL wordt verstrekt aan te passen. Als u bijvoorbeeld op `mydomain.com/test` staat, wordt `TestPage` weergegeven.

![ Verpletterend in een externe SPA ](assets/external-spa-routing.png)

Om het uitgeven binnen AEM voor dit SPA toe te laten, zijn de volgende stappen vereist.

1. Identificeer het niveau dat als wortel op AEM zou dienst doen.

   * Voor uw monster, overweeg wknd-spa-response/us/en als wortel van de SPA. Dit betekent dat alles vóór dat pad AEM alleen pagina&#39;s/inhoud is.

1. Maak een pagina op het vereiste niveau.

   * In dit voorbeeld is de pagina die moet worden bewerkt `mydomain.com/test` . `test` bevindt zich in het hoofdpad van de app. Dit hoofdpad moet ook behouden blijven wanneer u de pagina in AEM maakt. Daarom kunt u een pagina op het wortelniveau tot stand brengen dat in de vorige stap wordt bepaald.
   * De nieuwe pagina die u maakt, moet dezelfde naam hebben als de pagina die u wilt bewerken. In dit voorbeeld, voor `mydomain.com/test`, moet de nieuwe gemaakte pagina `/path/to/aem/root/test` zijn.

1. Voeg helpers binnen SPA het verpletteren toe.

   * De gemaakte pagina kan de verwachte inhoud nog niet in AEM weergeven. De reden is omdat de router een weg van `/test` verwacht terwijl de AEM actieve weg `/wknd-spa-react/us/en/test` is. Om het AEM-specifieke gedeelte van URL aan te passen, moet u sommige helpers op de SPA toevoegen.

   ![ Verpletterend helper ](assets/external-spa-router-helper.png)

   * U kunt de `toAEMPath` helper gebruiken die door `@adobe/cq-spa-page-model-manager` wordt geleverd. Het transformeert de weg die voor het verpletteren wordt verstrekt om AEM-specifieke gedeelten te omvatten wanneer de toepassing op een AEM instantie open is. Er worden drie parameters geaccepteerd:
      * De weg die voor het verpletteren wordt vereist
      * De oorsprong-URL van de AEM instantie waar de SPA wordt bewerkt
      * De projectwortel op AEM zoals bepaald in eerste stap

   * Deze waarden kunnen worden ingesteld als omgevingsvariabelen voor meer flexibiliteit.

1. Verifieer het uitgeven van de pagina in AEM.

   * Implementeer het project om te AEM en naar de gemaakte `test` pagina te navigeren. De pagina-inhoud wordt nu gerenderd en AEM componenten kunnen worden bewerkt.

## Kaderbeperkingen {#framework-limitations}

De component RemotePage verwacht dat de implementatie activa-manifest zoals [ webpack-manifest-stop op GitHub ](https://github.com/shellscape/webpack-manifest-plugin) verstrekt. De component RemotePage, echter, is slechts getest om met het kader van de Reactie (en Next.js via de ver-pagina-volgende component) te werken, en steunt daarom ver het laden van toepassingen van andere kaders, zoals Angular niet.

## Aanvullende bronnen {#additional-resources}

Het volgende referentiemateriaal kan nuttig zijn om SPA in de context van AEM te begrijpen.

* [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md)
* [ The AEM Project Archetype ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL)
* [ het WKND SPA project ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=nl-NL)
* [Aan de slag met SPA in AEM Reageren gebruiken](/help/implementing/developing/hybrid/getting-started-react.md)
* [Referentiematerialen SPA (API-referenties)](/help/implementing/developing/hybrid/reference-materials.md)
* [SPA Bladeren en PageModelManager](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager)
* [SPA](/help/implementing/developing/hybrid/routing.md)
