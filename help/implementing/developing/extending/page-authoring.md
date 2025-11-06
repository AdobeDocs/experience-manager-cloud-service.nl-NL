---
title: Paginaontwerp aanpassen
description: Meer informatie over de mechanismen die AEM as a Cloud Service biedt om de functionaliteit voor het schrijven van pagina's aan te passen.
exl-id: 98d3c7ab-46d2-4e8d-b0da-5c8a7b398135
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---

# Paginaontwerp aanpassen {#customizing-page-authoring}

Adobe Experience Manager as a Cloud Service verstrekt mechanismen om u de pagina auteursfunctionaliteit (en de [&#x200B; consoles &#x200B;](/help/implementing/developing/extending/consoles.md)) van uw auteursinstantie te laten aanpassen.

## Clientlibs {#clientlibs}

Clientlibs laten u de standaardimplementatie uitbreiden om nieuwe functionaliteit toe te laten, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes.

Bij het aanpassen kunt u uw eigen clientlib maken onder `/apps.` De nieuwe clientlib moet:

* Afhankelijk van de client lib die het document maakt `cq.authoring.editor.sites.page` .
* Maak deel uit van de juiste categorie `cq.authoring.editor.sites.page.hook` .

Zie [&#x200B; Gebruikend cliënt-Kant Bibliotheken op AEM as a Cloud Service &#x200B;](/help/implementing/developing/introduction/clientlibs.md).

## Bedekkingen {#overlays}

Bedekkingen zijn gebaseerd op knooppuntdefinities en maken het mogelijk om de standaardfunctionaliteit in `/libs` te bedekken met uw eigen aangepaste functionaliteit in `/apps` .

Wanneer het creëren van een bedekking, wordt een 1 :1 exemplaar van origineel niet vereist, aangezien de [&#x200B; het laten slingeren middelfusie &#x200B;](/help/implementing/developing/introduction/sling-resource-merger.md) voor overerving toestaat.

Voor meer informatie, zie de [&#x200B; JS documentatiereeks &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Voor meer informatie over overlays, zie [&#x200B; Bedekkingen voor Adobe Experience Manager as a Cloud Service &#x200B;](/help/implementing/developing/introduction/overlays.md).

## Nieuwe laag toevoegen (modus) {#add-new-layer-mode}

Wanneer u een pagina uitgeeft, zijn er diverse [&#x200B; beschikbare wijzen &#x200B;](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes). Deze wijzen worden uitgevoerd gebruikend [&#x200B; lagen &#x200B;](/help/implementing/developing/introduction/ui-structure.md#layer). Hiermee hebt u toegang tot verschillende typen functionaliteit voor dezelfde pagina-inhoud. De standaard AEM-modi zijn Bewerken, Layout, Ontwikkelaar, Tijdverdraaiing, Live Copy-status en Targeting.

### Voorbeeld van laag: status van actieve kopie {#layer-example-live-copy-status}

Een standaard AEM-instantie biedt de MSM-laag. Dit heeft toegang tot gegevens met betrekking tot [&#x200B; multisite beheer &#x200B;](/help/sites-cloud/administering/msm/overview.md) en benadrukt het in de laag.

Om het in actie te zien, kunt u om het even welk taalexemplaar in de [&#x200B; WKND steekproefinhoud &#x200B;](/help/implementing/developing/introduction/develop-wknd-tutorial.md) uitgeven en de **Levende 3&rbrace; wijze van de Status van het Exemplaar selecteren.**

U kunt de MSM laagdefinitie (voor verwijzing) vinden in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codevoorbeeld {#code-sample}

Dit is een voorbeeldpakket dat toont hoe te om een laag (wijze) voor mening tot stand te brengen MSM.

U kunt de code van deze pagina op [&#x200B; GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode) vinden.

## Nieuwe selectiecategorie toevoegen aan de middelenbrowser {#add-new-selection-category-to-asset-browser}

In de middelenbrowser worden elementen van verschillende typen/categorieën weergegeven (bijvoorbeeld afbeeldingen en documenten). De activa kunnen ook door deze activacategorieën worden gefiltreerd.

### Codevoorbeeld {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` is een voorbeeldpakket dat aangeeft hoe u een groep aan de elementenzoeker kunt toevoegen. Dit voorbeeld verbindt met [&#x200B; de openbare stroom van Flickr &#x200B;](https://www.flickr.com) en toont hen in het zijpaneel.

U kunt de code van deze pagina op [&#x200B; GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr) vinden.

## Bronnen filteren {#filtering-resources}

Bij het ontwerpen van pagina&#39;s moet de gebruiker vaak een keuze maken uit bronnen in een lijst.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Als de component `pathbrowser` Granite bijvoorbeeld wordt gebruikt om de gebruiker toe te staan het pad naar een bepaalde bron te selecteren, kunnen de voorgestelde paden als volgt worden gefilterd:

* Implementeer de aangepaste voorspelling door de [`com.day.cq.commons.predicate.AbstractNodePredicate` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/predicate/package-summary.html) -interface te implementeren.
* Geef een naam voor de voorspelling op en verwijs die naam wanneer u de voorspelling van `pathbrowser` gebruikt.

Voor verder detail bij het creëren van een douane predikt, zie [&#x200B; dit artikel &#x200B;](/help/implementing/developing/introduction/query-builder-custom-predicate.md).

## Nieuwe handeling toevoegen aan werkbalk Component {#add-new-action-to-a-component-toolbar}

Elke component heeft gewoonlijk een werkbalk die toegang biedt tot een reeks handelingen die op die component kunnen worden uitgevoerd.

### Codevoorbeeld {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` is een voorbeeldpakket dat aangeeft hoe u een aangepaste werkbalkactie kunt maken om componenten te renderen.

U kunt de code van deze pagina op [&#x200B; GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot) vinden.

## Nieuwe plaatseditor toevoegen {#add-new-in-place-editor}

### Standaardeditor {#standard-in-place-editor}

In een standaard AEM-installatie:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js` bevat definities van de verschillende beschikbare editors.

1. Er is een verbinding tussen de redacteur en elk middeltype (zoals in component) dat het kan gebruiken:

   * `cq:inplaceEditing`

     bijvoorbeeld:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * eigenschap: `editorType`

           Definieert het type inline-editor dat wordt gebruikt wanneer de bewerking op plaats wordt geactiveerd voor die component, bijvoorbeeld `text` , `textimage` , `image` , `title` .

1. Aanvullende configuratiedetails van de editor kunnen worden geconfigureerd met een `config` -knooppunt dat configuraties en een `plugin` -knooppunt voor de benodigde configuratiegegevens van de plug-in.


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
>AEM gewassenverhoudingen, zoals die door het `ratio` bezit worden geplaatst, worden bepaald als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. De ontwerpgebruikers zijn zich niet bewust van enig verschil op voorwaarde dat u de eigenschap `name` duidelijk definieert, aangezien dit is wat wordt weergegeven in de gebruikersinterface.

#### Een nieuwe plaatseditor maken {#creating-a-new-in-place-editor}

Om een nieuwe op zijn plaats redacteur (binnen uw clientlib) uit te voeren:

1. Implementeren:

   * `setUp`
   * `tearDown`

1. Registreer de editor (inclusief de constructor):

   * `editor.register`

1. Verstrek de verbinding tussen de redacteur en elk middeltype (zoals in component) dat het kan gebruiken.

#### Codevoorbeeld voor het maken van een nieuwe plaatseditor {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` is een voorbeeldpakket waarin wordt getoond hoe u een lokale editor in AEM kunt maken.

U kunt de code van deze pagina op [&#x200B; GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor) vinden.

## Handeling Nieuwe pagina toevoegen {#add-a-new-page-action}

Om een nieuwe paginaactie aan de paginatoolbar toe te voegen, bijvoorbeeld, a **terug naar Plaatsen** (console) actie.

### Codevoorbeeld {#code-sample-3}

`aem-authoring-extension-header-backtosites` is een voorbeeldpakket waarin wordt getoond hoe u een aangepaste actie voor de koptekstbalk kunt maken om terug te gaan naar de Sites-console.

U kunt de code van deze pagina op [&#x200B; GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites) vinden.

## De workflow voor het aanvragen van activering aanpassen {#customizing-the-request-for-activation-workflow}

Het uit-van-de-dooswerkschema, **Verzoek om Activering**:

* Zal automatisch op het aangewezen menu verschijnen wanneer een inhoudsauteur **&#x200B;**&#x200B;niet de aangewezen replicatierechten heeft, maar **heeft** lidmaatschap van DAM-Gebruikers en Auteurs.

* Anders wordt er niets weergegeven, omdat de replicatierechten zijn verwijderd.

Om aangepast gedrag op dergelijke activering te hebben, kunt u het **Verzoek om het werkschema van de Activering** bedekken:

1. In `/apps` bedekking de **2&rbrace; tovenaar van Plaatsen**`/libs/wcm/core/content/common/managepublicationwizard`

   * Op deze manier wordt de algemene instantie van `/libs/cq/gui/content/common/managepublicationwizard` genegeerd.

1. Werk het workflowmodel en de bijbehorende configuraties/scripts naar wens bij.
1. Verwijder het recht op de handeling `replicate` van alle relevante gebruikers voor alle relevante pagina&#39;s. Als u wilt dat deze workflow als een standaardhandeling wordt geactiveerd wanneer een gebruiker een pagina publiceert (of dupliceert), probeert u deze te publiceren.
