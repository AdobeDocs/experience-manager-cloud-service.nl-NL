---
title: Voeg uw digitale middelen toe aan [!DNL Adobe Experience Manager].
description: Voeg uw digitale middelen toe aan [!DNL Adobe Experience Manager] als [!DNL Cloud Service].
feature: Asset Ingestion, Asset Management, Asset Processing, Upload
role: User, Admin
exl-id: 0e624245-f52e-4082-be21-13cc29869b64
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '3071'
ht-degree: 0%

---

# Digitale elementen toevoegen aan [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [!DNL Assets] {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager Assets] accepteert veel typen digitale elementen van vele bronnen. De binaire en gemaakte uitvoeringen worden opgeslagen, er kunnen middelen worden verwerkt met behulp van verschillende workflows en [!DNL Adobe Sensei] de diensten, staat voor distributie door vele kanalen over vele oppervlakten toe.

[!DNL Adobe Experience Manager] Verrijkt de binaire inhoud van de geüploade digitale bestanden met rijke metagegevens, slimme tags, uitvoeringen en andere DAM-services (Digital Asset Management). U kunt verschillende bestandstypen uploaden van uw lokale map of een netwerkstation naar [!DNL Experience Manager Assets].

Naast de meest gebruikte browser uploadt, andere methodes om activa aan te voegen [!DNL Experience Manager] opslagplaats bestaat. Tot deze andere methoden behoren desktopclients, zoals Adobe Asset Link of [!DNL Experience Manager] desktop app, upload en opname scripts die klanten zouden maken, en geautomatiseerde integratie van indelingen toegevoegd als [!DNL Experience Manager] extensies.

Terwijl u elk binair bestand kunt uploaden en beheren in [!DNL Experience Manager]De meest gebruikte bestandsindelingen bieden ondersteuning voor aanvullende services, zoals het ophalen van metagegevens of het genereren van voorvertoningen. Zie [ondersteunde bestandsindelingen](file-format-support.md) voor meer informatie.

