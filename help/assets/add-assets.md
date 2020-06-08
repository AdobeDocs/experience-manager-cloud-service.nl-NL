---
title: Voeg uw digitale middelen toe aan Adobe Experience Manager
description: Voeg uw digitale middelen toe aan Adobe Experience Manager als Cloud Service
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 1%

---


# Digitale middelen toevoegen aan Adobe Experience Manager {#add-assets-to-experience-manager}

Adobe Experience Manager verrijkt de binaire inhoud van de geüploade digitale bestanden met rijke metagegevens, slimme tags, vertoningen en andere DAM-services (Digital Asset Management). U kunt verschillende bestandstypen uploaden van uw lokale map of een netwerkstation naar de middelen van Experience Manager, zoals afbeeldingen, documenten en Raw-afbeeldingsbestanden.

Er is een aantal uploadmethoden beschikbaar. Naast het meest gebruikte uploaden naar de browser bestaan er andere methoden om middelen toe te voegen aan de gegevensopslagruimte van Experience Manager, zoals desktopclients, zoals Adobe Asset Link of Experience Manager, scripts voor het uploaden en opnemen van gegevens die klanten zouden maken, en geautomatiseerde integratie van innamen die als AEM-extensies zouden worden toegevoegd.

We zullen ons hier concentreren op uploadmethoden voor eindgebruikers en koppelingen naar artikelen aanbieden waarin technische aspecten van het uploaden en opnemen van middelen worden beschreven met behulp van API&#39;s en SDK&#39;s van Experience Manager.

Hoewel u elk binair bestand kunt uploaden en beheren in Experience Manager, bieden de meest gebruikte bestandsindelingen ondersteuning voor extra services, zoals het ophalen van metagegevens of het genereren van voorvertoningen. Raadpleeg de [ondersteunde bestandsindelingen](file-format-support.md) voor meer informatie.

