---
title: Bedekkingen voor Adobe Experience Manager als Cloud Service
description: AEM als Cloud Service gebruikt het principe van overlays zodat u consoles en andere functionaliteit kunt uitbreiden en aanpassen
translation-type: tm+mt
source-git-commit: 8028682f19ba6ba7db6b60a2e5e5f5843f7ac11f
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---


# Overlays in AEM as a Cloud Service {#overlays-in-aem}

Adobe Experience Manager als Cloud Service gebruikt het beginsel van bedekkingen om u toe te staan om de consoles en andere functionaliteit (bijvoorbeeld, pagina creatie) uit te breiden en aan te passen.

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Bedekking is een term die in veel contexten kan worden gebruikt. In deze context (het uitbreiden van AEM als Cloud Service) betekent een bekleding het nemen van de vooraf bepaalde functionaliteit en het opleggen van uw eigen definities over dat (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit vastgehouden onder `/libs` en het wordt aanbevolen om uw bedekking (aanpassingen) onder de `/apps` vertakking te definiëren (met een [zoekpad](#search-paths) om de bronnen op te lossen).

* De interface met aanraakbediening gebruikt [graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)-gerelateerde overlays:

   * Methode

      * Reconstrueer de juiste `/libs` structuur onder `/apps`.

         Dit vereist geen 1:1 exemplaar, aangezien de [Verschuivende Fusie](/help/implementing/developing/introduction/sling-resource-merger.md) van het Middel wordt gebruikt om de originele definities van verwijzingen te voorzien die worden vereist. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen door (het differentiëren) mechanismen af te schilderen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Voordelen

      * Meer robuust voor veranderingen onder `/libs`.
      * Alleen opnieuw definiëren wat werkelijk vereist is.


<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>De [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) en de verwante methodes kunnen slechts met [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)worden gebruikt. Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.

Bedekkingen zijn de aanbevolen methode voor vele wijzigingen, zoals het configureren van de consoles of het maken van uw selectiecategorie in de middelenbrowser in het zijpaneel (wordt gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

<!--
Overlays are the recommended method for many changes, such as [configuring your consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) or [creating your selection category to the asset browser in the side panel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (used when authoring pages). They are required as:
-->

* U ***mag geen *wijzigingen aanbrengen in de`/libs`vertakking **. Wijzigingen die u aanbrengt, gaan mogelijk verloren, omdat deze vertakking kan veranderen wanneer upgrades op uw instantie worden toegepast.

* Ze concentreren uw wijzigingen op één locatie. het voor u gemakkelijker maken om uw wijzigingen te volgen, te migreren, er een back-up van te maken en/of er fouten in op te sporen.

## Paden zoeken {#search-paths}

AEM gebruikt een onderzoekspad om een middel te vinden, die (door gebrek) eerst de tak en toen de `/apps` `/libs` tak zoeken. Dit mechanisme houdt in dat uw bedekking in `/apps` (en de aanpassingen die daar worden gedefinieerd) prioriteit heeft.

Voor bekledingen is het geleverde middel een aggregaat van de middelen en eigenschappen die, afhankelijk van onderzoekswegen worden teruggewonnen die in de configuratie OSGi worden bepaald.

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->