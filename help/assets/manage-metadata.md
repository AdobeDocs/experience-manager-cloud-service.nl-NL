---
title: Metagegevens van digitale elementen beheren
description: Meer informatie over de typen metagegevens en hoe [!DNL Adobe Experience Manager Assets] helpt metagegevens voor elementen te beheren om elementen gemakkelijker in te delen en te ordenen. [!DNL Experience Manager] kunt u elementen automatisch ordenen en verwerken op basis van hun metagegevens.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management,Metadata
role: User,Architect,Admin
exl-id: 73a82bc2-1dda-4090-b7ee-29d1a632ba25
source-git-commit: 984ead39ef8c20f06ac63c88380323e403a08712
workflow-type: tm+mt
source-wordcount: '1924'
ht-degree: 3%

---

# Metagegevens van uw digitale elementen beheren {#managing-metadata-for-digital-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Experience Manager Assets] bewaart meta-gegevens voor elk middel. Het maakt het gemakkelijker om activa te categoriseren en te organiseren en het helpt mensen die naar een specifiek bezit zoeken. Met de mogelijkheid om metagegevens te extraheren uit bestanden die zijn geüpload naar [!DNL Experience Manager Assets], kan het beheer van metagegevens worden geïntegreerd met de creatieve workflow. Met de mogelijkheid om metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van hun metagegevens.

<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## Waarom we metagegevens nodig hebben {#why-metadata}

Metagegevens zijn gegevens over gegevens. In dit verband verwijzen gegevens naar uw digitale middel, bijvoorbeeld een afbeelding. Metagegevens zijn essentieel voor efficiënt middelenbeheer.

Metagegevens zijn de verzameling van alle gegevens die beschikbaar zijn voor een element, maar die niet noodzakelijkerwijs in die afbeelding voorkomen. Voorbeelden van metagegevens zijn:

* Naam van het element.
* Tijd en datum van laatste wijziging.
* Grootte van het middel zoals het in de bewaarplaats werd opgeslagen.
* Naam van de map waarin de map zich bevindt.
* Gerelateerde elementen of toegepaste tags.

Het bovenstaande zijn de basiseigenschappen van metagegevens die [!DNL Experience Manager] kan beheren voor elementen, waardoor gebruikers alle elementen kunnen zien. Het is bijvoorbeeld handig elementen te bestellen op de laatste wijzigingsdatum wanneer u onlangs toegevoegde of gewijzigde elementen probeert te detecteren.

U kunt meer gegevens op hoog niveau toevoegen aan digitale elementen, bijvoorbeeld:

* Type element (is het een afbeelding, video, audioclip of document?).
* Eigenaar van het actief.
* Titel van het element.
* Beschrijving van het actief.
* Tags die aan een element zijn toegewezen.

Met meer metagegevens kunt u elementen verder indelen. Dit is handig wanneer de hoeveelheid digitale informatie toeneemt. Het is mogelijk om een paar honderd bestanden te beheren op basis van alleen de bestandsnamen. Deze aanpak is echter niet schaalbaar. Het is te kort wanneer het aantal betrokkenen en het aantal beheerde activa toenemen.

Als er metagegevens worden toegevoegd, neemt de waarde van een digitaal element toe, omdat het element

* Toegankelijker - systemen en gebruikers kunnen het gemakkelijk vinden.
* Gemakkelijker te beheren - u kunt gemakkelijker middelen met de zelfde reeks eigenschappen vinden en veranderingen op hen toepassen.
* Volledig - asset bevat meer informatie en context met meer metagegevens.

Om deze redenen [!DNL Assets] biedt u de juiste middelen voor het maken, beheren en uitwisselen van metagegevens voor uw digitale elementen.

## Typen metagegevens {#types-of-metadata}

Metagegevens worden geclassificeerd als technische, informatieve en administratieve metagegevens.

### Technische metagegevens

