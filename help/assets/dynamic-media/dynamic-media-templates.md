---
title: Hoe te om  [!DNL Dynamic Media]  malplaatjes te beheren?
description: Leer hoe te om  [!DNL Dynamic Media]  malplaatjes tot stand te brengen gebruikend een het malplaatjeredacteur van WYSIWYG en veelvoudige beelden, teksten en vormlagen te omvatten om banners en vliegers snel tot stand te brengen en hen in stroomafwaartse toepassingen te gebruiken.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: d82d40ebb5417dfb7ce37c9995c5cadb74a2fe11
workflow-type: tm+mt
source-wordcount: '3605'
ht-degree: 0%

---


# [!DNL Dynamic Media] sjablonen{#dynamic-media-templates}

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

Maak aanpasbare sjablonen in real time voor uw banners en vliegers met gebruik van [!DNL Dynamic Media] sjablonen, een WYSIWYG-sjablooneditor. Publiceer de [!DNL Dynamic Media] -sjabloon en gebruik deze in downstreamtoepassingen. Een [!DNL Dynamic Media] -sjabloon bevat afbeeldings- en tekstlagen. Voeg parameters aan het beeld en tekstlagen van het malplaatje toe en gebruik [[!DNL Dynamic Media]  URLs ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media) om de laag te verplaatsen en resize en zijn inhoud in real time bij te werken.

Enkele van de belangrijkste functies zijn:

* **[!DNL Dynamic Media]WYSIWYG-sjablooneditor:** maak aanpasbare banners met afbeeldings- en tekstlagen.
* **Parameterization van de Laag:** bepaal dynamische sleutel-waarde paren voor lagen om updates in real time toe te laten.
* **[!DNL Dynamic Media]URL-ondersteuning:** gebruik [!DNL Dynamic Media] URL&#39;s voor sjablonen, waarbij gepersonaliseerde waarden uit toepassingen van het type 1st of van derden worden geïntegreerd.
* **Controle van de Zichtbaarheid van de Laag:** verberg of toon dynamisch lagen zoals nodig.
* **Slimme Tekst het Randen van de Tekst:** past automatisch tekstgrootte aan om aangewezen gebieden te passen.

Enkele belangrijke voordelen van [!DNL Dynamic Media] sjablonen zijn:

* **optimaliseer 1 :1 Personalization:** Inhoud van de spoorstaaf aan klantensignalen in real time.
* **Verminder Handmatige inspanning:** Automate en versnelt inhoudsverwezenlijking en beheer.
* **verzekert Consistente Ervaringen Omnichannel:** handhaaf merkconsistentie over kanalen.
* **Reuse Inhoud effectief:** vermijd enig-gebruiksinhoud en schaal met dynamische, geparametereerde malplaatjes.
* **Mitigate Risks:** update tarifering, kortingen, en verbindingen in real time.
* **verbeter de Betrokkenheid van de Klant:** aandrijving interactieve, contextafhankelijke ervaringen.

>[!NOTE]
>
>Klanten met een abonnement op de uitgebreide beveiligingsSKU kunnen geen gebruik maken van [!DNL Dynamic Media] -mogelijkheden, waaronder [!DNL Dynamic Media] Templates, voor dat Cloud Services-programma.

Leer hoe u in deze video stap voor stap een [!DNL Dynamic Media] -sjabloon maakt.

