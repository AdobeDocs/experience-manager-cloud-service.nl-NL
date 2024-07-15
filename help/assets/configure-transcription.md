---
title: Abonnementsservice configureren
description: Adobe Experience Manager Assets wordt gevormd met  [!DNL Azure Media Services]  die automatisch tekstranscriptie van de gesproken taal in een gesteund audio of videodossier in het formaat WebVTT (Vtt) produceert.
products: SG_EXPERIENCEMANAGER/ASSETS and Experience Manager as a Cloud Service
sub-product: assets
content-type: reference
contentOwner: Vishabh Gupta
topic-tags: Configuration
feature: Asset Management, Configuration
role: Admin
exl-id: e96c8d68-74a6-4d61-82dc-20e619338d4b
source-git-commit: 02ad83eb9fa9ed3bf06cf7fe0ef10fd9577f66a9
workflow-type: tm+mt
source-wordcount: '1606'
ht-degree: 0%

---

# Abonnement configureren in [!DNL Experience Manager Assets] {#configure-transcription-service}

Transcriptie is het proces waarbij de audio van een audio- of videobestand in tekst (spraak naar tekst) wordt omgezet met behulp van de spraakherkenningstechnologie.
[!DNL Adobe Experience Manager Assets] is geconfigureerd met [!DNL Azure Media Services] , dat automatisch teksttranscriptie van de gesproken taal genereert in een ondersteund audio- of videobestand in de WebVTT-indeling (.vtt). Wanneer een audio- of video-element wordt verwerkt in [!DNL Experience Manager Assets] , genereert de transcriptieservice automatisch de tekstranscriptie-uitvoering van het audio- of videoelement en slaat deze op dezelfde locatie op in de Assets-opslagplaats waar het oorspronkelijke element zich bevindt. Met de transcriptieservice van [!DNL Experience Manager Assets] kunnen marketers hun audio- en video-inhoud effectief beheren, waarbij de tekstinhoud extra kan worden gedetecteerd en de ROI van deze elementen kan worden verhoogd door toegankelijkheid en lokalisatie te ondersteunen.

Transcripties zijn tekstversies van gesproken inhoud. Een voorbeeld hiervan is een film die u bekijkt op elk OTT-platform dat vaak bijschriften bevat om de toegankelijkheid te verbeteren of de inhoud in andere talen te consumeren. Of een audio- of videobestand dat wordt gebruikt voor marketing, training of entertainmentdoeleinden. Deze ervaringen beginnen met een transcriptie die vervolgens wordt opgemaakt of waar nodig wordt vertaald. Het transcripten van audio of video is een tijdsintensief en foutgevoelig proces wanneer manueel uitgevoerd. Het is ook een uitdaging om het handmatige proces te schalen, gezien de steeds toenemende behoefte aan audio-video-inhoud. [!DNL Experience Manager Assets] gebruikt de op AI gebaseerde transcriptie van Azure die het op grote schaal verwerken van de audio- en video-elementen toestaat en de tekstranscripties (.vtt-bestanden) samen met de tijdstempeldetails genereert. Samen met Assets wordt de transcriptie-functie ook ondersteund in Dynamic Media.

