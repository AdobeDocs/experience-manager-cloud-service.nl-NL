---
title: Contentfragmenten aanpassen en uitbreiden
description: Een inhoudsfragment breidt een standaardelement uit.
exl-id: 58152d6e-21b6-4f45-a45c-0f46ee58825e
source-git-commit: c43b55243a73285b78447e32beb16b25608f6d3c
workflow-type: tm+mt
source-wordcount: '1808'
ht-degree: 1%

---

# Contentfragmenten aanpassen en uitbreiden{#customizing-and-extending-content-fragments}

Binnen Adobe Experience Manager als Cloud Service breidt een inhoudsfragment een standaardelement uit. zie:

* [Inhoudsfragmenten en ](/help/assets/content-fragments/content-fragments.md) pagina&#39;s  [ontwerpen en beheren met ](/help/sites-cloud/authoring/fundamentals/content-fragments.md) inhoudfragmenten voor meer informatie over inhoudsfragmenten.

* [Beheer van ](/help/assets/manage-digital-assets.md) activa voor meer informatie over standaardactiva.

## Architectuur {#architecture}

De [samenstellende delen](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) van een inhoudsfragment zijn:

* A *Inhoudsfragment*,
* bestaande uit een of meer *Inhoudselementen*,
* en die een of meer *Inhoudsvariaties* kunnen hebben.

De afzonderlijke inhoudsfragmenten zijn gebaseerd op modellen van inhoudsfragmenten:

* Inhoudsfragmentmodellen definiëren de structuur van een inhoudsfragment wanneer dit wordt gemaakt.
* Een fragment verwijst naar het model; wijzigingen in het model kunnen/zullen dus gevolgen hebben voor afhankelijke fragmenten.
* Modellen zijn samengesteld uit gegevenstypen.
* Functies om nieuwe variaties toe te voegen, enz., moeten het fragment dienovereenkomstig bijwerken.

   >[!NOTE]
   >
   >Als u een inhoudsfragment wilt weergeven/renderen, moet uw account `read` machtigingen voor het model hebben.

   >[!CAUTION]
   >
   >Wijzigingen in een bestaand inhoudsfragmentmodel kunnen van invloed zijn op afhankelijke fragmenten. dit kan leiden tot weeseigenschappen in die fragmenten .

### Integratie van sites met middelen {#integration-of-sites-with-assets}

CFM (Content Fragment Management) maakt deel uit van AEM Assets als:

* Inhoudsfragmenten zijn elementen.
* Ze gebruiken de bestaande functionaliteit Elementen.
* Ze zijn volledig geïntegreerd met middelen (beheerconsoles, enz.).

Inhoudsfragmenten worden als volgt beschouwd als een functie Sites:

* Deze worden gebruikt bij het ontwerpen van uw pagina&#39;s.

#### Inhoudsfragmenten toewijzen aan elementen {#mapping-content-fragments-to-assets}

![inhoudsfragment naar elementen](assets/content-fragment-to-assets.png)

Inhoudsfragmenten, gebaseerd op een inhoudsfragmentmodel, worden toegewezen aan één element:

* Alle inhoud wordt opgeslagen onder de `jcr:content/data`-node van het element:

   * De elementgegevens worden opgeslagen onder het master subknooppunt:
      `jcr:content/data/master`

   * Variaties worden opgeslagen onder een subknooppunt met de naam van de variatie:
bijv. `jcr:content/data/myvariation`

   * De gegevens van elk element worden in het desbetreffende subknooppunt opgeslagen als een eigenschap met de elementnaam:
De inhoud van element `text` wordt bijvoorbeeld als eigenschap `text` op `jcr:content/data/master` opgeslagen

* Metagegevens en bijbehorende inhoud worden onder `jcr:content/metadata` opgeslagen
Met uitzondering van de titel en de beschrijving, die niet als traditionele metagegevens worden beschouwd en op 
`jcr:content`

#### Locatie van element {#asset-location}

Net als bij standaardelementen wordt een inhoudsfragment opgeslagen onder:

`/content/dam`

#### Elementmachtigingen {#asset-permissions}

Zie [Inhoudsfragment - Overwegingen verwijderen](/help/assets/content-fragments/content-fragments-delete.md) voor meer informatie.

#### Functieintegratie {#feature-integration}

