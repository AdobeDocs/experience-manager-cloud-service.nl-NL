---
title: Concepten ontwerpen en publiceren
description: Leer de concepten ontwerpen in AEM, gebruikend de auteur, voorproef, en publicatiemilieu's.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# Concepten ontwerpen en publiceren {#authoring-publishing}

Een AEM as a Cloud Service-installatie kan voor een auteur van inhoud worden beschouwd als drie primaire lagen op het meest elementaire niveau

* Auteurslijst
* Voorvertoning van rij
* Publish-niveau

Deze lagen hebben invloed op de manier waarop u inhoud op uw website kunt plaatsen, zodat uw bezoekers er toegang toe hebben. De basisworkflow is:

1. Inhoudsauteurs maken hun inhoud met behulp van de auteurslaag.
1. Inhoudsauteurs stellen hun inhoud beschikbaar voor revisoren om een voorvertoning weer te geven met behulp van de voorvertoningslaag.
1. Wanneer de inhoud gereed is voor openbare consumptie, publiceren auteurs de inhoud met de publicatielijst.

Inhoud kan van verschillende typen zijn, zoals pagina&#39;s, elementen en publicaties. Voorvertoningen van inhoud kunnen naar goeddunken van de auteur worden overgeslagen.

![ Diagram van auteur, uitgever, en verzenders ](assets/author-publish.jpg)

Voor verdere details over de technische architectuur van AEM as a Cloud Service, gelieve te zien het document [ Een Inleiding aan de Architectuur van Adobe Experience Manager as a Cloud Service ](/help/overview/architecture.md).

{{edge-delivery-authoring}}

## Inhoud ontwerpen {#author-environment}

De auteursomgeving van de auteursrij verstrekt een makkelijk te gebruiken grafische gebruikersinterface voor het creëren van inhoud. De auteur moet zich aanmelden met een account waaraan de juiste toegangsrechten zijn toegewezen.

Afhankelijk van hoe uw instantie en uw persoonlijke toegangsrechten worden gevormd kunt u vele taken op uw inhoud, met inbegrip van (onder anderen) uitvoeren:

* Nieuwe inhoud genereren of bestaande inhoud op een pagina bewerken
* Vooraf gedefinieerde sjablonen gebruiken om inhoudspagina&#39;s te maken
* Uw elementen en verzamelingen maken, bewerken en beheren
* Inhoud, pagina&#39;s en elementen verplaatsen, kopiëren en verwijderen.
* Pagina&#39;s en elementen publiceren (of verwijderen).

Bovendien zijn er beheertaken die u helpen uw inhoud te beheren:

* Workflows die bepalen hoe wijzigingen worden beheerd, zoals het afdwingen van een revisie vóór publicatie
* Projecten die individuele taken coördineren

AEM wordt ook vanuit de auteursomgeving beheerd.

Gelieve te zien de document [ Snelle Gids van het Begin aan Authoring ](/help/sites-cloud/authoring/quick-start.md) voor een overzicht van het auteursproces.

## Inhoud voorvertonen {#previewing-content}

AEM biedt ook een voorbeeldservice waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en deze openbaar beschikbaar is.

Gelieve te zien het document [ Previewing Inhoud ](/help/sites-cloud/authoring/sites-console/previewing-content.md) voor verdere details.

## Publish-omgeving {#publish-environment}

Als de inhoud van uw site gereed is, wordt deze gepubliceerd naar de publicatieomgeving van de publicatielaag. Hier worden de pagina&#39;s van de website beschikbaar gesteld aan het beoogde publiek in overeenstemming met de vormgeving van uw inhoudssjabloon.

Gelieve te zien het document [ Publiceren Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) voor meer informatie over het publiceren en het unpublishing van pagina&#39;s.

## Dispatcher {#dispatcher}

Om prestaties voor bezoekers aan uw website te optimaliseren, voert **[Dispatcher](/help/implementing/dispatcher/overview.md)** lading het in evenwicht brengen en het in cache plaatsen voor zowel uit publiceren als voorproeflijsten.
