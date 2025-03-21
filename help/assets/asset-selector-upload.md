---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Gebruik de functie Asset Selector om de metagegevens en vertoningen van elementen in uw toepassing te zoeken, te zoeken en op te halen.
role: Admin,User
exl-id: d6ff601c-3111-421a-9a94-cc524ce7e432
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Bestanden en mappen uploaden naar Asset Selector {#upload-files-folders}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

U kunt bestanden of mappen vanuit uw lokale bestandssysteem uploaden naar Asset Selector. Als u bestanden wilt uploaden met het lokale bestandssysteem, moet u doorgaans een upload-functie gebruiken die wordt geleverd door een Asset Selector-microfront-end toepassing.

## Elementen uploaden vanuit een lokaal bestandssysteem {#basic-upload}

Voer de volgende stappen uit om elementen toe te voegen aan Asset Selector:

1. Als u spoormening gebruikt, dan ga naar ellips en klik dan ![ uploadpictogram ](assets/upload-icon.svg) **[!UICONTROL Upload]**. Anderzijds, klik ![ uploadt pictogram ](assets/upload-icon.svg) **[!UICONTROL Upload]** op top-right in het geval van modale mening. Het scherm [!UICONTROL Upload Assets] wordt weergegeven.

   ![ upload activa aan de Selecteur van Activa ](assets/upload-assets.png)

   Daarnaast kunt u in de sectie **[!UICONTROL Drag files or folders here]** de elementen slepen van het lokale bestandssysteem of op **[!UICONTROL Browse]** klikken om handmatig bestanden of mappen te selecteren die beschikbaar zijn op het lokale bestandssysteem. Deze lijst met bestanden die deel uitmaken van de upload, is beschikbaar als een lijst.

   ![ Basis uploadt activa aan de Selecteur van Activa ](assets/basic-upload.png)

   U kunt geselecteerde afbeeldingen ook voorvertonen met behulp van de miniaturen en op het X-pictogram klikken om een bepaalde afbeelding uit de lijst te verwijderen. Het X-pictogram wordt alleen weergegeven wanneer u de muis boven de naam of grootte van de afbeelding houdt. U kunt ook op **[!UICONTROL Remove all]** klikken om alle items uit de uploadlijst te verwijderen.

1. Klik op **[!UICONTROL Upload]** om het uploadproces te voltooien. Uw geüploade elementen worden weergegeven. Zie [ basisupload ](/help/assets/asset-selector-customization.md#basic-upload) voor de configureerbare code.

## Elementen uploaden met metagegevens {#upload-assets-with-metadata}

U kunt metagegevens aan de elementen toevoegen terwijl u deze direct in de toepassing uploadt. Metagegevens omvatten diverse velden, zoals de onderwerpregel van het bedrijf, productdetails, campagne enzovoort. Hiervoor wordt de eigenschap `metadataSchema` gebruikt. Ga naar [ eigenschappen van de activaselecteur ](/help/assets/asset-selector-properties.md) om meer over `metadataSchema` bezit te weten.

Zie [ uploaden met meta-gegevens ](/help/assets/asset-selector-customization.md#upload-with-metadata) voor het codefragment dat voor de configuratie wordt vereist.

![ upload activa met meta-gegevens ](assets/upload-with-metadata.png)

1. Definieer de naam voor het uploaden met behulp van het veld **[!UICONTROL Campaign name]** . U kunt een bestaande naam gebruiken of een nieuwe naam maken. Met de Asset Selector beschikt u over meer opties terwijl u de naam typt.

   Het wordt aanbevolen om bij voorkeur waarden in de overige velden op te geven en een verbeterde zoekervaring voor uw geüploade elementen te maken.

1. Definieer ook waarden voor de velden **[!UICONTROL Keywords]** , **[!UICONTROL Channels]** , **[!UICONTROL Timeframe]** en **[!UICONTROL Region]** . Tags toevoegen en elementen groeperen op trefwoorden, kanalen en locatie stelt iedereen die uw goedgekeurde bedrijfsinhoud gebruikt in staat deze elementen te vinden en te organiseren.

1. Klik op **[!UICONTROL Upload]** om elementen te uploaden naar de Asset Selector. Het bevestigingsvak [!UICONTROL Review details] wordt weergegeven. Klik op [!UICONTROL Continue].

1. Assets begint met uploaden. Klik op [!UICONTROL New Upload] om de uploadprocedure opnieuw te starten. Klik op [!UICONTROL Done] om het uploaden te voltooien.


## Aangepaste upload {#customize-upload}

Met Asset Selector kunt u een aangepast uploadformulier toevoegen. Er zijn verschillende aanpassingen beschikbaar. Bijvoorbeeld staat het [ hideUploadButton ](/help/assets/asset-selector-properties.md) bezit u toe om uploadt knoop te verbergen die door gebrek in de toepassing wordt getoond. In plaats daarvan, kunt u het aanpassen om buiten de MFE toepassing zoals vereist terug te geven. Zie [ aangepaste upload ](/help/assets/asset-selector-customization.md#customized-upload) voor de configuratie.

![ Aangepaste upload ](assets/customized-upload.png)

>[!MORELIKETHIS]
>
>* [ Voorbeelden van de Selecteur van Activa ](/help/assets/asset-selector-examples.md)
>* [ integreer de Selector van Activa met diverse toepassingen ](/help/assets/integrate-asset-selector.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
