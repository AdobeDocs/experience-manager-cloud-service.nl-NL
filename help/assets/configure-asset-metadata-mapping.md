---
title: Metagegevenstoewijzing tussen Workfront en Experience Manager Assets configureren
description: De metagegevensvelden voor elementen toewijzen aan Adobe Workfront- en Experience Manager as a Cloud Service-toepassingen. Als u metagegevensvelden toewijst aan Experience Manager Assets en een element verzendt van Workfront naar, kunt u de metagegevens van de toegewezen elementen weergeven in Experience Manager Assets.
exl-id: 71400769-b2bc-4f5d-8b6b-a73598e837b4
feature: Metadata, Workfront Integrations and Apps
role: User, Admin
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---

# Metagegevenstoewijzing tussen Adobe Workfront en Experience Manager Assets configureren {#asset-metadata-mapping-workfront-aem-assets}

U kunt de metagegevensvelden voor elementen toewijzen tussen Adobe Workfront- en Experience Manager as a Cloud Service-toepassingen. Als u metagegevensvelden toewijst aan Experience Manager Assets en een element verzendt van Workfront naar, kunt u de metagegevens van de toegewezen elementen weergeven in Experience Manager Assets.

Als u bijvoorbeeld de metagegevensvelden voor een afbeelding wilt behouden, zoals de naam, beschrijving en het project waartoe deze behoort in Workfront wanneer u de afbeelding naar Experience Manager Assets verzendt, configureert u deze velden en wijst u deze toe aan de Experience Manager Assets-eigenschappen.

**Geval van het Gebruik**

Er bestaat een afbeelding `add-users-workfront.png` in het `Metadata Syncs` -project in de Adobe Workfront-toepassing. U moet die afbeelding naar Experience Manager Assets as a Cloud Service verzenden met de volgende metagegevens:

* Projectnaam

* Documentnaam

* Documentbeschrijving

## Vereisten {#prerequisites}

* Beheerders hebben toegang tot Workfront- en Experience Manager Assets as a Cloud Service-toepassingen.

* Een integratie tussen [ Workfront en Experience Manager Assets as a Cloud Service toepassingen ](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&topicId=Content%2FDocuments%2FAdobe_Workfront_for_Experience_Manager_Assets_Essentials%2Fsetup-asset-essentials.htm&_LANG=enus).

## Metagegevenstoewijzing instellen in Workfront {#set-up-metadata-mapping}

Als u metagegevenstoewijzing wilt instellen voor de velden Projectnaam, Documentnaam en Documentbeschrijving in Workfront:

1. Klik het Belangrijkste pictogram van het Menu ![ tonen Menu ](assets/show-menu.svg) beschikbaar in de hoger-juiste hoek van de toepassing van Adobe Workfront, dan klik **[!UICONTROL Setup]**.

1. Selecteer **[!UICONTROL Documents]** in het linkerdeelvenster en selecteer vervolgens **[!UICONTROL Experience Manager Assets]** .

1. Selecteer de Experience Manager Assets-integratie en klik op **[!UICONTROL Edit]** .

1. Klik op **[!UICONTROL Metadata]**. Wijs op het tabblad **[!UICONTROL Assets]** het veld [!UICONTROL Project] > [!UICONTROL Name] Workfront toe aan het veld `wm:projectName` Experience Manager Assets. Als u de exacte overeenkomst niet vindt, raadt Adobe u aan te zoeken naar de beste overeenkomst om het Workfront- en Experience Manager Assets-veld in kaart te brengen. U kunt toewijzingsvelden van verschillende gegevenstypen vermijden. Een Workfront-datumveld bijvoorbeeld toewijzen aan een Assets-beschrijvingsveld.
1. Wijs het veld [!UICONTROL Document] > [!UICONTROL Name] Workfront toe aan het veld `wm:documentName` Experience Manager Assets.

   ![ Afbeelding in Workfront ](assets/workfront-metadata-mapping.png)

