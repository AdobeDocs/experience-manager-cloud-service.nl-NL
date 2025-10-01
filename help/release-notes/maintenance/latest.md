---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 8ee3da55024c0f5246f6c194bc07172b4b71823a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 22758 {#22758}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 22758 samengevat, die op 1 oktober 2025 openbaar werd gemaakt. De vorige onderhoudsrelease was release 22450.

De activering van de 2025.10.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-22758}

* ASSETS-56227: noem adobe-countdown-timer wijzigen.
* CNTBF-493: Bump content-backflow bundle versie aan 2.0.28.
* CQ-4361110: Graniet-vertalingen.
* CQ-4361112: Nieuwste AEM-vertalingen.
* GRANITE-56026: Verbeter toestemmings API statuscode reacties.
* GRANITE-61015: `org.apache.commons.io.channels` -pakket toegevoegd aan de openbare geëxporteerde lijst.
* GRANITE-61167: Felix log is bijgewerkt naar de nieuwste OSGI specificaties.
* GRANITE-61167: Update felix afhankelijkheden.
* GRANITE-61169: Verbeter de controle op beschermde koorden.
* GRANITE-61622: Laagafhankelijkheden bijwerken.
* GRANITE-61663: Voeg `com.adobe.granite.repository.indexdefs-1.0.2` toe aan de snelstartprocedure.
* GRANITE-61811: Voeg `com.adobe.granite.repository-2.0.0` toe aan de snelstartprocedure.
* SITES-32014: Luister naar externe gebeurtenissen om de dienstregistraties bij te werken.
* SITES-34277: Oplossing voor een blokkeringsfout in vertaalworkflows voor pagina&#39;s.
* SKYOPS-108706: Met een upgrade van de release schakelt u de bundel in op de nieuwste versie (etag caching).
* SKYOPS-114210: Bijwerken naar de nieuwste versie van aem.pss.service bundle.
* SKYOPS-116171: Update aan Sling ResourceResolver 1.12.12.
* SKYOPS-119811: Uitgegeven verzender-publish 2.0.258.

### Opgeloste problemen {#fixed-issues-22758}

* GRANITE-61875: Fix triggers for &quot;invalid expression evaluation&quot; - Auteurs cannot save Content Fragments &amp; assets failed to download.
* SITES-22059: JS-fout verhelpen in PDF Viewer-componenten. Niet-gelokaliseerde tekenreeks &quot;File preview not available&quot; in Core Components site > PDF Viewer.
* GRANITE-59704: Verbeter htmllibmanager.debug veroorzakend om wijze te ontbreken uit te geven.
* GRANITE-61042: Integreer FELIX-6796 (NPE van ServiceTracker) in de bundel van de Console van het Web van AEM Felix.
* GRANITE-61165: Workspace.copy() genereert RepositoryException.
* GRANITE-61875: Update ui.commons to 5.10.50.

### Bekende problemen {#known-issues-22758}

Geen.

### Verouderde functies en API&#39;s {#deprecated-22758}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [&#x200B; Vervangen en Verwijderde Eigenschappen en APIs &#x200B;](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-22758}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 13 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-22758}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 86,0 | [&#x200B; Oak 1.86.0 API &#x200B;](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| AEM SLING-API | 2,27,6 | [&#x200B; Apache Sling API 2.27.6 API &#x200B;](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [&#x200B; Specificatie van de Taal van het Malplaatje van HTML &#x200B;](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [&#x200B; Apache Httpd 2.4.65 &#x200B;](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2.30.1. | [&#x200B; AEM WCM de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [&#x200B; Ondersteunde versies Node.js &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
