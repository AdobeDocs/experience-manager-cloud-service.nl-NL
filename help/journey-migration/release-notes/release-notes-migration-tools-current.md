---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2023.06.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.06.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: a1597e4102589dfc9b5bdb8c2a54e8e9ec3392b7
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 2%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2023.06.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.06.0.

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v2.0.20 is 8 juni 2023.

### Wat is er nieuw? {#what-is-new-ctt}

* Een nieuw migratiehulpmiddel - de Transformator van de Inhoud (CT) is geïntegreerd met het Hulpmiddel van de Overdracht van de Inhoud (CTT) met deze versie. De Content Transformer kan automatisch problemen met betrekking tot inhoud die door de [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en) voordat u inhoud migreert van uw huidige AEM-implementatie (On-premise of Managed Services) naar AEM as a Cloud Service.
De contenttransformator biedt de volgende voordelen:
   * Misveilig: er wordt een pakket gemaakt door de Content Transformer telkens wanneer er wijzigingen in de opslagplaats worden aangebracht om problemen op te lossen. Indien nodig kunt u terugkeren naar de vorige status door het pakket te installeren.
   * Gebruiksvriendelijk: De Content Transformer is geïntegreerd met het Content Transfer Tool en wordt geleverd met een eenvoudige gebruikersinterface die intuïtief is.
   * Hiermee bespaart u tijd: wanneer u een groot aantal inhoudsproblemen hebt die onder één patrooncategorie vallen, kunt u ze allemaal oplossen met slechts een paar klikken met de Content Transformer, waardoor de tijd en migratie aanzienlijk afnemen.
