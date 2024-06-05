---
title: De siteconsole
description: Leer hoe u de Sites-console kunt gebruiken om uw AEM te beheren en in te delen.
exl-id: b666e62a-c3dc-4be3-8932-d5fe67b178d6
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1628'
ht-degree: 3%

---

# De siteconsole {#sites-console}

Leer hoe u de **Sites** -console voor het beheren en ordenen van uw AEM.

## Afdrukstand {#orientation}

De **Sites** kunt u de paginahiërarchie weergeven.

![Kolomweergave van de Sites-console met een geselecteerd item](assets/sites-console-column-view-selected.png)

Het biedt verschillende weergaven en werkbalken om u te helpen uw pagina&#39;s te beheren en te ordenen.

* [De consolewerkbalk](#toolbar) is altijd aanwezig om u te helpen navigeren.
* [Drie verschillende weergaven](#views) waarmee u de pagina gemakkelijk kunt vinden en selecteren.
* [De werkbalk Handeling](#action-toolbar) wordt weergegeven wanneer u een item hebt geselecteerd om actie te ondernemen.
* [Het zijpaneel](#side-panel) heeft meerdere opties om gedetailleerde informatie op een geselecteerde pagina weer te geven.

## Console, werkbalk {#console-toolbar}

De consoletoolbar is altijd aanwezig op de console en helpt u zich in uw inhoud oriënteren en de inhoud navigeren.

![De werkbalk van de Sites-console](assets/sites-console-toolbar.png)

### Kiezer zijpaneel {#side-panel-selector}

Met de kiezer in het zijpaneel kunt u aanvullende informatie over het geselecteerde item weergeven in de console.

![Selectieknop zijpaneel](assets/sites-console-side-panel-button.png)

Welke opties worden weergegeven, is afhankelijk van uw huidige console. Bijvoorbeeld in **Sites** u kunt alleen inhoud (standaard), de tijdlijn, verwijzingen of het filterzijpaneel selecteren.

![Voorbeeld van de selector van het zijpaneel](assets/sites-console-side-panel-selector.png)

Zie het document voor meer informatie over het zijpaneel [Zijpaneel siteconsole.](/help/sites-cloud/authoring/sites-console/console-side-panel.md)

### Broodkruimels {#breadcrumbs}

In het midden van de spoorstaaf, waarbij altijd de beschrijving van het geselecteerde artikel wordt getoond, kunt u met de broodkruimels door de niveaus van uw website navigeren.

![Broodkruimels in navigatiebalk](assets/sites-console-breadcrumbs-navigation.png)


Tik of klik op de tekst van de broodkruimel om een vervolgkeuzelijst weer te geven met de niveaus van de hiërarchie van het geselecteerde item. Tik of klik op een item om naar die locatie te gaan.

![Voorbeeld van uitvouwen broodkruimels](assets/sites-console-breadcrumbs-example.png)

### Alles selecteren {#select-all}

Tikken of klikken op de knop **Alles selecteren** selecteert alle punten in uw huidige mening van de console.

![Alles selecteren](assets/sites-console-select-all.png)

Wanneer u alle items hebt geselecteerd, wordt het aantal geselecteerde items rechtsboven op de werkbalk weergegeven op de plaats **Alles selecteren** weergegeven.

U kunt alle items deselecteren en de selectiemodus afsluiten door:

* Klik of tikken op de knop **X** naast de telling.
* Met de **ontsnappen** toets.

![Alle selecties opheffen](assets/sites-console-deselect-all.png)

### Knop Maken {#create-button}

De **Maken** kunt u nieuwe pagina&#39;s aan uw site toevoegen en aanvullende Sites-objecten maken, zoals Live kopieën of Launches.

![Knop Maken](assets/sites-console-create.png)

Zodra geklikt, zijn de getoonde opties aangewezen aan de console/de context. De meest voorkomende zijn:

* [Pagina](/help/sites-cloud/authoring/sites-console/creating-pages.md)
* [Site](/help/sites-cloud/administering/site-creation/create-site.md)
* [Live kopie](/help/sites-cloud/administering/msm/overview.md)
* [Starten](/help/sites-cloud/authoring/launches/overview.md)
* [Taalkopie](/help/sites-cloud/administering/translation/overview.md)
* [CSV-rapport](/help/sites-cloud/authoring/sites-console/csv-export.md)

Zie de koppelingen naar deze functies voor meer informatie over hoe ze werken.

## Weergaven en Pagina&#39;s selecteren {#views}

De **Sites** De console biedt drie verschillende meningen van uw inhoudshiërarchie aan. U kunt de bronnen weergeven, doorbladeren en selecteren (voor verdere actie) met een van de beschikbare weergaven.

* [Kolomweergave](#column-view)
* [Kaartweergave](#card-view)
* [Lijstweergave](#list-view)

De **Weergave** helemaal rechts van de werkbalk AEM geeft de geselecteerde weergave aan.

Als u hierop tikt of erop klikt, kunt u een andere weergave selecteren.

![Knop Weergaven](assets/sites-console-views-button.png)

U kunt schakelen tussen de kolomweergave, de kaartweergave en de lijstweergave. In de lijstweergave worden ook de weergave-instellingen weergegeven.

![Weergaven](assets/sites-console-view.png)

>[!NOTE]
>
>De optie **Instellingen weergeven** is alleen beschikbaar in de modus **Lijstweergave**.

Het bekijken, navigeren, en het selecteren zijn elk conceptueel het zelfde over alle meningen, maar hebben kleine variaties in behandeling, afhankelijk van de mening u gebruikt.

>[!NOTE]
>
>Standaard worden in AEM Assets de oorspronkelijke uitvoeringen van elementen in de gebruikersinterface niet als miniaturen weergegeven in een van de weergaven. Beheerders kunnen met overlays de oorspronkelijke uitvoeringen als miniaturen weergeven.

### Bronnen selecteren {#selecting-resources}

Het selecteren van een specifieke bron is afhankelijk van een combinatie van de weergave en het apparaat:

| Weergave | Aanraken selecteren | Bureaublad selecteren | Deselecteer Aanraken | Selectie van bureaublad opheffen |
|---|---|---|---|---|
| Kolom | Selecteer de miniatuur | Klik op de miniatuur | Selecteer de miniatuur | Klik op de miniatuur |
| Kaart | De kaart selecteren en de muisknop ingedrukt houden | Muisknop erboven gebruikt vervolgens de handeling Snel vinkje | Selecteer de kaart | Klik op de kaart |
| Lijst | Selecteer de miniatuur | Klik op de miniatuur | Selecteer de miniatuur | Klik op de miniatuur |

#### Voorbeeld selecteren {#selecting-example}

1. In de kaartweergave bijvoorbeeld:

   ![Kaartweergave selecteren](assets/sites-console-card-view-select.png)

1. Zodra u een middel hebt geselecteerd, wordt de hoogste kopbal behandeld door [werkbalk Handelingen](#actions-toolbar) die toegang biedt tot acties die momenteel van toepassing zijn op de geselecteerde bron.

1. Als u de selectiemodus wilt afsluiten, selecteert u de **X** rechtsboven, of gebruik **ontsnappen**.

### Kolomweergave {#column-view}

In de kolomweergave kunt u een inhoudsstructuur visueel navigeren door een reeks trapsgewijze kolommen. Met deze weergave kunt u de boomstructuur van uw website visualiseren en doorlopen.

![Kolomweergave](assets/sites-console-column-view.png)

Als u een bron in de kolom uiterst links selecteert, worden de onderliggende bronnen in een kolom rechts weergegeven. Als u een bron in de rechterkolom selecteert, worden de onderliggende bronnen in een andere kolom rechts weergegeven, enzovoort.

* U kunt omhoog en omlaag in de boom navigeren door op de middelnaam of chevron rechts van de middelnaam te tikken of te klikken.

   * De naam en het chevron van de bron worden benadrukt wanneer getikt of geklikt.
   * De kinderen van het geklikte/geplakte middel worden getoond in de kolom rechts van het aangeklikte/geplakte middel.
   * Als u een middelnaam selecteert die geen kinderen heeft, worden zijn details getoond in de definitieve kolom.

* Als u op de miniatuur tikt of erop klikt, wordt de bron geselecteerd.

   * Als deze optie is geselecteerd, wordt een vinkje op de miniatuur geplaatst en wordt de naam van de bron ook gemarkeerd.
   * De details van de geselecteerde bron worden getoond in de definitieve kolom.
   * De werkbalk Handeling wordt beschikbaar.

* Wanneer een pagina in kolomweergave is geselecteerd, wordt de geselecteerde pagina samen met de volgende details weergegeven in de definitieve kolom:

   * Paginatitel
   * Paginanaam (onderdeel van de URL van de pagina)
   * Sjabloon waarop de pagina is gebaseerd
   * Wijzigingsdetails
   * Paginataal
   * Publicatie- en voorvertoningsgegevens

### Kaartweergave {#card-view}

In de kaartweergave wordt elk item op het huidige niveau in de hiërarchie weergegeven als een grote kaart.

![Kaartweergave](assets/sites-console-card-view.png)

* Kaarten bieden informatie zoals:

   * Een visuele weergave van de pagina-inhoud.
   * De paginatitel.
   * Belangrijke datums (zoals laatst bewerkt, laatst gepubliceerd).
   * Als de pagina is vergrendeld, verborgen of deel uitmaakt van een livecopy.
   * Geeft aan of u op het item moet reageren als onderdeel van een workflow.

Kaartweergave biedt ook [snelle acties](#quick-actions) voor items zoals selectie en algemene handelingen zoals bewerken.

![Snelle acties](assets/sites-console-quick-actions.png)

U kunt door de boom omlaag navigeren door op kaarten te tikken of te klikken (zorg dat u niet op de snelle acties tikt) of door nogmaals op de knop [broodkruimels in de koptekst](#the-header).

### Lijstweergave {#list-view}

De mening van de lijst verstrekt informatie voor elk middel op het huidige niveau in een lijst.

![Lijstweergave](assets/sites-console-list-view.png)

* U kunt omlaag door de boom navigeren door op de middelnaam te tikken/te klikken en file door te gebruiken [broodkruimels in de koptekst](#the-header).
* Als u gemakkelijk alle items in de lijst wilt selecteren, gebruikt u de opdracht [**Alles selecteren** in de werkbalk.](#select-all)

* Selecteer de kolommen die u wilt weergeven **Instellingen weergeven** onder de knop Weergaven. De volgende kolommen zijn beschikbaar voor weergave:

   * **Naam** - Paginanaam, die nuttig kan zijn in een meertalige ontwerpomgeving omdat deze deel uitmaakt van de URL van de pagina en niet wordt gewijzigd, ongeacht de taal
   * **gewijzigd** - Datum van laatste wijziging en laatst gewijzigd door gebruiker
   * **Gepubliceerd** - Status van publicatie
   * **Voorvertoning** - Voorvertoningsstatus
   * **Sjabloon** - Sjabloon waarop de pagina is gebaseerd
   * **Bewerking**
   * **Workflow** - Werkstroom die momenteel op de pagina wordt toegepast. Er is meer informatie beschikbaar wanneer u de muis boven de tijdlijn houdt of deze opent.
   * **Vertaald**
   * **Paginaweergaven**
   * **Unieke bezoekers**
   * **Tijd op pagina**

![Kolommen configureren](assets/sites-console-select-columns.png)

Standaard worden de **Naam** wordt een kolom weergegeven die een deel van de URL voor de pagina uitmaakt. In sommige gevallen moet de auteur pagina&#39;s openen die in een andere taal zijn en kan het nuttig zijn de naam van de pagina (die gewoonlijk onveranderlijk is) te zien als de auteur de taal van de pagina niet kent.

* Wijzig de volgorde van de items met de gestippelde verticale balk helemaal rechts van elk item in de lijst.

![Kolomvolgorde](assets/sites-console-column-order.png)

Selecteer de verticale selectiebalk en sleep het item naar een nieuwe positie in de lijst.

![Orderlijst](assets/sites-console-order-list.png)

>[!NOTE]
>
>Het wijzigen van de volgorde werkt alleen in een geordende map die `jcr:primaryType` waarde als `sling:OrderedFolder`.

## Werkbalk Handelingen {#actions-toolbar}

Wanneer een middel wordt geselecteerd, kunt u diverse acties op het geselecteerde punt uitvoeren. Deze acties worden weergegeven op de werkbalk Handelingen.

![Werkbalk Handelingen](assets/introduction-actions-toolbar.png)

De actietoolbar verschijnt slechts wanneer een middel in de console wordt geselecteerd. De actie beschikbaar in de actiestoolbar verandert om op de acties te wijzen u op de specifieke geselecteerde punten kunt nemen. De meest voorkomende acties zijn:

* [**Maken**](#create-action) - Nieuwe handelingen maken die betrekking hebben op inhoud of inhoud
* **Bewerken** - Afhankelijk van hoe de geselecteerde pagina is gemaakt, wordt **Bewerken** de actie zal de aangewezen redacteur openen.
   * [Pagina-editor](/help/sites-cloud/authoring/page-editor/introduction.md) - Voor pagina&#39;s die zijn gemaakt met de AEM Pagina-editor
   * [Universele editor](/help/sites-cloud/authoring/universal-editor/authoring.md) - Voor pagina&#39;s die zijn gemaakt met de Universal Editor
* [**Eigenschappen**](/help/sites-cloud/authoring/sites-console/page-properties.md) - Hiermee opent u het venster met pagina-eigenschappen
* [**Vergrendelen**](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) - Een pagina vergrendelen om te voorkomen dat anderen deze wijzigen
* [**Kopiëren**](/help/sites-cloud/authoring/sites-console/managing-pages.md#copying-and-pasting-a-page) - Een pagina kopiëren
* [**Verplaatsen**](/help/sites-cloud/authoring/sites-console/managing-pages.md#moving-or-renaming-a-page) - Een pagina verplaatsen of de naam ervan wijzigen
* [**Snel publiceren**](/help/sites-cloud/authoring/sites-console/publishing-pages.md#quick-publish) - Een pagina of pagina&#39;s direct publiceren
* [**Publicatie beheren**](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication) - Een pagina of pagina&#39;s voor publicatie plannen
* [**Herstellen**](/help/sites-cloud/authoring/sites-console/page-versions.md#restore-version) - Een versie van een pagina of paginastructuur herstellen
* [**Verwijderen**](/help/sites-cloud/authoring/sites-console/managing-pages.md#deleting-a-page) - Een pagina of pagina&#39;s verwijderen

Vanwege de ruimtebeperkingen in sommige vensters kan de werkbalk snel langer worden dan de beschikbare ruimte. Als dit gebeurt, worden er extra opties weergegeven. Klikken of tikken op de ellips (de drie stippen of **...**) opent u een vervolgkeuzelijst met alle resterende handelingen.

![Aanvullende opties](assets/sites-console-additional-options.png)

### Handeling maken {#create-action}

De handeling Maken biedt vergelijkbare opties voor de [**Maken** werkbalkknop](#create-button) voor het maken van nieuwe pagina&#39;s en vergelijkbare items.

Bovendien biedt het de mogelijkheid om paginagerelateerde acties te maken.

* [**Workflow**](/help/sites-cloud/authoring/workflows/overview.md) - Een workflow toepassen op een pagina
* [**Versie**](/help/sites-cloud/authoring/sites-console/page-versions.md) - Een versie van een pagina maken

## Sjablonen

U kunt gemakkelijk zien op welke sjabloon de pagina is gebaseerd wanneer u de pagina selecteert in de [**kolomweergave**](/help/sites-cloud/authoring/basic-handling.md#column-view) of de [**lijstweergave**](/help/sites-cloud/authoring/basic-handling.md#list-view).
