---
title: Alles bij elkaar plaatsen - uw app en uw inhoud in AEM headless
description: In dit deel van de AEM Headless Ontwikkelaarsreis, leer hoe te om uw AEMProject met inbegrip van Inhoudsfragmenten, uw vraag GraphQL, uw vraag REST API, en uw toepassing te nemen, en het voor te bereiden voor het leven.
hide: true
hidefromtoc: true
index: false
exl-id: 254fb9dd-36c8-43ce-aaea-ceb4d079503d
translation-type: tm+mt
source-git-commit: e8eb9d2c96d24601e50c48f6846a8c8bac8b0252
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# Hoe te om het allen samen te zetten - Uw app en uw inhoud in AEM Zwaartepunt {#put-it-all-together}

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Headless Developer Journey,](overview.md) leert hoe te om uw AEM Project met inbegrip van Inhoudsfragmenten, uw vraag GraphQL, uw vraag REST API, en uw toepassing te nemen, en het voor te bereiden voor het leven.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [How to Update Your Content via AEM Assets APIs](update-your-content.md) leerde u hoe te om uw bestaande inhoud zonder kop in AEM via API bij te werken en u zou nu moeten:

* Begrijp de AEM Assets HTTP API.

Dit artikel bouwt verder op die grondbeginselen zodat u begrijpt hoe u uw eigen AEM headless project kunt voorbereiden om te leven.

## Doel {#objective}

* Begrijp wat de lokale ontwikkelingswerkschema voor AEM is
* Installeer de SDK van de AEM voor een lokale ontwikkelruntime waarop u de inhoud kunt testen
* Meer informatie over de ontwikkeltools die u nodig hebt naast de lokale ontwikkelruntime

## De lokale ontwikkelingsworkflow {#the-local-development-workflow}

Het lokale ontwikkelingsproject is gebaseerd op Apache Maven en gebruikt Git voor broncontrole. Om het project bij te werken, kunnen de ontwikkelaars hun aangewezen geïntegreerde ontwikkelomgeving, zoals Eclipse, de Code van Visual Studio of IntelliJ, onder andere gebruiken.

Als u code- of inhoudsupdates wilt testen die door uw toepassing zonder kop worden opgenomen, moet u de updates implementeren in een lokale AEM-runtime, die lokale instanties van de AEM auteur bevat en instanties publiceert.

Let op het verschil tussen de verschillende componenten in de lokale AEM runtime, want het is belangrijk dat u de updates test op de plaatsen waar ze het belangrijkst zijn. Test bijvoorbeeld de inhoud van updates op auteur of test nieuwe code op de publicatie-instantie.

In een productiesysteem, zullen een verzender en een server http Apache altijd voor een AEM publicatiegeval zitten. Zij verlenen caching en de dienstdiensten voor het AEM systeem, zodat is het uiterst belangrijk om code en inhoudsupdates tegen de verzender eveneens te testen.

Zodra u ervoor hebt gezorgd dat alles is getest en correct werkt, kunt u uw code-updates naar een gecentraliseerde Git-opslagplaats in Cloud Manager verzenden.

Nadat de updates zijn geüpload naar Cloud Manager, kunnen ze worden geïmplementeerd als een Cloud Service met de CI/CD-pijplijn van Cloud Manager.


## De AEM-SDK {#the-aem-sdk}

De AEM SDK wordt gebruikt om aangepaste code te maken en in te voeren. Het bevat de volgende artefacten:

* De QuickStart-jar - een uitvoerbaar JAR-bestand dat kan worden gebruikt om een auteur- en een publicatie-instantie in te stellen
* De hulpmiddelen van de verzending - de module van de Dispatcher en zijn gebiedsdelen voor Vensters en op UNIX gebaseerde systemen
* Java API Jar - De Java Jar/Maven-afhankelijkheid die alle toegestane Java API&#39;s beschikbaar maakt die kunnen worden gebruikt om zich te ontwikkelen tegen AEM
* Javadoc jar - de javadocs voor de Java API jar

## Local Development Environment Setup {#local-development-environment}

Als u uw AEM project zonder kop wilt voorbereiden op de start, moet u ervoor zorgen dat alle onderdelen van uw project goed werken.

Om dat te doen, moet u alles samenvoegen - code, inhoud en configuratie en het testen in een lokale ontwikkelomgeving voor levende bereidheid.

De lokale ontwikkelomgeving bestaat uit drie hoofdgebieden:

1. Het AEM Project - dit zal alle douanecode, configuratie en inhoud bevatten de AEM ontwikkelaars zullen werken aan
1. Lokale AEM Runtime - lokale versies van de AEM auteur en publiceer de diensten die zullen worden gebruikt om code van het AEM project op te stellen
1. De lokale Dispatcher Runtime - een lokale versie van de Apache htttpd-webserver die de Dispatcher-module bevat

## Ontwikkelingsgereedschappen {#development-tools}

Naast de AEM SDK hebt u aanvullende gereedschappen nodig die het ontwikkelen en testen van uw code en inhoud lokaal vergemakkelijken:

* Java
* Git
* Apache Maven
* De Node.js-bibliotheek
* De IDE van uw keuze

Omdat AEM een Java-toepassing is, moet u Java en de Java SDK installeren om de ontwikkeling van AEM als Cloud Service te ondersteunen.

Git is het hulpmiddel u zult gebruiken om broncontrole te beheren evenals de veranderingen in de Manager van de Wolk te controleren en dan hen op een productie-instantie op te stellen.

AEM gebruikt Apache Maven om projecten te bouwen die uit AEM Maven Project archetype worden geproduceerd. Alle belangrijke IDEs verstrekt integratiesteun voor Maven.

Node.js is een runtimeomgeving JavaScript die wordt gebruikt om met de front-end activa van het subproject ui.frontend van een AEM project te werken. Node.js wordt gedistribueerd met npm, is de facto het pakketbeheer Node.js, dat wordt gebruikt om JavaScript gebiedsdelen te beheren.

## Volgende {#what-is-next}

U zou uw AEM onophoudelijke reis moeten voortzetten door het document [te herzien hoe te met Uw Zwaarloze Toepassing ](go-live.md) gaan waar u werkelijk uw AEM Zwaardeloos project neemt levend!

## Aanvullende bronnen {#additional-resources}

* [De lokale Opstelling](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-dispatcher-runtime)  van het Milieu van de Ontwikkeling leren hoe te om toolt te installeren nodig beginnen zich voor AEM te ontwikkelen
* [AEM als Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)  - bekijk de AEM SDK diepgaand