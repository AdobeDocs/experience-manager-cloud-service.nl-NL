---
title: Integratie van AEM en handel van derden met behulp van het kader voor integratie van de handel
description: Ondernemingen kunnen aanvullende handelsoplossingen van derden nodig hebben om hun winkel te kunnen bedienen. Het Kader van de Integratie van de Handel (CIF) kan in dergelijke integratiescenario's worden gebruikt om een derde handelsoplossing met Adobe Experience Manager te verbinden gebruikend I/O Runtime.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# Integratie van AEM en handel van derden met behulp van het kader voor integratie van de handel {#aem-third-party}

Ondernemingen kunnen aanvullende handelsoplossingen van derden nodig hebben om hun winkel te kunnen bedienen. Het kader voor de integratie van de Handel (CIF) kan in dergelijke integratiescenario&#39;s worden gebruikt waar naast Magento, een derde handelsoplossing ook met AEM moet worden geïntegreerd. CIF verstrekt elementen zoals een opslag van de versnellerverwijzing, AEM de Componenten van de Kern van CIF en auteurshulpmiddelen die met Magento uit-van-de-doos werken. Om AEM en een handelsoplossing van derden te integreren en deze CIF-elementen opnieuw te gebruiken, is enige extra ontwikkeling nodig.

## Architectuur {#architecture}

De architectuur ziet er als volgt uit:

![Overzicht van architectuur van niet-Magento/derden AEM](/help/commerce-cloud/assets/AEM_nonMagento_Architecture.JPG)

Het belangrijkste verschil tussen de integratiearchitectuur voor AEM - Magento en AEM - derdehandel is de toevoeging van een integratie en een laag van de gegevenstransformatie zoals aangetoond in het beeld hierboven. De integratielaag moet worden gehost op het Adobe I/O Runtime-platform zonder Adobe. Je kunt meer leren over Adobe I/O Runtime [hier](https://www.adobe.io/apis/experienceplatform/runtime.html).

Het doel van deze integratielaag is om een niet-Magento of een derde-partij APIs tegen Adobe Handel APIs (Magento GraphQL APIs) in kaart te brengen. Met deze toewijzing kunnen de [AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) en CIF authoring tools gegevens ophalen van de niet-Magento oplossing. Met deze benadering, kapselt de integratielaag de integratielogica in en leidt tot een scheiding van zorg tussen AEM en de derdeoplossing. Hierdoor kunnen de CIF-elementen op agnostische wijze worden gebruikt met verschillende oplossingen van derden. De voordelen van het gebruiken van elementen CIF in uw project zijn beschreven in de [Inleiding](/help/commerce-cloud/overview.md).

## Een integratie ontwikkelen {#develop-integration}

Om u te helpen aan de bouw van de vereiste integratielaag beginnen om een niet-Magento/derdeoplossing met AEM te integreren, hebben wij een [verwijzingsimplementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference) gecreeerd om dit aan te tonen. Deze verwijzing kan als uitgangspunt in uw project worden gebruikt.