1. Wijs het veld [!UICONTROL Document] > [!UICONTROL Description] Workfront toe aan het veld `dc:description` Experience Manager Assets.

   >[!VIDEO](https://video.tv.adobe.com/v/344255)

## De afbeelding verzenden van Workfront naar Experience Manager Assets {#send-image-workfront-assets}

De afbeelding verzenden van Workfront naar Experience Manager Assets:

1. Klik het Belangrijkste pictogram van het Menu ![ tonen Menu ](assets/show-menu.svg) beschikbaar in de hoger-juiste hoek van de toepassing van Adobe Workfront, dan klik **[!UICONTROL Projects]**.

1. Klik op **[!UICONTROL New Project]** om een project te maken.

1. Klik op de optie **[!UICONTROL Documents]** in het linkerdeelvenster en sleep de afbeelding die u naar Experience Manager Assets wilt verzenden.

1. Klik op **[!UICONTROL Send to]** en kies vervolgens de integratienaam van Experience Manager Assets Essentials.

   ![ verzenden naar AEM ](assets/send-to-aem.png)

1. Kies de doelmap voor het element en klik op **[!UICONTROL Select Folder]** .

1. Klik op **[!UICONTROL Save]**.

## Metagegevenstoewijzing voor elementen configureren in Experience Manager as a Cloud Service {#metadata-mapping-aem}

Na [ vormend de afbeelding van activa meta-gegevens in Adobe Workfront ](#set-up-metadata-mapping), moet u de zelfde afbeelding in de toepassing van as a Cloud Service van Experience Manager Assets gebruiken om aangewezen meta-gegevensresultaten voor het beeld te tonen.

Metagegevenstoewijzing wordt uitgevoerd met gebruik van metagegevensschema&#39;s in Experience Manager Assets. U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat tabbladen en formulieritems binnen tabbladen. U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagplaats. U kunt tabs of formulieritems toevoegen aan het metagegevensschema. Voor meer informatie, zie [ Schema&#39;s van Meta-gegevens ](metadata-schemas.md).

U kunt als volgt metagegevenstoewijzing configureren met een nieuw metagegevensformulier in Experience Manager Assets as a Cloud Service:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .

1. Klik op **[!UICONTROL Create]** op de werkbalk. Geef in het dialoogvenster de titel van het schema op en klik op **[!UICONTROL Create]** om het maken van het formulier te voltooien.

1. Selecteer het schema en klik op **[!UICONTROL Edit]** .

1. (Optioneel) Klik in de Formuliereditor voor metagegevensschema op `+` om een tabblad te maken voor de Workfront-velden.

1. Klik op de tab **[!UICONTROL Build Form]** en sleep de component **[!UICONTROL Single Line Text]** naar het formulier. Klik op de component in het formulier. Op het tabblad **[!UICONTROL Build Form]** :

   1. Geef `Project Name` op in het veld **[!UICONTROL Field Label]** .

   1. Geef `./jcr:content/metadata/wm:projectName` op in het veld **[!UICONTROL Map to property]** . Gebruik als richtlijn de volgende sjabloon om de veldtoewijzingen in Experience Manager Assets te definiëren:
      `./jcr:content/metadata/<mapping defined for the field in workfront>`.

      Tijdens het configureren van toewijzingen in Workfront, hebt u het veld `wm:projectName` Experience Manager Assets toegewezen aan Project > Naam Workfront.

      `wm` verwijst naar de naamruimtenaam en `projectName` verwijst naar de titel van de eigenschap. Gebruik de indeling `namespace:propertyTitle` om veldtoewijzingen voor metagegevens te definiëren.

      ![ verzenden naar AEM ](assets/metadata-schema-mapping.png)

1. Klik op de tab **[!UICONTROL Build Form]** en sleep de component **[!UICONTROL Single Line Text]** naar het formulier. Klik op de component in het formulier. Op het tabblad **[!UICONTROL Build Form]** :

   1. Geef `Document Name` op in het veld **[!UICONTROL Field Label]** .

   1. Geef `./jcr:content/metadata/wm:documentName` op in het veld **[!UICONTROL Map to property]** .
Tijdens het configureren van toewijzingen in Workfront, hebt u het Experience Manager Assets-veld `wm:documentName` toegewezen aan Document > Naam Workfront-veld.

1. Klik op de tab **[!UICONTROL Build Form]** en sleep de component **[!UICONTROL Multi Line Text]** naar het formulier. Klik op de component in het formulier. Op het tabblad **[!UICONTROL Build Form]** :

   1. Geef `Document Description` op in het veld **[!UICONTROL Field Label]** .

   1. Geef `./jcr:content/metadata/dc:description` op in het veld **[!UICONTROL Map to property]** .
Tijdens het configureren van toewijzingen in Workfront, hebt u het veld `dc:description` Experience Manager Assets toegewezen aan Document > Beschrijving van Workfront.

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

   >[!VIDEO](https://video.tv.adobe.com/v/344314)

## Instellingen voor metagegevens toepassen op de afbeeldingsmap {#apply-metadata-settings-image-folder}

Na het vormen van de meta-gegevensmontages in de toepassing van Experience Manager as a Cloud Service, pas die montages op de [ omslag toe die het beeld bevat dat van de toepassing van Workfront ](#send-image-workfront-assets) wordt verzonden.

Instellingen voor metagegevens toepassen op de afbeeldingsmap:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .

1. Selecteer het metagegevensschema in de beschikbare lijst en klik op **[!UICONTROL Apply to Folders]** .

1. Selecteer de bestemmingsomslag waarnaar [ het beeld van de toepassing van Adobe Workfront ](#send-image-workfront-assets) wordt verzonden en **[!UICONTROL Apply]** klikt.

U kunt naar de afbeelding navigeren in Experience Manager Assets en de metagegevens bekijken die aan de afbeelding zijn gekoppeld. Selecteer de afbeelding en klik op **[!UICONTROL Properties]** om de metagegevens van de afbeelding weer te geven.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
