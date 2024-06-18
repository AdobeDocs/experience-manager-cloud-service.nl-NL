---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e0156c54b51eed0f729f2026c47eb93917143017
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 16799 {#release-16799}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 16799 samengevat, die op 18 juni 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 16544.

2024.6.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie .

### Verbeteringen {#enhancements-16799}

* ASSETS-31977: Verbeterde activiteiten voor het verplaatsen, kopiëren en verwijderen van bedrijfsmiddelen.
* ASSETS-33618: automatische transcriptie- en vertaalmogelijkheden voor video&#39;s in Dynamic Media.
* ASSETS-33618: Approval Action for ContentHub and DM and add properties to damAssetLucene properties.
* ASSETS-35533: Voeg DRM- en CAI-eigenschappen toe aan damAssetLucene-index.
* ASSETS-37280: Opeenvolgende taakafhandeling voor vertaling wanneer bronondertitel (vtt) nog steeds wordt verwerkt.
* ASSETS-37559: gebeurtenis Improved asset deleted.
* ASSETS-37723: Implementeer activa gepubliceerde gebeurtenis.
* ASSETS-37724: Implementeer activa niet-gepubliceerde gebeurtenis.
* ASSETS-38614: de verhogingen van de Verbinding van het aandeel UI.
* ASSETS-39601: pas validatieregex automatisch toe op de naam van de Asset Livecopy.
* ASSETS-39454: Upgrade to viewers 2024.5.0 in QuickStart.
* CNTBF-184: Onderliggende steunpaden `/conf` in Content Backflow.

### Opgeloste problemen {#fixed-issues-16799}

* ASSETS-37335: als u het deelvenster Zoeken in filter bewerkt, worden alle vakken uitgeschakeld.
* ASSETS-38069: AEM DAM-probleem met de voorvertoning van de PDF bij de selectie van de tijdlijnfilter.
* ASSETS-38215: Adobe Stock-licentieknop wordt weergegeven in AEM as a Cloud Service voor Enterprise-abonnement.
* ASSETS-38578: Onjuiste hyperlinks in het rapport voor het delen van middelenkoppelingen.
* ASSETS-38678: weergave-instellingen verbroken in Gegevens verzameling.
* ASSETS-39071: Voor het web geoptimaliseerde levering kan een uitzondering genereren als het oorspronkelijke renditiematype null is.
* ASSETS-39316: Sorteren op naam werkt niet in verzamelingen.
* ASSETS-39377: Bulk-import van OneDrive kan mislukken bij het ontvangen van backpressure van externe API.
* ASSETS-39428: Rendering issues in Copyright Management UI.
* CQ-4357150: Guava in cq-content-sync-bundel.
* SCRNS-4194: Verwijder afhankelijkheid van Google Guava API&#39;s.
* SCRNS-4360: Ontbrekende Manage Publication &amp; Quick Publish Knoop voor niet-admin gebruikers in Inhoudsleverancier voor Kanalen.
* SCRNS-4323: Verberg/maak lanceringen van screens.html onbruikbaar.

### Bekende problemen {#known-issues-16799}

Geen.

### Kennisgeving wijzigen {#change-notice-16799}

* Deze versie bevat de volgende nieuwe versies van de productindex:
   * **damAssetLucene-11**
   * **fragmenten-11**

  Aangepaste versies van de vorige indexversies worden automatisch samengevoegd met de nieuwe versie van de productindex. Pas verdere aangepaste updates toe op de samengevoegde versie.

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [de documentatie](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer informatie .

### Verouderde functies en API&#39;s {#deprecated-16799}

Als u wilt weten wat er is vervangen of verwijderd in AEM as a Cloud Service, raadpleegt u [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md).

### Ingesloten technologieën {#embedded-tech-16799}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM | 1 64,0 | [API voor eik 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2. | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2,25,4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
