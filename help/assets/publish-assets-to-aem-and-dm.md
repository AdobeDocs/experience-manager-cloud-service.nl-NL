---
title: Snel publiceren naar  [!DNL AEM and Dynamic Media]
description: Snel publiceert in  [!DNL Assets view]  laat u toe om activa aan  [!DNL AEM and Dynamic Media]  gelijktijdig of afzonderlijk te publiceren. U kunt activa en omslagen selecteren en verkiezen om aan  [!DNL Dynamic Media]  of  [!DNL AEM] te publiceren.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, [!DNL Dynamic Media]
role: User
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---

# Assets publiceren naar [!DNL AEM and Dynamic Media]{#Publish-Assets-to-AEM-and-Dynamic-Media}

Met [!DNL Experience Manager Assets] kunt u snel elementen publiceren naar [!DNL Experience Manager] en [!DNL Dynamic Media] met [!DNL Assets view] . Dit zorgt ervoor dat u uw activa beheert en dan hen publiceert gebruikend [[!DNL Assets view]  zonder omschakeling aan  [!DNL Admin view]](/help/assets/overview.md##persona-based-experiences).

[!DNL Experience Manager Assets view] biedt de flexibiliteit om elementen tegelijkertijd te publiceren naar [!DNL AEM] of [!DNL Dynamic Media] , of beide. U kunt elementen publiceren tijdens het uploaden, bladeren en zoeken in elementen. Al deze opties voor het publiceren van elementen worden in dit artikel uitgebreid uitgelegd.

## Voordat u begint {#before-you-begin}

Configureer deze instellingen om de publicatieopties voor [!DNL AEM and Dynamic Media] weer te geven:

* Als u de publicatieopties voor [!DNL Dynamic Media] wilt weergeven, configureert u de volgende instellingen met de beheerweergave:

   * [&#x200B; creeer de configuratie van de a [!DNL Dynamic Media]  Wolk &#x200B;](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Stel de publicatiemodus [!DNL Dynamic Media] in op mapniveau. U kunt deze instellingen configureren tijdens het maken van de [!DNL Dynamic Media] Cloud-configuratie. Om die montages op omslag-niveau te beschrijven, zie [&#x200B; Selectief publiceren op het omslagniveau in  [!DNL Dynamic Media]](/help/assets/dynamic-media/selective-publishing.md) vormen.

* Als u de publicatieopties voor [!DNL AEM] wilt weergeven, moet u het [!DNL AEM] -eindpunt voor de omgeving configureren.

## Assets publiceren tijdens uploaden {#piblish-assets-during-upload}

U kunt elementen naar [!DNL AEM and Dynamic Media] publiceren tijdens het uploaden van elementen naar een map. De publicatieopties die worden weergegeven, zijn afhankelijk van de instellingen in de publicatiemodus [!DNL Dynamic Media] van de map waarin de elementen worden geüpload. [!DNL Dynamic Media] -publicatiemodus kan worden ingesteld op:

* **[!UICONTROL Upon activaton]:** Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat een koppeling URL/Embed wordt opgegeven.

* **[!UICONTROL Immediate]:** Wanneer elementen naar deze map worden geüpload, voert het systeem de elementen in Experience Manager in en wordt de URL/Embed onmiddellijk weergegeven.
* **[!UICONTROL Selective Publish]:** Assets worden gepubliceerd naar keuze van [!DNL Experience Manager] of [!DNL Dynamic Media] voor levering in het publieke domein.

### [!UICONTROL Dynamic Media Publish Mode] ingesteld op [!UICONTROL Upon Activation] {#dynamic-media-publish-mode-set-to-upon-activation}

Elementen publiceren tijdens het uploaden naar een map waarvan [!DNL Dynamic Media Publish Mode] is ingesteld op **[!UICONTROL Upon Activation]** :

1. Klik op **[!UICONTROL Add Assets]** > **[!UICONTROL Browse]** > **[!UICONTROL Browse Files]** om naar de juiste map te navigeren om elementen te uploaden. In de sectie **[!UICONTROL Publish Options]** wordt **[!UICONTROL DM Publish Mode]** as **[!UICONTROL Upon Activation]** weergegeven.
   ![&#x200B; uploadt beeld op activering &#x200B;](/help/assets/assets/upload-uactivation.svg)
2. Selecteer **[!UICONTROL Publish to AEM and Dynamic Media]** en klik op **[!UICONTROL Upload]** . De elementen worden tegelijkertijd gepubliceerd naar [!DNL AEM and Dynamic Media] . Om bijgewerkte te zien publiceer status voor deze activa, zie [&#x200B; Controle publiceren status &#x200B;](#check-publish-status).

### [!UICONTROL Dynamic Media Publish Mode] ingesteld op [!UICONTROL Immediate] {#dynamic-media-publish-mode-set-to-immediate}

Elementen publiceren tijdens het uploaden naar een map waarvan [!UICONTROL Dynamic Media Publish Mode] is ingesteld op **[!UICONTROL Immediate]** :

1. Klik op **[!UICONTROL Add Assets]** > **[!UICONTROL Browse]** > **[!UICONTROL Browse Files]** om naar de juiste map te navigeren om elementen te uploaden. In de sectie **[!UICONTROL Publish Options]** wordt **[!UICONTROL DM Publish Mode]** as **[!UICONTROL Immediate]** weergegeven.
   ![&#x200B; dossier uploadt beeld - directe wijze &#x200B;](/help/assets/assets/resized-image-pdf-svg-new.svg)
Aangezien [!UICONTROL Dynamic Media Publish Mode] **[!UICONTROL Immediate]** is, worden de geüploade activa automatisch gepubliceerd aan [!DNL Dynamic Media] wanneer u **[!UICONTROL Upload]** klikt.

2. Selecteer **publiceren aan AEM** om de geuploade activa aan [!DNL AEM] te publiceren en **[!UICONTROL Upload]** te klikken.

   Als u **uitgezocht publiceer aan AEM**, worden de activa gepubliceerd aan [!DNL AEM and Dynamic Media], anders worden de activa gepubliceerd aan [!DNL Dynamic Media].

   Om bijgewerkte te zien publiceer status voor deze activa, zie [&#x200B; Controle publiceren status &#x200B;](#check-publish-status).

### [!UICONTROL Dynamic Media Publish Mode] ingesteld op [!UICONTROL Selective Publish] {#dynamic-media-publish-mode-set-to-selective-publish}

Elementen publiceren tijdens het uploaden naar een map met [!UICONTROL Dynamic Media Publish Mode] ingesteld op **[!UICONTROL Selective Publish]** :

1. Klik op **[!UICONTROL Add Assets]** > **[!UICONTROL Browse]** > **[!UICONTROL Browse Files]** om naar de juiste map te navigeren om elementen te uploaden. In de sectie **[!UICONTROL Publish Options]** wordt **[!UICONTROL DM Publish Mode]** as **[!UICONTROL Selective Publish]** weergegeven.
   ![&#x200B; uploadt beeld-selectieve het publiceren wijze &#x200B;](/help/assets/assets/upload-selective.svg)

2. Selecteer **[!UICONTROL Publish to AEM]**, **[!UICONTROL Publish to Dynamic Media]**, of allebei volgens uw vereisten en klik **uploaden**.

   De elementen worden gepubliceerd naar [!DNL AEM and Dynamic Media] op basis van uw selectie.

   Om bijgewerkte te zien publiceer status voor deze activa, zie [&#x200B; Controle publiceren status &#x200B;](#check-publish-status).

## Elementen publiceren met middelenbladerpagina {#publish-assets-using-asset-browse-page}

Als u elementen wilt publiceren met behulp van het element, bladert u naar de pagina:

1. Klik op **[!UICONTROL Assets]** in de sectie **[!UICONTROL Assets Management]** in het linkerdeelvenster.
2. Selecteer een of meer elementen of mappen die u wilt publiceren en klik op **[!UICONTROL Publish]** .
3. Selecteer **[!UICONTROL AEM]** en klik op **[!UICONTROL Publish]** om elementen te publiceren naar [!DNL AEM and Dynamic Media] .
   ![&#x200B; activa doorbladeren &#x200B;](/help/assets/assets/browse-uactivation-immediate.svg)
U kunt geen map publiceren waarvoor de publicatiemodus [!DNL Dynamic Media] is ingesteld op **[!UICONTROL Selective Publishing]** . Alle andere geselecteerde mappen of elementen worden gepubliceerd naar [!DNL AEM and Dynamic Media] nadat u [!DNL AEM] hebt geselecteerd.
   ![&#x200B; activa doorbladeren &#x200B;](/help/assets/assets/browse-selective123.svg)

## Elementen publiceren met de pagina met zoekresultaten {#publish-assets-using-search-results-page}

Elementen publiceren met de pagina met zoekresultaten voor elementen:

1. Geef de criteria op in de zoekbalk en klik op het zoekpictogram om de resultaten weer te geven.
2. Selecteer de elementen die u wilt publiceren en klik op **[!UICONTROL Publish].**
3. Selecteer [!DNL AEM, Dynamic Media] of beide naar wens en klik op **[!UICONTROL Publish]** .
   ![&#x200B; onderzoeksbeeld &#x200B;](/help/assets/assets/search-mode.svg)
De optie om naar [!DNL Dynamic Media] te publiceren op de pagina met zoekresultaten is afhankelijk van de [!DNL Dynamic Media] publicatiemodus die is ingesteld op de map waarin het element beschikbaar is in de gegevensopslagruimte.
   >[!NOTE]
   >
   >Als u een map selecteert en op **[!UICONTROL Publish]** klikt op de pagina met zoekresultaten, geeft [!DNL Experience Manager Assets] een optie weer om elementen naar [!DNL AEM] te publiceren en niet [!DNL Dynamic Media] ongeacht de instellingen voor de publicatiemodus van de map. [!DNL Dynamic Media]

## Publicatiestatus controleren {#check-publish-status}

U kunt als volgt de gepubliceerde status voor een element of map controleren:

1. Klik op **[!UICONTROL Assets]** in de sectie **[!UICONTROL Assets Management]** in het linkerdeelvenster.
2. Schakel over naar de lijstweergave met behulp van de View Switcher. U kunt eigenschappen van elementen weergeven, zoals [!UICONTROL AEM publish] , [!UICONTROL Dynamic Media Publish] , [!UICONTROL title] , [!UICONTROL size] , [!UICONTROL dimensions] , enzovoort.\
   Als een element of map niet is gepubliceerd, wordt de status voor kolommen **[!UICONTROL AEM Publish]** en **[!UICONTROL Dynamic Media Publish]** weergegeven als **[!UICONTROL N/A]** .
   ![&#x200B; controle publiceert status1 &#x200B;](/help/assets/assets/check-publish-status1.png)
Als u de kolommen [!DNL AEM] Publiceren en [!DNL Dynamic Media] Publiceren niet kunt weergeven in de lijstweergave:
   1. Klik ![&#x200B; montages &#x200B;](/help/assets/assets/settings-icon.svg) en selecteer **[!UICONTROL AEM Publish]** en **[!UICONTROL Dynamic Media Publish]** kolommen van de **[!UICONTROL Configurable Columns]** dialoog.
   2. Klik op **[!UICONTROL Confirm]**. [!DNL Experience Manager Assets] voegt de geselecteerde kolommen toe aan de lijstweergave.

      ![&#x200B; controle publiceert status2 &#x200B;](/help/assets/assets/check-publish-status2.png)

U kunt de publicatiestatus van een element ook controleren door een element te selecteren en op **[!UICONTROL Details]** te klikken. De details zijn beschikbaar in de sectie **[!UICONTROL Publish]** in het rechterdeelvenster. De sectie **[!UICONTROL Publish]** bevat de datum waarop de elementen worden gepubliceerd naar [!DNL Dynamic Media] en [!DNL AEM] . Als u de tijd moet bekijken waarop de elementen worden gepubliceerd, kunt u naar de lijstweergave navigeren en die details weergeven.

![&#x200B; controle publiceert status 3 &#x200B;](/help/assets/assets/check-publish-status3.png)

## Beperkingen {#limitations}

De volgende mogelijkheden zijn voorlopig buiten bereik wanneer u elementen publiceert naar [!DNL AEM and Dynamic Media] :

* Publiceer elementen naar [!DNL AEM and Dynamic Media] vanuit de [!DNL Asset details page] .
* Visualiseer de eindpunten waar de activa gebruikend de Snelle Publish tovenaar worden gepubliceerd.
* Voeg of verwijder meer elementen toe in de wizard Snel publiceren.
* Een pagina om gepubliceerde elementen weer te geven.
* De mogelijkheid om [!DNL Dynamic Media] URL te kopiëren of te plakken op elementniveau (als de elementen naar [!DNL Dynamic Media] worden gepubliceerd).
* De mogelijkheid om verwijzingen (elementen, tags, enzovoort) te publiceren wanneer u publiceert naar [!DNL AEM] .
* Mogelijkheid om de synchronisatiestatus van [!DNL Dynamic Media] op mapniveau te overschrijven.
* Mogelijkheid om de publicatiemodus [!DNL Dynamic Media] te overschrijven op mapniveau
* Publicatie beheren wordt nog niet ondersteund.
