---
title: Geoptimaliseerde afbeeldingen voor een responsieve site leveren
description: Leer hoe u de functie voor responsieve code gebruikt om geoptimaliseerde afbeeldingen van Dynamic Media te leveren.
feature: Asset Management
topic: Business Practitioner
role: Business Practitioner
exl-id: 62af6f3f-9c86-44ad-870d-140f572f99c5
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 12%

---

# Geoptimaliseerde afbeeldingen leveren voor een responsieve site {#delivering-optimized-images-for-a-responsive-site}

Gebruik de functie Responsieve code wanneer u de code wilt delen voor responsieve serving met uw webontwikkelaar. U kopieert de responsieve code (**[!UICONTROL RESS]**) naar het klembord zodat u deze kunt delen met de webontwikkelaar.

Deze functie is handig als uw website zich op een WCM van derden bevindt. Als uw website echter op AEM staat, rendert een externe afbeeldingsserver de afbeelding en levert deze aan de webpagina.

Zie ook [De video-viewer insluiten op een webpagina](embed-code.md).

Zie ook [URLs aan uw Toepassing van het Web verbinden](linking-urls-to-yourwebapplication.md).

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

## HTTP/2 gebruiken om uw Dynamic Media-middelen {#using-http-to-delivery-your-dynamic-media-assets} te leveren

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-elementen wordt ondersteund met HTTP/2, dat betere responstijd en laadtijd biedt.

Zie [HTTP2 Levering van Inhoud](http2faq.md) voor volledige informatie over het gaan gebruiken van HTTP/2 met uw Dynamic Media-account.
