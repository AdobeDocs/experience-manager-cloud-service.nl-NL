---
title: Problemen met blijvende GraphQL-query's oplossen
description: Leer hoe u problemen met aanhoudende GraphQL-query's in Adobe Experience Manager as a Cloud Service kunt oplossen.
feature: Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
source-git-commit: 220e86f18e4a61304764753d8daecb68503e9fd0
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Aanhoudende GraphQL-query&#39;s oplossen {#troubleshoot-persisted-graphql-queries}

De [Handelingencentrum](/help/operations/actions-center.md) bevat de **GraphQL-query-fout opgetreden** waarschuwing. Dit betekent dat je op de hoogte wordt gesteld wanneer een van je GraphQL-query&#39;s blijft bestaan en er een fout optreedt.

Om u te helpen dergelijke problemen problemen oplossen en oplossen, verklaren wij *meest voorkomende* oorzaken van mislukkingen, en stappen op hoe te om hen te bevestigen.

## Wijzigingen in het model Inhoudsfragment {#changes-to-content-fragment-model}

Een GraphQL-query die blijft bestaan, kan mislukken wanneer deze is gebaseerd op GraphQL-typen die verouderd zijn, vaak als gevolg van een wijziging in de onderliggende modellen van Content Fragment.

Dit kan om verschillende redenen gebeuren. Bijvoorbeeld wanneer de auteur van een inhoudsmodel:

* Hiermee verwijdert u een veld of wijzigt u de naam van het veld
* Hiermee worden de toegestane modellen bijgewerkt die zijn gedefinieerd voor een fragmentverwijzing
* publiceert een model waarnaar door andere modellen wordt verwezen, ongedaan
* andere acties en redenen

Om dit aan te pakken, kunt u:

* De voortgezette vraag die ontbreekt zou moeten worden bijgewerkt om de verandering op het model van het Fragment van de Inhoud aan te passen
* of de wijziging van het model dat het probleem heeft veroorzaakt moet worden teruggedraaid

## GraphQL-eindpunt niet geconfigureerd {#graphql-endpoint-not-configured}

Wanneer voortgeduurde vragen terugkeren `404` foutcode, samen met de informatie `No suitable endpoint found`, betekent dit dat geen eindpunt van GraphQL op het AEM milieu wordt gevormd.

Om dit te verbeteren, volg de stappen voor het toelaten van en het publiceren van uw eindpunt van [GraphQL-eindpunten beheren in AEM](/help/headless/graphql-api/graphql-endpoint.md).

## Ontbrekend pad in de GraphQL-URL voor doorlopende query {#missing-path-query-url}

Als voortgeduurde vragen terugkeren `400` foutcode met de informatie `Suffix: '/' does not contain a path`, wordt het GraphQL servlet geroepen zonder een wegachtervoegsel.

Het patroon moet `/graphql/execute.json/thePath`.

## Geblokkeerd vanwege IP-lijst van gewenste personen {#blocked-due-to-ip-allow-list}

In een dergelijk geval retourneert de query de `405` foutcode.

Dit is niet specifiek voor GraphQL. Zie het KB-artikel [405 Fout niet toegestaan](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-20824.html).

## Geblokkeerd door verzender {#blocked-dispatcher}

Als het GraphQL-eindpunt het `404` fout bij publiceren voor `POST` verzoeken, betekent het de vragen van GraphQL op het niveau van de verzender worden geblokkeerd en het eindpunt moet manueel worden toegelaten.

Dit zou niet het geval door gebrek moeten zijn, maar een configuratie van de douanevervanger zou deze kwestie kunnen veroorzaken. Meer onder bekijken [Dispatcher - Eindpuntconfiguratie met AEM headless](/help/headless/deployment/dispatcher.md).
