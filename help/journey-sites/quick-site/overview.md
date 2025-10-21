---
title: AEM Quick Site Creation Journey
description: Begin hier voor een begeleide reis door het gebruiksvriendelijke AEM Quick Site Creation-hulpmiddel om de front-end ontwikkeling van uw AEM-site te stroomlijnen en uw site snel aan te passen zonder kennis van AEM-backend.
exl-id: b8218232-0298-4b16-9dab-fa59be592a24
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
recommendations: display, noCatalog
source-git-commit: 0a458616afad836efae27e67dbe145fc44bee968
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 1%

---


# AEM Quick Site Creation Journey {#quick-site-creation-journey}

{{traditional-aem}}

Begin hier voor een begeleide reis door het gebruiksvriendelijke AEM Quick Site Creation-hulpmiddel om de front-end ontwikkeling van uw AEM-site te stroomlijnen en uw site snel aan te passen zonder kennis van AEM-backend.

## Inleiding {#introduction}

AEM Sites is een krachtig hulpmiddel voor het maken en beheren van digitale ervaringen. Inhoudsauteurs kunnen eenvoudig digitale ervaringen maken met de siteeditor en de inhoud ordenen met de siteconsole, terwijl ze de inhoud live kunnen zien zoals deze door AEM aan uw publiek wordt geleverd via verschillende kanalen.

Met het hulpprogramma AEM Quick Site Creation kunnen niet-ontwikkelaars snel een geheel nieuwe site maken met behulp van sitesjablonen. Nadat u de site hebt gemaakt, kunt u met het gereedschap Snel site maken het thema en de opmaak van de AEM-site (JavaScript, CSS en statische bronnen) snel aanpassen. Hierdoor kan de front-end ontwikkelaar, die geen kennis van AEM nodig heeft, onafhankelijk van en parallel met de makers van de inhoud werken. De AEM-beheerder downloadt eenvoudig het site-thema en stuurt het naar de front-end ontwikkelaar die het aanpast met hun favoriete tools en legt de wijzigingen vervolgens vast aan de AEM-codeopslagplaats, die vervolgens wordt geïmplementeerd.

Door elke kennis van ontwikkelaars voor het maken van sites te elimineren, de AEM-kennisvereisten voor front-end ontwikkeling te elimineren en de ontwikkeling van thema&#39;s parallel aan het maken van content te laten verlopen, versnelt het AEM Quick Site Creation-hulpprogramma de time-to-value-periode van uw site aanzienlijk en vergroot het de aanpassingsmogelijkheden en de implementatieflexibiliteit van uw site.

## Video-overzicht {#video-overview}

