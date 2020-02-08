---
title: Pagina's publiceren
description: Pagina's publiceren en verwijderen met AEM
translation-type: tm+mt
source-git-commit: e88a814a901d7fa0da2675fa6017c66d61a73445

---


# Pagina&#39;s publiceren {#publishing-pages}

Nadat u de inhoud hebt gemaakt en gecontroleerd in de auteursomgeving, [stelt u deze beschikbaar op uw openbare website](/help/sites-cloud/authoring/getting-started/concepts.md) (uw publicatieomgeving).

Dit wordt bedoeld als het publiceren van een pagina. Wanneer u een pagina uit het publicatiemilieu wilt verwijderen wordt bedoeld unpublishing. Wanneer u de pagina publiceert en publiceert, blijft deze beschikbaar in de ontwerpomgeving voor verdere wijzigingen totdat u de pagina verwijdert.

U kunt een pagina direct of op een vooraf gedefinieerde datum/tijd publiceren of verwijderen.

##  Terminologie {#terminology}

Tijdens het werken met AEM kunnen er verschillende termen voorkomen die betrekking hebben op publiceren.

* **Publiceren/Publiceren ongedaan maken**
   * Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
   * Dit zijn de termen die worden gebruikt in AEM-documentatie.
* **Activeren/deactiveren**
   * Deze termen zijn synoniem met publiceren/verwijderen.
   * Deze termen zijn gebruikt in eerdere versies van AEM.
* **Replicatie/replicatie**
   * Dit zijn de technische termen die de verplaatsing van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikersopmerkingen) van de ene omgeving naar de andere beschrijven wanneer u een pagina publiceert.
   * Deze termen worden vooral gebruikt door ontwikkelaars.

## Pagina&#39;s publiceren {#publishing-pages-1}

Afhankelijk van uw locatie kunt u publiceren:

