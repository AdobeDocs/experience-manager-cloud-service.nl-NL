---
title: Inhoudsfragmenten aanpassen en uitbreiden
description: Een inhoudsfragment breidt een standaardelement uit. Leer hoe u ze kunt aanpassen.
exl-id: 58152d6e-21b6-4f45-a45c-0f46ee58825e
feature: Developing, Content Fragments
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 0%

---

# Inhoudsfragmenten aanpassen en uitbreiden{#customizing-and-extending-content-fragments}

In Adobe Experience Manager as a Cloud Service breidt een inhoudsfragment een standaard element uit. Zie:

* [Inhoudsfragmenten maken en beheren](/help/sites-cloud/administering/content-fragments/overview.md) en [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md) voor meer informatie over inhoudsfragmenten.

* [Elementen beheren](/help/assets/manage-digital-assets.md) voor meer informatie over standaardactiva.

## Architectuur {#architecture}

De basis [samenstellende delen](/help/sites-cloud/administering/content-fragments/overview.md#constituent-parts-of-a-content-fragment) van een inhoudsfragment zijn:

* A *Inhoudsfragment* zichzelf
* Bestaat uit een of meer *Inhoud-elementen*
* Het kan een of meer *Inhoudsvariaties*

De afzonderlijke inhoudsfragmenten zijn gebaseerd op modellen van inhoudsfragmenten:

* Inhoudsfragmentmodellen definiëren de structuur van een inhoudsfragment wanneer dit wordt gemaakt.
* Een fragment verwijst naar het model. Wijzigingen in het model kunnen dus invloed hebben op afhankelijke fragmenten of dit effect hebben.
* Modellen zijn opgebouwd uit gegevenstypen.
* Functies om nieuwe variaties toe te voegen, enzovoort, moeten het fragment overeenkomstig bijwerken.

  >[!NOTE]
  >
  >Als u een inhoudsfragment wilt weergeven/renderen, moet uw account `read` machtigingen voor het model.

  >[!CAUTION]
  >
  >Wijzigingen in een bestaand inhoudsfragmentmodel kunnen van invloed zijn op afhankelijke fragmenten. Dit kan leiden tot weeseigenschappen in die fragmenten.

### Integratie van sites met middelen {#integration-of-sites-with-assets}

CFM (Content Fragment Management) maakt deel uit van Adobe Experience Manager (AEM) Assets als:

* Inhoudsfragmenten zijn elementen.
* Ze gebruiken de bestaande functionaliteit Elementen.
* Ze zijn volledig geïntegreerd met Elementen (beheerconsoles, enzovoort).

Inhoudsfragmenten worden als een AEM Sites-functie beschouwd:

* Deze worden gebruikt bij het ontwerpen van uw pagina&#39;s.

#### Inhoudsfragmenten toewijzen aan elementen {#mapping-content-fragments-to-assets}

![inhoudsfragment naar elementen](assets/content-fragment-to-assets.png)

Inhoudsfragmenten, gebaseerd op een inhoudsfragmentmodel, worden toegewezen aan één element:

* Alle inhoud wordt opgeslagen onder de `jcr:content/data` knooppunt van het element:

   * De elementgegevens worden opgeslagen onder het hoofdsubknooppunt:
     `jcr:content/data/master`

   * Variaties worden opgeslagen onder een subknooppunt met de naam van de variatie: bijvoorbeeld `jcr:content/data/myvariation`

   * De gegevens van elk element worden in het desbetreffende subknooppunt opgeslagen als een eigenschap met de elementnaam: bijvoorbeeld de inhoud van het element `text` is opgeslagen als eigenschap `text` op `jcr:content/data/master`

* Metagegevens en bijbehorende inhoud worden hieronder opgeslagen `jcr:content/metadata`
Met uitzondering van de titel en de beschrijving, die niet als traditionele metagegevens worden beschouwd en op `jcr:content`

#### Locatie van element {#asset-location}

Net als bij standaardelementen wordt een inhoudsfragment opgeslagen onder:

`/content/dam`

#### Elementmachtigingen {#asset-permissions}

Zie [Inhoudsfragment - Overwegingen verwijderen](/help/sites-cloud/administering/content-fragments/delete-considerations.md).

#### Functie-integratie {#feature-integration}

Integreren met de kern Elementen:

* De functie CFM (Content Fragment Management) is gebaseerd op de kern Elementen.

* CFM biedt zijn eigen implementaties voor items in de kaart-, kolom- of lijstweergaven; deze plug-in de bestaande implementaties voor het renderen van de inhoud van Elementen.

* Verschillende middelencomponenten zijn uitgebreid om rekening te houden met inhoudsfragmenten.

### Inhoudsfragmenten op pagina&#39;s gebruiken {#using-content-fragments-in-pages}

>[!CAUTION]
>
>De [De component Inhoudsfragment maakt deel uit van de kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html). Zie [Basiscomponenten ontwikkelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) voor meer informatie .

Vanuit AEM pagina&#39;s kan naar inhoudsfragmenten worden verwezen, net als met elk ander elementtype. AEM biedt de **[Basiscomponent van inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)** - een [component waarmee u inhoudsfragmenten op uw pagina&#39;s kunt opnemen](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-a-content-fragment-to-your-page). U kunt dit ook uitbreiden **[Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html)** kerncomponent.

* De component gebruikt de `fragmentPath` eigenschap om naar het daadwerkelijke inhoudsfragment te verwijzen. De `fragmentPath` Deze eigenschap wordt op dezelfde manier verwerkt als soortgelijke eigenschappen van andere elementtypen, bijvoorbeeld wanneer het inhoudsfragment naar een andere locatie wordt verplaatst.

* Met de component kunt u de variatie selecteren die moet worden weergegeven.

* U kunt ook een reeks alinea&#39;s selecteren om de uitvoer te beperken. Deze alinea kan bijvoorbeeld worden gebruikt voor uitvoer met meerdere kolommen.

* De component staat tussenliggende inhoud toe:

   * Hier kunt u met de component andere elementen (afbeeldingen, enzovoort) tussen de alinea&#39;s van het fragment waarnaar wordt verwezen plaatsen.

   * Voor tussenliggende inhoud:

      * Houd rekening met de mogelijkheid van onstabiele referenties. Tussen de inhoud (die bij het ontwerpen van een pagina wordt toegevoegd) bevindt zich geen vaste relatie met de alinea die ernaast staat. Als u een nieuwe alinea invoegt (in de inhoudfragmenteditor) vóór de positie van de tussenliggende inhoud, kan de relatieve positie verloren gaan.

      * Overweeg de extra parameters (zoals variatie- en alineafilters) om te configureren wat op de pagina wordt weergegeven.

>[!NOTE]
>
>**Inhoudsfragmentmodel:**
>
>Wanneer een inhoudsfragment op een pagina wordt gebruikt, wordt verwezen naar het model van het inhoudsfragment waarop het is gebaseerd.
>
>Dit betekent dat als het model niet is gepubliceerd op het moment dat u de pagina publiceert, dit wordt gemarkeerd en het model wordt toegevoegd aan de bronnen die met de pagina moeten worden gepubliceerd.

### Integratie met andere frameworks {#integration-with-other-frameworks}

Inhoudsfragmenten kunnen worden geïntegreerd met:

* **Vertalingen**

  Inhoudsfragmenten zijn volledig geïntegreerd met de [AEM vertaalworkflow](/help/sites-cloud/administering/translation/overview.md). Op architectonisch niveau betekent dit:

   * De afzonderlijke vertalingen van een inhoudsfragment zijn afzonderlijke fragmenten, bijvoorbeeld:

      * zij bevinden zich onder verschillende taalwortels, maar delen het relatieve pad onder de desbetreffende taalwortel:

        `/content/dam/<path>/en/<to>/<fragment>`

        vs

        `/content/dam/<path>/de/<to>/<fragment>`

   * Naast op regel gebaseerde paden is er geen andere verbinding tussen de verschillende taalversies van een inhoudsfragment. Deze fragmenten worden als twee afzonderlijke fragmenten behandeld, hoewel de interface de mogelijkheid biedt om tussen de taalvarianten te navigeren.

  >[!NOTE]
  >
  >De AEM vertaalworkflow werkt met `/content`:
  >
  >* Terwijl de modellen van het inhoudsfragment zich bevinden in `/conf`, worden deze niet in dergelijke vertalingen opgenomen. U kunt de UI-tekenreeksen internationaliseren.

* **Metagegevensschema&#39;s**

   * Inhoudsfragmenten gebruiken en hergebruiken de [metagegevensschema&#39;s](/help/assets/metadata-schemas.md) die met standaardelementen kunnen worden gedefinieerd.

   * CFM biedt een eigen, specifiek schema:

     `/libs/dam/content/schemaeditors/forms/contentfragment`

     dit kan zo nodig worden verlengd .

   * Het respectievelijke schema-formulier is geïntegreerd met de fragmenteditor.

## De API voor contentfragmentbeheer - Server-kant {#the-content-fragment-management-api-server-side}

U kunt de server-kant API gebruiken om tot uw inhoudsfragmenten toegang te hebben; zie:

[com.adobe.cq.dam.cfm](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/package-summary.html#package.description)

>[!CAUTION]
>
>Adobe raadt u aan de server-side API te gebruiken in plaats van rechtstreeks toegang te krijgen tot de inhoudsstructuur.

### Belangrijke interfaces {#key-interfaces}

De volgende drie interfaces kunnen als ingangspunten dienen:

* **Inhoudsfragment** ([ContentFragment](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

  Met deze interface kunt u op abstracte wijze met een inhoudsfragment werken.

  De interface voorziet u van de middelen:

   * Standaardgegevens beheren (bijvoorbeeld naam ophalen; titel/beschrijving ophalen/instellen)
   * Toegang tot metagegevens
   * Toegangselementen:

      * Lijstelementen
      * Elementen op naam ophalen
      * Elementen maken (zie [Caveats](#caveats))

      * Gegevens over toegangselementen (zie `ContentElement`)

   * Variaties weergeven die zijn gedefinieerd voor het fragment
   * Wereldwijd variaties maken
   * Gekoppelde inhoud beheren:

      * Lijstverzamelingen
      * Verzamelingen toevoegen
      * Verzamelingen verwijderen

   * Toegang krijgen tot het model van het fragment

  De interfaces die de belangrijkste elementen van een fragment vertegenwoordigen zijn:

   * **Inhoud-element** ([ContentElement](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Toegang tot variaties van een element:

         * Variaties weergeven
         * Variaties ophalen op naam
         * Variaties maken (zie [Caveats](#caveats))
         * Variaties verwijderen (zie [Caveats](#caveats))
         * Gegevens betreffende variatie van de toegang (zie `ContentVariation`)

      * Sneltoets voor het oplossen van variaties (door een aanvullende, implementatiespecifieke fallback-logica toe te passen als de opgegeven variatie niet beschikbaar is voor een element)

   * **Inhoudsvariatie** ([ContentVariation](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Eenvoudige synchronisatie, gebaseerd op laatst gewijzigde informatie

  Alle drie de interfaces ( `ContentFragment`, `ContentElement`, `ContentVariation`) de `Versionable` interface, die versiemogelijkheden toevoegt, vereist voor inhoudsfragmenten:

   * Een versie van het element maken
   * Versies van het element weergeven
   * Hiermee wordt de inhoud opgehaald van een specifieke versie van het element met versiebeheer

### Aanpassen - Using adjustTo() {#adapting-using-adaptto}

Het volgende kan worden aangepast:

* `ContentFragment` kan worden aangepast aan:

   * `Resource` - de onderliggende sloopbron; actualisering van de onderliggende `Resource` rechtstreeks vereist dat de `ContentFragment` object.

   * `Asset` - de DAM `Asset` abstractie die het inhoudsfragment vertegenwoordigt; het bijwerken van `Asset` rechtstreeks vereist dat de `ContentFragment` object.

* `ContentElement` kan worden aangepast aan:

   * [`ElementTemplate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/ElementTemplate.html) - voor toegang tot de structurele informatie van het element.

* [`FragmentTemplate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html)

* `Resource` kan worden aangepast aan:

   * `ContentFragment`

### Caveats {#caveats}

Er zij op gewezen dat:

* De gehele API is ontworpen voor **niet** Wijzigingen automatisch aanhouden (tenzij anders vermeld in de API JavaDoc). Zo, begaat altijd de middeloplosser van het respectieve verzoek (of resolver u eigenlijk gebruikt).

* Taken die extra inspanning zouden kunnen vereisen:

   * Adobe raadt u aan variaties te maken op basis van `ContentFragment`. Dit zorgt ervoor dat alle elementen deze variatie delen en dat de juiste algemene gegevensstructuren zo nodig worden bijgewerkt om de nieuwe variatie in de inhoudsstructuur te weerspiegelen.

   * Bestaande variaties verwijderen door een element, gebruiken `ContentElement.removeVariation()`, worden de algemene gegevensstructuren die aan de variatie zijn toegewezen, niet bijgewerkt. Om ervoor te zorgen dat deze gegevensstructuren synchroon blijven, gebruikt u `ContentFragment.removeVariation()` in plaats daarvan, die een variatie globaal verwijdert.

## De API voor contentfragmentbeheer - Client-kant {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>De client-side API is intern.

### Aanvullende informatie {#additional-information}

Zie het volgende:

* `filter.xml`

  De `filter.xml` voor inhoudsfragmentbeheer is zo geconfigureerd dat dit niet overlapt met het elementeninhoudspakket.

## Sessies bewerken {#edit-sessions}

>[!CAUTION]
>
>Overweeg deze achtergrondinformatie. U mag hier niets wijzigen (omdat het als een *privé-ruimte* in de opslagplaats), maar het kan soms helpen om te begrijpen hoe dingen onder de kap werken.

Het bewerken van een inhoudsfragment, dat meerdere weergaven kan beslaan (= HTML pagina&#39;s), is atomisch. Aangezien dergelijke atomische multi-view bewerkingsmogelijkheden geen typisch AEM concept zijn, gebruiken de inhoudsfragmenten wat wordt genoemd een *bewerksessie*.

Er wordt een bewerkingssessie gestart wanneer de gebruiker een inhoudsfragment in de editor opent. De bewerkingssessie is voltooid wanneer de gebruiker de editor verlaat door een van de volgende opties te selecteren **Opslaan** of **Annuleren**.

Technisch gezien worden alle bewerkingen uitgevoerd op *leven* inhoud, net als bij alle andere AEM bewerkingen. Wanneer de bewerkingssessie wordt gestart, wordt een versie van de huidige, onbewerkte status gemaakt. Als een gebruiker een bewerking annuleert, wordt die versie hersteld. Als de gebruiker klikt **Opslaan** Er wordt niets specifieks gedaan, omdat de bewerking is uitgevoerd op *leven* de inhoud, dus alle wijzigingen blijven al bestaan. Klik ook op **Opslaan** veroorzaakt sommige achtergrondverwerking zoals het creëren van volledige tekst onderzoeksinformatie, of het behandelen van gemengde media activa, of allebei.

Er zijn enkele veiligheidsmaatregelen voor randgevallen, bijvoorbeeld als de gebruiker de editor probeert te verlaten zonder de bewerkingssessie op te slaan of te annuleren. Er is ook een periodieke automatische opslag beschikbaar om gegevensverlies te voorkomen.
Twee gebruikers kunnen hetzelfde inhoudsfragment gelijktijdig bewerken en daarom elkaars wijzigingen overschrijven. Om dit te voorkomen, moet het inhoudsfragment worden vergrendeld door toepassing van de DAM-beheerfunctie *Afhandeling* handeling op het fragment.

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

Als u een inhoudsfragment programmatisch wilt maken, gebruikt u een `FragmentTemplate` aangepast aan een modelbron.

Bijvoorbeeld:

```java
Resource modelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = modelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Voorbeeld: het interval voor automatisch opslaan opgeven {#example-specifying-the-auto-save-interval}

De [automatisch opslaan, interval](/help/sites-cloud/administering/content-fragments/managing.md#save-close-and-versions) (gemeten in seconden) kan worden gedefinieerd met behulp van configuratiemanager (ConfMgr):

* Knooppunt: `<conf-root>/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`
* Type: `Long`

* Standaard: `600` (10 minuten); dit wordt gedefinieerd op `/libs/settings/dam/cfm/jcr:content`

Als u een auto-sparen interval van 5 minuten wilt plaatsen, bepaal het bezit op uw knoop.

Bijvoorbeeld:

* Knooppunt: `/conf/global/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`

* Type: `Long`

* Waarde: `300` (5 minuten komt overeen met 300 seconden)

## Componenten voor paginaontwerp {#components-for-page-authoring}

Zie voor meer informatie

* [Kerncomponenten - component Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) (aanbevolen)
