---
title: Kleurlabels voor afbeeldingen
description: Met Experience Manager Assets kunt u onderscheid maken tussen kleuren in een afbeelding en deze automatisch als tags toepassen. Vervolgens kunt u deze tags gebruiken om afbeeldingen te zoeken en te filteren.
exl-id: 3afa949b-ea1b-4b8e-ac94-06566e2c7147
source-git-commit: 2859fa68713b46083314d207abc4dec2e088a173
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 2%

---

# Kleurlabels voor afbeeldingen {#color-tag-images}

![Kleurlabelbanner](assets/banner-image.png)

Experience Manager Assets gebruikt Adobe Sensei AI-mogelijkheden om kleuren in een afbeelding te onderscheiden en deze automatisch als tags toe te passen bij opname. Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur.

U kunt het aantal kleuren binnen een bereik van 1 tot 40 configureren dat aan een afbeelding is gelabeld, zodat u later kunt zoeken naar afbeeldingen op basis van die kleuren. Experience Manager Assets past de labels toe op basis van de kleurdekking in een afbeelding. U kunt ook de weergave-indeling voor een kleurtag configureren.

In de volgende afbeelding ziet u de volgorde van taken die u uitvoert voor het configureren en beheren van kleurlabels voor afbeeldingen in Experience Manager Assets:

![Kleurlabels](assets/color-tagging-dfd.gif)

## Ondersteunde bestandsindelingen {#supported-file-formats-color-tags}

| Bestandsindeling | Extensie | MIME-type | Invoerkleurruimte | Maximale ondersteunde bronbestandsgrootte | Maximaal ondersteunde resolutie voor bestandsgrootte |
|---|---|---|---|---|---|
| JPEG | .jpg, .jpeg | image/jpeg | sRGB | 15GB | 20000px X, 20000px |
| PNG | .png | image/png | sRGB | 15GB | 20000px X, 20000px |
| TIFF | .tif, .tiff | image/tiff | sRGB | 4 GB (beperkt door indelingsspecificaties) | 20000px X, 20000px |
| PSD | .psd | image/vnd.adobe.photoshop | sRGB | 2 GB (beperkt door indelingsspecificaties) | 20000px X, 20000px |
| GIF | .gif | image/gif | sRGB | 15GB | 20000px X, 20000px |
| BMP | .bmp | image/bmp | sRGB | 4 GB (beperkt door indelingsspecificaties) | 20000px X, 20000px |

## Kleurtageigenschappen beheren {#manage-color-tagging-properties}

De eigenschappen voor kleurlabels voor afbeeldingen beheren:

1. Ga naar **[!UICONTROL Tools > Assets > Color Tagging]**.

   ![Eigenschappen van kleurtags](assets/color-tag-settings.png)

1. Geef een indeling op voor de weergave van de kleurtag in het dialoogvenster **[!UICONTROL Display Format]** veld. Mogelijke opties zijn de kleurnaam, de RGB- of de HEX-indeling.

1. Geef het aantal kleuren op dat u wilt labelen voor de afbeeldingen in het dialoogvenster **[!UICONTROL Limit]** veld. Deze kleuren worden weergegeven wanneer u de eigenschappen van een afbeelding bekijkt.  U kunt een getal tussen 1 en 40 definiëren in dit veld. De standaardwaarde voor dit veld is tien kleuren.

1. Geef het minimale percentage voor kleurdekking op om een kleurcode op te nemen in de zoekresultaten in het dialoogvenster **[!UICONTROL Coverage/Dominance Threshold %]** veld. Als de dekking van de rode kleur in een afbeelding bijvoorbeeld tien procent is en u in dit veld negen procent definieert, wordt de afbeelding opgenomen wanneer u naar afbeeldingen met rode kleur zoekt. Als de dekking van de rode kleur in een afbeelding echter tien procent is en u in dit veld elf procent definieert, wordt de afbeelding niet opgenomen wanneer u naar afbeeldingen met rode kleur zoekt.

   U kunt een willekeurig getal tussen vijf en honderd opgeven in dit veld. De standaardwaarde is elf.

   >[!NOTE]
   >
   >Adobe raadt u aan een waarde te gebruiken die de standaardwaarde in dit veld benadert. Als u een hoge getalwaarde instelt voor dit veld (bijvoorbeeld hoger dan 25), worden mogelijk zeer weinig zoekresultaten geretourneerd. Als u een lage getalwaarde instelt (bijvoorbeeld lager dan 6), worden mogelijk te veel zoekresultaten geretourneerd. Dit is mogelijk niet nuttig.

