---
title: Adobe Experience Manager as a Cloud Service Content Fragments Support in Assets HTTP API
description: Leer over steun voor de Fragments van de Inhoud in de API van Activa HTTP, een belangrijk stuk van AEM koploze leveringseigenschap.
feature: Content Fragments,Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
source-git-commit: 80ac947976bab2b0bfedb4ff9d5dd4634de6b4fc
workflow-type: tm+mt
source-wordcount: '1783'
ht-degree: 1%

---

# Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets {#content-fragments-support-in-aem-assets-http-api}

## Overzicht {#overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/assets-api-content-fragments.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Leer over steun voor de Fragments van de Inhoud in de API van Activa HTTP, een belangrijk stuk van AEM koploze leveringseigenschap.

>[!NOTE]
>
>De [Elementen HTTP-API](/help/assets/mac-api-assets.md) omvat:
>
>* REST-API voor middelen
>* inclusief ondersteuning voor inhoudsfragmenten
>
>De huidige implementatie van de HTTP-API voor middelen is gebaseerd op de [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) architectonische stijl.

De [REST-API voor middelen](/help/assets/mac-api-assets.md) Hiermee kunnen ontwikkelaars voor Adobe Experience Manager as a Cloud Service inhoud (opgeslagen in AEM) direct via de HTTP-API benaderen via CRUD-bewerkingen (Maken, Lezen, Bijwerken, Verwijderen).

Met de API kunt u Adobe Experience Manager as a Cloud Service als een headless CMS (Content Management System) gebruiken door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken.

Bijvoorbeeld: [Toepassingen op één pagina (SPA)](/help/implementing/developing/hybrid/introduction.md), op framework gebaseerd of aangepast, vereisen inhoud die via de HTTP-API wordt aangeboden, vaak in JSON-indeling.

while [AEM kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) Verstrek een zeer uitvoerige, flexibele en klantgerichte API die vereiste Gelezen verrichtingen voor dit doel kan dienen, en de waarvan output JSON kan worden aangepast, vereisen zij AEM WCM (het Beheer van de Inhoud van het Web) knowhow voor implementatie aangezien zij in pagina&#39;s moeten worden ontvangen die op specifieke AEM malplaatjes gebaseerd zijn. Niet elke SPA ontwikkelingsorganisatie heeft directe toegang tot deze kennis.

Dit is wanneer de REST API van Activa kan worden gebruikt. Ontwikkelaars hebben direct toegang tot elementen (bijvoorbeeld afbeeldingen en inhoudsfragmenten), zonder dat ze eerst in een pagina moeten worden ingesloten en hun inhoud in geserialiseerde JSON-indeling moeten leveren.

>[!NOTE]
>
>Het is niet mogelijk JSON-uitvoer van de REST API voor middelen aan te passen.

Met de REST API voor middelen kunnen ontwikkelaars ook inhoud wijzigen door nieuwe elementen, inhoudsfragmenten en mappen te maken, bij te werken of te verwijderen.

De REST-API voor middelen:

