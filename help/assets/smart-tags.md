---
title: Elementen automatisch labelen met door AI gegenereerde tags
description: Elementen labelen met behulp van kunstmatige intelligente services die contextafhankelijke en beschrijvende bedrijfstags toepassen met behulp van [!DNL Adobe Sensei] service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7af525ed1255fb4c4574c65dc855e0df5f1da402
workflow-type: tm+mt
source-wordcount: '2487'
ht-degree: 5%

---


# Slimme tags toevoegen aan uw elementen voor snellere zoekopdrachten {#smart-tag-assets-for-faster-search}

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar hun digitale activa te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u de elementen gemakkelijk herkennen en ophalen in zoekopdrachten.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren op basis van bedrijfstaxonomie de activa met de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen. Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer er wordt gezocht naar een promotiecampagne.

Op de achtergrond gebruiken de slimme tags het kunstmatig intelligente raamwerk van [Adobe Sensei](https://www.adobe.com/nl/sensei/experience-cloud-artificial-intelligence.html) om het algoritme voor beeldherkenning op te leiden in de codestructuur en de bedrijfsconomie. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen.

<!-- TBD: Create a flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

## Ondersteunde elementtypen {#smart-tags-supported-file-formats}

Slimme tags worden alleen toegepast op ondersteunde bestandstypen die uitvoeringen in de JPG- en PNG-indeling genereren. De functionaliteit wordt ondersteund voor de volgende typen elementen:

| Afbeeldingen (MIME-typen) | Op tekst gebaseerde elementen (bestandsindelingen) | Video-elementen (bestandsindelingen en codecs) |
|----|-----|------|
| image/jpeg | TXT | MP4 (H264/AVC) |
| image/tiff | RTF | MKV (H264/AVC) |
| image/png | DITA | MOV (H264/AVC, Motion JPEG) |
| image/bmp | XML | AVI (indeo4) |
| image/gif | JSON | FLV (H264/AVC, vp6f) |
| image/pjpeg | DOC | WMV (WMV2) |
| image/x-portable-anymap | DOCX |  |
| image/x-portable-bitmap | PDF |  |
| image/x-portable-graymap | CSV |  |
| image/x-portable-pixmap | PPT |  |
| image/x-rgb | PPTX |  |
| image/x-xbitmap | VTT |  |
| image/x-xpixmap | SRT |  |
| image/x-icon |  |  |
| image/photoshop |  |  |
| image/x-photoshop |  |  |
| image/psd |  |  |
| image/vnd.adobe.photoshop |  |  |

[!DNL Experience Manager] Hiermee voegt u de slimme tags standaard toe aan de op tekst gebaseerde elementen en aan video&#39;s. Als u slimme tags automatisch wilt toevoegen aan afbeeldingen, voert u de volgende taken uit.

* [ [!DNL Adobe Experience Manager] Integreren met Adobe Developer Console](#integrate-aem-with-aio).
* [Leer labelmodellen en richtlijnen](#understand-tag-models-guidelines).
* [Trein het model](#train-model).
* [Tags toewijzen aan uw digitale elementen](#tag-assets).
* [De tags en zoekopdrachten](#manage-smart-tags-and-searches) beheren.

>[!TIP]
>
>Slimme tags zijn alleen van toepassing voor [!DNL Adobe Experience Manager Assets]-klanten. De slimme tags kunnen worden aangeschaft als een invoegtoepassing voor [!DNL Experience Manager].

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? Provide a CTA here to buy or contacts Sales team. -->

## [!DNL Experience Manager] integreren met Adobe Developer Console {#integrate-aem-with-aio}

>[!IMPORTANT]
>
>De nieuwe [!DNL Experience Manager Assets]-implementaties zijn standaard geïntegreerd met [!DNL Adobe Developer Console]. De functie helpt de functionaliteit voor slimme tags sneller te configureren. Bij oudere implementaties kunnen beheerders handmatig [de integratie van slimme tags configureren](/help/assets/smart-tags-configuration.md#aio-integration).

U kunt [!DNL Adobe Experience Manager] met de Slimme Markeringen integreren gebruikend [!DNL Adobe Developer Console]. Gebruik deze configuratie om tot de Slimme dienst van Markeringen van binnen [!DNL Experience Manager] toegang te hebben. Zie [Experience Manager configureren voor slimme tags van elementen](smart-tags-configuration.md) voor taken om de slimme tags te configureren. Aan het achterste eind, verifieert de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van de Console van de Ontwikkelaar van Adobe alvorens uw verzoek aan de Slimme dienst van Markeringen door:sturen.

## Codemodellen en richtlijnen {#understand-tag-models-guidelines} begrijpen

Een tagmodel is een groep gerelateerde tags die een visueel aspect van de afbeelding hebben. Een schoenenverzameling kan bijvoorbeeld verschillende tags hebben, maar alle tags zijn gerelateerd aan schoenen en kunnen tot hetzelfde tagmodel behoren. Tags kunnen alleen betrekking hebben op de duidelijk verschillende visuele aspecten van afbeeldingen. Als u de inhoudsweergave van een trainingsmodel in [!DNL Experience Manager] wilt begrijpen, visualiseert u een trainingsmodel als een entiteit op hoofdniveau die bestaat uit een groep handmatig toegevoegde tags en voorbeeldafbeeldingen voor elke tag. Elke tag kan uitsluitend op een afbeelding worden toegepast.

Labels die op realistische wijze niet kunnen worden verwerkt, hebben betrekking op:

* Niet-visuele, abstracte aspecten, zoals het jaar of het seizoen waarin een product wordt uitgebracht, de sfeer van of de emotie die door een afbeelding wordt opgeroepen.
* Fijne visuele verschillen in producten zoals overhemden met en zonder halsbanden of op producten ingebedde logo&#39;s van kleine producten.

Voordat u een tagmodel maakt en de service traint, moet u een set unieke tags identificeren die de objecten in de afbeeldingen het beste beschrijven in de context van uw bedrijf. Zorg ervoor dat de elementen in de gekromde set voldoen aan [de trainingsrichtlijnen](#training-guidelines).

### Richtlijnen voor training {#training-guidelines}

De afbeeldingen in uw trainingsset moeten aan de volgende richtlijnen voldoen:

**Aantal en grootte:** minimaal 10 afbeeldingen en maximaal 50 afbeeldingen per tag.

**Coherentie**: Afbeeldingen voor een tag moeten visueel op elkaar lijken. U kunt de tags met betrekking tot dezelfde visuele aspecten (zoals hetzelfde type objecten in een afbeelding) het beste samenvoegen tot één tagmodel. Het is bijvoorbeeld geen goed idee om al deze afbeeldingen te labelen als `my-party` (voor training), omdat ze er anders uitzien.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/coherence.png)

**Dekking**: De beelden in de training moeten voldoende uiteenlopend zijn. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat AEM leert zich te richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen. Voor de tag *model-down-pose* neemt u bijvoorbeeld meer trainingsafbeeldingen op die lijken op de gemarkeerde afbeelding hieronder, zodat u vergelijkbare afbeeldingen tijdens het labelen nauwkeuriger kunt identificeren.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp). Voor de tag *casual-shoe* is de tweede afbeelding bijvoorbeeld geen goede trainingskandidaat.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/distraction.png)

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Als het bijvoorbeeld gaat om tags zoals *regenjas* en *modelweergave*, voegt u beide tags toe aan de desbetreffende asset voordat u dit opneemt voor training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](assets/do-not-localize/completeness.png)

**Aantal tags**: Adobe raadt u aan een model op te leiden met ten minste twee verschillende tags en ten minste 10 verschillende afbeeldingen voor elke tag. Voeg in één tagmodel niet meer dan 50 tags toe.

**Aantal voorbeelden**: Voeg voor elke tag ten minste 10 voorbeelden toe. Adobe beveelt echter ongeveer 30 voorbeelden aan. Er worden maximaal 50 voorbeelden per tag ondersteund.

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

1. Ga in [!DNL Experience Manager] interface naar **[!UICONTROL Tools] > **[!UICONTROL Assets] > **[!UICONTROL Reports]**.
1. Klik op **[!UICONTROL Asset Reports]** op de pagina.**[!UICONTROL Create]**
1. Selecteer het **[!UICONTROL Smart Tags Training]** rapport, en klik dan **[!UICONTROL Next]** van de toolbar.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk om het rapport weer te geven.
1. Bekijk de details van het rapport. Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de service Slimme tags is getraind voor de tag. Een gele kleur geeft aan dat de service niet volledig is getraind voor een bepaalde tag. Voeg in dit geval meer afbeeldingen met de desbetreffende tag toe en voer de trainingsworkflow uit om de service volledig op de tag te trainen. Als dit rapport uw tags niet bevat, voert u de trainingsworkflow voor deze tags opnieuw uit.Tags
1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een spreadsheet [!DNL Microsoft Excel].

## Elementen {#tag-assets} labelen

Nadat u de service Slimme tags hebt opgeleid, kunt u de codeerworkflow activeren en automatisch de juiste tags toepassen op een andere set vergelijkbare elementen. U kunt de workflow voor labelen periodiek of telkens wanneer dat nodig is toepassen. De workflow voor labelen is van toepassing op zowel elementen als mappen.

### Elementen labelen vanaf de workflowconsole {#tagging-assets-from-the-workflow-console}

1. Ga in de interface van de Experience Manager naar **[!UICONTROL Tools > Workflow > Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL DAM Smart Tags Assets]**-workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Blader in het dialoogvenster **[!UICONTROL Run Workflow]** naar de payload-map met elementen waarop u de tags automatisch wilt toepassen.
1. Geef een titel voor de workflow en een optionele opmerking op. Klik op **[!UICONTROL Run]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigeer naar de map met middelen en controleer de tags om te controleren of uw elementen correct zijn gecodeerd. Zie [Slimme tags beheren](#manage-smart-tags-and-searches) voor meer informatie.

### Elementen labelen vanaf de tijdlijn {#tagging-assets-from-the-timeline}

1. Selecteer in de gebruikersinterface Middelen de map met elementen of specifieke elementen waarop u slimme tags wilt toepassen.
1. Open in de linkerbovenhoek de **[!UICONTROL Timeline]**.
1. Open handelingen onder aan de linkerzijbalk en klik op **[!UICONTROL Start Workflow]**.

   ![start_workflow](assets/start_workflow.png)

1. Selecteer de **[!UICONTROL DAM Smart Tag Assets]** workflow en geef een titel op voor de workflow.
1. Klik op **[!UICONTROL Start]**. De workflow past de labels toe op elementen. Navigeer naar de map met middelen en controleer de tags om te controleren of uw elementen correct zijn gecodeerd. Zie [Slimme tags beheren](#manage-smart-tags-and-searches) voor meer informatie.

>[!NOTE]
>
>In de volgende coderingscycli worden alleen de gewijzigde elementen opnieuw gecodeerd met nieuw opgeleide tags. Zelfs ongewijzigde elementen worden echter gecodeerd als de ruimte tussen de laatste en huidige coderingscycli voor de coderingsworkflow meer dan 24 uur bedraagt. Voor workflows met periodieke labels worden ongewijzigde elementen gecodeerd wanneer de tijdruimte langer is dan zes maanden.

### Geüploade elementen {#tag-uploaded-assets} labelen

Experience Manager kan de elementen die gebruikers uploaden naar DAM automatisch labelen. Hiertoe configureren beheerders een workflow om een beschikbare stap aan slimme-tagelementen toe te voegen. Zie [slimme tags inschakelen voor geüploade elementen](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets).

<!-- TBD: Text-based assets are automatically smart tagged. -->

## Slimme tags beheren en zoeken naar middelen {#manage-smart-tags-and-searches}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkelementen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags ook verfijnen door ervoor te zorgen dat uw elementen in de zoekresultaten voor de meest relevante tags worden weergegeven. In feite helpt dit de kans te verkleinen dat niet-verwante elementen in zoekresultaten worden weergegeven.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie ervan met betrekking tot een element te vergroten. Door een tag voor een element te promoten, vergroot u de kans dat het element in de zoekresultaten wordt weergegeven wanneer een zoekopdracht wordt uitgevoerd op basis van de desbetreffende tag.

De slimme tags van uw elementen reduceren:

1. Zoek in het veld Onderzoek naar elementen op basis van een tag.

1. Inspect de zoekresultaten om de elementen te identificeren die je niet relevant vindt voor je zoekopdracht.

1. Selecteer het element en selecteer ![Tags beheren pictogram](assets/do-not-localize/manage-tags-icon.png) op de werkbalk.

1. Controleer de tags op de pagina **[!UICONTROL Manage Tags]**. Als u niet wilt dat het element wordt doorzocht op basis van een specifieke tag, selecteert u de tag en selecteert u ![Pictogram Verwijderen](assets/do-not-localize/delete-icon.png) op de werkbalk. U kunt ook `X`-symbool naast het label selecteren.

1. Als u een hogere rangorde aan een tag wilt toewijzen, selecteert u de tag en selecteert u ![Promote icon](assets/do-not-localize/promote-icon.png) op de werkbalk. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]**.

1. Selecteer **[!UICONTROL Save]** en selecteer **[!UICONTROL OK]** om het [!UICONTROL Success] dialoogvenster te sluiten.

1. Navigeer naar de pagina [!UICONTROL Properties] voor het element. Let erop dat de tag die u hebt bevorderd een grote relevantie krijgt en daarom hoger wordt weergegeven in de zoekresultaten.

### AEM zoekresultaten begrijpen met slimme tags {#understandsearch}

Standaard combineert AEM zoekopdracht de zoektermen met een `AND`-component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, voegt u een extra `OR`-component toe om een zoekterm in de toegepaste slimme tags te zoeken. U kunt bijvoorbeeld zoeken naar `woman running`. Elementen met alleen het trefwoord `woman` of `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat is gelabeld met `woman` of `running` met behulp van slimme tags, wordt echter wel weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* elementen met de trefwoorden `woman` en `running` in de metagegevens.

* elementen die zijn gelabeld met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. overeenkomend met `woman running` in de verschillende metagegevensvelden.
1. overeenkomsten van `woman running` in slimme markeringen.
1. overeenkomende met `woman` of `running` in slimme tags.

### Beperkingen voor tags {#limitations}

Verbeterde slimme tags zijn gebaseerd op leermodellen van merkafbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de slimme tags heeft de volgende beperkingen:

* Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
* Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
* Tags worden ondersteund in de talen die Experience Manager ondersteunt. Zie [Opmerkingen bij de release Smart Content Service](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/smart-content-service-release-notes.html#languages) voor een lijst met talen.

<!-- TBD: Add limitations related to text-based assets. -->

Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u de opdracht Middelen zoeken (zoeken in volledige tekst). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!NOTE]
>
>Of u met slimme tags op uw tags kunt trainen en deze kunt toepassen op andere afbeeldingen, is afhankelijk van de kwaliteit van de afbeeldingen die u gebruikt voor training.
>Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

>[!MORELIKETHIS]
>
>* [Experience Manager voor slimme tags configureren](smart-tags-configuration.md)
>* [Begrijp hoe slimme tags u helpen elementen te beheren](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)
>* [Slimme tags toepassen op video-elementen](smart-tags-video-assets.md)

