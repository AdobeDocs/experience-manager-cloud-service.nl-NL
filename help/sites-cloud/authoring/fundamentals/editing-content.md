---
title: Pagina-inhoud bewerken
description: Nadat u de pagina hebt gemaakt, kunt u de inhoud bewerken en de gewenste updates uitvoeren
exl-id: 8af0f621-14e8-4605-a51a-a3be21f19092
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '2974'
ht-degree: 4%

---


# Pagina-inhoud bewerken{#editing-page-content}

Nadat u de pagina hebt gemaakt (nieuw of als onderdeel van een opstart of live kopie), kunt u de inhoud bewerken en de gewenste updates uitvoeren.

De inhoud wordt toegevoegd gebruikend [ componenten ](/help/sites-cloud/authoring/features/components-console.md) (aangewezen aan het inhoudstype) die op de pagina kunnen worden gesleept. Deze kunnen vervolgens worden bewerkt, verplaatst of verwijderd.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten en machtigingen nodig om pagina&#39;s te kunnen bewerken.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.
<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to edit pages.
-->

>[!NOTE]
>
>Als uw pagina en/of malplaatje geschikt opstelling is geweest, dan kunt u [ ontvankelijke lay-out ](/help/sites-cloud/authoring/features/responsive-layout.md) gebruiken wanneer het uitgeven.

