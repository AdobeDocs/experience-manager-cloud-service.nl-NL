---
title: Alles bij elkaar plaatsen - uw app en uw inhoud in AEM headless
description: In dit deel van de AEM Headless Developer Journey leert u hoe u uw AEM Project met inbegrip van Inhoudsfragmenten, uw GraphQL-aanroepen, uw REST API-aanroepen en uw toepassing kunt uitvoeren en voorbereiden op live gaan.
exl-id: bece84ad-4c8c-410c-847e-9ef3f79970cb
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# Alles bij elkaar plaatsen - uw app en uw inhoud in AEM headless {#put-it-all-together}

In dit deel van de [ AEM Headless Reis van de Ontwikkelaar ](overview.md), wordt u vertrouwd met leren hoe te om het AEM ontwikkelingshulpmiddel en Headless SDK te gebruiken om uw toepassing samen te zetten.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [ hoe te om Uw Inhoud via AEM Assets APIs bij te werken ](update-your-content.md) leerde u hoe te om uw bestaande inhoud zonder kop in AEM via API bij te werken en u zou nu moeten:

* Begrijp de AEM Assets HTTP API.

## Doelstelling {#objective}

Dit artikel is bedoeld om u te helpen begrijpen hoe u uw AEM toepassing zonder kop kunt samenvoegen door:

* Leren over de AEM Headless SDK en de vereiste ontwikkelingshulpmiddelen
* Een lokale ontwikkelings-runtime instellen om uw inhoud te simuleren voordat u live gaat
* Grondbeginselen van AEM inhoudsreplicatie

## De AEM SDK {#the-aem-sdk}

De AEM SDK wordt gebruikt om aangepaste code te maken en in te voeren. Het is het belangrijkste hulpmiddel dat u nodig hebt, zodat u uw toepassing zonder kop kunt ontwikkelen en testen voordat u live gaat. Het bevat de volgende artefacten:

* De QuickStart-jar - een uitvoerbaar JAR-bestand dat kan worden gebruikt om een auteur- en een publicatie-instantie in te stellen
* Dispatcher tools - de Dispatcher module en zijn afhankelijkheden voor Windows- en UNIX®-systemen
* Java™ API Jar - De Java™ Jar/Maven Dependency die alle toegestane Java™ APIs blootstelt die kunnen worden gebruikt om tegen AEM te ontwikkelen
* Javadoc jar - de javadocs voor de Java™ API jar

## De AEM Headless SDK {#the-aem-headless-sdk}

Verschil van de AEM SDK, AEM **Koploze SDK** wordt geplaatst van bibliotheken die door cliënten kunnen worden gebruikt om met AEM Koploze APIs over HTTP snel en gemakkelijk in wisselwerking te staan.

Voor meer informatie zie [ AEM Koploze SDK ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=nl-NL).

## Aanvullende ontwikkelingsinstrumenten {#additional-development-tools}

Naast de AEM SDK hebt u aanvullende gereedschappen nodig die het ontwikkelen en testen van uw code en inhoud lokaal mogelijk maken:

* Java™
* Git
* Apache Maven
* De Node.js-bibliotheek
* De IDE van uw keuze

Omdat AEM een Java™-toepassing is, moet u Java™ en de Java™ SDK installeren om de ontwikkeling van AEM as a Cloud Service te ondersteunen.

Git is wat u gebruikt om broncontrole te beheren en in de veranderingen in Cloud Manager te controleren en dan hen op te stellen aan een productie-instantie.

AEM gebruikt Apache Maven om projecten te bouwen die uit het AEM Maven Project archetype worden geproduceerd. Alle belangrijke IDEs verstrekt integratiesteun voor Maven.

Node.js is een runtimeomgeving van JavaScript die wordt gebruikt voor het werken met de front-end elementen van het `ui.frontend` subproject van een AEM project. Node.js wordt gedistribueerd met npm, is de facto Manager van het Pakket Node.js, die wordt gebruikt om de gebiedsdelen van JavaScript te beheren.

## Componenten van een AEM systeem in één oogopslag {#components-of-an-aem-system-at-a-glance}

Laten we nu eens kijken naar de onderdelen van een AEM omgeving.

Een volledige AEM omgeving bestaat uit een auteur, Publish en Dispatcher. Deze componenten worden ook beschikbaar gesteld in de lokale ontwikkelruntime, zodat u gemakkelijker een voorvertoning van uw code en inhoud kunt weergeven voordat u live gaat.

