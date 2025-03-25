---
title: Geoptimaliseerde afbeeldingen leveren voor een responsieve site
description: Leer hoe u de functie voor responsieve code gebruikt om geoptimaliseerde afbeeldingen van Dynamic Media te leveren.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 62af6f3f-9c86-44ad-870d-140f572f99c5
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 9%

---

# Geoptimaliseerde afbeeldingen leveren voor een responsieve site {#delivering-optimized-images-for-a-responsive-site}

Gebruik de functie Responsieve code wanneer u de code wilt delen voor responsieve functies in uw webontwikkelaar. U kopieert de responsieve code (**[!UICONTROL RESS]**) naar het klembord zodat u deze kunt delen met de webontwikkelaar.

Deze functie is handig als uw website zich op een WCM van derden bevindt. Als uw website zich echter op Adobe Experience Manager bevindt, wordt de afbeelding door een externe afbeeldingsserver gerenderd en aan de webpagina geleverd.

Zie ook [ bed de VideoKijker op een Web-pagina ](embed-code.md) in.

Zie ook [ Verbinding URLs aan uw Webtoepassing ](linking-urls-to-yourwebapplication.md).

**om geoptimaliseerde beelden voor een ontvankelijke plaats te leveren:**

1. Navigeer naar de afbeelding waarvoor u responsieve code wilt opgeven en selecteer **[!UICONTROL Renditions]** in het keuzemenu.

   ![ chlimage_1-408 ](assets/chlimage_1-408.png)

1. Selecteer een responsieve voorinstelling voor de afbeelding. De knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** worden weergegeven.

   ![ chlimage_1-409 ](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >De geselecteerde asset *en* de geselecteerde afbeeldings- of viewervoorinstelling moeten worden gepubliceerd om de knoppen **[!UICONTROL URL]** of **[!UICONTROL RESS]** beschikbaar te maken.
   >
   >Voorinstellingen voor afbeeldingen worden automatisch gepubliceerd.

1. Selecteer **[!UICONTROL RESS]** .

   ![ chlimage_1-410 ](assets/chlimage_1-410.png)

1. Selecteer in het dialoogvenster **[!UICONTROL Embed Responsive Image]** de tekst van de responsieve code, kopieer deze en plak deze in uw website om het responsieve element te openen.
1. Bewerk de standaardonderbrekingspunten in de insluitcode zodat deze overeenkomen met de standaardonderbrekingspunten op de responsieve website, rechtstreeks in de code. Test bovendien de verschillende afbeeldingsresoluties die op verschillende pagina-onderbrekingspunten worden weergegeven.

## Het gebruiken van HTTP/2 om uw Dynamische activa van Media te leveren {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-elementen wordt ondersteund met HTTP/2, dat betere responstijd en laadtijden biedt.

Zie [ HTTP2 Levering van Inhoud ](http2faq.md) voor volledige details bij het worden begonnen HTTP/2 met uw Dynamische rekening van Media te gebruiken.
