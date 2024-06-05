---
title: Bedekkingen voor Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service gebruikt het principe van overlays om de consoles en andere functionaliteit uit te breiden en aan te passen
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Bedekkingen in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service gebruikt het principe van overlays om consoles en andere functies (bijvoorbeeld paginaontwerp) uit te breiden en aan te passen.

Bedekking is een term die in veel contexten kan worden gebruikt. In dit verband betekent het uitbreiden van AEM as a Cloud Service een overlay dat u de vooraf gedefinieerde functionaliteit overneemt en er uw eigen definities op legt om de standaardfunctionaliteit aan te passen.

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit onder gehouden `/libs` en het wordt aanbevolen om uw bedekking (aanpassingen) onder de `/apps` vertakking (met een [zoekpad](#search-paths) om de bronnen op te lossen).

* De gebruikersinterface met aanraakbediening gebruikt [Graniet](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-gerelateerde overlays:

   * Methode

      * Reconstrueren de juiste `/libs` structuur onder `/apps`.

        Voor deze herstructurering is geen 1:1-kopie nodig omdat de [Samenvoeging van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md) wordt gebruikt voor kruisverwijzingen naar de oorspronkelijke definities die vereist zijn. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen met (het onderscheiden) mechanismen toegang te hebben en samen te voegen.

      * Onder `/apps`, brengt u wijzigingen aan.

   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs`.
      * Alleen opnieuw definiëren wat vereist is.

>[!CAUTION]
>
>De [Samenvoeging van verkoopbronnen](/help/implementing/developing/introduction/sling-resource-merger.md) en de bijbehorende methoden mogen alleen worden gebruikt met [Graniet](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Deze regel houdt in dat het maken van een overlay met een skeletstructuur alleen geschikt is voor de standaardgebruikersinterface met aanraakbediening.

Bedekkingen zijn de aanbevolen methode voor veel wijzigingen. Stel bijvoorbeeld dat u de consoles configureert of dat u de selectiecategorie maakt in de middelenbrowser in het zijpaneel (gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* **In de `/libs` vertakking, *niet* wijzigingen aanbrengen**
Wijzigingen die u aanbrengt, kunnen verloren gaan omdat deze vertakking kan veranderen wanneer upgrades op uw instantie worden toegepast.

* Zij concentreren uw veranderingen in één plaats, die het voor u gemakkelijker maken om uw veranderingen te volgen, te migreren, file, of te zuiveren zonodig.

## Paden zoeken {#search-paths}

AEM gebruikt een zoekpad om een bron te zoeken, waarbij standaard eerst wordt gezocht naar `/apps` vertakking en vervolgens de `/libs` vertakking. Dit mechanisme betekent dat uw bedekking in `/apps` (en de aanpassingen die daar worden bepaald) hebben prioriteit.

Voor bekledingen is het geleverde middel een aggregaat van de middelen en eigenschappen die, afhankelijk van onderzoekswegen worden teruggewonnen die in de configuratie OSGi worden bepaald.
