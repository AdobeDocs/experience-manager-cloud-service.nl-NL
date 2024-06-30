---
title: Content Hub-gebruikersinterface configureren
description: Content Hub-gebruikersinterface configureren
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Content Hub-gebruikersinterface configureren {#configure-content-hub-user-interface}

<!-- ![Download assets](assets/download-asset.jpg) -->
![Elementen configureren op Content Hub](assets/configure-assets.png)

Met Experience Manager Assets kunnen beheerders de opties configureren die beschikbaar zijn in de Content Hub-gebruikersinterface. Op basis van de configuratieopties die door de beheerders zijn geselecteerd, kunnen de Content Hub-gebruikers velden weergeven op Content Hub. De configuratieopties omvatten:

* Filters die beschikbaar zijn voor gebruikers tijdens het zoeken naar elementen.

* De gegevens of eigenschappen van het element die beschikbaar zijn voor elk element.

* Metagegevensvelden die beschikbaar zijn voor gebruikers wanneer ze elementen toevoegen aan Content Hub.

* Veld voor metagegevens van middelen die beschikbaar zijn voor zoekopdrachten op Content Hub.

* Inhoud markeren die u voor uw organisatie moet weergeven.

* Aangepaste koppelingen die u op Content Hub moet opnemen, naast elementen, verzamelingen en inzichten.

## Vereisten {#prerequisites-configuration-ui}

[Content Hub-beheerders](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) U kunt de configuratieopties instellen voor andere gebruikers binnen uw organisatie.

## Toegang tot configuratieopties op Content Hub {#access-configuration-options-content-hub}

Configuratieopties openen op Content Hub:

1. Klik op het gebruikerspictogram in het rechterdeelvenster.

1. In de **[!UICONTROL Product Settings]** sectie, selecteert u **[!UICONTROL Configurations]**.

   ![Toegang tot configuratieopties op Content Hub](assets/access-content-hub-configuration-ui.png)

## Configuratieopties beheren in Content Hub {#manage-configuration-options}

Beheer de volgende configuratieopties voor uw gebruikers:

* [Importeren](#configure-import-options-content-hub)

* [Filters](#configure-filters-content-hub)

* [Gegevens van element](#configure-asset-details-content-hub)

* [Zoeken](#configure-metadata-search-content-hub)

* [Branding](#configure-branding-content-hub)

* [Aangepaste koppelingen](#configure-custom-links-content-hub)

### Importeren {#configure-import-options-content-hub}

U kunt de meta-gegevensgebieden vormen die aan de gebruikers tijdens het uploaden van of het invoeren van activa aan het portaal van Content Hub, zoals de Naam van de Campagne, Sleutelwoorden, Kanalen, Tijdkader, Gebied, etc. tonen. Voer daartoe de volgende stappen uit:

1. Op de [Configuraties](#access-configuration-options-content-hub) gebruikersinterface, klik **[!UICONTROL Import]**.

1. Klik op **[!UICONTROL Add metadata]**.

1. Geef een label voor de eigenschap op en wijs deze toe aan een eigenschap met de opdracht **[!UICONTROL Metadata]** en selecteert u het invoertype voor de metagegevens van het nieuwe element.

1. Klik op de knop **[!UICONTROL Required field]** Schakel deze optie in om het nieuwe metagegevensveld verplicht te maken voor gebruikers tijdens het uploaden van nieuwe elementen.

1. Klik op **[!UICONTROL Confirm]**. De nieuwe metagegevens worden weergegeven in de lijst met bestaande eigenschappen van elementen.

1. Klikken **[!UICONTROL Save]** om de wijzigingen toe te passen.

U kunt ook op ![Pictogram Bewerken](assets/do-not-localize/edit_icon.svg)Als u de labels wilt bewerken, maakt u deze velden verplicht of niet verplicht voor gebruikers wanneer u elementen uploadt met behulp van de **[!UICONTROL Required field]** Schakel deze optie in of klik op het pictogram Verwijderen om een eigenschap voor metagegevens te verwijderen.

Klik op de knop **[!UICONTROL Auto-approval]** Schakel deze optie in als u alle elementen die u toevoegt aan de Experience Manager Assets-opslagplaats automatisch wilt laten goedkeuren, zodat ze direct beschikbaar zijn in Content Hub. Anders moeten DAM-auteurs of -beheerders de elementen handmatig goedkeuren om deze beschikbaar te maken op Content Hub. De schakeloptie is standaard ingesteld op Uit.

Klikken **[!UICONTROL Save]** na alle wijzigingen om de wijzigingen toe te passen.

![Configuration UI upload details on Content Hub](assets/configuration-ui-upload-details.png)

Metagegevens die zijn ingeschakeld op de gebruikersinterfaceweergave van de configuratie op de pagina voor het uploaden van elementen:

![Metagegevens uploaden naar Content Hub](assets/configuration-ui-add-assets.png)

### Filters {#configure-filters-content-hub}

Met Content Hub kunnen beheerders filters configureren die worden weergegeven terwijl ze naar elementen zoeken. Voer de volgende stappen uit om een nieuw filter toe te voegen:

1. Op de [Configuraties](#access-configuration-options-content-hub) gebruikersinterface, klik **[!UICONTROL Filters]**.

1. Klik op **[!UICONTROL Add filters]**.

1. Geef een label voor het filter op en wijs het toe aan een eigenschap met de opdracht **[!UICONTROL Metadata]** en selecteert u het invoertype voor het nieuwe filter.
1. Klik op **[!UICONTROL Confirm]**. Het nieuwe filter wordt weergegeven in de lijst met bestaande filters.

1. Klikken **[!UICONTROL Save]** om de wijzigingen toe te passen zodat het nieuwe filter op de zoekpagina wordt weergegeven terwijl elementen worden gefilterd.

U kunt ook op ![Pictogram Bewerken](assets/do-not-localize/edit_icon.svg), beschikbaar naast elk beschikbaar filter, om de labels te bewerken of op het verwijderpictogram te klikken om een bestaand filter te verwijderen. Klikken **[!UICONTROL Save]** na alle wijzigingen om de wijzigingen toe te passen.

![Configuratie-UI-filters op Content Hub](assets/configuration-ui-filters.png)

De filters die op de vertoning van het Gebruikersinterface van de Configuratie op de pagina van het Onderzoek worden toegelaten:

![Zoeken op Content Hub](assets/filters-for-search.png)


### Gegevens van element {#configure-asset-details-content-hub}

U kunt ook de elementeigenschappen configureren die voor elk element worden weergegeven, zoals de bestandsnaam, titel, indeling, grootte, enzovoort. Voer daartoe de volgende stappen uit:

1. Op de [Configuraties](#access-configuration-options-content-hub) gebruikersinterface, klik **[!UICONTROL Asset details]**.

1. Klik op **[!UICONTROL Add metadata]**.

1. Geef een label voor de eigenschap op en wijs deze toe aan een eigenschap met de opdracht **[!UICONTROL Metadata]** en selecteert u het invoertype voor de metagegevens van het nieuwe element.
1. Klik op **[!UICONTROL Confirm]**. De nieuwe metagegevens worden weergegeven in de lijst met bestaande eigenschappen van elementen.

1. Klikken **[!UICONTROL Save]** om de wijzigingen toe te passen zodat de nieuwe eigenschap wordt weergegeven op de pagina met elementdetails.

U kunt ook op ![Pictogram Bewerken](assets/do-not-localize/edit_icon.svg), beschikbaar naast elke beschikbare eigenschap, om de labels te bewerken of op het verwijderpictogram te klikken om bestaande elementdetails te verwijderen. Klikken **[!UICONTROL Save]** na alle wijzigingen om de wijzigingen toe te passen.

![Configuratie-UI-elementgegevens op Content Hub](assets/configuration-ui-asset-details.png)

De eigenschappen die op de vertoning van het Gebruikersinterface van de Configuratie op de pagina van de Details van Activa worden toegelaten:

![Eigenschappen van middelen op Content Hub](assets/config-ui-asset-properties.png)

### Zoeken {#configure-metadata-search-content-hub}

Beheerders kunnen de metagegevensvelden definiëren die worden doorzocht wanneer een gebruiker een zoekcriterium opgeeft op Content Hub. Voer de volgende stappen uit:

1. Op de [Configuraties](#access-configuration-options-content-hub) gebruikersinterface, klik **[!UICONTROL Add metadata]**.

1. Geef het metagegevensveld op en klik op **[!UICONTROL Confirm]**.

1. Klikken **[!UICONTROL Save]** om de wijzigingen toe te passen, zodat de nieuwe eigenschap metadata wordt weergegeven in de lijst met metagegevensvelden.

U kunt ook op ![Pictogram Bewerken](assets/do-not-localize/edit_icon.svg), beschikbaar naast elke beschikbare eigenschap metadata, om de eigenschap te bewerken of op het verwijderpictogram te klikken om een bestaande eigenschap te verwijderen. Klikken **[!UICONTROL Save]** na alle wijzigingen om de wijzigingen toe te passen.

![Zoeken naar gebruikersinterface voor configuratie op Content Hub](assets/configuration-ui-metadata-search.png)


### Branding {#configure-branding-content-hub}

Beheerders kunnen de titel en de tekst van de tekst op de banner van het Content Hub-portaal ook aanpassen aan uw vereisten voor branding. Voer daartoe de volgende stappen uit:

1. Op de [Configuraties](#access-configuration-options-content-hub) gebruikersinterface, klik **[!UICONTROL Branding]**.

1. Tekst opgeven in **[!UICONTROL Title text on banner]** en **[!UICONTROL Body text on banner]** velden.

1. Klikken **[!UICONTROL Save]** om de wijzigingen toe te passen.

![Configuratie-UI-branding op Content Hub](assets/configuration-ui-branding.png)

De brandingsupdates die op de vertoning van het Gebruikersinterface van de Configuratie op de portaalbanner van Content Hub worden toegelaten:

![Configuratie-UI-branding op Content Hub](assets/configuration-ui-branding-updates.png)

### Aangepaste koppelingen {#configure-custom-links-content-hub}

Naast de standaard kunt u ook aangepaste tabbladen toevoegen **[!UICONTROL All Assets]**, **[!UICONTROL Collections]**, en **[!UICONTROL Insights]** tabs op het Content Hub-portaal net onder de banner. Voer daartoe de volgende stappen uit:

1. Op de [Configuraties](#access-configuration-options-content-hub) gebruikersinterface, klik **[!UICONTROL Custom Links]**.

1. Klik op **[!UICONTROL Add link]**.

1. Tekst opgeven in **[!UICONTROL Label]** en **[!UICONTROL URL]** velden. Het label dat u definieert, wordt weergegeven als een tab en wanneer u op het label klikt, gaat u naar de URL die is gedefinieerd in het dialoogvenster **[!UICONTROL URL]** veld.

1. Klik op **[!UICONTROL Confirm]**.

1. Klikken **[!UICONTROL Save]** om de wijzigingen toe te passen.

U kunt ook op ![Pictogram Bewerken](assets/do-not-localize/edit_icon.svg), beschikbaar naast elke URL, om de koppelingen te bewerken of op het verwijderpictogram te klikken om een bestaande URL te verwijderen. Klikken **[!UICONTROL Save]** na alle wijzigingen om de wijzigingen toe te passen.

![Aangepaste koppelingen voor configuratie-interface op Content Hub](assets/configuration-ui-custom-links.png)

De aangepaste koppeling wordt weergegeven als een nieuw tabblad naast het tabblad Inzichten op de startpagina van Content Hub.

![Aangepaste koppelingen voor configuratie-interface op Content Hub](assets/configuration-ui-custom-link-tab.png)


