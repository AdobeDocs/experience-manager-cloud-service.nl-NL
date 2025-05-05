---
title: AEM as a Cloud Service On-boarding Journey Introduction
description: Begin hier voor een overzicht van de begeleide journey via het onboarding proces naar AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
recommendations: noDisplay
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 2%

---


# Onboarding Journaal {#onboarding-journey}

Gefeliciteerd met het kiezen van AEM as a Cloud Service! Dit document is het uitgangspunt voor een geleide reis door het instapproces. Of u nu een nieuwe toepassing implementeert of een bestaande toepassing migreert, deze reis aan boord zet uw teams samen. Het zorgt ervoor dat ze toegang hebben tot AEM as a Cloud Service.

## Inleiding {#introduction}

Adobe Experience Manager is een krachtige suite van composable content services die snel indrukwekkende, persoonlijke ervaringen bieden over elk kanaal, waardoor inhoud voor iedereen wordt ontgrendeld. **Edge Delivery Services** is de recentste innovatie in Adobe Experience Manager die extreme inhoudssnelheid toelaat en uitzonderlijke ervaringen levert. Leer hoe te beginnen met Edge Delivery Services, door [ Overzicht van Edge Delivery Services te raadplegen ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/overview). Om te begrijpen hoe te om Edge Delivery Services te gebruiken, zie de [&#128279;](https://www.aem.live/developer/tutorial) pagina van het Leerprogramma van de 1&rbrace; Ontwikkelaar.

Onboarding is het proces waarbij een aangewezen systeembeheerder AEM as a Cloud Service voor uw organisatie instelt. Dit proces omvat de eerste levering van cloudbronnen en het toewijzen van gebruikers aan rollen op basis van hun taakverantwoordelijkheden. Dientengevolge, kan elk lid zich aanmelden en tot hun middel op AEM as a Cloud Service toegang hebben.

![ de reis aan boord ](/help/journey-onboarding/assets/onboarding-journey.png).

Deze gids leidt u door de belangrijkste onboarding onderwerpen zodat wanneer u klaar bent het volgende heeft:

* Volledige kennis van de verschillende voorwaarden, services en gebruikers die bij het instapproces betrokken zijn.
* Uw team kon aan de slag en de eerste stappen nemen in de richting van het leren om inhoud voor uw AEM as a Cloud Service-toepassing te ontwerpen en te ontwikkelen.

Dientengevolge:

* Uw team is ingesteld en heeft toegang tot cloudbronnen.
* AEM auteurs hebben toegang tot AEM as a Cloud Service en kunnen beginnen met het maken van inhoud.
* AEM ontwikkelaars en implementatiemanagers hebben toegang tot AEM as a Cloud Service en kunnen aangepaste toepassingen gaan maken en implementeren.

## Concepten en doelstellingen {#concepts}

Hoewel er wellicht veel te leren valt wanneer men met AEM as a Cloud Service aan de slag gaat, zijn er conceptueel slechts een paar logische stukken.

* **het Contract** - u moet met uw Adobe contract vertrouwd zijn aangezien het aspecten van het onboarding proces bepaalt.
* **Admin Console** - waar de gebruikers worden geleid en de rollen worden toegewezen.
* **Cloud Manager** - het hulpmiddel aan opstellingsmiddelen zoals programma&#39;s en milieu&#39;s. Het is ook waar u tot Git toegang hebt en pijpleidingen creeert om uw douanecode te beheren en op te stellen.

Deze begrippen worden in detail uiteengezet in deze instapreis. Het doel is dat aan het eind van de reis, u het volgende kunt doen:

* Bied de benodigde toegang van de gebruiker tot AEM as a Cloud Service.
* Stel de eerste cloudbronnen voor uw project in.
* Weet hoe u uw eerste code kunt implementeren en uw eerste inhoud kunt ontwerpen.

In feite heb je de grond op de grond gelopen met je nieuwe AEM as a Cloud Service-project!

## Publiek {#audience}

De onboarding reis wordt geschreven specifiek voor de **systeembeheerder** van klanten die aan AEM as a Cloud Service en aan AEM in het algemeen nieuw zijn. De systeembeheerder is het individu dat eerst contacten van de Adobe na uw contract van AEM as a Cloud Service wordt ondertekend. Meestal zijn ze de eerste die toegang krijgt tot en middelen instelt op AEM as a Cloud Service. Als u dit onderwerp leest, is het waarschijnlijk dat u de systeembeheerder bent.

De systeembeheerder beheert alle aspecten van de gebruikers AEMaaCS van hun organisatie, van toegang tot toestemmingen. Nochtans, moet de systeembeheerder met andere persona&#39;s in wisselwerking staan langs de weg.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Systeembeheerder | Het doel van deze reis biedt initiële provisioning van cloudbronnen en toewijzing van gebruikers aan de juiste rollen op basis van hun taakverantwoordelijkheden | Beheert alle aspecten van gebruikers van toegang tot machtigingen |
| Inhoudsauteur | Hiermee maakt en bekijkt u de inhoud in AEM | Als auteurs machtigingen hebben verleend door de systeembeheerder, kunnen ze hun eigen reis beginnen bij het maken van inhoud |
| Developer | Ontwikkelt AEM toepassingen die inhoud uit verschillende bronnen gebruiken | Zodra verleend de toestemmingen door de systeembeheerder, kunnen de ontwikkelaars hun eigen reis in het ontwikkelen van oplossingen beginnen |
| Implementatiebeheer | Voegt of werkt een milieu bij, stelt pijpleidingen in werking, en stelt code aan AEM milieu of code-kwaliteit op. | Zodra verleend de toestemmingen door de systeembeheerder, plaatsingsmanagers kunnen hun eigen reis leiden plaatsingen |

Deze instapkaartgids illustreert het volledige proces van instapweigering als systeembeheerder. De rollen van AEM gebruikers, ontwikkelaars, en plaatsingsmanagers worden verkend kort als extra, facultatieve delen van de reis.

>[!TIP]
>
>Als u aan AEM as a Cloud Service en vertrouwd met AEM bent en van op-gebouw of Adobe Managed Services migreert, controleer de [ Reis van de Migratie van AEM as a Cloud Service ](/help/journey-migration/getting-started.md).

## Reisoverzicht aan boord {#overview}

De volgende artikelen beschrijven in detail de kernconcepten voor instapweigering en geven u grondkennis van AEM as a Cloud Service. Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom, als u nieuw aan het instappen bent, adviseert de Adobe dat u bij het begin begint en opeenvolgend vordert.

| | Artikel | Beschrijving | Publiek |
|---|---|---|---|
| 0 | Onboarding Journaal | Dit document | Systeembeheerder |
| 1 | [ on boarding Preparation ](preparation.md) | Alvorens het aan boord gaan proces begint, zijn er een aantal of voorbereidende stappen die de systeembeheerder moet begrijpen alvorens in het systeem te registreren. | Systeembeheerder |
| 2 | [ Terminologie van AEM as a Cloud Service ](terminology.md) | Voordat u zich voor het eerst aanmeldt bij AEMaaCS, is het nuttig om enkele terminologie van het systeem en de basisstructuur te begrijpen. | Systeembeheerder |
| 3 | [ de Admin Console ](admin-console.md) | Leer wat de Admin Console is, hoe te login, en hoe te om uw profiel als systeembeheerder te verifiëren. | Systeembeheerder |
| 4 | [ Toewijzend de Profielen van het Product van Cloud Manager ](assign-profiles-cloud-manager.md) | Bekijk Cloud Manager-productprofielen en leer hoe u teamleden kunt toewijzen aan Cloud Manager-productprofielen. | Systeembeheerder |
| 5 | [ Toegang Cloud Manager ](cloud-manager.md) | Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen. | Systeembeheerder |
| 6 | [ creeer een Programma ](create-program.md) | Leer hoe u een programma maakt met Cloud Manager. | Systeembeheerder |
| 7 | [ creeer milieu&#39;s ](create-environments.md) | Leer hoe u een omgeving kunt maken met Cloud Manager. | Systeembeheerder |
| 8 | [ Toewijzend AEM Profielen van het Product ](assign-profiles-aem.md) | Leer hoe de Beheerder van het Systeem uw teamleden aan productprofielen in AEM as a Cloud Service toewijst. | Systeembeheerder |
| 9 | [ Taken van de Manager van de Ontwikkelaar en van de Plaatsing ](developers.md) | Optioneel - Leer als ontwikkelaar hoe u toegang krijgt tot Cloud Manager Git en hoe u als implementatiebeheerder pijpleidingen kunt instellen en code kunt implementeren in Cloud Manager. | Ontwikkelaars en implementatiemanagers |
| 10 | [ AEM de Taken van de Gebruiker ](aem-users.md) | Optioneel - Leer als AEM auteur hoe u toegang krijgt tot een AEM as a Cloud Service-exemplaar en hoe u vertrouwd bent met de ontwerpinhoud voor AEM as a Cloud Service. | AEM |

## Wat nu? {#what-is-next}

Je bent nu klaar om je AEM as a Cloud Service-instapreis te starten. U wordt aangemoedigd om aan het volgende deel van de reis verder te gaan en het artikel [ te lezen Onboarding Preparation ](preparation.md)

## AEM documentatiereizen {#documentation-journeys}

[ de documentatietraject van A ](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende, gecompliceerde onderwerpen en eigenschappen. Het verstrekt een verhaal dat een lezer nieuw helpt om een bedrijfsprobleem van begin tot eind te AEM begrijpen en op te lossen, terwijl het veronderstellen van minimaal voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices. Zij worden geïnformeerd met behulp van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie van Adobe consultants en feedback van klantprojecten.

Als u wilt weten welke Adobe u adviseert om uw team op uw nieuwe toepassing van AEM as a Cloud Service te laten inloggen, begin hier.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [ Op het instappen aan AEM as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/onboarding) - Deze korte video geeft een overzicht van de Cloud Service op het instappen proces voor AEM.
