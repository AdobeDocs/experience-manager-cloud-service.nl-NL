---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Gebruik de functie Asset Selector om de metagegevens en vertoningen van elementen in uw toepassing te zoeken, te zoeken en op te halen.
role: Admin, User
exl-id: 62b0b857-068f-45b7-9018-9c59fde01dc3
source-git-commit: 97a432270c0063d16f2144d76beb437f7af2895a
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 0%

---

# Micro-Frontend element selecteren {#Overview}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Micro-Frontend Asset Selector biedt een gebruikersinterface die eenvoudig kan worden geïntegreerd met de [!DNL Experience Manager Assets] -opslagplaats, zodat u door de beschikbare digitale middelen in de opslagplaats kunt bladeren of deze kunt zoeken en deze kunt gebruiken in uw ontwerpervaring.

De gebruikersinterface van Micro-Frontend wordt beschikbaar gesteld in uw toepassingservaring gebruikend het pakket van de Selecteur van Activa. Alle updates van het pakket worden automatisch geïmporteerd en de nieuwste versie van Asset Selector wordt automatisch in de toepassing geladen.

![Overzicht](assets/overview.png)

Asset Selector biedt vele voordelen, zoals:

* Versnelling van integratie met om het even welke [ Adobe ](/help/assets/integrate-asset-selector-adobe-app.md) of [ niet-Adobe ](/help/assets/integrate-asset-selector-non-adobe-app.md) toepassingen die de bibliotheek van JavaScript Vanilla gebruiken.
* Eenvoudig te onderhouden, aangezien updates van het Assets Selector-pakket automatisch worden geïmplementeerd op de Asset Selector die beschikbaar is voor uw toepassing. Uw toepassing hoeft geen updates uit te voeren om de laatste wijzigingen te laden.
* Gemakkelijk aan te passen omdat er eigenschappen beschikbaar zijn die de Asset Selector-weergave binnen uw toepassing regelen.
* Zoeken in volledige tekst, kant-en-klare en aangepaste filters om snel naar assets te navigeren voor gebruik binnen de ontwerpervaring.
* Mogelijkheid om binnen een IMS-organisatie tussen opslagplaatsen te schakelen voor activaselectie.
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

