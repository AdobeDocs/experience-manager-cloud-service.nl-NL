---
title: Pagina's publiceren
description: Pagina's publiceren en verwijderen met AEM
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
source-git-commit: 232ef0198888e55806bd1358d12829035c140c75
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 5%

---

# Pagina&#39;s publiceren {#publishing-pages}

Nadat u de inhoud in de ontwerpomgeving hebt gemaakt en gecontroleerd, wilt u deze [beschikbaar maken op uw openbare website](/help/sites-cloud/authoring/getting-started/concepts.md) (uw publicatieomgeving).

Dit wordt bedoeld als het publiceren van een pagina. Wanneer u een pagina uit het publicatiemilieu wilt verwijderen wordt bedoeld unpublishing. Wanneer u de pagina publiceert en publiceert, blijft deze beschikbaar in de ontwerpomgeving voor verdere wijzigingen totdat u de pagina verwijdert.

U kunt een pagina direct of op een vooraf gedefinieerde datum/tijd publiceren of verwijderen.

## Terminologie {#terminology}

Tijdens het werken met Adobe Experience Manager (AEM) als Cloud Service kunnen er verschillende termen voorkomen die betrekking hebben op publiceren.

* **Publiceren/Publiceren ongedaan maken**
   * Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
   * Dit zijn de termen die worden gebruikt in AEM documentatie.
* **Activeren/deactiveren**
   * Deze termen zijn synoniem met publiceren/verwijderen.
   * Deze termen zijn in vorige versies van AEM gebruikt.
* **Replicatie/replicatie**
   * Dit zijn de technische termen die de verplaatsing van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikersopmerkingen) van de ene omgeving naar de andere beschrijven wanneer u een pagina publiceert.
   * Deze termen worden vooral gebruikt door ontwikkelaars.

## Pagina&#39;s publiceren {#publishing-pages-1}

Afhankelijk van uw locatie kunt u publiceren:

