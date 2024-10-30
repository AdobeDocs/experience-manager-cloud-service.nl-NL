---
title: Configure Content Hub user interface
description: Content Hub-gebruikersinterface configureren
exl-id: e9e22862-9bcd-459a-bcf4-7f376a0b329a
source-git-commit: 76337282b7d3008864763541a957c44327e1a5be
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# Content Hub-gebruikersinterface configureren {#configure-content-hub-user-interface}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [](/help/assets/product-overview.md) | [](/help/assets/dynamic-media-open-apis-overview.md) | [](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!CONTEXTUALHELP]
>id="configure_content_hub"
>title="Configure Content Hub user interface"
>abstract="Met Experience Manager Assets kunnen beheerders de opties configureren die beschikbaar zijn in de Content Hub-gebruikersinterface. Op basis van de configuratieopties die door de beheerders zijn geselecteerd, kunnen de Content Hub-gebruikers velden weergeven op Content Hub. De configuratieopties omvatten meta-gegevens terwijl het invoeren van activa, filters, activa eigenschappen, meta-gegevens terwijl het zoeken van activa, gepersonaliseerde branding, en om het even welke douaneverbindingen."

<!-- ![Download assets](assets/download-asset.jpg) -->
![ vorm activa op Content Hub ](assets/configure-assets.png)

Met Experience Manager Assets kunnen beheerders de opties configureren die beschikbaar zijn in de Content Hub-gebruikersinterface. Op basis van de configuratieopties die door de beheerders zijn geselecteerd, kunnen de Content Hub-gebruikers velden weergeven op Content Hub. De configuratieopties omvatten:

* Filters die beschikbaar zijn voor gebruikers tijdens het zoeken naar elementen.

* De gegevens of eigenschappen van het element die beschikbaar zijn voor elk element.

* Metagegevensvelden die beschikbaar zijn voor gebruikers wanneer ze elementen toevoegen aan Content Hub.

* Veld voor metagegevens van middelen die beschikbaar zijn voor zoekopdrachten op Content Hub.

* Inhoud markeren die u voor uw organisatie moet weergeven.

* Aangepaste koppelingen die u op Content Hub moet opnemen, naast elementen, verzamelingen en inzichten.

## Vereisten {#prerequisites-configuration-ui}

[ de beheerders van Content Hub ](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) kunnen de configuratieopties voor andere gebruikers binnen uw organisatie plaatsen.

## Toegang tot configuratieopties op Content Hub {#access-configuration-options-content-hub}

Configuratieopties openen op Content Hub:

1. Klik op het gebruikerspictogram in het rechterdeelvenster.

1. Selecteer **[!UICONTROL Configurations]** in de sectie **[!UICONTROL Product Settings]** .

   ![ de configuratieopties van de Toegang op Content Hub ](assets/access-content-hub-configuration-ui.png)

## Configuratieopties beheren in Content Hub {#manage-configuration-options}

Als beheerder, beheer de volgende configuratieopties voor uw gebruikers:

