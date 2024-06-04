---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 558babc0124a8ee8c1337b91c5ef016ed238c935
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 16544 {#release-16544}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 16544 samengevat, die op 4 juni 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16461.

2024.6.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie .

### Verbeteringen {#enhancements-16544}

* GRANITE-41133: Ondersteuning voor Jakarta Servlet API 5 en OSGi Servlet Whiteboard API.
* GRANITE-51355: Deprecate org.slf4j.event.
* GRANITE-51565: AEM verliest de lokale groepsrelatie met externe groep wanneer de lokale groep van AEM wordt gepubliceerd.
* GRANITE-51707: Plaats de koekjessaml_request_path tijdens http redirect voor authentificatie.
* GRANITE-52010: Update Jackrabbit version to 2.20.16.
* GRANITE-52057: Werk FileVault bij naar 3.7.3-T20240514105118-694f6aea waarbij JCRVLT-745 wordt gecorrigeerd.
* SKYOPS-35998: Update &quot;Sling RepoInit&quot;gebiedsdelen: Punt Parser 1.9.0 opnieuw, richt JCR 1.1.46.

### Opgeloste problemen {#fixed-issues-16544}

* DXML-17171: AEM Hulplijnen: De kopiëren en plakken-bewerking van onderwerpen groter dan 15KB mislukt met een onverwachte fout.
* DXML-17088: AEM hulplijnen: de functionaliteit om de documentstatus te wijzigen vanuit de **Bestandseigenschappen** werkt niet correct en verandert in het dialoogvenster *Concept* status.
* DXML-16931: AEM Hulplijnen: gekoppelde afbeeldingen van de onderwerpen worden niet weergegeven in de basislijn na het maken van de versie.
* DXML-16896: AEM hulplijnen: in herbruikbare inhoudspanelen worden geen elementen vermeld wanneer de **Gebruikersvoorkeuren** zijn ingesteld op het weergeven van bestanden door **Bestandsnaam**.
* GRANITE-51375: idp-sync werpt NPE als geen middenweg wordt gespecificeerd.

### Bekende problemen {#known-issues-16544}

Geen.

### Verouderde functies en API&#39;s {#deprecated-16544}

Als u wilt weten wat er is vervangen of verwijderd in AEM as a Cloud Service, raadpleegt u [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md).

### Ingesloten technologieën {#embedded-tech-16544}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM | 1 64,0 | [API voor eik 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,25,4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
