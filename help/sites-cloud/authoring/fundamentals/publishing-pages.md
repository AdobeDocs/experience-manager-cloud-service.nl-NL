---
title: Pagina's publiceren
description: Leer hoe u uw pagina's op verschillende manieren in AEM publiceert en publiceert.
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '1927'
ht-degree: 4%

---

# Pagina&#39;s publiceren {#publishing-pages}

Wanneer u de inhoud in de ontwerpomgeving hebt gemaakt en gecontroleerd, is het doel [beschikbaar stellen op uw openbare website](/help/sites-cloud/authoring/getting-started/concepts.md) (uw publicatieomgeving).

Dit wordt bedoeld als het publiceren van een pagina. Wanneer u een pagina uit het publicatiemilieu wilt verwijderen wordt bedoeld unpublishing. Wanneer u de pagina publiceert en publiceert, blijft deze beschikbaar in de ontwerpomgeving voor verdere wijzigingen totdat u de pagina verwijdert.

U kunt een pagina direct of op een vooraf gedefinieerde datum/tijd publiceren of de publicatie ervan ongedaan maken.

>[!NOTE]
>
>Het publiceren van een Fragment van de Ervaring volgt hoofdzakelijk de zelfde procedure zoals voor het publiceren van een pagina, hoewel van de console of de redacteur van de Fragmenten van de Ervaring.

## Terminologie {#terminology}

Wanneer u met Adobe Experience Manager (AEM) as a Cloud Service werkt, kunnen er verschillende termen voorkomen die betrekking hebben op publiceren.

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

