---
title: SLA-rapporten
description: Leer hoe u de prestaties van uw AEM-productieomgeving kunt bekijken ten opzichte van de Service level agreement die u onder contract hebt.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---


# SLA-rapporten {#sla-reporting}

Leer hoe u de prestaties van uw productie-AEM-omgeving kunt bekijken in verhouding tot de SLA (Service level agreement) die u uitbesteedt.

## Een SLA-rapport weergeven {#introduction}

In SLA-rapporten worden prestatiegegevens bijgehouden voor twee productieniveaus: Auteurniveau en Publicatieniveau.

De lijngrafiek van een geselecteerd jaar bevat gegevenspunten voor elke maand van januari tot december. De volgende metriek worden bijgehouden.

| Metrisch bijgehouden | Lijnkleur | Beschrijving |
| --- | --- | --- |
| Auteur-reeks werkelijk | Lichtgroen | De gemeten uptime van de productiereeks van de auteur die door Adobe of Adobe verkopers wordt veroorzaakt. |
| Tier-contract voor auteur | Donkerblauw | De SLA die in uw contract met Adobe is gedefinieerd voor de lijst met auteurs. |
| Reële reeks publiceren | Oranje | De gemeten uptime van het publicatieniveau van de productie, factoring incidenten veroorzaakt door Adobe of Adobe verkopers. |
| Tier-contract publiceren | Rood | De SLA die in uw contract met Adobe is gedefinieerd voor de publicatielijst. |

**om een rapport van SLA te bekijken:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht van het Programma**, in het linkerzijmenu, klik **Rapporten**.

1. Klik **Rapporten van SLA**.

   ![ grafiek van de het rapportlijn van SLA ](/help/implementing/cloud-manager/reports/assets/cm-sla-report2.png)

1. Klik op het gewenste jaar om een lijngrafiek met SLA-gegevens weer te geven.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Plaats de cursor op een gegevenspunt in de lijngrafiek om de specifieke waarden voor dat punt weer te geven.
   * Onder het jaar van de lijngrafiek, klik de pictogram **Download** om een PNG- beelddossier van de lijngrafiek te bewaren.
   * Klik een metrische naam om enkel de gegevens van dat metrisch te zien. Of druk op `Shift` op het toetsenbord terwijl u een of meer namen voor metrische gegevens selecteert of deselecteert.

## Gebeurtenisanalyse {#event-analysis}

De **sectie van de Analyse van de Gebeurtenis** onder de grafiek toont de reeks incidenten die voor het programma tijdens het geselecteerde jaar voorkwamen.

Elk van de incidenten heeft een tijdbereik, een oorzaak en een reeks opmerkingen.

![ Voorbeeld van de Analyse van de Gebeurtenis ](/help/implementing/cloud-manager/reports/assets/sla-reporting-c.png)

## Interval vernieuwen voor SLA-rapporten {#refresh}

SLA-rapportering geeft u insight inzicht in de prestaties van uw AEM-productieomgeving en is up-to-date, maar niet onmiddellijk. SLA-rapporten worden maandelijks gegenereerd en gegenereerd voor nieuwe programma&#39;s die zijn gemarkeerd als `Production previous month` . Het is niet onmiddellijk. Houd daarom rekening met het volgende wanneer u uw SLA-rapport bekijkt:

* De gerapporteerde SLA is de die bestond aan het begin van de maand, zelfs als SLA in die maand veranderde.
* Als er aan het begin van de maand geen SLA was omdat het programma niet bestond, geldt de SLA die bestond op de datum waarop het programma werd opgezet.

## Voorvertoningsomgevingen {#preview}

De voorvertoningsomgeving is bedoeld als een hulpmiddel voor auteurs van inhoud om de uiteindelijke ervaring van de inhoud te controleren voordat deze wordt gepubliceerd. Vanwege deze functionaliteit zijn voorvertoningsomgevingen niet ontworpen met hoge beschikbaarheid en hebben ze geen bijbehorende SLA.

