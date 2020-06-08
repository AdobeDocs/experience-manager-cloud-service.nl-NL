---
title: Back-up en herstel in AEM als cloudservice
description: 'Back-up en herstel in AEM als cloudservice '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 1%

---


# Back-up en herstel in AEM als cloudservice

Als er inhoud of gegevensbeschadiging optreedt, kan AEM als cloudservice de volledige toepassing (code en inhoud) van een klant herstellen op specifieke, vooraf bepaalde tijdstippen in de laatste zeven dagen, ter vervanging van wat er in productie was.
Als de plaatsing van een klant, die de opgestelde toepassingscode betekent of gebroken of knecht is, is het verkieslijk om het te bevestigen en naar een nieuwe versie vooruit te rollen eerder dan het van steun te herstellen.

>[!CAUTION]
>
>Deze functie moet alleen worden gebruikt bij ernstige problemen met code of inhoud. De recente gegevens tussen het tijdstip van de herstelde back-up en het moment waarop deze wordt gemaakt, gaan verloren. Het opvoeren zal ook aan de oude versie worden hersteld.

## Het gebruik

Klanten dienen een ondersteuningsticket in te dienen waarin het probleem wordt beschreven dat zich voordoet. Dit zal leiden tot een onderzoek door de Steun van Adobe die zal bepalen als herstelt noodzakelijk is.

AEM als cloudservice ondersteunt:

* 24-uurs herstel, wat betekent dat het systeem in de laatste 24 uur op elk punt kan worden hersteld.
* Herstel van een specifieke, door Adobe gedefinieerde tijdstempel die éénmaal per dag wordt genomen gedurende de laatste 7 dagen.  Alle replicatieberichten (verwijderen, bijwerken, maken) blijven behouden.

In alle gevallen, zal de versie van de douanecode van de laatste succesvolle plaatsing vóór het terugzetpunt worden genomen.

De doelstelling van de hersteltijd (RTO) zal variëren afhankelijk van de grootte van de opslagplaats, maar als algemene richtlijn zou het ongeveer 30 minuten duren als de herstelvolgorde eenmaal is gestart.

Na een terugzetbewerking wordt de AEM-versie bijgewerkt naar de meest recente.

**De gegevens uit verwijderde omgevingen gaan permanent verloren en kunnen niet worden hersteld.**
