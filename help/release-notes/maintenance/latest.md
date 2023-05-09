---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: ea3a476f7f2d7d97a2428c6facf61b746dba7a23
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 2%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 11873 {#release-11873}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 11873 samengevat, die op 3 mei 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 11835.

Functie-activering voor deze onderhoudsrelease biedt u de volledige functieset. Zie de [Opmerkingen bij de huidige release](/help/release-notes/release-notes-cloud/release-notes-current.md) voor volledige informatie.

### Verbeteringen {#enhancements}

- SITES-1200 - API-verbeteringen doorzoeken met filteren op basis van tags
- GRANITE-42939 - Voeg afbrekingsannotaties en waarschuwingen toe aan code op de server van de server

### Bekende problemen {#known-issues-11873}

Geen.

### Opgeloste problemen {#fixed-issues-11873}

- SKYSI-1984/SKYOPS-53745 - Het probleem is opgelost met PublishPageRenderingErrorsHigh
- GRANITE-4388 - Vaste de productiedaling na groot aantal DAM asset-writes op Mongo
- SITES-11922 - Correctie van probleem waarbij de publicatie uit de voorvertoning werd ongedaan gemaakt en de synchronisatiestatus niet werd verwijderd
- ACTIVA-21648 - Vaste machtigingskwestie met de functie Relate van activa

### Ingesloten technologieën {#embedded-tech-11873}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,44-T20221206170501-6d59064 | [API 1.44.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Versie 2.27.0 | [API voor Apache Sling API 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.21.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
