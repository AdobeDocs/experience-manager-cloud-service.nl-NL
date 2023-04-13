---
title: JSON-inhoud ophalen met JavaScript
description: Ontdek het ophalen van JSON-inhoud uit uw testomgeving met een CodePen-app en de AEM Headless Client voor JavaScript.
hidefromtoc: true
index: false
source-git-commit: 3aff5ef2fb9ecdd815f0bc1a813d3a3982b4e0ed
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# JSON-inhoud ophalen met JavaScript {#fetch-json}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="JSON-inhoud ophalen met JavaScript"
>abstract="Ontdek het ophalen van JSON-inhoud uit uw testomgeving met een CodePen-app en de AEM Headless Client voor JavaScript."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="De voorbeeldtoepassing CodePen starten"
>abstract="We hebben een minimale CodePen-app samengesteld om het ophalen van JSON-gegevens uit uw testomgeving te introduceren met behulp van GraphQL persisted query&#39;s.<br><br>Start het voorbeeld CodePen door hieronder te klikken en volg deze handleiding voor meer informatie."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="In deze module hebt u geleerd hoe u de AEM Headless Client voor JavaScript kunt gebruiken om JSON-gegevens op te halen uit uw testomgeving met behulp van GraphQL persisted query&#39;s.<br><br>Nu begrijpt u hoe u deze client kunt gebruiken om gegevens te verbruiken vanuit uw eigen webtoepassing."
>abstract=""

## Inleiding {#intro}

U begint in de app CodePen, die als minimaal voorbeeld dient voor het ophalen van JSON-gegevens met behulp van de [AEM headless-client voor JavaScript](https://github.com/adobe/aem-headless-client-js). De voorbeeld-app is ontworpen om JSON-inhoud te renderen die wordt geretourneerd, ongeacht de structuur van het onderliggende inhoudsfragmentmodel. De toepassing CodePen probeert uitgebreid te zijn met eventuele fouten die worden aangetroffen. Het volgende foutbericht wordt dus afgedrukt in het onderste venster van de app:

```
{
  "status": "Failed to fetch persisted query: your-project/USE-YOUR-QUERY-HERE from publishHost: https://publish-p00000-e12345.adobeaemcloud.com",
  "message": "[AEMHeadless:REQUEST_ERROR] General Request error: Failed to fetch."
}
```

Deze fout wordt verwacht, aangezien app nog niet wordt gevormd om de persisted vraag te gebruiken die u in een vorige module bewaarde en publiceerde. U configureert de app in de volgende stappen om gegevens van uw specifieke query op te halen.

## Codepenanalyse {#code-walkthrough}

Het deelvenster JS (Javascript) op CodePen bevat de hersenen van de voorbeeld-app. Vanaf regel 2 importeren we de AEM Headless Client voor JavaScript vanuit de Skypack CDN. Skypack wordt gebruikt om ontwikkeling zonder een bouwstijlstap te vergemakkelijken, maar u kunt de Zwaarloze Cliënt van de AEM met NPM of van de Garde in uw eigen projecten ook gebruiken. Bekijk de gebruiksinstructies in het dialoogvenster [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) voor nadere bijzonderheden .

```
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

Op regel 6 lezen we uw publicatiehostgegevens van de `publishHost` queryparameter. Dit is de host waarop de AEM Headless-client gegevens kan ophalen. Dit wordt doorgaans gecodeerd in uw app, maar we gebruiken een queryparameter om het voor de CodePen-app eenvoudiger te maken met verschillende omgevingen te werken.

Wij vormen de Zwaardeloze Cliënt van de AEM op lijn 12 om een volmachtAdobe IO Runtime functie te gebruiken om CORS kwesties te vermijden. Dit is niet vereist voor uw eigen projecten, maar is vereist voor de CodePen-app voor uw testomgeving. De volmachtsfunctie wordt gevormd om te gebruiken `publishHost` waarde die is opgegeven in de queryparameter.

```
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

Ten slotte, de functie `fetchJsonFromGraphQL()` wordt gebruikt om het ophaalverzoek uit te voeren gebruikend de Zwaarloze Cliënt van de AEM. Deze wordt telkens aangeroepen wanneer de code wordt gewijzigd, of kan worden geactiveerd door op de koppeling &quot;Herstellen&quot; te drukken. De werkelijke `aemHeadlessClient.runPersistedQuery(..)` de vraag komt op lijn 34 voor. Een beetje later gaan we een wijziging aanbrengen in de manier waarop deze JSON-gegevens worden weergegeven, maar voorlopig zullen we deze alleen afdrukken op de `#output` div gebruiken `resultToPreTag(queryResult)` functie.

## Gegevens ophalen uit uw aanhoudende query {#use-persisted-query}

Op regel 25 geven we aan van welke GraphQL de query blijft uitvoeren waarvan de app gegevens moet ophalen. De persisted querynaam is een combinatie van de naam van het project (dat wil zeggen: `your-project`), gevolgd door een slash en vervolgens de naam van de query.

Werk de `persistedQueryName` variabele om de voortgezette vraag te gebruiken u in de vorige module creeerde. Als u de suggestie voor naamgeving hebt gevolgd, hebt u een doorlopende query met de naam `adventures` in de `your-project` en u zou de `persistedQueryName` variabele tot `your-project/adventures`:

```
//
// TODO: Use your persisted query here
//
persistedQueryName = 'your-project/adventures';
```

Zodra deze wijziging is aangebracht, moet de app automatisch vernieuwen en de onbewerkte JSON-reactie van uw aanhoudende query afdrukken naar de `#output` div. Als u een foutenmelding ziet, controleer de console voor extra details.

Bevat deze JSON precies de eigenschappen die uw app nodig heeft? Als dat niet het geval is, ga dan terug naar uw AEM-auteuromgeving, Tools, GraphQL Query Editor (of navigeer naar de `/aem/graphiql.html` (pad) en breng wijzigingen aan in uw voortgezette query. Vergeet niet om de vraag te bewaren en te publiceren zodra u wordt gedaan.

## De JSON-rendering wijzigen {#change-rendering}

De JSON wordt momenteel &#39;as-is&#39; gerenderd in een `pre` tag , die niet erg creatief is . Wij kunnen onze CodePen veranderen om te gebruiken `resultToDom()` in plaats daarvan om te illustreren hoe de JSON-reactie kan worden herhaald om een interessanter resultaat te maken.

Als u deze wijziging wilt aanbrengen, markeert u regel 37 en verwijdert u de opmerking uit regel 40:

```
// Output the results to a pre tag
//resultToPreTag(queryResult);

// Alternatively, build a colorful div structure with the JSON results and render images inline
resultToDom(queryResult);
```

Met deze functie worden ook alle afbeeldingen gerenderd die als een `img` tag. Als de &#39;Adventure&#39;-inhoudsfragmenten die u hebt gemaakt geen afbeeldingen bevatten, kunt u proberen over te schakelen om de `aem-demo-assets/adventures-all` voortgezette vraag door lijn 25 te wijzigen:

```
persistedQueryName = 'aem-demo-assets/adventures-all';
```

Deze query levert een JSON-reactie op die afbeeldingen bevat, en de `resultToDom()` Deze functie geeft ze inline weer.

![Resultaat van de adventures-all-query en de resultToDom-renderfunctie](assets/do-not-localize/adventures-all-query-result.png)
