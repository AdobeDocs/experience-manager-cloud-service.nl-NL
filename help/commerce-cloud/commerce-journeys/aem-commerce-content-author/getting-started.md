---
title: Aan de slag met CIF ontwerpen
description: Aan de slag met CIF ontwerpen.
exl-id: 0bef4d8c-0ad3-4ec8-ab08-8c83203b3b68
source-git-commit: 6f27c968c347e6b2be8c9bfcf9bb69e531d10ff9
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Aan de slag met AEM CIF ontwerpen {#getting-started}

Meer weten over Adobe Experience Manager (AEM) CIF Authoring.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van deze AEM Content and Commerce trip: [Meer informatie over AEM Content en Commerce](/help/commerce-cloud/introduction.md)U leerde de basistheorie en -concepten van CMS zonder kop en AEM Content en Commerce.

Dit artikel bouwt voort op die grondbeginselen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u CIF kunt gebruiken voor het maken van inhoud en voor het maken van specifieke Commerce-toepassingen. Na het lezen moet u:

* Begrijp de concepten CIF creatie gebruikend de Redacteur van de Pagina in AEM
* Toegang krijgen tot productcatalogusgegevens in AEM met product- en categoriekiezers
* Toegang krijgen tot inhoud en handelsgegevens met de productcockpit en AEM Omnsearch

## CIF maken in AEM paginaeditor {#cif-authoring}

CIF breidt de Redacteur van de Pagina in AEM met mogelijkheden uit om tot de productgegevens in real time toegang te hebben zonder de context te verlaten:

Open het zijpaneel en selecteer &quot;Producten&quot;van de drop-down lijst.
![Producttype selecteren](assets/asset-finder-overview.png)

U kunt door de productcatalogus bladeren of producten zoeken met het volledige tekstzoekveld.
![productsoort](assets/asset-finder-search.png)

Producten kunnen worden neergezet op componenten die productdruppels (bijvoorbeeld productgummetje, productcarrousel) direct op de pagina ondersteunen, waardoor automatisch een productgumcomponent wordt gemaakt.

## Product- en rubriekkiezers {#pickers}

Als de product en categoriegegevens in handelscomponenten of AEM achterkantoordialogen worden vereist, kunnen AEM auteurs plukkers gebruiken die UI-elementen zijn om gemakkelijk gegevens van de productcatalogus te zoeken en te selecteren.

### Productkiezer

Als u op het mappictogram klikt, wordt de modale gebruikersinterface van de kiezer geopend (bijvoorbeeld productgummetje)
![productkiezer](assets/product-picker-open.png)

Producten kunt u vinden door links in de catalogusstructuur te bladeren of door te zoeken. Bij zoeken in volledige tekst wordt rekening gehouden met de geselecteerde categorie en worden de zoekresultaten beperkt tot deze categorie.
![map met productkiezers](assets/product-picker-folders.png)

Producten met variaties worden gemarkeerd met een mappictogram waarop u kunt klikken om alle variaties weer te geven.
![productkiezervarianten](assets/product-picker-variants.png)
![productkiezervarianten openen](assets/product-picker-variants-open.png)

### Categoriekiezer

Werkt als een productkiezer. Als u op het mappictogram klikt, wordt de modale gebruikersinterface van de kiezer geopend (bijvoorbeeld carrousel voor categorieën)
![categoriekiezer](assets/category-picker-open.png)

Blader naar de catalogusstructuur aan de linkerkant en selecteer de categorie.
![categoriekiezer](assets/category-picker-folders.png)

## Product Cockpit {#cockpit}

De cockpit van het product is een centrale plaats om snel tot de productcatalogus met al zijn verrijkte inhoud toegang te hebben. In een van de volgende modules leert u hoe u productgegevens kunt verrijken met inhoud. Laten we ons nu concentreren op de toegang tot productgegevens.

Klik in het hoofdmenu op Handel om een lijst met alle gekoppelde productcatalogi weer te geven.
![menu-item handel](assets/commerce-menu-item.png)

Hier wordt een lijst met alle verbonden productcatalogi weergegeven.
![cockpit geïntegreerde catalogi](assets/cockpit-Integrated-catalogs.png)

In de productcatalogus worden standaard alle categorieën op het eerste niveau met alle producten weergegeven. Als u op een categorie klikt, wordt die categorie geopend met alle verwante producten en subcategorieën, inclusief de bijbehorende producten.
![cockpitproductcatalogus](assets/cockpit-product-catalog.png)

U kunt de eigenschappen van het product openen door op het eigenschapspictogram te klikken. Het pictogram wordt weergegeven door de muisaanwijzer op een productegel te plaatsen.
![eigenschappen van cockpit-producten](assets/cockpit-properties.png)

Alle producteigenschappen zijn alleen-lezen omdat de gegevens in real-time worden geladen vanaf de verbonden backend. Het veranderen van producteigenschappen moet in het achterste systeem worden gedaan dat het systeem van verslag is. Het tabblad **Varianten** worden alleen weergegeven als het product variaties heeft. Wanneer u op het tabblad klikt, worden alle variaties met de bijbehorende kenmerken weergegeven.
![cockpitproductvarianten](assets/cockpit-properties-variants.png)

Op de resterende tabbladen ziet u alle AEM inhoud die aan het product is gekoppeld. Deze lusjes worden besproken in één van de volgende modules.

## AEM Omnissearch {#omnisearch}

Het gebruik van Omnissearch is een eenvoudige manier om AEM inhoud te zoeken met behulp van full-text zoekopdrachten. CIF breidt Omnissearch uit met full-text onderzoek van productcatalogi met zijn bijbehorende AEM inhoud.
![menu-item handel](assets/omnisearch.png)

Omnissearch voert een full-text zoekopdracht uit in de commerceback om alle verwante producten te zoeken. Het resultaat wordt weergegeven onder **Alle producten weergeven**. Het onderzoek van Omnissearch zoekt ook AEM naar inhoud die aan het gezochte product wordt geassocieerd. De resultaten worden vermeld in de respectieve AEM categorieën. In dit voorbeeld is één inhoudsfragment gerelateerd aan het product.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis hebt voltooid, moet u:

* Begrijp de concepten CIF creatie gebruikend de Redacteur van de Pagina
* Toegang tot productcatalogus in AEM met product- en categoriekiezers
* Toegang krijgen tot inhoud en handelsgegevens met de productcockpit en AEM Omnsearch

Gebaseerd op deze kennis en doorgaan met uw reis door het document opnieuw te bekijken [Productcataloguspagina&#39;s en -sjablonen beheren](catalog-templates.md), waarin u leert hoe u uw eerste ervaring met de productcatalogus kunt opbouwen en aanpassen.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden door te gaan naar het volgende deel van de reis-[Productcataloguspagina&#39;s en -sjablonen beheren](catalog-templates.md)- het volgende is sommige facultatieve middelen die een diepere duik op sommige hier genoemde concepten doen. Deze facultatieve middelen zijn echter niet nodig om op de reis door te gaan.

* [Opslag en catalogi configureren](/help/commerce-cloud/getting-started.md#catalog)
