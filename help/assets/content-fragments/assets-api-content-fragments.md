---
title: Adobe Experience Manager as a Cloud Service Content Fragments Support in the Assets HTTP API
description: Meer informatie over ondersteuning voor Content Fragments in de Assets HTTP API, een belangrijke Adobe Experience Manager-functie voor headless-levering.
feature: Content Fragments, Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
role: User, Admin
source-git-commit: 1995c84bb669fd52ecd53c7e695acc518a5226e8
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 0%

---

# Ondersteuning voor inhoudsfragmenten in de AEM Assets HTTP API {#content-fragments-support-in-aem-assets-http-api}

## Overzicht {#overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/extending/assets-api-content-fragments.html) |
| AEM as a Cloud Service | Dit artikel |

>[!CAUTION]
>
>De Steun van het Fragment van de inhoud in HTTP API van Assets is nu verouderd [&#128279;](/help/release-notes/deprecated-removed-features.md).
>
>Het is vervangen door [ Levering van het Fragment van de Inhoud met OpenAPI ](/help/headless/aem-content-fragment-delivery-with-openapi.md) samen met [ Fragmenten van de Inhoud en Modellen van het Fragment van de Inhoud Management OpenAPIs ](/help/headless/content-fragment-openapis.md).

Meer informatie over ondersteuning voor Content Fragments in de Assets HTTP API, een belangrijke functie voor het leveren van koploze artikelen in Adobe Experience Manager (AEM).

>[!NOTE]
>
>Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

>[!NOTE]
>
>[ HTTP API van Assets ](/help/assets/mac-api-assets.md) omvat:
>
>* ASSETS REST API
>* inclusief ondersteuning voor inhoudsfragmenten
>
>De huidige implementatie van Assets HTTP API is gebaseerd op de [ REST ](https://en.wikipedia.org/wiki/Representational_state_transfer) architecturale stijl.

>[!NOTE]
>
>Voor de recentste informatie over Experience Manager APIs, bezoek [ Adobe Experience Manager as a Cloud Service APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

[ Assets REST API ](/help/assets/mac-api-assets.md) staat ontwikkelaars voor Adobe Experience Manager as a Cloud Service toe om tot inhoud (die in AEM wordt opgeslagen) direct over HTTP API, als (Create, Lees, Update, Schrapping) verrichtingen toegang te hebben CRUD.

Met de API kunt u Adobe Experience Manager as a Cloud Service gebruiken als een CMS zonder kop (Content Management System) door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken.

Bijvoorbeeld, [ Enige Toepassingen van de Pagina (SPA) ](/help/implementing/developing/hybrid/introduction.md), op kader-gebaseerd of douane, vereisen inhoud die over HTTP API, vaak in formaat wordt verstrekt JSON.

Terwijl [ de Componenten van de Kern van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) een klantgerichte API verstrekken die vereiste Gelezen verrichtingen voor dit doel kan dienen, en de waarvan output JSON kan worden aangepast, vereisen zij AEM WCM (het Beheer van de Inhoud van het Web) knowhow voor implementatie. Dit komt omdat ze moeten worden gehost op pagina&#39;s die zijn gebaseerd op speciale AEM-sjablonen. Niet elke SBZ-ontwikkelingsorganisatie heeft directe toegang tot deze kennis.

Dit is wanneer de Assets REST API kan worden gebruikt. Ontwikkelaars hebben direct toegang tot elementen (bijvoorbeeld afbeeldingen en inhoudsfragmenten), zonder dat ze eerst in een pagina moeten worden ingesloten en hun inhoud in geserialiseerde JSON-indeling moeten leveren.

>[!NOTE]
>
>Het is niet mogelijk JSON-uitvoer van de Assets REST API aan te passen.

Met de Assets REST API kunnen ontwikkelaars ook inhoud wijzigen door nieuwe elementen, inhoudsfragmenten en mappen te maken, bij te werken of te verwijderen.

De Assets REST API:

* volgt het [ HATEOAS beginsel ](https://en.wikipedia.org/wiki/HATEOAS)

* voert het [ formaat SIREN ](https://github.com/kevinswiber/siren) uit

## Vereisten {#prerequisites}

De Assets REST-API is beschikbaar voor elke installatie van een recente Adobe Experience Manager as a Cloud Service-versie die buiten de box valt.

## Belangrijke concepten {#key-concepts}

Assets REST API biedt [ REST ](https://en.wikipedia.org/wiki/Representational_state_transfer) - stijltoegang tot activa aan die binnen een instantie van AEM worden opgeslagen.

De methode gebruikt het eindpunt `/api/assets` en vereist het pad van het element om het te openen (zonder de regelafstand `/content/dam` ).

* Dit betekent dat toegang tot het actief moet worden verkregen tegen:
   * `/content/dam/path/to/asset`
* Verzoek:
   * `/api/assets/path/to/asset`

Als u bijvoorbeeld toegang wilt krijgen tot `/content/dam/wknd/en/adventures/cycling-tuscany` , vraagt u om `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Toegang over:
>
>* `/api/assets` **&#x200B;**&#x200B;nodig niet het gebruik van `.model` selecteur.
>* `/content/path/to/page` **&#x200B;**&#x200B;vereist het gebruik van `.model` selecteur.

De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - om een vertegenwoordiging JSON van activa of een omslag terug te winnen
* **POST** - om activa of omslagen te creëren
* **PUT** - om de eigenschappen van een activa of een omslag bij te werken
* **DELETE** - om activa of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; bijvoorbeeld, bepaal dat een omslag of een activa door a **POST** verzoek zou moeten worden gecreeerd.

Het nauwkeurige formaat van gesteunde verzoeken wordt bepaald in de [ API documentatie van de Verwijzing ](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference).

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

### Transactioneel gedrag {#transactional-behavior}

Alle verzoeken zijn atomisch.

Dit betekent dat de verdere (`write`) verzoeken niet in één enkele transactie kunnen worden gecombineerd die als één enkele entiteit kon slagen of ontbreken.

### AEM (Assets) REST API versus AEM Components {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Verhouding</td>
   <td>Assets REST API <br/> </td>
   <td>AEM-component <br/> (componenten die Sling-modellen gebruiken)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Ondersteunde gebruiksgevallen</td>
   <td>Algemeen doel.</td>
   <td><p>Geoptimaliseerd voor gebruik in een Single Page Application (SPA) of een andere (content consuming) context.</p> <p>Het kan ook lay-outinformatie bevatten.</p> </td>
  </tr>
  <tr>
   <td>Ondersteunde bewerkingen</td>
   <td><p>Maken, lezen, bijwerken, verwijderen.</p> <p>Met extra bewerkingen, afhankelijk van het type entiteit.</p> </td>
   <td>Alleen-lezen.</td>
  </tr>
  <tr>
   <td>Toegang</td>
   <td><p>Het kan direct worden betreden.</p> <p>Gebruikt het <code>/api/assets </code> eindpunt, in kaart gebracht aan <code>/content/dam</code> (in de bewaarplaats).</p> 
   <p>Een voorbeeldpad zou er als volgt uitzien: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Er moet naar worden verwezen via een AEM-component op een AEM-pagina.</p> <p>Gebruikt de kiezer van <code>.model</code> om de JSON-representatie te maken.</p> <p>Een voorbeeldpad zou er als volgt uitzien:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Beveiliging</td>
   <td><p>Er zijn meerdere opties mogelijk.</p> <p>OAuth wordt voorgesteld; kan los van de standaardopstelling worden gevormd.</p> </td>
   <td>Gebruikt standaard AEM-instelling.</td>
  </tr>
  <tr>
   <td>Architecten</td>
   <td><p>Schrijftoegang richt zich doorgaans op een instantie Auteur.</p> <p>Lees kan ook naar een instantie Publish worden geleid.</p> </td>
   <td>Omdat deze benadering alleen-lezen is, wordt deze doorgaans gebruikt voor instanties Publish.</td>
  </tr>
  <tr>
   <td>Uitvoer</td>
   <td>SIREN-uitvoer gebaseerd op JSON: uitgebreid, maar krachtig. Hiermee kunt u navigeren binnen de inhoud.</td>
   <td>Op JSON gebaseerde eigen uitvoer; configureerbaar via Sling Models. Navigeren door de inhoudsstructuur is moeilijk te implementeren (maar niet noodzakelijkerwijs onmogelijk).</td>
  </tr>
 </tbody>
</table>

### Beveiliging {#security}

Als de Assets REST API wordt gebruikt binnen een omgeving zonder specifieke verificatievereisten, moet het AEM CORS-filter correct zijn geconfigureerd.

>[!NOTE]
>
>Zie voor meer informatie:
>
>* [ CORS/AEM verklaarde ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html)
>* [ Video - het Ontwikkelen voor CORS met AEM (04:06) ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html)
>

In omgevingen met specifieke verificatievereisten wordt OAuth aanbevolen.

## Beschikbare functies {#available-features}

De Fragmenten van de inhoud zijn een specifiek type van Activa, zie [ Werkend met de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md).

Zie voor meer informatie over functies die beschikbaar zijn via de API:

* [ Assets REST API ](/help/assets/mac-api-assets.md)
* [ Types van Entiteit ](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types), waar de eigenschappen specifiek voor elk gesteund type (zoals relevant voor de Fragmenten van de Inhoud) worden verklaard

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

### Paginering {#paging}

De Assets REST API ondersteunt paginering (voor GET-aanvragen) via de URL-parameters:

* `offset` - het nummer van de eerste (onderliggende) entiteit die moet worden opgehaald
* `limit` - het maximale aantal geretourneerde entiteiten

De reactie bevat pagineringsinformatie als onderdeel van de sectie `properties` van de SIREN-uitvoer. Deze eigenschap `srn:paging` bevat het totale aantal (onderliggende) entiteiten ( `total` ), de verschuiving en de limiet ( `offset` , `limit` ) zoals opgegeven in de aanvraag.

>[!NOTE]
>
>Pagina&#39;s worden doorgaans toegepast op containerentiteiten (dat wil zeggen mappen of elementen met uitvoeringen), omdat ze betrekking hebben op de onderliggende elementen van de aangezochte entiteit.

#### Voorbeeld: Pagelen {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```json
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Typen entiteiten {#entity-types}

### Mappen {#folders}

Mappen fungeren als containers voor elementen en andere mappen. Ze weerspiegelen de structuur van de AEM-inhoudsopslagplaats.

De Assets REST API stelt toegang tot de eigenschappen van een map beschikbaar. Bijvoorbeeld de naam en de titel. Assets wordt weergegeven als onderliggende entiteiten van mappen en submappen.

>[!NOTE]
>
>Afhankelijk van het type element van de onderliggende elementen en mappen, bevat de lijst met onderliggende entiteiten mogelijk al de volledige reeks eigenschappen die de onderliggende entiteit definieert. Alternatief, slechts kan een beperkte reeks eigenschappen voor een entiteit in deze lijst van kindentiteiten worden blootgesteld.

### Assets {#assets}

Als een element wordt aangevraagd, retourneert het antwoord de metagegevens van het element, zoals titel, naam en andere informatie, zoals gedefinieerd in het desbetreffende elementschema.

De binaire gegevens van een element worden weergegeven als een SIREN-koppeling van het type `content` .

Assets kan meerdere uitvoeringen hebben. Deze worden doorgaans weergegeven als onderliggende entiteiten, waarbij één uitzondering een miniatuuruitvoering is die wordt weergegeven als een koppeling van het type `thumbnail` ( `rel="thumbnail"` ).

### Inhoudsfragmenten {#content-fragments}

A [ inhoudsfragment ](/help/assets/content-fragments/content-fragments.md) is een speciaal type van activa. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals tekst, getallen, datums.

Aangezien er verscheidene verschillen aan *standaard* activa (zoals beelden of audio) zijn, zijn sommige extra regels van toepassing op de behandeling van hen.

#### Vertegenwoordiging {#representation}

Inhoudsfragmenten:

* Maak geen binaire gegevens beschikbaar.
* Deze bevinden zich in de JSON-uitvoer (binnen de eigenschap `properties` ).

* Ze worden ook als atomisch beschouwd. De elementen en variaties worden dus weergegeven als onderdeel van de eigenschappen van het fragment in plaats van als koppelingen of onderliggende entiteiten. Op deze manier hebt u efficiënt toegang tot de lading van een fragment.

#### Inhoudsmodellen en inhoudsfragmenten {#content-models-and-content-fragments}

De modellen die de structuur van een inhoudsfragment definiëren, worden momenteel niet via een HTTP-API weergegeven. Daarom moet de *consument* over het model van een fragment (minstens een minimum) weten - hoewel de meeste informatie van de nuttige lading kan worden afgeleid; als gegevenstypes, etc., deel van de definitie uitmaken.

Als u een inhoudsfragment wilt maken, moet u het pad (interne gegevensopslagruimte) van het model opgeven.

#### Gekoppelde inhoud {#associated-content}

Gekoppelde inhoud wordt niet weergegeven.

## Gebruiken {#using}

Het gebruik kan verschillen, afhankelijk van het feit of u een AEM-auteur- of publicatieomgeving gebruikt en van uw specifieke gebruiksscenario.

* Men adviseert dat de verwezenlijking aan een instantie van de Auteur ([ verbindend is en momenteel is er geen middel om een fragment te herhalen om te publiceren gebruikend dit API ](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* Levering is mogelijk van beide, aangezien AEM aangevraagde inhoud alleen in JSON-indeling levert.

   * Opslag en levering door een AEM Author-instantie zouden voor achter-de-firewall, media bibliotheektoepassingen moeten volstaan.

   * Voor live webweergave wordt een AEM-publicatie-instantie aanbevolen.

>[!CAUTION]
>
>De Dispatcher-configuratie op AEM-cloudinstanties kan de toegang tot `/api` blokkeren.

>[!NOTE]
>
>Zie de [ API Verwijzing ](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). In het bijzonder, [ Adobe Experience Manager Assets API - de Fragmenten van de Inhoud ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html).
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

## Beperkingen {#limitations}

Er zijn een paar beperkingen:

* **de fragmentmodellen van de Inhoud worden momenteel niet gesteund**: zij kunnen niet worden gelezen of worden gecreeerd. Ontwikkelaars moeten het juiste pad naar het inhoudsfragmentmodel weten om een bestaand inhoudsfragment te kunnen maken of bijwerken. Momenteel is de enige methode om een overzicht van deze te krijgen door het beleid UI.
* **Verwijzingen worden genegeerd**. Er wordt momenteel niet gecontroleerd of naar een bestaand inhoudsfragment wordt verwezen. Daarom kan het verwijderen van een inhoudsfragment bijvoorbeeld resulteren in problemen op een pagina die een verwijzing naar het verwijderde inhoudsfragment bevat.
* **JSON gegevenstype** REST API output van het *JSON gegevenstype* is *op koord-gebaseerde output*.

## Statuscodes en foutberichten {#status-codes-and-error-messages}

De volgende statuscodes kunnen in de relevante omstandigheden worden gezien:

* **200** (OK)

  Geretourneerd wanneer:

   * een inhoudsfragment aanvragen als `GET`
   * het bijwerken van een inhoudsfragment met succes als `PUT`

* **201** (Gemaakt)

  Geretourneerd wanneer:

   * een inhoudsfragment maken met `POST`

* **404** (Niet gevonden)

  Geretourneerd wanneer:

   * het gewenste inhoudsfragment bestaat niet

* **500** (Interne serverfout)

  >[!NOTE]
  >
  >Deze fout wordt geretourneerd:
  >
  >* wanneer een fout is opgetreden die niet met een specifieke code kan worden geïdentificeerd
  >* wanneer de opgegeven lading niet geldig was

  In het volgende voorbeeld worden algemene scenario&#39;s weergegeven wanneer deze foutstatus wordt geretourneerd, samen met het gegenereerde foutbericht (monospace):

   * Bovenliggende map bestaat niet (wanneer u een inhoudsfragment maakt met de notatie `POST` )
   * Er is geen inhoudsfragmentmodel opgegeven (cq:model ontbreekt), kan niet worden gelezen (vanwege een ongeldig pad of een machtigingsprobleem) of er is geen geldig fragmentmodel:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`

   * Het inhoudsfragment kan niet worden gemaakt (mogelijk een probleem met de machtigingen):

      * `Could not create content fragment`

   * Titel en/of beschrijving kunnen niet worden bijgewerkt:

      * `Could not set value on content fragment`

   * Kan metagegevens niet instellen:

      * `Could not set metadata on content fragment`

   * Het element Content kan niet worden gevonden of kan niet worden bijgewerkt

      * `Could not update content element`
      * `Could not update fragment data of element`

  De gedetailleerde foutberichten worden als volgt geretourneerd:

  ```xml
  {
    "class": "core/response",
    "properties": {
      "path": "/api/assets/foo/bar/qux",
      "location": "/api/assets/foo/bar/qux.json",
      "parentLocation": "/api/assets/foo/bar.json",
      "status.code": 500,
      "status.message": "...{error message}.."
    }
  }
  ```

## API-naslag {#api-reference}

Zie hier voor gedetailleerde API-referenties:

* [ Adobe Experience Manager Assets API - de Fragmenten van de Inhoud ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html)

* [ASSETS HTTP API](/help/assets/mac-api-assets.md)

   * [Beschikbare functies](/help/assets/mac-api-assets.md#available-features)

* Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

## Aanvullende bronnen {#additional-resources}

Zie voor meer informatie:

* [Assets HTTP API-documentatie](/help/assets/mac-api-assets.md)
* [ AEM Gem zitting: OAuth ](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-oauth-server-functionality-in-aem.html)
