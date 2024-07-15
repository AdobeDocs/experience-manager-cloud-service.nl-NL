---
title: Uw Postvak IN
description: Leer hoe u de meldingen in uw Postvak IN kunt gebruiken om uw taken te beheren.
exl-id: 37d0cf43-192f-4a50-b174-42d7dced3b63
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 13%

---

# Uw Postvak IN {#your-inbox}

U kunt meldingen ontvangen van verschillende AEM, waaronder workflows en projecten. U ontvangt bijvoorbeeld meldingen over:

* Taken:
   * Deze kunnen ook op diverse punten binnen AEM UI, bijvoorbeeld, onder **Projecten** worden gecreeerd.
   * Dit kan het product zijn van een stap voor **Taak maken** of **Projecttaak maken** van een workflow.
* Workflows:
   * Werkitems die acties vertegenwoordigen die u moet uitvoeren op pagina-inhoud
      * Dit is het product van werkschema **Deelnemer** stappen.
   * Items mislukken, zodat beheerders de mislukte stap opnieuw kunnen proberen

U ontvangt deze meldingen in uw eigen Postvak IN waar u ze kunt bekijken en er actie op kunt ondernemen.

>[!NOTE]
>
>Raadpleeg de volgende secties voor meer informatie over de itemtypen:
>
>* [ Projecten ](/help/sites-cloud/authoring/projects/overview.md)
>* [ Projecten - het werken met Taken ](/help/sites-cloud/authoring/projects/tasks.md)
>* [ Werkstromen ](/help/sites-cloud/authoring/workflows/overview.md)

## Postvak IN van koptekst {#inbox-in-the-header}

Van om het even welke consoles wordt het huidige aantal punten in uw inbox getoond in de kopbal. De indicator kan ook worden geopend om snel toegang te geven tot de pagina&#39;s waarvoor een of meer handelingen vereist zijn, of om toegang te krijgen tot het Postvak IN:

