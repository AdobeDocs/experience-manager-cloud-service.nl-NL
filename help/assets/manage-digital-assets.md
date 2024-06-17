---
title: Digitale middelen beheren
description: Meer informatie over verschillende methoden voor middelenbeheer en -bewerking
contentOwner: AG
mini-toc-levels: 3
feature: Asset Management, Publishing,Collaboration, Asset Processing
role: User, Architect, Admin
exl-id: 51a26764-ac2b-4225-8d27-42a7fd906183
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '4129'
ht-degree: 8%

---

# Elementen beheren {#manage-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

In dit artikel wordt beschreven hoe u elementen beheert en bewerkt in [!DNL Adobe Experience Manager Assets]. Om te beheren [!DNL Content Fragments], zie [[!DNL Content Fragments]](content-fragments/content-fragments.md) activa.

## Mappen maken {#creating-folders}

Bij het organiseren van een verzameling elementen, bijvoorbeeld alle `Nature` afbeeldingen kunt u mappen maken om ze bij elkaar te houden. U kunt mappen gebruiken om uw elementen te categoriseren en in te delen. [!DNL Experience Manager Assets] vereist niet dat u elementen in mappen ordent om beter te werken.

>[!NOTE]
>
>* Een map Middelen van het type `sling:OrderedFolder`, wordt niet ondersteund bij delen naar Experience Cloud. Selecteer [!UICONTROL Ordered] wanneer u een map maakt.
>* Experience Manager staat het gebruik niet toe `subassets` woord als de naam van een map. Het is een trefwoord dat is gereserveerd voor knooppunten die subassets voor samengestelde elementen bevatten

1. Navigeer naar de plaats in de map met digitale elementen waar u een map wilt maken. Klik op **[!UICONTROL Create]**. Selecteren **[!UICONTROL New Folder]**.
1. In de **[!UICONTROL Title]** veld, geef een mapnaam op. Standaard gebruikt DAM de titel die u als mapnaam hebt opgegeven. Nadat de map is gemaakt, kunt u de standaardinstelling overschrijven en een andere mapnaam opgeven.
1. Klik op **[!UICONTROL Create]**. De map wordt weergegeven in de map met digitale middelen.

De volgende tekens (lijst met door spaties gescheiden tekens) worden niet ondersteund:

* De naam van een elementbestand mag geen van de volgende tekens bevatten: `* / : [ \\ ] | # % { } ? &`
* De naam van een elementmap mag geen van de volgende tekens bevatten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Elementen uploaden {#uploading-assets}

Zie [digitale elementen toevoegen aan Experience Manager](add-assets.md).

## ZIP-archieven extraheren {#extract-zip-archives}

Selecteer ZIP-archieven die in Experience Manager worden beheerd en extraheer de bestanden rechtstreeks naar de Experience Manager zonder ze te downloaden.

Voer de volgende stappen uit om de ZIP-bestanden te extraheren:

1. Selecteer het bestandstype ZIP.
1. Klik op de knop **[!UICONTROL Extract Archive]** beschikbaar op de actiebalk.
1. Selecteer de map waarin u de geëxtraheerde elementen wilt opslaan die beschikbaar zijn in de gecomprimeerde map.
1. Klik op **[!UICONTROL Next]**.
1. Selecteer het juiste gedrag om conflicten met bestandsnamen tijdens het uitpakken te verwerken. U kunt selecteren om een versie van een bestaand element te maken, het element te vervangen, beide elementen in de doelmap te houden of de extractie van het nieuwe element over te slaan.
1. Klik op **[!UICONTROL Extract]**. Het Zip-extractieproces wordt gestart. Nadat het proces is voltooid, kunt u de geëxtraheerde elementen weergeven in de doelmap.

   ![ZIP-extractie](assets/zip-extraction.png)

>[!NOTE]
>
>* De maximale ondersteunde ZIP-bestandsgrootte is 15 GB.
>* U kunt maximaal drie ZIP-bestanden tegelijk extraheren.

## Elementen voorvertonen {#previewing-assets}

Voer de volgende stappen uit om een voorvertoning van een element weer te geven.

1. Navigeer in de gebruikersinterface Elementen naar de locatie van het element waarvan u een voorvertoning wilt weergeven.
1. Selecteer het gewenste element om het te openen.

1. In de voorvertoningsmodus zijn zoomopties beschikbaar voor [ondersteunde afbeeldingstypen](/help/assets/file-format-support.md) (met interactieve bewerkingen).

   Als u wilt inzoomen op een element, selecteert u `+` (of selecteer het vergrootglas op het element). Als u wilt uitzoomen, selecteert u `-`. Wanneer u inzoomt, kunt u elk gebied van de afbeelding nauwkeurig bekijken door te pannen. Met de zoompijl opnieuw instellen keert u terug naar de oorspronkelijke weergave.

   Selecteren **[!UICONTROL Reset]** om de weergave weer in te stellen op de oorspronkelijke grootte.

## Eigenschappen bewerken {#editing-properties}

1. Navigeer naar de locatie van het element waarvan u de metagegevens wilt bewerken.

1. Selecteer het element en selecteer **[!UICONTROL Properties]** op de werkbalk om de eigenschappen van elementen weer te geven. U kunt ook de optie **[!UICONTROL Properties]** snelle actie op de asset card.

   ![properties_quickaction](assets/properties_quickaction.png)

1. In de [!UICONTROL Properties] pagina, bewerkt u de eigenschappen van de metagegevens onder verschillende tabbladen. Bijvoorbeeld onder de **[!UICONTROL Basic]** , bewerkt u de titel, beschrijving, enzovoort.

   >[!NOTE]
   >
   >De indeling van de [!UICONTROL Properties] De beschikbare pagina- en metagegevenseigenschappen zijn afhankelijk van het onderliggende metagegevensschema. Leren hoe u de lay-out van de [!UICONTROL Properties] pagina, zie [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md).

1. Gebruik de datumkiezer naast het veld **[!UICONTROL On Time]** om een bepaalde datum/tijd voor de activering van de asset te plannen.

   ![Datumkiezer](assets/date-picker.png)

1. Als u het element na een bepaalde duur wilt deactiveren, kiest u de datum/tijd van deactivering in de datumkiezer naast de **[!UICONTROL Off Time]** veld. De deactiveringsdatum moet later zijn dan de activeringsdatum voor een element. Na de [!UICONTROL Off Time], een middel en de vertoningen ervan zijn niet beschikbaar via de interface Middelen of de HTTP-API.

   <!--![chlimage_1-218](assets/chlimage_1-218.png)
1. In de **[!UICONTROL Tags]** veld, selecteert u een of meer tags. Als u een aangepaste tag wilt toevoegen, typt u de naam van de tag in het vak en selecteert u de optie `Enter` toets. De nieuwe tag wordt opgeslagen in [!DNL Experience Manager].

   YouTube vereist dat tags worden gepubliceerd en een koppeling naar YouTube hebben (als er een geschikte koppeling is gevonden).

   >[!NOTE]
   >
   > Als u tags wilt maken, moet u schrijfmachtigingen hebben op `/content/cq:tags/default` pad in de CRX-opslagplaats.

1. Selecteren **[!UICONTROL Save & Close]**.

1. Navigeer naar de gebruikersinterface Elementen. De bewerkte eigenschappen van metagegevens, zoals titel, beschrijving en tags, worden weergegeven op de elementenkaart in de Kaart-weergave en onder de desbetreffende kolommen in de lijstweergave.

<!-- TBD: Uncomment after verification for Dec release.

## View asset usage and references {#usage-and-references}

[!DNL Experience Manager] lets you track statistics about usage of a digital asset. The usage statistics include the following:

    * Number of times the asset was viewed or downloaded
    * Channels/devices through which the asset was used
    * Creative solutions where the asset was recently used

To view usage statistics for an asset, in the [!UICONTROL Properties] page, click the **[!UICONTROL Insights]** tab. For more details, see [Assets Insights](assets-insights.md).

[!DNL Experience Manager] also lets you check all the incoming references to an asset, that is, the usage of an asset in remote [!DNL Sites] and in compound assets. Authors of webpages on [!DNL Experience Manager Sites] deployment can use an asset on a remote [!DNL Assets] deployment using the Connected Assets functionality. The [!UICONTROL References] tab in an asset's [!UICONTROL Properties] page lists the local and remote references of the asset. That is, the use of assets in compound assets in [!DNL Assets] and its use in remote [!DNL Sites] pages.

-->

## Elementen kopiëren {#copying-assets}

Wanneer u een middel of een omslag kopieert, wordt het volledige middel of de omslag gekopieerd, samen met zijn inhoudsstructuur. Een gekopieerd middel of een omslag wordt gedupliceerd bij de doelplaats. Het element op de bronlocatie wordt niet gewijzigd.

Enkele kenmerken die uniek zijn voor een bepaalde kopie van een element, worden niet overgedragen. Enkele voorbeelden zijn:

* Element-id, aanmaakdatum en -tijd en versies en versiehistorie. Sommige eigenschappen worden aangegeven door de eigenschappen `jcr:uuid`, `jcr:created`, en `cq:name`.

* De aanmaaktijd en de paden waarnaar wordt verwezen, zijn uniek voor elk element en elke uitvoering ervan.

De andere eigenschappen en metagegevens blijven behouden. Er wordt geen gedeeltelijke kopie gemaakt wanneer een element wordt gekopieerd.

1. Selecteer in de interface Elementen een of meer elementen en selecteer vervolgens de **[!UICONTROL Copy]** op de werkbalk. U kunt ook de **[!UICONTROL Copy]** ![copy_icon](assets/copy_icon.png) snelle actie van de assetkaart.

   >[!NOTE]
   >
   >Als u het [!UICONTROL Copy] snel kunt u slechts één element tegelijk kopiëren.

1. Navigeer naar de locatie waar u de elementen wilt kopiëren.

   >[!NOTE]
   >
   >Als u een element op dezelfde locatie kopieert, [!DNL Experience Manager] genereert automatisch een variatie in de naam. Als u bijvoorbeeld een element met de naam `Square`, [!DNL Experience Manager] genereert automatisch de titel voor de kopie als `Square1`.

1. Klik op de knop **[!UICONTROL Paste]** middelenpictogram van de werkbalk. Elementen worden naar deze locatie gekopieerd.

   <!--![chlimage_1-219](assets/chlimage_1-219.png)-->

   >[!NOTE]
   >
   >De **[!UICONTROL Paste]** is beschikbaar op de werkbalk totdat de plakbewerking is voltooid.

### Elementen verplaatsen of hernoemen {#moving-or-renaming-assets}

1. Navigeer naar de locatie van het element dat u wilt verplaatsen.

1. Selecteer het element en selecteer het **[!UICONTROL Move]** pictogram ![move_icon](assets/move_icon.png) op de werkbalk.

1. Voer een van de volgende handelingen uit in de wizard Elementen verplaatsen:

   * Geef de naam voor het element op nadat het is verplaatst. Selecteer vervolgens **[!UICONTROL Next]** om verder te gaan.

   * Selecteren **[!UICONTROL Cancel]** om het proces te stoppen.

   >[!NOTE]
   >
   >* U kunt dezelfde naam opgeven voor het element als er geen element met die naam is op de nieuwe locatie. U moet echter een andere naam gebruiken als u het element verplaatst naar een locatie waar zich een element met dezelfde naam bevindt. Als u dezelfde naam gebruikt, genereert het systeem automatisch een variatie in de naam. Als uw element bijvoorbeeld de naam Vierkant heeft, genereert het systeem de naam Vierkant1 voor de kopie.
   >* Bij het wijzigen van de naam is witruimte niet toegestaan in de bestandsnaam.

1. Op de **[!UICONTROL Select Destination]** voert u een van de volgende handelingen uit:

   * Ga naar de nieuwe locatie voor de elementen en selecteer **[!UICONTROL Next]** om verder te gaan.

   * Selecteren **[!UICONTROL Back]** om terug te keren naar de **[!UICONTROL Rename]** scherm.

1. Als de elementen die worden verplaatst, verwijzen naar pagina&#39;s, elementen of verzamelingen, wordt het **[!UICONTROL Adjust References]** wordt weergegeven naast de **[!UICONTROL Select Destination]** tab.

   Voer een van de volgende handelingen uit in de **[!UICONTROL Adjust References]** scherm:

   * Geef de referenties op die u wilt aanpassen op basis van de nieuwe details en selecteer **[!UICONTROL Move]** om verder te gaan.

   * Van de **[!UICONTROL Adjust]** -kolom, verwijzingen naar de elementen selecteren of de selectie ervan opheffen.
   * Selecteren **[!UICONTROL Back]** om terug te keren naar de **[!UICONTROL Select Destination]** scherm.

   * Selecteren **[!UICONTROL Cancel]** om de verplaatsingsbewerking te stoppen.

   Als u verwijzingen niet bijwerkt, blijven ze naar het vorige pad van het element wijzen. Als u de referenties aanpast, worden deze bijgewerkt naar het nieuwe middelenpad.

### Uitvoeringen beheren {#managing-renditions}

1. U kunt uitvoeringen voor een element toevoegen of verwijderen, behalve voor het origineel. Navigeer naar de locatie van het element waaraan u uitvoeringen wilt toevoegen of verwijderen.

1. Selecteer het element om de elementpagina te openen.

   <!--![chlimage_1-220](assets/chlimage_1-220.png)-->

1. Selecteer het GlobalNav-pictogram en selecteer **[!UICONTROL Renditions]** in de lijst.

   ![renditions_menu](assets/renditions_menu.png)

1. In de **[!UICONTROL Renditions]** weergegeven.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Standaard, [!DNL Experience Manager Assets] geeft de oorspronkelijke vertoning van het element niet weer in de voorvertoningsmodus. Als u een beheerder bent, kunt u overlays gebruiken om te vormen [!DNL Assets] om de originele uitvoeringen weer te geven in de voorvertoningsmodus.

1. Selecteer een vertoning om de vertoning weer te geven of te verwijderen.

   **Een vertoning verwijderen**

   Selecteer een vertoning in het menu **[!UICONTROL Renditions]** en selecteert u vervolgens de **[!UICONTROL Delete Rendition]** op de werkbalk. Uitvoeringen kunnen niet bulksgewijs worden verwijderd nadat de verwerking van het element is voltooid. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u [!DNL Experience Manager] om specifieke vertoningen te verwijderen of de elementen te verwijderen en de verwijderde elementen opnieuw te uploaden.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **Een nieuwe uitvoering uploaden**

   Navigeer naar de pagina met elementdetails voor het element en selecteer de optie **[!UICONTROL Add Rendition]** op de werkbalk om een nieuwe uitvoering voor het element te uploaden.

   <!--![chlimage_1-221](assets/chlimage_1-221.png)-->

   >[!NOTE]
   >
   >Als u een uitvoering selecteert in het deelvenster **[!UICONTROL Renditions]**, verandert de context van de werkbalk en worden alleen die acties weergegeven die relevant zijn voor de uitvoering. Opties zoals het pictogram Uitvoering uploaden worden niet weergegeven. Ga naar de pagina met details voor de asset om deze opties in de werkbalk weer te geven.

   U kunt de afmetingen configureren voor de vertoning die u wilt weergeven op de detailpagina van een afbeelding of video-element. Op basis van de afmetingen die u opgeeft, wordt de vertoning in Elementen weergegeven met de exacte of dichtstbijzijnde afmetingen.

   U kunt geen uitvoeringen maken met de volgende voorvoegsels, omdat deze intern zijn voor Adobe:

   * cq5

   * cqdam

   * cq5dam

   Als u weergaveafmetingen van een afbeelding op het niveau van de assetdetails wilt configureren, overlapt u het knooppunt `renditionpicker` (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) en configureert u de waarde van de breedte-eigenschap. Configureer de eigenschap **[!UICONTROL size (Long) in KB]** in plaats van de breedte om de weergave op de pagina met assetdetails aan te passen op basis van de afbeeldingsgrootte. Voor aanpassing op basis van grootte wijst de eigenschap `preferOriginal` de voorkeur toe aan het origineel als de grootte van de overeenkomstige weergave groter is dan het origineel.

   Op dezelfde manier kunt u de afbeelding van de pagina Annotatie aanpassen door deze te bedekken `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   <!--![chlimage_1-222](assets/chlimage_1-222.png)-->

   Navigeer naar het deelvenster `videopicker` knooppunt in de CRX-opslagplaats op de locatie `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, bedekt het knooppunt en bewerkt vervolgens de desbetreffende eigenschap.

   >[!NOTE]
   >
   >Videoannotaties worden alleen ondersteund in browsers met video-indelingen die compatibel zijn met HTML5. Afhankelijk van de browser worden bovendien verschillende video-indelingen ondersteund. De MXF-video-indeling wordt echter nog niet ondersteund met video-annotaties.

## Elementen verwijderen {#delete-assets}

Als u de inkomende verwijzingen van andere pagina&#39;s wilt oplossen of verwijderen, werkt u de relevante verwijzingen bij voordat u een element verwijdert.

Schakel ook de knop forceren verwijderen uit met behulp van een overlay, zodat gebruikers geen bestanden waarnaar wordt verwezen kunnen verwijderen en verbroken koppelingen behouden blijven.

1. Navigeer naar de locatie van de elementen die u wilt verwijderen.

1. Selecteer het element en klik op **[!UICONTROL Delete]** ![delete_icon](assets/do-not-localize/delete-icon.png) op de werkbalk.

1. Klik in het bevestigingsdialoogvenster op:

   * **[!UICONTROL Cancel]** om de handeling te stoppen
   * **[!UICONTROL Delete]** ter bevestiging van de actie :

      * Als het element geen verwijzingen bevat, wordt het element verwijderd.
      * Als het element verwijzingen bevat, wordt u via een foutbericht geïnformeerd dat **[!UICONTROL One or more assets are referenced]**. U kunt **[!UICONTROL Force Delete]** of **[!UICONTROL Cancel]**.

   >[!NOTE]
   >
   >U hebt verwijdermachtigingen voor dam/asset nodig om een element te kunnen verwijderen. Als u alleen over wijzigingsmachtigingen beschikt, kunt u alleen de metagegevens van de elementen bewerken en annotaties toevoegen aan het element. U kunt het element of de metagegevens echter niet verwijderen.

   >[!NOTE]
   >
   >Als u de inkomende verwijzingen van andere pagina&#39;s wilt oplossen of verwijderen, werkt u de relevante verwijzingen bij voordat u een element verwijdert. U kunt het verwijderen van middelen waarnaar wordt verwezen, uitschakelen omdat verbroken koppelingen hierdoor worden veroorzaakt. Schakel de knop Kracht verwijderen uit met behulp van een bedekking.

## Elementen downloaden {#download-assets}

Zie [middelen downloaden van [!DNL Experience Manager]](/help/assets/download-assets-from-aem.md).

## Elementen publiceren of publiceren ongedaan maken {#publish-assets}

1. Navigeer naar de locatie van het element of de map met middelen die u wilt publiceren of die u uit de publicatieomgeving wilt verwijderen (publicatie ongedaan maken).

1. Selecteer het element of de map die u wilt publiceren of de publicatie ongedaan wilt maken en selecteer **[!UICONTROL Manage Publication]** ![publicatieoptie beheren](assets/do-not-localize/globe-publication.png) van de werkbalk. Als u snel wilt publiceren, selecteert u **[!UICONTROL Quick Publish]** van de werkbalk. Als de map die u wilt publiceren een lege map bevat, wordt de lege map niet gepubliceerd.

1. Selecteer de **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** naar wens.

   ![Handeling Unpublish](assets/unpublish_action.png)
   *Afbeelding: Publiceer- en publicatieopties en de planningsoptie.*

1. Selecteren **[!UICONTROL Now]** om direct op het middel te handelen of selecteer **[!UICONTROL Later]** om de actie te plannen. Selecteer een datum en tijd als u de optie **[!UICONTROL Later]** -optie. Klik op **[!UICONTROL Next]**.

1. Als een element bij het publiceren naar andere elementen verwijst, worden de bijbehorende verwijzingen in de wizard weergegeven. Alleen die verwijzingen worden weergegeven die niet zijn gepubliceerd of zijn gewijzigd sinds de laatste publicatie. Kies de referenties die u wilt publiceren.

1. Wanneer u de publicatie ongedaan maakt, kiest u de referenties die u ongedaan wilt maken wanneer een element naar andere elementen verwijst. Klik op **[!UICONTROL Unpublish]**. Klik in het bevestigingsdialoogvenster op **[!UICONTROL Cancel]** om de handeling te stoppen of klik op **[!UICONTROL Unpublish]** om te bevestigen dat de activa op de vastgestelde datum niet gepubliceerd zullen worden.

De volgende beperkingen en tips voor het publiceren of verwijderen van middelen of mappen zijn beschikbaar:

* De optie om [!UICONTROL Manage Publication] is beschikbaar slechts aan de gebruikersrekeningen die replicatiemachtigingen hebben.
* Verwijder tijdens het verwijderen van de publicatie van een complex element alleen de publicatie van het element. Verwijder de publicatie van de verwijzingen niet omdat er mogelijk naar wordt verwezen door andere gepubliceerde elementen.
* Lege mappen worden niet gepubliceerd.
* Als u elementen publiceert die worden verwerkt, wordt alleen de oorspronkelijke inhoud gepubliceerd. De uitvoeringen ontbreken. Wacht tot de verwerking is voltooid en publiceer het element of publiceer het opnieuw nadat de verwerking is voltooid.

## Gesloten gebruikersgroep {#closed-user-group}

Er wordt een gesloten gebruikersgroep (CUG) gebruikt om de toegang te beperken tot specifieke mappen met elementen die zijn gepubliceerd vanuit [!DNL Experience Manager]. Als u een CUG maakt voor een map, is de toegang tot de map (inclusief mapelementen en submappen) beperkt tot alleen toegewezen leden of groepen. Om tot de omslag toegang te hebben, moeten zij login gebruikend hun veiligheidsgeloofsbrieven.

CUG&#39;s zijn een extra manier om de toegang tot uw elementen te beperken. U kunt ook een aanmeldingspagina voor de map configureren.

1. Selecteer een map in de interface Middelen en selecteer het pictogram Eigenschappen op de werkbalk om de pagina met eigenschappen weer te geven.
1. Van de **[!UICONTROL Permissions]** tabblad, leden of groepen toevoegen onder **[!UICONTROL Closed User Group]**.

   ![add_user](assets/add_user.png)

1. Als u een aanmeldingsscherm wilt weergeven wanneer gebruikers de map openen, selecteert u de optie **[!UICONTROL Enable]** -optie. Selecteer vervolgens het pad naar een aanmeldingspagina in [!DNL Experience Manager]en sla de wijzigingen op.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >Als u het pad naar een aanmeldingspagina niet opgeeft, [!DNL Experience Manager] Hiermee geeft u de standaardaanmeldingspagina weer in de publicatie-instantie.

1. Publiceer de map en probeer deze vervolgens te openen vanuit de publicatie-instantie. Er wordt een aanmeldingsscherm weergegeven.
1. Als u lid van de GECG bent, ga uw veiligheidsgeloofsbrieven in. De map wordt weergegeven na [!DNL Experience Manager] verklaart u voor authentiek.

## Zoeken in middelen {#search-assets}

Het zoeken naar middelen is van cruciaal belang voor het gebruik van een systeem voor het beheer van digitale activa — of het nu gaat om verder gebruik door creatieve ondernemingen, voor een robuust beheer van activa door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders.

Voor eenvoudige, geavanceerde, en douaneonderzoeken om de meest aangewezen activa te ontdekken en te gebruiken, zie [zoekelementen in [!DNL Experience Manager]](/help/assets/search-assets.md).

## Snelle acties {#quick-actions}

De snelle actiepictogrammen zijn beschikbaar voor één middel tegelijkertijd. Voer afhankelijk van het apparaat de volgende handelingen uit om de snelactiepictogrammen weer te geven:

* Aanraakapparaten: aanraken en vasthouden. Op een iPad kunt u bijvoorbeeld een element selecteren en ingedrukt houden, zodat de snelle acties worden weergegeven.
* Niet-aanraakapparaten: Aanwijzer aanwijzen. Op een bureaubladapparaat wordt bijvoorbeeld de snelle actiebalk weergegeven als u de aanwijzer boven de elementminiatuur houdt.

<!-- Hiding this topic via cqdoc-18707

## Edit images {#editing-images}

The editing tools in the [!DNL Experience Manager Assets] interface let you perform small editing jobs on image assets. You can crop, rotate, flip, and perform other editing jobs on images. You can also add image maps to assets.

>[!NOTE]
>
>For some components, the Full Screen mode has additional options available.

1. Do one of the following to open an asset in edit mode:

    * Select the asset and then select the **[!UICONTROL Edit]** icon in the toolbar.
    * Select the **[!UICONTROL Edit]** icon that appears on an asset in the Card view.
    * In the asset page, select the **[!UICONTROL Edit]** icon in the toolbar.

   ![edit_icon](assets/edit_icon.png)

1. To crop the image, select the **Crop** icon.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. Select the desired option from the list. The crop area appears on the image based on the option you choose. The **Free Hand** option lets you crop the image without any aspect ratio restrictions.

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Select the area to be cropped, and resize or reposition it on the image.
1. Use the **Finish** icon (top right corner) to crop the image. Clicking the **Finish** icon also triggers the regeneration of renditions.

   ![chlimage_1-228](assets/chlimage_1-228.png)

1. Use the **Undo** and **Redo** icons on the top right to revert to the uncropped image or retain the cropped image, respectively.

   ![chlimage_1-229](assets/chlimage_1-229.png)

1. Select the appropriate Rotate icon to rotate the image clockwise or anti-clockwise.

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Select the appropriate Flip icon to flip the image horizontally or vertically.

   ![chlimage_1-231](assets/chlimage_1-231.png)

1. Select the **Finish** icon to save the changes.

   ![chlimage_1-232](assets/chlimage_1-232.png)

>[!NOTE]
>
>Image editing is supported for BMP, GIF, PNG, and JPEG files formats.

>[!NOTE]
>
>To edit a TXT file, set **Day CQ Link Externalizer** from Configuration Manager.
-->

## Tijdlijn {#timeline}

In de tijdlijn kunt u verschillende gebeurtenissen voor een geselecteerd item weergeven, zoals actieve workflows voor een element, opmerkingen/annotaties, activiteitenlogbestanden en versies.

![Tijdlijnitems voor een element sorteren](assets/sort_timeline.gif)
*Afbeelding: Tijdlijnitems voor een element sorteren*

>[!NOTE]
>
>In de [Collectieconsole](/help/assets/manage-collections.md#navigate-the-collections-console)de **[!UICONTROL Show All]** biedt alleen opties voor het weergeven van opmerkingen en workflows. Bovendien wordt de chronologie getoond slechts voor top-level inzamelingen die in de console vermeld zijn. Deze wordt niet weergegeven als u in een van de verzamelingen navigeert.

>[!NOTE]
>
>De tijdlijn bevat verschillende [specifieke opties voor inhoudsfragmenten](content-fragments/content-fragments.md).

## Elementen notities aanbrengen {#annotating}

Annotaties zijn opmerkingen of toelichtingen die aan afbeeldingen of video&#39;s worden toegevoegd. Annotaties bieden marketers de mogelijkheid samen te werken en feedback over middelen te geven.

Videoannotaties worden alleen ondersteund in browsers met video-indelingen die compatibel zijn met HTML5. De video-indelingen die door Middelen worden ondersteund, zijn afhankelijk van de browser. De MXF-video-indeling wordt echter nog niet ondersteund met video-annotaties.

>[!NOTE]
>
>Voor inhoudsfragmenten, [annotaties worden gemaakt in de fragmenteditor](content-fragments/content-fragments.md).

1. Navigeer naar de locatie van het element waaraan u annotaties wilt toevoegen.
1. Selecteer de **[!UICONTROL Annotate]** pictogram uit een van de volgende opties:

   * [Snelle acties](#quick-actions)
   * Vanuit de werkbalk nadat u het element hebt geselecteerd of naar de elementpagina bent gegaan

   <!--![chlimage_1-233](assets/chlimage_1-233.png)-->

1. Voeg een opmerking toe in het vak **[!UICONTROL Comment]** onder aan de tijdlijn. U kunt ook een gebied in de afbeelding markeren en een annotatie toevoegen in het dialoogvenster **[!UICONTROL Add Annotation]**.

<!-- ![chlimage_1-234](assets/chlimage_1-234.png)-->

<!--
1. To notify a user about an annotation, specify the email address of the user and add the comment. For example, to notify Aaron MacDonald about an annotation, enter @aa. Hints for all matching users is displayed in a list. Select Aaron's email address from the list to tag her with the comment. Similarly, you can tag more users anywhere within the annotation or before or after it.
-->

>[!NOTE]
>
>Voor een gebruiker die geen beheerder is, worden suggesties alleen weergegeven als de gebruiker Leesmachtigingen heeft op `/home` in CRXDE.

<!--![chlimage_1-235](assets/chlimage_1-235.png)-->

1. Nadat u de annotatie hebt toegevoegd, klikt u op **[!UICONTROL Add]** opslaan. Een kennisgeving voor de aantekening wordt verzonden naar Aaron.

   <!--![chlimage_1-236](assets/chlimage_1-236.png)-->

   >[!NOTE]
   >
   >U kunt meerdere annotaties toevoegen voordat u ze opslaat.

1. Selecteren **[!UICONTROL Close]** om de Annotatiemodus te verlaten.
1. Meld u aan bij Middelen met de gegevens van Aaron MacDonald en klik op de knop **[!UICONTROL Notifications]** pictogram om het bericht weer te geven.

   >[!NOTE]
   >
   >U kunt ook annotaties toevoegen aan video-elementen. Tijdens het annoteren van video&#39;s pauzeert de speler zodat u notities kunt aanbrengen in een frame. Zie voor meer informatie [beheren, video-elementen](manage-video-assets.md). De MXF-video-indeling wordt echter nog niet ondersteund met video-annotaties.

1. Als u een andere kleur wilt kiezen, zodat u onderscheid kunt maken tussen gebruikers, selecteert u het pictogram Profiel en selecteert u **[!UICONTROL My Preferences]**.

   <!--![chlimage_1-237](assets/chlimage_1-237.png)-->

   Geef de gewenste kleur op in het dialoogvenster **[!UICONTROL Annotation Color]** en selecteer vervolgens **[!UICONTROL Accept]**.

<!-- ![chlimage_1-238](assets/chlimage_1-238.png)-->

>[!NOTE]
>
>U kunt ook annotaties toevoegen aan een verzameling. Als een verzameling onderliggende verzamelingen bevat, kunt u echter alleen annotaties/opmerkingen aan de bovenliggende verzameling toevoegen. De optie Annoteren is niet beschikbaar voor onderliggende verzamelingen.

### Opgeslagen annotaties weergeven {#viewing-saved-annotations}

U kunt slechts één annotatie tegelijk weergeven.

>[!NOTE]
>
>Als u meerdere annotaties selecteert, wordt de laatste annotatie weergegeven in de gebruikersinterface.
>
>Multi-select wordt alleen ondersteund voor het afdrukken van het geannoteerde element als PDF.

1. Als u opgeslagen annotaties voor een element wilt weergeven, navigeert u naar de locatie van het element en opent u de elementpagina voor het element.

1. Selecteer het GlobalNav-pictogram en kies **[!UICONTROL Timeline]** in de lijst.

   <!--![chlimage_1-239](assets/chlimage_1-239.png)-->

1. Selecteer in de lijst **[!UICONTROL Show All]** in de tijdlijn de optie **[!UICONTROL Comments]** om de resultaten te filteren op basis van annotaties.

   <!--![chlimage_1-240](assets/chlimage_1-240.png)-->

   Selecteer een opmerking in het dialoogvenster **[!UICONTROL Timeline]** om de bijbehorende annotatie in de afbeelding weer te geven.

   <!--![chlimage_1-241](assets/chlimage_1-241.png)-->

   Selecteren **[!UICONTROL Delete]** om een bepaalde opmerking te verwijderen.

### Annotaties afdrukken {#printing-annotations}

Als een element annotaties heeft of een revisiewerkstroom heeft ondergaan, kunt u het element samen met annotaties afdrukken en de status controleren als een PDF-bestand voor offline revisie.

U kunt ook alleen de annotaties of de revisiestatus afdrukken.

>[!NOTE]
>
>U kunt meerdere annotaties selecteren wanneer u het geannoteerde element afdrukt als PDF.

Als u de annotaties en de revisiestatus wilt afdrukken, selecteert u de optie **[!UICONTROL Print]** en volgt u de instructies in de wizard. De **[!UICONTROL Print]** wordt alleen op de werkbalk weergegeven als aan het element ten minste één aantekening of revisiestatus is toegewezen.

1. Open vanuit de interface Middelen de voorvertoningspagina voor een element.
1. Voer een van de volgende handelingen uit:

   * Als u alle annotaties en de revisiestatus wilt afdrukken, slaat u stap 3 over en gaat u rechtstreeks naar stap 4.
   * Als u specifieke annotaties en de revisiestatus wilt afdrukken, opent u het dialoogvenster [tijdlijn](/help/assets/manage-digital-assets.md#timeline) en ga vervolgens naar stap 3.

1. Als u specifieke annotaties wilt afdrukken, selecteert u de annotaties in de tijdlijn.

   <!--![chlimage_1-242](assets/chlimage_1-242.png)-->

   Als u alleen de revisiestatus wilt afdrukken, selecteert u deze in de tijdlijn.

   <!--![chlimage_1-243](assets/chlimage_1-243.png)-->

1. Selecteer de **[!UICONTROL Print]** op de werkbalk.

   <!--![chlimage_1-244](assets/chlimage_1-244.png)-->

1. Kies in het dialoogvenster Afdrukken de positie waarop u de annotaties/revisiestatus wilt weergeven op de PDF. Als u bijvoorbeeld wilt dat de annotaties/status rechtsboven op de pagina met de afgedrukte afbeelding worden afgedrukt, gebruikt u de optie **Linksboven** instellen. Deze optie is standaard geselecteerd.

   <!--![chlimage_1-245](assets/chlimage_1-245.png)-->

   U kunt andere instellingen kiezen, afhankelijk van de positie waar u de annotaties/status wilt weergeven in de afgedrukte PDF. Kies **[!UICONTROL Next Page]** als u de annotaties/status wilt weergeven op een pagina die gescheiden is van de afgedrukte asset.

1. Klik op **[!UICONTROL Print]**. Afhankelijk van de optie die u kiest in stap 2, geeft de gegenereerde PDF de annotaties/status op de opgegeven positie weer. Als u bijvoorbeeld zowel annotaties als de revisiestatus wilt afdrukken met de instelling **Linksboven**, lijkt de gegenereerde uitvoer op het PDF-bestand dat hier wordt weergegeven.

   <!--![chlimage_1-246](assets/chlimage_1-246.png)-->

1. Download of druk de PDF af met de opties rechtsboven.

   <!--![chlimage_1-247](assets/chlimage_1-247.png)-->

   Als u de vormgeving van het gerenderde PDF-bestand wilt wijzigen, bijvoorbeeld de lettertypekleur, -grootte en -stijl, de achtergrondkleur van de opmerkingen en status, opent u het dialoogvenster **[!UICONTROL Annotation PDF configuration]** van de Manager van de Configuratie, en wijzig de gewenste opties. Als u bijvoorbeeld de weergavekleur van de goedgekeurde status wilt wijzigen, wijzigt u de kleurcode in het desbetreffende veld. Zie voor informatie over het wijzigen van de fontkleur van annotaties [Annotatie](/help/assets/manage-digital-assets.md#annotating).

   Ga terug naar het gerenderde PDF-bestand en vernieuw het. De vernieuwde PDF geeft de wijzigingen weer die u hebt aangebracht.

## Asset versioning {#asset-versioning}

Met Versioning maakt u een momentopname van digitale elementen op een bepaald tijdstip. Versioning helpt bij het terugzetten van elementen naar een vorige status op een later tijdstip. Als u bijvoorbeeld een wijziging in een element ongedaan wilt maken, herstelt u de onbewerkte versie van het element.

Hieronder vindt u scenario&#39;s waarin u versies maakt:

* U wijzigt een afbeelding in een andere toepassing en uploadt deze naar Elementen. Er wordt een versie van de afbeelding gemaakt, zodat de oorspronkelijke afbeelding niet wordt overschreven.
* U bewerkt de metagegevens van een element.
* U gebruikt [!DNL Experience Manager] bureaubladtoepassing om een bestaand middel uit te checken en uw wijzigingen op te slaan. Telkens wanneer het element wordt opgeslagen, wordt een nieuwe versie gemaakt.

U kunt automatische versioning ook inschakelen via een workflow. Wanneer u een versie voor een element maakt, worden de metagegevens en de uitvoeringen samen met de versie opgeslagen. Uitvoeringen zijn alternatieven voor dezelfde afbeeldingen, bijvoorbeeld een PNG-uitvoering van een geüpload JPEG-bestand.

Met de versiefunctionaliteit kunt u het volgende doen:

* Maak een versie van een element.
* De huidige revisie voor een element weergeven.
* Herstel het element naar een vorige versie.

1. Navigeer naar de locatie van het element waarvoor u een versie wilt maken en selecteer het element om de elementpagina te openen.

1. Selecteer het GlobalNav-pictogram en kies **[!UICONTROL Timeline]** in het menu.

   ![tijdlijn](assets/timeline.png)

1. Selecteer de **[!UICONTROL Actions]** (pijl) onder aan om de beschikbare acties weer te geven die u op het element kunt uitvoeren.

   <!--![chlimage_1-249](assets/chlimage_1-249.png)-->

1. Selecteren **[!UICONTROL Save as Version]** om een versie voor het element te maken.

<!--![chlimage_1-250](assets/chlimage_1-250.png)-->

1. Voeg een label en een opmerking toe en klik vervolgens op **[!UICONTROL Create]** om een versie te maken. U kunt ook **Annuleren** om de bewerking af te sluiten.

   <!--![chlimage_1-251](assets/chlimage_1-251.png)-->

1. Als u de nieuwe versie wilt weergeven, opent u de lijst **[!UICONTROL Show All]** in de tijdlijn op de pagina met assetdetails of op de gebruikersinterface Assets en kiest u **[!UICONTROL Versions]**. Alle versies die voor een asset zijn gemaakt, worden weergegeven onder het tabblad Tijdlijn. U kunt de lijst filteren om Versies weer te geven door op de pijl-omlaag te klikken en **[!UICONTROL Versions]** in de lijst te selecteren.

   ![version_option](assets/versions_option.png)

1. Selecteer een specifieke versie voor het element om er een voorvertoning van weer te geven of schakel de optie in voor weergave in de interface Middelen.

   ![select_version](assets/select_version.png)

1. Voeg een label en een opmerking voor de versie toe om terug te keren naar de specifieke versie in de interface Middelen.

   ![save_version](assets/save_version.png)

1. Als u een voorvertoning voor de versie wilt genereren, selecteert u **[!UICONTROL Preview Version]**.
1. Selecteer **[!UICONTROL Revert to this Version]**.
1. Als u twee versies wilt vergelijken, gaat u naar de elementenpagina van het element en selecteert u de versie die u met de huidige versie wilt vergelijken.

   ![select_version_to_compare](assets/select_version_tocompare.png)

1. Selecteer in de tijdlijn de versie die u wilt vergelijken en sleep de schuifregelaar naar links om deze versie over de huidige versie heen te plaatsen en te vergelijken.

   ![compare_versions](assets/compare_versions.png)

### Een workflow op een element starten {#starting-a-workflow-on-an-asset}

1. Navigeer naar de locatie van het element waarvoor u een workflow wilt starten en selecteer het element om de elementpagina te openen.
1. Selecteer het GlobalNav-pictogram en kies **[!UICONTROL Timeline]** in het menu om de tijdlijn weer te geven.

   ![timeline-1](assets/timeline-1.png)

1. Selecteer de **[!UICONTROL Actions]** (pijl) onderaan om de lijst met acties te openen die beschikbaar zijn voor het element.

   <!--![chlimage_1-252](assets/chlimage_1-252.png)-->

1. Selecteren **[!UICONTROL Start Workflow]** in de lijst.

   <!--![chlimage_1-253](assets/chlimage_1-253.png)-->

1. In de **[!UICONTROL Start Workflow]** selecteert u een workflowmodel in de lijst.

   <!--![chlimage_1-254](assets/chlimage_1-254.png)-->

1. (Optioneel) Geef een titel voor de workflow op, die kan worden gebruikt om naar de instantie van de workflow te verwijzen.

   <!--![chlimage_1-255](assets/chlimage_1-255.png)-->

1. Selecteren **[!UICONTROL Start]** en selecteer vervolgens **[!UICONTROL Proceed]** in het te bevestigen dialoogvenster. Elke stap van de workflow wordt als een gebeurtenis in de tijdlijn weergegeven.

   <!--![chlimage_1-256](assets/chlimage_1-256.png)-->

## Verzamelingen {#collections}

Een verzameling is een geordende set elementen. Gebruik verzamelingen om elementen tussen gebruikers te delen.

* Een verzameling kan elementen van verschillende locaties bevatten, omdat deze alleen verwijzingen naar deze elementen bevatten. Bij elke verzameling blijft de referentiële integriteit van de elementen behouden.
* U kunt verzamelingen delen met meerdere gebruikers met verschillende machtigingsniveaus, zoals bewerken, weergeven, enzovoort.

Voor meer informatie over het beheer van verzamelingen raadpleegt u [Verzamelingen beheren](/help/assets/manage-collections.md).

## Verlopen elementen verbergen bij weergave van elementen in bureaubladtoepassing of Adobe Asset Link {#hide-expired-assets-via-acp-api}

[!DNL Experience Manager] bureaubladtoepassing biedt toegang tot de DAM-opslagplaats van Windows of Mac-desktop. Met de Adobe Asset Link hebt u toegang tot elementen vanuit de ondersteunde [!DNL Creative Cloud] bureaubladtoepassingen.

Bij bladeren door elementen vanuit [!DNL Experience Manager] gebruikersinterface, worden de verlopen elementen niet weergegeven. Beheerders kunnen de volgende configuratie uitvoeren om te voorkomen dat verlopen middelen worden weergegeven, gezocht en opgehaald wanneer ze middelen zoeken vanuit de bureaubladtoepassing en de Asset Link. De configuratie werkt voor alle gebruikers, ongeacht beheerderrechten.

Voer het volgende bevel CURL uit. Leestoegang verzekeren bij `/conf/global/settings/dam/acpapi/` voor gebruikers die toegang hebben tot elementen. Gebruikers die deel uitmaken van `dam-user` groep heeft standaard de machtiging.

```curl
curl -v -u admin:admin --location --request POST 'http://localhost:4502/conf/global/settings/dam/acpapi/configuration/_jcr_content' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'jcr:title=acpapiconfig' \
--data-urlencode 'hideExpiredAssets=true' \
--data-urlencode 'hideExpiredAssets@TypeHint=Boolean' \
--data-urlencode 'jcr:primaryType=nt:unstructured' \
--data-urlencode '../../jcr:primaryType=sling:Folder'
```

Meer informatie vindt u in [door DAM-middelen bladeren met bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) en [hoe te om de Verbinding van Activa van de Adobe te gebruiken](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html).

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
