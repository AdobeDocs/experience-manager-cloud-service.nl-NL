---
title: Reis voor snel maken van site AEM
description: Begin hier voor een begeleide reis door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Aanmaak van de Plaats om de front-end ontwikkeling van uw AEM Plaats te stroomlijnen en snel uw plaats aan te passen zonder AEM achtergrondkennis.
exl-id: b8218232-0298-4b16-9dab-fa59be592a24
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 1%

---

# Reis voor snel maken van site AEM {#quick-site-creation-journey}

Begin hier voor een begeleide reis door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Aanmaak van de Plaats om de front-end ontwikkeling van uw AEM Plaats te stroomlijnen en snel uw plaats aan te passen zonder AEM achtergrondkennis.

## Inleiding {#introduction}

AEM Sites is een krachtig hulpmiddel voor het maken en beheren van digitale ervaringen. Inhoudsauteurs kunnen eenvoudig digitale ervaringen maken met de siteeditor en de inhoud indelen met de siteconsole, terwijl ze de inhoud live kunnen zien zoals deze via AEM aan uw publiek wordt geleverd.

Met het gereedschap AEM Snel site maken kunnen niet-ontwikkelaars snel een geheel nieuwe site maken met behulp van sitesjablonen. Nadat u de site hebt gemaakt, kunt u met het gereedschap Snel site maken het thema en de opmaak van de AEM site (JavaScript, CSS en statische bronnen) snel aanpassen. Hierdoor kan de front-end ontwikkelaar, die geen kennis van AEM nodig heeft, onafhankelijk van en parallel met de makers van de inhoud werken. De AEM beheerder downloadt eenvoudig het plaatsthema en verstrekt het aan de front-end ontwikkelaar die het gebruikend hun favoriete hulpmiddelen aanpast en dan de veranderingen in de AEM codebewaarplaats vastlegt, die dan wordt opgesteld.

Door elke kennis van ontwikkelaars voor het maken van sites te elimineren, AEM kennisvereisten voor front-end ontwikkeling te elimineren en de ontwikkeling van thema&#39;s parallel met het maken van inhoud te laten verlopen, zorgt het gereedschap Snel maken van sites voor een aanzienlijke versnelling van de tijd tot waarde van uw site en verhoogt het de aanpassingsmogelijkheden en de implementatieflexibiliteit van uw site.

## Video-overzicht {#video-overview}

