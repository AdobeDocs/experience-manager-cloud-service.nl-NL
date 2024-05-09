---
title: Metagegevenstoewijzing tussen Workfront en Experience Manager Assets configureren
description: Wijs de gebieden van activa meta-gegevens tussen Adobe Workfront en Experience Manager as a Cloud Service toepassingen toe. Als u metagegevensvelden toewijst aan Experience Manager Assets en een element verzendt van Workfront naar, kunt u de metagegevens van de toegewezen elementen weergeven in Experience Manager Assets.
exl-id: 71400769-b2bc-4f5d-8b6b-a73598e837b4
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---

# Metagegevenstoewijzing tussen Adobe Workfront en Experience Manager Assets configureren {#asset-metadata-mapping-workfront-aem-assets}

U kunt de gebieden van activa meta-gegevens tussen Adobe Workfront en Experience Manager as a Cloud Service toepassingen in kaart brengen. Als u metagegevensvelden toewijst aan Experience Manager Assets en een element verzendt van Workfront naar, kunt u de metagegevens van de toegewezen elementen weergeven in Experience Manager Assets.

Als u bijvoorbeeld de metagegevensvelden voor een afbeelding wilt behouden, zoals de naam, beschrijving en het project waartoe deze behoort in Workfront wanneer u de afbeelding naar Experience Manager Assets verzendt, configureert u deze velden en wijst u deze toe aan de Experience Manager Assets-eigenschappen.

**Hoofdletters gebruiken**

Een afbeelding `add-users-workfront.png` bestaat in de `Metadata Syncs` project in Adobe Workfront-toepassing. U moet die afbeelding naar Experience Manager Assets verzenden as a Cloud Service met de volgende metagegevens:

* Projectnaam

* Documentnaam

* Documentbeschrijving

## Vereisten {#prerequisites}

* Beheerders hebben toegang tot as a Cloud Service Workfront- en Experience Manager Assets-toepassingen.

* Een integratie tussen [as a Cloud Service Workfront- en Experience Manager Assets-toepassingen](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FDocuments%2FAdobe_Workfront_for_Experience_Manager_Assets_Essentials%2Fsetup-asset-essentials.htm&amp;_LANG=enus).

## Metagegevenstoewijzing instellen in Workfront {#set-up-metadata-mapping}

Als u metagegevenstoewijzing wilt instellen voor de velden Projectnaam, Documentnaam en Documentbeschrijving in Workfront:

1. Klik op het pictogram Hoofdmenu ![Menu tonen](assets/show-menu.svg) beschikbaar in de rechterbovenhoek van de Adobe Workfront-toepassing en klik vervolgens op **[!UICONTROL Setup]**.

1. Selecteren **[!UICONTROL Documents]** in het linkerdeelvenster selecteert u vervolgens **[!UICONTROL Experience Manager Assets]**.

1. Selecteer de Experience Manager Assets-integratie en klik op **[!UICONTROL Edit]**.

1. Klik op **[!UICONTROL Metadata]**. In de **[!UICONTROL Assets]** tab, wijs de [!UICONTROL Project] > [!UICONTROL Name] Workfront-veld naar de `wm:projectName` Experience Manager Assets. Als u niet de nauwkeurige gelijke vindt, adviseert de Adobe dat u naar de beste gelijke zoekt om het gebied van Workfront en van Experience Manager Assets in kaart te brengen. U kunt toewijzingsvelden van verschillende gegevenstypen vermijden. U kunt bijvoorbeeld een Workfront-datumveld toewijzen aan een beschrijvingsmiddelenveld.
1. Wijs de [!UICONTROL Document] > [!UICONTROL Name] Workfront-veld naar de `wm:documentName` Experience Manager Assets.

   ![Toewijzing in Workfront](assets/workfront-metadata-mapping.png)

