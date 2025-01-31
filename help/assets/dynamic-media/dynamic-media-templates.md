---
title: Hoe kan ik Dynamic Media-sjablonen beheren?
description: Leer hoe u Dynamic Media-sjablonen maakt met een WYSIWYG-sjablooneditor en meerdere afbeeldingen en tekstlagen opneemt om snel banners en flyers te maken en deze te gebruiken in downstreamtoepassingen.
hide: true
role: User
source-git-commit: ada339567716a126d3288246c148c551dff298f4
workflow-type: tm+mt
source-wordcount: '2592'
ht-degree: 0%

---

# Dynamic Media-sjablonen{#dynamic-media-templates}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|-----|

Maak Dynamic Media-sjablonen met een WYSIWYG-sjablooneditor en voeg meerdere afbeeldingen en tekstlagen toe om snel banners en flyers te maken en deze te gebruiken in downstreamtoepassingen. U kunt parameters aan de beelden en tekstlagen ook toevoegen inbegrepen in het malplaatje en [ Dynamic Media URLs ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media) gebruiken om de waarden voor die lagen in real time bij te werken.

Enkele van de belangrijkste functies zijn:

* **de Redacteur van het Malplaatje van Dynamic Media WYSIWYG:** creeer klantgerichte banners met beeld en tekstlagen.
* **Parameterization van de Laag:** bepaal dynamische sleutel-waarde paren voor lagen om updates in real time toe te laten.
* **de Steun van Dynamic Media URL:** Gebruik Dynamic Media URLs voor malplaatjes, die gepersonaliseerde waarden van eerste of derdetoepassingen integreren.
* **Controle van de Zichtbaarheid van de Laag:** verberg of toon dynamisch lagen zoals nodig.
* **Slimme Tekst het Randen van de Tekst:** past automatisch tekstgrootte aan om aangewezen gebieden te passen.

Enkele belangrijke voordelen van Dynamic Media-sjablonen zijn:

* **optimaliseer 1:1 Personalization:** Inhoud van de Tailor aan klantensignalen in real time.
* **Verminder Handmatige inspanning:** Automate en versnelt inhoudsverwezenlijking en beheer.
* **verzekert Consistente Ervaringen Omnichannel:** handhaaf merkconsistentie over kanalen.
* **Reuse Inhoud effectief:** vermijd enig-gebruiksinhoud en schaal met dynamische, geparametereerde malplaatjes.
* **Mitigate Risks:** update tarifering, kortingen, en verbindingen in real time.
* **verbeter de Betrokkenheid van de Klant:** aandrijving interactieve, contextafhankelijk relevante ervaringen.

>[!NOTE]
>
>Klanten met een abonnement op de uitgebreide beveiligingsSKU kunnen geen Dynamic Media-mogelijkheden, waaronder Dynamic Media Templates, voor dat Cloud Service-programma gebruiken.

## Voordat u begint{#prerequisites-for-dynamic-media-wysiwyg-template}

Als u een Dynamic Media-sjabloon wilt maken, moet u beschikken over:

1. Toegang tot Dynamic Media.
1. [ synchroniseerde de beelden beschikbaar in uw instantie van AEM Assets met Dynamic Media om hen te gebruiken voor het creëren van het malplaatje ](/help/assets/dynamic-media/config-dm.md).

## Dynamic Media WYSIWYG-sjabloon maken{#how-to-create-dynamic-media-wysiwyg-template}

Ga als volgt te werk om een DM-sjabloon te maken:

