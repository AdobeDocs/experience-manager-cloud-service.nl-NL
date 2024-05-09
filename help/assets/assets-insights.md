---
title: Assets Insights
description: Houd gebruikersbeoordelingen en gebruiksstatistieken bij van afbeeldingen die worden gebruikt op websites van derden, marketingcampagnes en creatieve oplossingen van de Adobe.
contentOwner: AG
feature: Asset Insights,Asset Reports
role: User,Leader
exl-id: e268453b-e7c0-4aa4-bd29-2686edb5f99a
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 2%

---

# Assets Insights {#asset-insights}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/asset-insights.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Met de functie Assets Insights kunt u gebruikersbeoordelingen en gebruiksstatistieken bijhouden van afbeeldingen die worden gebruikt in websites van derden, marketingcampagnes en creatieve oplossingen van de Adobe. Hierdoor krijgt u meer inzicht in de prestaties en de populariteit van de afbeeldingen.

Met Elementinzichten worden gegevens over gebruikersactiviteit vastgelegd, zoals het aantal keer dat een afbeelding wordt beoordeeld, geklikt en afbeeldingen worden afgedrukt (het aantal keer dat een afbeelding op de website wordt geladen). Er worden scores toegewezen aan afbeeldingen op basis van deze statistieken. U kunt de scores en de prestatiesstatistieken gebruiken om populaire beelden voor opneming in catalogi, marketing campagnes, etc. te selecteren. U kunt zelfs archiverings en vergunningsvernieuwing beleid formuleren dat op deze statistieken wordt gebaseerd.

Als u met behulp van Assets gebruiksstatistieken wilt vastleggen voor afbeeldingen van een website, moet u de insluitcode voor de afbeelding opnemen in de websitecode.