Voor een snel overzicht van deze functie in actie, [je kunt deze vijf minuten durende inleiding bekijken .](https://www.youtube.com/watch?v=NQeQ1jZ7ZBw)

Deze documentatietraject leidt u door alle functies in de video stap voor stap en in detail, zodat u de workflow begrijpt en het proces opnieuw kunt maken in uw eigen omgeving.

## AEM Documentenreizen {#documentation-journeys}

[Een documentatiereis](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende, ingewikkelde onderwerpen en eigenschappen met elkaar door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op basis van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie door consultants van de Adobe en feedback van klantprojecten.

Als u wilt weten hoe de Adobe aanbeveelt om vestigingenzaken met AEM op te lossen, zijn de Reizen van AEM Sites waar te beginnen.

## Publiek {#audience}

Deze reis beschrijft de vereisten, de stappen, en de benadering om de thema&#39;s van AEM Sites aan te passen. Het primaire publiek is de front-end ontwikkelaar, die geen kennis van AEM nodig heeft. Om het hele proces te illustreren, zijn er echter beheerders bij betrokken, die verondersteld worden basiskennis van AEM Sites en Cloud Manager te hebben. In de praktijk, kunnen de veelvoudige mensen veelvoudige rollen dienen en deze reis steunt perspectieven van zowel beheerders als front-end ontwikkelaars.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Front-endontwikkelaar | Hiermee past u het sitethema aan | Neemt thema dat door de AEM beheerder wordt verstrekt en past het aan zodat die aan de plaats van de AEM kan worden opgesteld. |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die wordt geleverd als sites | Inhoudsauteurs maken inhoud op AEM die wordt weergegeven met het thema dat door de front-end ontwikkelaar is aangepast. |
| AEM-beheerder | Hiermee wordt een nieuwe AEM gemaakt | De AEM beheerder leidt tot een nieuwe plaats die op een malplaatje wordt gebaseerd en verstrekt dan de front-end ontwikkelaar van een thema om aan te passen. |
| Cloud Manager-beheerder | Hiermee maakt u pijpleidingen en verleent u toegang | De beheerder van de Manager van de Wolk leidt tot de front-end pijpleiding en verleent toegang tot de front-end ontwikkelaar om aanpassingen aan de AEM git bewaarplaats kunnen begaan. |

## De AEM weg voor het maken van de snelle site {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. De volgende artikelen bieden u basiskennis van het maken en aanpassen van AEM sites met het gereedschap Snel site maken en bieden een koppeling naar gedetailleerde technische documentatie.

| Aantal | Artikel | Beschrijving | Verantwoordelijke rol |
|---|---|---|--|
| 0 | Reis voor snel maken van site AEM | Dit document | Beheerders van AEM en cloud-beheer |
| 1 | [Inzicht krijgen in Cloud Manager en de workflow voor snel maken van sites](cloud-manager.md) | Leer meer over Cloud Manager en hoe dit het nieuwe proces voor het maken van de Snelle site samenbrengt. | AEM-beheerder |
| 2 | [Site maken van sjabloon](create-site.md) | Leer hoe u snel een AEM site kunt maken met een sitesjabloon. | AEM-beheerder |
| 3 | [De pijplijn instellen](pipeline-setup.md) | Maak een front-end pijplijn om de aanpassing van het thema van uw site te beheren. | Cloud Manager-beheerder |
| 4 | [Toegang verlenen aan de front-end ontwikkelaar](grant-access.md) | Aan boord van de front-end ontwikkelaars in Cloud Manager zodat hebben zij toegang tot uw AEM plaats git bewaarplaats en pijpleiding. | Cloud Manager-beheerder |
| 5 | [Toegangsgegevens van de opslagplaats ophalen](retrieve-access.md) | Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot gegevensopslagruimte. | Front-endontwikkelaar |
| 6 | [Het sitethema aanpassen](customize-theme.md) | Leer hoe u een site-thema maakt, aanpast en test met live AEM-inhoud. | Front-endontwikkelaar |
| 7 | [Uw aangepaste thema implementeren](deploy-theme.md) | Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding. | Front-endontwikkelaar |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan met uw Adobe voor het snel maken van sites.

* Als u een beheerder van de Manager van de AEM of van de Wolk bent, of als u zowel front-end ontwikkelaar als beheerderrollen dient, of als u eenvoudig het proces van begin tot eind in AEM wilt begrijpen, begin bij het begin van de reis met [Cloud Manager begrijpen](cloud-manager.md) zoals hieronder uiteengezet.
* Als u alleen verantwoordelijk bent voor de ontwikkeling op de voorgrond en met de beheerders van AEM en Cloud Manager werkt, kunt u rechtstreeks overslaan naar [Toegangsgegevens van de opslagplaats ophalen](retrieve-access.md) toegang krijgen tot de AEM git-opslagplaats en beginnen met aanpassen.
* Als u al begrijpt dat AEM Sites en Cloud Manager samenwerken en rechtstreeks met de configuratie willen beginnen, kunt u [Ga rechtstreeks naar het maken van een site vanuit een sjabloon.](create-site.md)

## Aanvullende bronnen {#additional-resources}

Bekijk deze extra bronnen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [as a Cloud Service technische documentatie AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - Als u al een duidelijk inzicht hebt in AEM, kunt u de diepgaande technische documenten direct raadplegen.
* [Documentatie voor sitebeheer](/help/sites-cloud/administering/site-creation/create-site.md) - Ontdek de technische documentatie bij het maken van de site voor meer informatie over de functies van het gereedschap Snel maken.
