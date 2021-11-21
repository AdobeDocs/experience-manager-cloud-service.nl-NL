---
title: Voeg uw digitale middelen toe aan [!DNL Adobe Experience Manager].
description: Voeg uw digitale middelen toe aan [!DNL Adobe Experience Manager] als [!DNL Cloud Service].
feature: Asset Management,Upload
role: User,Admin
exl-id: 0e624245-f52e-4082-be21-13cc29869b64
source-git-commit: e7028272a32c2f53c3438cb918caaf04445442af
workflow-type: tm+mt
source-wordcount: '2093'
ht-degree: 0%

---

# Digitale elementen toevoegen aan [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [!DNL Assets] {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager Assets] accepteert veel typen digitale elementen van vele bronnen. De binaire bestanden en gemaakte uitvoeringen worden opgeslagen, er kunnen verschillende workflows voor worden gebruikt en [!DNL Adobe Sensei] de diensten, staat voor distributie door vele kanalen over vele oppervlakten toe.

[!DNL Adobe Experience Manager] Verrijkt de binaire inhoud van de geüploade digitale bestanden met rijke metagegevens, slimme tags, uitvoeringen en andere DAM-services (Digital Asset Management). U kunt verschillende bestandstypen uploaden van uw lokale map of een netwerkstation naar [!DNL Experience Manager Assets].

Naast de meest gebruikte browsers die uploaden, kunt u ook andere methoden gebruiken om elementen toe te voegen aan de [!DNL Experience Manager] opslagplaats bestaat, inclusief desktopclients, zoals Adobe Asset Link of [!DNL Experience Manager] desktop app, upload en opname scripts die klanten zouden maken, en geautomatiseerde integratie van indelingen toegevoegd als [!DNL Experience Manager] extensies.

Terwijl u elk binair bestand kunt uploaden en beheren in [!DNL Experience Manager]De meest gebruikte bestandsindelingen bieden ondersteuning voor aanvullende services, zoals het ophalen van metagegevens of het genereren van voorvertoningen. Zie [ondersteunde bestandsindelingen](file-format-support.md) voor meer informatie.