1. Klik op **[!UICONTROL Save]**.


   >[!VIDEO](https://video.tv.adobe.com/v/340108)


### Kleurlabels uitschakelen {#disable-color-tagging}

Kleurlabels voor afbeeldingen zijn standaard ingeschakeld. U kunt kleurlabeling op mapniveau uitschakelen. Alle onderliggende mappen overerven de eigenschappen voor kleurlabels van de bovenliggende map.

Kleurlabelen op mapniveau uitschakelen:

1. Ga naar **[!UICONTROL Adobe Experience Manager > Assets > Files]**.

1. Selecteer de map en klik op **[!UICONTROL Properties]**.

1. In de **[!UICONTROL Asset Processing]** tabblad, navigeert u naar de **[!UICONTROL Color Tags for images]** map. Selecteer een van de volgende waarden in de vervolgkeuzelijst:

   * Overgenomen - De map neemt de opties voor in- of uitschakelen over van de bovenliggende map.

   * Inschakelen - Schakelt kleurlabeling in voor de geselecteerde map.

   * Uitschakelen - Schakelt kleurcodering voor de geselecteerde map uit.

   ![Instellingen voor kleurlabels](assets/color-tags-folder.png)

## Metagegevensschema configureren om component voor slimme kleurcodes toe te voegen {#configure-metadata-schema}

Metagegevensschema&#39;s bevatten specifieke velden waarin specifieke informatie moet worden ingevuld. Het bevat ook lay-outinformatie om meta-gegevensgebieden op een gebruikersvriendelijke manier te tonen. Metagegevenseigenschappen zijn onder andere titel, beschrijving, MIME-typen, tags en meer. U kunt de [!UICONTROL Metadata Schema Forms] editor om de bestaande schema&#39;s te wijzigen of aangepaste schema&#39;s voor metagegevens toe te voegen.

>[!NOTE]
>
>Het veld Slimme kleur is beschikbaar in het standaardmetagegevensschema. Als u een aangepast metagegevensschema gebruikt, configureert u het schema zodanig dat het veld voor slimme-kleurcodes wordt toegevoegd.

U voegt als volgt de component Slimme kleurcodes toe aan de formuliereditor voor het metagegevensschema:

1. Ga naar **[!UICONTROL Tools > Assets > Metadata Schemas]**.

1. Selecteer de schemanaam en klik **[!UICONTROL Edit]**.

1. Slepen **[!UICONTROL Smart Color Tags]** van de **[!UICONTROL Build Form]** aan de **[!UICONTROL Metadata Schema Form Editor]**.

1. Klik op de knop **[!UICONTROL Smart Color Tag Field]** in de **[!UICONTROL Metadata Schema Form Editor]**.

1. Geef een geschikte waarde op in het dialoogvenster **[!UICONTROL Field Label]** in het **[!UICONTROL Settings]**  tab.

1. Klik op **[!UICONTROL Save]**.

   >[!VIDEO](https://video.tv.adobe.com/v/340124)

## Kleurlabels voor bestaande afbeeldingen in DAM {#color-tags-existing-images}

De al bestaande afbeeldingen in DAM worden niet automatisch van een kleurlabel voorzien. U moet [!UICONTROL Reprocess Assets] handmatig om er kleurcodes voor te genereren.

Voer de volgende stappen uit als u afbeeldingen met kleurcodes of mappen (inclusief submappen) van elementen die al in de opslagplaats voor elementen bestaan, wilt kleuren:

1. Selecteer [!DNL Adobe Experience Manager] logo en selecteer vervolgens elementen in het [!UICONTROL Navigation] pagina.

1. Selecteren [!UICONTROL Files] om de interface Elementen weer te geven.

1. Navigeer naar de map waarop u kleurcodes wilt toepassen.

1. Selecteer de volledige map of specifieke afbeeldingen.

1. Selecteren ![Pictogram Elementen opnieuw verwerken](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Reprocess Assets] en selecteert u de [!UICONTROL Full Process] optie.

Als het proces is voltooid, navigeert u naar de [!UICONTROL Properties] pagina van om het even welke beeld binnen de omslag. De automatisch toegevoegde tags worden weergegeven in [!UICONTROL Smart Color Tags] sectie in [!UICONTROL Basic] tab.


## Slimme-kleurtags voor afbeeldingen weergeven {#view-color-tags}

Slimme-kleurtags voor afbeeldingen weergeven:

1. Ga naar **[!UICONTROL Adobe Experience Manager > Assets > Files]**.

1. Klik op de juiste map en selecteer de afbeelding.

1. Selecteren **[!UICONTROL Properties]** en bekijk de tags in de **[!UICONTROL Smart Color Tags]** veld.

   ![Kleurlabels weergeven](assets/view-color-tags.png)

   Houd de muis boven een kleurtag om de **[!UICONTROL Coverage/Dominance Threshold %]** van een kleur in een afbeelding.

## AEM Assets-kleurvoorspelling configureren {#configure-search-predicate}

U kunt het zoekfilter voor afbeeldingen configureren. Vervolgens kunt u de zoekcriteria baseren op een specifieke kleur om de resultaten te filteren.

>[!NOTE]
>
>Configureer alleen de AEM Assets-kleurvoorspelling als u het standaardzoekformulier niet gebruikt.

Als u het zoekfilter wilt configureren, maakt u een voorspelling van de elementkleur met behulp van de zoekfunctie voor middelenbeheer.

Het zoekfilter configureren:

1. Ga naar **[!UICONTROL Tools > General > Search Forms]**.

1. Selecteren **[!UICONTROL Assets Admin Search Rail]** en klik op **[!UICONTROL Edit]**.

1. Slepen **[!UICONTROL Asset Color Predicate]** van de **[!UICONTROL Select Predicate]** aan de **[!UICONTROL Search Form Editor]**.

1. Geef een geschikte waarde op in het dialoogvenster **[!UICONTROL Field Label]** in het **[!UICONTROL Settings]**  tab.

1. Klikken **[!UICONTROL Done]** om de instellingen op te slaan.

   >[!VIDEO](https://video.tv.adobe.com/v/340110)

## Afbeeldingen zoeken op basis van kleuren {#search-images-based-on-colors}

>[!VIDEO](https://video.tv.adobe.com/v/340761)

Na het configureren van alle eigenschappen voor kleurlabels en [configureren, voorspelling van middelenkleur](#search-images-based-on-colors), kunt u afbeeldingen op basis van een kleur zoeken als een filter.

Zo zoekt u afbeeldingen op basis van kleuren:

1. Ga naar **[!UICONTROL Assets > Files]**.

1. Selecteren **[!UICONTROL Filter]** in de vervolgkeuzelijst.
   ![Elementen filteren](assets/filter-assets.png)

1. Selecteer [AEM Assets-kleurvoorspelling](#configure-search-predicate).

1. Sleep de kleurkiezer om de gewenste kleur te selecteren. De geselecteerde kleur wordt weergegeven in het alleen-lezen veld dat beschikbaar is onder de kleurkiezer. U kunt RGB of HEX selecteren als de weergave-indeling voor de kleur.

   ![Kleurkiezer](assets/color-picker-color-tags.png)

   U kunt afbeeldingen filteren op basis van de selectie van één kleur. De afbeeldingen met de geselecteerde kleur als een van de slimme-kleurtags en boven de [Dekking/Dominantiedrempel %](#manage-color-tagging-settings) in het rechterdeelvenster.

1. Klik op x in de zoekbalk om het filter te wissen.
