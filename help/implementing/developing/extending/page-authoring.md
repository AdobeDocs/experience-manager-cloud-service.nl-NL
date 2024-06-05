---
title: Paginaontwerp aanpassen
description: Leer over de mechanismen die AEM as a Cloud Service verstrekt om de functionaliteit van de paginascreatie aan te passen.
exl-id: 98d3c7ab-46d2-4e8d-b0da-5c8a7b398135
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# Paginaontwerp aanpassen {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service biedt mechanismen waarmee u de functionaliteit voor het schrijven van pagina&#39;s (en de [consoles](/help/implementing/developing/extending/consoles.md)) van de ontwerpinstantie.

## Clientlibs {#clientlibs}

Clientlibs laten u de standaardimplementatie uitbreiden om nieuwe functionaliteit toe te laten, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes.

Bij het aanpassen kunt u uw eigen clientlib maken onder `/apps.` De nieuwe client moet:

* Afhankelijk van de publicatieclib `cq.authoring.editor.sites.page`.
* Maak deel uit van de `cq.authoring.editor.sites.page.hook` categorie.

Zie [Client-Side bibliotheken gebruiken op AEM as a Cloud Service](/help/implementing/developing/introduction/clientlibs.md).

## Bedekkingen {#overlays}

Bedekkingen zijn gebaseerd op knooppuntdefinities en maken het mogelijk de standaardfunctionaliteit te bedekken in `/libs` met uw eigen aangepaste functionaliteit in `/apps`.

Bij het maken van een bedekking is een 1:1-kopie van het origineel niet vereist, omdat de [fusie van bronnen](/help/implementing/developing/introduction/sling-resource-merger.md) staat overerving toe.

