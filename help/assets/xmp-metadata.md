---
title: XMP-metagegevens
description: Meer informatie over de metagegevensstandaard van XMP (Extensible Metadata Platform) voor metagegevensbeheer. Experience Manager gebruikt deze als een gestandaardiseerde indeling voor het maken, verwerken en uitwisselen van metagegevens.
contentOwner: AG
feature: Metadata
role: Admin, User
exl-id: fd9af408-d2a3-4c7a-9423-c4b69166f873
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 13%

---

# XMP-metagegevens {#xmp-metadata}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/xmp-writeback.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

XMP (Extensible Metadata Platform) is de metagegevensstandaard die Experience Manager Assets gebruikt voor alle metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal verschillende toepassingen.

Naast het aanbieden van universele meta-gegevens het coderen die in alle dossierformaten kunnen worden ingebed, verstrekt XMP een rijk [ inhoudsmodel ](#xmp-core-concepts) en wordt [ gesteund door Adobe ](#advantages-of-xmp) en andere bedrijven, zodat de gebruikers van XMP in combinatie met [!DNL Assets] een krachtig platform hebben om op te bouwen.

## Overzicht en ecosysteem van XMP {#xmp-ecosystem}

[!DNL Assets] biedt native ondersteuning voor de XMP-metagegevensstandaard. XMP is een standaard voor het verwerken en opslaan van gestandaardiseerde en merkgebonden metagegevens in digitale middelen. XMP is ontworpen als de algemene standaard waarmee meerdere toepassingen effectief kunnen werken met metagegevens.

Productieprofessionals gebruiken bijvoorbeeld de ingebouwde XMP-ondersteuning in Adobe-toepassingen om informatie door te geven in meerdere bestandsindelingen. De [!DNL Assets] -opslagplaats extraheert de XMP-metagegevens en gebruikt deze om de levenscyclus van de inhoud te beheren en biedt de mogelijkheid om automatiseringsworkflows te maken.

XMP normaliseert hoe metagegevens worden gedefinieerd, gemaakt en verwerkt door een gegevensmodel, een opslagmodel en schema&#39;s op te geven. Al deze concepten worden behandeld in deze sectie.

Alle oudere metagegevens van EXIF, ID3 of Microsoft Office worden automatisch vertaald naar XMP. Deze gegevens kunnen worden uitgebreid ter ondersteuning van klantspecifiek metagegevensschema, zoals productcatalogi.

Metagegevens in XMP bestaan uit een set eigenschappen. Deze eigenschappen worden altijd geassocieerd met een specifieke entiteit die als middel wordt bedoeld; namelijk zijn de eigenschappen &quot;over&quot;de middel. In het geval van XMP is de bron altijd het middel.

XMP definieert een [metadatamodel](https://nl.wikipedia.org/wiki/Metadata) dat kan worden gebruikt met elke gedefinieerde set metadataitems. XMP definieert ook bepaalde [schema&#39;s](https://nl.wikipedia.org/wiki/XML_schema) voor basiseigenschappen die nuttig zijn voor het opnemen van de geschiedenis van een resource tijdens het doorlopen van meerdere verwerkingsstappen, van het fotograferen, [scannen](https://en.wikipedia.org/wiki/Image_scanner) of ontwerpen als tekst, het doorlopen van fotobewerkingsstappen (zoals [bijsnijden](https://en.wikipedia.org/wiki/Cropping_%28image%29) of kleuraanpassing) tot het samenvoegen in een uiteindelijke afbeelding. Met XMP kan elk softwareprogramma of apparaat in de loop van de tijd zijn eigen informatie toevoegen aan een digitale resource, die vervolgens in het uiteindelijke digitale bestand kan worden bewaard.

XMP wordt doorgaans geserialiseerd en opgeslagen met behulp van een subset van het [W3C](https://nl.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://nl.wikipedia.org/wiki/Resource_Description_Framework) (RDF), dat op zijn beurt wordt uitgedrukt in [XML](https://nl.wikipedia.org/wiki/XML).

### Voordelen van XMP {#advantages-of-xmp}

XMP heeft de volgende voordelen ten opzichte van andere coderingsstandaarden en -schema&#39;s:

* Op XMP gebaseerde metagegevens zijn zeer krachtig en fijnkorrelig.
* Met XMP kunt u meerdere waarden voor één eigenschap gebruiken.
* XMP heeft gestandaardiseerde codering, waarmee u metagegevens eenvoudig kunt uitwisselen.
* XMP is uitbreidbaar. U kunt aanvullende informatie aan uw elementen toevoegen.

De XMP-standaard is uitbreidbaar, zodat u aangepaste typen metagegevens kunt toevoegen aan de XMP-gegevens. EXIF heeft daarentegen geen vaste lijst met eigenschappen die niet kunnen worden uitgebreid.

>[!NOTE]
>
>In XMP kunnen binaire gegevenstypen doorgaans niet worden ingesloten. Als u binaire gegevens wilt meenemen in XMP, bijvoorbeeld miniatuurafbeeldingen, moeten deze worden gecodeerd in een XML-vriendelijke indeling, zoals `Base64` .

### Basisbegrippen van XMP {#xmp-core-concepts}

**Namespaces en schema&#39;s**

Een XMP-schema is een set eigenschapnamen in een algemene XML-naamruimte die
het gegevenstype en de beschrijvende informatie. Een XMP-schema wordt aangeduid met de XML-naamruimte-URI. Het gebruik van naamruimten voorkomt conflicten tussen eigenschappen in verschillende schema&#39;s die dezelfde naam maar een andere betekenis hebben.

Bijvoorbeeld, zou het **bezit van de Maker** in twee onafhankelijk ontworpen schema&#39;s de persoon kunnen betekenen die tot de activa leidde of het de toepassing kon betekenen die tot de activa (bijvoorbeeld, Adobe Photoshop) leidde.

**eigenschappen en waarden van XMP**

XMP kan eigenschappen van een of meer schema&#39;s bevatten. Een standaardsubset die door veel Adobe-toepassingen wordt gebruikt, kan bijvoorbeeld het volgende zijn:

* Dublin-kernschema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP-basisschema: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP-schema voor rechtenbeheer: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP-schema voor mediabeheer: `xmpMM:DocumentID`

**de alternatieven van de Taal**

XMP biedt u de mogelijkheid om een eigenschap `xml:lang` aan teksteigenschappen toe te voegen om de taal van de tekst op te geven.

## Terugschrijven naar XMP-uitvoeringen {#xmp-writeback-to-renditions}

Met deze XMP-schrijffunctie in [!DNL Adobe Experience Manager Assets] worden de wijzigingen in de metagegevens van de uitvoeringen van het oorspronkelijke element gerepliceerd.
Wanneer u de metagegevens van een element wijzigt vanuit [!DNL Assets] of wanneer u het element uploadt, worden de wijzigingen in eerste instantie opgeslagen in het metagegevensknooppunt in de elementenhiërarchie. Met de functie Terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De functie schrijft alleen die metagegevenseigenschappen terug die `jcr` naamruimte gebruiken. Een eigenschap met de naam `dc:title` wordt teruggeschreven, maar een eigenschap met de naam `mytitle` niet.

Neem bijvoorbeeld een scenario waarin u de eigenschap [!UICONTROL Title] van het element met de naam `Classic Leather` to `Nylon` wijzigt.

![ meta-gegevens ](assets/metadata.png)

In dit geval slaat [!DNL Assets] de wijzigingen in de eigenschap **[!UICONTROL Title]** op in de parameter `dc:title` voor de metagegevens van de elementen die zijn opgeslagen in de elementenhiërarchie.

![ die meta-gegevens in activaknoop in de bewaarplaats worden opgeslagen ](assets/metadata_stored.png)

>[!IMPORTANT]
>
>De functie Terugschrijven is niet standaard ingeschakeld in [!DNL Assets] . Zie hoe te [ meta-gegevensschrijver ](#enable-xmp-writeback) toelaten. MSM voor digitale elementen werkt niet wanneer terugschrijven van metagegevens is ingeschakeld. Bij terugschrijven wordt de overerving onderbroken.

### Terugschrijven naar XMP inschakelen {#enable-xmp-writeback}

[!UICONTROL DAM Metadata Writeback] wordt gebruikt om de metagegevens van een element te schrijven. Voer een van de volgende drie methoden uit om terugschrijven in te schakelen:

* Lanceerinrichtingen gebruiken.
* Start de `DAM MetaData Writeback` -workflow handmatig.
* Vorm werkschema om deel van naverwerking te zijn.

Voer de volgende stappen uit als u Launchers wilt gebruiken:

1. Als beheerder opent u **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]** .
1. Selecteer de [!UICONTROL Launcher] waarvoor de **[!UICONTROL Workflow]** kolom **[!UICONTROL DAM MetaData Writeback]** wordt weergegeven. Klik op **[!UICONTROL Properties]** op de werkbalk.

   ![ Uitgezochte DAM de lancerer van de meta-gegevensbrief om zijn eigenschappen te wijzigen en het te activeren ](assets/launcher-properties-metadata-writeback1.png)

1. Selecteer **[!UICONTROL Activate]** op de **[!UICONTROL Launcher Properties]** -pagina. Klik op **[!UICONTROL Save & Close]**.

Als u de workflow slechts eenmaal handmatig op een element wilt toepassen, past u de [!UICONTROL DAM Metadata Writeback] -workflow vanuit het linkerspoor toe.

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

1. Select the Experience Manager logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Workflow]** &gt; **[!UICONTROL Models]**.
1. From the Models page, open the **[!UICONTROL DAM Metadata Writeback]** workflow model.
1. In the **[!UICONTROL DAM Metadata Writeback]** properties page, open the **[!UICONTROL XMP Writeback Process]** step.
1. In the **[!UICONTROL Step Properties]** dialog box, select the **[!UICONTROL Process]** tab.
1. In the **[!UICONTROL Arguments]** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, and then select **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Save the changes.
1. To regenerate the Pyramid TIFF (PTIFF) renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata write-back workflow. PTIFF renditions are only created and stored locally in a Dynamic Media Hybrid implementation.

1. Save the workflow.

The metadata changes are propagated to the renditions renditions thumbnail.140.100.png and thumbnail.319.319.png of the asset, and not the others.
-->

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
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
