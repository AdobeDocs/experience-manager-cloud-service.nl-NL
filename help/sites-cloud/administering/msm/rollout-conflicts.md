---
title: Conflicten bij rollout
description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt beheren en oplossen.
feature: Multi Site Manager
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 1%

---


# Uitrolconflicten {#msm-rollout-conflicts}

Er kunnen conflicten optreden als er nieuwe pagina&#39;s met dezelfde paginanaam worden gemaakt in zowel de vertakking Verfafdruk als een afhankelijke vertakking Live kopie. Dergelijke conflicten moeten bij de uitrol worden afgehandeld en opgelost.

## Conflictverwerking {#conflict-handling}

Wanneer conflicterende pagina&#39;s wel bestaan (in de vertakkingen Bladeren en Actieve kopie), kunt u met MSM definiëren hoe (of zelfs als) deze moeten worden verwerkt.

Om ervoor te zorgen dat de rollout niet wordt geblokkeerd, kunnen mogelijke definities omvatten:

* Welke pagina (blauwdruk of Live kopie) prioriteit krijgt tijdens de rollout
* Welke pagina&#39;s worden hernoemd (en hoe)
* Hoe dit effect heeft op gepubliceerde inhoud

Het standaardgedrag van AEM out-of-the-box is dat gepubliceerde inhoud niet wordt beïnvloed. Dus als een pagina die handmatig is gemaakt in de vertakking Live kopie is gepubliceerd, wordt die inhoud nog steeds gepubliceerd na de conflictafhandeling en -rollout.

Naast de standaardfunctionaliteit, kunnen de aangepaste conflicthandlers worden toegevoegd om verschillende regels uit te voeren. Hierdoor kunnen publicatiehandelingen ook als een afzonderlijk proces worden toegestaan.

### Voorbeeldscenario {#example-scenario}

In de volgende secties gebruiken wij het voorbeeld van een nieuwe pagina `b`, die in zowel de blauwdruk als de Levende (manueel gecreeerd) tak van het Exemplaar wordt gecreeerd, om de diverse methodes van conflictoplossing te illustreren:

* blauwdruk: `/b`

   Een master pagina met 1 onderliggende pagina, `bp-level-1`

* Live kopie: `/b`

   Een pagina die handmatig is gemaakt in de vertakking Live kopie met 1 onderliggende pagina, `lc-level-1`

   * Geactiveerd bij publicatie als `/b`, samen met de onderliggende pagina

#### Voor rollout {#before-rollout}

|  | Vervagen voor rollout | Actieve kopie voor rollout | Publiceren vóór rollout |
|---|---|---|---|
| Waarde | `b` | `b` | `b` |
| Opmerking | Gemaakt in vertakking Vervagen, klaar voor rollout | Handmatig gemaakt in de vertakking Live kopie | Bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie |
| Waarde | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  | Handmatig gemaakt in de vertakking Live kopie | bevat de inhoud van de pagina `child-level-1` die handmatig is gemaakt in de vertakking Live kopie |

## Uitrolbeheer en Conflict-verwerking {#rollout-manager-and-conflict-handling}

Met de rollout Manager kunt u conflictbeheer activeren of deactiveren.

Dit wordt gedaan gebruikend [OSGi configuratie](/help/implementing/deploying/configuring-osgi.md) van **Dag CQ WCM de Manager van de Uitvoer**. Stel de waarde **Conflict verwerken met handmatig gemaakte pagina&#39;s** ( `rolloutmgr.conflicthandling.enabled`) in op true als de rollout Manager conflicten moet afhandelen van een pagina die is gemaakt in Live Copy met een naam die voorkomt in de blauwdruk.

