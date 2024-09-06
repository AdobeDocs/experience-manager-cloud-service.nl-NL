---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Gebruik de functie Asset Selector om de metagegevens en vertoningen van elementen in uw toepassing te zoeken, te zoeken en op te halen.
role: Admin, User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 0%

---

# Micro-Frontend element selecteren {#Overview}

Micro-Frontend Asset Selector biedt een gebruikersinterface die eenvoudig kan worden geïntegreerd met de [!DNL Experience Manager Assets] -opslagplaats, zodat u door de beschikbare digitale middelen in de opslagplaats kunt bladeren of deze kunt zoeken en deze kunt gebruiken in uw ontwerpervaring.

De gebruikersinterface van Micro-Frontend wordt beschikbaar gesteld in uw toepassingservaring gebruikend het pakket van de Selecteur van Activa. Alle updates van het pakket worden automatisch geïmporteerd en de nieuwste versie van Asset Selector wordt automatisch in de toepassing geladen.

![Overzicht](assets/overview.png)

Asset Selector biedt vele voordelen, zoals:

* Versnelling van integratie met om het even welke [ Adobe ](#integrate-asset-selector-adobe-app.md) of [ niet-Adobe ](#integrate-asset-selector.md) toepassingen die de bibliotheek van JavaScript Vanilla gebruiken.
* Eenvoudig te onderhouden, aangezien updates van het Assets Selector-pakket automatisch worden geïmplementeerd op de Asset Selector die beschikbaar is voor uw toepassing. Uw toepassing hoeft geen updates uit te voeren om de laatste wijzigingen te laden.
* Gemakkelijk aanpassen aangezien er eigenschappen beschikbaar zijn die de vertoning van de Selecteur van Activa binnen uw toepassing controleren.
* In de volledige tekst doorzoeken, uit-van-de-doos, en aangepaste filters om snel aan activa voor gebruik binnen de auteurservaring te navigeren.
* Mogelijkheid om binnen een IMS-organisatie te schakelen tussen opslagruimten voor het selecteren van bedrijfsmiddelen.
* De mogelijkheid om elementen te sorteren op naam, afmetingen en grootte en ze weer te geven in de weergave Lijst, Raster, Galerie of Waterval.

<!--Perform the following tasks to integrate and use Asset Selector with your [!DNL Experience Manager Assets] repository:

1. [Install Asset Selector](#installation)
2. [Integrate Asset Selector using Vanilla JS](#integration-using-vanilla-js)
3. [Use Asset Selector](#using-asset-selector)
-->

<!--
## Setting up Asset Selector {#asset-selector-setup}

![Asset Selector set up](assets/asset-selector-prereqs.png)
-->

## Vereisten{#prereqs}

U moet de volgende communicatiemethoden gebruiken:

* De toepassing wordt uitgevoerd op HTTPS.
* De URL van de toepassing bevindt zich in de lijst van gewenste personen van de IMS-client voor het doorsturen van URL&#39;s.
* De IMS-aanmeldstroom wordt geconfigureerd en weergegeven met een pop-up in de webbrowser. Daarom moeten pop-ups worden ingeschakeld of toegestaan in de doelbrowser.

Gebruik de bovenstaande voorwaarden als u de IMS-verificatieworkflow van de Asset Selector nodig hebt. Als u al bent geverifieerd met de IMS-workflow, kunt u in plaats daarvan de IMS-informatie toevoegen.

**zie meer**

* [Asset Selector integreren met een Adobe-app](#integrate-asset-selector-adobe-app.md)
* [Asset Selector integreren met een app die geen Adobe is](#integrate-asset-selector-non-adobe-app.md)
* [Dynamische API&#39;s voor het openen van media voor middelenselectie integreren](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!IMPORTANT]
>
> Deze opslagplaats is bedoeld als aanvullende documentatie waarin de beschikbare API&#39;s en gebruiksvoorbeelden voor de integratie van Asset Selector worden beschreven. Voordat u de functie Asset Selector gaat installeren of gebruiken, moet u controleren of uw organisatie beschikt over de toegang tot Asset Selector als onderdeel van het Experience Manager Assets as a Cloud Service-profiel. Als u niet provisioned bent, kunt u deze componenten niet integreren of gebruiken. Om levering te verzoeken, zou uw programma admin een steunkaartje moeten opheffen dat als P2 van de Admin Console wordt gemerkt en de volgende informatie omvatten:
>
>* Domeinnamen waarbij de integrerende toepassing wordt gehost.
>* Na provisioning ontvangt uw organisatie `imsClientId` , `imsScope` en een `redirectUrl` die overeenkomen met de gevraagde omgevingen die essentieel zijn voor de configuratie van Asset Selector. Zonder deze geldige eigenschappen kunt u de installatiestappen niet uitvoeren.

## Installatie {#installation}

De Selecteur van activa is beschikbaar via zowel ESM CDN (bijvoorbeeld, [ esm.sh ](https://esm.sh/)/[ kabel ](https://www.skypack.dev/)) als [ UMD ](https://github.com/umdjs/umd) versie.

In browsers die {versie 0} gebruiken UMD **(geadviseerd):**

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

In browsers met `import maps` steun gebruikend **versie van ESM CDN**:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

In Deno/de Federatie van de Module van het Pakket gebruikend **versie van ESM CDN**:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## Elementkiezer gebruiken {#using-asset-selector}

Nadat de Asset Selector is ingesteld en u bent gemachtigd om Asset Selector te gebruiken in uw [!DNL Adobe Experience Manager] -toepassing als [!DNL Cloud Service] -toepassing, kunt u elementen selecteren of verschillende andere bewerkingen uitvoeren om te zoeken naar uw elementen in de opslagplaats.

![ gebruiken-activa-selecteur ](assets/using-asset-selector.png)

* **A**: [ verberg/toon paneel ](#hide-show-panel)
* **B**: [ de schakelaar van de Bewaarplaats ](#repository-switcher)
* **C**: [ Assets ](#repository)
* **D**: [ Filters ](#filters)
* **E**: [ bar van het Onderzoek ](#search-bar)
* **F**: [ Sorterend ](#sorting)
* **G**: [ Sorterend in het stijgen of dalende orde ](#sorting)
* **H**: [ Mening ](#types-of-view)

### Deelvenster verbergen/tonen {#hide-show-panel}

Als u mappen in de linkernavigatie wilt verbergen, klikt u op het pictogram **[!UICONTROL Hide folders]** . Als u de wijzigingen ongedaan wilt maken, klikt u nogmaals op het pictogram **[!UICONTROL Hide folders]** .

### Repository-switch {#repository-switcher}

Met Asset Selector kunt u ook schakelen tussen opslagruimten voor middelenselectie. U kunt de opslagplaats van uw keus van drop-down selecteren beschikbaar in het linkerpaneel. De opslagruimteopties in de vervolgkeuzelijst zijn gebaseerd op de eigenschap `repositoryId` die is gedefinieerd in het `index.html` -bestand. Het is gebaseerd op de omgeving van de geselecteerde IMS-org die wordt benaderd door de aangemelde gebruiker. Consumenten kunnen een voorkeur `repositoryID` doorgeven en in dat geval stopt de Asset Selector met het renderen van de repo-switch en renderen van alleen de gegeven opslagplaats.

### Assets-opslagplaats

Het is een verzameling mappen met elementen die u kunt gebruiken om bewerkingen uit te voeren.

### Buiten-de-box filters {#filters}

De Kiezer van activa verstrekt ook uit-van-de-doos filteropties om uw onderzoeksresultaten te verfijnen. De volgende filters zijn beschikbaar:

* **[!UICONTROL Status]:** bevat de huidige status van het element tussen `all` , `approved`, `rejected` of `no status` .
* **[!UICONTROL File type]:** includes `folder`, `file`, `images`, `documents` of `video` .
* **[!UICONTROL Expiration status]:** verwijst naar de elementen op basis van de vervalduur. U kunt het selectievakje `[!UICONTROL Expired]` inschakelen om verlopen elementen te filteren, of u kunt `[!UICONTROL Expiration Duration]` van een element instellen om elementen weer te geven op basis van de vervaldatum. Wanneer een element al is verlopen of bijna is verlopen, lijkt een badge om het zelfde aan te geven. Bovendien kunt u bepalen of u het gebruik (of slepen en neerzetten) van een verlopen element wilt toestaan. Zie meer over [ verlopen activa ](#asset-selector-customization.md#customize-expired-assets) aanpassen. Door gebrek, wordt het **Verlopen Soon** badge getoond voor activa die in de volgende 30 dagen verlopen. U kunt de vervaldatum echter configureren met de eigenschap `expirationDate` .

  >[!TIP]
  >
  > Als u elementen wilt weergeven of filteren op basis van de vervaldatum in de toekomst, geeft u het datumbereik voor de toekomst op in het veld `[!UICONTROL Expiration Duration]` . Het toont de activa met **die spoedig** badge op hen verlopen.

* **[!UICONTROL MIME type]:** includes `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`.
* **[!UICONTROL Image Size]:** omvat minimum/maximumbreedte, minimum/maximumhoogte van beeld.

  ![ spoorstaaf-mening-voorbeeld ](assets/filters-asset-selector.png)

### Aangepaste zoekopdracht

Met Asset Selector kunt u naast de zoekopdracht in volledige tekst ook elementen in bestanden zoeken met behulp van een aangepaste zoekopdracht. U kunt aangepaste zoekfilters gebruiken in zowel de modusweergave als de spoorweergave.

![ douane-onderzoek ](assets/custom-search1.png)

U kunt ook een standaardzoekfilter maken om de velden op te slaan waarnaar u vaak zoekt en deze later te gebruiken. Als u een aangepaste zoekopdracht naar uw elementen wilt maken, kunt u de eigenschap `filterSchema` gebruiken.

### Zoekbalk {#search-bar}

Met Asset Selector kunt u een volledige tekstzoekopdracht uitvoeren naar elementen in de geselecteerde opslagplaats. Als u bijvoorbeeld het trefwoord `wave` in de zoekbalk typt, worden alle elementen met het trefwoord `wave` dat in een van de metagegevenseigenschappen wordt vermeld, weergegeven.

### Sorteren {#sorting}

U kunt elementen in de Asset Selector sorteren op naam, afmetingen of grootte van een element. U kunt de elementen ook in oplopende of aflopende volgorde sorteren.

### Weergavetypen {#types-of-view}

Met Asset Selector kunt u het element in vier verschillende weergaven weergeven:

* **![lijstmening ](assets/do-not-localize/list-view.png)[!UICONTROL List View]** de lijstmening toont scrollable dossiers en omslagen in één enkele kolom.
* **![netmening ](assets/do-not-localize/grid-view.png)[!UICONTROL Grid View]** de netmening toont scrollable dossiers en omslagen in een net van rijen en kolommen.
* **![galeriemening ](assets/do-not-localize/gallery-view.png)[!UICONTROL Gallery View]** de de vertoningendossiers of omslagen van de galeriemening in een centrum-gesloten horizontale lijst.
* **![watervalmening ](assets/do-not-localize/waterfall-view.png)[!UICONTROL Waterfall View]** De watervalmening toont dossiers of omslagen in de vorm van een Bridge.

**Grafische van het Overzicht**


## Meer informatie over sleutelmogelijkheden {#key-capabilities-asset-selector}

<table>
<tr>
    <td>
        <img src="assets/integrate-asset-selector.gif" width="70px" height="70px" alt="Afbeelding voor middelenkiezer integreren"><br/>
        <a href="integrate-asset-selector.md"> integreer de Kiezer van Activa </a>
        <p>
        <em> Leer diverse mogelijkheden om de Selecteur van Activa met veelvoudige toepassingen te integreren.
        </p>
     </td>
    <td>
        <img src="assets/with-adobe-app.gif" width="70px" height="70px" alt="Asset Selector integreren met grafische Adobe voor toepassingen"><br/>
        <a href="integrate-asset-selector.md"> integreer de Selector van Activa met de toepassingen van de Adobe </a>
        <p>
        <em> ontdekt hoe te om de Selecteur van Activa met diverse toepassingen van de Adobe te integreren.</em>
        </p>
    </td>
    <td>
        <img src="assets/third-party-app.gif" width="70px" height="70px" alt="Afbeelding voor middelenkiezer integreren"><br/>
        <a href="integrate-asset-selector.md"> integreer de Selector van Activa met derdetoepassingen </a>
        <p>
        <em> dig omhoog de mogelijkheden om de Selector van Activa met niet-Adobe toepassingen te integreren.</em>
        </p>
    </td>
    <td>
        <img src="assets/with-dynamic-media-open-api.gif" width="70px" height="70px" alt="Afbeelding voor middelenkiezer integreren"><br/>
        <a href="integrate-asset-selector.md"> integreer de Selector van Activa met Dynamic Media Open APIs </a>
        <p>
        <em> Begrijp hoe te om de Selecteur van Activa met Dynamic Media te integreren Open APIs.</em>
        </p>
     </td>
</tr>
<tr>
    <td>
        <img src="assets/asset-selector-examples.gif" width="70px" height="70px" alt="Eigenschappen van Asset Selector, afbeelding"><br/>
        <a href="asset-selector-customization.md"> Eigenschappen van de Selecteur van Activa </a>
        <p>
        <em> Leer de grondbeginselen van het aanpassen van diverse componenten van de Selector van Activa, zoals filters, selectie van activa, verlopen activa, en veel meer. </em>
        </p>
    </td>
    <td>
        <img src="assets/asset-selector-properties.gif" width="70px" height="70px" alt="Voorbeelden van Asset Selector"><br/>
        <a href="asset-selector-customization.md"> Voorbeelden van de Selecteur van Activa </a>
        <p>
        <em> begrijp het gebruik van eigenschappen op een praktische manier. </em>
        </p>
    </td>
    <td>
        <img src="assets/customize-asset-selector.gif" width="70px" height="70px" alt="Afbeelding voor middelenkiezer aanpassen"><br/>
        <a href="asset-selector-customization.md"> Aanpassingen van de Selecteur van Activa </a>
        <p>
        <em> vormt en past diverse componenten van de Selecteur van Activa aan die op uw bruikbaarheid worden gebaseerd. </em>
        </p>
    </td>
    <td></td>
</tr>
</table>

>[!MORELIKETHIS]
>
>* [ de aanpassing van de Selecteur van Activa ](/help/assets/asset-selector-customization.md)
>* [ integreer de Selector van Activa met diverse toepassingen ](/help/assets/integrate-asset-selector.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
>* [ integreer de dynamische media van de Selecteur van Activa open APIs ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
