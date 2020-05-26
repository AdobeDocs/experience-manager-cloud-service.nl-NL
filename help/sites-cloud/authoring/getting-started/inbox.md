---
title: Uw inbox
description: Taken beheren met de Postvak IN
translation-type: tm+mt
source-git-commit: 672f1483c017d791365173c91b0bee5c44c33535
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 15%

---


# Uw inbox {#your-inbox}

U kunt meldingen ontvangen van verschillende onderdelen van AEM, zoals workflows en projecten. U ontvangt bijvoorbeeld meldingen over:

* Taken:
   * Deze kunnen ook op diverse punten binnen AEM UI, bijvoorbeeld, onder **Projecten** worden gecreeerd.
   * Dit kan het product zijn van een stap voor **Taak maken** of **Projecttaak maken** van een workflow.
* Workflows:
   * Werkitems die acties vertegenwoordigen die u moet uitvoeren op pagina-inhoud
      * Dit is het product van de stappen van de werkstroom **Deelnemer** .
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
>Bepaalde acties zullen ook in de [kaartmening van het aangewezen middel](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view)worden getoond.

## De Postvak IN openen {#opening-the-inbox}

Het AEM-meldingsvak openen:

1. Klik/tik op de indicator in de werkbalk.

1. Selecteer **Alles bekijken**. De **AEM Inbox** wordt geopend. In de inbox ziet u items uit workflows, projecten en taken.
1. De standaardweergave is [Lijstweergave](#inbox-list-view), maar u kunt ook schakelen naar [Kalenderweergave](#inbox-calendar-view). Dit gebeurt met de weergavekiezer (werkbalk, rechtsboven).

   Voor beide weergaven kunt u ook [Weergave-instellingen](#inbox-view-settings)definiëren. Welke opties beschikbaar zijn, is afhankelijk van de huidige weergave.

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

* Selecteer een specifieke weergave: **Tijdlijn**, **kolom**, **lijst**
* Geef de taken op die u wilt weergeven volgens **Planning**: **Alles**, **Gepland**, **In uitvoering**, **Vervalt binnenkort**, **Vervallen**
* Boor neer voor meer gedetailleerde informatie over een punt
* Selecteer een datumbereik waarop u de focus op de weergave wilt plaatsen:

![Datumbereik van de kalenderweergave in Postvak In](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Postvak IN - Instellingen weergeven {#inbox-view-settings}

Voor beide weergaven (Lijst en Kalender) kunt u instellingen definiëren:

* **Kalenderweergave**

   Voor de **kalenderweergave** kunt u het volgende configureren:

   * **Groeperen op**
   * **Planning** of **Geen**
   * **Kaartgrootte**
   ![Instellingen voor de postkalenderweergave in het vak](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Lijstweergave**

   Voor de Mening **van de** Lijst kunt u het soortmechanisme vormen:

   * **Sorteren op**
   * **Sorteervolgorde**
   ![Weergave-instellingen in de keuzelijst](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

   U kunt uw agenda ook delegeren aan andere gebruikers, u kunt verzoeken om delegatie van andere gebruikers en uw delegaties beheren.

   ![Instellingen voor delegatie van weergave in de keuzelijst](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Actie ondernemen op een item {#taking-action-on-an-item}

>[!NOTE]
>
>Hoewel het mogelijk is meerdere items te selecteren, kunnen acties slechts op één item tegelijk worden uitgevoerd.

1. Als u een actie wilt uitvoeren op een item, selecteert u de miniatuur voor het desbetreffende item. Pictogrammen voor de acties die op dat item van toepassing zijn, worden weergegeven op de werkbalk:

   ![Item in vak selecteren](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   De acties zijn geschikt voor het item en omvatten:

   * **Voltooien** , actie
   * **Een item delegeren**
   * **Open** een item, afhankelijk van het type item dat deze handeling kan bevatten:

      * Eigenschappen van item weergeven
      * Open een geschikt dashboard of een geschikte wizard voor verdere actie
      * Gerelateerde documentatie openen
   * **Terug naar** een vorige stap
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
   Bijvoorbeeld, zal de **Afgevaardigde** een dialoog openen:

   ![Inbox-taak delegeren](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Afhankelijk van of een dialoogvenster, wizard, documentatiepagina is geopend, kunt u:

   * Bevestig de juiste actie, bijvoorbeeld door opnieuw toe te wijzen.
   * De handeling annuleren
   * Selecteer de pijl Vorige om terug te keren naar het Postvak IN, bijvoorbeeld als een handelingstovenaar of documentatiepagina is geopend, kunt u terugkeren naar het Postvak In.


## Een taak maken {#creating-a-task}

In het Postvak IN kunt u taken maken:

1. Selecteer **Maken**, dan **Taak**.
1. Vul de vereiste velden in op de tabbladen **Standaard** en **Geavanceerd** (alleen de **Titel** is verplicht, alle andere velden zijn optioneel):

   * **Standaard**:

      * **Titel**
      * **Project**
      * **Geadresseerde**
      * **Inhoud**, vergelijkbaar met Payload, is een verwijzing van de taak naar een locatie in de repository
      * **Beschrijving**
      * **Taakprioriteit**
      * **Begindatum**
      * **Vervaldatum**
   ![Inbox add task](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Geavanceerd**

      * **Naam**:Deze wordt gebruikt om de URL te vormen en als deze leeg is, wordt deze gebaseerd op de **Titel**.
   ![Geavanceerde opties voor Inbox Add task](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Selecteer **Verzenden**.

## Een project maken {#creating-a-project}

Voor bepaalde taken kunt u een [Project](/help/sites-cloud/authoring/projects/overview.md) tot stand brengen dat op die taak wordt gebaseerd:

1. Selecteer de gewenste taak door op de miniatuur te tikken of te klikken.

   >[!NOTE]
   >
   >Alleen taken die zijn gemaakt met de optie **Maken** van **Inbox** kunnen worden gebruikt om een project te maken.
   >
   >De punten van het werk (van een werkschema) kunnen niet worden gebruikt om een project tot stand te brengen.

1. Selecteer **Project maken** op de werkbalk om de wizard te openen.
1. Select the appropriate template, then **Next**.
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
   >Zie Een project [](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) maken voor volledige informatie.

1. Selecteer **Maken** om de handeling te bevestigen.

## Items in het Postvak IN filteren {#filtering-items-in-the-aem-inbox}

U kunt de vermelde items filteren:

1. Open het **AEM-vak**.

1. Open de filterkiezer:

   ![Inbox-zoekopdracht](/help/sites-cloud/authoring/assets/inbox-search.png)

1. U kunt de vermelde items filteren op basis van een reeks criteria, waarvan er vele kunnen worden verfijnd. Bijvoorbeeld:

   ![Inbox-zoekfilter](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >Met de Montages [van de](#inbox-view-settings) Mening kunt u de soortorde ook vormen wanneer het gebruiken van de Mening [van de](#inbox-list-view)Lijst.