* [Importeren](#configure-import-options-content-hub)

* [Filters](#configure-filters-content-hub)

* [Gegevens van element](#configure-asset-details-content-hub)
* [Asset Card](#asset-card)

* [Zoeken](#configure-metadata-search-content-hub)

* [Branding](#configure-branding-content-hub)

* [Verlopen Assets](#expired-assets-content-hub)

* [Aangepaste koppelingen](#configure-custom-links-content-hub)

### Importeren {#configure-import-options-content-hub}

U kunt de meta-gegevensgebieden vormen die aan de gebruikers tijdens het uploaden van of het invoeren van activa aan het portaal van Content Hub, zoals de Naam van de Campagne, Sleutelwoorden, Kanalen, Tijdkader, Gebied, etc. tonen. Voer daartoe de volgende stappen uit:

1. Voor het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **[!UICONTROL Import]**.

1. Klik op **[!UICONTROL Add metadata]**.

1. Geef een label voor de eigenschap op, wijs deze toe aan een eigenschap met behulp van het veld **[!UICONTROL Metadata]** en selecteer het invoertype voor de nieuwe metagegevens van het element.

1. **[!UICONTROL Required field]**

1. Klik op **[!UICONTROL Confirm]**. De nieuwe metagegevens worden weergegeven in de lijst met bestaande eigenschappen van elementen.

1. Klik op **[!UICONTROL Save]** om de wijzigingen toe te passen.

Op dezelfde manier kunt u ![ klikken geeft pictogram ](assets/do-not-localize/edit_icon.svg) uit, beschikbaar naast elk beschikbaar bezit, om de etiketten uit te geven, deze gebieden verplicht of niet-verplicht te maken aan gebruikers terwijl het uploaden van activa gebruikend de **[!UICONTROL Required field]** knevel, of het pictogram van de Schrapping te klikken om het even welk meta-gegevensbezit te schrappen.

Klik op de schakeloptie **[!UICONTROL Auto-approval]** als u alle elementen die u toevoegt aan de Experience Manager Assets-opslagplaats automatisch wilt laten goedkeuren, zodat ze direct beschikbaar zijn in Content Hub. Else, DAM authors or administrators need to manually approve the assets to make them available on Content Hub. De schakeloptie is standaard ingesteld op Uit.

Klik op **[!UICONTROL Save]** nadat u alle wijzigingen hebt aangebracht om de wijzigingen toe te passen.

![ UI van de Configuratie uploadt details op Content Hub ](assets/configuration-ui-upload-details.png)

Metagegevens die zijn ingeschakeld op de gebruikersinterfaceweergave van de configuratie op de pagina voor het uploaden van elementen:

![ upload meta-gegevens op Content Hub ](assets/configuration-ui-add-assets.png)

### Filters {#configure-filters-content-hub}

Met Content Hub kunnen beheerders filters configureren die worden weergegeven terwijl ze naar elementen zoeken. Voer de volgende stappen uit om een nieuw filter toe te voegen:

1. Voor het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **[!UICONTROL Filters]**.

1. Klik op **[!UICONTROL Add filters]**.

1. Geef een label voor het filter op, wijs het filter toe aan een eigenschap met behulp van het veld **[!UICONTROL Metadata]** en selecteer het invoertype voor het nieuwe filter.
1. Klik op **[!UICONTROL Confirm]**. The new filter displays in the list of the existing filters.

1. **[!UICONTROL Save]**

   >[!NOTE]
   >
   >The new filter gets displayed on the Search page only if there is alteast one asset in the repository matching the filter criteria.

![](assets/do-not-localize/edit_icon.svg) Klik op **[!UICONTROL Save]** nadat u alle wijzigingen hebt aangebracht om de wijzigingen toe te passen.

![ filters UI van de Configuratie op Content Hub ](assets/configuration-ui-filters.png)

The filters enabled on the Configuration User Interface display on the Search page:

![](assets/filters-for-search.png)


### Asset details {#configure-asset-details-content-hub}

You can also configure the asset properties that display for each asset, such as file name, title, format, size, and so on. To do so, execute the following steps:

1. [](#access-configuration-options-content-hub)**[!UICONTROL Asset details]**

1. Klik op **[!UICONTROL Add metadata]**.

1. Geef een label voor de eigenschap op, wijs deze toe aan een eigenschap met behulp van het veld **[!UICONTROL Metadata]** en selecteer het invoertype voor de nieuwe metagegevens van het element.
1. Klik op **[!UICONTROL Confirm]**. De nieuwe metagegevens worden weergegeven in de lijst met bestaande eigenschappen van elementen.

1. Klik op **[!UICONTROL Save]** om de wijzigingen toe te passen, zodat de nieuwe eigenschap wordt weergegeven op de pagina met elementdetails.

Op dezelfde manier kunt u ![ klikken geeft pictogram ](assets/do-not-localize/edit_icon.svg) uit, beschikbaar naast elk beschikbaar bezit, om de etiketten uit te geven of het schrappingspictogram te klikken om het even welk bestaand activadetail te schrappen. Klik op **[!UICONTROL Save]** nadat u alle wijzigingen hebt aangebracht om de wijzigingen toe te passen.

![ de activadetails van de Configuratie UI op Content Hub ](assets/configuration-ui-asset-details.png)

De eigenschappen die op de vertoning van het Gebruikersinterface van de Configuratie op de pagina van de Details van Activa worden toegelaten:

![ eigenschappen van Activa op Content Hub ](assets/config-ui-asset-properties.png)

### Asset Card {#asset-card}

U kunt de zeer belangrijke meta-gegevensgebieden ook vormen die u op de **Kaart van Activa** tot een maximum van 6 gebieden moet tonen. Voer daartoe de volgende stappen uit:

![ zeer belangrijke meta-gegevens op de Kaart van Activa ](/help/assets/assets/asset-card-key-metadata.png)

1. Op het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **Kaart van Activa**.
2. Klik **toevoegen meta-gegevens**. **voegt de meta-gegevens van de activakaart** vertoningen van de dialoogdoos toe.
3. Specificeer de meta-gegevensnaam op het **gebied van het Etiket** en selecteer een meta-gegevensbezit op het **Meta-gegevens** gebied.
4. Klik **bevestigen** en klik dan **sparen** om de veranderingen toe te passen zodat de nieuwe bezitsvertoning op de pagina van activadetails.
   ![ activakaart ](/help/assets/assets/asset-card.png)

Op dezelfde manier geeft de klik ![ ](/help/assets/assets/edit-content-hub.svg) uit die naast elk beschikbaar bezit beschikbaar is, om het even welke vereiste wijzigingen te maken of ![ schrapping ](/help/assets/assets/delete-content-hub.svg) te klikken om het even welk bestaand meta-gegevensbezit te schrappen. Klik **sparen** na het aanbrengen van alle wijzigingen om de veranderingen toe te passen.


### Zoeken {#configure-metadata-search-content-hub}

Beheerders kunnen de metagegevensvelden definiëren die worden doorzocht wanneer een gebruiker een zoekcriterium opgeeft op Content Hub. Voer de volgende stappen uit:

1. Voor het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **[!UICONTROL Add metadata]**.

1. Geef het metagegevensveld op en klik op **[!UICONTROL Confirm]** .

1. Klik op **[!UICONTROL Save]** om de wijzigingen toe te passen, zodat de nieuwe eigenschap metadata wordt weergegeven in de lijst met metagegevensvelden.

Op dezelfde manier kunt u ![ klikken geeft pictogram ](assets/do-not-localize/edit_icon.svg) uit, beschikbaar naast elk beschikbaar meta-gegevensbezit, om het bezit uit te geven of het schrappingspictogram te klikken om het even welk bestaand bezit te schrappen. Klik op **[!UICONTROL Save]** nadat u alle wijzigingen hebt aangebracht om de wijzigingen toe te passen.

![ Onderzoek UI van de Configuratie op Content Hub ](assets/configuration-ui-metadata-search.png)


### Branding {#configure-branding-content-hub}

Beheerders kunnen de titel en de tekst van de tekst op de banner van het Content Hub-portaal ook aanpassen aan uw vereisten voor branding. Voer daartoe de volgende stappen uit:

1. Voor het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **[!UICONTROL Branding]**.

1. Geef tekst op in **[!UICONTROL Title text on banner]** - en **[!UICONTROL Body text on banner]** -velden.

1. Klik op **[!UICONTROL Save]** om de wijzigingen toe te passen.

![ het brandmerken van de Configuratie UI op Content Hub ](assets/configuration-ui-branding.png)

De brandingsupdates die op de vertoning van het Gebruikersinterface van de Configuratie op de portaalbanner van Content Hub worden toegelaten:

![ het brandmerken van de Configuratie UI op Content Hub ](assets/configuration-ui-branding-updates.png)

### Verlopen activa{#expired-assets-content-hub}

Beheerders kunnen bepalen of verlopen elementen zichtbaar moeten zijn op Content Hub. Als de verlopen elementen zichtbaar worden gemaakt, kunnen ze ook definiëren of gebruikers ze kunnen downloaden.

Verlopen elementen worden standaard niet weergegeven in Content Hub.

Voer daartoe de volgende stappen uit:

1. Voor het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **[!UICONTROL Expired Assets]**.

1. Schakel in de sectie **[!UICONTROL Visible]** de schakeloptie **[!UICONTROL Allow users to view expired assets]** in om alle verlopen elementen zichtbaar te maken op Content Hub.

1. Nadat u de zichtbaarheid van elementen hebt ingeschakeld, kunt u de mogelijkheid om verlopen elementen te downloaden in- of uitschakelen met de schakeloptie **[!UICONTROL Allow users to download expired assets]** .

1. Klik op **[!UICONTROL Save]** om de wijzigingen toe te passen.

   ![ Verlopen activa op Content Hub ](assets/expired-assets-content-hub.png)

Nadat u de zichtbaarheid van elementen hebt ingeschakeld, kunt u de verlopen elementen op Content Hub weergeven, zoals in de volgende afbeelding wordt getoond:

![ Verlopen activa op Content Hub ](assets/view-download-expired-assets.png)

Als de beheerder downloaden heeft ingeschakeld, kunnen de Content Hub-gebruikers deze ook downloaden, zoals in de afbeelding is aangegeven.

Als de zichtbaarheid van verlopen elementen is ingeschakeld, markeert Content Hub ook elementen die binnen de komende 15 dagen verlopen met behulp van het `Expiring in n days` -bericht op de Asset Card.


### Custom Links {#configure-custom-links-content-hub}

**[!UICONTROL All Assets]****[!UICONTROL Collections]****[!UICONTROL Insights]** To do so, execute the following steps:

1. Voor het [ gebruikersinterface van Configuraties ](#access-configuration-options-content-hub), klik **[!UICONTROL Custom Links]**.

1. Klik op **[!UICONTROL Add link]**.

1. Geef tekst op in **[!UICONTROL Label]** - en **[!UICONTROL URL]** -velden. **[!UICONTROL URL]**

1. Klik op **[!UICONTROL Confirm]**.

1. **[!UICONTROL Save]**

![](assets/do-not-localize/edit_icon.svg) **[!UICONTROL Save]**

![](assets/configuration-ui-custom-links.png)

De aangepaste koppeling wordt weergegeven als een nieuw tabblad naast het tabblad Inzichten op de startpagina van Content Hub.

![ UI van de Configuratie de lusjes van de Verbindingen van de Douane op Content Hub ](assets/configuration-ui-custom-link-tab.png)