* [Vanuit de pagina-editor](#publishing-from-the-editor)
* [Van de plaatsenconsole](#publishing-from-the-console)

>[!NOTE]
>
>Als u niet over de vereiste rechten voor het publiceren van een specifieke pagina beschikt:
>
>* Er wordt een workflow gestart om de juiste persoon op de hoogte te stellen van uw verzoek om te publiceren.
>* Deze workflow is mogelijk aangepast door uw ontwikkelingsteam.
>* Er wordt kort een bericht weergegeven om u te laten weten dat de workflow is geactiveerd.


>[!NOTE]
>
> Zie **On Time** en **Off Time** op het tabblad [Standaard van Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic) voor meer mogelijkheden

### Publiceren vanuit de Editor {#publishing-from-the-editor}

Als u een pagina bewerkt, kunt u deze rechtstreeks vanuit de editor publiceren.

1. Selecteer het pictogram **Pagina-informatie** om het menu te openen en selecteer vervolgens de optie **Pagina publiceren**.

   ![Pagina&#39;s publiceren via paginaopties](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Afhankelijk van het feit of de pagina verwijzingen bevat die moeten worden gepubliceerd:

   * De pagina wordt rechtstreeks gepubliceerd als er geen referenties zijn die moeten worden gepubliceerd.
   * Als de pagina verwijzingen heeft die het publiceren vereisen, zullen deze in **Publish** tovenaar worden vermeld, waar u of kunt:
      * Geef aan welke elementen/tags/etc. Als u samen met de pagina wilt publiceren, gebruikt u **Publiceren** om het proces te voltooien.
      * Gebruik **Annuleren** om de handeling af te breken.

   ![Referenties publiceren met de pagina](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Als u **Publiceren** selecteert, wordt de pagina naar de publicatieomgeving gekopieerd. In de paginaeditor wordt een informatiebanner weergegeven die de publicatieactie bevestigt.

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

**Quick** Publishing voor eenvoudige gevallen en publiceert de geselecteerde pagina(&#39;s) direct zonder verdere interactie. Daarom worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

Een pagina publiceren met Snel publiceren:

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Snel publiceren**.

   ![Pagina&#39;s selecteren voor publicatie](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Bevestig in het dialoogvenster Snel publiceren de publicatie door te klikken op **Publiceren** of Annuleren door te klikken op **Annuleren**. Onthoud dat niet-gepubliceerde verwijzingen automatisch ook worden gepubliceerd.

   ![Snelle publicatiebevestiging](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Wanneer de pagina wordt gepubliceerd, wordt een waarschuwing getoond die de publicatie bevestigt.

>[!NOTE]
>
>Snel publiceren is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina(&#39;s) wordt/worden gepubliceerd en onderliggende pagina&#39;s niet.

#### Publicatie beheren {#manage-publication}

**Het beheren van** Publicatie biedt meer opties dan  **Snelle Publicatie**, die voor de opneming van kindpagina&#39;s, aanpassing van de verwijzingen, en het beginnen van om het even welke toepasselijke werkschema&#39;s toestaat evenals de optie om op een recentere datum te publiceren.

Een pagina publiceren of de publicatie ervan ongedaan maken met Publicatie beheren:

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Publicatie beheren**.

   ![Pagina&#39;s selecteren voor publicatie](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. De wizard **Publicatie beheren** wordt gestart. In de eerste stap, **Options**, kunt u:

   * **Actie**

      Kies of u de geselecteerde pagina&#39;s wilt publiceren of de publicatie ervan ongedaan wilt maken.

   * **Planning**

      Kies of u deze handeling nu of op een latere datum wilt uitvoeren.

      Als u later publiceert, wordt een workflow gestart om de geselecteerde pagina of pagina&#39;s op het opgegeven tijdstip te publiceren. Als u de publicatie later ongedaan maakt, wordt een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald moment ongedaan te maken.

      >[!NOTE]
      >
      >Als u een publicatie/unpublish later wilt annuleren, gaat u naar [Workflowconsole](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) om de corresponderende workflow te beëindigen.
   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. Klik **Volgende** om door te gaan.

1. In de volgende stap van de Manage tovenaar van de Publicatie, **Scope**, kunt u het werkingsgebied van de publicatie/unpublication bepalen zoals het omvatten van kindpagina&#39;s en/of het omvatten van verwijzingen.

   ![Publicatiebereik beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **Inhoud toevoegen**

   U kunt de knop **Inhoud toevoegen** gebruiken om extra pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die moeten worden gepubliceerd voor het geval u deze niet hebt geselecteerd voordat u de wizard Publicatie beheren start.

   Als u de knop **Inhoud toevoegen** selecteert, wordt de [padbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) gestart om het selecteren van inhoud toe te staan.

   Selecteer de vereiste pagina&#39;s en klik dan **Select** om de inhoud aan de tovenaar toe te voegen of **Cancel** om de selectie te annuleren en aan de tovenaar terug te keren.

   **Selectie verwijderen**

   U kunt vervolgens weer in de wizard een item in de lijst selecteren om het item uit de selectie te verwijderen.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Gepubliceerde verwijzingen**

   U kunt de te publiceren verwijzingen of unpublished voor een pagina bekijken en wijzigen door het te selecteren en dan de **Gepubliceerde Verwijzingen** knoop te klikken.

   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   In het dialoogvenster **Gepubliceerde verwijzingen** worden de referenties voor de geselecteerde inhoud weergegeven. Standaard zijn ze allemaal geselecteerd en worden ze gepubliceerd/niet gepubliceerd, maar u kunt de selectie van ze opheffen, zodat ze niet worden opgenomen in de handeling.

   Klik **Done** om uw wijzigingen op te slaan of **Cancel** om de selectie te annuleren en terug te keren naar de wizard.

   In de wizard wordt de kolom **References** bijgewerkt om de selectie van te publiceren of ongepubliceerde verwijzingen weer te geven.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Inclusief onderliggende items**

   >[!NOTE]
   >
   >Zie [Een structuur publiceren en verwijderen](#publishing-and-unpublishing-a-tree)

   Als u op **Inclusief onderliggende elementen** klikt, wordt een dialoogvenster geopend waarin u:

   * **Inclusief kinderen**
   * **Alleen directe kinderen opnemen**
   * **Alleen gewijzigde pagina&#39;s opnemen**
   * **Alleen reeds gepubliceerde pagina&#39;s opnemen**

   Activeer de vereiste opties en bevestig deze met **OK** om de onderliggende pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die gepubliceerd of ongepubliceerd moeten worden op basis van de selectieopties. Klik **Annuleren** om de selectie te annuleren en terug te keren naar de wizard.

   ![Publicatie beheren, waaronder kinderen](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. Klik **Publiceren** om te voltooien.

   Terug in de plaatsenconsole zal een berichtbericht de publicatie bevestigen.

1. Als de gepubliceerde pagina&#39;s aan werkschema&#39;s worden geassocieerd, kunnen zij in een definitieve **Werkschema** stap van de publicatietovenaar worden getoond.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png)

   >[!NOTE]
   >
   >De stap **Workflows** wordt weergegeven op basis van de rechten die de gebruiker kan hebben of niet. Zie de vorige notitie op deze pagina met betrekking tot publicatiebevoegdheden en het beheren van toegang tot werkstromen en [Workflows toepassen op pagina&#39;s](/help/sites-cloud/authoring/workflows/applying.md) voor meer informatie.

   De bronnen worden gegroepeerd op basis van de workflows die worden geactiveerd en elke optie heeft de volgende opties:

   * Definieer de titel van de workflow.
   * Behoud het workflowpakket, mits de workflow ondersteuning biedt voor meerdere bronnen.
   * Definieer een titel van het workflowpakket als de optie om het workflowpakket te behouden is gekozen.

1. Klik op **Publiceren** of **Later publiceren** om de publicatie te voltooien.

## Publicatie van pagina&#39;s ongedaan maken {#unpublishing-pages}

Als u de publicatie van een pagina ongedaan maakt, wordt deze verwijderd uit uw publicatieomgeving, zodat deze niet langer beschikbaar is voor uw lezers.

Op een [manier gelijkend op het publiceren](#publishing-pages), kunnen één of meerdere pagina&#39;s unpublished:

* [Vanuit de pagina-editor](#unpublishing-from-the-editor)
* [Van de plaatsenconsole](#unpublishing-from-the-console)

### Publicatie ongedaan maken vanuit de Editor {#unpublishing-from-the-editor}

Als u de publicatie van een pagina ongedaan wilt maken, selecteert u **Publicatie van pagina** ongedaan maken in het menu **Pagina-informatie**, net als wanneer u de pagina](#publishing-from-the-editor) zou publiceren.[

### Publicatie ongedaan maken vanuit de console {#unpublishing-from-the-console}

Net zoals u [de optie Publicatie beheren gebruikt om te publiceren](#manage-publication), kunt u deze ook gebruiken om de publicatie ongedaan te maken.

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Publicatie beheren**.
1. De wizard **Publicatie beheren** wordt gestart. In de eerste stap, bij **Opties**, selecteert u **Publicatie ongedaan maken** in plaats van de standaardoptie **Publiceren**.

   ![Unpublishing - Opties](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Net zoals later met publiceren een workflow wordt gestart om deze versie van de pagina op het opgegeven tijdstip te publiceren, wordt later met deactiveren een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald tijdstip ongedaan te maken.

   >[!NOTE]
   >
   >Als u een publicatie/unpublish later wilt annuleren, gaat u naar [Workflowconsole](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) om de corresponderende workflow te beëindigen.

1. Als u de niet-publicatie wilt voltooien, gaat u door met de wizard zoals u de pagina [publiceert.](#manage-publication)

   ![Unpublishing - Scope](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Een boomstructuur publiceren en de publicatie ervan opheffen {#publishing-and-unpublishing-a-tree}

Wanneer u een aanzienlijk aantal inhoudspagina&#39;s hebt ingevoerd of bijgewerkt - die allen onder de zelfde wortelpagina ingezeten zijn - kan het gemakkelijker zijn om de volledige boom in één actie te publiceren.

U kunt de [Publicatie beheren](#manage-publication) optie op de plaatsenconsole gebruiken om dit te doen.

1. Selecteer in de siteconsole de basispagina van de boomstructuur die u wilt publiceren of verwijderen en selecteer **Publicatie beheren**.
1. De wizard **Publicatie beheren** wordt gestart. Kies of u wilt publiceren of de publicatie ongedaan wilt maken en wanneer dit moet gebeuren en selecteer **Volgende** om door te gaan.
1. Selecteer in de stap **Bereik** de hoofdpagina en selecteer **Inclusief onderliggende elementen**.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. In het dialoogvenster **Inclusief onderliggende elementen**:

   * Selecteer **Inclusief onderliggende elementen**
   * **Alleen directe onderliggende elementen opnemen** uitschakelen
   * **Alleen reeds gepubliceerde pagina&#39;s opnemen** uitschakelen
   * configureren **Alleen gewijzigde pagina&#39;s opnemen** naar wens

   Deze opties zijn standaard geselecteerd, dus u moet eraan denken om ze te configureren. Bevestig de selectie met **OK** om de inhoud toe te voegen aan de publicatie/unpublicatie.

   ![Inclusief onderliggende elementen voor boompublicatie](/help/sites-cloud/authoring/assets/publishing-include-children-tree.png)

1. In de wizard **Publicatie beheren** kunt u de selectie verder aanpassen door extra pagina&#39;s toe te voegen of de geselecteerde pagina&#39;s te verwijderen.

   Herinner dat u de verwijzingen kunt ook herzien die via **Gepubliceerde Verwijzingen** optie moeten worden gepubliceerd.

1. [Ga als ](#manage-publication) normaal verder met de wizard Publicatie beheren om de publicatie of publicatie van de boomstructuur te voltooien.

## Publicatiestatus bepalen {#determining-publication-status}

U kunt de publicatiestatus van een pagina bepalen:

* In de [informatie van het middeloverzicht op de plaatsenconsole](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   ![Status van publicatie in de kaartweergave](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   De publicatiestatus wordt weergegeven in [kaart](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view)-, [kolom](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view)- en [lijstweergaven](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) in de Sites-console.

* In de [tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![Status van publicatie in tijdlijnweergave](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* In het menu [Pagina-informatie](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) wanneer u een pagina bewerkt

   ![Status van publicatie in het menu Pagina-informatie](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