De technische metagegevens zijn toegespitst op de technische aspecten van digitale elementen en verschaffen cruciale informatie met betrekking tot:

* Bestandsgrootte
* Indeling
* Resolutie
* Dimensionen
* Kleurmodus

Dit type metagegevens helpt gebruikers om digitale elementen te begrijpen en efficiënt te gebruiken.

### Informatieve metagegevens

Informatiemetagegevens bieden beschrijvende informatie om het begrip van de inhoud te verbeteren, waardoor de inhoud gemakkelijker kan worden opgespoord en doorzocht. Het bevat trefwoorden, bijschriften en beschrijvingen. <br>Wanneer u bijvoorbeeld een video beheert in Experience Manager Assets, kunnen we de volgende metagegevens over informatie opnemen:

* **Trefwoorden**: marketing, productintroductie, promotie
* **Bijschrift**: Maak kennis met ons nieuwste product met spannende functies
* **Beschrijving**: Een gedetailleerd overzicht van de video-inhoud.

### Administratieve metagegevens

Administratieve metagegevens hebben betrekking op de beheeraspecten van digitale elementen. Het zorgt voor toegangsbeheer, naleving en beheer van de algemene levenscyclus van middelen binnen het systeem voor beheer van digitale middelen. Het bevat informatie over:

* Eigendom van activa
* Gebruiksrechten
* Machtigingen
* Overige administratieve gegevens

Dit type metagegevens zorgt voor een effectief beheer van bedrijfsmiddelen, toegangsbeheer en compatibiliteit.

<!-- Learn more about [metadata best practices](metadata-best-practices.md) to manage your digital assets effectively. -->

<!-- The two basic types of metadata are technical metadata and descriptive metadata.

Technical metadata is useful for software applications that are dealing with digital assets and should not be maintained manually. [!DNL Experience Manager Assets] and other software automatically determine technical metadata and the metadata may change when the asset is modified. The available technical metadata of an asset depends largely on the file type of the asset. Some examples of technical metadata are:

* Size of a file.
* Dimensions (height and width) of an image.
* Bit rate of an audio or video file.
* Resolution (level of detail) of an image.

Descriptive metadata is metadata concerned with the application domain, for example, the business that an asset is coming from. Descriptive metadata cannot be determined automatically. It is created manually or semi-automatically. For example, a GPS-enabled camera can automatically track the latitude and longitude and add geotag the image.

The cost of manually creating descriptive metadata information is high. So, standards are established to ease the exchange of metadata across software systems and organizations. [!DNL Experience Manager Assets] supports all relevant standards for metadata management. -->

## Metagegevens en laatste wijziging {#last-modification}

De datum van laatste wijziging van een element geeft de laatste keer weer dat het oorspronkelijke bestand voor een element wordt gewijzigd. De wijzigingsdatum en -gebruiker worden daarom alleen gewijzigd als:

* Er wordt een nieuwe versie van het element geüpload
* Een actief wordt opnieuw verwerkt

De laatste wijzigingsdatum en -gebruiker worden niet gewijzigd:

* Wanneer een element wordt verplaatst of hernoemd
* Wanneer een element is uitgecheckt, is deze ingecheckt of is de versie
* Wanneer een actief wordt gepubliceerd of niet gepubliceerd
* Updates van metagegevens
* Referentie- of verzamelingsupdates

## Coderingsnormen {#encoding-standards}

Er zijn verschillende manieren om metagegevens in bestanden in te sluiten. Er wordt ondersteuning geboden voor een selectie coderingsstandaarden:

