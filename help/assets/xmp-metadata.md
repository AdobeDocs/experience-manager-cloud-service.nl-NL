---
title: XMP-metadata
description: Meer informatie over de XMP-metagegevensstandaard (Extensible Metadata Platform) voor metagegevensbeheer. Het wordt door AEM gebruikt als een gestandaardiseerde indeling voor het maken, verwerken en uitwisselen van metagegevens.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 496ad0831d20eb7653a3c5727999a2abc5728ec7
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 15%

---


# XMP-metadata {#xmp-metadata}

XMP (Extensible Metadata Platform) is de metagegevensstandaard die wordt gebruikt door AEM Assets voor al het metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal toepassingen.

XMP biedt niet alleen universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten, maar biedt ook een rijk [inhoudsmodel](#xmp-core-concepts) en wordt [ondersteund door Adobe](#advantages-of-xmp) en andere bedrijven, zodat gebruikers van XMP in combinatie met AEM Assets een krachtig platform hebben waarop kan worden gebouwd.

## XMP-overzicht en ecosysteem {#xmp-ecosystem}

AEM-middelen bieden native ondersteuning voor de standaard voor XMP-metagegevens. XMP is een standaard voor het verwerken en opslaan van gestandaardiseerde en merkgebonden metagegevens in digitale elementen. XMP is ontworpen als de algemene standaard die meerdere toepassingen in staat stelt effectief met metagegevens te werken.

Productieprofessionals gebruiken bijvoorbeeld de ingebouwde XMP-ondersteuning in Adobe-toepassingen om informatie door te geven in meerdere bestandsindelingen. De AEM Assets-opslagplaats extraheert de XMP-metagegevens en gebruikt deze om de levenscyclus van de inhoud te beheren en biedt de mogelijkheid om automatiseringsworkflows te maken.

XMP is gestandaardiseerd hoe metagegevens worden gedefinieerd, gemaakt en verwerkt door een gegevensmodel, een opslagmodel en schema&#39;s op te geven. Al deze concepten worden behandeld in deze sectie.

Alle oudere metagegevens van EXIF, ID3 of Microsoft Office worden automatisch vertaald naar XMP, dat kan worden uitgebreid ter ondersteuning van klantspecifiek metagegevensschema, zoals productcatalogi.

Metagegevens in XMP bestaan uit een set eigenschappen. Deze eigenschappen worden altijd geassocieerd met een specifieke entiteit die als middel wordt bedoeld; dat wil zeggen dat de eigenschappen &quot;over&quot; de bron zijn. In het geval van XMP is de bron altijd het element.

XMP definieert een [metadatamodel](https://nl.wikipedia.org/wiki/Metadata) dat kan worden gebruikt met elke gedefinieerde set metadataitems. XMP definieert ook bepaalde [schema&#39;s](https://nl.wikipedia.org/wiki/XML_schema) voor basiseigenschappen die nuttig zijn voor het opnemen van de geschiedenis van een resource tijdens het doorlopen van meerdere verwerkingsstappen, van het fotograferen, [scannen](https://en.wikipedia.org/wiki/Image_scanner) of ontwerpen als tekst, het doorlopen van fotobewerkingsstappen (zoals [bijsnijden](https://en.wikipedia.org/wiki/Cropping_%28image%29) of kleuraanpassing) tot het samenvoegen in een uiteindelijke afbeelding. Met XMP kan elk softwareprogramma of apparaat in de loop van de tijd zijn eigen informatie toevoegen aan een digitale resource, die vervolgens in het uiteindelijke digitale bestand kan worden bewaard.

XMP wordt doorgaans geserialiseerd en opgeslagen met behulp van een subset van het [W3C](https://nl.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://nl.wikipedia.org/wiki/Resource_Description_Framework) (RDF), dat op zijn beurt wordt uitgedrukt in [XML](https://nl.wikipedia.org/wiki/XML).

### Voordelen van XMP {#advantages-of-xmp}

XMP heeft de volgende voordelen ten opzichte van andere coderingsstandaarden en -schema&#39;s:

* Op XMP gebaseerde metagegevens zijn zeer krachtig en fijnkorrelig.
* Met XMP kunt u meerdere waarden voor één eigenschap hebben.
* XMP heeft gestandaardiseerde codering, waarmee u metagegevens eenvoudig kunt uitwisselen.
* XMP kan worden uitgebreid. U kunt aanvullende informatie aan uw elementen toevoegen.

De XMP-standaard is zo ontworpen dat deze uitbreidbaar is, zodat u aangepaste typen metagegevens kunt toevoegen aan de XMP-gegevens. EXIF heeft daarentegen geen vaste lijst met eigenschappen die niet kunnen worden uitgebreid.

>[!NOTE]
>
>XMP staat meestal niet toe dat binaire gegevenstypen worden ingesloten. Als u binaire gegevens bijvoorbeeld wilt meenemen in XMP-miniatuurafbeeldingen, moeten deze worden gecodeerd in een XML-vriendelijke indeling, zoals `Base64`.

### XMP-kernconcepten {#xmp-core-concepts}

**Naamruimten en schema&#39;s**

Een XMP-schema is een set eigenschapnamen in een algemene XML-naamruimte die het gegevenstype en beschrijvende informatie bevat. Een XMP-schema wordt aangeduid met de XML-naamruimte-URI. Het gebruik van naamruimten voorkomt conflicten tussen eigenschappen in verschillende schema&#39;s die dezelfde naam maar een andere betekenis hebben.

De eigenschap **Creator** kan bijvoorbeeld in twee onafhankelijk ontworpen schema&#39;s verwijzen naar de persoon die het element heeft gemaakt of naar de toepassing die het element heeft gemaakt (bijvoorbeeld Adobe Photoshop).

**XMP-eigenschappen en -waarden**

XMP kan eigenschappen van één of meerdere schema&#39;s omvatten. Een standaardsubset die door veel Adobe-toepassingen wordt gebruikt, kan bijvoorbeeld het volgende zijn:

* Dublin-kernschema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP-basisschema: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP-schema voor rechtenbeheer: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP-schema voor mediabeheer: `xmpMM:DocumentID`

**Taalalternatieven**

Met XMP kunt u een `xml:lang` eigenschap aan teksteigenschappen toevoegen om de taal van de tekst op te geven.

## XMP-terugverwijzing naar uitvoeringen {#xmp-writeback-to-renditions}

Met deze functie voor terugschrijven van XMP in Adobe Experience Manager (AEM) Elementen worden wijzigingen in de metagegevens van elementen overgenomen in de uitvoeringen van het element.

Wanneer u de metagegevens voor een element wijzigt vanuit AEM-elementen of wanneer u het element uploadt, worden de wijzigingen in eerste instantie opgeslagen in het knooppunt met elementen in CRXDE.

De functie voor terugschrijven van XMP verspreidt de metagegevenswijzigingen in alle of specifieke uitvoeringen van het element.

Neem bijvoorbeeld een scenario waarin u de [!UICONTROL Title] eigenschap van het element `Classic Leather` met de naam wijzigt `Nylon`.

![metadata](assets/metadata.png)

In dit geval slaat AEM Assets de veranderingen in het **[!UICONTROL Title]** bezit in de `dc:title` parameter voor de activa op die meta-gegevens in de activahiërarchie worden opgeslagen.

![metadata_stored](assets/metadata_stored.png)

AEM-elementen geven echter niet automatisch metagegevenswijzigingen door in de uitvoeringen van een element.

Met de functie voor terugschrijven van XMP kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De wijzigingen worden echter niet opgeslagen onder het metagegevensknooppunt in de elementenhiërarchie. In plaats daarvan worden de wijzigingen in de binaire bestanden voor de uitvoeringen ingesloten.

### Terugschrijven XMP inschakelen {#enable-xmp-writeback}

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

Om de meta-gegevensveranderingen toe te laten om aan de vertoningen van de activa worden verspreid wanneer het uploaden van het, wijzig de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie in de Manager van de Configuratie.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie.
1. Selecteer de **[!UICONTROL Propagate XMP]** optie en sla de wijzigingen op.

### Terugschrijven van XMP inschakelen voor specifieke uitvoeringen {#enable-xmp-writeback-for-specific-renditions}

Als u wilt dat de XMP-schrijffunctie wijzigingen in metagegevens doorgeeft aan geselecteerde uitvoeringen, geeft u deze uitvoeringen op in de [!UICONTROL XMP Writeback Process] workflowstap van de DAM-workflow voor het schrijven van metagegevens. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de functie voor terugschrijven van XMP om metagegevens door te geven aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Tik of klik op het AEM-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Open het **[!UICONTROL DAM Metadata Writeback]** workflowmodel op de pagina Modellen.
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. Tik of klik in het dialoogvenster **[!UICONTROL Step Properties]** op het tabblad **[!UICONTROL Process]**.
1. Voeg in het **[!UICONTROL Arguments]** vak toe `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`en tik/klik op **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Sla de wijzigingen op.
1. Als u de PTIFF-uitvoeringen (Piramid TIFF) voor dynamische media-afbeeldingen met de nieuwe kenmerken opnieuw wilt genereren, voegt u de stap **[!UICONTROL Dynamic Media Process Image Assets]** toe aan de terugschrijfworkflow voor DAM-metadata. PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De wijzigingen in de metagegevens worden doorgegeven aan de uitvoeringen miniatuur.140.100.png en miniatuur.319.319.png van het element, en niet aan de andere.

<!--
>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).
-->

### XMP-metagegevens filteren {#filtering-xmp-metadata}

AEM-elementen ondersteunen het filteren van eigenschappen/knooppunten voor XMP-metagegevens die worden gelezen van binaire elementen van elementen en die worden opgeslagen in JCR wanneer elementen worden ingepakt. Filteren is mogelijk via een geblokkeerde lijst en een toegestane lijst.

Als u filtert met een geblokkeerde lijst, kunt u alle eigenschappen van XMP-metagegevens importeren, behalve de eigenschappen die voor uitsluiting zijn opgegeven. Voor elementtypen zoals INDD-bestanden met grote hoeveelheden XMP-metagegevens (bijvoorbeeld 1000 knooppunten met 10.000 eigenschappen) zijn de namen van te filteren knooppunten echter niet altijd van tevoren bekend. Als het filtreren gebruikend een geblokkeerde lijst een groot aantal activa met talrijke meta-gegevens XMP om toelaat worden ingevoerd, kan de instantie AEM/de cluster stabiliteitskwesties, bijvoorbeeld verstopte observatierijen ontmoeten.

Door het filteren van XMP-metagegevens via de toegestane lijst verhelpt u dit probleem door de XMP-eigenschappen te definiëren die moeten worden geïmporteerd. Op deze manier worden andere/onbekende XMP-eigenschappen genegeerd. Voor achterwaartse verenigbaarheid, kunt u sommige van deze eigenschappen aan het filter toevoegen dat een geblokkeerde lijst gebruikt.

>[!NOTE]
>
>Filteren werkt alleen voor de eigenschappen die zijn afgeleid van XMP-bronnen in binaire elementen. Voor de eigenschappen die van niet-XMP bronnen, zoals formaten EXIF en IPTC worden afgeleid, werkt het filtreren niet. De aanmaakdatum van elementen wordt bijvoorbeeld opgeslagen in een eigenschap met de naam EXIF TIFF. `CreateDate` Deze waarde wordt in het metagegevensveld genaamd `exif:DateTimeOriginal`. Aangezien de bron een niet-XMP-bron is, werkt het filteren niet op deze eigenschap.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM XmpFilter]** configuratie.
1. Als u filtering wilt toepassen via een toegestane lijst, selecteert u de eigenschappen die u wilt importeren in het **[!UICONTROL Apply Whitelist to XMP Properties]****[!UICONTROL Whitelisted XML Names for XMP filtering]** vak en geeft u deze op.

1. Als u geblokkeerde XMP-eigenschappen wilt uitfilteren nadat u filters hebt toegepast via de lijst met toegestane waarden, geeft u ze op in het **[!UICONTROL Blacklisted XML Names for XMP filtering]** vak.

   >[!NOTE]
   >
   >The **[!UICONTROL Apply Blacklist to XMP Properties]** option is selected by default. Met andere woorden, het filtreren gebruikend een geblokkeerde lijst wordt toegelaten door gebrek. Als u dergelijke filters wilt uitschakelen, schakelt u de **[!UICONTROL Apply Blacklist to XMP Properties]** optie uit.

1. Sla de wijzigingen op.

>[!MORELIKETHIS]
>
>* [XMP-specificatie van Adobe](https://www.adobe.com/devnet/xmp.html)

