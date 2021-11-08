---
title: Reis voor snel maken van site AEM
description: Begin hier voor een begeleide reis door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Aanmaak van de Plaats om de front-end ontwikkeling van uw AEM Plaats te stroomlijnen en snel uw plaats aan te passen zonder AEM achtergrondkennis.
source-git-commit: efeb97d4bd7e7c11ec2c0ba1244a32b8b9affdab
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# Reis voor snel maken van site AEM {#quick-site-creation-journey}

Begin hier voor een begeleide reis door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Aanmaak van de Plaats om de front-end ontwikkeling van uw AEM Plaats te stroomlijnen en snel uw plaats aan te passen zonder AEM achtergrondkennis.

>[!CAUTION]
>
>Het gereedschap Snel site maken is momenteel een technische voorvertoning. Het wordt ter beschikking gesteld voor test- en evaluatiedoeleinden en is niet bestemd voor gebruik in de productie, tenzij overeengekomen met Adobe Support.

## Inleiding {#introduction}

AEM Sites is een krachtig hulpmiddel voor het maken en beheren van digitale ervaringen. Content authors can easily create digital experiences using the sites editor and organize the content using the sites console, all while being able to see the content live as it will be delivered by AEM to your audiences across channels.

Met het gereedschap AEM Snel site maken kunnen niet-ontwikkelaars snel een nieuwe site maken met behulp van sitesjablonen. Nadat u de site hebt gemaakt, kunt u met het gereedschap Snel site maken het thema en de opmaak van de AEM site (JavaScript, CSS en statische bronnen) snel aanpassen. Hierdoor kan de front-end ontwikkelaar, die geen kennis van AEM nodig heeft, onafhankelijk van en parallel met de makers van de inhoud werken. De AEM beheerder downloadt eenvoudig het plaatsthema en verstrekt het aan de front-end ontwikkelaar die het gebruikend hun favoriete hulpmiddelen aanpast en dan de veranderingen in de AEM codebewaarplaats vastlegt, die dan wordt opgesteld.

By eliminating any developer knowledge for site creation, eliminating AEM knowledge requirements for front end development, and allowing theme development to proceed in parallel with content creation, the AEM Quick Site Creation tool greatly accelerates your site&#39;s time-to-value and increases your site customization and deployment agility.

## AEM Documentenreizen {#documentation-journeys}

[Een documentatiereis](/help/journey-documentation/home.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen met elkaar door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn ontworpen op basis van de beginselen van best practices, gebaseerd op de meest recente onderzoeken, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

If you want to know how Adobe recommends how to solve sites business cases with AEM, AEM Sites Journeys are where to start.

## Audience {#audience}

This journey lays out the requirements, steps, and approach to customize AEM Sites themes. Its primary audience is the front-end developer, who needs no knowledge of AEM. However, in order to illustrate the entire process, the journey involves administrators, who are assumed to have basic AEM Sites and Cloud Manager knowledge. In de praktijk, kunnen de veelvoudige mensen veelvoudige rollen dienen en deze reis steunt perspectieven van zowel beheerders als front-end ontwikkelaars.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Front-endontwikkelaar | Customizes the site theme | Neemt thema dat door de AEM beheerder wordt verstrekt en past het aan zodat die aan de plaats van de AEM kan worden opgesteld. |
| Content Author | Hiermee maakt en beheert u inhoud die wordt geleverd als sites | Content Authors create content on AEM that is rendered with the theme customized by the front-end developer. |
| AEM-beheerder | Creates a new AEM site | De AEM beheerder leidt tot een nieuwe plaats die op een malplaatje wordt gebaseerd en verstrekt dan de front-end ontwikkelaar van een thema om aan te passen. |
| Cloud Manager-beheerder | Creates pipelines and grants access | De beheerder van de Manager van de Wolk leidt tot de front-end pijpleiding en verleent toegang tot de front-end ontwikkelaar om aanpassingen aan de AEM git bewaarplaats kunnen begaan. |

## De AEM weg voor het maken van de snelle site {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. De volgende artikelen bieden u basiskennis van het maken en aanpassen van AEM sites met het gereedschap Snel site maken en bieden een koppeling naar gedetailleerde technische documentatie.

|#|Artikel|Beschrijving|Verantwoordelijke rol| |—|—|—|—| |0|AEM Snel site-ontwerppad|Dit document|AEM &amp; Cloud Manager-beheerders| |1|[Inzicht krijgen in Cloud Manager en de workflow voor snel maken van sites](cloud-manager.md)|Leer meer over Cloud Manager en hoe deze functie het nieuwe proces voor het maken van snelle sites samenbrengt.|AEM Beheerder| |2|[Site maken van sjabloon](create-site.md)|Leer hoe u snel een nieuwe AEM site kunt maken met een sitesjabloon.|AEM Beheerder| |3|[De pijplijn instellen](pipeline-setup.md)|Maak een front-end pijplijn om de aanpassing van het thema van uw site te beheren.|Beheerder van wolkenbeheer| |4|[Toegang verlenen aan de front-end ontwikkelaar](grant-access.md)|Aan boord van de front-end ontwikkelaars in Cloud Manager zodat hebben zij toegang tot uw AEM plaats git bewaarplaats en pijpleiding.|Beheerder van wolkenbeheer| |5|[Toegangsgegevens van opslagplaats ophalen](retrieve-access.md)|Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot informatie in de git-opslagplaats.|Front-End Developer|
|6|[Customize the site theme](customize-theme.md)|Learn how a site theme is built, how to customize it, and how to test it using live AEM content.|Front-endontwikkelaar| |7|[Uw aangepaste thema implementeren](deploy-theme.md)|Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding.|Front-End Developer|

## Volgende functies {#what-is-next}

You are now ready to get started on your Adobe Quick Site Creation journey.

* Als u een beheerder van de Manager van de AEM of van de Wolk bent, of als u zowel front-end ontwikkelaar als beheerderrollen dient, of als u eenvoudig het proces van begin tot eind in AEM wilt begrijpen, te beginnen bij het begin van de reis met [Cloud Manager begrijpen](cloud-manager.md) zoals hieronder uiteengezet.
* Als u alleen verantwoordelijk bent voor de ontwikkeling op de voorgrond en met de beheerders van AEM en Cloud Manager werkt, kunt u rechtstreeks overslaan naar [Toegangsgegevens van opslagplaats ophalen](retrieve-access.md) toegang krijgen tot de AEM git-opslagplaats en beginnen met aanpassen.
* If you already understand AEM Sites and Cloud Manager work together and want to start directly with configuration, you can [skip directly to creating a new site from a template.](create-site.md)

## Aanvullende bronnen {#additional-resources}

Bekijk deze extra bronnen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [AEM as a Cloud Service technical documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - If you already have a firm understanding of AEM, you may want to directly consult the in-depth technical docs.
* [Site Administration Documentation](/help/sites-cloud/administering/site-creation/create-site.md) - Check out the technical docs on site creation for more details on the Quick Site Creation tool&#39;s features.
