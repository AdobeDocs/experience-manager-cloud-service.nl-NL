---
title: Geoptimaliseerde afbeeldingen leveren voor een responsieve site
description: Leer hoe u de functie voor responsieve code gebruikt om geoptimaliseerde afbeeldingen van Dynamic Media te leveren.
feature: Asset Management
role: User
exl-id: 62af6f3f-9c86-44ad-870d-140f572f99c5
source-git-commit: a11529886d4b158c19a97ccbcb7d004cf814178d
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 10%

---

# Geoptimaliseerde afbeeldingen leveren voor een responsieve site {#delivering-optimized-images-for-a-responsive-site}

Gebruik de functie Responsieve code wanneer u de code wilt delen voor responsieve serving met uw webontwikkelaar. U kopieert de responsieve (**[!UICONTROL RESS]**) naar het klembord zodat u deze kunt delen met de webontwikkelaar.

Deze functie is handig als uw website zich op een WCM van derden bevindt. Als uw website zich echter op Adobe Experience Manager bevindt, wordt de afbeelding door een externe afbeeldingsserver gerenderd en aan de webpagina geleverd.

Zie ook [De video-viewer insluiten op een webpagina](embed-code.md).

Zie ook [URL&#39;s koppelen aan uw webtoepassing](linking-urls-to-yourwebapplication.md).

**Om geoptimaliseerde afbeeldingen te leveren voor een responsieve site:**

1. Navigeer naar de afbeelding waarvoor u responsieve code wilt opgeven en selecteer in het keuzemenu de optie **[!UICONTROL Renditions]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Selecteer een responsieve voorinstelling voor de afbeelding. De knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** worden weergegeven.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >De geselecteerde asset *en* de geselecteerde afbeeldings- of viewervoorinstelling moeten worden gepubliceerd om de knoppen **[!UICONTROL URL]** of **[!UICONTROL RESS]** beschikbaar te maken.
   >
   >Voorinstellingen voor afbeeldingen worden automatisch gepubliceerd.

1. Selecteer **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. In de **[!UICONTROL Embed Responsive Image]** , selecteert en kopieert u de tekst van de responsieve code en plakt u deze in uw website om het responsieve element te openen.
1. Bewerk de standaardonderbrekingspunten in de insluitcode zodat deze overeenkomen met de standaardonderbrekingspunten op de responsieve website, rechtstreeks in de code. Test bovendien de verschillende afbeeldingsresoluties die op verschillende pagina-onderbrekingspunten worden weergegeven.

## HTTP/2 gebruiken om uw Dynamic Media-middelen te leveren {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-elementen wordt ondersteund met HTTP/2, dat betere responstijd en laadtijd biedt.

Zie [HTTP2 Levering van inhoud](http2faq.md) voor volledige informatie over hoe u aan de slag gaat met HTTP/2 met uw Dynamic Media-account.
