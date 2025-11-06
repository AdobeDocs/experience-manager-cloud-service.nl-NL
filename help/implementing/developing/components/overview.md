---
title: Overzicht van componenten
description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Overzicht van componenten {#components-overview}

Deze pagina verstrekt een overzicht van de componenten van Adobe Experience Manager (AEM) zoals die [&#x200B; die voor pagina creatie &#x200B;](/help/sites-cloud/authoring/page-editor/components.md) worden gebruikt.

## Wat zijn componenten? {#what-are-components}

* Modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website te presenteren.
* Herbruikbaar.
* Ontwikkeld als zelfstandige eenheden in één map van de opslagplaats.
* Geen verborgen configuratiebestanden hebben.
* Ze kunnen andere componenten bevatten.
* Ze kunnen overal in elk AEM-systeem worden uitgevoerd en kunnen ook beperkt zijn tot specifieke onderdelen.
* Een gestandaardiseerde gebruikersinterface hebben.
* Heb bewerkingsgedrag dat kan worden gevormd.
* Dialoogvensters van het gebruik die gebruikend subelementen worden gebouwd die op componenten van Granite UI worden gebaseerd.
* Zij worden ontwikkeld gebruikend [&#x200B; HTML &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html).
* Ze kunnen worden ontwikkeld om aangepaste componenten te maken die de standaardfunctionaliteit uitbreiden.

Omdat componenten modulair zijn, kunt u:

* Ontwikkel een nieuwe component op uw lokale instantie.
* Implementeer deze in de testomgeving.
* Implementeer deze in uw live ontwerpomgeving, waar auteurs en/of beheerders inhoud kunnen toevoegen en configureren.
* Implementeer deze in uw livepublicatieomgevingen, waar ze worden gebruikt om inhoud te renderen voor bezoekers van uw website.

Elke AEM-component:

* Is een middeltype.
* Is een inzameling van manuscripten die een specifieke functie volledig realiseren.
* Kan afzonderlijk functioneren, wat zowel in AEM als in een portaal betekent.

## AEM-kerncomponenten {#aem-core-components}

[&#x200B; de Componenten van de Kern van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en de onderhoudskosten van uw websites te drukken.

De Componenten van de Kern worden voorzien van AEM as a Cloud Service en het [&#x200B; WKND Leerprogramma &#x200B;](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustreert hoe te om componenten uit te voeren en te gebruiken. De componenten worden voorzien van al broncode en kunnen als zijn of als uitgangspunt voor gewijzigde of uitgebreide componenten worden gebruikt.

### Beschikbare componenten weergeven {#viewing-available-components}

Voor een overzicht van alle beschikbare componenten in uw instantie van AEM, gebruik de [&#x200B; Console van Componenten &#x200B;](/help/sites-cloud/authoring/components-console.md).

U kunt ook CRXDE Lite gebruiken om een lijst met alle beschikbare componenten in de opslagplaats op te halen.

1. Selecteer in **[!UICONTROL CRXDE Lite]** eerst **[!UICONTROL Tools]** op de werkbalk en vervolgens **[!UICONTROL Query]** , waarna het tabblad **[!UICONTROL Query]** wordt geopend.

1. Selecteer **[!UICONTROL Query]** as `XPath` op het tabblad **[!UICONTROL Type]** .

1. Voer in het invoerveld **[!UICONTROL Query]** de volgende tekenreeks in:

   `//element(*, cq:Component)`

1. Klik op **[!UICONTROL Execute]** en de componenten worden weergegeven.