* De hosttoepassing wordt uitgevoerd op HTTPS.
* U kunt de toepassing niet uitvoeren op `localhost` . Als u de Asset Selector op uw lokale computer wilt integreren, moet u een aangepast domein maken, bijvoorbeeld `[https://<your_campany>.localhost.com:<port_number>]` , en dit aangepaste domein toevoegen in de `redirectUrl list` .
* U kunt `ADOBE_PROVIDED_CLIENT_ID` configureren en toevoegen aan de omgevingsvariabele van AEM Cloud Service met de respectievelijke `imsClientId` .
  {het milieu van identiteitskaart van de Cliënt IMS van de Selecteur van activa 0} ](assets/asset-selector-ims-client-id-env.png)![
* De lijst van het werkingsgebied IMS moet in de omgevingsconfiguratie worden bepaald.
* De URL van de toepassing bevindt zich in de lijst van gewenste personen van de IMS-client voor het doorsturen van URL&#39;s.
* De IMS-aanmeldstroom wordt geconfigureerd en weergegeven met een pop-up in de webbrowser. Daarom moeten pop-ups worden ingeschakeld of toegestaan in de doelbrowser.

Gebruik de bovenstaande vereisten als u de IMS-verificatiewerkstroom van Asset Selector vereist. Als u al bent geverifieerd met de IMS-werkstroom, kunt u in plaats daarvan de IMS-gegevens toevoegen.

**Lees meer**

* [Asset Selector integreren met een Adobe-app](/help/assets/integrate-asset-selector-adobe-app.md)
* [Asset Selector integreren met een app die niet van Adobe is](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Dynamische API&#39;s voor het openen van media integreren in Asset Selector](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!IMPORTANT]
>
> Deze opslagplaats is bedoeld als aanvullende documentatie waarin de beschikbare API&#39;s en gebruiksvoorbeelden voor de integratie van Asset Selector worden beschreven. Voordat u de functie Asset Selector gaat installeren of gebruiken, moet u controleren of uw organisatie de toegang tot Asset Selector heeft ingericht als onderdeel van het Experience Manager Assets as a Cloud Service-profiel. Als u niet provisioned bent, kunt u deze componenten niet integreren of gebruiken. Om levering te verzoeken, zou uw programma admin een steunkaartje moeten opheffen dat als P2 van Admin Console wordt gemerkt en de volgende informatie omvatten:
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

Zodra de Asset Selector is ingesteld en u bent geverifieerd om Asset Selector te gebruiken met uw [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] toepassing, kunt u activa selecteren of verschillende andere bewerkingen uitvoeren om naar uw activa in de opslagplaats te zoeken.

![gebruikmakende-activa-selector](assets/using-asset-selector.png)

* **A**: [Paneel Verbergen/Tonen](#hide-show-panel)
* **B**: [Wissel voor opslagplaats](#repository-switcher)
* **C**: [Activa](#repository)
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
* **[!UICONTROL Expiration status]:** verwijst naar de elementen op basis van de vervalduur. U kunt het selectievakje `[!UICONTROL Expired]` inschakelen om verlopen elementen te filteren, of u kunt `[!UICONTROL Expiration Duration]` van een element instellen om elementen weer te geven op basis van de vervaldatum. Wanneer een element al is verlopen of bijna is verlopen, lijkt een badge om het zelfde aan te geven. Bovendien kunt u bepalen of u het gebruik (of slepen en neerzetten) van een verlopen element wilt toestaan. Zie meer over [ verlopen activa ](/help/assets/asset-selector-customization.md#customize-expired-assets) aanpassen. Door gebrek, wordt het **Verlopen Soon** badge getoond voor activa die in de volgende 30 dagen verlopen. U kunt de vervaldatum echter configureren met de eigenschap `expirationDate` .

  >[!TIP]
  >
  > Als u elementen wilt weergeven of filteren op basis van de vervaldatum in de toekomst, geeft u het datumbereik voor de toekomst op in het veld `[!UICONTROL Expiration Duration]` . Het toont de activa met **die spoedig** badge op hen verlopen.

* **[!UICONTROL MIME type]:** includes `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`.
* **[!UICONTROL Image Size]:** inclusief minimale/maximale breedte, minimale/maximale hoogte van de afbeelding.

  ![spoor-weergave-voorbeeld](assets/filters-asset-selector.png)

### Aangepast zoeken

Met Asset Selector kunt u naast de zoekopdracht in volledige tekst ook elementen in bestanden zoeken met behulp van een aangepaste zoekopdracht. U kunt aangepaste zoekfilters gebruiken in zowel de modusweergave als de spoorweergave.

![ douane-onderzoek ](assets/custom-search1.png)

U kunt ook een standaardzoekfilter maken om de velden op te slaan waarnaar u vaak zoekt en deze later te gebruiken. Als u een aangepaste zoekopdracht naar uw elementen wilt maken, kunt u de eigenschap `filterSchema` gebruiken.

### Zoekbalk {#search-bar}

Met Asset Selector kunt u een volledige tekstzoekopdracht uitvoeren naar elementen in de geselecteerde opslagplaats. Als u bijvoorbeeld het trefwoord `wave` in de zoekbalk typt, worden alle elementen met het trefwoord `wave` dat in een van de metagegevenseigenschappen wordt vermeld, weergegeven.

### Sorteren {#sorting}

U kunt elementen in de Asset Selector sorteren op naam, afmetingen of grootte van een element. U kunt de elementen ook in oplopende of aflopende volgorde sorteren.

### Weergavetypen {#types-of-view}

Met Asset Selector kunt u het element in vier verschillende weergaven weergeven:

* ![lijstweergave](assets/do-not-localize/list-view.png) [!UICONTROL **Lijstweergave**] In de lijstweergave worden schuifbare bestanden en mappen in één kolom weergegeven.
* ](assets/do-not-localize/grid-view.png) [!UICONTROL **de mening van het Net**] van de netmening toont scrollable dossiers en omslagen in een net van rijen en kolommen.![
* ![galerijweergave](assets/do-not-localize/gallery-view.png) [!UICONTROL **Galerijweergave**] In de galerijweergave worden bestanden of mappen weergegeven in een centraal vergrendelde horizontale lijst.
* ![watervalweergave](assets/do-not-localize/waterfall-view.png) [!UICONTROL **Watervalweergave]** In de watervalweergave worden bestanden of mappen weergegeven in de vorm van een brug.

## Meer informatie over de belangrijkste mogelijkheden {#key-capabilities-asset-selector}

<table>
<tr>
    <td>
        <img src="assets/integrate-asset-selector.gif" width="70px" height="70px" alt="Afbeelding van Asset Selector integreren"><br/>
        <a href="integrate-asset-selector.md"> integreer de Kiezer van Activa </a>
        <p>
        <em> Leer diverse mogelijkheden om de Selecteur van Activa met veelvoudige toepassingen te integreren.
        </p>
     </td>
    <td>
        <img src="assets/with-adobe-app.gif" width="70px" height="70px" alt="Asset Selector integreren met grafische Adobe-toepassingen"><br/>
        <a href="integrate-asset-selector.md"> integreer de Selector van Activa met de toepassingen van Adobe </a>
        <p>
        <em> ontdekt hoe te om de Selecteur van Activa met diverse toepassingen van Adobe te integreren.</em>
        </p>
    </td>
    <td>
        <img src="assets/third-party-app.gif" width="70px" height="70px" alt="Afbeelding voor middelenkiezer integreren"><br/>
        <a href="integrate-asset-selector.md"> integreer de Selector van Activa met derdetoepassingen </a>
        <p>
        <em> dig omhoog de mogelijkheden om de Selector van Activa met toepassingen te integreren niet-Adobe.</em>
        </p>
    </td>
    <td>
        <img src="assets/with-dynamic-media-open-api.gif" width="70px" height="70px" alt="Afbeelding voor middelenkiezer integreren"><br/>
        <a href="integrate-asset-selector.md"> integreer de Selector van Activa met Dynamische Media Open APIs </a>
        <p>
        <em> Begrijp hoe te om de Selector van Activa met Dynamische Media te integreren Open APIs.</em>
        </p>
     </td>
     <td>
        <img src="assets/asset-selector-examples.gif" width="70px" height="70px" alt="Afbeelding met eigenschappen van de activakiezer"><br/>
        <a href="asset-selector-customization.md">Eigenschappen van activakiezer</a>
        <p>
        <em>Leer de basisprincipes van het aanpassen van verschillende onderdelen van Asset Selector, zoals filters, selectie van activa, verlopen items en nog veel meer. </em>
        </p>
    </td>
</tr>
<tr>
    <td>
        <img src="assets/asset-selector-properties.gif" width="70px" height="70px" alt="Afbeelding met voorbeelden van Asset Selector"><br/>
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
    <td>
        <img src="assets/asset-selector-upload.gif" width="70px" height="70px" alt="Uploadafbeelding voor middelenkiezer"><br/>
        <a href="asset-selector-upload.md"> de Selecteur van Activa uploadt </a>
        <p>
        <em> Leer hoe u dossiers of omslagen aan de Selecteur van Activa van uw lokaal of derdedossiersysteem kunt uploaden. </em>
        </p>
    </td>
     <td>
        <img src="assets/asset-selector-collections.gif" width="70px" height="70px" alt="Verzamelingen voor middelenkiezer, afbeelding"><br/>
        <a href="asset-selector-collections.md"> Verzamelingen van de Selecteur van Activa </a>
        <p>
        <em> Leer hoe te om inzamelingen binnen de Selector van Activa te gebruiken gebruikend de bewaarplaats van Experience Manager. </em>
        </p>
    </td>
    <td>
    </td>
</tr>
</table>

>[!MORELIKETHIS]
>
>* [ de aanpassingen van de Selecteur van Activa ](/help/assets/asset-selector-customization.md)
>* [ integreer de Selector van Activa met diverse toepassingen ](/help/assets/integrate-asset-selector.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
>* [ integreer de Selector van Activa met Dynamische Media met mogelijkheden OpenAPI ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
