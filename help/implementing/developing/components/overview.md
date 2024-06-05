---
title: Overzicht van componenten
description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Overzicht van componenten {#components-overview}

Deze pagina biedt een overzicht van Adobe Experience Manager (AEM)-componenten, zoals [gebruikt voor het ontwerpen van pagina&#39;s](/help/sites-cloud/authoring/page-editor/components.md).

## Wat zijn componenten? {#what-are-components}

* Modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website te presenteren.
* Herbruikbaar.
* Ontwikkeld als zelfstandige eenheden in één map van de opslagplaats.
* Geen verborgen configuratiebestanden hebben.
* Ze kunnen andere componenten bevatten.
* Ze kunnen overal binnen elk AEM systeem worden uitgevoerd en kunnen ook beperkt zijn tot bepaalde onderdelen.
* Een gestandaardiseerde gebruikersinterface hebben.
* Heb bewerkingsgedrag dat kan worden gevormd.
* Dialoogvensters van het gebruik die gebruikend subelementen worden gebouwd die op componenten van Granite UI worden gebaseerd.
* Ze worden ontwikkeld met [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html).
* Ze kunnen worden ontwikkeld om aangepaste componenten te maken die de standaardfunctionaliteit uitbreiden.

Omdat componenten modulair zijn, kunt u:

* Ontwikkel een nieuwe component op uw lokale instantie.
* Implementeer deze in de testomgeving.
* Implementeer deze in uw live ontwerpomgeving, waar auteurs en/of beheerders inhoud kunnen toevoegen en configureren.
* Implementeer deze in uw livepublicatieomgevingen, waar ze worden gebruikt om inhoud te renderen voor bezoekers van uw website.

Elke AEM component:

* Is een middeltype.
* Is een inzameling van manuscripten die een specifieke functie volledig realiseren.
* Kan afzonderlijk functioneren, wat ofwel binnen AEM ofwel een portaal betekent.

## AEM-kerncomponenten {#aem-core-components}

[De AEM kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde WCM-componenten (Web Content Management) voor AEM om de ontwikkelingstijd te versnellen en de onderhoudskosten van uw websites te verlagen.

De Core Components worden geleverd met AEM as a Cloud Service en de [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustreert hoe u componenten kunt implementeren en gebruiken. De componenten worden voorzien van al broncode en kunnen als zijn of als uitgangspunt voor gewijzigde of uitgebreide componenten worden gebruikt.

### Beschikbare componenten weergeven {#viewing-available-components}

Voor een overzicht van alle beschikbare componenten in uw AEM instantie, gebruik [Componentenconsole](/help/sites-cloud/authoring/components-console.md).

U kunt ook CRXDE Lite gebruiken om een lijst met alle componenten in de opslagplaats op te halen.

1. In **[!UICONTROL CRXDE Lite]**, selecteert u **[!UICONTROL Tools]** vanaf de werkbalk, dan **[!UICONTROL Query]**, die de **[!UICONTROL Query]** tab.

1. In de **[!UICONTROL Query]** tab, selecteert u `XPath` als **[!UICONTROL Type]**.

1. In de **[!UICONTROL Query]** Voer de volgende tekenreeks in in het invoerveld:

   `//element(*, cq:Component)`

1. Klikken **[!UICONTROL Execute]** en de componenten worden vermeld.
