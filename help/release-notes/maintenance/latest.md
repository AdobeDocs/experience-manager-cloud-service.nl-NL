---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a1baa7f29c6e15af11347debdd341f9972c06e83
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 17258 {#release-17258}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 17258 samengevat, die op 30 juli 2024 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 17098.

De activering van de 2024.8.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-17258}

* ASSETS-31445 - Aanvankelijke Dynamic Media-sjabloonfuncties
* ASSETS-40399 - Bijgewerkte DM Auto transcripbe rijmontages
* ASSETS-40873 - Toestaan dat de maximum rijen van de meta-export via OSGI config worden geplaatst

### Opgeloste problemen {#fixed-issues-17258}

* ASSETS-30613 - Asset vervangen verwijdert en voegt geen middel toe in de nieuwe leveringslaag
* ASSETS-31882 - Het is niet toegestaan toegang te krijgen tot het manifestbestand voor streaming in de auteur
* ASSETS-39598 - Bulk Import cannot delete assets with special characters in name from S3 backend
* CNTBF-209 - Verbeteringen voor annulering van back-uptaken
* SCRNS-3762 - Verbeter spelerLogger in het kanaal van de Opeenvolging om logboeken op console te zetten wanneer het voorvertonen van kanaal op browser
* SCRNS-4455 - Ontbrekende &quot;Publicatie beheren&quot; &amp; &quot;Quick Publish&quot;-knop voor gebruikers zonder ADMIN in Content Provider voor kanalen
* SITES-22940 - Kan inhoudsfragment niet weergeven als nuttige werkstroom

### Bekende problemen {#known-issues-17258}

Geen

### Kennisgeving wijzigen {#change-notice-17258}

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [ de documentatie ](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer details.

### Verouderde functies en API&#39;s {#deprecated-17258}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Ingesloten technologieën {#embedded-tech-17258}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 66,0 | [ Oak API 1.66.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING-API | 2.27.2. | [ Apache Sling API 2.27.2 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2,25,4 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
