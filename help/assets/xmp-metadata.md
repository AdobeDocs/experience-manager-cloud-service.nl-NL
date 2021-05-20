---
title: XMP-metadata
description: Meer informatie over de metagegevensstandaard van de XMP (Extensible Metadata Platform) voor metagegevensbeheer. Deze wordt door AEM gebruikt als een gestandaardiseerde indeling voor het maken, verwerken en uitwisselen van metagegevens.
contentOwner: AG
feature: Metagegevens
role: Business Practitioner,Administrator
exl-id: fd9af408-d2a3-4c7a-9423-c4b69166f873
source-git-commit: 212e4e7cfb93d5765f80003c42ba6afb9af45c13
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 16%

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

Met deze XMP schrijffunctie in [!DNL Adobe Experience Manager Assets] worden de wijzigingen in metagegevens in de uitvoeringen van het oorspronkelijke element gerepliceerd.
Wanneer u de metagegevens voor een element wijzigt vanuit [!DNL Assets] of tijdens het uploaden van het element, worden de wijzigingen aanvankelijk opgeslagen in het metagegevensknooppunt in de elementenhiërarchie. Met de functie Terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De eigenschap schrijft slechts die meta-gegevenseigenschappen terug die `jcr` namespace gebruiken, namelijk wordt een bezit genoemd `dc:title` teruggeschreven maar een bezit genoemd `mytitle` is niet.

Neem bijvoorbeeld een scenario waarin u de eigenschap [!UICONTROL Title] van het element `Classic Leather` wijzigt in `Nylon`.

![metadata](assets/metadata.png)

In dit geval slaat [!DNL Assets] de wijzigingen in de eigenschap **[!UICONTROL Title]** op in de parameter `dc:title` voor de metagegevens van de elementen die zijn opgeslagen in de elementenhiërarchie.

![metagegevens die zijn opgeslagen in het knooppunt asset in de gegevensopslagruimte](assets/metadata_stored.png)

>[!IMPORTANT]
>
>De functie voor terugschrijven is standaard niet ingeschakeld in [!DNL Assets]. Zie hoe te [toelaten meta-gegevensschrijver](#enable-xmp-writeback). MSM voor digitale elementen werkt niet wanneer terugschrijven van metagegevens is ingeschakeld. Bij terugschrijven wordt de overerving onderbroken.

### Terugschrijven XMP {#enable-xmp-writeback} inschakelen

[!UICONTROL DAM Metadata Writeback] wordt gebruikt om de metagegevens van een element te schrijven. Voer een van de volgende drie methoden uit om terugschrijven in te schakelen:

* Lanceerprogramma&#39;s gebruiken.
* Start `DAM MetaData Writeback` handmatig.
* Vorm werkschema om deel van naverwerking te zijn.

Voer de volgende stappen uit als u Launchers wilt gebruiken:

1. Als beheerder, toegang **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.
1. Selecteer [!UICONTROL Launcher] waarvoor **[!UICONTROL DAM MetaData Writeback]** kolomvertoningen **[!UICONTROL Workflow]**. Klik op **[!UICONTROL Properties]** op de werkbalk.

   ![Open de DAM-wizard voor het schrijven van metagegevens om de eigenschappen ervan te wijzigen en te activeren](assets/launcher-properties-metadata-writeback1.png)

1. Selecteer **[!UICONTROL Activate]** op de **[!UICONTROL Launcher Properties]** pagina. Klik op **[!UICONTROL Save & Close]**.

Als u de workflow slechts eenmaal handmatig op een element wilt toepassen, past u de [!UICONTROL DAM Metadata Writeback]-workflow vanuit de linkerrail toe.

Als u de workflow op alle geüploade elementen wilt toepassen, voegt u de workflow toe aan een naverwerkingsprofiel.

<!-- Commenting for now. Need to document how to enable metadata writeback. See CQDOC-17254.

### Enable XMP writeback {#enable-xmp-writeback}

To enable the metadata changes to be propagated to the renditions of the asset when uploading it, modify the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration in Configuration Manager.

1. To open Configuration Manager, access `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration.
1. Select the **[!UICONTROL Propagate XMP]** option, and then save the changes.

### Enable XMP write-back for specific renditions {#enable-xmp-writeback-for-specific-renditions}

To let the XMP write-back feature propagate metadata changes to select renditions, specify these renditions to the [!UICONTROL XMP Writeback Process] workflow step of DAM Metadata WriteBack workflow. By default, this step is configured with the original rendition.

For the XMP write-back feature to propagate metadata to the rendition thumbnails 140.100.png and 319.319.png, perform these steps.

1. Tap/click the AEM logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Workflow]** &gt; **[!UICONTROL Models]**.
1. From the Models page, open the **[!UICONTROL DAM Metadata Writeback]** workflow model.
1. In the **[!UICONTROL DAM Metadata Writeback]** properties page, open the **[!UICONTROL XMP Writeback Process]** step.
1. In the **[!UICONTROL Step Properties]** dialog box, tap/click the **[!UICONTROL Process]** tab.
1. In the **[!UICONTROL Arguments]** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, and then tap/click **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Save the changes.
1. To regenerate the Pyramid TIFF (PTIFF) renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata write-back workflow. PTIFF renditions are only created and stored locally in a Dynamic Media Hybrid implementation.

1. Save the workflow.

The metadata changes are propagated to the renditions renditions thumbnail.140.100.png and thumbnail.319.319.png of the asset, and not the others.
-->
