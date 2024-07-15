---
title: Kleurlabels voor afbeeldingen
description: Met Adobe Experience Manager Assets kunt u onderscheid maken tussen kleuren in een afbeelding en deze automatisch als tags toepassen. Vervolgens kunt u deze tags gebruiken om afbeeldingen te zoeken en te filteren.
exl-id: 3afa949b-ea1b-4b8e-ac94-06566e2c7147
feature: Smart Imaging, Interactive Images, Asset Management
role: User, Admin
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Kleurlabels voor afbeeldingen {#color-tag-images}

![ de Tagging van de Kleur Banner ](assets/banner-image.png)

Adobe Experience Manager (AEM) Assets gebruikt Adobe Sensei AI-mogelijkheden om kleuren in een afbeelding van elkaar te onderscheiden en deze automatisch als tags toe te passen bij opname. Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur.

U kunt het aantal kleuren binnen een bereik van 1 tot 40 configureren dat aan een afbeelding is gelabeld, zodat u later kunt zoeken naar afbeeldingen op basis van die kleuren. Experience Manager Assets past de labels toe op basis van de kleurdekking in een afbeelding. U kunt ook de weergave-indeling voor een kleurtag configureren.

In de volgende afbeelding ziet u de volgorde van taken die u uitvoert voor het configureren en beheren van kleurlabels voor afbeeldingen in Experience Manager Assets:

![ Tags voor de Kleur ](assets/color-tagging-dfd.gif)

## Ondersteunde bestandsindelingen {#supported-file-formats-color-tags}

| Bestandsindeling | Extensie | MIME-type | Invoerkleurruimte | Maximale ondersteunde bronbestandsgrootte | Maximaal ondersteunde resolutie voor bestandsgrootte |
|---|---|---|---|---|---|
| JPEG | .jpg en .jpeg | image/jpeg | sRGB | 15 GB | 20000 × 20000 pixels |
| PNG | .png | image/png | sRGB | 15 GB | 20000 × 20000 pixels |
| TIFF | .tif en .tiff | image/tiff | sRGB | 4 GB (beperkt door indelingsspecificaties) | 20000 × 20000 pixels |
| PSD | .psd | image/vnd.adobe.photoshop | sRGB | 2 GB (beperkt door indelingsspecificaties) | 20000 × 20000 pixels |
| GIF | .gif | image/gif | sRGB | 15 GB | 20000 × 20000 pixels |
| BMP | .bmp | image/bmp | sRGB | 4 GB (beperkt door indelingsspecificaties) | 20000 × 20000 pixels |

## Kleurtageigenschappen beheren {#manage-color-tagging-properties}

De eigenschappen voor kleurlabels voor afbeeldingen beheren:

1. Navigeer naar **[!UICONTROL Tools > Assets > Color Tagging]** .

   ![ het Tags toevoegen van de Kleur Eigenschappen ](assets/color-tag-settings.png)

1. Geef in het veld **[!UICONTROL Display Format]** een weergave-indeling voor de kleurtag op. Mogelijke opties zijn de kleurnaam, de RGB- of de HEX-indeling.

1. Geef in het veld **[!UICONTROL Limit]** het aantal kleuren op dat u voor de afbeeldingen wilt labelen. Deze kleuren worden weergegeven wanneer u de eigenschappen van een afbeelding bekijkt. U kunt een getal tussen 1 en 40 definiëren in dit veld. De standaardwaarde voor dit veld is tien kleuren.

1. Geef het minimale percentage van de kleurdekking op om een kleurcode op te nemen in de zoekresultaten in het veld **[!UICONTROL Coverage/Dominance Threshold %]** . Als de dekking van de rode kleur in een afbeelding bijvoorbeeld tien procent is en u in dit veld negen procent definieert, wordt de afbeelding opgenomen wanneer u naar afbeeldingen met rode kleur zoekt. Als de dekking van de rode kleur in een afbeelding echter tien procent is en u in dit veld 11 procent definieert, wordt de afbeelding niet opgenomen wanneer u naar afbeeldingen met rode kleur zoekt.

   U kunt een willekeurig getal tussen vijf en 100 opgeven in dit veld. De standaardwaarde is 11.

   >[!NOTE]
   >
   >Adobe raadt u aan een waarde te gebruiken die dicht bij de standaardwaarde in dit veld ligt. Als u een hoge getalwaarde instelt voor dit veld (bijvoorbeeld hoger dan 25), worden mogelijk weinig zoekresultaten geretourneerd. Als u een lage getalwaarde instelt (bijvoorbeeld lager dan 6), worden mogelijk te veel zoekresultaten geretourneerd. Dit is mogelijk niet nuttig.

1. Klik op **[!UICONTROL Save]**.


   >[!VIDEO](https://video.tv.adobe.com/v/340108)


### Kleurlabels uitschakelen {#disable-color-tagging}

Kleurlabels voor afbeeldingen zijn standaard ingeschakeld. U kunt kleurlabeling op mapniveau uitschakelen. Alle onderliggende mappen overerven de eigenschappen voor kleurlabels van de bovenliggende map.

Kleurlabelen op mapniveau uitschakelen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager > Assets > Files]** .

1. Selecteer de map en klik op **[!UICONTROL Properties]** .

1. Navigeer op het tabblad **[!UICONTROL Asset Processing]** naar de map **[!UICONTROL Color Tags for images]** . Selecteer een van de volgende waarden in de vervolgkeuzelijst:

   * Overgenomen - De map neemt de opties voor in- of uitschakelen over van de bovenliggende map.

   * Inschakelen - Schakelt kleurlabeling in voor de geselecteerde map.

   * Uitschakelen - Schakelt kleurcodering voor de geselecteerde map uit.

   ![ het Tags toevoegen van de Kleur Montages ](assets/color-tags-folder.png)

## Metagegevensschema configureren om component voor slimme kleurcodes toe te voegen {#configure-metadata-schema}

Metagegevensschema&#39;s bevatten specifieke velden waarin specifieke informatie moet worden ingevuld. Het bevat ook lay-outinformatie om meta-gegevensgebieden op een gebruikersvriendelijke manier te tonen. Metagegevenseigenschappen zijn onder andere titel, beschrijving, MIME-typen, tags en meer. U kunt de [!UICONTROL Metadata Schema Forms] redacteur gebruiken om de bestaande schema&#39;s te wijzigen of douanemetagegevensschema&#39;s toe te voegen.

>[!NOTE]
>
>Het veld Slimme kleur is beschikbaar in het standaardmetagegevensschema. Als u een aangepast metagegevensschema gebruikt, configureert u het schema zodanig dat een veld voor een slimme-kleurtag wordt toegevoegd.

U voegt als volgt de component Slimme kleurcodes toe aan de formuliereditor voor het metagegevensschema:

1. Navigeer naar **[!UICONTROL Tools > Assets > Metadata Schemas]** .

1. Selecteer de schemanaam en klik **[!UICONTROL Edit]**.

1. Sleep **[!UICONTROL Smart Color Tags]** van het **[!UICONTROL Build Form]** lusje aan **[!UICONTROL Metadata Schema Form Editor]**.

1. Klik op **[!UICONTROL Smart Color Tag Field]** in de **[!UICONTROL Metadata Schema Form Editor]** .

1. Geef een toepasselijke waarde op in het veld **[!UICONTROL Field Label]** op het tabblad **[!UICONTROL Settings]** .

1. Klik op **[!UICONTROL Save]**.

   >[!VIDEO](https://video.tv.adobe.com/v/340124)

## Kleurlabels voor bestaande afbeeldingen in DAM {#color-tags-existing-images}

De bestaande afbeeldingen in DAM hebben niet automatisch een kleurlabel. [!UICONTROL Reprocess Assets] handmatig om er kleurcodes voor te genereren.

Voer de volgende stappen uit als u afbeeldingen met kleurcodes of mappen (inclusief submappen) van elementen in de opslagplaats voor elementen wilt kleuren:

1. Selecteer het logo [!DNL Adobe Experience Manager] en selecteer vervolgens elementen op de pagina [!UICONTROL Navigation] .

1. Selecteer [!UICONTROL Files] .

1. Navigeer in de Assets-interface naar de map waarop u kleurcodes wilt toepassen.

1. Selecteer de volledige map of specifieke afbeeldingen.

1. Selecteer ![ opnieuw verwerken activa pictogram ](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Reprocess Assets] pictogram en selecteer de [!UICONTROL Full Process] optie.

Wanneer het proces is voltooid, navigeert u naar de pagina [!UICONTROL Properties] van een willekeurige afbeelding in de map. De automatisch toegevoegde tags worden weergegeven in de sectie [!UICONTROL Smart Color Tags] op het tabblad [!UICONTROL Basic] .


## Slimme-kleurtags voor afbeeldingen weergeven {#view-color-tags}

Slimme-kleurtags voor afbeeldingen weergeven:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager > Assets > Files]** .

1. Klik op de juiste map en selecteer de afbeelding.

1. Selecteer **[!UICONTROL Properties]** en bekijk de tags in het veld **[!UICONTROL Smart Color Tags]** .

   ![ de Markeringen van de Kleur van de Mening ](assets/view-color-tags.png)

   Houd de muis boven een kleurtag zodat u de **[!UICONTROL Coverage/Dominance Threshold %]** -kleur van een afbeelding kunt bekijken.

## AEM Assets-kleurvoorspelling configureren {#configure-search-predicate}

U kunt een zoekfilter configureren voor afbeeldingen. Vervolgens kunt u de zoekcriteria baseren op een specifieke kleur om de resultaten te filteren.

>[!NOTE]
>
>Configureer de AEM Assets-kleurvoorspelling alleen als u het standaardzoekformulier niet gebruikt.

Als u het zoekfilter wilt configureren, maakt u een voorspelling van de elementkleur met behulp van de Assets Admin Search Rail.

U configureert als volgt het zoekfilter:

1. Navigeer naar **[!UICONTROL Tools > General > Search Forms]** .

1. Selecteer **[!UICONTROL Assets Admin Search Rail]** en klik op **[!UICONTROL Edit]** .

1. Sleep **[!UICONTROL Asset Color Predicate]** van het **[!UICONTROL Select Predicate]** lusje aan **[!UICONTROL Search Form Editor]**.

1. Geef een toepasselijke waarde op in het veld **[!UICONTROL Field Label]** op het tabblad **[!UICONTROL Settings]** .

1. Klik op **[!UICONTROL Done]** om de instellingen op te slaan.

   >[!VIDEO](https://video.tv.adobe.com/v/340110)

## Afbeeldingen zoeken op basis van kleuren {#search-images-based-on-colors}

>[!VIDEO](https://video.tv.adobe.com/v/340761)

Na het vormen van alle kleur etiketterend eigenschappen en [ vormend de kleur van Assets voorspellen ](#search-images-based-on-colors), kunt u beelden zoeken die op een kleur als filter worden gebaseerd.

Zo zoekt u afbeeldingen op basis van kleuren:

1. Navigeer naar **[!UICONTROL Assets > Files]** .

1. Selecteer **[!UICONTROL Filter]** in de vervolgkeuzelijst.
   ![ Filter Assets ](assets/filter-assets.png)

1. Selecteer het [ de kleurenpredikaat van AEM Assets ](#configure-search-predicate).

1. Sleep de kleurkiezer om de gewenste kleur te selecteren. De geselecteerde kleur wordt weergegeven in het alleen-lezen veld dat beschikbaar is onder de kleurkiezer. U kunt RGB of HEX selecteren als de weergave-indeling voor de kleur.

   ![ de Plukker van de Kleur ](assets/color-picker-color-tags.png)

   U kunt afbeeldingen filteren op basis van de selectie van één kleur. De beelden die de geselecteerde kleur als één van de slimme kleurenmarkeringen en boven [ Coverage/de Verschijning % van de Dominantie ](#manage-color-tagging-settings) vertoning in de juiste ruit hebben.

1. Wis de filter door X in de bar van het Onderzoek te klikken.

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
