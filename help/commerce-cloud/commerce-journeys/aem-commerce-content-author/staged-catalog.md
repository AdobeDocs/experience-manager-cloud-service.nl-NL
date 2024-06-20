---
title: Ervaringen met gefaseerde productcatalogi beheren
description: Leer hoe u ervaringen met gefaseerde productcatalogi beheert.
exl-id: 1db18818-b8e0-4127-8a65-dc3dea1f2927
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Werken met nog niet voltooide productcataloguservaringen {#building-experiences}

Leer hoe u ervaringen met gefaseerde productcatalogi beheert.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de reis AEM Content en Commerce: [Productcataloguspagina&#39;s en -sjablonen beheren](catalog-templates.md)hebt u geleerd hoe u ervaringen met productcatalogi kunt beheren en samenstellen op basis van sjablonen.

Dit artikel bouwt voort op die grondbeginselen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de ervaring van de productcatalogus kunt beheren op basis van gefaseerde productgegevens en AEM Launches. Vaak moeten auteurs zich tegelijkertijd voorbereiden op een volgende productintroductie (bijvoorbeeld een nieuwe kledingcollectie). Dit vereist toegang tot gefaseerde productgegevens (nog niet live) en de mogelijkheid om de inhoud voor te bereiden. Deze nieuwe inhoud wordt live weergegeven met de introductie van het product.

    >[!OPMERKING]
    >
    >Deze functie is alleen beschikbaar bij Adobe Commerce of Cloud Edition en connectors van derden die tokenverificatie ondersteunen. Zie [Aan de slag] (https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/storefront/getting-started.html) voor meer informatie.

Eerst, zien wij hoe de auteurs tot gefaseerde productgegevens met CIF kunnen toegang hebben.

## Werken met gefaseerde productgegevens {#staged-product-data}

Een manier om gefaseerde productgegevens te openen is het gebruik van de productcockpit. Open de productcatalogus door op het Commerce-pictogram in het AEM te klikken. Hierdoor hebt u toegang tot live productgegevens. De filtertab links openen en uitvouwen **STAGED CATALOGUS**. Met de voorvertoningsgegevens hebt u nu toegang tot de gefaseerde productgegevens voor elk gewenst moment. De gefaseerde gegevens omvatten nieuwe categorieën, producten, of bijgewerkte gebieden zoals prijs.

![werkcockpit](assets/staged-cockpit.png)

Het is mogelijk om een voorvertoning van een opslagruimte met gefaseerde gegevens weer te geven met de tijdverdraaiingsweergave. Open de editor en schakel over naar de modus voor tijdverdraaiing. Selecteer een toekomstige datum. U ziet de informatie boven op de editor dat u de pagina voor een bepaalde datum bekijkt.

![tijdverdraaiing van werkgebied](assets/staged-timewarp.png)

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

U kunt nu [productervaring](product-experience-management.md). Voor AEM Content en Commerce zijn echter veel extra opties beschikbaar. Bekijk enkele aanvullende bronnen die beschikbaar zijn in het dialoogvenster [Sectie Aanvullende bronnen](#additional-resources) voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

* [Product Cockpit](/help/commerce-cloud/authoring/product-cockpit.md)
* [Aan de slag](/help/commerce-cloud/getting-started.md)
* [Lanceringen](/help/sites-cloud/authoring/launches/overview.md)
