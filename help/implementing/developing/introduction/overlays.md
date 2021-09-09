---
title: Bedekkingen voor Adobe Experience Manager als Cloud Service
description: AEM als Cloud Service gebruikt het principe van overlays zodat u consoles en andere functies kunt uitbreiden en aanpassen
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: ac760e782f80ee82a9b0604ef64721405fc44ee4
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---

# Overlays in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager als Cloud Service gebruikt het principe van overlays om de consoles en andere functies (bijvoorbeeld paginaontwerp) uit te breiden en aan te passen.

Bedekking is een term die in veel contexten kan worden gebruikt. In deze context (het uitbreiden van AEM als Cloud Service) betekent een bekleding het nemen van de vooraf bepaalde functionaliteit en het opleggen van uw eigen definities over dat (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit gehouden onder `/libs` en het wordt aanbevolen om uw bedekking (aanpassingen) te definiëren onder de `/apps`-vertakking (met een [zoekpad](#search-paths) om de bronnen op te lossen).

* De interface met aanraakbediening gebruikt [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)-gerelateerde overlays:

   * Methode

      * Reconstrueer de aangewezen `/libs` structuur onder `/apps`.

         Dit vereist geen 1:1 exemplaar, aangezien [Sling het Samenvoegen van het Middel ](/help/implementing/developing/introduction/sling-resource-merger.md) wordt gebruikt om de originele definities te verwijzen die worden vereist. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen door (het differentiëren) mechanismen af te schilderen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs`.
      * Alleen opnieuw definiëren wat werkelijk vereist is.


>[!CAUTION]
>
>De [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) en de verwante methoden kunnen alleen worden gebruikt met [Granite](https://www.adobe.io/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.

Bedekkingen zijn de aanbevolen methode voor veel wijzigingen, zoals het configureren van de consoles of het maken van de selectiecategorie in de middelenbrowser in het zijpaneel (wordt gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* U ***mag niet* wijzigingen aanbrengen in de `/libs`-vertakking **Wijzigingen die u aanbrengt, kunnen verloren gaan omdat deze vertakking kan veranderen wanneer upgrades op uw instantie worden toegepast.

* Ze concentreren uw wijzigingen op één locatie. het voor u gemakkelijker maken om uw wijzigingen te volgen, te migreren, er een back-up van te maken en/of er fouten in op te sporen.

## Paden zoeken {#search-paths}

AEM gebruikt een onderzoekspad om een middel te vinden, zoekend (door gebrek) eerst de `/apps` tak en toen `/libs` tak. Dit mechanisme betekent dat uw overlay in `/apps` (en de aanpassingen die daar worden bepaald) prioriteit zal hebben.

Voor bekledingen is het geleverde middel een aggregaat van de middelen en eigenschappen die, afhankelijk van onderzoekswegen worden teruggewonnen die in de configuratie OSGi worden bepaald.
