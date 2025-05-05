---
title: Micro-Frontend Inhoud selecteren voor Adobe Experience Manager as a Cloud Service
description: Met de Micro-Front Content Fragment Selector kunt u inhoudsfragmenten zoeken, zoeken en ophalen vanuit uw toepassing.
role: Admin, User
source-git-commit: 32e1b3cef768b420f32b70202ddadc80db2b74e8
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Micro-front-Content Fragment selecteren {#micro-frontend-content-fragment-selector}

De Micro-Front Content Fragment Selector biedt een gebruikersinterface die eenvoudig kan worden geïntegreerd met de Adobe Experience Manager (AEM) as a Cloud Service-opslagplaats. Met de interface kunt u in de opslagplaats door Content Fragments bladeren of deze doorzoeken en in uw toepassing gebruiken.

De gebruikersinterface Micro-Frontend wordt beschikbaar gesteld in uw toepassing gebruikend het pakket van de Selector van het Fragment van de Inhoud. Alle updates van het pakket worden automatisch geïmporteerd en in de toepassing geladen.

![ Micro-Front de Selector van het Fragment van de Inhoud - Overzicht ](/help/headless/assets/content-fragment-selector-overview.png)

De kiezer voor het inhoudsfragment biedt veel voordelen, zoals:

* Eenvoudige integratie met alle Adobe-toepassingen.
* Eenvoudig te onderhouden, aangezien updates van het pakket Content Fragment Selector automatisch worden geïmplementeerd in de Content Fragment Selector die beschikbaar is voor uw toepassing. Dit betekent dat uw toepassing geen actie hoeft te ondernemen om de laatste wijzigingen te laden.
* Gemakkelijk aan te passen, gebruikend eigenschappen die de vertoning van de Selecteur van het Fragment van de Inhoud binnen uw toepassing controleren.
* Met zoeken in volledige tekst en aanpasbare filters kunt u snel Content Fragments binnen de ontwerpervaring navigeren.
* Mogelijkheid om te schakelen tussen opslagruimten binnen een IMS-organisatie voor de selectie van inhoudsfragmenten.
* U kunt inhoudsfragmenten sorteren en deze weergeven in de geselecteerde weergave.

## Vereisten {#prerequisites}

### IMS-verificatie {#ims-authentication}

Als u de IMS-verificatieworkflow nodig hebt, moet u ervoor zorgen dat:

* De toepassing wordt uitgevoerd op `HTTPS` .
* De URL van de toepassing staat in de lijst met toegestane omleidings-URL&#39;s voor de IMS-client.
* De IMS-aanmeldstroom wordt geconfigureerd en weergegeven met een pop-up in de webbrowser. Daarom moeten pop-ups worden ingeschakeld of toegestaan in de doelbrowser.

Als uw toepassing al is geverifieerd met de IMS-workflow, kunt u in plaats daarvan de juiste IMS-informatie toevoegen.

## Installatie {#installation}

Gebruik de component `ContentFragmentSelector` . Er zijn verschillende installatieopties:

1. NPM-register (private Adobe-register)

   * Voeg het volgende toe aan `.npmrc`:

     ```html
     @aem-sites:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-sites-release/
     ```

   * Vervolgens installeren

     ```html
     npm install @aem-sites/content-fragment-selector
     ```

1. Git Repository

   * Voeg het volgende toe aan `package.json` afhankelijkheden:

     ```html
     "@aem-sites/content-fragment-selector": "git+https://github.com/adobe/<your-private-repo-url>.git#version"
     ```

## De Content Fragment Selector gebruiken {#using-the-Content-Fragment-selector}

Als de Content Fragment Selector is ingesteld en geverifieerd voor gebruik van de Content Fragment Selector met uw AEM as a Cloud Service-toepassing, kunt u Content Fragments selecteren of verschillende andere bewerkingen uitvoeren om te zoeken naar uw fragmenten in de dataopslag:

![ de Selector van het Fragment van de Inhoud ](/help/headless/assets/content-fragment-selector-using.png)

* Met de **1&rbrace; selecteur van de Bewaarplaats &lbrace;bij het hoogste recht, kunt u de bewaarplaats selecteren u wilt gebruiken**
* In het linkerdeelvenster kunt u:
   * Mappen verbergen of weergeven in de geselecteerde opslagplaats
   * Selecteer een specifieke map om inhoudsfragmenten in die map weer te geven
* In het hoofdvenster kunt u:
   * Inhoudsfragmenten selecteren
   * Zoeken naar inhoudsfragmenten
   * De huidige lijst sorteren op basis van verschillende kolommen; beide oplopend of aflopend
   * Zie de weergaveformaat-indicator
   * Filters weergeven, verbergen en opgeven

### Deelvenster verbergen/tonen {#hide-show-panel}

Om omslagen in de linkernavigatie te verbergen, klik **de omslagen van de Huid** pictogram. Om de veranderingen ongedaan te maken, klik opnieuw het **Omslagen van de Huid** pictogram.

### Repository-switch {#repository-switcher}

Met de Content Fragment Selector kunt u een opslagplaats voor fragmentselectie selecteren.

U kunt de bewaarplaats van uw keus van **Repository** drop-down selecteren, beschikbaar bij de bovenkant van het belangrijkste paneel.

![ de Selector van het Fragment van de Inhoud ](/help/headless/assets/content-fragment-repository-selector.png)

De opslagruimteopties in de vervolgkeuzelijst zijn gebaseerd op de eigenschap `repositoryId` die is gedefinieerd in het `index.html` -bestand. Deze eigenschap is gebaseerd op de omgeving van de geselecteerde IMS-org die wordt benaderd door de gebruiker die momenteel is aangemeld.

Consumenten kunnen een voorkeursoptie `repositoryID` doorgeven om fragmenten te renderen uit een specifieke opslagplaats en het renderen van de repository switch te stoppen.

### Inhoudsfragmenten, mappen {#content-fragments-folders}

De gegevensopslagruimte van Inhoudsfragmenten is een verzameling mappen voor inhoudsfragmenten die u kunt gebruiken om bewerkingen uit te voeren.

### Filters {#filters}

De kiezer voor inhoudsfragmenten beschikt ook over filteropties buiten de doos om de zoekresultaten te verfijnen. Er zijn verschillende filters beschikbaar, waaronder:

* **model van het Fragment**
* **Localization**
* **Status**: de huidige staat van het fragment; `New`, `Draft`, `Published`, `Modified`, `Unpublished`
* Tags
* Gebruikers
* Termijnen en data

![ de opties van de Filter ](/help/headless/assets/content-selector-filters.png)

U kunt ook een standaardzoekfilter maken om op te slaan voor toekomstig gebruik. U kunt de eigenschap `filterSchema` gebruiken om aangepaste zoekfilters voor uw inhoudsfragmenten te maken.

### Zoekbalk {#search-bar}

Met de Content Fragment Selector kunt u een volledige tekstzoekopdracht uitvoeren naar fragmenten in de geselecteerde opslagplaats. Als u bijvoorbeeld het trefwoord `wave` typt in de zoekbalk, worden alle fragmenten weergegeven waarvan het trefwoord `wave` wordt vermeld in een van de eigenschappen van de metagegevens.

### Sorteren {#sorting}

U kunt fragmenten in de Inhoudsfragmentkiezer op verschillende eigenschappen sorteren. U kunt de fragmenten ook in oplopende of aflopende volgorde sorteren.

### Type weergave {#view-type}

Met de optie Selector voor inhoudsfragment kunt u het fragment weergeven in het volgende:

* **Mening van de Lijst**
