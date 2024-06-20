---
title: Pagina's en sjablonen van productcatalogi beheren
description: Meer informatie over het beheren van productcataloguspagina's en -sjablonen
exl-id: 0d795d85-c865-40d5-941e-e02ee96fdd11
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# Pagina&#39;s en sjablonen van productcatalogi beheren {#product-catalog}

Meer weten over het beheren van productcataloguspagina&#39;s en -sjablonen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM Content and Commerce authoring trip: [Aan de slag met AEM basisbeginselen van CIF authoring](getting-started.md), u leerde de basis van CIF creatie.

Dit artikel bouwt voort op die grondbeginselen.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om de pagina&#39;s en de malplaatjes van de productcatalogus te beheren. Na het lezen moet u:

* begrijpen de concepten van catalogussjablonen
* hoe generieke sjablonen werken
* een afzonderlijke sjabloon hebben gemaakt

## Het basisconcept {#basic-concept}

De Venia-winkel wordt geleverd met een typische ervaring in de productcatalogus met navigatie, landen, categorieën (PLP) en productdetails (PDP).

Cataloguspagina&#39;s worden dynamisch gebouwd gebruikend een AEM CIF catalogusmalplaatje en productgegevens in real time die van het handelseindpunt wanneer nodig worden gehaald. Elke catalogus heeft een algemene sjabloon voor product- en categoriepagina&#39;s.
![catalogusstructuur](assets/catalog-structure.png)

De navigatiecomponent toont inhoud en cataloguspagina&#39;s. Het is mogelijk om de bestemmingspagina van de catalogus of de categorieën van het eerste niveau in de navigatie te tonen. Als u de muisaanwijzer boven een categorie houdt, worden de categorieën op het tweede niveau weergegeven als een tweede regel.
![catalogusnavigatie](assets/catalog-navigation.png)

Als u op een categorie klikt, wordt de pagina met categorieën (of de pagina met productlijsten) geopend.

![PLP](assets/catalog-plp.png)

Als u op een product klikt, wordt de pagina met productdetails geopend.

![PLP](assets/catalog-pdp.png)

## De sjablonen {#templates}

### Algemene sjablonen {#generic}

De algemene Venia-catalogussjabloon gebruikt de component Product List Core. In dit onderdeel wordt de categorieafbeelding weergegeven, indien beschikbaar, en de producten uit de categorie.
![categoriesjabloon](assets/category-template.png)

De generieke productsjabloon van Venia gebruikt de component Product Detail Core. Dit onderdeel geeft productinformatie weer voor verschillende producttypen en acties voor invoegtoepassingen.
![productsjabloon](assets/product-template.png)

### Sjablonen bewerken {#edit-templates}

Sjablonen kunnen worden bewerkt door de sjabloonpagina rechtstreeks te openen of door over te schakelen op de bewerkingsmodus terwijl u door een pagina in de productcatalogus bladert. Als u de pagina wijzigt, wordt de sjabloon gewijzigd en niet alleen de specifieke pagina van het product of de categorie.

### Categorie- of productspecifieke sjablonen {#specific}

CIF ondersteunt meerdere sjablonen met slechts een paar klikken. Als u een andere sjabloon wilt maken, selecteert u de algemene sjabloon in de desbetreffende categorie en maakt u een pagina met de **Maken** handeling.

![sjabloonpagina maken](assets/create-template-page.png)

Selecteer de desbetreffende product- of categoriesjabloon.

![Sjabloonselectie maken](assets/create-template-select.png)

Voer de titel in en maak de pagina.

![sjabloon maken](assets/create-template-enter.png)

U ziet nu een specifieke sjabloon onder de algemene sjabloon.

![sjabloonhiërarchie maken](assets/create-template-hierachry.png)

Open de sjabloon. Het lijkt precies op de generieke categoriesjabloon.

![nieuwe sjabloon maken](assets/create-template-new.png)

Voeg een afbeelding toe boven op de pagina.

![sjabloonupdate maken](assets/create-template-update.png)

U kunt een voorbeeld van de sjabloon bekijken in elke gewenste categorie/product. Openen **Pagina-informatie** en selecteer vervolgens **Weergeven met categorie/product**. Selecteer het product/de categorie in de kiezer voor een voorvertoning met dit product/deze categorie. Selecteren **De look kopen** voor een voorvertoning van de bijgewerkte sjabloon.

![sjabloon maken ](assets/create-template-picker.png)

Nu moet u deze sjabloon toewijzen aan de specifieke categorie. Eigenschappen openen in het dialoogvenster **Pagina-informatie** en schakelen naar het tabblad Handel. Klik op het mappictogram om het **De look kopen** categorie uit de categoriekiezer. Het is mogelijk meerdere categorieën aan een sjabloon toe te wijzen en ook subcategorieën op te nemen door het selectievakje in te schakelen.

![sjabloonkoppeling maken](assets/create-template-associate.png)

Ga terug naar de hoofdstartpagina en klik op **De look kopen** categorie om de specifieke template te zien. Alle andere categorieën gebruiken nog het generische malplaatje.

![sjabloonresultaat maken](assets/create-template-result.png)

Dezelfde workflow kan worden toegepast om afzonderlijke productsjablonen te maken.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis hebt voltooid, moet u:

* begrijpen de concepten van catalogussjablonen
* hoe generieke sjablonen werken
* een afzonderlijke sjabloon hebben gemaakt

Gebaseerd op deze kennis en doorgaan met uw reis door het document opnieuw te bekijken [Ervaringen met gefaseerde productcatalogi beheren](staged-catalog.md), waar u leert werken met gefaseerde productgegevens en AEM.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de rit gaan door het document te bekijken [Ervaringen met gefaseerde productcatalogi beheren](staged-catalog.md)Hieronder volgt een aantal aanvullende, optionele bronnen die een dieper inzicht geven in bepaalde concepten die in dit document worden genoemd, maar die niet nodig zijn om verder te gaan op de weg zonder kop:

* [Meerdere categorieën en productpagina&#39;s maken](/help/commerce-cloud/authoring/multi-template-usage.md)
* [Migratiehandleiding voor de Experience Manager Cloud Service](/help/commerce-cloud/migration.md) - Migreren naar de AEM Commerce integration framework (CIF)-invoegtoepassing vanuit een oude versie
