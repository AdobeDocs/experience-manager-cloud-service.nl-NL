---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 241dcc75e9f2c840be85c34800d8145457baa58d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 12697 {#release-12697}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 12697 samengevat, die op 14 juli 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 12549. Onderhoudsrelease 12697 vervangt 12585 om één probleem op te lossen.

2023.7.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-12697}

- Algemene verbeteringen in de RDE-stabiliteit (SKYOPS-61133, SKYOPS-55281, SKYOPS-61216 en SKYOPS-61401)
- DXML-12327: Hulplijnen AEM: Ondersteuning voor taalvariabelen in publicaties met eigen PDF
- DXML-11518: Hulplijnen AEM: Verbeterde ondersteuning voor metagegevens in Native PDF-publicaties
- DXML-10093: Hulplijnen AEM: Steun voor het verbinden met externe gegevensbronnen en het opnemen van gegevens in dita onderwerpen
- DXML-10699: Hulplijnen AEM: Ondersteuning voor XLIFF-indeling in vertaling
- DXML-10141: Hulplijnen AEM: Optie voor het gebruik van op microservices gebaseerde publicaties voor de typen PDF (native en DITA-OT), HTML en Aangepaste voorinstellingen
- SKYOPS-61385 - Update de verzender om libpcre2 te gebruiken wanneer het evalueren van regelmatige uitdrukkingen in Apache HTTPD

### Opgeloste problemen {#fixed-issues-12697}

- Hulplijnen AEM: Verschillende correcties voor Native PDF
- SKYOPS-53130: Verbeterde ondersteuning voor wisselstroomgereedschappen in RDE
- SKYOPS-57146: Blokkering bij AEM opstarten verhelpen

### Bekende problemen {#known-issues-12697}

Geen.

### Ingesloten technologieën {#embedded-tech-12697}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,52-T20230629133256-25c01b8 | [API 1.52.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.0 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
