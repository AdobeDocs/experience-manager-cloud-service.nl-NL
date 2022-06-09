---
title: Blijvende query's voor GraphQL
description: Leer hoe u GraphQL-query's in Adobe Experience Manager as a Cloud Service kunt voortzetten om de prestaties te optimaliseren. De aanhoudende vragen kunnen door cliënttoepassingen worden gevraagd gebruikend de methode van de GET van HTTP en de reactie kan bij de verzender en lagen worden in het voorgeheugen ondergebracht CDN, die uiteindelijk de prestaties van de cliënttoepassingen verbeteren.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 2ee21b507b5dcc9471063b890976a504539b7e10
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 1%

---

# Blijvende query&#39;s voor GraphQL {#persisted-queries-caching}

De gepersisteerde vragen zijn vragen GraphQL die op de as a Cloud Service server van Adobe Experience Manager (AEM) worden gecreeerd en worden opgeslagen. Ze kunnen worden aangevraagd met een GET-aanvraag door clienttoepassingen. De reactie van een verzoek van de GET kan bij de verzender en lagen CDN in het voorgeheugen ondergebracht worden, die uiteindelijk de prestaties van de het verzoeken cliënttoepassing verbeteren. Dit verschilt van standaardvragen GraphQL, die gebruikend POST verzoeken worden uitgevoerd waar de reactie niet gemakkelijk in het voorgeheugen kan worden opgeslagen.

De [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md) is beschikbaar in AEM voor u om, uw vragen te ontwikkelen te testen en voort te zetten GraphQL, alvorens [overbrengen naar uw productieomgeving](#transfer-persisted-query-production). Voor gevallen die aanpassing vereisen (bijvoorbeeld wanneer [cache aanpassen](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) u kunt de API gebruiken; zie het curvevoorbeeld in [Hoe te om een vraag te handhaven GraphQL](#how-to-persist-query).

## Blijvende query&#39;s en eindpunten {#persisted-queries-and-endpoints}

De aanhoudende vragen moeten altijd het eindpunt met betrekking tot [geschikte configuratie Sites](graphql-endpoint.md); zodat ze beide of beide kunnen gebruiken:

* De globale configuratie en het eindpunt de vraag heeft toegang tot alle Modellen van het Fragment van de Inhoud.
* De specifieke configuratie(s) van Plaatsen en eindpunt(s) Creërend een persisted vraag voor een specifieke configuratie van Plaatsen vereist een overeenkomstig plaats-configuratie-specifiek eindpunt (om toegang tot de verwante Modellen van het Fragment van de Inhoud te verlenen).
Bijvoorbeeld, om een voortgeduurde vraag specifiek voor de configuratie van Plaatsen te creëren WKND, moet een overeenkomstige WKND-Specifieke configuratie van Plaatsen, en een WKND-Specifiek eindpunt vooraf worden gecreeerd.

>[!NOTE]
>
>Zie [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) voor meer informatie .
>
>De **GrafiekQL blijvende vragen** moet worden toegelaten, voor de aangewezen configuratie van Plaatsen.

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

## Hoe te om een vraag te handhaven GraphQL {#how-to-persist-query}

Aanbevolen wordt om query&#39;s in een AEM ontwerpomgeving in eerste instantie voort te zetten en vervolgens [de query overdragen](#transfer-persisted-query-production) naar uw productie AEM publicatieomgeving, voor gebruik door toepassingen.

Er zijn verschillende methoden om query&#39;s te blijven uitvoeren, waaronder:

* GraphiQL IDE - zie [Blijvende query&#39;s opslaan](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries)
* krullen - zie het volgende voorbeeld
* Andere gereedschappen, inclusief [Postman](https://www.postman.com/)

Hier zijn de stappen om een bepaalde vraag voort te zetten gebruikend **krullen** opdrachtregelgereedschap:

1. Bereid de vraag door PUTing het aan het nieuwe eindpunt URL voor `/graphql/persist.json/<config>/<persisted-label>`.

   Maak bijvoorbeeld een doorlopende query:

   ```xml
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

   ```xml
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

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Werk een voortgezette vraag door POSTing aan een reeds bestaand vraagweg bij.

   Gebruik bijvoorbeeld de voortgezette query:

   ```xml
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

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Creeer een verpakte onbewerkte vraag met geheim voorgeheugencontrole.

   Bijvoorbeeld:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Maak een doorlopende query met parameters:

   Bijvoorbeeld:

   ```xml
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

1. Een query uitvoeren met parameters.

   Bijvoorbeeld:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

## Het overbrengen van een blijvende vraag aan uw milieu van de Productie  {#transfer-persisted-query-production}

Uiteindelijk moet uw persisted query zich in uw productie-publicatieomgeving bevinden (van AEM as a Cloud Service), waar deze kan worden aangevraagd door clienttoepassingen. Als u een aanhoudende query wilt gebruiken in uw publicatieomgeving voor productie, moet de verwante permanente structuur worden gerepliceerd:

* aanvankelijk aan productieauteur voor het bevestigen van onlangs authored inhoud met de vragen,
* vervolgens ten slotte de productie publiceren voor levende consumptie

Er zijn verscheidene benaderingen om uw persisted vraag over te brengen:

1. Een pakket gebruiken:
   1. Maak een nieuwe pakketdefinitie.
   1. De configuratie opnemen (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).
   1. Maak het pakket.
   1. Breng het pakket over (downloaden/uploaden of repliceren).
   1. Installeer het pakket.

1. Een POST voor replicatie gebruiken:

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->

Zodra de vraagconfiguratie op uw publiceer milieu in productie is, zijn de zelfde authentificatiebeginselen van toepassing, enkel gebruikend het publiceereindpunt.

>[!NOTE]
>
>Voor anonieme toegang veronderstelt het systeem dat ACL &quot;iedereen&quot;toestaat om toegang tot de vraagconfiguratie te hebben.
>
>Als dat niet het geval is, zal het niet kunnen uitvoeren.

## De URL van de query coderen voor gebruik door een app {#encoding-query-url}

Voor gebruik door een toepassing moeten eventuele puntkomma&#39;s (&quot;;&quot;) in de URL&#39;s worden gecodeerd.

Bijvoorbeeld, zoals in het verzoek om een voortgezette vraag uit te voeren:

```xml
curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
```

Als u een voortgezette query in een client-app wilt gebruiken, moet de SDK van de client zonder kop worden gebruikt [AEM headless-client voor JavaScript](https://github.com/adobe/aem-headless-client-js).