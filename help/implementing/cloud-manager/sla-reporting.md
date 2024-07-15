---
title: SLA-rapportage
description: Leer hoe u de prestaties van uw productie AEM omgeving kunt bekijken ten opzichte van de overeenkomst voor serviceniveau (SLA).
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# SLA-rapportage {#sla-reporting}

Leer hoe u de prestaties van uw productie AEM omgeving kunt bekijken ten opzichte van de overeenkomst voor serviceniveau (SLA).

## Inleiding {#introduction}

SLA die gegevens melden is beschikbaar voor elk productieprogramma via de **Rapporten** tabel. Voer de volgende stappen uit om toegang te krijgen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Gebruikend het paneel van de zijnavigatie, navigeer aan het **lusje van Rapporten** van de **pagina van het Overzicht**.

1. Klik op het gewenste jaar om de SLA-gegevens te zien.

![ SLA grafiekvoorbeeld ](assets/sla-reporting-1.png)

Plaats de cursor op een gegevenspunt om de specifieke waarden voor dat punt weer te geven.

![ tonend gedetailleerde gegevens ](assets/sla-reporting-b.png)

## SLA-waarden {#sla-metrics}

De grafiek van het geselecteerde jaar bevat verschillende gegevenssets.

* **de Rij van Publish Contract** - dit is SLA die in uw contract met Adobe voor publiceert rij wordt bepaald.

* **Echte Rij van Publish** - dit is gemeten uptime van de productie publiceren de incidenten van de rij die door de verkopers van de Adobe of van de Adobe worden veroorzaakt.

* **de Rij van de Auteur van het Eind** - dit is SLA die in uw contract met Adobe voor de auteursrij wordt bepaald.

* **Echte de Reeks van de Auteur van de Auteur** - dit is de gemeten uptime van de de factoring van de productiepauteur incidenten die door de verkopers van de Adobe of van de Adobe worden veroorzaakt.

## Gebeurtenisanalyse {#event-analysis}

De **sectie van de Analyse van de Gebeurtenis** onder de grafiek toont de reeks incidenten die voor het programma tijdens het geselecteerde jaar voorkwamen.

Elk van de incidenten heeft een tijdbereik, een oorzaak en een reeks opmerkingen.

![ Voorbeeld van de Analyse van de Gebeurtenis ](assets/sla-reporting-c.png)

## Interval vernieuwen {#refresh}

SLA-rapportering geeft u inzicht in de prestaties van uw AEM productieomgeving en is up-to-date, maar niet onmiddellijk. SLA- rapportgeneratie gebeurt maandelijks en het wordt geproduceerd voor nieuwe programma&#39;s die als Productie vorige maand duidelijk zijn. Het is niet onmiddellijk. Wegens deze vertraging, te houden gelieve het volgende in mening aangezien u uw SLA rapport controleert:

* De gerapporteerde SLA zal de SLA zijn die aan het begin van de maand bestond, zelfs als de SLA in die maand veranderde.
* Als er aan het begin van de maand geen SLA was omdat het programma toen niet bestond, is de SLA van toepassing die bestond op de datum waarop het programma werd opgesteld.

## Omgevingen voorvertonen {#preview}

De voorvertoningsomgeving is bedoeld als een hulpmiddel voor auteurs van inhoud om de uiteindelijke ervaring van de inhoud te controleren voordat deze wordt gepubliceerd. Daarom zijn voorvertoningsomgevingen niet ontworpen met hoge beschikbaarheid en beschikken ze niet over een bijbehorende SLA.
