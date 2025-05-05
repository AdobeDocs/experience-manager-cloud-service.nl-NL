---
title: Reis voor snel maken van site AEM
description: Begin hier voor een begeleide reis door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Aanmaak van de Plaats om de front-end ontwikkeling van uw AEM Plaats te stroomlijnen en snel uw plaats aan te passen zonder AEM achtergrondkennis.
exl-id: b8218232-0298-4b16-9dab-fa59be592a24
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
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

Voor een snel overzicht van deze eigenschap in actie, [ kunt u op deze vijf minieme inleiding ](https://www.youtube.com/watch?v=NQeQ1jZ7ZBw) letten.

Deze documentatietraject leidt u door alle functies in de video stap voor stap en in detail, zodat u de workflow begrijpt en het proces opnieuw kunt maken in uw eigen omgeving.

## AEM Documentenreizen {#documentation-journeys}

[ de Reis van de Documentatie van A ](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende, ingewikkelde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op basis van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie door consultants van de Adobe en feedback van klantprojecten.

Als u wilt weten hoe de Adobe aanbeveelt om vestigingenzaken met AEM op te lossen, zijn de Reizen van AEM Sites waar te beginnen.

## Publiek {#audience}

Deze reis beschrijft de vereisten, de stappen, en de benadering om de thema&#39;s van AEM Sites aan te passen. Het primaire publiek is de front-end ontwikkelaar, die geen kennis van AEM nodig heeft. Om het hele proces te illustreren, zijn er echter beheerders bij betrokken, die verondersteld worden basiskennis van AEM Sites en Cloud Manager te hebben. In de praktijk, kunnen de veelvoudige mensen veelvoudige rollen dienen en deze reis steunt perspectieven van zowel beheerders als front-end ontwikkelaars.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Front-endontwikkelaar | Hiermee past u het sitethema aan | Neemt thema dat door de AEM beheerder wordt verstrekt en past het aan zodat die aan de plaats van de AEM kan worden opgesteld. |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die wordt geleverd als sites | Inhoudsauteurs maken inhoud op AEM die wordt weergegeven met het thema dat door de front-end ontwikkelaar is aangepast. |
| AEM-beheerder | Hiermee wordt een nieuwe AEM gemaakt | De AEM beheerder leidt tot een nieuwe plaats die op een malplaatje wordt gebaseerd en verstrekt dan de front-end ontwikkelaar van een thema om aan te passen. |
| Cloud Manager-beheerder | Hiermee maakt u pijpleidingen en verleent u toegang | De beheerder van Cloud Manager maakt de front-end pijpleiding en verleent toegang tot de front-end ontwikkelaar om aanpassingen aan de AEM git bewaarplaats te kunnen begaan. |

## De AEM weg voor het maken van de snelle site {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. De volgende artikelen bieden u basiskennis van het maken en aanpassen van AEM sites met het gereedschap Snel site maken en bieden een koppeling naar gedetailleerde technische documentatie.

| Aantal | Artikel | Beschrijving | Verantwoordelijke rol |
|---|---|---|--|
| 0 | Reis voor snel maken van site AEM | Dit document | AEM- en Cloud Manager-beheerders |
| 1 | [ Begrijp Cloud Manager en het Snelle Werkschema van de Verwezenlijking van de Plaats ](cloud-manager.md) | Meer informatie over Cloud Manager en hoe het nieuwe proces voor het maken van de Snelle site samenbrengt. | AEM-beheerder |
| 2 | [ creeer plaats van malplaatje ](create-site.md) | Leer hoe u snel een AEM site kunt maken met een sitesjabloon. | AEM-beheerder |
| 3 | [ Opstelling uw pijpleiding ](pipeline-setup.md) | Maak een front-end pijplijn om de aanpassing van het thema van uw site te beheren. | Cloud Manager-beheerder |
| 4 | [ de toegang van de Verlening tot de front-end ontwikkelaar ](grant-access.md) | Aan boord van de front-end ontwikkelaars in Cloud Manager zodat hebben zij toegang tot uw AEM plaats git bewaarplaats en pijpleiding. | Cloud Manager-beheerder |
| 5 | [ wint de toegangsinformatie van de git bewaarplaats ](retrieve-access.md) terug | Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot informatie in de git-opslagplaats. | Front-endontwikkelaar |
| 6 | [ pas het plaatsthema ](customize-theme.md) aan | Leer hoe u een site-thema maakt, aanpast en test met live AEM-inhoud. | Front-endontwikkelaar |
| 7 | [ stel uw aangepast thema ](deploy-theme.md) op | Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding. | Front-endontwikkelaar |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan met uw Adobe voor het snel maken van sites.

* Als u een AEM of beheerder van Cloud Manager bent, of als u zowel front-end ontwikkelaar als beheerderrollen dient, of als u eenvoudig het proces van begin tot eind in AEM wilt begrijpen, begin bij het begin van de reis met [ Cloud Manager ](cloud-manager.md) begrijpen zoals hieronder vermeld.
* Als u slechts voor front-end ontwikkeling verantwoordelijk bent en met de AEM en beheerders van Cloud Manager zult in wisselwerking staan, kunt u direct aan [ overslaan terugwinnen de toegangsinformatie van de git bewaarplaats ](retrieve-access.md) om toegang tot de AEM git bewaarplaats te krijgen en beginnen aan het aanpassen.
* Als u reeds AEM Sites en Cloud Manager het werk begrijpt en direct met configuratie wilt beginnen, kunt u [ direct overslaan aan het creëren van een plaats van een malplaatje ](create-site.md).

## Aanvullende bronnen {#additional-resources}

Bekijk deze extra bronnen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [ AEM as a Cloud Service technische documentatie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=nl-NL) - als u reeds een vast begrip van AEM hebt, kunt u de diepgaande technische documenten direct willen raadplegen.
* [ Documentatie van het Beleid van de Plaats ](/help/sites-cloud/administering/site-creation/create-site.md) - Controle uit de technische documenten op plaatsverwezenlijking voor meer details op de Snelle eigenschappen van het hulpmiddel van de Aanmaak van de Plaats.
