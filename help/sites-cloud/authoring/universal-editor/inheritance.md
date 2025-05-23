---
title: Overerving van inhoud in de Universal Editor
description: Leer hoe de Universal Editor het overnemen van inhoud ondersteunt voor beheer van meerdere sites en Starten om hergebruik en lokalisatie van inhoud te ondersteunen.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 2a1b87c2-29b9-4689-9a15-e17942439160
source-git-commit: 9941c652a1509934662cdaae6d187d1a28a1cc31
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Overerving van inhoud in de Universal Editor {#inheritance}

Leer hoe de Universal Editor het overnemen van inhoud ondersteunt voor beheer van meerdere sites en Starten om hergebruik en lokalisatie van inhoud te ondersteunen.

>[!NOTE]
>
>Deze functie is alleen beschikbaar voor inhoud die is opgeslagen in de AEM-opslagplaats.

## Hoofdletters gebruiken {#use-case}

Voor veel gebruikers van AEM is het maken van een pagina nog maar het begin. Als u inhoud effectief wilt schalen, worden de volgende stappen doorgaans doorlopen nadat u de pagina hebt gemaakt:

1. **vertaal de pagina** door taalexemplaren en vertaalwerkschema&#39;s te gebruiken.
1. **lokaliseer de pagina** door het Beheer van de MultiPlaats te gebruiken om de vertaalde pagina aan verschillende markten uit te rollen.
1. **creeer nieuwe versies** door Lagen te gebruiken om toekomstige herhalingen van de pagina voor te bereiden en die veranderingen levend te nemen.

Deze stappen kunnen de snelheid van de inhoud versnellen en de consistentie van de inhoud garanderen. De Universele Redacteur steunt inhoudsovererving, die de exemplaren van de mechanisetaal, het Beheer van de MultiPlaats, en Lanceringen baseert zich op.

## Overerving {#what-is-inheritance}

Overerving is het mechanisme waarbij inhoud kan worden gekoppeld, zodat het ene element automatisch het andere verandert.

MSM en Launches zijn krachtige hulpmiddelen waarmee u uw inhoud kunt hergebruiken via overerving. Pagina&#39;s kunnen vanuit een centrale bron (de blauwdruk) worden gekopieerd, zodat auteurs specifieke wijzigingen kunnen aanbrengen in de context van die kopieën, terwijl de rest van de inhoud overerfd blijft van de blauwdruk. Dit is bijzonder handig wanneer u sites lokaliseert.

Om bepaalde inhoud van de kopieën te wijzigen, breken auteurs de overerving op de desbetreffende componenten om ervoor te zorgen dat hun lokale wijzigingen niet worden overschreven wanneer de kopieën worden gesynchroniseerd van de blauwdruk.

## Inhoudsovererving en de Universal Editor {#universal-editor}

Wanneer een pagina deel van MSM uitmaakt of een Lanceer en de inhoud met de Universele Redacteur wordt uitgegeven, maakt de redacteur automatisch overerving voor alle veranderingen onbruikbaar die door auteurs op die pagina worden aangebracht, die ervoor zorgen dat de gewijzigde inhoud wordt behouden wanneer de updates van de blauwdruk worden gesynchroniseerd.

De auteur hoeft niet op een knop te klikken of op een andere manier andere stappen te ondernemen om overerving uit te schakelen voordat hij lokale bewerkingen uitvoert. Zodra een verandering wordt aangebracht, wordt de erfenis impliciet geannuleerd. Dit werkschema is in tegenstelling tot de [ Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components).

Overerving kan voor de gehele pagina worden hersteld via:

* [ Levende Console van het Overzicht van het Exemplaar ](/help/sites-cloud/administering/msm/live-copy-overview.md)
* [Opstartconsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
* Gebruikend de **knoop van het Terugstellen** op het **Levende lusje van het Exemplaar** van het [ pagina eigenschappen venster ](/help/sites-cloud/authoring/sites-console/page-properties.md).

De Universal Editor heeft geen invloed op het onderliggende overervingsmechanisme. Raadpleeg de volgende documentatie voor meer informatie over hoe overerving werkt.

* [Beheer van meerdere sites (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Lanceringen](/help/sites-cloud/authoring/launches/overview.md)

### MSM-extensie (AEM Multi-Site Management) {#msm-extension}

Indien geïnstalleerd, toont de **multi-plaats-beheer van AEM (MSM) Uitbreiding** zowel de huidige overervingsstatus van de geselecteerde component evenals staat u toe om overerving op het componentenniveau te breken of opnieuw op te nemen.

Gelieve te zien [ auteursdocumentatie voor meer informatie over hoe te om deze uitbreiding te gebruiken.](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)

Voor informatie over hoe te om deze uitbreiding toe te laten, [ te zien gelieve de documentatie van Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## Beperkingen {#limitations}

* Om overerving voor enige componenten terug te keren, moet de **multi-plaats-beheer van AEM (MSM) Uitbreiding** worden toegelaten.
* Voor visueel terugkoppel om te zien welke componenten hun gehandicapte erving hebben en die het nog hebben behouden, moet de **uitbreiding van het Beheer van AEM multi-Plaats-Beheer (MSM)** worden toegelaten.
* Deze eigenschappen zijn momenteel beperkt tot componenten in pagina&#39;s en zijn nog niet van toepassing op [ de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md), ondanks die ook die mogelijkheden MSM hebben en lanceren.
