---
title: Toegang tot en navigatie in de Universal Editor
description: Leer de basisbeginselen van toegang tot en navigatie in de Universal Editor.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 213ef604-1a09-41f1-b051-3d8254b8164f
source-git-commit: eddccf5a9d5c6be8d07120ea2f9e36007f7f909f
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 0%

---

# Toegang tot en navigatie in de Universal Editor {#navigating}

Leer de basisbeginselen van toegang tot en navigatie in de Universal Editor.

## Inleiding {#introduction}

Met de Universal Editor kunt u elk aspect van elke inhoud in een implementatie bewerken, zodat u uitzonderlijke ervaringen kunt bieden, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.

Hiervoor verschaft de Universal Editor de auteur van inhoud een intuïtieve gebruikersinterface die minimale training vereist om eenvoudig in de inhoud te kunnen springen en beginnen met het bewerken ervan. In dit document wordt beschreven hoe u door de Universal Editor kunt navigeren.

>[!TIP]
>
>* Voor details bij het ontwerpen die de Universele Redacteur gebruiken, zie het document [ Authoring Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md).
>* Voor een meer gedetailleerde inleiding aan de Universele Redacteur, zie [ Universele Inleiding van de Redacteur ](/help/implementing/universal-editor/introduction.md).

## De app voorbereiden {#prepare-app}

Als u inhoud voor een app wilt ontwerpen met de Universal Editor, moet de app van instrumenten zijn voorzien door een ontwikkelaar om de editor te ondersteunen.

>[!TIP]
>
>Zie [ Begonnen het Worden met de Universele Redacteur in AEM ](/help/implementing/universal-editor/getting-started.md) voor een voorbeeld van hoe te om een toepassing van AEM te vormen om met de Universele Redacteur te werken.

## De universele editor openen {#accessing}

Zodra de app van instrumenten is voorzien om met de Universal Editor te werken, kan de Universal Editor zowel in AEM as a Cloud Service als rechtstreeks toegang krijgen tot de toepassing zonder AEM te openen.

### Toegang tot AEM as a Cloud Service {#accessing-aem}

