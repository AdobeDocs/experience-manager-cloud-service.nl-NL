---
title: AEM as a Cloud Service introductie van on-boarding
description: Begin hier voor een overzicht van de begeleide journey via het onboarding proces naar AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
recommendations: noDisplay
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 2%

---


# Onboarding Journaal {#onboarding-journey}

Gefeliciteerd met het kiezen van AEM as a Cloud Service! Dit document is het uitgangspunt voor een geleide reis door het instapproces. Of u nu een nieuwe toepassing implementeert of een bestaande toepassing migreert, deze instapreis zorgt ervoor dat uw teams zijn ingesteld en toegang hebben tot AEM as a Cloud Service.

## Inleiding {#introduction}

Adobe Experience Manager is een krachtige suite van composable content services die snel indrukwekkende, persoonlijke ervaringen bieden over elk kanaal, waardoor inhoud voor iedereen wordt ontgrendeld. **Edge Delivery Services** Dit is de nieuwste innovatie in Adobe Experience Manager die de snelheid van de content kan verhogen en uitzonderlijke ervaringen oplevert. Leer hoe u aan de slag kunt met Edge Delivery Services, door te gaan [deze pagina](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html). Als u wilt weten hoe u Edge Delivery Services gebruikt, raadpleegt u de [Zelfstudie voor ontwikkelaars](https://www.hlx.live/developer/tutorial) pagina.

Onboarding is het proces waarin een aangewezen systeembeheerder opstelling AEM as a Cloud Service voor uw organisatie. Dit proces omvat de eerste levering van cloudbronnen en het toewijzen van gebruikers aan rollen op basis van hun taakverantwoordelijkheden. Dientengevolge, kan elk lid zich aanmelden en tot hun middel toegang hebben op AEM as a Cloud Service.

![De instapreis](/help/journey-onboarding/assets/onboarding-journey.png)

Deze gids leidt u door de belangrijkste onboarding onderwerpen zodat wanneer u klaar bent het volgende heeft:

* Volledige kennis van de verschillende voorwaarden, services en gebruikers die bij het instapproces betrokken zijn.
* Uw team kon aan de slag gaan en de eerste stappen nemen in de richting van het leren hoe te om inhoud voor uw AEM as a Cloud Service toepassing te ontwerpen en te ontwikkelen.

Dientengevolge:

* Uw team is ingesteld en heeft toegang tot cloudbronnen.
* AEM auteurs hebben toegang tot AEM as a Cloud Service en kunnen beginnen met het maken van inhoud.
* AEM ontwikkelaars en plaatsingsmanagers hebben toegang tot AEM as a Cloud Service en kunnen beginnen creërend en plaatsend douanetoepassingen.

## Concepten en doelstellingen {#concepts}

Hoewel er veel te leren kan zijn wanneer begonnen met AEM as a Cloud Service, conceptueel zijn er slechts een paar, logische stukken.

* **Het contract** - U moet bekend zijn met uw contract voor Adobe, aangezien hierin aspecten van het instapproces worden gedefinieerd.
* **Admin Console** - Waar gebruikers worden beheerd en rollen worden toegewezen.
* **Cloud Manager** - Het hulpmiddel om middelen zoals programma&#39;s en milieu&#39;s op te zetten. Het is ook waar u toegang hebt tot it en pijpleidingen creeert om uw douanecode te beheren en op te stellen.

Deze begrippen worden in detail uiteengezet in deze instapreis. Het doel is dat je aan het einde van de reis:

* de noodzakelijke toegang van de gebruiker tot AEM as a Cloud Service hebben verleend.
* De eerste cloudbronnen voor uw project hebben ingesteld.
* Weet hoe u uw eerste code kunt implementeren en uw eerste inhoud kunt ontwerpen.

In feite heb je de grond bereikt met je nieuwe AEM as a Cloud Service project.

## Publiek {#audience}

De instapreis wordt specifiek geschreven voor de **systeembeheerder** van de nieuwe klant om as a Cloud Service en AEM in het algemeen te AEM. De systeembeheerder is het individu dat eerst door Adobe wordt gecontacteerd nadat uw AEM as a Cloud Service contract wordt ondertekend. Zij zijn typisch de eerste persoon aan toegang en opstelling uw middelen op AEM as a Cloud Service. Als u dit onderwerp leest, is het waarschijnlijk dat u de systeembeheerder bent.

De systeembeheerder beheert alle aspecten van de gebruikers AEMaaCS van hun organisatie, van toegang tot toestemmingen. Nochtans moet de systeembeheerder met andere persona&#39;s in wisselwerking staan langs de weg.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Systeembeheerder | Doel van deze reis, verstrekt aanvankelijke levering van wolkenmiddelen en toewijzing van gebruikers aan aangewezen rollen die op hun baanverantwoordelijkheden worden gebaseerd | Beheert alle aspecten van gebruikers van toegang tot machtigingen |
| Inhoudsauteur | Hiermee maakt en bekijkt u de inhoud in AEM | Als auteurs machtigingen hebben verleend door de systeembeheerder, kunnen ze hun eigen reis maken en inhoud maken |
| Developer | Ontwikkelt AEM toepassingen die inhoud uit verschillende bronnen gebruiken | Zodra verleend de toestemmingen door de systeembeheerder, kunnen de ontwikkelaars hun eigen reis beginnen die oplossingen ontwikkelen |
| Implementatiebeheer | Voegt of werkt een milieu bij, stelt pijpleidingen in werking, en stelt code aan AEM milieu of code-kwaliteit op. | Zodra verleend de toestemmingen door de systeembeheerder, plaatsingsmanagers kunnen hun eigen reis leiden plaatsingen |

Deze instapkaartgids illustreert het volledige proces van instapweigering als systeembeheerder. De rollen van AEM gebruikers, ontwikkelaars, en plaatsingsmanagers worden verkend kort als extra, facultatieve delen van de reis.

>[!TIP]
>
>Als u as a Cloud Service bent om te AEM en vertrouwd met AEM bent en van op-gebouw of Adobe Managed Services migreert, ben zeker om uit te checken [AEM as a Cloud Service migratiereis](/help/journey-migration/getting-started.md).

## Reisoverzicht aan boord {#overview}

De volgende artikelen beschrijven in detail de kernconcepten op het instapniveau en geven u fundamentele kennis van AEM as a Cloud Service. Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom, als u nieuw aan het instappen bent, adviseert de Adobe dat u bij het begin begint en opeenvolgend vordert.

| Aantal | Artikel | Beschrijving | Publiek |
|---|---|---|---|
| 0 | Onboarding Journaal | Dit document | Systeembeheerder |
| 1 | [Voorbereiding aan boord](preparation.md) | Alvorens het aan boord gaan proces begint, zijn er een aantal of voorbereidende stappen die de systeembeheerder moet begrijpen alvorens in het systeem te registreren. | Systeembeheerder |
| 2 | [as a Cloud Service terminologie AEM](terminology.md) | Voordat u zich voor het eerst aanmeldt bij AEMaaCS, is het nuttig om enkele terminologie van het systeem en de basisstructuur te begrijpen. | Systeembeheerder |
| 3 | [De Admin Console](admin-console.md) | Leer wat de Admin Console is, hoe te login, en hoe te om uw profiel als systeembeheerder te verifiëren. | Systeembeheerder |
| 4 | [Productprofielen voor Cloud Manager toewijzen](assign-profiles-cloud-manager.md) | Bekijk de productprofielen van Cloud Manager en leer hoe u teamleden toewijst aan productprofielen van Cloud Manager. | Systeembeheerder |
| 5 | [Cloud Manager openen](cloud-manager.md) | Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen. | Systeembeheerder |
| 6 | [Een programma maken](create-program.md) | Leer hoe u een programma maakt met Cloud Manager. | Systeembeheerder |
| 7 | [Omgevingen maken](create-environments.md) | Leer hoe u een omgeving kunt maken met Cloud Manager. | Systeembeheerder |
| 8 | [AEM productprofielen toewijzen](assign-profiles-aem.md) | Leer hoe de Beheerder van het Systeem uw teamleden aan productprofielen in AEM as a Cloud Service toewijst. | Systeembeheerder |
| 9 | [Taken van ontwikkelaar- en implementatiebeheer](developers.md) | Optioneel - Leer als ontwikkelaar hoe u toegang krijgt tot de Cloud Manager Git en hoe u als implementatiebeheerder pijpleidingen kunt instellen en code kunt implementeren in Cloud Manager. | Ontwikkelaars en implementatiemanagers |
| 10 | [AEM](aem-users.md) | Optioneel - Leer als AEM auteur hoe u toegang kunt krijgen tot AEM as a Cloud Service instantie en hoe u vertrouwd bent met het ontwerpen van inhoud voor AEM as a Cloud Service. | AEM |

## Volgende functies {#what-is-next}

U bent nu klaar om uw AEM as a Cloud Service instapreis te beginnen. U wordt aangemoedigd om door te gaan naar het volgende deel van de reis en het artikel te lezen [Voorbereiding aan boord](preparation.md)

## AEM Documentenreizen {#documentation-journeys}

[Een documentatiereis](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende, gecompliceerde onderwerpen en eigenschappen samen. Het verstrekt een verhaal dat een lezer nieuw helpt om een bedrijfsprobleem van begin tot eind te AEM begrijpen en op te lossen, terwijl het veronderstellen van minimaal voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op basis van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie door consultants van de Adobe en feedback van klantprojecten.

Als u wilt weten welke Adobe u adviseert om uw team op uw nieuwe AEM as a Cloud Service toepassing in te laten gaan, begin hier!

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [Aan boord gaan naar AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/onboarding.html) - In deze korte video wordt een overzicht gegeven van het proces voor het aan boord nemen van Cloud Servicen voor AEM.
