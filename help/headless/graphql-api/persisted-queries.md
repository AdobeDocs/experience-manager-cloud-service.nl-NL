---
title: Blijvende GraphQL-query's
description: Leer hoe u GraphQL-query's in Adobe Experience Manager as a Cloud Service kunt voortzetten voor optimale prestaties. Blijvende query's kunnen worden aangevraagd door clienttoepassingen met de HTTP GET-methode en de reactie kan in de cache worden geplaatst bij de verzender- en CDN-lagen, waardoor de prestaties van de clienttoepassingen uiteindelijk worden verbeterd.
feature: Headless, Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
role: Admin, Developer
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 0%

---

# Blijvende GraphQL-query&#39;s {#persisted-graphql-queries}

Blijvende query&#39;s zijn GraphQL-query&#39;s die zijn gemaakt en opgeslagen op de Adobe Experience Manager (AEM) as a Cloud Service-server. Ze kunnen worden aangevraagd met een GET-aanvraag door clienttoepassingen. De reactie van een GET-verzoek kan in de cache worden geplaatst bij de verzender- en CDN-lagen, waardoor de prestaties van de client-toepassing die het verzoek indient, uiteindelijk worden verbeterd. Dit verschilt van standaard GraphQL query&#39;s, die worden uitgevoerd met POST-verzoeken waarbij de reactie niet gemakkelijk in cache kan worden geplaatst.

>[!NOTE]
>
>Blijvende query&#39;s worden aanbevolen. Zie [ Beste praktijken van de Vraag van GraphQL (Dispatcher) ](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) voor details, en de verwante configuratie van Dispatcher.