Ook kunt u ervoor kiezen om extra verwerkingen uit te voeren voor de geüploade elementen. U kunt een aantal profielen voor middelenverwerking configureren in de map waarin elementen worden geüpload om specifieke metagegevens, uitvoeringen of services voor beeldverwerking toe te voegen. Zie [proceselementen bij uploaden](#process-when-uploaded).

[!DNL Assets] biedt de volgende uploadmethoden. Adobe raadt u aan om uw gebruiksscenario en toepasselijkheid van een uploadoptie te begrijpen voordat u deze gebruikt.

| Upload, methode | Wanneer gebruiken? | Primaire persoon |
|---------------------|----------------|-----------------|
| [Gebruikersinterface middelenconsole](#upload-assets) | Soms uploaden, indrukken en slepen, zoeken naar uploaden. Gebruik deze optie niet om een groot aantal elementen te uploaden. | Alle gebruikers |
| [API uploaden](#upload-using-apis) | Voor dynamische beslissingen tijdens het uploaden. | Developer |
| [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Lage hoeveelheden asset opnemen, maar niet voor migratie. | Beheerder, Marketer |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) | Nuttig wanneer creatieve en marketingmedewerkers werken aan middelen van binnen de ondersteunde [!DNL Creative Cloud] bureaubladtoepassingen. | Creatief, Marketer |
| [Vlek van activa](#asset-bulk-ingestor) | Aanbevolen voor grootschalige migraties en incidentele bulkopname. Alleen voor ondersteunde datastores. | Beheerder, ontwikkelaar |

## Elementen uploaden {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The [!UICONTROL Pause] option does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** option appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload` node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click **[!UICONTROL Play]** option.
-->

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->

Als u een bestand (of meerdere bestanden) wilt uploaden, kunt u de bestanden op uw bureaublad selecteren en in de gebruikersinterface (webbrowser) naar de doelmap slepen. U kunt het uploaden ook starten vanuit de gebruikersinterface.

1. In de [!DNL Assets] navigeer in de gebruikersinterface naar de locatie waar u digitale elementen wilt toevoegen.
1. Voer een van de volgende handelingen uit om de elementen te uploaden:

   * Klik op de werkbalk op **[!UICONTROL Create]** > **[!UICONTROL Files]**. U kunt de naam van het bestand desgewenst wijzigen in het dialoogvenster dat verschijnt.
   * In browser die HTML5 steunt, sleep de activa direct op [!DNL Assets] gebruikersinterface. Het dialoogvenster voor het wijzigen van de naam van het bestand wordt niet weergegeven.

   ![create_menu](assets/create_menu.png)

   Als u meerdere bestanden wilt selecteren, selecteert u de optie `Ctrl` of de `Command` en selecteert u de elementen in het dialoogvenster Bestandenkiezer. Als u een iPad gebruikt, kunt u slechts één bestand tegelijk selecteren.

1. Als u een actieve upload wilt annuleren, klikt u op Sluiten (`X`) naast de voortgangsbalk. Wanneer u het uploaden annuleert, [!DNL Assets] Hiermee verwijdert u het gedeeltelijk geüploade gedeelte van het element.
Als u een upload annuleert voordat de bestanden zijn geüpload, [!DNL Assets] uploadt het huidige bestand niet meer en vernieuwt de inhoud. Bestanden die al zijn geüpload, worden echter niet verwijderd.

1. Het dialoogvenster Uploadvoortgang in [!DNL Assets] geeft het aantal geüploade bestanden weer en de bestanden die niet zijn geüpload.
Bovendien [!DNL Assets] in de gebruikersinterface wordt het meest recente element weergegeven dat u uploadt of de map die u als eerste hebt gemaakt.

>[!NOTE]
>
>Als u geneste maphiërarchieën wilt uploaden, raadpleegt u [bulkupload-elementen](#bulk-upload).

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of [!DNL Assets]. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests [!DNL Assets] can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, [!DNL Assets] may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, [!DNL Assets] ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in CRX-DE and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to [!DNL Experience Manager], the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. [!DNL Assets] supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in [!DNL Assets].

>[!NOTE]
>
>Streaming upload is disabled for [!DNL Experience Manager] running on JEE server with servlet-api version lower than 3.1.
-->

### Uploads verwerken wanneer element al bestaat {#handling-upload-existing-file}

U kunt een element uploaden met hetzelfde pad (dezelfde naam en dezelfde locatie) als een bestaand element. Er wordt echter een waarschuwingsvenster weergegeven met de volgende opties:

* Bestaand element vervangen: Als u een bestaand element vervangt, worden de metagegevens voor het element en eventuele eerdere wijzigingen (bijvoorbeeld annotaties, uitsnijden, enzovoort) die u in het bestaande element hebt aangebracht, verwijderd.
* Een andere versie maken: Er wordt een nieuwe versie van het bestaande middel gemaakt in de repository. U kunt de twee versies weergeven in het dialoogvenster [!UICONTROL Timeline] en kan desgewenst terugkeren naar de vorige bestaande versie.
* Beide behouden: Als u ervoor kiest beide elementen te behouden, wordt de naam van het nieuwe element gewijzigd.

Het dubbele element behouden in [!DNL Assets], klikt u op **[!UICONTROL Keep]**. Als u het geüploade dubbele element wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

### Bestandsnaamverwerking en verboden tekens {#filename-handling}

[!DNL Experience Manager Assets] Hiermee voorkomt u dat u elementen uploadt met de verboden tekens in de bestandsnaam. Als u een element probeert te uploaden met een bestandsnaam die een niet-toegestaan teken of meer bevat, [!DNL Assets] geeft een waarschuwingsbericht weer en stopt de upload totdat u deze tekens verwijdert of uploadt met een toegestane naam.

Als u specifieke conventies voor de naamgeving van bestanden voor uw organisatie wilt aanpassen, kunt u de opdracht [!UICONTROL Upload Assets] kunt u lange namen opgeven voor de bestanden die u uploadt. De volgende tekens (lijst met door spaties gescheiden tekens) worden niet ondersteund:

* ongeldige tekens voor de naam van het elementbestand `* / : [ \\ ] | # % { } ? &`
* ongeldige tekens voor naam van elementmap `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Bulkupload-elementen {#bulk-upload}

De grote leverancier van bedrijfsmiddelen kan een zeer groot aantal bedrijfsmiddelen efficiënt verwerken. Een grootschalige inname is echter niet alleen een grote bestandsstortplaats of een tijdelijke migratie. Voor een grootschalig project om een zinvol project te zijn dat uw bedrijfsdoel dient en efficiënt is, plant de migratie en leidt de middelenorganisatie. Alle ingesties zijn verschillend zo in plaats van generaliserend, factor in de genuanceerde bewaarplaats samenstelling en bedrijfsbehoeften. Hieronder volgen enkele overkoepelende suggesties voor het plannen en uitvoeren van bulkopname:

* Cursieve elementen: Verwijder elementen die niet nodig zijn in de DAM. Overweeg ongebruikte, verouderde of dubbele elementen te verwijderen. Dit vermindert de gegevens die worden overgedragen en de elementen die worden opgenomen, waardoor er sneller ingestie ontstaat.
* Elementen ordenen: U kunt de inhoud in een logische volgorde ordenen, bijvoorbeeld op bestandsgrootte, bestandsindeling, hoofdlettergebruik of prioriteit. Over het algemeen is voor grote complexe bestanden meer verwerking nodig. U kunt ook overwegen grote bestanden afzonderlijk in te voegen met de filteroptie voor bestandsgrootte (hieronder beschreven).
* Staggeringestie: Overweeg uw inname op te splitsen in meerdere projecten voor bulkinname. Zo kunt u inhoud sneller zien en uw opname indien nodig bijwerken. U kunt bijvoorbeeld verwerkingsintensieve elementen opnemen tijdens niet-piekuren of geleidelijk in meerdere stukken. U kunt echter kleinere en eenvoudigere elementen invoeren die niet veel verwerkingstijd in één keer vereisen.

Als u een groter aantal bestanden wilt uploaden, gebruikt u een van de volgende methoden. Zie ook de [gebruiksgevallen en -methoden](#upload-methods-comparison)

* [API&#39;s voor middelenupload](developer-reference-material-apis.md#asset-upload): Gebruik een aangepast uploadscript of een aangepast gereedschap waarmee API&#39;s kunnen worden gebruikt om aanvullende verwerking van elementen toe te voegen (bijvoorbeeld metagegevens vertalen of bestanden hernoemen), indien nodig.
* [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html): Nuttig voor creatieve professionals en marketers die middelen uploaden vanaf hun lokale bestandssysteem. Gebruik deze optie om geneste mappen te uploaden die lokaal beschikbaar zijn.
* [Gereedschap Bulkopname](#asset-bulk-ingestor): Wordt gebruikt voor inname van grote hoeveelheden elementen, soms of in eerste instantie bij implementatie [!DNL Experience Manager].

### Hulpmiddel voor het bulkmiddel {#asset-bulk-ingestor}

Het hulpmiddel wordt verstrekt slechts aan de beheerdersgroep om voor grootschalige opname van activa van Azure of S3 datastores te gebruiken. Bekijk een videodemo van de configuratie en opname.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

Voer de volgende stappen uit om het gereedschap te configureren:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]**. Selecteer **[!UICONTROL Create]** optie.

![Configuratie van bulkimporteur](assets/bulk-import-config.png)

1. Aan **[!UICONTROL bulk import configuration]** pagina, geef de vereiste waarden op en selecteer **[!UICONTROL Save]**.

   * [!UICONTROL Title]: Een beschrijvende titel.
   * [!UICONTROL Import Source]: Selecteer de toepasselijke gegevensbron.
   * [!UICONTROL Azure Storage Account]: Geef de naam van de [!DNL Azure] opslagaccount.
   * [!UICONTROL Azure Blob Container]: Geef de [!DNL Azure] opslagcontainer.
   * [!UICONTROL Azure Access Key]: Geef de toegangstoets op aan [!DNL Azure] account.
   * [!UICONTROL Source Folder]: Dit filter wordt doorgaans ondersteund door Azure- en AWS-cloudopslagproviders.
   * [!UICONTROL Filter by Min Size]: Geef een minimale bestandsgrootte van elementen op in MB.
   * [!UICONTROL Filter by Max Size]: Geef de maximale bestandsgrootte van elementen op in MB.
   * [!UICONTROL Exclude Mime Types]: Door komma&#39;s gescheiden lijst met MIME-typen die van de opname moeten worden uitgesloten. Bijvoorbeeld, `image/jpeg, image/.*, video/mp4`. Zie [alle ondersteunde bestandsindelingen](/help/assets/file-format-support.md).
   * [!UICONTROL Include Mime Types]: Door komma&#39;s gescheiden lijst met MIME-typen die in de opname moeten worden opgenomen. Zie [alle ondersteunde bestandsindelingen](/help/assets/file-format-support.md).
   * [!UICONTROL Import Mode]: Selecteer Versie overslaan, vervangen of maken. De modus Overslaan is de standaardmodus en in deze modus slaat de regelaar over om een element te importeren als dit al bestaat. Zie de betekenis van [versieopties vervangen en maken](#handling-upload-existing-file).
   * [!UICONTROL Assets Target Folder]: Map importeren in DAM waar elementen moeten worden geïmporteerd. Bijvoorbeeld, `/content/dam/imported_assets`
   * [!UICONTROL Metadata File]: Het metagegevensbestand dat moet worden geïmporteerd, opgegeven in de CSV-indeling. U geeft dit CSV-bestand op de locatie van het bronblob en raadpleegt het pad in de configuratie van het gereedschap voor het bulkinvoeren.

1. U kunt schrapen, wijzigen, uitvoeren en meer doen met uw gecreeerde spelersconfiguraties. Als u een configuratie met een grote importingestor selecteert, zijn de volgende opties beschikbaar in de werkbalk.

   * [!UICONTROL Edit]: Bewerk de geselecteerde configuratie.
   * [!UICONTROL Delete]: Verwijder de geselecteerde configuratie.
   * [!UICONTROL Check]: Verbinding met de datastore valideren.
   * [!UICONTROL Dry Run]: Roep een testrun van de bulkopname aan.
   * [!UICONTROL Run]: Voer de geselecteerde configuratie uit.
   * [!UICONTROL Stop]: Beëindig een actieve configuratie.
   * [!UICONTROL Schedule]: Stel een eenmalige of terugkerende planning in om elementen in te voeren.
   * [!UICONTROL Job Status]: Bekijk de status van de configuratie wanneer deze wordt gebruikt in een actieve importtaak of wordt gebruikt voor een voltooide taak.
   * [!UICONTROL Job History]: Eerdere exemplaren van de taak.
   * [!UICONTROL View Assets]: Geef de doelmap weer als deze bestaat.

   ![Werkbalkopties voor ingangconfiguraties](assets/bulk-ingest-toolbar-options.png)

Voer de volgende stappen uit om een eenmalige of herhaalde bulkimport te plannen:

1. Maak een configuratie voor bulkimport.
1. Selecteer de configuratie en selecteer **[!UICONTROL Schedule]** op de werkbalk.
1. Stel een eenmalige opname in of voer een uur-, dag- of wekelijks schema in. Klik op **[!UICONTROL Submit]**.

   ![Taak bulkingestor plannen](assets/bulk-ingest-schedule1.png)

## Elementen uploaden met desktopclients {#upload-assets-desktop-clients}

Naast de gebruikersinterface van de webbrowser [!DNL Experience Manager] ondersteunt andere clients op het bureaublad. Ze bieden ook uploadervaring zonder dat u naar de webbrowser hoeft te gaan.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) biedt toegang tot elementen van [!DNL Experience Manager] in Adobe Photoshop-, Adobe Illustrator- en Adobe InDesign-bureaubladtoepassingen. U kunt het momenteel geopende document uploaden naar [!DNL Experience Manager] rechtstreeks vanuit de gebruikersinterface van Adobe Asset Link vanuit deze bureaubladtoepassingen.
* [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) vereenvoudigt het werken met middelen op Desktop, onafhankelijk op hun dossiertype of inheemse toepassing die hen behandelt. Het is vooral handig om bestanden in geneste maphiërarchieën vanuit uw lokale bestandssysteem te uploaden, omdat het uploaden van de browser alleen het uploaden van platte bestandslijsten ondersteunt.

## Elementen verwerken bij het uploaden {#process-when-uploaded}

Als u de geüploade elementen extra wilt verwerken, kunt u verwerkingsprofielen toepassen op de uploadmappen. De profielen zijn beschikbaar in het dialoogvenster **[!UICONTROL Properties]** pagina van een map in [!DNL Assets]. Een digitaal element zonder extensie of met een onjuiste extensie wordt niet naar wens verwerkt. Wanneer u dergelijke elementen uploadt, gebeurt er bijvoorbeeld niets of wordt een onjuist verwerkingsprofiel toegepast op het element. Gebruikers kunnen de binaire bestanden nog steeds opslaan in de DAM.

![Eigenschappen van een elementmap met opties voor het toevoegen van een verwerkingsprofiel](assets/assets-folder-properties.png)

De volgende tabbladen zijn beschikbaar:

* [Metagegevensprofielen](metadata-profiles.md) Hiermee kunt u standaardeigenschappen van metagegevens toepassen op elementen die naar die map zijn geüpload.
* [Profielen verwerken](asset-microservices-configure-and-use.md) Hiermee kunt u meer uitvoeringen genereren dan standaard mogelijk is.

Bovendien, als [!DNL Dynamic Media] is op uw plaatsing toegelaten, zijn de volgende lusjes beschikbaar:

* [[!DNL Dynamic Media] Afbeeldingsprofielen](dynamic-media/image-profiles.md) Hiermee kunt u specifieke uitsnijdingen toepassen (**[!UICONTROL Smart Cropping]** en pixeluitsnijding) en verscherpingsconfiguratie voor de geüploade elementen.
* [[!DNL Dynamic Media] Videoprofielen](dynamic-media/video-profiles.md) Hiermee kunt u specifieke videocoderingsprofielen (resolutie, indeling, parameters) toepassen.

>[!NOTE]
>
>[!DNL Dynamic Media] uitsnijden en andere bewerkingen op elementen zijn niet-destructief, dat wil zeggen dat de bewerkingen het geüploade origineel niet wijzigen. In plaats daarvan biedt het parameters voor uitsnijden of transformeren bij het leveren van de elementen.

Voor mappen waaraan een verwerkingsprofiel is toegewezen, wordt de profielnaam weergegeven op de miniatuur in de kaartweergave. In de lijstweergave wordt de profielnaam weergegeven in het dialoogvenster **[!UICONTROL Processing Profile]** kolom.

## Elementen uploaden of toevoegen met API&#39;s {#upload-using-apis}

Technische details van de upload APIs en het protocol, en verbindingen aan open-bron SDK en steekproefcliënten worden verstrekt in [elementen uploaden](developer-reference-material-apis.md#asset-upload) in de naslaggids voor ontwikkelaars.

## Tips, aanbevolen procedures en beperkingen {#tips-limitations}

* Directe binaire upload is een nieuwe methode om activa te uploaden. Dit wordt standaard ondersteund door de mogelijkheden en clients van het product, zoals [!DNL Experience Manager] gebruikersinterface, [!DNL Adobe Asset Link], en [!DNL Experience Manager] bureaubladtoepassing. Om het even welke douanecode die door klanten technische teams wordt aangepast of uitgebreid moet nieuwe uploaden APIs en protocollen gebruiken.

* Adobe raadt aan niet meer dan 1000 elementen toe te voegen aan elke map in [!DNL Experience Manager Assets]. U kunt wel meer elementen aan een map toevoegen, maar er kunnen prestatieproblemen optreden, zoals een tragere navigatie naar dergelijke mappen.

* Wanneer u **[!UICONTROL Replace]** in de [!UICONTROL Name Conflict] wordt de element-id opnieuw gegenereerd voor het nieuwe element. Deze id verschilt van de id van het vorige element. Indien [Assets Insights](/help/assets/assets-insights.md) is ingeschakeld voor het bijhouden van indrukken of klikken met [!DNL Adobe Analytics]maakt de opnieuw gegenereerde element-id de gegevensopname voor het element op ongeldig [!DNL Analytics].

* Sommige uploadmethoden verhinderen niet dat u elementen uploadt met [verboden tekens](#filename-handling) in de bestandsnamen. De tekens worden vervangen door `-` symbool.

* Het uploaden van elementen via de browser ondersteunt alleen platte bestandslijsten en geen geneste maphiërarchieën. Als u alle elementen in een geneste map wilt uploaden, kunt u het beste [bureaubladtoepassing](#upload-assets-desktop-clients).

* Met de methode Bulk importeren wordt de volledige mapstructuur geïmporteerd zoals deze op de gegevensbron bestaat. Alleen de niet-lege mappen worden echter gemaakt in [!DNL Experience Manager].


<!-- TBD: Link to file name handling in DA docs when it is documented. 
-->

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [Info [!DNL Adobe Asset Link]](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Technische referentie voor het uploaden van bedrijfsmiddelen](developer-reference-material-apis.md#asset-upload)

