---
title: Sitethema's
description: Leer hoe AEM-sitethema's kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen voor traditionele AEM-ontwerpprojecten met publicatieweergave.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
solution: Experience Manager Sites
source-git-commit: 9efba01add46c09e9839da6bb96b138d48018e54
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# Sitethema&#39;s {#site-themes}

{{traditional-aem}}

Leer hoe AEM-sitethema&#39;s kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen voor traditionele AEM-ontwerpprojecten met publicatieweergave.

## Overzicht {#overview}

Een AEM-sitethema is een pakket met de CSS-, JavaScript- en statische bronnen die de opmaak van uw AEM-site definiëren en die voldoet aan de structuur van een AEM-sitethema.

De plaatsen die met de plaatsmalplaatjes van AEM worden gecreeerd staan voor de gemakkelijke download, aanpassing, en herplaatsing van de thema&#39;s voor traditionele het auteursprojecten van AEM met [ toe publiceren levering.](/help/sites-cloud/authoring/author-publish.md)

>[!NOTE]
>
>De de plaatsthema&#39;s van AEM zouden niet met [ de plaatsmalplaatjes van AEM ](site-templates.md) moeten worden verward. AEM-sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM-site. De plaatsmalplaatjes van AEM bepalen plaatsstructuur en aanvankelijke inhoud, en bevatten een de plaatsthema van AEM om voor [ snelle plaatsverwezenlijking toe te staan.](create-site.md)

## Sitethema&#39;s gebruiken {#using-themes}

Sitethema&#39;s worden op twee verschillende manieren gebruikt:

* Zij worden gebruikt als deel van een plaatsmalplaatje om het stileren te bepalen wanneer [ creërend een plaats.](create-site.md)
* Ze worden gedownload nadat een site op basis van een sitesjabloon is gemaakt, zodat een ontwikkelaar aan de voorzijde de opmaak verder kan aanpassen.

>[!TIP]
>
>Een beschrijving van begin tot eind van het proces om een plaats van een malplaatje te creëren en zijn thema aan te passen kan in de [ Snelle Reis van de Aanmaak van de Plaats worden gevonden.](/help/journey-sites/quick-site/overview.md)

## Structuur van sitethema {#structure}

Sitethema&#39;s zijn eenvoudig pakketten met een logische structuur die duidelijk het doel van de pakketinhoud weerspiegelt. Voor een typisch front-end project, adviseert Adobe de volgende structuur voor een plaatsthema:

* `src/theme.ts`: Het belangrijkste ingangspunt van uw JS &amp; CSS-thema
* `src/site`: JS- en CSS-bestanden die van toepassing zijn op de gehele site
* `src/components`: JS- en CSS-bestanden die specifiek zijn voor AEM-componenten
* `src/resources`: statische bestanden zoals pictogrammen, logo&#39;s en lettertypen

Afhankelijk van de specifieke projectbehoeften, kan de themastructuur variëren zolang het hoofdingangspunt, `src/theme.ts`, behouden blijft.

## Standaardsitethema {#standard-site-theme}

Adobe biedt een verwijzingsthema voor tips en trucs dat u kunt gebruiken als basis voor het maken van uw eigen thema. [ het StandaardThema van de Plaats is beschikbaar op GitHub.](https://github.com/adobe/aem-site-template-standard/tree/main/theme)

## Sitethema&#39;s ontwikkelen {#developing-themes}

Adobe biedt een AEM Site Theme Builder als een set scripts voor het maken van nieuwe sitethema&#39;s.

[ de Bouwer van het Thema van de Plaats van AEM is beschikbaar samen met gebruiksdocumentatie op GitHub.](https://github.com/adobe/aem-site-theme-builder) Voor het aanpassen van het thema is een ontwikkelervaring op de voorgrond vereist.
