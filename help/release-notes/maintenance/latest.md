---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 1d6a54f87d55179c11c7ccc7766eeeb475674f05
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 19567 {#19567}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 19567 samengevat, die op 18 februari 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 19352.

De activering van de 2025.2.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-19567}

* GRANITE-56650: De distributie van de inhoud zou geblokkeerde rij na een paar herpogingen slechts moeten signaleren
* SKYOPS-89616: toestaan om maximaal 40 technische accounts te maken in Adobe Developer Console

### Opgeloste problemen {#fixed-issues-19567}

* CNTBF-232: Deep package nt:file nodes to include mandatory jcr:content child
* CQ-4358930: Prestatieprobleem tijdens laden van pagina-eigenschappen met veel multifields
* GRANITE-55960: Prestatieprobleem met Coral Select Field op AEM als Cloud Service
* GRANITE-56197: De nieuwe de werkschemastap TreeActivation bewaart geen activa in grote vlakke omslagstructuur

#### AEM Guides {#guides}

* GUIDEN-23526: Wanneer het bijwerken van voorwaarden van het omslagprofiel, alle voorwaardengroepen worden verloren en de voorwaarden worden afgevlakt.
* GUIDEN-22574: Als een externe verbinding een UUID bevat, gaat het in postverwerking en zet de externe verbinding aan verbinding UUID daardoor om de verbinding op redacteur en ook op de het publiceren plaatsen te breken.
* GUIDEN-24983: Wanneer het kopiëren van een beeld van om het even welk extern product (bijvoorbeeld, MS PowerPoint) en het kleven van het in Gidsen, de functionaliteit om de activa te uploaden op de vlucht voor gebruik in de dossieronderbrekingen.
* HULPLIJNEN-21772: De inheemse generatie van PDF ontbreekt voor inhoud met **brokkenattribuut** die aan **wordt geplaatst aan-inhoud**.
* HULPLIJNEN-23964: Wanneer het kiezen van **geeft eigenschappen** uit, toont de basislijndialoog niet de eerder bewaarde criteria voor dynamische basislijn.
* GUIDEN-19067: Wanneer u een mapprofiel dupliceert, wordt de bijbehorende lijst met gebruikers ook gekopieerd uit het oorspronkelijke mapprofiel

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-19567}

Geen.

### Verouderde functies en API&#39;s {#deprecated-19567}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-19567}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 21 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-19567}

| Technologie | Versie | Koppeling |
|---|--------------|-------------------------------------------------------------------------------------------------------------------|
| AEM Oak | 1 76,0 | [ Oak API 1.76.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.26-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 27,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
