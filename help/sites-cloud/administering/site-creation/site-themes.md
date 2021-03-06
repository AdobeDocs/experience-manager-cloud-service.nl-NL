---
title: Sitethema's
description: Leer hoe AEM sitethema's kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Sitethema&#39;s {#site-themes}

Leer hoe AEM sitethema&#39;s kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen.

## Overzicht {#overview}

Een AEM site-thema is een pakket met de CSS-, JavaScript- en statische bronnen die de opmaak van uw AEM-site definiëren en die voldoet aan de structuur van een AEM-sitethema.

Sites die zijn gemaakt met AEM sitesjablonen maken het eenvoudig downloaden, aanpassen en opnieuw gebruiken van de thema&#39;s mogelijk.

>[!NOTE]
>
>AEM sitethema&#39;s mogen niet worden verward met [AEM sitesjablonen.](site-templates.md) AEM sitethema&#39;s bevatten alleen de opmaakgegevens voor een AEM site. Met AEM sitesjablonen kunt u de sitestructuur en de initiële inhoud definiëren en een AEM sitethema bevatten om het mogelijk te maken [snel websites maken.](create-site.md)

## Sitethema&#39;s gebruiken {#using-themes}

Sitethema&#39;s worden op twee verschillende manieren gebruikt:

* Ze worden gebruikt als onderdeel van een sitesjabloon om stijlen te definiëren wanneer [een site maken.](create-site.md)
* Ze worden gedownload nadat een site op basis van een sitesjabloon is gemaakt, zodat een ontwikkelaar aan de voorzijde de opmaak verder kan aanpassen.

>[!TIP]
>
>Een end-to-end beschrijving van het proces om een plaats van een malplaatje te creëren en zijn thema aan te passen kan in worden gevonden [Reis voor snel maken van site.](/help/journey-sites/quick-site/overview.md)

## Structuur van sitethema {#structure}

Sitethema&#39;s zijn eenvoudig pakketten met een logische structuur die duidelijk het doel van de pakketinhoud weerspiegelt. Een site-thema heeft de volgende structuur die kenmerkend is voor een front-end project.

* `src/main.ts`: Het belangrijkste ingangspunt van uw thema JS &amp; CSS
* `src/site`: JS- en CSS-bestanden die van toepassing zijn op de gehele site
* `src/components`: JS- en CSS-bestanden die specifiek zijn voor AEM componenten
* `src/resources`: Statische bestanden zoals pictogrammen, logo&#39;s en lettertypen

## Standaardsitethema {#standard-site-theme}

Adobe biedt een verwijzingsthema voor tips en trucs dat u kunt gebruiken als basis voor het maken van uw eigen thema. [Het standaardthema van de Plaats is beschikbaar op GitHub.](https://github.com/adobe/aem-site-template-standard-theme-e2e)

## Sitethema&#39;s ontwikkelen {#developing-themes}

Adobe biedt een AEM Site Theme Builder als een set scripts voor het maken van nieuwe sitethema&#39;s.

[De Bouwer van het Thema van de Plaats van de AEM is beschikbaar samen met gebruiksdocumentatie op GitHub.](https://github.com/adobe/aem-site-theme-builder) Voor het aanpassen van het thema is ontwikkelervaring op de voorgrond vereist.
