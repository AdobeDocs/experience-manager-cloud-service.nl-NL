---
title: Concepten ontwerpen
description: Leer de concepten ontwerpen in AEM, gebruikend de auteur, voorproef en publicatiemilieu's.
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# Concepten ontwerpen {#authoring-concepts}

Een AEM installatie bestaat meestal uit minstens twee omgevingen:

* Auteur
* Publiceren

Deze omgevingen hebben invloed op het beschikbaar stellen van inhoud op uw website, zodat uw bezoekers er toegang toe hebben.

De auteursomgeving verstrekt de mechanismen om, deze inhoud tot stand te brengen bij te werken en te herzien alvorens het daadwerkelijk te publiceren:

* Een auteur maakt de inhoud en bekijkt deze. Inhoud kan van verschillende typen zijn, zoals pagina&#39;s, elementen en publicaties.
* Deze inhoud wordt op een gegeven moment gepubliceerd op uw website.

![Diagram van auteur, uitgever, en verzenders](/help/sites-cloud/authoring/assets/author-publish.png)

In de auteursomgeving, wordt de functionaliteit van AEM ter beschikking gesteld door AEM auteursgebruikersinterface. Voor het publicatiemilieu, ontwerpt u het volledige blik-en-gevoel van de interface die aan uw gebruikers ter beschikking wordt gesteld.

{{edge-delivery-authoring}}

## Auteursomgeving {#author-environment}

De auteur werkt in wat als **auteursomgeving**. Deze omgeving biedt een gebruiksvriendelijke interface (GUI of UI) voor het maken van de inhoud. De auteur moet zich aanmelden met een account waaraan de juiste toegangsrechten zijn toegewezen.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten nodig om inhoud te maken, bewerken of publiceren.

Afhankelijk van hoe uw instantie en uw persoonlijke toegangsrechten worden gevormd kunt u vele taken op uw inhoud, met inbegrip van (onder anderen) uitvoeren:

* Nieuwe inhoud genereren of bestaande inhoud op een pagina bewerken
* Vooraf gedefinieerde sjablonen gebruiken om inhoudspagina&#39;s te maken
* Uw elementen en verzamelingen maken, bewerken en beheren
* Inhoud, pagina&#39;s en elementen verplaatsen, kopiëren en verwijderen.
* Pagina&#39;s en elementen publiceren (of verwijderen).

Bovendien zijn er beheertaken die u helpen uw inhoud te beheren:

* Workflows die bepalen hoe wijzigingen worden beheerd, zoals het afdwingen van een revisie vóór publicatie
* Projecten die individuele taken coördineren

>[!NOTE]
>
>AEM wordt ook vanuit de auteursomgeving beheerd.

## Inhoud voorvertonen {#previewing-content}

AEM biedt ook een Sites Preview-service waarmee ontwikkelaars en makers van inhoud de uiteindelijke ervaring van een website kunnen voorvertonen voordat deze de publicatieomgeving bereikt en openbaar beschikbaar is.

Zie [Inhoud voorvertonen](/help/sites-cloud/authoring/fundamentals/previewing-content.md) voor nadere bijzonderheden.

## Publicatie-omgeving {#publish-environment}

Als de inhoud van uw site gereed is, wordt deze gepubliceerd naar de **publicatieomgeving**. Hier worden de pagina&#39;s van de website beschikbaar gemaakt voor het beoogde publiek, in overeenstemming met de vormgeving van de ontworpen interface.

Zie het document voor meer informatie over het publiceren en ongedaan maken van de publicatie van pagina&#39;s [Pagina&#39;s publiceren](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

## Dispatcher {#dispatcher}

Om de prestaties voor bezoekers van uw website te optimaliseren, **[Dispatcher](/help/implementing/dispatcher/overview.md)** implementeert taakverdeling en caching.
