---
title: Adobe Experience Manager als de Fragments van de Inhoud van de Cloud Service Steun in Activa HTTP API
description: Meer informatie over Adobe Experience Manager als ondersteuning voor Cloud Service Content Fragments in Assets HTTP API.
translation-type: tm+mt
source-git-commit: efbd21aa7d8aa5b32d0af720466e4ffe92a012dd
workflow-type: tm+mt
source-wordcount: '1891'
ht-degree: 1%

---


# Ondersteuning voor inhoudsfragmenten in HTTP-API van AEM Assets{#content-fragments-support-in-aem-assets-http-api}

## Overzicht {#overview}

>[!NOTE]
>
>De [middelen HTTP API](/help/assets/mac-api-assets.md) omvat:
>
>* REST-API voor middelen
>* inclusief ondersteuning voor inhoudsfragmenten
>
>
De huidige implementatie van de Elementen HTTP API is gebaseerd op de architecturale stijl [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) .

Met de REST-API [voor](/help/assets/mac-api-assets.md) middelen hebben ontwikkelaars voor Adobe Experience Manager als Cloud Service via CRUD-bewerkingen rechtstreeks toegang tot inhoud (opgeslagen in AEM) (maken, lezen, bijwerken, verwijderen) via de HTTP-API.

Met de API kunt u Adobe Experience Manager als een Cloud Service als een CMS (Content Management System) zonder kop gebruiken door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken.

Bijvoorbeeld, de Enige Toepassingen van de Pagina (SPA), op kader-gebaseerd of douane, vereisen inhoud die over HTTP API, vaak in formaat JSON wordt verstrekt.

Hoewel [AEM Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) een zeer uitvoerige, flexibele en aanpasbare API biedt die de vereiste leesbewerkingen voor dit doel kan dienen en waarvan de JSON-uitvoer kan worden aangepast, is voor de implementatie wel AEM WCM (Web Content Management)-knowhow vereist, omdat deze moet worden gehost op pagina&#39;s die zijn gebaseerd op speciale AEM-sjablonen. Niet elke SBZ-ontwikkelingsorganisatie heeft directe toegang tot deze kennis.

Dit is wanneer de REST API van Activa kan worden gebruikt. Ontwikkelaars hebben direct toegang tot elementen (bijvoorbeeld afbeeldingen en inhoudsfragmenten), zonder dat ze eerst in een pagina moeten worden ingesloten en hun inhoud in geserialiseerde JSON-indeling moeten leveren.

>[!NOTE]
>
>Het is niet mogelijk JSON-uitvoer van de REST API voor middelen aan te passen.

Met de REST API voor middelen kunnen ontwikkelaars ook inhoud wijzigen door nieuwe elementen, inhoudsfragmenten en mappen te maken, bij te werken of te verwijderen.

De REST-API voor middelen:

