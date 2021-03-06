---
title: Uw inbox
description: Taken beheren met de Postvak IN
exl-id: 37d0cf43-192f-4a50-b174-42d7dced3b63
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 15%

---

# Uw inbox {#your-inbox}

U kunt meldingen ontvangen van verschillende AEM, waaronder workflows en projecten. U ontvangt bijvoorbeeld meldingen over:

* Taken:
   * Deze kunnen ook op verschillende punten binnen AEM UI worden gecreeerd, bijvoorbeeld onder **Projecten**.
   * Dit kan het product zijn van een stap voor **Taak maken** of **Projecttaak maken** van een workflow.
* Workflows:
   * Werkitems die acties vertegenwoordigen die u moet uitvoeren op pagina-inhoud
      * Dit is het product van de workflow **Deelnemer** stappen.
   * Items mislukken, zodat beheerders de mislukte stap opnieuw kunnen proberen

U ontvangt deze meldingen in uw eigen Postvak IN waar u ze kunt bekijken en actie kunt ondernemen.

>[!NOTE]
>
>Zie ook voor meer informatie over de objecttypen:
>
>* [Projecten](/help/sites-cloud/authoring/projects/overview.md)
>* [Projecten - werken met taken](/help/sites-cloud/authoring/projects/tasks.md)
>* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)


## Postvak IN van koptekst {#inbox-in-the-header}

