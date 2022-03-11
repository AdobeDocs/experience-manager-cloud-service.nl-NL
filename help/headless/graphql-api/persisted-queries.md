---
title: Blijvende query's voor GraphQL
description: Leer hoe u GraphQL-query's in Adobe Experience Manager kunt voortzetten om de prestaties te optimaliseren. De aanhoudende vragen kunnen door cliënttoepassingen worden gevraagd gebruikend de methode van de GET van HTTP en de reactie kan bij de verzender en lagen worden in het voorgeheugen ondergebracht CDN, die uiteindelijk de prestaties van de cliënttoepassingen verbeteren.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 1%

---

# Blijvende query&#39;s voor GraphQL {#persisted-queries-caching}

De gepersisteerde vragen zijn vragen GraphQL die op de AEM server worden gecreeerd en worden opgeslagen. De standaard vragen GraphQL worden uitgevoerd gebruikend de verzoeken van de POST en de reactie kan niet gemakkelijk in het voorgeheugen onder worden gebracht. Blijvende query&#39;s kunnen worden aangevraagd met een GET-aanvraag door clienttoepassingen. De reactie van een verzoek van de GET kan bij de verzender en lagen CDN in het voorgeheugen ondergebracht worden, die uiteindelijk de prestaties van de het verzoeken cliënttoepassing verbeteren.

De aanhoudende vragen moeten altijd het eindpunt met betrekking tot [geschikte configuratie Sites](graphql-endpoint.md); zodat ze beide of beide kunnen gebruiken:

* De globale configuratie en het eindpunt de vraag heeft toegang tot alle Modellen van het Fragment van de Inhoud.
* De specifieke configuratie(s) van Plaatsen en eindpunt(s) Creërend een persisted vraag voor een specifieke configuratie van Plaatsen vereist een overeenkomstig plaats-configuratie-specifiek eindpunt (om toegang tot de verwante Modellen van het Fragment van de Inhoud te verlenen).
Bijvoorbeeld, om een voortgeduurde vraag specifiek voor de configuratie van Plaatsen te creëren WKND, moet een overeenkomstige WKND-Specifieke configuratie van Plaatsen, en een WKND-Specifiek eindpunt vooraf worden gecreeerd.

>[!NOTE]
>
>Zie [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) voor meer informatie .
>
>De **GraphQL-vragen over persistentie** moet worden toegelaten, voor de aangewezen configuratie van Plaatsen.

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

## Hoe te om een vraag te handhaven GraphQL

Aanbevolen wordt om query&#39;s in een AEM ontwerpomgeving in eerste instantie voort te zetten en vervolgens [de query publiceren](#publish-persisted-query) naar een AEM publicatieomgeving. Gereedschappen zoals [Postman](https://www.postman.com/) of opdrachtregelprogramma&#39;s zoals [krullen](https://curl.se/) kan worden gebruikt.

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

## Een voortgezette query publiceren {#publish-persisted-query}

Persisted query&#39;s kunnen worden gepubliceerd naar een AEM-publicatieomgeving waar ze kunnen worden aangevraagd door clienttoepassingen. Om een persisted query bij het publiceren te gebruiken, moet de verwante blijvende boomstructuur worden gerepliceerd.

Er zijn verscheidene benaderingen voor het publiceren van een persisted vraag:

* **Een POST gebruiken voor replicatie**:

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

* **Een pakket gebruiken**:
   1. Maak een nieuwe pakketdefinitie.
   1. De configuratie opnemen (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).
   1. Maak het pakket.
   1. Herhaal het pakket.

* **Gereedschap replicatie/distributie gebruiken**:
   1. Ga naar het gereedschap Distributie.
   1. Selecteer boomactivering voor de configuratie (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).

* **Een workflow gebruiken (via configuratie voor het starten van een workflow)**:
   1. Definieer een workflowstartregel voor het uitvoeren van een workflowmodel dat de configuratie van verschillende gebeurtenissen zou repliceren (bijvoorbeeld, maken, wijzigen, enz.).

Zodra de vraagconfiguratie is op publiceren, zijn de zelfde authentificatiebeginselen van toepassing, enkel gebruikend het publiceereindpunt.

>[!NOTE]
>
>Voor anonieme toegang veronderstelt het systeem dat ACL &quot;iedereen&quot;toestaat om toegang tot de vraagconfiguratie te hebben.
>
>Als dat niet het geval is, zal het niet kunnen uitvoeren.

>[!NOTE]
>
>Eventuele puntkomma&#39;s (&quot;;&quot;) in de URL&#39;s moeten worden gecodeerd.
>
>Bijvoorbeeld, zoals in het verzoek om een voortgezette vraag uit te voeren:
>
>
```xml
>curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
>```
