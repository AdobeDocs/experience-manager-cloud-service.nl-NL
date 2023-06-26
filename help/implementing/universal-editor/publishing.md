---
title: Inhoud publiceren met de Universal Visual Editor
description: Leer hoe de Universal Visual Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Inhoud publiceren met de Universal Visual Editor {#publishing}

Leer hoe de Universal Visual Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.

## Gelijksoortigheid met AEM {#similarities}

Voor gebruikers van AEM, werkt het proces om inhoud met de Universele Visuele Redacteur te publiceren aangezien u gewend bent: bij publicatie in AEM wordt de inhoud overgenomen van de auteurslaag naar de publicatielaag.

## Verschillen {#differences}

Wat het publiceren met de Universele Visuele Redacteur een beetje verschillend maakt is niet zozeer de redacteur zelf, maar eerder het externe ontvangen van app die de Universele Redacteur mogelijk maakt.

Als de app extern wordt gehost, zorgt de webtoepassing ervoor dat inhoud uit de auteurslaag wordt geladen wanneer de app door auteurs in de editor wordt geopend en vanaf de publicatielaag wordt geladen wanneer bezoekers de app openen.

## Rij in de app detecteren {#detecting}

U kunt bepalen of de auteur- of publicatielaag toegang moet hebben door een eenvoudige voorwaardelijke instructie in de app te kiezen om de juiste auteur of het juiste publicatiepunt te kiezen wanneer wordt gedetecteerd dat deze wordt geopend in de editor.

Een andere optie is de app te implementeren in twee verschillende omgevingen die anders zijn geconfigureerd, zodat de inhoud wordt opgehaald uit de auteurslaag en een omgeving die deze ophaalt uit de publicatielaag. Om auteurs in staat te stellen de gepubliceerde URL te openen in de Universal Editor, kan een klein script worden gemaakt om de publicatie-side URL om te zetten in een equivalent ervan in de auteursomgeving (bijvoorbeeld door een voorinstelling van een `author` subdomein), zodat de auteurs automatisch worden omgeleid.

## Samenvatting {#summary}

Het doel van de Universele Redacteur is om geen enkel bepaald patroon op te leggen, zodat de tenuitvoerlegging zijn doelstellingen het best op een volledig ontkoppelde manier kan bereiken terwijl alles eenvoudig en recht voor de uitvoering blijft.

Evenzo stelt de Universele Redacteur geen vereisten op hoe om het even welk bepaald project zou moeten gaan bepalen van welke rij om de inhoud te leveren. In plaats daarvan biedt het een aantal mogelijkheden en stelt het project in staat te bepalen welke oplossing het beste is voor zijn eigen vereisten.
