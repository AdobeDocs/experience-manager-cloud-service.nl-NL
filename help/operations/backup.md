---
title: Back-up en herstel in AEM als Cloud Service
description: 'Back-up en herstel in AEM als Cloud Service '
translation-type: tm+mt
source-git-commit: c3af507716ef60541ecca8dafb797651e8ece9d3
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Back-up en herstel in AEM als Cloud Service

Mocht inhoud of gegevenscorruptie voorkomen, AEM als Cloud Service de volledige toepassing van een klant (code en inhoud) aan specifieke, vooraf bepaalde tijden in de laatste zeven dagen kan herstellen, die wat op productie was vervangen.
Als de plaatsing van een klant, die de opgestelde toepassingscode betekent of gebroken of knecht is, is het verkieslijk om het te bevestigen en naar een nieuwe versie vooruit te rollen eerder dan het van steun te herstellen. Back-up wordt uitgevoerd op een manier die geen invloed heeft op de prestaties tijdens de uitvoering van een toepassing.

>[!CAUTION]
>
>Deze functie moet alleen worden gebruikt bij ernstige problemen met code of inhoud. De recente gegevens tussen het tijdstip van de herstelde back-up en het moment waarop deze wordt gemaakt, gaan verloren. Het opvoeren zal ook aan de oude versie worden hersteld.

## Het gebruik

Klanten dienen een ondersteuningsticket in te dienen waarin het probleem wordt beschreven dat zich voordoet. Dit zal leiden tot een onderzoek door Adobe support, die zal bepalen of een herstel nodig is.

AEM als Cloud Service ondersteunt:

* 24-uurs herstel, wat betekent dat het systeem in de laatste 24 uur op elk punt kan worden hersteld.
* Herstel van een specifieke, door Adobe gedefinieerde tijdstempel die eenmaal per dag is genomen gedurende de laatste 7 dagen.  Alle replicatieberichten (verwijderen, bijwerken, maken) blijven behouden.

In alle gevallen, zal de versie van de douanecode van de laatste succesvolle plaatsing vóór het terugzetpunt worden genomen.

De doelstelling van de hersteltijd (RTO) zal variëren afhankelijk van de grootte van de opslagplaats, maar als algemene richtlijn zou het ongeveer 30 minuten duren als de herstelvolgorde eenmaal is gestart.

Na een terugzetbewerking wordt de AEM versie bijgewerkt naar de meest recente.

**De gegevens uit verwijderde omgevingen gaan permanent verloren en kunnen niet worden hersteld.**
