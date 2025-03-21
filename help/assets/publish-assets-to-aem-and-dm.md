---
title: Snel publiceren naar AEM en Dynamic Media
description: Met Snel publiceren in de weergave Assets kunt u elementen gelijktijdig of afzonderlijk publiceren naar AEM en Dynamic Media. U kunt elementen en mappen selecteren en publiceren naar Dynamic Media of AEM.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, Dynamic Media
role: User
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 0%

---

# Assets publiceren naar AEM en Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

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

Met Experience Manager Assets kunt u snel elementen publiceren naar Experience Manager en Dynamic Media met de Assets-weergave. Dit zorgt ervoor dat u uw activa beheert en dan hen publiceert gebruikend de [ mening van Assets zonder omschakeling aan de mening Admin ](/help/assets/overview.md##persona-based-experiences).

De Experience Manager Assets-weergave biedt de flexibiliteit om elementen tegelijkertijd te publiceren naar AEM of Dynamic Media. U kunt elementen publiceren tijdens het uploaden, bladeren en zoeken in elementen. Al deze opties voor het publiceren van elementen worden in dit artikel uitgebreid uitgelegd.

## Voordat u begint {#before-you-begin}

Configureer deze instellingen om de publicatieopties voor AEM en Dynamic Media weer te geven:

* Als u de publicatieopties voor dynamische media wilt weergeven, configureert u de volgende instellingen met de beheerweergave:

   * [ creeer een Dynamische configuratie van de Wolk van Media ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Stel de publicatiemodus Dynamische media in op mapniveau. U kunt deze instellingen configureren tijdens het maken van de Dynamic Media Cloud-configuratie. Om die montages op omslag-niveau te beschrijven, zie [ Selectief publiceren op het omslagniveau in Dynamische Media ](/help/assets/dynamic-media/selective-publishing.md) vormen.

* Als u de publicatieopties voor AEM wilt weergeven, moet u het AEM-eindpunt voor publicatie voor uw omgeving configureren.

## Assets publiceren tijdens uploaden {#piblish-assets-during-upload}

U kunt elementen publiceren naar AEM en Dynamic Media tijdens het uploaden van elementen naar een map. De publicatieopties die worden weergegeven, zijn afhankelijk van de publicatie-modusinstellingen van de map waarin de elementen worden geüpload. Dynamische media-publicatiemodus kan worden ingesteld op:

* **op activering:** wanneer de activa aan deze omslag worden geupload, moet u de activa eerst uitdrukkelijk publiceren alvorens een verbinding URL/Embed wordt verstrekt.

* **Onmiddellijk:** wanneer de activa aan deze omslag worden geupload, neemt het systeem de activa in Experience Manager op en verstrekt direct URL/Embed.
* **Selectief publiceren:** Assets wordt gepubliceerd aan uw keus van of Experience Manager of aan Dynamische Media voor levering in het openbare domein.

### Dynamische media publicatiemodus ingesteld op Na activering {#dynamic-media-publish-mode-set-to-upon-activation}

Om activa te publiceren terwijl het uploaden van hen aan een omslag de waarvan Dynamische Media publiceer Wijze aan **op Activering** wordt geplaatst:

1. Klik **toevoegen Assets** > **doorbladert** > **doorbladert Dossiers** om aan de aangewezen omslag te navigeren om activa te uploaden. De **publiceer opties** sectie toont **DM publiceer Wijze** als **op Activering**.
   ![ uploadt beeld op activering ](/help/assets/assets/upload-uactivation.svg)
2. Selecteer **publiceren aan AEM en Dynamische Media** en klik **uploaden**. De elementen worden tegelijkertijd gepubliceerd naar AEM en Dynamic Media. Om bijgewerkte te zien publiceer status voor deze activa, zie [ Controle publiceren status ](#check-publish-status).

### Dynamische media publicatiemodus ingesteld op Direct {#dynamic-media-publish-mode-set-to-immediate}

Om activa te publiceren terwijl het uploaden van hen aan een omslag waarvan de Dynamische Media publiceer Wijze aan **Onmiddellijk** wordt geplaatst:

1. Klik **toevoegen Assets** > **doorbladert** > **doorbladert Dossiers** om aan de aangewezen omslag te navigeren om activa te uploaden. De **publiceer opties** sectie toont **DM publiceer Wijze** als **Onmiddellijk**.
   ![ dossier uploadt beeld - directe wijze ](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Aangezien de Dynamische Media publiceer Wijze **onmiddellijk** is, worden de geuploade activa automatisch gepubliceerd aan Dynamische Media wanneer u **klikt uploadt**.

2. Selecteer **publiceren aan AEM** om de geuploade activa aan AEM te publiceren en Upload te klikken.

   Als u **uitgezocht publiceer aan AEM**, worden de activa gepubliceerd aan AEM en Dynamische Media, anders worden de activa gepubliceerd aan Dynamische Media.

   Om bijgewerkte te zien publiceer status voor deze activa, zie [ Controle publiceren status ](#check-publish-status).

### Dynamische media-publicatiemodus ingesteld op Selectief publiceren {#dynamic-media-publish-mode-set-to-selective-publish}

Om activa tijdens te publiceren upload aan een omslag met Dynamische Media publiceer Wijze die aan **wordt geplaatst Selectief publiceert**:

1. Klik **toevoegen Assets** > **doorbladert** > **doorbladert Dossiers** om aan de aangewezen omslag te navigeren om activa te uploaden. De **publiceer opties** sectie toont **DM publiceer Wijze** als **Selectief publiceren**.
   ![ uploadt beeld-selectieve het publiceren wijze ](/help/assets/assets/upload-selective.svg)

2. Selecteer **publiceren aan AEM**, **publiceren aan Dynamische Media**, of allebei volgens uw vereisten en klikken **uploadt**.

   De elementen worden op basis van uw selectie gepubliceerd naar AEM en Dynamic Media.

   Om bijgewerkte te zien publiceer status voor deze activa, zie [ Controle publiceren status ](#check-publish-status).

## Elementen publiceren met middelenbladerpagina {#publish-assets-using-asset-browse-page}

Als u elementen wilt publiceren met behulp van het element, bladert u naar de pagina:

1. Klik **Assets** in de **sectie van het Beheer van Assets** beschikbaar in de linkerruit.
2. Selecteer één of meerdere activa of omslagen die u moet publiceren en **klikken publiceren**.
3. Selecteer **AEM** en klik **publiceren** om activa aan AEM en Dynamische Media te publiceren.
   ![ activa doorbladeren ](/help/assets/assets/browse-uactivation-immediate.svg)
U kunt geen omslag publiceren die Dynamische Media heeft publiceer Wijze die aan **Selectief het Publiceren wordt geplaatst.** Alle andere geselecteerde mappen of elementen worden na het selecteren van AEM gepubliceerd naar AEM en Dynamic Media.
   ![ activa doorbladeren ](/help/assets/assets/browse-selective123.svg)

## Elementen publiceren met de pagina met zoekresultaten {#publish-assets-using-search-results-page}

Elementen publiceren met de pagina met zoekresultaten voor elementen:

1. Geef de criteria op in de zoekbalk en klik op het zoekpictogram om de resultaten weer te geven.
2. Selecteer de activa die u moet publiceren en **klikken publiceert.**
3. Selecteer AEM, Dynamische Media, of allebei volgens uw vereisten en klik **publiceren.**
   ![ onderzoeksbeeld ](/help/assets/assets/search-mode.svg)
De optie om naar Dynamic Media te publiceren op de pagina met zoekresultaten is afhankelijk van de Dynamic Media Publish-modus die is ingesteld op de map waarin het element beschikbaar is in de gegevensopslagruimte.

   >[!NOTE]
   >
   >Als u een omslag selecteert en **klikt publiceer** van de pagina van onderzoeksresultaten dan toont Experience Manager Assets een optie om activa aan AEM en niet Dynamische Media ongeacht de Dynamische montages van de Media te publiceren van de Wijze van de Media voor de omslag.

## Publicatiestatus controleren {#check-publish-status}

U kunt als volgt de gepubliceerde status voor een element of map controleren:

1. Klik op **[!UICONTROL Assets]** in de sectie **[!UICONTROL Assets Management]** in het linkerdeelvenster.
2. Schakel over naar de lijstweergave met behulp van de View Switcher. U kunt de eigenschappen van elementen weergeven, zoals AEM-publicatie, Dynamische media publiceren, titel, grootte, afmetingen enzovoort.\
   Als een activa of een omslag niet worden gepubliceerd, publiceert de status voor kolommen **AEM** en **Dynamische Media publiceren** wordt getoond als **N/A.**
   ![ controle publiceert status1 ](/help/assets/assets/check-publish-status1.png)
Als u de kolommen AEM Publiceren en Dynamische media publiceren niet kunt weergeven in de lijstweergave:
   1. Klik ![ montages ](/help/assets/assets/settings-icon.svg) en selecteer **AEM publiceren** en **Dynamische Media publiceren** kolommen van de **Configurable dialoog van Kolommen**.
   2. Klik **bevestigen.** Experience Manager Assets voegt de geselecteerde kolommen toe aan de lijstweergave.

      ![ controle publiceert status2 ](/help/assets/assets/check-publish-status2.png)

U kunt activa controleren publiceert status door activa te selecteren en **Details te klikken.** De details zijn beschikbaar in **publiceren** sectie beschikbaar in de juiste ruit. De **publiceer** sectie maakt een lijst van de datum wanneer de activa aan Dynamische Media en AEM worden gepubliceerd. Als u de tijd moet bekijken waarop de elementen worden gepubliceerd, kunt u naar de lijstweergave navigeren en die details weergeven.

![ controle publiceert status 3 ](/help/assets/assets/check-publish-status3.png)

## Beperkingen {#limitations}

De volgende mogelijkheden zijn momenteel buiten bereik wanneer u middelen publiceert naar AEM en Dynamic Media:

* Publiceer middelen naar AEM en Dynamic Media vanaf de pagina met de gegevens over middelen.
* Visualiseer de eindpunten waar de activa gebruikend de Snelle Publish tovenaar worden gepubliceerd.
* Voeg of verwijder meer elementen toe in de wizard Snel publiceren.
* Een pagina om gepubliceerde elementen weer te geven.
* De mogelijkheid om dynamische media-URL op elementniveau te kopiëren of te plakken (als de elementen zijn gepubliceerd naar dynamische media).
* De mogelijkheid om verwijzingen (elementen, tags, enzovoort) te publiceren tijdens het publiceren naar AEM.
* Mogelijkheid om de synchronisatie van dynamische media op mapniveau te overschrijven.
* Mogelijkheid om de publicatiemodus Dynamische media te overschrijven op mapniveau
* Publicatie beheren wordt nog niet ondersteund.