Zie de klasse [JS-documentatieset](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Zie voor meer informatie over overlays [Bedekkingen voor Adobe Experience Manager as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

## Nieuwe laag toevoegen (modus) {#add-new-layer-mode}

Wanneer u een pagina bewerkt, zijn er verschillende [modi](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes) beschikbaar. Deze modi worden geïmplementeerd met [lagen](/help/implementing/developing/introduction/ui-structure.md#layer). Hiermee hebt u toegang tot verschillende typen functionaliteit voor dezelfde pagina-inhoud. AEM modi zijn Bewerken, Layout, Ontwikkelaar, Tijdverdraaiing, Live Copy-status en Doel.

### Voorbeeld van laag: status van actieve kopie {#layer-example-live-copy-status}

Een standaard AEM instantie verstrekt de laag MSM. Hiermee krijgt u toegang tot gegevens die betrekking hebben op [multisite beheer](/help/sites-cloud/administering/msm/overview.md) en markeert deze in de laag.

Als u het wilt zien in actie, kunt u elke taalkopie in het dialoogvenster [WKND-voorbeeldinhoud](/help/implementing/developing/introduction/develop-wknd-tutorial.md) en selecteert u de **Status van live kopiëren** -modus.

U kunt de MSM laagdefinitie (voor verwijzing) vinden in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codevoorbeeld {#code-sample}

Dit is een voorbeeldpakket dat toont hoe te om een laag (wijze) voor mening tot stand te brengen MSM.

U kunt de code van deze pagina vinden op [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)

## Nieuwe selectiecategorie toevoegen aan de middelenbrowser {#add-new-selection-category-to-asset-browser}

In de middelenbrowser worden elementen van verschillende typen/categorieën weergegeven (bijvoorbeeld afbeeldingen en documenten). De activa kunnen ook door deze activacategorieën worden gefiltreerd.

### Codevoorbeeld {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` Dit is een voorbeeldpakket dat aangeeft hoe u een groep aan de zoeker van middelen kunt toevoegen. Dit voorbeeld maakt verbinding met [Flickr](https://www.flickr.com)s public stream en toont deze in het zijpaneel.

U kunt de code van deze pagina vinden op [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)

## Bronnen filteren {#filtering-resources}

Bij het ontwerpen van pagina&#39;s moet de gebruiker vaak een keuze maken uit bronnen in een lijst.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Als de `pathbrowser` De component van graniet wordt gebruikt om de gebruiker toe te staan om de weg aan een bepaalde middel te selecteren, kunnen de voorgestelde wegen op de volgende manier worden gefiltreerd:

* Implementeer de aangepaste voorspelling door deze te implementeren [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html) interface.
* Geef een naam voor de voorspelling op en verwijs deze naam naar het tabblad `pathbrowser`.

Zie voor meer informatie over het maken van een aangepaste predikaat [dit artikel.](/help/implementing/developing/introduction/query-builder-custom-predicate.md)

## Nieuwe handeling toevoegen aan werkbalk Component {#add-new-action-to-a-component-toolbar}

Elke component heeft gewoonlijk een werkbalk die toegang biedt tot een reeks handelingen die op die component kunnen worden uitgevoerd.

### Codevoorbeeld {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` Dit is een voorbeeldpakket dat laat zien hoe u een aangepaste werkbalkactie maakt om componenten te renderen.

U kunt de code van deze pagina vinden op [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)

## Nieuwe plaatseditor toevoegen {#add-new-in-place-editor}

### Standaardeditor {#standard-in-place-editor}

In een standaard AEM-installatie:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js` bevat definities van de verschillende beschikbare redacteuren.

1. Er is een verbinding tussen de redacteur en elk middeltype (zoals in component) dat het kan gebruiken:

   * `cq:inplaceEditing`

     bijvoorbeeld:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * eigenschap: `editorType`

           Bepaalt het type van gealigneerde redacteur die wordt gebruikt wanneer het op zijn plaats uitgeven voor die component wordt teweeggebracht; bijvoorbeeld `text`, `textimage`, `image`, `title`.

1. De extra configuratiedetails van de redacteur kunnen worden gevormd gebruikend een `config` knooppunt met configuraties en een `plugin` -knooppunt voor de benodigde configuratiegegevens voor de plug-in.


Hieronder ziet u een voorbeeld van het definiëren van hoogte-breedteverhoudingen voor de uitsnijdplug-in van de afbeeldingscomponent.

```xml
   <cq:inplaceEditing
           jcr:primaryType="cq:InplaceEditingConfig"
           active="{Boolean}true"
           editorType="image">
           <config jcr:primaryType="nt:unstructured">
               <plugins jcr:primaryType="nt:unstructured">
                   <crop jcr:primaryType="nt:unstructured">
                       <aspectRatios jcr:primaryType="nt:unstructured">
                           <_x0031_6-10
                               jcr:primaryType="nt:unstructured"
                               name="16 : 10"
                               ratio="0.625"/>
                       </aspectRatios>
                   </crop>
               </plugins>
           </config>
   </cq:inplaceEditing>
```

>[!NOTE]
>
>Uitsnijdverhoudingen AEM, zoals ingesteld door de `ratio` eigenschap, worden gedefinieerd als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. De gebruikers van de auteur zullen zich niet van enig verschil bewust zijn op voorwaarde dat u bepaalt `name` duidelijk bezit aangezien dit is wat in UI wordt getoond.

#### Een nieuwe plaatseditor maken {#creating-a-new-in-place-editor}

Om een nieuwe op zijn plaats redacteur (binnen uw clientlib) uit te voeren:

1. Implementeren:

   * `setUp`
   * `tearDown`

1. Registreer de editor (inclusief de constructor):

   * `editor.register`

1. Verstrek de verbinding tussen de redacteur en elk middeltype (zoals in component) dat het kan gebruiken.

#### Codevoorbeeld voor het maken van een nieuwe plaatseditor {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` Dit is een voorbeeldpakket waarin wordt getoond hoe u een lokale editor in AEM kunt maken.

U kunt de code van deze pagina vinden op [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)

## Handeling Nieuwe pagina toevoegen {#add-a-new-page-action}

Als u een nieuwe paginahandeling wilt toevoegen aan de pagina-werkbalk, bijvoorbeeld een handeling **Terug naar sites** (console) handeling.

### Codevoorbeeld {#code-sample-3}

`aem-authoring-extension-header-backtosites` is een voorbeeldpakket dat toont hoe te om een actie van de douanekopbalbar tot stand te brengen om terug naar de console van Plaatsen te springen.

U kunt de code van deze pagina vinden op [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)

## De workflow voor het aanvragen van activering aanpassen {#customizing-the-request-for-activation-workflow}

De workflow buiten de box, **Verzoek om activering**:

* Wordt automatisch weergegeven in het juiste menu wanneer een inhoudsauteur **heeft geen** de juiste replicatierechten, maar **heeft** lidmaatschap van DAM-gebruikers en auteurs.

* Anders wordt er niets weergegeven, omdat de replicatierechten zijn verwijderd.

Voor een aangepast gedrag bij een dergelijke activering kunt u de **Verzoek om activering** workflow:

1. In `/apps` bedekken de **Sites** wizard `/libs/wcm/core/content/common/managepublicationwizard`

   * Dit zelf, treedt het gemeenschappelijke geval van `/libs/cq/gui/content/common/managepublicationwizard`.

1. Werk het workflowmodel en de bijbehorende configuraties/scripts naar wens bij.
1. Rechts van de `replicate` actie van alle relevante gebruikers voor alle relevante pagina&#39;s. Als u wilt dat deze workflow als een standaardhandeling wordt geactiveerd wanneer een gebruiker een pagina publiceert (of dupliceert), probeert u deze te publiceren.
