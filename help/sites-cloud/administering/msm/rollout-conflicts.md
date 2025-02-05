---
title: Conflicten bij rollout
description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt beheren en oplossen.
feature: Multi Site Manager
role: Admin
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
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

In de volgende secties wordt een voorbeeld van een nieuwe pagina `b` gebruikt, die in zowel de blauwdruk als de (manueel gemaakte) vertakking Live Copy is gemaakt, om de verschillende methoden voor conflictoplossing te illustreren:

* blauwdruk: `/b`

  Een basispagina met één onderliggende pagina, `bp-level-1`

* Live kopie: `/b`

  Een pagina die handmatig is gemaakt in de vertakking Live kopie met één onderliggende pagina, `lc-level-1`

   * Geactiveerd bij publicatie als `/b` , samen met de onderliggende pagina

#### Voor rollout {#before-rollout}

|  | Vervagen voor rollout | Actieve kopie voor rollout | Publish Voor rollout |
|---|---|---|---|
| Waarde | `b` | `b` | `b` |
| Opmerking | Gemaakt in vertakking Vervagen, klaar voor rollout | Handmatig gemaakt in de vertakking Live kopie | Bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie |
| Waarde | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  | Handmatig gemaakt in de vertakking Live kopie | bevat de inhoud van de pagina `child-level-1` die handmatig is gemaakt in de vertakking Live kopie. |

## Rolloutbeheer en Conflict-verwerking {#rollout-manager-and-conflict-handling}

Met de rollout Manager kunt u conflictbeheer activeren of deactiveren.

Dit wordt gedaan gebruikend [ configuratie OSGi ](/help/implementing/deploying/configuring-osgi.md) van **de Manager van de Uitvoer van CQ WCM van de Dag**. Plaats het van de waarde{**handvat conflict met manueel gecreeerde Pagina&#39;s** ( `rolloutmgr.conflicthandling.enabled`) aan waar als de rollout manager conflicten van een pagina zou moeten behandelen die in Levend Exemplaar met een naam wordt gecreeerd die in de blauwdruk bestaat.

AEM heeft [ vooraf bepaald gedrag wanneer het conflictbeheer ](#behavior-when-conflict-handling-deactivated) is gedeactiveerd.

## Conflicthandlers {#conflict-handlers}

AEM gebruikt conflicthandlers om eventuele pagineconflicten op te lossen die bestaan wanneer inhoud van een blauwdruk aan Levend Exemplaar wordt uitrollen. De naam van pagina&#39;s wijzigen is de gebruikelijke (niet alleen) methode voor het oplossen van dergelijke conflicten. Er kunnen meerdere conflicthandlers operationeel zijn, zodat u verschillende gedragingen kunt selecteren.

AEM biedt:

* De [ standaardconflictmanager ](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* De mogelijkheid om a [ aangepaste manager ](#customized-handlers) uit te voeren
* Het de dienstrangschikkingsmechanisme dat u de prioriteit van elke individuele manager laat plaatsen
   * De dienst met het hoogste rangschikken wordt gebruikt.

### Standaardconflicthandler {#default-conflict-handler}

De standaardconflicthandler is `ResourceNameRolloutConflictHandler`

* Met deze handler krijgt de blauwdrukpagina prioriteit.
* De dienst die voor deze manager rangschikt wordt geplaatst laag. Dat wil zeggen, onder de standaardwaarde voor de eigenschap `service.ranking` omdat wordt aangenomen dat aangepaste handlers een hogere positie nodig hebben. De rangorde is echter niet het absolute minimum om zo nodig flexibiliteit te garanderen.

Deze conflicthandler geeft voorrang aan de blauwdruk. De pagina Live kopie `/b` wordt bijvoorbeeld binnen de vertakking Live kopie verplaatst naar `/b_msm_moved` .

* Live kopie: `/b`

  Wordt verplaatst binnen de live kopie naar `/b_msm_moved` . Dit fungeert als back-up en zorgt ervoor dat er geen inhoud verloren gaat.

   * `lc-level-1` wordt niet verplaatst.

* Blauwdruk: `/b`

  Wordt uitgevouwen naar de pagina Live kopie `/b` .

   * `bp-level-1` wordt uitgerold naar de live kopie.

#### Na rollout {#after-rollout}

|  | Vervagen na rollout | Live kopie na rollout | Live kopie na rollout | Publish After Rollout |
|---|---|---|---|---|
| Waarde | `b` | `b` | `b_msm_moved` | `b` |
| Opmerking |  | Bevat de inhoud van de verfpagina `b` die is uitgevouwen | Bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie | Geen wijziging; bevat de inhoud van de oorspronkelijke pagina `b` die handmatig is gemaakt in de vertakking Live kopie en nu ook `b_msm_moved` wordt genoemd |
| Waarde | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  |  | Geen wijziging | Geen wijziging |

### Aangepaste handlers {#customized-handlers}

De aangepaste conflictmanagers staan u toe om uw eigen regels uit te voeren. Gebruikend het de dienstrangschikkingsmechanisme kunt u ook bepalen hoe zij met andere managers in wisselwerking staan.

Aangepaste conflicthandlers kunnen:

* Geef een naam op basis van uw vereisten.
* Ontwikkeld/geconfigureerd worden volgens uw vereisten.
   * U kunt bijvoorbeeld een handler ontwikkelen die voorrang geeft aan de pagina Live kopie.
* Het kan worden gevormd gebruikend de [ configuratie OSGi ](/help/implementing/deploying/configuring-osgi.md). In het bijzonder:
   * **het Rangschikken van de Dienst** bepaalt de orde met betrekking tot andere conflictmanagers ( `service.ranking`).
      * De standaardwaarde is `0` .

### Gedrag wanneer Conflict afhandelen is gedeactiveerd {#behavior-when-conflict-handling-deactivated}

Als u manueel [ conflicten behandeling ](#rollout-manager-and-conflict-handling) deactiveert, neemt AEM geen actie op om het even welke conflicterende pagina&#39;s. Niet-conflicterende pagina&#39;s worden naar behoren geïmplementeerd.

>[!CAUTION]
>
>Wanneer conflictafhandeling wordt gedeactiveerd, geeft AEM geen enkele aanwijzing dat conflicten worden genegeerd. Aangezien in dergelijke gevallen dit gedrag uitdrukkelijk moet worden gevormd, wordt aangenomen dat het het gewenste gedrag is.

In dit geval heeft Live Copy in feite voorrang. De pagina met de blauwdruk `/b` wordt niet gekopieerd en de pagina Live kopie `/b` blijft ongewijzigd.

* Blauwdruk: `/b`

  Het wordt helemaal niet gekopieerd, maar wordt genegeerd.

* Live kopie: `/b`

  Het blijft hetzelfde.

#### Na rollout {#after-rollout-no-conflict}

|  | Vervagen na rollout | Live kopie na rollout | Publish After Rollout |
|---|---|---|---|
| Waarde | `b` | `b` | `b` |
| Opmerking |  | Geen wijziging; heeft de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie | Geen wijziging; bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie |
| Waarde | `/bp-level-1,` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  | Geen wijziging | Geen wijziging |

### Servicebeoordelingen {#service-rankings}

De [ OSGi ](https://www.osgi.org/) dienst rangschikt kan worden gebruikt om de prioriteit van individuele conflictmanagers te bepalen.
