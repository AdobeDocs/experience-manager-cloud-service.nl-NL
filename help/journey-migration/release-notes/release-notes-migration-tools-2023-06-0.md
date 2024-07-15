---
title: Opmerkingen bij de release AEM as a Cloud Service 2023.06.0 voor migratiehulpprogramma's
description: Opmerkingen bij de release AEM as a Cloud Service 2023.06.0 voor migratiehulpprogramma's
feature: Release Information
exl-id: 021b7472-d1e4-4ef6-a040-c612fed8d3c3
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Opmerkingen bij de release AEM as a Cloud Service 2023.06.0 voor migratiehulpprogramma&#39;s {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2023.06.0.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v2.0.20 is 8 juni 2023.

### Wat is er nieuw? {#what-is-new-ctt}

* Een nieuw migratiehulpmiddel - de Transformator van de Inhoud (CT) is geïntegreerd met het Hulpmiddel van de Overdracht van de Inhoud (CTT) met deze versie. De transformator van de Inhoud kan inhoud gerelateerde kwesties automatisch ontdekken en bevestigen die door de [ Analysator van Beste praktijken (BPA) ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html) worden gemeld alvorens inhoud van uw huidige AEM implementatie (On-premise of Managed Services) aan AEM as a Cloud Service te migreren.
De contenttransformator biedt de volgende voordelen:
   * Niet-veilig: een pakket wordt gemaakt door de Content Transformer telkens wanneer de opslagplaats wijzigingen aanbrengt om problemen op te lossen. Indien nodig kunt u terugkeren naar de vorige status door het pakket te installeren.
   * Eenvoudig te gebruiken: de Inhoudstransformer is geïntegreerd met het gereedschap Inhoudsoverdracht en wordt geleverd met een eenvoudige, intuïtieve gebruikersinterface.
   * Bespart tijd: wanneer u veel inhoudsproblemen hebt die onder één patrooncategorie vallen, kunt u deze allemaal oplossen met meerdere klikken met de Content Transformer, waardoor de tijd en migratie aanzienlijk afnemen.
