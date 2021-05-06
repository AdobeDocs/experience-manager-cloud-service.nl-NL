---
title: Uw inhoud bijwerken via AEM Assets API's
description: In dit deel van de AEM Headless Developer Journey leert u hoe u de REST API kunt gebruiken om toegang te krijgen tot de inhoud van de Content Fragments en deze bij te werken.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 0c47dec1e96fc3137d17fc3033f05bf1ae278141
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 2%

---

# Uw inhoud bijwerken via AEM Assets API&#39;s {#update-your-content}

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Headless Developer Journey,](overview.md) leert u hoe u de REST API kunt gebruiken om de inhoud van uw Content Fragments te openen en bij te werken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [How to Access Your Content via AEM Delivery APIs](access-your-content.md) leerde u hoe te om tot uw inhoud zonder kop in AEM via AEM GraphQL API toegang te hebben en u zou nu moeten:

* Heb een inzicht op hoog niveau van GraphQL.
* Begrijp hoe de AEM GraphQL API werkt.
* Begrijp sommige praktische steekproefvragen.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe u bestaande inhoud zonder kop in AEM kunt bijwerken via de REST API.

## Doel {#objective}

* **Publiek**: Geavanceerd
* **Doel**: Leer hoe u de REST API kunt gebruiken om de inhoud van de inhoudsfragmenten te openen en bij te werken:
   * Introduceer de AEM Assets HTTP API.
   * Introduceer en bespreek de ondersteuning voor inhoudsfragmenten in de API.
   * Details van de API illustreren.

<!--
  * Look at sample code to see how things work in practice.
-->

## Waarom hebt u de HTTP-API voor middelen nodig voor inhoudsfragmenten {#why-http-api}

In het vorige stadium van de Headless Reis, leerde u over het gebruiken van AEM GraphQL API om uw inhoud terug te winnen gebruikend vragen.

Waarom is er dus nog een API nodig?

Met de HTTP-API voor middelen kunt u uw inhoud **Lezen**, maar u kunt ook **Maken**, **Bijwerken** en **Verwijderen** inhoud - handelingen uitvoeren die niet mogelijk zijn met de API GraphQL.

## HTTP-API voor assets {#assets-http-api}

De [Elementen HTTP API](/help/assets/mac-api-assets.md) omvat het volgende:

* REST-API voor middelen
* inclusief ondersteuning voor inhoudsfragmenten

De huidige implementatie van de Elementen HTTP API is gebaseerd op de **REST** architecturale stijl.

Met de REST-API voor middelen hebben ontwikkelaars van Adobe Experience Manager als Cloud Service rechtstreeks via de HTTP-API toegang tot inhoud (opgeslagen in AEM) via de bewerkingen **CRUD** (Maken, Lezen, Bijwerken, Verwijderen).

Met de API kunt u Adobe Experience Manager als een Cloud Service als een CMS zonder kop (Content Management System) gebruiken door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken.

Toepassingen voor één pagina (SPA), die zijn gebaseerd op een framework of die zijn aangepast, vereisen bijvoorbeeld inhoud die via een API wordt aangeboden, vaak in JSON-indeling.

Terwijl AEM de Componenten van de Kern een zeer uitvoerige, flexibele en klantgerichte API verstrekken die vereiste Gelezen verrichtingen voor dit doel kan dienen, en de waarvan output JSON kan worden aangepast, vereisen zij AEM WCM (het Beheer van de Inhoud van het Web) knowhow voor implementatie aangezien zij in pagina&#39;s moeten worden ontvangen die op specifieke AEM malplaatjes gebaseerd zijn. Niet elke SPA ontwikkelingsorganisatie heeft directe toegang tot deze kennis.

Dit is wanneer de REST API van Activa kan worden gebruikt. Ontwikkelaars hebben direct toegang tot elementen (bijvoorbeeld afbeeldingen en inhoudsfragmenten), zonder dat ze eerst in een pagina moeten worden ingesloten en hun inhoud in geserialiseerde JSON-indeling moeten leveren.

>[!NOTE]
>
>Het is niet mogelijk JSON-uitvoer van de REST API voor middelen aan te passen.

Met de REST API voor middelen kunnen ontwikkelaars ook inhoud wijzigen door nieuwe elementen, inhoudsfragmenten en mappen te maken, bij te werken of te verwijderen.

De REST-API voor middelen:

* volgt het HATEOAS-beginsel
* implementeert de SIREN-indeling

## Vereisten {#prerequisites}

De REST API voor middelen is beschikbaar voor elke installatie van een recente Adobe Experience Manager als Cloud Service buiten de box.

## Belangrijke concepten {#key-concepts}

De REST API van Activa biedt REST-stijl toegang tot activa die binnen een AEM instantie worden opgeslagen.

Het gebruikt het `/api/assets` eindpunt en vereist de weg van de activa om tot het (zonder het leiden `/content/dam`) toegang te hebben.

* Dit betekent dat toegang tot het actief moet worden verkregen tegen:
   * `/content/dam/path/to/asset`
* U moet een aanvraag indienen:
   * `/api/assets/path/to/asset`