Integreren met de kern Elementen:

* De functie CFM (Content Fragment Management) is gebaseerd op de kern Elementen.

* CFM biedt zijn eigen implementaties voor items in de kaart-, kolom- of lijstweergaven; Deze plug-in de bestaande implementaties voor het renderen van de inhoud van Elementen.

* Verschillende middelencomponenten zijn uitgebreid om rekening te houden met inhoudsfragmenten.

### Inhoudsfragmenten op pagina&#39;s gebruiken {#using-content-fragments-in-pages}

>[!CAUTION]
>
>De component [Inhoudsfragment maakt deel uit van Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html). Zie [Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html) ontwikkelen voor meer informatie.

Vanuit AEM pagina&#39;s kan naar inhoudsfragmenten worden verwezen, net als met elk ander elementtype. AEM biedt de **[kerncomponent van inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)** - een [component waarmee u inhoudsfragmenten op uw pagina&#39;s kunt opnemen](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-a-content-fragment-to-your-page). U kunt dit **[Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html)** kerncomponent ook uitbreiden.

* De component gebruikt de eigenschap `fragmentPath` om naar het daadwerkelijke inhoudsfragment te verwijzen. De `fragmentPath`-eigenschap wordt op dezelfde wijze afgehandeld als soortgelijke eigenschappen van andere soorten activa; bijvoorbeeld wanneer het inhoudsfragment naar een andere locatie wordt verplaatst.

* Met de component kunt u de variatie selecteren die moet worden weergegeven.

* Bovendien kan een reeks alinea&#39;s worden geselecteerd om de uitvoer te beperken; Dit kan bijvoorbeeld worden gebruikt voor uitvoer met meerdere kolommen.

* De component staat tussenliggende inhoud toe:

   * Hier kunt u andere elementen (afbeeldingen, enz.) plaatsen tussen de alinea&#39;s van het fragment waarnaar wordt verwezen.

   * Voor tussenliggende inhoud moet u:

      * zich bewust zijn van de mogelijkheid van onstabiele referenties; tussenliggende inhoud (toegevoegd tijdens het ontwerpen van een pagina) heeft geen vaste relatie met de alinea die naast de inhoud wordt geplaatst, waarbij een nieuwe alinea (in de inhoudfragmenteditor) wordt ingevoegd voordat de positie van de tussenliggende inhoud de relatieve positie kan verliezen

      * Overweeg de extra parameters (zoals variatie en paragraaffilters) om te vormen wat op de pagina wordt teruggegeven

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

   Inhoudsfragmenten zijn volledig geïntegreerd met de vertaalworkflow [AEM. ](/help/sites-cloud/administering/translation/overview.md) Op architectonisch niveau betekent dit:

   * De afzonderlijke vertalingen van een inhoudsfragment zijn eigenlijk afzonderlijke fragmenten. bijvoorbeeld:

      * zij zijn in verschillende taalgebieden gevestigd; maar deel exact hetzelfde relatieve pad onder de relevante taalbasis:

         `/content/dam/<path>/en/<to>/<fragment>`

         vs

         `/content/dam/<path>/de/<to>/<fragment>`
   * Naast de op regel gebaseerde paden bestaat er geen verdere verbinding tussen de verschillende taalversies van een inhoudsfragment. ze worden behandeld als twee afzonderlijke fragmenten, hoewel de interface de mogelijkheid biedt om tussen de taalvarianten te navigeren.
   >[!NOTE]
   >
   >De AEM vertaalworkflow werkt met `/content`:
   >
   >* Aangezien de modellen van het inhoudsfragment in `/conf` verblijven, zijn deze niet inbegrepen in dergelijke vertalingen. U kunt de UI-tekenreeksen internationaliseren.