>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Voordat u begint{#prerequisites-for-dynamic-media-wysiwyg-template}

Voer de volgende vereisten in om een [!DNL Dynamic Media] -sjabloon te maken en de URL voor levering te genereren:

1. Toegang tot [!DNL Dynamic Media] .
1. Op de startpagina van [!DNL Assets View] hebt u een map in **[!UICONTROL Dynamic Media Assets]** om uw sjabloon op te slaan. [ creeer een omslag ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![ Assets ](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**om die omslag in **[!UICONTROL Dynamic Media Assets]**te herhalen.
1. [ Synchroniseer de beelden beschikbaar in uw  [!DNL AEM Assets]  instantie met  [!DNL Dynamic Media]  om hen te gebruiken voor het creëren van het malplaatje ](/help/assets/dynamic-media/config-dm.md).
1. Publiceer de afbeeldingen die u wilt gebruiken bij het maken van de sjabloon om de URL van de levering van de sjabloon te genereren nadat u deze hebt gemaakt. De leverings-URL kan worden gebruikt in downstreamtoepassingen.
1. Om een doopvont buiten het gebrek [!UICONTROL Adobe Sans F2] doopvont in de de tekstlaag van het malplaatje te gebruiken, [ upload en publiceer gelijktijdig het doopvontdossier aan AEM en Dynamische Media ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation). [ de gesteunde formaten van het doopvontdossier zijn, AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF ](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Ook, verzeker om [ ](/help/assets/reprocessing-assets-view.md) opnieuw te verwerken de bestaande doopvonten om hen te gebruiken. Zie [ Doopvonten ](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/support-files/fonts) voor meer informatie.<!--(On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**)-->
1. Controleer het volgende in de aanraakinterface:
   * Op het tabblad **[!UICONTROL Edit [!DNL Dynamic Media] Configuration page]** wordt **[!UICONTROL [!DNL Dynamic Media] sync mode]** dat is ingesteld op **[!UICONTROL Disabled by default]** , niet toegepast op alle AEM-mappen (**[!UICONTROL Sync all content]** is uitgeschakeld). Zie [ vormend Dynamische Media Cloud Service ](/help/assets/dynamic-media/config-dm.md) voor meer informatie.
   * **[!UICONTROL [!DNL Dynamic Media] sync mode]** wordt ingesteld op **[!UICONTROL Enable for subfolders]** voor de doelmap of -submap waarin u de sjabloon na het maken wilt opslaan. Zie [ het vormen  [!DNL Dynamic Media]  Cloud Service ](/help/assets/dynamic-media/config-dm.md) voor meer informatie.

## [!DNL Dynamic Media] -sjabloon maken{#how-to-create-dynamic-media-template}

Voer de volgende stappen uit om een [!DNL Dynamic Media] -sjabloon te maken:

<!--
1. Navigate to your [!DNL Assets View] and [create a folder](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**. The folder tree in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** replicates in **[!UICONTROL Dynamic Media Assets]**. Save your [!DNL Dynamic Media] template in this [!UICONTROL Dynamic Media Assets] folder.
1. Select ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** and [upload and publish your images to [!DNL AEM] and [!DNL Dynamic Media] simultaneously](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm#dynamic-media-publish-mode-set-to-upon-activation) to use them in creating the template. Publishing images is required to generate the template's delivery URL, after creating the template. The delivery URL can be used in downstream applications.
1. [Execute these asset uploading and publishing steps](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation) to upload and publish a font file to AEM and Dynamic Media simultaneously to use it in creating the template. [!UICONTROL Adobe Sans F2] is the only default font available in the text layer. [The supported font file formats are, AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Ensure to [reprocess](/help/assets/reprocessing-assets-view.md) the existing fonts to use them in creating the template (On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**). See [Fonts](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/support-files/fonts) to know more about fonts.
-->

1. [Een leeg canvas maken](#create-a-canvas)
1. [Afbeeldingen toevoegen aan het canvas](#add-images-to-the-canvas)
1. [Tekstlagen toevoegen aan het canvas](#add-text-to-the-canvas)
1. [Vormen toevoegen aan het canvas](#add-shapes-to-the-canvas)
1. [Een laag bewerken of verwijderen](#edit-or-delete-a-layer)
1. [Lagen parametereren](#parameterise-a-layer)

### Een leeg canvas maken{#create-a-canvas}

Voer de volgende stappen uit om een leeg canvas te maken:

1. Navigeer naar [!DNL Assets View] , selecteer **[!UICONTROL Dynamic Media Assets]** beschikbaar in het linkerpaneel en navigeer naar uw map om de sjabloon in die map op te slaan.

   ![ Dynamische malplaatjes van Media ](/help/assets/assets/DM-Assets1.png)

1. Selecteer **[!UICONTROL Create Template]**. Het dialoogvenster **[!UICONTROL New Template]** wordt weergegeven.

   ![ hoe te om dynamische malplaatjes tot stand te brengen die in real time kunnen worden aangepast ](/help/assets/assets/new-template.png)

   >[!NOTE]
   >
   >  De sjabloon wordt opgeslagen op de locatie waar u de sjabloon maakt. Selecteer [!DNL Assets View] op de startpagina van **[!UICONTROL Dynamic Media Assets]** en klik op **[!UICONTROL Create Template]** om de sjabloon op te slaan in de hoofdmap van **[!UICONTROL Dynamic Media Assets]** .

1. Geef een sjabloonnaam op, definieer de canvasbreedte en -hoogte en klik op **[!UICONTROL Create]** . Er wordt een leeg canvas weergegeven met menuopties aan beide zijden voor het maken van de sjabloon. Houd de muisaanwijzer boven de menuopties om de knopinfo weer te geven.
   ![ in real time aanpasbaar malplaatje ](/help/assets/assets/blank-canvas-page.png)

   >[!NOTE]
   >
   > Het toegestane breedte- en hoogtebereik ligt tussen 50 en 5000.

**opties van het Menu op de juiste ruit:** Gebruik deze opties om de noodzakelijke beelden en tekstlagen aan het canvas toe te voegen.

* ![ DM Malplaatjes ](/help/assets/assets/add-image.svg): Klik om beelden aan het canvas toe te voegen.
* ![ aanpasbare malplaatjes ](/help/assets/assets/add-text.svg): Klik om teksten aan het canvas toe te voegen.
* ![ aanpasbare malplaatjes ](/help/assets/assets/show-layers-list.svg): Klik om de lijst van alle lagen (beeld en tekst) op het canvas te zien. Elke afbeelding en tekst die aan het canvas wordt toegevoegd, wordt weergegeven als een afzonderlijke laag.

**opties van het Menu op de linkerruit:** Gebruik deze opties voor de volgende gemeenschappelijke redacteursacties.

* ![ DM Malplaatjes ](/help/assets/assets/layer-selector.svg): Selecteer ![ Malplaatjes DM ](/help/assets/assets/layer-selector.svg) en klik een laag op het canvas om het te selecteren.
* ![ malplaatjes die aanpassing ](/help/assets/assets/bring-forward.svg) steunen: Klik ![ malplaatjes die aanpassing ](/help/assets/assets/bring-forward.svg) steunen of toetsenbordkortere weg gebruiken, **CTRL** + **`]`** (Vensters) of **Cmd** + **`]`** (Mac) om een geselecteerde laag vooruit te brengen.
* ![ hoe te om een malplaatje tot stand te brengen dat gemakkelijk kan worden aangepast ](/help/assets/assets/send-backward.svg): Klik ![ hoe te om een malplaatje tot stand te brengen dat gemakkelijk kan worden aangepast ](/help/assets/assets/send-backward.svg) of toetsenbordkortere weg, **CTRL** + **`[`** (Vensters) of **Cmd** + **`[`** (Mac) gebruiken om een geselecteerde laag achterwaarts te verzenden.
* ![ creeer een malplaatje dat onmiddellijk ](/help/assets/assets/undo.svg) kan worden aangepast: Klik ![ creeer een malplaatje dat onmiddellijk ](/help/assets/assets/undo.svg) of gebruikstoetsenbordkortere weg kan worden aangepast, **CTRL** + **Z** (Vensters) of **Cmd** + **Z** (Mac) om de laatste actie ongedaan te maken.
* ![ malplaatje om banners snel ](/help/assets/assets/redo.svg) tot stand te brengen: Klik ![ malplaatje om banners snel ](/help/assets/assets/redo.svg) tot stand te brengen of toetsenbordkortere weg te gebruiken, **CTRL** + **Y** (Vensters) of **Cmd** + **Y** (Mac) om de laatste actie opnieuw uit te voeren.
* ![ malplaatje om snel vliegers ](/help/assets/assets/zoom-in.svg) tot stand te brengen: Klik ![ malplaatje om snel vliegers ](/help/assets/assets/zoom-in.svg) tot stand te brengen of toetsenbordkortere weg te gebruiken, **CTRL** + **+** (Vensters) of **Cmd** + **+** (Mac) om binnen het canvas te zoemen.
* ![ malplaatje om banners snel ](/help/assets/assets/Zoom-out.svg) tot stand te brengen: Klik ![ malplaatje om banners snel ](/help/assets/assets/Zoom-out.svg) tot stand te brengen of toetsenbordkortere weg te gebruiken, **CTRL** + **-** (Vensters) of **Cmd** + **-** (Mac) om uit het canvas te zoemen.
* De pers **backspace** of **schrapt** om de geselecteerde laag te schrappen als geen tekst of het bezit wordt uitgegeven.

Klik ![ malplaatje om snel flyers ](/help/assets/assets/show-layers-list.svg) tot stand te brengen en meer opties (![](/help/assets/assets/three-dots.svg)) op de laag van het Canvas te selecteren om de canvasdimensies op elk ogenblik uit te geven terwijl het creëren van het malplaatje.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> Sjablonen staan maximaal 20 lagen toe, waaronder het canvas.

### Afbeeldingen toevoegen aan het canvas{#add-images-to-the-canvas}

Voer de volgende stappen uit om afbeeldingen aan het canvas toe te voegen:

1. Klik ![ creeer een banner in geen tijd ](/help/assets/assets/add-image.svg) om het [ paneel van de Selecteur van Activa ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) te openen. In het deelvenster worden de afbeeldingen weergegeven die in uw AEM Assets-instantie zijn gesynchroniseerd met [!DNL Dynamic Media] .
1. Blader in het deelvenster of gebruik trefwoorden in de zoekbalk om een specifieke afbeelding te zoeken.
1. Sleep een afbeelding naar het canvas om deze te gebruiken. Zie [**[!UICONTROL Properties Panel]**](#reposition-resize-delete-a-layer) voor het wijzigen van het formaat of het verplaatsen van een laag op het canvas.
   ![ creeer een banner binnen seconden ](/help/assets/assets/add-image-to-canvas.png)
1. Schakel de schakeloptie **[!UICONTROL Uniform Radius]** in en gebruik de schuifregelaar **[!UICONTROL Corner Radius]** om de afronding van alle vier de hoeken van een afbeelding op uniforme wijze aan te passen. Schakel de schakeloptie uit om de afronding van hoeken aan te passen door aan elke hoek specifieke straalwaarden toe te wijzen.
   ![ pas hoekronding van beeld ](/help/assets/assets/enable-uniform-radius-image.png) aan

### Tekstlagen toevoegen aan het canvas{#add-text-to-the-canvas}

Voer de volgende stappen uit om tekstlagen aan het canvas toe te voegen:

1. Klik ![ creërend nieuwe banners geleidelijk ](/help/assets/assets/add-text.svg) om een tekstlaag aan het canvas toe te voegen en het paneel van Eigenschappen te openen.
1. Selecteer de laag en klik op de tekst om deze bij te werken.
1. Selecteer **[!UICONTROL Smart Text Resize]** in het deelvenster Eigenschappen om de tekstlengte en tekengrootte automatisch aan te passen aan de optimale grootte in het desbetreffende gebied.
   ![ best klantgerichte banners ](/help/assets/assets/add-text-layer.png)

Zie [**[!UICONTROL Properties Panel]**](#reposition-resize-delete-a-layer) om de laag te verplaatsen, te vergroten of te verkleinen, te roteren of te verwijderen. Maak de tekst op in het gewenste lettertype, de gewenste grootte, kleur, stijl, uitlijning (in de laag) door de waarden van de tekst te wijzigen in de desbetreffende velden onder de sectie **[!UICONTROL Text]** van het deelvenster. In het veld **[!UICONTROL Font Family]** wordt het standaardlettertype van [!UICONTROL Adobe Sans F2] weergegeven, evenals de opnieuw verwerkte bestaande lettertypen en de nieuw geüploade en gepubliceerde lettertypen. Zie punt 5 in [ alvorens u ](#prerequisites-for-dynamic-media-wysiwyg-template) sectie hierboven voor meer informatie begint.

[ de specifieke delen van het Formaat van tekst ](#apply-formatting-to-substring) en [ bepalen hen om hen onafhankelijk te controleren ](#substring-parameterisation).

#### Selectieve tekst opmaken{#apply-formatting-to-substring}

Voer de volgende stappen uit om specifieke delen van een tekenreeks op te maken:

1. Selecteer een of meer tekens in de tekenreeks die u wilt opmaken.
1. Formaat de selectie gebruikend het [ eigenschappen paneel ](#properties-panel). De volgende opmaakopties zijn van toepassing op subtekenreeksen en hun onderdelen:
   * **Stijl van de Doopvont**: Vet, cursief, onderstrepen, subscript, en superscript gebruikend de **[!UICONTROL Font Style]** optie.
   * **Eigenschappen van de Doopvont**: De doopvontfamilie van de verandering, kleur, en grootte gebruikend de respectieve paneelopties.
     ![ formaat-substring ](/help/assets/assets/format-substring.png)

[ elk geformatteerd koorddeel toont als substring in de substring selecteur, beschikbaar binnen het parameterpaneel. Voeg parameters aan deze geformatteerde delen toe om hen dynamisch te formatteren gebruikend de levering URL van het malplaatje ](#substring-parameterisation).

### Vormen toevoegen aan het canvas {#add-shapes-to-the-canvas}

Voer de volgende stappen uit om vormen toe te voegen aan het canvas:

1. Klik ![ creërend vormen ](/help/assets/assets/Shapes.svg), selecteer een vorm (rechthoek of cirkel) om het aan het canvas toe te voegen. Gebruik de vorm [[!UICONTROL Properties Panel]](#reposition-resize-delete-a-layer) om de laag te verplaatsen, te vergroten of te verkleinen, te roteren of te verwijderen.
1. Blader naar de sectie **[!UICONTROL Style]** van het deelvenster, definieer een hexadecimale code in het veld **[!UICONTROL Shape Color]** of gebruik de kleurkiezer om de kleur in de geselecteerde vorm te vullen.
1. Schakel de schakeloptie **[!UICONTROL Uniform Radius]** in en gebruik de schuifregelaar **[!UICONTROL Corner Radius]** om de afronding van alle vier de hoeken van de rechthoek uniform aan te passen. Schakel de schakeloptie uit om de afronding van hoeken aan te passen door aan elke hoek specifieke straalwaarden toe te wijzen.
   ![ pas hoekronding van vormen ](/help/assets/assets/enable-uniform-radius-shape.png) aan
1. [ voeg de **[!UICONTROL Hide]** parameter aan de geselecteerde laag ](#parameterise-a-layer) toe om de laag in het malplaatje in real time te tonen of te verbergen gebruikend het malplaatje URL.
1. Selecteer de laag aan [ om a [!UICONTROL CTA] verbinding ](#add-CTA-in-dynamic-media-templates) aan het toe te voegen, toestaand gebruikers om de vorm als hyperlink in het levende malplaatje te klikken.

### Een laag bewerken of verwijderen {#edit-or-delete-a-layer}

Voer de volgende stappen uit om een canvaslaag te bewerken of te verwijderen:

1. Klik ![ malplaatjes met steun aan dynamische updates ](/help/assets/assets/show-layers-list.svg) en selecteer de laag of op het canvas of van de lijst van Lagen.
1. Klik **[!UICONTROL more options]** (![ malplaatjes met steun aan updates in real time ](/help/assets/assets/three-dots.svg)) om de laag uit te geven of te schrappen.
1. Klik op **[!UICONTROL Delete]** om de laag te verwijderen.
1. Klik op **[!UICONTROL Edit]** om de laag te bewerken met [**[!UICONTROL Properties Panel]**](#reposition-resize-delete-a-layer) .
   ![ snelle bannerverwezenlijking ](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Deelvenster Eigenschappen{#properties-panel}

[!UICONTROL Properties] paneel omvat secties aan [ herpositie ](#reposition-resize-delete-a-layer), [ resize ](#reposition-resize-delete-a-layer) en [ roteert ](#reposition-resize-delete-a-layer) een laag.  Het verstrekt ook de opties van de kleurenvulling voor [ vormlagen ](#add-shapes-to-the-canvas), [ tekst het formatteren opties ](#text-formatting-options-on-properties-panel) voor [ tekstlagen ](#add-text-to-the-canvas), en een optie om [ toe te voegen a [!UICONTROL CTA] verbinding ](#add-CTA-in-dynamic-media-templates) aan om het even welke geselecteerde laag.
Om aan het de eigenschappenpaneel van een laag te navigeren, klik ![ snelle inhoudsverwezenlijking ](/help/assets/assets/show-layers-list.svg) en selecteer de laag van de lijst om zijn [!UICONTROL Properties] paneel te tonen.

![ snelle inhoudsverwezenlijking ](/help/assets/assets/properties-panel.png)

Selecteer in het deelvenster [!UICONTROL Properties] van een laag een andere laag op het canvas om naar het deelvenster [!UICONTROL Properties] te navigeren.

#### Een laag verplaatsen, vergroten, verkleinen, roteren of verwijderen{#reposition-resize-delete-a-layer}

Zie de volgende algemene handelingen voor het bewerken van lagen om tekst of een afbeeldingslaag te bewerken:

* **verplaats de laag:** sleep de laag om het overal op het canvas te bewegen. Met deze actie worden de X- en Y-waarden in het deelvenster Eigenschappen bijgewerkt. X en Y zijn de coördinaten van het middelpunt van de laag op het canvasvlak.
* **resize de laag:** selecteer de laag en sleep zijn randhandvatten om het te resize. Met deze handeling worden de waarden voor B (breedte) en H (hoogte) in het deelvenster Eigenschappen bijgewerkt.
* **roteer de laag:** sleep het vierkante handvat dat verticaal boven de laag wordt geplaatst om het rond zijn centrum te roteren. Met deze handeling worden de hoekwaarden in het deelvenster Eigenschappen bijgewerkt.
* **Schrap de laag:** Pers **Backspace** of **schrapt** en klikt dan **[!UICONTROL Confirm]** om een geselecteerde laag te schrappen.

#### Opties voor tekstopmaak{#text-formatting-options-on-properties-panel}

Maak de tekst op in het gewenste lettertype, de gewenste grootte, kleur, stijl, uitlijning (binnen de laag) door de waarden van de tekst te wijzigen in de desbetreffende velden onder de sectie **[!UICONTROL Text]** in het deelvenster.
Zorg ervoor dat u **[!UICONTROL Smart Text Resize]** opneemt. [!UICONTROL Smart Text Resize] werkt op [ Copyfitting ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting) algoritme om tekst in het tekstgebied optimaal te vullen en tekstoverloop te verhinderen en extra ruimte bij de bodem van de tekst te minimaliseren.

![ inhoudsverwezenlijking in geen tijd ](/help/assets/assets/smart-text-resize.png)

### Lagen parametereren {#parameterise-a-layer}

Nadat u een sjabloon hebt gemaakt met meerdere lagen afbeeldingen, tekst en vormen, kunt u de geselecteerde lagen het beste bepalen. Wanneer een laag of zijn bezit wordt bepaald, krijgt het een zeer belangrijk-waardepaar (ook genoemd als parameter). Deze parameter kan in het malplaatje URL worden omvat om de positie, de grootte of de inhoud van de laag in echt bij te werken - tijd resulterend in malplaatjeaanpassing in geen tijd.

U kunt als volgt een laag bepalen:

1. klik ![ onmiddellijke inhoudsverwezenlijking ](/help/assets/assets/show-layers-list.svg), selecteer een laag en klik **[!UICONTROL Parameters]**. Het deelvenster **[!UICONTROL Parameters]** wordt weergegeven.
1. Schakel **[!UICONTROL Include Parameter]** in om een eigenschap te bepalen. Zie de [ het paneeloptie van Parameters ](#parameterisation-options-or-allowed-parameters) om het gedrag van het bezit na parameterization te kennen.
1. **Facultatief:** noem de parameternaam anders. Een parameternaam heeft een laagnaam gevolgd door een achtervoegsel. Voor een geselecteerde laag delen alle eigenschappen met parameters dezelfde laagnaam, gevolgd door een variërend achtervoegsel. Wijzig de naam van de laag door de semantische noemende overeenkomst te volgen zodat wanneer u de parameter in URL omvat, de parameternaam zelf over de inhoud van de laag of zijn doel verklaart.
1. Klik op **[!UICONTROL Save]**.
   ![ onmiddellijke inhoudsverwezenlijking ](/help/assets/assets/parameterise-a-layer.png)
Als u wilt schakelen tussen het deelvenster Parameter van een afbeelding en een tekstlaag, selecteert u de laag op het canvas en klikt u op **[!UICONTROL Parameters]** .

#### Opties in het deelvenster Parameters {#parameterisation-options-or-allowed-parameters}

De parameters van eigenschappen kunnen als parameters URL in het malplaatje URL worden omvat om het malplaatje in echt uit te geven - tijd gebruikend URL.

##### Laagparameters{#layer-parameters}

Hier volgt een lijst met laagparameters die op zowel afbeeldings- als tekstlagen van toepassing zijn.

**[!UICONTROL X]:** neem op om de laag horizontaal langs zijn middellijn, parallel aan de x-as van het malplaatjevliegtuig, te bewegen door de waarde van de parameter in URL te veranderen.
**[!UICONTROL Y]:** neem op om de laag verticaal langs zijn middellijn, parallel aan de y-as van het malplaatjevliegtuig, te bewegen door de waarde van de parameter in URL te veranderen.
**[!UICONTROL Width]:** neem op om de breedte van de laag aan te passen door de waarde van de parameter in URL te wijzigen.
**[!UICONTROL Height]:** neem op om de hoogte van de laag aan te passen door de waarde van de parameter in URL te wijzigen.
**[!UICONTROL Hide]:** neem op om de laag in de sjabloon te verbergen of weer te geven met 0 (show) en 1 (hide).

##### Afbeeldingsparameter{#image-parameter}

Neem de parameter **[!UICONTROL Source]** op om de afbeelding van de laag te vervangen door een nieuwe afbeelding door het afbeeldingspad in de waarde van de parameter in de URL te wijzigen.
![ de parameter van de beeldbron ](/help/assets/assets/image-parameter.png)

##### Tekstopmaakparameters{#text-formatting-parameters}

Neem de volgende parameters op om de tekst, het lettertype, de kleur en de grootte van de tekst vanuit de leverings-URL te bewerken door de parameterwaarden in de URL bij te werken:

**[!UICONTROL Text]:** neem hier tekst op om de URL bij te werken.
**[!UICONTROL Font Family]:** neem op om het lettertype van de tekst via de URL bij te werken.
**[!UICONTROL Font Size]:** neem hier de tekengrootte van de tekst op via de URL.
**[!UICONTROL Text color]:** neem de lettertypekleur van de tekst op om deze bij te werken via de URL.

##### Subtekenreeksen parametereren{#substring-parameterisation}

Blader in het deelvenster **[!UICONTROL Parameters]** naar de sectie **[!UICONTROL Substring Parameters]** . Deze sectie omvat a **substring selecteur** die het volledige koord (geselecteerde tekstlaag) met het verenigbare formatteren of zijn geformatteerde delen als afzonderlijke substrings toont. Selecteer substring aan [ parameterize zijn tekst, doopvontfamilie, doopvontgrootte, en kleur ](#text-formatting-parameters).
Gebruik substring selecteur aan [ gespleten substrings ](#split-substring) om zijn individuele delen van parameters te bepalen of [ substrings ](#merge-substring) samenvoegen om eenvormige parameters toe te passen.

###### Subtekenreeks splitsen{#split-substring}

Als u een bepaald gedeelte van een subtekenreeks wilt parameteren, haalt u het onderdeel uit en maakt u het als een aparte subtekenreeks voor de afzonderlijke selectie en parameterbepaling. Voer de volgende stappen uit om een subtekenreeks in afzonderlijke subtekenreeksen te splitsen:

1. Selecteer in de subtekenreeks-kiezer de tekens in een subtekenreeks om deze te scheiden.
1. Klik ![ gespleten substring ](/help/assets/assets/unmerge.svg) om de selectie uit te trekken en het een afzonderlijk substring binnen de **substring selecteur** te maken.
   ![ gespleten substring ](/help/assets/assets/split-a-substring.png)
U kunt vereiste substring selecteren om [ zijn tekst, doopvontfamilie, doopvontgrootte, en kleur ](#text-formatting-parameters) te bepalen.

###### Subtekenreeks samenvoegen{#merge-substring}

Het samenvoegen van subtekenreeksen verwijdert de bestaande individuele parameters en stelt u in staat consistente parameters toe te passen op de nieuw gevormde subtekenreeks.
Voer de volgende stappen uit om twee aangrenzende subtekenreeksen samen te voegen om uniforme parameters toe te passen op de resulterende subtekenreeks:

1. Selecteer in de subtekenreekskiezer tekens voor twee aangrenzende subtekenreeksen met dezelfde opmaak.
1. Klik ![ samenvoegen substring ](/help/assets/assets/merge.svg) om substrings samen te voegen.
   ![ fusie identieke substrings ](/help/assets/assets/merge-two-substrings.png)
U kunt uniforme parameters toepassen op de nieuwe subtekenreeks.
   >[!NOTE]
   >
   >Alleen subtekenreeksen met dezelfde opmaak kunnen worden samengevoegd.

### Lagen groeperen om de zichtbaarheid ervan tegelijk te regelen{#group-layers}

Een andere manier om uw malplaatjes flexibel te houden, is door één enkele parameternaam te gebruiken om veelvoudige lagen te controleren. Deze strategie is handig voor de zichtbaarheidsparameter (lagen verbergen of weergeven) om het ontwerp of de afbeeldingen van één sjabloon bij te werken.

Volg deze stappen om de zelfde naam aan de [!UICONTROL Hide] parameters (![ snelle inhoudsverwezenlijking ](/help/assets/assets/Visibility-icon.svg)) van veelvoudige lagen toe te wijzen, toestaand u om hen gelijktijdig te verbergen of te tonen.

1. Navigeer naar de [**[!UICONTROL Properties Panel]**](#parameterise-a-layer) van een laag.
1. Schakel de parameter **[!UICONTROL Hide]** in als deze niet eerder is geparametereerd.
1. **Facultatief:** noem de **[!UICONTROL Hide]** Parameter anders.
1. Kopieer de naam van de parameter **[!UICONTROL Hide]** .
1. Ga naar het deelvenster Parameter van andere lagen door deze op het canvas te selecteren en schakel de parameter **[!UICONTROL Hide]** ervan in of u de parameters niet wilt wijzigen.
1. Vervang de naam **[!UICONTROL Hide parameter]** ervan door de gekopieerde naam.
1. Klik op **[!UICONTROL Save]** om de lagen te groeperen.
1. Voer stap 3 en vervolgens 4 uit in de sectie [**[!UICONTROL Preview and Publish]**](#preview-and-publish-template-and-copy-template-deliver-url) om uw wijzigingen te zien.

## De sjabloon voorvertonen en publiceren om de leverings-URL te kopiëren{#preview-and-publish-template-and-copy-template-deliver-url}

Voer de volgende stappen uit om de sjabloon voor te vertonen en te publiceren en de URL van de levering te kopiëren:

1. Klik op **[!UICONTROL Preview]** op de canvaspagina. U kunt ook naar **[!UICONTROL Assets View]** **>** **[!UICONTROL Dynamic Media Assets]** **>** zoeken navigeren en uw malplaatje selecteren **>** klikken **[!UICONTROL Edit Template]** **>** klikken **[!UICONTROL Preview]**. Op de voorvertoningspagina worden de sjabloon, de parameters (geparametereerde lagen en eigenschappen), de publicatiestatus en de optie **[!UICONTROL Publish]** weergegeven.
1. Selecteer parameters in het deelvenster **[!UICONTROL Template Parameters]** om de waarden van de parameters te bewerken en de inhoud, grootte, positie of tekstopmaak van de overeenkomstige sjabloonlaag in de voorvertoning direct bij te werken. Bijvoorbeeld:
   1. Selecteer een tekstlaag en bewerk de tekst of
   1. Selecteer een beeldlaag, klik ![ creërend inhoud op de vlucht ](/help/assets/assets/add-image.svg), selecteer een beeld van de activaselecteur, en klik **[!UICONTROL Refresh]**.

   De sjabloon wordt onmiddellijk bijgewerkt, waarbij de bewerkte tekst wordt weergegeven en de vorige afbeelding wordt vervangen door de nieuwe. Bovendien weerspiegelt de waarde van de afbeeldingsparameter het nieuwe afbeeldingspad. Op dezelfde manier kunt u het formaat van een laag aanpassen door zijn waarden aan te passen, en de veranderingen worden toegepast op het malplaatje in echt - tijd.
1. Selecteer de **[!UICONTROL Hide]** parameter voor [ gegroepeerde lagen ](#group-layers) van de lijst om hen samen in het malplaatje te tonen of te verbergen.
1. **Facultatief:** verander de **[!UICONTROL Hide]** parameterwaarde tussen 0 en 1 en klik **[!UICONTROL Refresh]** om de veranderingen te zien. Lagen met dezelfde parameter **[!UICONTROL Hide]** worden samen verborgen of weergegeven. Op dezelfde manier kunt u de zichtbaarheid van lagen bepalen via de URL.

   ![ creërend inhoud op de vlucht ](/help/assets/assets/dm-templates-publish-status.png)
U kunt **[!UICONTROL Include all parameters]** ook schakelen om alle weergegeven parameterwaarden te bewerken en de updates in de sjabloonvoorvertoning te bekijken.
   <br>
1. Als u de sjabloon vanaf de voorvertoningspagina wilt publiceren, klikt u op **[!UICONTROL Publish]** en bevestigt u dat u de sjabloon wilt publiceren. Er wordt een **[!UICONTROL Publish Complete]** -bericht weergegeven en de publicatiestatus wordt bijgewerkt naar **[!UICONTROL Published]** .

### De leverings-URL kopiëren

De geselecteerde parameters op de pagina **[!UICONTROL Preview]** worden de URL-parameters in de sjabloon-URL.

Zorg ervoor dat de afbeeldingen in de sjabloon al zijn gepubliceerd naar AEM en Dynamic Media om de leverings-URL van de sjabloon te genereren.

Voer de volgende stappen uit om de leverings-URL van de sjabloon te kopiëren:

1. Klik op **[!UICONTROL Copy URL]**. Het dialoogvenster **[!UICONTROL Copy URL]** wordt weergegeven. Selecteer en kopieer de weergegeven URL. De eerste parameter in URL begint na een vraagteken **([!UICONTROL ?])** en een zeer belangrijk-waardepaar begint met **[!UICONTROL $]** en beëindigt met **[!UICONTROL &]**. De sleutel en de waarde worden gescheiden door een gelijkteken **([!UICONTROL =])**, met de sleutel op de linkerzijde en de waarde op het recht.
1. Plak deze URL in het browsertabblad en bekijk de live sjabloon. Pas het malplaatje in real time aan door de vereiste waarde van de parameter (de waarde van Sleutel) in URL direct bij te werken zoals aangetoond in [ stap 2 ](#preview-and-publish-template-and-copy-template-deliver-url) van **Voorproef en publiceer** sectie.
1. Gebruik deze URL voor snelle verkoop van uw producten of services. U kunt deze URL delen met uw klanten of deze integreren in uw website of een andere downstreamtoepassing van derden om de banner weer te geven en er realtime updates voor uit te voeren die de lopende aanbiedingen weerspiegelen.

## Updates in real time van de sjabloon maken via de URL{#update-the-template-from-the-url}

Het rechtstreeks bewerken van parameters in de URL kan vervelend zijn. Ter vereenvoudiging:

1. Kopieer de URL en plak deze in een blok.
1. Gebruik Cmd+F (Mac) of Ctrl+F (Windows) om de parameterwaarden te zoeken en te bewerken. Bijvoorbeeld:
   * Afbeeldingspaden voor afbeeldingslagen zoeken en vervangen.
   * Vind de laag [ geparameterized ](#parameterise-a-layer) coördinaten, breedte en hoogte, om hun waarden aan te passen.
   * Bewerk tekst, lettertype, kleur, grootte of uitlijning voor tekstlagen.
   * Wijzig de zichtbaarheidswaarden tussen 0 en 1.

Plak deze bijgewerkte URL in uw browser om de wijzigingen weer te geven.

## De sjabloon bewerken{#edit-the-template}

Voer de volgende stappen uit om de sjabloon te bewerken:

1. Klik op [!DNL Assets view] in het **[!UICONTROL Dynamic Media Assets]** .
2. Navigeer naar de sjabloonlocatie.
3. Selecteer de sjabloon.
4. Klik op **[!UICONTROL Edit Template]**. Op het sjablooncanvas worden de sjabloon en de lijst met alle lagen in het deelvenster Lagen weergegeven. Begin uw sjabloon naar wens te bewerken.

## Koppeling naar Call to action (CTA) toevoegen aan uw sjabloonlaag{#add-CTA-in-dynamic-media-templates}

U kunt elke afbeelding, tekst of vormlaag van uw [!DNL Dynamic Media] -sjabloon omzetten in een hyperlink door er een CTA-koppeling aan toe te voegen die gebruikers naar een doelpagina stuurt.

Voer de volgende stappen uit om een CTA-koppeling aan een laag toe te voegen:

1. Navigeer aan uw malplaatjeplaats, selecteer het malplaatje en klik ![ uitgeven ](/help/assets/assets/edit-pen-icon.svg) **[!UICONTROL Edit Template]**. De sjabloon wordt weergegeven op het canvas.
1. Selecteer de malplaatjelaag en [ navigeer aan zijn eigenschappen paneel ](#edit-or-delete-a-layer) om een verbinding van CTA aan het toe te voegen.
1. Selecteer **[!UICONTROL Add CTA]** in het deelvenster Eigenschappen, geef de doel-URL op in het veld **[!UICONTROL URL]** en klik op **[!UICONTROL Save]** .

   ![ voeg CTA ](/help/assets/assets/add-cta.png) toe

1. Klik op **[!UICONTROL Preview]** en selecteer **[!UICONTROL Publish]** om de sjabloon te publiceren als deze niet eerder is gepubliceerd.
1. Navigeer aan de omslag waar dit malplaatje wordt bewaard, selecteer dit malplaatje en klik ![ detailspagina ](/help/assets/assets/details-page-icon.svg) **[!UICONTROL Details]**.
1. Klik op **[!UICONTROL Copy Options]** en selecteer **[!UICONTROL Copy Embed Code]** . Publiceer de sjabloonafbeeldingen naar [!DNL AEM and Dynamic Media] om de insluitcode te kopiëren.

   ![ exemplaar bedt code ](/help/assets/assets/copy-options1.png) in

   Hieronder ziet u een voorbeeld van de insluitcode:

   ```json
    <div class="adobe-dynamicmedia-template-embed-container">
    <img id="<Image ID>>" src="<Image Source>>" alt="adobe dynamicmedia template" usemap="#adobe-dynamicmedia-template-map" width="800" height="300">
    <map name="adobe-dynamicmedia-template-map">
    <area shape="rect" coords="417,-60,817,340" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    <area shape="rect" coords="6,206.57,129,231.43" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    </map>
    </div>
   ```

1. Voeg de gekopieerde insluitcode toe aan het HTML-bestand van uw site en voer deze code uit in uw browser om de sjabloon weer te geven.

Klik op het CTA-element op de sjabloon om naar de doelpagina te navigeren.

Bekijk deze stapsgewijze video om te leren hoe u een CTA-koppeling aan een sjabloonlaag kunt toevoegen.

>[!VIDEO](https://video.tv.adobe.com/v/3457616)

## Belangrijke opmerkingen {#important-points-to-note}

* Nadat u een sjabloon hebt gemaakt met geparametriseerde afbeeldingslagen voor dynamische updates, zorgt u ervoor dat de afbeeldingen die u wilt bijwerken in de toekomst dezelfde afmetingen hebben als de geparametriseerde afbeeldingen. Zo kunt u ervoor zorgen dat de afbeeldingen perfect in de lagen passen zonder dat ze te veel stromen of lege ruimten overblijven. De sjabloon ondersteunt momenteel geen automatische dimensionering om afbeeldingen in de lagen te passen.
* Een tekstlaag biedt geen ondersteuning voor subtekenreeksen. De gebruiker kan geen verschillende lettertype-eigenschappen toepassen op een subtekenreeks van een tekstlaag.
* Ondersteuning voor meerdere [!DNL Dynamic Media] -bedrijven is momenteel niet beschikbaar voor [!DNL Dynamic Media] Templates.
* In het geval van kopiëren of verplaatsen toont de Bestemmingskiezer alle mappen (inclusief niet- [!DNL Dynamic Media] gesynchroniseerde mappen). Momenteel worden ook niet de sjabloonelementen van [!DNL Dynamic Media] weergegeven (beide zijn beperkingen van de doelkiezer).
* Elke updatebewerking in een map (bijvoorbeeld Publiceren of Verwijderen) uit de Assets-sectie heeft invloed op de [!DNL Dynamic Media] -sjablonen die beschikbaar zijn in die map.
* Prullenbak werkt niet voor [!DNL Dynamic Media] sjablonen. Als een element naar de prullenbak wordt verplaatst en vervolgens wordt teruggezet, wordt het element in AEM teruggezet, maar niet op [!DNL Dynamic Media] . Hetzelfde geldt voor [!DNL Dynamic Media] Templates.

## Zie ook

1. Onderzoek [[!DNL Dynamic Media]  en zijn mogelijkheden ](/help/assets/dynamic-media/dynamic-media.md)
1. Onderzoek [[!DNL Dynamic Media]  met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md)