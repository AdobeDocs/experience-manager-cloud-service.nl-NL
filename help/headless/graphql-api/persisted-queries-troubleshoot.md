---
title: Problemen met blijvende GraphQL-query's oplossen
description: Leer hoe u problemen met aanhoudende GraphQL-query's in Adobe Experience Manager as a Cloud Service kunt oplossen.
feature: Headless, Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Aanhoudende GraphQL-query&#39;s oplossen {#troubleshoot-persisted-graphql-queries}

Het [ Centrum van Acties ](/help/operations/actions-center.md) omvat **GraphQL voortgeduurde vraagfout** alarm. Dit betekent dat je op de hoogte wordt gesteld wanneer een van je GraphQL-query&#39;s blijft bestaan en er een fout optreedt.

Om u te helpen dergelijke problemen problemen problemen oplossen en oplossen, behandelt deze pagina de *gemeenschappelijkste* oorzaken van mislukkingen, en stappen op hoe te om hen te bevestigen.

## Wijzigingen in het model Inhoudsfragment {#changes-to-content-fragment-model}

Een GraphQL-query die blijft bestaan, kan mislukken wanneer deze is gebaseerd op GraphQL-typen die verouderd zijn, vaak als gevolg van een wijziging in de onderliggende modellen van Content Fragment.

Dergelijke fouten kunnen om diverse redenen voorkomen. Voorbeelden zijn (de lijst is niet uitputtend) wanneer de auteur van een Content Fragment-model:

* Hiermee verwijdert u een veld of wijzigt u de naam van het veld
* werkt het **ModelType** bij dat de modellen voor de fragmentverwijzing worden toegestaan
* publiceert een model waarnaar door andere modellen wordt verwezen, niet

Als u dergelijke fouten wilt verhelpen, moet u:

* Werk de voortgezette vraag bij die niet de veranderingen aanpast die aan het Model van het Fragment van de Inhoud worden aangebracht
* de wijziging herstellen van het model dat het probleem heeft veroorzaakt

## GraphQL-eindpunt niet geconfigureerd {#graphql-endpoint-not-configured}

Wanneer voortgeduurde vragen de `404` foutencode, samen met de informatie `No suitable endpoint found` terugkeren, betekent dit dat geen eindpunt van GraphQL op het AEM milieu wordt gevormd.

Om dit te verbeteren, volg de stappen voor het toelaten en het publiceren van uw eindpunt van [ GraphQL eindpunten in AEM ](/help/headless/graphql-api/graphql-endpoint.md) leiden.

## Ontbrekend pad in de GraphQL-URL voor doorlopende query {#missing-path-query-url}

Als voortgezette query&#39;s de `400` foutcode retourneren met de informatie `Suffix: '/' does not contain a path` , wordt de GraphQL servlet aangeroepen zonder een padachtervoegsel.

Het patroon moet `/graphql/execute.json/thePath` zijn.

## Geblokkeerd vanwege IP-lijst van gewenste personen {#blocked-due-to-ip-allow-list}

In een dergelijk geval retourneert de query de foutcode `405` .

Een dergelijke fout is niet specifiek voor GraphQL. Zie KB artikel [ 405 Fout niet toegestaan ](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-20824).

## Geblokkeerd door verzender {#blocked-dispatcher}

Als het eindpunt van GraphQL `404` fout bij het publiceren voor `POST` verzoeken terugkeert, betekent het dat de vragen van GraphQL op het niveau van de verzender worden geblokkeerd en het eindpunt moet manueel worden toegelaten.

Dit zou niet het geval door gebrek moeten zijn, maar een configuratie van de douanevervanger zou deze kwestie kunnen veroorzaken. Zie meer onder [ Dispatcher - de configuratie van het Eindpunt met AEM Zwaartepunt ](/help/headless/deployment/dispatcher.md).