* **Metagegevensschema&#39;s**

   * Inhoudsfragmenten (weder)gebruiken de [metagegevensschema&#39;s](/help/assets/metadata-schemas.md), die kunnen worden gedefinieerd met standaardelementen.

   * CFM biedt een eigen, specifiek schema:

      `/libs/dam/content/schemaeditors/forms/contentfragment`

      dit kan zo nodig worden verlengd .

   * Het respectievelijke schema-formulier is geïntegreerd met de fragmenteditor.

## De API voor contentfragmentbeheer - Server-kant {#the-content-fragment-management-api-server-side}

U kunt de server-kant API gebruiken om tot uw inhoudsfragmenten toegang te hebben; zie:

[com.adobe.cq.dam.cfm](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/package-summary.html#package.description)

>[!CAUTION]
>
>Het wordt ten zeerste aanbevolen de server-side API te gebruiken in plaats van rechtstreeks toegang te krijgen tot de inhoudsstructuur.

### Belangrijke interfaces {#key-interfaces}

De volgende drie interfaces kunnen als ingangspunten dienen:

* **Inhoudsfragment**  ([ContentFragment](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

   Met deze interface kunt u op abstracte wijze werken met een inhoudsfragment.

   De interface voorziet u van de middelen:

   * Basisgegevens beheren (bijvoorbeeld naam ophalen; get/set titel/beschrijving)
   * Toegang tot metagegevens
   * Toegangselementen:

      * Lijstelementen
      * Elementen op naam ophalen
      * Nieuwe elementen maken (zie [Voorbehouden](#caveats))

      * Gegevens van toegangselement (zie `ContentElement`)
   * Variaties weergeven die zijn gedefinieerd voor het fragment
   * Nieuwe variaties wereldwijd maken
   * Gekoppelde inhoud beheren:

      * Lijstverzamelingen
      * Verzamelingen toevoegen
      * Verzamelingen verwijderen
   * Het model van het fragment openen

   De interfaces die de belangrijkste elementen van een fragment vertegenwoordigen zijn:

   * **Content Element**  ([ContentElement](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Toegang tot variaties van een element:

         * Variaties weergeven
         * Variaties ophalen op naam
         * Nieuwe variaties maken (zie [Caveats](#caveats))
         * Variaties verwijderen (zie [Bijschriften](#caveats))
         * Toegang krijgen tot variatiegegevens (zie `ContentVariation`)
      * Sneltoets voor het oplossen van variaties (door een aanvullende, implementatiespecifieke fallback-logica toe te passen als de opgegeven variatie niet beschikbaar is voor een element)
   * **Inhoudsvariatie** ([ContentVariation](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Eenvoudige synchronisatie, gebaseerd op laatst gewijzigde informatie

   Alle drie interfaces ( `ContentFragment`, `ContentElement`, `ContentVariation`) breiden de `Versionable` interface uit, die versiemogelijkheden toevoegt, die voor inhoudsfragmenten worden vereist:

   * Nieuwe versie van het element maken
   * Versies van het element weergeven
   * Hiermee wordt de inhoud opgehaald van een specifieke versie van het element met versiebeheer







### Aanpassen - Using adjustTo() {#adapting-using-adaptto}

Het volgende kan worden aangepast:

* `ContentFragment` kan worden aangepast aan:

   * `Resource` - de onderliggende sloopbron; wanneer u de onderliggende waarde  `Resource` rechtstreeks wilt bijwerken, moet u het  `ContentFragment` object opnieuw opbouwen.

   * `Asset` - de DAM- `Asset` abstractie die het inhoudsfragment vertegenwoordigt; als u het  `Asset` object  `ContentFragment` rechtstreeks wilt bijwerken, moet u het opnieuw samenstellen.

* `ContentElement` kan worden aangepast aan:

   * [`ElementTemplate`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/ElementTemplate.html) - voor toegang tot de structurele informatie van het element.

* [`FragmentTemplate`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html)

* `Resource` kan worden aangepast aan:

   * `ContentFragment`

### Caveats {#caveats}

Er zij op gewezen dat:

* De gehele API is ontworpen om automatisch wijzigingen te behouden **en niet** (tenzij anders vermeld in de API JavaDoc). Zo zult u altijd de middeloplosser van het respectieve verzoek (of resolver moeten begaan u eigenlijk gebruikt).

* Taken die extra inspanning zouden kunnen vereisen:

   * Het wordt sterk geadviseerd om nieuwe variaties van `ContentFragment` tot stand te brengen. Dit zorgt ervoor dat alle elementen deze variatie zullen delen en dat de aangewezen globale gegevensstructuren zonodig zullen worden bijgewerkt om de pas gecreëerde variatie in de inhoudsstructuur te weerspiegelen.

   * Als u bestaande variaties verwijdert via een element en `ContentElement.removeVariation()` gebruikt, worden de algemene gegevensstructuren die aan de variatie zijn toegewezen, niet bijgewerkt. Om ervoor te zorgen dat deze gegevensstructuren gesynchroniseerd blijven, gebruikt u `ContentFragment.removeVariation()`, waardoor een variatie globaal wordt verwijderd.

## De API voor contentfragmentbeheer - Client-kant {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>De client-side API is intern.

### Aanvullende informatie {#additional-information}

Zie het volgende:

* `filter.xml`

   `filter.xml` voor inhoudsfragmentbeheer is zo geconfigureerd dat het niet overlapt met het elementeninhoudspakket.

## Sessies bewerken {#edit-sessions}

>[!CAUTION]
>
>Houd rekening met deze achtergrondinformatie. U wordt verondersteld om niets hier te veranderen (aangezien het als *privé gebied* in de bewaarplaats) wordt gemerkt, maar het zou in sommige gevallen kunnen helpen om te begrijpen hoe de dingen onder de kap werken.

Het bewerken van een inhoudsfragment, dat meerdere weergaven kan beslaan (= HTML-pagina&#39;s), is atomisch. Aangezien dergelijke atomische multi-view bewerkingsmogelijkheden geen typisch AEM concept zijn, gebruiken de inhoudsfragmenten wat *het uitgeven zitting* wordt genoemd.

Er wordt een bewerkingssessie gestart wanneer de gebruiker een inhoudsfragment in de editor opent. De bewerkingssessie wordt beëindigd wanneer de gebruiker de editor verlaat door **Opslaan** of **Annuleren** te selecteren.

Technisch gezien worden alle bewerkingen uitgevoerd op *live*-inhoud, net als bij alle andere AEM bewerkingen. Wanneer de bewerkingssessie wordt gestart, wordt een versie van de huidige, onbewerkte status gemaakt. Als een gebruiker een bewerking annuleert, wordt die versie hersteld. Als de gebruiker op **Save** klikt, wordt niets specifiek gedaan, aangezien al het uitgeven op *live* inhoud werd uitgevoerd, daarom worden alle veranderingen reeds voortgeduurd. Als u op **Opslaan** klikt, wordt ook een achtergrondverwerking geactiveerd (zoals het maken van volledige zoekinformatie voor tekst en/of het verwerken van media-elementen).

Er zijn enkele veiligheidsmaatregelen voor randgevallen. bijvoorbeeld als de gebruiker de editor probeert te verlaten zonder de bewerkingssessie op te slaan of te annuleren. Er is ook een periodieke automatische opslag beschikbaar om gegevensverlies te voorkomen.
Twee gebruikers kunnen hetzelfde inhoudsfragment tegelijk bewerken en kunnen daarom elkaars wijzigingen overschrijven. Om dit te voorkomen, moet het inhoudsfragment worden vergrendeld door de handeling *Checkout* van de DAM-administratie op het fragment toe te passen.

## Voorbeelden {#examples}

### Voorbeeld: Een bestaand inhoudsfragment openen {#example-accessing-an-existing-content-fragment}

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

### Voorbeeld: Een nieuw inhoudsfragment maken {#example-creating-a-new-content-fragment}

Als u programmatisch een nieuw inhoudsfragment wilt maken, moet u een
`FragmentTemplate` aangepast aan de hand van een modelbron.

Bijvoorbeeld:

```java
Resource modelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = modelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Voorbeeld: Het interval voor automatisch opslaan opgeven {#example-specifying-the-auto-save-interval}

Het [interval voor automatisch opslaan](/help/assets/content-fragments/content-fragments-managing.md#save-close-and-versions) (gemeten in seconden) kan worden gedefinieerd met behulp van configuratiebeheer (ConfMgr):

* Knooppunt: `<conf-root>/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`
* Type: `Long`

* Standaard: `600` (10 minuten); this is defined on `/libs/settings/dam/cfm/jcr:content`

Als u een auto sparen interval van 5 minuten wilt plaatsen moet u het bezit op uw knoop bepalen; bijvoorbeeld:

* Knooppunt: `/conf/global/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`

* Type: `Long`

* Waarde: `300` (5 minuten komt overeen met 300 seconden)

## Componenten voor paginaontwerp {#components-for-page-authoring}

Zie voor meer informatie

* [Core Components - Content Fragment Component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)  (aanbevolen)
