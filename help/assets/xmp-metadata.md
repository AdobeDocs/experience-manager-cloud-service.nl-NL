---
title: Metagegevens XMP
description: Leer meer over de metagegevensstandaard van het XMP (Extensible Metadata Platform) voor metagegevensbeheer. Deze wordt door de Experience Manager gebruikt als een gestandaardiseerde indeling voor het maken, verwerken en uitwisselen van metagegevens.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: fd9af408-d2a3-4c7a-9423-c4b69166f873
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 13%

---

# Metagegevens XMP {#xmp-metadata}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/xmp-writeback.html) |
| AEM as a Cloud Service | Dit artikel |

XMP (Extensible Metadata Platform) is de metagegevensstandaard die Experience Manager Assets gebruikt voor alle metagegevensbeheer. XMP biedt een standaardindeling voor het maken, verwerken en uitwisselen van metagegevens voor een groot aantal verschillende toepassingen.

Naast het aanbieden van universele metagegevenscodering die in alle bestandsindelingen kan worden ingesloten, biedt XMP [inhoudsmodel](#xmp-core-concepts) en is [ondersteund door Adobe](#advantages-of-xmp) en andere ondernemingen, zodat de gebruikers van XMP in combinatie met [!DNL Assets] beschikken over een krachtig platform waarop kan worden voortgebouwd.

## XMP overzicht en ecosysteem {#xmp-ecosystem}

[!DNL Assets] native ondersteunt de standaard voor XMP metagegevens. XMP is een standaard voor het verwerken en opslaan van gestandaardiseerde en merkgebonden metagegevens in digitale elementen. XMP wordt ontworpen om de gemeenschappelijke norm te zijn die veelvoudige toepassingen toestaat om effectief met meta-gegevens te werken.

Productieprofessionals gebruiken bijvoorbeeld de ingebouwde XMP binnen de toepassingen van de Adobe om informatie door te geven over meerdere bestandsindelingen. De [!DNL Assets] opslagplaats extraheert de XMP metagegevens en gebruikt deze om de levenscyclus van de inhoud te beheren en biedt de mogelijkheid om automatiseringsworkflows te maken.

XMP standaardiseren hoe metagegevens worden gedefinieerd, gemaakt en verwerkt door een gegevensmodel, een opslagmodel en schema&#39;s op te geven. Al deze concepten worden behandeld in deze sectie.

Alle verouderde meta-gegevens van EXIF, ID3, of Microsoft Office wordt automatisch vertaald aan XMP, die kan worden uitgebreid om klant-specifiek meta-gegevensschema, zoals productcatalogi te steunen.

Metagegevens in XMP bestaan uit een set eigenschappen. Deze eigenschappen worden altijd geassocieerd met een specifieke entiteit die als middel wordt bedoeld; namelijk zijn de eigenschappen &quot;over&quot;de middel. In het geval van XMP is de bron altijd het middel.

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
>XMP staat over het algemeen niet binaire gegevenstypes toe om worden ingebed. Als u binaire gegevens bijvoorbeeld in XMP wilt meenemen, moeten deze worden gecodeerd in een XML-vriendelijke indeling, zoals `Base64`.

### XMP kernbegrippen {#xmp-core-concepts}

**Naamruimten en schema&#39;s**

Een XMP schema is een reeks eigenschapnamen in een gemeenschappelijke XML-naamruimte die het gegevenstype en beschrijvende informatie bevat. Een XMP schema wordt geïdentificeerd door zijn XML namespace URI. Het gebruik van naamruimten voorkomt conflicten tussen eigenschappen in verschillende schema&#39;s die dezelfde naam maar een andere betekenis hebben.

Bijvoorbeeld de **Maker** eigenschap in twee onafhankelijk ontworpen schema&#39;s kan de persoon zijn die het element heeft gemaakt of de toepassing die het element heeft gemaakt (bijvoorbeeld Adobe Photoshop).

**Eigenschappen en waarden XMP**

XMP kunnen eigenschappen van een of meer schema&#39;s omvatten. Een standaardsubset die bijvoorbeeld door veel Adobe-toepassingen wordt gebruikt, kan het volgende zijn:

* Dublin-kernschema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* Basisschema XMP: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* Schema voor XMP rechtenbeheer: `xmpRights:WebStatement`, `xmpRights:Marked`
* Schema voor mediabeheer XMP: `xmpMM:DocumentID`

**Taalalternatieven**

XMP biedt u de mogelijkheid een `xml:lang` eigenschap aan teksteigenschappen om de taal van de tekst op te geven.

## Terugverwijzing naar vertoningen XMP {#xmp-writeback-to-renditions}

Deze XMP functie voor terugschrijven in [!DNL Adobe Experience Manager Assets] Hiermee worden de wijzigingen in de metagegevens van de uitvoeringen van het oorspronkelijke element gerepliceerd.
Wanneer u de metagegevens van een element wijzigt vanuit [!DNL Assets] of tijdens het uploaden van het element, worden de wijzigingen in eerste instantie opgeslagen in het metagegevensknooppunt in de elementenhiërarchie. Met de functie Terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De functie schrijft alleen die metagegevenseigenschappen terug die `jcr` namespace, dat wil zeggen, een eigenschap genaamd `dc:title` is teruggeschreven maar een eigenschap met een naam `mytitle` is niet.

Neem bijvoorbeeld een scenario waarin u het [!UICONTROL Title] eigendom van het getitelde actief `Classic Leather` tot `Nylon`.

![metagegevens](assets/metadata.png)

In dit geval: [!DNL Assets] Hiermee slaat u de wijzigingen op in de **[!UICONTROL Title]** eigenschap in de `dc:title` parameter voor de metagegevens van elementen die zijn opgeslagen in de elementhiërarchie.

![metagegevens opgeslagen in elementknooppunt in de gegevensopslagruimte](assets/metadata_stored.png)

>[!IMPORTANT]
>
>De functie Terugschrijven is niet standaard ingeschakeld in [!DNL Assets]. Zie hoe te [metagegevensterugkoppeling inschakelen](#enable-xmp-writeback). MSM voor digitale elementen werkt niet wanneer terugschrijven van metagegevens is ingeschakeld. Bij terugschrijven wordt de overerving onderbroken.

### Terugschrijven XMP inschakelen {#enable-xmp-writeback}

[!UICONTROL DAM Metadata Writeback] wordt gebruikt om de metagegevens van een element te schrijven. Voer een van de volgende drie methoden uit om terugschrijven in te schakelen:

* Lanceerinrichtingen gebruiken.
* Handmatig starten `DAM MetaData Writeback` workflow.
* Vorm werkschema om deel van naverwerking te zijn.

Voer de volgende stappen uit als u Launchers wilt gebruiken:

1. Als beheerder, toegang **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.
1. Selecteer de [!UICONTROL Launcher] waarvoor de **[!UICONTROL Workflow]** kolomweergaven **[!UICONTROL DAM MetaData Writeback]**. Klik op **[!UICONTROL Properties]** op de werkbalk.

   ![Open de DAM-wizard voor het schrijven van metagegevens om de eigenschappen ervan te wijzigen en te activeren](assets/launcher-properties-metadata-writeback1.png)

1. Selecteren **[!UICONTROL Activate]** op de **[!UICONTROL Launcher Properties]** pagina. Klik op **[!UICONTROL Save & Close]**.

Als u de workflow slechts eenmaal op een element wilt toepassen, past u de toepassing toe [!UICONTROL DAM Metadata Writeback] workflow van de linkerspoorstaaf.

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