![ Inbox overzicht in kopbal ](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Bepaalde acties zullen ook in de [ kaartmening van het aangewezen middel ](/help/sites-cloud/authoring/basic-handling.md#card-view) worden getoond.

## De Postvak IN openen {#opening-the-inbox}

U opent als volgt het AEM-vak:

1. Selecteer de indicator in de toolbar.

1. Selecteer **Alles bekijken**. **AEM Inbox** opent. In de inbox ziet u items uit workflows, projecten en taken.
1. De standaardweergave is [Lijstweergave](#inbox-list-view), maar u kunt ook schakelen naar [Kalenderweergave](#inbox-calendar-view). Dit gebeurt met de weergavekiezer (werkbalk, rechtsboven).

   Voor beide meningen kunt u [ Montages van de Mening ](#inbox-view-settings) ook bepalen. De beschikbare opties zijn afhankelijk van de huidige weergave.

   ![ Inbox meningsmontages ](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>De inbox werkt als console, gebruik dus [Globale navigatie](/help/sites-cloud/authoring/basic-handling.md#global-navigation) of [Zoeken](/help/sites-cloud/authoring/search.md) om naar een andere locatie te gaan wanneer u klaar bent.

### Postvak IN - Lijstweergave {#inbox-list-view}

In deze weergave worden alle items weergegeven, samen met relevante informatie:

![ Inbox lijstmening ](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Postvak IN - Kalenderweergave {#inbox-calendar-view}

In deze weergave worden de items weergegeven op basis van hun positie in de kalender:

![ Inbox kalendermening ](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

U kunt:

* Selecteer een specifieke mening: **Chronologie**, **Kolom**, **Lijst**
* Geef de taken op die u wilt weergeven volgens **Planning**: **Alles**, **Gepland**, **In uitvoering**, **Vervalt binnenkort**, **Vervallen**
* Boor neer voor meer gedetailleerde informatie over een punt
* Selecteer een datumbereik waarop u de focus op de weergave wilt plaatsen:

![ Inbox de waaier van de de meningsdatum van de kalender ](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Postvak IN - Instellingen weergeven {#inbox-view-settings}

Voor beide weergaven (Lijst en Kalender) kunt u instellingen definiëren:

* **Kalenderweergave**

  Voor **Mening van de Kalender** kunt u vormen:

   * **Groep door**
   * **Planning** of **Geen**
   * **Grootte van de Kaart**

  ![ Inbox montages van de kalendermening van de Kalender ](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **de Mening van de Lijst**

  Voor **Mening van de Lijst** kunt u het soortmechanisme vormen:

   * **Soort op**
   * **de Orde van de Sortering**

  ![ Inbox de montages van de lijstmening ](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

  U kunt uw agenda ook delegeren aan andere gebruikers, vragen om delegatie van andere gebruikers en uw delegaties beheren.

  ![ Inbox de montages van de de lijstmening van de lijstdelegatie ](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Actie ondernemen op een item {#taking-action-on-an-item}

>[!NOTE]
>
>Hoewel het mogelijk is meerdere items te selecteren, kunnen acties slechts op één item tegelijk worden uitgevoerd.

1. Als u een actie wilt uitvoeren op een item, selecteert u de miniatuur voor het desbetreffende item. Pictogrammen voor de acties die op dat item van toepassing zijn, worden weergegeven op de werkbalk:

   ![ Uitgezochte inbox punt ](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   De acties zijn geschikt voor het item en omvatten:

   * **Volledige** actie
   * **Afgevaardigde** een punt
   * **Open** een punt, afhankelijk van het punttype deze actie kan:

      * Eigenschappen van item weergeven
      * Open een geschikt dashboard of een geschikte wizard voor verdere actie
      * Gerelateerde documentatie openen

   * **Stap terug** aan een vorige stap
   * De lading voor een werkstroom weergeven
   * Een project maken van het item

   >[!NOTE]
   >
   >Raadpleeg de volgende secties voor meer informatie:
   >
   >* De punten van het werkschema - [ Deelnemend aan Werkschema&#39;s ](/help/sites-cloud/authoring/workflows/participating.md)

2. Afhankelijk van het geselecteerde item wordt een handeling gestart, bijvoorbeeld:

   * Er wordt een dialoogvenster geopend dat geschikt is voor de handeling
   * Een wizard Handelingen is gestart
   * Er wordt een documentatiepagina geopend

   Bijvoorbeeld, **Afgevaardigde** opent een dialoog:

   ![ Delegate inbox taak ](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Afhankelijk van of een dialoogvenster, wizard, documentatiepagina is geopend, kunt u:

   * Bevestig de juiste handeling, bijvoorbeeld opnieuw toewijzen.
   * De handeling annuleren
   * Selecteer de pijl Vorige om terug te keren naar het Postvak IN. Als bijvoorbeeld een handelingstovenaar of documentatiepagina is geopend, kunt u terugkeren naar het Postvak In.

## Een taak maken {#creating-a-task}

In het Postvak IN kunt u taken maken:

1. Selecteer **creeer**, toen **Taak**.
1. Vul de vereiste velden in op de tabbladen **Standaard** en **Geavanceerd** (alleen de **Titel** is verplicht, alle andere velden zijn optioneel):

   * **Basis**:

      * **Titel**
      * **Project**
      * **Geadresseerde**
      * **Inhoud**, gelijkend op Payload, is dit een verwijzing van de taak aan een plaats in de bewaarplaats
      * **Beschrijving**
      * **Prioriteit van de Taak**
      * **Datum van het Begin**
      * **Vervaldatum**

   ![ binnen voegt taak ](/help/sites-cloud/authoring/assets/inbox-create-task.png) toe

   * **Geavanceerd**

      * **Naam**: Gebruikt om URL te vormen en als het leeg is gebaseerd op de **Titel**.

   ![ binnen voegt taak geavanceerde opties ](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png) toe

1. Selecteer **voorleggen**.

## Een project maken {#creating-a-project}

Voor bepaalde taken kunt u a [ Project ](/help/sites-cloud/authoring/projects/overview.md) creëren dat op die taak wordt gebaseerd:

1. Selecteer de gewenste taak door op de miniatuur te tikken of te klikken.

   >[!NOTE]
   >
   >Slechts kunnen de taken die gebruikend **worden gecreeerd** optie van **binnen** worden gecreeerd om een project tot stand te brengen.
   >
   >Werkitems (vanuit een workflow) kunnen niet worden gebruikt om een project te maken.

1. Selecteer **Project maken** op de werkbalk om de wizard te openen.
1. Selecteer het aangewezen malplaatje, toen **daarna**.
1. Geef de vereiste eigenschappen op:

   * **Basis**

      * **Titel**
      * **Beschrijving**
      * **Datum van het Begin**
      * **Vervaldatum**
      * **Gebruiker** en rol

   * **Geavanceerd**

      * **Naam**

   >[!NOTE]
   >
   >Zie [ Creërend een Project ](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) voor volledige informatie.

1. Selecteer **creeer** om de actie te bevestigen.

## Items in AEM Postvak IN filteren {#filtering-items-in-the-aem-inbox}

U kunt de vermelde items filteren:

1. Open **AEM Inbox**.

1. Open de filterkiezer:

   ![ Inbox onderzoek ](/help/sites-cloud/authoring/assets/inbox-search.png)

1. U kunt de vermelde items filteren op basis van een reeks criteria, waarvan er vele kunnen worden verfijnd. Bijvoorbeeld:

   ![ Inbox onderzoeksfilter ](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >Met [ Montages van de Mening ](#inbox-view-settings) kunt u de soortorde ook vormen wanneer het gebruiken van de [ Mening van de Lijst ](#inbox-list-view).
