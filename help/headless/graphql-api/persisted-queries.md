---
title: Blijvende GraphQL-query's
description: Leer hoe u GraphQL-query's in Adobe Experience Manager as a Cloud Service kunt voortzetten om de prestaties te optimaliseren. De aanhoudende vragen kunnen door cliënttoepassingen worden gevraagd gebruikend de methode van de GET van HTTP en de reactie kan bij de verzender en lagen worden in het voorgeheugen ondergebracht CDN, die uiteindelijk de prestaties van de cliënttoepassingen verbeteren.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 9bfb5bc4b340439fcc34e97f4e87d711805c0d82
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 0%

---

# Blijvende GraphQL-query&#39;s {#persisted-queries-caching}

Blijvende query&#39;s zijn GraphQL query&#39;s die worden gemaakt en opgeslagen op de Adobe Experience Manager (AEM) as a Cloud Service server. Ze kunnen worden aangevraagd met een GET-aanvraag door clienttoepassingen. De reactie van een verzoek van de GET kan bij de verzender en lagen CDN in het voorgeheugen ondergebracht worden, die uiteindelijk de prestaties van de het verzoeken cliënttoepassing verbeteren. Dit verschilt van standaard GraphQL query&#39;s, die worden uitgevoerd met behulp van POST-aanvragen waarbij de reactie niet gemakkelijk in cache kan worden geplaatst.

>[!NOTE]
>
>Blijvende query&#39;s worden aanbevolen. Zie [Aanbevolen werkwijzen voor GraphQL-query (Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) voor details, en de verwante configuratie van de Verzender.

De [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md) is beschikbaar in AEM voor u om uw GraphQL-query&#39;s te ontwikkelen, te testen en voort te zetten voordat [overbrengen naar uw productieomgeving](#transfer-persisted-query-production). Voor gevallen die aanpassing vereisen (bijvoorbeeld wanneer [cache aanpassen](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) u kunt de API gebruiken; zie het curvevoorbeeld in [Een GraphQL-query laten doorgaan](#how-to-persist-query).

## Blijvende query&#39;s en eindpunten {#persisted-queries-and-endpoints}

De aanhoudende vragen moeten altijd het eindpunt met betrekking tot [geschikte configuratie Sites](graphql-endpoint.md); zodat ze beide of beide kunnen gebruiken:

* De globale configuratie en het eindpunt de vraag heeft toegang tot alle Modellen van het Fragment van de Inhoud.
* De specifieke configuratie(s) van Plaatsen en eindpunt(s) Creërend een persisted vraag voor een specifieke configuratie van Plaatsen vereist een overeenkomstig plaats-configuratie-specifiek eindpunt (om toegang tot de verwante Modellen van het Fragment van de Inhoud te verlenen).
Bijvoorbeeld, om een voortgeduurde vraag specifiek voor de configuratie van Plaatsen te creëren WKND, moet een overeenkomstige WKND-Specifieke configuratie van Plaatsen, en een WKND-Specifiek eindpunt vooraf worden gecreeerd.

>[!NOTE]
>
>Zie [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) voor meer informatie .
>
>De **Aangehouden GraphQL-query&#39;s** moet worden toegelaten, voor de aangewezen configuratie van Plaatsen.

Als er bijvoorbeeld een bepaalde query wordt uitgevoerd, `my-query`, die een model gebruikt `my-model` vanuit de configuratie Sites `my-conf`:

* U kunt een query maken met de opdracht `my-conf` specifiek eindpunt, en dan zal de vraag als volgt worden bewaard:
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* U kunt dezelfde query maken met `global` eindpunt, maar dan zal de vraag als volgt worden bewaard:
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Dit zijn twee verschillende query&#39;s die zijn opgeslagen onder verschillende paden.
>
>Ze gebruiken gewoon hetzelfde model, maar via verschillende eindpunten.

## Een GraphQL-query laten doorgaan {#how-to-persist-query}

Aanbevolen wordt om query&#39;s in een AEM ontwerpomgeving in eerste instantie voort te zetten en vervolgens [de query overdragen](#transfer-persisted-query-production) naar uw productie AEM publicatieomgeving, voor gebruik door toepassingen.

Er zijn verschillende methoden om query&#39;s te blijven uitvoeren, waaronder:

