---
title: Weergaven van pagina-eigenschappen aanpassen
description: Leer hoe u pagina-eigenschappen kunt weergeven en bewerken door auteurs.
exl-id: 363b3c2d-f965-485f-bdae-2ea5b4cecb83
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Weergaven van pagina-eigenschappen aanpassen{#customizing-views-of-page-properties}

Elke pagina heeft een reeks [ eigenschappen ](/help/sites-cloud/authoring/sites-console/page-properties.md) die door gebruikers kunnen worden bekeken en worden uitgegeven. Sommige zijn vereist voor het maken van de pagina (de weergave Maken), andere kunnen in een later stadium worden weergegeven en bewerkt (de weergave Bewerken). Deze pagina-eigenschappen worden gedefinieerd en beschikbaar gesteld door het dialoogvenster (`cq:dialog`) van de juiste paginacomponent.

De standaardstatus voor elke pagina-eigenschap is:

* Verborgen in creeer mening (bijvoorbeeld, **creeer de tovenaar van de Pagina**)

* Beschikbaar in geef mening uit (bijvoorbeeld, **Eigenschappen van de Mening**)

De gebieden moeten specifiek worden gevormd als om het even welke verandering wordt vereist. Dit wordt gedaan gebruikend de aangewezen knoopeigenschappen:

* Het bezit van de pagina dat in creeert mening (bijvoorbeeld, **moet beschikbaar zijn leidt tot de tovenaar van de Pagina**):

   * Naam: `cq:showOnCreate`
   * Type: `Boolean`

* Het bezit van de pagina om in uit te geven mening zoals de **Mening** te zijn/ **geeft** **Eigenschappen** optie uit:

   * Naam: `cq:hideOnEdit`
   * Type: `Boolean`

>[!TIP]
>
>Zie het [ Uitbreiden van de zelfstudie van de Eigenschappen van de Pagina ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=nl-NL) voor een gids aan het aanpassen van paginaeigenschappen.

## De pagina-eigenschappen configureren {#configuring-your-page-properties}

U kunt ook de beschikbare velden configureren door het dialoogvenster van de paginacomponent te configureren en de juiste knoopeigenschappen toe te passen.

Bijvoorbeeld, door gebrek leidt [**tot de tovenaar van de Pagina** ](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page) de gebieden die onder **Meer Titels en Beschrijving** worden gegroepeerd. Om deze te verbergen vormt u:

1. Maak uw paginacomponent onder `/apps` .
1. Creeer een opheffing (gebruikend *diff van de dialoog* die door [ wordt verstrekt het Verspreiden van de Fusie van het Middel ](/help/implementing/developing/introduction/sling-resource-merger.md)) voor de `basic` sectie van uw paginacomponent; bijvoorbeeld:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

1. Stel de eigenschap `path` op `basic` zo in dat deze naar de overschrijving van het basistabblad verwijst (zie ook de volgende stap). Bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Maak een overschrijving van de sectie `basic` - `moretitles` op het bijbehorende pad, bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Pas de juiste node-eigenschap toe:

   * **Naam**: `cq:showOnCreate`
   * **Type**: `Boolean`
   * **Waarde**: `false`

   De **Meer Titels en de sectie van de Beschrijving** zullen niet meer in **worden getoond creëren de tovenaar van de Pagina**.

>[!NOTE]
>
>Wanneer het vormen van paginaeigenschappen voor gebruik met levende exemplaren, zie [ Uitbreidend de Multi Manager van de Plaats ](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties) voor meer details.

## Voorbeeldconfiguratie van pagina-eigenschappen {#sample-configuration-of-page-properties}

Deze steekproef toont de dialoog afschuivende techniek van de [ Verzameling van het Middel ](/help/implementing/developing/introduction/sling-resource-merger.md) met inbegrip van gebruik van [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties) aan. Het illustreert ook het gebruik van zowel `cq:showOnCreate` als `cq:hideOnEdit` .

U kunt de code van deze pagina op [ GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog) vinden.
