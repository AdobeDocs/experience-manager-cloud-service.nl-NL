---
title: SLA-rapportage
description: Leer hoe u de prestaties van uw productie AEM omgeving kunt bekijken ten opzichte van de overeenkomst voor serviceniveau (SLA).
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# SLA-rapportage {#sla-reporting}

Leer hoe u de prestaties van uw productie AEM omgeving kunt bekijken ten opzichte van de overeenkomst voor serviceniveau (SLA).

## Inleiding {#introduction}

SLA-rapporteringsgegevens zijn beschikbaar voor elk productieprogramma via **Rapporten** tab. Voer de volgende stappen uit om toegang te krijgen.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Rapporten** van de **Overzicht** pagina.

1. Klik op het gewenste jaar om de SLA-gegevens te zien.

![SLA-grafiekvoorbeeld](assets/sla-reporting-1.png)

Schuif de cursor over een gegevenspunt om de specifieke waarden voor dat punt weer te geven.

![Gedetailleerde gegevens weergeven](assets/sla-reporting-b.png)

## SLA-waarden {#sla-metrics}

De grafiek van het geselecteerde jaar bevat een aantal gegevenssets.

* **Tier-contract publiceren** - Dit is SLA die in uw contract met Adobe voor publicatielaag wordt bepaald.

* **Reële reeks publiceren** - Dit is de gemeten uptime van de productie publiceer tier factoring die door Adobe of Adobe incidenten wordt veroorzaakt.

* **Tier-contract voor auteur** - Dit is SLA die in uw contract met Adobe voor de auteursrij wordt bepaald.

* **Reële lijst van auteur** - Dit is de gemeten uptime van de productiefabrikant die door Adobe of Adobe incidenten wordt veroorzaakt.

## Gebeurtenisanalyse {#event-analysis}

De **Gebeurtenisanalyse** in het gedeelte onder de grafiek wordt de reeks incidenten weergegeven die zich tijdens het geselecteerde jaar voor het programma hebben voorgedaan.

Elk van de incidenten heeft een tijdbereik, een oorzaak en een reeks opmerkingen.

![Voorbeeld van gebeurtenisanalyse](assets/sla-reporting-c.png)
