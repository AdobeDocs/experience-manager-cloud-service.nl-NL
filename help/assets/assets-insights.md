---
title: 'Asset Insights '
description: Leer hoe u met de functie Asset Insights gebruikersbeoordelingen en gebruiksstatistieken kunt bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van Adobe.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 2%

---


# Asset Insights {#asset-insights}

Asset Insights houdt gebruikersbeoordelingen en gebruiksstatistieken bij van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van Adobe. Hierdoor krijgt u meer inzicht in de prestaties en de populariteit van de afbeeldingen.

Met Elementinzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keer dat een afbeelding wordt beoordeeld, geklikt en afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Als u met behulp van Assets gebruiksstatistieken wilt vastleggen voor afbeeldingen van een website, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Als u het gebruik van bedrijfsgegevens voor elementen wilt laten weergeven, configureert u eerst de functie voor het ophalen van rapportgegevens van Adobe Analytics. Zie [Elementinzichten](#configure-asset-insights)configureren voor meer informatie.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

## Statistieken voor een afbeelding weergeven {#viewing-statistics-for-an-image}

U kunt de Asset Insights-scores van de metagegevenspagina weergeven.

1. Selecteer de afbeelding in de gebruikersinterface Elementen (UI) en tik vervolgens op **[!UICONTROL Properties]** de werkbalk.
1. Tik op de pagina Eigenschappen **[!UICONTROL Insights]**.
1. Controleer de gebruiksdetails voor het element op het **[!UICONTROL Insights]** tabblad. In de **[!UICONTROL Score]** sectie worden het totale gebruik en de prestatiesbronnen van een element beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL Impressions]** score is het aantal keren dat het element op de website wordt geladen. Het getal dat onder **[!UICONTROL Clicks]** wordt weergegeven, is het aantal keren dat op het element wordt geklikt.

1. Controleer de **[!UICONTROL Usage Statistics]** sectie om te weten bij welke entiteiten het actief hoort en welke creatieve oplossingen het onlangs heeft gebruikt. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **[!UICONTROL Asset]**: Het aantal keren dat het actief deel uitmaakte van een collectie of samengesteld middel.
   * **[!UICONTROL Web & Mobile]**: Het aantal keren dat het middel deel uitmaakte van websites en apps.
   * **[!UICONTROL Social]**: Het aantal keren dat het middel is gebruikt in oplossingen, zoals Adobe Social en Adobe Campaign.
   * **[!UICONTROL Email]**: Het aantal keren dat het middel in e-mailcampagnes is gebruikt.
   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de functie Asset Insights de gegevens van Oplossingen gewoonlijk periodiek ophaalt van Adobe Analytics, wordt de meeste recente gegevens mogelijk niet weergegeven in de sectie Oplossingen. De tijdspanne waarvoor de gegevens worden getoond hangt het programma van de haalverrichting af die de Inzichten van Activa loopt om de gegevens van de Analyse terug te winnen.

1. To view performance statistics for the asset graphically over a period of time, select period in the **[!UICONTROL Performance Statistics]** section. De details, inclusief klikken en impressies, worden getoond als trendlijnen van een grafiek.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Tik op of klik **[!UICONTROL Get Embed Code]** onder de elementminiatuur om de insluitcode te verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen. <!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## Samengevoegde statistieken voor afbeeldingen weergeven {#viewing-aggregate-statistics-for-images}

You can view scores of all assets within a folder simultaneously using **[!UICONTROL Insights View]**.

1. Navigeer in de interface Elementen naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Tik op het pictogram Lay-out of klik op het pictogram Lay-out op de werkbalk en kies **[!UICONTROL Insights View]**.
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

## Achtergrondtaak plannen {#scheduling-background-job}

Asset Insights haalt op periodieke wijze gebruiksgegevens voor middelen op uit Adobe Analytics-rapportreeksen. Door gebrek, stelt de Inzichten van Activa een achtergrondbaan om de 24 uur bij 2 AM aan de ophaalgegevens in werking. Nochtans, kunt u zowel de frequentie als de tijd wijzigen door de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** dienst van de Webconsole te vormen.

1. Tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** serviceconfiguratie.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Specificeer de gewenste plannerfrequentie en de begintijd voor de baan in de uitdrukking van de bezitsplanner. Sla de wijzigingen op.

## Elementinzichten configureren {#configure-asset-insights}

Met Adobe Experience Manager (AEM) worden gebruiksgegevens opgehaald van AEM-elementen die door websites van derden worden gebruikt met Adobe Analytics. Als u Asset Insights wilt inschakelen om deze gegevens op te halen en inzichten te genereren, moet u eerst de functie configureren voor integratie met Adobe Analytics.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. Klik in AEM op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Klik op de **[!UICONTROL Insights Configuration]** kaart.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![Adobe Analytics voor Assets Insights configureren in AEM](assets/insights_config2.png)

   *Afbeelding: Adobe Analytics voor Assets Insights configureren in AEM*

1. Klik of tik op **[!UICONTROL Authenticate]**. Nadat AEM uw gegevens heeft geverifieerd, kiest u in de **[!UICONTROL Report Suite]** lijst een Adobe Analytics-rapportsuite waaruit u gegevens wilt ophalen met behulp van Asset Insights. Klik op **[!UICONTROL Add]**.
1. Tik op uw rapportsuite nadat AEM de rapportsuite heeft ingesteld **[!UICONTROL Done]**.

### Paginanummering {#page-tracker}

Nadat u uw Adobe Analytics-account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Als u Assets Insights wilt inschakelen om AEM-elementen die worden gebruikt op websites van derden bij te houden, neemt u de paginacontrackercode op in de websitecode. Gebruik het hulpprogramma Paginanummering in AEM Assets om de code van de paginacontracker te genereren. <!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. Klik in AEM op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Klik op de **[!UICONTROL Navigation]** **[!UICONTROL Insights Page Tracker]** kaart op de pagina.
1. Klik **[!UICONTROL Download]** om de code van de paginacontracker te downloaden.

<!--

## Using demo package for Asset Insights {#using-demo-package-for-asset-insights}

Using the demo package, you can enable Adobe Asset Insights to capture data from and generate insights for a sample web page.

1. Configure Asset Insights using the instructions in [Configure Asset Insights](#configure-asset-insights).
1. Download the sample AEM Assets package from below and install the package from CRXDE package manager.

   [Get File](assets/insightsdemo.zip)

1. Download the ZIP file containing the sample web page from below and extract on your local file system.

   [Get File](assets/demosite.zip)

1. Click the web page to open it in the web browser.

   >[!CAUTION]
   >
   >Web Page is configured to load asset from the localhost server . In case your server is running somewhere else change server address from localhost to server address in the HTML content of the web page.

   >[!NOTE]
   >
   >The external web page can be in AEM itself.

-->
