---
title: Uw inhoud renderen in een eenvoudige app
description: Ontdek het ophalen van JSON-inhoud uit uw testomgeving met een CodePen-voorbeeldtoepassing en de AEM Headless Client voor JavaScript.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---


# Uw inhoud renderen in een eenvoudige app {#render-content-simple-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="Uw inhoud renderen in een eenvoudige app"
>abstract="Ontdek het ophalen van JSON-inhoud uit uw testomgeving met een CodePen-voorbeeldtoepassing en de AEM Headless Client voor JavaScript."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="De voorbeeldtoepassing CodePen starten"
>abstract="In deze handleiding worden JSON-gegevens uit uw testomgeving opgevraagd in een standaard JavaScript-webapp. U gebruikt de Inhoudsfragmenten die u hebt gemodelleerd en gemaakt in de eerdere leermodules. Indien nodig, werk eerst door die gidsen alvorens in dit te springen."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="In deze module, leerde u hoe te om de Cliënt zonder AEM voor JavaScript te gebruiken om JSON- gegevens van uw proefmilieu te halen gebruikend GraphQL persisted vragen.<br><br> nu begrijpt u hoe u deze cliënt kunt gebruiken om gegevens van binnen uw eigen Webtoepassing te verbruiken."
>abstract=""

## CodePen {#codepen}

