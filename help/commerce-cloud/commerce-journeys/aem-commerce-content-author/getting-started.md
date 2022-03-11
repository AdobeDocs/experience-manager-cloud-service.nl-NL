---
title: Aan de slag met CIF Authoring
description: Aan de slag met CIF Authoring
exl-id: 0bef4d8c-0ad3-4ec8-ab08-8c83203b3b68
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# Aan de slag met AEM CIF Authoring {#getting-started}

Meer weten over AEM CIF Authoring.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van deze AEM reis van de Inhoud en de Handel, [Meer informatie over AEM inhoud en handel](/help/commerce-cloud/introduction.md)U leerde de basistheorie van wat een CMS zonder kop is en u zou nu de basisconcepten van AEM Inhoud en Handel moeten begrijpen.

Dit artikel bouwt voort op die grondbeginselen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om CIF voor Inhoud en Handel specifieke creatie te gebruiken. Na het lezen moet u:

* Begrijp de concepten creatie CIF gebruikend de Universele Redacteur
* Toegang krijgen tot productcatalogusgegevens in AEM met product- en categoriekiezers
* Toegang krijgen tot inhoud en handelsgegevens met de productcockpit en AEM Omnsearch

## CIF Authoring in de Universal Editor {#cif-authoring}

CIF breidt de Universele Redacteur met mogelijkheden uit om tot de productgegevens in real time toegang te hebben zonder de context te verlaten:

Open het zijpaneel en selecteer &#39;Producten&#39; in het vervolgkeuzemenu.
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

De cockpit van het product is een centrale plaats om snel tot productcatalogus met al zijn verrijkte inhoud toegang te hebben. In een van de volgende modules leert u hoe u productgegevens kunt verrijken met inhoud. Laten we ons nu concentreren op de toegang tot productgegevens.

Klik in het hoofdmenu op Handelsversie om een lijst met alle gekoppelde productcatalogi weer te geven.
![menu-item handel](assets/commerce-menu-item.png)

Dit toont een lijst van alle verbind productcatalogi.
![cockpit geïntegreerde catalogi](assets/cockpit-Integrated-catalogs.png)

De productcatalogus bevat standaard alle categorieën op het eerste niveau met alle producten. Als u op een categorie klikt, wordt die categorie geopend met alle verwante producten en subcategorieën, inclusief hun producten.
![cockpitproductcatalogus](assets/cockpit-product-catalog.png)

U kunt de producteigenschappen openen door op het bezitspictogram te klikken. Het pictogram wordt weergegeven door de muisaanwijzer op een productegel te plaatsen.
![eigenschappen van cockpit-producten](assets/cockpit-properties.png)

Alle producteigenschappen zijn alleen-lezen omdat de gegevens in real-time worden geladen vanaf de verbonden backend. Het veranderen van producteigenschappen moet in het achterste systeem worden gedaan dat het systeem van verslag is. Het tabblad **Varianten** wordt alleen weergegeven als het product variaties heeft. Wanneer u op het tabblad klikt, worden alle variaties met de bijbehorende kenmerken weergegeven.
![cockpitproductvarianten](assets/cockpit-properties-variants.png)

Op de resterende tabbladen ziet u alle AEM inhoud die aan het product is gekoppeld. We zullen deze tabbladen in een van de volgende modules bespreken.

## AEM Omnissearch {#omnisearch}

Het gebruik van Omnissearch is een eenvoudige manier om AEM inhoud te zoeken met behulp van full-text zoekopdrachten. CIF breidt Omnissearch uit met full-text onderzoek van productcatalogi met zijn bijbehorende AEM inhoud.
![menu-item handel](assets/omnisearch.png)

Het onderzoek zal een full-text onderzoek in de handelskolterug in werking stellen om alle verwante producten te vinden. Het resultaat wordt onder **Alle producten weergeven**. InSearch wordt ook AEM gezocht naar inhoud die is gekoppeld aan het doorzochte product. De resultaten worden vermeld in de respectieve AEM. In dit voorbeeld is één inhoudsfragment gerelateerd aan het product.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis hebt voltooid, moet u:

* Begrijp de concepten creatie CIF gebruikend de Universele Redacteur
* Toegang tot productcatalogus in AEM met product- en categoriekiezers
* Toegang krijgen tot inhoud en handelsgegevens met de productcockpit en AEM Omnsearch

Gebaseerd op deze kennis en doorgaan met uw reis door het document opnieuw te bekijken [Productcataloguspagina&#39;s en -sjablonen beheren](catalog-templates.md), waar u leert hoe u uw eerste ervaring met de productcatalogus kunt opbouwen en aanpassen.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de rit gaan door het document te bekijken [Productcataloguspagina&#39;s en -sjablonen beheren](catalog-templates.md)Hieronder volgt een aantal aanvullende, optionele bronnen die een diepgaander inzicht geven in bepaalde concepten die in dit document worden genoemd, maar die niet nodig zijn om verder te gaan op de reis.

* [Opslag en catalogi configureren](/help/commerce-cloud/getting-started.md#catalog)
