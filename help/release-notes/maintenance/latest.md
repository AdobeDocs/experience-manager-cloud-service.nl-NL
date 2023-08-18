---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: cf8b5d8b11452268b2839053c1e05cc2ec107a91
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 2%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13173 {#release-13173}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13173 samengevat, die op 18 augustus 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 13099.

2023.8.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13173}

Geen.

### Opgeloste problemen {#fixed-issues-13173}

- SITES-15463: Sitesjablonen - Sjablonen kunnen niet worden gepubliceerd.

### Bekende problemen {#known-issues-13173}

- SITES-15359: Inhoudsfragmenten - Het patroon van de variatienaam komt niet correct overeen met variaties die ```'_'``` in hun resourceramen.
- FORMS-10444: Adaptieve Forms-sjablonen - Sjablonen kunnen niet worden gepubliceerd (tijdelijke oplossing: distributieconsole gebruiken).
- CQ-4354191: Workflows - Aangepaste opstartcher kan vele malen worden geactiveerd vanwege replicatiemetagegevens die aanwezig zijn op nt:ungestructureerde knooppunten (workaround: updatedetectoren om eigenschappen van replicatiemetagegevens uit te sluiten om overlapping te voorkomen).

### Ingesloten technologieën {#embedded-tech-13173}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,52-T20230629133256-25c01b8 | [API 1.52.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
