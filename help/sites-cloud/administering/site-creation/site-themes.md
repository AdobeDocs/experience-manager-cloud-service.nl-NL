---
title: Sitethema's
description: Leer hoe AEM sitethema's kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
solution: Experience Manager Sites
source-git-commit: 92c0e556eb1f92dadd396a479a8bf933715935a7
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Sitethema&#39;s {#site-themes}

Leer hoe AEM sitethema&#39;s kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen.

## Overzicht {#overview}

Een AEM site-thema is een pakket met de CSS-, JavaScript- en statische bronnen die de opmaak van uw AEM-site definiëren en die voldoet aan de structuur van een AEM-sitethema.

Sites die zijn gemaakt met AEM sitesjablonen maken het eenvoudig downloaden, aanpassen en opnieuw gebruiken van de thema&#39;s mogelijk.

>[!NOTE]
>
>AEM zouden de plaatsthema&#39;s niet met [ AEM plaatssjablonen ](site-templates.md) moeten worden verward. AEM sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM site. AEM plaatssjablonen bepalen plaatsstructuur en aanvankelijke inhoud, en bevatten een AEM plaatsthema om voor [ snelle plaatsverwezenlijking ](create-site.md) toe te staan.

## Sitethema&#39;s gebruiken {#using-themes}

Sitethema&#39;s worden op twee verschillende manieren gebruikt:

* Zij worden gebruikt als deel van een plaatsmalplaatje om het stileren te bepalen wanneer [ creërend een plaats.](create-site.md)
* Ze worden gedownload nadat een site op basis van een sitesjabloon is gemaakt, zodat een ontwikkelaar aan de voorzijde de opmaak verder kan aanpassen.

>[!TIP]
>
>Een beschrijving van begin tot eind van het proces om een plaats van een malplaatje te creëren en zijn thema aan te passen kan in de [ Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md) worden gevonden.

## Structuur van sitethema {#structure}

Sitethema&#39;s zijn eenvoudig pakketten met een logische structuur die duidelijk het doel van de pakketinhoud weerspiegelt. Voor een typisch front-end project, adviseert de Adobe de volgende structuur voor een plaatsthema:

* `src/theme.ts`: Het belangrijkste ingangspunt van uw JS &amp; CSS-thema
* `src/site`: JS- en CSS-bestanden die van toepassing zijn op de gehele site
* `src/components`: JS- en CSS-bestanden die specifiek zijn voor AEM componenten
* `src/resources`: statische bestanden zoals pictogrammen, logo&#39;s en lettertypen

Afhankelijk van de specifieke projectbehoeften, kan de themastructuur variëren zolang het hoofdingangspunt, `src/theme.ts`, behouden blijft.

## Standaardsitethema {#standard-site-theme}

Adobe biedt een verwijzingsthema met tips en trucs dat u kunt gebruiken als basis voor het maken van uw eigen thema. [ het StandaardThema van de Plaats is beschikbaar op GitHub ](https://github.com/adobe/aem-site-template-standard/tree/main/theme).

## Sitethema&#39;s ontwikkelen {#developing-themes}

Adobe biedt een AEM Site Theme Builder als een set scripts voor het maken van nieuwe sitethema&#39;s.

[ de Bouwer van het Thema van de Plaats van de AEM is beschikbaar samen met gebruiksdocumentatie op GitHub ](https://github.com/adobe/aem-site-theme-builder). Voor het aanpassen van het thema is ontwikkelervaring op de voorgrond vereist.
