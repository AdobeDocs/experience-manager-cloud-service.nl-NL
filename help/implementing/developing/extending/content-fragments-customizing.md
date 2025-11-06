---
title: Inhoudsfragmenten aanpassen en uitbreiden
description: Een inhoudsfragment breidt een standaardelement uit. Leer hoe u ze kunt aanpassen.
exl-id: 58152d6e-21b6-4f45-a45c-0f46ee58825e
feature: Developing, Content Fragments
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 0%

---

# Inhoudsfragmenten aanpassen en uitbreiden{#customizing-and-extending-content-fragments}

In Adobe Experience Manager as a Cloud Service breidt een inhoudsfragment een standaard element uit. Zie:

* [&#x200B; Creërend en het Leiden de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md) en [&#x200B; Pagina Authoring met de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) voor verdere informatie over inhoudsfragmenten.

* [&#x200B; het Leiden Assets &#x200B;](/help/assets/manage-digital-assets.md) voor verdere informatie over standaardactiva.

## Architectuur {#architecture}

De basis [&#x200B; samenstellende delen &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md#constituent-parts-of-a-content-fragment) van een inhoudsfragment zijn het volgende:

* A *het Fragment van de Inhoud* zelf
* Het bestaat uit één of meerdere *Elementen van de Inhoud*
* Het kan één of meerdere *Variaties van de Inhoud* hebben

De afzonderlijke inhoudsfragmenten zijn gebaseerd op modellen van inhoudsfragmenten:

* Inhoudsfragmentmodellen definiëren de structuur van een inhoudsfragment wanneer dit wordt gemaakt.
* Een fragment verwijst naar het model. Wijzigingen in het model kunnen dus invloed hebben op afhankelijke fragmenten of dit effect hebben.
* Modellen zijn opgebouwd uit gegevenstypen.
* Functies om nieuwe variaties toe te voegen, enzovoort, moeten het fragment overeenkomstig bijwerken.

  >[!NOTE]
  >
  >Als u een inhoudsfragment wilt weergeven/renderen, moet uw account `read` machtigingen voor het model hebben.

  >[!CAUTION]
  >
  >Wijzigingen in een bestaand inhoudsfragmentmodel kunnen van invloed zijn op afhankelijke fragmenten. Dit kan leiden tot weeseigenschappen in die fragmenten.

### Integratie van sites met Assets {#integration-of-sites-with-assets}

Content Fragment Management (CFM) maakt deel uit van Adobe Experience Manager (AEM) Assets als:

* Inhoudsfragmenten zijn elementen.
* Ze gebruiken de bestaande Assets-functionaliteit.
* Ze zijn volledig geïntegreerd met Assets (beheerconsoles, enzovoort).

Inhoudsfragmenten worden als een AEM Sites-functie beschouwd:

* Deze worden gebruikt bij het ontwerpen van uw pagina&#39;s.

#### Inhoudsfragmenten toewijzen aan Assets {#mapping-content-fragments-to-assets}

![&#x200B; inhoudsfragment aan activa &#x200B;](assets/content-fragment-to-assets.png)

Inhoudsfragmenten, gebaseerd op een inhoudsfragmentmodel, worden toegewezen aan één element:

* Alle inhoud wordt opgeslagen onder het knooppunt `jcr:content/data` van het element:

   * De elementgegevens worden opgeslagen onder het hoofdsubknooppunt:
     `jcr:content/data/master`

   * Variaties worden opgeslagen onder een subknooppunt met de naam van de variatie:
bijvoorbeeld, `jcr:content/data/myvariation`

   * De gegevens van elk element worden in de respectieve subnode opgeslagen als een bezit met de elementnaam:
De inhoud van element `text` wordt bijvoorbeeld opgeslagen als eigenschap `text` on `jcr:content/data/master` .

* Metagegevens en bijbehorende inhoud worden opgeslagen onder `jcr:content/metadata`
Met uitzondering van de titel en beschrijving, die niet als traditionele metagegevens worden beschouwd en worden opgeslagen op `jcr:content`

#### Locatie van element {#asset-location}

Net als bij standaardelementen wordt een inhoudsfragment opgeslagen onder:

`/content/dam`

#### Elementmachtigingen {#asset-permissions}

Zie [&#x200B; het Fragment van de Inhoud - Schrap Overwegingen &#x200B;](/help/sites-cloud/administering/content-fragments/delete-considerations.md).

#### Functie-integratie {#feature-integration}

Integreren met Assets core:

* De functie CFM (Content Fragment Management) is gebaseerd op de Assets-kern.

* CFM biedt zijn eigen implementaties voor items in de kaart-/kolom-/lijstweergaven; deze plug-in de bestaande Assets-implementaties voor het renderen van inhoud.

* Verschillende Assets-componenten zijn uitgebreid om rekening te houden met inhoudsfragmenten.

### Inhoudsfragmenten op pagina&#39;s gebruiken {#using-content-fragments-in-pages}

>[!CAUTION]
>
>De [&#x200B; component van het Fragment van de Inhoud is een deel van de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html). Zie [&#x200B; het Ontwikkelen van de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) voor meer details.

Vanuit AEM-pagina&#39;s kan naar inhoudsfragmenten worden verwezen, net als met elk ander elementtype. AEM verstrekt de **[kerncomponent van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)** - a [&#x200B; component die u inhoudsfragmenten op uw pagina&#39;s &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-a-content-fragment-to-your-page) laat omvatten. U kunt dit **[de kerncomponent van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html)** ook uitbreiden.

* De component gebruikt de eigenschap `fragmentPath` om naar het daadwerkelijke inhoudsfragment te verwijzen. De eigenschap `fragmentPath` wordt op dezelfde manier afgehandeld als soortgelijke eigenschappen van andere elementtypen, bijvoorbeeld wanneer het inhoudsfragment naar een andere locatie wordt verplaatst.

* Met de component kunt u de variatie selecteren die moet worden weergegeven.

* U kunt ook een reeks alinea&#39;s selecteren om de uitvoer te beperken. Deze alinea kan bijvoorbeeld worden gebruikt voor uitvoer met meerdere kolommen.

* De component staat tussenliggende inhoud toe:

   * Hier kunt u met de component andere elementen (afbeeldingen, enzovoort) tussen de alinea&#39;s van het fragment waarnaar wordt verwezen plaatsen.

   * Voor tussenliggende inhoud:

      * Houd rekening met de mogelijkheid van onstabiele referenties. Tussen de inhoud (die bij het ontwerpen van een pagina wordt toegevoegd) bevindt zich geen vaste relatie met de alinea die ernaast staat. Als u een nieuwe alinea invoegt (in de inhoudfragmenteditor) vóór de positie van de tussenliggende inhoud, kan de relatieve positie verloren gaan.

      * Overweeg de extra parameters (zoals variatie- en alineafilters) om te configureren wat op de pagina wordt weergegeven.

>[!NOTE]
>
>**Model van het Fragment van de Inhoud:**
>
>Wanneer een inhoudsfragment op een pagina wordt gebruikt, wordt verwezen naar het model van het inhoudsfragment waarop het is gebaseerd.
>
>Dit betekent dat als het model niet is gepubliceerd op het moment dat u de pagina publiceert, dit wordt gemarkeerd en het model wordt toegevoegd aan de bronnen die met de pagina moeten worden gepubliceerd.

### Integratie met andere frameworks {#integration-with-other-frameworks}

Inhoudsfragmenten kunnen worden geïntegreerd met:

* **Vertalingen**

  De Fragmenten van de inhoud zijn volledig geïntegreerd met het [&#x200B; de vertaalwerkschema van AEM &#x200B;](/help/sites-cloud/administering/translation/overview.md). Op architectonisch niveau betekent dit:

   * De afzonderlijke vertalingen van een inhoudsfragment zijn afzonderlijke fragmenten, bijvoorbeeld:

      * zij bevinden zich onder verschillende taalwortels, maar delen het relatieve pad onder de desbetreffende taalwortel:

        `/content/dam/<path>/en/<to>/<fragment>`

        vs

        `/content/dam/<path>/de/<to>/<fragment>`

   * Naast op regel gebaseerde paden is er geen andere verbinding tussen de verschillende taalversies van een inhoudsfragment. Deze fragmenten worden als twee afzonderlijke fragmenten behandeld, hoewel de interface de mogelijkheid biedt om tussen de taalvarianten te navigeren.

  >[!NOTE]
  >
  >De AEM-vertaalworkflow werkt met `/content` :
  >
  >* Aangezien de modellen van het inhoudsfragment in `/conf` verblijven, zijn deze niet inbegrepen in dergelijke vertalingen. U kunt de UI-tekenreeksen internationaliseren.

* **schema&#39;s van Meta-gegevens**

   * De fragmenten van de inhoud gebruiken en hergebruiken de [&#x200B; meta-gegevensschema&#39;s &#x200B;](/help/assets/metadata-schemas.md) die met standaardactiva kunnen worden bepaald.

   * CFM biedt een eigen, specifiek schema:

     `/libs/dam/content/schemaeditors/forms/contentfragment`

     dit kan zo nodig worden verlengd .

   * Het respectievelijke schema-formulier is geïntegreerd met de fragmenteditor.

## De API voor contentfragmentbeheer - Server-kant {#the-content-fragment-management-api-server-side}

U kunt de server-kant API gebruiken om tot uw inhoudsfragmenten toegang te hebben; zie:

[&#x200B; com.adobe.cq.dam.cfm &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/package-summary.html#package.description)

>[!CAUTION]
>
>Adobe raadt u aan de server-side API te gebruiken in plaats van rechtstreeks toegang te krijgen tot de inhoudsstructuur.

### Belangrijke interfaces {#key-interfaces}

De volgende drie interfaces kunnen als ingangspunten dienen:

* **Fragment van de Inhoud** ([&#x200B; ContentFragment &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

  Met deze interface kunt u op abstracte wijze met een inhoudsfragment werken.

  De interface voorziet u van de middelen:

   * Standaardgegevens beheren (bijvoorbeeld naam ophalen; titel/beschrijving ophalen/instellen)
   * Toegang tot metagegevens
   * Toegangselementen:

      * Lijstelementen
      * Elementen op naam ophalen
      * Creeer elementen (zie [&#x200B; Gebieden &#x200B;](#caveats))

      * Gegevens over toegangselementen (zie `ContentElement`)

   * Variaties weergeven die zijn gedefinieerd voor het fragment
   * Wereldwijd variaties maken
   * Gekoppelde inhoud beheren:

      * Lijstverzamelingen
      * Verzamelingen toevoegen
      * Verzamelingen verwijderen

   * Toegang krijgen tot het model van het fragment

  De interfaces die de belangrijkste elementen van een fragment vertegenwoordigen zijn:

   * **Element van de Inhoud** ([&#x200B; ContentElement &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Toegang tot variaties van een element:

         * Variaties weergeven
         * Variaties ophalen op naam
         * Creeer variaties (zie [&#x200B; Beveats &#x200B;](#caveats))
         * Verwijder variaties (zie [&#x200B; Gebieden &#x200B;](#caveats))
         * Toegang krijgen tot variatiegegevens (zie `ContentVariation`)

      * Sneltoets voor het oplossen van variaties (door een aanvullende, implementatiespecifieke fallback-logica toe te passen als de opgegeven variatie niet beschikbaar is voor een element)

   * **de Variatie van de Inhoud** ([&#x200B; ContentVariation &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Eenvoudige synchronisatie, gebaseerd op laatst gewijzigde informatie

  Alle drie de interfaces ( `ContentFragment`, `ContentElement`, `ContentVariation`) breiden de `Versionable` -interface uit, die versiemogelijkheden toevoegt, die vereist zijn voor inhoudsfragmenten:

   * Een versie van het element maken
   * Versies van het element weergeven
   * Hiermee wordt de inhoud opgehaald van een specifieke versie van het element met versiebeheer

### Aanpassen - Using adjustTo() {#adapting-using-adaptto}

Het volgende kan worden aangepast:

* `ContentFragment` kan worden aangepast aan:

   * `Resource` - de onderliggende Sling-bron; wanneer u de onderliggende `Resource` rechtstreeks bijwerkt, moet het `ContentFragment` -object opnieuw worden opgebouwd.

   * `Asset` - De DAM `Asset` -abstractie die het inhoudsfragment vertegenwoordigt. Wanneer u `Asset` rechtstreeks bijwerkt, moet het `ContentFragment` -object opnieuw worden opgebouwd.

* `ContentElement` kan worden aangepast aan:

   * [`ElementTemplate` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ElementTemplate.html) - voor de toegang tot van de structurele informatie van het element.

* [`FragmentTemplate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html)

* `Resource` kan worden aangepast aan:

   * `ContentFragment`

### Caveats {#caveats}

Er zij op gewezen dat:

* Volledige API wordt ontworpen om **niet** veranderingen automatisch te handhaven (tenzij anders vermeld in API JavaDoc). Zo, begaat altijd de middeloplosser van het respectieve verzoek (of resolver u eigenlijk gebruikt).

* Taken die extra inspanning zouden kunnen vereisen:

   * Adobe raadt u aan om variaties te maken vanuit `ContentFragment` . Dit zorgt ervoor dat alle elementen deze variatie delen en dat de juiste algemene gegevensstructuren zo nodig worden bijgewerkt om de nieuwe variatie in de inhoudsstructuur te weerspiegelen.

   * Wanneer u bestaande variaties via een element verwijdert, werkt u met `ContentElement.removeVariation()` de algemene gegevensstructuren die aan de variatie zijn toegewezen, niet bij. Om ervoor te zorgen dat deze gegevensstructuren gesynchroniseerd blijven, gebruikt u `ContentFragment.removeVariation()` , waarmee een variatie wereldwijd wordt verwijderd.

## De API voor contentfragmentbeheer - Client-kant {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>De client-side API is intern.

### Aanvullende informatie {#additional-information}

Zie het volgende:

* `filter.xml`

  Het `filter.xml` for content fragment management is zo geconfigureerd dat het niet overlapt met het Assets core content package.

## Sessies bewerken {#edit-sessions}

>[!CAUTION]
>
>Overweeg deze achtergrondinformatie. U wordt verondersteld om niets hier te veranderen (aangezien het als a *privé gebied* in de bewaarplaats) duidelijk is, maar het zou soms kunnen helpen om te begrijpen hoe de dingen onder de kap werken.

Het bewerken van een inhoudsfragment, dat meerdere weergaven kan beslaan (= HTML-pagina&#39;s), is atomisch. Als zulk atoommulti-mening uitgeeft mogelijkheden zijn geen typisch concept van AEM, gebruiken de inhoudsfragmenten wat een *het uitgeven zitting* wordt genoemd.

Er wordt een bewerkingssessie gestart wanneer de gebruiker een inhoudsfragment in de editor opent. De het uitgeven zitting wordt gebeëindigd wanneer de gebruiker de redacteur door of **te selecteren sparen** of **annuleert**.

Technisch, worden alle uitgeeft gedaan op *levende* inhoud, zoals met alle andere AEM die uitgeven. Wanneer de bewerkingssessie wordt gestart, wordt een versie van de huidige, onbewerkte status gemaakt. Als een gebruiker een bewerking annuleert, wordt die versie hersteld. Als de gebruiker **sparen** klikt, wordt niets specifiek gedaan, omdat het uitgeven op *levende* inhoud in werking werd gesteld, daarom worden alle veranderingen reeds voortgeduurd. Ook, leidt het klikken **sparen** sommige achtergrondverwerking zoals het creëren van volledige informatie van het tekstonderzoek, of het behandelen van gemengde-media activa, of allebei.

Er zijn enkele veiligheidsmaatregelen voor randgevallen, bijvoorbeeld als de gebruiker de editor probeert te verlaten zonder de bewerkingssessie op te slaan of te annuleren. Er is ook een periodieke automatische opslag beschikbaar om gegevensverlies te voorkomen.
Twee gebruikers kunnen hetzelfde inhoudsfragment gelijktijdig bewerken en daarom elkaars wijzigingen overschrijven. Om dit te verhinderen, moet het inhoudsfragment worden gesloten door de handeling van de Controle van DAM van het beleid ** op het fragment toe te passen.

## Voorbeelden {#examples}

### Voorbeeld: een bestaand inhoudsfragment openen {#example-accessing-an-existing-content-fragment}

Hiertoe kunt u de bron die de API vertegenwoordigt aanpassen aan:

`com.adobe.cq.dam.cfm.ContentFragment`

Bijvoorbeeld:

```java
// first, get the resource
Resource fragmentResource = resourceResolver.getResource("/content/dam/fragments/my-fragment");
// then adapt it
if (fragmentResource != null) {
    ContentFragment fragment = fragmentResource.adaptTo(ContentFragment.class);
    // the resource is now accessible through the API
}
```

### Voorbeeld: een inhoudsfragment maken {#example-creating-a-new-content-fragment}

Als u een inhoudsfragment programmatisch wilt maken, gebruikt u een `FragmentTemplate` die is aangepast op basis van een modelbron.

Bijvoorbeeld:

```java
Resource modelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = modelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Voorbeeld: het interval voor automatisch opslaan opgeven {#example-specifying-the-auto-save-interval}

Het [&#x200B; auto-sparen interval &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#save-close-and-versions) (die in seconden wordt gemeten) kan worden bepaald gebruikend de configuratiemanager (ConfMgr):

* Knooppunt: `<conf-root>/settings/dam/cfm/jcr:content`
* Eigenschapnaam: `autoSaveInterval`
* Type: `Long`

* Standaard: `600` (10 minuten); dit is gedefinieerd voor `/libs/settings/dam/cfm/jcr:content`

Als u een auto-sparen interval van 5 minuten wilt plaatsen, bepaal het bezit op uw knoop.

Bijvoorbeeld:

* Knooppunt: `/conf/global/settings/dam/cfm/jcr:content`
* Eigenschapnaam: `autoSaveInterval`

* Type: `Long`

* Waarde: `300` (5 minuten komt overeen met 300 seconden)

## Componenten voor paginaontwerp {#components-for-page-authoring}

Zie voor meer informatie

* [&#x200B; Componenten van de Kern - de Component van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) (geadviseerd)
