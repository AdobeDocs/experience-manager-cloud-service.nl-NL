---
title: Inhoud publiceren met de Universal Editor
description: Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Inhoud publiceren met de Universal Editor {#publishing}

Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.

{{universal-editor-status}}

## Gelijksoortigheid met AEM {#similarities}

Voor gebruikers van AEM werkt het proces om inhoud te publiceren met de Universele Redacteur zoals u gewend bent: bij publicatie in AEM, wordt de inhoud herhaald van de auteursrij aan de publicatielaag.

## Verschillen {#differences}

Wat het publiceren met de Universele Redacteur een beetje anders maakt is niet zozeer de redacteur zelf, maar eerder het externe ontvangen van de app die de Universele Redacteur mogelijk maakt.

Als de app extern wordt gehost, zorgt de webtoepassing ervoor dat inhoud uit de auteurslaag wordt geladen wanneer de app door auteurs in de editor wordt geopend en vanaf de publicatielaag wordt geladen wanneer bezoekers de app openen.

## Rij in de app detecteren {#detecting}

U kunt bepalen of de auteur- of publicatielaag toegang moet hebben door een eenvoudige voorwaardelijke instructie in de app te kiezen om de juiste auteur of het juiste publicatiepunt te kiezen wanneer wordt gedetecteerd dat deze wordt geopend in de editor.

Een andere optie is de app te implementeren in twee verschillende omgevingen die anders zijn geconfigureerd, zodat de inhoud wordt opgehaald uit de auteurslaag en een omgeving die deze ophaalt uit de publicatielaag. Om auteurs in staat te stellen de gepubliceerde URL te openen in de Universal Editor, kunt u een klein script maken om de publicatie-side URL om te zetten in een equivalent ervan in de auteursomgeving (bijvoorbeeld door een subdomein van `author` voor te bereiden), zodat de auteurs automatisch worden omgeleid.

## Samenvatting {#summary}

Het doel van de Universele Redacteur is om geen enkel bepaald patroon op te leggen, zodat de implementatie het best zijn doelstellingen op een volledig ontkoppelde manier kan bereiken terwijl alles eenvoudig en recht voor de uitvoering blijft.

Evenzo stelt de Universele Redacteur geen vereisten op hoe om het even welk bepaald project zou moeten gaan bepalen van welke rij om de inhoud te leveren. In plaats daarvan biedt het meerdere mogelijkheden en kan het project bepalen welke oplossing het beste is voor zijn eigen vereisten.