1. Wijs de [!UICONTROL Document] > [!UICONTROL Description] Workfront-veld naar de `dc:description` Experience Manager Assets.

   >[!VIDEO](https://video.tv.adobe.com/v/344255)

## De afbeelding verzenden van Workfront naar Experience Manager Assets {#send-image-workfront-assets}

De afbeelding verzenden van Workfront naar Experience Manager Assets:

1. Klik op het pictogram Hoofdmenu ![Menu tonen](assets/show-menu.svg) beschikbaar in de rechterbovenhoek van de Adobe Workfront-toepassing en klik vervolgens op **[!UICONTROL Projects]**.

1. Klikken **[!UICONTROL New Project]** om een project te maken.

1. Klikken **[!UICONTROL Documents]** in het linkervenster beschikbaar, sleept u en selecteert u de afbeelding die u naar Experience Manager Assets wilt verzenden.

1. Klikken **[!UICONTROL Send to]** en kiest u vervolgens de naam van de Experience Manager Assets Essentials-integratie.

   ![Naar AEM](assets/send-to-aem.png)

1. Kies de doelmap voor het element en klik op **[!UICONTROL Select Folder]**.

1. Klik op **[!UICONTROL Save]**.

## Metagegevenstoewijzing voor elementen configureren in as a Cloud Service Experience Manager {#metadata-mapping-aem}

Na [assetmetagegevenstoewijzing configureren in Adobe Workfront](#set-up-metadata-mapping)Als u de juiste metagegevensresultaten voor de afbeelding wilt weergeven, moet u dezelfde toewijzing gebruiken in de as a Cloud Service Experience Manager Assets-toepassing.

Metagegevenstoewijzing wordt uitgevoerd met gebruik van metagegevensschema&#39;s in Experience Manager Assets. U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat tabbladen en formulieritems binnen tabbladen. U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte. U kunt tabs of formulieritems toevoegen aan het metagegevensschema. Zie voor meer informatie [Metagegevensschema&#39;s](metadata-schemas.md).

U kunt als volgt de toewijzing van metagegevens configureren met een nieuw metagegevensformulier in as a Cloud Service Experience Manager Assets:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.

1. Klik op **[!UICONTROL Create]** op de werkbalk. Geef in het dialoogvenster de titel van het schema op en klik op **[!UICONTROL Create]** om het maken van het formulier te voltooien.

1. Selecteer het schema en klik op **[!UICONTROL Edit]**.

1. (Optioneel) Klik in de formuliereditor voor metagegevensschema op `+` om een tabblad te maken voor de Workfront-velden.

1. Klik op de knop **[!UICONTROL Build Form]** en sleep de **[!UICONTROL Single Line Text]** aan het formulier. Klik op de component in het formulier. In de **[!UICONTROL Build Form]** tab:

   1. Opgeven `Project Name` in de **[!UICONTROL Field Label]** veld.

   1. Opgeven `./jcr:content/metadata/wm:projectName` in de **[!UICONTROL Map to property]** veld. Gebruik als richtlijn de volgende sjabloon om de veldtoewijzingen in Experience Manager-elementen te definiëren:
      `./jcr:content/metadata/<mapping defined for the field in workfront>`.

      Tijdens het configureren van toewijzingen in Workfront, hebt u toegewezen `wm:projectName` Experience Manager Assets-veld naar project > Naam Workfront-veld.

      `wm` verwijst naar de naamruimte en `projectName` verwijst naar de titel van de eigenschap. Gebruik de `namespace:propertyTitle` opmaak voor het definiëren van toewijzingen van metagegevensvelden.

      ![Naar AEM](assets/metadata-schema-mapping.png)

1. Klik op de knop **[!UICONTROL Build Form]** en sleep de **[!UICONTROL Single Line Text]** aan het formulier. Klik op de component in het formulier. In de **[!UICONTROL Build Form]** tab:

   1. Opgeven `Document Name` in de **[!UICONTROL Field Label]** veld.

   1. Opgeven `./jcr:content/metadata/wm:documentName` in de **[!UICONTROL Map to property]** veld.
Tijdens het configureren van toewijzingen in Workfront, hebt u toegewezen `wm:documentName` Experience Manager Assets field to Document > Name Workfront field.

1. Klik op de knop **[!UICONTROL Build Form]** en sleep de **[!UICONTROL Multi Line Text]** aan het formulier. Klik op de component in het formulier. In de **[!UICONTROL Build Form]** tab:

   1. Opgeven `Document Description` in de **[!UICONTROL Field Label]** veld.

   1. Opgeven `./jcr:content/metadata/dc:description` in de **[!UICONTROL Map to property]** veld.
Tijdens het configureren van toewijzingen in Workfront, hebt u toegewezen `dc:description` Experience Manager Assets field to Document > Description Workfront field.

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan

   >[!VIDEO](https://video.tv.adobe.com/v/344314)

## Instellingen voor metagegevens toepassen op de afbeeldingsmap {#apply-metadata-settings-image-folder}

Nadat u de metagegevensinstellingen hebt geconfigureerd in de as a Cloud Service toepassing Experience Manager, past u deze instellingen toe op de [map met de afbeelding die vanuit de Workfront-toepassing is verzonden](#send-image-workfront-assets).

Instellingen voor metagegevens toepassen op de afbeeldingsmap:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.

1. Selecteer het metagegevensschema in de beschikbare lijst en klik op **[!UICONTROL Apply to Folders]**.

1. Selecteer de doelmap waarnaar [de afbeelding wordt verzonden vanuit de Adobe Workfront-toepassing](#send-image-workfront-assets) en klik op **[!UICONTROL Apply]**.

U kunt naar de afbeelding navigeren in Experience Manager Assets en de metagegevens bekijken die aan de afbeelding zijn gekoppeld. Selecteer de afbeelding en klik op **[!UICONTROL Properties]** om de metagegevens van de afbeelding weer te geven.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