* [Vanuit de paginaeditor](#publishing-from-the-editor)
* [Van de plaatsenconsole](#publishing-from-the-console)

>[!NOTE]
>
>Als u niet over de vereiste rechten voor het publiceren van een specifieke pagina beschikt:
>
>* Er wordt een workflow gestart om de juiste persoon op de hoogte te stellen van uw verzoek om te publiceren.
>* Deze workflow is mogelijk aangepast door uw ontwikkelingsteam.
>* Er wordt kort een bericht weergegeven om u te melden dat de workflow is geactiveerd.

>[!NOTE]
>
>Als u de paginavolgorde wilt behouden, moet u [Publicatie beheren](#manage-publication) de bovenliggende pagina samen met eventuele onderliggende pagina&#39;s in één actie publiceren.
>
>Paginavolgorde is niet gegarandeerd:
>* als alleen onderliggende pagina&#39;s zijn geselecteerd voor publicatie (aangezien de orderinformatie op de bovenliggende pagina staat)
>* als de bovenliggende en onderliggende pagina&#39;s in afzonderlijke handelingen worden gepubliceerd

>[!NOTE]
>
> Zie voor meer mogelijkheden **Op tijd** en **Uit-tijd** in de [Het tabblad Standaard van Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)

### Publiceren vanuit de Editor {#publishing-from-the-editor}

Als u een pagina bewerkt, kunt u deze rechtstreeks vanuit de editor publiceren.

1. Selecteer de **Pagina-informatie** het pictogram om het menu te openen en dan **Pagina publiceren** -optie.

   ![Pagina&#39;s publiceren via paginaopties](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Afhankelijk van het feit of de pagina verwijzingen bevat die moeten worden gepubliceerd:

   * De pagina wordt rechtstreeks gepubliceerd als er geen referenties zijn die moeten worden gepubliceerd.
   * Als de pagina verwijzingen bevat die moeten worden gepubliceerd, worden deze vermeld in de **Publiceren** wizard, waarbij u:
      * Geef op welke elementen, tags enzovoort, u samen met de pagina wilt publiceren en gebruik vervolgens **Publiceren** om het proces te voltooien.
      * Gebruiken **Annuleren** om de handeling af te breken.

   ![Referenties publiceren met de pagina](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Selecteren **Publiceren** wordt de pagina gerepliceerd naar de publicatieomgeving. In de paginaredacteur, wordt een informatiebanner getoond die de publicatieactie bevestigen.

   ![Statusinformatiebanner publiceren](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wanneer u dezelfde pagina in de console weergeeft, is de bijgewerkte publicatiestatus zichtbaar.

   ![De publicatiestatus van de pagina in kolomweergave in de siteconsole](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Publiceren vanuit de editor is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina(&#39;s) wordt/worden gepubliceerd en onderliggende pagina(&#39;s) niet.

>[!NOTE]
>
>Pagina&#39;s die worden benaderd door [aliassen](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) in de editor kan niet worden gepubliceerd. Publicatieopties in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.

### Publiceren vanuit de console {#publishing-from-the-console}

In de siteconsole zijn er twee opties voor publiceren:

* [Snel publiceren](#quick-publish)
* [Publicatie beheren](#manage-publication)

#### Snel publiceren {#quick-publish}

**Snel publiceren** is voor eenvoudige gevallen en publiceert de geselecteerde pagina(&#39;s) direct zonder verdere interactie. Daarom worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

Een pagina publiceren met Snel publiceren:

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Snel publiceren** knop.

   ![Pagina&#39;s selecteren voor publicatie](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Bevestig de publicatie in het dialoogvenster Snel publiceren door op **Publiceren** of annuleren door op **Annuleren**. Onthoud dat niet-gepubliceerde verwijzingen automatisch ook worden gepubliceerd.

   ![Snelle publicatie](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Wanneer de pagina wordt gepubliceerd, wordt een waarschuwing getoond die de publicatie bevestigt.

>[!NOTE]
>
>Snel publiceren is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina of pagina&#39;s worden gepubliceerd en onderliggende pagina&#39;s niet.

#### Publicatie beheren {#manage-publication}

**Publicatie beheren** biedt meer opties dan **Snel publiceren**, zodat onderliggende pagina&#39;s kunnen worden opgenomen, de referenties kunnen worden aangepast en alle toepasselijke workflows kunnen worden gestart en de optie kan worden geboden om op een latere datum te publiceren.

>[!NOTE]
>
>Als u de paginavolgorde wilt behouden, moet u **Publicatie beheren** om de bovenliggende pagina samen met eventuele onderliggende pagina&#39;s in één handeling te publiceren.
>
>Paginavolgorde is niet gegarandeerd:
>* als alleen onderliggende pagina&#39;s zijn geselecteerd voor publicatie (aangezien de orderinformatie op de bovenliggende pagina staat)
>* als de bovenliggende en onderliggende pagina&#39;s in afzonderlijke handelingen worden gepubliceerd

Een pagina publiceren of de publicatie ervan ongedaan maken met Publicatie beheren:

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Publicatie beheren** knop.

   ![Pagina&#39;s selecteren voor publicatie](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. De wizard **Publicatie beheren** wordt gestart. De eerste stap, **Opties**, laat u:

   * **Handeling**

     Kies of u de geselecteerde pagina&#39;s wilt publiceren of de publicatie ervan ongedaan wilt maken.

   * **Planning**

     Kies of u deze handeling nu of op een latere datum wilt uitvoeren.

     Als u later publiceert, wordt een workflow gestart om de geselecteerde pagina of pagina&#39;s op het opgegeven tijdstip te publiceren. Als u de publicatie later ongedaan maakt, wordt een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald moment ongedaan te maken.

     >[!NOTE]
     >
     >Als u een publicatie/publicatie later wilt annuleren, gaat u naar de [Workflowconsole](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) om de corresponderende workflow te beëindigen.

   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. Klikken **Volgende** om door te gaan.

1. In de volgende stap van de wizard Publicatie beheren: **Toepassingsgebied**, kunt u het bereik van de publicatie/niet-publicatie definiëren, bijvoorbeeld om onderliggende pagina&#39;s en/of verwijzingen op te nemen.

   ![Publicatiebereik beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **Inhoud toevoegen**

   U kunt de knop **Inhoud toevoegen** gebruiken om extra pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die moeten worden gepubliceerd voor het geval u deze niet hebt geselecteerd voordat u de wizard Publicatie beheren start.

   De **Inhoud toevoegen** start de knop [padbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) om inhoudselectie toe te staan.

   Selecteer de vereiste pagina&#39;s en klik vervolgens op **Selecteren** om de inhoud toe te voegen aan de wizard of **Annuleren** om de selectie te annuleren en terug te keren naar de wizard.

   **Selectie verwijderen**

   U kunt vervolgens weer in de wizard een item in de lijst selecteren om het item uit de selectie te verwijderen.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Gepubliceerde verwijzingen**

   U kunt de te publiceren of niet gepubliceerde verwijzingen voor een pagina bekijken en wijzigen door het te selecteren en dan te klikken **Gepubliceerde verwijzingen** knop.

   ![Publicatieopties beheren](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   De **Gepubliceerde verwijzingen** geeft de referenties voor de geselecteerde inhoud weer. Deze zijn standaard allemaal geselecteerd en worden gepubliceerd/niet gepubliceerd, maar u kunt de selectie opheffen om ze uit te schakelen, zodat ze niet worden opgenomen in de handeling.

   Klikken **Gereed** om uw wijzigingen op te slaan of **Annuleren** om de selectie te annuleren en terug te keren naar de wizard.

   Terug in de wizard **Verwijzingen** wordt bijgewerkt om uw selectie van te publiceren of niet-gepubliceerde verwijzingen te weerspiegelen.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Inclusief onderliggende items**

   >[!NOTE]
   >
   >Zie [Een boomstructuur publiceren en de publicatie ervan opheffen](#publishing-and-unpublishing-a-tree)

   Klikken **Inclusief onderliggende items** Hiermee opent u een dialoogvenster waarin u:

   * **Inclusief onderliggende items**
   * **Alleen directe kinderen opnemen**
   * **Alleen gewijzigde pagina&#39;s opnemen**
   * **Alleen reeds gepubliceerde pagina&#39;s opnemen**

   Activeer de vereiste opties en bevestig deze met **OK** om de onderliggende pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die op basis van de selectieopties moeten worden gepubliceerd of niet gepubliceerd. Klikken **Annuleren** om de selectie te annuleren en terug te keren naar de wizard.

   ![Publicatie beheren, waaronder kinderen](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. Klikken **Publiceren** in.

   Terug in de plaatsenconsole zal een berichtbericht de publicatie bevestigen.

1. Als de gepubliceerde pagina&#39;s zijn gekoppeld aan workflows, kunnen deze in een definitieve versie worden weergegeven **Workflows** stap van de publicatiewizard.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png)

   >[!NOTE]
   >
   >De **Workflows** deze stap wordt weergegeven op basis van de rechten die de gebruiker al dan niet heeft. Zie de vorige opmerking op deze pagina over publicatiebevoegdheden en het beheren van toegang tot workflows en [Workflows toepassen op pagina&#39;s](/help/sites-cloud/authoring/workflows/applying.md) voor meer informatie.

   De bronnen worden gegroepeerd op basis van de workflows die worden geactiveerd en elke optie heeft de volgende opties:

   * Definieer de titel van de workflow.
   * Behoud het workflowpakket, mits de workflow ondersteuning biedt voor meerdere bronnen.
   * Definieer een titel van het workflowpakket als de optie om het workflowpakket te behouden is gekozen.

1. Klik op **Publiceren** of **Later publiceren** om de publicatie te voltooien.

## Publicatie van pagina&#39;s ongedaan maken {#unpublishing-pages}

Als u de publicatie van een pagina ongedaan maakt, wordt deze verwijderd uit uw publicatie, of [voorvertoning](/help/sites-cloud/authoring/fundamentals/previewing-content.md), zodat deze niet langer beschikbaar is voor uw lezers.

In een [vergelijkbare manier van publiceren](#publishing-pages), kan de publicatie van een of meer pagina&#39;s ongedaan worden gemaakt vanaf het gewenste doel:

* [Vanuit de paginaeditor](#unpublishing-from-the-editor)
* [Van de plaatsenconsole](#unpublishing-from-the-console)

### Publicatie ongedaan maken vanuit de Editor {#unpublishing-from-the-editor}

Als u tijdens het bewerken van een pagina de publicatie van die pagina ongedaan wilt maken, selecteert u **Publicatie van pagina ongedaan maken** in de **Pagina-informatie** zoals u zou doen [de pagina publiceren](#publishing-from-the-editor).

>[!NOTE]
>
>Pagina&#39;s die worden benaderd door [aliassen](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) in de editor kan niet worden gepubliceerd. Publicatieopties in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.

### Publicatie ongedaan maken vanuit de console {#unpublishing-from-the-console}

Net zoals u [de optie Publicatie beheren gebruiken om te publiceren](#manage-publication)kunt u de publicatie ook ongedaan maken.

1. Selecteer de pagina of pagina&#39;s in de siteconsole en klik op de knop **Publicatie beheren** knop.
1. De wizard **Publicatie beheren** wordt gestart. In de eerste stap, bij **Opties**, selecteert u **Publicatie ongedaan maken** in plaats van de standaardoptie **Publiceren**.

   ![Publiceren ongedaan maken - opties](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Net zoals later met publiceren een workflow wordt gestart om deze versie van de pagina op het opgegeven tijdstip te publiceren, wordt later met deactiveren een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald tijdstip ongedaan te maken.

   >[!NOTE]
   >
   >Als u een publicatie/publicatie later wilt annuleren, gaat u naar de [Workflowconsole](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) om de corresponderende workflow te beëindigen.

   >[!NOTE]
   >Als u een [Voorvertoning](/help/sites-cloud/authoring/fundamentals/previewing-content.md) omgeving die u kunt selecteren **Doel** tijdens Publicatie beheren.

1. Als u de niet-publicatie wilt voltooien, gaat u door met de wizard zoals u [de pagina publiceren](#manage-publication).

   ![Unpublishing - Scope](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Een boomstructuur publiceren en de publicatie ervan opheffen {#publishing-and-unpublishing-a-tree}

Wanneer u een aanzienlijk aantal inhoudspagina&#39;s hebt ingevoerd of bijgewerkt - die allen onder de zelfde wortelpagina ingezeten zijn - kan het gemakkelijker zijn om de volledige boom in één actie te publiceren.

U kunt de [Publicatie beheren](#manage-publication) optie op de plaatsenconsole om dit te doen.

1. Selecteer in de siteconsole de hoofdpagina van de boomstructuur die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken, en selecteer **Publicatie beheren**.
1. De wizard **Publicatie beheren** wordt gestart. Kies of u wilt publiceren of de publicatie wilt ongedaan maken en wanneer deze moet plaatsvinden en selecteer **Volgende** om door te gaan.
1. In de **Toepassingsgebied** stap, selecteer de basispagina en selecteer **Inclusief onderliggende items**.

   ![Publicatie beheren door pagina&#39;s te selecteren](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. In de **Inclusief onderliggende items** dialoogvenster:

   * selecteren **Inclusief onderliggende items**
   * deselecteren **Alleen directe kinderen opnemen**
   * deselecteren **Alleen reeds gepubliceerde pagina&#39;s opnemen**
   * vormen **Alleen gewijzigde pagina&#39;s opnemen** indien vereist

   Deze opties zijn standaard geselecteerd, dus u moet eraan denken om ze te configureren. De selectie bevestigen met **OK** om de inhoud toe te voegen aan de publicatie/niet-publicatie.

   ![Inclusief onderliggende elementen voor boompublicatie](/help/sites-cloud/authoring/assets/publishing-include-children-tree.png)

1. In de **Publicatie beheren** kunt u de selectie verder aanpassen door extra pagina&#39;s toe te voegen of geselecteerde pagina&#39;s te verwijderen.

   U kunt ook de referenties controleren die via het dialoogvenster **Gepubliceerde verwijzingen** -optie.

1. [Doorgaan met de normale wizard Publicatie beheren](#manage-publication) om de publicatie of niet-publicatie van de boom te voltooien.

## Publicatiestatus bepalen {#determining-publication-status}

U kunt de publicatiestatus van een pagina bepalen:

* In de [bron overzichtsinformatie over de plaatsenconsole](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

  ![Publicatiestatus in de kaartweergave](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

  De publicatiestatus wordt weergegeven in [kaart](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view)-, [kolom](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view)- en [lijstweergaven](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) in de Sites-console.

* In de [tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

  ![Status van publicatie in tijdlijnweergave](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* In de [Menu Paginagegevens](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) bij het bewerken van een pagina

  ![Status van publicatie in het menu Pagina-informatie](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
