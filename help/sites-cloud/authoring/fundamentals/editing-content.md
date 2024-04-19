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

Inhoud wordt toegevoegd met [componenten](/help/sites-cloud/authoring/features/components-console.md) (van toepassing op het inhoudstype) dat naar de pagina kan worden gesleept. Deze kunnen vervolgens worden bewerkt, verplaatst of verwijderd.

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
>Als uw pagina en/of sjabloon op de juiste wijze is ingesteld, kunt u [responsieve indeling](/help/sites-cloud/authoring/features/responsive-layout.md) bij het bewerken.

>[!TIP]
>
>Wanneer in **Bewerken** in de modus, zijn koppelingen in de inhoud zichtbaar, maar **niet toegankelijk**. Gebruiken [Voorvertoningsmodus](#previewing-pages) als u wilt navigeren met de koppelingen in de inhoud.

{{edge-delivery-authoring}}

## Werkbalk Pagina {#page-toolbar}

De paginawerkbalk biedt toegang tot de juiste functionaliteit, afhankelijk van de paginaconfiguratie.

![Pagina, werkbalk](/help/sites-cloud/authoring/assets/editing-page-toolbar.png)

De werkbalk biedt toegang tot een groot aantal opties. Afhankelijk van uw huidige context en configuratie zijn sommige opties mogelijk niet beschikbaar.

* **Zijpaneel in-/uitschakelen**

  Hiermee opent/sluit u het zijpaneel, dat de [Middelenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser), [Componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser), en [Inhoudsstructuur](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree).

  ![Zijpaneel in-/uitschakelen](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **Pagina-informatie**

  Biedt toegang tot de [Pagina-informatie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) menu met paginagegevens en handelingen die op de pagina kunnen worden uitgevoerd, zoals het weergeven en bewerken van pagina-informatie, het weergeven van pagina-eigenschappen en het publiceren/ongedaan maken van de publicatie van de pagina.

  ![Paginagegevens, knop](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **Emulator**

  Hiermee schakelt u het [emulator, werkbalk](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate), die wordt gebruikt om het uiterlijk van de pagina op een ander apparaat na te bootsen. Dit wordt automatisch in- en uitgeschakeld in de lay-outmodus.

  ![Emulator-knop](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

  Hiermee opent u de [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md). Alleen beschikbaar in de modus Voorbeeld.

  ![Knop Contexthub](/help/sites-cloud/authoring/assets/context-hub.png)

* **Paginatitel**

  Dit is puur informatief.

  ![Paginatitel](/help/sites-cloud/authoring/assets/page-title.png)

* **Modus selecteren**

  Hiermee wordt de huidige [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) en kunt u een andere modus selecteren, zoals bewerken, lay-out, tijdverdraaiing of doelversie.

  ![Modus selecteren, knop](/help/sites-cloud/authoring/assets/mode-selector.png)

* **Voorvertoning**

  Inschakelen [voorbeeldmodus](#preview-mode). Hiermee wordt de pagina weergegeven zoals deze wordt weergegeven bij publicatie.

  ![Knop Voorvertoning](/help/sites-cloud/authoring/assets/preview.png)

* **Annoteren**

  Hiermee kunt u toevoegen [annotaties](/help/sites-cloud/authoring/fundamentals/annotations.md) naar de pagina wanneer een pagina wordt gecontroleerd. Na de eerste annotatie schakelt het pictogram over naar een getal dat het aantal annotaties op de pagina aangeeft.

  ![Knop Annotatie](/help/sites-cloud/authoring/assets/annotations.png)

### Statusmelding {#status-notification}

Als een pagina deel uitmaakt van een [werkstroom](/help/sites-cloud/authoring/workflows/overview.md) Voor meerdere workflows wordt deze informatie weergegeven in een berichtenbalk boven aan het scherm wanneer u de pagina bewerkt.

![Workflowmelding](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>De statusbalk is alleen zichtbaar voor gebruikersaccounts met de juiste rechten.

In het bericht wordt de workflow weergegeven die op de pagina wordt uitgevoerd. Als de gebruiker betrokken is bij de huidige workflowstap, kunt u [de workflowstatus beïnvloeden](/help/sites-cloud/authoring/workflows/participating.md) en meer informatie over de workflow vindt u onder andere :

* **Voltooid** - Opent de **Voltooid het werkitem** dialoogvenster
* **Delegeren** - Opent de **Voltooid het werkitem** dialoogvenster
* **Details weergeven** - Opent de **Details** venster van de workflow

Workflowstappen uitvoeren en delegeren via de berichtenbalk werkt op dezelfde manier als wanneer [deelnemen aan workflows](/help/sites-cloud/authoring/workflows/participating.md) in het vak Melding.

Als de pagina aan veelvoudige werkschema&#39;s onderworpen is, wordt het aantal werkschema&#39;s getoond aan het rechtereind van het bericht samen met pijlknopen om u toe te staan om door de werkschema&#39;s te scrollen.

![Meerdere workflowmeldingen](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## Tijdelijke aanduiding voor onderdeel {#component-placeholder}

De tijdelijke aanduiding van de component is een indicator waarmee wordt aangegeven waar een component zich bevindt wanneer u deze neerzet - boven de component waarover u momenteel beweegt.

* Bij het toevoegen van een nieuwe component aan de pagina (slepen vanuit de componentbrowser):

  ![Tijdelijke aanduiding bij het toevoegen van een nieuwe component aan een pagina](/help/sites-cloud/authoring/assets/editing-component-placeholder.png)

* Bij het verplaatsen van een bestaande component:

  ![Tijdelijke aanduiding bij het verplaatsen van een bestaande component op een pagina](/help/sites-cloud/authoring/assets/editing-component-placeholder-existing.png)

## Een component invoegen {#inserting-a-component}

### Een component invoegen vanuit de Componentbrowser {#inserting-a-component-from-the-components-browser}

U kunt een nieuwe component toevoegen door de [componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser). De [tijdelijke aanduiding voor onderdeel](#component-placeholder) toont u waar de component wordt geplaatst:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Open de [componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
1. Sleep de vereiste component naar de [vereiste positie](#component-placeholder).
1. [Bewerken](#edit-content) de component.

>[!NOTE]
>
>Op een mobiel apparaat vult de componentbrowser het volledige scherm. Nadat u een component hebt gesleept, wordt de pagina in de browser weer weergegeven, zodat u de component kunt plaatsen.

### Een component invoegen vanuit het alineasysteem {#inserting-a-component-from-the-paragraph-system}

U kunt een nieuwe component toevoegen door de **Componenten hierheen slepen** vak van het alineasysteem:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Er zijn twee manieren om een nieuwe component in het alineasysteem te selecteren en toe te voegen:

   * Selecteer de **Component invoegen** van de werkbalk van een bestaande component of van de **Componenten hierheen slepen** doos.

     ![Een component invoegen](/help/sites-cloud/authoring/assets/editing-insert-component.png)

   * Als u zich op een desktopapparaat bevindt, kunt u dubbelklikken op de knop **Componenten hierheen slepen** doos.

   * De **Nieuwe component invoegen** wordt geopend zodat u de gewenste component kunt selecteren:

     ![Dialoogvenster Nieuwe component invoegen](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. De geselecteerde component wordt onder aan de pagina toegevoegd. [Bewerken](#edit-content) de component naar wens.

### Een component invoegen met de middelenbrowser {#inserting-a-component-using-the-assets-browser}

U kunt ook een nieuwe component aan de pagina toevoegen door een element van de [middelenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser). Hiermee wordt automatisch een component van het juiste type gemaakt (en die het element bevat).

Dit gedrag kan voor uw installatie worden gevormd. Zie Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt voor meer informatie. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

Een component maken door een van de bovenstaande elementtypen te slepen:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Open de [middelenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
1. Sleep het vereiste element naar de gewenste positie. De [tijdelijke aanduiding voor onderdeel](#component-placeholder) Hiermee kunt u zien waar de component zich bevindt.

   Een component die geschikt is voor het type element, wordt op de vereiste locatie gemaakt en bevat het geselecteerde element.

1. [Bewerken](#edit-content) het onderdeel, indien nodig.

>[!NOTE]
>
>Op een mobiel apparaat vult de middelenbrowser het volledige scherm. Nadat u een element hebt gesleept, wordt de pagina in de browser weergegeven, zodat u het element kunt plaatsen.

Als u bij het bladeren in de elementen opmerkt dat u snel een wijziging in een element moet aanbrengen, kunt u het dialoogvenster [middeleneditor](/help/assets/manage-digital-assets.md) rechtstreeks vanuit de browser door op het pictogram Bewerken naast de naam van het element te klikken.

![De knop Element bewerken](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Werkbalk Component {#component-toolbar}

Als u een component selecteert, wordt de werkbalk geopend. Dit verleent toegang tot diverse acties die op de component kunnen worden uitgevoerd.

De acties die de gebruiker daadwerkelijk kan uitvoeren, worden op de juiste wijze weergegeven en niet alle acties worden hier beschreven.

![Werkbalk Component](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

* **Bewerken**

  [Afhankelijk van het componenttype](/help/sites-cloud/authoring/fundamentals/components.md)kunt u [de inhoud van de component bewerken](#edit-content). Er wordt vaak een werkbalk weergegeven.

  ![Bewerken, knop](/help/sites-cloud/authoring/assets/editing-component-toolbar-edit.png)

* **Configureren**

  [Afhankelijk van het componenttype](/help/sites-cloud/authoring/fundamentals/components.md)Hiermee kunt u de eigenschappen van de component bewerken en configureren. Er wordt vaak een dialoogvenster geopend.

  ![Knop Configureren](/help/sites-cloud/authoring/assets/editing-component-toolbar-configure.png)

* **Kopiëren**

  Hiermee wordt de component naar het klembord gekopieerd. Na de plakactie, zal de originele component blijven.

  ![Kopiëren, knop](/help/sites-cloud/authoring/assets/editing-component-toolbar-copy.png)

* **Knippen**

  Hiermee wordt de component naar het klembord gekopieerd. Na de plakhandeling wordt de oorspronkelijke component verwijderd.

  ![Knop Knippen](/help/sites-cloud/authoring/assets/editing-component-toolbar-cut.png)

* **Verwijderen**

  Hiermee verwijdert u de component van de pagina met uw bevestiging.

  ![Knop Verwijderen](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **Component invoegen**

  Hiermee wordt het dialoogvenster geopend voor [een nieuwe component toevoegen](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system).

  ![De knop Invoegen](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **Plakken**

  Hiermee wordt de component van het klembord naar de pagina geplakt. Of het origineel overblijft, hangt af van het feit of u de kopie of het knipsel hebt gebruikt.

   * U kunt op dezelfde pagina of op een andere pagina plakken.
   * Het geplakte item wordt boven het item geplakt waar u de plakactie selecteert.
   * De handeling Pate wordt alleen weergegeven als er inhoud op het klembord staat.

  ![Knop Plakken](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

  >[!NOTE]
  >
  >Als u plakt naar een andere pagina die al was geopend vóór de knip-/kopieerbewerking, moet u de pagina vernieuwen om de geplakte inhoud te zien.

* **Groep**

  Hiermee kunt u meerdere componenten tegelijk selecteren. Hetzelfde kan worden bereikt op een desktopapparaat met een **Ctrl+klikken** of **Command+klikken**.

  ![Groeperen, knop](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **Bovenliggend**

  Hiermee kunt u de bovenliggende component van de geselecteerde component selecteren.

  ![Bovenliggende knop](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **Layout**

  Hiermee kunt u de [layout](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) van de geselecteerde component. Dit geldt alleen voor de geselecteerde component en activeert de component [Lay-outmodus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) voor de gehele pagina.

  ![Indeling, knop](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **Omzetten in een ervaringsfragmentvariatie**

  Hiermee kunt u een [ervaren, fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) van de geselecteerde component of voeg het aan een bestaand ervaringsfragment toe.

  ![Omzetten in knop Fragment ervaren](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## Inhoud bewerken {#edit-content}

Er zijn twee methoden om inhoud toe te voegen en/of te bewerken in componenten:

* Open de [dialoogvenster voor bewerking](#component-edit-dialog).
* [Middelen slepen en neerzetten](#drag-and-drop-assets-into-component) vanuit de middelenbrowser om rechtstreeks inhoud toe te voegen.

### Dialoogvenster Component Edit {#component-edit-dialog}

U kunt een component openen om de content te bewerken met het pictogram [Bewerken (potlood) van de werkbalk van de component](#component-toolbar).

De exacte bewerkingsopties zijn afhankelijk van de component. Voor sommige componenten [alle acties zijn alleen beschikbaar in de modus Volledig scherm](#edit-content-full-screen-mode). Bijvoorbeeld:

* Tekstcomponent

  ![Werkbalk van de tekstcomponent](/help/sites-cloud/authoring/assets/editing-text-component-toolbar.png)

* Afbeeldingscomponent

  ![Werkbalk van de afbeeldingscomponent](/help/sites-cloud/authoring/assets/editing-image-component-toolbar.png)

  >[!NOTE]
  >
  >Bewerken werkt niet op een lege afbeeldingscomponent.
  >
  >U moet een afbeelding naar de component slepen of uploaden voordat u deze kunt bewerken.

* Afbeeldingscomponent - volledig scherm

  [Modus Volledig scherm activeren](#edit-content-full-screen-mode) voor de afbeeldingscomponent is er meer ruimte voor het bewerken van de afbeelding en het weergeven van extra bewerkingsopties, zoals **Toewijzing starten** en **Zoomen herstellen**. Bovendien kunt u op het volledige scherm voorinstellingen voor bijsnijden selecteren.

  ![De modus Volledig scherm van de component Image](/help/sites-cloud/authoring/assets/editing-image-component-full-screen.png)

* Componenten die zijn samengesteld uit meerdere basiscomponenten vragen u eerst om te bevestigen welke set bewerkingsopties u wilt:

### Elementen naar component slepen en neerzetten {#drag-and-drop-assets-into-component}

Voor specifieke componenttypen (zoals afbeeldingen) kunt u elementen van de elementenbrowser rechtstreeks naar de component slepen om de inhoud bij te werken.

## Inhoud bewerken in de modus Volledig scherm {#edit-content-full-screen-mode}

Voor alle componenten kunt u de modus Volledig scherm openen (en afsluiten):

![De knop Volledig scherm](/help/sites-cloud/authoring/assets/editing-full-screen.png)

Bijvoorbeeld de **Tekst** component:

![Tekstcomponent op volledig scherm](/help/sites-cloud/authoring/assets/editing-text-full-screen.png)

>[!NOTE]
>
>Voor sommige componenten zal de modus Volledig scherm meer opties beschikbaar hebben dan de standaard interne editor.

## Een component verplaatsen {#moving-a-component}

Een alinea-component verplaatsen:

1. Selecteer de alinea die u wilt verplaatsen met de optie voor selecteren en vasthouden of met klikken en vasthouden.
1. Sleep de alinea naar de nieuwe locatie. AEM geeft aan waar de alinea kan worden geplaatst. Zet het neer op de gewenste plaats.

   ![Een component verplaatsen](/help/sites-cloud/authoring/assets/editing-moving-component.png)

1. Uw alinea wordt verplaatst.

>[!TIP]
>
>U kunt ook [Knippen en plakken](#component-toolbar) een component verplaatsen.

## Componentlay-out bewerken {#edit-component-layout}

In plaats van herhaaldelijk over te schakelen van de bewerkingsmodus naar [de lay-outmodus](/help/sites-cloud/authoring/features/responsive-layout.md) om een component aan te passen, kunt u de actie **Lay-out** selecteren zodat een component de lay-out van die component kan wijzigen en tijd kan besparen door de bewerkingsmodus niet te verlaten.

1. Wanneer in **Bewerken** wijze van de plaatsenconsole, die een component selecteert openbaart de toolbar van de component.

   ![De componentwerkbalk van een pagina-component](/help/sites-cloud/authoring/assets/editing-layout-toolbar.png)

   Selecteer de **Layout** actie om de lay-out van de component aan te passen.

   ![De knop Lay-out van de componentwerkbalk](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

1. Nadat de handeling Lay-out is geselecteerd:

   * De formaatgrepen voor de componentweergave.
   * De emulatorwerkbalk wordt boven in het scherm weergegeven.
   * De acties van de lay-out in plaats van de standaard geeft acties uit tonen op de componententoolbar.

   ![Een component in de lay-outmodus](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   U kunt nu de lay-out van de component wijzigen zoals u zou doen binnen [lay-outmodus](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

1. Klik op de knop **Sluiten** in het actiemenu van de component om het wijzigen van de lay-out van de component op te houden. De werkbalk van de component keert terug naar de normale bewerkingsstatus.

   ![De componentwerkbalk van een pagina-component](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>De actie Lay-out is beperkt in werkingsgebied tot de geselecteerde component. Als u bijvoorbeeld de lay-out van een component bewerkt en vervolgens op een andere component klikt, wordt de werkbalk voor standaardbewerking (niet de layoutwerkbalk) weergegeven voor de zojuist geselecteerde component en verdwijnen de formaatgrepen en de emulatorwerkbalk.
>
>Als u de algemene lay-out van de pagina moet bewerken, wat van invloed is op meerdere componenten, schakelt u over naar de [lay-outmodus](/help/sites-cloud/authoring/features/responsive-layout.md).

## Overgenomen componenten {#inherited-components}

Overerving is het mechanisme waarbij inhoud automatisch van de ene component naar de andere kan worden verplaatst. Overerfde componenten kunnen het product van diverse scenario&#39;s zijn, die omvatten:

* [Beheer van meerdere sites](/help/sites-cloud/administering/msm/overview.md)
* [Starten](/help/sites-cloud/authoring/launches/overview.md) (indien gebaseerd op live kopie).

U kunt de overerving annuleren (en vervolgens opnieuw inschakelen). Afhankelijk van de component kan deze beschikbaar zijn op de werkbalk van de component als de component zich op een pagina bevindt die deel uitmaakt van een live kopie of opstart (op basis van een live kopie).

![Een componentwerkbalk met de overervingsrelatie](/help/sites-cloud/authoring/assets/editing-component-toolbar-inheritance.png)

Bijvoorbeeld:

* Overerving annuleren

  ![Overerving annuleren, knop](/help/sites-cloud/authoring/assets/editing-cancel-inheritance.png)

* Overerving opnieuw inschakelen (als overerving al is geannuleerd)

  ![Knop Overerving opnieuw inschakelen](/help/sites-cloud/authoring/assets/editing-reenable-inheritance.png)

* De handeling Uitvoeren is ook beschikbaar in de blauwdruk of de bron van Actieve kopie

  ![De knop Uitvoeren](/help/sites-cloud/authoring/assets/editing-rollout.png)

## De paginasjabloon bewerken {#editing-the-page-template}

U kunt eenvoudig overschakelen naar de [sjablooneditor](/help/sites-cloud/authoring/features/templates.md#editing-templates-template-authors) door **Sjabloon bewerken** te selecteren in het menu [Pagina-informatie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information).

U kunt gemakkelijk zien op welke sjabloon de pagina is gebaseerd wanneer u de pagina selecteert in de [kolomweergave](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) of de [lijstweergave](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view).

## Status van live kopiëren {#live-copy-status}

De [De paginamodus Actieve kopie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) Hiermee kunt u snel een overzicht geven van de status van de live kopie en van de onderdelen die u wel of niet wilt overnemen:

* Groene rand: Overgenomen
* Roze rand: overerving is geannuleerd

Bijvoorbeeld:

![Voorbeeld van live kopieerstatus die wordt weergegeven](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## Annotaties toevoegen {#adding-annotations}

[Annotaties](/help/sites-cloud/authoring/fundamentals/annotations.md) revisoren en andere auteurs feedback geven over uw inhoud. Ze worden vaak gebruikt voor controle- en validatiedoeleinden.

## Pagina&#39;s voorvertonen {#previewing-pages}

Er zijn twee opties voor het voorvertonen van een pagina:

* [Voorvertoningsmodus](#preview-mode) - een snelle voorvertoning op locatie
* [Weergeven als gepubliceerd](#view-as-published) - een volledige voorvertoning waarmee de pagina in een nieuw tabblad wordt geopend

>[!TIP]
>
>* Koppelingen in de inhoud zijn zichtbaar, maar niet toegankelijk in de bewerkingsmodus.
>* Gebruik een van de voorvertoningsopties als u door de koppelingen wilt navigeren.
>* Gebruik de [sneltoets](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M` om te schakelen tussen de voorvertoning en de laatst geselecteerde modus.

>[!NOTE]
>
>Het WCM-modencookie wordt ingesteld voor beide voorvertoningsopties.

### Voorvertoningsmodus {#preview-mode}

Wanneer u inhoud bewerkt, kunt u een voorvertoning van de pagina weergeven met behulp van de voorvertoning [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes). Deze modus:

* Hiermee verbergt u verschillende bewerkingsmechanismen waarmee u snel kunt zien hoe de pagina er bij het publiceren uitziet.
* Hiermee kunt u navigeren met koppelingen.
* doet **niet** Vernieuw de pagina-inhoud.

Tijdens het ontwerpen is de voorvertoningsmodus beschikbaar met het pictogram rechtsboven in de pagina-editor:

![Knop Voorvertoning](/help/sites-cloud/authoring/assets/preview.png)

### Weergeven als gepubliceerd {#view-as-published}

De **Weergeven als gepubliceerd** Deze optie is beschikbaar via de [Pagina-informatie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) -menu. Hierdoor wordt de pagina op een nieuw tabblad geopend, wordt de inhoud vernieuwd en wordt de pagina precies zo weergegeven als in de publicatieomgeving.

## Een pagina vergrendelen {#locking-a-page}

AEM kunt u een pagina vergrendelen, zodat niemand anders de inhoud kan bewerken. Deze vergrendeling is handig wanneer u meerdere bewerkingen op een bepaalde pagina uitvoert of wanneer u een pagina kort wilt stilzetten.

Een pagina kan worden vergrendeld vanuit:

* **Sites** console

   1. Selecteer de pagina met [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
   1. Selecteer het slotpictogram.

      ![Knop Vergrendelen](/help/sites-cloud/authoring/assets/lock.png)

* **Pagina-editor**

   1. Selecteer de **Pagina-informatie** om het menu te openen.
   1. Selecteer de **Pagina vergrendelen** -optie.

Nadat de weergave op de console is vergrendeld, wordt de informatie bijgewerkt en wanneer u een vergrendelingssymbool bewerkt, wordt deze weergegeven op de werkbalk.

![Voorbeeld van een vergrendelde pagina](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer u een gebruiker imiteert. Een pagina die op deze manier is vergrendeld, kan echter alleen worden ontgrendeld (door klanten) met behulp van de gebruiker die als imitatie is opgetreden.
>
>Pagina&#39;s kunnen niet worden ontgrendeld door zich voor te doen als de gebruiker die de pagina heeft vergrendeld.
>
>Als de gebruiker die de pagina heeft vergrendeld niet beschikbaar is om de pagina te ontgrendelen, neemt u contact op met de Klantenondersteuning om de opties voor het verwijderen van de vergrendeling te evalueren.

## Een pagina ontgrendelen {#unlocking-a-page}

Het ontgrendelen van een pagina lijkt veel op [de pagina vergrendelen](#locking-a-page). Nadat de pagina is vergrendeld, worden de vergrendelingsopties vervangen door ontgrendelingsacties.

In het menu Pagina-informatie wordt **Ontgrendelen** als optie weergegeven en het pictogram Vergrendelen in de Sites-console wordt vervangen door een pictogram **Ontgrendelen**.

![Knop Ontgrendelen](/help/sites-cloud/authoring/assets/unlock.png)

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

![De knoppen Ongedaan maken en Opnieuw](/help/sites-cloud/authoring/assets/redo.png)

>[!TIP]
>
>* De [sneltoets](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Z` is ook beschikbaar voor het ongedaan maken van paginabewerkingsacties.
>* De sneltoets `Ctrl-Y` is ook beschikbaar voor het opnieuw uitvoeren van paginabewerkingsacties.

>[!NOTE]
>
>Zie [Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie](#undoing-and-redoing-page-edits-the-theory) voor de volledige details van wat mogelijk is wanneer het ongedaan maken van en het opnieuw doen van paginaedetingen.

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie {#undoing-and-redoing-page-edits-the-theory}

AEM slaat een geschiedenis van acties op die u uitvoert en de opeenvolging waarin u hen uitvoerde zodat u veelvoudige acties in de orde ongedaan kunt maken dat u hen uitvoerde en hen opnieuw doet om één of meerdere acties indien nodig opnieuw toe te passen.

Als een element op de inhoudspagina wordt geselecteerd (zoals een tekstcomponent), dan is het ongedaan maken en opnieuw bevel op het geselecteerde punt van toepassing.

Het gedrag van de opdrachten Ongedaan maken en Opnieuw is vergelijkbaar met dat van andere software. Gebruik de opdrachten om de recente status van uw webpagina te herstellen terwijl u beslissingen neemt over de inhoud. Als u bijvoorbeeld een tekstalinea naar een andere locatie op de pagina verplaatst, kunt u de opdracht Ongedaan maken gebruiken om de alinea terug te verplaatsen. Als u vervolgens besluit dat de vorige positie beter was, gebruikt u de opdracht Opnieuw uitvoeren om de bewerking Ongedaan maken ongedaan te maken.

U kunt bijvoorbeeld:

* Voer handelingen opnieuw uit zolang u geen paginabewerking hebt uitgevoerd nadat u Ongedaan maken hebt gebruikt.
* U kunt maximaal 20 bewerkingen ongedaan maken (standaardinstelling).
* Ook gebruiken [Sneltoetsen](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) voor ongedaan maken en opnieuw uitvoeren.

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