* volgt [HATEOAS-beginsel](https://en.wikipedia.org/wiki/HATEOAS)

* implementeert de [SIREN-indeling](https://github.com/kevinswiber/siren)

## Vereisten {#prerequisites}

De REST API voor middelen is beschikbaar voor elke installatie van een recente Adobe Experience Manager as a Cloud Service-versie die buiten de box valt.

## Belangrijke concepten {#key-concepts}

De REST API-aanbiedingen voor middelen [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)-style toegang tot elementen die zijn opgeslagen in een AEM instantie.

Het gebruikt de `/api/assets` eindpunt en vereist de weg van de activa om tot het toegang te hebben (zonder het leiden `/content/dam`).

* Dit betekent dat toegang tot het actief moet worden verkregen tegen:
   * `/content/dam/path/to/asset`
* U moet een aanvraag indienen:
   * `/api/assets/path/to/asset`

Bijvoorbeeld om `/content/dam/wknd/en/adventures/cycling-tuscany`, verzoek `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Toegang over:
>
>* `/api/assets` **niet** het gebruik van de `.model` kiezer.
>* `/content/path/to/page` **doet** het gebruik van de `.model` kiezer.


De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - om een JSON-representatie van een middel of een map op te halen
* **POST** - om nieuwe elementen of mappen te maken
* **PUT** - om de eigenschappen van een middel of een omslag bij te werken
* **DELETE** - om een middel of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; moet u bijvoorbeeld definiëren dat een map of element moet worden gemaakt met een **POST** verzoek.

De exacte indeling van ondersteunde aanvragen wordt gedefinieerd in het dialoogvenster [API-naslag](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference) documentatie.

### Transactioneel gedrag {#transactional-behavior}

Alle verzoeken zijn atomisch.

Dit betekent dat`write`) verzoeken kunnen niet worden gecombineerd tot één enkele transactie die als één enkele entiteit zou kunnen slagen of mislukken.

### AEM (Middelen) REST API versus AEM componenten {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Verhouding</td>
   <td>REST-API voor middelen<br/> </td>
   <td>AEM<br/> (componenten die gebruikmaken van modellen voor schuiven)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Ondersteunde gebruikscase(s)</td>
   <td>Algemeen doel.</td>
   <td><p>Geoptimaliseerd voor gebruik in een toepassing voor één pagina (SPA) of in een andere (content consuming) context.</p> <p>Kan ook lay-outgegevens bevatten.</p> </td>
  </tr>
  <tr>
   <td>Ondersteunde bewerkingen</td>
   <td><p>Maken, lezen, bijwerken, verwijderen.</p> <p>Met extra bewerkingen afhankelijk van het type entiteit.</p> </td>
   <td>Alleen-lezen.</td>
  </tr>
  <tr>
   <td>Toegang</td>
   <td><p>Kan rechtstreeks worden benaderd.</p> <p>Gebruikt de <code>/api/assets </code>eindpunt, toegewezen aan <code>/content/dam</code> (in de repository).</p> 
   <p>Een voorbeeldpad ziet er als volgt uit: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Moet door een AEM component op een AEM pagina worden van verwijzingen voorzien.</p> <p>Gebruikt de <code>.model</code> om de JSON-representatie te maken.</p> <p>Een voorbeeldpad ziet er als volgt uit:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Beveiliging</td>
   <td><p>Er zijn meerdere opties mogelijk.</p> <p>OAuth wordt voorgesteld; kan los van standaardopstelling worden gevormd.</p> </td>
   <td>Gebruikt AEM standaardinstallatie.</td>
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

Als de REST API van Middelen binnen een milieu zonder specifieke authentificatievereisten wordt gebruikt, moet AEM filter CORS correct worden gevormd.

>[!NOTE]
>
>Zie voor meer informatie:
>
>* [CORS/AEM toegelicht](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [Video - Ontwikkelen voor CORS met AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
>


In omgevingen met specifieke verificatievereisten wordt OAuth aanbevolen.

## Beschikbare functies {#available-features}

Inhoudsfragmenten zijn een specifiek type element, zie [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md).

Zie voor meer informatie over functies die beschikbaar zijn via de API:

* De [REST-API voor middelen](/help/assets/mac-api-assets.md)
* [Typen entiteiten](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types), waarbij de kenmerken die specifiek zijn voor elk ondersteund type (voor zover relevant voor inhoudsfragmenten) worden toegelicht

### Paginering {#paging}

De REST API voor middelen ondersteunt paginering (voor GET-aanvragen) via de URL-parameters:

* `offset` - het nummer van de eerste (onderliggende) entiteit die moet worden opgehaald
* `limit` - het maximumaantal geretourneerde entiteiten

De reactie zal het pagineren informatie als deel van bevatten `properties` van de SIREN-uitvoer. Dit `srn:paging` eigenschap bevat het totale aantal (onderliggende) entiteiten ( `total`), de verschuiving en de limiet ( `offset`, `limit`) zoals opgegeven in de aanvraag.

>[!NOTE]
>
>Paginering wordt doorgaans toegepast op containerentiteiten (d.w.z. mappen of elementen met uitvoeringen), aangezien deze betrekking hebben op de onderliggende elementen van de aangezochte entiteit.

#### Voorbeeld: Paginering {#example-paging}

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

De REST API van Middelen stelt toegang tot de eigenschappen van een omslag bloot; bijvoorbeeld naam, titel, enz. Elementen worden weergegeven als onderliggende entiteiten van mappen en submappen.

>[!NOTE]
>
>Afhankelijk van het type element van de onderliggende elementen en mappen bevat de lijst met onderliggende entiteiten mogelijk al de volledige set eigenschappen die de onderliggende entiteit definieert. Alternatief, slechts kan een beperkte reeks eigenschappen voor een entiteit in deze lijst van kindentiteiten worden blootgesteld.

### Assets {#assets}

Als een element wordt gevraagd, zal de reactie zijn meta-gegevens terugkeren; zoals titel, naam en andere informatie zoals gedefinieerd in het desbetreffende elementschema.

De binaire gegevens van een element worden blootgesteld als een verbinding SIREN van type `content`.

Elementen kunnen meerdere uitvoeringen hebben. Deze worden doorgaans weergegeven als onderliggende entiteiten, waarbij één uitzondering een miniatuuruitvoering is die wordt weergegeven als een koppeling van het type `thumbnail` ( `rel="thumbnail"`).

### Contentfragmenten {#content-fragments}

A [inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal soort actief. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, getallen, datums.

Aangezien er verschillende verschillen zijn tussen *standaard* elementen (zoals afbeeldingen of audio). Voor de afhandeling ervan gelden enkele aanvullende regels.

#### Vertegenwoordiging {#representation}

Inhoudsfragmenten:

* Maak geen binaire gegevens beschikbaar.
* volledig ingesloten in de JSON-uitvoer (binnen de `properties` eigenschap).

* Wordt ook als atomisch beschouwd, d.w.z. de elementen en variaties worden blootgesteld als onderdeel van de eigenschappen van het fragment ten opzichte van als koppelingen of onderliggende entiteiten. Op deze manier hebt u efficiënt toegang tot de lading van een fragment.

#### Inhoudsmodellen en Inhoudsfragmenten {#content-models-and-content-fragments}

De modellen die de structuur van een inhoudsfragment definiëren, worden momenteel niet via een HTTP-API weergegeven. Daarom *consument* moet op de hoogte zijn van het model van een fragment (ten minste minimaal), hoewel de meeste informatie kan worden afgeleid uit de lading; als gegevenstypen, enz. maken deel uit van de definitie.

Als u een nieuw inhoudsfragment wilt maken, moet u het pad (interne gegevensopslagruimte) van het model opgeven.

#### Gekoppelde inhoud {#associated-content}

Gekoppelde inhoud wordt momenteel niet weergegeven.

## Gebruiken {#using}

Het gebruik kan verschillen afhankelijk van of u een AEM auteur of publicatieomgeving gebruikt, samen met uw specifieke gebruiksscenario.

* Het wordt ten zeerste aanbevolen dat het maken is gebonden aan een instantie van de auteur ([en er is momenteel geen manier om een fragment te repliceren dat moet worden gepubliceerd met deze API](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* De levering is mogelijk van beide, aangezien AEM gevraagde inhoud in formaat slechts JSON dient.

   * Opslag en levering vanuit een AEM auteur-instantie zouden voldoende moeten zijn voor toepassingen achter de firewall, in de mediabibliotheek.

   * Voor live webweergave wordt een AEM-publicatie-instantie aanbevolen.

>[!CAUTION]
>
>De configuratie van de verzender op AEM wolkeninstanties zou toegang tot kunnen blokkeren `/api`.

>[!NOTE]
>
>Zie voor meer informatie de [API-naslag](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). Met name: [Adobe Experience Manager Assets API - Inhoudsfragmenten](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html).

## Beperkingen {#limitations}

Er zijn enkele beperkingen:

* **Inhoudsfragmentmodellen worden momenteel niet ondersteund**: ze kunnen niet worden gelezen of gemaakt. Ontwikkelaars moeten het juiste pad naar het inhoudsfragmentmodel weten om een nieuw inhoudsfragment te kunnen maken of een bestaand inhoudsfragment bij te werken. Momenteel is de enige methode om een overzicht van deze te krijgen door het beleid UI.
* **Verwijzingen worden genegeerd**. Er wordt momenteel niet gecontroleerd of naar een bestaand inhoudsfragment wordt verwezen. Daarom kan het verwijderen van een inhoudsfragment bijvoorbeeld resulteren in problemen op een pagina die een verwijzing naar het verwijderde inhoudsfragment bevat.
* **JSON-gegevenstype** De REST API-uitvoer van de *JSON-gegevenstype* is momenteel *op tekenreeks gebaseerde uitvoer*.

## Statuscodes en foutberichten {#status-codes-and-error-messages}

De volgende statuscodes kunnen in de relevante omstandigheden worden gezien:

* **200** (OK)

   Geretourneerd wanneer:

   * een inhoudsfragment aanvragen via `GET`
   * het bijwerken van een inhoudsfragment via `PUT`

* **201** (Gemaakt)

   Geretourneerd wanneer:

   * een inhoudsfragment maken via `POST`

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

* [Adobe Experience Manager Assets API - Inhoudsfragmenten](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html)

* [HTTP-API voor assets](/help/assets/mac-api-assets.md)

   * [Beschikbare functies](/help/assets/mac-api-assets.md#available-features)

## Aanvullende bronnen {#additional-resources}

Zie voor meer informatie:

* [Elementen HTTP API-documentatie](/help/assets/mac-api-assets.md)
* [AEM Gem-sessie: OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)
