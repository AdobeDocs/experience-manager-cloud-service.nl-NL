---
title: Abonnementsservice configureren
description: Adobe Experience Manager Assets is geconfigureerd met [!DNL Azure Media Services] waarmee automatisch teksttranscriptie van de gesproken taal wordt gegenereerd in een ondersteund audio- of videobestand in de indeling WebVTT (Vtt).
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
[!DNL Adobe Experience Manager Assets] is geconfigureerd met [!DNL Azure Media Services] waarmee automatisch teksttranscriptie van de gesproken taal wordt gegenereerd in een ondersteund audio- of videobestand in de WebVTT-indeling (.vtt). Wanneer een audio- of videoelement wordt verwerkt in [!DNL Experience Manager Assets], genereert de transcriptieservice automatisch de tekstranscriptie-uitvoering van het audio- of videoelement en slaat deze op dezelfde locatie op in de gegevensopslagruimte waar het oorspronkelijke element zich bevindt. De [!DNL Experience Manager Assets] Met de transcriptieservice kunnen marketers hun audio- en video-inhoud effectief beheren met extra ontdekkingsmogelijkheden voor de tekstinhoud en de ROI van deze elementen verhogen door toegankelijkheid en lokalisatie te ondersteunen.

Transcripties zijn tekstversies van gesproken inhoud. Een voorbeeld hiervan is een film die u bekijkt op elk OTT-platform dat vaak bijschriften bevat om de toegankelijkheid te verbeteren of de inhoud in andere talen te consumeren. Of een audio- of videobestand dat wordt gebruikt voor marketing, training of entertainmentdoeleinden. Deze ervaringen beginnen met een transcriptie die vervolgens wordt opgemaakt of waar nodig wordt vertaald. Het transcripten van audio of video is een tijdsintensief en foutgevoelig proces wanneer manueel uitgevoerd. Het is ook een uitdaging om het handmatige proces te schalen, gezien de steeds toenemende behoefte aan audio-video-inhoud. [!DNL Experience Manager Assets] gebruikt de op AI-gebaseerde transcriptie van Azure die het op grote schaal verwerken van de audio- en video-elementen toestaat en de tekstranscripties (.vtt-bestanden) samen met de tijdstempelgegevens genereert. De transcriptie-functie wordt samen met Assets ook ondersteund in Dynamic Media.

