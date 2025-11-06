---
title: Bedekkingen voor Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service gebruikt het principe van overlays om consoles en andere functies uit te breiden en aan te passen
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Bedekkingen in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager as a Cloud Service gebruikt het principe van overlays om consoles en andere functies (bijvoorbeeld paginaontwerp) uit te breiden en aan te passen.

Bedekking is een term die in veel contexten kan worden gebruikt. In dit verband betekent het uitbreiden van AEM as a Cloud Service dat een overlay de vooraf gedefinieerde functionaliteit overneemt en er uw eigen definities op legt om de standaardfunctionaliteit aan te passen.

In een standaardinstantie, wordt de vooraf bepaalde functionaliteit gehouden onder `/libs` en het wordt geadviseerd praktijk om uw bekleding (aanpassingen) onder de `/apps` tak te bepalen (gebruikend a [ onderzoekspad ](#search-paths) om de middelen) op te lossen.

* Het aanraking-toegelaten gebruikersinterface gebruikt [ graniet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) - verwante overlays:

   * Methode

      * Reconstrueer de juiste `/libs` -structuur onder `/apps` .

        Deze herstructurering vereist geen 1 :1 exemplaar omdat de [ Verschuivende Fusie van het Middel ](/help/implementing/developing/introduction/sling-resource-merger.md) wordt gebruikt om de originele definities van verwijzingen te voorzien die worden vereist. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen met (het onderscheiden) mechanismen toegang te hebben en samen te voegen.

      * Breng wijzigingen aan onder `/apps` .

   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs` .
      * Alleen opnieuw definiëren wat vereist is.

>[!CAUTION]
>
>De [ Verschuivende Fusie van het Middel ](/help/implementing/developing/introduction/sling-resource-merger.md) en de verwante methodes kunnen slechts met [ Graniet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) worden gebruikt. Deze regel houdt in dat het maken van een overlay met een skeletstructuur alleen geschikt is voor de standaardgebruikersinterface met aanraakbediening.

Bedekkingen zijn de aanbevolen methode voor veel wijzigingen. Stel bijvoorbeeld dat u de consoles configureert of dat u de selectiecategorie maakt in de middelenbrowser in het zijpaneel (gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* **in de `/libs` tak, *maakt geen* veranderingen**
Wijzigingen die u aanbrengt, kunnen verloren gaan omdat deze vertakking kan veranderen wanneer upgrades op uw instantie worden toegepast.

* Zij concentreren uw veranderingen in één plaats, die het voor u gemakkelijker maken om uw veranderingen te volgen, te migreren, file, of te zuiveren zonodig.

## Paden zoeken {#search-paths}

AEM gebruikt een zoekpad om een bron te zoeken, waarbij eerst de `/apps` -vertakking en vervolgens de `/libs` -vertakking worden gezocht. Dit mechanisme houdt in dat uw bedekking in `/apps` (en de aanpassingen die daar worden gedefinieerd) prioriteit heeft.

Voor bekledingen is het geleverde middel een aggregaat van de middelen en eigenschappen die, afhankelijk van onderzoekswegen worden teruggewonnen die in de configuratie OSGi worden bepaald.