Ook kunt u ervoor kiezen om extra verwerkingen uit te voeren voor de geüploade elementen. U kunt een aantal profielen voor middelenverwerking configureren in de map waarin elementen worden geüpload om specifieke metagegevens, uitvoeringen of services voor beeldverwerking toe te voegen. Zie [Aanvullende verwerking](#additional-processing) hieronder voor meer informatie.

>[!NOTE]
>
> Experience Manager als Cloud Service gebruikt een nieuwe manier om elementen te uploaden: directe binaire upload. Deze wordt standaard ondersteund door de productmogelijkheden en clients buiten de verpakking, zoals de AEM-gebruikersinterface, Adobe Asset Link, de AEM-bureaubladtoepassing en dus transparant voor de eindgebruikers.
>
> Upload code die door klanten technische teams wordt aangepast of uitgebreid moet de nieuwe upload APIs en protocollen gebruiken.

## Elementen uploaden {#upload-assets}

Als u een bestand (of meerdere bestanden) wilt uploaden, kunt u de bestanden op uw bureaublad selecteren en naar de gebruikersinterface (webbrowser) naar de doelmap slepen. U kunt het uploaden ook starten vanuit de gebruikersinterface.

1. Navigeer in de gebruikersinterface Elementen naar de locatie waar u digitale elementen wilt toevoegen.
1. Voer een van de volgende handelingen uit om de elementen te uploaden:

   * Tik op het **[!UICONTROL Create]** pictogram op de werkbalk. Tik vervolgens op het menu **[!UICONTROL Files]**. U kunt de naam van het bestand desgewenst wijzigen in het dialoogvenster dat verschijnt.
   * In een browser die HTML5 ondersteunt, sleept u de elementen rechtstreeks naar de gebruikersinterface van Elementen. Het dialoogvenster voor het wijzigen van de naam van het bestand wordt niet weergegeven.
   ![create_menu](assets/create_menu.png)

   Als u meerdere bestanden wilt selecteren, drukt u op Ctrl of Command en selecteert u de elementen in het dialoogvenster Bestandenkiezer. Als u een iPad gebruikt, kunt u slechts één bestand tegelijk selecteren.

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

1. Als u een actieve upload wilt annuleren, klikt u op Sluiten (`X`) naast de voortgangsbalk. Wanneer u het uploaden annuleert, verwijdert AEM Assets het gedeeltelijk geüploade gedeelte van het element.

   Als u het uploaden annuleert voordat de bestanden zijn geüpload, wordt het huidige bestand niet meer geüpload en wordt de inhoud vernieuwd. Bestanden die al zijn geüpload, worden echter niet verwijderd.


<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, AEM saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, AEM consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->


1. In het dialoogvenster Uploadvoortgang in AEM Assets wordt het aantal bestanden weergegeven dat is geüpload en de bestanden die niet zijn geüpload.

Daarnaast wordt in de gebruikersinterface Middelen het meest recente element weergegeven dat u uploadt of de map die u als eerste hebt gemaakt.

>[!NOTE]
>
> Voor het uploaden van geneste maphiërarchieën naar AEM raadpleegt u het [bulkuploaden van elementen](#bulk-upload).

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of your AEM Assets instance. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests AEM Assets can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, AEM assets may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, AEM Assets ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in Crx-de and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to AEM, the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. AEM Assets supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in AEM Assets.

>[!NOTE]
>
>Streaming upload is disabled for AEM running on JEE server with servlet-api version lower than 3.1.
-->

### Uploads verwerken wanneer element al bestaat {#handling-upload-existing-file}

Als u een element uploadt met dezelfde naam als een element dat al beschikbaar is op de locatie waar u het element uploadt, wordt een waarschuwingsvenster weergegeven.

U kunt een bestaand element vervangen, een andere versie maken of beide behouden door de naam van het nieuwe element dat wordt geüpload te wijzigen. Als u een bestaand element vervangt, worden de metagegevens voor het element en eventuele eerdere wijzigingen (bijvoorbeeld annotaties, uitsnijden, enzovoort) die u in het bestaande element hebt aangebracht, verwijderd. Als u ervoor kiest beide elementen te behouden, wordt de naam van het nieuwe element gewijzigd in het nummer dat aan de naam wordt `1` toegevoegd.

>[!NOTE]
>
>Wanneer u **[!UICONTROL Replace]** in het [!UICONTROL Name Conflict] dialoogvenster selecteert, wordt de element-id opnieuw gegenereerd voor het nieuwe element. Deze id verschilt van de id van het vorige element.
>
>Als Asset Insights is ingeschakeld voor het bijhouden van indrukken/klikken met Adobe Analytics, maakt de opnieuw gegenereerde asset-id de gegevensopname voor het element op Analytics ongeldig.

Tik/klik op het dubbele element om het gedupliceerde element in AEM Assets te behouden **[!UICONTROL Keep]**. Tik/klik op het geüploade dubbele element om het geüploade element te verwijderen. **[!UICONTROL Delete]**

### Bestandsnaamverwerking en verboden tekens {#filename-handling}

Met AEM-elementen kunt u geen elementen uploaden met de verboden tekens in de bestandsnaam. Als u een element probeert te uploaden met een bestandsnaam die een niet-toegestaan teken of meer bevat, wordt in AEM Assets een waarschuwingsbericht weergegeven en wordt het uploaden gestopt totdat u deze tekens verwijdert of uploadt met een toegestane naam.

In het [!UICONTROL Upload Assets] dialoogvenster kunt u lange namen opgeven voor de bestanden die u uploadt, zodat deze passen bij specifieke naamconventies voor bestanden voor uw organisatie.

De volgende tekens (lijst met door spaties gescheiden tekens) worden echter niet ondersteund:

* de naam van het elementbestand mag geen elementen bevatten `* / : [ \\ ] | # % { } ? &`
* de naam van de elementenmap mag niet bevatten `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Bulkupload van elementen {#bulk-upload}

Als u een groter aantal bestanden wilt uploaden, vooral als deze zich in een geneste maphiërarchie op schijf bevinden, kunt u de volgende methoden gebruiken:

* Gebruik een aangepast uploadscript of een aangepast gereedschap dat gebruik maakt van API&#39;s voor het uploaden van [elementen](developer-reference-material-apis.md#asset-upload-technical). Een dergelijk aangepast gereedschap kan indien nodig extra elementen verwerken (bijvoorbeeld metagegevens vertalen of de naam van bestanden wijzigen).
* Gebruik de bureaubladtoepassing [van](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) Experience Manager om geneste maphiërarchieën te uploaden.

>[!NOTE]
>
> Bulkupload als onderdeel van de migratie van inhoud van andere systemen wanneer het opzetten en het opstellen aan de Manager van de Ervaring vereist zorgvuldige planning, overweging, en keus van hulpmiddelen. Zie de [implementatiegids](/help/implementing/deploying/overview.md) voor richtlijnen voor de aanpak van contentmigratie.

## Elementen uploaden met desktopclients {#upload-assets-desktop-clients}

In aanvulling op de gebruikersinterface van de webbrowser biedt Experience Manager ondersteuning voor andere clients op het bureaublad. Ze bieden ook uploadervaring zonder dat u naar de webbrowser hoeft te gaan.

* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) biedt toegang tot elementen van AEM in Adobe Photoshop-, Adobe Illustrator- en Adobe InDesign-bureaubladtoepassingen. U kunt het momenteel geopende document rechtstreeks vanuit de gebruikersinterface van Adobe Asset Link uploaden naar AEM vanuit deze bureaubladtoepassingen.
* [De Experience Manager-bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) vereenvoudigt het werken met middelen op het bureaublad, onafhankelijk van het bestandstype of de native toepassing waarin ze worden verwerkt. Het is vooral handig om bestanden in geneste maphiërarchieën vanuit uw lokale bestandssysteem te uploaden, omdat het uploaden van de browser alleen het uploaden van platte bestandslijsten ondersteunt.

## Aanvullende verwerking {#additional-processing}

Als u extra verwerkingen wilt uitvoeren op de geüploade elementen, kunt u profielen voor middelenverwerking gebruiken in de map waarin elementen worden geüpload. Deze bestanden zijn beschikbaar in het **[!UICONTROL Properties]** dialoogvenster Map.

![assets-folder-eigenschappen](assets/assets-folder-properties.png)

De volgende profielen zijn beschikbaar:

* [Met metagegevensprofielen](metadata-profiles.md) kunt u standaardeigenschappen voor metagegevens toepassen op elementen die naar die map zijn geüpload
* [Met verwerkingsprofielen](asset-microservices-configure-and-use.md#processing-profiles) kunt u de verwerking van vertoningen toepassen en uitvoeringen genereren in aanvulling op de standaarduitvoeringen

Als Dynamische media ook in uw omgeving is ingeschakeld:

* Met [afbeeldingsprofielen](dynamic-media/image-profiles.md) kunt u specifieke configuraties voor bijsnijden (**[!UICONTROL Smart Cropping]** en pixels bijsnijden) en verscherpen toepassen op de geüploade assets
* [Met videoprofielen](dynamic-media/video-profiles.md) kunt u specifieke videocoderingsprofielen (resolutie, indeling, parameters) toepassen

>[!NOTE]
>
> Dynamische uitsnijdingen van media en andere bewerkingen op elementen zijn niet-destructief, dat wil zeggen dat ze het geüploade origineel niet wijzigen, maar in plaats daarvan parameters bieden voor uitsnijden of mediatransformatie die moet worden uitgevoerd wanneer de elementen worden geleverd

Voor mappen waaraan een verwerkingsprofiel is toegewezen, wordt de profielnaam weergegeven op de miniatuur in de kaartweergave. In de lijstweergave wordt de profielnaam weergegeven in de **[!UICONTROL Processing Profile]** kolom.

## Elementen uploaden of toevoegen met API&#39;s {#upload-using-apis}

Technische details van de upload APIs en het protocol, en verbindingen aan open-bron SDK en steekproefcliënten worden verstrekt in de sectie van de ontwikkelaarsverwijzing van het [activa uploaden](developer-reference-material-apis.md#asset-upload-technical) .

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager-bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)
>* [Adobe-elementkoppeling](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Documentatie Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Technische referentie voor het uploaden van bedrijfsmiddelen](developer-reference-material-apis.md#asset-upload-technical)