Als u bijvoorbeeld toegang wilt krijgen tot `/content/dam/wknd/en/adventures/cycling-tuscany`, vraagt u `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Toegang over:
>
>* `/api/assets` **U** hoeft de  `.model` kiezer niet te gebruiken.
>* `/content/path/to/page` **Het** gebruik van de  `.model` kiezer is vereist.


De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - om een JSON-representatie van een element of map op te halen
* **POST** - om nieuwe elementen of mappen te maken
* **PUT** - om de eigenschappen van een middel of een omslag bij te werken
* **DELETE** - om een middel of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; Stel bijvoorbeeld dat een map of een element moet worden gemaakt door een **POST**-verzoek.

De exacte indeling van ondersteunde aanvragen wordt gedefinieerd in de API-naslagdocumentatie.

### Transactioneel gedrag {#transactional-behavior}

Alle verzoeken zijn atomisch.

Dit betekent dat de verdere (`write`) verzoeken niet in één enkele transactie kunnen worden gecombineerd die als één enkele entiteit zou kunnen slagen of ontbreken.

### AEM (Middelen) REST API versus AEM componenten {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Verhouding</td>
   <td>Elementen REST API<br/> </td>
   <td>AEM Component<br/> (componenten die Sling Models gebruiken)</td>
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
   <td><p>Kan rechtstreeks worden benaderd.</p> <p>Gebruikt het <code>/api/assets </code>eindpunt, toegewezen aan <code>/content/dam</code> (in de bewaarplaats).</p> 
   <p>Een voorbeeldpad zou er als volgt uitzien: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Moet door een AEM component op een AEM pagina worden van verwijzingen voorzien.</p> <p>Gebruikt de <code>.model</code> selecteur om de vertegenwoordiging tot stand te brengen JSON.</p> <p>Een voorbeeldpad zou er als volgt uitzien:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
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
>* CORS/AEM toegelicht
>* Video - Ontwikkelen voor CORS met AEM

>



In omgevingen met specifieke verificatievereisten wordt OAuth aanbevolen.

## Beschikbare functies {#available-features}

Inhoudsfragmenten zijn een specifiek type element. Zie Werken met inhoudfragmenten.

Zie voor meer informatie over functies die beschikbaar zijn via de API:

* De REST-API voor middelen
* Soorten entiteiten, waarbij de kenmerken die specifiek zijn voor elk ondersteund type (voor zover relevant voor inhoudsfragmenten) worden toegelicht

### {#paging} pagineren

De REST API voor middelen ondersteunt paginering (voor GET-aanvragen) via de URL-parameters:

* `offset` - het nummer van de eerste (onderliggende) entiteit die moet worden opgehaald
* `limit` - het maximumaantal geretourneerde entiteiten

De reactie zal het pagineren informatie als deel van `properties` sectie van de output bevatten SIREN. Deze `srn:paging` eigenschap bevat het totale aantal (onderliggende) entiteiten ( `total`), de verschuiving en de limiet ( `offset`, `limit`) zoals opgegeven in de aanvraag.

>[!NOTE]
>
>Paginering wordt doorgaans toegepast op containerentiteiten (d.w.z. mappen of elementen met uitvoeringen), aangezien deze betrekking hebben op de onderliggende elementen van de aangezochte entiteit.

#### Voorbeeld: {#example-paging} pagineren

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

Een inhoudsfragment is een speciaal type element. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, getallen, datums.

Aangezien er verschillende verschillen zijn met *standard* elementen (zoals afbeeldingen of audio), zijn er enkele aanvullende regels van toepassing op de afhandeling ervan.

#### Weergave {#representation}

Inhoudsfragmenten:

* Maak geen binaire gegevens beschikbaar.
* Deze bevinden zich volledig in de JSON-uitvoer (binnen de eigenschap `properties`).

* Wordt ook als atomisch beschouwd, d.w.z. de elementen en variaties worden blootgesteld als onderdeel van de eigenschappen van het fragment ten opzichte van als koppelingen of onderliggende entiteiten. Op deze manier hebt u efficiënt toegang tot de lading van een fragment.

#### Content Models and Content Fragments {#content-models-and-content-fragments}

De modellen die de structuur van een inhoudsfragment definiëren, worden momenteel niet via een HTTP-API weergegeven. Daarom moet de *consument* op de hoogte zijn van het model van een fragment (ten minste een minimum) - hoewel de meeste informatie kan worden afgeleid uit de lading; als gegevenstypen, enz. maken deel uit van de definitie.

Als u een nieuw inhoudsfragment wilt maken, moet u het pad (interne gegevensopslagruimte) van het model opgeven.

#### Gekoppelde inhoud {#associated-content}

Gekoppelde inhoud wordt momenteel niet weergegeven.

## De REST API {#using-aem-assets-rest-api} voor middelen gebruiken

Voor meer informatie over het gebruik van de AEM Assets REST API kunt u verwijzen naar:

* Adobe Experience Manager Assets HTTP API
* Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets

## Volgende {#whats-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Begrijp de AEM Assets HTTP API.
* Begrijp hoe de Fragments van de Inhoud in deze API worden gesteund.

<!--
* Have experience with sample code and know how the API works in practice.
-->

U zou uw AEM onophoudelijke reis moeten voortzetten door het document [te herzien hoe te om het allen samen te brengen - Uw App en Uw Inhoud in AEM Koploze](put-it-all-together.md) waar u leert hoe te om uw AEM Project zonder Zoppen te nemen en het voor te bereiden op het leven.

## Aanvullende bronnen {#additional-resources}

* [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
* [HATEOAS-beginsel](https://en.wikipedia.org/wiki/HATEOAS)
* [SIREN-indeling](https://github.com/kevinswiber/siren)
* [HTTP-API voor assets](/help/assets/mac-api-assets.md)
* [Content Fragments REST API](/help/assets/content-fragments/assets-api-content-fragments.md)
   * [API-naslag](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)
* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)
* [AEM kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [CORS/AEM toegelicht](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [Video - Ontwikkelen voor CORS met AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

