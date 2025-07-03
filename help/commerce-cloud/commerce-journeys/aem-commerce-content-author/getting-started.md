---
title: Aan de slag met CIF Authoring
description: Aan de slag met CIF Authoring.
exl-id: 0bef4d8c-0ad3-4ec8-ab08-8c83203b3b68
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Aan de slag met AEM CIF Authoring {#getting-started}

Meer informatie over Adobe Experience Manager (AEM) CIF Authoring.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van deze reis van de Inhoud van AEM en van Commerce, [ Leer over de Inhoud van AEM en Commerce ](/help/commerce-cloud/introduction.md), leerde u de basistheorie en de concepten CMS en AEM Content en Commerce zonder kop.

Dit artikel bouwt voort op die grondbeginselen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u CIF for Content en Commerce-specifieke authoring kunt gebruiken. Na het lezen moet u:

* Begrijp de concepten van CIF authoring using Page Editor in AEM
* Toegang tot productcatalogusgegevens in AEM met product- en categoriekiezers
* Toegang krijgen tot inhoud en handelsgegevens met de productcockpit en AEM Omnsearch

## CIF Authoring in AEM Page Editor {#cif-authoring}

CIF breidt de Pagina-editor in AEM uit met mogelijkheden om toegang te krijgen tot de realtime productgegevens zonder de context te verlaten:

Open het zijpaneel en selecteer &quot;Producten&quot;van de drop-down lijst.
![ Uitgezochte producttype ](assets/asset-finder-overview.png)

U kunt door de productcatalogus bladeren of producten zoeken met het volledige tekstzoekveld.
![ producttype ](assets/asset-finder-search.png)

Producten kunnen worden neergezet op componenten die productdruppels (bijvoorbeeld productgummetje, productcarrousel) direct op de pagina ondersteunen, waardoor automatisch een productgumcomponent wordt gemaakt.

## Product- en rubriekkiezers {#pickers}

Als product- en categoriegegevens vereist zijn in commerciële componenten of in AEM-dialoogvensters voor back-office, kunnen AEM-auteurs gebruikmaken van kiezers die UI-elementen zijn voor het eenvoudig zoeken naar en selecteren van productcatalogusgegevens.

### Productkiezer

Als u op het mappictogram klikt, wordt de modale gebruikersinterface van de kiezer geopend (bijvoorbeeld productgummetje)
![ productplukker ](assets/product-picker-open.png)

Producten kunt u vinden door links in de catalogusstructuur te bladeren of door te zoeken. Bij zoeken in volledige tekst wordt rekening gehouden met de geselecteerde categorie en worden de zoekresultaten beperkt tot deze categorie.
![ de omslag van de productkiezer ](assets/product-picker-folders.png)

Producten met variaties worden gemarkeerd met een mappictogram waarop u kunt klikken om alle variaties weer te geven.
![ varianten van de productkiezer ](assets/product-picker-variants.png)
![ open de varianten van de productplukker ](assets/product-picker-variants-open.png)

### Categoriekiezer

Werkt als een productkiezer. Als u op het mappictogram klikt, wordt de modale gebruikersinterface van de kiezer geopend (bijvoorbeeld carrousel voor categorieën)
![ categoriekiezer ](assets/category-picker-open.png)

Blader naar de catalogusstructuur aan de linkerkant en selecteer de categorie.
![ categoriekiezer ](assets/category-picker-folders.png)

## Product Cockpit {#cockpit}

De cockpit van het product is een centrale plaats om snel tot de productcatalogus met al zijn verrijkte inhoud toegang te hebben. In een van de volgende modules leert u hoe u productgegevens kunt verrijken met inhoud. Laten we ons nu concentreren op de toegang tot productgegevens.

Klik in het hoofdmenu op Handel om een lijst met alle gekoppelde productcatalogi weer te geven.
![ het punt van het handelingenmenu ](assets/commerce-menu-item.png)

Hier wordt een lijst met alle verbonden productcatalogi weergegeven.
![ cockpit geïntegreerde catalogi ](assets/cockpit-Integrated-catalogs.png)

In de productcatalogus worden standaard alle categorieën op het eerste niveau met alle producten weergegeven. Als u op een categorie klikt, wordt die categorie geopend met alle verwante producten en subcategorieën, inclusief de bijbehorende producten.
![ cockpit productcatalogus ](assets/cockpit-product-catalog.png)

U kunt de eigenschappen van het product openen door op het eigenschapspictogram te klikken. Het pictogram wordt weergegeven door de muisaanwijzer op een productegel te plaatsen.
![ cockpit producteigenschappen ](assets/cockpit-properties.png)

Alle producteigenschappen zijn alleen-lezen omdat de gegevens in real-time worden geladen vanaf de verbonden backend. Het veranderen van producteigenschappen moet in het achterste systeem worden gedaan dat het systeem van verslag is. De lusje **Varianten** verschijnen slechts als het product variaties heeft. Wanneer u op het tabblad klikt, worden alle variaties met de bijbehorende kenmerken weergegeven.
![ cockpit productvarianten ](assets/cockpit-properties-variants.png)

Op de resterende tabbladen ziet u alle AEM-inhoud die aan het product is gekoppeld. Deze lusjes worden besproken in één van de volgende modules.

## AEM Omnissearch {#omnisearch}

Het gebruik van Omnissearch is een eenvoudige manier om AEM-inhoud te zoeken met behulp van full-text zoekopdrachten. CIF breidt Omnissearch uit met full-text zoekopdrachten van productcatalogi met de bijbehorende AEM-inhoud.
![ het punt van het handelingenmenu ](assets/omnisearch.png)

Omnissearch voert een full-text zoekopdracht uit in de commerceback om alle verwante producten te zoeken. Het resultaat wordt vermeld onder **Mening Alle Producten**. Het onderzoek van Omnissearch zoekt ook AEM naar inhoud die met het gezochte product wordt geassocieerd. De resultaten worden vermeld in de respectieve categorieën van AEM. In dit voorbeeld is één inhoudsfragment gerelateerd aan het product.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis hebt voltooid, moet u:

* Begrijp de concepten van CIF authoring gebruikend de Redacteur van de Pagina
* Toegang krijgen tot productcatalogus in AEM met product- en rubriekkiezers
* Toegang krijgen tot inhoud en handelsgegevens met de productcockpit en AEM Omnsearch

Bouw op deze kennis voort en zet uw reis door het document [ te herzien leiden de Pagina&#39;s en de Malplaatjes van de Catalogus van het Product ](catalog-templates.md), waar u leert om uw eerste ervaring van de productcatalogus te bouwen en aan te passen.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van reis [ beweegt de Pagina&#39;s en de Malplaatjes van de Catalogus van het Product beheren ](catalog-templates.md) - het volgende zijn sommige facultatieve middelen die een diepere duik op sommige hier genoemde concepten doen. Deze facultatieve middelen zijn echter niet nodig om op de reis door te gaan.

* [Opslag en catalogi configureren](/help/commerce-cloud/getting-started.md#catalog)
