---
title: Hoe kunt u slimme tags toevoegen aan elementen in AEM?
description: Voeg slimme tags toe aan elementen in AEM met een kunstmatige intelligente service die contextafhankelijke en beschrijvende bedrijfstags toepast.
contentOwner: AG
feature: Smart Tags
role: Admin, User
exl-id: a2abc48b-5586-421c-936b-ef4f896d78b7
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 3%

---


# Slimme tags toevoegen aan elementen in AEM {#smart-tags-assets-aem}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/enhanced-smart-tags.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar hun digitale activa te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u de elementen gemakkelijk herkennen en ophalen in zoekopdrachten.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren op basis van bedrijfstaxonomie de activa met de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen. Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer er wordt gezocht naar een promotiecampagne.

In de achtergrond, gebruikt de functionaliteit het kunstmatig intelligente kader van [ Adobe Sensei ](https://business.adobe.com/why-adobe/experience-cloud-artificial-intelligence.html) om zijn algoritme van de beelderkenning op uw markeringsstructuur en bedrijftaxonomie te trainen. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen. AEM past automatisch slimme tags toe op geüploade elementen.

<!-- TBD: Create a flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

## Ondersteunde elementtypen voor slimme tags in AEM {#smart-tags-supported-file-formats}

U kunt de volgende typen elementen labelen:

* **Beelden**: De beelden in vele formaten worden geëtiketteerd gebruikend de de slimme inhoudsdiensten van Adobe Sensei. U [ creeert een opleidingsmodel ](#train-model) en dan worden de geuploade beelden automatisch geëtiketteerd. Slimme tags worden toegepast op de ondersteunde bestandstypen die uitvoeringen genereren in JPG-indeling en PNG-indeling.
* **Op tekst gebaseerde activa**: [!DNL Experience Manager Assets] auto-markeringen de gesteunde op tekst-gebaseerde activa wanneer geupload.
* **Video activa**: Het video etiketteren wordt toegelaten door gebrek in [!DNL Adobe Experience Manager] als [!DNL Cloud Service]. [ de Video&#39;s zijn auto-geëtiketteerd ](/help/assets/smart-tags-video-assets.md) wanneer u nieuwe video&#39;s uploadt of bestaande degenen opnieuw verwerkt.

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

* [ begrijp markeringsmodellen en richtlijnen ](#understand-tag-models-guidelines).
* [ Trein het model ](#train-model).
* [ markering uw digitale activa ](#tag-assets).
* [ beheer de markeringen en de onderzoeken ](#manage-smart-tags-and-searches).

## Leer labelmodellen en -richtlijnen {#understand-tag-models-guidelines}

Een labelmodel is een groep gerelateerde tags die zijn gekoppeld aan verschillende visuele aspecten van afbeeldingen die worden gecodeerd. Tags hebben betrekking op de duidelijk verschillende visuele aspecten van afbeeldingen, zodat de tags, wanneer deze worden toegepast, helpen bij het zoeken naar specifieke typen afbeeldingen. Een schoenenverzameling kan bijvoorbeeld verschillende tags hebben, maar alle tags zijn gerelateerd aan schoenen en kunnen tot hetzelfde tagmodel behoren. Wanneer u de labels toepast, kunt u verschillende soorten schoenen vinden, bijvoorbeeld op basis van ontwerp of gebruik. Als u de inhoudsweergave van een trainingsmodel in [!DNL Experience Manager] wilt begrijpen, visualiseert u een trainingsmodel als een entiteit op hoofdniveau die bestaat uit een groep handmatig toegevoegde tags en voorbeeldafbeeldingen voor elke tag. Elke tag kan uitsluitend op een afbeelding worden toegepast.

Voordat u een tagmodel maakt en de service traint, moet u een set unieke tags identificeren die de objecten in de afbeeldingen het beste beschrijven in de context van uw bedrijf. Zorg ervoor dat de activa in uw gebogen reeks met [ de opleidingsrichtlijnen ](#training-guidelines) in overeenstemming zijn.

### Richtlijnen voor training {#training-guidelines}

Zorg ervoor dat de afbeeldingen in de trainingsset voldoen aan de volgende richtlijnen:

**Aantal en grootte:** minimum 10 beelden en maximum 50 beelden per markering.

**Samenhang**: Zorg ervoor dat de beelden voor een markering visueel gelijkaardig zijn. U kunt de tags met betrekking tot dezelfde visuele aspecten (zoals hetzelfde type objecten in een afbeelding) het beste aan één tagmodel toevoegen. Het is bijvoorbeeld geen goed idee om deze afbeeldingen als `my-party` (voor training) te labelen, omdat ze er anders uitzien.

![ Illustratieve beelden om de richtlijnen voor opleiding ](assets/do-not-localize/coherence.png) te illustreren

**Dekking**: Er zou voldoende verscheidenheid in de beelden in de opleiding moeten zijn. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat [!DNL Experience Manager] leert focussen op de juiste dingen. Als u dezelfde tag toepast op visueel ongelijke afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen. Bijvoorbeeld, voor de markering *model-onderstel*, omvat meer opleidingsbeelden gelijkend op het benadrukte beeld hieronder voor de dienst om gelijkaardige beelden nauwkeuriger tijdens het etiketteren te identificeren.

![ Illustratieve beelden om de richtlijnen voor opleiding ](assets/do-not-localize/coverage_1.png) te illustreren

**Vervorming/belemmering**: De de diensttreinen beter op beelden die minder afleiding (duidelijke achtergronden, niet verwante accompanimenten, zoals voorwerpen/personen met het belangrijkste onderwerp) hebben. Bijvoorbeeld, voor de markering *casual-shoe*, is het tweede beeld geen goede opleidingskandidaat.

![ Illustratieve beelden om de richtlijnen voor opleiding ](assets/do-not-localize/distraction.png) te illustreren

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Als het bijvoorbeeld gaat om tags zoals *regenjas* en *modelweergave*, voegt u beide tags toe aan de desbetreffende asset voordat u dit opneemt voor training.

![ Illustratieve beelden om de richtlijnen voor opleiding ](assets/do-not-localize/completeness.png) te illustreren

**Aantal markeringen**: de Adobe adviseert dat u een model gebruikend minstens twee verschillende markeringen en minstens tien verschillende beelden voor elke markering opleidt. Voeg in één tagmodel niet meer dan 50 tags toe.

**Aantal voorbeelden**: Voor elke markering, voeg minstens tien voorbeelden toe. De Adobe beveelt echter ongeveer 30 voorbeelden aan. Er worden maximaal 50 voorbeelden per tag ondersteund.

**verhindert valse positieven en conflicten**: de Adobe adviseert het creëren van één enkel markeringsmodel voor één enkel visueel aspect. Structuur de labelmodellen zodanig dat overlappende codes tussen de modellen worden voorkomen. Gebruik bijvoorbeeld geen gemeenschappelijke tags, zoals `sneakers` , in twee verschillende modelnamen voor tags `shoes` en `footwear` . Het trainingsproces overschrijft het ene getrainde tagmodel met het andere voor een algemeen trefwoord.

**Voorbeelden**: Sommige meer voorbeelden voor begeleiding zijn:

* Maak een tagmodel dat alleen het volgende bevat:

   * De labels die betrekking hebben op automodellen.
   * De labels hadden betrekking op hoesjes voor volwassenen en kinderen.

* Niet maken,

   * Een labelmodel dat automodellen bevat die in 2019 en 2020 zijn uitgebracht.
   * Meerdere labelmodellen met dezelfde paar automodellen.

**Beelden die worden gebruikt om** te trainen: U kunt de zelfde beelden gebruiken om verschillende markeringsmodellen te trainen. Koppel een afbeelding echter niet aan meerdere tags in een labelmodel. U kunt dezelfde afbeelding labelen met verschillende tags die bij verschillende labelmodellen horen.

U kunt de training niet ongedaan maken. Aan de hand van de bovenstaande richtlijnen kunt u goede afbeeldingen kiezen om te trainen.

## Het model trainen voor uw douanetags {#train-model}

Voer de volgende stappen uit om een model voor uw bedrijfsspecifieke tags te maken en op te leiden:

1. Maak de benodigde labels en de juiste codestructuur. Upload de relevante afbeeldingen in de DAM-opslagplaats.
1. Open **[!UICONTROL Assets]** > **[!UICONTROL Smart Tag Training]** in de [!DNL Experience Manager] -gebruikersinterface.
1. Klik op **[!UICONTROL Create]**. Geef een waarde op **[!UICONTROL Title]** , **[!UICONTROL Description]** .
1. Klik op het mappictogram in het veld **[!UICONTROL Tags]** . Er wordt een pop-upvenster geopend.
1. Zoek of selecteer de juiste tags van de bestaande tags in `cq-tags` die u aan het model wilt toevoegen. Klik op **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >U kunt de codestructuur in oplopende of aflopende volgorde sorteren op basis van de datum **[!UICONTROL Name]** (alfabetische volgorde), **[!UICONTROL Created]** date of **[!UICONTROL Modified]** .


1. Klik in het dialoogvenster **[!UICONTROL Select Assets]** op **[!UICONTROL Add Assets]** voor elke tag. Zoek in de DAM-opslagplaats of blader door de opslagplaats om ten minste 10 en ten hoogste 50 afbeeldingen te selecteren. Selecteer elementen en niet de map. Klik op **[!UICONTROL Select]** nadat u de afbeeldingen hebt geselecteerd.

   ![ de opleidingsstatus van de Mening ](assets/smart-tags-training-status.png)

1. Als u een voorvertoning van de miniaturen van de geselecteerde afbeeldingen wilt weergeven, klikt u op de accordeon vóór een tag. U kunt de selectie wijzigen door op **[!UICONTROL Add Assets]** te klikken. Klik op **[!UICONTROL Submit]** als u tevreden bent met de selectie. In de gebruikersinterface wordt onder aan de pagina een melding weergegeven dat de training wordt gestart.
1. Controleer de status van de training in de kolom **[!UICONTROL Status]** voor elk tagmodel. Mogelijke statussen zijn [!UICONTROL Pending] , [!UICONTROL Trained] en [!UICONTROL Failed] .

![ Werkschema om het etiketteren model voor Slimme Markeringen te trainen ](assets/smart-tag-model-training-flow.png)

*Cijfer: Stappen van het opleidingswerkschema om het etiketteren model te trainen.*

### Trainingsstatus en rapport weergeven {#training-status}

Als u wilt controleren of de service Slimme tags is opgeleid voor uw tags in de trainingsset met elementen, raadpleegt u het workflowrapport voor training in de rapportconsole.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]** .
1. Klik op **[!UICONTROL Create]** op de pagina **[!UICONTROL Asset Reports]** .
1. Selecteer het rapport **[!UICONTROL Smart Tags Training]** en klik vervolgens op **[!UICONTROL Next]** op de werkbalk.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk om het rapport weer te geven.
1. Bekijk de details van het rapport. Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de service Slimme tags is getraind voor de tag. Gele kleur geeft aan dat de service gedeeltelijk is opgeleid voor een bepaalde tag. Als u de service volledig wilt trainen voor een tag, voegt u meer afbeeldingen met de desbetreffende tag toe en voert u de trainingsworkflow uit. Als dit rapport uw tags niet bevat, voert u de trainingsworkflow opnieuw uit voor deze tags.Tags
1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een spreadsheet.

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

Alle typen ondersteunde elementen worden automatisch gelabeld door [!DNL Experience Manager Assets] wanneer ze worden geüpload. Tags worden standaard ingeschakeld en werkt. AEM past de juiste slimme tags toe in bijna real-time. <!-- TBD: You can also apply the tagging workflow on-demand. The workflow applies to both, assets and folders. -->

* Voor afbeeldingen en video&#39;s zijn de slimme tags gebaseerd op een visueel aspect.

* Voor op tekst gebaseerde elementen is de effectiviteit van slimme tags niet afhankelijk van de hoeveelheid tekst in het element, maar van de relevante trefwoorden of entiteiten in de tekst van het element. Voor op tekst gebaseerde elementen zijn de slimme tags de trefwoorden die in de tekst worden weergegeven, maar de trefwoorden die het element het beste beschrijven. Voor ondersteunde elementen extraheert [!DNL Experience Manager] al de tekst, die vervolgens wordt geïndexeerd en wordt gebruikt om de elementen te zoeken. Slimme tags die op trefwoorden in de tekst zijn gebaseerd, bieden echter een toegewezen, gestructureerde en prioriteitszoekfacet. Deze laatste functie verbetert de detectie van elementen in vergelijking met een zoekindex.

## Slimme tags beheren en zoeken naar middelen {#manage-smart-tags-and-searches}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkelementen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags ook verfijnen door ervoor te zorgen dat uw elementen in de zoekresultaten voor de meest relevante tags worden weergegeven. In feite helpt dit de kans te verkleinen dat niet-verwante elementen in zoekresultaten worden weergegeven.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie van de tag voor het element te vergroten. Door een tag voor een element te promoten, vergroot u de kans dat het element in de zoekresultaten wordt weergegeven wanneer een zoekopdracht wordt uitgevoerd op basis van de desbetreffende tag.

Slimme tags toepassen op uw digitale elementen:

1. Zoek in het zoekveld naar digitale elementen op basis van een tag.

1. Om de digitale activa te identificeren die u niet relevant voor uw onderzoek vindt, inspecteer de onderzoeksresultaten.

1. Selecteer een activa, en selecteer dan ![ beheer markeringen pictogram ](assets/do-not-localize/manage-tags-icon.png) van de toolbar.

1. Controleer de tags op de pagina **[!UICONTROL Manage Tags]** . Als u niet de activa wilt worden gezocht die op een specifieke markering worden gebaseerd, dan selecteer de markering en selecteer ![ pictogram van de Schrapping ](assets/do-not-localize/delete-icon.png) van de toolbar. U kunt ook het symbool `X` naast het label selecteren.

1. Om een hogere rangorde aan een markering toe te wijzen, selecteer de markering en selecteer ![ bevorderen pictogram ](assets/do-not-localize/promote-icon.png) van de toolbar. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]** .

1. Selecteer **[!UICONTROL Save]** en selecteer vervolgens **[!UICONTROL OK]** om het dialoogvenster [!UICONTROL Success] te sluiten.

1. Navigeer naar de pagina [!UICONTROL Properties] voor het element. Let erop dat de tag die u hebt bevorderd een grote relevantie krijgt en daarom hoger wordt weergegeven in de zoekresultaten.

### [!DNL Experience Manager] Zoekresultaten met slimme tags begrijpen {#understand-search}

Standaard worden in [!DNL Experience Manager] zoektermen gecombineerd met een `AND` -component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Met slimme tags voegt u een `OR` -component toe om een zoekterm in de toegepaste slimme tags te zoeken. Zoek bijvoorbeeld naar `woman running` . Assets met alleen het trefwoord `woman` of alleen het trefwoord `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. In een dergelijke zoekopdracht wordt echter een element weergegeven dat is gelabeld met `woman` of `running` met slimme tags. De zoekresultaten zijn dus een combinatie van:

* Assets met `woman` en `running` trefwoorden in de metagegevens.

* Assets smart wordt getagd met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. komt overeen met `woman running` in de verschillende metagegevensvelden.
1. overeenkomende met `woman running` in slimme tags.
1. overeenkomende met `woman` of van `running` in slimme tags.

## Beperkingen en beste praktijken op het gebied van tags {#limitations}

Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de slimme tags heeft de volgende beperkingen:

* Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne of standaard passend overhemden.
* Kan geen tags identificeren op basis van kleine patronen of delen van een afbeelding. Bijvoorbeeld logo&#39;s op hemden.
* Tags worden ondersteund in de talen die door [!DNL Experience Manager] worden ondersteund.
* De tags die niet worden verwerkt, hebben betrekking op:

   * Niet-visuele, abstracte aspecten. Bijvoorbeeld het jaar of het seizoen waarin een product wordt uitgebracht, de sfeer van of de emotie die door een beeld wordt opgeroepen, en een subjectieve connotatie van een video.
   * Fijne visuele verschillen in producten zoals overhemden met en zonder halsbanden of op producten ingebedde logo&#39;s van kleine producten.

Gebruik de meest geschikte afbeeldingen om het model op te leiden. De training kan niet worden teruggezet of het trainingsmodel kan niet worden verwijderd. De nauwkeurigheid van de tags is afhankelijk van de huidige training, dus doe dit zorgvuldig.

<!-- TBD: Add limitations related to text files. -->

Als u bestanden met slimme tags wilt zoeken (normaal of uitgebreid), gebruikt u de zoekopdracht [!DNL Assets] (zoeken in volledige tekst). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!NOTE]
>
>Of u met slimme tags op uw tags kunt trainen en deze kunt toepassen op andere afbeeldingen, is afhankelijk van de kwaliteit van de afbeeldingen die u gebruikt voor training.
>Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

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

>[!MORELIKETHIS]
>
>* [ Begrijp hoe de slimme markeringen helpen uw digitale dossiers beheren ](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)
>* [ Gebruik Slimme Markeringen voor video&#39;s ](smart-tags-video-assets.md)
