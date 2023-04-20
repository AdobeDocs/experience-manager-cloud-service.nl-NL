---
title: Authoring van concepten
description: Concepten van ontwerpen in AEM
exl-id: ee9e4952-e075-4398-b31f-d7886153efff
source-git-commit: b407765438086bb2f7fb720fb7f1dd05699cb48f
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---

# Authoring van concepten {#authoring-concepts}

Een AEM installatie bestaat meestal uit minstens twee omgevingen:

* Auteur
* Publicatie

Met deze interacties kunt u inhoud op uw website beschikbaar maken zodat uw bezoekers deze kunnen openen.

De auteursomgeving verstrekt de mechanismen om, deze inhoud tot stand te brengen bij te werken en te herzien alvorens het daadwerkelijk te publiceren:

* Een auteur maakt de inhoud en bekijkt deze. Inhoud kan van verschillende typen zijn, zoals pagina&#39;s, middelen, publicaties, enz.
* Deze inhoud wordt op een gegeven moment gepubliceerd op uw website.

![Diagram van auteur, uitgever, en verzenders](/help/sites-cloud/authoring/assets/author-publish.png)

In de auteursomgeving wordt de functionaliteit van AEM beschikbaar gesteld door AEM auteursinterface. Voor het publicatiemilieu ontwerpt u de volledige blik-en-gevoel van de interface die aan uw gebruikers ter beschikking wordt gesteld.

## Auteursomgeving {#author-environment}

De auteur werkt in wat bekend staat als de **auteursomgeving**. Dit verstrekt een makkelijk te gebruiken interface (grafische gebruikersinterface (GUI of UI)) voor het creëren van de inhoud. De auteur moet zich aanmelden met een account waaraan de juiste toegangsrechten zijn toegewezen.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten nodig om inhoud te maken, bewerken of publiceren.

Afhankelijk van hoe uw instantie en uw persoonlijke toegangsrechten worden gevormd kunt u vele taken op uw inhoud, met inbegrip van (onder andere) uitvoeren:

* Nieuwe inhoud genereren of bestaande inhoud op een pagina bewerken
* Vooraf gedefinieerde sjablonen gebruiken om nieuwe inhoudspagina&#39;s te maken
* Uw elementen en verzamelingen maken, bewerken en beheren
* Inhoud, elementen, enzovoort verplaatsen, kopiëren en verwijderen.
* Pagina&#39;s, elementen, enz. publiceren (of niet publiceren)

Daarnaast zijn er beheertaken die u helpen uw inhoud te beheren:

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

Zie het document voor meer informatie over het publiceren en ongedaan maken van de publicatie van pagina&#39;s [Pagina&#39;s publiceren.](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)

## Dispatcher {#dispatcher}

Om de prestaties voor bezoekers van uw website te optimaliseren, **[verzender](/help/implementing/dispatcher/overview.md)** implementeert taakverdeling en caching.