De transcriptie-functie is zonder kosten beschikbaar in [!DNL Experience Manager Assets]. Nochtans, vereisen de beheerders de Azure geloofsbrieven van de gebruiker om de transcriptiedienst in te vormen [!DNL Experience Manager Assets]. U kunt [de proefreferenties ophalen](https://azure.microsoft.com/en-us/pricing/details/media-services/) rechtstreeks vanuit Microsoft® voor de functie voor audio- of video-transcriptie in Elementen.

## Voorwaarden voor transcriptie {#prerequisites}

1. Aan de slag [!DNL Experience Manager Assets as a Cloud Service] -instantie.
1. De volgende Azure-referenties zijn vereist voor configuratie in [!DNL Experience Manager Assets]:

   * Client-id (API-sleutel)
   * Clientbeveiligingssleutel
   * Tenant Endpoint (domein)
   * Mediaaccount
   * Brongroep
   * Abonnement-id

   Zie [Azure-documentatie](https://docs.microsoft.com/en-us/azure/media-services/latest/access-api-howto?tabs=portal) voor toegang tot Azure Media Services API.

1. Zorg ervoor dat de Azure-account voldoende krediet heeft om nieuwe aanvragen te verwerken.

## Abonnement configureren in [!DNL Experience Manager Assets] {#configure-transcription}

Hieronder vindt u de configuraties die nodig zijn om de transcriptie-functie in te schakelen [!DNL Experience Manager Assets]:

1. [Azure Media Services configureren](#configure-azure-media-service)
1. [Verwerkingsprofiel configureren voor audio- of videotranscriptie](#configure-processing-profile-for-transcription)


### Azure Media Services configureren {#configure-azure-media-services}

[!DNL Experience Manager Assets] gebruikt de [!DNL Azure Media Services] waarmee automatisch teksttranscripties van de gesproken taal worden gegenereerd in een [ondersteund audio- of videobestand](#supported-file-formats-for-transcription) in de WebVTT-indeling (.vtt). De beheerders kunnen vormen [!DNL Azure Media Services] in [!DNL Experience Manager Assets] de Azure-referenties gebruiken. De [omschrijvingsvoorwaarden](#transcription-prerequisites) de lijst [!DNL Azure] geloofsbrieven die voor de configuratie worden vereist. Als u geen [!DNL Azure] account en referenties, zie [Azure Media Services-documentatie](https://azure.microsoft.com/en-us/pricing/details/media-services/) om referenties van proefversie op te halen.

![configure-transcriptie-dienst](assets/configure-transcription-service.png)

Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Media Services Configuration]**. Selecteer een map (locatie) in de linkertrack en klik op de knop [!UICONTROL Create] om de verbinding met uw te vormen [!DNL Azure] account. Deze map is de locatie waar uw [!DNL Azure] cloudconfiguratie wordt opgeslagen in Experience Manager Assets. Voer de [!DNL Azure] referenties en klik op **[!UICONTROL Save & Close]**.

### Verwerkingsprofiel voor transcriptie configureren {#configure-processing-profile}

Wanneer de [!DNL Azure Media Services] is geconfigureerd in Experience Manager Assets, bestaat de volgende stap uit het maken van een middelenverwerkingsprofiel voor het genereren van op AI gebaseerde transcriptie van de audio- en video-elementen. Het op AI-gebaseerde verwerkingsprofiel genereert transcripties van de [ondersteunde audio- of video-elementen](#supported-file-formats-for-transcription) als een uitvoering in Experience Manager Assets en slaat de transcriptie (.vtt-bestand) op in dezelfde map als het oorspronkelijke element. Het is dus gemakkelijker voor de gebruikers om het element en de transcriptie-uitvoering te zoeken en te zoeken.

Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en klik op de knop **[!UICONTROL Create]** om een op AI gebaseerd verwerkingsprofiel te maken voor het genereren van transcriptie van uw audio- en videobestanden. Standaard geeft de pagina met het verwerkingsprofiel slechts drie tabbladen weer (Afbeelding, Video en Aangepast). Een **[!UICONTROL Content AI]** tab is zichtbaar als u hebt geconfigureerd [!DNL Azure Media Services] in uw [!DNL Experience Manager Assets] -instantie. Controleer uw [!DNL Azure] referenties als de **[!UICONTROL Content AI]** tijdens het maken van een verwerkingsprofiel.

In de **[!UICONTROL Content AI]** klikt u op de knop **[!UICONTROL Add New]** om transcriptie te configureren. Hier kunt u de bestandsindelingen (MIME-typen) voor het genereren van transcripties opnemen en uitsluiten door bestandstypen in de vervolgkeuzelijst te selecteren. In de volgende afbeelding worden alle ondersteunde audio- en videobestanden opgenomen en worden de tekstbestanden uitgesloten.

De optie **[!UICONTROL Create VTT transcript in same directory]** Schakel deze optie in om de transcriptie-uitvoering (.vtt-bestand) te maken en op te slaan in dezelfde map als het oorspronkelijke element. De andere uitvoeringen worden ook gegenereerd door de standaard DAM-workflow voor elementverwerking, ongeacht deze instelling.

![configure-transcriptie-dienst](assets/configure-transcription-profile.png)

In de volgende afbeelding wordt een aangepast videoprofiel weergegeven dat in Experience Manager Assets is gemaakt.

![configure-transcriptie-dienst](assets/video-processing-profile.png)

Het videoprofiel bevat ook de volgende aangepaste configuraties. Zie [procesprofieldocumentatie](/help/assets/asset-microservices-configure-and-use.md) voor meer informatie over het maken van een aangepast verwerkingsprofiel.

![configure-transcriptie-dienst](assets/video-processing-profile2.png)

Laten we nu de transcriptie in dit videoprofiel configureren. Ga naar de **[!UICONTROL Content AI]** en klik op de knop **[!UICONTROL Add New]** knop. Neem alle audio- en videobestanden op en sluit de afbeeldings- en toepassingsbestanden uit. De optie **[!UICONTROL Create VTT transcript in same directory]** schakelen en opslaan van configuratie.

![configure-transcriptie-dienst](assets/video-processing-profile1.png)

Als het verwerkingsprofiel is geconfigureerd voor het transcripten van audio- en videobestanden, kunt u dit verwerkingsprofiel op een van de volgende manieren toepassen op mappen:

* Selecteer een definitie van het verwerkingsprofiel in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]** en gebruik **[!UICONTROL Apply Profile to Folders]** handeling. Met de inhoudbrowser kunt u naar een specifieke map navigeren, map selecteren en de toepassing van het profiel bevestigen.
* Selecteer een map in de gebruikersinterface Elementen en klik op **[!UICONTROL Properties]** handeling om mapeigenschappen te openen. Klik op de knop **[!UICONTROL Asset Processing]** en selecteert u het juiste verwerkingsprofiel voor de map in de **[!UICONTROL Processing Profile]** lijst. Klik op **[!UICONTROL Save & Close]**.

  ![configure-transcriptie-dienst](assets/video-processing-profile3.png)

* Gebruikers kunnen mappen of specifieke elementen in de gebruikersinterface Middelen selecteren om een verwerkingsprofiel toe te passen. Selecteer vervolgens **[!UICONTROL Reprocess Assets]** van de opties beschikbaar op de bovenkant.

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

Wanneer u een video-element verwerkt, wordt [Op AI gebaseerd verwerkingsprofiel](#configure-processing-profile-for-transcription) genereert automatisch de transcriptie (.vtt-bestand) als een uitvoering samen met het oorspronkelijke element in dezelfde map.

![configure-transcriptie-dienst](assets/transcript1.png)

U kunt de transcriptie-uitvoering ook zien door de uitvoeringen van het oorspronkelijke video-element te openen. Als u toegang wilt krijgen tot **[!UICONTROL Renditions]** selecteert u het oorspronkelijke video-element en opent u de linkertrack. U ziet dat de transcriptie-uitvoering (.vtt-bestand) zichtbaar is onder het dialoogvenster **[!UICONTROL TRANSCRIPTVTT]** hoofd.

![configure-transcriptie-dienst](assets/transcript.png)

U kunt de transcriptie (vtt-tekstbestand) rechtstreeks vanuit de map downloaden als een aparte elementuitvoering, of vanuit de map **[!UICONTROL Renditions]** van het oorspronkelijke element door alle uitvoeringen van het element te downloaden.

Experience Manager biedt momenteel geen ondersteuning voor het native voorvertonen van volledige tekst of het bewerken van VTT-bestanden. U kunt de transcriptie echter downloaden en een teksteditor gebruiken om de transcriptie te bewerken of te verifiëren. De transcriptie weerspiegelt de gesproken taal als tekst op het opgegeven tijdstempel in de video met de betrouwbaarheidsscore (nauwkeurigheid) van de transcriptie.

![configure-transcriptie-dienst](assets/transcript-text.png)

## Transcriptie gebruiken in Dynamic Media {#using-transcription-in-dynamic-media}

Als u [geconfigureerde Dynamic Media](/help/assets/dynamic-media/config-dm.md) in uw Experience Manager Assets-instantie kunt u het element (audio- of videobestand) en de bijbehorende transcriptie (vtt-bestand) publiceren naar Dynamic Media. Op deze manier worden het oorspronkelijke element (audio- of videobestand) en de transcriptie (vtt-bestand) in dezelfde map gepubliceerd naar Dynamic Media. De Dynamic Media-beheerder kan [CC Closed Caption-ervaring inschakelen](/help/assets/dynamic-media/video.md#adding-captions-to-video) voor het audio- of videobestand met behulp van de transcriptie-uitvoering (.vtt-bestand).

Zie ook:

* [Videozelfstudie over het toevoegen van CC Closed Caption aan Dynamic Media-video](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html#add-cc-closed-captioning-to-dynamic-media-video)
* [Dynamic Media-video&#39;s publiceren naar YouTube](/help/assets/dynamic-media/video.md#publishing-videos-to-youtube)

In de volgende afbeelding geeft de URL het bijschriftgedeelte weer dat naar de transcriptie (.vtt-bestand) verwijst. De video weerspiegelt de gesproken taal (getranscripte tekst) als een **[!UICONTROL Closed Caption]** op de opgegeven tijdstempel in de video. De gebruiker kan het bijschrift in- of uitschakelen met de opdracht **[!UICONTROL CC]** knop.

![configure-transcriptie-dienst](assets/transcript-example.png)

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
* Betaald [!DNL Azure] -account, kunt u maximaal 50 films per minuut uploaden. In een proefaccount kunt u echter maximaal vijf films per minuut uploaden.

## Tips voor het oplossen van problemen {#troubleshooting}

Aanmelden bij uw [!DNL Azure Media Services] account met de zelfde geloofsbrieven (die u voor configuratie) hebt gebruikt om de verzoekstatus te verifiëren. Contact [!DNL Azure] als uw verzoek niet met succes wordt verwerkt.

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
