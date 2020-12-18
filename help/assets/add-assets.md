---
title: Voeg uw digitale elementen toe aan  [!DNL Adobe Experience Manager].
description: Voeg uw digitale middelen aan [!DNL Adobe Experience Manager] als a [!DNL Cloud Service] toe.
translation-type: tm+mt
source-git-commit: 42d607c2dc938c2ed91ecac10b29824050dd6810
workflow-type: tm+mt
source-wordcount: '1839'
ht-degree: 0%

---


# Digitale elementen toevoegen aan Adobe Experience Manager {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager] Verrijkt de binaire inhoud van de geüploade digitale bestanden met rijke metagegevens, slimme tags, uitvoeringen en andere DAM-services (Digital Asset Management). U kunt verschillende bestandstypen uploaden van uw lokale map of een netwerkstation naar [!DNL Experience Manager Assets], zoals afbeeldingen, documenten en Raw-afbeeldingsbestanden.

Er is een aantal uploadmethoden beschikbaar. Naast de meest gebruikte browser upload bestaan er andere methoden om elementen aan de [!DNL Experience Manager]-opslagplaats toe te voegen, zoals bureaubladclients, zoals Adobe Asset Link of [!DNL Experience Manager] desktop app, upload- en innamescripts die klanten zouden maken, en geautomatiseerde innamesintegraties die als [!DNL Experience Manager]-extensies worden toegevoegd.

We zullen ons hier concentreren op uploadmethoden voor eindgebruikers en koppelingen verschaffen naar artikelen die technische aspecten van het uploaden en opnemen van middelen beschrijven met behulp van [!DNL Experience Manager] API&#39;s en SDK&#39;s.

Hoewel u elk binair bestand in [!DNL Experience Manager] kunt uploaden en beheren, bieden de meest gebruikte bestandsindelingen ondersteuning voor extra services, zoals het ophalen van metagegevens of het genereren van voorvertoningen. Raadpleeg [ondersteunde bestandsindelingen](file-format-support.md) voor meer informatie.

