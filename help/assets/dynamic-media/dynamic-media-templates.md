---
title: Hoe te om  [!DNL Dynamic Media]  malplaatjes te beheren?
description: Leer hoe te om  [!DNL Dynamic Media]  malplaatjes tot stand te brengen gebruikend een het malplaatjeredacteur van WYSIWYG en veelvoudige beelden en tekstlagen te omvatten om banners en vliegers snel tot stand te brengen en hen in stroomafwaartse toepassingen te gebruiken.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: 6223937acc317ea57a7e91c90bac36f1b1d4be67
workflow-type: tm+mt
source-wordcount: '2886'
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

Maak aanpasbare sjablonen in real time voor uw banners en vliegers met gebruik van [!DNL Dynamic Media] sjablonen, een WYSIWYG-sjablooneditor. Gebruik de [!DNL Dynamic Media] -sjabloon in downstreamtoepassingen. Een [!DNL Dynamic Media] -sjabloon bevat afbeeldings- en tekstlagen. Voeg parameters aan het beeld en tekstlagen van het malplaatje toe en gebruik [[!DNL Dynamic Media]  URLs ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media) om de laag te verplaatsen en resize en zijn inhoud in real time bij te werken.

Enkele van de belangrijkste kenmerken zijn:

* **[!DNL Dynamic Media]WYSIWYG Template Editor:** Maak aanpasbare banners met afbeeldings- en tekstlagen.
* **Laagparametrisering:** Definieer dynamische sleutel-waardeparen voor lagen om realtime updates mogelijk te maken.
* **[!DNL Dynamic Media]URL-ondersteuning:** Gebruik [!DNL Dynamic Media] URL&#39;s voor sjablonen, waarbij gepersonaliseerde waarden van 1e of externe applicaties worden geïntegreerd.
* **Controle over de zichtbaarheid van lagen:** Verberg of toon lagen dynamisch als dat nodig is.
* **Slimme tekstgrootte:** Pas de tekstgrootte automatisch aan de aangewezen gebieden aan.

Enkele van de belangrijkste voordelen van [!DNL Dynamic Media] sjablonen zijn:

* **Optimaliseer 1:1 personalisatie:** Stem content af op real-time klantsignalen.
* **Verminder handmatige inspanningen:** Automatiseer en versnel de creatie en het beheer van content.
* **Zorg voor consistente omnichannel-ervaringen:** Zorg voor merkconsistentie op alle kanalen.
* **Inhoud effectief hergebruiken:** Vermijd inhoud voor eenmalig gebruik en schaal op met dynamische, geparametriseerde sjablonen.
* **Beperk risico&#39;s:** Werk prijzen, kortingen en links in realtime bij.
* **Verbeter de klantbetrokkenheid:** Stimuleer interactieve, contextueel relevante ervaringen.

>[!NOTE]
>
>Klanten met een abonnement op de SKU Verbeterde beveiliging kunnen geen mogelijkheden, inclusief [!DNL Dynamic Media] sjablonen, gebruiken [!DNL Dynamic Media] in dat Cloud Services-programma.

## Voordat u begint{#prerequisites-for-dynamic-media-wysiwyg-template}

Als u een sjabloon wilt maken, moet u over het [!DNL Dynamic Media] volgende beschikken:

1. Toegang tot [!DNL Dynamic Media].
1. [Gesynchroniseerde de afbeeldingen die beschikbaar zijn in uw [!DNL AEM Assets] instantie om [!DNL Dynamic Media] ze te gebruiken voor het maken van de sjabloon](/help/assets/dynamic-media/config-dm.md).
1. heeft het volgende gecontroleerd in de Touch UI:
   * Op de **[!UICONTROL Edit [!DNL Dynamic Media] Configuration page]**, **[!UICONTROL [!DNL Dynamic Media] sync mode]** die is ingesteld op **[!UICONTROL Disabled by default]**, wordt niet toegepast op alle AEM mappen (**[!UICONTROL Sync all content]** is niet aangevinkt). Zie [Dynamic Media Cloud Service](/help/assets/dynamic-media/config-dm.md) configureren voor meer informatie.
   * **[!UICONTROL [!DNL Dynamic Media] sync mode]** is ingesteld op **[!UICONTROL Enable for subfolders]** voor de doelmap of submap waarin u de sjabloon opslaat nadat u deze hebt gemaakt. Zie [Cloudservice](/help/assets/dynamic-media/config-dm.md) configureren [!DNL Dynamic Media] voor meer informatie.

