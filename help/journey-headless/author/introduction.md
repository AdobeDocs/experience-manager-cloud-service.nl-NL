---
title: Ontwerpen voor AEM als een headless CMS - Een inleiding
description: Een inleiding tot het gebruiken van de eigenschappen van Adobe Experience Manager as a Cloud Service als Zwaardeloze CMS om inhoud voor uw project te ontwerpen.
exl-id: 065b00cb-a82d-4bcb-b2c9-44542cee6303
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Ontwerpen voor AEM als een headless CMS - Een inleiding {#author-headless-introduction}

In dit deel van het [AEM Schrijverreis zonder kopinhoud](overview.md), kunt u de (basis)concepten en de terminologie leren noodzakelijk om auteursinhoud te begrijpen wanneer het gebruiken van Adobe Experience Manager (AEM) as a Cloud Service als Zwaardeloze CMS. Dit betekent dat u inhoud zonder kop moet structureren en maken.

{{headless-trials-promotion}}

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de concepten en de terminologie relevant voor Headless Authoring.

## Inhoudsbeheersysteem (CMS) {#content-management-system}

Wat is een inhoudsbeheersysteem?

Een inhoudsbeheersysteem (CMS) is precies wat het zegt: een computersysteem dat wordt gebruikt om inhoud te beheren. Dat is een beetje algemeen, dus om preciezer te zijn, wordt het (typisch) gebruikt voor het beheren van inhoud die u op uw website(s) ter beschikking wilt stellen.

## CMS zonder hoofd {#headless-cms}

Headless is een term die wordt gebruikt om systemen te beschrijven die de inhoud effectief losmaken van de manier waarop die inhoud op het web wordt weergegeven.

Doorgaans beheert u de inhoud in een CMS en dezelfde CMS is verantwoordelijk voor het weergeven van die inhoud op uw webpagina&#39;s.

Nu betekent headless dat uw inhoudset kan worden beheerd in het CMS en vervolgens kan worden geopend door een of meer (onafhankelijke) toepassingen.

Dit betekent dat uw inhoud op elk apparaat in een groot aantal indelingen kan worden geleverd. Hierdoor wordt het hele proces veel flexibeler en hoeft u zich geen zorgen te maken over de indeling en opmaak.

>[!NOTE]
>
>Als u meer wilt weten over de technische details van Headless CMS, kunt u meer lezen op Learn About CMS Headless Development.

## Adobe Experience Manager as a Cloud Service {#aem-cloud-service}

Dus wat is AEM?

In de eerste plaats is AEM een contentbeheersysteem met een groot aantal functies die ook aan uw vereisten kunnen worden aangepast.

Dit alles betekent dat het kan worden gebruikt als:

* CMS zonder hoofd
   * Voor headless, kan uw inhoud worden ontworpen zoals **Inhoudsfragmenten**.
Dit zijn zelfstandige inhoudselementen die rechtstreeks door een waaier van toepassingen kunnen worden betreden, aangezien zij een vooraf bepaalde structuur hebben, die op wordt gebaseerd **Modellen van inhoudsfragmenten**.
Dit betekent dat uw inhoud een groot aantal apparaten kan bereiken, in een groot aantal indelingen en met een grote verscheidenheid aan functies.
(Deze fragmenten kunnen desgewenst ook worden gebruikt bij het samenstellen van AEM webpagina&#39;s.)

* &quot;Traditioneel&quot; CMS
   * Inhoud wordt gemaakt voor webpagina&#39;s met behulp van een reeks componenten die definiëren hoe de inhoud op uw website wordt weergegeven. Zelfs hier is AEM uiterst flexibel aangezien uw projectteam aangepaste componenten kan ontwikkelen.

## Inhoud modelleren {#content-modeling}

Dus contentmodellering (ook wel data modellering genoemd) is een andere technische term - waarom zou het jou als auteur interesseren?

Voor toepassingen zonder titel hebt u een vooraf gedefinieerde structuur nodig om toegang te krijgen tot uw inhoud en er iets mee te kunnen doen. Het zou mogelijk zijn om uw inhoud als vrije vorm te hebben, maar het zou leven maken *zeer* ingewikkeld voor de toepassingen.

Het proces om de structuur voor uw inhoud te bepalen om aan te houden impliceert het ontwerpen van een model - en dit wordt genoemd gegevensmodellering.

Voor AEM de rol van Content Architect (vaak een andere persoon) zal de gegevensmodellering uitvoeren om een reeks van **Modellen van inhoudsfragmenten** - dat u dan als basis voor uw inhoud gebruikt door **Inhoudsfragmenten**.

>[!NOTE]
>
>Als u meer wilt weten over gegevensmodellering, kunt u meer lezen onder de AEM Headless Content Architect Journey.

## Volgende functies {#whats-next}

Nu u de concepten en de terminologie hebt geleerd, is de volgende stap: [Leer de grondbeginselen van het ontwerpen van inhoudsfragmenten](basics.md). Dit zal de basisbehandeling van AEM samen met hoe te om de Fragments van de Inhoud introduceren.

## Aanvullende bronnen {#additional-resources}

* [Inleiding tot AEM als een headless CMS](/help/headless/introduction.md)

* [Tutorials voor headless in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)

* AEM Headless Developer Journey
   * [Meer informatie over CMS Headless Development](/help/journey-headless/developer/learn-about.md)
   * [Leer hoe u uw inhoud kunt modelleren](/help/journey-headless/developer/model-your-content.md)

* [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)

* [Reis van architect zonder hoofdinhoud AEM](/help/journey-headless/architect/overview.md)

* [Reis voor omzetting van inhoud zonder kop AEM](/help/journey-headless/translation/overview.md)