Ook kunt u ervoor kiezen om extra verwerkingen uit te voeren voor de geüploade elementen. U kunt een aantal profielen voor middelenverwerking configureren in de map waarin elementen worden geüpload om specifieke metagegevens, uitvoeringen of services voor beeldverwerking toe te voegen. Zie [Middelen verwerken bij uploaden](#process-when-uploaded).

>[!NOTE]
>
>[!DNL Experience Manager] als  [!DNL Cloud Service] hefboom een nieuwe manier om activa te uploaden - directe binaire upload. Deze wordt standaard ondersteund door de productmogelijkheden en clients buiten de verpakking, zoals [!DNL Experience Manager]-gebruikersinterface, [!DNL Adobe Asset Link]-, [!DNL Experience Manager]-bureaubladtoepassing en dus transparant voor de eindgebruikers.
>
>Upload code die door klanten technische teams wordt aangepast of uitgebreid moet de nieuwe upload APIs en protocollen gebruiken.

Elementen als een [!DNL Cloud Service] bieden de volgende uploadmethoden. Adobe raadt u aan om uw gebruiksscenario en toepasselijkheid van een uploadoptie te begrijpen voordat u deze gebruikt.

| Upload, methode | Wanneer gebruiken? | Primaire persoon |
|---------------------|----------------|-----------------|
| [Gebruikersinterface middelenconsole](#upload-assets) | Soms uploaden, indrukken en slepen, zoeken naar uploaden. Gebruik deze optie niet om een groot aantal elementen te uploaden. | Alle gebruikers |
| [API uploaden](#upload-using-apis) | Voor dynamische beslissingen tijdens het uploaden. | Developer |
| [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Lage hoeveelheid asset-opname, maar voor migratie. | Beheerder, Marketer |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) | Nuttig wanneer creatieve en marketingmedewerkers hun bedrijfsmiddelen gebruiken vanuit de ondersteunde [!DNL Creative Cloud]-bureaubladtoepassingen. | Creatief, Marketer |
| [Vlek van activa](#asset-bulk-ingestor) | Aanbevolen voor grootschalige migraties en incidentele bulkopname. Alleen voor ondersteunde datastores. | Beheerder, ontwikkelaar |

## Elementen uploaden {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->

Als u een bestand (of meerdere bestanden) wilt uploaden, kunt u de bestanden op uw bureaublad selecteren en in de gebruikersinterface (webbrowser) naar de doelmap slepen. U kunt het uploaden ook starten vanuit de gebruikersinterface.

1. Navigeer in de gebruikersinterface [!DNL Assets] naar de locatie waar u digitale elementen wilt toevoegen.
1. Voer een van de volgende handelingen uit om de elementen te uploaden:

   * Klik op **[!UICONTROL Create]** > **[!UICONTROL Files]** op de werkbalk. U kunt de naam van het bestand desgewenst wijzigen in het dialoogvenster dat verschijnt.
   * In browser die HTML5 steunt, sleep de activa direct op [!DNL Assets] gebruikersinterface. Het dialoogvenster voor het wijzigen van de naam van het bestand wordt niet weergegeven.

   ![create_menu](assets/create_menu.png)

   Als u meerdere bestanden wilt selecteren, selecteert u `Ctrl` of `Command` en selecteert u de elementen in het dialoogvenster Bestandenkiezer. Als u een iPad gebruikt, kunt u slechts één bestand tegelijk selecteren.

1. Als u een actieve upload wilt annuleren, klikt u op Sluiten (`X`) naast de voortgangsbalk. Wanneer u de uploadbewerking annuleert, verwijdert [!DNL Assets] het gedeeltelijk geüploade gedeelte van het element.
Als u een uploadbewerking annuleert voordat de bestanden zijn geüpload, wordt het huidige bestand niet meer geüpload en wordt de inhoud vernieuwd. [!DNL Assets] Bestanden die al zijn geüpload, worden echter niet verwijderd.

1. Het dialoogvenster voor uploadvoortgang in [!DNL Assets] geeft het aantal bestanden weer dat is geüpload en de bestanden die niet zijn geüpload.
Daarnaast wordt in de gebruikersinterface [!DNL Assets] het element weergegeven dat u het laatst hebt geüpload of de map die u het eerst hebt gemaakt.

>[!NOTE]
>
>Voor het uploaden van geneste maphiërarchieën raadpleegt u [bulkuploadmiddelen](#bulk-upload).

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of [!DNL Assets]. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests [!DNL Assets] can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, [!DNL Assets] may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, [!DNL Assets] ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in Crx-de and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to [!DNL Experience Manager], the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. [!DNL Assets] supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in [!DNL Assets].

>[!NOTE]
>
>Streaming upload is disabled for [!DNL Experience Manager] running on JEE server with servlet-api version lower than 3.1.
-->

### Uploads verwerken wanneer element al bestaat {#handling-upload-existing-file}

U kunt een element uploaden met hetzelfde pad (dezelfde naam en dezelfde locatie) als een bestaand element. Er wordt echter een waarschuwingsvenster weergegeven met de volgende opties:

* Bestaand element vervangen: Als u een bestaand element vervangt, worden de metagegevens voor het element en eventuele eerdere wijzigingen (bijvoorbeeld annotaties, uitsnijden, enzovoort) die u in het bestaande element hebt aangebracht, verwijderd.
* Een andere versie maken: Er wordt een nieuwe versie van het bestaande middel gemaakt in de repository. U kunt de twee versies weergeven in de [!UICONTROL Timeline] en desgewenst terugkeren naar de vorige bestaande versie.
* Beide behouden: Als u ervoor kiest beide elementen te behouden, wordt de naam van het nieuwe element gewijzigd in het nummer `1` dat aan de naam wordt toegevoegd.

>[!NOTE]
>
>Als u **[!UICONTROL Replace]** selecteert in het dialoogvenster [!UICONTROL Name Conflict], wordt de element-id opnieuw gegenereerd voor het nieuwe element. Deze id verschilt van de id van het vorige element.
>
>Als Asset Insights is ingeschakeld voor het bijhouden van indrukken of klikken met [!DNL Adobe Analytics], maakt de opnieuw gegenereerde element-id de gegevensopname voor het element op [!DNL Analytics] ongeldig.

Als u het gedupliceerde element wilt behouden in [!DNL Assets], klikt u op **[!UICONTROL Keep]**. Tik op **[!UICONTROL Delete]** om het geüploade dubbele element te verwijderen.

### Bestandsnaamverwerking en verboden tekens {#filename-handling}

[!DNL Experience Manager Assets] Hiermee voorkomt u dat u elementen uploadt met de verboden tekens in de bestandsnaam. Als u een element probeert te uploaden met een bestandsnaam die een niet-toegestaan teken of meer bevat, wordt een waarschuwingsbericht weergegeven en wordt het uploaden gestopt totdat u deze tekens verwijdert of uploadt met een toegestane naam. [!DNL Assets] Sommige uploadmethoden verhinderen niet dat u elementen uploadt met verboden tekens in de bestandsnamen, maar vervangen de tekens door `-`.

In het dialoogvenster [!UICONTROL Upload Assets] kunt u lange namen opgeven voor de bestanden die u uploadt, zodat u de specifieke conventies voor bestandsnaamgeving voor uw organisatie kunt gebruiken. De volgende tekens (lijst met door spaties gescheiden tekens) worden niet ondersteund:

* ongeldige tekens voor elementbestandsnaam `* / : [ \\ ] | # % { } ? &`
* ongeldige tekens voor elementmapnaam `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Elementen voor uploaden in bulk {#bulk-upload}

De grote leverancier van bedrijfsmiddelen kan duizenden bedrijfsmiddelen efficiënt verwerken. Een grootschalige inname is echter niet alleen een grote bestandsstortplaats of blinde migratie. Om een zinvol project te zijn dat uw bedrijfsdoel dient, leidt het plannen en beheren van de activa tot een veel efficiëntere opname. Alle ingesties zijn niet het zelfde en generalisaties kunnen niet worden gemaakt zonder rekening te houden in de genadekte bewaarplaats samenstelling en bedrijfsbehoeften. Hieronder vindt u overkoepelende suggesties voor het plannen en uitvoeren van bulkopname:

* Cursieve elementen: Verwijder elementen die niet nodig zijn in de DAM. Overweeg ongebruikte, verouderde of dubbele elementen te verwijderen. Dit vermindert de gegevens die worden overgedragen en de elementen die worden opgenomen, waardoor er sneller ingestie ontstaat.
* Elementen ordenen: U kunt de inhoud in een logische volgorde ordenen, bijvoorbeeld op bestandsgrootte, bestandsindeling, hoofdlettergebruik of prioriteit. Over het algemeen is voor grote complexe bestanden meer verwerking nodig. U kunt ook overwegen grote bestanden afzonderlijk in te voegen met de filteroptie voor bestandsgrootte (hieronder beschreven).
* Staggeringestie: Overweeg uw inname op te splitsen in meerdere projecten voor bulkinname. Hierdoor kunt u de inhoud sneller zien en uw opname indien nodig bijwerken. U kunt bijvoorbeeld verwerkingsintensieve elementen opnemen tijdens niet-piekuren of geleidelijk in meerdere stukken. U kunt echter kleinere en eenvoudigere elementen invoeren die niet veel verwerkingstijd in één keer vereisen.

Als u een groter aantal bestanden wilt uploaden, gebruikt u een van de volgende methoden. Zie ook [use cases and methods](#upload-methods-comparison)

* [API&#39;s voor middelenupload](developer-reference-material-apis.md#asset-upload-technical): Gebruik een aangepast uploadscript of een aangepast gereedschap waarmee API&#39;s kunnen worden gebruikt om aanvullende verwerking van elementen toe te voegen (bijvoorbeeld metagegevens vertalen of bestanden hernoemen), indien nodig.
* [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html): Nuttig voor creatieve professionals en marketers die middelen uploaden vanaf hun lokale bestandssysteem. Gebruik deze optie om geneste mappen te uploaden die lokaal beschikbaar zijn.
* [Gereedschap](#asset-bulk-ingestor) voor bulkinvoer: Wordt gebruikt voor inname van grote hoeveelheden elementen, soms of in eerste instantie bij de implementatie  [!DNL Experience Manager].

### Gereedschap {#asset-bulk-ingestor} voor het bulkmiddel

Het hulpmiddel wordt verstrekt slechts aan de beheerdersgroep om voor grootschalige opname van activa van Azure of S3 datastores te gebruiken.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

Voer de volgende stappen uit om het gereedschap te configureren:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]**. Selecteer de optie **[!UICONTROL Create]**.

![Configuratie van bulkimporteur](assets/bulk-import-config.png)

1. Geef op [!UICONTROL bulk import configuration] pagina de vereiste waarden op.

   * [!UICONTROL Title]: Een beschrijvende titel.
   * [!UICONTROL Import Source]: Selecteer de toepasselijke gegevensbron.
   * [!UICONTROL Filter by Min Size]: Geef een minimale bestandsgrootte van elementen op in MB.
   * [!UICONTROL Filter by Max Size]: Geef de maximale bestandsgrootte van elementen op in MB.
   * [!UICONTROL Exclude Mime Types]: Door komma&#39;s gescheiden lijst met MIME-typen die van de opname moeten worden uitgesloten. Bijvoorbeeld, `image/jpeg, image/.*, video/mp4`.
   * [!UICONTROL Include Mime Types]: Door komma&#39;s gescheiden lijst met MIME-typen die in de opname moeten worden opgenomen. Zie [alle ondersteunde bestandsindelingen](/help/assets/file-format-support.md).
   * [!UICONTROL Import Mode]: Selecteer Versie overslaan, vervangen of maken. De modus Overslaan is de standaardmodus en in deze modus slaat de regelaar over om een element te importeren als dit al bestaat. Zie de betekenis van [vervang en maak versieopties](#handling-upload-existing-file).
   * [!UICONTROL Assets Target Folder]: Map importeren in DAM waar elementen moeten worden geïmporteerd. Bijvoorbeeld, `/content/dam/imported_assets`

1. U kunt schrapen, wijzigen, uitvoeren en meer doen met uw gecreeerde spelersconfiguraties. Als u een configuratie met een grote importingestor selecteert, is de optie Volgende beschikbaar op de werkbalk.

   * [!UICONTROL Edit]: Bewerk de geselecteerde configuratie.
   * [!UICONTROL Delete]: Verwijder de geselecteerde configuratie.
   * [!UICONTROL Check]: Verbinding met de datastore valideren.
   * [!UICONTROL Dry Run]: Roep een testrun van de bulkopname aan.
   * [!UICONTROL Run]: Voer de geselecteerde configuratie uit.
   * [!UICONTROL Stop]: Beëindig een actieve configuratie.
   * [!UICONTROL Job Status]: Bekijk de status van de configuratie wanneer deze wordt gebruikt in een actieve importtaak of wordt gebruikt voor een voltooide taak.
   * [!UICONTROL View Assets]: Geef de doelmap weer als deze bestaat.

## Elementen uploaden met desktopclients {#upload-assets-desktop-clients}

Naast de gebruikersinterface van de webbrowser biedt [!DNL Experience Manager] ondersteuning voor andere clients op het bureaublad. Ze bieden ook uploadervaring zonder dat u naar de webbrowser hoeft te gaan.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) biedt toegang tot middelen van  [!DNL Experience Manager] Adobe Photoshop-, Adobe Illustrator- en Adobe InDesign-bureaubladtoepassingen. U kunt het momenteel geopende document rechtstreeks vanuit de gebruikersinterface Adobe Asset Link vanuit deze bureaubladtoepassingen uploaden naar [!DNL Experience Manager].
* [[!DNL Experience Manager] desktop ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) past het werken met middelen op desktop toe, onafhankelijk van het bestandstype of de oorspronkelijke toepassing die ze verwerkt. Het is vooral handig om bestanden in geneste maphiërarchieën vanuit uw lokale bestandssysteem te uploaden, omdat het uploaden van de browser alleen het uploaden van platte bestandslijsten ondersteunt.

## Elementen verwerken bij het uploaden {#process-when-uploaded}

Als u de geüploade elementen extra wilt verwerken, kunt u verwerkingsprofielen toepassen op de uploadmappen. De profielen zijn beschikbaar op de **[!UICONTROL Properties]** pagina van een omslag in [!DNL Assets].

![assets-folder-eigenschappen](assets/assets-folder-properties.png)

De volgende tabbladen zijn beschikbaar:

* [Met ](metadata-profiles.md) metagegevensprofielen kunt u standaardeigenschappen voor metagegevens toepassen op elementen die naar die map zijn geüpload
* [Met ](asset-microservices-configure-and-use.md) verwerkingsprofielen kunt u meer uitvoeringen genereren dan standaard mogelijk is.

Daarnaast zijn de volgende tabbladen beschikbaar als [!DNL Dynamic Media] is ingeschakeld voor uw implementatie:

* [Met Dynamic Media-afbeeldingsprofielen kunt ](dynamic-media/image-profiles.md) u specifieke uitsnijdconfiguratie (**[!UICONTROL Smart Cropping]** en pixeluitsnijding) en verscherpingsconfiguratie toepassen op de geüploade elementen.
* [Met Dynamic Media Video-](dynamic-media/video-profiles.md) profielen kunt u specifieke videocoderingsprofielen (resolutie, indeling, parameters) toepassen.

>[!NOTE]
>
>Uitsnijden en andere bewerkingen van Dynamic Media op elementen zijn niet-destructief, dat wil zeggen dat ze het geüploade origineel niet wijzigen, maar in plaats daarvan parameters bieden voor uitsnijden of mediatransformatie die moet worden uitgevoerd wanneer de elementen worden geleverd

Voor mappen waaraan een verwerkingsprofiel is toegewezen, wordt de profielnaam weergegeven op de miniatuur in de kaartweergave. In de lijstmening, verschijnt de profielnaam in **[!UICONTROL Processing Profile]** kolom.

## Elementen uploaden of invoegen met behulp van API&#39;s {#upload-using-apis}

Technische details van de upload APIs en het protocol, en verbindingen aan open-bron SDK en steekproefcliënten worden verstrekt in [activaupload](developer-reference-material-apis.md#asset-upload-technical) sectie van de ontwikkelaarsverwijzing.

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [Info [!DNL Adobe Asset Link]](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Technische referentie voor het uploaden van bedrijfsmiddelen](developer-reference-material-apis.md#asset-upload-technical)

