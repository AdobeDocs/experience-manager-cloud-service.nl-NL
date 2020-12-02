---
title: XMP-metadata
description: Meer informatie over de metagegevensstandaard van de XMP (Extensible Metadata Platform) voor metagegevensbeheer. Deze wordt door AEM gebruikt als een gestandaardiseerde indeling voor het maken, verwerken en uitwisselen van metagegevens.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0c915b32d676ff225cbe276be075d3ae1a865f11
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 20%

---


# XMP-metadata {#xmp-metadata}

XMP (Extensible Metadata Platform) is de metagegevensstandaard die door AEM Assets wordt gebruikt voor alle metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal verschillende toepassingen.

Naast het aanbieden van universele meta-gegevenscodering die in alle dossierformaten kan worden ingebed, verstrekt XMP een rijk [inhoudsmodel](#xmp-core-concepts) en [gesteund door Adobe](#advantages-of-xmp) en andere bedrijven, zodat de gebruikers van XMP in combinatie met AEM Assets een krachtig platform hebben om op te bouwen.

## XMP overzicht en ecosysteem {#xmp-ecosystem}

AEM Assets biedt native ondersteuning voor de standaard voor XMP metagegevens. XMP is een standaard voor het verwerken en opslaan van gestandaardiseerde en merkgebonden metagegevens in digitale elementen. XMP wordt ontworpen om de gemeenschappelijke norm te zijn die veelvoudige toepassingen toestaat om effectief met meta-gegevens te werken.

Productieprofessionals gebruiken bijvoorbeeld de ingebouwde XMP ondersteuning binnen toepassingen om informatie in meerdere indelingen door te geven. De AEM Assets-opslagplaats extraheert de XMP metagegevens en gebruikt deze om de levenscyclus van de inhoud te beheren en biedt de mogelijkheid om automatiseringsworkflows te maken.

XMP standaardiseren hoe metagegevens worden gedefinieerd, gemaakt en verwerkt door een gegevensmodel, een opslagmodel en schema&#39;s op te geven. Al deze concepten worden behandeld in deze sectie.

Alle oudere meta-gegevens van EXIF, ID3, of Microsoft Office wordt automatisch vertaald aan XMP, die kan worden uitgebreid om klant-specifiek meta-gegevensschema, zoals productcatalogi te steunen.

Metagegevens in XMP bestaan uit een set eigenschappen. Deze eigenschappen worden altijd geassocieerd met een specifieke entiteit die als middel wordt bedoeld; dat wil zeggen dat de eigenschappen &quot;over&quot; de bron zijn. In het geval van XMP is de bron altijd het middel.

XMP definieert een [metadatamodel](https://nl.wikipedia.org/wiki/Metadata) dat kan worden gebruikt met elke gedefinieerde set metadataitems. XMP definieert ook bepaalde [schema&#39;s](https://nl.wikipedia.org/wiki/XML_schema) voor basiseigenschappen die nuttig zijn voor het opnemen van de geschiedenis van een resource tijdens het doorlopen van meerdere verwerkingsstappen, van het fotograferen, [scannen](https://en.wikipedia.org/wiki/Image_scanner) of ontwerpen als tekst, het doorlopen van fotobewerkingsstappen (zoals [bijsnijden](https://en.wikipedia.org/wiki/Cropping_%28image%29) of kleuraanpassing) tot het samenvoegen in een uiteindelijke afbeelding. Met XMP kan elk softwareprogramma of apparaat in de loop van de tijd zijn eigen informatie toevoegen aan een digitale resource, die vervolgens in het uiteindelijke digitale bestand kan worden bewaard.

XMP wordt doorgaans geserialiseerd en opgeslagen met behulp van een subset van het [W3C](https://nl.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://nl.wikipedia.org/wiki/Resource_Description_Framework) (RDF), dat op zijn beurt wordt uitgedrukt in [XML](https://nl.wikipedia.org/wiki/XML).

### Voordelen van XMP {#advantages-of-xmp}

XMP heeft de volgende voordelen ten opzichte van andere coderingsnormen en -schema&#39;s:

* Op XMP gebaseerde metagegevens zijn zeer krachtig en fijnkorrelig.
* Met XMP kunt u meerdere waarden voor één eigenschap hebben.
* XMP heeft gestandaardiseerde codering, waarmee u metagegevens eenvoudig kunt uitwisselen.
* XMP is uitbreidbaar. U kunt aanvullende informatie aan uw elementen toevoegen.

De XMP standaard is zo ontworpen dat deze uitbreidbaar is, zodat u aangepaste typen metagegevens kunt toevoegen aan de XMP. EXIF heeft daarentegen geen vaste lijst met eigenschappen die niet kunnen worden uitgebreid.

>[!NOTE]
>
>XMP staat over het algemeen niet binaire gegevenstypes toe om worden ingebed. Als u binaire gegevens wilt meenemen in XMP, bijvoorbeeld miniatuurafbeeldingen, moeten deze worden gecodeerd in een XML-vriendelijke indeling, zoals `Base64`.

### XMP kernconcepten {#xmp-core-concepts}

**Naamruimten en schema&#39;s**

Een XMP schema is een set eigenschapnamen in een algemene XML-naamruimte die
het gegevenstype en de beschrijvende informatie. Een XMP schema wordt geïdentificeerd door zijn XML namespace URI. Het gebruik van naamruimten voorkomt conflicten tussen eigenschappen in verschillende schema&#39;s die dezelfde naam maar een andere betekenis hebben.

De eigenschap **Creator** in twee onafhankelijk ontworpen schema&#39;s kan bijvoorbeeld betekenen dat de persoon die het element heeft gemaakt of dat de toepassing die het element heeft gemaakt, kan betekenen (bijvoorbeeld Adobe Photoshop).

**Eigenschappen en waarden XMP**

XMP kunnen eigenschappen van een of meer schema&#39;s omvatten. Een standaardsubset die door veel Adobe-toepassingen wordt gebruikt, kan bijvoorbeeld het volgende zijn:

* Dublin-kernschema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* Basisschema XMP: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* Schema voor XMP rechtenbeheer: `xmpRights:WebStatement`, `xmpRights:Marked`
* Schema voor mediabeheer XMP: `xmpMM:DocumentID`

**Taalalternatieven**

XMP biedt u de mogelijkheid om een eigenschap `xml:lang` toe te voegen aan teksteigenschappen om de taal van de tekst op te geven.

## Terugverwijzing naar vertoningen XMP {#xmp-writeback-to-renditions}

Met deze XMP functie voor terugschrijven in Adobe Experience Manager-elementen (AEM) worden wijzigingen in de metagegevens van elementen overgenomen in de uitvoeringen van het element.

Wanneer u de metagegevens voor een element wijzigt vanuit AEM Assets of wanneer u het element uploadt, worden wijzigingen in eerste instantie opgeslagen in het knooppunt met elementen in CRXDE.

De XMP schrijffunctie geeft de wijzigingen in metagegevens door aan alle of aan specifieke uitvoeringen van het element.

Overweeg een scenario waarbij u de [!UICONTROL Title] eigenschap van het element `Classic Leather` aan `Nylon` wijzigt.

![metadata](assets/metadata.png)

In dit geval slaat de AEM Assets de wijzigingen in de eigenschap **[!UICONTROL Title]** op in de parameter `dc:title` voor de metagegevens van de elementen die zijn opgeslagen in de elementenhiërarchie.

![metadata_stored](assets/metadata_stored.png)

AEM Assets verspreidt echter niet automatisch metagegevenswijzigingen in de uitvoeringen van een element.

Met de functie XMP terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De wijzigingen worden echter niet opgeslagen onder het metagegevensknooppunt in de elementenhiërarchie. In plaats daarvan worden de wijzigingen in de binaire bestanden voor de uitvoeringen ingesloten.

### XMP terugschrijven {#enable-xmp-writeback} inschakelen

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

Om de meta-gegevensveranderingen toe te laten om aan de vertoningen van de activa worden verspreid wanneer het uploaden van het, wijzig de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie in de Manager van de Configuratie.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie.
1. Selecteer de optie **[!UICONTROL Propagate XMP]** en sla de wijzigingen op.

### XMP terugschrijven inschakelen voor specifieke uitvoeringen {#enable-xmp-writeback-for-specific-renditions}

Als u wilt dat de XMP terugschrijffunctie wijzigingen in metagegevens doorgeeft aan geselecteerde uitvoeringen, geeft u deze uitvoeringen op in de werkstroomstap [!UICONTROL XMP Writeback Process] van de DAM-workflow voor terugschrijven van metagegevens. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de XMP-schrijffunctie om metagegevens door te geven aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Tik of klik op het AEM-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Open op de pagina Modellen het workflowmodel **[!UICONTROL DAM Metadata Writeback]**.
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. Tik of klik in het dialoogvenster **[!UICONTROL Step Properties]** op het tabblad **[!UICONTROL Process]**.
1. Voeg in het tekstvak **[!UICONTROL Arguments]** `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png` toe en tik op **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Sla de wijzigingen op.
1. Als u de PTIFF-uitvoeringen (Piramid TIFF) voor dynamische media-afbeeldingen met de nieuwe kenmerken opnieuw wilt genereren, voegt u de stap **[!UICONTROL Dynamic Media Process Image Assets]** toe aan de terugschrijfworkflow voor DAM-metadata. PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De wijzigingen in de metagegevens worden doorgegeven aan de uitvoeringen miniatuur.140.100.png en miniatuur.319.319.png van het element, en niet aan de andere.

>[!MORELIKETHIS]
>
>* [XMP specificeren door Adobe](https://www.adobe.com/devnet/xmp.html)

