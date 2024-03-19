---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: dbdc63db9a9ac954ce6359d3643231d6e195fd53
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 15575 {#release-15575}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 15575 samengevat, die op 19 maart 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 15262.

2024.3.0 Activering van functies biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-15575}

Geen.

### Opgeloste problemen {#fixed-issues-15575}

* ASSETS-36358: Upload Report cannot be rendered.
* GRANITE-50774: GraniteContent zou deterministische orde van bezit-waarden op init tijd moeten gebruiken.

### Bekende problemen {#known-issues-15575}

Geen.

### Kennisgeving wijzigen {#change-notice-15575}

**Handelingen vereist**

#### CM Java-versie instellen op 11 {#set-java-version-11}

De nieuwe versie van aem-sdk-api bevat klassen die met een doel Java 11 worden gecompileerd, die niet compatibel is met de milieu-standaard JDK versie 1.8 van de Manager van de Wolk bouwt. Deze update vereist dat Maven wordt uitgevoerd met JDK 11.

Klanten wordt aangeraden een `.cloudmanager/java-version` bestand naar de hoofdmap van hun waarschuwingsbericht met de inhoud: `11`. Zie [Build Environment / Setting the Maven JDK Version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).

#### Aem-cloud-testing-clients bijwerken naar 1.2.1 {#update-aem-cloud-testing-clients}

Voor komende wijzigingen is de bibliotheek vereist [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) gebruikt in uw aangepaste functionele tests die moeten worden bijgewerkt naar ten minste versie **1.**

Zorg ervoor dat uw afhankelijkheid binnen `it.tests/pom.xml` is bijgewerkt.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Deze wijziging moet worden uitgevoerd vóór 6 april 2024.

Als u er niet in slaagt de afhankelijkheidsbibliotheek bij te werken, treedt er een fout op bij de stap Aangepast functioneel testen.

### Ingesloten technologieën {#embedded-tech-15575}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,60-T20240131102219-0cde853 | [API voor eik 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
