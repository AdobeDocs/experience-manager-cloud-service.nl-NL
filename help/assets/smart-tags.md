---
title: Auto-markering activa met  [!DNL Adobe Sensei]  slimme dienst
description: Elementen labelen met een kunstmatig intelligente service die contextuele en beschrijvende bedrijfstags toepast.
feature: Smart Tags,Tagging
role: Admin,User
exl-id: a2abc48b-5586-421c-936b-ef4f896d78b7
source-git-commit: e253445d04889390ea9bf34df4ab14a9583d78aa
workflow-type: tm+mt
source-wordcount: '2398'
ht-degree: 0%

---

# Slimme tags voor AEM Assets {#using-smart-tags}

Organisaties beschikken over talrijke digitale middelen en dit aantal blijft snel groeien. Het zoeken naar een specifiek actief tussen zo&#39;n grote hoeveelheid gegevens vormt een belangrijke uitdaging. `metadata` en `tags` worden gebruikt om de doorzoekbaarheid van digitale elementen te verbeteren. Organisaties gebruiken woordenboeken die door taxonomie worden gecontroleerd in metagegevens van elementen. Deze bestaan typisch uit sleutelwoordlijsten die de werknemers, de partners, en de klanten algemeen gebruiken om naar digitale activa te verwijzen en de plaats te bepalen.

Slimme tags zijn trefwoorden die niet alleen in de tekst worden weergegeven, maar ook het element het beste beschrijven. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunnen ze gemakkelijk worden geïdentificeerd en opgehaald door middel van zoekopdrachten.

Woorden die alfabetisch in een woordenboek zijn gerangschikt, zijn bijvoorbeeld gemakkelijker te vinden dan willekeurig verspreide woorden. Tags zijn een soortgelijk doel. Het organiseert activa volgens bedrijfstaxonomie, die ervoor zorgt dat de meest relevante degenen in onderzoeksresultaten verschijnen. Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven bij het ontwerpen van een promotiecampagne. Of gebruikers nu &#39;runners&#39; of &#39;loopschoenen&#39; labelen, gebruikers hoeven zich geen zorgen te maken over typos, spellingvariaties of andere zoektermen. Slimme tags herkennen ze allemaal.

