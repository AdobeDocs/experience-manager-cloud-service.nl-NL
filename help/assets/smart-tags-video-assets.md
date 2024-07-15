---
title: Slimme tag toewijzen aan video-elementen
description: Experience Manager voegt contextafhankelijke en beschrijvende slimme tags automatisch toe aan video's met  [!DNL Adobe Sensei] .
feature: Smart Tags
role: Admin, User
exl-id: b59043c5-5df3-49a7-b4fc-da34c03649d7
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---

# Slimme tag toewijzen aan video-elementen {#video-smart-tags}

De groeiende behoefte aan nieuwe inhoud vraagt om minder handmatige inspanningen om op korte termijn aantrekkelijke digitale ervaringen te bieden. [!DNL Adobe Experience Manager] als [!DNL Cloud Service] ondersteunt automatische labeling van video-elementen met behulp van kunstmatige intelligentie. Het kan tijdrovend zijn om de video&#39;s handmatig te labelen. Intelligente tags voor video&#39;s die door [!DNL Adobe Sensei] worden gebruikt, maken echter gebruik van kunstmatige intelligentiemodellen om video-inhoud te analyseren en tags toe te voegen aan de video-elementen. Hierdoor verkort u tijd voor DAM-gebruikers om hun klanten rijke ervaringen te bieden. De leerservice voor computers van Adobe genereert twee sets tags voor een video. De ene set komt weliswaar overeen met objecten, scènes en kenmerken in die video, maar de andere set heeft betrekking op handelingen zoals drinken, lopen en jogging.

Het coderen van video&#39;s is standaard ingeschakeld in [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] . Nochtans, kunt u [ opt-out van video het slimme etiketteren ](#opt-out-video-smart-tagging) op een omslag. Video&#39;s worden automatisch van tags voorzien wanneer u nieuwe video&#39;s uploadt of bestaande video&#39;s opnieuw verwerkt. [!DNL Experience Manager] maakt ook de miniaturen en extraheert de metagegevens van de videobestanden. De slimme markeringen worden getoond in dalende orde van hun [ betrouwbaarheidsscore ](#confidence-score-video-tag) in activa [!UICONTROL Properties].

## Slimme tags toepassen op video&#39;s tijdens het uploaden {#smart-tag-assets-on-ingestion}

