---
title: Structuur van de gebruikersinterface van AEM
description: De gebruikersinterface van AEM heeft verschillende onderliggende beginselen en bestaat uit verschillende sleutelelementen
exl-id: ac211716-d699-4fdb-a286-a0a1122c86c5
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Structuur van de gebruikersinterface van AEM {#structure-of-the-aem-ui}

De gebruikersinterface van AEM heeft verschillende onderliggende principes en bestaat uit verschillende sleutelelementen:

## Consoles {#consoles}

### Basislay-out en -formaat {#basic-layout-and-resizing}

De interface biedt ruimte voor zowel mobiele apparaten als bureaubladapparaten. In plaats van twee stijlen te maken, gebruikt AEM één stijl die geschikt is voor alle schermen en apparaten.

Alle modules gebruiken de zelfde basislay-out:

![&#x200B; AEM Sites console &#x200B;](assets/ui-sites-console.png)

De lay-out volgt een ontvankelijke ontwerpstijl en past zich aan de grootte van het apparaat, of venster, of allebei aan, dat u gebruikt.

Als de resolutie bijvoorbeeld lager is dan 1024 pixels (zoals op een mobiel apparaat), wordt het beeldscherm dienovereenkomstig aangepast:

![&#x200B; de console mobiele mening van Plaatsen &#x200B;](assets/ui-sites-mobile.png)

### Koptekstbalk {#header-bar}

![&#x200B; de kopbalbar van AEM &#x200B;](assets/ui-header-bar.png)

De kopbalbar toont globale elementen met inbegrip van:

* Het logo en het specifieke product/de specifieke oplossing die u momenteel gebruikt. Voor AEM vormt dit element ook een koppeling naar de globale navigatie
* Zoeken
* Pictogram voor toegang tot de Help-bronnen
* Pictogram voor toegang tot andere oplossingen
* Een indicator van - en toegang tot - om het even welke alarm of Inbox punten die op u wachten
* Het gebruikerspictogram en een koppeling naar uw profielbeheer

### Werkbalk {#toolbar}

De werkbalk is contextueel ten opzichte van uw locatie en de gereedschappen voor oppervlakken die relevant zijn voor het beheren van de weergave of elementen op de onderstaande pagina. De werkbalk is productspecifiek, maar de elementen hebben een zekere gemeen.

Op de werkbalk ziet u de acties die momenteel beschikbaar zijn.

![&#x200B; de toolbar van AEM Sites &#x200B;](assets/ui-sites-toolbar.png)

Ook afhankelijk van of een bron is geselecteerd:

![&#x200B; geselecteerde de toolbar van AEM Sites &#x200B;](assets/ui-sites-toolbar-selected.png)

### Linkerspoor {#left-rail}

De linkerspoorstaaf kan worden geopend/verborgen zoals vereist om te tonen:

* **slechts Inhoud**
* **de Boom van de Inhoud**
* **Chronologie**
* **Verwijzingen**
* **Filter**

Het gebrek is **slechts Inhoud** (spoorstaaf verborgen).

![&#x200B; Linkerspoor &#x200B;](assets/ui-left-rail.png)

## Pagina&#39;s ontwerpen {#page-authoring}

Bij het ontwerpen van pagina&#39;s ziet u de volgende structurele gebieden.

### Inhoudskader {#content-frame}

De pagina-inhoud wordt weergegeven in het inhoudskader. Het inhoudskader is onafhankelijk van de editor - om ervoor te zorgen dat er geen conflicten optreden vanwege CSS of JavaScript.

Het inhoudskader bevindt zich in de rechtersectie van het venster, onder de werkbalk.

![&#x200B; kader van de Inhoud &#x200B;](assets/ui-content-frame.png)

### Editor frame {#editor-frame}

Het editorkader laat de het uitgeven eigenschappen toe.

Het editorframe is een container (abstract) voor alle pagina-ontwerpelementen. Het leeft bovenop het inhoudskader, en omvat:

* De bovenste werkbalk
* Het zijpaneel
* Alle overlays
* Een ander pagina-ontwerpelement, bijvoorbeeld de componentwerkbalk

![&#x200B; Kader van de Redacteur &#x200B;](assets/ui-editor-frame.png)

### Zijpaneel {#side-panel}

Bevat drie standaardtabbladen. De **Assets** en **Componenten** lusjes laten u dergelijke elementen selecteren en hen slepen van het paneel en hen laten vallen op de pagina. Het **lusje van de Boom van de Inhoud** laat u de hiërarchie van inhoud op de pagina inspecteren.

Het zijpaneel is standaard verborgen. Als deze optie is geselecteerd, wordt deze links weergegeven of als de vensterbreedte kleiner is dan 1024 pixels, schuift deze over om het hele venster te bedekken, bijvoorbeeld op een mobiel apparaat.

![&#x200B; Zijpaneel &#x200B;](assets/ui-side-panel.png)

### Zijpaneel - Assets {#side-panel-assets}

Op het tabblad Assets kunt u een selectie maken uit het assortiment elementen. U kunt ook filteren op een bepaalde term of een groep selecteren.

![&#x200B; Assets tabel &#x200B;](assets/ui-side-panel-assets.png)

### Zijpaneel - Elementgroepen {#side-panel-asset-groups}

Op het tabblad Assets vindt u een vervolgkeuzelijst waarmee u de specifieke groepen elementen kunt selecteren.

![&#x200B; de groepen van Activa &#x200B;](assets/ui-side-panel-asset-groups.png)

### Zijpaneel - Componenten {#side-panel-components}

Op het tabblad Componenten kunt u een keuze maken uit het bereik van componenten. U kunt ook filteren op een bepaalde term of een groep selecteren.

![&#x200B; Componenten tabel &#x200B;](assets/ui-side-panel-components.png)

### Zijpaneel - Inhoudsstructuur {#side-panel-content-tree}

Op het tabblad Inhoudsstructuur kunt u de hiërarchie van inhoud op de pagina weergeven. Wanneer u op een item in het tabblad klikt, gaat u naar het item op de pagina in de editor en selecteert u het item.

![&#x200B; de boom van de Inhoud &#x200B;](assets/ui-side-panel-content-tree.png)

### Bedekkingen {#overlays}

Bedekt het inhoudskader en door de [&#x200B; lagen &#x200B;](#layer) gebruikt om de mechanica van te realiseren hoe u met de componenten en hun inhoud transparant kunt in wisselwerking staan.

De overlays bevinden zich in het editorframe (met alle andere pagina-ontwerpelementen), hoewel ze de juiste componenten in het inhoudsframe bedekken.

![&#x200B; Bedekkingen &#x200B;](assets/ui-overlays.png)

### Laag {#layer}

Een laag is een onafhankelijke bundel van functionaliteit die kan worden geactiveerd aan:

* Een andere weergave van de pagina opgeven
* Hiermee kunt u een pagina bewerken en/of ermee werken

De lagen bieden geavanceerde functionaliteit voor de gehele pagina, in tegenstelling tot specifieke handelingen voor een afzonderlijke component.

AEM wordt geleverd met verschillende lagen die al zijn geïmplementeerd voor het ontwerpen van pagina&#39;s, zoals het bewerken, voorvertonen en annoteren van lagen.

>[!NOTE]
>
>Lagen zijn een krachtig concept dat invloed heeft op de weergave van en interactie met de pagina-inhoud. Wanneer u uw eigen lagen ontwikkelt, moet u ervoor zorgen dat de laag wordt opgeschoond wanneer deze wordt afgesloten.

### Laagschakelaar {#layer-switcher}

Met de laagschakeloptie kunt u de laag kiezen die u wilt gebruiken. Als u deze optie sluit, wordt de laag weergegeven die momenteel wordt gebruikt.

De laagschakelaar is beschikbaar als drop-down van de toolbar (bij de bovenkant van het venster, binnen het redacteurskader).

![&#x200B; de schakelaar van de Laag &#x200B;](assets/ui-layer-switcher.png)

### Werkbalk Component {#component-toolbar}

Elke instantie van een component toont zijn toolbar wanneer geklikt (of eens of met een langzaam tweemaal klikken). De werkbalk bevat de specifieke handelingen (bijvoorbeeld kopiëren, plakken, open editor) die beschikbaar zijn voor de componentinstantie op de pagina.

Afhankelijk van de beschikbare ruimte, worden de componententoolbars geplaatst bij de bovenkant, of bodem, juiste hoek van de aangewezen component.

![&#x200B; de toolbar van de Component &#x200B;](assets/ui-component-toolbar.png)

## Aanvullende informatie {#further-information}

<!--For more details about the concepts around the touch-enabled UI, continue to the article [Concepts of the AEM Touch-Enabled UI](/help/sites-developing/touch-ui-concepts.md).-->

Voor meer technische informatie, zie de [&#x200B; JS documentatiereeks &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html) voor de paginaredacteur.

### Unified Shell {#unified-shell}

Zie [&#x200B; AEM as a Cloud Service op Verenigde Shell &#x200B;](/help/overview/aem-cloud-service-on-unified-shell.md) als u Verenigde Shell als uw AEM UI gebruikt.

Als u moet maken, of reeds gemaakt, om het even welke aanpassingen maken, verenigd zal kunnen worden onbruikbaar gemaakt:

* [van de gebruikersinterface](/help/overview/aem-cloud-service-on-unified-shell.md#disabling-unified-shell)

* van uw projectcode, door:

   * op `/conf/global/setting/unifiedshell`

      * de eigenschap `Boolean` instellen op `enable` `false`