* volgt het [HATEOAS-beginsel](https://en.wikipedia.org/wiki/HATEOAS)

* implementeert de [SIREN-indeling](https://github.com/kevinswiber/siren)

## Vereisten {#prerequisites}

De REST API van Middelen is beschikbaar op elke uit-van-de-doos installatie van een recente Adobe Experience Manager als versie van de Cloud Service.

## Belangrijke concepten {#key-concepts}

De REST API van Activa biedt [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)-stijl toegang tot activa die binnen een instantie AEM worden opgeslagen.

Het gebruikt het `/api/assets` eindpunt en vereist de weg van de activa om tot het (zonder het leiden `/content/dam`) toegang te hebben.

* Dit betekent dat toegang tot het actief moet worden verkregen tegen:
   * `/content/dam/path/to/asset`
* U moet een aanvraag indienen:
   * `/api/assets/path/to/asset`

Bijvoorbeeld om toegang te krijgen `/content/dam/wknd/en/adventures/cycling-tuscany`, verzoek `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Toegang over:
>* `/api/assets` **heeft het gebruik van de** kiezer niet `.model` nodig.
>* `/content/assets` **vereist** het gebruik van de `.model` kiezer.


De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - voor het ophalen van een JSON-representatie van een middel of een map
* **POST** - voor het maken van nieuwe elementen of mappen
* **PUT** - om de eigenschappen van een middel of een omslag bij te werken
* **DELETE** - om een middel of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; U kunt bijvoorbeeld definiëren dat een map of element moet worden gemaakt door een **POST** -aanvraag.

<!--
The exact format of supported requests is defined in the [API Reference](/help/assets/assets-api-content-fragments.md#api-reference) documentation.
-->

### Transactioneel gedrag {#transactional-behavior}

Alle verzoeken zijn atomisch.

Dit betekent dat latere (`write`) verzoeken niet kunnen worden gecombineerd tot één enkele transactie die als één enkele entiteit zou kunnen slagen of mislukken.

### AEM (Middelen) REST API versus AEM-componenten {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Verhouding</td>
   <td>REST-API voor middelen<br/> </td>
   <td>AEM-component<br/> (componenten die gebruikmaken van Sling-modellen)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Ondersteunde gebruikscase(s)</td>
   <td>Algemeen doel.</td>
   <td><p>Geoptimaliseerd voor gebruik in een Single Page Application (SPA) of een andere (content consuming) context.</p> <p>Kan ook lay-outgegevens bevatten.</p> </td>
  </tr>
  <tr>
   <td>Ondersteunde bewerkingen</td>
   <td><p>Maken, lezen, bijwerken, verwijderen.</p> <p>Met extra bewerkingen afhankelijk van het type entiteit.</p> </td>
   <td>Alleen-lezen.</td>
  </tr>
  <tr>
   <td>Toegang</td>
   <td><p>Kan rechtstreeks worden benaderd.</p> <p>Gebruikt het <code>/api/assets </code>eindpunt, in kaart gebracht aan <code>/content/dam</code> (in de bewaarplaats).</p> 
   <p>Een voorbeeldpad zou er als volgt uitzien: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Er moet naar worden verwezen via een AEM-component op een AEM-pagina.</p> <p>Gebruikt de <code>.model</code> kiezer om de JSON-representatie te maken.</p> <p>Een voorbeeldpad zou er als volgt uitzien:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Beveiliging</td>
   <td><p>Er zijn meerdere opties mogelijk.</p> <p>OAuth wordt voorgesteld; kan los van standaardopstelling worden gevormd.</p> </td>
   <td>Gebruikt de standaardinstallatie van AEM.</td>
  </tr>
  <tr>
   <td>Architecten</td>
   <td><p>Schrijftoegang richt zich gewoonlijk tot een auteurinstantie.</p> <p>Lees kan ook naar een publicatie-instantie worden gestuurd.</p> </td>
   <td>Aangezien deze benadering read-only is, zal het typisch voor publiceer instanties worden gebruikt.</td>
  </tr>
  <tr>
   <td>Uitvoer</td>
   <td>Op JSON gebaseerde SIREN-uitvoer: uitgebreid, maar krachtig. Hiermee kunt u navigeren binnen de inhoud.</td>
   <td>op JSON gebaseerde eigen output; configureerbaar via Sling Models. Navigeren door de inhoudsstructuur is moeilijk te implementeren (maar niet noodzakelijkerwijs onmogelijk).</td>
  </tr>
 </tbody>
</table>

### Beveiliging {#security}

Als de REST API van Middelen binnen een milieu zonder specifieke authentificatievereisten wordt gebruikt, moet het filter van CORS van AEM correct worden gevormd.

>[!NOTE]
>
>Zie voor meer informatie:
>
>* [CORS/AEM toegelicht](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [Video - Ontwikkelen voor CORS met AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
>



In omgevingen met specifieke verificatievereisten wordt OAuth aanbevolen.

## Beschikbare functies {#available-features}

Inhoudsfragmenten zijn een specifiek type element. Zie [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md).

Zie voor meer informatie over functies die beschikbaar zijn via de API:

* De REST-API voor [middelen](/help/assets/mac-api-assets.md)
* [Typen](/help/assets/assets-api-content-fragments.md#entity-types)entiteiten, waarbij de kenmerken die specifiek zijn voor elk ondersteund type (voor zover relevant voor inhoudsfragmenten) worden toegelicht

### Paginering {#paging}

De REST API voor middelen ondersteunt paginering (voor GET-aanvragen) via de URL-parameters:

* `offset` - het nummer van de eerste (onderliggende) entiteit die moet worden opgehaald
* `limit` - het maximumaantal geretourneerde entiteiten

De reactie zal het pagineren informatie als deel van de `properties` sectie van de output bevatten SIREN. Deze `srn:paging` eigenschap bevat het totale aantal (onderliggende) entiteiten ( `total`), de verschuiving en de limiet ( `offset`, `limit`) zoals opgegeven in de aanvraag.

>[!NOTE]
>
>Paginering wordt doorgaans toegepast op containerentiteiten (d.w.z. mappen of elementen met uitvoeringen), aangezien deze betrekking hebben op de onderliggende elementen van de aangezochte entiteit.

#### Voorbeeld: Paginering {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```
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

De REST API van Middelen stelt toegang tot de eigenschappen van een omslag bloot; bijvoorbeeld naam, titel, enz. Elementen worden weergegeven als onderliggende entiteiten van mappen en submappen.

>[!NOTE]
>
>Afhankelijk van het type element van de onderliggende elementen en mappen bevat de lijst met onderliggende entiteiten mogelijk al de volledige set eigenschappen die de onderliggende entiteit definieert. Alternatief, slechts kan een beperkte reeks eigenschappen voor een entiteit in deze lijst van kindentiteiten worden blootgesteld.

### Assets {#assets}

Als een element wordt gevraagd, zal de reactie zijn meta-gegevens terugkeren; zoals titel, naam en andere informatie zoals gedefinieerd in het desbetreffende elementschema.

De binaire gegevens van een element worden blootgesteld als verbinding SIREN van type `content` (die ook als `rel attribute`) wordt bekend.

Elementen kunnen meerdere uitvoeringen hebben. Deze worden doorgaans weergegeven als onderliggende entiteiten, waarbij één uitzondering een miniatuuruitvoering is, die wordt weergegeven als een koppeling van het type `thumbnail` ( `rel="thumbnail"`).

### Contentfragmenten {#content-fragments}

Een [inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal type element. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, getallen, datums.

Aangezien er verschillende verschillen zijn met *standaardmiddelen* (zoals afbeeldingen of audio), zijn er enkele aanvullende regels van toepassing op de afhandeling ervan.

#### Vertegenwoordiging {#representation}

Inhoudsfragmenten:

* Maak geen binaire gegevens beschikbaar.
* Deze bevinden zich volledig in de JSON-uitvoer (binnen de `properties` eigenschap).

* Wordt ook als atomisch beschouwd, d.w.z. de elementen en variaties worden blootgesteld als onderdeel van de eigenschappen van het fragment ten opzichte van als koppelingen of onderliggende entiteiten. Op deze manier hebt u efficiënt toegang tot de lading van een fragment.

#### Inhoudsmodellen en Inhoudsfragmenten {#content-models-and-content-fragments}

De modellen die de structuur van een inhoudsfragment definiëren, worden momenteel niet via een HTTP-API weergegeven. Daarom moet de *consument* op de hoogte zijn van het model van een fragment (ten minste minimaal), hoewel de meeste informatie kan worden afgeleid uit de lading; als gegevenstypen, enz. maken deel uit van de definitie.

Als u een nieuw inhoudsfragment wilt maken, moet u het pad (interne gegevensopslagruimte) van het model opgeven.

#### Gekoppelde inhoud {#associated-content}

Gekoppelde inhoud wordt momenteel niet weergegeven.

## Gebruiken {#using}

Het gebruik kan verschillen afhankelijk van of u een auteur AEM of publicatiemilieu, samen met uw specifiek gebruiksgeval gebruikt.

* Het maken is strikt gebonden aan een instantie van de auteur ([en er is momenteel geen manier om een fragment te repliceren om te publiceren met behulp van deze API](/help/assets/assets-api-content-fragments.md#limitations)).
* De levering is mogelijk van beide, aangezien AEM gevraagde inhoud slechts in formaat JSON dient.

   * Opslag en levering van een AEM-auteur-instantie zou voldoende moeten zijn voor toepassingen achter de firewall en in de mediabibliotheek.

   * Voor live webweergave wordt een AEM-publicatie-instantie aanbevolen.

>[!CAUTION]
>
>De configuratie van de verzender op AEM wolkeninstanties zou toegang tot kunnen blokkeren `/api`.

<!--
>[!NOTE]
>
>For further details, see the [API Reference](/help/assets/assets-api-content-fragments.md#api-reference). In particular, [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html). 
-->

### Lezen/Levering {#read-delivery}

Gebruik gebeurt via:

`GET /{cfParentPath}/{cfName}.json`

Bijvoorbeeld:

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

De reactie is geserialiseerd met JSON met de inhoud gestructureerd zoals in het inhoudsfragment. Referenties worden als referentie-URL&#39;s geleverd.

Er zijn twee typen leesbewerkingen mogelijk:

* Als u een specifiek inhoudsfragment leest per pad, wordt hiermee de JSON-representatie van het inhoudsfragment geretourneerd.
* Een map met inhoudsfragmenten lezen op pad: Hiermee worden de JSON-representaties van alle inhoudsfragmenten in de map geretourneerd.

### Maken {#create}

Gebruik gebeurt via:

`POST /{cfParentPath}/{cfName}`

De hoofdtekst moet een JSON-representatie bevatten van het inhoudsfragment dat moet worden gemaakt, inclusief de initiële inhoud die moet worden ingesteld op de elementen van het inhoudsfragment. Het is verplicht om de `cq:model` eigenschap in te stellen en deze moet verwijzen naar een geldig inhoudsfragmentmodel. Als u dit niet doet, treedt er een fout op. Er moet ook een koptekst worden toegevoegd `Content-Type` die is ingesteld op `application/json`.

### Update {#update}

Gebruik is via

`PUT /{cfParentPath}/{cfName}`

De hoofdtekst moet een JSON-representatie bevatten van wat voor het opgegeven inhoudsfragment moet worden bijgewerkt.

Dit kan gewoon de titel of beschrijving zijn van een inhoudsfragment, of één element, of alle elementwaarden en/of metagegevens.

### Verwijderen {#delete}

Gebruik gebeurt via:

`DELETE /{cfParentPath}/{cfName}`

## Beperkingen {#limitations}

Er zijn enkele beperkingen:

* **Variaties kunnen niet worden geschreven en bijgewerkt.** Als deze variaties aan een lading worden toegevoegd (bijvoorbeeld voor updates) zullen zij worden genegeerd. De variatie zal echter via levering ( `GET`) worden bereikt.

* **Inhoudsfragmentmodellen worden momenteel niet ondersteund**: ze kunnen niet worden gelezen of gemaakt. Ontwikkelaars moeten het juiste pad naar het inhoudsfragmentmodel weten om een nieuw inhoudsfragment te kunnen maken of een bestaand inhoudsfragment bij te werken. Momenteel is de enige methode om een overzicht van deze te krijgen door het beleid UI.
* **Verwijzingen worden genegeerd**. Er wordt momenteel niet gecontroleerd of naar een bestaand inhoudsfragment wordt verwezen. Daarom kan het verwijderen van een inhoudsfragment bijvoorbeeld resulteren in problemen op een pagina die een verwijzing naar het verwijderde inhoudsfragment bevat.

## Statuscodes en foutberichten {#status-codes-and-error-messages}

De volgende statuscodes kunnen in de relevante omstandigheden worden gezien:

* **200** (OK)

   Geretourneerd wanneer:

   * een inhoudsfragment aanvragen via `GET`

   * het bijwerken van een inhoudsfragment via `PUT`

* **201** (gemaakt)

   Geretourneerd wanneer:

   * een inhoudsfragment maken via `POST`

* **404** (Niet gevonden)

   Geretourneerd wanneer:

   * het gewenste inhoudsfragment bestaat niet

* **500** (interne serverfout)

   >[!NOTE]
   >
   >Deze fout wordt geretourneerd:
   >
   >    * wanneer een fout is opgetreden die niet met een specifieke code kan worden geïdentificeerd
   >    * wanneer de opgegeven lading niet geldig was


   In het volgende voorbeeld worden algemene scenario&#39;s weergegeven wanneer deze foutstatus wordt geretourneerd, samen met het gegenereerde foutbericht (monospace):

   * Bovenliggende map bestaat niet (wanneer u een inhoudsfragment maakt via `POST`)
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
   De gedetailleerde foutberichten worden meestal als volgt geretourneerd:

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
<!--
* [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
-->

* [HTTP-API voor assets](/help/assets/mac-api-assets.md)

   * [Beschikbare functies](/help/assets/mac-api-assets.md#available-features)

## Aanvullende bronnen {#additional-resources}

Zie voor meer informatie:

* [Elementen HTTP API-documentatie](/help/assets/mac-api-assets.md)
* [AEM Gem-sessie: OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)

