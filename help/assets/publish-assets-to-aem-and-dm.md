---
title: Quick Publish to AEM and Dynamic Media
description: Met Quick Publish in Assets-weergave kunt u elementen gelijktijdig of afzonderlijk publiceren naar AEM en Dynamic Media. U kunt elementen en mappen selecteren en publiceren naar Dynamic Media of AEM.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, Dynamic Media
role: User
source-git-commit: 991888d532b3396054bd04c11c7257b61c337725
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Publish Assets naar AEM en Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Met Experience Manager Assets kunt u snel elementen publiceren naar Experience Manager en Dynamic Media met de Assets-weergave. Dit zorgt ervoor dat u uw activa beheert en dan hen publiceert gebruikend de [ mening van Assets zonder omschakeling aan de mening Admin ](/help/assets/overview.md##persona-based-experiences).

De weergave Experience Manager Assets biedt de flexibiliteit om elementen tegelijkertijd naar AEM of Dynamic Media te publiceren. U kunt elementen publiceren tijdens het uploaden, bladeren en zoeken in elementen. Al deze opties voor het publiceren van elementen worden in dit artikel uitgebreid uitgelegd.

## Voordat u begint {#before-you-begin}

Configureer deze instellingen om de publicatieopties voor AEM en Dynamic Media weer te geven:

* Als u de publicatieopties voor Dynamic Media wilt weergeven, configureert u de volgende instellingen in de beheerweergave:

   * [ creeer een configuratie van de Wolk van Dynamic Media ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Stel de Dynamic Media Publish-modus in op mapniveau. U kunt deze instellingen ook configureren tijdens het maken van de Dynamic Media Cloud-configuratie. Om die montages op omslag-niveau te beschrijven, zie [ Selectieve Publish op het omslagniveau in Dynamic Media ](/help/assets/dynamic-media/selective-publishing.md) vormen.

* Als u de publicatieopties voor AEM wilt weergeven, moet u het AEM voor uw omgeving configureren.

## Publish Assets tijdens uploaden {#piblish-assets-during-upload}

U kunt elementen publiceren naar AEM en Dynamic Media terwijl u elementen uploadt naar een map. De publicatieopties die worden weergegeven, zijn afhankelijk van de Dynamic Media-instellingen in de publicatiemodus van de map waarin de elementen worden geüpload. De Dynamic Media-publicatiemodus kan worden ingesteld op:

* **op activering:** wanneer de activa aan deze omslag worden geupload, moet u de activa eerst uitdrukkelijk publiceren alvorens een verbinding URL/Embed wordt verstrekt.

* **Onmiddellijk:** wanneer de activa aan deze omslag worden geupload, neemt het systeem de activa in Experience Manager op en verstrekt direct URL/bedt.
* **Selectieve Publish:** Assets wordt gepubliceerd aan uw keus van of Experience Manager of aan Dynamic Media voor levering in het openbare domein.

### Dynamic Media Publish-modus ingesteld op Na activering {#dynamic-media-publish-mode-set-to-upon-activation}

Om activa te publiceren terwijl het uploaden van hen aan een omslag de waarvan Wijze van Dynamic Media Publish aan **op Activering** wordt geplaatst:

1. Klik **toevoegen Assets** > **doorbladert** > **doorbladert Dossiers** om aan de aangewezen omslag te navigeren om activa te uploaden. De **opties van Publish** sectie toont de **Wijze van Publish DM** als **op Activering**.
   ![ uploadt beeld op activering ](/help/assets/assets/upload-uactivation.svg)
2. Selecteer **Publish aan AEM en Dynamic Media** en klik **uploaden**. De activa worden tegelijkertijd aan AEM en Dynamic Media gepubliceerd. Om bijgewerkte te zien publiceer status voor deze activa, zie [ de status van Publish van de Controle ](#check-publish-status).

### Dynamic Media Publish-modus ingesteld op Direct {#dynamic-media-publish-mode-set-to-immediate}

Om activa te publiceren terwijl het uploaden van hen aan een omslag waarvan de Wijze van Dynamic Media Publish aan **Onmiddellijk** wordt geplaatst:

1. Klik **toevoegen Assets** > **doorbladert** > **doorbladert Dossiers** om aan de aangewezen omslag te navigeren om activa te uploaden. De **opties van Publish** sectie toont de **Wijze van Publish DM** als **Onmiddellijk**.
   ![ dossier uploadt beeld - directe wijze ](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Aangezien de Wijze van Dynamic Media Publish **Onmiddellijk** is, worden de geuploade activa automatisch gepubliceerd aan Dynamic Media wanneer u **klikt uploadt**.

2. Selecteer **Publish aan AEM** om de geuploade activa aan AEM te publiceren en Upload te klikken.

   Als u **Publish aan AEM** selecteert, worden de activa gepubliceerd aan AEM en Dynamic Media, anders worden de activa gepubliceerd aan Dynamic Media.

   Om bijgewerkte te zien publiceer status voor deze activa, zie [ de status van Publish van de Controle ](#check-publish-status).

### Dynamic Media Publish Mode ingesteld op Selective Publish {#dynamic-media-publish-mode-set-to-selective-publish}

Om activa tijdens te publiceren upload aan een omslag met de Wijze die van Dynamic Media Publish aan **Selectieve Publish** wordt geplaatst:

1. Klik **toevoegen Assets** > **doorbladert** > **doorbladert Dossiers** om aan de aangewezen omslag te navigeren om activa te uploaden. De **opties van Publish** sectie toont de **Wijze van Publish DM** als **Selectieve Publish**.
   ![ uploadt beeld-selectieve het publiceren wijze ](/help/assets/assets/upload-selective.svg)

2. Selecteer **Publish aan AEM**, **Publish aan Dynamic Media**, of allebei zoals per uw vereisten en klik **uploaden**.

   De middelen worden op basis van uw selectie gepubliceerd naar AEM en Dynamic Media.

   Om bijgewerkte te zien publiceer status voor deze activa, zie [ de status van Publish van de Controle ](#check-publish-status).

## Publish-elementen met middelenbladerpagina {#publish-assets-using-asset-browse-page}

Als u elementen wilt publiceren met behulp van het element, bladert u naar de pagina:

1. Klik **Assets** in de **sectie van het Beheer van Assets** beschikbaar in de linkerruit.
2. Selecteer één of meerdere activa of omslagen die u moet publiceren en **Publish** klikken.
3. Selecteer **AEM** en klik **Publish** om activa aan AEM en Dynamic Media te publiceren.
   ![ activa doorbladeren ](/help/assets/assets/browse-uactivation-immediate.svg)
U kunt geen omslag publiceren die de Wijze heeft van Dynamic Media Publish die aan **Selectief het Publiceren wordt geplaatst.** Alle andere geselecteerde mappen of elementen worden na het selecteren van AEM gepubliceerd naar AEM en Dynamic Media.
   ![ activa doorbladeren ](/help/assets/assets/browse-selective123.svg)

## Publish-elementen met de pagina met zoekresultaten {#publish-assets-using-search-results-page}

Elementen publiceren met de pagina met zoekresultaten voor elementen:

1. Geef de criteria op in de zoekbalk en klik op het zoekpictogram om de resultaten weer te geven.
2. Selecteer de activa die u moet publiceren en **Publish klikken.**
3. Selecteer AEM, Dynamic Media, of allebei volgens uw vereisten en klik **Publish.**
   ![ onderzoeksbeeld ](/help/assets/assets/search-mode.svg)
De optie om naar Dynamic Media te publiceren op de pagina met zoekresultaten is afhankelijk van de Dynamic Media Publish-modus die is ingesteld op de map waarin het element beschikbaar is in de opslagplaats.

   >[!NOTE]
   >
   >Als u een omslag selecteert en **Publish** van de pagina van onderzoeksresultaten klikt dan toont Experience Manager Assets een optie om activa aan AEM en niet Dynamic Media ongeacht de montages van de Wijze van Dynamic Media Publish voor de omslag te publiceren.

## Publish-status controleren {#check-publish-status}

U kunt als volgt de gepubliceerde status voor een element of map controleren:

1. Klik op **[!UICONTROL Assets]** in de sectie **[!UICONTROL Assets Management]** in het linkerdeelvenster.
2. Schakel over naar de lijstweergave met behulp van de View Switcher. U kunt de eigenschappen van elementen weergeven, zoals AEM publiceren, Dynamic Media Publish, titel, grootte, afmetingen enzovoort.\
   Als een activa of een omslag niet worden gepubliceerd, wordt de status voor kolommen **AEM Publish** en **Dynamic Media Publish** getoond als **N/A.**
   ![ controle publiceert status1 ](/help/assets/assets/check-publish-status1.png)
Als u de kolommen AEM Publish en Dynamic Media Publish niet kunt weergeven in de lijstweergave:
   1. Klik ![ montages ](/help/assets/assets/settings-icon.svg) en selecteer **AEM Publish** en **Publish van Dynamic Media** kolommen van de **Configurable dialoog van Kolommen**.
   2. Klik **bevestigen.** Experience Manager Assets voegt de geselecteerde kolommen toe aan de lijstweergave.

      ![ controle publiceert status2 ](/help/assets/assets/check-publish-status2.png)

U kunt activa controleren publiceert status door activa te selecteren en **Details te klikken.** De details zijn beschikbaar in de **Publish** sectie beschikbaar in de juiste ruit. De **Publish** sectie maakt een lijst van de datum wanneer de activa aan Dynamic Media en AEM worden gepubliceerd. Als u de tijd moet bekijken waarop de elementen worden gepubliceerd, kunt u naar de lijstweergave navigeren en die details weergeven.

![ controle publiceert status 3 ](/help/assets/assets/check-publish-status3.png)

## Beperkingen {#limitations}

De volgende mogelijkheden zijn momenteel buiten bereik wanneer u middelen publiceert naar AEM en Dynamic Media:

* Publish-middelen naar AEM en Dynamic Media vanaf de pagina met gegevens over middelen.
* Visualiseer de eindpunten waar de activa gebruikend de Snelle tovenaar van Publish worden gepubliceerd.
* Voeg of verwijder meer elementen toe aan de wizard Quick Publish.
* Een pagina om gepubliceerde elementen weer te geven.
* De mogelijkheid om Dynamic Media URL te kopiëren of te plakken op elementniveau (als de elementen naar Dynamic Media worden gepubliceerd).
* De mogelijkheid om verwijzingen (elementen, tags, enzovoort) te publiceren tijdens het publiceren naar AEM.
* Mogelijkheid om de Dynamic Media-synchronisatiestatus op mapniveau te overschrijven.
* Mogelijkheid om de Dynamic Media Publish-modus op mapniveau te overschrijven
* Publicatie beheren wordt nog niet ondersteund.
