---
title: Pagina's publiceren
description: Leer hoe u uw pagina's op verschillende manieren in AEM publiceert en publiceert.
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1936'
ht-degree: 4%

---

# Pagina&#39;s publiceren {#publishing-pages}

Zodra u hebt gecreeerd en uw inhoud op het auteursmilieu herzien, moet het doel [ het op uw openbare website ](/help/sites-cloud/authoring/author-publish.md) (uw publicatiemilieu) ter beschikking stellen.

Dit wordt bedoeld als het publiceren van een pagina. Wanneer u een pagina uit het publicatiemilieu wilt verwijderen wordt bedoeld unpublishing. Wanneer u de pagina publiceert en publiceert, blijft deze beschikbaar in de ontwerpomgeving voor verdere wijzigingen totdat u de pagina verwijdert.

U kunt een pagina direct of op een vooraf gedefinieerde datum/tijd publiceren of de publicatie ervan ongedaan maken.

>[!NOTE]
>
>Het publiceren van een Fragment van de Ervaring volgt hoofdzakelijk de zelfde procedure zoals voor het publiceren van een pagina, hoewel van de console of de redacteur van de Fragmenten van de Ervaring.

## Terminologie {#terminology}

Bij het werken met Adobe Experience Manager (AEM) as a Cloud Service kunnen er verschillende termen voorkomen die betrekking hebben op publiceren.

* **Publish/Unpublish**
   * Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
   * Dit zijn de termen die worden gebruikt in AEM documentatie.
* **activeert/deactiveert**
   * Deze termen zijn synoniem met publiceren/verwijderen.
   * Deze termen zijn in vorige versies van AEM gebruikt.
* **Replicatie/Replicatie**
   * Dit zijn de technische termen die de verplaatsing van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikersopmerkingen) van de ene omgeving naar de andere beschrijven wanneer u een pagina publiceert.
   * Deze termen worden vooral gebruikt door ontwikkelaars.

## Pagina&#39;s publiceren {#publishing-pages-1}

Afhankelijk van uw locatie kunt u publiceren:

* [Vanuit de paginaeditor](#publishing-from-the-page-editor)
* [Van de ](#publishing-from-the-sites-console)
* [Van de universele editor](/help/sites-cloud/authoring/universal-editor/publishing.md)

>[!NOTE]
>
>Als u niet over de vereiste rechten voor het publiceren van een specifieke pagina beschikt:
>
>* Er wordt een workflow gestart om de juiste persoon op de hoogte te stellen van uw verzoek om te publiceren.
>* Deze workflow is mogelijk aangepast door uw ontwikkelingsteam.
>* Er wordt kort een bericht weergegeven om u te melden dat de workflow is geactiveerd.

>[!NOTE]
>
>Als u paginaorde wilt bewaren moet u [ gebruiken leidt Publicatie ](#manage-publication) om de ouderpagina samen met om het even welke kindpagina&#39;s - in één enkele actie te publiceren.
>
>Paginavolgorde is niet gegarandeerd:
>* als alleen onderliggende pagina&#39;s zijn geselecteerd voor publicatie (aangezien de orderinformatie op de bovenliggende pagina staat)
>* als de bovenliggende en onderliggende pagina&#39;s in afzonderlijke handelingen worden gepubliceerd

>[!NOTE]
>
> Voor extra mogelijkheden zie **op Tijd** en **van Tijd** in het [ Basis lusje van de Eigenschappen van de Pagina ](/help/sites-cloud/authoring/sites-console/page-properties.md#basic)

### Publiceren vanuit de Pagina-editor {#publishing-from-the-page-editor}

Als u een pagina in de [ paginaredacteur uitgeeft, ](/help/sites-cloud/authoring/page-editor/introduction.md) het kan direct van de redacteur worden gepubliceerd.

1. Selecteer het **pictogram van de Informatie van de Pagina** om het menu en toen de **pagina van Publish** optie te openen.

   ![ het Publiceren van een pagina via paginaopties ](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Afhankelijk van het feit of de pagina verwijzingen bevat die moeten worden gepubliceerd:

   * De pagina wordt rechtstreeks gepubliceerd als er geen referenties zijn die moeten worden gepubliceerd.
   * Als de pagina verwijzingen heeft die het publiceren vereisen, zijn deze vermeld in **Publish** tovenaar, waar u of kunt:
      * Specificeer welke van de activa, of markeringen, etc., die u samen met de pagina wilt publiceren, dan gebruik **Publish** om het proces te voltooien.
      * Het gebruik **annuleert** om de actie af te breken.

   ![ het Publiceren verwijzingen met de pagina ](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Het selecteren van **Publish** zal de pagina aan het publicatiemilieu herhalen. In de paginaredacteur, wordt een informatiebanner getoond die de publicatieactie bevestigen.

   ![ de status van Publish info banner ](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wanneer u dezelfde pagina in de console weergeeft, is de bijgewerkte publicatiestatus zichtbaar.

   ![ de publicatiestatus van de Pagina in kolommening in de plaatsenconsole ](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Publiceren vanuit de pagina-editor is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina(&#39;s) wordt/worden gepubliceerd en onderliggende pagina(&#39;s) niet.

>[!NOTE]
>
>De pagina&#39;s die door [ aliassen ](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced) in de redacteur worden betreden kunnen niet worden gepubliceerd. Publish-opties in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.

### Publiceren vanuit de siteconsole {#publishing-from-the-sites-console}

In de **console van Plaatsen** zijn er twee opties voor het publiceren:

* [Quick Publish](#quick-publish)
* [Publicatie beheren](#manage-publication)

#### Quick Publish {#quick-publish}

**Snelle Publish** is voor eenvoudige gevallen en publiceert de geselecteerde pagina(s) onmiddellijk zonder enige verdere interactie. Daarom worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

Een pagina publiceren met Quick Publish:

1. Selecteer de pagina of de pagina&#39;s in de plaatsenconsole en klik de **Snelle knoop van Publish**.

   ![ Selecterend pagina&#39;s voor publicatie ](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. In de Snelle dialoog van Publish, bevestig de publicatie door op **Publish** te klikken of annuleer door op **te klikken annuleert**. Onthoud dat niet-gepubliceerde verwijzingen automatisch ook worden gepubliceerd.

   ![ Snelle publicatiebevestiging ](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Wanneer de pagina wordt gepubliceerd, wordt een waarschuwing getoond die de publicatie bevestigt.

>[!NOTE]
>
>Quick Publish is een oppervlakkige publicatie, dat wil zeggen dat alleen de geselecteerde pagina(&#39;s) wordt/worden gepubliceerd en onderliggende pagina&#39;s niet.

#### Publicatie beheren {#manage-publication}

**beheer Publicatie** aanbiedingen meer opties dan **Snelle Publish**, die voor de opneming van kindpagina&#39;s, aanpassing van de verwijzingen, en het beginnen van om het even welke toepasselijke werkschema&#39;s toestaan en de optie aanbieden om op een recentere datum te publiceren.

>[!NOTE]
>
>Als u paginaorde wilt bewaren moet u **gebruiken leidt Publicatie** om de ouderpagina samen met om het even welke kindpagina&#39;s in één enkele actie te publiceren.
>
>Paginavolgorde is niet gegarandeerd:
>* als alleen onderliggende pagina&#39;s zijn geselecteerd voor publicatie (aangezien de orderinformatie op de bovenliggende pagina staat)
>* als de bovenliggende en onderliggende pagina&#39;s in afzonderlijke handelingen worden gepubliceerd

Een pagina publiceren of de publicatie ervan ongedaan maken met Publicatie beheren:

1. Selecteer de pagina of de pagina&#39;s in de plaatsenconsole en klik **leiden Publicatie** knoop.

   ![ Selecterend pagina&#39;s voor publicatie ](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. De wizard **Publicatie beheren** wordt gestart. De eerste stap, **Opties**, laat u:

   * **Actie**

     Kies of u de geselecteerde pagina&#39;s wilt publiceren of de publicatie ervan ongedaan wilt maken.

   * **Plannend**

     Kies of u deze handeling nu of op een latere datum wilt uitvoeren.

     Als u later publiceert, wordt een workflow gestart om de geselecteerde pagina of pagina&#39;s op het opgegeven tijdstip te publiceren. Als u de publicatie later ongedaan maakt, wordt een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald moment ongedaan te maken.

     >[!NOTE]
     >
     >Als u wilt annuleren publiceren/unpublish later, ga naar de [ Console van het Werkschema ](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) om het overeenkomstige werkschema te eindigen.

   ![ beheert de Opties van de Publicatie ](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. Klik **daarna** om verder te gaan.

1. In de volgende stap van de Manage tovenaar van de Publicatie, **Reikwijdte**, kunt u het werkingsgebied van de publicatie/unpublication zoals het omvatten van kindpagina&#39;s en/of het omvatten van verwijzingen bepalen.

   ![ beheer het Toepassingsgebied van de Publicatie ](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **voeg Inhoud** toe

   U kunt de knop **Inhoud toevoegen** gebruiken om extra pagina&#39;s toe te voegen aan de lijst met pagina&#39;s die moeten worden gepubliceerd voor het geval u deze niet hebt geselecteerd voordat u de wizard Publicatie beheren start.

   Het selecteren van **voegt Inhoud** knoop toe begint [ wegbrowser ](/help/sites-cloud/authoring/path-selection.md) om inhoudselectie toe te staan.

   Selecteer de vereiste pagina&#39;s en klik dan **Uitgezocht** om de inhoud aan de tovenaar toe te voegen of **annuleert** om de selectie te annuleren en aan de tovenaar terug te keren.

   **verwijder Selectie**

   U kunt vervolgens weer in de wizard een item in de lijst selecteren om het item uit de selectie te verwijderen.

   ![ beheer Publicatie die pagina&#39;s ](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png) selecteert

   **Gepubliceerde Verwijzingen**

   U kunt de verwijzingen bekijken en wijzigen die of unpublished voor een pagina moeten worden gepubliceerd door het te selecteren en dan de **Gepubliceerde knoop van Verwijzingen** te klikken.

   ![ beheert de Opties van de Publicatie ](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   De **Gepubliceerde dialoog van Verwijzingen** toont de verwijzingen voor de geselecteerde inhoud. Deze zijn standaard allemaal geselecteerd en worden gepubliceerd/niet gepubliceerd, maar u kunt de selectie opheffen om ze uit te schakelen, zodat ze niet worden opgenomen in de handeling.

   Klik **Gedaan** om uw veranderingen te bewaren of **annuleert** om de selectie te annuleren en aan de tovenaar terug te keren.

   Terug in de tovenaar, wordt de **kolom van Verwijzingen** bijgewerkt om op uw selectie van te publiceren verwijzingen te wijzen of unpublished.

   ![ beheer Publicatie die pagina&#39;s ](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png) selecteert

   **omvat Kinderen**

   >[!NOTE]
   >
   >Zie [ Publiceren en Unpublishing aTree ](#publishing-and-unpublishing-a-tree)

   Het klikken **omvat Kinderen** opent een dialoogdoos die u toestaat:

   * **omvat kinderen**
   * **omvat slechts directe kinderen**
   * **omvatten slechts gewijzigde pagina&#39;s**
   * **omvat slechts reeds gepubliceerde pagina&#39;s**

   Activeer de vereiste opties en bevestig met **O.K.** om de kindpagina&#39;s aan de lijst van pagina&#39;s toe te voegen die moeten worden gepubliceerd of unpublished gebaseerd op de selectieopties. Klik **annuleren** om de selectie te annuleren en aan de tovenaar terug te keren.

   ![ beheer Publicatie met inbegrip van kinderen ](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. Klik **Publish** om te voltooien.

   Terug in de plaatsenconsole zal een berichtbericht de publicatie bevestigen.

1. Als de gepubliceerde pagina&#39;s met werkschema&#39;s worden geassocieerd, kunnen zij in een definitieve **stap van de Werkschema&#39;s** van de publicatietovenaar worden getoond.

   ![ beheer Publicatie die pagina&#39;s ](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png) selecteert

   >[!NOTE]
   >
   >De **stap van de Werkschema&#39;s** wordt getoond gebaseerd op welke rechten uw gebruiker kan of niet kan hebben. Zie de vorige nota op deze pagina betreffende het publiceren voorrechten en het Leiden Toegang tot Werkschema&#39;s en [ Toepassend Werkschema&#39;s op Pagina&#39;s ](/help/sites-cloud/authoring/workflows/applying.md) voor details.

   De bronnen worden gegroepeerd op basis van de workflows die worden geactiveerd en elke optie heeft de volgende opties:

   * Definieer de titel van de workflow.
   * Behoud het workflowpakket, mits de workflow ondersteuning biedt voor meerdere bronnen.
   * Definieer een titel van het workflowpakket als de optie om het workflowpakket te behouden is gekozen.

1. Klik op **Publiceren** of **Later publiceren** om de publicatie te voltooien.

## Publicatie van pagina&#39;s ongedaan maken {#unpublishing-pages}

Het ongedaan maken van een pagina zal het uit uw publiceren, of [ voorproef ](/help/sites-cloud/authoring/sites-console/previewing-content.md), milieu verwijderen zodat het niet meer beschikbaar aan uw lezers is.

Op a [ manier gelijkend op het publiceren ](#publishing-pages), kunnen één of meerdere pagina&#39;s van de gewenste bestemming unpublished:

* [Vanuit de paginaeditor](#unpublishing-from-the-editor)
* [Van de plaatsenconsole](#unpublishing-from-the-console)

### Publicatie ongedaan maken vanuit de Editor {#unpublishing-from-the-editor}

Wanneer het uitgeven van een pagina, als u die pagina ongedaan wilt maken, uitgezocht **publiceert Pagina** in het **menu van de Informatie van de Pagina**, veel aangezien u [ de pagina ](#publishing-from-the-editor) zou publiceren.

>[!NOTE]
>
>De pagina&#39;s die door [ aliassen ](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced) in de redacteur worden betreden kunnen niet worden ongepubliceerd. Publish-opties in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.

### Publicatie ongedaan maken vanuit de console {#unpublishing-from-the-console}

Enkel aangezien u [ de Manage optie van de Publicatie gebruikt om ](#manage-publication) te publiceren, kunt u het ook gebruiken om unpublish.

1. Selecteer de pagina of de pagina&#39;s in de plaatsenconsole en klik **leiden Publicatie** knoop.
1. De wizard **Publicatie beheren** wordt gestart. In de eerste stap, bij **Opties**, selecteert u **Publicatie ongedaan maken** in plaats van de standaardoptie **Publiceren**.

   ![ Unpublishing - Opties ](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Net zoals later met publiceren een workflow wordt gestart om deze versie van de pagina op het opgegeven tijdstip te publiceren, wordt later met deactiveren een workflow gestart om de publicatie van de geselecteerde pagina of pagina&#39;s op een bepaald tijdstip ongedaan te maken.

   >[!NOTE]
   >
   >Als u wilt annuleren publiceren/unpublish later, ga naar de [ Console van het Werkschema ](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) om het overeenkomstige werkschema te eindigen.

   >[!NOTE]
   >Als u het milieu van de a [ Voorproef ](/help/sites-cloud/authoring/sites-console/previewing-content.md) hebt kunt u de **Doel** tijdens Manage Publication selecteren.

1. Om unpublication te voltooien, ga door de tovenaar verder aangezien u [ de pagina ](#manage-publication) zou publiceren.

   ![ Unpublishing - werkingsgebied ](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Een boomstructuur publiceren en de publicatie ervan opheffen {#publishing-and-unpublishing-a-tree}

Wanneer u een aanzienlijk aantal inhoudspagina&#39;s hebt ingevoerd of bijgewerkt - die allen onder de zelfde wortelpagina ingezeten zijn - kan het gemakkelijker zijn om de volledige boom in één actie te publiceren.

U kunt [ gebruiken beheert Publicatie ](#manage-publication) optie op de plaatsenconsole om dit te doen.

1. In de plaatsenconsole, selecteer de wortelpagina van de boom u publiceren of wilt unpublish en selecteren **Publicatie** leiden.
1. De wizard **Publicatie beheren** wordt gestart. Kies om te publiceren of unpublish en wanneer het zou moeten voorkomen en **daarna** selecteren om verder te gaan.
1. In de **stap van het Bereik**, selecteer de wortelpagina en selecteer **omvat Kinderen**.

   ![ beheer Publicatie die pagina&#39;s ](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png) selecteert

1. In **omvat de dialoog van Kinderen**:

   * selecteren **omvat Kinderen**
   * unselect **omvat slechts directe kinderen**
   * unselect **omvat slechts reeds gepubliceerde pagina&#39;s**
   * vorm **omvat slechts gewijzigde pagina&#39;s** zoals vereist

   Deze opties zijn standaard geselecteerd, dus u moet eraan denken om ze te configureren. Bevestig de selectie met **O.K.** om de inhoud aan de publicatie/unpublication toe te voegen.

   ![ Met inbegrip van kinderen voor boompublicatie ](/help/sites-cloud/authoring/assets/publishing-include-children-tree.png)

1. In **beheer de tovenaar van de Publicatie** u kunt de selectie verder aanpassen door extra pagina&#39;s toe te voegen of die te verwijderen selecteerde.

   Herinner dat u de verwijzingen kunt ook herzien die via de **Gepubliceerde optie van Verwijzingen** moeten worden gepubliceerd.

1. [ ga de Manage tovenaar van de Publicatie als normaal ](#manage-publication) verder om de publicatie of unpublication van de boom te voltooien.

## Publicatiestatus bepalen {#determining-publication-status}

U kunt de publicatiestatus van een pagina bepalen:

* In de [ informatie van het middeloverzicht over de plaatsenconsole ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)

  ![ de status van de Publicatie in kaartmening ](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

  De publicatiestatus wordt weergegeven in [kaart](/help/sites-cloud/authoring/basic-handling.md#card-view)-, [kolom](/help/sites-cloud/authoring/basic-handling.md#column-view)- en [lijstweergaven](/help/sites-cloud/authoring/basic-handling.md#list-view) in de Sites-console.

* In de [ chronologie ](/help/sites-cloud/authoring/basic-handling.md#timeline)

  ![ de status van de Publicatie in chronologiemening ](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* In het [ menu van de Informatie van de Pagina ](/help/sites-cloud/authoring/page-editor/introduction.md#page-information) wanneer het uitgeven van een pagina

  ![ de status van de Publicatie in het menu van de Informatie van de Pagina ](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
