---
title: Beheer en vertaling van meerdere sites
description: Leer hoe u uw inhoud kunt hergebruiken in uw project en meertalige websites in AEM kunt beheren.
feature: Administering
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Beheer en vertaling van meerdere sites {#msm-and-translation}

Met de ingebouwde tools voor beheer van meerdere sites van Adobe Experience Manager kunt u uw inhoud eenvoudiger lokaliseren.

* Met MSM (Multi Site Manager) en de bijbehorende functies voor Live Copy kunt u dezelfde site-inhoud op meerdere locaties gebruiken, terwijl variaties mogelijk zijn:
   * [Inhoud opnieuw gebruiken: Beheer van meerdere sites en Live Copy](msm/overview.md)
* Met vertaling kunt u de vertaling van pagina-inhoud automatiseren om meertalige websites te maken en onderhouden:
   * [Inhoud vertalen voor meertalige sites](translation/overview.md)

Deze twee eigenschappen kunnen worden gecombineerd om voor websites te behandelen die zowel [multinationaal als meertalig](#multinational-and-multilingual-sites) zijn.

## Meertalige en meertalige sites {#multinational-and-multilingual-sites}

U kunt op efficiënte wijze inhoud maken voor multinationale en meertalige sites door het gecombineerde gebruik van de Multi-Site Manager en de vertaalworkflow.

Doorgaans maakt u een master site in één taal en voor een specifiek land en gebruikt u die inhoud als basis voor de andere sites, waar nodig met vertaling.

1. [](translation/overview.md) Vertaal de master site in verschillende talen.
1. [Beheer van meerdere sites](msm/overview.md) gebruiken om:
   1. Inhoud van de master site en de vertalingen ervan hergebruiken om sites te maken voor andere landen en culturen.
   1. Koppel zo nodig elementen van de actieve kopieën los om lokalisatiegegevens toe te voegen.

>[!TIP]
>
>Beperk het gebruik van beheer van meerdere sites tot inhoud in één taal.
>
>Gebruik bijvoorbeeld de master Engelse versie om de Engelse versie van pagina&#39;s te maken voor de VS, Canada, het Verenigd Koninkrijk, enz. pagina&#39;s en gebruik de master Franse versie om de Franse versie van pagina&#39;s voor Frankrijk, Zwitserland, Canada, enz. te maken.

In het volgende diagram ziet u hoe de hoofdconcepten elkaar snijden (maar niet alle niveaus/elementen in kwestie weergeven):

![Overzicht van lokalisatie](assets/localization-overview.png)

In dit, en vergelijkbaar, scenario&#39;s MSM beheert niet de verschillende taalversies als dusdanig.

* [Het ](msm/overview.md) MSMbeheer de plaatsing van vertaalde inhoud van een blauwdruk (d.w.z. een algemeen master) aan Levende Exemplaren (d.w.z. de lokale plaatsen), binnen de grenzen van een taal.
* Met de [integratiemogelijkheden van AEM voor vertaling](translation/overview.md), in combinatie met vertaalbeheerservices van derden, worden de talen beheerd en wordt inhoud in deze verschillende talen vertaald.

Voor geavanceerdere gebruiksgevallen kan MSM ook voor alle taalmeesters worden gebruikt.

>[!TIP]
>
>Voor alle gebruiksgevallen is het raadzaam de volgende aanbevolen procedures te lezen:
>
>* [Beste praktijken voor MSM](msm/best-practices.md)
>* [Aanbevolen procedures voor vertaling](translation/best-practices.md)