* XMP: gebruikt door [!DNL Assets] om de geëxtraheerde metagegevens op te slaan in de gegevensopslagruimte.
* ID3: voor audio- en videobestanden.
* Exif: voor afbeeldingsbestanden.
* Overig/Verouderd: van [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], enzovoort.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) is een open standaard die wordt gebruikt door [!DNL Experience Manager Assets] voor alle metagegevensbeheer. De standaard biedt universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten. Adobe en andere bedrijven ondersteunen XMP standaard omdat deze een Rich Content-model biedt. Gebruikers van XMP norm en van [!DNL Experience Manager Assets] beschikken over een krachtig platform waarop kan worden voortgebouwd. Zie voor meer informatie [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

Gegevens die in deze ID3-tags zijn opgeslagen, worden weergegeven wanneer u een digitaal audiobestand afspeelt op uw computer of op een draagbare MP3-speler.

ID3-tags zijn ontworpen voor de MP3-bestandsindeling. Aanvullende informatie over indelingen:

* ID3-tags werken in MP3- en MP3PRO-bestanden.
* WAV heeft geen tags.
* WMA heeft merkgebonden markeringen die open-bronimplementatie niet toestaan.
* Ogg Vorbis gebruikt Xiph-opmerkingen die zijn ingesloten in de Ogg-container.
* AAC gebruikt een merkgebonden etiketteringsformaat.

### Exif {#exif}

Exchangeable image file format (Exif) is de meest gebruikte metagegevensindeling voor digitale fotografie. Hiermee kunt u een vaste woordenlijst met metagegevenseigenschappen insluiten in een groot aantal bestandsindelingen, zoals JPEG, TIFF, RIFF en WAV. In Exif worden metagegevens opgeslagen als paren van een metagegevensnaam en een metagegevenswaarde. Deze naam-waarde-paren voor metagegevens worden ook wel tags genoemd en mogen niet worden verward met de tags in [!DNL Experience Manager]. Moderne digitale camera&#39;s maken Exif-metagegevens en de moderne grafische software ondersteunt deze. De EXIF-indeling is de kleinste gemene deler voor het beheer van metagegevens, met name voor afbeeldingen.

Een belangrijke beperking van Exif is dat een aantal populaire indelingen voor afbeeldingsbestanden, zoals BMP, GIF of PNG, dit niet ondersteunen.

Metagegevensvelden die door EXIF worden gedefinieerd, zijn doorgaans technisch van aard en worden slechts in beperkte mate gebruikt voor beschrijvend metagegevensbeheer. Daarom [!DNL Experience Manager Assets] biedt toewijzing van EXIF-eigenschappen in [algemene metagegevensschema&#39;s](metadata-schemas.md) en in XMP.

#### Overige metagegevens {#other-metadata}

Andere metagegevens die kunnen worden ingesloten vanuit bestanden, zijn onder andere [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], enzovoort.

## Metagegevens van uw digitale elementen beheren {#manage-assets-metadata}

Met Enterprise Manager-middelen kunt u de metagegevens van meerdere elementen tegelijk bewerken, zodat u snel algemene wijzigingen in metagegevens in meerdere elementen kunt doorgeven. Gebruik de [!UICONTROL Properties] pagina om de eigenschappen van metagegevens te wijzigen in een algemene waarde of om tags toe te voegen of te wijzigen. Gebruik de Schema-editor om de pagina Eigenschappen van metagegevens aan te passen, inclusief het toevoegen, wijzigen of verwijderen van eigenschappen van metagegevens.

>[!NOTE]
>
>De bulkbewerkingsmethoden werken voor elementen die beschikbaar zijn in een map of een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die overeenkomen met een algemeen criterium, is het mogelijk om [bulkupdate van metagegevens na het zoeken](/help/assets/search-assets.md#metadata-updates).

1. Navigeer naar de locatie van de elementen die u wilt bewerken.
1. Selecteer de elementen waarvan u de algemene eigenschappen wilt bewerken.
1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]** om de [!UICONTROL Properties] pagina voor de geselecteerde elementen.

   >[!NOTE]
   >
   >Wanneer u meerdere elementen selecteert, wordt het laagste gebruikelijke bovenliggende formulier geselecteerd voor de elementen. Met andere woorden: [!UICONTROL Properties] op de pagina worden alleen metagegevensvelden weergegeven die in de [!UICONTROL Properties] pagina&#39;s van alle afzonderlijke elementen.

1. Wijzig de eigenschappen van metagegevens voor geselecteerde elementen onder de verschillende tabbladen.
1. Als u de metagegevenseditor voor een bepaald element wilt weergeven, annuleert u de selectie van de overige elementen in de lijst. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor het bepaalde middel.

   >[!NOTE]
   >
   >* In de [!UICONTROL Properties] pagina, kunt u elementen uit de elementenlijst verwijderen door de selectie te annuleren. In de lijst met elementen zijn standaard alle elementen geselecteerd. De metagegevens voor elementen die u uit de lijst verwijdert, worden niet bijgewerkt.
   >* Selecteer boven aan de lijst met elementen het selectievakje bij **[!UICONTROL Title]** schakelen tussen het selecteren van de elementen en het wissen van de lijst.

1. Selecteer een ander metagegevensschema voor de elementen door **[!UICONTROL Settings]** op de werkbalk en selecteer het gewenste schema. Sla de wijzigingen op.
1. Selecteer **[!UICONTROL Append mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata in velden die meerdere waarden bevatten. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Selecteren **[!UICONTROL Submit]**.

   >[!CAUTION]
   >
   >Voor velden met één waarde worden de nieuwe metadata niet toegevoegd aan de bestaande waarde in het veld, zelfs niet als u **[!UICONTROL Append mode]** selecteert.

## Aangepaste metagegevens met verwerkingsprofiel {#metadata-compute-service}

Activa als een [!DNL Cloud Service] U kunt aangepaste metagegevens voor een element genereren met gebruik van services in de cloud. Configureer een verwerkingsprofiel om aangepaste metagegevens te genereren. Zie [verwerkingsprofiel gebruiken](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

![Metagegevensuitvoering in verwerkingsprofiel](assets/processing-profile-metadata.png)

>[!TIP]
>
>Er kan slechts één verwerkingsprofiel worden toegepast op een map. Als u meerdere verwerkingen wilt toepassen op elementen in een map, voegt u meer opties toe aan één verwerkingsprofiel. Met één profiel kunt u bijvoorbeeld uitvoeringen genereren, elementen transcoderen, aangepaste metagegevens genereren enzovoort. U kunt MIME-typefilters toepassen voor elke taak, zodat de juiste taak wordt geactiveerd voor de vereiste bestandsindeling.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Configure limit for bulk metadata update {#configlimit}

To prevent DOS-like situation, [!DNL Experience Manager] limits the number of parameters supported in a Sling request. When updating metadata of many assets in one go, you may reach the limit and the metadata does not get updated for more assets. [!DNL Experience Manager] generates the following warning in the logs:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

To change the limit, access Web Console ( **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**) and change the value of **[!UICONTROL Maximum POST Parameters]** in **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi configuration.
-->

## Metagegevensschema {#metadata-schemata}

Metagegevensschema&#39;s zijn vooraf gedefinieerde sets definities van metagegevenseigenschappen die in verschillende toepassingen kunnen worden gebruikt. Eigenschappen worden altijd gekoppeld aan een element. Dit houdt in dat de eigenschappen &#39;over&#39; de bron zijn.

U kunt ook uw eigen metagegevensschema&#39;s ontwerpen als er geen schema&#39;s zijn die aan uw behoeften voldoen. Dupliceer bestaande informatie niet. Binnen een organisatie, maakt het scheiden van schema&#39;s het gemakkelijker om meta-gegevens te delen. [!DNL Experience Manager] biedt u een standaardlijst met de populairste metagegevensschema&#39;s. De lijst helpt u om uw meta-gegevensstrategie te springen en snel de meta-gegevenseigenschappen te kiezen die u nodig hebt.

De ondersteunde metagegevensschema&#39;s worden hieronder weergegeven.

### Standaardmetagegevens {#standard-metadata}

* DC - [!DNL Dublin Core] is een belangrijke en veelgebruikte reeks metagegevens.
* DICOM - Digital Imaging and Communications in Medicine.
* `Iptc4xmpCore` en `iptc4xmpExt` - De International Press Communications Standard bevat veel onderwerpspecifieke metagegevens.
* RDF - Resource Description Framework - voor algemene semantische webmetagegevens.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ` - Basic Job Ticketing.

### Toepassingsspecifieke metagegevens {#application-specific-metadata}

De toepassingsspecifieke metagegevens bevatten technische en beschrijvende metagegevens. Als u dergelijke metagegevens gebruikt, kunnen andere toepassingen de metagegevens mogelijk niet gebruiken. Een andere toepassing voor het renderen van afbeeldingen kan bijvoorbeeld geen toegang krijgen tot [!DNL Adobe Photoshop] metagegevens. U kunt een workflowstap maken waarmee een toepassingsspecifieke eigenschap wordt gewijzigd in een standaardeigenschap.

* ACDSee - Metagegevens beheerd door de [!DNL ACDSee] programma. Zie [www.acdsee.com/](https://www.acdsee.com/).
* Album - [!DNL Adobe Photoshop Album].
* CQ - Gebruikt door [!DNL Experience Manager Assets].
* DAM - Gebruikt door [!DNL Experience Manager Assets].
* DEX - [Optima SC Description Explorer](https://www.optimasc.com/products/dex/index.html) is een inzameling van hulpmiddelen voor meta-gegevens en dossierbeheer voor werkende systemen van Vensters.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto en MP - Microsoft Photo.
* PDF en PDF/X.
* Photoshop en psAux - [!DNL Adobe Photoshop].

### Metagegevens Digital Rights Management {#digital-rights-management-metadata}

* CC - [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS - [Universal System met afbeeldingslicentie](https://www.useplus.com).
<!--THIS LINK IS 404 WITH NO SUITABLE REPLACEMENT * PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata). -->
* PRL - PRISM Rights Language.
* PUR - PRISM-gebruiksrechten.
* `xmpPlus` - integratie van PLUS met XMP.

### Specifieke metagegevens voor fotografie {#photography-specific-metadata}

* EXIF - Technische informatie van camera, inclusief GPS-positie.
* CRS - [!DNL Camera Raw] schema.
* `iptc4xmpCore` en `iptc4xmpExt`.
* TIFF - metagegevens van afbeeldingen (niet alleen voor TIFF-afbeeldingen).

### Afdrukspecifieke metagegevens {#print-specific-metadata}

* PDF en PDF/X - Adobe PDF en toepassingen van derden.
<!--THIS LINK IS 404 WITH NO SUITABLE REPLACEMENT * PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata). -->
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG` - XMP metagegevens voor gepagineerde tekst.

### Multimediaspecifieke metagegevens {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - Mediabeheer.

## Workflows met metagegevens {#metadata-driven-workflows}

Door workflows te maken die op metagegevens zijn gebaseerd, kunt u bepaalde processen automatiseren, wat de efficiëntie ten goede komt. In een workflow met metagegevens leest het workflowbeheersysteem de workflow en wordt er dus een vooraf gedefinieerde actie uitgevoerd. U kunt bijvoorbeeld op een aantal manieren werkstromen gebruiken die zijn gebaseerd op metagegevens:

* De workflow kan controleren of een afbeelding een titel heeft of niet. Als dit niet het geval is, wordt een melding weergegeven om een titel toe te voegen.
* De workflow kan controleren of een copyrightkennisgeving op een middel distributie toestaat of niet. Het systeem verzendt het middel dus naar de ene of de andere server.
* Een workflow kan controleren op elementen zonder vooraf gedefinieerde, verplichte metagegevens of elementen *ongeldig* metagegevens.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [XMP-metadata](xmp-metadata.md)
>* [Metagegevens bewerken of toevoegen](meta-edit.md)
