---
title: Slimme tag toewijzen aan video-elementen
description: Experience Manager voegt contextafhankelijke en beschrijvende slimme tags automatisch toe aan video's die [!DNL Adobe Sensei].
feature: Smart Tags,Tagging
role: Admin,User
exl-id: b59043c5-5df3-49a7-b4fc-da34c03649d7
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---

# Slimme tag toewijzen aan video-elementen {#video-smart-tags}

De groeiende behoefte aan nieuwe inhoud vraagt om minder handmatige inspanningen om op korte termijn aantrekkelijke digitale ervaringen te bieden. [!DNL Adobe Experience Manager] als [!DNL Cloud Service] ondersteunt automatische labeling van video-elementen met behulp van kunstmatige intelligentie. Het kan tijdrovend zijn om de video&#39;s handmatig te labelen. Maar [!DNL Adobe Sensei] Intelligente videotags worden gebruikt voor kunstmatige intelligentiemodellen om video-inhoud te analyseren en tags toe te voegen aan de video-elementen. Hierdoor verkort u tijd voor DAM-gebruikers om hun klanten rijke ervaringen te bieden. De leerservice voor computers van Adobe genereert twee sets tags voor een video. De ene set komt weliswaar overeen met objecten, scènes en kenmerken in die video, maar de andere set heeft betrekking op handelingen zoals drinken, lopen en jogging.

