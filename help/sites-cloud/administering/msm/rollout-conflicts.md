---
title: Conflicten bij rollout
description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt beheren en oplossen.
feature: Multi Site Manager
role: Admin
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 0%

---

# Conflicten bij rollout {#msm-rollout-conflicts}

Er kunnen conflicten optreden als er nieuwe pagina&#39;s met dezelfde paginanaam worden gemaakt in zowel de vertakking Verfafdruk als een afhankelijke vertakking Live kopie. Dergelijke conflicten moeten bij de uitrol worden afgehandeld en opgelost.

## Conflictbehandeling {#conflict-handling}

Wanneer conflicterende pagina&#39;s wel bestaan (in de vertakkingen Bladeren en Actieve kopie), kunt u met MSM definiëren hoe (of zelfs als) deze moeten worden verwerkt.

Om ervoor te zorgen dat de rollout niet wordt geblokkeerd, kunnen mogelijke definities omvatten:

* Welke pagina (blauwdruk of Live kopie) prioriteit heeft tijdens de rollout
* Welke pagina&#39;s worden hernoemd en hoe
* Hoe dit invloed heeft op gepubliceerde inhoud

Het standaardgedrag van Adobe Experience Manager (AEM) is dat gepubliceerde inhoud niet wordt beïnvloed. Dus als een pagina die handmatig is gemaakt in de vertakking Live kopie is gepubliceerd, wordt die inhoud nog steeds gepubliceerd na de conflictafhandeling en -rollout.

Naast de standaardfunctionaliteit, kunnen de aangepaste conflicthandlers worden toegevoegd om verschillende regels uit te voeren. Hierdoor kunnen publicatiehandelingen ook als een afzonderlijk proces worden toegestaan.

### Voorbeeldscenario {#example-scenario}

In de volgende secties, een voorbeeld van een nieuwe pagina `b` wordt gebruikt en gemaakt in zowel de blauwdruk als de vertakking Live kopie (handmatig gemaakt) om de verschillende methoden voor het oplossen van conflicten te illustreren:

* blauwdruk: `/b`

  Een basispagina met één onderliggende pagina, `bp-level-1`

* Live kopie: `/b`

  Een pagina die handmatig in de vertakking Live kopie is gemaakt met één onderliggende pagina, `lc-level-1`

   * Geactiveerd bij publiceren als `/b`, samen met de onderliggende pagina

#### Voor rollout {#before-rollout}

|  | Vervagen voor rollout | Actieve kopie voor rollout | Publiceren vóór rollout |
|---|---|---|---|
| Waarde | `b` | `b` | `b` |
| Opmerking | Gemaakt in vertakking Vervagen, klaar voor rollout | Handmatig gemaakt in de vertakking Live kopie | Bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie |
| Waarde | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  | Handmatig gemaakt in de vertakking Live kopie | bevat de inhoud van de pagina `child-level-1` die handmatig is gemaakt in de vertakking Live kopie |

## Rolloutbeheer en Conflict-verwerking {#rollout-manager-and-conflict-handling}

Met de rollout Manager kunt u conflictbeheer activeren of deactiveren.

Dit gebeurt met [OSGi-configuratie](/help/implementing/deploying/configuring-osgi.md) van **Day CQ WCM-implementatiebeheer**. De waarde instellen **Conflict met handmatig gemaakte pagina&#39;s afhandelen** ( `rolloutmgr.conflicthandling.enabled`) wordt ingesteld op true als de rollout manager conflicten moet verwerken met een pagina die is gemaakt in Live Copy met een naam die voorkomt in de blauwdruk.

