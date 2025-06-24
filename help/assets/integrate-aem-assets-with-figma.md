---
title: Integreer  [!DNL AEM Assets]  met  [!DNL Figma].
description: Leer om  [!DNL AEM Assets]  met  [!DNL Figma]  te integreren om tot de activa van uw organisatie binnen uw  [!DNL Figma]  ontwerpwerkschema toegang te hebben en te gebruiken.
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: 1d4dc40497113aded6abbf3d9a92b24f94f0b25b
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# [!DNL AEM Assets] integreren met [!DNL Figma]{#integrate-aem-assets-with-figma}

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

[!DNL AEM Assets] kan op een native manier worden geïntegreerd met [!DNL Figma] , zodat ontwerpers vanuit de gebruikersinterface van [!DNL Figma] rechtstreeks toegang hebben tot de elementen die zijn opgeslagen in [!DNL AEM Assets] . U kunt inhoud die wordt beheerd in [!DNL AEM Assets] plaatsen in het [!DNL Figma] canvas en vervolgens nieuwe of bewerkte inhoud opslaan in de [!DNL AEM Assets] -opslagruimte.

## Voordat u begint{#prerequisites-for-aem-assets-and-figma-integration}

* Minimaal vereiste AEM-releaseversie is `19149` .

* U moet geldige [!DNL AEM Assets] - en [!DNL Figma] -licenties hebben om [!DNL AEM Assets] te kunnen integreren met [!DNL Figma] .

## Toegang [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]{#access-aem-assets-connector}

Voer de volgende stappen uit om toegang te krijgen tot [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] :

1. Klik op de startpagina van [!DNL Figma] op **[!UICONTROL Actions]** op de werkbalk onder aan het canvas en zoek naar [!DNL Adobe Experience Manager (AEM) Assets Connector] op de zoekbalk in het dialoogvenster.
1. Selecteer [!DNL Adobe Experience Manager (AEM) Assets Connector] om het deelvenster [!DNL Adobe Experience Manager (AEM) Assets Connector] weer te geven.  [!DNL AEM]  activa van de Invoer [ &lbrace;in uw  [!DNL Figma]  canvas ](#import-aem-assets-into-figma-workflow) gebruikend dit paneel.
   ![ acties ](/help/assets/assets/actions-on-figma.png)
U kunt ook de [[!DNL Adobe Experience Manager (AEM) Assets Connector] ](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) beschikbare informatie over [!DNL Figma] -community openen, op **[!UICONTROL Open in...]** klikken, een recent bestand selecteren of een nieuw bestand maken en op **[!UICONTROL Run]** klikken om het deelvenster [!DNL Adobe Experience Manager (AEM) Assets Connector] te openen.
   ![ insteekmodule-pagina-op-beeld-gemeenschap ](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [ de Steun van Adobe van het Contact ](https://helpx.adobe.com/contact.html) voor hulp als u een **[!UICONTROL Network Error]** bericht na het programma openen aan uw [!DNL AEM] milieu ziet.

## [!DNL AEM] -elementen importeren in [!DNL Figma] canvas{#import-aem-assets-into-figma-workflow}

[ toegang [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] paneel ](#access-aem-assets-connector) binnen uw [!DNL Figma] ontwerpinterface en doe het volgende:

1. Zoeken naar elementen in het deelvenster [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] . Voor meer informatie, zie [ gebruikend de Selecteur van Activa ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Sleep het element naar het canvas of selecteer het element en klik op **[!UICONTROL Select]** om het element op het canvas te plaatsen.

1. Klik ![ drie punten ](/help/assets/assets/three-dots.svg) in de omslagweg om alle ouder en kindomslagen in de huidige hiërarchie te tonen. Selecteer een map om naar die locatie te navigeren.
   ![ drie punten ](/help/assets/assets/assets-folder-structure.png)

Zodra uw ontwerp van Cijfers klaar is, kunt u [ de activa naar de bewaarplaats van AEM Assets ](#export-figma-design-to-aem-assets-folder) uitvoeren.

## Elementen exporteren naar [!DNL AEM Assets] repository{#export-figma-design-to-aem-assets-folder}

[ toegang [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] paneel ](#access-aem-assets-connector) binnen uw [!DNL Figma] ontwerpinterface en voer de volgende stappen uit om uw ontwerp naar de [!DNL AEM Assets] bewaarplaats uit te voeren:

1. Navigeer naar de doelmap waarin u het [!DNL Figma] -ontwerp wilt opslaan. Als u reeds binnen een omslag bent, klik Meer opties (![ drie punten ](/help/assets/assets/three-dots.svg)) in de omslagweg om een verschillende bestemmingsomslag te selecteren.
1. Optioneel: groepeer elementen op het canvas om deze als één eenheid te selecteren en te uploaden in uw map.
1. Klik ![ dossier uploadt ](/help/assets/assets/upload-icon.svg) **[!UICONTROL Upload]** om de **[!UICONTROL Upload Asset]** dialoogdoos te tonen.
1. Geef in het dialoogvenster een bestandsnaam op, kies een bestandsindeling, selecteer **[!UICONTROL Selected Item]** of **[!UICONTROL Page]** en klik op **[!UICONTROL Upload]** om het geselecteerde element of het volledige ontwerp naar de doelmap te uploaden.
   ![ upload beeldontwerp ](/help/assets/assets/upload-figma-design.png)

## Belangrijke opmerkingen{#Limitations-of-using-aem-assets-into-figma}

Deze integratie kent momenteel de volgende beperkingen:

* Voor het invoeren van [!DNL AEM] activa in Cijfer, zijn de gesteunde formaten **JPEG**, **PNG**.
* Voor het uitvoeren van ontwerpen van [!DNL Figma] aan [!DNL AEM Assets], zijn de gesteunde formaten **PNG**, **PDF**, **JPG**, **SVG**.
