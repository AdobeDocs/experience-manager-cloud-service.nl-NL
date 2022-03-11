---
title: Bedekkingen voor Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service gebruikt het principe van overlays om de consoles en andere functionaliteit uit te breiden en aan te passen
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: ac760e782f80ee82a9b0604ef64721405fc44ee4
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---

# Overlays in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service gebruikt het principe van overlays om consoles en andere functies (bijvoorbeeld paginaontwerp) uit te breiden en aan te passen.

Bedekking is een term die in veel contexten kan worden gebruikt. In deze context (uitbreiden AEM as a Cloud Service) betekent een overlay dat u de vooraf gedefinieerde functionaliteit overneemt en dat u uw eigen definities daarop legt (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit onder gehouden `/libs` en het wordt aanbevolen om uw bedekking (aanpassingen) onder de `/apps` vertakking (met een [zoekpad](#search-paths) om de bronnen op te lossen).

* De interface met aanraakbediening gebruikt [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)-gerelateerde overlays:

   * Methode

      * Reconstrueren `/libs` structuur onder `/apps`.

         Hiervoor is geen 1:1-kopie nodig, aangezien de [Samenvoegen van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md) wordt gebruikt voor kruisverwijzingen naar de oorspronkelijke definities die vereist zijn. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen door (het differentiëren) mechanismen af te schilderen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs`.
      * Alleen opnieuw definiëren wat werkelijk vereist is.


>[!CAUTION]
>
>De [Samenvoegen van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md) en de bijbehorende methoden mogen alleen worden gebruikt met [Graniet](https://www.adobe.io/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.

Bedekkingen zijn de aanbevolen methode voor vele wijzigingen, zoals het configureren van de consoles of het maken van uw selectiecategorie in de middelenbrowser in het zijpaneel (wordt gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* U ***mogen* wijzigingen aanbrengen in de `/libs` vertakking **Wijzigingen die u aanbrengt, kunnen verloren gaan omdat deze vertakking kan veranderen wanneer upgrades op uw instantie worden toegepast.

* Ze concentreren uw wijzigingen op één locatie. het voor u gemakkelijker maken om uw wijzigingen te volgen, te migreren, er een back-up van te maken en/of er fouten in op te sporen.

## Paden zoeken {#search-paths}

AEM gebruikt een zoekpad om een bron te zoeken, waarbij (standaard) eerst wordt gezocht in de `/apps` vertakt en vervolgens `/libs` vertakking. Dit mechanisme betekent dat uw bedekking in `/apps` (en de aanpassingen die daar worden bepaald) zullen prioriteit hebben.

Voor bekledingen is het geleverde middel een aggregaat van de middelen en eigenschappen die, afhankelijk van onderzoekswegen worden teruggewonnen die in de configuratie OSGi worden bepaald.
