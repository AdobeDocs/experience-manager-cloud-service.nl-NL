---
title: Assets Insights
description: Houd gebruikersbeoordelingen en gebruiksstatistieken bij van afbeeldingen die worden gebruikt in marketingcampagnes van derden en creatieve oplossingen voor Adobe.
contentOwner: AG
feature: Asset Insights, Asset Reports
role: Business Practitioner,Leader
exl-id: e268453b-e7c0-4aa4-bd29-2686edb5f99a
source-git-commit: 1c841eaa49eeb021fc7583c58aeaefc1236650f9
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 1%

---

# Elementen {#asset-insights}

Met de functie voor beperkte informatie kunt u gebruikersbeoordelingen en gebruiksstatistieken bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen voor Adobe. Hierdoor krijgt u meer inzicht in de prestaties en de populariteit van de afbeeldingen.

Met Elementinzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keer dat een afbeelding wordt beoordeeld, geklikt en afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Als u met behulp van Assets gebruiksstatistieken wilt vastleggen voor afbeeldingen van een website, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Om de statistieken van het de vertoningsgebruik van Activa van Inzichten voor activa te laten, vorm eerst de eigenschap om rapportgegevens van [!DNL Adobe Analytics] te halen. Voor details, zie [Elementen inzichten](#configure-asset-insights) vormen. Koop [!DNL Adobe Analytics] licentie afzonderlijk om deze functie te gebruiken.

>[!NOTE]
>
>Inzichten worden ondersteund en alleen voor afbeeldingen verstrekt.

## Statistieken weergeven voor een afbeelding {#viewing-statistics-for-an-image}

U kunt de elementinzichten van de metagegevenspagina weergeven.

1. Selecteer de afbeelding in de gebruikersinterface Elementen en klik op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op **[!UICONTROL Insights]** op de pagina Eigenschappen.
1. Controleer de gebruiksdetails voor het element op het tabblad **[!UICONTROL Insights]**. In de sectie **[!UICONTROL Score]** worden het totale gebruik en de prestatiesbronnen van een element beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL Impressions]** score is het aantal keren dat het element op de website wordt geladen. Het getal dat onder **[!UICONTROL Clicks]** wordt weergegeven, is het aantal keren dat op het element wordt geklikt.

1. Controleer de sectie **[!UICONTROL Usage Statistics]** om te weten van welke entiteiten het middel deel uitmaakte en welke creatieve oplossingen het onlangs gebruikten. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **[!UICONTROL Asset]**: Het aantal keren dat het actief deel uitmaakte van een collectie of samengesteld middel.
   * **[!UICONTROL Web & Mobile]**: Het aantal keren dat het middel deel uitmaakte van websites en apps.
   * **[!UICONTROL Social]**: Het aantal keren dat het element is gebruikt in andere oplossingen, zoals een  [!DNL Adobe Campaign].
   * **[!UICONTROL Email]**: Het aantal keren dat het middel in e-mailcampagnes is gebruikt.

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de eigenschap van de Inzichten van Activa typisch de gegevens van Oplossingen van [!DNL Adobe Analytics] periodiek ophaalt, kan de sectie van Oplossingen niet de meest recente gegevens tonen. De tijdspanne waarvoor de gegevens worden getoond hangt het programma van de haalverrichting af die de Inzichten van Activa in werking stellen om de gegevens van de Analyse terug te winnen.

1. Als u de prestatiestatistieken voor het element gedurende een bepaalde periode grafisch wilt weergeven, selecteert u een punt in de sectie **[!UICONTROL Performance Statistics]**. De details, inclusief klikken en impressies, worden getoond als trendlijnen van een grafiek.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Klik **[!UICONTROL Get Embed Code]** onder de elementminiatuur om de insluitcode te verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen. <!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## Samengevoegde statistieken weergeven voor afbeeldingen {#viewing-aggregate-statistics-for-images}

U kunt de scores van alle elementen in een map tegelijkertijd weergeven met **[!UICONTROL Insights View]**.

1. Navigeer in de interface Elementen naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Klik op de optie Indeling op de werkbalk en kies **[!UICONTROL Insights View]**.
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Schedule background job {#scheduling-background-job}

Assets Insights fetches usage data for assets from Adobe Analytics report suites in a periodic manner. By default, Assets Insights runs a background job every 24 hours at 2 AM to the fetch data. However, you can modify both the frequency and the time by configuring the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service from the web console.

1. Click the [!DNL Experience Manager] logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service configuration.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Specify the desired scheduler frequency and the start time for the job in the property scheduler expression. Save the changes.
-->

## Elementeninzichten configureren {#configure-asset-insights}

[!DNL Experience Manager Assets] Hiermee haalt u gebruiksgegevens op van digitale elementen die door websites van derden worden gebruikt  [!DNL Adobe Analytics]. Om ActivaInzichten toe te laten om deze gegevens terug te winnen en inzichten te produceren, vorm eerst de eigenschap om met [!DNL Adobe Analytics] te integreren.

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Klik op de **[!UICONTROL Insights Configuration]**-kaart.
1. Selecteer een datacenter in de wizard en geef uw referenties op, inclusief de naam van uw organisatie, gebruikersnaam en gedeeld geheim.

   ![Adobe Analytics for Assets Insights configureren in  [!DNL Experience Manager]](assets/insights_config2.png)

   *Afbeelding: Adobe Analytics for Assets Insights configureren in[!DNL Experience Manager]*

1. Klik op **[!UICONTROL Authenticate]**. Nadat [!DNL Experience Manager] uw geloofsbrieven voor authentiek verklaart, van **[!UICONTROL Report Suite]** lijst, kies een het rapportreeks van Adobe Analytics van waar u de Inzichten van Activa wilt om gegevens te halen. Klik op **[!UICONTROL Add]**.
1. Nadat [!DNL Experience Manager] uw rapportsuite heeft ingesteld, klikt u op **[!UICONTROL Done]**.

### Paginanummering {#page-tracker}

Nadat u uw Adobe Analytics-account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Als u Assets Insights wilt inschakelen om de [!DNL Experience Manager]-elementen bij te houden die worden gebruikt in websites van derden, neemt u de paginacontrackercode op in de websitecode. Gebruik het hulpprogramma Paginanummering in Elementen om de code van de paginacontracker te genereren. <!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. Klik in [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Klik op de **[!UICONTROL Navigation]**-pagina op de **[!UICONTROL Insights Page Tracker]**-kaart.
1. Klik **[!UICONTROL Download]** om de code van de paginacontracker te downloaden.

<!--

## Using demo package for Assets Insights {#using-demo-package-for-asset-insights}

Using the demo package, you can enable Adobe Assets Insights to capture data from and generate insights for a sample web page.

1. Configure Assets Insights using the instructions in [Configure Assets Insights](#configure-asset-insights).
1. Download the sample [!DNL Experience Manager Assets] package from below and install the package from CRXDE package manager.

   [Get File](assets/insightsdemo.zip)

1. Download the ZIP file containing the sample web page from below and extract on your local file system.

   [Get File](assets/demosite.zip)

1. Click the web page to open it in the web browser.

   >[!CAUTION]
   >
   >Web Page is configured to load asset from the localhost server . In case your server is running somewhere else change server address from localhost to server address in the HTML content of the web page.

   >[!NOTE]
   >
   >The external web page can be in [!DNL Experience Manager] itself.

-->
