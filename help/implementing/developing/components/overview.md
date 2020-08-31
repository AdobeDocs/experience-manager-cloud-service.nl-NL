---
title: Overzicht van componenten
description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 4%

---


# Overzicht van componenten {#components-overview}

Deze pagina biedt een overzicht van Adobe Experience Manager (AEM)-componenten, zoals de componenten die worden [gebruikt voor het ontwerpen](/help/sites-cloud/authoring/fundamentals/components.md)van pagina&#39;s.

## Wat zijn componenten? {#what-are-components}

Componenten in AEM zijn:

* Modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website te presenteren.
* Herbruikbaar.
* Ontwikkeld als zelfstandige eenheden in één map van de opslagplaats.
* Geen verborgen configuratiebestanden hebben.
* Kan andere componenten bevatten.
* Kan overal binnen om het even welk AEM systeem lopen en kan ook beperkt zijn om onder specifieke componenten te lopen.
* Een gestandaardiseerde gebruikersinterface hebben.
* Heb bewerkingsgedrag dat kan worden gevormd.
* Dialoogvensters gebruiken die zijn gebouwd met subelementen op basis van graniet UI-componenten.
* worden ontwikkeld met [HTML](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html).
* Kan worden ontwikkeld om aangepaste componenten te maken die de standaardfunctionaliteit uitbreiden.

Omdat componenten modulair zijn, kunt u:

* Ontwikkel een nieuwe component op uw lokale instantie.
* Implementeer deze in de testomgeving.
* Implementeer deze in uw live ontwerpomgeving, waar auteurs en/of beheerders inhoud kunnen toevoegen en configureren.
* Implementeer deze in uw live publicatieomgeving(en), waar ze worden gebruikt om inhoud te renderen voor bezoekers van uw website.

Elke AEM component:

* Is een middeltype.
* Is een inzameling van manuscripten die een specifieke functie volledig realiseren.
* Kan afzonderlijk functioneren, wat ofwel binnen AEM ofwel een portaal betekent.

## AEM kerncomponenten {#aem-core-components}

[De AEM Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken.

De Core Components worden voorzien van AEM als Cloud Service en het [WKND leerprogramma](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustreert hoe te om componenten uit te voeren en te gebruiken. De componenten worden voorzien van al broncode en kunnen als zijn of als uitgangspunt voor gewijzigde of uitgebreide componenten worden gebruikt.

### Beschikbare componenten weergeven {#viewing-available-components}

Voor een overzicht van alle beschikbare componenten in uw AEM instantie, gebruik de Console [van](/help/sites-cloud/authoring/features/components-console.md)Componenten.

U kunt ook CRXDE Lite gebruiken om een lijst met alle componenten in de opslagplaats op te halen.

1. Selecteer in **[!UICONTROL CRXDE Lite]** de werkbalk vervolgens **[!UICONTROL Tools]** de optie **[!UICONTROL Query]** waarmee het **[!UICONTROL Query]** tabblad wordt geopend.

1. Selecteer op het **[!UICONTROL Query]** tabblad `XPath` als **[!UICONTROL Type]**.

1. Voer in het **[!UICONTROL Query]** invoerveld de volgende tekenreeks in:

   `//element(*, cq:Component)`

1. Klik **[!UICONTROL Execute]** en de componenten worden vermeld.

