---
title: Metagegevens voor digitale elementen beheren
description: Leer meer over de typen metagegevens en hoe u met AEM Assets metagegevens voor elementen kunt beheren, zodat elementen gemakkelijker kunnen worden gecategoriseerd en ingedeeld. Met de mogelijkheid om willekeurige metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van de metagegevens van de elementen.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Metagegevens van digitale elementen beheren {#managing-metadata-for-digital-assets}

Adobe Experience Manager (AEM)-middelen houden metagegevens bij voor elk element. Dit maakt het gemakkelijker om middelen in te delen en te organiseren en helpt mensen die een bepaald goed zoeken. Dankzij de mogelijkheid metagegevens te extraheren uit bestanden die naar AEM Assets zijn geüpload, kan het beheer van metagegevens worden geïntegreerd in de creatieve workflow. Met de mogelijkheid om willekeurige metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van de metagegevens van de elementen.

>[!MORELIKETHIS]
>
>* [XMP-metagegevens](xmp-metadata.md)
>* [Metagegevens bewerken of toevoegen](meta-edit.md)


<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## Waarom metagegevens {#why-metadata}

Metagegevens zijn gegevens over gegevens. In dit verband verwijzen de gegevens naar het element dat u behandelt, bijvoorbeeld een afbeelding. Metagegevens zijn belangrijk omdat gebruikers elementen efficiënter kunnen beheren.

Metagegevens zijn de verzameling van alle gegevens die beschikbaar zijn voor deze afbeelding, maar die niet noodzakelijkerwijs in die afbeelding staan, bijvoorbeeld:

* de naam van het element
* de datum en het tijdstip waarop deze voor het laatst is gewijzigd
* de grootte van de afbeelding zoals deze is opgeslagen in de opslagplaats
* de naam van de map waarin deze zich bevindt

Dit zijn de basiseigenschappen van metagegevens die AEM kan beheren voor elementen, waardoor gebruikers alle elementen kunnen zien, bijvoorbeeld geordend op de laatste wijzigingsdatum. Dit is handig wanneer ze proberen te achterhalen welke elementen onlangs aan de opslagplaats zijn toegevoegd.

U kunt meer gegevens op hoog niveau toevoegen aan digitale elementen, bijvoorbeeld:

* het type element (is het een afbeelding, video, audioclip of document?)
* de eigenaar van het actief
* de titel van het actief
* de beschrijving van het actief
* de labels die aan een element zijn toegewezen

Met meer metagegevens kunt u elementen verder indelen. Dit is handig wanneer de hoeveelheid digitale informatie toeneemt. Hoewel het voor één enkele persoon mogelijk is om een lijst van een paar honderd dossiers te beheren eenvoudig die op hun dossiernamen worden gebaseerd, is deze benadering ontoereikend wanneer het aantal betrokken personen en het aantal beheerde activa groeit.

Wanneer metagegevens aan elementen worden toegevoegd, neemt de waarde van het element toe omdat het element

* toegankelijker - mensen kunnen het veel gemakkelijker vinden
* eenvoudiger te beheren - u kunt gemakkelijker middelen vinden met dezelfde set eigenschappen en er wijzigingen op toepassen
* complexer - hoe meer metagegevens u aan een element hebt toegevoegd, des te belangrijker het beheer van metagegevens wordt

Daarom biedt AEM Assets u de juiste middelen om metagegevens voor uw digitale elementen te maken, beheren en uit te wisselen.

## Metagegevens: basiskennis {#metadata-basics}

Metagegevens worden uit elementen geëxtraheerd wanneer deze worden geïmporteerd (ingestort). Bovendien kunt u elementen nog verder categoriseren door metagegevens toe te voegen.

In deze sectie worden de typen metagegevens en coderingsnormen besproken.

### Technische metagegevens {#technical-metadata}

Technische metagegevens zijn handig voor softwaretoepassingen die werken met digitale elementen en mogen niet handmatig worden onderhouden. Technische metagegevens kunnen automatisch worden bepaald door AEM Assets en andere software en kunnen worden gewijzigd wanneer het element wordt gewijzigd. De beschikbare technische metagegevens van een element zijn grotendeels afhankelijk van het bestandstype van het element. Voorbeelden van technische metagegevens zijn:

* de grootte van een bestand
* de afmetingen (hoogte en breedte) van een afbeelding
* de bitsnelheid van een audio- of videobestand
* de resolutie (detailniveau) van een afbeelding

### Beschrijvende metagegevens {#descriptive-metadata}

De beschrijvende meta-gegevens zijn meta-gegevens betrokken bij het toepassingsdomein, bijvoorbeeld, de zaken die een activa uit komt. Metagegevens met een beschrijving kunnen niet automatisch worden bepaald. Deze moet handmatig of halfautomatisch worden gemaakt. Een camera met GPS-functionaliteit kan bijvoorbeeld automatisch de breedte- en lengtegraad bijhouden van een afbeelding die is gemaakt en deze informatie toevoegen aan de metagegevens van de afbeelding.

Vanwege de hoge kosten van de handmatige inspanningen die nodig zijn om beschrijvende metagegevens te maken, zijn er normen opgesteld om de uitwisseling van metagegevens tussen softwaresystemen en organisaties te vergemakkelijken.

AEM Assets steunt alle relevante normen voor meta-gegevensbeheer.

Vanwege het belang van metagegevens en de grote handmatige betrokkenheid die nodig is om metagegevens te maken, zijn er normen opgesteld die het uitwisselen van gegevens vergemakkelijken.

### Coderingsnormen {#encoding-standards}

Er zijn verschillende manieren waarop metagegevens in bestanden kunnen worden ingesloten. Een selectie coderingsstandaarden wordt ondersteund:

* XMP: worden gebruikt door AEM Assets om de opgehaalde metagegevens in de gegevensopslagruimte op te slaan.
* ID3: voor audio- en videobestanden.
* EXIF: voor afbeeldingsbestanden.
* Overige/Verouderd: vanuit Microsoft Word, PowerPoint, Excel enzovoort.

#### XMP {#xmp}

XMP betekent Extensible Metadata Platform en is de metagegevensstandaard die door AEM Assets wordt gebruikt voor al het metagegevensbeheer. XMP biedt niet alleen universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten, maar biedt ook een uitgebreid inhoudsmodel en wordt ondersteund door Adobe en andere bedrijven, zodat gebruikers van XMP in combinatie met AEM Assets een krachtig platform hebben waarop kan worden gebouwd.

#### ID3 {#id}

Gegevens die in deze ID3-tags zijn opgeslagen, worden weergegeven wanneer u een digitaal audiobestand afspeelt op uw computer of op een draagbare MP3-speler.

ID3-tags zijn ontworpen voor de MP3-bestandsindeling. Aanvullende informatie over indelingen:

* ID3-tags werken in MP3- en MP3pro-bestanden.
* WAV heeft geen tags.
* WMA heeft merkgebonden markeringen die open bronimplementatie niet toestaan.
* Ogg Vorbis gebruikt Xiph-opmerkingen die zijn ingesloten in de OGG-container.
* AAC gebruikt een merkgebonden etiketteringsformaat.

#### EXIF {#exif}

EXIF betekent Exchangeable image file format en is de populairste metagegevensindeling die wordt gebruikt voor digitale fotografie. Hiermee kunt u een vaste woordenlijst met metagegevenseigenschappen insluiten in een aantal bestandsindelingen, zoals

* JPEG
* TIFF
* RIFF
* WAV

Een belangrijke beperking van EXIF is dat deze niet wordt ondersteund door populaire indelingen voor afbeeldingsbestanden, zoals BMP, GIF of PNG.

EXIF slaat metagegevens op als paren van een metagegevensnaam en een metagegevenswaarde. Deze naam-waarde-paren voor metagegevens worden ook wel tags genoemd, maar mogen niet worden verward met de codering in AEM.

Aangezien EXIF automatisch door moderne digitale camera&#39;s wordt gecreeerd en door moderne grafieksoftware wordt gesteund, kan het als laagste gemeenschappelijke noemer voor meta-gegevensbeheer worden gezien.

De meeste metagegevensvelden die door EXIF worden gedefinieerd, zijn van zeer technische aard en van beperkte toepassing voor het beheer van beschrijvende metagegevens. Daarom biedt AEM Assets toewijzing van EXIF-eigenschappen aan in [algemene metagegevensschema](metadata-schemas.md) en in [XMP](xmp-metadata.md), de krachtige metagegevensindeling die AEM Assets gebruikt voor metagegevensbeheer.

#### Andere metagegevens {#other-metadata}

Andere meta-gegevens die van dossiers kunnen worden ingebed omvatten Microsoft Word, PowerPoint, Excel, etc.

## Metagegevens van uw digitale middelen beheren {#manage-assets-metadata}

Met Enterprise Manager-middelen kunt u de metagegevens van meerdere elementen tegelijk bewerken, zodat u snel algemene wijzigingen in metagegevens in elementen bulksgewijs kunt doorgeven. Met de pagina [!UICONTROL Eigenschappen] kunt u eigenschappen van metagegevens wijzigen in een algemene waarde of tags toevoegen of wijzigen. Gebruik de Schema-editor om de pagina Eigenschappen van metagegevens aan te passen, inclusief het toevoegen, wijzigen of verwijderen van eigenschappen van metagegevens.

>[!NOTE]
>
>De bulkbewerkingsmethoden werken voor elementen die beschikbaar zijn in een map of een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die voldoen aan een algemeen criterium, is het mogelijk om de metagegevens na het zoeken [in grote](/help/assets/search-assets.md#metadataupdates)hoeveelheden bij te werken.

1. Navigeer naar de locatie van de elementen die u wilt bewerken.
1. Selecteer de elementen waarvan u de algemene eigenschappen wilt bewerken.
1. Tik op de werkbalk of klik op **[!UICONTROL Eigenschappen]** om de pagina [!UICONTROL Eigenschappen] voor de geselecteerde elementen te openen.

   >[!NOTE]
   >
   >Wanneer u meerdere elementen selecteert, wordt het laagste gebruikelijke bovenliggende formulier geselecteerd voor de elementen. Met andere woorden, op de pagina [!UICONTROL Eigenschappen] worden alleen metagegevensvelden weergegeven die op de pagina&#39;s [!UICONTROL Eigenschappen] van alle afzonderlijke elementen gemeenschappelijk zijn.

1. Wijzig de eigenschappen van metagegevens voor geselecteerde elementen onder de verschillende tabbladen.
1. Schakel de overige elementen in de lijst uit als u de metagegevenseditor voor een bepaald element wilt weergeven. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor het bepaalde middel.

   >[!NOTE]
   >
   >* Op de pagina [!UICONTROL Eigenschappen] kunt u elementen uit de lijst met elementen verwijderen door deze uit te schakelen. In de lijst met elementen zijn standaard alle elementen geselecteerd. De metagegevens voor elementen die u uit de lijst verwijdert, worden niet bijgewerkt.
   >* Selecteer boven aan de lijst met elementen het selectievakje bij **[!UICONTROL Titel]** om te schakelen tussen het selecteren van de elementen en het wissen van de lijst.


1. Tik op **[!UICONTROL Instellingen]** op de werkbalk en selecteer het gewenste schema om een ander metagegevensschema voor de elementen te selecteren. Sla de wijzigingen op.
1. Als u de nieuwe metagegevens wilt toevoegen aan de bestaande metagegevens in velden die meerdere waarden bevatten, selecteert u de modus **** Toevoegen. Als u deze optie niet selecteert, worden de bestaande metagegevens in de velden vervangen door de nieuwe metagegevens. Tik/klik op **[!UICONTROL Verzenden]**.

   >[!CAUTION]
   >
   >Voor velden met één waarde worden de nieuwe metagegevens niet toegevoegd aan de bestaande waarde in het veld, zelfs niet als u de modus **** Toevoegen selecteert.

## Limiet voor bijwerken van bulkmetagegevens configureren {#configlimit}

Om DOS-achtige situatie te verhinderen, beperkt AEM het aantal parameters die in een Verschuivend verzoek worden gesteund. Wanneer u metagegevens van veel elementen in één keer bijwerkt, kunt u de limiet bereiken en worden de metagegevens niet bijgewerkt voor meer elementen. AEM genereert de volgende waarschuwing in de logboeken:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Als u de limiet wilt wijzigen, opent u de webconsole ( **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**) en wijzigt u de waarde van **[!UICONTROL Maximale POST-parameters]** in de OSGi-configuratie van **[!UICONTROL Apache Sling Request-parameters]** .

## Metagegevensschema {#metadata-schemata}

Metagegevensschema&#39;s zijn vooraf gedefinieerde sets definities van metagegevenseigenschappen die in een groot aantal toepassingen kunnen worden gebruikt. Eigenschappen zijn altijd gekoppeld aan een element. Dit houdt in dat de eigenschappen &quot;over&quot; de bron zijn.

U kunt ook uw eigen schema&#39;s voor metagegevens ontwerpen als er geen bestaan die aan uw behoeften voldoen (zorg er echter voor dat u iets dat al bestaat, niet dupliceert). Binnen een organisatie, maakt het scheiden van schema&#39;s het gemakkelijker om meta-gegevens onder organisaties te delen.

AEM voorziet u van een uit-van-de-doos lijst van de populairste meta-gegevensschema&#39;s, die u toestaan om uw meta-gegevensstrategie te springen en de meta-gegevenseigenschappen te kiezen die u van een reeds-bepaalde schema&#39;s nodig hebt.

De ondersteunde metagegevensschema&#39;s worden in de volgende sectie weergegeven.

### Standaardmetagegevens {#standard-metadata}

* dc - Dublin Core - de belangrijkste en meest gebruikte reeks metagegevens
* DICOM - Digital Imaging and Communications in Medicine
* IPTC4xmpCore &amp; iptc4xmpExt - International Press Communications Standard - veel onderwerpspecifieke metagegevens
* rdf - Resource Description Framework - voor algemene semantische webmetagegevens
* xmp - Extensible Metadata Platform
* xmpBJ - Basic Job Ticketing

### Toepassingsspecifieke metagegevens {#application-specific-metadata}

>[!NOTE]
>
>Toepassingsspecifieke metagegevens omvatten technische en beschrijvende metagegevens. Als u deze gebruikt, kunnen andere toepassingen mogelijk de meta-gegevens niet gebruiken. Als u bijvoorbeeld een element hebt met Adobe Photoshop-metagegevens en een andere toepassing voor het renderen van afbeeldingen probeert toegang te krijgen tot de metagegevens, is dat mogelijk niet het geval.
>
>Als u ontdekt dat u veel toepassing-specifieke meta-gegevens in uw activa hebt, kunt u een werkschemastap tot stand brengen die de toepassing-specifieke bezit in een norm verandert.

* acdsee - metagegevens beheerd door het ACDSee-programma [www.acdsee.com/](https://www.acdsee.com/)
* album - Adobe Photoshop Album
* cq - gebruikt door AEM Assets
* dam - gebruikt door AEM Assets
* dex - Optima SC Description Explorer
* crs - Adobe Photoshop Camera Raw
* lr - Adobe Lightroom
* mediapro - IView MediaPro
* Microsoft Photo &amp; MP - Microsoft Photo
* pdf en pdfx
* Photoshop &amp; psAux - Adobe Photoshop

### Metagegevens van Digital Rights Management {#digital-rights-management-metadata}

* cc - creative commons
* xmpRights
* plus - Picture Licensing Universal System - https://www.useplus.com/
* prism - https://www.idealliance.org/prism-metadata Publishing Requirements for Industry Standard Metadata
* prl - Prism Rights Language
* pur - Rechten van riskgebruik
* xmpPlus - integratie van PLUS met XMP

### Fotografiespecifieke metagegevens {#photography-specific-metadata}

* exif - veel technische informatie van de camera, waaronder de GPS-positie
* crs - photoshop camera raw
* Iptc4xmpCore en iptc4xmpExt
* TIFF - metagegevens van afbeeldingen (niet alleen voor TIFF-afbeeldingen)

### Afdrukspecifieke metagegevens {#print-specific-metadata}

* pdf en pdfx - Adobe PDF en toepassingen van derden
* prism - [www.prismstandard.org](https://www.prismstandard.org) Publicatie-vereisten voor industriestandaard metagegevens
* xmp
* xmpPG - xmp voor gepagineerde tekst

### Multimediaspecifieke metagegevens {#multimedia-specific-metadata}

* xmpDM - Dynamische media
* xmpMM - Mediabeheer

## Workflows met metagegevens {#metadata-driven-workflows}

Door workflows te maken die op metagegevens zijn gebaseerd, kunt u sommige processen automatiseren, wat de efficiëntie ten goede komt. In een workflow met metagegevens leest het workflowbeheersysteem de workflow en wordt er dus een vooraf gedefinieerde actie uitgevoerd.

U kunt bijvoorbeeld op een aantal manieren werkstromen gebruiken die zijn gebaseerd op metagegevens:

* Met de workflow kunt u controleren of een afbeelding een titel heeft. Als dit niet het geval is, wordt een bepaalde gebruiker door het systeem op de hoogte gesteld van het toevoegen van een titel.
* De workflow kan controleren of een copyrightkennisgeving op een middel distributie mogelijk maakt. Als dit het geval is, verzendt het systeem het middel naar één server. Als dit niet het geval is, verzendt het systeem het element naar een andere server.