* GraphiQL IDE - zie [Blijvende query&#39;s opslaan](/help/headless/graphql-api/graphiql-ide.md#saving-persisted-queries) (voorkeursmethode)
* krullen - zie het volgende voorbeeld
* Andere gereedschappen, inclusief [Postman](https://www.postman.com/)

GraphiQL IDE is de **voorkeur** methode voor het voortduren van vragen. Om een bepaalde vraag voort te zetten gebruikend **krullen** opdrachtregelgereedschap:

1. Bereid de vraag door PUTing het aan het nieuwe eindpunt URL voor `/graphql/persist.json/<config>/<persisted-label>`.

   Maak bijvoorbeeld een doorlopende query:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. Controleer nu het antwoord.

   Controleer bijvoorbeeld of het programma is gelukt:

   ```json
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. U kunt de voortgezette vraag dan verzoeken door URL te winnen `/graphql/execute.json/<shortPath>`.

   Gebruik bijvoorbeeld de voortgezette query:

   ```shell
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Werk een voortgezette vraag door POSTing aan een reeds bestaand vraagweg bij.

   Gebruik bijvoorbeeld de voortgezette query:

   ```shell
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Een onbewerkte query maken.

   Bijvoorbeeld:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Creeer een verpakte onbewerkte vraag met geheim voorgeheugencontrole.

   Bijvoorbeeld:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Maak een doorlopende query met parameters:

   Bijvoorbeeld:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```


## Hoe te om een Verlengde vraag uit te voeren {#execute-persisted-query}

Een clienttoepassing vraagt een aanvraag tot GET met de volgende syntaxis uit om een query met behoud van waarden uit te voeren:

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Wanneer `PERSISTENT_PATH` is een verkort pad naar de opslaglocatie van de Persisted-query.

1. Bijvoorbeeld `wknd` is de configuratienaam en `plain-article-query` is de naam van de Persisted-query. De query uitvoeren:

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. Een query uitvoeren met parameters.

   >[!NOTE]
   >
   > De variabelen en de waarden van de vraag moeten behoorlijk zijn [gecodeerd](#encoding-query-url) bij het uitvoeren van een blijvende query.

   Bijvoorbeeld:

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Zie gebruiken [queryvariabelen](#query-variables) voor meer informatie .

## Query-variabelen gebruiken {#query-variables}

De variabelen van de vraag kunnen met Verblijfsde Vragen worden gebruikt. De vraagvariabelen worden toegevoegd aan het verzoek vooraf bepaald met een puntkomma (`;`) met de naam en de waarde van de variabele. Meerdere variabelen worden gescheiden door puntkomma&#39;s.

Het patroon ziet er als volgt uit:

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

De volgende query bevat bijvoorbeeld een variabele `activity` een lijst filteren op basis van een activiteitwaarde:

```graphql
query getAdventuresByActivity($activity: String!) {
      adventureList (filter: {
        adventureActivity: {
          _expressions: [
            {
              value: $activity
            }
          ]
        }
      }){
        items {
          _path
        adventureTitle
        adventurePrice
        adventureTripLength
      }
    }
  }
```

Deze query kan worden uitgevoerd onder een pad `wknd/adventures-by-activity`. Om de Permanente vraag te roepen waar `activity=Camping` het verzoek zou er als volgt uitzien :

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

Let op: `%3B` is de UTF-8-codering voor `;` en `%3D` is de codering voor `=`. De vraagvariabelen en om het even welke speciale karakters moeten [correct gecodeerd](#encoding-query-url) voor de Persisted query die moet worden uitgevoerd.

## Door uw doorlopende query&#39;s in cache te plaatsen {#caching-persisted-queries}

Aanbevolen wordt om query&#39;s door te voeren omdat deze in het cachegeheugen kunnen worden opgeslagen bij de verzender- en CDN-lagen, waardoor de prestaties van de toepassing die de aanvraag indient uiteindelijk verbeteren.

Standaard maakt AEM de CDN-cache (Content Delivery Network) ongeldig op basis van een standaardtijd tot live (TTL).

Deze waarde is ingesteld op:

* 7200 seconden is standaardTTL voor de Verzender en CDN; ook bekend als *gedeelde cache*
   * standaard: s-maxage=7200
* 60 is standaard TTL voor de cliënt (bijvoorbeeld, browser)
   * standaard: maxage=60

Als u TTL voor uw vraag wilt veranderen GraphLQ, dan moet de vraag of zijn:

* aanhouden na het beheren van de [HTTP Cache headers - van GraphQL IDE](#http-cache-headers)
* blijft bestaan met de [API-methode](#cache-api).

### HTTP-cachekoppen beheren in GraphQL  {#http-cache-headers-graphql}

GraphiQL IDE - zie [Blijvende query&#39;s opslaan](/help/headless/graphql-api/graphiql-ide.md#managing-cache)

### Cache beheren vanuit de API {#cache-api}

Dit impliceert het posten van de vraag aan AEM gebruikend CURL in uw interface van de bevellijn.

Een voorbeeld:

```xml
curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "https://publish-p123-e456.adobeaemcloud.com/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

De `cache-control` kan worden ingesteld tijdens het maken (PUT) of later (bijvoorbeeld via een aanvraag voor een POST). Het cache-control is optioneel wanneer u de aanhoudend query maakt, omdat AEM de standaardwaarde kan opgeven. Zie [Een GraphQL-query laten doorgaan](/help/headless/graphql-api/persisted-queries.md#how-to-persist-query), bijvoorbeeld om een vraag voort te zetten gebruikend krullen.

## De URL van de query coderen voor gebruik door een app {#encoding-query-url}

Voor gebruik door een toepassing worden speciale tekens gebruikt bij het samenstellen van queryvariabelen (dus puntkomma&#39;s (`;`), gelijkteken (`=`), slashes `/`) moet worden omgezet om de overeenkomstige UTF-8-codering te gebruiken.

Bijvoorbeeld:

```xml
curl -X GET \ "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

De URL kan worden opgesplitst in de volgende onderdelen:

| URL-onderdeel | Beschrijving |
|----------| -------------|
| `/graphql/execute.json` | Blijvend vraageindpunt |
| `/wknd/adventure-by-path` | Pad voor permanente query |
| `%3B` | Codering van `;` |
| `adventurePath` | Query-variabele |
| `%3D` | Codering van `=` |
| `%2F` | Codering van `/` |
| `%2Fcontent%2Fdam...` | Gecodeerd pad naar het inhoudsfragment |

In onbewerkte tekst ziet de aanvraag-URI er als volgt uit:

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

Als u een voortgezette query in een client-app wilt gebruiken, moet de SDK van de client zonder kop worden gebruikt voor [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java), of [NodeJS](https://github.com/adobe/aem-headless-client-nodejs). De Headless Client SDK codeert alle queryvariabelen automatisch naar behoren in de aanvraag.

## Het overbrengen van een blijvende vraag aan uw milieu van de Productie  {#transfer-persisted-query-production}

Verblijfsde vragen zouden altijd op de dienst van de Auteur AEM moeten worden gecreeerd en dan gepubliceerd (herhaald) aan de dienst van de Publicatie AEM. Vaak, worden de Persisted vragen gecreeerd en op lagere milieu&#39;s zoals lokale of milieu&#39;s van de Ontwikkeling getest. Het is dan noodzakelijk om Verlengde vragen aan hogere niveaumilieu&#39;s te bevorderen, die hen uiteindelijk op een productieAEM publiceren milieu voor cliënttoepassingen ter beschikking stellen om te verbruiken.

### Voorbehouden query&#39;s verpakken

De blijvende vragen kunnen in worden gebouwd [AEM](/help/implementing/developing/tools/package-manager.md). AEM pakketten kunnen vervolgens worden gedownload en geïnstalleerd in verschillende omgevingen. AEM Pakketten kunnen ook worden gerepliceerd vanuit een AEM-auteuromgeving naar een AEM-publicatieomgeving.

Een pakket maken:

1. Navigeren naar **Gereedschappen** > **Implementatie** > **Pakketten**.
1. Een nieuw pakket maken door te tikken **Pakket maken**. Hiermee wordt een dialoogvenster geopend waarin het pakket wordt gedefinieerd.
1. In het dialoogvenster Pakketdefinitie, onder **Algemeen** Voer een **Naam** zoals &quot;wknd-persistent-questions&quot;.
1. Voer een versienummer in, bijvoorbeeld &quot;1.0&quot;.
1. Onder **Filters** een nieuwe **Filter**. Gebruik de Finder van de Weg om te selecteren `persistentQueries` onder de configuratie. Bijvoorbeeld voor de `wknd` configuratie het volledige weg zal zijn `/conf/wknd/settings/graphql/persistentQueries`.
1. Tikken **Opslaan** om de nieuwe pakketdefinitie op te slaan en het dialoogvenster te sluiten.
1. Tik op de knop **Opbouwen** in de nieuw gecreëerde definitie van het Pakket.

Nadat het pakket is gemaakt, kunt u:

* **Downloaden** het pakket en heruploaden in een andere omgeving.
* **Repliceren** het pakket door te tikken **Meer** > **Repliceren**. Hierdoor wordt het pakket gerepliceerd naar de verbonden AEM-publicatieomgeving.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
