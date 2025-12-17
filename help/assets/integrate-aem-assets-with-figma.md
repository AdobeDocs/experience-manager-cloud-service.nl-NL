---
title: Integreer  [!DNL AEM Assets]  met  [!DNL Figma].
description: Leer om  [!DNL AEM Assets]  met  [!DNL Figma]  te integreren om tot de activa van uw organisatie binnen uw  [!DNL Figma]  ontwerpwerkschema toegang te hebben en te gebruiken.
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: a9c1f5472092b3b9fa7a5e5570feb92f32e9ef6c
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# [!DNL AEM Assets] integreren met [!DNL Figma]{#integrate-aem-assets-with-figma}

[!DNL AEM Assets] kan op een native manier worden geïntegreerd met [!DNL Figma] , zodat ontwerpers vanuit de gebruikersinterface van [!DNL AEM Assets] rechtstreeks toegang hebben tot de elementen die zijn opgeslagen in [!DNL Figma] . U kunt inhoud die wordt beheerd in [!DNL AEM Assets] plaatsen in het [!DNL Figma] canvas en vervolgens nieuwe of bewerkte inhoud opslaan in de [!DNL AEM Assets] -opslagruimte.

## Voordat u begint{#prerequisites-for-aem-assets-and-figma-integration}

* Minimaal vereiste AEM-releaseversie is `19149` .

* U moet geldige [!DNL AEM Assets] - en [!DNL Figma] -licenties hebben om [!DNL AEM Assets] te kunnen integreren met [!DNL Figma] .

## Ondersteunde bestandsindelingen {#supported-file-formats-integration-figma}


* Voor het importeren van [!DNL AEM] -elementen in Figma zijn de ondersteunde indelingen afbeeldingselementen (JPEG, PNG), videobestanden (MP4, MOV, WebM), Geanimeerde bestanden (GIF) en Vectorbestanden (SVG).
* Voor het uitvoeren van ontwerpen van [!DNL Figma] aan [!DNL AEM Assets], zijn de gesteunde formaten **PNG**, **PDF**, **JPG**, **SVG**.

## Toegang [!UICONTROL Adobe Experience Manager (AEM) Assets Connector]{#access-aem-assets-connector}

Voer de volgende stappen uit om toegang te krijgen tot [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] :

1. Klik op de startpagina van [!DNL Figma] op **[!UICONTROL Actions]** op de werkbalk onder aan het canvas en zoek naar [!DNL Adobe Experience Manager (AEM) Assets Connector] op de zoekbalk in het dialoogvenster.
1. Selecteer [!DNL Adobe Experience Manager (AEM) Assets Connector] om het deelvenster [!DNL Adobe Experience Manager (AEM) Assets Connector] weer te geven. [&#x200B; activa van de Invoer  [!DNL AEM]  &lbrace;in uw  [!DNL Figma]  canvas &#x200B;](#import-aem-assets-into-figma-workflow) gebruikend dit paneel.
   ![&#x200B; acties &#x200B;](/help/assets/assets/actions-on-figma.png)
U kunt ook de [[!DNL Adobe Experience Manager (AEM) Assets Connector] &#x200B;](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) beschikbare informatie over [!DNL Figma] -community openen, op **[!UICONTROL Open in...]** klikken, een recent bestand selecteren of een nieuw bestand maken en op **[!UICONTROL Run]** klikken om het deelvenster [!DNL Adobe Experience Manager (AEM) Assets Connector] te openen.
   ![&#x200B; insteekmodule-pagina-op-beeld-gemeenschap &#x200B;](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [&#x200B; de Steun van Adobe van het Contact &#x200B;](https://helpx.adobe.com/contact.html) voor hulp als u een **[!UICONTROL Network Error]** bericht na het programma openen aan uw [!DNL AEM] milieu ziet.

## [!DNL AEM] -elementen importeren in [!DNL Figma] canvas{#import-aem-assets-into-figma-workflow}

[&#x200B; toegang [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] paneel &#x200B;](#access-aem-assets-connector) binnen uw [!DNL Figma] ontwerpinterface en doe het volgende:

1. Zoeken naar elementen in het deelvenster [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] . Voor meer informatie, zie [&#x200B; gebruikend de Selecteur van Activa &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Sleep het element naar het canvas of selecteer het element en klik op **[!UICONTROL Select]** om het element op het canvas te plaatsen.

1. Klik ![&#x200B; drie punten &#x200B;](/help/assets/assets/three-dots.svg) in de omslagweg om alle ouder en kindomslagen in de huidige hiërarchie te tonen. Selecteer een map om naar die locatie te navigeren.
   ![&#x200B; drie punten &#x200B;](/help/assets/assets/figma-v2-plugin.png)

1. [ Facultatieve ] klik **[!UICONTROL Check for updates]**. De elementen die in het huidige Figma-document worden gebruikt, worden vergeleken met de elementen in AEM. Alle updates worden weergegeven in een apart venster. Klik op **[!UICONTROL Update]** om het bijgewerkte element van AEM in uw Figma-document te plaatsen.

Zodra uw ontwerp van Cijfers klaar is, kunt u [&#x200B; de activa naar de bewaarplaats van AEM Assets &#x200B;](#export-figma-design-to-aem-assets-folder) uitvoeren.

## Elementen exporteren naar [!DNL AEM Assets] repository{#export-figma-design-to-aem-assets-folder}

[&#x200B; toegang [!UICONTROL Adobe Experience Manager (AEM) Assets Connector] paneel &#x200B;](#access-aem-assets-connector) binnen uw [!DNL Figma] ontwerpinterface en voer de volgende stappen uit om uw ontwerp naar de [!DNL AEM Assets] bewaarplaats uit te voeren:

1. Navigeer naar de doelmap waarin u het [!DNL Figma] -ontwerp wilt opslaan. Als u reeds binnen een omslag bent, klik Meer opties (![&#x200B; drie punten &#x200B;](/help/assets/assets/three-dots.svg)) in de omslagweg om een verschillende bestemmingsomslag te selecteren.
1. Optioneel: groepeer elementen op het canvas om deze als één eenheid te selecteren en te uploaden in uw map.
1. Klik ![&#x200B; dossier uploadt &#x200B;](/help/assets/assets/upload-icon.svg) **[!UICONTROL Upload]** om de **[!UICONTROL Upload Asset]** dialoogdoos te tonen.
1. Selecteer **[!UICONTROL Selected Item]** of **[!UICONTROL Page]** in het dialoogvenster, geef een bestand- of paginanaam op, definieer een exportconfiguratie en klik op **[!UICONTROL Upload]** om het geselecteerde element of het volledige ontwerp naar de doelmap te uploaden.

   De exportconfiguratie bestaat uit de bestandsindeling, schaal en kwaliteit. Als u bijvoorbeeld JPG selecteert als bestandsindeling, kunt u ook de schaal en kwaliteit van de afbeelding definiëren. Als u PNG selecteert als bestandsindeling, kunt u ook de afbeeldingsschaal definiëren.
   ![&#x200B; upload beeldontwerp &#x200B;](/help/assets/assets/upload-figma-design.png)
