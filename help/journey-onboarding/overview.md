---
title: AEM as a Cloud Service On-boarding Journey Introduction
description: Begin hier voor een overzicht van de begeleide journey via het onboarding proces naar AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
recommendations: noDisplay
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 841e30bc279a3859ce9a302b18ddf566d8163100
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 2%

---


# Onboarding Journaal {#onboarding-journey}

Gefeliciteerd met het kiezen van AEM as a Cloud Service! Dit document is het uitgangspunt voor een geleide reis door het instapproces. Of u nu een nieuwe toepassing implementeert of een bestaande toepassing migreert, deze reis aan boord zet uw teams samen. Het zorgt ervoor dat ze toegang hebben tot AEM as a Cloud Service.

## Inleiding {#introduction}

Adobe Experience Manager is een krachtige suite van composable content services die snel indrukwekkende, persoonlijke ervaringen bieden over elk kanaal, waardoor inhoud voor iedereen wordt ontgrendeld. **Edge Delivery Services** is de recentste innovatie in Adobe Experience Manager die extreme inhoudssnelheid toelaat en uitzonderlijke ervaringen levert. Leer hoe te beginnen met Edge Delivery Services, door [&#x200B; Overzicht van Edge Delivery Services &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/edge-delivery/overview) te raadplegen. Om te begrijpen hoe te om Edge Delivery Services te gebruiken, zie de [&#x200B; pagina van het Leerprogramma van de Ontwikkelaar &#x200B;](https://www.aem.live/developer/tutorial).

Onboarding is het proces waarbij een aangewezen systeembeheerder AEM as a Cloud Service voor uw organisatie instelt. Dit proces omvat de eerste levering van cloudbronnen en het toewijzen van gebruikers aan rollen op basis van hun taakverantwoordelijkheden. Dientengevolge, kan elk lid zich aanmelden en tot hun middel op AEM as a Cloud Service toegang hebben.

![&#x200B; de reis aan boord &#x200B;](/help/journey-onboarding/assets/onboarding-journey.png).

Deze gids leidt u door de belangrijkste onboarding onderwerpen zodat wanneer u klaar bent het volgende heeft:

* Volledige kennis van de verschillende voorwaarden, services en gebruikers die bij het instapproces betrokken zijn.
* Uw team kon aan de slag en de eerste stappen nemen in de richting van het leren om inhoud voor uw AEM as a Cloud Service-toepassing te ontwerpen en te ontwikkelen.

Dientengevolge:

* Uw team is ingesteld en heeft toegang tot cloudbronnen.
* AEM-auteurs hebben toegang tot AEM as a Cloud Service en kunnen beginnen met het maken van inhoud.
* AEM-ontwikkelaars en -implementatiemanagers hebben toegang tot AEM as a Cloud Service en kunnen aangepaste toepassingen maken en implementeren.

## Concepten en doelstellingen {#concepts}

<!-- Although there may appear to be a lot to learn when getting started with AEM as a Cloud Service, conceptually there are only a few, logical pieces.-->

De instapreis voor AEM as a Cloud Service draait om de volgende kernelementen:

* **Contract** - herzie uw contract van Adobe om de belangrijkste details van het onboarding proces te begrijpen.
* **Experience Hub** - gebruik [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com/) als uw centraal ingangspunt voor de mogelijkheden van AEM. De Experience Hub past zich aan uw persoonlijke wensen en rechten aan, zodat u efficiënt kunt werken. Navigeer van hieruit naar:
   * **Admin Console** - beheer gebruikers en wijs rollen toe.
   * **Cloud Manager** - de programma&#39;s en de milieu&#39;s van de opstelling, toegang Git, en creeer pijpleidingen om douanecode te beheren en op te stellen.
   * **Plaatsen** - creeer, beheer, en lever digitale ervaringen. (Op licentie gebaseerde machtiging)
   * **Assets** - organiseer, bewaar, en verdeel uw digitale activa. (Op licentie gebaseerde machtiging)
   * **Forms** - creeer en beheer adaptieve en ontvankelijke vormen. (Op licentie gebaseerde machtiging)

Deze begrippen worden in detail uiteengezet in deze instapreis. Het doel is dat aan het eind van de reis, u het volgende kunt doen:

* Bied de benodigde toegang van de gebruiker tot AEM as a Cloud Service.
* Stel de eerste cloudbronnen voor uw project in.
* Weet hoe u uw eerste code kunt implementeren en uw eerste inhoud kunt ontwerpen.

In feite heb je de grond op de grond gelopen met je nieuwe AEM as a Cloud Service-project!

## Publiek {#audience}

De onboarding reis wordt geschreven specifiek voor de **systeembeheerder** van klanten die aan AEM as a Cloud Service en aan AEM in het algemeen nieuw zijn. De systeembeheerder is het individu dat Adobe eerst contacteert nadat uw contract van AEM as a Cloud Service wordt ondertekend. Meestal zijn ze de eerste die toegang krijgt tot en middelen instelt op AEM as a Cloud Service. Als u dit onderwerp leest, is het waarschijnlijk dat u de systeembeheerder bent.

De systeembeheerder beheert alle aspecten van de gebruikers AEMaaCS van hun organisatie, van toegang tot toestemmingen. Nochtans, moet de systeembeheerder met andere persona&#39;s in wisselwerking staan langs de weg.

| Persona | Beschrijving | Rol in reis |
| --- | --- | --- |
| Systeembeheerder | Het doel van deze reis voorziet in de initiële levering van cloudbronnen en de toewijzing van gebruikers aan de juiste rollen op basis van hun taakverantwoordelijkheden. | De rol helpt u alle aspecten van gebruikers van toegang tot toestemmingen beheren. |
| Inhoudsauteur | Maakt en bekijkt de inhoud in AEM. | Als de systeembeheerder machtigingen heeft verleend, kunnen auteurs hun eigen reis beginnen bij het maken van inhoud. |
| Developer | Ontwikkelt AEM-toepassingen die inhoud uit verschillende bronnen gebruiken. | Zodra verleend de toestemmingen door de systeembeheerder, kunnen de ontwikkelaars hun eigen reis in het ontwikkelen van oplossingen beginnen. |
| Implementatiebeheer | Voegt of werkt een milieu toe bij, stelt pijpleidingen in werking, en stelt code aan het milieu van AEM of code-kwaliteit op. | Zodra verleend de toestemmingen door de systeembeheerder, plaatsingsmanagers kunnen hun eigen reis beginnen die plaatsingen beheren. |

Deze instapkaartgids illustreert het volledige proces van instapweigering als systeembeheerder. De rollen van gebruikers, ontwikkelaars, en plaatsingsmanagers van AEM worden kort verkend als extra, facultatieve delen van de reis.

>[!TIP]
>
>Als u aan AEM as a Cloud Service en vertrouwd met AEM nieuw bent en van op-gebouw of Adobe Managed Services migreert, controleer de [&#x200B; Reis van de Migratie van AEM as a Cloud Service &#x200B;](/help/journey-migration/getting-started.md).

## Reisoverzicht aan boord {#overview}

De volgende artikelen beschrijven in detail de kernconcepten voor instapweigering en geven u grondkennis van AEM as a Cloud Service. Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom raadt Adobe u aan om, als u nog niet eerder aan het instappen bent, aan aan het begin te beginnen en opeenvolgend te vorderen.

| | Artikel | Beschrijving | Publiek |
| --- | --- | --- | --- |
| 0 | Onboarding Journaal | Dit document | Systeembeheerder |
| 1 | [&#x200B; on boarding Preparation &#x200B;](preparation.md) | Alvorens het aan boord gaan proces begint, zijn er een aantal of voorbereidende stappen die de systeembeheerder moet begrijpen alvorens in het systeem te registreren. | Systeembeheerder |
| 2 | [&#x200B; Terminologie van AEM as a Cloud Service &#x200B;](terminology.md) | Voordat u zich voor het eerst aanmeldt bij AEMaaCS, is het nuttig om enkele terminologie van het systeem en de basisstructuur te begrijpen. | Systeembeheerder |
| 3 | [&#x200B; Admin Console &#x200B;](admin-console.md) | Leer wat de Admin Console is, hoe u zich aanmeldt en hoe u uw profiel als systeembeheerder verifieert. | Systeembeheerder |
| 4 | [&#x200B; Toewijzend de Profielen van het Product van Cloud Manager &#x200B;](assign-profiles-cloud-manager.md) | Bekijk Cloud Manager-productprofielen en leer hoe u teamleden kunt toewijzen aan Cloud Manager-productprofielen. | Systeembeheerder |
| 5 | [&#x200B; Toegang Experience Hub &#x200B;](/help/experience-hub.md) | Gebruik Experience Hub, dat fungeert als één gepersonaliseerd toegangspunt voor het AEM-ecosysteem. | AEM-gebruikers |
| 6 | [&#x200B; Toegang Cloud Manager &#x200B;](cloud-manager.md) | Leer hoe u toegang krijgt tot Cloud Manager zodat u uw projectbronnen kunt instellen. | Systeembeheerder |
| 7 | [&#x200B; creeer een Programma &#x200B;](create-program.md) | Leer hoe u een programma maakt met Cloud Manager. | Systeembeheerder |
| 8 | [&#x200B; creeer milieu&#39;s &#x200B;](create-environments.md) | Leer hoe u een omgeving kunt maken met Cloud Manager. | Systeembeheerder |
| 9 | [&#x200B; Toewijzend de Profielen van het Product van AEM &#x200B;](assign-profiles-aem.md) | Leer hoe de systeembeheerder uw teamleden toewijst aan productprofielen in AEM as a Cloud Service. | Systeembeheerder |
| 10 | [&#x200B; Taken van de Manager van de Ontwikkelaar en van de Plaatsing &#x200B;](developers.md) | Optioneel - Leer als ontwikkelaar hoe u toegang krijgt tot Cloud Manager Git en hoe u deze beheert. Als Manager van de Plaatsing, leer hoe te opstellings pijpleidingen en opstellen code in Cloud Manager. | Ontwikkelaars en implementatiemanagers |
| 11 | [&#x200B; de Taken van de Gebruiker van AEM &#x200B;](aem-users.md) | Optioneel - Als AEM-auteur leert u hoe u toegang krijgt tot een AEM as a Cloud Service-exemplaar en hoe u vertrouwd bent met de ontwerpinhoud voor AEM as a Cloud Service. | AEM-gebruikers |

## Wat nu? {#what-is-next}

Je bent nu klaar om je AEM as a Cloud Service-instapreis te starten. U wordt aangemoedigd om aan het volgende deel van de reis verder te gaan en het artikel [&#x200B; te lezen Onboarding Preparation &#x200B;](preparation.md)

## AEM-documentatietrajecten {#documentation-journeys}

[&#x200B; de documentatietraject van A &#x200B;](/help/journey-documentation/documentation-journeys.md) verbindt vele verschillende, gecompliceerde onderwerpen en eigenschappen. Het verstrekt een verhaal dat een lezer nieuw aan AEM helpt een bedrijfsprobleem van begin tot eind begrijpen en oplossen, terwijl het veronderstellen van minimaal voorafgaand onderwerp of kennis van AEM.

Documentatiereizen zijn gebaseerd op de beginselen van best practices. Ze worden op de hoogte gesteld met behulp van het nieuwste onderzoek van Adobe, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

Als u wilt weten wat Adobe aanbeveelt om uw team aan te melden bij uw nieuwe AEM as a Cloud Service-toepassing, start u hier.

## Aanvullende bronnen {#additional-resources}

Hieronder volgen aanvullende, optionele bronnen als u verder wilt gaan dan de inhoud van de instapreis.

* [&#x200B; op instapniveau aan AEM as a Cloud Service &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/onboarding) - Deze korte video geeft een overzicht van Cloud Service op instapproces voor AEM.