Videocodering is standaard ingeschakeld in [!DNL Adobe Experience Manager] als [!DNL Cloud Service]. U kunt echter [opt-out van slimme tags voor video](#opt-out-video-smart-tagging) in een map. Video&#39;s worden automatisch van tags voorzien wanneer u nieuwe video&#39;s uploadt of bestaande video&#39;s opnieuw verwerkt. [!DNL Experience Manager] Hiermee maakt u ook de miniaturen en extraheert u de metagegevens van de videobestanden. De slimme tags worden in aflopende volgorde weergegeven [betrouwbaarheidsscore](#confidence-score-video-tag) in actief [!UICONTROL Properties].

## Slimme tags toepassen op video&#39;s tijdens het uploaden {#smart-tag-assets-on-ingestion}

Wanneer u [video-elementen uploaden](add-assets.md#upload-assets) tot [!DNL Adobe Experience Manager] als [!DNL Cloud Service], worden de video&#39;s verwerkt. Als de verwerking is voltooid, raadpleegt u de [!UICONTROL Basic] tabblad van element [!UICONTROL Properties] pagina. Slimme tags worden automatisch toegevoegd aan de video onder [!UICONTROL Smart Tags]. Gebruik van Asset Microservices [!DNL Adobe Sensei] om deze slimme tags te maken.

![Slimme tags worden toegevoegd aan video&#39;s en weergegeven op het tabblad Standaard van de Eigenschappen van elementen](assets/smart-tags-added-to-videos.png)

De toegepaste slimme tags worden in aflopende volgorde gesorteerd van [betrouwbaarheidsscore](#confidence-score-video-tag), gecombineerd voor object- en actietags, binnen [!UICONTROL Smart Tags].

>[!IMPORTANT]
>
>U wordt geadviseerd om deze automatisch geproduceerde markeringen te herzien om ervoor te zorgen dat zij aan uw merk en zijn waarden in overeenstemming zijn.

## Bestaande video&#39;s slim labelen in DAM {#smart-tag-existing-videos}

De bestaande video-elementen in DAM worden niet automatisch gecodeerd als slimme tags. U moet [!UICONTROL Reprocess Assets] handmatig om slimme tags voor deze tags te genereren.

Voer de volgende stappen uit om slimme tags toe te wijzen aan video-elementen of mappen (inclusief submappen) van elementen die al in de opslagplaats voor elementen bestaan:

1. Selecteer de [!DNL Adobe Experience Manager] logo en selecteer vervolgens elementen in het [!UICONTROL Navigation] pagina.

1. Selecteren [!UICONTROL Files] om de interface Elementen weer te geven.

1. Ga naar de map waarop u slimme tags wilt toepassen.

1. Selecteer de volledige map of specifieke video-elementen.

1. Selecteren ![Pictogram Elementen opnieuw verwerken](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Reprocess Assets] en selecteert u de [!UICONTROL Full Process] -optie.

<!-- TBD: Limit size -->

![Elementen opnieuw verwerken om tags toe te voegen aan video&#39;s in de bestaande DAM-opslagplaats](assets/reprocess.gif)

Als het proces is voltooid, navigeert u naar de [!UICONTROL Properties] pagina met alle video-elementen in de map. De automatisch toegevoegde tags worden weergegeven in [!UICONTROL Smart Tags] sectie in [!UICONTROL Basic] tab. Deze toegepaste slimme tags worden in aflopende volgorde gesorteerd op [betrouwbaarheidsscore](#confidence-score-video-tag).

## Zoeken naar gelabelde video&#39;s {#search-smart-tagged-videos}

Als u de video-elementen wilt zoeken op basis van de automatisch gegenereerde slimme tags, gebruikt u [Omnissearch](search-assets.md#search-assets-in-aem):

1. Selecteer het zoekpictogram ![zoekpictogram](assets/do-not-localize/search_icon.png) om het veld Onderzoek weer te geven.

1. Geef in het veld Onderzoek een tag op die u niet expliciet aan een video hebt toegevoegd.

1. Zoeken op basis van de tag.

De zoekresultaten geven de video-elementen weer op basis van de tag die u hebt opgegeven.

Uw zoekresultaten zijn een combinatie van video-elementen met gezochte trefwoorden in de metagegevens en de video-elementen die zijn gelabeld met de gezochte trefwoorden. De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden echter eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. Zie voor meer informatie [Begrijpen [!DNL Experience Manager] zoekresultaten met slimme tags](smart-tags.md#understand-search).

## Slimme videolabels modereren {#moderate-video-smart-tags}

[!DNL Adobe Experience Manager] Hiermee kunt u de slimme tags krommen naar:

* Verwijder onjuiste tags die zijn toegewezen aan uw merkvideo&#39;s.

* U kunt zoekopdrachten op basis van tags verfijnen voor video&#39;s door ervoor te zorgen dat de video wordt weergegeven in de zoekresultaten voor de meest relevante tags. Hierdoor wordt de kans dat niet-verwante video&#39;s in zoekresultaten worden weergegeven, weggenomen.

* U kunt een tag een hogere positie geven om de relevantie ervan voor een video te vergroten. Door een tag voor een video te promoten, neemt de kans toe dat de video in de zoekresultaten wordt weergegeven wanneer een zoekopdracht op basis van die tag wordt uitgevoerd.

Zie voor meer informatie over hoe u de slimme tags voor elementen kunt verkleinen [Slimme tags beheren](smart-tags.md#manage-smart-tags-and-searches).

![Slimme videolabels modereren](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>Alle tags die met de stappen in [Slimme tags beheren](smart-tags.md#manage-smart-tags-and-searches) niet worden onthouden bij de opwerking van het actief. De originele set labels wordt opnieuw weergegeven.

## Slimme tags toepassen op video uitschakelen {#opt-out-video-smart-tagging}

Wanneer het automatisch labelen van video&#39;s tegelijkertijd met andere taken voor middelenverwerking wordt uitgevoerd, zoals het maken van miniaturen en het uitnemen van metagegevens, kan dit tijdrovend zijn. Als u de verwerking van elementen wilt versnellen, kunt u de optie Slimme tags toepassen bij het uploaden van video&#39;s op mapniveau uitschakelen.

U kunt het genereren van automatische slimme-videolabels uitschakelen voor elementen die naar een specifieke map zijn geüpload:

1. Openen [!UICONTROL Asset Processing] tabblad in map [!UICONTROL Properties].

1. In [!UICONTROL Smart Tags for Videos] menu, [!UICONTROL Inherited] Deze optie is standaard geselecteerd en de slimme tag video is ingeschakeld.

   Wanneer de [!UICONTROL Inherited] is geselecteerd, is het overgeërfde mappad ook zichtbaar samen met de informatie of het is ingesteld op [!UICONTROL Enable] of [!UICONTROL Disable].

   ![Slimme tags toepassen op video uitschakelen](assets/disable-video-tagging.png)

1. Selecteren [!UICONTROL Disable] om te weigeren om slimme tags toe te wijzen aan video&#39;s die naar de map zijn geüpload.

>[!IMPORTANT]
>
>Als u er bij het uploaden voor hebt gekozen om geen tags aan video&#39;s toe te wijzen in een map en de video&#39;s na het uploaden een slimme tag wilt geven, **[!UICONTROL Enable Smart Tags for Videos]** van [!UICONTROL Asset Processing] tabblad van de map [!UICONTROL Properties] en gebruik [[!UICONTROL Reprocess Asset] option](#smart-tag-existing-videos) om slimme tags toe te voegen aan de video.

## Vertrouwensscore {#confidence-score-video-tag}

[!DNL Adobe Experience Manager] past een minimale betrouwbaarheidsdrempel toe voor slimme tags voor objecten en handelingen om te voorkomen dat er te veel tags voor elk video-element zijn, waardoor de indexering wordt vertraagd. De zoekresultaten van uw middelen worden gerangschikt op basis van de betrouwbaarheidsscores, die over het algemeen de zoekresultaten verbeteren en verder gaan dan wat een inspectie van de toegewezen tags van een video-element suggereert. Onnauwkeurige tags hebben vaak lage betrouwbaarheidsscores, zodat ze zelden boven aan de lijst Slimme tags voor elementen worden weergegeven.

De standaarddrempel voor actie- en objecttags in [!DNL Adobe Experience Manager] is 0,7 (moet een waarde tussen 0 en 1 zijn). Als bepaalde video-elementen niet zijn gecodeerd met een specifieke tag, geeft dit aan dat het algoritme minder dan 70% zeker is van de voorspelde tags. De standaarddrempel is mogelijk niet altijd optimaal voor alle gebruikers. U kunt, daarom, de waarde van de betrouwbaarheidsscore in configuratie veranderen OSGI.

Om de configuratie van de betrouwbaarheidsscoreOSGI aan het project toe te voegen dat wordt opgesteld aan [!DNL Adobe Experience Manager] als [!DNL Cloud Service] doorheen [!DNL Cloud Manager]:

* In de [!DNL Adobe Experience Manager] project (`ui.config` sinds Archetype 24 of eerder `ui.apps`de `config.author` OSGi configuratie, omvat een config dossier genoemd `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` met de volgende inhoud:

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

* U kunt de service die slimme tags toepast op video&#39;s niet trainen met behulp van specifieke video&#39;s. Het werkt standaard [!DNL Adobe Sensei] instellingen.

* De voortgang van de codering wordt niet weergegeven.

* Alleen video&#39;s die kleiner zijn dan 300 MB, worden automatisch gecodeerd. De [!DNL Adobe Sensei] De dienst slaat videodossiers over die in grootte groter zijn.

* Alleen de video&#39;s in de bestandsindelingen en ondersteunde codecs die worden vermeld in [Slimme tags](/help/assets/smart-tags.md#smart-tags-supported-file-formats) zijn gelabeld.

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
>* [Slimme tags beheren en zoeken naar middelen](smart-tags.md#manage-smart-tags-and-searches)
>* [De service Slimme tags toepassen en uw afbeeldingen labelen](smart-tags.md)
