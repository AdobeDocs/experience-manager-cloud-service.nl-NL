---
title: Snel publiceren naar AEM en Dynamic Media
description: Met Snel publiceren in middelenweergave kunt u elementen gelijktijdig of afzonderlijk publiceren naar AEM en dynamische media. U kunt elementen en mappen selecteren en publiceren naar Dynamic Media of AEM.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
source-git-commit: 0891d58e10e8be746c0be5f55d554174567fcd64
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 0%

---

# Middelen publiceren naar AEM en Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

Met Experience Manager Assets kunt u snel elementen publiceren naar Experience Manager en Dynamic Media via de weergave Middelen. Zo beheert u uw elementen en publiceert u deze met [Weergave Middelen zonder over te schakelen op de beheerweergave](/help/assets/overview.md##persona-based-experiences).

De weergave Experience Manager Assets biedt de flexibiliteit om elementen tegelijkertijd naar AEM of Dynamic Media te publiceren. U kunt elementen publiceren tijdens het uploaden, bladeren en zoeken in elementen. Al deze opties voor het publiceren van elementen worden in dit artikel uitgebreid uitgelegd.

## Voordat u begint {#before-you-begin}

Configureer deze instellingen om de publicatieopties voor AEM en Dynamic Media weer te geven:

* Als u de publicatieopties voor Dynamic Media wilt weergeven, configureert u de volgende instellingen met de Admin-weergave:

   * [Een Dynamic Media-cloudconfiguratie maken](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Stel de Dynamic Media-publicatiemodus in op mapniveau. U kunt deze instellingen configureren tijdens het maken van de Dynamic Media-cloudconfiguratie. Als u deze instellingen op mapniveau wilt overschrijven, raadpleegt u [Selectieve publicatie op mapniveau in Dynamic Media configureren](/help/assets/dynamic-media/selective-publishing.md).

* Om de publicatieopties voor AEM te bekijken, moet u AEM vormen publiceert eindpunt voor uw milieu.

## Elementen publiceren tijdens uploaden {#piblish-assets-during-upload}

U kunt elementen publiceren naar AEM en Dynamic Media terwijl u elementen uploadt naar een map. De publicatieopties die worden weergegeven, zijn afhankelijk van de Dynamic Media-publicatiemodus die is ingesteld voor de map waarnaar de elementen worden geüpload. De Dynamic Media-publicatiemodus kan worden ingesteld op:

* **Bij activering:** Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat er een koppeling URL/Embed wordt opgegeven.

* **Direct:** Wanneer elementen naar deze map worden geüpload, worden de elementen door het systeem in de Experience Manager ingevoerd en wordt de URL/Embed onmiddellijk weergegeven.
* **Selectieve publicatie:** De activa worden gepubliceerd aan uw keuze van of Experience Manager of aan Dynamic Media voor levering in het openbare domein.

### Dynamic Media-publicatiemodus ingesteld op Na activering {#dynamic-media-publish-mode-set-to-upon-activation}

Elementen publiceren tijdens het uploaden naar een map met de Dynamic Media-publicatiemodus ingesteld op **Bij activering**:

1. Klikken **Elementen toevoegen** > **Bladeren** > **Door bestanden bladeren** om naar de juiste map te navigeren om elementen te uploaden. De **Publicatieopties** wordt de sectie weergegeven **DM-publicatiemodus** als **Bij activering**.
   ![Afbeelding uploaden na activering](/help/assets/assets/upload-upon-activation.png)
2. Selecteren **Publiceren naar AEM en Dynamic Media** en klik op **Uploaden**. De activa worden tegelijkertijd aan AEM en Dynamic Media gepubliceerd. Ga voor de bijgewerkte publicatiestatus voor deze elementen naar [Publicatiestatus controleren](#check-publish-status).

### Dynamic Media-publicatiemodus ingesteld op Direct {#dynamic-media-publish-mode-set-to-immediate}

Elementen publiceren tijdens het uploaden naar een map met de Dynamic Media-publicatiemodus ingesteld op **Meteen**:

1. Klikken **Elementen toevoegen** > **Bladeren** > **Door bestanden bladeren** om naar de juiste map te navigeren om elementen te uploaden. In het gedeelte Publicatieopties wordt het dialoogvenster **DM-publicatiemodus** als **Meteen**.
   ![bestandsupload afbeelding - directe modus](/help/assets/assets/upload-immediate-mode.png)
Als de Dynamic Media-publicatiemodus **Meteen** worden de geüploade elementen automatisch naar Dynamic Media gepubliceerd wanneer u op **Uploaden**.

2. Publiceren selecteren voor **AEM publiceren** de geüploade elementen die u wilt AEM en klik op Uploaden.

   Als u **Publiceren naar AEM** De activa worden gepubliceerd aan AEM en Dynamic Media, anders worden de activa gepubliceerd aan Dynamic Media.

   Ga voor de bijgewerkte publicatiestatus voor deze elementen naar [Publicatiestatus controleren](#check-publish-status).

### Dynamic Media-publicatiemodus ingesteld op Selectief publiceren {#dynamic-media-publish-mode-set-to-selective-publish}

Elementen publiceren tijdens het uploaden naar een map met de Dynamic Media-publicatiemodus ingesteld op **Selectieve publicatie**:

1. Klikken **Elementen toevoegen** > **Bladeren** > **Door bestanden bladeren** om naar de juiste map te navigeren om elementen te uploaden. In het gedeelte Publicatieopties wordt het gedeelte **DM-publicatiemodus** als **Selectieve publicatie**.
   ![afbeeldingsselectieve publicatiemodus uploaden](/help/assets/assets/upload-image-selective-publish-mode.png)

2. Selecteren **Publiceren naar AEM**, **Publiceren naar Dynamic Media**, of beide naar wens en klik op **Uploaden**.

   De middelen worden op basis van uw selectie gepubliceerd naar AEM en Dynamic Media.

   Ga voor de bijgewerkte publicatiestatus voor deze elementen naar [Publicatiestatus controleren](#check-publish-status).

## Elementen publiceren met middelenbladerpagina {#publish-assets-using-asset-browse-page}

Als u elementen wilt publiceren met behulp van het element, bladert u naar de pagina:

1. Klikken **Activa** in de **Elementbeheer** in het linkerdeelvenster beschikbaar.
2. Selecteer de middelen of mappen die u wilt publiceren en klik op **Publiceren**.
3. Selecteren **AEM** en klik op **Publiceren** om elementen te publiceren naar AEM en Dynamic Media.
   ![bestanden bladeren](/help/assets/assets/assets-browse-1.png)
U kunt geen map publiceren waarvoor de Dynamic Media-publicatiemodus is ingesteld op **Selectieve publicatie.** Alle andere geselecteerde mappen of elementen worden naar AEM en Dynamic Media gepubliceerd nadat u AEM hebt geselecteerd.
   ![bestanden bladeren](/help/assets/assets/assets-browse-2.png)

## Elementen publiceren met de pagina met zoekresultaten {#publish-assets-using-search-results-page}

Elementen publiceren met de pagina met zoekresultaten voor elementen:

1. Geef de criteria op in de zoekbalk en klik op het pictogram Zoeken om de resultaten weer te geven.
2. Selecteer de elementen die u wilt publiceren en klik op **Publiceren.**
3. Selecteer AEM, Dynamic Media of beide naar wens en klik op **Publiceren.**
   ![zoekafbeelding](/help/assets/assets/search-image1.png)
De optie om naar Dynamic Media te publiceren op de pagina met zoekresultaten is afhankelijk van de Dynamic Media-publicatiemodus die is ingesteld op de map waarin het element beschikbaar is in de gegevensopslagruimte.

   >[!NOTE]
   >
   >Als u een map selecteert en klikt op **Publiceren** op de pagina met zoekresultaten geeft Experience Manager Assets een optie weer voor het publiceren van middelen naar AEM en niet naar Dynamic Media, ongeacht de Dynamic Media-instellingen voor de publicatiemodus voor de map.

## Publicatiestatus controleren {#check-publish-status}

De publicatiestatus controleren op een middel of een map:

1. Klikken **[!UICONTROL Assets]** in de **[!UICONTROL Assets Management]** in het linkerdeelvenster beschikbaar.
2. Schakelaar aan de Mening van de Lijst gebruikend de Schakelaar van de Mening. U kunt de eigenschappen van elementen weergeven, zoals AEM Publiceren, Dynamic Media Publiceren, titel, grootte, afmetingen enzovoort.\
   Als een middel of een omslag niet wordt gepubliceerd, de status voor **AEM publiceren** en **Dynamic Media Publiceren** kolommen worden weergegeven als **Nvt.**
   ![publicatiestatus controleren1](/help/assets/assets/check-publish-status1.png)
Als u de kolommen AEM Publiceren en Dynamic Media publiceren niet kunt weergeven in de lijstweergave:
   1. Klikken ![instellingen](/help/assets/assets/settings-icon.svg) en selecteert u **AEM publiceren** en **Dynamic Media Publiceren** kolommen uit de **Configureerbare kolommen** in.
   2. Klikken **Bevestigen.** Experience Manager Assets voegt de geselecteerde kolommen toe aan de lijstweergave.

      ![publicatiestatus2 controleren](/help/assets/assets/check-publish-status2.png)

U kunt ook de publicatiestatus van een element controleren door een element te selecteren en op **Details.** De details zijn beschikbaar in het **Publiceren** in het rechterdeelvenster. De **Publiceren** wordt de datum weergegeven waarop de middelen naar Dynamic Media en AEM worden gepubliceerd. Als u de tijd moet bekijken waarop de elementen worden gepubliceerd, kunt u naar de lijstweergave navigeren en die details weergeven.

![publicatiestatus controleren 3](/help/assets/assets/check-publish-status3.png)

## Beperkingen {#limitations}

De volgende mogelijkheden zijn momenteel buiten bereik wanneer u middelen publiceert naar AEM en Dynamic Media:

* Publiceer middelen naar AEM en Dynamic Media vanaf de pagina met gegevens over middelen.
* Visualiseer de eindpunten waar de activa gepubliceerd worden gebruikend de Snelle Publish tovenaar.
* Voeg of verwijder meer elementen toe in de wizard Snel publiceren.
* Een pagina om gepubliceerde elementen weer te geven.
* De mogelijkheid om Dynamic Media URL te kopiëren of te plakken op elementniveau (als de elementen naar Dynamic Media worden gepubliceerd).
* De mogelijkheid om verwijzingen (elementen, tags, enzovoort) te publiceren tijdens het publiceren naar AEM.
* Mogelijkheid om de Dynamic Media-synchronisatiestatus op mapniveau te overschrijven.
* Mogelijkheid om de Dynamic Media-publicatiemodus te overschrijven op mapniveau
* Publicatie beheren wordt nog niet ondersteund.
