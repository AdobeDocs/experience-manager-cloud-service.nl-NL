---
title: Inhoud ontwerpen met de Universal Editor
description: Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '2189'
ht-degree: 0%

---


# Inhoud ontwerpen met de Universal Editor {#authoring}

Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.

{{universal-editor-status}}

## Inleiding {#introduction}

Met de Universal Editor kunt u elk aspect van elke inhoud in een implementatie bewerken, zodat u uitzonderlijke ervaringen kunt bieden, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.

Hiervoor verschaft de Universal Editor de auteur van inhoud een intuïtieve gebruikersinterface die minimale training vereist om eenvoudig in de inhoud te kunnen springen en beginnen met het bewerken ervan. In dit document wordt de auteurservaring van de Universal Editor beschreven.

>[!TIP]
>
>Zie het document voor een meer gedetailleerde inleiding tot de Universal Editor [Introductie van de Universal Editor.](introduction.md)

## De app voorbereiden {#prepare-app}

Als u inhoud voor een app wilt ontwerpen met de Universal Editor, moet de app van instrumenten zijn voorzien door een ontwikkelaar om de editor te ondersteunen.

>[!TIP]
>
>Zie [Aan de slag met de Universal Editor in AEM](getting-started.md) voor een voorbeeld van hoe u een AEM toepassing configureert voor gebruik met de Universal Editor.

## Aanmelden {#sign-in}

