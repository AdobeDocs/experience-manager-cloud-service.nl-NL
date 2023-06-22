---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 46f0f8ba51b328bef1061d574b0d378a510fcf38
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 12255 {#release-12255}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 12255 samengevat, die op 13 juni 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 12142.

Functie-activering voor deze onderhoudsrelease biedt u de volledige functieset met functieactivering 2023.6.0. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-12255}

Geen.

### Opgeloste problemen {#fixed-issues-12255}

- Verschillende updates met betrekking tot toegankelijkheid
- ASSETS-15116 - &quot;Ga naar locatie&quot;-optie beschikbaar in de weergave Middelen zoeken
- ASSETS-17453 - (Dynamic Media) Kan geen aangepaste miniatuur voor video&#39;s selecteren
- ASSETS-19279 - Assets download archive voor grote bestanden
- ACTIVA-19544 - Laatst gewijzigd door gebruiker voor updates van activa
- ASSETS-20146 - (Touch UI) Assets Download Report Failed Reports due to validation errors up always on the top of the list page for reports
- ASSETS-21056 - Optimize Asset Reference Performance to minimize writes
- ASSETS-21909 - Smart crop video kan niet worden weergegeven wanneer de video niet kan worden gedownload
- ASSETS-22261 - LinkShare downloadt de mapstructuur die inconsistent is met het downloaden van de interface Middelen
- ASSETS-22550 - Deelvenster met zoekfilters wordt nu standaard geopend
- ASSETS-22920 - Unpublishing folder from Brand Portal does not mark the assets within as unpublished
- ASSETS-22922 - Uitgeschakelde voorinstellingen van viewer worden weergegeven in de Dynamic Media-component
- ASSETS-23461 - Brand Portal Quick Publish from Assets search view
- ASSETS-23466 - InDesign Server ontoegankelijke koppelingsafhandeling kan AAL-koppelingen met spaties niet oplossen
- ASSETS-23469 - Default Asset Filters botsen met aangepaste filters
- ASSETS-23981 - Sorteerfunctie voor titels die niet werken in verzamelingskoppelingen
- ACTIVA-24723 - Gepubliceerde activa werden opnieuw verwerkt zonder tussenkomst van de gebruiker
- GRANITE-45385 - Boomactivering migreren om een afdruktaak te gebruiken in plaats van een workflow

### Bekende problemen {#known-issues-12255}

- ASSETS-25729 - Het menu Weergave schakelt uit
- ACTIVA-25728 - Optie voor herverwerking van activa niet beschikbaar in de zoekweergave
- ASSETS-22603 - sommige Download-type kolommen van het Rapport van Activa tonen &quot;ongeldige&quot;waarden in UI. Dit heeft geen invloed op downloadbare CSV.

### Ingesloten technologieën {#embedded-tech-12255}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,50-T20230405052634-f9df4aa | [API 1.50.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING-API | Versie 2.27.0 | [API voor Apache Sling API 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.0 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
