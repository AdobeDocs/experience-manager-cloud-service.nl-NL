---
title: Beheer en vertaling van meerdere sites
description: Leer hoe u uw inhoud kunt hergebruiken in uw project en meertalige websites in AEM kunt beheren.
feature: Administering
role: Admin
exl-id: a3d48884-081e-44f8-8055-ee3657757bfd
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Beheer en vertaling van meerdere sites {#msm-and-translation}

Met de ingebouwde tools voor beheer en vertaling van meerdere sites van Adobe Experience Manager kunt u uw inhoud eenvoudiger lokaliseren.

* Met MSM (Multi Site Manager) en de bijbehorende functies voor Live Copy kunt u dezelfde site-inhoud op meerdere locaties gebruiken, terwijl variaties mogelijk zijn:
   * [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](msm/overview.md)
* Met vertaling kunt u de vertaling van pagina-inhoud automatiseren om meertalige websites te maken en onderhouden:
   * [Inhoud vertalen voor meertalige sites](translation/overview.md)

Deze twee functies kunnen worden gecombineerd om te kunnen werken met websites die beide [multinationaal en meertalig](#multinational-and-multilingual-sites).

>[!TIP]
>
>Als u nog geen ervaring hebt met het vertalen van inhoud, raadpleegt u [Vertaalreis naar sites](/help/journey-sites/translation/overview.md). Het is een geleid pad door uw AEM Sites-inhoud te vertalen met behulp van AEM krachtige vertaalhulpmiddelen. Ideaal als u geen AEM of vertaalervaring hebt.

## Meertalige en meertalige sites {#multinational-and-multilingual-sites}

U kunt op efficiënte wijze inhoud maken voor multinationale en meertalige sites door het gecombineerde gebruik van de Multi-Site Manager en de vertaalworkflow.

Doorgaans maakt u een primaire site in één taal en voor een specifiek land en gebruikt u die inhoud als basis voor de andere sites, waar nodig met vertaling.

1. [Vertalen](translation/overview.md) de primaire site in verschillende talen.
1. Gebruiken [Beheer van meerdere sites](msm/overview.md) tot:
   1. Inhoud van de primaire site en de bijbehorende vertalingen opnieuw gebruiken om sites te maken voor andere landen en culturen.
   1. Koppel zo nodig elementen van de actieve kopieën los om lokalisatiegegevens toe te voegen.

>[!TIP]
>
>Beperk het gebruik van beheer van meerdere sites tot inhoud in één taal.
>
>Gebruik bijvoorbeeld het primaire Engels om de Engelse versie van pagina&#39;s voor de pagina&#39;s VS, Canada en VK te maken. Gebruik vervolgens de primaire Fransen om de Franse versie van pagina&#39;s voor Frankrijk, Zwitserland, Canada enzovoort te maken.

In het volgende diagram ziet u hoe de hoofdconcepten elkaar snijden (maar niet alle niveaus/elementen in kwestie weergeven):

![Overzicht van lokalisatie](assets/localization-overview.png)

In dit scenario, en vergelijkbare, beheert MSM niet de verschillende taalversies als dusdanig.

* [MSM](msm/overview.md) beheert de implementatie van vertaalde inhoud van een blauwdruk (dat wil zeggen een primaire globale blauwdruk) tot de Actieve Exemplaren (dat wil zeggen, de lokale plaatsen), binnen de grenzen van een taal.
* De [vertalen](translation/overview.md) de integratiemogelijkheden van AEM, met de vertaalbeheerservices van derden, beheren de talen en vertalen van inhoud in deze verschillende talen.

Voor geavanceerdere gebruiksgevallen kan MSM ook in de primaire talen worden gebruikt.

>[!TIP]
>
>Voor alle gebruiksgevallen is het raadzaam de volgende aanbevolen procedures te lezen:
>
>* [Beste praktijken voor MSM](msm/best-practices.md)
>* [Aanbevolen procedures voor vertaling](translation/best-practices.md)
