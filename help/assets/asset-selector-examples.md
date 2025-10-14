---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Voorbeelden om Asset Selector te gebruiken om naar wens aan te passen.
role: Admin, User
exl-id: 7a393a96-f2a2-4a25-922c-577271cafc57
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Voorbeelden voor het gebruik van de eigenschappen van Asset Selector {#usage-examples}

U kunt de Eigenschappen van de Selecteur van Activa [&#128279;](/help/assets/asset-selector-properties.md) in het **index.html** dossier bepalen om de vertoning van de Selecteur van Activa binnen uw toepassing aan te passen.

## Voorbeeld 1: Kiezer voor bedrijfsmiddelen in spoorwegweergave

![&#x200B; spoorstaaf-mening-voorbeeld &#x200B;](assets/rail-view-example-vanilla.png)

Als de waarde van de AssetSelector `rail` is ingesteld op `false` of niet wordt vermeld in de eigenschappen, wordt de functie Asset Selector standaard weergegeven in de modale weergave. Met de eigenschap `acvConfig` kunt u bepaalde diepgaande configuraties gebruiken, zoals Slepen en neerzetten. Bezoek [&#x200B; laat of maak belemmering en daling &#x200B;](asset-selector-customization.md#enable-disable-drag-and-drop) toe onbruikbaar om het gebruik van `acvConfig` bezit te begrijpen.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

## Voorbeeld 2: popover-metagegevens

Gebruik verschillende eigenschappen om de metagegevens te definiëren van een element dat u wilt weergeven met een info-pictogram. De info popover verstrekt de inzameling van informatie over activa of de omslag met inbegrip van titel, afmetingen, datum van wijziging, plaats, en beschrijving van activa. In het onderstaande voorbeeld worden verschillende eigenschappen gebruikt om metagegevens van een element weer te geven. Met de eigenschap `repo:path` wordt bijvoorbeeld de locatie van een element opgegeven. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![&#x200B; meta-gegevens-popover-voorbeeld &#x200B;](assets/metadata-popover.png)

## Voorbeeld 3: Aangepaste filtereigenschap in de rasterweergave

Naast de beperkte zoekopdracht kunt u met Assets Selector verschillende kenmerken aanpassen om uw zoekopdracht te verfijnen van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] -toepassing. Voeg de volgende code toe om aangepaste zoekfilters in uw toepassing toe te voegen. In het onderstaande voorbeeld zoekt u in `Type Filter` het elementtype tussen Afbeeldingen, Documenten of Video&#39;s of het filtertype dat u voor de zoekopdracht hebt toegevoegd.

![&#x200B; douane-filter-voorbeeld-vanilla &#x200B;](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->


>[!MORELIKETHIS]
>
>* [&#x200B; de aanpassingen van de Selecteur van Activa &#x200B;](/help/assets/asset-selector-customization.md)
>* [&#x200B; de selecteur van Activa uploadt &#x200B;](/help/assets/asset-selector-upload.md)
>* [&#x200B; Eigenschappen van de Selecteur van Activa &#x200B;](/help/assets/asset-selector-properties.md)
>* [&#x200B; integreer de Selector van Activa met Dynamische Media met mogelijkheden OpenAPI &#x200B;](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
