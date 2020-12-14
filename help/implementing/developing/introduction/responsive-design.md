---
title: Responsief ontwerp
description: Met responsief ontwerp kunnen dezelfde ervaringen effectief worden weergegeven op meerdere apparaten in meerdere richtingen
translation-type: tm+mt
source-git-commit: a3b2a66958fd8d3a68b450938c5c18053f00b998
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Responsief ontwerp {#responsive-design}

Ontwerp uw ervaringen zodat ze zich aanpassen aan de clientviewport waarin ze worden weergegeven. Met responsief ontwerp kunnen dezelfde pagina&#39;s effectief op meerdere apparaten in beide richtingen worden weergegeven. In de volgende afbeelding ziet u enkele manieren waarop een pagina kan reageren op wijzigingen in de viewportgrootte:

* Layout: Gebruik lay-outs met één kolom voor kleinere viewports en lay-outs met meerdere kolommen voor grotere viewports.
* Tekengrootte: Gebruik grotere tekstgrootte (indien van toepassing, zoals koppen) in grotere viewports.
* Inhoud: Neem alleen de belangrijkste inhoud op wanneer u deze weergeeft op kleinere apparaten.
* Navigatie: Er zijn apparaatspecifieke gereedschappen voor toegang tot andere pagina&#39;s.
* Afbeeldingen: Uitvoerende afbeeldingsuitvoeringen die geschikt zijn voor de viewport van de client, afhankelijk van de afmetingen van het venster.

![Voorbeelden van responsief ontwerp](assets/responsive-example.png)

Ontwikkel Adobe Experience Manager (AEM) toepassingen die HTML5 genereren die zich aanpast aan meerdere venstergrootten en -standen. De volgende bereiken van viewport-breedten komen bijvoorbeeld overeen met verschillende apparaattypen en -oriëntaties

* Maximale breedte van 480 pixels (telefoon, staand)
* Maximale breedte van 767 pixels (telefoon, liggend)
* Breedte tussen 768 pixels en 979 pixels (tablet, staand)
* Breedte tussen 980 pixels en 1199 pixels (tablet, liggend)
* Breedte van 1200 px of hoger (bureaublad)

Zie de volgende onderwerpen voor informatie over het uitvoeren van ontvankelijk ontwerpgedrag:

* [Mediaquery&#39;s](#using-media-queries)
* [Vloeiende rasters](#developing-a-fluid-grid)
* [Adaptieve afbeeldingen](#using-adaptive-images)

Tijdens het ontwerpen kunt u de werkbalk **Emulator** gebruiken om een voorvertoning van uw pagina&#39;s weer te geven voor verschillende schermgrootten.

## Voordat u {#before-you-develop} ontwikkelt

Voordat u de AEM ontwikkelt die uw webpagina&#39;s ondersteunt, moet u een aantal ontwerpbeslissingen nemen. U moet bijvoorbeeld over de volgende informatie beschikken:

* De apparaten waarvoor u zich richt
* De doelviewportgrootten
* De paginalay-outs voor elk van de beoogde viewportgrootte

### Toepassingsstructuur {#application-structure}

De typische AEM toepassingsstructuur ondersteunt alle responsieve ontwerpimplementaties:

* Paginacomponenten bevinden zich onder `/apps/<application_name>/components`
* Sjablonen bevinden zich onder `/apps/<application_name>/templates`

## Mediaquery&#39;s {#using-media-queries} gebruiken

Met mediaquery&#39;s kunt u CSS-stijlen selectief gebruiken voor het weergeven van pagina&#39;s. AEM ontwikkelingshulpmiddelen en eigenschappen laten u toe om media vragen in uw toepassingen effectief en efficiënt uit te voeren.

De W3C-groep biedt de aanbeveling [Mediaquery&#39;s](https://www.w3.org/TR/css3-mediaqueries/) waarmee deze CSS3-functie en de syntaxis worden beschreven.

### Het CSS-bestand {#creating-the-css-file} maken

Definieer in uw CSS-bestand mediaquery&#39;s op basis van de eigenschappen van de apparaten waarvoor u een mediaquery maakt. De volgende implementatiestrategie is effectief voor het beheren van stijlen voor elke mediaquery:

* Gebruik een [map Clientbibliotheek](clientlibs.md) om de CSS te definiëren die wordt samengevoegd wanneer de pagina wordt weergegeven.
* Definieer elke mediaquery en de bijbehorende stijlen in afzonderlijke CSS-bestanden. Het is handig bestandsnamen te gebruiken die de apparaatfuncties van de mediaquery vertegenwoordigen.
* Definieer stijlen die op alle apparaten in een afzonderlijk CSS-bestand van toepassing zijn.
* In het css.txt- dossier van de omslag van de Bibliotheek van de Cliënt, orde de lijst CSS dossiers zoals vereist in het geassembleerde CSS dossier.

De [WKND-zelfstudie](develop-wknd-tutorial.md) gebruikt deze strategie om stijlen in het siteontwerp te definiëren. Het CSS-bestand dat door WKND wordt gebruikt, bevindt zich op `/apps/wknd/clientlibs/clientlib-grid/less/grid.less`.
