---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1dd2eae9201c86d2cdac78ff99634eff8ca57a05
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 15860 {#release-15860}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 15860 samengevat, die op 10 april 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 15787.

2024.3.0 Activering van functies biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-15860}

Geen.

### Opgeloste problemen {#fixed-issues-15860}

* Hiermee wordt de regressie voor de weergave van de Launches-console gecorrigeerd wanneer een opstart verwijst naar een verwijderde of verplaatste pagina.

### Bekende problemen {#known-issues-15860}

Geen.

### Verouderde functies en API&#39;s {#deprecated-15860}

* [JWT Credentials Deprection in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Kijk eens naar [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md) om te weten wat in AEM as a Cloud Service is vervangen of verwijderd.

### Kennisgeving wijzigen {#change-notice-15860}

**Handelingen vereist**

#### CM Java-versie instellen op 11 {#set-java-version-11}

De nieuwe versie van aem-sdk-api bevat klassen die met een doel Java 11 worden gecompileerd, die niet compatibel is met de milieu-standaard JDK versie 1.8 van de Manager van de Wolk bouwt. Deze update vereist dat Maven wordt uitgevoerd met JDK 11.

Klanten wordt aangeraden een `.cloudmanager/java-version` bestand naar de hoofdmap van hun waarschuwingsbericht met de inhoud: `11`. Zie [Build Environment / Setting the Maven JDK Version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).


### Ingesloten technologieën {#embedded-tech-15860}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,60-T20240131102219-0cde853 | [API voor eik 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.2.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