AEM heeft [vooraf gedefinieerd gedrag wanneer het conflictbeheer is gedeactiveerd.](#behavior-when-conflict-handling-deactivated)

## Conflicthandlers {#conflict-handlers}

AEM gebruikt conflicthandlers om eventuele pagineconflicten op te lossen die bestaan wanneer inhoud van een blauwdruk aan Levend Exemplaar wordt uitrollen. De naam van pagina&#39;s wijzigen is de gebruikelijke (niet alleen) methode voor het oplossen van dergelijke conflicten. Er kunnen meerdere conflicthandlers operationeel zijn, zodat u verschillende gedragingen kunt selecteren.

AEM biedt:

* De [standaardconflicthandler](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* De mogelijkheid om een [aangepaste manager](#customized-handlers) uit te voeren
* Het de dienstrangschikkingsmechanisme dat u toestaat om de prioriteit van elke individuele manager te plaatsen
   * De dienst met het hoogste rangschikken wordt gebruikt.

### Standaardconflicthandler {#default-conflict-handler}

De standaardconflicthandler is `ResourceNameRolloutConflictHandler`

* Met deze handler krijgt de blauwdrukpagina prioriteit.
* De de dienstrangschikking voor deze manager wordt geplaatst laag, d.w.z. onder de standaardwaarde voor het `service.ranking` bezit, aangezien de veronderstelling is dat de aangepaste managers een hogere rangschikking zullen vereisen. De rangorde is echter niet het absolute minimum om zo nodig flexibiliteit te garanderen.

Deze conflicthandler geeft voorrang aan de blauwdruk. De pagina Live kopie `/b` wordt bijvoorbeeld verplaatst binnen de vertakking Live kopie naar `/b_msm_moved`.

* Live kopie: `/b`

   Wordt verplaatst binnen de actieve kopie naar `/b_msm_moved`. Dit fungeert als back-up en zorgt ervoor dat er geen inhoud verloren gaat.

   * `lc-level-1` wordt niet verplaatst.

* Blauwdruk: `/b`

   Wordt uitgevouwen naar de pagina Live kopie `/b`.

   * `bp-level-1` wordt uitgerold naar de live kopie.

#### Na rollout {#after-rollout}

|  | Vervagen na rollout | Live kopie na rollout | Live kopie na rollout | Publiceren na rollout |
|---|---|---|---|---|
| Waarde | `b` | `b` | `b_msm_moved` | `b` |
| Opmerking |  | Bevat de inhoud van de pagina `b` die is uitgevouwen | Bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie | Geen wijziging, bevat de inhoud van de oorspronkelijke pagina `b` die handmatig is gemaakt in de vertakking Live kopie en nu `b_msm_moved` wordt aangeroepen |
| Waarde | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  |  | Geen wijziging | Geen wijziging |

### Aangepaste handlers {#customized-handlers}

De aangepaste conflictmanagers staan u toe om uw eigen regels uit te voeren. Gebruikend het de dienstrangschikkingsmechanisme kunt u ook bepalen hoe zij met andere managers in wisselwerking staan.

Aangepaste conflicthandlers kunnen:

* Geef een naam op basis van uw vereisten.
* Ontwikkeld/geconfigureerd worden volgens uw vereisten.
   * U kunt bijvoorbeeld een handler ontwikkelen die voorrang geeft aan de pagina Live kopie.
* Kan worden ontworpen om worden gevormd gebruikend [OSGi configuratie](/help/implementing/deploying/configuring-osgi.md). In het bijzonder:
   * **De** Rankingdefinitie van de dienst bepaalt de orde met betrekking tot andere conflictmanagers (  `service.ranking`).
      * De standaardwaarde is `0`.

### Gedrag wanneer Conflict verwerken wordt gedeactiveerd {#behavior-when-conflict-handling-deactivated}

Als u handmatig [conflictafhandeling deactiveert, voert ](#rollout-manager-and-conflict-handling) AEM geen actie op conflicterende pagina&#39;s. Niet-conflicterende pagina&#39;s worden naar behoren geïmplementeerd.

>[!CAUTION]
>
>Wanneer conflictafhandeling wordt gedeactiveerd, geeft AEM geen enkele aanwijzing dat conflicten worden genegeerd. Aangezien in dergelijke gevallen dit gedrag uitdrukkelijk moet worden gevormd, wordt aangenomen dat het het gewenste gedrag is.

In dit geval heeft Live Copy voorrang. De pagina `/b` wordt niet gekopieerd en de pagina `/b` van Live kopie blijft ongewijzigd.

* Blauwdruk: `/b`

   Wordt helemaal niet gekopieerd, maar wordt genegeerd.

* Live kopie: `/b`

   Dat blijft zo.

#### Na rollout {#after-rollout-no-conflict}

|  | Vervagen na rollout | Live kopie na rollout | Publiceren na rollout |
|---|---|---|---|
| Waarde | `b` | `b` | `b` |
| Opmerking |  | Geen wijziging, heeft de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie | Geen wijziging, bevat de inhoud van de pagina `b` die handmatig is gemaakt in de vertakking Live kopie |
| Waarde | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Opmerking |  | Geen wijziging | Geen wijziging |

### Servicerendeclaraties {#service-rankings}

De [OSGi](https://www.osgi.org/) de dienstrangschikking kan worden gebruikt om de prioriteit van individuele conflictmanagers te bepalen.