AEM heeft [vooraf gedefinieerd gedrag wanneer conflictbeheer is gedeactiveerd.](#behavior-when-conflict-handling-deactivated)

## Conflicthandlers {#conflict-handlers}

AEM gebruikt conflicthandlers om eventuele pagineconflicten op te lossen die bestaan wanneer inhoud van een blauwdruk aan Levend Exemplaar wordt uitrollen. De naam van pagina&#39;s wijzigen is de gebruikelijke (niet alleen) methode voor het oplossen van dergelijke conflicten. Er kunnen meerdere conflicthandlers operationeel zijn, zodat u verschillende gedragingen kunt selecteren.

AEM biedt:

* De [default conflict handler](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* De mogelijkheid om een [aangepaste handler](#customized-handlers)
* Het de dienstrangschikkingsmechanisme dat u de prioriteit van elke individuele manager laat plaatsen
   * De dienst met het hoogste rangschikken wordt gebruikt.

### Standaardconflicthandler {#default-conflict-handler}

De standaardconflicthandler is `ResourceNameRolloutConflictHandler`

* Met deze handler krijgt de blauwdrukpagina prioriteit.
* De dienst die voor deze manager rangschikt wordt geplaatst laag. Dat wil zeggen, onder de standaardwaarde voor de `service.ranking` bezit omdat de veronderstelling is dat de aangepaste managers een hogere rangschikking nodig hebben. De rangorde is echter niet het absolute minimum om zo nodig flexibiliteit te garanderen.

Deze conflicthandler geeft voorrang aan de blauwdruk. Bijvoorbeeld de pagina Live kopie `/b` wordt verplaatst binnen de vertakking Live kopie naar `/b_msm_moved`.

* Live kopie: `/b`

  Wordt verplaatst binnen de live kopie naar `/b_msm_moved`. Dit fungeert als back-up en zorgt ervoor dat er geen inhoud verloren gaat.

   * `lc-level-1` wordt niet verplaatst.

* Blauwdruk: `/b`

  Is uitgevouwen naar de pagina Live kopie `/b`.

   * `bp-level-1` wordt uitgerold naar de live kopie.

#### Na rollout {#after-rollout}

|  | Vervagen na rollout | Live kopie na rollout | Live kopie na rollout | Publiceren na rollout |
|---|---|---|---|---|
| Waarde | `b` | `b` | `b_msm_moved` | `b` |
| Opmerking |  | Bevat de inhoud van de pagina Bladeren `b` dat is uitgevoerd | Bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie | Geen wijziging; bevat de inhoud van de oorspronkelijke pagina `b` die handmatig is gemaakt in de vertakking Live kopie en nu wordt aangeroepen `b_msm_moved` |
| Waarde | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  |  | Geen wijziging | Geen wijziging |

### Aangepaste handlers {#customized-handlers}

De aangepaste conflictmanagers staan u toe om uw eigen regels uit te voeren. Gebruikend het de dienstrangschikkingsmechanisme kunt u ook bepalen hoe zij met andere managers in wisselwerking staan.

Aangepaste conflicthandlers kunnen:

* Geef een naam op basis van uw vereisten.
* Ontwikkeld/geconfigureerd worden volgens uw vereisten.
   * U kunt bijvoorbeeld een handler ontwikkelen die voorrang geeft aan de pagina Live kopie.
* Het kan worden gevormd gebruikend [OSGi-configuratie](/help/implementing/deploying/configuring-osgi.md). In het bijzonder:
   * **Servicereeks** definieert de volgorde voor andere conflicthandlers ( `service.ranking`).
      * De standaardwaarde is `0`.

### Gedrag wanneer Conflict afhandelen is gedeactiveerd {#behavior-when-conflict-handling-deactivated}

Als u handmatig [conflictafhandeling deactiveren,](#rollout-manager-and-conflict-handling) AEM onderneemt geen actie op conflicterende pagina&#39;s. Niet-conflicterende pagina&#39;s worden naar behoren geïmplementeerd.

>[!CAUTION]
>
>Wanneer conflictafhandeling wordt gedeactiveerd, geeft AEM geen enkele aanwijzing dat conflicten worden genegeerd. Aangezien in dergelijke gevallen dit gedrag uitdrukkelijk moet worden gevormd, wordt aangenomen dat het het gewenste gedrag is.

In dit geval heeft Live Copy in feite voorrang. De blauwdrukpagina `/b` wordt niet gekopieerd en de pagina Live Copy `/b` onaangeroerd blijft.

* Blauwdruk: `/b`

  Het wordt helemaal niet gekopieerd, maar wordt genegeerd.

* Live kopie: `/b`

  Het blijft hetzelfde.

#### Na rollout {#after-rollout-no-conflict}

|  | Vervagen na rollout | Live kopie na rollout | Publiceren na rollout |
|---|---|---|---|
| Waarde | `b` | `b` | `b` |
| Opmerking |  | Geen wijziging; heeft de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie | Geen wijziging; bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie |
| Waarde | `/bp-level-1,` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  | Geen wijziging | Geen wijziging |

### Servicebeoordelingen {#service-rankings}

De [OSGi](https://www.osgi.org/) de dienst rangschikt kan worden gebruikt om de prioriteit van individuele conflictmanagers te bepalen.
