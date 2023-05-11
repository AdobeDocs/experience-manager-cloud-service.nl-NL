---
title: Opmerkingen bij de release Cloud Manager 2023.5.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.5.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4340b957cea86452f916ab615b383aabacc21676
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2023.5.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.5.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.5.0 in AEM as a Cloud Service is 11 mei 2023. De volgende release is gepland voor 8 juni 2023.

## Wat is er nieuw? {#what-is-new}

* Ondersteuning voor product-, functionele en UI-tests is uitgebreid tot [niet-productie van pijpleidingen.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
* Naast het inschakelen van stroomopwaartse tests, [Ondersteuning voor UI-tests is uitgebreid tot Cypress-tests.](/help/implementing/cloud-manager/ui-testing.md)
* [Self-service inhoud kopiëren](/help/implementing/developing/tools/content-copy.md) is nu beschikbaar van een hogere naar een lagere omgeving via de interface van Cloud Manager.
* De stap van de de bevestigingsbevestiging van de pijpleidingsuitvoering is verbeterd om de staat van de replicatierijen vroeg in het uitvoeringsproces te bevestigen. Dit zorgt ervoor dat de plaatsingsstappen niet door geblokkeerde rijen worden beïnvloed die door AEM beheerdergebruikers direct in het auteursmilieu zouden moeten worden gericht.

## Opgeloste problemen {#bug-fixes}

* Het maken van omgevingen mislukt niet meer wanneer multi-bytetekens worden gebruikt in de naam van de omgeving.
