---
title: Inhoud ontwerpen met de Universal Editor
description: Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: f28b8a85de76a1658ef45c509cbf5600baa1bb3a
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 0%

---


# Inhoud ontwerpen met de Universal Editor {#authoring}

Leer hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud tot stand te brengen gebruikend de Universele Redacteur.

## Inleiding {#introduction}

Met de Universal Editor kunt u elk aspect van elke inhoud in een implementatie bewerken, zodat u uitzonderlijke ervaringen kunt bieden, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.

Hiervoor verschaft de Universal Editor de auteur van inhoud een intuïtieve gebruikersinterface die minimale training vereist om eenvoudig in de inhoud te kunnen springen en beginnen met het bewerken ervan. In dit document wordt de auteurservaring van de Universal Editor beschreven.

>[!TIP]
>
>Zie het document voor een meer gedetailleerde inleiding tot de Universal Editor [Introductie van de Universal Editor.](introduction.md)

>[!NOTE]
>
>De Universal Editor is nog in ontwikkeling. Momenteel kunnen niet alle inhoudstypen worden bewerkt.

## De app voorbereiden {#prepare-app}

Als u inhoud voor een app wilt ontwerpen met de Universal Editor, moet de app van instrumenten zijn voorzien door een ontwikkelaar om de editor te ondersteunen.

>[!TIP]
>
>Zie [Aan de slag met de Universal Editor in AEM](getting-started.md) voor een voorbeeld van hoe u een AEM toepassing configureert voor gebruik met de Universal Editor.

## Aanmelden {#sign-in}

