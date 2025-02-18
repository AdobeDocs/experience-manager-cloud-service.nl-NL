---
title: Inhoud publiceren met de Universal Editor
description: Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 64c257adc7e1f22531c0fe45b44b27ab4e0badb8
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---


# Inhoud publiceren met de Universal Editor {#publishing}

Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.

>[!TIP]
>
>Het hier beschreven publicatieproces is de standaard out-of-the-box eigenschap van de Universele Redacteur.
>
>De Universele Redacteur steunt ook [ uitbreidingen en de rekbaarheid UI ](/help/implementing/universal-editor/extending.md) om werkschema&#39;s toe te staan om uw publicatieproces te steunen, zodat kan uw publicatiestroom variëren.

## Inhoud publiceren vanuit de Universal Editor {#publishing-content}

Wanneer u als inhoudauteur bereid bent om uw inhoud te publiceren, moet u eenvoudig tikken of het **klikken publiceert** pictogram in de Universele het hulpmiddelbar van de Redacteur.

![ het Publiceren pagina&#39;s ](assets/publish-menu.png)

1. In de Universele Redacteur, tik of klik [ het **publiceren** pictogram in de Universele het hulpmiddelbar van de Redacteur.](/help/sites-cloud/authoring/universal-editor/navigation.md#publish)
1. Als u de voorproefdienst van a [ ](/help/sites-cloud/authoring/sites-console/previewing-content.md) beschikbaar hebt, kunt u kiezen waar u uw inhoud publiceert, of aan **Voorproef** of **publiceren**.
1. De **Punten** sectie maakt een lijst van de inhoud die in de publicatie omvat:
   * **Nieuwe** punten die nog niet zijn gepubliceerd.
   * **veranderde** inhoud die is gepubliceerd, maar sinds de laatste publicatie gewijzigd.
   * **Gepubliceerde** inhoud die is gepubliceerd en niet sinds die publicatie gewijzigd.

   Tik of klik op de selectievakjes naast deze items om ze naar wens in of uit te sluiten van publicatie. Tik of klik **breid** uit om individuele punten inbegrepen in de totalen voor de drie categorieën te zien en hen te kunnen in/uitsluiten individueel.

   ![ publiceer punten ](assets/publish-items.png)

   Tik of klik de achterpijl naast de **rubriek van Punten** om aan het overzicht terug te keren.

1. Tik of klik **publiceer** om te publiceren of **annuleer** om te aborteren.

## Publicatie van inhoud in de Universal Editor ongedaan maken {#unpublishing-content}

Het ongedaan maken van de publicatie van inhoud werkt op vergelijkbare wijze als het publiceren van inhoud. Wanneer u als inhoudauteur bereid bent om inhoud uit publicatie te verwijderen, tik of klik het ellipsiepictogram in de Universele het hulpmiddelbar van de Redacteur en dan **unpublish**.

U hebt dan de zelfde opties om inhoud ongedaan te maken zoals u toen [ publiceerde inhoud.](#publishing-content) inclusief het ongedaan maken van de publicatie van een voorvertoningsinstantie, indien beschikbaar, en van de items die u wilt opnemen in de publicatie.

## Publiceren en Publiceren ongedaan maken vanuit de Sites-console {#publishing-sites-console}

U kunt [ van de console van Plaatsen ook publiceren, ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) die nuttig kan zijn wanneer u wenst om veelvoudige pagina&#39;s van inhoud te publiceren of publicatie of unpublication te plannen.

## Vergelijkbaar met de Pagina-editor {#similarities}

Voor gebruikers van de [ Redacteur van de Pagina van AEM, ](/help/sites-cloud/authoring/page-editor/introduction.md) het proces om inhoud met de Universele Redacteur te publiceren werkt aangezien u gewend bent: bij publicatie in AEM, wordt de inhoud herhaald van de auteursrij aan publiceer rij.

## Verschillen {#differences}

Wat het publiceren met de Universele Redacteur een beetje anders maakt is niet zozeer de redacteur zelf, maar eerder het externe ontvangen van de app die de Universele Redacteur mogelijk maakt.

Als de app extern wordt gehost, zorgt de webtoepassing ervoor dat inhoud uit de auteurslaag wordt geladen wanneer de app door auteurs in de editor wordt geopend en vanaf de publicatielaag wordt geladen wanneer bezoekers de app openen.

## Rij in de app detecteren {#detecting}

U kunt bepalen of de auteur- of publicatielaag toegang moet hebben door een eenvoudige voorwaardelijke instructie in de app te kiezen om de juiste auteur of het juiste publicatiepunt te kiezen wanneer wordt gedetecteerd dat deze wordt geopend in de editor.

Een andere optie is de app te implementeren in twee verschillende omgevingen die anders zijn geconfigureerd, zodat de inhoud wordt opgehaald uit de auteurslaag en een omgeving die deze ophaalt uit de publicatielaag. Om auteurs in staat te stellen de gepubliceerde URL te openen in de Universal Editor, kunt u een klein script maken om de publicatie-side URL om te zetten in een equivalent ervan in de auteursomgeving (bijvoorbeeld door een subdomein van `author` voor te bereiden), zodat de auteurs automatisch worden omgeleid.

## Samenvatting {#summary}

Het doel van de Universele Redacteur is om geen enkel bepaald patroon op te leggen, zodat de implementatie het best zijn doelstellingen op een volledig ontkoppelde manier kan bereiken terwijl alles eenvoudig en recht voor de uitvoering blijft.

Evenzo stelt de Universele Redacteur geen vereisten op hoe om het even welk bepaald project zou moeten gaan bepalen van welke rij om de inhoud te leveren. In plaats daarvan biedt het meerdere mogelijkheden en kan het project bepalen welke oplossing het beste is voor zijn eigen vereisten.

## Aanvullende bronnen {#additional-resources}

Zie dit document voor meer informatie over het schrijven van inhoud naar de universele editor.

* [ Authoring Inhoud met de Universele Redacteur ](authoring.md) - Leer hoe gemakkelijk en intuïtief het voor inhoudsauteurs is om inhoud tot stand te brengen gebruikend de Universele Redacteur.

Zie deze ontwikkelaarsdocumenten voor meer informatie over de technische details van de Universal Editor.

* [ Universele Inleiding van de Redacteur ](/help/implementing/universal-editor/introduction.md) - Leer hoe de Universele Redacteur het uitgeven om het even welk aspect van om het even welke inhoud in om het even welke implementatie toelaat zodat kunt u uitzonderlijke ervaringen leveren, inhoudssnelheid verhogen, en een ervaring van de allernieuwste ontwikkelaar verstrekken.
* [ Begonnen het Worden met de Universele Redacteur in AEM ](/help/implementing/universal-editor/getting-started.md) - leer hoe te om toegang tot de Universele Redacteur te krijgen en hoe te beginnen van instrumenten voorzien uw eerste AEM app om het te gebruiken.
* [ Universele Architectuur van de Redacteur ](/help/implementing/universal-editor/architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [ Attributen en Types ](/help/implementing/universal-editor/attributes-types.md) - leer over de gegevensattributen en de types die de Universele Redacteur vereist.
* [ Universele Authentificatie van de Redacteur ](/help/implementing/universal-editor/authentication.md) - leer hoe de Universele Redacteur voor authentiek verklaart.
