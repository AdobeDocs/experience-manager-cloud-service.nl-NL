---
title: Videoassets beheren
description: Video-elementen uploaden, voorvertonen, notities aanbrengen en publiceren in [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 7%

---


# Videoassets beheren {#manage-video-assets}

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen in beheert en bewerkt [!DNL Adobe Experience Manager Assets]. Videocodering en -transcodering, bijvoorbeeld MPEG-transcodering, is mogelijk met behulp van Procesprofielen en [!DNL Dynamic Media] integratie. Zonder [!DNL Dynamic Media] licentie biedt [!DNL Experience Manager] u basisondersteuning voor video&#39;s, zoals transcoderen met Mpeg, het uitnemen van voorvertoningsminiaturen voor de ondersteunde bestandsindelingen en een voorvertoning in de gebruikersinterface voor indelingen die worden ondersteund voor rechtstreeks afspelen in de browser.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] Hiermee genereert u voorvertoningen voor video-elementen met de extensie MP4. U kunt een voorvertoning van de uitvoeringen weergeven in de [!DNL Assets] gebruikersinterface.

1. Navigeer in de map met digitale elementen of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Als u het element wilt uploaden, klikt u op **[!UICONTROL Create]** de werkbalk en kiest u **[!UICONTROL Files]**. U kunt ook een bestand naar de gebruikersinterface slepen. Zie [Elementen](manage-digital-assets.md#uploading-assets) uploaden voor meer informatie.
1. Als u een voorvertoning van een video wilt weergeven in de kaartweergave, klikt u op de optie voor het **[!UICONTROL Play]** afspelen ![](assets/do-not-localize/play.png) van het video-element. U kunt video alleen in de kaartweergave pauzeren of afspelen. De opties [!UICONTROL Play] en [!UICONTROL Pause] zijn niet beschikbaar in de lijstweergave.
1. Selecteer op de kaart om een voorvertoning van de video weer te geven op de pagina met elementdetails. **[!UICONTROL Edit]** De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

## Video-elementen publiceren {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Zie Dynamische media-elementen [](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)publiceren voor meer informatie.

## Transcoderen met verwerkingsprofiel {#transcode-video}

[!DNL Experience Manager] als Cloud Service kunt u standaardtranscodering van MP4-videobestanden uitvoeren met behulp van Procesprofielen. Met deze functionaliteit kunt u niet alleen een MP4-videobestand uploaden, maar ook een voorvertoning weergeven en schalen.

![Verwerkingsprofiel maken voor videotranscodering in Experience Manager](assets/video-processing-profile-for-mp4.png)

*Afbeelding: A Processing Profile for video transcoding in [!DNL Experience Manager].*

Als u alleen de breedte of alleen de hoogte opgeeft en het andere veld leeg laat, behouden de uitvoeringen de hoogte-breedteverhouding. Momenteel is alleen de h264-codec beschikbaar voor transcodering.

Als u elementen wilt verwerken met een verwerkingsprofiel, voegt u een profiel toe aan een map. Zie [verwerkingsprofielen gebruiken om elementen](/help/assets/asset-microservices-configure-and-use.md#use-profiles)te verwerken.

## Video-elementen notities aanbrengen {#annotate-video-assets}

1. Selecteer in de [!DNL Assets] console **[!UICONTROL Edit]** op de elementenkaart om de pagina met elementdetails weer te geven.
1. Klik op **[!UICONTROL Preview]** om de video af te spelen.
1. Klik op **[!UICONTROL Annotate]** de video als u deze wilt annoteren. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen. Klik op de knop **[!UICONTROL Close]** om de wizard Annotatie af te sluiten.
1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 20 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.
1. Klik op een annotatie om deze in de tijdlijn weer te geven. Klik op de knop **[!UICONTROL Delete]**.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Zonder Dynamic Media-licentie kunt u alleen MP4-bestanden verwerken met behulp van verwerkingsprofielen.
* Voor elementaire transcodering met

>[!MORELIKETHIS]
>
>* [Dynamische mediavideodocumentatie](/help/assets/dynamic-media/video.md).
>* [Meer informatie over gebruik, typen en configuratie van verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).