1. Meld u aan bij uw AEM as a Cloud Service-ontwerpinstantie.
1. Gebruik de **console van 1&rbrace; Plaatsen [&#128279;](/help/sites-cloud/authoring/sites-console/introduction.md) om aan de pagina te navigeren die voor gebruik met de Universele Redacteur wordt gecreeerd die u wenst uit te geven.**
1. Bewerk de pagina.
1. De Universal Editor wordt geopend om de geselecteerde pagina te bewerken.

>[!NOTE]
>
>Wanneer het uitgeven van een pagina in de **console van Plaatsen [&#128279;](/help/sites-cloud/authoring/sites-console/introduction.md), zal de console de redacteur aangewezen aan het 3&rbrace; malplaatje van de pagina [&#128279;](/help/sites-cloud/authoring/page-editor/templates.md) of de Universele Redacteur openen die in dit document wordt beschreven, of de [ paginaredacteur ](/help/sites-cloud/authoring/page-editor/introduction.md).**

### Direct toegang {#accessing-directly}

1. Meld u aan bij de Universal Editor. U hebt een Adobe ID nodig om binnen te ondertekenen en [ heeft toegang tot de Universele Redacteur ](/help/implementing/universal-editor/getting-started.md#request-access).

1. Nadat u binnen wordt ondertekend, ga URL van de pagina in u in de [ plaats bar ](#location-bar) wilt uitgeven, zodat kunt u beginnen inhoud zoals tekstinhoud of media inhoud uit te geven.

## De gebruikersinterface begrijpen {#ui}

De interface is verdeeld in deze hoofdgebieden.

* [De Experience Cloud-header](#experience-cloud-header)
* [De werkbalk van de Universal Editor](#universal-editor-toolbar)
* [De editor](#editor)
* [Het deelvenster Eigenschappen](#properties-rail)

![ Universele Redacteur UI ](assets/ui.png)

>[!TIP]
>
>De Universele Redacteur biedt een aantal [ aanpassingsopties ](/help/implementing/universal-editor/customizing.md) en [ uitbreidingspunten ](/help/implementing/universal-editor/extending.md) aan die kunnen wijzigen en aan de functionaliteit van de redacteur toevoegen. Daarom ziet u mogelijk andere opties dan de hier beschreven standaardopties.

### De Experience Cloud-header {#experience-cloud-header}

De Experience Cloud-header staat altijd boven aan het scherm. Het is een anker dat u vertelt waar u zich in Experience Cloud bevindt en dat u helpt naar andere Experience Cloud-toepassingen te navigeren.

![ de kopbal van Experience Cloud ](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Selecteer de verbinding van Adobe Experience Cloud links van de kopbal om aan de wortel van uw oplossing van Experience Manager te navigeren om tot hulpmiddelen zoals [ Cloud Manager ](/help/onboarding/cloud-manager-introduction.md), [ Cloud Acceleration Manager ](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md), en [ de Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=nl-NL) toegang te hebben.

![ Globale knoop van de Navigatie ](assets/global-navigation.png)

#### Organisatie {#organization}

Hier wordt de organisatie weergegeven waarmee u momenteel bent aangemeld. Schakel deze optie in om over te schakelen naar een andere organisatie als uw Adobe ID aan meerdere organisaties is gekoppeld.

![ de indicator van de Organisatie ](assets/organization.png)

#### Oplossingen {#solutions}

Als u op de schakeloptie voor oplossingen tikt of erop klikt, kunt u snel naar andere Experience Cloud-oplossingen gaan.

![ de schakelaar van Oplossingen ](assets/solutions.png)

#### Help {#help}

Met het Help-pictogram hebt u snel toegang tot leermiddelen en ondersteuningsbronnen.

![ Hulp ](assets/help.png)

#### Meldingen {#notifications}

Dit pictogram wordt getekend met het aantal momenteel toegewezen onvolledige [ berichten ](/help/implementing/cloud-manager/notifications.md).

![ Meldingen ](assets/notifications.png)

#### Gebruikerseigenschappen {#user-properties}

Selecteer het pictogram dat uw gebruiker vertegenwoordigt om tot uw gebruikersmontages toegang te hebben. Als u geen gebruikersbeeld hebt gevormd, wordt een pictogram willekeurig toegewezen.

![ Eigenschappen van de Gebruiker ](assets/user-properties.png)

### De werkbalk Universele editor {#universal-editor-toolbar}

De Universele toolbar van de Redacteur is altijd aanwezig bij de bovenkant van het scherm enkel onder [ de kopbal van Experience Cloud ](#experience-cloud-header). Hiermee kunt u snel naar een andere pagina navigeren om deze te bewerken en te publiceren.

Afhankelijk van de configuratie van uw programma, kan het [ extra eigenschappen ook voorstellen die als uitbreidingen door uw beheerder zijn toegelaten.](#additional-toolbar-buttons)

![ de Universele toolbar van de Redacteur ](assets/universal-editor-toolbar.png)

#### De knop Home {#home-button}

Met de knop Home keert u terug naar de startpagina van de Universal Editor

![ het menu van de Hamburger ](assets/home-button.png)

Op de startpagina kunt u de URL invoeren van de site die u wilt bewerken met de Universal Editor.

![ pagina van het Begin ](assets/start-page.png)

>[!NOTE]
>
>Om het even welke pagina die u met de Universele Redacteur wilt uitgeven moet [ van instrumenten worden voorzien om de Universele Redacteur ](/help/implementing/universal-editor/getting-started.md) te steunen.

#### Locatiebalk {#location-bar}

Op de locatiebalk ziet u het adres van de pagina die u bewerkt. Selecteer deze optie om het adres in te voeren van een andere pagina die u wilt bewerken.

![ bar van de Plaats ](assets/location-bar.png)

>[!TIP]
>
>Open de adresbalk met de sneltoets `l` (de letter l).

>[!NOTE]
>
>Om het even welke pagina die u met de Universele Redacteur wilt uitgeven moet [ van instrumenten worden voorzien om de Universele Redacteur ](/help/implementing/universal-editor/getting-started.md) te steunen.

#### Instellingen voor verificatiekoptekst {#authentication-settings}

Selecteer het de montagespictogram van de authentificatiekopbal als u een kopbal van de douaneauthentificatie voor lokale ontwikkelingsdoeleinden [&#128279;](/help/implementing/universal-editor/developer-overview.md#auth-header) moet plaatsen.

![ de knoop van de het hedentemenu van de Authentificatie ](assets/authentication-header-settings.png)

#### Emulatorinstellingen {#emulator}

Selecteer het emulatiepictogram om te bepalen hoe de Universal Editor de pagina weergeeft.

![ Emulatorpictogram ](assets/emulator.png)

Als u op het emulatiepictogram tikt of erop klikt, worden de opties weergegeven.

![ de opties van de Emulatie ](assets/emulation-options.png)

Standaard wordt de editor geopend in de computerlay-out, waarbij de hoogte en breedte automatisch door de browser worden gedefinieerd.

U kunt er ook voor kiezen om een mobiel apparaat te emuleren en in de Universele Editor:

* De oriëntatie definiëren
* Breedte en hoogte definiëren
* De richting wijzigen

#### Voorvertoningsmodus {#preview-mode}

In voorproefwijze, de pagina die in de redacteur wordt teruggegeven zoals het op uw gepubliceerde dienst zou worden gezien. Hierdoor kan de auteur van de inhoud door de inhoud navigeren door op koppelingen te klikken, enzovoort.

![ wijze van de Voorproef ](assets/preview-mode.png)

>[!TIP]
>
>Met de sneltoets `p` kunt u schakelen van en naar de voorvertoningsmodus.

#### App-voorvertoning openen {#open-app-preview}

Selecteer het pictogram voor de voorvertoning van de geopende app om de pagina die u momenteel bewerkt te openen op een eigen browsertabblad, zodat de editor geen voorvertoning van uw inhoud kan weergeven.

![ Open app voorproef ](assets/open-app-preview.png)

>[!TIP]
>
>Gebruik de sneltoets `o` (de letter o) om de voorvertoning van de app te openen.

>[!TIP]
>
>De voorproef URL voor uw app [ kan worden aangepast ](/help/implementing/universal-editor/customizing.md#custom-preview-urls).

#### Publiceren {#publish}

Selecteer de knop Publiceren, zodat u de wijzigingen in de live inhoud kunt publiceren voor gebruik door uw lezers of voor een voorbeeldomgeving ter controle.

![ publiceer knoop ](assets/publish.png)

>[!TIP]
>
>Zie het document [ het Publiceren Inhoud met de Universele Redacteur ](publishing.md) voor meer informatie bij het publiceren met de Universele Redacteur.

#### Weglatingsteken {#ellipsis}

Aanvullende standaardopties zijn toegankelijk met de knop Ovaal.

![ knoop van de Ellipsis ](assets/ellipsis.png)

Bijvoorbeeld, is de capaciteit om een pagina (d.w.z. omgekeerd de actie van [**publiceren** knoop ](#publish)) toegankelijk via de ellipsieknoop.

#### Aanvullende knoppen {#additional-toolbar-buttons}

De Universal Editor biedt een aanpasbare en uitbreidbare ontwerpervaring. Als er extra knoppen op de werkbalk staan, is de Universal Editor uitgebreid.

* Voor details op hoe een individuele uitbreiding werkt, [ gelieve te zien de Universele het auteursdocumentatie van de Redacteur.](/help/sites-cloud/authoring/universal-editor/authoring.md#managing-page-content)
* Voor details op uitbreidingsmogelijkheden, te zien gelieve [ Uitbreidend de Universele Redacteur ](/help/implementing/universal-editor/extending.md).
* Voor details op hoe te om een individuele uitbreiding te installeren, te zien gelieve de [ documentatie van Extension Manager ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/).

### De Editor {#editor}

De redacteur bezet het grootste deel van het venster en is waar de pagina die in [ wordt gespecificeerd de plaatsbar ](#location-bar) wordt teruggegeven.

![ Redacteur ](assets/editor.png)

Als de redacteur op [ voorproefwijze ](#preview-mode) is, zal de inhoud navigeerbaar zijn en u kunt verbindingen volgen, maar u kunt niet de inhoud uitgeven.

### Deelvenster Eigenschappen {#properties-rail}

Het deelvenster Eigenschappen is altijd aanwezig aan de rechterkant van de editor. Afhankelijk van de modus, kunnen er details worden weergegeven voor een component die is geselecteerd in de inhoud of de hiërarchie van de pagina-inhoud.

![ het eigenschappen paneel ](assets/properties-rail.png)

#### Eigenschappenmodus {#properties-mode}

In de modus Eigenschappen toont het deelvenster de eigenschappen van de component die momenteel in de editor is geselecteerd. Dit is de standaardmodus van het deelvenster Eigenschappen wanneer een pagina wordt geladen.

![ wijze van Eigenschappen ](assets/properties-mode.png)

Afhankelijk van het type component dat u selecteert, kunnen details worden weergegeven en gewijzigd in het deelvenster Eigenschappen.

![ de details van de Component ](assets/component-details.png)

Niet alle componenten hebben details die kunnen worden getoond en/of worden uitgegeven.

>[!TIP]
>
>Gebruik de sneltoets `d` om over te schakelen naar de modus Eigenschappen.

#### Modus Inhoudsstructuur {#content-tree-mode}

In de modus Inhoudsboomstructuur wordt in het deelvenster de hiërarchie van de pagina-inhoud weergegeven.

![ de boomwijze van de Inhoudsboom ](assets/content-tree-mode.png)

Wanneer het selecteren van een punt in de inhoudsboom, scrolt de redacteur aan die inhoud en selecteert het.

![ de boom van de Inhoud ](assets/content-tree.png)

>[!TIP]
>
>Gebruik de hete sleutel `f` om over te schakelen op de modus van de inhoudstructuur.

##### Openen in CF-editor {#edit}

Tijdens het bewerken worden de opties voor de geselecteerde component weergegeven in het deelvenster Eigenschappen, waar u de geselecteerde component kunt bewerken. Als de geselecteerde component een Fragment van de Inhoud is, kunt u **Open in de redacteur van het CF** knoop ook selecteren.

![ Open in het pictogram van de Redacteur van CF ](assets/open-in-cf-editor.png)

Tapping of het klikken van **Open in de redacteur van het CF** knoop opent de [ redacteur van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor) in een nieuw lusje. Op deze manier hebt u toegang tot alle mogelijkheden van de editor voor inhoudsfragmenten om het bijbehorende inhoudsfragment te bewerken.

Afhankelijk van de behoeften van uw workflow wilt u het inhoudsfragment wellicht bewerken in de universele editor of rechtstreeks in de editor voor inhoudsfragmenten.

>[!TIP]
>
>Gebruik de sneltoets `e` om een geselecteerd inhoudsfragment te openen in de inhoudsfragmenteditor.

##### Toevoegen {#add}

Als u een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de optie Toevoegen weergegeven in het deelvenster Eigenschappen.

![ voeg pictogram ](assets/ue-add-component-icon.png) toe

Tapping of het klikken van toevoegt knoop opent een drop-down menu van componenten die beschikbaar zijn aan [ toevoegen aan de geselecteerde container ](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components).

![ voeg contextmenu ](assets/add-context-menu.png) toe

>[!TIP]
>
>Gebruik de sneltoets `a` om een component aan een geselecteerde containercomponent toe te voegen.

##### Dupliceren {#duplicate}

Als u een component binnen een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de optie Dupliceren weergegeven in het deelvenster Eigenschappen.

![ Dupliceer pictogram ](assets/duplicate.png)

Tapping of het klikken van de dubbele knoop [ dupliceert de geselecteerde component ](/help/sites-cloud/authoring/universal-editor/authoring.md#duplicating-components).

##### Verwijderen {#delete}

Als u een component binnen een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de verwijderingsoptie weergegeven in het deelvenster Eigenschappen.

![ pictogram van de Schrapping ](assets/ue-delete-component-icon.png)

Tapping of het klikken van de schrappingsknoop [ schrapt de component ](/help/sites-cloud/authoring/universal-editor/authoring.md#deleting-components).

>[!TIP]
>
>Gebruik de sneltoets `Shift+Backspace` om een geselecteerde component uit een container te verwijderen.

## Extra functies {#additional-features}

De Universal Editor biedt een aanpasbare en uitbreidbare ontwerpervaring. Als u extra knoppen of opties ziet in het deelvenster Eigenschappen of op de werkbalk, is de Universal Editor uitgebreid.

* Voor details op uitbreidingsmogelijkheden, gelieve te zien [ Aanpassen en de Universele Redacteur ](/help/implementing/universal-editor/customizing.md) uitbreiden.
* Voor details op hoe een individuele uitbreiding werkt, te zien gelieve de [ documentatie van Extension Manager ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/).

## Volgende stappen {#next-steps}

Nu u weet om tot de Universele Redacteur toegang te hebben en te navigeren, bent u klaar aan [ auteursinhoud gebruikend het ](/help/sites-cloud/authoring/universal-editor/authoring.md).
