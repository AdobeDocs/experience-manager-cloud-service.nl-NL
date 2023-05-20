---
title: Uw inhoud renderen in een eenvoudige app
description: Ontdek het ophalen van JSON-inhoud uit uw testomgeving met een CodePen-voorbeeldtoepassing en de AEM Headless Client voor JavaScript.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
source-git-commit: 1949ee211b4f816e05aa779deb9e287347f006ad
workflow-type: tm+mt
source-wordcount: '987'
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
>abstract="In deze handleiding worden JSON-gegevens uit uw testomgeving opgevraagd in een standaard JavaScript-webapp. We gebruiken de Content Fragments die u hebt gemodelleerd en gemaakt in de eerdere leermodules. Werk deze gidsen dus eerst door voordat u naar deze gaat."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="In deze module hebt u geleerd hoe u de AEM Headless Client voor JavaScript kunt gebruiken om JSON-gegevens op te halen uit uw testomgeving met behulp van GraphQL persisted query&#39;s.<br><br>Nu begrijpt u hoe u deze client kunt gebruiken om gegevens te verbruiken vanuit uw eigen webtoepassing."
>abstract=""

## CodePen {#codepen}

CodePen is een online code-editor en afspeellocatie voor webontwikkeling aan de voorkant. Hiermee kunt u HTML-, CSS- en JavaScript-code schrijven in uw browser en de resultaten van uw werk vrijwel direct bekijken. U kunt uw werk ook opslaan en met anderen delen. We hebben een app in CodePen gemaakt die u kunt gebruiken om JSON-gegevens op te halen uit uw testomgeving met behulp van de [AEM headless-client voor JavaScript](https://github.com/adobe/aem-headless-client-js). U kunt deze app ongewijzigd gebruiken of deze in uw eigen CodePen-account opnemen om deze verder aan te passen.

Klik op de knop **De voorbeeldtoepassing CodePen starten** van de proefversie gaat u naar de app in CodePen. De app dient als minimaal voorbeeld voor het ophalen van JSON-gegevens met JavaScript. De voorbeeld-app is ontworpen om JSON-inhoud te renderen die wordt geretourneerd, ongeacht de structuur van het onderliggende model van inhoudsfragment. De app haalt gegevens op van een `aem-demo-assets` persisted query die is opgenomen in uw testomgeving. U moet een JSON-respons zien die vergelijkbaar is met het volgende:

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

Als u in plaats daarvan een fout ziet, controleer de browser console voor meer detail of bereik uit [op Slack](https://adobe-dx-support.slack.com).

Nu u een beetje over CodePen kent, zult u dan app vormen om gegevens van de voortgezette vraag te halen u in een vorige module creeerde.

## JavaScript-code doorlopen {#code-walkthrough}

De **JS** aan de rechterkant in CodePen bevat de Javascript-code van de voorbeeld-app. Vanaf regel 2 importeren we de AEM Headless Client voor JavaScript vanuit de Skypack CDN. Skypack wordt gebruikt om ontwikkeling zonder een bouwstijlstap te vergemakkelijken, maar u kunt de Zwaarloze Cliënt van de AEM met NPM of van de Garde in uw eigen projecten ook gebruiken. Bekijk de gebruiksinstructies in het dialoogvenster [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) voor nadere bijzonderheden .

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

Op regel 6 lezen we uw publicatiehostgegevens van de `publishHost` queryparameter. Dit is de host waarop de AEM Headless-client gegevens kan ophalen. Dit wordt doorgaans gecodeerd in uw app, maar we gebruiken een queryparameter om het voor de CodePen-app eenvoudiger te maken met verschillende omgevingen te werken.

Wij vormen de Zwaarloze Cliënt van de AEM op lijn 12:

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
>De **serviceURL** is ingesteld om een Adobe IO-runtime-proxyfunctie te gebruiken om CORS-problemen te voorkomen. Dit is niet vereist voor uw eigen projecten, maar is vereist voor de CodePen-app voor uw testomgeving. De volmachtsfunctie wordt gevormd om te gebruiken **publishHost** waarde die is opgegeven in de queryparameter.

Ten slotte, de functie `fetchJsonFromGraphQL()` wordt gebruikt om het ophaalverzoek uit te voeren gebruikend de Zwaarloze Cliënt van de AEM. Deze wordt telkens aangeroepen wanneer de code wordt gewijzigd of kan worden geactiveerd door op de knop **Herstellen** koppeling. De werkelijke `aemHeadlessClient.runPersistedQuery(..)` de vraag komt op lijn 34 voor. Een beetje later gaan we een wijziging aanbrengen in de manier waarop deze JSON-gegevens worden weergegeven, maar voorlopig zullen we deze alleen afdrukken op de `#output` div gebruiken `resultToPreTag(queryResult)` functie.

## Gegevens ophalen van uw permanente query {#use-persisted-query}

Op regel 25 geven we aan van welke GraphQL de query blijft uitvoeren waarvan de app gegevens moet ophalen. De voortgeduurde vraagnaam is een combinatie van de naam van het eindpunt (dat wil zeggen. `your-project` of `aem-demo-assets`), gevolgd door een slash en vervolgens de naam van de query. Als u de eerdere moduleinstructies precies hebt gevolgd, bevindt de voortgezette query die u hebt gemaakt zich in het dialoogvenster `your-project` eindpunt.

1. Werk de `persistedQueryName` variabele om de voortgezette vraag te gebruiken u in de vorige module creeerde. Als u de naamgevingssuggestie hebt gevolgd, hebt u een doorlopende query met de naam `adventure-list` in de `your-project` en u zou het `persistedQueryName` variabele tot `your-project/adventure-list`:

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. Zodra deze wijziging is aangebracht, moet de app automatisch vernieuwen en de onbewerkte JSON-reactie van uw aanhoudende query afdrukken naar de `#output` div. Als u een foutenmelding ziet, controleer de console voor extra details. Bereik uit [op Slack](https://adobe-dx-support.slack.com) als er nog problemen zijn met deze stap.

1. Bevat deze JSON precies de eigenschappen die uw app nodig heeft? Indien niet, ga terug naar de [Inhoud extraheren met de GraphQL API](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql) leergids om wijzigingen aan te brengen. Vergeet niet om uw vraag te bewaren en te publiceren zodra u wordt gedaan.

## De JSON-rendering wijzigen {#change-rendering}

De JSON wordt &#39;as-is&#39; weergegeven in een `pre` tag , die niet erg creatief is . Wij kunnen onze CodePen veranderen om te gebruiken `resultToDom()` in plaats daarvan om te illustreren hoe de JSON-reactie kan worden herhaald om een interessanter resultaat te maken.

1. Als u deze wijziging wilt aanbrengen, markeert u regel 37 en verwijdert u de opmerking uit regel 40:

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. Met deze functie worden ook alle afbeeldingen gerenderd die als een `img` tag. Als de **Adventure** als de door u gemaakte inhoudsfragmenten geen afbeeldingen bevatten, kunt u proberen om te schakelen om de `aem-demo-assets/adventures-all` voortgezette vraag door lijn 25 te wijzigen:

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

Deze query levert een JSON-reactie op die afbeeldingen bevat, en de `resultToDom()` Deze functie geeft ze inline weer.

![Resultaat van de adventures-all-query en de resultToDom-renderfunctie](assets/do-not-localize/adventures-all-query-result.png)

Nu u het werk hebt gedaan om de modellen en vragen te bouwen, kan uw inhoudsteam gemakkelijk overnemen. In de volgende module wordt de stroom van de inhoudsauteur weergegeven.
