---
title: Opmerkingen bij de release Cloud Manager 2023.9.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.9.0 in AEM as a Cloud Service.
feature: Release Information
source-git-commit: dd52aef2f88cf64e8d9a32b1c8cafe4fcfbcb812
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2023.9.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.9.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.9.0 in AEM as a Cloud Service is 7 september 2023. De volgende release is gepland voor 5 oktober 2023.

## Wat is er nieuw? {#what-is-new}

Deze release is gericht op opgeloste problemen.

## Programma voor vroegtijdige adoptie {#early-adoption}

Maak deel uit van ons programma voor vroegtijdige goedkeuring en heb de kans om een aantal van de komende kenmerken te testen.

### Self-Service inhoud herstellen {#content-restore}

[Een nieuwe functie voor het terugzetten van selfservice-inhoud](/help/operations/restore.md) biedt nu back-upherstel voor maximaal zeven dagen en is beschikbaar voor vroege gebruikers voor evaluatiedoeleinden met:

* Point-in-time back-upherstel voor de voorgaande 24 uur
* Herstel van vaste tijd tot zeven dagen

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `aemcs-restorefrombackup-adopter@adobe.com` van uw e-mail die aan uw Adobe ID is gekoppeld. Opmerking:

* Het programma voor vroege adoptie is beperkt tot ontwikkelomgevingen.
* De beschikbaarheid van het programma voor vroege adoptie van deze functie is beperkt.
* Deze functie is bedoeld om per ongeluk verwijderde inhoud te herstellen en is niet bedoeld voor noodherstel.

### Experience Audit Dashboard {#experience-audit-dashboard}

[Cloud Manager Experience Audit-dashboard](/help/implementing/cloud-manager/experience-audit-dashboard.md) bevat een trendweergave van de prestatiesscores van uw pagina, samen met inzichten en aanbevelingen om u te helpen deze te verbeteren. Experience Audit is opgenomen als een stap in de productiepijplijn van Cloud Manager.

Het dashboard maakt gebruik van Google Lighthouse, een opensource, geautomatiseerd programma voor het verbeteren van de kwaliteit van uw webapps. U kunt het tegen om het even welke Web-pagina in werking stellen, openbaar of het vereisen van authentificatie. Er zijn audits voor prestaties, toegankelijkheid, progressieve webapps, SEO en meer.

Geïnteresseerd in het testen van het nieuwe dashboard? Stuur een e-mail naar `aem-lighthouse-pilot@adobe.com` via je e-mail die aan je Adobe ID is gekoppeld. We kunnen je aan de slag.

## Opgeloste problemen {#bug-fixes}

* Wanneer een programma wordt geschrapt, wordt om het even welke bijbehorende, lopende pijpleiding ook geschrapt, die ervoor zorgen dat de pijpleiding niet verkeerd als ontbroken status wordt aangewezen.
* Af en toe, wanneer alle stappen van een pijpleidingsuitvoering &quot;voltooid&quot;zijn, wordt de status van de pijpleiding beschouwd als &quot;lopend&quot;, die het schijnen in een vastgelopen staat te zijn. Het wordt nu beschouwd als een &#39;complete&#39;.
* Voor bewaarplaatsaftakkingen die gebruikend het archetype van de codegenerator worden geproduceerd, ontbreekt de pijpleiding van CI/CD.