Van om het even welke consoles wordt het huidige aantal punten in uw inbox getoond in de kopbal. De indicator kan ook worden geopend om snel toegang te krijgen tot de pagina(&#39;s) waarvoor een actie(s) vereist is of om toegang te krijgen tot het Postvak IN:

![Overzicht van Postvak In koptekst](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Bepaalde acties worden ook weergegeven in de [kaartweergave van de juiste bron](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view).

## De Postvak IN openen {#opening-the-inbox}

U opent als volgt het AEM-vak:

1. Klik/tik op de indicator in de werkbalk.

1. Selecteer **Alles bekijken**. De **AEM Inbox** wordt geopend. In de inbox ziet u items uit workflows, projecten en taken.
1. De standaardweergave is [Lijstweergave](#inbox-list-view), maar u kunt ook schakelen naar [Kalenderweergave](#inbox-calendar-view). Dit gebeurt met de weergavekiezer (werkbalk, rechtsboven).

   Voor beide weergaven kunt u ook defini??ren [Instellingen weergeven](#inbox-view-settings). Welke opties beschikbaar zijn, is afhankelijk van de huidige weergave.

   ![Inbox-weergave-instellingen](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>De inbox werkt als console, gebruik dus [Globale navigatie](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) of [Zoeken](/help/sites-cloud/authoring/getting-started/search.md) om naar een andere locatie te gaan wanneer u klaar bent.

### Postvak IN - Lijstweergave {#inbox-list-view}

In deze weergave worden alle items weergegeven, samen met relevante informatie:

![Lijstweergave in vak](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Postvak IN - Kalenderweergave {#inbox-calendar-view}

In deze weergave worden de items weergegeven op basis van hun positie in de kalender:

![Kalenderweergave in postvak](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

U kunt:

* Selecteer een specifieke weergave: **Tijdlijn**, **Kolom**, **Lijst**
* Geef de taken op die u wilt weergeven volgens **Planning**: **Alles**, **Gepland**, **In uitvoering**, **Vervalt binnenkort**, **Vervallen**
* Boor neer voor meer gedetailleerde informatie over een punt
* Selecteer een datumbereik waarop u de focus op de weergave wilt plaatsen:

![Datumbereik van de kalenderweergave in Postvak In](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Postvak IN - Instellingen weergeven {#inbox-view-settings}

Voor beide weergaven (Lijst en Kalender) kunt u instellingen defini??ren:

* **Kalenderweergave**

   Voor **Kalenderweergave** u kunt configureren:

   * **Groeperen op**
   * **Planning** of **Geen**
   * **Kaartgrootte**

   ![Instellingen voor de postkalenderweergave in het vak](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Lijstweergave**

   Voor **Lijstweergave** u kunt het sorteermechanisme configureren:

   * **Sorteren op**
   * **Sorteervolgorde**

   ![Weergave-instellingen in de keuzelijst](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

   U kunt uw agenda ook delegeren aan andere gebruikers, u kunt verzoeken om delegatie van andere gebruikers en uw delegaties beheren.

   ![Instellingen voor delegatie van weergave in de keuzelijst](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Actie ondernemen op een item {#taking-action-on-an-item}

>[!NOTE]
>
>Hoewel het mogelijk is meerdere items te selecteren, kunnen acties slechts op ????n item tegelijk worden uitgevoerd.

1. Als u een actie wilt uitvoeren op een item, selecteert u de miniatuur voor het desbetreffende item. Pictogrammen voor de acties die op dat item van toepassing zijn, worden weergegeven op de werkbalk:

   ![Item in vak selecteren](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   De acties zijn geschikt voor het item en omvatten:

   * **Voltooid** action
   * **Delegeren** een item
   * **Openen** een item, afhankelijk van het type item dat deze handeling kan bevatten:

      * Eigenschappen van item weergeven
      * Open een geschikt dashboard of een geschikte wizard voor verdere actie
      * Gerelateerde documentatie openen
   * **Stap terug** naar een vorige stap
   * De lading voor een werkstroom weergeven
   * Een project maken van het item

   >[!NOTE]
   >
   >Zie voor meer informatie:
   >
   >* Workflowitems - [Deelnemen aan workflows](/help/sites-cloud/authoring/workflows/participating.md)


2. Afhankelijk van het geselecteerde item wordt een handeling gestart, bijvoorbeeld:

   * Er wordt een dialoog geopend die geschikt is voor de actie
   * Er wordt een wizard Handelingen gestart
   * Er wordt een documentatiepagina geopend

   Bijvoorbeeld: **Delegeren** wordt een dialoogvenster geopend:

   ![Inbox-taak delegeren](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Afhankelijk van of een dialoogvenster, wizard, documentatiepagina is geopend, kunt u:

   * Bevestig de juiste actie, bijvoorbeeld door opnieuw toe te wijzen.
   * De handeling annuleren
   * Selecteer de pijl Vorige om terug te keren naar het Postvak IN, bijvoorbeeld als een handelingstovenaar of documentatiepagina is geopend, kunt u terugkeren naar het Postvak In.


## Een taak maken {#creating-a-task}

In het Postvak IN kunt u taken maken:

1. Selecteren **Maken** vervolgens **Taak**.
1. Vul de vereiste velden in op de tabbladen **Standaard** en **Geavanceerd** (alleen de **Titel** is verplicht, alle andere velden zijn optioneel):

   * **Basis**:

      * **Titel**
      * **Project**
      * **Geadresseerde**
      * **Inhoud** Net als bij Payload is dit een verwijzing van de taak naar een locatie in de repository
      * **Beschrijving**
      * **Taakprioriteit**
      * **Begindatum**
      * **Vervaldatum**

   ![Inbox add task](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Geavanceerd**

      * **Naam**:Dit wordt gebruikt om de URL te vormen en als deze leeg is, wordt deze gebaseerd op de **Titel**.

   ![Geavanceerde opties voor Inbox Add task](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Selecteren **Verzenden**.

## Een project maken {#creating-a-project}

Voor bepaalde taken kunt u een [Project](/help/sites-cloud/authoring/projects/overview.md) op basis van die taak :

1. Selecteer de gewenste taak door op de miniatuur te tikken of te klikken.

   >[!NOTE]
   >
   >Alleen taken die zijn gemaakt met de opdracht **Maken** de **Inbox** kan worden gebruikt om een project tot stand te brengen.
   >
   >De punten van het werk (van een werkschema) kunnen niet worden gebruikt om een project tot stand te brengen.

1. Selecteer **Project maken** op de werkbalk om de wizard te openen.
1. Selecteer de gewenste sjabloon en **Volgende**.
1. Geef de vereiste eigenschappen op:

   * **Basis**

      * **Titel**
      * **Beschrijving**
      * **Begindatum**
      * **Vervaldatum**
      * **Gebruiker** en rol
   * **Geavanceerd**

      * **Naam**
   >[!NOTE]
   >
   >Zie [Een project maken](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) voor volledige informatie.

1. Selecteren **Maken** om de actie te bevestigen.

## Items in AEM Postvak IN filteren {#filtering-items-in-the-aem-inbox}

U kunt de vermelde items filteren:

1. Open de **AEM Postvak IN**.

1. Open de filterkiezer:

   ![Inbox-zoekopdracht](/help/sites-cloud/authoring/assets/inbox-search.png)

1. U kunt de vermelde items filteren op basis van een reeks criteria, waarvan er vele kunnen worden verfijnd. Bijvoorbeeld:

   ![Inbox-zoekfilter](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >Met [Instellingen weergeven](#inbox-view-settings) u kunt de sorteervolgorde ook configureren wanneer u de [Lijstweergave](#inbox-list-view).
