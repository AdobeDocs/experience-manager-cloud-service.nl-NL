---
title: Structuur van de AEM-interface
description: De AEM UI heeft verschillende onderliggende beginselen en bestaat uit verschillende sleutelelementen
exl-id: ac211716-d699-4fdb-a286-a0a1122c86c5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7d09e0c990c716d7bbb305210960621ba8735de4
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Structuur van de AEM-interface {#structure-of-the-aem-ui}

De AEM UI heeft verschillende onderliggende beginselen en bestaat uit verschillende sleutelelementen:

## Consoles {#consoles}

### Basislay-out en -formaat {#basic-layout-and-resizing}

De interface biedt ruimte voor zowel mobiele apparaten als bureaubladapparaten, in plaats van twee stijlen te maken, AEM gebruikt één stijl die voor alle schermen en apparaten werkt.

Alle modules gebruiken de zelfde basislay-out:

![ AEM Sites console ](assets/ui-sites-console.png)

De lay-out volgt een ontvankelijke ontwerpstijl en past zich aan de grootte van het apparaat, of venster, of allebei aan, dat u gebruikt.

Als de resolutie bijvoorbeeld lager is dan 1024 pixels (zoals op een mobiel apparaat), wordt het beeldscherm dienovereenkomstig aangepast:

![ de console mobiele mening van Plaatsen ](assets/ui-sites-mobile.png)

### Koptekstbalk {#header-bar}

![ AEM kopbalbar ](assets/ui-header-bar.png)

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

![ de toolbar van AEM Sites ](assets/ui-sites-toolbar.png)

Ook afhankelijk van of een bron is geselecteerd:

![ geselecteerde de toolbar van AEM Sites ](assets/ui-sites-toolbar-selected.png)

### Linkerspoor {#left-rail}

De linkerspoorstaaf kan worden geopend/verborgen zoals vereist om te tonen:

* **slechts Inhoud**
* **de Boom van de Inhoud**
* **Chronologie**
* **Verwijzingen**
* **Filter**

Het gebrek is **slechts Inhoud** (spoorstaaf verborgen).

![ Linkerspoor ](assets/ui-left-rail.png)

## Pagina&#39;s ontwerpen {#page-authoring}

Bij het ontwerpen van pagina&#39;s ziet u de volgende structurele gebieden.

### Inhoudskader {#content-frame}

De pagina-inhoud wordt weergegeven in het inhoudskader. Het inhoudskader is onafhankelijk van de editor - om ervoor te zorgen dat er geen conflicten optreden vanwege CSS of JavaScript.

Het inhoudskader bevindt zich in de rechtersectie van het venster, onder de werkbalk.

![ kader van de Inhoud ](assets/ui-content-frame.png)

### Editor frame {#editor-frame}

Het editorkader laat de het uitgeven eigenschappen toe.

Het editorframe is een container (abstract) voor alle pagina-ontwerpelementen. Het leeft bovenop het inhoudskader, en omvat:

* De bovenste werkbalk
* Het zijpaneel
* Alle overlays
* Een ander pagina-ontwerpelement, bijvoorbeeld de componentwerkbalk

![ Kader van de Redacteur ](assets/ui-editor-frame.png)

### Zijpaneel {#side-panel}

Bevat drie standaardtabbladen. De **Assets** en **Componenten** lusjes laten u dergelijke elementen selecteren en hen slepen van het paneel en hen laten vallen op de pagina. Het **lusje van de Boom van de Inhoud** laat u de hiërarchie van inhoud op de pagina inspecteren.

Het zijpaneel is standaard verborgen. Als deze optie is geselecteerd, wordt deze links weergegeven of als de vensterbreedte kleiner is dan 1024 pixels, schuift deze over om het hele venster te bedekken, bijvoorbeeld op een mobiel apparaat.

![ Zijpaneel ](assets/ui-side-panel.png)

### Zijpaneel - Assets {#side-panel-assets}

Op het tabblad Assets kunt u een selectie maken uit het assortiment elementen. U kunt ook filteren op een bepaalde term of een groep selecteren.

![ Assets tabel ](assets/ui-side-panel-assets.png)

### Zijpaneel - Elementgroepen {#side-panel-asset-groups}

Op het tabblad Assets vindt u een vervolgkeuzelijst waarmee u de specifieke groepen elementen kunt selecteren.

![ de groepen van Activa ](assets/ui-side-panel-asset-groups.png)

### Zijpaneel - Componenten {#side-panel-components}

Op het tabblad Componenten kunt u een keuze maken uit het bereik van componenten. U kunt ook filteren op een bepaalde term of een groep selecteren.

![ Componenten tabel ](assets/ui-side-panel-components.png)

### Zijpaneel - Inhoudsstructuur {#side-panel-content-tree}

Op het tabblad Inhoudsstructuur kunt u de hiërarchie van inhoud op de pagina weergeven. Wanneer u op een item in het tabblad klikt, gaat u naar het item op de pagina in de editor en selecteert u het item.

![ de boom van de Inhoud ](assets/ui-side-panel-content-tree.png)

### Bedekkingen {#overlays}

Bedekt het inhoudskader en door de [ lagen ](#layer) gebruikt om de mechanica van te realiseren hoe u met de componenten en hun inhoud transparant kunt in wisselwerking staan.

De overlays bevinden zich in het editorframe (met alle andere pagina-ontwerpelementen), hoewel ze de juiste componenten in het inhoudsframe bedekken.

![ Bedekkingen ](assets/ui-overlays.png)

### Laag {#layer}

Een laag is een onafhankelijke bundel van functionaliteit die kan worden geactiveerd aan:

* Een andere weergave van de pagina opgeven
* Hiermee kunt u een pagina bewerken en/of ermee werken

De lagen bieden geavanceerde functionaliteit voor de gehele pagina, in tegenstelling tot specifieke handelingen voor een afzonderlijke component.

AEM wordt geleverd met verschillende lagen die al zijn geïmplementeerd voor het ontwerpen van pagina&#39;s, zoals het bewerken, voorvertonen en notities aanbrengen van lagen.

>[!NOTE]
>
>Lagen zijn een krachtig concept dat invloed heeft op de weergave van en interactie met de pagina-inhoud. Wanneer u uw eigen lagen ontwikkelt, moet u ervoor zorgen dat de laag wordt opgeschoond wanneer deze wordt afgesloten.

### Laagschakelaar {#layer-switcher}

Met de laagschakeloptie kunt u de laag kiezen die u wilt gebruiken. Als u deze optie sluit, wordt de laag weergegeven die momenteel wordt gebruikt.

De laagschakelaar is beschikbaar als drop-down van de toolbar (bij de bovenkant van het venster, binnen het redacteurskader).

![ de schakelaar van de Laag ](assets/ui-layer-switcher.png)

### Werkbalk Component {#component-toolbar}

Elke instantie van een component toont zijn toolbar wanneer geklikt (of eens of met een langzaam tweemaal klikken). De werkbalk bevat de specifieke handelingen (bijvoorbeeld kopiëren, plakken, open editor) die beschikbaar zijn voor de componentinstantie op de pagina.

Afhankelijk van de beschikbare ruimte, worden de componententoolbars geplaatst bij de bovenkant, of bodem, juiste hoek van de aangewezen component.

![ de toolbar van de Component ](assets/ui-component-toolbar.png)

## Aanvullende informatie {#further-information}

<!--For more details about the concepts around the touch-enabled UI, continue to the article [Concepts of the AEM Touch-Enabled UI](/help/sites-developing/touch-ui-concepts.md).-->

Voor meer technische informatie, zie de [ JS documentatiereeks ](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html) voor de paginaredacteur.

### Unified Shell {#unified-shell}

Zie [ AEM as a Cloud Service op Verenigde Shell ](/help/overview/aem-cloud-service-on-unified-shell.md) als u Verenigde Shell als uw AEM UI gebruikt.

Als u moet maken, of reeds gemaakt, om het even welke aanpassingen maken, verenigd zal kunnen worden onbruikbaar gemaakt:

* [van de gebruikersinterface](/help/overview/aem-cloud-service-on-unified-shell.md#disabling-unified-shell)

* van uw projectcode, door:

   * op `/conf/global/setting/unifiedshell`

      * de eigenschap `Boolean` instellen op `enable` `false`