>[!TIP]
>
>Wanneer op **** wijze uitgeeft, zijn de verbindingen in uw inhoud zichtbaar, maar **niet toegankelijk**. De wijze van de Voorproef van het gebruik ](#previewing-pages) als u wilt navigeren gebruikend de verbindingen in uw inhoud.[

{{edge-delivery-authoring}}

## Werkbalk Pagina {#page-toolbar}

De paginawerkbalk biedt toegang tot de juiste functionaliteit, afhankelijk van de paginaconfiguratie.

![ de toolbar van de Pagina ](/help/sites-cloud/authoring/assets/editing-page-toolbar.png)

De werkbalk biedt toegang tot een groot aantal opties. Afhankelijk van uw huidige context en configuratie zijn sommige opties mogelijk niet beschikbaar.

* **Knevel Zijpaneel**

  Dit opent/sluit het zijpaneel, dat [ Browser van Activa ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) houdt, [ Browser van de Component ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser), en [ de Boom van de Inhoud ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree).

  ![ Kneep van het Zijpaneel ](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **Informatie van de Pagina**

  Verleent toegang tot het [ menu van de Informatie van de Pagina ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) met inbegrip van paginadetails en acties die op de pagina met inbegrip van het bekijken en het uitgeven van paginainformatie, het bekijken van paginaeigenschappen, en het publiceren/unpublishing van de pagina kunnen worden genomen.

  ![ knoop van de Informatie van de Pagina ](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **Emulator**

  Knevels de [ mededingertoolbar ](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate), die wordt gebruikt om het blik-en-gevoel van de pagina op een ander apparaat na te bootsen. Dit wordt automatisch in- en uitgeschakeld in de lay-outmodus.

  ![ knoop van de Mededinger ](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

  Opent [ ContextHub ](/help/sites-cloud/authoring/personalization/contexthub.md). Alleen beschikbaar in de modus Voorbeeld.

  ![ knoop van de Hub van de Context ](/help/sites-cloud/authoring/assets/context-hub.png)

* **Titel van de Pagina**

  Dit is puur informatief.

  ![ Titel van de Pagina ](/help/sites-cloud/authoring/assets/page-title.png)

* **de Selector van de Wijze**

  Toont de huidige [ wijze ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) en laat u een andere wijze zoals uitgeven, lay-out, timewarp, of het richten selecteren.

  ![ de knoop van de Selecteur van de Wijze ](/help/sites-cloud/authoring/assets/mode-selector.png)

* **Voorproef**

  Laat [ voorproefwijze ](#preview-mode) toe. Hiermee wordt de pagina weergegeven zoals deze wordt weergegeven bij publicatie.

  ![ knoop van de Voorproef ](/help/sites-cloud/authoring/assets/preview.png)

* **annoteert**

  Laat u [ annotaties ](/help/sites-cloud/authoring/fundamentals/annotations.md) aan de pagina toevoegen wanneer het herzien van een pagina. Na de eerste annotatie schakelt het pictogram over naar een getal dat het aantal annotaties op de pagina aangeeft.

  ![ knoop van de Annotatie ](/help/sites-cloud/authoring/assets/annotations.png)

### Statusmelding {#status-notification}

Als een pagina deel van a [ werkschema ](/help/sites-cloud/authoring/workflows/overview.md) of veelvoudige werkschema&#39;s uitmaakt, wordt deze informatie getoond in een berichtbar bij de bovenkant van het scherm wanneer het uitgeven van de pagina.

![ Bericht van het Werkschema ](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>De statusbalk is alleen zichtbaar voor gebruikersaccounts met de juiste rechten.

In het bericht wordt de workflow weergegeven die op de pagina wordt uitgevoerd. Als de gebruiker in de huidige werkschemastap geïmpliceerd is, beïnvloeden de opties [ de werkschemastatus ](/help/sites-cloud/authoring/workflows/participating.md) en krijgen meer informatie over het werkschema ook beschikbaar zoals:

* **Volledig** - opent de **Volledige dialoog van het Punt van het Werk**
* **Afgevaardigde** - opent de **Volledige dialoog van het Punt van het Werk**
* **Details van de Mening** - opent het **venster van Details** van het werkschema

Het voltooien van en het delegeren van werkschemastappen via de kennisgevingsbar werken aangezien het wanneer [ deelnemend aan werkschema&#39;s ](/help/sites-cloud/authoring/workflows/participating.md) van het Bericht inbox.

Als de pagina aan veelvoudige werkschema&#39;s onderworpen is, wordt het aantal werkschema&#39;s getoond aan het rechtereind van het bericht samen met pijlknopen om u toe te staan om door de werkschema&#39;s te scrollen.

![ Veelvoudige werkschemaberichten ](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## Tijdelijke aanduiding voor onderdeel {#component-placeholder}

De tijdelijke aanduiding van de component is een indicator waarmee wordt aangegeven waar een component zich bevindt wanneer u deze neerzet - boven de component waarover u momenteel beweegt.

* Bij het toevoegen van een nieuwe component aan de pagina (slepen vanuit de componentbrowser):

  ![ Placeholder wanneer het toevoegen van een nieuwe component aan een pagina ](/help/sites-cloud/authoring/assets/editing-component-placeholder.png)

* Bij het verplaatsen van een bestaande component:

  ![ Placeholder wanneer het bewegen van een bestaande component op een pagina ](/help/sites-cloud/authoring/assets/editing-component-placeholder-existing.png)

## Een component invoegen {#inserting-a-component}

### Een component invoegen vanuit de Componentbrowser {#inserting-a-component-from-the-components-browser}

U kunt een nieuwe component toevoegen door [ componentenbrowser ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) te gebruiken. De [ componentenplaceholder ](#component-placeholder) toont u waar de component wordt geplaatst:

1. Zorg ervoor dat uw pagina op [**is geef** wijze ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) uit.
1. Open [ componentenbrowser ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
1. Sleep de vereiste component aan de [ vereiste positie ](#component-placeholder).
1. [ geeft ](#edit-content) de component uit.

>[!NOTE]
>
>Op een mobiel apparaat vult de componentbrowser het volledige scherm. Nadat u een component hebt gesleept, wordt de pagina in de browser weer weergegeven, zodat u de component kunt plaatsen.

### Een component invoegen vanuit het alineasysteem {#inserting-a-component-from-the-paragraph-system}

U kunt een nieuwe component toevoegen door de **componenten van de Belemmering hier** doos van het paragraafsysteem te gebruiken:

1. Zorg ervoor dat uw pagina op [**is geef** wijze ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) uit.
1. Er zijn twee manieren om een nieuwe component in het alineasysteem te selecteren en toe te voegen:

   * Selecteer de **optie van de Component van het Tussenvoegsel** (+) van of de toolbar van een bestaande component of de **componenten van de Belemmering hier** doos.

     ![ neem een component ](/help/sites-cloud/authoring/assets/editing-insert-component.png) op

   * Als u op een Desktopapparaat bent kunt u de **componenten van de Belemmering hier** doos tweemaal klikken.

   * De **dialoog van het Tussenvoegsel Nieuwe Component** open om u uw vereiste component te laten selecteren:

     ![ Tussenvoegsel Nieuwe dialoog van de Component ](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. De geselecteerde component wordt onder aan de pagina toegevoegd. [ geeft ](#edit-content) de component zoals vereist uit.

### Een component invoegen met de Assets-browser {#inserting-a-component-using-the-assets-browser}

U kunt een nieuwe component aan de pagina ook toevoegen door activa van [ activa te slepen browser ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser). Hiermee wordt automatisch een component van het juiste type gemaakt (en die het element bevat).

Dit gedrag kan voor uw installatie worden gevormd. Zie Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt voor meer informatie. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

Een component maken door een van de bovenstaande elementtypen te slepen:

1. Zorg ervoor dat uw pagina op [**is geef** wijze ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) uit.
1. Open [ activa browser ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
1. Sleep het vereiste element naar de gewenste positie. De [ componentenplaceholder ](#component-placeholder) toont u waar de component wordt geplaatst.

   Een component die geschikt is voor het type element, wordt op de vereiste locatie gemaakt en bevat het geselecteerde element.

1. [ geef ](#edit-content) de component indien nodig uit.

>[!NOTE]
>
>Op een mobiel apparaat vult de middelenbrowser het volledige scherm. Nadat u een element hebt gesleept, wordt de pagina in de browser weergegeven, zodat u het element kunt plaatsen.

Als wanneer het doorbladeren van de activa u vindt dat u een snelle verandering in activa moet aanbrengen, kunt u de [ activaredacteur ](/help/assets/manage-digital-assets.md) direct van browser beginnen door het uitgeven pictogram naast de naam van activa te klikken.

![ Activa geeft knoop uit ](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Werkbalk Component {#component-toolbar}

Als u een component selecteert, wordt de werkbalk geopend. Dit verleent toegang tot diverse acties die op de component kunnen worden uitgevoerd.

De acties die de gebruiker daadwerkelijk kan uitvoeren, worden op de juiste wijze weergegeven en niet alle acties worden hier beschreven.

![ Toolbar van de Component ](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

* **geeft** uit

  [ afhankelijk van het componenttype ](/help/sites-cloud/authoring/fundamentals/components.md), laat dit u [ uitgeven de inhoud van de component ](#edit-content). Er wordt vaak een werkbalk weergegeven.

  ![ geef knoop ](/help/sites-cloud/authoring/assets/editing-component-toolbar-edit.png) uit

* **vormen**

  [ afhankelijk van het componenttype ](/help/sites-cloud/authoring/fundamentals/components.md), laat dit u uitgeven en de eigenschappen van de component vormen. Er wordt vaak een dialoogvenster geopend.

  ![ vorm knoop ](/help/sites-cloud/authoring/assets/editing-component-toolbar-configure.png)

* **Exemplaar**

  Hiermee wordt de component naar het klembord gekopieerd. Na de plakactie, zal de originele component blijven.

  ![ knoop van het Exemplaar ](/help/sites-cloud/authoring/assets/editing-component-toolbar-copy.png)

* **Besnoeiing**

  Hiermee wordt de component naar het klembord gekopieerd. Na de plakhandeling wordt de oorspronkelijke component verwijderd.

  ![ knoop van de Besnoeiing ](/help/sites-cloud/authoring/assets/editing-component-toolbar-cut.png)

* **Schrapping**

  Hiermee verwijdert u de component van de pagina met uw bevestiging.

  ![ knoop van de Schrapping ](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **component van het Tussenvoegsel**

  Dit opent de dialoog om [ een nieuwe component ](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system) toe te voegen.

  ![ knoop van het Tussenvoegsel ](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **Deeg**

  Hiermee wordt de component van het klembord naar de pagina geplakt. Of het origineel overblijft, hangt af van het feit of u de kopie of het knipsel hebt gebruikt.

   * U kunt op dezelfde pagina of op een andere pagina plakken.
   * Het geplakte item wordt boven het item geplakt waar u de plakactie selecteert.
   * De handeling Pate wordt alleen weergegeven als er inhoud op het klembord staat.

  ![ knoop van het Deeg ](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

  >[!NOTE]
  >
  >Als u plakt naar een andere pagina die al was geopend vóór de knip-/kopieerbewerking, moet u de pagina vernieuwen om de geplakte inhoud te zien.

* **Groep**

  Hiermee kunt u meerdere componenten tegelijk selecteren. Het zelfde kan op een Desktopapparaat door a **worden bereikt Control+Click** of **Command+Click**.

  ![ knoop van de Groep ](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **Ouder**

  Hiermee kunt u de bovenliggende component van de geselecteerde component selecteren.

  ![ Bovenliggende knoop ](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **Lay-out**

  Dit laat u de [ lay-out ](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) van de geselecteerde component wijzigen. Dit is slechts op de geselecteerde component van toepassing en activeert niet de [ wijze van de Lay-out ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) voor de volledige pagina.

  ![ knoop van de Lay-out ](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **Bekeerling in een variatie van het ervaringsfragment**

  Dit laat u een [ ervaringsfragment ](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) van de geselecteerde component tot stand brengen of het toevoegen aan een bestaand ervaringsfragment.

  ![ Bekeerling in de knoop van het Fragment van de Ervaring ](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## Inhoud bewerken {#edit-content}

Er zijn twee methoden om inhoud toe te voegen en/of te bewerken in componenten:

* Open de [ componentendialoog voor het uitgeven ](#component-edit-dialog).
* [ belemmering en laat vallen activa ](#drag-and-drop-assets-into-component) van activa browser om inhoud direct toe te voegen.

### Dialoogvenster Component Edit {#component-edit-dialog}

U kunt een component openen om de content te bewerken met het pictogram [Bewerken (potlood) van de werkbalk van de component](#component-toolbar).

De exacte bewerkingsopties zijn afhankelijk van de component. Voor sommige componenten [ zullen alle acties slechts op het volledige schermwijze ](#edit-content-full-screen-mode) beschikbaar zijn. Bijvoorbeeld:

* Tekstcomponent

  ![ Toolbar van de tekstcomponent ](/help/sites-cloud/authoring/assets/editing-text-component-toolbar.png)

* Afbeeldingscomponent

  ![ Toolbar van de beeldcomponent ](/help/sites-cloud/authoring/assets/editing-image-component-toolbar.png)

  >[!NOTE]
  >
  >Bewerken werkt niet op een lege afbeeldingscomponent.
  >
  >U moet een afbeelding naar de component slepen of uploaden voordat u deze kunt bewerken.

* Afbeeldingscomponent - volledig scherm

  [ het ingaan van volledige het schermwijze ](#edit-content-full-screen-mode) voor de beeldcomponent staat voor meer ruimte toe om het beeld uit te geven en extra het uitgeven opties zoals **Kaart van de Lancering** en **Gezoem van het Terugstellen** te tonen. Bovendien kunt u op het volledige scherm voorinstellingen voor bijsnijden selecteren.

  {het volledige schermwijze van de Component van het Beeld 0} ](/help/sites-cloud/authoring/assets/editing-image-component-full-screen.png)![

* Componenten die zijn samengesteld uit meerdere basiscomponenten vragen u eerst om te bevestigen welke set bewerkingsopties u wilt:

### Assets naar component slepen {#drag-and-drop-assets-into-component}

Voor specifieke componenttypen (zoals afbeeldingen) kunt u elementen van de elementenbrowser rechtstreeks naar de component slepen om de inhoud bij te werken.

## Inhoud bewerken in de modus Volledig scherm {#edit-content-full-screen-mode}

Voor alle componenten kunt u de modus Volledig scherm openen (en afsluiten):

![ Volledige knoop van het Scherm ](/help/sites-cloud/authoring/assets/editing-full-screen.png)

Bijvoorbeeld, de **component van de Tekst**:

![ component van de Tekst in volledig scherm ](/help/sites-cloud/authoring/assets/editing-text-full-screen.png)

>[!NOTE]
>
>Voor sommige componenten zal de modus Volledig scherm meer opties beschikbaar hebben dan de standaard interne editor.

## Een component verplaatsen {#moving-a-component}

Een alinea-component verplaatsen:

1. Selecteer de alinea die u wilt verplaatsen met de optie voor selecteren en vasthouden of met klikken en vasthouden.
1. Sleep de alinea naar de nieuwe locatie. AEM geeft aan waar de alinea kan worden geplaatst. Zet het neer op de gewenste plaats.

   ![ Bewegend een component ](/help/sites-cloud/authoring/assets/editing-moving-component.png)

1. Uw alinea wordt verplaatst.

>[!TIP]
>
>U kunt ook gebruiken [ Besnoeiing en Deeg ](#component-toolbar) om een component te bewegen.

## Componentlay-out bewerken {#edit-component-layout}

In plaats van herhaaldelijk over te schakelen van de bewerkingsmodus naar [de lay-outmodus](/help/sites-cloud/authoring/features/responsive-layout.md) om een component aan te passen, kunt u de actie **Lay-out** selecteren zodat een component de lay-out van die component kan wijzigen en tijd kan besparen door de bewerkingsmodus niet te verlaten.

1. Wanneer op **uitgeeft** wijze van de plaatsenconsole, die een component selecteert openbaart de toolbar van de component.

   ![ de componententoolbar van een paginacomponent ](/help/sites-cloud/authoring/assets/editing-layout-toolbar.png)

   Selecteer de **Lay-out** actie om de lay-out van de component aan te passen.

   ![ de knoop van de Lay-out van de componententoolbar ](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

1. Nadat de handeling Lay-out is geselecteerd:

   * De formaatgrepen voor de componentweergave.
   * De emulatorwerkbalk wordt boven in het scherm weergegeven.
   * De acties van de lay-out in plaats van de standaard geeft acties uit tonen op de componententoolbar.

   ![ een component op lay-outwijze ](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   U kunt de lay-out van de component nu wijzigen aangezien u op [ lay-outwijze ](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode) zou.

1. Na het aanbrengen van de noodzakelijke lay-outveranderingen, klik **dicht** knoop in het menu van de componentenactie ophouden wijzigend de lay-out van de component. De werkbalk van de component keert terug naar de normale bewerkingsstatus.

   ![ de componententoolbar van een paginacomponent ](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>De actie Lay-out is beperkt in werkingsgebied tot de geselecteerde component. Als u bijvoorbeeld de lay-out van een component bewerkt en vervolgens op een andere component klikt, wordt de werkbalk voor standaardbewerking (niet de layoutwerkbalk) weergegeven voor de zojuist geselecteerde component en verdwijnen de formaatgrepen en de emulatorwerkbalk.
>
>Als u de algemene lay-out van de pagina moet uitgeven, die veelvoudige componenten beïnvloeden, schakelaar aan de [ lay-outwijze ](/help/sites-cloud/authoring/features/responsive-layout.md).

## Overgenomen componenten {#inherited-components}

Overerving is het mechanisme waarbij inhoud automatisch van de ene component naar de andere kan worden verplaatst. Overerfde componenten kunnen het product van diverse scenario&#39;s zijn, die omvatten:

* [Beheer van meerdere sites](/help/sites-cloud/administering/msm/overview.md)
* [ Lanceringen ](/help/sites-cloud/authoring/launches/overview.md) (wanneer gebaseerd op levende kopie).

U kunt de overerving annuleren (en vervolgens opnieuw inschakelen). Afhankelijk van de component kan deze beschikbaar zijn op de werkbalk van de component als de component zich op een pagina bevindt die deel uitmaakt van een live kopie of opstart (op basis van een live kopie).

![ een componententoolbar die overervingsverhouding ](/help/sites-cloud/authoring/assets/editing-component-toolbar-inheritance.png) tonen

Bijvoorbeeld:

* Overerving annuleren

  ![ annuleert Overerving knoop ](/help/sites-cloud/authoring/assets/editing-cancel-inheritance.png)

* Overerving opnieuw inschakelen (als overerving al is geannuleerd)

  ![ re-Enable de knoop van de Overerving ](/help/sites-cloud/authoring/assets/editing-reenable-inheritance.png)

* De handeling Uitvoeren is ook beschikbaar in de blauwdruk of de bron van Actieve kopie

  ![ knoop van de Uitvoer ](/help/sites-cloud/authoring/assets/editing-rollout.png)

## De paginasjabloon bewerken {#editing-the-page-template}

U kunt eenvoudig overschakelen naar de [sjablooneditor](/help/sites-cloud/authoring/features/templates.md#editing-templates-template-authors) door **Sjabloon bewerken** te selecteren in het menu [Pagina-informatie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information).

U kunt gemakkelijk zien op welke sjabloon de pagina is gebaseerd wanneer u de pagina selecteert in de [kolomweergave](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) of de [lijstweergave](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view).

## Status van live kopiëren {#live-copy-status}

De [ Levende de paginamodus van de Status van het Exemplaar ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) staat u een snel overzicht van de levende exemplaarstatus toe en welke componenten niet worden/worden geërft:

* Groene rand: Overgenomen
* Roze rand: overerving is geannuleerd

Bijvoorbeeld:

![ Voorbeeld van levende die exemplaarstatus wordt getoond ](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## Annotaties toevoegen {#adding-annotations}

[ Annotaties ](/help/sites-cloud/authoring/fundamentals/annotations.md) staan controleurs en andere auteurs toe om feedback op uw inhoud te verstrekken. Ze worden vaak gebruikt voor controle- en validatiedoeleinden.

## Pagina&#39;s voorvertonen {#previewing-pages}

Er zijn twee opties voor het voorvertonen van een pagina:

* ](#preview-mode) de Wijze van de Voorproef van 0} - snel, op zijn plaats voorproef[
* [ Mening zoals Gepubliceerd ](#view-as-published) - een volledige voorproef die de pagina in een nieuw lusje opent

>[!TIP]
>
>* Koppelingen in de inhoud zijn zichtbaar, maar niet toegankelijk in de bewerkingsmodus.
>* Gebruik een van de voorvertoningsopties als u door de koppelingen wilt navigeren.
>* Gebruik de [ toetsenbordkortere weg ](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M` om tussen voorproef en de laatste geselecteerde wijze te schakelen.

>[!NOTE]
>
>Het WCM-modencookie wordt ingesteld voor beide voorvertoningsopties.

### Voorvertoningsmodus {#preview-mode}

Wanneer het uitgeven van inhoud kunt u voorproef de pagina gebruikend de voorproef [ wijze ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes). Deze modus:

* Hiermee verbergt u verschillende bewerkingsmechanismen waarmee u snel kunt zien hoe de pagina er bij het publiceren uitziet.
* Hiermee kunt u navigeren met koppelingen.
* Vernieuw **** niet de paginainhoud.

Tijdens het ontwerpen is de voorvertoningsmodus beschikbaar met het pictogram rechtsboven in de pagina-editor:

![ knoop van de Voorproef ](/help/sites-cloud/authoring/assets/preview.png)

### Weergeven als gepubliceerd {#view-as-published}

De **Mening zoals Gepubliceerde** optie is beschikbaar bij het [ menu van de Informatie van de Pagina ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information). Hierdoor wordt de pagina op een nieuw tabblad geopend, wordt de inhoud vernieuwd en wordt de pagina precies zo weergegeven als in de publicatieomgeving.

## Een pagina vergrendelen {#locking-a-page}

AEM kunt u een pagina vergrendelen, zodat niemand anders de inhoud kan bewerken. Deze vergrendeling is handig wanneer u meerdere bewerkingen op een bepaalde pagina uitvoert of wanneer u een pagina kort wilt stilzetten.

Een pagina kan worden vergrendeld vanuit:

* **Sites** console

   1. Selecteer de pagina met [ selectiemodus ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
   1. Selecteer het slotpictogram.

      ![ knoop van het Slot ](/help/sites-cloud/authoring/assets/lock.png)

* **Redacteur van de Pagina**

   1. Selecteer het **pictogram van de Informatie van de Pagina** om het menu te openen.
   1. Selecteer de **optie van de Pagina van het Slot**.

Nadat de weergave op de console is vergrendeld, wordt de informatie bijgewerkt en wanneer u een vergrendelingssymbool bewerkt, wordt deze weergegeven op de werkbalk.

![ Voorbeeld van een gesloten pagina ](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer u een gebruiker imiteert. Een pagina die op deze manier is vergrendeld, kan echter alleen worden ontgrendeld (door klanten) met behulp van de gebruiker die als imitatie is opgetreden.
>
>Pagina&#39;s kunnen niet worden ontgrendeld door zich voor te doen als de gebruiker die de pagina heeft vergrendeld.
>
>Als de gebruiker die de pagina heeft vergrendeld niet beschikbaar is om de pagina te ontgrendelen, neemt u contact op met de Klantenondersteuning om de opties voor het verwijderen van de vergrendeling te evalueren.

## Een pagina ontgrendelen {#unlocking-a-page}

Het ontgrendelen van een pagina is zeer gelijkaardig aan [ het sluiten van de pagina ](#locking-a-page). Nadat de pagina is vergrendeld, worden de vergrendelingsopties vervangen door ontgrendelingsacties.

In het menu Pagina-informatie wordt **Ontgrendelen** als optie weergegeven en het pictogram Vergrendelen in de Sites-console wordt vervangen door een pictogram **Ontgrendelen**.

![ ontgrendelingsknoop ](/help/sites-cloud/authoring/assets/unlock.png)

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer u een gebruiker imiteert. Een pagina die op deze manier is vergrendeld, kan echter alleen dan worden ontgrendeld (door klanten) met de gebruiker die zich heeft voorgedaan.
>
>Pagina&#39;s kunnen niet worden ontgrendeld door zich voor te doen als de gebruiker die de pagina heeft vergrendeld.
>
>Als de gebruiker die de pagina heeft vergrendeld niet beschikbaar is om de pagina te ontgrendelen, neemt u contact op met de Klantenondersteuning om de opties voor het verwijderen van de vergrendeling te evalueren.

<!--
>[!CAUTION]
>
>Locking a page can be performed when impersonating a user. However a page locked in this way can only then be unlocked by the user who was impersonated, or by a user with admin rights (a member of AEM Administrator IMS profile).
>
>Pages cannot be unlocked by impersonating the user who locked the page.
-->

<!--
>Locking a page can be performed when [impersonating a user](/help/sites-administering/security.md#impersonating-another-user). However a page locked in this way can only then be unlocked by the user who was impersonated or by the admin user.
-->

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren {#undoing-and-redoing-page-edits}

Met de volgende pictogrammen kunt u een handeling ongedaan maken of opnieuw uitvoeren. Deze worden in voorkomend geval weergegeven op de werkbalk:

![ Ongedaan maken en Opnieuw knopen ](/help/sites-cloud/authoring/assets/redo.png)

>[!TIP]
>
>* De [ toetsenbordkortere weg ](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Z` is ook beschikbaar om pagina uit te geven acties.
>* De sneltoets `Ctrl-Y` is ook beschikbaar voor het opnieuw uitvoeren van paginabewerkingsacties.

>[!NOTE]
>
>Zie [ ongedaan maken en het Opnieuw doen van de Uitgeeft van de Pagina - de Theorie ](#undoing-and-redoing-page-edits-the-theory) voor de volledige details van wat mogelijk is wanneer het ongedaan maken en het opnieuw doen van pagina geeft uit.

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie {#undoing-and-redoing-page-edits-the-theory}

AEM slaat een geschiedenis van acties op die u uitvoert en de opeenvolging waarin u hen uitvoerde zodat u veelvoudige acties in de orde ongedaan kunt maken dat u hen uitvoerde en hen opnieuw doet om één of meerdere acties indien nodig opnieuw toe te passen.

Als een element op de inhoudspagina wordt geselecteerd (zoals een tekstcomponent), dan is het ongedaan maken en opnieuw bevel op het geselecteerde punt van toepassing.

Het gedrag van de opdrachten Ongedaan maken en Opnieuw is vergelijkbaar met dat van andere software. Gebruik de opdrachten om de recente status van uw webpagina te herstellen terwijl u beslissingen neemt over de inhoud. Als u bijvoorbeeld een tekstalinea naar een andere locatie op de pagina verplaatst, kunt u de opdracht Ongedaan maken gebruiken om de alinea terug te verplaatsen. Als u vervolgens besluit dat de vorige positie beter was, gebruikt u de opdracht Opnieuw uitvoeren om de bewerking Ongedaan maken ongedaan te maken.

U kunt bijvoorbeeld:

* Voer handelingen opnieuw uit zolang u geen paginabewerking hebt uitgevoerd nadat u Ongedaan maken hebt gebruikt.
* U kunt maximaal 20 bewerkingen ongedaan maken (standaardinstelling).
* Gebruik ook [ kortere weg van het Toetsenbord ](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) voor ongedaan maken en opnieuw doen.

U kunt de volgende typen paginawijzigingen ongedaan maken en opnieuw uitvoeren:

* Alinea&#39;s toevoegen, bewerken, verwijderen en verplaatsen
* Lokaal bewerken van alinea-inhoud
* Items op een pagina kopiëren, knippen en plakken

>[!NOTE]
>
>* Er zijn speciale machtigingen vereist voor het ongedaan maken en opnieuw uitvoeren van wijzigingen in bestanden en afbeeldingen.
>* De geschiedenis van wijzigingen in bestanden en afbeeldingen duurt minimaal tien uur. Na deze tijd is het ongedaan maken van de wijzigingen echter niet gegarandeerd. De beheerder kan de standaardtijd van tien uur wijzigen.
>* Uw systeembeheerder kan diverse aspecten van Undo/Opnieuw eigenschappen volgens de vereisten voor uw instantie vormen.
<!--* Your system administrator can [configure various aspects of the Undo/Redo features](/help/sites-administering/config-undo.md) according to the requirements for your instance.-->
