---
title: Geoptimaliseerde afbeeldingen voor een responsieve site leveren
description: De functie voor responsieve code gebruiken om geoptimaliseerde afbeeldingen te leveren
translation-type: tm+mt
source-git-commit: d6e92a433e61c2a959c62080fcd52fe0ebe67c4f
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 12%

---


# Geoptimaliseerde afbeeldingen leveren voor een responsieve site {#delivering-optimized-images-for-a-responsive-site}

Gebruik de functie Responsieve code wanneer u de code wilt delen voor responsieve serving met uw webontwikkelaar. U kopieert de responsieve code (**[!UICONTROL RESS]**) naar het klembord zodat u deze kunt delen met de webontwikkelaar.

Deze functie is handig als uw website zich op een WCM van derden bevindt. Als uw website echter op AEM staat, rendert een externe afbeeldingsserver de afbeelding en levert deze aan de webpagina.

Zie ook [De video-viewer insluiten op een webpagina.](embed-code.md)

Zie ook [URL&#39;s koppelen aan uw webtoepassing.](linking-urls-to-yourwebapplication.md)

**Geoptimaliseerde afbeeldingen leveren voor een responsieve site**:

1. Navigeer naar de afbeelding waarvoor u responsieve code wilt opgeven en tik in het keuzemenu op **[!UICONTROL Renditions]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Selecteer een responsieve voorinstelling voor de afbeelding. De knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** worden weergegeven.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >De geselecteerde asset *en* de geselecteerde afbeeldings- of viewervoorinstelling moeten worden gepubliceerd om de knoppen **[!UICONTROL URL]** of **[!UICONTROL RESS]** beschikbaar te maken.
   >
   >Voorinstellingen voor afbeeldingen worden automatisch gepubliceerd.

1. Tik op **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Selecteer en kopieer in het dialoogvenster **[!UICONTROL Embed Responsive Image]** de tekst van de responsieve code en plak deze in uw website om het responsieve element te openen.
1. Bewerk de standaardbreekpunten in de insluitcode zodat deze overeenkomen met die van de responsieve website rechtstreeks in de code. Test bovendien de verschillende afbeeldingsresoluties die op verschillende pagina-onderbrekingspunten worden weergegeven.

## Het gebruiken van HTTP/2 om uw Dynamische activa van Media {#using-http-to-delivery-your-dynamic-media-assets} te leveren

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-elementen wordt ondersteund met HTTP/2, dat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](http2faq.md) voor volledige details bij het worden begonnen met het gebruiken van HTTP/2 met uw Dynamische rekening van Media.