CodePen is een online code-editor en afspeellocatie voor webontwikkeling aan de voorkant. Hiermee kunt u HTML-, CSS- en JavaScript-code in uw browser schrijven en de resultaten van uw werk vrijwel direct bekijken. U kunt uw werk ook opslaan en met anderen delen. De Adobe heeft tot een app in CodePen geleid die u kunt gebruiken om JSON- gegevens van uw proefmilieu te halen gebruikend de [ AEM Cliënt zonder Titel voor JavaScript ](https://github.com/adobe/aem-headless-client-js). U kunt deze app ongewijzigd gebruiken of deze in uw eigen CodePen-account opnemen om deze verder aan te passen.

Het klikken van de **Lancering app van de steekproefCodePen** knoop van de proef neemt u aan app in CodePen. De app dient als minimaal voorbeeld voor het ophalen van JSON-gegevens met JavaScript. De voorbeeld-app is ontworpen om JSON-inhoud te renderen die wordt geretourneerd, ongeacht de structuur van het onderliggende model van inhoudsfragment. De app haalt gegevens op uit een `aem-demo-assets` aanhoudend query dat in uw testomgeving is opgenomen. U dient een JSON-respons te zien die vergelijkbaar is met het volgende:

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp",
          "title": "Bali Surf Camp",
          "price": "$5000 USD",
          ...
```

Als u in plaats daarvan een fout ziet, controleer de browser console voor meer detail of reik [ door e-mail ](mailto:aem-headless-trials-support@adobe.com?subject=AEM%20Trials%20support%20request).

Nu u een beetje over CodePen kent, zult u dan app vormen om gegevens van de voortgezette vraag te halen u in een vorige module creeerde.

## JavaScript Code Walkthrough {#code-walkthrough}

De **JS** ruit aan het recht in CodePen bevat JavaScript van voorbeeldapp. Vanaf regel 2 importeert u de AEM Headless Client voor JavaScript vanuit de Skypack CDN. Skypack wordt gebruikt om ontwikkeling zonder een bouwstijlstap te vergemakkelijken, maar u kunt de Zwaarloze Cliënt van de AEM met NPM of van de Garde in uw eigen projecten ook gebruiken. Controle uit de gebruiksinstructies in [ README ](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) voor verder detail.

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

Op regel 6 zijn de gegevens van de publicatiehost gelezen uit de parameter `publishHost` query. Deze parameter is de gastheer waarvan de Zwaardeloze Cliënt van de AEM gegevens haalt. Deze functionaliteit zou typisch in uw app worden gecodeerd, maar u gebruikt een vraagparameter om het voor de app CodePen gemakkelijker te maken om met verschillende milieu&#39;s te werken.

U vormt de Zwaarloze Cliënt van de AEM op lijn 12:

```javascript
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

>[!NOTE]
>
>**serviceURL** wordt geplaatst om een functie van volmachtAdobe I/O Runtime te gebruiken om kwesties te vermijden CORS. Deze proxy is niet vereist voor uw eigen projecten, maar is vereist voor de CodePen-app voor uw testomgeving. De volmachtsfunctie wordt gevormd om de **te gebruiken publishHost** waarde die in de vraagparameter werd verstrekt.

Tot slot wordt de functie `fetchJsonFromGraphQL()` gebruikt om het ophaalverzoek uit te voeren gebruikend de Cliënt AEM Headless. Het wordt geroepen telkens als de code wordt veranderd, of kan worden teweeggebracht door **te klikken herstelt** verbinding. De daadwerkelijke `aemHeadlessClient.runPersistedQuery(..)` vraag komt op lijn 34 voor. Een beetje later wijzigt u de manier waarop deze JSON-gegevens worden gerenderd, maar drukt u deze nu af naar het `#output` div-element met behulp van de functie `resultToPreTag(queryResult)` .

## Gegevens ophalen van uw permanente query {#use-persisted-query}

Op regel 25 geeft u aan van welke GraphQL-query de app gegevens moet ophalen. De persisted querynaam is een combinatie van de naam van het eindpunt (dat wil zeggen `your-project` of `aem-demo-assets` ), gevolgd door een slash en vervolgens de naam van de query. Als u de eerdere moduleinstructies precies hebt gevolgd, bevindt de voortgezette query die u hebt gemaakt zich op het `your-project` eindpunt.

1. Werk de `persistedQueryName` variabele bij zodat gebruikt het de voortgezette vraag u in de vorige module creeerde. Als u de suggestie voor naamgeving hebt gevolgd, zou u een voortgezette query met de naam `adventure-list` in het `your-project` -eindpunt hebben gemaakt en zou u de `persistedQueryName` variabele instellen op `your-project/adventure-list` :

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. Nadat deze wijziging is aangebracht, moet de app automatisch vernieuwen en de onbewerkte JSON-reactie van uw aanhoudende query naar het `#output` div-element afdrukken. Als u een foutenmelding ziet, controleer de console voor extra details. Bereik uit [ door e-mail ](mailto:aem-headless-trials-support@adobe.com?subject=AEM%20Trials%20support%20request) als u nog kwesties met deze stap hebt.

1. Bevat deze JSON precies de eigenschappen die uw app nodig heeft? Als niet, kom terug naar [ inhoud van het Extraheren gebruikend de GraphQL API ](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql) het leren gids om veranderingen aan te brengen. Vergeet niet om uw vraag te bewaren en te publiceren zodra u wordt gedaan.

## De JSON-rendering wijzigen {#change-rendering}

De JSON wordt &#39;as-is&#39; weergegeven in een `pre` -tag, die niet te creatief is. U kunt van CodePen wisselen om de functie `resultToDom()` te gebruiken in plaats daarvan om te laten zien hoe de JSON-reactie kan worden herhaald om een interessanter resultaat te maken.

1. Als u deze wijziging wilt aanbrengen, markeert u regel 37 en verwijdert u de opmerking uit regel 40:

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. Deze functie geeft alle afbeeldingen die in het JSON-antwoord zijn opgenomen, weer als een `img` -tag. Als de **1} de inhoudsfragmenten van het Avontuur {u creeerde geen beelden omvatten, kunt u omschakeling proberen om de `aem-demo-assets/adventures-all` voortgeduurde vraag te gebruiken door lijn 25 te wijzigen:**

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

Deze query levert een JSON-reactie op die afbeeldingen bevat en de functie `resultToDom()` geeft deze inline weer.

![ Resultaat van avonturen-al vraag en resultToDom teruggevende functie ](assets/do-not-localize/adventures-all-query-result.png)

Nu u het werk hebt gedaan om de modellen en vragen te bouwen, kan uw inhoudsteam overnemen met gemak. In de volgende module, toont u van de stroom van de inhoudauteur.
