---
title: Console voor live kopiëren
description: Leer meer over de basisbeginselen van de overzichtsconsole van Live Copy om snel inzicht te krijgen in de status van uw actieve kopieën om inhoud te synchroniseren.
feature: Multi Site Manager
role: Admin
exl-id: 3ef7fbce-10a1-4b21-8486-d3c3706e537c
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 0%

---

# Console voor live kopiëren {#live-copy-overview-console}

De **Overzicht van live kopiëren** de console laat u toe:

* Overerving op een site weergeven/beheren.
   * De boomstructuur en de bijbehorende structuur van Actieve kopie samen met de overervingsstatus weergeven
   * De overervingsstatus wijzigen, zoals opschorten en hervatten
   * Vervaging en eigenschappen van Live Copy weergeven
* Voer rollout-handelingen uit.

## Het Live Copy-overzicht openen {#opening-the-live-copy-overview}

U kunt het Live Copy-overzicht openen via het volgende:

* [Referenties in het zijpaneel van een blauwdrukpagina (Sites-console)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [Eigenschappen van een blauwdrukpagina](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Verwijzingen naar een vervagingspagina {#references-to-a-blueprint-page}

De **Overzicht van live kopiëren** kan worden geopend vanuit de **Verwijzingen** zijpaneel van **Sites** console:

1. In de **Sites** console, [navigeer naar uw blauwdrukpagina en selecteer deze](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de **[Verwijzingen](/help/sites-cloud/authoring/basic-handling.md#references)** spoor en selecteer **Actieve kopieën**.

   ![Live kopie van referentiespoor](../assets/live-copy-references.png)

   >[!TIP]
   >
   >U kunt verwijzingen ook eerst openen en vervolgens de blauwdruk selecteren.

1. Selecteren **Overzicht van live kopiëren** om het overzicht van alle actieve kopieën met betrekking tot de geselecteerde blauwdruk weer te geven en te gebruiken.
1. Gebruiken **Sluiten** om te vertrekken en terug te keren naar de **Sites** console.

### Eigenschappen van een vervagingspagina {#properties-of-a-blueprint-page}

De **Overzicht van live kopiëren** kan worden geopend wanneer u de eigenschappen van een pagina met een blauwdruk bekijkt:

1. Openen **Eigenschappen** voor de juiste blauwdrukpagina.
1. Open de **Blauwdruk** tab - the **Overzicht van live kopiëren** Deze optie wordt weergegeven in de bovenste werkbalk:

   ![tabblad Eigenschappen van vervaging](../assets/live-copy-blueprint-tab.png)

1. Selecteren **Overzicht van live kopiëren** om het overzicht van alle actieve kopieën met betrekking tot de huidige blauwdruk weer te geven en te gebruiken.

1. Gebruiken **Sluiten** om te vertrekken en terug te keren naar de **Sites** console.

## Het Live Copy-overzicht gebruiken {#using-the-live-copy-overview}

De **Overzicht van live kopiëren** biedt een overzicht van de status van de actieve kopieën die betrekking hebben op de geselecteerde pagina.

![Het venster Overzicht van live kopiëren](../assets/live-copy-overview.png)

Een rollout hangt van de synchronisatieacties af die in de specifieke rollout configuratie worden bepaald. Sommige acties zijn afhankelijk van wijzigingen in de inhoud. Er zijn echter ook veel acties die niet afhankelijk zijn van wijzigingen in de inhoud, maar die afhankelijk zijn van gebeurtenissen zoals paginanactivering. Dergelijke gebeurtenissen wijzigen de inhoud niet, maar wijzigen wel de interne eigenschappen die betrekking hebben op de inhoud.

De statusvelden zijn ook afhankelijk van de synchronisatiehandelingen die zijn gedefinieerd in de specifieke rollout-configuratie en geven aan of dergelijke acties zijn uitgevoerd voor de blauwdruk of de Live Copy sinds de laatste geslaagde rollout. Een statusgebied zal slechts op de acties in de specifieke rollout configuratie wijzen. Als er nooit een actieve kopie is uitgevoerd zonder dat dit is gelukt, wordt de status altijd bijgewerkt.

Een rollout-configuratie wordt bijvoorbeeld gedefinieerd als `targetActivate`. Daarom zal een uitrol alleen afhankelijk zijn van activeringsgebeurtenissen. Het statusveld geeft alleen aan of er activeringsgebeurtenissen zijn opgetreden sinds de laatste geslaagde implementatie.

De **Overzicht van live kopiëren** kan ook worden gebruikt voor het uitvoeren van handelingen op Live Copy:

1. Open de **Overzicht van live kopiëren**.
1. Selecteer de gewenste blauwdruk of pagina Live kopie en de werkbalk wordt bijgewerkt om de beschikbare acties weer te geven. De [handelingen](overview.md#terms-used) afhankelijk van de vraag of u een [blauwdruk](#actions-for-a-blueprint-page) of [Live kopie](#actions-for-a-live-copy-page) pagina.

### Handelingen voor een vervagingspagina {#actions-for-a-blueprint-page}

Wanneer u een blauwdrukpagina selecteert, zijn de volgende acties beschikbaar:

![Handelingen voor het overzicht van live kopiëren voor een blauwdruk](../assets/live-copy-overview-actions-blueprint.png)

* **Bewerken** - Open de pagina met de blauwdruk om deze te bewerken.
* **[Uitrol](overview.md#rollout-and-synchronize)** - Voer een rollout uit om de wijzigingen van de bron naar Live kopie door te voeren.

### Handelingen voor een Live Copy-pagina {#actions-for-a-live-copy-page}

Wanneer u een pagina voor Live kopie selecteert, zijn de volgende acties beschikbaar:

![Acties in het kader van Live Copy-overzicht voor een live kopie](../assets/live-copy-overview-actions.png)

* **Bewerken** - Open de pagina Live kopie voor bewerking.
* **[Relatie status](#relationship-status)** - Informatie weergeven over de status en overerving.
* **[Synchroniseren](overview.md#rollout-and-synchronize)** - Synchroniseer een actieve kopie om wijzigingen van de bron naar de actieve kopie over te brengen.
* **[Herstellen](creating-live-copies.md#resetting-a-live-copy-page)** - Een pagina van Live kopie opnieuw instellen om alle annuleringen van overerving te verwijderen en de pagina terug te brengen naar dezelfde status als de bronpagina.
* **[Onderbreken](overview.md#suspending-and-cancelling-inheritance-and-synchronization)** - Hiermee deactiveert u tijdelijk de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina.
* **[Hervatten](creating-live-copies.md#resuming-inheritance-for-a-page)** - Met Hervatten kunt u een geschorste relatie herstellen.
* **[Loskoppelen](overview.md#detaching-a-live-copy)** - Hiermee wordt de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina permanent verwijderd.

## Relatie status {#relationship-status}

De **Relatie status** console heeft twee lusjes die een waaier van functionaliteit verstrekken.

* [Relatie status](#relationship-status-tab)
* [Live kopie](#live-copy-tab)

### Relatie status {#relationship-status-tab}

Dit tabblad bevat gedetailleerde informatie over de status van de relatie tussen de blauwdruk en Live kopie.

![Het tabblad Relatie-status](../assets/live-copy-relationship-status.png)

### Live kopie {#live-copy-tab}

Op dit tabblad kunt u de Live Copy-configuratie weergeven en bewerken.

![Tabblad Live kopiëren](../assets/live-copy-relationship-status-live-copy.png)
