---
title: Back-up en herstel in AEM as a Cloud Service
description: Back-up en herstel in AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 12e747ff73e9416775a3f26040ac7e15c21505ec
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# Back-up en herstel in AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Back-up en herstel"
>abstract="AEM as a Cloud Service kan de volledige toepassing van een klant (code en inhoud) aan specifieke, vooraf bepaalde tijden in de laatste zeven dagen herstellen, die wat op productie was vervangen. Deze functie moet alleen worden gebruikt bij ernstige problemen met code of inhoud. De recente gegevens tussen het tijdstip van de herstelde back-up en het moment waarop deze wordt gemaakt, gaan verloren. Het opvoeren zal ook aan de oude versie worden hersteld."

Mocht inhoud of gegevenscorruptie voorkomen, AEM as a Cloud Service kan de volledige toepassing (code en inhoud) van een klant aan specifieke, vooraf bepaalde tijden in de laatste zeven dagen herstellen, die wat op productie was vervangen.
Als de plaatsing van een klant, die de opgestelde toepassingscode betekent of gebroken of knecht is, is het verkieslijk om het te bevestigen en naar een nieuwe versie vooruit te rollen eerder dan het van steun te herstellen. Back-up wordt uitgevoerd op een manier die geen invloed heeft op de prestaties tijdens de uitvoering van een toepassing.

>[!CAUTION]
>
>Deze functie moet alleen worden gebruikt bij ernstige problemen met code of inhoud. De recente gegevens tussen het tijdstip van de herstelde back-up en het moment waarop deze wordt gemaakt, gaan verloren. Het opvoeren zal ook aan de oude versie worden hersteld.

## Het gebruik {#how-to-use}

Klanten dienen een ondersteuningsticket in te dienen waarin het probleem wordt beschreven dat zich voordoet. Dit zal leiden tot een onderzoek door Adobe support, die zal bepalen of een herstel nodig is.

AEM as a Cloud Service ondersteuning:

* Back-up en herstel voor stadium-, productie- en ontwikkelomgevingen.
* 24-uurs herstel, wat betekent dat het systeem in de laatste 24 uur op elk punt kan worden hersteld.
* Herstel van een specifieke, door Adobe gedefinieerde tijdstempel die tweemaal per dag is genomen gedurende de laatste 7 dagen.  Alle replicatieberichten (verwijderen, bijwerken, maken) blijven behouden.

In alle gevallen, zal de versie van de douanecode van de laatste succesvolle plaatsing vóór het terugzetpunt worden genomen.

De hersteltijddoelstelling (RTO) kan variëren, maar als algemene richtlijn duurt de herstelvolgorde gemiddeld tussen 60 en 90 minuten, afhankelijk van verschillende factoren, zoals de grootte van de opslagplaats.

Na een terugzetbewerking wordt de AEM versie bijgewerkt naar de meest recente.

>[!CAUTION]
>
>Gegevens uit verwijderde omgevingen gaan permanent verloren en kunnen niet worden hersteld.

## Offsite back-up {#offsite-backup}

Hoewel regelmatige back-ups het risico dekken van onopzettelijke verwijderingen of technische fouten binnen AEM Cloud Services, moeten de risico&#39;s die kunnen ontstaan door het falen van een regio ook worden gedekt. Naast beschikbaarheid is het grootste risico in dergelijke uitvallen van gegevensgebieden in de eerste plaats een verlies van gegevens.
AEM as a Cloud Service dekt dit risico als standaard voor alle AEM productieomgevingen door voortdurend het volledige AEM naar een afgelegen gebied te kopiëren en het voor herstel beschikbaar te stellen gedurende een periode van drie maanden. We noemen deze mogelijkheid Offsite back-up.
Het herstel van AEM Cloud Services voor stadium- en productieomgevingen wordt uitgevoerd door AEM Service Reliability Engineering in het geval van een storing in een gegevensgebied.