* [Vanuit de paginaeditor](#publishing-from-the-editor)
* [Van de plaatsenconsole](#publishing-from-the-console)

>[!NOTE]
>
>Als u niet over de vereiste rechten voor het publiceren van een specifieke pagina beschikt:
>
>* Er wordt een workflow gestart om de juiste persoon op de hoogte te stellen van uw verzoek om te publiceren.
>* Deze workflow is mogelijk aangepast door uw ontwikkelingsteam.
>* Er wordt kort een bericht weergegeven om u te laten weten dat de workflow is geactiveerd.

<!--
>* This [workflow may have been customized](/help/sites-developing/workflows-models.md#main-pars-procedure-6fe6) by your development team.
>* A message will be displayed briefly to notify you that the workflow was triggered.
-->

### Publiceren vanuit de Editor {#publishing-from-the-editor}

Als u een pagina bewerkt, kunt u deze rechtstreeks vanuit de editor publiceren.

1. Selecteer het pictogram **Pagina-informatie** om het menu te openen en klik vervolgens op de optie **Pagina** publiceren.

   ![Pagina&#39;s publiceren via paginaopties](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Afhankelijk van het feit of de pagina verwijzingen bevat die moeten worden gepubliceerd:

   * De pagina wordt rechtstreeks gepubliceerd als er geen referenties zijn die moeten worden gepubliceerd.
   * Als de pagina verwijzingen heeft die moeten publiceren, zullen deze in de **Publish** tovenaar worden vermeld, waar u of kunt:
      * Geef aan welke elementen/tags/etc. Als u samen met de pagina wilt publiceren, gebruikt u **Publiceren** om het proces te voltooien.
      * Gebruik **Annuleren** om de handeling af te breken.
   ![Referenties publiceren met de pagina](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Als u **Publiceren** selecteert, wordt de pagina gekopieerd naar de publicatieomgeving. In de paginaeditor wordt een informatiebanner weergegeven die de publicatieactie bevestigt.

   ![Statusinformatiebanner publiceren](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wanneer u dezelfde pagina in de console weergeeft, is de bijgewerkte publicatiestatus zichtbaar.

   ![De publicatiestatus van de pagina in kolomweergave in de siteconsole](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Publiceren vanuit de editor is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina(&#39;s) wordt/worden gepubliceerd en onderliggende pagina(&#39;s) niet.

### Publiceren vanuit de console {#publishing-from-the-console}

In de siteconsole zijn er twee opties voor publiceren:

* [Snel publiceren](#quick-publish)
* [Publicatie beheren](#manage-publication)

#### Snel publiceren {#quick-publish}

**Snel publiceren** is voor eenvoudige gevallen en publiceert de geselecteerde pagina(&#39;s) direct zonder verdere interactie. Daarom worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

Een pagina publiceren met Snel publiceren:

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Snel publiceren** .

   ![Pagina&#39;s selecteren voor publicatie](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Bevestig de publicatie in het dialoogvenster Snel publiceren door te klikken op **Publiceren** of Annuleren door te klikken op **Annuleren**. Onthoud dat niet-gepubliceerde verwijzingen automatisch ook worden gepubliceerd.

   ![Snelle publicatiebevestiging](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Wanneer de pagina wordt gepubliceerd, wordt een waarschuwing getoond die de publicatie bevestigt.

>[!NOTE]
>
>Snel publiceren is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina(&#39;s) wordt/worden gepubliceerd en onderliggende pagina&#39;s niet.

#### Publicatie beheren {#manage-publication}

**Publicatie** beheren biedt meer opties dan Snel publiceren, waardoor onderliggende pagina&#39;s kunnen worden opgenomen, de referenties kunnen worden aangepast en toepasselijke workflows kunnen worden gestart en de optie kan worden geboden om op een latere datum te publiceren.

Een pagina publiceren of de publicatie ervan ongedaan maken met Publicatie beheren:

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop Publicatie **beheren** .

   ![Pagina&#39;s selecteren voor publicatie](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. De wizard **Publicatie** beheren wordt gestart. In de eerste stap, **Opties**, kunt u:

   * Kies of u de geselecteerde pagina&#39;s wilt publiceren of de publicatie ervan ongedaan wilt maken.
   * Kies of u deze handeling nu of op een latere datum wilt uitvoeren.
   Als u later publiceert, wordt een workflow gestart om de geselecteerde pagina of pagina&#39;s op het opgegeven tijdstip te publiceren. Als u de publicatie later ongedaan maakt, wordt een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald moment ongedaan te maken.

   Als u een publicatie/publicatie later wilt annuleren, gaat u naar de workflowconsole om de bijbehorende workflow te beëindigen. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

   Klik op **Volgende** om door te gaan.

1. In de volgende stap van de wizard Publicatie beheren, **Bereik**, kunt u het bereik van de publicatie/niet-publicatie definiëren, zoals het opnemen van onderliggende pagina&#39;s en/of het opnemen van referenties.

   ![Publicatiebereik beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   U kunt de knop Inhoud **** toevoegen gebruiken om extra pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die moeten worden gepubliceerd voor het geval u deze niet hebt geselecteerd voordat u de wizard Publicatie beheren start.

   Klik op de knop Inhoud toevoegen om de [padbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) te starten en de inhoud te selecteren.

   Selecteer de vereiste pagina&#39;s en klik vervolgens op **Selecteren** om de inhoud aan de wizard toe te voegen of op **Annuleren **om de selectie te annuleren en terug te keren naar de wizard.

   Terug in de tovenaar, kunt u een punt in de lijst selecteren om zijn verdere opties zoals te vormen:

   * Inclusief de onderliggende elementen.
   * Verwijder het uit de selectie.
   * De gepubliceerde referenties beheren.
   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   Klik op **Inclusief onderliggende items** om een dialoogvenster te openen waarin u:

   * Alleen directe kinderen opnemen.
   * Alleen gewijzigde pagina&#39;s opnemen.
   * Alleen al gepubliceerde pagina&#39;s opnemen.
   Klik op **Toevoegen** om de onderliggende pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die gepubliceerd of niet gepubliceerd moeten worden op basis van de selectieopties. Klik op **Annuleren** om de selectie te annuleren en terug te keren naar de wizard.

   ![Publicatie beheren, waaronder kinderen](/help/sites-cloud/authoring/assets/publishing-include-children.png)

   Als u terugkeert naar de wizard, ziet u de toegevoegde pagina&#39;s op basis van uw keuze voor opties in het dialoogvenster Inclusief onderliggende items.

   U kunt de te publiceren of ongepubliceerde verwijzingen voor een pagina bekijken en wijzigen door het te selecteren en dan de **Gepubliceerde knoop van Verwijzingen** te klikken.

   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   In het dialoogvenster **Gepubliceerde verwijzingen** worden de referenties voor de geselecteerde inhoud weergegeven. Standaard zijn ze allemaal geselecteerd en worden ze gepubliceerd/niet gepubliceerd, maar u kunt de selectie van ze opheffen, zodat ze niet worden opgenomen in de handeling.

   Klik op **Gereed** om de wijzigingen op te slaan of op **Annuleren** om de selectie te annuleren en terug te keren naar de wizard.

   In de wizard wordt de kolom **Verwijzingen** bijgewerkt met de verwijzingen die u hebt geselecteerd om te publiceren of ongepubliceerd.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Klik op **Publiceren** om te voltooien.

   Terug in de plaatsenconsole zal een berichtbericht de publicatie bevestigen.

1. Als de gepubliceerde pagina&#39;s aan werkschema&#39;s worden geassocieerd, kunnen zij in een definitieve stap van de **Werkschema** van de publicatietovenaar worden getoond.

   >[!NOTE]
   >
   >De stap **Workflows** wordt weergegeven op basis van de rechten die de gebruiker heeft of niet. Zie de vorige opmerking op deze pagina over publicatiebevoegdheden en het beheren van toegang tot workflows en het [toepassen van workflows op pagina](/help/sites-cloud/authoring/workflows/applying.md) &#39;s voor meer informatie.
   <!--
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as [Managing Access to Workflows](/help/sites-administering/workflows-managing.md) and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   -->

   De bronnen worden gegroepeerd op basis van de workflows die worden geactiveerd en elke optie heeft de volgende opties:

   * Definieer de titel van de workflow.
   * Behoud het workflowpakket, mits de workflow ondersteuning biedt voor meerdere bronnen. <!--Keep the workflow package, provided that the workflow has [multi-resource support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).-->
   * Definieer een titel van het workflowpakket als de optie om het workflowpakket te behouden is gekozen.
   Klik op **Publiceren** of Later **** publiceren om de publicatie te voltooien.

## Publicatie van pagina&#39;s ongedaan maken {#unpublishing-pages}

Als u de publicatie van een pagina ongedaan maakt, wordt deze verwijderd uit uw publicatieomgeving, zodat deze niet langer beschikbaar is voor uw lezers.

Op een [manier die vergelijkbaar is met publiceren](#publishing-pages), kunnen een of meer pagina&#39;s niet worden gepubliceerd:

* [Vanuit de paginaeditor](#unpublishing-from-the-editor)
* [Van de plaatsenconsole](#unpublishing-from-the-console)

### Publicatie ongedaan maken vanuit de Editor {#unpublishing-from-the-editor}

Als u een pagina bewerkt en de publicatie van die pagina ongedaan wilt maken, selecteert u **Publicatie van pagina** ongedaan maken in het menu **Pagina-informatie** , net zoals u de pagina [zou](#publishing-from-the-editor)publiceren.

### Publicatie ongedaan maken vanuit de console {#unpublishing-from-the-console}

Net zoals u de optie Publicatie beheren [gebruikt om te publiceren](#manage-publication), kunt u deze ook gebruiken om de publicatie ongedaan te maken.

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop Publicatie **beheren** .
1. De wizard **Publicatie** beheren wordt gestart. In de eerste stap, **Opties**, selecteer om **Unpublish** in plaats van de standaardoptie van **Publiceren** te schrappen.

   ![Publiceren ongedaan maken](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Net zoals later met publiceren een workflow wordt gestart om deze versie van de pagina op het opgegeven tijdstip te publiceren, wordt later met deactiveren een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald tijdstip ongedaan te maken.

   Als u een publicatie/publicatie later wilt annuleren, gaat u naar de workflowconsole om de bijbehorende workflow te beëindigen. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

1. Als u de niet-publicatie wilt voltooien, gaat u door met de wizard zoals u de pagina [wilt](#manage-publication)publiceren.

## Een boomstructuur publiceren en de publicatie ervan opheffen {#publishing-and-unpublishing-a-tree}

Wanneer u een aanzienlijk aantal inhoudspagina&#39;s hebt ingevoerd of bijgewerkt - die allen onder de zelfde wortelpagina ingezeten zijn - kan het gemakkelijker zijn om de volledige boom in één actie te publiceren.

Hiervoor kunt u de optie Publicatie [](#manage-publication) beheren op de siteconsole gebruiken.

1. Selecteer in de siteconsole de hoofdpagina van de boomstructuur die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken, en selecteer Publicatie **beheren**.
1. De wizard **Publicatie** beheren wordt gestart. Kies of u wilt publiceren of de publicatie ongedaan wilt maken en wanneer dit moet gebeuren en selecteer **Volgende** om door te gaan.
1. Selecteer in de stap **Bereik** de basispagina en selecteer **Onderliggende** elementen opnemen.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Schakel in het dialoogvenster Onderliggende **items** opnemen de opties uit:

   * Alleen directe kinderen opnemen
   * Alleen reeds gepubliceerde pagina&#39;s opnemen
   Deze opties zijn standaard geselecteerd, dus u moet niet vergeten deze te deselecteren. Klik op **Toevoegen** om de inhoud te bevestigen en toe te voegen aan de publicatie/niet-publicatie.

   ![Inclusief kinderen tijdens niet-publiceren](/help/sites-cloud/authoring/assets/publishing-tree-children.png)

1. De wizard **Publicatie** beheren geeft een overzicht van de inhoud van de structuur die u wilt controleren. U kunt de selectie verder aanpassen door extra pagina&#39;s toe te voegen of geselecteerde pagina&#39;s te verwijderen.

   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-tree-select.png)

   U kunt ook de verwijzingen controleren die via de optie **Gepubliceerde verwijzingen** moeten worden gepubliceerd.

1. [Ga verder met de normale](#manage-publication) wizard Publicatie beheren om de publicatie of publicatie van de boomstructuur te voltooien.

## Publicatiestatus bepalen {#determining-publication-status}

U kunt de publicatiestatus van een pagina bepalen:

* In de informatie van het [middeloverzicht over de plaatsenconsole](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   ![Status van publicatie in de kaartweergave](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   De publicatiestatus wordt weergegeven in [kaart](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view)-, [kolom](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view)- en [lijstweergaven](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) in de siteconsole.

* In de [tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![Status van publicatie in tijdlijnweergave](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* In het menu [](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) Pagina-informatie wanneer u een pagina bewerkt

   ![Status van publicatie in het menu Pagina-informatie](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