De transcriptie functie is zonder kosten beschikbaar in [!DNL Experience Manager Assets] . De beheerders hebben echter de Azure-referenties van de gebruiker nodig om de transcriptieservice in [!DNL Experience Manager Assets] te configureren. U kunt ook [ de proefgeloofsbrieven ](https://azure.microsoft.com/en-us/pricing/details/media-services/) direct van Microsoft® krijgen om de audio of videobeschrijvingseigenschap in Assets te ervaren.

## Voorwaarden voor transcriptie {#prerequisites}

1. Een actieve [!DNL Experience Manager Assets as a Cloud Service] -instantie.
1. De volgende Azure-referenties zijn vereist voor configuratie in [!DNL Experience Manager Assets] :

   * Client-id (API-sleutel)
   * Clientbeveiligingssleutel
   * Tenant Endpoint (domein)
   * Mediaaccount
   * Brongroep
   * Abonnement-id

   Zie [ Azure documentatie ](https://docs.microsoft.com/en-us/azure/media-services/latest/access-api-howto?tabs=portal) om geloofsbrieven te krijgen om tot Azure Media Services API toegang te hebben.

1. Zorg ervoor dat de Azure-account voldoende krediet heeft om nieuwe aanvragen te verwerken.

## Abonnement configureren in [!DNL Experience Manager Assets] {#configure-transcription}

Hieronder vindt u de configuraties die nodig zijn om de transcriptie-functie in [!DNL Experience Manager Assets] in te schakelen:

1. [Azure Media Services configureren](#configure-azure-media-service)
1. [Verwerkingsprofiel configureren voor audio- of videotranscriptie](#configure-processing-profile-for-transcription)


### Azure Media Services configureren {#configure-azure-media-services}

[!DNL Experience Manager Assets] gebruikt [!DNL Azure Media Services] die automatisch tekstranscripties van de gesproken taal in a [ gesteunde audio of videodossier ](#supported-file-formats-for-transcription) in het formaat WebVTT (.vtt) produceert. De beheerders kunnen [!DNL Azure Media Services] in [!DNL Experience Manager Assets] configureren met behulp van de Azure-referenties. De [ vereisten van de transcriptie ](#transcription-prerequisites) maken een lijst van de [!DNL Azure] geloofsbrieven die voor de configuratie worden vereist. Als u geen [!DNL Azure] rekening en geloofsbrieven hebt, zie [ Azure documentatie van de Diensten van Media ](https://azure.microsoft.com/en-us/pricing/details/media-services/) om proefgeloofsbrieven te krijgen.

![ vorm-transcriptie-dienst ](assets/configure-transcription-service.png)

Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Media Services Configuration]** . Selecteer een map (locatie) in de linkertrack en klik op de knop [!UICONTROL Create] om de verbinding met uw [!DNL Azure] -account te configureren. Deze map is de locatie waar de [!DNL Azure] -cloudconfiguratie is opgeslagen in Experience Manager Assets. Voer de [!DNL Azure] referenties in en klik op **[!UICONTROL Save & Close]** .

### Verwerkingsprofiel voor transcriptie configureren {#configure-processing-profile}

Als [!DNL Azure Media Services] eenmaal is geconfigureerd in Experience Manager Assets, bestaat de volgende stap uit het maken van een middelenverwerkingsprofiel voor het genereren van op AI gebaseerde transcriptie van de audio- en video-elementen. Het op AI-Gebaseerde verwerkingsprofiel produceert transcripties van [ gesteunde audio of videoactiva ](#supported-file-formats-for-transcription) als vertoning in Experience Manager Assets en slaat de transcriptie (.vtt- dossier) in de zelfde omslag op waar het originele element verblijft. Het is dus gemakkelijker voor de gebruikers om het element en de transcriptie-uitvoering te zoeken en te zoeken.

Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en klik op de knop **[!UICONTROL Create]** om een op AI gebaseerd verwerkingsprofiel te maken voor het genereren van transcriptie van uw audio- en videobestanden. Standaard geeft de pagina met het verwerkingsprofiel slechts drie tabbladen weer (Afbeelding, Video en Aangepast). Een tab **[!UICONTROL Content AI]** is echter zichtbaar als u [!DNL Azure Media Services] in de instantie [!DNL Experience Manager Assets] hebt geconfigureerd. Controleer uw [!DNL Azure] -referenties als het tabblad **[!UICONTROL Content AI]** niet wordt weergegeven tijdens het maken van een verwerkingsprofiel.

Klik op het tabblad **[!UICONTROL Content AI]** op de knop **[!UICONTROL Add New]** om de transcriptie te configureren. Hier kunt u de bestandsindelingen (MIME-typen) voor het genereren van transcripties opnemen en uitsluiten door bestandstypen in de vervolgkeuzelijst te selecteren. In de volgende afbeelding worden alle ondersteunde audio- en videobestanden opgenomen en worden de tekstbestanden uitgesloten.

Schakel de schakeloptie **[!UICONTROL Create VTT transcript in same directory]** in om de transcriptie-uitvoering (.vtt-bestand) te maken en op te slaan in dezelfde map als het oorspronkelijke element. De andere uitvoeringen worden ook gegenereerd door de standaard DAM-workflow voor elementverwerking, ongeacht deze instelling.

![ vorm-transcriptie-dienst ](assets/configure-transcription-profile.png)

In de volgende afbeelding wordt een aangepast videoprofiel weergegeven dat in Experience Manager Assets is gemaakt.

![ vorm-transcriptie-dienst ](assets/video-processing-profile.png)

Het videoprofiel bevat ook de volgende aangepaste configuraties. Zie [ documentatie van het verwerkingsprofiel ](/help/assets/asset-microservices-configure-and-use.md) voor details op hoe te om profiel van de douaneverwerking tot stand te brengen.

![ vorm-transcriptie-dienst ](assets/video-processing-profile2.png)

Laten we nu de transcriptie in dit videoprofiel configureren. Navigeer naar het tabblad **[!UICONTROL Content AI]** en klik op de knop **[!UICONTROL Add New]** . Neem alle audio- en videobestanden op en sluit de afbeeldings- en toepassingsbestanden uit. Schakel de schakeloptie **[!UICONTROL Create VTT transcript in same directory]** in en sla de configuratie op.

![ vorm-transcriptie-dienst ](assets/video-processing-profile1.png)

Als het verwerkingsprofiel is geconfigureerd voor het transcripten van audio- en videobestanden, kunt u dit verwerkingsprofiel op een van de volgende manieren toepassen op mappen:

* Selecteer een definitie van het verwerkingsprofiel in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en gebruik de handeling **[!UICONTROL Apply Profile to Folders]** . Met de inhoudbrowser kunt u naar een specifieke map navigeren, map selecteren en de toepassing van het profiel bevestigen.
* Selecteer een map in de Assets-gebruikersinterface en klik op **[!UICONTROL Properties]** Handeling om de eigenschappen van mappen te openen. Klik op de tab **[!UICONTROL Asset Processing]** en selecteer in de lijst **[!UICONTROL Processing Profile]** het juiste verwerkingsprofiel voor de map. Klik op **[!UICONTROL Save & Close]** om de wijzigingen op te slaan.

  ![ vorm-transcriptie-dienst ](assets/video-processing-profile3.png)

* Gebruikers kunnen mappen of specifieke elementen in de Assets-gebruikersinterface selecteren om een verwerkingsprofiel toe te passen en vervolgens **[!UICONTROL Reprocess Assets]** kiezen uit de opties die bovenaan beschikbaar zijn.

>[!TIP]
>Er kan slechts één verwerkingsprofiel worden toegepast op een map.
>
>Nadat een verwerkingsprofiel is toegepast op een map, worden alle nieuwe elementen die in deze map of een van de submappen van deze map zijn geüpload (of bijgewerkt), verwerkt met behulp van het extra verwerkingsprofiel dat is geconfigureerd. Deze verwerking is een aanvulling op het standaardprofiel.

>[!NOTE]
>
>Een verwerkingsprofiel dat is toegepast op een map, werkt voor de gehele structuur. Een ander profiel kan echter worden overschreven wanneer een submap wordt toegepast.
>
>Wanneer middelen aan een omslag worden geupload, communiceert de Experience Manager met de bevattende eigenschappen van de omslag om het verwerkingsprofiel te identificeren. Als er geen toepassing is, wordt gecontroleerd of er een verwerkingsprofiel van toepassing is in een bovenliggende map in de hiërarchie.


## Abonnement op audio- of video-elementen genereren {#generate-transcription}

Wanneer het verwerken van een videoactiva, [ op AI-Gebaseerde verwerkingsprofiel ](#configure-processing-profile-for-transcription) automatisch de transcriptie (.vtt- dossier) als vertoning samen met oorspronkelijke activa in de zelfde omslag produceert.

![ vorm-transcriptie-dienst ](assets/transcript1.png)

U kunt de transcriptie-uitvoering ook zien door de uitvoeringen van het oorspronkelijke video-element te openen. Als u het deelvenster **[!UICONTROL Renditions]** wilt openen, selecteert u het oorspronkelijke video-element en opent u de linkertrack. U ziet dat de transcriptie-uitvoering (.vtt-bestand) zichtbaar is onder de kop van **[!UICONTROL TRANSCRIPTVTT]** .

![ vorm-transcriptie-dienst ](assets/transcript.png)

U kunt de transcriptie (vtt-tekstbestand) rechtstreeks vanuit de map downloaden als een aparte elementuitvoering, of vanuit het deelvenster **[!UICONTROL Renditions]** van het oorspronkelijke element door alle uitvoeringen van het element te downloaden.

Experience Manager biedt momenteel geen ondersteuning voor het native voorvertonen van volledige tekst of het bewerken van VTT-bestanden. U kunt de transcriptie echter downloaden en een teksteditor gebruiken om de transcriptie te bewerken of te verifiëren. De transcriptie weerspiegelt de gesproken taal als tekst op het opgegeven tijdstempel in de video met de betrouwbaarheidsscore (nauwkeurigheid) van de transcriptie.

![ vorm-transcriptie-dienst ](assets/transcript-text.png)

## Transcriptie gebruiken in Dynamic Media {#using-transcription-in-dynamic-media}

Als u [ gevormd Dynamic Media ](/help/assets/dynamic-media/config-dm.md) in uw instantie van Experience Manager Assets hebt, kunt u activa (audio of videodossier) en zijn transcriptie (vtdossier) aan Dynamic Media publiceren. Op deze manier worden het oorspronkelijke element (audio- of videobestand) en de transcriptie (vtt-bestand) in dezelfde map gepubliceerd naar Dynamic Media. De beheerder van Dynamic Media kan [ CC Gesloten ervaring van de Titel ](/help/assets/dynamic-media/video.md#adding-captions-to-video) voor het audio of videodossier toelaten gebruikend de transcriptie vertoning (.vtt- dossier).

Zie ook:

* [ Videozelfstudie op hoe te om CC Gesloten Bijschrift aan de video van Dynamic Media toe te voegen ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html#add-cc-closed-captioning-to-dynamic-media-video)
* [Publish Dynamic Media-video&#39;s naar YouTube](/help/assets/dynamic-media/video.md#publishing-videos-to-youtube)

In de volgende afbeelding geeft de URL het bijschriftgedeelte weer dat naar de transcriptie (.vtt-bestand) verwijst. De video weerspiegelt de gesproken taal (getranscripte tekst) als een **[!UICONTROL Closed Caption]** op het opgegeven tijdstempel in de video. De gebruiker kan het bijschrift in- of uitschakelen met de knop **[!UICONTROL CC]** .

![ vorm-transcriptie-dienst ](assets/transcript-example.png)

## Ondersteunde bestandsindelingen voor transcriptie {#supported-file-format}

De volgende indelingen voor audio- en videobestanden worden ondersteund voor transcriptie:

| Ondersteunde audio- of video-indelingen | Extensies |
|----|----|
| FLV (met H.264- en AAC-codecs) | (.flv) |
| MXF | (.mxf) |
| MPEG2-PS, MPEG2-TS, 3GP | (.ts, .ps, .3gp, .3gpp, .mpg) |
| Windows Media Video (WMV)/ASF | (.wmv, .asf) |
| AVI (niet-gecomprimeerd 8 bits/10 bits) | (.avi) |
| MP4 | (.mp4, .m4a, .m4v) |
| Microsoft® Digital Video Recording (DVR-MS) | (.dvr-ms) |
| Matroska/WebM | (.mkv) |
| WAVE/WAV | (.wav) |
| QuickTime | (.mov) |


>[!NOTE]
>
>De elementen (audio- of videobestanden) die van het toepassingstype zijn, worden niet ondersteund voor transcriptie.

## Bekende beperkingen {#known-limitations}

* De transcriptie functie wordt ondersteund voor video&#39;s met een duur van maximaal 10 minuten.
* De titel van de video moet uit maximaal 80 tekens bestaan.
* De ondersteunde bestandsgrootte is maximaal 15 GB.
* De maximale verwerkingstijd die wordt ondersteund, is 60 minuten.
* In een betaalaccount van [!DNL Azure] kunt u maximaal 50 films per minuut uploaden. In een proefaccount kunt u echter maximaal vijf films per minuut uploaden.

## Tips voor het oplossen van problemen {#troubleshooting}

Meld u aan bij uw [!DNL Azure Media Services] -account met dezelfde referenties (die u voor de configuratie hebt gebruikt) om de aanvraagstatus te controleren. Neem contact op met de [!DNL Azure] -ondersteuning als uw aanvraag niet correct is verwerkt.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
