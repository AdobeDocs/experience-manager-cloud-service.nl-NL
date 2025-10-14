---
title: Ontwerpen voor AEM als een CMS zonder koppen - Een inleiding
description: Een inleiding tot het gebruik van de functies van Adobe Experience Manager as a Cloud Service als een Headless CMS voor het schrijven van inhoud voor uw project.
exl-id: 065b00cb-a82d-4bcb-b2c9-44542cee6303
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: cc2e73da123d3e0676a8e175a18c1dc0bdff1daa
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Ontwerpen voor AEM als een CMS zonder koppen - Een inleiding {#author-headless-introduction}

In dit deel van de [&#x200B; Hoofdloze Reis van de Auteur van de Inhoud van AEM &#x200B;](overview.md), kunt u de (basis) concepten en de terminologie noodzakelijk leren om auteursinhoud te begrijpen wanneer het gebruiken van Adobe Experience Manager (AEM) as a Cloud Service als Headless CMS. Dit betekent dat u inhoud zonder kop moet structureren en maken.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de concepten en de terminologie relevant voor Schrijven zonder hoofd.

## Inhoudsbeheersysteem (CMS) {#content-management-system}

Wat is een inhoudsbeheersysteem?

Een inhoudsbeheersysteem (CMS) is precies wat het zegt: een computersysteem dat wordt gebruikt om inhoud te beheren. Dat is een beetje algemeen, dus om preciezer te zijn, wordt het (typisch) gebruikt voor het beheren van inhoud die u op uw website(s) ter beschikking wilt stellen.

## Headless CMS {#headless-cms}

Headless is een term die wordt gebruikt om systemen te beschrijven die de inhoud effectief losmaken van de manier waarop die inhoud op het web wordt weergegeven.

Traditioneel beheert u de inhoud in een CMS en dezelfde CMS is verantwoordelijk voor het weergeven van die inhoud op uw webpagina&#39;s.

Nu betekent headless dat uw inhoudset kan worden beheerd in de CMS en vervolgens kan worden geopend door een of meer (onafhankelijke) toepassingen.

Dit betekent dat uw inhoud op elk apparaat in een groot aantal indelingen kan worden geleverd. Hierdoor wordt het hele proces veel flexibeler en hoeft u zich geen zorgen te maken over de indeling en opmaak.

>[!NOTE]
>
>Als je meer wilt weten over de technische details van Headless CMS, kun je meer lezen op Learn About CMS Headless Development.

## Adobe Experience Manager as a Cloud Service {#aem-cloud-service}

Wat is AEM?

AEM is in de eerste plaats een contentbeheersysteem met een groot aantal functies die ook aan uw wensen kunnen worden aangepast.

Dit alles betekent dat het kan worden gebruikt als:

* Headless CMS
   * Voor headless, kan uw inhoud als **Fragments van de Inhoud** worden authored.
Dit zijn met alle accomodatie punten van inhoud die rechtstreeks door een waaier van toepassingen kunnen worden betreden, aangezien zij een vooraf bepaalde structuur hebben, die op **Modellen van het Fragment van de Inhoud** wordt gebaseerd.
Dit betekent dat uw inhoud een groot aantal apparaten kan bereiken, in een groot aantal indelingen en met een grote verscheidenheid aan functies.
(En deze fragmenten kunnen desgewenst ook worden gebruikt bij het samenstellen van AEM-webpagina&#39;s.)

* &quot;Traditioneel&quot; CMS
   * Inhoud wordt gemaakt voor webpagina&#39;s met behulp van een reeks componenten die definiëren hoe de inhoud op uw website wordt weergegeven. Zelfs hier is AEM uiterst flexibel omdat uw projectteam aangepaste componenten kan ontwikkelen.

## Inhoud modelleren {#content-modeling}

Dus contentmodellering (ook wel data modellering genoemd) is een andere technische term - waarom zou het jou als auteur interesseren?

Voor toepassingen zonder titel hebt u een vooraf gedefinieerde structuur nodig om toegang te krijgen tot uw inhoud en er iets mee te kunnen doen. Het zou mogelijk zijn om uw inhoud als vrij-vorm te hebben, maar het zou het leven *zeer* gecompliceerd voor de toepassingen maken.

Het proces om de structuur voor uw inhoud te bepalen om aan te houden impliceert het ontwerpen van een model - en dit wordt genoemd gegevensmodellering.

Voor AEM zal de rol van de Architect van de Inhoud (vaak een verschillende persoon) de gegevens modelleren om een waaier van **Modellen van het Fragment van de Inhoud te ontwerpen** - dat u dan als basis voor uw inhoud gebruikt door **de Fragmenten van de Inhoud** te gebruiken.

>[!NOTE]
>
>Als u meer wilt weten over gegevensmodellering, kunt u meer lezen onder de AEM Headless Content Architect Journey.

## Volgende functies {#whats-next}

Nu u de concepten en de terminologie hebt geleerd, moet de volgende stap [&#x200B; de grondbeginselen van het schrijven van de Fragmenten van de Inhoud &#x200B;](basics.md) leren. Dit zal de basisbehandeling van AEM samen met hoe te om de Fragments van de Inhoud introduceren.

## Aanvullende bronnen {#additional-resources}

* [Inleiding tot AEM als een CMS zonder kop](/help/headless/introduction.md)

* [&#x200B; Leerprogramma&#39;s voor Zwaartepunt in AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL)

* AEM Headless Developer Journey
   * [Meer informatie over CMS Headless Development](/help/journey-headless/developer/learn-about.md)
   * [Leer hoe u uw inhoud kunt modelleren](/help/journey-headless/developer/model-your-content.md)

* [&#x200B; AEM Developer Portal &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)

* [AEM Headless Content Architect Reis](/help/journey-headless/architect/overview.md)

* [AEM Headless Content Translation Reis](/help/journey-headless/translation/overview.md)
