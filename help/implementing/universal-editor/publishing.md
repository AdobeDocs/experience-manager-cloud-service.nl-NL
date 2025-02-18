---
title: Hoe de Universal Editor inhoud publiceert
description: Leer hoe de Universal Editor de inhoud publiceert, hoe deze verschilt van het proces in de Sites Console en hoe u uw eigen apps ontwikkelt om ermee te werken.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0ee6689460ac0ecc5c025fb6a940d69a16699c85
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Hoe de Universal Editor inhoud publiceert {#publishing}

Leer hoe de Universal Editor de inhoud publiceert, hoe deze verschilt van het proces in de Sites Console en hoe u uw eigen apps ontwikkelt om ermee te werken.

>[!TIP]
>
>In dit artikel worden de details besproken van het publicatieproces van de Universal Editor voor de ontwikkelaar. Voor de inhoudauteur, [ wordt het proces om uw inhoud te publiceren hier beschreven.](/help/sites-cloud/authoring/universal-editor/publishing.md)

## Vergelijkbaar met het Sites Console-proces {#similarities}

Voor gebruikers van de [ Redacteur van de Pagina van AEM ](/help/sites-cloud/authoring/page-editor/introduction.md) en [ Console van Plaatsen, ](/help/sites-cloud/authoring/sites-console/introduction.md) het proces om inhoud met de Universele Redacteur te publiceren werkt aangezien u gewend bent: bij publicatie in AEM, wordt de inhoud herhaald van de auteursdienst aan de publicatiedienst (of aan [ de voorproefdienst ](/help/sites-cloud/authoring/sites-console/previewing-content.md) als beschikbaar en afhankelijk van de opties de auteur wanneer het publiceren kiest.)

## Verschillen {#differences}

Wat het publiceren met de Universele Redacteur een beetje anders maakt is niet zozeer de redacteur zelf, maar eerder het externe ontvangen van de app die de Universele Redacteur mogelijk maakt.

Als de app extern wordt gehost, zorgt de webtoepassing ervoor dat inhoud van de auteurservice wordt geladen wanneer de app door auteurs in de editor wordt geopend en vanaf de publicatieservice wordt geladen wanneer bezoekers de app openen.

## De service in de app detecteren {#detecting}

Bepalen of de auteur- of publicatieservice moet worden benaderd, kan worden verwezenlijkt met een eenvoudige voorwaardelijke instructie in de app om de juiste auteur of het juiste publicatiepunt te kiezen wanneer wordt gedetecteerd dat deze wordt geopend in de editor.

Een andere optie is de app te implementeren in twee verschillende omgevingen die anders zijn geconfigureerd, zodat de inhoud van de toepassing wordt opgehaald uit de auteurservice en een omgeving die de toepassing ophaalt uit de publicatieservice. Om auteurs in staat te stellen de gepubliceerde URL te openen in de Universal Editor, kunt u een klein script maken om de publicatie-side URL om te zetten in een equivalent ervan in de auteursomgeving (bijvoorbeeld door een subdomein van `author` voor te bereiden), zodat de auteurs automatisch worden omgeleid.

## Samenvatting {#summary}

Het doel van de Universele Redacteur is om geen enkel bepaald patroon op te leggen, zodat de implementatie het best zijn doelstellingen op een volledig ontkoppelde manier kan bereiken terwijl alles eenvoudig en recht voor de uitvoering blijft.

Evenzo stelt de Universele Redacteur geen vereisten op hoe om het even welk bepaald project zou moeten gaan bepalen van welke dienst om de inhoud te leveren. In plaats daarvan biedt het meerdere mogelijkheden en kan het project bepalen welke oplossing het beste is voor zijn eigen vereisten.

## Aanvullende bronnen {#additional-resources}

Zie deze ontwikkelaarsdocumenten voor meer informatie over de technische details van de Universal Editor.

* [ Universele Inleiding van de Redacteur ](/help/implementing/universal-editor/introduction.md) - Leer hoe de Universele Redacteur het uitgeven om het even welk aspect van om het even welke inhoud in om het even welke implementatie toelaat zodat kunt u uitzonderlijke ervaringen leveren, inhoudssnelheid verhogen, en een ervaring van de allernieuwste ontwikkelaar verstrekken.
* [ Begonnen het Worden met de Universele Redacteur in AEM ](/help/implementing/universal-editor/getting-started.md) - leer hoe te om toegang tot de Universele Redacteur te krijgen en hoe te beginnen van instrumenten voorzien uw eerste AEM app om het te gebruiken.
* [ Universele Architectuur van de Redacteur ](/help/implementing/universal-editor/architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [ Attributen en Types ](/help/implementing/universal-editor/attributes-types.md) - leer over de gegevensattributen en de types die de Universele Redacteur vereist.
* [ Universele Authentificatie van de Redacteur ](/help/implementing/universal-editor/authentication.md) - leer hoe de Universele Redacteur voor authentiek verklaart.