## [!DNL Dynamic Media] WYSIWYG-sjabloon maken{#how-to-create-dynamic-media-wysiwyg-template}

Voer de volgende stappen uit om een [!DNL Dynamic Media] -sjabloon te maken:

1. Navigeer aan uw [!DNL Assets View] en [ creeer een omslag ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in **[!UICONTROL Assets]**. De mapstructuur in **[!UICONTROL Assets]** wordt herhaald in **[!UICONTROL Dynamic Media Assets]** . Gebruik deze [!UICONTROL Dynamic Media Assets] map om uw [!DNL Dynamic Media] sjabloon later op te slaan.
1. Selecteer **[!UICONTROL Assets]** en [upload en publiceer uw afbeeldingen naar [!DNL AEM] en [!DNL Dynamic Media] tegelijkertijd](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm#dynamic-media-publish-mode-set-to-upon-activation) om ze te gebruiken voor het maken van de sjabloon.
1. [Een leeg canvas maken](#create-a-canvas)
1. [Afbeeldingen toevoegen aan het canvas](#add-images-to-the-canvas)
1. [Tekstlagen toevoegen aan het canvas](#add-text-to-the-canvas)
1. [Een laag bewerken of verwijderen](#edit-or-delete-a-layer)
1. [Lagen parametereren](#parameterise-a-layer)

### Een leeg canvas maken{#create-a-canvas}

Voer de volgende stappen uit om een leeg canvas te maken:

1. Navigeer naar [!DNL Assets View] en selecteer **[!UICONTROL Dynamic Media Assets]** beschikbaar in het linkerdeelvenster.

   ![Sjablonen voor dynamische media](/help/assets/assets/DM-Assets1.png)

1. Selecteer **[!UICONTROL Create Template]** op deze pagina of navigeer naar uw **[!UICONTROL Dynamic Media Assets]** map en selecteer **[!UICONTROL Create Template]**. De sjabloon wordt opgeslagen op de locatie waar u de sjabloon maakt, in de hoofdmap zoals **[!UICONTROL Dynamic Media Assets]** of in een map in de hoofdmap. Nadat u het dialoogvenster hebt geselecteerd **[!UICONTROL Create Template]** , wordt het **[!UICONTROL New Template]** weergegeven.
   ![ hoe te om dynamische malplaatjes tot stand te brengen die in real time kunnen worden aangepast ](/help/assets/assets/new-template.png)

1. Geef een sjabloonnaam op, definieer de canvasbreedte en -hoogte en klik op **[!UICONTROL Create]** . Er wordt een leeg canvas weergegeven met menuopties aan beide zijden voor het maken van de sjabloon. Houd de muisaanwijzer boven de menuopties om de knopinfo weer te geven.
   ![ in real time aanpasbaar malplaatje ](/help/assets/assets/blank-canvas-page.png)

   >[!NOTE]
   >
   > Het toegestane breedte- en hoogtebereik ligt tussen 50 en 5000.

**opties van het Menu op de juiste ruit:** Gebruik deze opties om de noodzakelijke beelden en tekstlagen aan het canvas toe te voegen.

* ![ DM Malplaatjes ](/help/assets/assets/add-image.svg): Klik om beelden aan het canvas toe te voegen.
* ![ aanpasbare malplaatjes ](/help/assets/assets/add-text.svg): Klik om teksten aan het canvas toe te voegen.
* ![ aanpasbare malplaatjes ](/help/assets/assets/show-layers-list.svg): Klik om de lijst van alle lagen (beeld en tekst) op het canvas te zien. Elke afbeelding en tekst die aan het canvas wordt toegevoegd, wordt weergegeven als een afzonderlijke laag.

**opties van het Menu op de linkerruit:** Gebruik deze opties voor gemeenschappelijke redacteursacties zoals hieronder vermeld.

* ![ DM Malplaatjes ](/help/assets/assets/layer-selector.svg): Selecteer een laag.
* ![ malplaatjes die aanpassing ](/help/assets/assets/bring-forward.svg) steunen: Klik om een geselecteerde laag vooruit te brengen of **CTRL** + **te drukken]** (Vensters) of **Cmd** + **]** (Mac).
* ![ hoe te om een malplaatje tot stand te brengen dat gemakkelijk kan worden aangepast ](/help/assets/assets/send-backward.svg): Klik om een geselecteerde laag achterwaarts te verzenden of **CTRL** + **te drukken (** (Vensters) of **Cmd** + **(**) (Mac).
* ![ creeer een malplaatje dat onmiddellijk ](/help/assets/assets/undo.svg) kan worden aangepast: klik om de laatste actie ongedaan te maken of **CTRL** + **te drukken Z** (Vensters) of **Cmd** + **Z** (Mac).
* ![ malplaatje om banners snel ](/help/assets/assets/redo.svg) tot stand te brengen: Klik om de laatste actie opnieuw uit te voeren of **CTRL** + **Y** (Vensters) of **Cmd** + **Y** (Mac) te drukken.
* ![ malplaatje om snel flyers ](/help/assets/assets/zoom-in.svg) tot stand te brengen: Klik om binnen het canvas te zoemen of **CTRL** + **+** (Vensters) of Cmd + **+** (Mac) te drukken.
* ![ malplaatje om banners snel ](/help/assets/assets/Zoom-out.svg) tot stand te brengen: Klik om uit het canvas te zoemen of **CTRL** + **te drukken -** (Vensters) of **Cmd** + **-** (Mac).
* Pers **Backspace** of **schrapt** om de geselecteerde laag te schrappen als geen tekst of het bezit wordt uitgegeven.

Klik ![ malplaatje om snel flyers ](/help/assets/assets/show-layers-list.svg) **>** meer opties (![](/help/assets/assets/three-dots.svg)) op de laag van het Canvas te creëren om de canvasdimensies op elk ogenblik uit te geven terwijl het creëren van het malplaatje.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> Sjablonen staan maximaal 20 lagen toe, waaronder het canvas.

### Afbeeldingen toevoegen aan het canvas{#add-images-to-the-canvas}

Voer de volgende stappen uit om afbeeldingen aan het canvas toe te voegen:

1. Klik in een mum van tijd](/help/assets/assets/add-image.svg) op ![een banner maken om het [deelvenster Asset Selector](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) weer te geven. In het deelvenster worden de afbeeldingen in uw AEM Assets-instantie weergegeven die zijn gesynchroniseerd met [!DNL Dynamic Media].
1. Blader door het paneel of gebruik trefwoorden in de zoekbalk om een specifieke afbeelding te vinden.
1. Sleep een afbeelding op het canvas om deze te gebruiken. Zie voor het wijzigen van het [**[!UICONTROL Properties Panel]**](#reposition-resize-delete-a-layer) formaat of de positie van een laag op het canvas.
   ![Maak binnen enkele seconden een banner](/help/assets/assets/add-image-to-canvas.png)

### Tekstlagen toevoegen aan het canvas{#add-text-to-the-canvas}

Voer deze stappen uit om tekstlagen aan het canvas toe te voegen:

1. Klik snel](/help/assets/assets/add-text.svg) op ![het maken van nieuwe banners om een tekstlaag aan het canvas toe te voegen en open het deelvenster Eigenschappen.
1. Selecteer de laag en klik op de tekst om deze bij te werken.
1. Selecteer **[!UICONTROL Smart Text Resize]** in het deelvenster Eigenschappen om de tekstlengte en tekengrootte automatisch aan te passen zodat deze optimaal in het aangewezen gebied passen.
   ![Beste aanpasbare banners](/help/assets/assets/add-text-layer.png)

Zie de [**[!UICONTROL Properties Panel]**](#reposition-resize-delete-a-layer) om de laag te verplaatsen, te vergroten, te verkleinen, te roteren of te verwijderen. Maak uw tekst op in het gewenste lettertype, de gewenste grootte, de kleur, de stijl en de uitlijning (in de laag) door de waarden te wijzigen in de respectieve velden onder de **[!UICONTROL Text]** sectie van het paneel.

>[!NOTE]
>
> Als u een ander lettertype wilt gebruiken dan de standaardlettertypefamilie Adobe Sans F2, moet u het lettertypebestand uploaden en publiceren naar [!AEM Assets] en [!DNL Dynamic Media]. Als u een aantal oude lettertypen in uw exemplaar hebt, zorg er dan voor dat u [ze opnieuw](/help/assets/reprocessing-assets-view.md) verwerkt om ze in de sjablooneditor te bekijken.

### Een laag bewerken of verwijderen {#edit-or-delete-a-layer}

Voer de volgende stappen uit om een canvaslaag te bewerken of te verwijderen:

1. Klik op ![sjablonen met ondersteuning voor dynamische updates](/help/assets/assets/show-layers-list.svg) en selecteer de laag op het canvas of in de lijst met lagen.
1. Klik **[!UICONTROL more options]** (![ malplaatjes met steun aan updates in real time ](/help/assets/assets/three-dots.svg)) om de laag uit te geven of te schrappen.
1. Klik op **[!UICONTROL Delete]** om de laag te verwijderen.
1. Klik op **[!UICONTROL Edit]** om de laag te bewerken met [**[!UICONTROL Properties Panel]**](#reposition-resize-delete-a-layer) .
   ![ snelle bannerverwezenlijking ](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Deelvenster Eigenschappen{#properties-panel}

Navigeren naar het deelvenster met laageigenschappen:

1. Klik ![ snelle inhoudsverwezenlijking ](/help/assets/assets/show-layers-list.svg).
1. Selecteer de laag in de lijst.

In dit deelvenster worden de positie van het middelpunt van de laag op het canvasvlak (X- en Y-waarden) en de afmetingen van de laag (breedte en hoogte) weergegeven, samen met tekstopmaakopties.

![ snelle inhoudsverwezenlijking ](/help/assets/assets/properties-panel.png)

Selecteer in het eigenschappenvenster van een laag een andere laag op het canvas om naar het eigenschappenvenster te navigeren.


#### Een laag verplaatsen, vergroten of verkleinen, roteren of verwijderen{#reposition-resize-delete-a-layer}

Bekijk deze veelvoorkomende acties voor het bewerken van lagen om een tekst- of afbeeldingslaag te bewerken:

* **verplaats de laag:** sleep de laag om het overal op het canvas te bewegen. Met deze actie worden de X- en Y-waarden in het deelvenster Eigenschappen bijgewerkt.
* **resize de laag:** selecteer de laag en sleep zijn randhandvatten om het te resize. Met deze handeling worden de waarden voor B (breedte) en H (hoogte) in het deelvenster Eigenschappen bijgewerkt.
* **roteer de laag:** sleep het vierkante handvat dat verticaal boven de laag wordt geplaatst om het rond zijn centrum te roteren. Met deze actie worden de hoekwaarden in het eigenschappenpaneel bijgewerkt.
* **De laag verwijderen:** Druk op **Backspace** of **delete** en klik vervolgens om **[!UICONTROL Confirm]** een geselecteerde laag te verwijderen.

#### Opties voor tekstopmaak{#text-formatting-options-on-properties-panel}

Maak uw tekst op in het gewenste lettertype, de grootte, de kleur, de stijl en de uitlijning (binnen de laag) door de waarden te wijzigen in de respectievelijke velden onder het **[!UICONTROL Text]** gedeelte op het paneel.
Zorg ervoor dat u **[!UICONTROL Smart Text Resize]**. [!UICONTROL Smart Text Resize] werkt op [Copyfitting](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting) algorithum om tekst in het tekstgebied optimaal te vullen en voorkomt tekstoverloop en minimaliseert extra ruimte onderaan de tekst.

![ inhoudsverwezenlijking in geen tijd ](/help/assets/assets/smart-text-resize.png)

### Lagen parametereren {#parameterise-a-layer}

Nadat u een sjabloon met meerdere lagen afbeeldingen en tekst hebt gemaakt, kunt u de parameters van de geselecteerde lagen bepalen. Wanneer een laag of zijn bezit wordt bepaald, krijgt het een zeer belangrijk-waardepaar (ook genoemd als parameter). Deze parameter kan in het malplaatje URL worden omvat om de positie, de grootte of de inhoud van de laag in echt bij te werken - tijd resulterend in malplaatjeaanpassing in geen tijd.

U kunt als volgt een laag bepalen:

1. klik ![ onmiddellijke inhoudsverwezenlijking ](/help/assets/assets/show-layers-list.svg), selecteer een laag en klik **[!UICONTROL Parameters]**. Het deelvenster **[!UICONTROL Parameters]** wordt weergegeven.
1. Schakel **[!UICONTROL Include Parameter]** in om een eigenschap te bepalen. Zie [ het paneeloptie van Parameters ](#parameterisation-options-or-allowed-parameters) om het gedrag van het bezit na parameterization te kennen.
1. **Facultatief:** noem de parameternaam anders. Een parameternaam heeft een laagnaam gevolgd door een achtervoegsel. Voor een geselecteerde laag delen alle eigenschappen met parameters dezelfde laagnaam, gevolgd door een variërend achtervoegsel. Wijzig de naam van de laag door de semantische noemende overeenkomst te volgen zodat wanneer u de parameter in URL omvat, de parameternaam zelf over de inhoud van de laag of zijn doel verklaart.
1. Klik op **[!UICONTROL Save]**.
   ![ onmiddellijke inhoudsverwezenlijking ](/help/assets/assets/parameterise-a-layer.png)
Als u wilt schakelen tussen het deelvenster Parameter van een afbeelding en een tekstlaag, selecteert u de laag op het canvas en klikt u op **[!UICONTROL Parameters]** .

#### Opties in het deelvenster Parameters {#parameterisation-options-or-allowed-parameters}

De parameters van eigenschappen kunnen als parameters URL in het malplaatje URL worden omvat om het malplaatje in echt uit te geven - tijd gebruikend URL.

**parameters van het Beeld:**

**[!UICONTROL X]:** neem op om de laag horizontaal langs zijn middellijn, parallel aan de x-as van het malplaatjevliegtuig, te bewegen door de waarde van de parameter in URL te veranderen.
**[!UICONTROL Y]:** neem op om de laag verticaal langs zijn centrumlijn, parallel aan de y-as van het malplaatjevlak te bewegen, door de waarde van de parameter in URL te veranderen.
**[!UICONTROL Width]:** neem op om de breedte van de laag aan te passen door de waarde van de parameter in URL te wijzigen.
**[!UICONTROL Height]:** neem op om de hoogte van de laag aan te passen door de waarde van de parameter in URL te wijzigen.
**[!UICONTROL Hide]:** neem op om de laag in de sjabloon te verbergen of weer te geven met 0 (show) en 1 (hide).
**[!UICONTROL Source]:** neem op om de afbeelding van de laag te vervangen door een nieuwe afbeelding door het afbeeldingspad te wijzigen in de waarde van de parameter in de URL.

**het formatteren van de Tekst parameters:**

Neem de onderstaande parameters op om de tekst, het lettertype, de kleur en de grootte van de tekst vanuit de URL te bewerken door de parameterwaarden in de URL bij te werken.

**[!UICONTROL Text]:** neem hier tekst op om de URL bij te werken.
**[!UICONTROL Font Family]:** Opnemen om het lettertype van de tekst bij te werken vanaf de URL.
**[!UICONTROL Font Size]:** Opnemen om de lettergrootte van de tekst bij te werken vanaf de URL.
**[!UICONTROL Text color]:** Opnemen om de tekstkleur van de URL bij te werken.

### Groepeer lagen om hun zichtbaarheid tegelijkertijd te regelen{#group-layers}

Een andere manier om uw sjablonen flexibel te houden, is door een enkele parameternaam te gebruiken om meerdere lagen te beheren. Deze strategie is handig voor de parameter zichtbaarheid (lagen verbergen of weergeven), om het ontwerp of de afbeeldingen bij te werken vanuit één sjabloon.

Volg deze stappen om dezelfde naam toe te wijzen aan de verbergparameters (![snelle contentcreatie](/help/assets/assets/Visibility-icon.svg)) van meerdere lagen, zodat u ze tegelijkertijd kunt verbergen of weergeven.

1. Navigeer naar de [**[!UICONTROL Properties Panel]**](#parameterise-a-layer) van een laag.
1. Schakel de **[!UICONTROL Hide]** parameter in als deze niet eerder is geparametriseerd.
1. **Optioneel:** Wijzig de naam van de **[!UICONTROL Hide]** parameter.
1. Kopieer de **[!UICONTROL Hide]** parameternaam.
1. Ga naar het deelvenster Parameter van andere lagen door ze in het canvas te selecteren en schakel hun **[!UICONTROL Hide]** parameter in als deze niet is geparametriseerd.
1. Vervang de **[!UICONTROL Hide parameter]** naam door de gekopieerde naam.
1. Klik om **[!UICONTROL Save]** de lagen te groeperen.
1. Voer stap 3 en vervolgens 4 in [**[!UICONTROL Preview and Publish]**](#preview-and-publish-template-and-copy-template-deliver-url) sectie uit om uw wijzigingen te bekijken.

## Bekijk een voorbeeld en publiceer de sjabloon om de leverings-URL te kopiëren{#preview-and-publish-template-and-copy-template-deliver-url}

Voer deze stappen uit om de sjabloon te bekijken en te publiceren en de leverings-URL te kopiëren:

1. Klik op de canvaspagina op **[!UICONTROL Preview]**. U kunt ook naar **[!UICONTROL Assets View]** **>** ****[!UICONTROL Dynamic Media Assets]**navigeren >** uw sjabloon **zoeken en selecteren >** op ****[!UICONTROL Edit Template]**>** klikken klikken.**[!UICONTROL Preview]** Op de voorbeeldpagina worden de sjabloon, de parameters (geparametriseerde lagen en eigenschappen), de publicatiestatus en de **[!UICONTROL Publish]** optie weergegeven.
1. Selecteer parameters in het deelvenster **[!UICONTROL Template Parameters]** om de waarden van de parameters te bewerken en de inhoud, grootte, positie of tekstopmaak van de overeenkomstige sjabloonlaag in de voorvertoning direct bij te werken. Bijvoorbeeld:
   1. Selecteer een tekstlaag en bewerk de tekst of
   1. Selecteer een beeldlaag, klik ![ creërend inhoud op de vlucht ](/help/assets/assets/add-image.svg), selecteer een beeld van de activaselecteur, en klik **[!UICONTROL Refresh]**.

   De sjabloon wordt onmiddellijk bijgewerkt, waarbij de bewerkte tekst wordt weergegeven en de vorige afbeelding wordt vervangen door de nieuwe. Bovendien weerspiegelt de waarde van de afbeeldingsparameter het nieuwe afbeeldingspad. Op dezelfde manier kunt u het formaat van een laag aanpassen door zijn waarden aan te passen, en de veranderingen worden toegepast op het malplaatje in echt - tijd.
1. Selecteer de **[!UICONTROL Hide]** parameter voor [ gegroepeerde lagen ](#group-layers) van de lijst om hen samen in het malplaatje te tonen of te verbergen.
1. **Facultatief:** verander de **[!UICONTROL Hide]** parameterwaarde tussen 0 en 1 en klik **[!UICONTROL Refresh]** om de veranderingen te zien. Lagen met dezelfde parameter **[!UICONTROL Hide]** worden samen verborgen of weergegeven. Op dezelfde manier kunt u de zichtbaarheid van lagen bepalen via de URL.

   ![ creërend inhoud op de vlucht ](/help/assets/assets/dm-templates-publish-status.png)
U kunt **[!UICONTROL Include all parameters]** ook schakelen om alle weergegeven parameterwaarden te bewerken en de updates in de sjabloonvoorvertoning te bekijken.
   <br>
1. Als u de sjabloon op de voorvertoningspagina wilt publiceren, klikt u op **[!UICONTROL Publish]** en bevestigt u dat u de sjabloon wilt publiceren. Publiceer volledige berichtweergaven en de publicatiestatusupdates naar Gepubliceerd.

>[!NOTE]
>
>Als u de sjabloon wilt publiceren, moeten de sjabloonafbeeldingen eerst worden gepubliceerd.

### Kopieer de bezorgings-URL

De geselecteerde parameters op de pagina **[!UICONTROL Preview]** worden de URL-parameters in de sjabloon-URL.

U kunt als volgt de URL van de gepubliceerde sjabloon kopiëren die in de voorvertoning wordt weergegeven:

1. Klik op **[!UICONTROL Copy URL]**. Het dialoogvenster **[!UICONTROL Copy URL]** wordt weergegeven. Selecteer en kopieer de weergegeven URL. De eerste parameter in de URL begint na een vraagteken **([!UICONTROL ?])** en een sleutel-waardepaar begint met **[!UICONTROL $]** en eindigt met **[!UICONTROL &]**. De sleutel en de waarde worden gescheiden door een gelijkteken **([!UICONTROL =]),** met de sleutel aan de linkerkant en de waarde aan de rechterkant.
1. Plak deze URL in uw browsertabblad en bekijk uw live-sjabloon. Pas de sjabloon in realtime aan door de vereiste parameterwaarde (sleutelwaarde) rechtstreeks in de URL bij te werken, zoals wordt gedemonstreerd in [stap 2](#preview-and-publish-template-and-copy-template-deliver-url) van **de sectie Voorbeeld en publicatie** .
1. Gebruik deze URL voor snelle merchandising van uw producten of diensten. U kunt deze URL delen met uw klanten of integreren in uw website of een downstream-applicatie van derden om de banner weer te geven en er realtime updates op uit te voeren om de lopende aanbiedingen weer te geven.

Leer hoe u in deze video stap voor stap een [!DNL Dynamic Media] -sjabloon maakt.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

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

1. Klik op **[!UICONTROL Dynamic Media Assets]** in het [!DNL Assets view] .
2. Navigeer naar de sjabloonlocatie.
3. Selecteer de sjabloon.
4. Klik op **[!UICONTROL Edit Template]**. Op het sjablooncanvas worden de sjabloon en de lijst met alle lagen in het deelvenster Lagen weergegeven. Begin uw sjabloon naar wens te bewerken.

## Vraag aan Actie toevoegen (CTA) verbinding aan uw malplaatjelaag{#add-CTA-in-dynamic-media-templates}

Zet een afbeeldings- of tekstlaag van de [!DNL Dynamic Media] -sjabloon om in een hyperlink door er een CTA-koppeling aan toe te voegen die gebruikers naar een doelpagina stuurt. Voer de volgende stappen uit om een CTA-koppeling aan een laag toe te voegen:

1. Navigeer aan uw malplaatjeplaats, selecteer het malplaatje en klik ![ uitgeven ](/help/assets/assets/edit-pen-icon.svg) **[!UICONTROL Edit Template]**. De sjabloon wordt weergegeven op het canvas.
1. Selecteer de malplaatjelaag en [ navigeer aan zijn eigenschappen paneel ](#edit-or-delete-a-layer) om een verbinding van CTA aan het toe te voegen.
1. Selecteer **[!UICONTROL Add CTA]** in het deelvenster Eigenschappen, geef de doel-URL op in het veld **[!UICONTROL URL]** en klik op **[!UICONTROL Save]** .

   ![ voeg CTA ](/help/assets/assets/add-cta.png) toe

1. Klik op **[!UICONTROL Preview]** om een voorvertoning van de sjabloon weer te geven en de gedefinieerde parameters te bekijken.
1. Klik op **[!UICONTROL Publish]** en selecteer **[!UICONTROL Yes]** om de sjabloon te publiceren als deze niet eerder is gepubliceerd.
1. Navigeer aan de omslag waar dit malplaatje wordt bewaard, selecteer dit malplaatje en klik ![ detailspagina ](/help/assets/assets/details-page-icon.svg) **[!UICONTROL Details]**.
1. Klik op **[!UICONTROL Copy Options]** en selecteer **[!UICONTROL Copy Embed Code]** .

   ![Insluitcode kopiëren](/help/assets/assets/copy-options1.png)

   Het volgende is een voorbeeld van de insluitcode:

   ```json
    <div class="adobe-dynamicmedia-template-embed-container">
    <img id="<Image ID>>" src="<Image Source>>" alt="adobe dynamicmedia template" usemap="#adobe-dynamicmedia-template-map" width="800" height="300">
    <map name="adobe-dynamicmedia-template-map">
    <area shape="rect" coords="417,-60,817,340" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    <area shape="rect" coords="6,206.57,129,231.43" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    </map>
    </div>
   ```

1. Voeg de gekopieerde insluitcode toe aan het HTML-bestand van uw site en voer deze uit in uw browser om de sjabloon weer te geven.

Klik op het CTA-element in de sjabloon om naar de bestemmingspagina te navigeren.

Bekijk deze stapsgewijze video om te leren hoe u een CTA-link toevoegt aan een sjabloonlaag.

>[!VIDEO](https://video.tv.adobe.com/v/3457616)

## Belangrijke punten om op te merken {#important-points-to-note}

* Nadat u een sjabloon hebt gemaakt met geparametriseerde afbeeldingslagen voor dynamische updates, moet u ervoor zorgen dat de afbeeldingen die bedoeld zijn voor toekomstige updates dezelfde afmetingen hebben als de geparametriseerde afbeeldingen. Dit zorgt ervoor dat de afbeeldingen perfect in de lagen passen zonder over te lopen of lege ruimtes achter te laten. Momenteel biedt de sjabloon geen ondersteuning voor automatische maatvoeringsaanpassingen om afbeeldingen in de lagen te passen.
* Er is geen ondersteuning voor subtekenreeksen in een tekstlaag. De gebruiker kan geen verschillende lettertype-eigenschappen toepassen op de subtekenreeks van een tekstlaag.
* Ondersteuning voor meerdere [!DNL Dynamic Media] -bedrijven is momenteel niet beschikbaar voor [!DNL Dynamic Media] Templates.
* In het geval van kopiëren of verplaatsen toont de Bestemmingskiezer alle mappen (inclusief niet- [!DNL Dynamic Media] gesynchroniseerde mappen). Momenteel worden de [!DNL Dynamic Media] Sjabloonelementen niet weergegeven (beide zijn beperkingen van de doelkiezer).
* Elke updatebewerking in een map (bijvoorbeeld Publiceren of Verwijderen) uit de Assets-sectie heeft invloed op de [!DNL Dynamic Media] -sjablonen die beschikbaar zijn in die map.
* Prullenbak werkt niet voor [!DNL Dynamic Media] sjablonen. Als een element naar de prullenbak wordt verplaatst en vervolgens wordt teruggezet, wordt het element in AEM teruggezet, maar niet op [!DNL Dynamic Media] . Hetzelfde geldt voor [!DNL Dynamic Media] Templates.

## Zie ook

1. Onderzoek [[!DNL Dynamic Media]  en zijn mogelijkheden ](/help/assets/dynamic-media/dynamic-media.md)
1. Onderzoek [[!DNL Dynamic Media]  met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md)