Op de achtergrond, gebruikt de functionaliteit het kunstmatig intelligente kader van [ Adobe Sensei ](https://business.adobe.com/products/sensei/adobe-sensei.html) automatisch Slimme Markeringen op geüploade activa-door gebrek-samen met tekst die aan de bedrijfstaxonomie wordt gericht.

## Vereisten en configuratie {#smart-tags-prereqs-config}

Slimme tags worden automatisch ingericht voor [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] en er is dus geen configuratie vereist.

## Workflow Slimme tags {#smart-tags-workflow}

[!DNL Adobe Sensei] Slim labelen met voeding maakt gebruik van kunstmatige intelligentiemodellen voor het analyseren van inhoud en het toevoegen van tags aan de elementen. Hierdoor neemt de tijd voor DAM-gebruikers af om hun klanten rijke ervaringen te bieden. De slimme Markeringen worden getoond in dalende orde van hun [ betrouwbaarheidsscore ](#confidence-score) in activa eigenschappen.

* **Op beeld-gebaseerde activa**
Voor afbeeldingen zijn de slimme tags gebaseerd op een visueel aspect. Afbeeldingen in veel indelingen worden gelabeld met behulp van services voor slimme inhoud. De slimme Markeringen worden toegepast op [ gesteunde dossiertypes ](#supported-file-formats) die vertoningen in formaat JPG en PNG produceren.

  <!-- ![Image Smart Tag](assets/image-smart-tag.png)-->

* **Op video-Gebaseerde activa**
Voor op video gebaseerde elementen is codering standaard ingeschakeld in [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] . Op dezelfde manier worden tags voor afbeeldingen en tekst automatisch gecodeerd voor video&#39;s wanneer u nieuwe video&#39;s uploadt of bestaande video&#39;s opnieuw verwerkt. [!DNL Adobe Sensei] genereert twee sets tags voor een video: een set komt overeen met objecten, scènes en kenmerken in die video, terwijl de andere set betrekking heeft op handelingen zoals drinken, uitvoeren en jogging. Controleer ook [ opt out video slimme het etiketteren ](#opt-out-video-smart-tagging).

* **Op tekst gebaseerde activa**
Voor ondersteunde elementen extraheert [!DNL Experience Manager] al de tekst, die vervolgens wordt geïndexeerd en wordt gebruikt om de elementen te zoeken. Slimme tags die op trefwoorden in de tekst zijn gebaseerd, bieden echter een toegewezen, gestructureerde en prioriteitszoekfacet. Deze laatste functie verbetert de detectie van elementen in vergelijking met een zoekindex.
Voor op tekst gebaseerde elementen is de effectiviteit van slimme tags niet afhankelijk van de hoeveelheid tekst in het element, maar van de relevante trefwoorden of entiteiten in de tekst van het element.

  ![ slim-markering-types ](assets/smart-tags-types.png)

Slimme tags worden geïmplementeerd in AEM Assets met behulp van de volgende workflow:

1. Maak of upload middelen in AEM. Er worden tags buiten het vak gegenereerd voor Assets op basis van afbeeldingen, video en tekst.

1. Als u vindt dat er geen specifieke tags worden gegenereerd, kunt u de tags van het afbeeldingstype dienovereenkomstig trainen. Verwijs naar [ Slimme opleiding van Markeringen ](#smart-tags-training.md).

## Ondersteunde bestandsindelingen voor slimme tags {#supported-file-formats}

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

## Middelen voorbereiden voor slimme tags buiten het vak

Wanneer u [ activa ](add-assets.md#upload-assets) aan [!DNL Adobe Experience Manager] als a [!DNL Cloud Service] uploadt, worden de geuploade activa verwerkt. Als de verwerking is voltooid, raadpleegt u het tabblad [!UICONTROL Basic] van de pagina Middelen [!UICONTROL Properties] . Slimme tags worden automatisch toegevoegd aan de elementen onder [!UICONTROL Smart Tags] . Asset microservices gebruikt [!DNL Adobe Sensei] om deze slimme tags te maken.

![ de Slimme Markeringen worden toegevoegd aan video&#39;s en gezien in Basis lusje van activaEigenschappen ](assets/smart-tags-added-to-videos.png)

<!--
The applied smart tags are sorted in descending order of [confidence score](#confidence-score), combined for object and action tags, within [!UICONTROL Smart Tags].
-->

>[!IMPORTANT]
>
>U wordt geadviseerd om deze automatisch geproduceerde markeringen te herzien om ervoor te zorgen dat zij aan uw merk en zijn waarden in overeenstemming zijn.

## Niet-gelabelde Assets in DAM {#smart-tag-existing-assets}

De bestaande of oudere elementen in DAM worden niet automatisch gemarkeerd met slimme tags. U moet ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/about-image-video-profiles.html?lang=en#adjusting-load) Assets opnieuw verwerken [ manueel om Slimme Markeringen voor hen te produceren. Als het proces is voltooid, navigeert u naar de [!UICONTROL Properties] -pagina van elk element in de map. De automatisch toegevoegde tags worden weergegeven in de sectie [!UICONTROL Smart Tags] op het tabblad [!UICONTROL Basic] . Deze toegepaste Slimme Markeringen worden gesorteerd in dalende orde van [ betrouwbaarheidsscore ](#confidence-score).

<!--
To smart tag assets, or folders (including subfolders) of assets that exist in assets repository, follow these steps:

1. Select the [!DNL Adobe Experience Manager] logo and then select assets from the [!UICONTROL Navigation] page.

1. Select [!UICONTROL Files] to display the Assets interface.

1. Navigate to the folder to which you want to apply Smart Tags.

1. Select the assets and click ![Reprocess assets icon](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Reprocess Assets] icon and select the [!UICONTROL Full Process] option.

![Reprocess assets to add tags to videos existing DAM repository](assets/reprocess.gif)-->

## Vertrouwensscore {#confidence-score}

De resultaten van uw middelenzoekopdracht worden gerangschikt op basis van de betrouwbaarheidsscores, die over het algemeen de zoekresultaten verbeteren en verder gaan dan wat een inspectie van de toegewezen labels van een element suggereert. Onnauwkeurige tags hebben vaak lage betrouwbaarheidsscores, zodat ze zelden boven aan de lijst Slimme tags voor elementen worden weergegeven.
<!--
[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] applies a minimum confidence threshold for object and action-smart tags to avoid having too many tags for each asset, which slows down indexing. 

The default threshold for action and object tags in [!DNL Adobe Experience Manager] for an image is 0.5 and for video it is 0.7 (should be value from 0 through 1). If some assets are not tagged by a specific tag, then it indicates that the algorithm is less than 70% confident in the predicted tags. The default threshold might not always be optimal for all the users. You can, therefore, change the confidence score value in OSGI configuration.

To add the confidence score OSGI configuration to the project deployed to [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] through [!DNL Cloud Manager]:

In the [!DNL Adobe Experience Manager] project (`ui.config` since Archetype 24, or previously `ui.apps`) the `config.author` OSGi configuration, include a config file named `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` with the following contents:

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```
-->

>[!NOTE]
>
>Handmatige tags krijgen een betrouwbaarheid van 100% (maximale betrouwbaarheid). Daarom als er activa met handmarkeringen zijn die de onderzoeksvraag aanpassen, worden zij getoond vóór Slimme Markeringen die de onderzoeksvraag aanpassen.

## Moderne slimme tags {#moderate-smart-tags}

Met [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] kunt u de slimme tags op de volgende manier curven:

* onjuiste tags verwijderen die zijn toegewezen aan uw merkelementen.

* U kunt zoekopdrachten op basis van tags verfijnen voor elementen door ervoor te zorgen dat uw element wordt weergegeven in zoekresultaten voor de meest relevante tags. Daardoor wordt de kans dat niet-verbonden activa in de zoekresultaten worden weergegeven, weggenomen.

* een hogere rangorde aan een tag toewijzen om de relevantie ervan met betrekking tot een element te vergroten. Door een tag voor een element te promoten, neemt de kans toe dat het specifieke element in de zoekresultaten wordt weergegeven wanneer een zoekopdracht op basis van die tag wordt uitgevoerd.

Meer over weten hoe te om de Slimme Markeringen voor activa te matigen, zie [ Slimme Markeringen ](smart-tags.md#manage-smart-tags-and-searches) leiden.

![ Gematigde video Slimme Markeringen ](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>Om het even welke markeringen die gebruikend de stappen in [ worden gematigd leiden Slimme Markeringen ](smart-tags.md#manage-smart-tags-and-searches) worden niet herinnerd bij herverwerking van de activa. De originele tagsets worden opnieuw weergegeven.

## Slimme tags beheren en zoeken naar middelen {#manage-smart-tags-and-searches}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkelementen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van labels naar elementen verfijnen door ervoor te zorgen dat uw elementen in de zoekresultaten voor de meest relevante tags worden weergegeven. In feite helpt dit de kans te verkleinen dat niet-verwante elementen in zoekresultaten worden weergegeven.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie van de tag voor het element te vergroten. Door een tag voor een element te promoten, vergroot u de kans dat het element in de zoekresultaten wordt weergegeven wanneer een zoekopdracht wordt uitgevoerd op basis van de desbetreffende tag.

Slimme tags toepassen op uw digitale middelen:

1. Zoek in het zoekveld naar digitale elementen op basis van een tag.

1. Om de digitale activa te identificeren die u niet relevant voor uw onderzoek vindt, inspecteer de onderzoeksresultaten.

1. Selecteer een activa, en selecteer dan ![ beheer markeringen pictogram ](assets/do-not-localize/manage-tags-icon.png) van de toolbar.

1. Controleer de tags op de pagina **[!UICONTROL Manage Tags]** . Als u niet de activa wilt worden gezocht die op een specifieke markering worden gebaseerd, dan selecteer de markering en selecteer ![ pictogram van de Schrapping ](assets/do-not-localize/delete-icon.svg) van de toolbar. Alternatief, selecteer ![ dicht pictogram ](assets/do-not-localize/close_icon.svg) naast het etiket.

1. Om een hogere rangorde aan een markering toe te wijzen, selecteer de markering en selecteer ![ bevorderen pictogram ](assets/do-not-localize/promote-icon.svg) van de toolbar. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]** .

1. Selecteer **[!UICONTROL Save]** en selecteer vervolgens **[!UICONTROL OK]** om het dialoogvenster [!UICONTROL Success] te sluiten.

1. Navigeer naar de pagina [!UICONTROL Properties] voor het element. Let erop dat de tag die u hebt bevorderd een grote relevantie krijgt en daarom hoger wordt weergegeven in de zoekresultaten.

### [!DNL Experience Manager] Zoekresultaten begrijpen met slimme tags {#understand-search}

Standaard combineert [!DNL Experience Manager] de zoektermen met een `AND` - of `OR` -component om een zoekterm te zoeken in de toegepaste slimme tags. Dit standaardgedrag verandert niet als u Slimme tags gebruikt. Zoek bijvoorbeeld naar `woman running` . Assets met alleen het trefwoord `woman` of alleen het trefwoord `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. In een dergelijke zoekopdracht wordt echter een element weergegeven dat is gelabeld met `woman` of `running` met slimme tags. De zoekresultaten zijn dus een combinatie van:

* Assets met `woman` en `running` trefwoorden in de metagegevens.

* Assets smart wordt getagd met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. komt overeen met `woman running` in de verschillende metagegevensvelden.
1. overeenkomende met `woman running` in slimme tags.
1. overeenkomende met `woman` of `running` in slimme tags.

## Slimme tags uitschakelen {#opt-out-smart-tagging}

Wanneer de automatische codering van elementen parallel loopt met andere elementverwerkingstaken, zoals het maken van miniaturen en het uitnemen van metagegevens, kan dit tijdrovend zijn. Als u de verwerking van elementen wilt versnellen, kunt u ervoor kiezen geen slimme tags toe te wijzen bij het uploaden naar een map. U kunt het genereren van geautomatiseerde slimme tags uitschakelen voor elementen die naar een specifieke map zijn geüpload:

1. Open [!UICONTROL Asset Processing] in de map [!UICONTROL Properties] .
1. In het menu [!UICONTROL Smart Tags for Videos] is de optie [!UICONTROL Inherited] bijvoorbeeld standaard geselecteerd en wordt slimme tag voor video ingeschakeld.

   Wanneer de optie [!UICONTROL Inherited] is geselecteerd, is het overgeërfde mappad ook zichtbaar samen met de informatie of het is ingesteld op [!UICONTROL Enable] of [!UICONTROL Disable] .

   ![ maak slimme het etiketteren ](assets/disable-tagging.png) onbruikbaar

1. Selecteer [!UICONTROL Disable] om de optie voor het niet langer gebruiken van slimme tags die naar de map zijn geüpload.

1. U kunt slimme tags ook uitschakelen voor [!UICONTROL Smart Tags for Text] , [!UICONTROL Smart Tags for Image] en [!UICONTROL Color Tags for Images] .

>[!IMPORTANT]
>
>Als u er bij het uploaden voor hebt gekozen om geen tags toe te wijzen aan een map en u wilt de map na het uploaden een slimme tag toewijzen, kiest u **[!UICONTROL Enable Smart Tags]** op het tabblad [!UICONTROL Asset Processing] van de map [!UICONTROL Properties] en gebruikt u [[!UICONTROL Reprocess Asset] optie ](#smart-tag-existing-assets) om slimme tags toe te voegen aan de elementen.

<!--
## Benefits of Smart Tags to your assets {#benefits-of-smart-tags}

Following are the benefits of using Smart Tags in your AEM Assets:
*  Makes an asset searchable.
*  Smart Tags are generated automatically to your assets, thus, it minimizes your effort to perform tagging manually.
*  It allows the usage of the same vocabulary, tag structure, and taxonomy so that you need not to worry about tagging if by chance you miss tagging at first.
*  Whether you are tagging "runners" or "running" shoes, you do not need to worry about typos, wrong spellings, or alternative search terms as Smart Tags know it already!
*  Helps your assets to become organized and categorized.
-->

## Detectie van inhoud verbeteren met door AI gegenereerde metagegevens {#ai-smart-tags}

In plaats van handmatig in te voeren, wijst AI automatisch beschrijvende tags toe aan digitale elementen. Deze door AI gegenereerde tags verbeteren de kwaliteit van de metagegevens, waardoor de elementen gemakkelijker kunnen worden doorzocht, gecategoriseerd en aanbevolen. Deze aanpak verbetert niet alleen de efficiëntie door handmatige codering te elimineren, maar zorgt ook voor consistentie en schaalbaarheid op grote volumes digitale inhoud. Als het element bijvoorbeeld een afbeelding is, kan AI objecten, scènes, emoties of zelfs merklogo&#39;s in het element herkennen en relevante tags genereren, zoals &quot;zonsondergang&quot;, &quot;strand&quot;, &quot;vakantie&quot; of &quot;glimlachen&quot;. Door AI gegenereerde inhoud kan het zoeken naar elementen verbeteren door gebruik te maken van zowel semantische als lexicale zoektechnieken. Zie meer [ Onderzoek Assets ](search-assets.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![ Verbeterde slimme markeringen ](assets/enhanced-smart-tags1.png)

### Hoe kan ik door AI gegenereerde metagegevens inschakelen? {#enable-ai-generated-metadata}

Door AI gegenereerde metagegevens inschakelen:

* Minimaal vereiste AEM-releaseversie is `20626` .

* U moet een GenAI Rider-overeenkomst ondertekenen. Neem voor meer informatie contact op met uw Adobe-vertegenwoordiger.

  >[!IMPORTANT]
  >
  > De door AI gegenereerde titel van een element wordt alleen op de Asset-kaart weergegeven wanneer u de titel van het element niet hebt gedefinieerd. De titel van het element die u hebt opgegeven, wordt niet overschreven.

### Door AI gegenereerde metagegevens gebruiken {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Voer de volgende stappen uit om de verbeterde functie Slimme tags te gebruiken:

1. Ga in de interface [!DNL Experience Manager] naar de gewenste map en klik op **[!UICONTROL Add Assets]** . <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> De compatibele indelingen voor afbeeldingsbestanden zijn `png` , `jpg` , `jpeg` , `psd` , `tiff` , `gif` , `webp` , `crw` , `cr2` , `3fr` , `nef` , `arw` en `bmp` .

1. Wacht tot het net geüploade element is verwerkt. Ga vervolgens naar de eigenschappen van de elementen.

1. Ga naar tabblad **[!UICONTROL AI-Generated]** . Als de [!DNL Experience Manager] -versie incompatibel is of niet wordt bijgewerkt, is dit tabblad niet zichtbaar. De volgende velden zijn beschikbaar:

   * **[!UICONTROL Generated title]:** de titel verstrekt een duidelijke en beknopte titel die het kernidee van een geüploade activa vangt, die het gemakkelijk maken in een blik te begrijpen. Als u een element toevoegt en u een titel opgeeft (in `dc:title` ), wordt deze weergegeven in de bladerweergave met elementen. Als deze optie leeg blijft, wordt automatisch een door AI gegenereerde titel toegewezen.
   * **[!UICONTROL Generated description]:** De beschrijving geeft een korte maar informatieve samenvatting van wat de activa over is, die gebruikers en onderzoeksmodule helpen om zijn relevantie snel te begrijpen.
   * **[!UICONTROL Generated keywords]:** De trefwoorden zijn doeltermen die de hoofdthema&#39;s van een element vertegenwoordigen en die u helpen bij het labelen en filteren van inhoud.

1. [ Facultatief ] u kunt extra markeringen toevoegen of uw creëren als u om het even welke relevante markeringen voelt ontbreken. U doet dit door uw tags in het veld **[!UICONTROL Generated keywords]** te schrijven en op **[!UICONTROL Save]** te klikken.

## Beperkingen en aanbevolen procedures voor slimme tags {#limitations-best-practices-smart-tags}

Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de slimme tags heeft de volgende beperkingen:

* Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne of standaard passend overhemden.
* Kan geen tags identificeren op basis van kleine patronen of delen van een afbeelding. Bijvoorbeeld logo&#39;s op hemden.
* De tags die niet worden verwerkt, hebben betrekking op:

   * Niet-visuele, abstracte aspecten. Bijvoorbeeld het jaar of het seizoen waarin een product wordt uitgebracht, de stemming of emotie die door een afbeelding wordt opgewekt en een subjectieve connotatie van een video.
   * Fijne visuele verschillen in producten zoals overhemden met en zonder halsbanden of op producten ingebedde logo&#39;s van kleine producten.

* Alleen video&#39;s die kleiner zijn dan 300 MB, worden automatisch gecodeerd. De service [!DNL Adobe Sensei] slaat videobestanden over die groter zijn.
* Als u bestanden met slimme tags wilt zoeken (normaal of uitgebreid), gebruikt u de zoekopdracht [!DNL Assets] (zoeken in volledige tekst). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.
* In vergelijking met algemene tags zijn de elementen die zijn gecodeerd met bedrijfstaxonomie gemakkelijker te identificeren en op te halen door zoekopdrachten op basis van tags.

## Veelgestelde vragen{#faq-smart-tags}

+++**Hoe verbeteren de Slimme Markeringen onderzoekservaring van een activa?**

[!DNL Adobe] Sensei labelt de elementen automatisch als u ze uploadt. Het geautomatiseerde proces wordt zo snel op de achtergrond uitgevoerd dat er na een paar seconden tags aan uw elementen worden toegevoegd wanneer het uploaden is voltooid.

+++

+++**wat gebeurt als de Slimme lijst van Markeringen onnauwkeurig of het tonen van ongewenste markering is?**

Een onjuiste of ongewenste tag kan uit de lijst worden verwijderd. Als autohandelaar wilt u bijvoorbeeld de tag &#39;beschadigd&#39; uit de lijst verwijderen.

+++

+++**hoe u activa kunt voorrang geven die zelfde markeringen bevatten?**

Ja, u kunt aan activa voorrang geven die de zelfde markeringen bevatten. U kunt een tag opwaarderen in de lijst Slimme tags van een element om prioriteiten toe te passen. Door een tag te promoten, kunt u de prioriteit bepalen van de afbeeldingen in de zoekresultaten voor die tag.

+++

+++**is de toepassing van Slimme Markeringen beperkt tot een bepaalde omslag?**

Slimme tags kunnen worden geconfigureerd en worden toegepast op elke map in DAM.

+++

+++**Hoe kan ik weten dat het etiketteren opleiding vereist?**

Verwijs naar [ het Bepalen van het vereiste van de Slimme opleiding van Markeringen ](#smart-tags-training.md#smart-tag-training-requirement).

+++

+++**wat zijn de gesteunde dossierformaten voor het etiketteren van activa?**

Verwijs naar [ Gesteunde dossierformaten ](#supported-file-formats).

+++

+++**waarin de taal slimme markeringen worden geproduceerd?**

Slimme tags worden alleen in de Engelse taal gegenereerd. Ze kunnen naar andere talen worden vertaald door het volledige middel, inclusief metagegevens, te vertalen.

+++

+++**ik wil geen Slimme Tags meer gebruiken.**

U kunt [ kiezen uit Slimme Tags ](#opt-out-smart-tagging) wanneer u wilt beëindigen.

+++
