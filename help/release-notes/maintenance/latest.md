---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6884e33a922a7147e3a6a3f3ddb3dd3b2da85fbf
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 21005 {#21005}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 21005 samengevat, die op 27 mei 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 20626.

De activering van de 2025.5.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-21005}

* GRANITE-58927: Verbeteringen in de schakeloptie Semantische zoekopdracht.
* GRANITE-58800: Update of Apache Commons Collections to version 4.5.0.
* GRANITE-58866: Bijwerking van Oak tot 1.80.0.
* SKYOPS-106509: Verbeterde GSON-compatibiliteit via reflectieve toegang in Java 21.
* SKYOPS-107761: Update of Sling Models Jackson Exporter to 1.1.6.
* SKYOPS-107813: Update aan Sling ResourceResolver 1.12.8.

### Opgeloste problemen {#fixed-issues-21005}

* CNTBF-443: Fixed SearchSlingJob `EVENT_JOB_TOPIC` -eigenschap.
* GRANITE-57853: Opgeloste problemen met uitlijning van vervolgkeuzelijsten in UI.
* GRANITE-58107: Vaste 404 fouten op Publish door op gebruiker-gebaseerde podaffiniteit in manager uit te schakelen OAuth.
* GRANITE-58276, SLING-12755: Vaste OSGi gebiedscycli die de fabriek van de Motor van het Manuscript van HTML konden verhinderen correct te beginnen, veroorzakend periodiek server-zijteruggevende fouten.
* SKYOPS-105151: Vaste NPE bij de toegang tot van bundellijst.
* SKYOPS-83910, SKYOPS-82371 - Vaste JSP-compilatieproblemen.

#### AEM Guides {#guides}

* GUIDEN-26919: Wanneer het openen van een kaart DITA met verenigde toegelaten shell, verandert de redacteur af en toe.
* GUIDEN-26282: Het niet sluiten van JCR zittingsverbindingen terwijl het bijwerken van of het creëren van onderwerpen in geheugenlekken en de dienstonderbreking resulteren.
* GUIDES-26434: Native PDF-publicatie gaat eindeloos door als de DITA-inhoud een webkoppeling heeft zonder bereik als `external` .
* GUIDEN-26516: Het publiceren van inheemse PDFs en de plaatsen van AEM stallen en wordt een rij gevormd, wanneer er fouten in de inhoud zijn.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-21005}

Geen.

### Verouderde functies en API&#39;s {#deprecated-21005}

* GRANITE-54164: Verwijderd `org.apache.jackrabbit.oak.plugins.blob` uit openbare API.
* GRANITE-54280: Verwijderd `org.apache.jackrabbit.oak.cache` uit openbare API.
* GRANITE-58332: Vervangen `org.apache.jackrabbit.oak.plugins.memory` in openbare API.
* YUI-compressor voor javascript is vervangen.
* De ](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) functionaliteit van de Automatisering van de Opstelling van 0} Experience Cloud is afgekeurd.[

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-21005}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 5 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Kennisgeving wijzigen {#change-notice-21005}

* Deze versie bevat de volgende nieuwe versies van de productindex:
   * **damAssetLucene-12**

Aangepaste versies van de vorige indexversies worden automatisch samengevoegd met de nieuwe versie van de productindex. Pas verdere aangepaste updates toe op de samengevoegde versie.

#### Aem-cloud-testing-clients bijwerken {#update-aem-cloud-testing-clients-21005}

De aanstaande veranderingen zullen de bibliotheek [ aem-wolk-test-cliënten ](https://github.com/adobe/aem-testing-clients) vereisen die in uw douane functionele tests worden gebruikt om aan minstens versie **1.2.1** worden bijgewerkt (geadviseerd: recentste versie 1.2.9)

Controleer of uw afhankelijkheid in `it.tests/pom.xml` is bijgewerkt.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.9</version>
</dependency>
```

Deze wijziging moet vóór 15 juni 2025 worden uitgevoerd.
Als u er niet in slaagt de afhankelijkheidsbibliotheek bij te werken, treedt er een fout op bij de stap Aangepast functioneel testen.

### Ingesloten technologieën {#embedded-tech-21005}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 80,0 | [ Oak API 1.80.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