Ook kunt u ervoor kiezen om extra verwerkingen uit te voeren voor de geüploade elementen. Verschillende profielen voor middelenverwerking kunnen worden geconfigureerd in de map waarin elementen worden geüpload om specifieke metagegevens, uitvoeringen of services voor beeldverwerking toe te voegen. Zie [proceselementen bij uploaden](#process-when-uploaded).

[!DNL Assets] Geef de volgende uploadmethoden op. Adobe raadt u aan om uw gebruiksscenario en toepasselijkheid van een uploadoptie te begrijpen voordat u deze gebruikt.

| Upload, methode | Wanneer gebruiken? | Primaire persoon |
|---------------------|----------------|-----------------|
| [Gebruikersinterface middelenconsole](#upload-assets) | Soms uploaden, indrukken en slepen, zoeken naar uploaden. Gebruik deze optie niet om veel elementen te uploaden. | Alle gebruikers |
| [API uploaden](#upload-using-apis) | Voor dynamische beslissingen tijdens het uploaden. | Developer |
| [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Lage hoeveelheden asset opnemen, maar niet voor migratie. | Beheerder, Marketer |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Nuttig wanneer creatieve en marketingmedewerkers werken aan middelen van binnen de ondersteunde [!DNL Creative Cloud] bureaubladtoepassingen. | Creatief, Marketer |
| [Bulkingestor](#asset-bulk-ingestor) | Aanbevolen voor grootschalige migraties en incidentele bulkopname. Alleen voor ondersteunde datastores. | Beheerder, ontwikkelaar |

## Elementen uploaden {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Select the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

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

>[!IMPORTANT]
>
>Elementen die u uploadt naar een Experience Manager met een bestandsnaam die groter is dan 100 tekens, krijgen een kortere naam wanneer ze worden gebruikt in Dynamic Media.
>
>De eerste 100 tekens in de bestandsnaam worden als volgt gebruikt. De resterende tekens worden vervangen door een alfanumerieke tekenreeks. Deze methode voor het wijzigen van de naam garandeert een unieke naam wanneer het element in Dynamic Media wordt gebruikt. Het is ook bedoeld om rekening te houden met de maximale lengte voor elementbestanden die in Dynamic Media is toegestaan.


1. In de [!DNL Assets] navigeer in de gebruikersinterface naar de locatie waar u digitale elementen wilt toevoegen.
1. Voer een van de volgende handelingen uit om de elementen te uploaden:

   * Klik op de werkbalk op **[!UICONTROL Create]** > **[!UICONTROL Files]**. U kunt de naam van het bestand desgewenst wijzigen in het dialoogvenster dat verschijnt.
   * In browser die HTML5 steunt, sleep de activa direct op [!DNL Assets] gebruikersinterface. Het dialoogvenster voor het wijzigen van de naam van het bestand wordt niet weergegeven.

   ![create_menu](assets/create_menu.png)

   Als u meerdere bestanden wilt selecteren, selecteert u de `Ctrl` of de `Command` en selecteert u de elementen in het dialoogvenster Bestandenkiezer. Als u een iPad gebruikt, kunt u slechts één bestand tegelijk selecteren.

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

### Uploads voor bestaande elementen verwerken {#handling-upload-existing-file}

U kunt een element uploaden met hetzelfde pad (dezelfde naam en dezelfde locatie) als een bestaand element. Er wordt echter een waarschuwingsvenster weergegeven met de volgende opties:

* Bestaande element vervangen: als u een bestaand element vervangt, worden de metagegevens voor het element en eventuele eerdere wijzigingen (bijvoorbeeld annotaties en bijsnijden) die u in het bestaande element hebt aangebracht, verwijderd.

  >[!NOTE]
  >
  >De optie om elementen te vervangen is niet beschikbaar als het element is vergrendeld of uitgecheckt.

* Een andere versie maken: er wordt een nieuwe versie van het bestaande element gemaakt in de repository. U kunt de twee versies weergeven in het dialoogvenster [!UICONTROL Timeline] en kan zo nodig terugkeren naar de vorige bestaande versie.
* Beide houden: als u beide elementen wilt behouden, wordt de naam van het nieuwe element gewijzigd.

Het dubbele element behouden in [!DNL Assets], klikt u op **[!UICONTROL Keep]**. Als u het geüploade dubbele element wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

### Bestandsnaamverwerking en verboden tekens {#filename-handling}

[!DNL Experience Manager Assets] Hiermee voorkomt u dat elementen met de verboden tekens in de bestandsnaam worden geüpload. Als u een element probeert te uploaden met bestandsnamen die een niet-toegestaan teken of meer bevatten, [!DNL Assets] geeft een waarschuwingsbericht weer en stopt de upload totdat u deze tekens verwijdert of uploadt met een toegestane naam.

Als u de specifieke naamgevingsconventies voor uw organisatie wilt aanpassen, [!UICONTROL Upload Assets] kunt u lange namen opgeven voor de bestanden die u uploadt. De volgende tekens (lijst met door spaties gescheiden tekens) worden niet ondersteund:

* Ongeldige tekens voor elementnaam: `* / : [ \\ ] | # % { } ? &`
* Ongeldige tekens voor naam van elementmap: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Bulkupload-elementen {#bulk-upload}

De grote leverancier van bedrijfsmiddelen kan veel bedrijfsmiddelen efficiënt verwerken. Een grootschalige inname is echter niet alleen een grote bestandsstortplaats of een tijdelijke migratie. Voor een grootschalig project om een zinvol project te zijn dat uw bedrijfsdoel dient en efficiënt is, plant de migratie en leidt de middelenorganisatie. Alle ingesties zijn verschillend zo in plaats van generaliserend, factor in de genuanceerde bewaarplaats samenstelling en bedrijfsbehoeften. Hieronder volgen enkele overkoepelende suggesties voor het plannen en uitvoeren van bulkopname:

* Curate-elementen: verwijder elementen die niet nodig zijn in de DAM. Overweeg ongebruikte, verouderde of dubbele elementen te verwijderen. Dergelijke huishouden vermindert de overgedragen gegevens en opgenomen activa die tot snellere inname leiden.
* Elementen ordenen: u kunt de inhoud in een logische volgorde ordenen, bijvoorbeeld op bestandsgrootte, bestandsindeling, gebruik van hoofdletters en kleine letters of prioriteit. Over het algemeen is voor grote complexe bestanden meer verwerking nodig. U kunt ook overwegen grote bestanden afzonderlijk in te voegen met de filteroptie voor bestandsgrootte (hieronder beschreven).
* Staggeringestie: Overweeg uw inname op te delen in meerdere bulkinname-projecten. Met q kunt u de inhoud sneller zien en zonodig uw opname bijwerken. U kunt bijvoorbeeld verwerkingsintensieve elementen opnemen tijdens niet-piekuren of geleidelijk in meerdere stukken. U kunt echter kleinere en eenvoudigere elementen invoeren die niet veel verwerkingstijd in één keer vereisen.

Als u een groter aantal bestanden wilt uploaden, gebruikt u een van de volgende methoden. Zie ook de [gebruiksgevallen en -methoden](#upload-methods-comparison)

* [API&#39;s voor middelenupload](developer-reference-material-apis.md#asset-upload): Gebruik een aangepast uploadscript of een aangepast gereedschap dat API&#39;s gebruikt om aanvullende verwerking van elementen toe te voegen (bijvoorbeeld metagegevens vertalen of bestanden hernoemen), indien nodig.
* [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html): Nuttig voor creatieve professionals en marketers die middelen uploaden vanaf hun lokale bestandssysteem. Gebruik deze optie om geneste mappen te uploaden die lokaal beschikbaar zijn.
* [Gereedschap Bulkopname](#asset-bulk-ingestor): Wordt gebruikt voor inname van grote hoeveelheden elementen, soms of in eerste instantie bij implementatie [!DNL Experience Manager].

### Gereedschap Asset Bulk importeren {#asset-bulk-ingestor}

Het hulpmiddel wordt verstrekt slechts aan de groep van beheerders voor grootschalige opname van activa van Azure of S3 datastores te gebruiken. Bekijk een videodemo van de configuratie en opname.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

De volgende afbeelding illustreert de verschillende fasen wanneer u elementen vanuit een gegevensopslagruimte in een Experience Manager invoert:

![Bulkopname](assets/bulk-ingestion.png)

**Vereisten**

Voor het gebruik van deze functie is een externe opslagaccount of emmer uit Azure of AWS vereist.

>[!NOTE]
>
>Maak de container of het emmertje van de opslagaccount als privé en accepteer alleen verbindingen van geoorloofde verzoeken. Aanvullende beperkingen op ingangsnetwerkverbindingen worden echter niet ondersteund.

>[!NOTE]
>
>Externe opslagaccounts kunnen andere naamregels voor bestanden/mappen hebben dan het gereedschap Bulk importeren. Zie [Bestandsnamen verwerken tijdens bulkimport](#filename-handling-bulkimport) voor meer informatie over namen die niet zijn toegestaan of die niet zijn beschermd.


### Het gereedschap Bulkimport configureren {#configure-bulk-ingestor-tool}

Voer de volgende stappen uit om het gereedschap Bulk importeren te configureren:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]**. Selecteer de **[!UICONTROL Create]** -optie.

1. Geef een titel op voor de configuratie voor bulkimport in het dialoogvenster **[!UICONTROL Title]** veld.

1. Selecteer het gegevenstype van de gegevensbron in het menu **[!UICONTROL Import Source]** vervolgkeuzelijst.

1. Geef de waarden op om een verbinding met de gegevensbron te maken. Als u bijvoorbeeld **Azure Blob Storage** als gegevensbron, specificeer de waarden voor Azure opslagrekening, Azure blob container, en Azure toegangssleutel.

1. Selecteer de vereiste authentificatiemodus van de drop-down lijst. **Azure Access Key** volledige toegang biedt tot de Azure-opslagaccount, terwijl **Azure SAS Token** staat de beheerder toe om de mogelijkheden van het teken te beperken gebruikend toestemmingen en vervalsingsbeleid.

1. Geef de naam op van de hoofdmap die elementen bevat in de gegevensbron in het dialoogvenster **[!UICONTROL Source Folder]** veld.

1. (Optioneel) Geef de minimale bestandsgrootte van elementen op in MB om ze op te nemen in het innameproces in het dialoogvenster **[!UICONTROL Filter by Min Size]** veld.

1. (Optioneel) Geef de maximale bestandsgrootte van elementen op in MB om ze op te nemen in het innameproces in het dialoogvenster **[!UICONTROL Filter by Max Size]** veld.

1. (Optioneel) Geef een door komma&#39;s gescheiden lijst op met MIME-typen die u wilt uitsluiten van de opname in het dialoogvenster **[!UICONTROL Exclude MIME Types]** veld. Bijvoorbeeld: `image/jpeg, image/.*, video/mp4`. Zie [alle ondersteunde bestandsindelingen](/help/assets/file-format-support.md).

1. Geef een door komma&#39;s gescheiden lijst op met MIME-typen die u wilt opnemen in de opname in het dialoogvenster **[!UICONTROL Include MIME Types]** veld. Zie [alle ondersteunde bestandsindelingen](/help/assets/file-format-support.md).

1. Selecteer de **[!UICONTROL Delete source file after import]** als u de oorspronkelijke bestanden uit de opslag van brongegevens wilt verwijderen nadat de bestanden zijn geïmporteerd in [!DNL Experience Manager].

1. Selecteer de **[!UICONTROL Import Mode]**. Selecteren **Overslaan**, **Vervangen**, of **Versie maken**. De modus Overslaan is de standaardinstelling en in deze modus slaat de functie Instantor over om een element te importeren als dit al bestaat. Zie de betekenis van [versieopties vervangen en maken](#handling-upload-existing-file).

1. Om een plaats in DAM te bepalen waar de activa moeten worden ingevoerd gebruikend **[!UICONTROL Assets Target Folder]** veld, geeft u een pad op. Bijvoorbeeld: `/content/dam/imported_assets`.

1. (Optioneel) Geef het metagegevensbestand op dat u wilt importeren, in CSV-indeling, in het dialoogvenster **[!UICONTROL Metadata File]** veld. Geef het CSV-bestand op de locatie van het bronblob en raadpleeg het pad tijdens het configureren van het gereedschap Bulk importeren. De CSV-bestandsindeling waarnaar in dit veld wordt verwezen, is dezelfde als de CSV-bestandsindeling wanneer u [Metagegevens van elementen in bulk importeren en exporteren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/metadata-import-export.html). Als u **Bronbestand verwijderen na importeren** filter CSV-bestanden met behulp van de **Uitsluiten** of **MIME-type opnemen** of **Filteren op pad/bestand** velden. U kunt een reguliere expressie gebruiken om CSV-bestanden in deze velden te filteren.

1. Klikken **[!UICONTROL Save]** om de configuratie op te slaan.

### De configuratie van het gereedschap Bulkimport beheren {#manage-bulk-import-configuration}

Na het creëren van het Bulk het hulpmiddelconfiguratie van de Invoer, kunt u taken uitvoeren om de configuratie vóór bulk te evalueren het opnemen van activa aan uw instantie van de Experience Manager. Om de beschikbare opties te bekijken om uw het hulpmiddelconfiguratie van de Invoer van het Bulk te beheren, selecteer de configuratie beschikbaar bij **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]**.

### De configuratie bewerken {#edit-configuration}

Om de configuratiedetails uit te geven, selecteer de configuratie, en klik dan **[!UICONTROL Edit]**. U kunt de titel van de configuratie en de gegevensbron van het voer niet uitgeven terwijl het uitvoeren van geeft verrichting uit.

### De configuratie verwijderen {#delete-configuration}

Selecteer de configuratie en klik op **[!UICONTROL Delete]** om de configuratie van de Invoer van het Bulk te schrappen.

### Verbinding met gegevensbron valideren {#validate-connection}

Als u de verbinding met de gegevensbron wilt valideren, selecteert u de configuratie en klikt u op **[!UICONTROL check]**. Als de verbinding succesvol is, toont de Experience Manager het volgende bericht:

![Bericht met succes bij importeren van bulkgoederen](assets/bulk-import-success-message.png)

### Een testrun aanroepen voor de Bulk Import-taak {#invoke-test-run-bulk-import}

Selecteer de configuratie en klik op **[!UICONTROL Dry Run]** om een testlooppas voor de BulkTaak van de Invoer aan te halen. Experience Manager geeft de volgende gegevens weer over de Bulk Import-taak:

![Droog resultaat](assets/dry-assets-result.png)

### Bestandsnamen verwerken tijdens bulkimport {#filename-handling-bulkimport}

Wanneer u elementen of mappen in bulk importeert, [!DNL Experience Manager Assets] importeert de gehele structuur van wat er in de invoerbron bestaat. [!DNL Experience Manager] volgt de ingebouwde regels voor speciale tekens in de naam van het element en de map. Deze bestandsnamen moeten daarom worden ontsmet. Voor zowel de mapnaam als de elementnaam blijft de door de gebruiker gedefinieerde titel ongewijzigd en wordt deze opgeslagen in `jcr:title`.

Tijdens de bulkinvoer [!DNL Experience Manager] zoekt u naar de bestaande mappen om te voorkomen dat de elementen en mappen opnieuw worden geïmporteerd, en controleert u ook de ontsmettingsregels die zijn toegepast in de bovenliggende map waar het importeren plaatsvindt. Als de ontsmettingsregels worden toegepast in de bovenliggende map, worden dezelfde regels toegepast op de importbron. Voor nieuwe importbewerkingen worden de volgende ontsmettingsregels toegepast om de bestandsnamen van elementen en mappen te beheren.

**Namen die niet zijn toegestaan tijdens bulkimport**

De volgende tekens zijn niet toegestaan in bestands- en mapnamen:

* Besturings- en privé-gebruik (0x00 tot 0x1F, \u0081, \uE000)
* Bestands- of mapnamen die eindigen met een punt (.)

Bestanden of mappen met namen die aan deze voorwaarden voldoen, worden tijdens het importproces overgeslagen en gemarkeerd als mislukt.

**Elementnaam verwerken in bulkimport**

Voor namen van elementbestanden worden de naam en het pad van de JCR gesimuleerd met behulp van de API: `JcrUtil.escapeIllegalJcrChars`.

* Unicode-tekens worden niet gewijzigd
* Vervang de speciale tekens bijvoorbeeld door hun URL Escape-code. `new%asset.png` wordt bijgewerkt naar `new%25asset.png`:

  ```
                  URL escape code   
  
  "               %22
  %               %25
  '               %27
  *               %2A
  /               %2F
  :               %3A
  [               %5B
  \n              %0A
  \r              %0D
  \t              %09
  ]               %5D
  |               %7C
  ```

**Mapnaam verwerken in bulkimport**

Voor mapbestandsnamen worden de naam en het pad van de JCR ontsmet met behulp van de API: `DamUtil.getSanitizedFolderName`.

* Hoofdletters worden omgezet in kleine letters
* Unicode-tekens worden niet gewijzigd
* De speciale tekens bijvoorbeeld vervangen door een streepje (&#39;-&#39;) `new folder` wordt bijgewerkt naar `new-folder`:

  ```
  "                           
  #                         
  %                           
  &                          
  *                           
  +                          
  .                           
  :                           
  ;                          
  ?                          
  [                           
  ]                           
  ^                         
  {                         
  }                         
  |                           
  /         It is used for split folder in cloud storage and is pre-handled, no conversion here.
  \         Not allowed in Azure, allowed in AWS.
  \t
  space     It is the space character.
  ```

<!-- 
[!DNL Experience Manager Assets] manages the forbidden characters in the filenames while you upload assets or folders. [!DNL Experience Manager] updates only the node names in the DAM repository. However, the `title` of the asset or folder remains unchanged.

Following are the file naming conventions that are applied while uploading assets or folders in [!DNL Experience Manager Assets]:

| Characters &Dagger; | When occurring in file names | When occurring in folder names | Example |
|---|---|---|---|
| `. / : [ ] | *` | Replaced with `-` (hyphen). | Replaced with `-` (hyphen). A `.` (dot) in the filename extension is retained as is. | Replaced with `-` (hyphen). | `myimage.jpg` remains as is and `my.image.jpg` changes to `my-image.jpg`. |
| `% ; # , + ? ^ { } "` and whitespaces | Whitespaces are retained | Replaced with `-` (hyphen). | `My Folder.` changes to `my-folder-`. |
| `# % { } ? & .` | Replaced with `-` (hyphen). | NA. | `#My New File.` changes to `-My New File-`. |
| Uppercase characters | Casing is retained as is. | Changed to lowercase characters. | `My New Folder` changes to `my-new-folder`. |
| Lppercase characters | Casing is retained as is. | Casing is retained as is. | NA. |

&Dagger; The list of characters is a whitespace-separated list.
-->

#### Eenmalige of terugkerende bulkimport plannen {#schedule-bulk-import}

Voer de volgende stappen uit om een eenmalige of terugkerende bulkimport te plannen:

1. Maak een configuratie voor bulkimport.
1. Selecteer de configuratie en selecteer **[!UICONTROL Schedule]** op de werkbalk.
1. Stel een eenmalige opname in of voer een uur-, dag- of wekelijks schema in. Klik op **[!UICONTROL Submit]**.

   ![Taak bulkingestor plannen](assets/bulk-ingest-schedule1.png)


#### De doelmap Middelen weergeven {#view-assets-target-folder}

Als u de doellocatie van de middelen wilt weergeven waar de elementen worden geïmporteerd nadat de Bulkimporttaak is uitgevoerd, selecteert u de configuratie en klikt u vervolgens op **[!UICONTROL View Assets]**.

#### Het gereedschap Bulkimport uitvoeren {#run-bulk-import-tool}

Na [configureren van het gereedschap Bulkimport](#configure-bulk-ingestor-tool) en optioneel [de configuratie van het gereedschap Bulkimport beheren](#manage-bulk-import-configuration)kunt u de configuratietaak uitvoeren om de bulkopname van elementen te starten.

Als u het Bulk-importproces wilt starten, gaat u naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]**, selecteert u de [Configuratie voor Bulkimport](#configure-bulk-ingestor-tool)en klik vervolgens op **[!UICONTROL Run]**. Klikken **[!UICONTROL Run]** nogmaals ter bevestiging.

Experience Manager werkt de status van de taak bij naar **Verwerking** en **Geslaagd** als de taak met succes is voltooid. Klik op **Elementen weergeven**.

Wanneer de taak wordt uitgevoerd, kunt u ook de configuratie selecteren en op **Stoppen** om het bulkingestitieproces te stoppen. Klikken **Uitvoeren** om het proces te hervatten. U kunt ook op **Droog** de details te kennen van de activa die nog moeten worden geïmporteerd.

#### Taken beheren na uitvoering {#manage-jobs-after-execution}

Met Experience Manager kunt u de geschiedenis van de bulkimporttaken bekijken. De taakgeschiedenis bestaat uit de status van de taak, de maker van de taak, de logbestanden, samen met andere gegevens zoals de begindatum en -tijd, de datum en tijd en de einddatum en -tijd.

Om tot de baangeschiedenis voor een configuratie toegang te hebben, selecteer de configuratie en klik **[!UICONTROL Job History]**. Selecteer een taak en klik op **Openen**.

![Taak bulkingestor plannen](assets/job-history-bulk-import.png)

Experience Manager geeft de taakgeschiedenis weer. Op de pagina Opsommingtaakhistorie kunt u ook op **Verwijderen** om die baan voor de Bulk configuratie van de Invoer te schrappen.


## Elementen uploaden met desktopclients {#upload-assets-desktop-clients}

Naast de gebruikersinterface van de webbrowser [!DNL Experience Manager] ondersteunt andere clients op het bureaublad. Ze bieden ook uploadervaring zonder dat u naar de webbrowser hoeft te gaan.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) biedt toegang tot elementen van [!DNL Experience Manager] in Adobe Photoshop-, Adobe Illustrator- en Adobe InDesign-bureaubladtoepassingen. U kunt het momenteel geopende document uploaden naar [!DNL Experience Manager] rechtstreeks vanuit de gebruikersinterface Adobe Asset Link vanuit deze bureaubladtoepassingen.
* [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) vereenvoudigt het werken met middelen op Desktop, onafhankelijk op hun dossiertype of inheemse toepassing die hen behandelt. Het is handig om bestanden in geneste maphiërarchieën vanuit uw lokale bestandssysteem te uploaden, omdat het uploaden van de browser alleen het uploaden van platte bestandslijsten ondersteunt.

## Elementen verwerken bij het uploaden {#process-when-uploaded}

Als u de geüploade elementen extra wilt verwerken, kunt u verwerkingsprofielen toepassen op de uploadmappen. De profielen zijn beschikbaar in het dialoogvenster **[!UICONTROL Properties]** pagina van een map in [!DNL Assets]. Een digitaal element zonder extensie of met een onjuiste extensie wordt niet naar wens verwerkt. Wanneer u dergelijke elementen uploadt, gebeurt er bijvoorbeeld niets of wordt een onjuist verwerkingsprofiel toegepast op het element. Gebruikers kunnen de binaire bestanden nog steeds opslaan in de DAM.

![Eigenschappen van een elementmap met opties voor het toevoegen van een verwerkingsprofiel](assets/assets-folder-properties.png)

De volgende tabbladen zijn beschikbaar:

* [Metagegevensprofielen](metadata-profiles.md) Hiermee kunt u standaardeigenschappen van metagegevens toepassen op elementen die naar die map zijn geüpload.
* [Profielen verwerken](asset-microservices-configure-and-use.md) Hiermee kunt u meer uitvoeringen genereren dan standaard mogelijk is.

Ook als [!DNL Dynamic Media] is op uw plaatsing toegelaten, zijn de volgende lusjes beschikbaar:

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

* Adobe raadt aan niet meer dan 1000 elementen aan elke map toe te voegen in [!DNL Experience Manager Assets]. Als u dit probeert, kunt u een waarschuwingsbericht krijgen die zegt, &quot;Deze folder bevat meer dan 1000 punten. Uploads en nieuwe omslagverwezenlijking kunnen worden vertraagd.&quot; U kunt nog steeds meer elementen aan een map toevoegen, maar er kunnen prestatieproblemen optreden, zoals een tragere navigatie naar dergelijke mappen.

* Wanneer u **[!UICONTROL Replace]** in de [!UICONTROL Name Conflict] wordt de element-id opnieuw gegenereerd voor het nieuwe element. Deze id verschilt van de id van het vorige element. Indien [Assets Insights](/help/assets/assets-insights.md) is ingeschakeld voor het bijhouden van indrukken of klikken met [!DNL Adobe Analytics]maakt de opnieuw gegenereerde element-id de gegevensopname voor het element op ongeldig [!DNL Analytics].

* Sommige uploadmethoden verhinderen niet dat u elementen uploadt met [verboden tekens](#filename-handling) in de bestandsnamen. De tekens worden vervangen door `-` symbool.

* Het uploaden van elementen via de browser ondersteunt alleen platte bestandslijsten en geen geneste maphiërarchieën. Als u alle elementen in een geneste map wilt uploaden, kunt u het beste [bureaubladtoepassing](#upload-assets-desktop-clients).

* Met de methode Bulk importeren wordt de volledige mapstructuur geïmporteerd zoals deze op de gegevensbron bestaat. Alleen de niet-lege mappen worden echter gemaakt in [!DNL Experience Manager].


<!-- TBD: Link to file name handling in DA docs when it is documented. 
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

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [Info [!DNL Adobe Asset Link]](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] documentatie](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Technische referentie voor het uploaden van bedrijfsmiddelen](developer-reference-material-apis.md#asset-upload)