1. [Een leeg canvas maken](#create-a-canvas)
1. [Afbeeldingen toevoegen aan het canvas](#add-images-to-the-canvas)
1. [Tekstlagen toevoegen aan het canvas](#add-text-to-the-canvas)
1. [Een laag bewerken of verwijderen](#edit-or-delete-a-layer)
1. [Lagen parametereren](#parameterise-a-layer)


### Een leeg canvas maken{#create-a-canvas}

Voer de volgende stappen uit om een leeg canvas te maken:

1. Navigeer aan de Mening van Assets en klik **Dynamic Media Assets** beschikbaar in het linkerpaneel.

   ![](/help/assets/assets/dm-templates/DM-Assets1.png)

1. Klik **creëren Malplaatje** om het malplaatje onder Dynamic Media Assets te bewaren of aan een omslag te navigeren en **te klikken creeer Malplaatje** om het malplaatje binnen die omslag te bewaren. De **Nieuwe vertoningen van de Malplaatje** dialoogdoos.
   ![](/help/assets/assets/dm-templates/new-template.png)
Om [ tot een omslag ](/help/assets/add-delete-assets-view.md) onder **Dynamic Media Assets** te leiden, creeer een omslag onder **Assets**. De omslagboom onder **Assets** duikt onder **Assets van Dynamic Media**.
1. Specificeer een malplaatjenaam, bepaal de de canvasbreedte en hoogte, en klik **creeer**. Er wordt een leeg canvas weergegeven met menuopties aan beide zijden voor het maken van de sjabloon. Houd de muisaanwijzer boven de menuopties om de knopinfo weer te geven.
   ![](/help/assets/assets/dm-templates/blank-canvas-page.png)

>[!NOTE]
>
> Het toegestane breedte- en hoogtebereik ligt tussen 50 en 5000.

**opties van het Menu op de juiste ruit:** Gebruik deze opties om de noodzakelijke beelden en tekstlagen aan het canvas toe te voegen.

* ![](/help/assets/assets/dm-templates/add-image.svg): klik om afbeeldingen toe te voegen aan het canvas.
* ![](/help/assets/assets/dm-templates/add-text.svg): klik om tekst aan het canvas toe te voegen.
* ![](/help/assets/assets/dm-templates/show-layers-list.svg) - Klik om de lijst met alle lagen (afbeelding en tekst) op het canvas weer te geven. Elke afbeelding en tekst die aan het canvas wordt toegevoegd, wordt weergegeven als een afzonderlijke laag.

**opties van het Menu op de linkerruit:** Gebruik deze opties voor gemeenschappelijke redacteursacties zoals hieronder vermeld.

* ![](/help/assets/assets/dm-templates/layer-selector.svg): selecteer een laag.
* ![](/help/assets/assets/dm-templates/bring-forward.svg): Klik om een geselecteerde laag vooruit te brengen of **CTRL** + **te drukken]** (Vensters) of **Cmd** + **]** (Mac).
* ![](/help/assets/assets/dm-templates/send-backward.svg): Klik om een geselecteerde laag achteruit te verzenden of **CTRL** + **te drukken (** (Vensters) of **Cmd** + **[** (Mac).
* ![](/help/assets/assets/dm-templates/undo.svg): Klik om de laatste actie ongedaan te maken of **CTRL** te drukken + **Z** (Vensters) of **Cmd** + **Z** (Mac).
* ![](/help/assets/assets/dm-templates/redo.svg): Klik om de laatste actie opnieuw uit te voeren of **CTRL** te drukken + **Y** (Vensters) of **Cmd** + **Y** (Mac).
* ![](/help/assets/assets/dm-templates/zoomin.svg): Klik om in het canvas te zoemen of **CTRL** + **+** (Vensters) of Cmd + **+** (Mac) te drukken.
* ![](/help/assets/assets/dm-templates/zoomout.svg): Klik om uit het canvas te zoemen of **CTRL** te drukken + **-** (Vensters) of **Cmd** + **-** (Mac).
* Pers **Backspace** of **schrapt** om de geselecteerde laag te schrappen als geen tekst of het bezit wordt uitgegeven.

Klik op ![](/help/assets/assets/dm-templates/show-layers-list.svg) en meer opties (![](/help/assets/assets/dm-templates/three-dots.svg) ) op de Canvaslaag om de canvasafmetingen op elk gewenst moment te bewerken tijdens het maken van de sjabloon.
![](/help/assets/assets/dm-templates/edit-canvas1.png)

>[!NOTE]
>
> Sjablonen staan maximaal 20 lagen toe, waaronder het canvas.

### Afbeeldingen toevoegen aan het canvas{#add-images-to-the-canvas}

Voer de volgende stappen uit om afbeeldingen aan het canvas toe te voegen:

1. Klik ![](/help/assets/assets/dm-templates/add-image.svg) om het [ paneel van de Selecteur van Activa ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) te tonen. In het deelvenster worden de afbeeldingen weergegeven die in uw AEM Assets-instantie zijn gesynchroniseerd met Dynamic Media.
1. Blader in het deelvenster of gebruik trefwoorden in de zoekbalk om een specifieke afbeelding te zoeken.
1. Sleep een afbeelding naar het canvas om deze te gebruiken. Zie het [ paneel van Eigenschappen ](#4) voor het resizing of het verplaatsen van een laag op het canvas.
   ![](/help/assets/assets/dm-templates/add-image-to-canvas.png)

### Tekstlagen toevoegen aan het canvas{#add-text-to-the-canvas}

Voer de volgende stappen uit om tekstlagen aan het canvas toe te voegen:

1. Klik op ![](/help/assets/assets/dm-templates/add-text.svg) om een tekstlaag toe te voegen aan het canvas en het deelvenster Eigenschappen te openen.
1. Selecteer de laag en klik op de tekst om deze bij te werken.
1. Laat **Slimme Tekst toe Resize** in het paneel van Eigenschappen om de tekstlengte en de doopvontgrootte automatisch aan te passen om in het aangewezen gebied optimaal te passen.
   ![](/help/assets/assets/dm-templates/add-text-layer.png)

Zie het [ paneel van Eigenschappen ](#4) om de laag te verplaatsen, resize, te roteren of te schrappen. Maak uw tekst aan uw gewenste doopvont, grootte, kleur, stijl, groepering (in de laag) door hun waarden op de respectieve gebieden onder de **sectie van de Tekst** van het paneel te veranderen.

>[!NOTE]
>
> Als u een ander lettertype wilt gebruiken dan de standaardlettertypefamilie Sans F2, moet u het lettertypebestand uploaden en publiceren naar AEM Assets en Dynamic Media. Als u sommige oude doopvonten in uw instantie hebt, verzeker [ opnieuw verwerken ](/help/assets/reprocessing-assets-view.md) om hen in de redacteur van het Malplaatje te bekijken.

### Een laag bewerken of verwijderen {#edit-or-delete-a-layer}

Voer de volgende stappen uit om een canvaslaag te bewerken of te verwijderen:

1. Klik op ![](/help/assets/assets/dm-templates/show-layers-list.svg) en selecteer de laag op het canvas of in de lijst Lagen.
1. Klik **meer opties** (![](/help/assets/assets/dm-templates/three-dots.svg)) om de laag uit te geven of te schrappen.
1. Klik **Schrapping** om de laag te schrappen.
1. Klik **uitgeven** om de laag uit te geven gebruikend het [ paneel van Eigenschappen ](#4).
   ![](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Deelvenster Eigenschappen{#properties-panel}

Navigeren naar het deelvenster met laageigenschappen:

1. Klik op ![](/help/assets/assets/dm-templates/show-layers-list.svg).
1. Selecteer de laag in de lijst.

In dit deelvenster ziet u de positie van het middelpunt van de laag op het canvasvlak (X- en Y-waarden) en de afmetingen van de laag (breedte en hoogte), samen met tekstopmaakopties.

![](/help/assets/assets/dm-templates/properties-panel.png)

Selecteer in het deelvenster Eigenschappen van een laag een andere laag op het canvas om naar het deelvenster met eigenschappen te navigeren.
<a id="4"></a>

#### Een laag verplaatsen, vergroten, verkleinen, roteren of verwijderen{#reposition-resize-delete-a-layer}

Zie de volgende algemene handelingen voor het bewerken van lagen om tekst of een afbeeldingslaag te bewerken:

* **verplaats de laag:** sleep de laag om het overal op het canvas te bewegen. Met deze actie worden de X- en Y-waarden in het deelvenster Eigenschappen bijgewerkt.
* **resize de laag:** selecteer de laag en sleep zijn randhandvatten om het te resize. Met deze handeling worden de waarden voor B (breedte) en H (hoogte) in het deelvenster Eigenschappen bijgewerkt.
* **roteer de laag:** sleep het vierkante handvat dat verticaal boven de laag wordt geplaatst om het rond zijn centrum te roteren. Met deze handeling worden de hoekwaarden in het deelvenster Eigenschappen bijgewerkt.
* **Schrap de laag:** Pers **Backspace** of **schrapt** en klik dan **bevestigen** om een geselecteerde laag te schrappen.

#### Opties voor tekstopmaak{#text-formatting-options-on-properties-panel}

Maak uw tekst aan uw gewenste doopvont, grootte, kleur, stijl, groepering (in de laag) door hun waarden op de respectieve gebieden onder de **sectie van de Tekst** van het paneel te veranderen.

**Slimme Tekst Resize:** verzeker om **Slimme Tekst te omvatten vergroot** ([ het Aanpassen van de Tekst ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting)) om het even welke tekst in het aangewezen gebied optimaal te passen door zijn doopvontgrootte en lengte slim aan te passen. Zo voorkomt u tekstoverloop of minimaliseert u extra spaties onder aan de tekst.
![](/help/assets/assets/dm-templates/smart-text-resize.png)

### Lagen parametereren {#parameterise-a-layer}

Nadat u een sjabloon met meerdere lagen afbeeldingen en tekst hebt gemaakt, kunt u de parameters van de geselecteerde lagen bepalen. Wanneer een laag of zijn bezit wordt bepaald, krijgt het een zeer belangrijk-waardepaar (ook genoemd als parameter). Deze parameter kan in het malplaatje URL worden omvat om de positie, de grootte of de inhoud van de laag in echt bij te werken - tijd resulterend in malplaatjeaanpassing in geen tijd.

Een laag bepalen: <a id="1"></a>

1. Klik ![](/help/assets/assets/dm-templates/show-layers-list.svg), selecteer een laag en klik **Parameters**. De **paneelvertoningen van Parameters**.
1. Wissel **omvatten Parameter** om een bezit te parameters. Zie [ dit ](#parameterisation-options-or-allowed-parameters) om het gedrag van het bezit na parameterization te kennen.
1. **Facultatief:** noem de parameternaam anders. Een parameternaam heeft een laagnaam gevolgd door een achtervoegsel. Voor een geselecteerde laag delen alle eigenschappen met parameters dezelfde laagnaam, gevolgd door een variërend achtervoegsel. Wijzig de naam van de laag door de semantische noemende overeenkomst te volgen zodat wanneer u de parameter in URL omvat, de parameternaam zelf over de inhoud van de laag of zijn doel verklaart.
1. Klik **sparen**.
   ![](/help/assets/assets/dm-templates/parameterise-a-layer.png)
Om tussen het paneel van de Parameter van een beeld en tekstlaag te schakelen, selecteer de laag op het canvas en klik **Parameters**.

#### Opties in het deelvenster Parameters {#parameterisation-options-or-allowed-parameters}

De parameters van eigenschappen kunnen als parameters URL in het malplaatje URL worden omvat om het malplaatje in echt uit te geven - tijd gebruikend URL.

**parameters van het Beeld:**

**X:** omvat om de laag horizontaal langs zijn middellijn, parallel aan de x-as van het malplaatjevlak te bewegen, door de waarde van de parameter in URL te veranderen.
**Y:** omvat om de laag verticaal langs zijn centrumlijn, parallel aan de y-as van het malplaatjevlak te bewegen, door de waarde van de parameter in URL te veranderen.
**Breedte:** omvat om de breedte van de laag aan te passen door de waarde van de parameter in URL te veranderen.
**Hoogte:** omvat om de hoogte van de laag aan te passen door de waarde van de parameter in URL te veranderen.
**Verbergen:** omvatten om de laag in het malplaatje te verbergen of te tonen gebruikend 0 (toon) en 1 (verberg).
**Source:** omvat om het beeld van de laag met nieuw beeld te vervangen door de beeldweg in de waarde van de parameter in URL te veranderen.

**het formatteren van de Tekst parameters:**

Neem de onderstaande parameters op om de tekst, het lettertype, de kleur en de grootte van de tekst vanuit de URL te bewerken door de parameterwaarden in de URL bij te werken.

**Tekst:** omvat om tekst van URL bij te werken.
**Familie van de Doopvont:** omvat om de doopvont van de tekst van URL bij te werken.
**Grootte van de Doopvont:** omvat om de de doopvontgrootte van de tekst van URL bij te werken.
**kleur van de Tekst:** omvat om de de doopvontkleur van de tekst van URL bij te werken.

### Lagen groeperen om de zichtbaarheid ervan tegelijk te regelen{#group-layers}

Een andere manier om uw malplaatjes flexibel te houden, is door één enkele parameternaam te gebruiken om veelvoudige lagen te controleren. Deze strategie is handig voor de zichtbaarheidsparameter (lagen verbergen of weergeven) om het ontwerp of de afbeeldingen van één sjabloon bij te werken.

Voer de volgende stappen uit om dezelfde naam toe te wijzen aan de verborgen parameters (![](/help/assets/assets/dm-templates/Visibility-icon.svg)) van meerdere lagen, zodat u deze tegelijk kunt verbergen of weergeven.

1. Navigeer aan het [ paneel van Parameters ](#1) van een laag.
1. Wissel de **Parameter van de Verbergen** als niet vroeger parameters bepaald.
1. **Facultatief:** noem de Parameter van de Verbergen anders.
1. Kopieer de naam Parameter verbergen.
1. Ga naar het paneel van de Parameter van andere lagen door hen van het canvas te selecteren en van een knevel te voorzien hun **** Parameter van de Verbergen als niet parameters bepaald.
1. Vervang hun **naam van de Parameter van de Verbergen** met de gekopieerde naam.
1. Klik **sparen** om de lagen te groeperen.
1. Voer stap 3 en dan 4 in [ Voorproef en Publish ](#2) sectie uit om uw veranderingen te zien.

## De sjabloon voorvertonen en publiceren om de leverings-URL te kopiëren{#preview-and-publish-template-and-copy-template-deliver-url}

Voer de volgende stappen uit om de sjabloon voor te vertonen en te publiceren en de URL van de levering te kopiëren:

1. Voor de pagina van het canvas, klik **Voorproef**. U kunt ook aan **Mening van Assets > Assets van Dynamic Media navigeren >** vinden en uw malplaatje selecteren **>** klik **uitgeven Malplaatje >** klikken **Voorproef**. De voorproefpagina toont het malplaatje, zijn parameters (parameters bepaalde lagen en eigenschappen), publiceert status, en de **Publish** optie. <a id="3"></a>
1. Selecteer parameters van **het paneel van de Parameters van het Malplaatje** om hun waarden uit te geven en onmiddellijk de inhoud, de grootte, de positie, of tekst het formatteren van de overeenkomstige malplaatjelaag in de voorproef bij te werken. Bijvoorbeeld:
   1. Selecteer een tekstlaag en bewerk de tekst of
   1. Selecteer een beeldlaag, klik ![](/help/assets/assets/dm-templates/add-image.svg), selecteer een beeld van de activaselecteur, en klik **verfrissen zich**.

   De sjabloon wordt onmiddellijk bijgewerkt, waarbij de bewerkte tekst wordt weergegeven en de vorige afbeelding wordt vervangen door de nieuwe. Bovendien weerspiegelt de waarde van de afbeeldingsparameter het nieuwe afbeeldingspad. Op dezelfde manier kunt u het formaat van een laag aanpassen door zijn waarden aan te passen, en de veranderingen worden toegepast op het malplaatje in echt - tijd. <a id="2"></a>
1. Selecteer de huidenparameter voor [ gegroepeerde lagen ](#group-layers) van de lijst om hen samen in het malplaatje te tonen of te verbergen.
1. **Facultatief:** verander de **waarde van de Parameter van de Verbergen** tussen 0 en 1 en klik **verfrissen zich** om de veranderingen te zien. Lagen met dezelfde parameter hide worden samen verborgen of weergegeven. Op dezelfde manier kunt u de zichtbaarheid van lagen bepalen via de URL.

   ![](/help/assets/assets/dm-templates-publish-status.png)
U kunt **ook van een knevel voorzien omvat alle parameters** om alle getoonde parameterwaarden uit te geven en de updates in de malplaatjevoorproef te zien.
   <br>
1. Om het malplaatje op de voorproefpagina te publiceren, klik **Publish** en bevestig om te publiceren. Publish Complete-berichten worden weergegeven en de publicatiestatus wordt bijgewerkt naar Published.

>[!NOTE]
>
>Als u de sjabloon publiceert, moeten de sjabloonafbeeldingen eerst worden gepubliceerd.

### De leverings-URL kopiëren

De geselecteerde parameters op de **pagina van de Voorproef** worden de parameters URL in het malplaatje URL.

U kunt als volgt de URL van de gepubliceerde sjabloon kopiëren die in de voorvertoning wordt weergegeven:

1. Klik **Exemplaar URL**. De **vertoningen van de de dialoogdoos van het Exemplaar URL**. Selecteer en kopieer de weergegeven URL. Merk op dat de eerste parameter in de URL begint na een vraagteken **(?)** en een zeer belangrijk-waardepaar beginnen met **$** en eindigen met **&amp;**. De sleutel en de waarde worden gescheiden door een gelijkteken **(=)**, met de sleutel op de linkerzijde en de waarde op het recht.
1. Plak deze URL in het browsertabblad en bekijk de live sjabloon. Pas het malplaatje in real time aan door de vereiste waarde van de parameter (de waarde van Sleutel) in URL direct bij te werken zoals aangetoond in [ stap 2 ](#3) van **Voorproef en van Publish** sectie.
1. Gebruik deze URL voor snelle verkoop van uw producten of services. U kunt deze URL delen met uw klanten of deze integreren in uw website of een andere downstreamtoepassing van derden om de banner weer te geven en er realtime updates voor uit te voeren die de lopende aanbiedingen weerspiegelen.

Leer hoe u stap voor stap een Dynamic Media-sjabloon maakt in deze video.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Updates in real time van de sjabloon maken via de URL{#update-the-template-from-the-url}

Het rechtstreeks bewerken van parameters in de URL kan vervelend zijn. Ter vereenvoudiging:

1. Kopieer de URL en plak deze in een blok.
1. Gebruik Cmd+F (Mac) of Ctrl+F (Windows) om de parameterwaarden te zoeken en te bewerken. Bijvoorbeeld:
   * Vervang afbeeldingspaden voor afbeeldingslagen.
   * Pas laagdimensies en posities (als [ geparameterized ](#parameterise-a-layer)) aan.
   * Bewerk tekst, lettertype, kleur, grootte of uitlijning voor tekstlagen.
   * Wijzig de zichtbaarheidswaarden tussen 0 en 1.

Plak deze bijgewerkte URL in uw browser om de wijzigingen weer te geven.

## De sjabloon bewerken{#edit-the-template}

Voer de volgende stappen uit om de sjabloon te bewerken:

1. Voor de mening van Assets, klik **Assets van Dynamic Media**.
2. Navigeer naar de sjabloonlocatie.
3. Selecteer de sjabloon.
4. Klik **uitgeven Malplaatje**. Op het sjablooncanvas worden de sjabloon en de lijst met alle lagen in het deelvenster Lagen weergegeven. Begin de sjabloon naar wens te bewerken.

## Belangrijke opmerkingen {#important-points-to-note}

* Nadat u een sjabloon hebt gemaakt met geparametriseerde afbeeldingslagen voor dynamische updates, zorgt u ervoor dat de afbeeldingen die u wilt bijwerken in de toekomst dezelfde afmetingen hebben als de geparametriseerde afbeeldingen. Zo kunt u ervoor zorgen dat de afbeeldingen perfect in de lagen passen zonder dat ze te veel stromen of lege ruimten overblijven. De sjabloon ondersteunt momenteel geen automatische dimensionering om afbeeldingen in de lagen te passen.
* Een tekstlaag biedt geen ondersteuning voor subtekenreeksen. De gebruiker kan geen verschillende doopvonteigenschappen op substring van een tekstlaag toepassen.
* Er is momenteel geen ondersteuning voor meerdere Dynamic Media-bedrijven beschikbaar met Dynamic Media Templates.
* In het geval van kopiëren of verplaatsen worden in de doelkiezer alle mappen weergegeven (inclusief mappen die niet door Dynamic Media zijn gesynchroniseerd). Momenteel worden de Dynamic Media-sjabloonelementen niet weergegeven (beide zijn beperkingen van de doelkiezer).
* Elke updatebewerking op een map (bijvoorbeeld Publish of Delete) uit de Assets-sectie heeft invloed op de Dynamic Media-sjablonen die beschikbaar zijn in die map.
* Prullenbak werkt niet voor Dynamic Media-sjablonen. Als een element naar de prullenbak wordt verplaatst en vervolgens wordt teruggezet, wordt het middel in AEM teruggezet, maar niet in Dynamic Media. Hetzelfde geldt voor Dynamic Media-sjablonen.

## Zie ook

1. Onderzoek [ Dynamic Media en zijn mogelijkheden ](/help/assets/dynamic-media/dynamic-media.md)
1. Onderzoek [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md)