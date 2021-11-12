---
title: Ervaringen met gefaseerde productcatalogi beheren
description: Leer hoe u ervaringen met gefaseerde productcatalogi beheert.
source-git-commit: a98d525512dcba790d002d6a4042558962c36c97
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Trainingen met gefaseerde productcatalogus maken {#building-experiences}

Leer hoe u ervaringen met gefaseerde productcatalogi beheert.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de reis AEM Inhoud en Handel: [Productcataloguspagina&#39;s en -sjablonen beheren](catalog-templates.md)hebt u geleerd hoe u ervaringen met productcatalogi kunt beheren en samenstellen op basis van sjablonen.

Dit artikel bouwt voort op die grondbeginselen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de ervaring van de productcatalogus kunt beheren op basis van gefaseerde productgegevens en AEM Launches. Vaak moeten auteurs zich tegelijkertijd voorbereiden op een volgende productintroductie (bijvoorbeeld een nieuwe kledingcollectie). Dit vereist toegang tot gefaseerde productgegevens (nog niet live) en de mogelijkheid om de inhoud voor te bereiden. Deze nieuwe inhoud wordt live weergegeven met de introductie van het product.

    >[!OPMERKING]
    >
    >Deze functie is alleen beschikbaar voor connectors van Adobe Commerce of Cloud Edition en andere leveranciers die tokenverificatie ondersteunen. Zie [Aan de slag] (https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/storefront/getting-started.html) voor meer informatie.

Eerst, zien hoe de auteurs tot gefaseerde productgegevens met CIF kunnen toegang hebben.

## Werken met gefaseerde productgegevens {#staged-product-data}

Een manier om gefaseerde productgegevens te openen is het gebruik van de productcockpit. Open de productcatalogus door op het pictogram Handel in het AEM te klikken. Hierdoor hebt u toegang tot live productgegevens. De filtertab links openen en uitvouwen **STAGED CATALOGUS**. Met de voorvertoningsgegevens hebt u nu toegang tot de gefaseerde productgegevens voor elk gewenst moment. De gefaseerde gegevens omvatten nieuwe categorieën, producten, of bijgewerkte gebieden zoals prijs.

![werkcockpit](assets/staged-cockpit.png)

Het is mogelijk om een voorvertoning van een opslagruimte met gefaseerde gegevens weer te geven met de tijdverdraaiingsweergave. Open de editor en schakel over naar de modus voor tijdverdraaiing. Selecteer een datum in de toekomst. U ziet de informatie boven op de editor dat u de pagina voor een bepaalde datum bekijkt.

![tijdverdraaiing werkgebied](assets/staged-timewarp.png)

U kunt nu door de catalogus bladeren met de gegevens in het werkgebied. Als u een gefaseerde categorie of productpagina opent, zal de redacteur een visuele indicator tonen.

![podium plp](assets/staged-plp.png)

    >[!OPMERKING]
    >
    >Omnissearch heeft geen context en retourneert dus alleen live productcatalogusgegevens

## AEM starten {#launches}

Met AEM Launches kunt u inhoud maken voor gefaseerde productgegevens. Als u niet bekend bent met Launches, volgt u de documentatiekoppeling onder het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources). De datum van de Lancering wordt dan gebruikt om tot gefaseerde productgegevens toegang te hebben.

![start](assets/staged-launch.png)

De kiezers respecteren de startdatum met de gefaseerde indicator aan de rechterkant.

![werkgebiedkiezer](assets/staged-picker.png)

## Volgende functies {#what-is-next}

Nu u dit deel van de reis hebt voltooid, moet u:

* begrijpen de concepten van een gefaseerde productcatalogus en inhoud met Launches
* toegang hebben tot gegevens uit de gefaseerde productcatalogus via productcockpit en editor

U bent nu klaar om te beheren [productreervaringen](product-experience-management.md). Voor AEM Inhoud en Handel zijn echter veel extra opties beschikbaar. Bekijk enkele aanvullende bronnen die beschikbaar zijn in het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources) voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

* [Product Cockpit](/help/commerce-cloud/authoring/product-cockpit.md)
* [Aan de slag](/help/commerce-cloud/getting-started.md)
* [Lanceringen](/help/sites-cloud/authoring/launches/overview.md)
