---
title: Inhoud publiceren met de Universal Editor
description: Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Inhoud publiceren met de Universal Editor {#publishing}

Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.

## Gelijksoortigheid met AEM {#similarities}

Voor gebruikers van AEM werkt het proces om inhoud te publiceren met de Universele Redacteur zoals u gewend bent: bij publicatie in AEM, wordt de inhoud herhaald van de auteursrij aan de publicatielaag.

## Verschillen {#differences}

Wat het publiceren met de Universele Redacteur een beetje anders maakt is niet zozeer de redacteur zelf, maar eerder het externe ontvangen van de app die de Universele Redacteur mogelijk maakt.

Als de app extern wordt gehost, zorgt de webtoepassing ervoor dat inhoud uit de auteurslaag wordt geladen wanneer de app door auteurs in de editor wordt geopend en vanaf de publicatielaag wordt geladen wanneer bezoekers de app openen.

## Rij in de app detecteren {#detecting}

U kunt bepalen of de auteur- of publicatielaag toegang moet hebben door een eenvoudige voorwaardelijke instructie in de app te kiezen om de juiste auteur of het juiste publicatiepunt te kiezen wanneer wordt gedetecteerd dat deze wordt geopend in de editor.

Een andere optie is de app te implementeren in twee verschillende omgevingen die anders zijn geconfigureerd, zodat de inhoud wordt opgehaald uit de auteurslaag en een omgeving die deze ophaalt uit de publicatielaag. Als u wilt dat auteurs de gepubliceerde URL kunnen openen in de Universal Editor, kunt u een klein script maken om de publicatie-side URL om te zetten in een equivalente URL in de auteursomgeving (bijvoorbeeld door een voorvoegsel van een `author` subdomein), zodat de auteurs automatisch worden omgeleid.

## Samenvatting {#summary}

Het doel van de Universele Redacteur is om geen enkel bepaald patroon op te leggen, zodat de implementatie het best zijn doelstellingen op een volledig ontkoppelde manier kan bereiken terwijl alles eenvoudig en recht voor de uitvoering blijft.

Evenzo stelt de Universele Redacteur geen vereisten op hoe om het even welk bepaald project zou moeten gaan bepalen van welke rij om de inhoud te leveren. In plaats daarvan biedt het meerdere mogelijkheden en kan het project bepalen welke oplossing het beste is voor zijn eigen vereisten.

## Aanvullende bronnen {#additional-resources}

Zie dit document voor meer informatie over het schrijven van inhoud naar de universele editor.

* [Inhoud ontwerpen met de Universal Editor](authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.

Zie deze ontwikkelaarsdocumenten voor meer informatie over de technische details van de Universal Editor.

* [Introductie van Universal Editor](/help/implementing/universal-editor/introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](/help/implementing/universal-editor/architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](/help/implementing/universal-editor/attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](/help/implementing/universal-editor/authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
