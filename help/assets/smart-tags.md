---
title: Elementen automatisch labelen met [!DNL Adobe Sensei] slimme service
description: Elementen labelen met een kunstmatige intelligente service die contextuele en beschrijvende bedrijfstags toepast.
contentOwner: AG
feature: Slimme tags,tags toepassen
role: Administrator,Business Practitioner
exl-id: a2abc48b-5586-421c-936b-ef4f896d78b7
translation-type: tm+mt
source-git-commit: 2633a8fdd8301a38cd044ba822494ed54c564863
workflow-type: tm+mt
source-wordcount: '2353'
ht-degree: 5%

---


# Slimme tags toevoegen aan uw elementen om de zoekervaring te verbeteren {#smart-tag-assets-for-faster-search}

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar hun digitale activa te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u de elementen gemakkelijk herkennen en ophalen in zoekopdrachten.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren op basis van bedrijfstaxonomie de activa met de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen. Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer er wordt gezocht naar een promotiecampagne.

Op de achtergrond gebruikt de functionaliteit het kunstmatig intelligente framework van [Adobe Sensei](https://www.adobe.com/nl/sensei/experience-cloud-artificial-intelligence.html) om het algoritme voor beeldherkenning op te leiden in de codestructuur en de bedrijfsconomie. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. [!DNL Experience Manager Assets] implementaties worden  [!DNL Adobe Developer Console] standaard geïntegreerd met .

<!-- TBD: Create a flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

## Ondersteunde elementtypen {#smart-tags-supported-file-formats}

U kunt de volgende typen elementen labelen:

* **Afbeeldingen**: Afbeeldingen in veel indelingen worden gelabeld met behulp van de services voor slimme inhoud van Adobe Sensei. U [maakt een trainingsmodel](#train-model) en [pas slimme tags](#tag-assets) toe op afbeeldingen. Slimme tags worden toegepast op de ondersteunde bestandstypen waarmee uitvoeringen in de JPG- en PNG-indeling worden gegenereerd.
* **Elementen** op basis van tekst:  [!DNL Experience Manager Assets] worden de ondersteunde op tekst gebaseerde elementen automatisch van tags voorzien wanneer deze worden geüpload. Meer informatie over [het labelen van op tekst gebaseerde elementen](#smart-tag-text-based-assets).
* **Video-elementen**: Videocodering is standaard ingeschakeld  [!DNL Adobe Experience Manager] als een  [!DNL Cloud Service]. [Video&#39;s worden automatisch ](/help/assets/smart-tags-video-assets.md) gecodeerd wanneer u nieuwe video&#39;s uploadt of bestaande video&#39;s opnieuw verwerkt.

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
| image/x-xbitmap |  |  |
| image/x-xpixmap |  |  |
| image/x-icon |  |  |
| image/photoshop |  |  |
| image/x-photoshop |  |  |
| image/psd |  |  |
| image/vnd.adobe.photoshop |  |  |

[!DNL Experience Manager] Hiermee voegt u de slimme tags standaard toe aan de op tekst gebaseerde elementen en aan video&#39;s. Als u slimme tags automatisch wilt toevoegen aan afbeeldingen, voert u de volgende taken uit.

* [Leer labelmodellen en richtlijnen](#understand-tag-models-guidelines).
* [Trein het model](#train-model).
* [Tags toewijzen aan uw digitale elementen](#tag-assets).
* [De tags en zoekopdrachten](#manage-smart-tags-and-searches) beheren.

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? Provide a CTA here to buy or contacts Sales team. -->

## Op tekst gebaseerde elementen labelen met slimme tags {#smart-tag-text-based-assets}

De ondersteunde op tekst gebaseerde elementen worden bij het uploaden automatisch gelabeld door [!DNL Experience Manager Assets]. Deze optie is standaard ingeschakeld. De effectiviteit van slimme tags is niet afhankelijk van de hoeveelheid tekst in het element, maar van de relevante trefwoorden of entiteiten in de tekst van het element. Voor op tekst gebaseerde elementen zijn de slimme tags de trefwoorden die in de tekst worden weergegeven, maar de trefwoorden die het element het beste beschrijven. Voor ondersteunde elementen wordt de tekst al geëxtraheerd door [!DNL Experience Manager]. Deze wordt vervolgens geïndexeerd en wordt gebruikt om de elementen te zoeken. Slimme tags die zijn gebaseerd op trefwoorden in de tekst bieden echter een speciale, gestructureerde en prioriteitszoekfactor die wordt gebruikt om de detectie van elementen te verbeteren in vergelijking met de volledige zoekindex.

In vergelijking hiermee worden slimme tags afgeleid van een visueel aspect voor afbeeldingen en video&#39;s.

## Codemodellen en richtlijnen {#understand-tag-models-guidelines} begrijpen

Een labelmodel is een groep gerelateerde tags die zijn gekoppeld aan verschillende visuele aspecten van afbeeldingen die worden gecodeerd. Tags hebben betrekking op de duidelijk verschillende visuele aspecten van afbeeldingen, zodat de tags, wanneer deze worden toegepast, helpen bij het zoeken naar specifieke typen afbeeldingen. Een schoenenverzameling kan bijvoorbeeld verschillende tags hebben, maar alle tags zijn gerelateerd aan schoenen en kunnen tot hetzelfde tagmodel behoren. Wanneer u de labels toepast, kunt u verschillende soorten schoenen vinden, bijvoorbeeld in kleur, op ontwerp of op gebruik. Als u de inhoudsweergave van een trainingsmodel in [!DNL Experience Manager] wilt begrijpen, visualiseert u een trainingsmodel als een entiteit op hoofdniveau die bestaat uit een groep handmatig toegevoegde tags en voorbeeldafbeeldingen voor elke tag. Elke tag kan uitsluitend op een afbeelding worden toegepast.

Voordat u een tagmodel maakt en de service traint, moet u een set unieke tags identificeren die de objecten in de afbeeldingen het beste beschrijven in de context van uw bedrijf. Zorg ervoor dat de elementen in de gekromde set voldoen aan [de trainingsrichtlijnen](#training-guidelines).

### Richtlijnen voor training {#training-guidelines}

Zorg ervoor dat de afbeeldingen in de trainingsset voldoen aan de volgende richtlijnen:

**Aantal en grootte:** minimaal 10 afbeeldingen en maximaal 50 afbeeldingen per tag.

**Coherentie**: Zorg ervoor dat de afbeeldingen voor een tag visueel overeenkomen. U kunt de tags met betrekking tot dezelfde visuele aspecten (zoals hetzelfde type objecten in een afbeelding) het beste aan één tagmodel toevoegen. Het is bijvoorbeeld geen goed idee om al deze afbeeldingen te labelen als `my-party` (voor training), omdat ze er anders uitzien.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/coherence.png)

**Dekking**: De beelden in de training moeten voldoende uiteenlopend zijn. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat AEM leert zich te richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen. Voor de tag *model-down-pose* neemt u bijvoorbeeld meer trainingsafbeeldingen op die lijken op de gemarkeerde afbeelding hieronder, zodat u vergelijkbare afbeeldingen tijdens het labelen nauwkeuriger kunt identificeren.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp). Voor de tag *casual-shoe* is de tweede afbeelding bijvoorbeeld geen goede trainingskandidaat.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/distraction.png)

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Als het bijvoorbeeld gaat om tags zoals *regenjas* en *modelweergave*, voegt u beide tags toe aan de desbetreffende asset voordat u dit opneemt voor training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/completeness.png)

**Aantal tags**: Adobe raadt u aan een model op te leiden met ten minste twee verschillende tags en ten minste tien verschillende afbeeldingen voor elke tag. Voeg in één tagmodel niet meer dan 50 tags toe.

**Aantal voorbeelden**: Voeg voor elke tag ten minste tien voorbeelden toe. Adobe beveelt echter ongeveer 30 voorbeelden aan. Er worden maximaal 50 voorbeelden per tag ondersteund.

**Voorkomen van valse positieven en conflicten**: Adobe raadt u aan één tagmodel te maken voor één visueel aspect. Structuur de labelmodellen zodanig dat overlappende codes tussen de modellen worden voorkomen. Gebruik bijvoorbeeld geen gemeenschappelijke tags zoals `sneakers` in twee verschillende labelmodellen: `shoes` en `footwear`. Het trainingsproces overschrijft het ene getrainde tagmodel met het andere voor een algemeen trefwoord.

**Voorbeelden**: Hier volgen nog enkele voorbeelden van:

* Maak een labelmodel dat het volgende bevat:
   * alleen de labels die betrekking hebben op automodellen.
   * alleen de labels die betrekking hebben op kleuren van overhemden.
   * alleen de labels voor jassen voor vrouwen en mannen.
* Niet maken,
   * een tagmodel dat automodellen bevat die in 2019 en 2020 zijn uitgebracht .
   * meerdere tagmodellen met dezelfde paar automodellen.

**Afbeeldingen die worden gebruikt om te trainen**: U kunt dezelfde afbeeldingen gebruiken om verschillende tagmodellen te trainen. Koppel een afbeelding echter niet aan meerdere tags in een labelmodel. U kunt dezelfde afbeelding labelen met verschillende tags die bij verschillende labelmodellen horen.

U kunt de training niet ongedaan maken. Aan de hand van de bovenstaande richtlijnen kunt u goede afbeeldingen kiezen om te trainen.

## Het model voor uw aangepaste tags {#train-model}

Voer de volgende stappen uit om een model voor uw bedrijfsspecifieke tags te maken en op te leiden:

1. Maak de benodigde labels en de juiste codestructuur. Upload de relevante afbeeldingen in de DAM-opslagplaats.
1. In [!DNL Experience Manager] gebruikersinterface, toegang **[!UICONTROL Assets]** > **[!UICONTROL Smart Tag Training]**.
1. Klik op **[!UICONTROL Create]**. Geef **[!UICONTROL Title]**, **[!UICONTROL Description]** op.
1. Blader en selecteer de tags van de bestaande tags in `cq:tags` waarvoor u het model wilt trainen. Klik op **[!UICONTROL Next]**.
1. Klik in het dialoogvenster **[!UICONTROL Select Assets]** op **[!UICONTROL Add Assets]** bij elke tag. Zoek in de DAM-opslagplaats of blader door de opslagplaats om ten minste 10 en ten hoogste 50 afbeeldingen te selecteren. Selecteer elementen en niet de map. Als u de afbeeldingen hebt geselecteerd, klikt u op **[!UICONTROL Select]**.

   ![Trainingsstatus weergeven](assets/smart-tags-training-status.png)

1. Als u een voorvertoning van de miniaturen van de geselecteerde afbeeldingen wilt weergeven, klikt u op de accordeon vóór een tag. U kunt de selectie wijzigen door op **[!UICONTROL Add Assets]** te klikken. Als u tevreden bent met de selectie, klikt u op **[!UICONTROL Submit]**. In de gebruikersinterface wordt onder aan de pagina een melding weergegeven dat de training wordt gestart.
1. Controleer de status van de training in de kolom **[!UICONTROL Status]** voor elk tagmodel. Mogelijke statussen zijn [!UICONTROL Pending], [!UICONTROL Trained] en [!UICONTROL Failed].

![Workflow voor het trainen van coderingsmodel voor slimme tags](assets/smart-tag-model-training-flow.png)

*Afbeelding: Stappen van de trainingsworkflow om het coderingsmodel te trainen.*

### Trainingsstatus weergeven en {#training-status} rapporteren

Als u wilt controleren of de service Slimme tags is opgeleid voor uw tags in de trainingsset met elementen, raadpleegt u het workflowrapport voor training in de rapportconsole.

1. Ga in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. Klik op **[!UICONTROL Asset Reports]** op de pagina.**[!UICONTROL Create]**
1. Selecteer het **[!UICONTROL Smart Tags Training]** rapport, en klik dan **[!UICONTROL Next]** van de toolbar.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk om het rapport weer te geven.
1. Bekijk de details van het rapport. Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de service Slimme tags is getraind voor de tag. Een gele kleur geeft aan dat de service niet volledig is getraind voor een bepaalde tag. Voeg in dit geval meer afbeeldingen met de desbetreffende tag toe en voer de trainingsworkflow uit om de service volledig op de tag te trainen. Als dit rapport uw tags niet bevat, voert u de trainingsworkflow voor deze tags opnieuw uit.Tags
1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een spreadsheet [!DNL Microsoft Excel].

## Elementen {#tag-assets} labelen

Nadat u de service Slimme tags hebt opgeleid, worden de geüploade elementen automatisch gecodeerd. [!DNL Experience Manager] past de juiste tags toe in bijna real-time. U kunt de workflow voor labelen op aanvraag toepassen of u kunt deze plannen om periodiek uit te voeren. De workflow voor labelen is van toepassing op zowel elementen als mappen.

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

## Slimme tags beheren en zoeken naar middelen {#manage-smart-tags-and-searches}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkelementen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags ook verfijnen door ervoor te zorgen dat uw elementen in de zoekresultaten voor de meest relevante tags worden weergegeven. In feite helpt dit de kans te verkleinen dat niet-verwante elementen in zoekresultaten worden weergegeven.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie van de tag voor het element te vergroten. Door een tag voor een element te promoten, vergroot u de kans dat het element in de zoekresultaten wordt weergegeven wanneer een zoekopdracht wordt uitgevoerd op basis van de desbetreffende tag.

De slimme tags van uw elementen reduceren:

1. Zoek in het zoekveld naar elementen op basis van een tag.

1. Inspect de zoekresultaten om de elementen te identificeren die je niet relevant vindt voor je zoekopdracht.

1. Selecteer het element en selecteer ![Tags beheren pictogram](assets/do-not-localize/manage-tags-icon.png) op de werkbalk.

1. Controleer de tags op de pagina **[!UICONTROL Manage Tags]**. Als u niet wilt dat het element wordt doorzocht op basis van een specifieke tag, selecteert u de tag en selecteert u ![Pictogram Verwijderen](assets/do-not-localize/delete-icon.png) op de werkbalk. U kunt ook `X`-symbool naast het label selecteren.

1. Als u een hogere rangorde aan een tag wilt toewijzen, selecteert u de tag en selecteert u ![Promote icon](assets/do-not-localize/promote-icon.png) op de werkbalk. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]**.

1. Selecteer **[!UICONTROL Save]** en selecteer **[!UICONTROL OK]** om het [!UICONTROL Success] dialoogvenster te sluiten.

1. Navigeer naar de pagina [!UICONTROL Properties] voor het element. Let erop dat de tag die u hebt bevorderd een grote relevantie krijgt en daarom hoger wordt weergegeven in de zoekresultaten.

### AEM zoekresultaten begrijpen met slimme tags {#understand-search}

Standaard combineert AEM zoekopdracht de zoektermen met een `AND`-component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, wordt een `OR`-component toegevoegd om een zoekterm in de toegepaste slimme tags te zoeken. U kunt bijvoorbeeld zoeken naar `woman running`. Elementen met alleen het trefwoord `woman` of `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat is gelabeld met `woman` of `running` met behulp van slimme tags, wordt echter wel weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* elementen met de trefwoorden `woman` en `running` in de metagegevens.

* elementen die zijn gelabeld met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. overeenkomend met `woman running` in de verschillende metagegevensvelden.
1. overeenkomsten van `woman running` in slimme markeringen.
1. overeenkomende met `woman` of `running` in slimme tags.

## Beperkingen en aanbevolen procedures voor tags {#limitations}

Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de slimme tags heeft de volgende beperkingen:

* Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
* Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
* Tags worden ondersteund in de talen die [!DNL Experience Manager] ondersteunt. Zie [Opmerkingen bij de release Smart Content Service](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/smart-content-service-release-notes.html#languages) voor een lijst met talen.
* Tags die niet op realistische wijze worden verwerkt, hebben betrekking op:

   * Niet-visuele, abstracte aspecten. Bijvoorbeeld het jaar of het seizoen waarin een product wordt uitgebracht, de sfeer of emotie die door een beeld wordt opgewekt, de subjectieve connotatie van een video enzovoort.
   * Fijne visuele verschillen in producten zoals overhemden met en zonder halsbanden of op producten ingebedde logo&#39;s van kleine producten.

<!-- TBD: Add limitations related to text-based assets. -->

Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u de zoekopdracht [!DNL Assets] (zoeken in volledige tekst). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!NOTE]
>
>Of u met slimme tags op uw tags kunt trainen en deze kunt toepassen op andere afbeeldingen, is afhankelijk van de kwaliteit van de afbeeldingen die u gebruikt voor training.
>Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

>[!MORELIKETHIS]
>
>* [Begrijp hoe slimme tags u helpen elementen te beheren](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)
>* [Slimme tags toepassen op de video-elementen](smart-tags-video-assets.md)

