---
title: Overzicht van componenten
description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Overzicht van componenten {#components-overview}

Deze pagina biedt een overzicht van Adobe Experience Manager (AEM)-componenten, zoals [gebruikt voor het ontwerpen van pagina&#39;s](/help/sites-cloud/authoring/fundamentals/components.md).

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
* worden ontwikkeld met [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html).
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

## AEM-kerncomponenten {#aem-core-components}

[De AEM kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde WCM-componenten (Web Content Management) voor AEM om de ontwikkelingstijd te versnellen en de onderhoudskosten van uw websites te verlagen.

De Core Components worden geleverd met AEM as a Cloud Service en de [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustreert hoe te om componenten uit te voeren en te gebruiken. De componenten worden voorzien van al broncode en kunnen als zijn of als uitgangspunt voor gewijzigde of uitgebreide componenten worden gebruikt.

### Beschikbare componenten weergeven {#viewing-available-components}

Voor een overzicht van alle beschikbare componenten in uw AEM instantie, gebruik [Componentenconsole](/help/sites-cloud/authoring/features/components-console.md).

U kunt ook CRXDE Lite gebruiken om een lijst met alle componenten in de opslagplaats op te halen.

1. In **[!UICONTROL CRXDE Lite]**, selecteert u **[!UICONTROL Tools]** vanaf de werkbalk, dan **[!UICONTROL Query]**, die de **[!UICONTROL Query]** tab.

1. In de **[!UICONTROL Query]** tab, selecteert u `XPath` als **[!UICONTROL Type]**.

1. In de **[!UICONTROL Query]** invoerveld, voer de volgende tekenreeks in:

   `//element(*, cq:Component)`

1. Klikken **[!UICONTROL Execute]** en de componenten worden vermeld.