Voor een snel overzicht van deze eigenschap in actie, [&#x200B; kunt u op deze vijf minieme inleiding &#x200B;](https://www.youtube.com/watch?v=NQeQ1jZ7ZBw) letten.

Deze documentatietraject leidt u door alle functies in de video stap voor stap en in detail, zodat u de workflow begrijpt en het proces opnieuw kunt maken in uw eigen omgeving.

## AEM-documentatiereizen {#documentation-journeys}

[&#x200B; de Reis van de Documentatie van A &#x200B;](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende, gecompliceerde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die aan AEM nieuw kan zijn, een bedrijfsprobleem van begin tot eind begrijpen en oplossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of kennis van AEM.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op informatie van Adobe over het meest recente onderzoek, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

Als je wilt weten hoe Adobe aanraadt om zakelijke kwesties met AEM op te lossen, dan is AEM Sites Journey de plek waar je moet beginnen.

## Publiek {#audience}

Deze reis beschrijft de vereisten, de stappen, en de benadering om de thema&#39;s van AEM Sites aan te passen. Zijn belangrijkste publiek is de front-end ontwikkelaar, die geen kennis van AEM nodig heeft. Om het hele proces te illustreren, zijn er echter beheerders bij betrokken, die verondersteld worden basiskennis van AEM Sites en Cloud Manager te hebben. In de praktijk, kunnen de veelvoudige mensen veelvoudige rollen dienen en deze reis steunt perspectieven van zowel beheerders als front-end ontwikkelaars.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Front-endontwikkelaar | Hiermee past u het sitethema aan | Neemt thema door de beheerder van AEM wordt verstrekt en past het aan zodat die aan de plaats van AEM kan worden opgesteld. |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die wordt geleverd als sites | Inhoudsauteurs maken op AEM inhoud die wordt weergegeven met het thema dat door de front-end ontwikkelaar is aangepast. |
| AEM-beheerder | Hiermee wordt een nieuwe AEM-site gemaakt | De beheerder van AEM leidt tot een nieuwe plaats die op een malplaatje wordt gebaseerd en dan verstrekt de front-end ontwikkelaar van een thema om aan te passen. |
| Cloud Manager-beheerder | Hiermee maakt u pijpleidingen en verleent u toegang | De Cloud Manager Administrator maakt de front-end pijplijn en biedt toegang tot de front-end ontwikkelaar om aanpassingen te kunnen doorvoeren in de AEM git-opslagplaats. |

## De AEM Quick Site Creation Reis {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. De volgende artikelen bieden u basiskennis van het maken en aanpassen van AEM-sites met het gereedschap Snel site maken en bieden een koppeling naar gedetailleerde technische documentatie.

| Aantal | Artikel | Beschrijving | Verantwoordelijke rol |
|---|---|---|--|
| 0 | AEM Quick Site Creation Journey | Dit document | AEM- en Cloud Manager-beheerders |
| 1 | [&#x200B; Begrijp Cloud Manager en het Snelle Werkschema van de Verwezenlijking van de Plaats &#x200B;](cloud-manager.md) | Meer informatie over Cloud Manager en hoe het nieuwe proces voor het maken van de Snelle site samenbrengt. | AEM-beheerder |
| 2 | [&#x200B; creeer plaats van malplaatje &#x200B;](create-site.md) | Leer hoe u snel een AEM-site kunt maken met een sitesjabloon. | AEM-beheerder |
| 3 | [&#x200B; Opstelling uw pijpleiding &#x200B;](pipeline-setup.md) | Maak een front-end pijplijn om de aanpassing van het thema van uw site te beheren. | Cloud Manager-beheerder |
| 4 | [&#x200B; de toegang van de Verlening tot de front-end ontwikkelaar &#x200B;](grant-access.md) | Aan boord van de front-end ontwikkelaars in Cloud Manager zodat ze toegang hebben tot uw AEM-site git-opslagplaats en -pijpleiding. | Cloud Manager-beheerder |
| 5 | [&#x200B; wint de toegangsinformatie van de git bewaarplaats &#x200B;](retrieve-access.md) terug | Leer hoe de front-end ontwikkelaar Cloud Manager gebruikt om toegang te krijgen tot informatie in de git-opslagplaats. | Front-endontwikkelaar |
| 6 | [&#x200B; pas het plaatsthema &#x200B;](customize-theme.md) aan | Leer hoe u een site-thema maakt, aanpast en test met live AEM-inhoud. | Front-endontwikkelaar |
| 7 | [&#x200B; stel uw aangepast thema &#x200B;](deploy-theme.md) op | Leer hoe te om het plaatsthema op te stellen gebruikend de pijpleiding. | Front-endontwikkelaar |

## Volgende functies {#what-is-next}

U kunt nu aan de slag met uw Adobe Quick Site Creation-tocht.

* Als u een beheerder van AEM of van Cloud Manager bent, of als u zowel front-end ontwikkelaar als beheerderrollen dient, of als u eenvoudig het proces van begin tot eind in AEM wilt begrijpen, begin bij het begin van de reis met [&#x200B; Cloud Manager &#x200B;](cloud-manager.md) begrijpen zoals hieronder vermeld.
* Als u slechts voor front-end ontwikkeling verantwoordelijk bent en met de beheerders van AEM en van Cloud Manager zult in wisselwerking staan, kunt u direct aan [&#x200B; overslaan terugwinnen de informatie van de de toegangstoegang van de git van de git &#x200B;](retrieve-access.md) om toegang tot de git bewaarplaats van AEM te krijgen en beginnen aan het aanpassen.
* Als u reeds AEM Sites en Cloud Manager het werk begrijpt en direct met configuratie wilt beginnen, kunt u [&#x200B; direct overslaan aan het creëren van een plaats van een malplaatje &#x200B;](create-site.md).

## Aanvullende bronnen {#additional-resources}

Zie deze extra bronnen voor meer informatie over hoe de krachtige functies van AEM samenwerken.

* [&#x200B; AEM as a Cloud Service technische documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=nl-NL) - als u reeds een vast begrip van AEM hebt, kunt u de diepgaande technische documenten direct willen raadplegen.
* [&#x200B; Documentatie van het Beleid van de Plaats &#x200B;](/help/sites-cloud/administering/site-creation/create-site.md) - Controle uit de technische documenten op plaatsverwezenlijking voor meer details op de Snelle eigenschappen van het hulpmiddel van de Aanmaak van de Plaats.