* **de dienst van de Auteur** is waar de interne gebruikers, inhoud creëren leiden en voorproef.

* **de dienst van Publish** wordt beschouwd als het &quot;Levende&quot;milieu en is typisch wat eind - gebruikers met in wisselwerking staan. Inhoud wordt na bewerking en goedkeuring op de service Auteur gedistribueerd naar de Publish-service. Het meest gangbare implementatiepatroon met AEM toepassingen zonder kop is dat de productieversie van de toepassing verbinding maakt met een AEM Publish-service.

* **Dispatcher** is een statische Webserver die met de module van Dispatcher van de AEM wordt uitgebreid. Webpagina&#39;s die door de instantie publish worden gemaakt, worden in het cachegeheugen opgeslagen om de prestaties te verbeteren.

## De workflow voor lokale ontwikkeling {#the-local-development-workflow}

Het lokale ontwikkelingsproject is gebaseerd op Apache Maven en gebruikt Git voor broncontrole. Om het project bij te werken, kunnen de ontwikkelaars hun aangewezen geïntegreerde ontwikkelomgeving, zoals Verduistering, de Code van Visual Studio, of IntelliJ, onder anderen gebruiken.

Als u code- of inhoudsupdates wilt testen die door uw toepassing zonder kop worden opgenomen, moet u de updates implementeren naar de lokale AEM runtime, die lokale instanties van de AEM auteur en publicatieservices bevat.

Let op het verschil tussen de verschillende componenten in de lokale AEM runtime, want het is belangrijk dat u de updates test op de plaatsen waar ze het belangrijkst zijn. Test bijvoorbeeld de inhoud van updates op de auteur of test nieuwe code op de publicatie-instantie.

In een productiesysteem zullen een Dispatcher en een http Apache-server altijd voor een AEM publicatie-instantie zitten. Zij verlenen caching en de veiligheidsdiensten voor het AEM systeem, zodat is het uiterst belangrijk om code en inhoudsupdates tegen Dispatcher eveneens te testen.

## Een lokale voorvertoning van uw code en inhoud weergeven in de lokale ontwikkelomgeving {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Als u uw AEM project zonder kop wilt voorbereiden op de start, moet u ervoor zorgen dat alle onderdelen van uw project goed werken.

Om dat te doen, moet u alles samenvoegen: code, inhoud, en configuratie en het testen in een lokale ontwikkelomgeving voor levende bereidheid.

De lokale ontwikkelomgeving bestaat uit drie hoofdgebieden:

1. Het AEM Project - dit project bevat alle douanecode, configuratie, en inhoud de AEM ontwikkelaars zullen werken aan
1. Lokale AEM Runtime - lokale versies van de AEM auteur en publiceer de diensten die worden gebruikt om code van het AEM project op te stellen
1. De lokale Dispatcher Runtime - een lokale versie van de Apache htttpd-webserver die de Dispatcher-module bevat

Nadat de lokale ontwikkelomgeving is ingesteld, kunt u inhoud die in de React-app wordt gebruikt, simuleren door een statische Node-server lokaal te implementeren.

<!-- THIS TOPIC IS 404. IT DOES NOT APPEAR IN THE TOC OR ANYWHERE ELSE To get a more in-depth look at setting up a local development environment and all dependencies needed for content preview, see [Production Deployment documentation](https://experienceleague.adobe.com/docs/experience-manager-learn/headless-tutorial/graphql/multi-step/production-deployment.html). -->

## Volgende functies {#whats-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Kennis hebben van de AEM-ontwikkelingsinstrumenten
* De lokale ontwikkelingsworkflow begrijpen

Ga uw AEM headless reis door het document [ te herzien hoe te met Uw Zwaarloze Toepassing ](/help/journey-headless/developer/go-live.md) gaan waar u eigenlijk uw AEM Zwaardeloos project neemt levend!

## Aanvullende bronnen {#additional-resources}

* [De SDK van AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [ opstelling een Lokale AEM milieu ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=nl-NL)
* [ AEM Koploze SDK voor cliënt-zijbrowsers (JavaScript) ](https://github.com/adobe/aem-headless-client-js)
* [ AEM Headless SDK voor server-side/Node.js (JavaScript) ](https://github.com/adobe/aem-headless-client-nodejs)
* [ AEM Headless SDK voor Java™ ](https://github.com/adobe/aem-headless-client-java)
* [Inleiding tot AEM als een CMS zonder kop](/help/headless/introduction.md)
* [ AEM het Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
* [ Tutorials voor Zwaartepunt in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL)