Wanneer de app van instrumenten is voorzien om met de Universal Editor te werken, moet u zich aanmelden bij de Universal Editor. U hebt een Adobe ID nodig om u aan te melden en [toegang hebben tot de Universal Editor.](getting-started.md#request-access)

Nadat u bent aangemeld, voert u de URL van de pagina die u wilt bewerken in het dialoogvenster [locatiebalk.](#location-bar) zodat u inhoud zoals [tekstinhoud](#text-mode) of [media-inhoud.](#media-mode)

## De gebruikersinterface begrijpen {#ui}

De interface is verdeeld in vijf hoofdgebieden.

* [De koptekst van het Experience Cloud](#experience-cloud-header)
* [De koptekst van de Universal Editor](#universal-editor-header)
* [De modusrail](#mode-rail)
* [De editor](#editor)
* [De componentrail](#component-rail)

![De gebruikersinterface van de Universal Editor](assets/ui.png)

### De koptekst van het Experience Cloud {#experience-cloud-header}

De koptekst van het Experience Cloud bevindt zich altijd boven aan het scherm. Het is een anker dat u vertelt waar u binnen Experience Cloud bent en u helpt aan andere Experience Cloud apps navigeren.

![De koptekst van het Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Selecteer de verbinding van Adobe Experience Cloud bij de linkerzijde van de kopbal om aan de wortel van uw oplossing van de Experience Manager te navigeren om tot hulpmiddelen zoals [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) en [Softwaredistributie.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

![De knop Algemene navigatie](assets/global-navigation.png)

#### Organisatie {#organization}

Hier wordt de organisatie weergegeven waarmee u momenteel bent aangemeld. Tik of klik om over te schakelen naar een andere organisatie als uw Adobe ID is gekoppeld aan meerdere.

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

Tik of klik op het pictogram dat uw gebruiker vertegenwoordigt om toegang te krijgen tot uw gebruikersinstellingen. Als u geen gebruikersbeeld hebt gevormd, wordt een pictogram willekeurig toegewezen.

![Gebruikerseigenschappen](assets/user-properties.png)

### De koptekst van de Universal Editor {#universal-editor-header}

De Universal Editor-koptekst bevindt zich altijd boven aan het scherm net onder [de koptekst van het Experience Cloud.](#experience-cloud-header) Hiermee kunt u snel naar een andere pagina navigeren om deze te bewerken en te publiceren.

![De koptekst van de Universal Editor](assets/universal-editor-header.png)

#### Het menu Hamburger {#hamburger-menu}

Het hamburgermenu is nog niet geïmplementeerd.

![Hamburger-menu](assets/hamburger-menu.png)

#### Locatiebalk {#location-bar}

Op de locatiebalk ziet u het adres van de pagina die u bewerkt. Tik of klik om het adres in te voeren van een andere pagina die u wilt bewerken.

![Locatiebalk](assets/location-bar.png)

>[!TIP]
>
>De sneltoets gebruiken `L` de adresbalk openen.

>[!NOTE]
>
>Elke pagina die u wilt bewerken met de universele editor moet [van instrumenten voorzien om de Universele Redacteur te steunen.](getting-started.md)

#### Emulatorinstellingen {#emulator}

Tik of klik op het emulatiepictogram om te bepalen hoe de Universal Editor de pagina weergeeft.

![Emulatorpictogram](assets/emulator.png)

Als u op het emulatiepictogram tikt of erop klikt, worden de opties weergegeven.

![Opties voor emulatie](assets/emulation-options.png)

Standaard wordt de editor geopend in een computerlay-out waarin de hoogte en breedte automatisch door de browser worden gedefinieerd.

U kunt er ook voor kiezen om een mobiel apparaat te emuleren en in de Universele Editor:

* De oriëntatie definiëren
* Breedte en hoogte definiëren
* De richting wijzigen

#### App-voorvertoning openen {#open-app-preview}

Tik of klik op het pictogram met de voorvertoning van de geopende app om de pagina die u momenteel bewerkt te openen op een eigen browsertabblad, zodat de editor er geen voorvertoning van kan weergeven.

![App-voorvertoning openen](assets/open-app-preview.png)

>[!TIP]
>
>De sneltoets gebruiken `O` (de letter O) om de voorvertoning van de app te openen.

#### Publicatie {#publish}

Tik of klik op de knop Publiceren zodat u de wijzigingen in de live inhoud kunt publiceren voor gebruik door uw lezers.

![Knop Publiceren](assets/publish.png)

>[!TIP]
>
>Zie het document [Inhoud publiceren met de Universal Visual Editor](publishing.md) voor meer informatie over publiceren met de Universele Redacteur.

### De Modus Rail {#rail}

De modusrail is altijd aanwezig langs de linkerkant van de editor. Zo kunt u gemakkelijk schakelen tussen de verschillende bewerkingsmodi.

![De modusrail](assets/mode-rail.png)

#### Voorvertoningsmodus {#preview-mode}

In voorproefwijze, de pagina die in de redacteur wordt teruggegeven zoals het op uw gepubliceerde dienst zou worden gezien. Hierdoor kan de auteur van de inhoud door de inhoud navigeren door op koppelingen te klikken, enz.

![Voorvertoningsmodus](assets/preview-mode.png)

>[!TIP]
>
>De sneltoets gebruiken `P` om over te schakelen naar de voorvertoningsmodus.

#### Tekstmodus {#text-mode}

In de tekstmodus kan de auteur van de inhoud klikken om tekstinhoud te selecteren.

![Tekstmodus](assets/text-mode.png)

* U kunt [onbewerkte tekst bewerken](#editing-content) op zijn plaats.
* U kunt [RTF bewerken](#editing-rich-text) op zijn plaats met extra opmaakopties die in de componentrail worden weergegeven.

>[!TIP]
>
>De sneltoets gebruiken `T` om over te schakelen naar de tekstmodus.

#### Mediamodus {#media-mode}

In de mediamodus kan de auteur van de inhoud klikken om media-inhoud te selecteren.

![Mediamodus](assets/media-mode.png)

De details van de inhoud worden weergegeven in de componentrail en de auteur kan ook [bewerk de media-inhoud.](#editing-media)

>[!TIP]
>
>De sneltoets gebruiken `M` om over te schakelen naar de mediamodus.

#### Componentmodus {#component-mode}

In de componentmodus kan de auteur van de inhoud klikken om te selecteren [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)

![Componentmodus](assets/component-mode.png)

Wanneer u een inhoudsfragment selecteert, worden de details ervan weergegeven in de componenttrack waar u het fragment kunt selecteren [Bewerk het inhoudsfragment.](#edit-content-fragment)

>[!TIP]
>
>De sneltoets gebruiken `C` om over te schakelen naar componentmodus.

### De Editor {#editor}

De editor neemt het grootste deel van het venster in beslag en is de locatie van de pagina die is opgegeven in [de locatiebalk](#location-bar) wordt weergegeven.

* Als de editor zich in een bewerkingsmodus bevindt, zoals [tekstmodus](#text-mode) of [mediamodus,](#media-mode) de inhoud kan worden bewerkt, maar u kunt geen koppelingen volgen.
* Als de editor zich bevindt in [voorvertoningsmodus,](#preview-mode) U kunt wel navigeren naar de inhoud en koppelingen volgen, maar u kunt de inhoud niet bewerken.

![Editor](assets/editor.png)

### Component Rail {#component-rail}

De componentrail is altijd aanwezig aan de rechterkant van de editor. Afhankelijk van de modus, kunnen er details worden weergegeven voor een component die is geselecteerd in de inhoud of de hiërarchie van de pagina-inhoud.

![De componentrail](assets/component-rail.png)

#### Eigenschappenmodus {#properties-mode}

In de modus Eigenschappen toont de rail de eigenschappen van de component die momenteel in de editor is geselecteerd. Dit is de standaardmodus van de componentrail wanneer een pagina wordt geladen.

![Eigenschappenmodus](assets/properties-mode.png)

Afhankelijk van het type component dat u selecteert, kunnen details worden weergegeven en gewijzigd in de eigenschappenrails.

![Componentdetails](assets/component-details.png)

Niet alle componenten hebben details die kunnen worden weergegeven en/of bewerkt.

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

#### Bewerken {#edit}

Wanneer in [componentmodus,](#component-mode) als u een [Inhoudsfragment](/help/assets/content-fragments/content-fragments.md) de bewerkingsoptie verschijnt op de componentrail.

![Pictogram Bewerken](assets/edit.png)

Als u op de knop Bewerken tikt of erop klikt, wordt het dialoogvenster [Inhoudsfragmenteditor](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor) op een nieuw tabblad, zodat u toegang hebt tot de volledige bevoegdheden van de Inhoudsfragmenteditor.

U kunt de details van het inhoudsfragment ook bewerken in de componenttrack, afhankelijk van de vereisten van de workflow.

>[!TIP]
>
>De sneltoets gebruiken `E` om een geselecteerde component te bewerken.

#### Toevoegen {#add}

Als u een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de optie voor toevoegen weergegeven op de componentrails.

![Pictogram toevoegen](assets/ue-add-component-icon.png)

Als u op de knop Toevoegen tikt of erop klikt, wordt een vervolgkeuzelijst geopend met componenten die beschikbaar zijn voor [toevoegen aan de geselecteerde container.](#adding-components)

>[!TIP]
>
>De sneltoets gebruiken `A` om een component aan een geselecteerde containercomponent toe te voegen.

#### Verwijderen {#delete}

Als u een component binnen een containercomponent selecteert in de inhoudsstructuur of in de editor, wordt de verwijderingsoptie weergegeven op de componentrail.

![Pictogram Verwijderen](assets/ue-delete-component-icon.png)

Tikken of klikken op de knop Verwijderen [verwijdert de component.](#deleting-components)

>[!TIP]
>
>De sneltoets gebruiken `Shift+Backspace` om een geselecteerde component uit een container te verwijderen.

## Inhoud bewerken {#editing-content}

Inhoud bewerken is eenvoudig en intuïtief. In de bewerkingsmodi ([tekstmodus](#text-mode), [mediamodus](#media-mode), en [componentmodus](#component-mode)), wordt bewerkbare inhoud gemarkeerd met een blauw vak terwijl u de muis over de inhoud in de editor beweegt.

![Bewerkbare inhoud wordt gemarkeerd door een blauw vak](assets/editable-content.png)

Houd er rekening mee dat in de bewerkingsmodus door tikken of klikken op inhoud wordt geprobeerd deze te selecteren voor bewerking. Als u door de inhoud wilt navigeren door de koppelingen te volgen, schakelt u over naar [voorvertoningsmodus.](#preview-mode)

Afhankelijk van de [mode](#mode-rail) Als u werkt met de inhoud die u selecteert, hebt u mogelijk andere opties voor het bewerken van de plaats en kunt u wellicht extra eigenschappen voor de inhoud bekijken met de opdracht [spoorstaaf.](#component-rail)

### Onbewerkte tekst bewerken {#edit-plain-text}

Als u binnen [tekstmodus](#text-mode) en selecteert u een tekstcomponent zonder opmaak, kunt u de tekst op zijn plaats bewerken.

![Inhoud bewerken](assets/editing-content.png)

Typ gewoon om de inhoud bij te werken. Druk op Enter/Return of tik of klik buiten het tekstvak om de wijzigingen op te slaan.

### RTF-tekst bewerken {#edit-rich-text}

Als u binnen [tekstmodus](#text-mode) en selecteert u een RTF-component, kunt u de tekst op zijn plaats bewerken.

Typ gewoon om de inhoud bij te werken. Druk op Enter/Return of tik of klik buiten het tekstvak om de wijzigingen op te slaan.

Bovendien zijn opmaakopties en details in de tekst beschikbaar in de componentrail.

![Een RTF-component bewerken](assets/rich-text-editing.png)

Opmaakwijzigingen worden automatisch naar uw inhoud opgeslagen.

### Media bewerken {#edit-media}

Als u binnen [mediamodus](#media-mode) Als u een afbeelding selecteert, kunt u de details ervan bekijken in de componentrail.

![Media bewerken](assets/ue-edit-media.png)

Tik of klik op de knop **Vervangen** onder de voorvertoning van de geselecteerde afbeelding in de componentrails om de afbeelding te vervangen door een andere afbeelding uit de bibliotheek met elementen.

1. De [middelenkiezer](/help/assets/asset-selector.md#using-asset-selector) wordt geopend zodat u een element kunt selecteren.
1. Tik of klik om een nieuw element te selecteren.
1. Tik of klik op **Selecteren** om terug te keren naar de spoorstaaf waar het actief is vervangen.

Wijzigingen worden automatisch in de inhoud opgeslagen.

>[!TIP]
>
>De sneltoets gebruiken `R` om de elementkiezer te openen en de geselecteerde afbeelding te vervangen.

### Inhoudsfragmenten bewerken {#edit-content-fragment}

Als u binnen [componentmodus](#component-mode) en selecteert u een [Inhoudsfragment](/help/assets/content-fragments/content-fragments.md) u kunt de details in de componentrail bewerken.

![Een inhoudsfragment bewerken](assets/ue-edit-cf.png)

De velden die zijn gedefinieerd in het inhoudsmodel van het geselecteerde inhoudsfragment, worden weergegeven en kunnen worden bewerkt in de componentrail.

Wijzigingen worden automatisch in de inhoud opgeslagen.

Als u het inhoudsfragment in het dialoogvenster [Inhoudsfragmenteditor](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor) in plaats daarvan, klik [bewerkknop](#edit) in de modusrail.

### Componenten toevoegen aan containers {#adding-components}

1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Tik vervolgens op het pictogram Toevoegen of klik op het pictogram in de componenttrack.

   ![Een component selecteren om aan een container toe te voegen](assets/ue-add-component.png)

De component wordt opgenomen in de container en kan in de redacteur worden uitgegeven.

### Componenten uit containers verwijderen {#deleting-components}

1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Tik of klik op het chevron-pictogram van de container om de inhoud ervan in de inhoudsstructuur uit te vouwen.
1. Selecteer vervolgens in de inhoudsstructuur een component in de container.
1. Tik of klik op het verwijderpictogram in de componenttrack.

   ![Een component verwijderen](assets/ue-delete-component.png)

De geselecteerde component is verwijderd.

### Componenten opnieuw ordenen in containers {#reordering-components}

1. Selecteer een containercomponent in de inhoudsstructuur of in de editor.
1. Indien nog niet in [de modus Inhoudsboomstructuur,](#content-tree-mode) ga naar de site.
1. Tik of klik op het chevron-pictogram van de container om de inhoud ervan in de inhoudsstructuur uit te vouwen.
1. De greeppictogrammen van de belemmering naast de componenten binnen de container tonen dat u hen kunt herschikken. Sleep de componenten om deze binnen de container opnieuw te ordenen.

   ![Componenten opnieuw ordenen](assets/ue-reordering-components.png)
1. De gesleepte component wordt grijs in de componentstructuur, terwijl de invoegpositie wordt aangeduid met een blauwe lijn. Laat de component los om deze op de nieuwe locatie te plaatsen.

De componenten worden opnieuw gerangschikt in zowel de inhoudsstructuur als de editor

## Inhoud voorvertonen {#previewing-content}

Wanneer u klaar bent met het bewerken van inhoud, wilt u er vaak door navigeren om te zien hoe de inhoud er op andere pagina&#39;s uitziet. In [voorbeeldmodus](#preview-mode) u kunt op koppelingen klikken om door de inhoud te navigeren zoals een lezer zou doen. De inhoud wordt in de editor gerenderd zoals deze zou worden gepubliceerd.

Houd er rekening mee dat in de voorvertoningsmodus tikken of klikken op inhoud reageert op de manier waarop dit voor een lezer van de inhoud gebeurt. Als u de te bewerken inhoud wilt selecteren, schakelt u over naar een bewerkingsmodus, zoals [tekstmodus](#text-mode) of [mediamodus.](#media-mode)

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Inhoud publiceren met de Universal Editor](publishing.md) - Leer hoe de Universal Visual Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