[ IDE GraphiQL ](/help/headless/graphql-api/graphiql-ide.md) is beschikbaar in AEM voor u om, uw vragen van GraphQL te ontwikkelen te testen en voort te zetten, alvorens [ over te brengen naar uw productiemilieu ](#transfer-persisted-query-production). Voor gevallen die aanpassing (bijvoorbeeld, wanneer [ het geheime voorgeheugen ](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries) aanpassen) nodig hebben kunt u API gebruiken; zie het cURL voorbeeld dat in [ wordt verstrekt hoe te om een vraag van GraphQL ](#how-to-persist-query) voort te zetten.

## Blijvende query&#39;s en eindpunten {#persisted-queries-and-endpoints}

De aangehouden vragen moeten altijd het eindpunt met betrekking tot de [ aangewezen configuratie van Plaatsen ](graphql-endpoint.md) gebruiken; zodat kunnen zij of, of allebei gebruiken:

* De globale configuratie en het eindpunt
De query heeft toegang tot alle modellen van inhoudsfragmenten.
* Specifieke configuratie(s) en eindpunt(en) van sites
Creërend een persisted vraag voor een specifieke configuratie van Plaatsen vereist een overeenkomstig plaats-configuratie-specifiek eindpunt (om toegang tot de verwante Modellen van het Fragment van de Inhoud te verlenen).
Bijvoorbeeld, om een voortgeduurde vraag specifiek voor de configuratie van Plaatsen te creëren WKND, moet een overeenkomstige WKND-Specifieke configuratie van Plaatsen, en een WKND-Specifiek eindpunt vooraf worden gecreeerd.

>[!NOTE]
>
>Zie [ Functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie ](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) voor meer details toelaten.
>
>De **GraphQL Persisted Vragen** moeten worden toegelaten, voor de aangewezen configuratie van Plaatsen.

Als er bijvoorbeeld een bepaalde query met de naam `my-query` is, die een model `my-model` uit de configuratie Sites `my-conf` gebruikt:

* U kunt een vraag tot stand brengen gebruikend het `my-conf` specifieke eindpunt, en dan wordt de vraag bewaard als volgt:
  `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* U kunt dezelfde query maken met het eindpunt `global` , maar de query wordt als volgt opgeslagen:
  `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Dit zijn twee verschillende query&#39;s die zijn opgeslagen onder verschillende paden.
>
>Ze gebruiken gewoon hetzelfde model, maar via verschillende eindpunten.

## Een GraphQL-query laten doorgaan {#how-to-persist-query}

Het wordt geadviseerd om vragen op een de auteur van AEM milieu aanvankelijk voort te zetten en dan [ de vraag ](#transfer-persisted-query-production) over te brengen aan uw productie AEM publiceert milieu, voor gebruik door toepassingen.

Er zijn verschillende methoden om query&#39;s te blijven uitvoeren, waaronder:

* IDE GraphiQL - zie [ het Opslaan van Persisted Vragen ](/help/headless/graphql-api/graphiql-ide.md#saving-persisted-queries) (aangewezen methode)
* cURL - zie het volgende voorbeeld
* Andere hulpmiddelen, met inbegrip van [ Postman ](https://www.postman.com/)

IDE GraphiQL is de **geprefereerde** methode voor het voortduren van vragen. Om een bepaalde vraag voort te zetten gebruikend het **cURL** hulpmiddel van de bevellijn:

1. Bereid de vraag voor door het aan het nieuwe eindpunt URL `/graphql/persist.json/<config>/<persisted-label>` te PLAATSEN.

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

1. Vervolgens kunt u de voortgezette query aanvragen door de URL op te halen `/graphql/execute.json/<shortPath>` .

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

Een clienttoepassing vraagt een GET-aanvraag met de volgende syntaxis uit om een Persisted-query uit te voeren:

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Waar `PERSISTENT_PATH` een verkort pad is naar waar de Persisted-query wordt opgeslagen.

1. `wknd` is bijvoorbeeld de configuratienaam en `plain-article-query` is de naam van de Persisted-query. De query uitvoeren:

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. Een query uitvoeren met parameters.

   >[!NOTE]
   >
   > De variabelen en de waarden van de vraag moeten behoorlijk [ worden gecodeerd ](#encoding-query-url) wanneer het uitvoeren van een Verlengde vraag.

   Bijvoorbeeld:

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Zie het gebruiken van [ vraagvariabelen ](#query-variables) voor meer details.

## Query-variabelen gebruiken {#query-variables}

De variabelen van de vraag kunnen met Verblijfsde Vragen worden gebruikt. De vraagvariabelen worden toegevoegd aan het verzoek vooraf bepaald met een puntkomma (`;`) gebruikend de veranderlijke naam en de waarde. Meerdere variabelen worden gescheiden door puntkomma&#39;s.

Het patroon ziet er als volgt uit:

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

De volgende query bevat bijvoorbeeld een variabele `activity` om een lijst te filteren op basis van een activiteitwaarde:

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

Deze query kan worden uitgevoerd onder een pad `wknd/adventures-by-activity` . Om de Persisted vraag te roepen waar `activity=Camping` het verzoek als dit zou kijken:

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

De UTF-8-codering `%3B` is voor `;` en `%3D` is de codering voor `=` . De vraagvariabelen en om het even welke speciale karakters moeten [ behoorlijk ](#encoding-query-url) voor de Persisted vraag worden gecodeerd om uit te voeren.

### Query-variabelen gebruiken - Aanbevolen werkwijzen {#query-variables-best-practices}

Wanneer het gebruiken van variabelen in uw vragen zijn er een paar beste praktijken die zouden moeten worden gevolgd:

* Codering
In het algemeen wordt het altijd aanbevolen alle speciale tekens te coderen, bijvoorbeeld `;` , `=` , `?` , `&` .

* Puntkomma
De aanhoudende vragen die veelvoudige variabelen gebruiken (die door puntkomma&#39;s worden gescheiden) moeten of hebben:
   * de gecodeerde puntkomma&#39;s (`%3B`); het coderen van URL zal dit ook bereiken
   * of een volgpuntkomma die aan het einde van de query is toegevoegd

* `CACHE_GRAPHQL_PERSISTED_QUERIES`
Wanneer `CACHE_GRAPHQL_PERSISTED_QUERIES` is ingeschakeld voor de Dispatcher, worden parameters die de `/` - of `\` -tekens in hun waarde bevatten, twee keer gecodeerd op Dispatcher-niveau.
Om deze situatie te voorkomen:

   * Schakel `DispatcherNoCanonURL` in op de Dispatcher.
Hiermee geeft u de Dispatcher de opdracht om de oorspronkelijke URL door te sturen naar AEM, zodat dubbele coderingen worden voorkomen.
Deze instelling werkt momenteel echter alleen op `vhost` niveau. Als u Dispatcher-configuraties hebt voor het herschrijven van URL&#39;s (bijvoorbeeld wanneer u verkorte URL&#39;s gebruikt), hebt u mogelijk een aparte `vhost` nodig voor doorlopende query-URL&#39;s.

   * Verzend `/` - of `\` -tekens zonder codering.

     Wanneer u de URL van de blijvende query aanroept, zorgt u ervoor dat alle `/` - of `\` -tekens niet-gecodeerd blijven in de waarde van doorlopende queryvariabelen.

     >[!NOTE]
     >
     >Deze optie wordt alleen aanbevolen wanneer de `DispatcherNoCanonURL` -oplossing om welke reden dan ook niet kan worden geïmplementeerd.

* `CACHE_GRAPHQL_PERSISTED_QUERIES`

  Wanneer `CACHE_GRAPHQL_PERSISTED_QUERIES` is ingeschakeld voor de Dispatcher, kan het teken `;` niet worden gebruikt in de waarde van een variabele.

## Door uw doorlopende query&#39;s in cache te plaatsen {#caching-persisted-queries}

De geadviseerde vragen worden geadviseerd aangezien zij bij de [ Dispatcher ](/help/headless/deployment/dispatcher.md) en de lagen van het Netwerk van de Levering van de Inhoud (CDN) in het voorgeheugen kunnen worden ondergebracht, uiteindelijk verbeterend de prestaties van de het vragen cliënttoepassing.

Standaard maakt AEM de cache ongeldig op basis van de definitie &#39;Tijd naar live&#39; (TTL). Deze TTLs kan door de volgende parameters worden bepaald. Deze parameters zijn op verschillende manieren toegankelijk, waarbij de namen variëren volgens het gebruikte mechanisme:

| Cachetype | [ HTTP- kopbal ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control)  | cURL  | OSGi-configuratie  | Cloud Manager |
|--- |--- |--- |--- |--- |
| Browser | `max-age` | `cache-control : max-age` | `cacheControlMaxAge` | `graphqlCacheControl` |
| CDN | `s-maxage` | `surrogate-control : max-age` | `surrogateControlMaxAge` | `graphqlSurrogateControl` \|60 |
| CDN | `stale-while-revalidate` | `surrogate-control : stale-while-revalidate ` | `surrogateControlStaleWhileRevalidate` | `graphqlStaleWhileRevalidate` |
| CDN | `stale-if-error` | `surrogate-control : stale-if-error` | `surrogateControlStaleIfError` | `graphqlStaleIfError` |

{style="table-layout:auto"}

### Auteursinstanties {#author-instances}

Voor auteur-instanties zijn de standaardwaarden:

* `max-age` : 60
* `s-maxage` : 60
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Hiervoor gold het volgende:

* kan niet worden overschreven:
   * met een OSGi-configuratie
* kan worden overschreven:
   * door een verzoek dat de kopbalmontages van HTTP gebruikend cURL bepaalt; het zou geschikte montages voor `cache-control` en/of `surrogate-control` moeten omvatten; voor voorbeelden, zie [ Beheerd Geheime voorgeheugen bij het Gepersisteerde Niveau van de Vraag ](#cache-persisted-query-level)
   * als u waarden in de **Kopballen** dialoog van [ GraphiQL winde ](#http-cache-headers-graphiql-ide) specificeert

### Exemplaren publiceren {#publish-instances}

Voor publicatie-instanties zijn de standaardwaarden:

* `max-age` : 60
* `s-maxage` : 7200
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Deze kunnen worden overschreven:

* [van de GraphQL IDE](#http-cache-headers-graphiql-ide)

* [ bij het Blijven Niveau van de Vraag ](#cache-persisted-query-level); dit impliceert het posten van de vraag aan AEM gebruikend cURL in uw interface van de bevellijn, en het publiceren van de Verlengde Vraag.

* [met Cloud Manager-variabelen](#cache-cloud-manager-variables)

* [met een OSGi-configuratie](#cache-osgi-configration)

### Het beheren van de Kopballen van het Geheime voorgeheugen van HTTP in GrahiQL winde {#http-cache-headers-graphiql-ide}

GrahiQL winde - zie [ het Opslaan van Persisted Vragen ](/help/headless/graphql-api/graphiql-ide.md#managing-cache)

### Het beheren van Geheime voorgeheugen op het Aanhoudende Niveau van de Vraag {#cache-persisted-query-level}

Dit betekent dat de query naar AEM moet worden gepost met behulp van cURL in de opdrachtregelinterface.

Een voorbeeld van de methode PUT (create):

```bash
curl -u admin:admin -X PUT \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

Een voorbeeld van de methode POST (update):

```bash
curl -u admin:admin -X POST \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

De `cache-control` kan worden ingesteld tijdens het maken (PUT) of later (bijvoorbeeld via een POST-aanvraag). Het cache-besturingselement is optioneel bij het maken van de permanente query, omdat AEM de standaardwaarde kan opgeven. Zie [ hoe te om een vraag van GraphQL ](#how-to-persist-query), voor een voorbeeld voort te zetten om een vraag te gebruiken cURL.

### Cache beheren met Cloud Manager-variabelen {#cache-cloud-manager-variables}

[ de Variabelen van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) kunnen met Cloud Manager worden bepaald om de vereiste waarden te bepalen:

| Naam | Waarde | Toegepaste service | Type |
|--- |--- |--- |--- |
| `graphqlStaleIfError` | 86400 | *zoals aangewezen* | *zoals aangewezen* |
| `graphqlSurrogateControl` | 600 | *zoals aangewezen* | *zoals aangewezen* |

{style="table-layout:auto"}

### Het beheren van Geheime voorgeheugen met een configuratie OSGi {#cache-osgi-configration}

Om het geheime voorgeheugen globaal te beheren, kunt u [ de montages OSGi ](/help/implementing/deploying/configuring-osgi.md) voor de **Verlengde Configuratie van de Dienst van de Vraag** vormen.

>[!NOTE]
>
>Voor geheim voorgeheugencontrole, is de configuratie OSGi slechts aangewezen voor publiceer instanties. De configuratie bestaat bij de instanties van de auteur, maar wordt genegeerd.

>[!NOTE]
>
>De **Verlengde Configuratie van de Dienst van de Vraag** wordt ook gebruikt voor [ vormend de code van de vraagreactie ](#configuring-query-response-code).

De standaard configuratie OSGi voor publiceer instanties:

* leest de Cloud Manager-variabelen, indien beschikbaar:

  | OSGi-configuratieeigenschap | leest dit | Cloud Manager-variabele |
  |--- |--- |--- |
  | `cacheControlMaxAge` | leest | `graphqlCacheControl` |
  | `surrogateControlMaxAge` | leest | `graphqlSurrogateControl` |
  | `surrogateControlStaleWhileRevalidate` | leest | `graphqlStaleWhileRevalidate` |
  | `surrogateControlStaleIfError` | leest | `graphqlStaleIfError` |

  {style="table-layout:auto"}

* en als niet beschikbaar, gebruikt de configuratie OSGi de [ standaardwaarden voor publiceer instanties ](#publish-instances).

## De antwoordcode voor de query configureren {#configuring-query-response-code}

Standaard verzendt `PersistedQueryServlet` een `200` -reactie wanneer een query wordt uitgevoerd, ongeacht het werkelijke resultaat.

U kunt [ de montages OSGi ](/help/implementing/deploying/configuring-osgi.md) voor de **Versiesde Configuratie van de Dienst van de Vraag** vormen om te controleren of de meer gedetailleerde statuscodes door het `/execute.json/persisted-query` eindpunt zijn teruggekeerd, wanneer er een fout in de gepersisteerde vraag is.

>[!NOTE]
>
>De **Verlengde Configuratie van de Dienst van de Vraag** wordt ook gebruikt voor [ het beheren van geheim voorgeheugen ](#cache-osgi-configration).

Het veld `Respond with application/graphql-response+json` (`responseContentTypeGraphQLResponseJson`) kan als vereist worden gedefinieerd:

* `false` (standaardwaarde):
Het maakt niet uit of de voortgezette query succesvol is of niet. De `Content-Type` teruggekeerde kopbal is `application/json`, en `/execute.json/persisted-query` *altijd* keert de statuscode `200` terug.

* `true` :
De geretourneerde `Content-Type` is `application/graphql-response+json` en het eindpunt retourneert de juiste antwoordcode wanneer er een fout optreedt bij het uitvoeren van de voortgezette query:

  | Code | Beschrijving |
  |--- |--- |
  | 200 | Geslaagd antwoord |
  | 400 | Geeft aan dat er koppen ontbreken of dat er een probleem is met het voortgezette querypad. Configuratienaam niet opgegeven, achtervoegsel niet opgegeven en andere.<br> zie [ het Oplossen van problemen - het eindpunt van GraphQL niet gevormd ](/help/headless/graphql-api/persisted-queries-troubleshoot.md#missing-path-query-url). |
  | 404 | Kan de gewenste bron niet vinden. Bijvoorbeeld, is het eindpunt Graphql niet beschikbaar op de server.<br> zie [ het Oplossen van problemen - Ontbrekende weg in GraphQL voortgeduurde vraag URL ](/help/headless/graphql-api/persisted-queries-troubleshoot.md#graphql-endpoint-not-configured). |
  | 500 | Interne serverfout. Bijvoorbeeld validatiefouten, persistentiefout en andere. |

  >[!NOTE]
  >
  >Zie ook https://graphql.github.io/graphql-over-http/draft/#sec-Status-Codes

## De URL van de query coderen voor gebruik door een app {#encoding-query-url}

Voor gebruik door een toepassing, moeten om het even welke speciale karakters die wanneer het construeren van vraagvariabelen (namelijk puntkomma&#39;s (`;`), gelijkteken (`=`), schuine strepen `/`) worden gebruikt worden omgezet om het overeenkomstige coderen te gebruiken UTF-8.

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

Om een voortgezette vraag in een cliëntapp te gebruiken, zou de cliënt SDK zonder kop van AEM voor [ JavaScript ](https://github.com/adobe/aem-headless-client-js), [ Java ](https://github.com/adobe/aem-headless-client-java), of [ NodeJS ](https://github.com/adobe/aem-headless-client-nodejs) moeten worden gebruikt. De Headless Client SDK codeert alle queryvariabelen automatisch op de juiste wijze in de aanvraag.

## Het overbrengen van een blijvende vraag aan uw milieu van de Productie  {#transfer-persisted-query-production}

Blijvende query&#39;s moeten altijd worden gemaakt op een AEM Auteur-service en vervolgens worden gepubliceerd (gerepliceerd) naar een AEM Publish-service. Vaak, worden de Persisted vragen gecreeerd en op lagere milieu&#39;s zoals lokale of milieu&#39;s van de Ontwikkeling getest. Het is dan nodig om Persisted query&#39;s te promoten naar omgevingen op een hoger niveau, zodat deze uiteindelijk beschikbaar komen in een AEM-publicatie-productieomgeving voor gebruik door clienttoepassingen.

### Voorbehouden query&#39;s verpakken

De aanhoudende vragen kunnen in [ Pakketten van AEM ](/help/implementing/developing/tools/package-manager.md) worden gebouwd. AEM Packages kunnen vervolgens worden gedownload en geïnstalleerd in verschillende omgevingen. AEM Packages kunnen ook worden gerepliceerd vanuit een AEM Author-omgeving naar een AEM Publish-omgeving.

Een pakket maken:

1. Navigeer aan **Hulpmiddelen** > **Plaatsing** > **Pakketten**.
1. Creeer een nieuw pakket door **te tikken creeer Pakket**. Hiermee wordt een dialoogvenster geopend waarin het pakket wordt gedefinieerd.
1. In de Dialoog van de Definitie van het Pakket, onder **Algemene** ga a **Naam** als &quot;wknd-persistente-query&#39;s&quot; in.
1. Voer een versienummer in, bijvoorbeeld &quot;1.0&quot;.
1. Onder **Filters** voeg een nieuwe **Filter** toe. Gebruik de Finder van het Weg om de `persistentQueries` omslag onder de configuratie te selecteren. Voor de `wknd` -configuratie is het volledige pad bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries` .
1. Selecteer **sparen** om de nieuwe definitie van het Pakket te bewaren en de dialoog te sluiten.
1. Selecteer **bouwt** knoop in de gecreeerde definitie van het Pakket.

Nadat het pakket is gemaakt, kunt u:

* **Download** het pakket en herupload op een verschillend milieu.
* **Repliceer** het pakket door **meer** te tikken > **Repliceer**. Hiermee wordt het pakket gerepliceerd naar de verbonden AEM-publicatieomgeving.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