Wanneer u [ videoactiva ](add-assets.md#upload-assets) aan [!DNL Adobe Experience Manager] als a [!DNL Cloud Service] uploadt, worden de video&#39;s verwerkt. Als de verwerking is voltooid, raadpleegt u het tabblad [!UICONTROL Basic] van de pagina Middelen [!UICONTROL Properties] . Slimme tags worden automatisch onder [!UICONTROL Smart Tags] aan de video toegevoegd. Asset microservices gebruikt [!DNL Adobe Sensei] om deze slimme tags te maken.

![ de Slimme Markeringen worden toegevoegd aan video&#39;s en gezien in Basis lusje van activaEigenschappen ](assets/smart-tags-added-to-videos.png)

De toegepaste slimme markeringen worden gesorteerd in dalende orde van [ betrouwbaarheidsscore ](#confidence-score-video-tag), die voor voorwerp en actietags, binnen [!UICONTROL Smart Tags] wordt gecombineerd.

>[!IMPORTANT]
>
>U wordt geadviseerd om deze automatisch geproduceerde markeringen te herzien om ervoor te zorgen dat zij aan uw merk en zijn waarden in overeenstemming zijn.

## Bestaande video&#39;s slim labelen in DAM {#smart-tag-existing-videos}

De bestaande video-elementen in DAM worden niet automatisch gecodeerd als slimme tags. U moet [!UICONTROL Reprocess Assets] handmatig gebruiken om slimme tags voor deze tags te genereren.

Voer de volgende stappen uit om slimme tags toe te wijzen aan video-elementen of mappen (inclusief submappen) van elementen die al in de opslagplaats voor elementen bestaan:

1. Selecteer het logo [!DNL Adobe Experience Manager] en selecteer vervolgens elementen op de pagina [!UICONTROL Navigation] .

1. Selecteer [!UICONTROL Files] om de Assets-interface weer te geven.

1. Ga naar de map waarop u slimme tags wilt toepassen.

1. Selecteer de volledige map of specifieke video-elementen.

1. Selecteer ![ opnieuw verwerken activa pictogram ](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Reprocess Assets] pictogram en selecteer de [!UICONTROL Full Process] optie.

<!-- TBD: Limit size -->

![ herproces activa om markeringen aan video&#39;s toe te voegen bestaande bewaarplaats DAM ](assets/reprocess.gif)

Wanneer het proces is voltooid, navigeert u naar de pagina [!UICONTROL Properties] van elk video-element in de map. De automatisch toegevoegde tags worden weergegeven in de sectie [!UICONTROL Smart Tags] op het tabblad [!UICONTROL Basic] . Deze toegepaste slimme markeringen worden gesorteerd in dalende orde van [ betrouwbaarheidsscore ](#confidence-score-video-tag).

## Zoeken naar gelabelde video&#39;s {#search-smart-tagged-videos}

Om naar de videoactiva te zoeken die op de auto geproduceerde slimme markeringen worden gebaseerd, gebruik [ Onderzoek ](search-assets.md#search-assets-in-aem):

1. Selecteer het onderzoekspictogram ![ onderzoekspictogram ](assets/do-not-localize/search_icon.png) om het gebied van het Onderzoek te tonen.

1. Geef in het veld Onderzoek een tag op die u niet expliciet aan een video hebt toegevoegd.

1. Zoeken op basis van de tag.

De zoekresultaten geven de video-elementen weer op basis van de tag die u hebt opgegeven.

Uw zoekresultaten zijn een combinatie van video-elementen met gezochte trefwoorden in de metagegevens en de video-elementen die zijn gelabeld met de gezochte trefwoorden. De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden echter eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. Voor meer informatie, zie [  [!DNL Experience Manager]  onderzoeksresultaten met slimme markeringen ](smart-tags.md#understand-search) begrijpen.

## Slimme videolabels modereren {#moderate-video-smart-tags}

Met [!DNL Adobe Experience Manager] kunt u slimme tags toepassen op:

* Verwijder onjuiste tags die zijn toegewezen aan uw merkvideo&#39;s.

* U kunt zoekopdrachten op basis van tags verfijnen voor video&#39;s door ervoor te zorgen dat de video wordt weergegeven in de zoekresultaten voor de meest relevante tags. Hierdoor wordt de kans dat niet-verwante video&#39;s in zoekresultaten worden weergegeven, weggenomen.

* U kunt een tag een hogere positie geven om de relevantie ervan voor een video te vergroten. Door een tag voor een video te promoten, neemt de kans toe dat de video in de zoekresultaten wordt weergegeven wanneer een zoekopdracht op basis van die tag wordt uitgevoerd.

Meer over weten hoe te om de slimme markeringen voor activa te matigen, zie [ slimme markeringen ](smart-tags.md#manage-smart-tags-and-searches) leiden.

![ Moderate video slimme markeringen ](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>Om het even welke markeringen die gebruikend de stappen in [ worden gematigd leiden slimme markeringen ](smart-tags.md#manage-smart-tags-and-searches) worden niet herinnerd bij het opwerken van de activa. De originele set labels wordt opnieuw weergegeven.

## Slimme tags toepassen op video uitschakelen {#opt-out-video-smart-tagging}

Wanneer het automatisch labelen van video&#39;s tegelijkertijd met andere taken voor middelenverwerking wordt uitgevoerd, zoals het maken van miniaturen en het uitnemen van metagegevens, kan dit tijdrovend zijn. Als u de verwerking van elementen wilt versnellen, kunt u de optie Slimme tags toepassen bij het uploaden van video&#39;s op mapniveau uitschakelen.

U kunt het genereren van automatische slimme-videolabels uitschakelen voor elementen die naar een specifieke map zijn geüpload:

1. Open [!UICONTROL Asset Processing] in de map [!UICONTROL Properties] .

1. In het menu [!UICONTROL Smart Tags for Videos] is de optie [!UICONTROL Inherited] standaard geselecteerd en wordt slimme tag voor video ingeschakeld.

   Wanneer de optie [!UICONTROL Inherited] is geselecteerd, is het overgeërfde mappad ook zichtbaar samen met de informatie of het is ingesteld op [!UICONTROL Enable] of [!UICONTROL Disable] .

   ![ maak video slimme het etiketteren ](assets/disable-video-tagging.png) onbruikbaar

1. Selecteer [!UICONTROL Disable] om slimme tags toepassen voor video&#39;s die naar de map zijn geüpload.

>[!IMPORTANT]
>
>Als u er bij het uploaden voor hebt gekozen om geen tags aan video&#39;s toe te wijzen in een map en de video&#39;s na het uploaden slimme tags toe te wijzen, kiest u **[!UICONTROL Enable Smart Tags for Videos]** op [!UICONTROL Asset Processing] tab van de map [!UICONTROL Properties] en gebruikt u [[!UICONTROL Reprocess Asset] option ](#smart-tag-existing-videos) om slimme tags aan de video toe te voegen.

## Vertrouwensscore {#confidence-score-video-tag}

[!DNL Adobe Experience Manager] past een minimale betrouwbaarheidsdrempel voor object- en handeling-slimme tags toe om te voorkomen dat er te veel tags voor elk video-element zijn, waardoor de indexering wordt vertraagd. De zoekresultaten van uw middelen worden gerangschikt op basis van de betrouwbaarheidsscores, die over het algemeen de zoekresultaten verbeteren en verder gaan dan wat een inspectie van de toegewezen tags van een video-element suggereert. Onnauwkeurige tags hebben vaak lage betrouwbaarheidsscores, zodat ze zelden boven aan de lijst Slimme tags voor elementen worden weergegeven.

De standaardwaarde voor actie- en objecttags in [!DNL Adobe Experience Manager] is 0,7 (moet een waarde tussen 0 en 1 zijn). Als bepaalde video-elementen niet zijn gecodeerd met een specifieke tag, geeft dit aan dat het algoritme minder dan 70% zeker is van de voorspelde tags. De standaarddrempel is mogelijk niet altijd optimaal voor alle gebruikers. U kunt, daarom, de waarde van de betrouwbaarheidsscore in configuratie veranderen OSGI.

U kunt als volgt de OSGI-configuratie met de betrouwbaarheidsscore toevoegen aan het project dat als een [!DNL Cloud Service] tot en met [!DNL Cloud Manager] wordt geïmplementeerd: [!DNL Adobe Experience Manager]

* In het [!DNL Adobe Experience Manager] project (`ui.config` sinds Archetype 24, of eerder `ui.apps`) omvat de `config.author` configuratie OSGi, een config dossier genoemd `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` met de volgende inhoud:

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```

>[!NOTE]
>
>Handmatige tags krijgen een betrouwbaarheid van 100% (maximale betrouwbaarheid). Daarom als er videoactiva met handmarkeringen zijn die de onderzoeksvraag aanpassen, worden zij getoond vóór slimme markeringen die de onderzoeksvraag aanpassen.

## Beperkingen {#video-smart-tagging-limitations}

* U kunt de service die slimme tags toepast op video&#39;s niet trainen met behulp van specifieke video&#39;s. Dit werkt met de standaardinstellingen van [!DNL Adobe Sensei] .

* De voortgang van de codering wordt niet weergegeven.

* Alleen video&#39;s die kleiner zijn dan 300 MB, worden automatisch gecodeerd. De service [!DNL Adobe Sensei] slaat videobestanden over die groter zijn.

* Slechts worden de video&#39;s in de dossierformaten en gesteunde codecs die in [ worden vermeld Slimme Markeringen ](/help/assets/smart-tags.md#smart-tags-supported-file-formats) geëtiketteerd.

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
>* [ beheer slimme markeringen en activa onderzoeken ](smart-tags.md#manage-smart-tags-and-searches)
>* [ de Slimme dienst van de Markering van de Lijn en etiketteer uw beelden ](smart-tags.md)
