---
title: Weergaven van pagina-eigenschappen aanpassen
description: Leer hoe u pagina-eigenschappen kunt weergeven en bewerken door auteurs.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Weergaven van pagina-eigenschappen aanpassen{#customizing-views-of-page-properties}

Elke pagina heeft een set [eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) die door gebruikers kunnen worden weergegeven en bewerkt. Sommige zijn vereist voor het maken van de pagina (de weergave Maken), andere kunnen in een later stadium worden weergegeven en bewerkt (de weergave Bewerken). Deze pagina-eigenschappen worden gedefinieerd en beschikbaar gesteld door het dialoogvenster (`cq:dialog`) van het desbetreffende pagina-onderdeel.

De standaardstatus voor elke pagina-eigenschap is:

* Verborgen in de ontwerpweergave (bijvoorbeeld **Pagina maken** wizard)

* Beschikbaar in de bewerkingsweergave (bijvoorbeeld **Eigenschappen weergeven**)

De gebieden moeten specifiek worden gevormd als om het even welke verandering wordt vereist. Dit wordt gedaan gebruikend de aangewezen knoopeigenschappen:

* De eigenschap Pagina die beschikbaar moet zijn in de weergave Maken (bijvoorbeeld **Pagina maken** wizard):

   * Naam: `cq:showOnCreate`
   * Type: `Boolean`

* De eigenschap Pagina die beschikbaar moet zijn in de bewerkingsweergave, zoals de **Weergave**/**Bewerken**  **Eigenschappen** optie:

   * Naam: `cq:hideOnEdit`
   * Type: `Boolean`

>[!TIP]
>
>Zie de [Zelfstudie Pagina-eigenschappen uitbreiden](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) voor een handleiding voor het aanpassen van pagina-eigenschappen.

## De pagina-eigenschappen configureren {#configuring-your-page-properties}

U kunt ook de beschikbare velden configureren door het dialoogvenster van de paginacomponent te configureren en de juiste knoopeigenschappen toe te passen.

Standaard worden bijvoorbeeld de [**Pagina maken** wizard](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) geeft de velden weer die onder zijn gegroepeerd **Meer titels en beschrijving**. Om deze te verbergen vormt u:

1. De pagina-component maken onder `/apps`.
1. Overschrijven maken (met *Diff* door de [Samenvoeging van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md)) voor de `basic` sectie van uw paginacomponent; bijvoorbeeld:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

1. Stel de `path` eigenschap op `basic` om naar de opheffing van het basislusje te wijzen (zie ook de volgende stap). Bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Een overschrijving maken van de `basic` - `moretitles` het desbetreffende pad, bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Pas de juiste node-eigenschap toe:

   * **Naam**: `cq:showOnCreate`
   * **Type**: `Boolean`
   * **Waarde**: `false`

   De **Meer titels en beschrijving** wordt niet meer weergegeven in het dialoogvenster **Pagina maken** wizard.

>[!NOTE]
>
>Wanneer u pagina-eigenschappen configureert voor gebruik met live kopieën, raadpleegt u het document [Het beheer van meerdere sites uitbreiden](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties) voor meer informatie .

## Voorbeeldconfiguratie van pagina-eigenschappen {#sample-configuration-of-page-properties}

In dit voorbeeld ziet u de dialoochtechniek van het dialoogvenster [Samenvoeging van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md) inclusief het gebruik van [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties). Het illustreert ook het gebruik van beide `cq:showOnCreate` en `cq:hideOnEdit`.

U kunt de code van deze pagina vinden op [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