Om de statistieken van het vertoningsgebruik van Activa van Inzichten voor activa te laten, vorm eerst de eigenschap om rapportgegevens van te halen [!DNL Adobe Analytics]. Zie voor meer informatie [Elementengegevens configureren](#configure-asset-insights). Als u deze functie wilt gebruiken, koopt u [!DNL Adobe Analytics] licentie afzonderlijk.

>[!NOTE]
>
>Inzichten worden ondersteund en alleen voor afbeeldingen verstrekt.

## Statistieken voor een afbeelding weergeven {#viewing-statistics-for-an-image}

U kunt de elementinzichten van de metagegevenspagina weergeven.

1. Selecteer de afbeelding in de gebruikersinterface Elementen en klik vervolgens op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op de pagina Eigenschappen op **[!UICONTROL Insights]**.
1. Bekijk de gebruiksdetails voor het element in de **[!UICONTROL Insights]** tab. De **[!UICONTROL Score]** in dit gedeelte wordt het totale gebruik en de prestatiesbronnen van een actief beschreven.

   De score van het gebruik beschrijft het aantal tijden activa wordt gebruikt in diverse oplossingen.

   De **[!UICONTROL Impressions]** De score is het aantal keren dat het element op de website wordt geladen. Het nummer dat onder wordt weergegeven **[!UICONTROL Clicks]** is het aantal keren dat op het element wordt geklikt.

1. Controleer de **[!UICONTROL Usage Statistics]** sectie om te weten van welke entiteiten het actief deel uitmaakte en welke creatieve oplossingen het onlangs gebruikten. Hoe hoger het gebruik, hoe groter de kans dat het middel populair is bij gebruikers. Gebruiksgegevens worden onder de volgende koppen weergegeven:

   * **[!UICONTROL Asset]**: Het aantal keren dat het actief deel uitmaakte van een collectie of samengesteld middel.
   * **[!UICONTROL Web & Mobile]**: Het aantal keren dat het middel deel uitmaakte van websites en apps.
   * **[!UICONTROL Social]**: Het aantal keren dat het element is gebruikt in andere oplossingen, zoals een [!DNL Adobe Campaign].
   * **[!UICONTROL Email]**: Het aantal keren dat het middel in e-mailcampagnes is gebruikt.

   ![usage_statistics](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Omdat de eigenschap van de Inzichten van Activa typisch de gegevens van Oplossingen van haalt [!DNL Adobe Analytics] op een periodieke manier, kan de sectie van Oplossingen niet de meest recente gegevens tonen. De tijdspanne waarvoor de gegevens worden getoond hangt het programma van de haalverrichting af die de Inzichten van Activa in werking stellen om de gegevens van de Analyse terug te winnen.

1. Als u de prestatiestatistieken voor het actief grafisch wilt weergeven over een bepaalde periode, selecteert u de periode in het dialoogvenster **[!UICONTROL Performance Statistics]** sectie. De details, inclusief klikken en impressies, worden getoond als trendlijnen van een grafiek.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >In tegenstelling tot de gegevens in de sectie van Oplossingen, toont de sectie van de Statistieken van Prestaties de meest recente gegevens.

1. Als u de insluitcode wilt verkrijgen voor het element dat u in websites opneemt om prestatiegegevens op te halen, klikt u op **[!UICONTROL Get Embed Code]** onder de elementminiatuur. <!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## Samengevoegde statistieken voor afbeeldingen weergeven {#viewing-aggregate-statistics-for-images}

U kunt de scores van alle elementen in een map tegelijk weergeven met **[!UICONTROL Insights View]**.

1. Navigeer in de gebruikersinterface Elementen naar de map met de elementen waarvoor u inzichten wilt weergeven.
1. Klik op de knop **[!UICONTROL Layout]** en kiest u **[!UICONTROL Insights View]**.
1. Op de pagina worden gebruiksscores voor de elementen weergegeven. Vergelijk de ratings van de verschillende activa en teken inzichten.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Schedule background job {#scheduling-background-job}

Assets Insights fetches usage data for assets from Adobe Analytics report suites in a periodic manner. By default, Assets Insights runs a background job every 24 hours at 2 AM to the fetch data. However, you can modify both the frequency and the time by configuring the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service from the web console.

1. Click the [!DNL Experience Manager] logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open the **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** service configuration.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Specify the desired scheduler frequency and the start time for the job in the property scheduler expression. Save the changes.
-->

## Elementengegevens configureren {#configure-asset-insights}

[!DNL Experience Manager Assets] haalt gebruiksgegevens op over digitale middelen die door websites van derden worden gebruikt [!DNL Adobe Analytics]. Om de Inzichten van Activa toe te laten om deze gegevens terug te winnen en inzichten te produceren, vorm eerst de eigenschap om met te integreren [!DNL Adobe Analytics].

>[!NOTE]
>
>Inzichten worden alleen ondersteund en opgegeven voor afbeeldingen.

1. In [!DNL Experience Manager], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Klik op de knop **[!UICONTROL Insights Configuration]** kaart.

1. Ga voor de toegangsgegevens van de Analyse-webservice naar **[!UICONTROL Analytics]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Tools]** > **[!UICONTROL Company Settings]** > **[!UICONTROL Web Services]** en kopieer de **[!UICONTROL Shared Secret]** toets.

   Selecteer in de wizard de optie **[!UICONTROL Data Center]** en geef de weergavenaam van de **[!UICONTROL Company]**, Webservices **[!UICONTROL Username]** en plak de **[!UICONTROL Shared Secret]** toets.

   Klik op **[!UICONTROL Authenticate]**.

   ![Adobe Analytics for Assets Insights configureren in [!DNL Experience Manager]](assets/analytics-insight-config.png)

   *Afbeelding: Adobe Analytics for Assets Insights configureren in[!DNL Experience Manager]*

1. Bij succesvolle authentificatie, zult u de Reeksen van het Rapport krijgen die in drop-down worden vermeld. Selecteer de Adobe Analytics **[!UICONTROL Report Suite]** van waar u de Inzichten van Activa om gegevens wilt halen. Klik op **[!UICONTROL Add]**.

1. Na [!DNL Experience Manager] stelt uw rapportsuite in, klikt u op **[!UICONTROL Done]**.

Zie voor meer informatie [Adobe Analytics Web Services](https://experienceleague.adobe.com/docs/analytics/admin/company-settings/web-services-admin.html#api-access-information).

### Paginanummer {#page-tracker}

Nadat u uw Adobe Analytics-account hebt geconfigureerd, wordt de code van Paginanummer voor u gegenereerd. Om de Inzichten van Activa toe te laten om te volgen [!DNL Experience Manager] elementen die in websites van derden worden gebruikt, nemen de paginacontrackercode in de websitecode op. Gebruik het hulpprogramma Paginanummering in Elementen om de code van de paginacontracker te genereren. <!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. In [!DNL Experience Manager], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Van de **[!UICONTROL Navigation]** pagina, klikt u op de **[!UICONTROL Insights Page Tracker]** kaart.
1. Klikken **[!UICONTROL Download]** om de code van de paginacontracker te downloaden.

<!--
Add page tracker code, CQDOC-18045, 30/07/2021
-->
In het volgende voorbeeldcodefragment wordt de code van Paginanummer weergegeven die in een voorbeeldwebpagina is opgenomen:

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>

 </head>
```



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