Meld u aan bij de Universal Editor nadat de app van instrumenten is voorzien om te werken met de Universal Editor. U hebt een Adobe ID nodig om u aan te melden en [toegang hebben tot de Universal Editor.](getting-started.md#request-access)

Nadat u bent aangemeld, voert u de URL van de pagina die u wilt bewerken in het dialoogvenster [locatiebalk.](#location-bar) zodat u inhoud zoals [tekstinhoud](#text-mode) of [media-inhoud.](#media-mode)

## De gebruikersinterface begrijpen {#ui}

De interface is verdeeld in deze hoofdgebieden.

* [De koptekst van het Experience Cloud](#experience-cloud-header)
* [De werkbalk van de Universal Editor](#universal-editor-toolbar)
* [De editor](#editor)
* [De eigenschappen per spoor](#properties-rail)

![De gebruikersinterface van de Universal Editor](assets/ui.png)

### De koptekst van het Experience Cloud {#experience-cloud-header}

De koptekst van het Experience Cloud bevindt zich altijd boven aan het scherm. Het is een anker dat u vertelt waar u binnen Experience Cloud bent en u helpt aan andere Experience Cloud apps navigeren.

![De koptekst van het Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Selecteer de verbinding van Adobe Experience Cloud bij de linkerzijde van de kopbal om aan de wortel van uw oplossing van de Experience Manager te navigeren om tot hulpmiddelen zoals [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) en [Softwaredistributie.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

![De knop Algemene navigatie](assets/global-navigation.png)

#### Organisatie {#organization}

Hier wordt de organisatie weergegeven waarmee u momenteel bent aangemeld. Schakel deze optie in om over te schakelen naar een andere organisatie als uw Adobe ID aan meerdere organisaties is gekoppeld.

![Organisatie-indicator](assets/organization.png)

#### Oplossingen {#solutions}

Als u op de schakeloptie voor oplossingen tikt of erop klikt, kunt u snel naar andere oplossingen voor Experiencen Cloud gaan.

![Oplossingsschakelaar](assets/solutions.png)

#### Help {#help}

Met het Help-pictogram hebt u snel toegang tot leermiddelen en ondersteuningsbronnen.

![Help](assets/help.png)

#### Meldingen {#notifications}

Dit pictogram is gemarkeerd met het aantal momenteel toegewezen onvolledige [meldingen.](/help/implementing/cloud-manager/notifications.md)

![Meldingen](assets/notifications.png)

#### Gebruikerseigenschappen {#user-properties}

Selecteer het pictogram dat uw gebruiker vertegenwoordigt om tot uw gebruikersmontages toegang te hebben. Als u geen gebruikersbeeld hebt gevormd, wordt een pictogram willekeurig toegewezen.

![Gebruikerseigenschappen](assets/user-properties.png)

### De werkbalk Universele editor {#universal-editor-toolbar}

De werkbalk Universele editor bevindt zich altijd boven in het scherm net onder [de koptekst van het Experience Cloud.](#experience-cloud-header) Hiermee kunt u snel naar een andere pagina navigeren om deze te bewerken en te publiceren.

![De werkbalk van de Universal Editor](assets/universal-editor-toolbar.png)

#### De knop Home {#home-button}

Met de knop Home keert u terug naar de startpagina van de Universal Editor

![Hamburger-menu](assets/home-button.png)

Op de startpagina kunt u de URL invoeren van de site die u wilt bewerken met de Universal Editor.

![Startpagina](assets/start-page.png)

>[!NOTE]
>
>Elke pagina die u wilt bewerken met de universele editor moet [van instrumenten voorzien om de Universele Redacteur te steunen.](getting-started.md)

#### Locatiebalk {#location-bar}

Op de locatiebalk ziet u het adres van de pagina die u bewerkt. Selecteer deze optie om het adres in te voeren van een andere pagina die u wilt bewerken.

![Locatiebalk](assets/location-bar.png)

>[!TIP]
>
>De sneltoets gebruiken `L` de adresbalk openen.

>[!NOTE]
>
>Elke pagina die u wilt bewerken met de universele editor moet [van instrumenten voorzien om de Universele Redacteur te steunen.](getting-started.md)

#### Instellingen voor verificatiekoptekst {#authentication-settings}

Selecteer het pictogram voor de instellingen van de verificatiekoptekst als u [Stel een aangepaste verificatieheader in voor lokale ontwikkelingsdoeleinden.](/help/implementing/universal-editor/developer-overview.md#auth-header)

![Knop Instellingen van verificatieheader](assets/authentication-header-settings.png)

#### Emulatorinstellingen {#emulator}

Selecteer het emulatiepictogram om te bepalen hoe de Universal Editor de pagina weergeeft.

![Emulatorpictogram](assets/emulator.png)

Als u op het emulatiepictogram tikt of erop klikt, worden de opties weergegeven.

![Opties voor emulatie](assets/emulation-options.png)

Standaard wordt de editor geopend in de computerlay-out, waarbij de hoogte en breedte automatisch door de browser worden gedefinieerd.

U kunt er ook voor kiezen om een mobiel apparaat te emuleren en in de Universele Editor:

* De oriëntatie definiëren
* Breedte en hoogte definiëren
* De richting wijzigen

#### Voorvertoningsmodus {#preview-mode}

In voorproefwijze, de pagina die in de redacteur wordt teruggegeven zoals het op uw gepubliceerde dienst zou worden gezien. Hierdoor kan de auteur van de inhoud door de inhoud navigeren door op koppelingen te klikken, enzovoort.

![Voorvertoningsmodus](assets/preview-mode.png)

>[!TIP]
>
>De sneltoets gebruiken `P` om van en naar voorvertoningsmodus te schakelen.

#### App-voorvertoning openen {#open-app-preview}

Selecteer het pictogram voor de voorvertoning van de geopende app om de pagina die u momenteel bewerkt te openen op een eigen browsertabblad, zodat de editor geen voorvertoning van uw inhoud kan weergeven.

![App-voorvertoning openen](assets/open-app-preview.png)

>[!TIP]
>
>De sneltoets gebruiken `O` (de letter O) om de voorvertoning van de app te openen.

#### Publiceren {#publish}

Selecteer de knop Publiceren zodat u de wijzigingen in de inhoud live kunt publiceren voor gebruik door de lezers.

![Knop Publiceren](assets/publish.png)

>[!TIP]
>
>Zie het document [Inhoud publiceren met de Universal Editor](publishing.md) voor meer informatie over publiceren met de Universele Redacteur.

### De Editor {#editor}

De editor neemt het grootste deel van het venster in beslag en is de locatie van de pagina die is opgegeven in [de locatiebalk](#location-bar) wordt weergegeven.

![Editor](assets/editor.png)

Als de editor zich bevindt in [voorvertoningsmodus,](#preview-mode) U kunt wel navigeren naar de inhoud en koppelingen volgen, maar u kunt de inhoud niet bewerken.

### Eigenschappenspoorlijn {#properties-rail}

De eigenschap rail is altijd aanwezig langs de rechterkant van de redacteur. Afhankelijk van de modus, kunnen er details worden weergegeven voor een component die is geselecteerd in de inhoud of de hiërarchie van de pagina-inhoud.

![De eigenschappen per spoor](assets/component-rail.png)

#### Eigenschappenmodus {#properties-mode}

In de modus Eigenschappen toont de rail de eigenschappen van de component die momenteel in de editor is geselecteerd. Dit is de standaardmodus van de eigenschap rail wanneer een pagina wordt geladen.

![Eigenschappenmodus](assets/properties-mode.png)

Afhankelijk van het type component dat u selecteert, kunnen details worden weergegeven en gewijzigd in de eigenschappenrails.

![Componentdetails](assets/component-details.png)

Niet alle componenten hebben details die kunnen worden getoond en/of worden uitgegeven.

>[!TIP]
>
>De sneltoets gebruiken `D` om over te schakelen naar de modus Eigenschappen.

#### Modus Inhoudsstructuur {#content-tree-mode}

In de modus Inhoudsboomstructuur wordt in de rails de hiërarchie van de pagina-inhoud weergegeven.

![Modus Inhoudsboomstructuur](assets/content-tree-mode.png)

Wanneer het selecteren van een punt in de inhoudsboom, scrolt de redacteur aan die inhoud en selecteert het.

![Inhoudsstructuur](assets/content-tree.png)

>[!TIP]
>
>De sneltoets gebruiken `F` om over te schakelen naar de modus voor de inhoudstructuur.

##### Bewerken {#edit}

Tijdens het bewerken worden de opties voor de geselecteerde component weergegeven in de eigenschappenbalk, waar u de geselecteerde component kunt bewerken. Als de geselecteerde component een inhoudsfragment is, kunt u ook de knop Bewerken selecteren.

![Pictogram Bewerken](assets/edit.png)

Als u op de knop Bewerken tikt of erop klikt, wordt het dialoogvenster [Inhoudsfragmenteditor](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor) op een nieuw tabblad. Hierdoor hebt u toegang tot alle mogelijkheden van de Content Fragment Editor om het bijbehorende Content Fragment te bewerken.

Afhankelijk van de behoeften van uw workflow wilt u het inhoudsfragment wellicht bewerken in de universele editor of rechtstreeks in de editor voor inhoudsfragmenten.

>[!TIP]
>
>De sneltoets gebruiken `E` om een geselecteerde component te bewerken.

##### Toevoegen {#add}

Als u een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de optie Toevoegen weergegeven op de eigenschappenrails.

![Pictogram toevoegen](assets/ue-add-component-icon.png)

Als u op de knop Toevoegen tikt of erop klikt, wordt een vervolgkeuzelijst geopend met componenten die beschikbaar zijn voor [toevoegen aan de geselecteerde container.](#adding-components)

![Contextmenu toevoegen](assets/add-context-menu.png)

>[!TIP]
>
>De sneltoets gebruiken `A` om een component aan een geselecteerde containercomponent toe te voegen.

##### Verwijderen {#delete}

Als u een component binnen een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de verwijderingsoptie weergegeven op de eigenschappenrails.

![Pictogram Verwijderen](assets/ue-delete-component-icon.png)

Tikken of klikken op de knop Verwijderen [verwijdert de component.](#deleting-components)

>[!TIP]
>
>De sneltoets gebruiken `Shift+Backspace` om een geselecteerde component uit een container te verwijderen.

## Inhoud bewerken {#editing-content}

Inhoud bewerken is eenvoudig en intuïtief. Terwijl u de muis over de inhoud in de editor beweegt, wordt bewerkbare inhoud gemarkeerd met een blauw vak.

![Bewerkbare inhoud wordt gemarkeerd door een blauw vak](assets/editable-content.png)

>[!TIP]
>
>Door gebrek, selecteert het tikken of het klikken op inhoud het voor het uitgeven. Als u door de inhoud wilt navigeren door de koppelingen te volgen, schakelt u over naar [voorvertoningsmodus.](#preview-mode)

Afhankelijk van de inhoud die u selecteert, zijn er mogelijk verschillende opties voor lokale bewerking en kunt u aanvullende informatie en opties voor de inhoud in het dialoogvenster [eigenschappen rail.](#properties-rail)

### Onbewerkte tekst bewerken {#edit-plain-text}

U kunt de tekst op zijn plaats bewerken door te dubbelklikken op de component of erop te dubbeltikken.

![Inhoud bewerken](assets/editing-content.png)

Druk op Enter/Return of selecteer buiten het tekstvak om uw wijzigingen op te slaan.

Wanneer u ervoor kiest om de tekstcomponent te selecteren, worden de details weergegeven in de eigenschappen rail. U kunt de tekst ook in de rails bewerken.

![Tekst bewerken in de eigenschappenbalk](assets/ue-editing-text-component-rail.png)

De details van uw tekst zijn ook beschikbaar in de eigenschappen rail. Wijzigingen worden automatisch opgeslagen als de focus het bewerkte veld verlaat in de eigenschappenrails.

### RTF-tekst bewerken {#edit-rich-text}

U kunt de tekst op zijn plaats bewerken door te dubbelklikken op de component of erop te dubbeltikken.

![Een RTF-component bewerken](assets/rich-text-editing.png)

Voor uw gemak zijn opmaakopties en details op uw tekst beschikbaar op twee plaatsen.

* De **contextmenu** wordt boven het tekstblok met tekstopmaak geopend en biedt in context basisopmaakopties. Vanwege ruimtebeperkingen kunnen sommige opties achter de knop voor ovaal worden verborgen.
* De **eigenschappen per spoor** toont alle opmaakopties die beschikbaar zijn samen met de tekst.

Wijzigingen worden automatisch opgeslagen als de focus het bewerkte veld verlaat.

### Media bewerken {#edit-media}

U kunt de details bekijken in de eigenschappen rail.

![Media bewerken](assets/ue-edit-media.png)

1. Tik of klik op de voorvertoning van de geselecteerde afbeelding in de eigenschappenbalk.
1. De [middelenkiezer](/help/assets/asset-selector.md#using-asset-selector) wordt geopend zodat u een element kunt selecteren.
1. Selecteer deze optie om een nieuw element te selecteren.
1. Selecteren **Selecteren** om terug te keren naar de spoorstaaf waar het activum is vervangen.

Wijzigingen worden automatisch in de inhoud opgeslagen.

### Inhoudsfragmenten bewerken {#edit-content-fragment}

Als u een [Inhoudsfragment](/help/sites-cloud/administering/content-fragments/overview.md) u kunt de details ervan in de eigenschappen rail uitgeven.

![Een inhoudsfragment bewerken](assets/ue-edit-cf.png)

De velden die zijn gedefinieerd in het inhoudsmodel van het geselecteerde inhoudsfragment, worden weergegeven en kunnen worden bewerkt in de eigenschappenbalk.

Als u een veld selecteert dat verwant is aan een inhoudsfragment, wordt het inhoudsfragment in de componentrail geladen en wordt het veld automatisch naar het veld geschoven.

Wijzigingen worden automatisch opgeslagen als de focus het bewerkte veld verlaat in de eigenschappenrails.

Als u het inhoudsfragment in het dialoogvenster [Inhoudsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md) in plaats daarvan, klik [bewerkknop](#edit) in de modusrail.

Afhankelijk van de behoeften van uw workflow wilt u het inhoudsfragment wellicht bewerken in de universele editor of rechtstreeks in de editor voor inhoudsfragmenten.

### Componenten toevoegen aan containers {#adding-components}

1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Selecteer vervolgens het invoegpictogram in de eigenschappenrails.

   ![Een component selecteren om aan een container toe te voegen](assets/ue-add-component.png)

De component wordt opgenomen in de container en kan in de redacteur worden uitgegeven.

>[!TIP]
>
>De sneltoets gebruiken `A` om een component aan de geselecteerde container toe te voegen.

### Componenten uit containers verwijderen {#deleting-components}

1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Selecteer het chevron-pictogram van de container om de inhoud ervan in de inhoudsstructuur uit te vouwen.
1. Selecteer vervolgens in de inhoudsstructuur een component in de container.
1. Selecteer het verwijderingspictogram in de eigenschappenrails.

   ![Een component verwijderen](assets/ue-delete-component.png)

De geselecteerde component is verwijderd.

>[!TIP]
>
>De sneltoets gebruiken `Shift+Backspace` om de geselecteerde component uit zijn container te schrappen.

### Componenten opnieuw ordenen in containers {#reordering-components}

1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Indien nog niet in [de modus Inhoudsboomstructuur,](#content-tree-mode) ga naar de site.
1. Selecteer het chevron-pictogram van de container om de inhoud ervan in de inhoudsstructuur uit te vouwen.
1. De greeppictogrammen van de belemmering naast de componenten binnen de container tonen dat u hen kunt herschikken. Sleep de componenten om deze binnen de container opnieuw te ordenen.

   ![Componenten opnieuw ordenen](assets/ue-reordering-components.png)

1. De gesleepte component wordt grijs in de componentstructuur, terwijl de invoegpositie wordt aangeduid met een blauwe lijn. Laat de component los om deze op de nieuwe locatie te plaatsen.

De componenten worden opnieuw gerangschikt in zowel de inhoudsstructuur als de editor

## Inhoud voorvertonen {#previewing-content}

Wanneer u klaar bent met het bewerken van inhoud, wilt u er vaak door navigeren om te zien hoe de inhoud er op andere pagina&#39;s uitziet. In [voorbeeldmodus](#preview-mode) u kunt op koppelingen klikken om door de inhoud te navigeren zoals een lezer zou doen. De inhoud wordt in de editor gerenderd zoals deze zou worden gepubliceerd.

In de voorvertoningsmodus reageert de gebruiker op de inhoud door erop te tikken of erop te klikken, net als bij een lezer van de inhoud. Als u de te bewerken inhoud wilt selecteren, schakelt u uit van [voorvertoningsmodus.](#preview-mode)

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Inhoud publiceren met de Universal Editor](publishing.md) - Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
