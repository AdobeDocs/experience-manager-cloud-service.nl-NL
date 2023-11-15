---
title: Back-up en herstel in AEM as a Cloud Service
description: Meer informatie over Back-up en Herstellen in AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 83b5d9a3ff0e9a3c69e36a97a3f733b05f827d3b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---


# Back-up en herstel in AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Back-up en herstel"
>abstract="AEM as a Cloud Service kan de volledige toepassing van een klant (code en inhoud) aan specifieke, vooraf bepaalde tijden in de laatste zeven dagen herstellen, die wat op productie was vervangen. Deze functie moet alleen worden gebruikt bij ernstige problemen met code of inhoud. De recente gegevens tussen het tijdstip van de herstelde back-up en het moment waarop deze wordt gemaakt, gaan verloren. Het opvoeren wordt ook hersteld aan de oude versie."

Als er inhoud of gegevensbeschadiging optreedt, kan AEM as a Cloud Service de volledige toepassing van de klant (code en inhoud) herstellen. De laatste zeven dagen is de productie weer op specifieke, vooraf bepaalde tijdstippen teruggebracht, in plaats van de productie.
Als de plaatsing van een klant, die de opgestelde toepassingscode betekent of gebroken of knecht is, is het verkieslijk om het te bevestigen en naar een nieuwe versie vooruit te rollen eerder dan het van steun te herstellen. Back-up wordt uitgevoerd op een manier die geen invloed heeft op de prestaties tijdens de uitvoering van een toepassing.

>[!CAUTION]
>
>Deze functie moet alleen worden gebruikt bij ernstige problemen met code of inhoud. De recente gegevens tussen het tijdstip van de herstelde back-up en het moment waarop deze wordt gemaakt, gaan verloren. Het opvoeren wordt ook hersteld aan de oude versie.

## Het gebruik {#how-to-use}

Klanten dienen een ondersteuningsticket in te dienen waarin het probleem wordt beschreven dat zich voordoet. Het ondersteuningsticket leidt gewoonlijk tot een onderzoek door ondersteuning van de Adobe, die dan kan bepalen of een terugzetbewerking nodig is.

AEM as a Cloud Service ondersteuning:

* Back-up en herstel voor stadium-, productie- en ontwikkelomgevingen.
* 24-uurs punt in tijdterugwinning, die betekent dat het systeem aan om het even welk punt in de laatste 24 uren kan worden hersteld.
* Herstel op basis van een specifieke, door de Adobe gedefinieerde tijdstempel, die de laatste zeven dagen tweemaal per dag wordt genomen. Alle replicatieberichten (verwijderen, bijwerken, maken) blijven behouden.

In alle gevallen, is de versie van de douanecode genomen van de laatste succesvolle plaatsing vóór herstellen punt.

De hersteltijddoelstelling (RTO) kan variëren, maar als algemene richtlijn duurt de herstelvolgorde gemiddeld van 60 tot 90 minuten, afhankelijk van verschillende factoren, zoals de grootte van de opslagplaats. Voorvertoningen van omgevingen en meerdere regio&#39;s kunnen de hersteltijddoelstelling verlengen.

Na een terugzetbewerking wordt de AEM versie bijgewerkt naar de meest recente.

>[!CAUTION]
>
>Gegevens uit verwijderde omgevingen gaan permanent verloren en kunnen niet worden hersteld.

## Offsite back-up {#offsite-backup}

Hoewel regelmatige back-ups het risico van onopzettelijke verwijderingen of technische storingen binnen AEM Cloud Servicen dekken, moeten ook de risico&#39;s die kunnen ontstaan door het falen van een regio worden gedekt. Naast beschikbaarheid is het grootste risico in dergelijke uitvallen van gegevensgebieden in de eerste plaats een verlies van gegevens.
AEM as a Cloud Service dekt dit risico als standaard voor alle AEM productieomgevingen. De volledige AEM inhoud wordt voortdurend naar een afgelegen gebied gekopieerd en gedurende drie maanden beschikbaar voor herstel. Adobe roept deze mogelijkheid aan offsite back-up.
De restauratie van AEM Cloud Servicen voor stadium en productiemilieu&#39;s wordt uitgevoerd door AEM de Techniek van de Betrouwbaarheid van de Dienst als er gegevensgebiedstroomonderbrekingen zijn.