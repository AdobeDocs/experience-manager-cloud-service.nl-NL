---
title: Hoe kunt u slimme tags toevoegen aan elementen in AEM?
description: Voeg slimme tags toe aan elementen in AEM met een kunstmatige intelligente service die contextafhankelijke en beschrijvende bedrijfstags toepast.
contentOwner: AG
feature: Smart Tags
role: Admin, User
exl-id: a2abc48b-5586-421c-936b-ef4f896d78b7
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 4%

---


# Slimme tags toevoegen aan elementen in AEM {#smart-tags-assets-aem}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/enhanced-smart-tags.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar hun digitale activa te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u de elementen gemakkelijk herkennen en ophalen in zoekopdrachten.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren op basis van bedrijfstaxonomie de activa met de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen. Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer er wordt gezocht naar een promotiecampagne.

Op de achtergrond gebruikt de functionaliteit het kunstmatig intelligente framework van [Adobe Sensei](https://business.adobe.com/why-adobe/experience-cloud-artificial-intelligence.html) om het algoritme voor imageherkenning op te leiden in de codestructuur en de taxonomie van het bedrijf. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. AEM past automatisch slimme tags toe op geüploade elementen.

<!-- TBD: Create a flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

## Ondersteunde elementtypen voor slimme tags in AEM {#smart-tags-supported-file-formats}

U kunt de volgende typen elementen labelen:

* **Afbeeldingen**: Afbeeldingen in veel indelingen worden gelabeld met behulp van de services voor slimme inhoud van Adobe Sensei. U [een trainingsmodel maken](#train-model) en worden de geüploade afbeeldingen automatisch gelabeld. Slimme tags worden toegepast op de ondersteunde bestandstypen die uitvoeringen genereren in de JPG- en PNG-indeling.
* **Op tekst gebaseerde elementen**: [!DNL Experience Manager Assets] worden de ondersteunde op tekst gebaseerde elementen automatisch van tags voorzien wanneer deze worden geüpload.
* **Video-elementen**: Videocodering is standaard ingeschakeld in [!DNL Adobe Experience Manager] als [!DNL Cloud Service]. [Video&#39;s hebben automatisch tags](/help/assets/smart-tags-video-assets.md) wanneer u nieuwe video&#39;s uploadt of bestaande video&#39;s opnieuw verwerkt.

| Afbeeldingen (MIME-typen) | Op tekst gebaseerde elementen (bestandsindelingen) | Video-elementen (bestandsindelingen en codecs) |
|----|-----|------|
| image/jpeg | CSV | MP4 (H264/AVC) |
| image/tiff | DOC | MKV (H264/AVC) |
| image/png | DOCX | MOV (H264/AVC, Motion JPEG) |
| image/bmp | HTML | AVI (indeo4) |
| image/gif | PDF | FLV (H264/AVC, vp6f) |
| image/pjpeg | PPT | WMV (WMV2) |
| image/x-portable-anymap | PPTX |  |
| image/x-portable-bitmap | RTF |  |
| image/x-portable-graymap | SRT |  |
| image/x-portable-pixmap | TXT |  |
| image/x-rgb | VTT |  |
| image/x-xbitmap | |  |
| image/x-xpixmap | |  |
| image/x-icon |  |  |
| image/photoshop |  |  |
| image/x-photoshop |  |  |
| image/psd |  |  |
| image/vnd.adobe.photoshop |  |  |

AEM voegt de slimme tags standaard toe aan de tekstelementen en aan video&#39;s. Als u slimme tags automatisch wilt toevoegen aan afbeeldingen, voert u de volgende taken uit.

* [Leer labelmodellen en -richtlijnen](#understand-tag-models-guidelines).
* [Het model trainen](#train-model).
* [Tags toewijzen aan digitale elementen](#tag-assets).
* [Tags en zoekopdrachten beheren](#manage-smart-tags-and-searches).

## Leer labelmodellen en -richtlijnen {#understand-tag-models-guidelines}

Een labelmodel is een groep gerelateerde tags die zijn gekoppeld aan verschillende visuele aspecten van afbeeldingen die worden gecodeerd. Tags hebben betrekking op de duidelijk verschillende visuele aspecten van afbeeldingen, zodat de tags, wanneer deze worden toegepast, helpen bij het zoeken naar specifieke typen afbeeldingen. Een schoenenverzameling kan bijvoorbeeld verschillende tags hebben, maar alle tags zijn gerelateerd aan schoenen en kunnen tot hetzelfde tagmodel behoren. Wanneer u de labels toepast, kunt u verschillende soorten schoenen vinden, bijvoorbeeld op basis van ontwerp of gebruik. De inhoudrepresentatie van een trainingsmodel begrijpen in [!DNL Experience Manager]U kunt een trainingsmodel visualiseren als een entiteit op hoofdniveau die bestaat uit een groep handmatig toegevoegde tags en voorbeeldafbeeldingen voor elke tag. Elke tag kan uitsluitend op een afbeelding worden toegepast.

Voordat u een tagmodel maakt en de service traint, moet u een set unieke tags identificeren die de objecten in de afbeeldingen het beste beschrijven in de context van uw bedrijf. Zorg ervoor dat de elementen in de beheerde set overeenkomen met [de opleidingsrichtsnoeren](#training-guidelines).

### Richtlijnen voor training {#training-guidelines}

Zorg ervoor dat de afbeeldingen in de trainingsset voldoen aan de volgende richtlijnen:

**Hoeveelheid en grootte:** Minimaal 10 afbeeldingen en maximaal 50 afbeeldingen per tag.

**Coherentie**: Zorg ervoor dat de afbeeldingen voor een tag visueel op elkaar lijken. U kunt de tags met betrekking tot dezelfde visuele aspecten (zoals hetzelfde type objecten in een afbeelding) het beste aan één tagmodel toevoegen. Het is bijvoorbeeld geen goed idee om deze afbeeldingen van tags te voorzien `my-party` (voor training) omdat ze niet op elkaar lijken.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/coherence.png)

**Dekking**: De beelden in de training moeten voldoende uiteenlopend zijn. Het is de bedoeling om een paar maar redelijk uiteenlopende voorbeelden te geven, zodat [!DNL Experience Manager] leert u te focussen op de juiste zaken . Als u dezelfde tag toepast op visueel ongelijke afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen. Bijvoorbeeld voor de tag *model-down-pose* neemt u meer trainingsafbeeldingen op die lijken op de gemarkeerde afbeelding hieronder, zodat u vergelijkbare afbeeldingen tijdens het labelen nauwkeuriger kunt identificeren.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp). Bijvoorbeeld voor de tag *casual-shoe* Het tweede imago is geen goede kandidaat voor opleiding.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/distraction.png)

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Als het bijvoorbeeld gaat om tags zoals *regenjas* en *modelweergave*, voegt u beide tags toe aan de desbetreffende asset voordat u dit opneemt voor training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/completeness.png)

**Aantal tags**: Adobe raadt u aan een model op te leiden met ten minste twee verschillende tags en ten minste tien verschillende afbeeldingen voor elke tag. Voeg in één tagmodel niet meer dan 50 tags toe.

**Aantal voorbeelden**: Voeg voor elke tag ten minste tien voorbeelden toe. De Adobe beveelt echter ongeveer 30 voorbeelden aan. Er worden maximaal 50 voorbeelden per tag ondersteund.

**Voorkomen van valse positieven en conflicten**: Adobe raadt u aan één tagmodel te maken voor één visueel aspect. Structuur de labelmodellen zodanig dat overlappende codes tussen de modellen worden voorkomen. Gebruik bijvoorbeeld geen algemene tags, zoals `sneakers` in twee verschillende tagmodellen: `shoes` en `footwear`. Het trainingsproces overschrijft het ene getrainde tagmodel met het andere voor een algemeen trefwoord.

**Voorbeelden**: Meer voorbeelden hiervan zijn:

* Maak een tagmodel dat alleen het volgende bevat:

   * De labels die betrekking hebben op automodellen.
   * De labels hadden betrekking op hoesjes voor volwassenen en kinderen.

* Niet maken,

   * Een labelmodel dat automodellen bevat die in 2019 en 2020 zijn uitgebracht.
   * Meerdere labelmodellen met dezelfde paar automodellen.

**Afbeeldingen die worden gebruikt om te trainen**: U kunt dezelfde afbeeldingen gebruiken om verschillende tagmodellen te trainen. Koppel een afbeelding echter niet aan meerdere tags in een labelmodel. U kunt dezelfde afbeelding labelen met verschillende tags die bij verschillende labelmodellen horen.

U kunt de training niet ongedaan maken. Aan de hand van de bovenstaande richtlijnen kunt u goede afbeeldingen kiezen om te trainen.

## Het model trainen voor uw douanetags {#train-model}

Voer de volgende stappen uit om een model voor uw bedrijfsspecifieke tags te maken en op te leiden:

1. Maak de benodigde labels en de juiste codestructuur. Upload de relevante afbeeldingen in de DAM-opslagplaats.
1. In [!DNL Experience Manager] gebruikersinterface, toegang **[!UICONTROL Assets]** > **[!UICONTROL Smart Tag Training]**.
1. Klik op **[!UICONTROL Create]**. Geef een **[!UICONTROL Title]**, **[!UICONTROL Description]**.
1. Klik op het mappictogram in **[!UICONTROL Tags]** veld. Er wordt een pop-upvenster geopend.
1. Zoek of selecteer de juiste tags van de bestaande tags in `cq-tags` die u aan het model wilt toevoegen. Klik op **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >U kunt de codestructuur in oplopende of aflopende volgorde sorteren op basis van de opties **[!UICONTROL Name]** (alfabetische volgorde), **[!UICONTROL Created]** datum, of **[!UICONTROL Modified]** datum.


1. In de **[!UICONTROL Select Assets]** dialoogvenster, klikt u op **[!UICONTROL Add Assets]** op elke tag. Zoek in de DAM-opslagplaats of blader door de opslagplaats om ten minste 10 en ten hoogste 50 afbeeldingen te selecteren. Selecteer elementen en niet de map. Klik op **[!UICONTROL Select]**.

   ![Trainingsstatus weergeven](assets/smart-tags-training-status.png)

1. Als u een voorvertoning van de miniaturen van de geselecteerde afbeeldingen wilt weergeven, klikt u op de accordeon vóór een tag. U kunt uw selectie wijzigen door op **[!UICONTROL Add Assets]**. Als u tevreden bent met de selectie, klikt u **[!UICONTROL Submit]**. In de gebruikersinterface wordt onder aan de pagina een melding weergegeven dat de training wordt gestart.
1. Controleer de status van de training in het deelvenster **[!UICONTROL Status]** kolom voor elk tagmodel. Mogelijke statussen zijn [!UICONTROL Pending], [!UICONTROL Trained], en [!UICONTROL Failed].

![Workflow voor het trainen van coderingsmodel voor slimme tags](assets/smart-tag-model-training-flow.png)

*Afbeelding: Stappen van de trainingsworkflow om het coderingsmodel op te leiden.*

### Trainingsstatus en rapport weergeven {#training-status}

Als u wilt controleren of de service Slimme tags is opgeleid voor uw tags in de trainingsset met elementen, raadpleegt u het workflowrapport voor training in de rapportconsole.

1. In [!DNL Experience Manager] interface, ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. In de **[!UICONTROL Asset Reports]** pagina, klikt u **[!UICONTROL Create]**.
1. Selecteer de **[!UICONTROL Smart Tags Training]** rapport, en klik dan **[!UICONTROL Next]** op de werkbalk.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk.
1. Bekijk de details van het rapport. Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in het dialoogvenster **[!UICONTROL Training Status]** de kolom wijst erop dat de Slimme dienst van Markeringen voor de markering wordt getraind. Gele kleur geeft aan dat de service gedeeltelijk is opgeleid voor een bepaalde tag. Als u de service volledig wilt trainen voor een tag, voegt u meer afbeeldingen met de desbetreffende tag toe en voert u de trainingsworkflow uit. Als dit rapport uw tags niet bevat, voert u de trainingsworkflow opnieuw uit voor deze tags.Tags
1. Om het rapport te downloaden, selecteer het van de lijst, en klik **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een spreadsheet.

<!--
### Tag assets from the workflow console {#tagging-assets-from-the-workflow-console}

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL DAM Smart Tags Assets]** workflow and then click **[!UICONTROL Start Workflow]** from the toolbar.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. In the **[!UICONTROL Run Workflow]** dialog, browse to the payload folder containing assets on which you want to apply your tags automatically.
1. Specify a title for the workflow and an optional comment. Click **[!UICONTROL Run]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   *Figure: Navigate to the asset folder and review the tags to verify whether your assets are tagged properly. For details, see [manage smart tags](#manage-smart-tags-and-searches).*

### Tag assets from the timeline {#tagging-assets-from-the-timeline}

1. From the [!DNL Assets] user interface, select the folder containing assets or specific assets to which you want to apply smart tags.
1. From upper-left corner, open the **[!UICONTROL Timeline]**.
1. Open actions from the bottom of the left sidebar and click **[!UICONTROL Start Workflow]**.

   ![start_workflow](assets/start_workflow.png)

1. Select the **[!UICONTROL DAM Smart Tag Assets]** workflow, and specify a title for the workflow.
1. Click **[!UICONTROL Start]**. The workflow applies your tags on assets. Navigate to the asset folder and review the tags to verify that your assets are tagged properly. For details, see [manage smart tags](#manage-smart-tags-and-searches).

>[!NOTE]
>
>In the subsequent tagging cycles, only the modified assets are tagged again with newly trained tags. However, even unaltered assets are tagged if the gap between the last and current tagging cycles for the tagging workflow exceeds 24 hours. For periodic tagging workflows, unaltered assets are tagged when the time gap exceeds six months.

### Tag uploaded assets {#tag-uploaded-assets}

[!DNL Experience Manager] can automatically tag the assets that users upload to DAM. To do so, administrators configure a workflow to add an available step that tags assets. See [how to enable Smart Tags for uploaded assets](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets).
-->

## Elementen labelen met slimme tags in AEM {#tag-assets}

Alle typen ondersteunde elementen worden automatisch gelabeld door [!DNL Experience Manager Assets] bij uploaden. Tags worden standaard ingeschakeld en werkt. AEM past de juiste slimme tags toe in bijna real-time. <!-- TBD: You can also apply the tagging workflow on-demand. The workflow applies to both, assets and folders. -->

* Voor afbeeldingen en video&#39;s zijn de slimme tags gebaseerd op een visueel aspect.

* Voor op tekst gebaseerde elementen is de effectiviteit van slimme tags niet afhankelijk van de hoeveelheid tekst in het element, maar van de relevante trefwoorden of entiteiten in de tekst van het element. Voor op tekst gebaseerde elementen zijn de slimme tags de trefwoorden die in de tekst worden weergegeven, maar de trefwoorden die het element het beste beschrijven. Voor ondersteunde elementen: [!DNL Experience Manager] Hiermee wordt de tekst al uitgepakt. Deze wordt vervolgens geïndexeerd en wordt gebruikt om de elementen te zoeken. Slimme tags die op trefwoorden in de tekst zijn gebaseerd, bieden echter een toegewezen, gestructureerde en prioriteitszoekfacet. Deze laatste functie verbetert de detectie van elementen in vergelijking met een zoekindex.

## Slimme tags beheren en zoeken naar middelen {#manage-smart-tags-and-searches}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkelementen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags ook verfijnen door ervoor te zorgen dat uw elementen in de zoekresultaten voor de meest relevante tags worden weergegeven. In feite helpt dit de kans te verkleinen dat niet-verwante elementen in zoekresultaten worden weergegeven.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie van de tag voor het element te vergroten. Door een tag voor een element te promoten, vergroot u de kans dat het element in de zoekresultaten wordt weergegeven wanneer een zoekopdracht wordt uitgevoerd op basis van de desbetreffende tag.

Slimme tags toepassen op uw digitale elementen:

1. Zoek in het zoekveld naar digitale elementen op basis van een tag.

1. Om de digitale activa te identificeren die u niet relevant voor uw onderzoek vindt, inspecteer de onderzoeksresultaten.

1. Selecteer een element en selecteer vervolgens ![Tags beheren, pictogram](assets/do-not-localize/manage-tags-icon.png) op de werkbalk.

1. Van de **[!UICONTROL Manage Tags]** pagina, controleert u de tags. Als u het element niet wilt doorzoeken op basis van een specifieke tag, selecteert u de tag en selecteert u ![Pictogram Verwijderen](assets/do-not-localize/delete-icon.png) op de werkbalk. U kunt ook `X` naast het label.

1. Als u een hogere rang aan een tag wilt toewijzen, selecteert u de tag en selecteert u ![Pictogram Promoten](assets/do-not-localize/promote-icon.png) op de werkbalk. De tag die u promoot, wordt verplaatst naar de **[!UICONTROL Tags]** sectie.

1. Selecteren **[!UICONTROL Save]** en selecteer vervolgens **[!UICONTROL OK]** om de [!UICONTROL Success] in.

1. Ga naar de [!UICONTROL Properties] pagina voor het element. Let erop dat de tag die u hebt bevorderd een grote relevantie krijgt en daarom hoger wordt weergegeven in de zoekresultaten.

### Begrijpen [!DNL Experience Manager] zoekresultaten met slimme tags {#understand-search}

Standaard, [!DNL Experience Manager] zoektermen worden gecombineerd met een `AND` clausule. Het gebruik van slimme tags verandert dit standaardgedrag niet. Slimme tags gebruiken voegt een `OR` om een zoekterm te zoeken in de toegepaste slimme tags. Kijk bijvoorbeeld eens naar `woman running`. Middelen met alleen `woman` of alleen `running` trefwoorden in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat echter is gelabeld met een van de `woman` of `running` het gebruik van slimme tags wordt weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* Middelen met `woman` en `running` trefwoorden in de metagegevens.

* Elementen die zijn getagd met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. overeenkomend met `woman running` in de verschillende metagegevensvelden.
1. overeenkomend met `woman running` in slimme tags.
1. overeenkomend met `woman` of van `running` in slimme tags.

## Beperkingen en beste praktijken op het gebied van tags {#limitations}

Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de slimme tags heeft de volgende beperkingen:

* Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne of standaard passend overhemden.
* Kan geen tags identificeren op basis van kleine patronen of delen van een afbeelding. Bijvoorbeeld logo&#39;s op hemden.
* Tags worden ondersteund in de talen die [!DNL Experience Manager] ondersteunt.
* De tags die niet worden verwerkt, hebben betrekking op:

   * Niet-visuele, abstracte aspecten. Bijvoorbeeld het jaar of het seizoen waarin een product wordt uitgebracht, de sfeer van of de emotie die door een beeld wordt opgeroepen, en een subjectieve connotatie van een video.
   * Fijne visuele verschillen in producten zoals overhemden met en zonder halsbanden of op producten ingebedde logo&#39;s van kleine producten.

Gebruik de meest geschikte afbeeldingen om het model op te leiden. De training kan niet worden teruggezet of het trainingsmodel kan niet worden verwijderd. De nauwkeurigheid van de tags is afhankelijk van de huidige training, dus doe dit zorgvuldig.

<!-- TBD: Add limitations related to text files. -->

Als u bestanden met slimme tags wilt zoeken (normaal of verbeterd), gebruikt u de opdracht [!DNL Assets] zoeken (zoeken in volledige tekst). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!NOTE]
>
>Of u met slimme tags op uw tags kunt trainen en deze kunt toepassen op andere afbeeldingen, is afhankelijk van de kwaliteit van de afbeeldingen die u gebruikt voor training.
>Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

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

>[!MORELIKETHIS]
>
>* [Begrijp hoe slimme tags helpen uw digitale bestanden te beheren](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)
>* [Slimme tags gebruiken voor video&#39;s](smart-tags-video-assets.md)
