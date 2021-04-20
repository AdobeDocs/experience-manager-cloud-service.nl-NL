---
title: Videoassets beheren
description: Upload, voorproef, annoteer, en publiceer videoactiva in  [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management,Publishing,Collaboration,Video
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 6%

---


# Videoassets beheren {#manage-video-assets}

De video-indeling is een essentieel onderdeel van digitale middelen van een organisatie. [!DNL Adobe Experience Manager] biedt geavanceerde aanbiedingen en functies om de volledige levenscyclus van uw video-elementen te beheren nadat deze zijn gemaakt.

Leer hoe u de video-elementen beheert en bewerkt in [!DNL Adobe Experience Manager Assets]. Videocodering en -transcodering, bijvoorbeeld MPEG-transcodering, is mogelijk met behulp van Procesprofielen en met behulp van [!DNL Dynamic Media]-integratie. Zonder [!DNL Dynamic Media] licentie biedt [!DNL Experience Manager] basisondersteuning voor video&#39;s, zoals transcodering met Mpeg, het uitnemen van voorvertoningsminiaturen voor de ondersteunde bestandsindelingen en een voorvertoning in de gebruikersinterface voor indelingen die rechtstreeks worden ondersteund voor afspelen in de browser.

## Video-elementen uploaden en voorvertonen {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] Hiermee genereert u voorvertoningen voor video-elementen met de extensie MP4. U kunt een voorvertoning van de uitvoeringen weergeven in de gebruikersinterface [!DNL Assets].

1. Navigeer in de map met digitale elementen of in de submappen naar de locatie waar u digitale elementen wilt toevoegen.
1. Als u het element wilt uploaden, klikt u op **[!UICONTROL Create]** op de werkbalk en kiest u **[!UICONTROL Files]**. U kunt ook een bestand naar de gebruikersinterface slepen. Zie [Elementen uploaden](manage-digital-assets.md#uploading-assets) voor meer informatie.
1. Als u een video wilt voorvertonen in de kaartweergave, klikt u op de optie **[!UICONTROL Play]** ![afspeeloptie](assets/do-not-localize/play.png) op het video-element. U kunt video alleen in de kaartweergave pauzeren of afspelen. De opties [!UICONTROL Play] en [!UICONTROL Pause] zijn niet beschikbaar in de lijstweergave.
1. Selecteer **[!UICONTROL Edit]** op de kaart om een voorvertoning van de video weer te geven op de pagina met elementdetails. De video wordt afgespeeld in de native videospeler van de browser. U kunt de video afspelen, pauzeren, het volume bepalen en op het volledige scherm in- of uitzoomen.

## Video-elementen publiceren {#publish-video-assets}

Na publicatie kunt u de video-elementen in een webpagina opnemen als een URL of de elementen rechtstreeks insluiten. Zie [publish [!DNL Dynamic Media] assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor meer informatie.

## Transcoderen met behulp van verwerkingsprofiel {#transcode-video}

[!DNL Experience Manager] als een  [!DNL Cloud Service] methode gebruikt, kunt u standaardtranscodering van MP4-videobestanden uitvoeren met behulp van Procesprofielen. Met deze functionaliteit kunt u niet alleen een MP4-videobestand uploaden, maar ook een voorvertoning weergeven en schalen.

![Verwerkingsprofiel maken voor videotranscodering in  [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*Afbeelding: A Processing Profile for video transcoding in  [!DNL Experience Manager].*

Als u alleen de breedte of alleen de hoogte opgeeft en het andere veld leeg laat, behouden de uitvoeringen de hoogte-breedteverhouding. H.264-videocodec is beschikbaar voor transcodering.

Als u elementen wilt verwerken met een verwerkingsprofiel, voegt u een profiel toe aan een map. Zie [verwerkingsprofielen gebruiken om elementen te verwerken](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Video-elementen {#annotate-video-assets} notities aanbrengen

1. Selecteer **[!UICONTROL Edit]** op de elementenkaart in de [!DNL Assets]-console om de pagina met elementdetails weer te geven.
1. Klik op **[!UICONTROL Preview]** om de video af te spelen.
1. Klik op **[!UICONTROL Annotate]** om de video een annotatie te geven. Er wordt een aantekening toegevoegd op het specifieke tijdstip (frame) in de video. Wanneer u notities maakt, kunt u op het canvas tekenen en een opmerking bij de tekening opnemen. Opmerkingen worden automatisch opgeslagen. Klik op **[!UICONTROL Close]** om de wizard Annotatie af te sluiten.
1. Zoek naar een specifiek punt in de video, geef de tijd in seconden op in het veld voor **tekst** en klik op **Springen**. Als u bijvoorbeeld de eerste 20 seconden van de video wilt overslaan, voert u 20 in het tekstveld in.
1. Klik op een annotatie om deze in de tijdlijn weer te geven. Als u de annotatie uit de tijdlijn wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

## Beste werkwijzen en beperkingen {#tips-limitations}

* Zonder [!DNL Dynamic Media]-licentie kunt u alleen MP4-bestanden verwerken met behulp van verwerkingsprofielen.
* Bij het transcoderen van MP4-bestanden met verwerkingsprofielen gelden de volgende richtlijnen en beperkingen:

   * Apple ProRes-bestanden kunnen alleen transcoderen naar een maximale resolutie van 1080p.
   * Als het bronbestand een bitsnelheid > 200 Mbps heeft, kunt u alleen transcoderen naar een maximale resolutie van 1080p.
   * Als de bronframesnelheid >=60 fps is, is de maximale grootte van het bronbestand dat u kunt gebruiken:

      * 400 MB voor 4.000 transcodering.
      * 800 MB voor 1080p-transcodering.
      * 8 GB voor 720p-transcodering.
   * De maximale bestandsgrootte die u kunt transcoderen naar een resolutie van 4 k is 2,55 GB MP4-bestand met een resolutie van 4 k, een bitsnelheid van 12 Mbps en 23 fps.


>[!MORELIKETHIS]
>
>* [Dynamic Media-videodocumentatie](/help/assets/dynamic-media/video.md).
>* [Meer informatie over gebruik, typen en configuratie van verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).

