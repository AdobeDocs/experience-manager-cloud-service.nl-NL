---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 82be9b2b328343e827b90bd8266d93127757f477
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 17569 {#release-17569}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 17569 samengevat, die op 27 augustus 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 17465.

De activering van de 2024.9.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-17569}

* CQ-4353778: Gebeurtenissen vertaalproces.
* CQ-4354583: Verstuur vertaalprocesgebeurtenissen via Adobe Pipeline.
* CQ-4356479: Alleen Adobe-code toestaan om de /adobe servlet-context te gebruiken.
* CQ-4358133: Jenkins-arbeidersgebruik optimaliseren.
* CQ-4358226: De functionaliteit van het sleutelwoord van de Bewaarvertaling werkt niet voor bepaalde formaat van het Koord.
* CQ-4358270: AEM Vertaalkit: 8 augustus.
* CQ-4358310: Voeg eak-compat-query-spi-1.2 toe aan snelstart.
* GRANITE-36205: Automated update for internal eak release in QS.
* GRANITE-49833: Batching support for event sender and proxy.
* GRANITE-52053: Verwijder het gebruik van Commons Collections 3: Platform anderen.
* GRANITE-52492: Elastische async catchup in geval van PIT-herstel.
* GRANITE-53086: Werk de versie van de jacoco-plug-in bij naar 0.8.12 in AEMaaCS.
* GRANITE-53099: Bijwerken naar Apache Felix HTTP Jetty 5.1.24.
* GRANITE-53125: Voeg classificatie toe aan CloudEvent.
* GRANITE-53328: Werk FileVault bij tot 3.8.0-T20240726111512-3cc11d50 met verbeteringen voor het strepen van logboekregistratie.
* GRANITE-53340: AEM660: correcte versioning en vertakking voor 660 CQ/Platform.
* GRANITE-53341: Let niet op het gebruik van ACS-commons 6.
* GRANITE-53453: update commons-lang tot 3.15.0.
* GRANITE-53473: Instellingen voor onbewerkte verkoop.
* GRANITE-53478: Werk FileVault bij naar versie 3.8.0.
* GRANITE-53505: Werk QS aan commons-collections-3.2.2-adobe-2 bij.
* GRANITE-53528: Update version of platform artifacts.
* GRANITE-53547: Alternatieve API aanbieden om het gebruik van Apache Commons Lang 2 te voorkomen.
* GRANITE-53575: gebruik BSAFE 6.2.5 in CS.
* GRANITE-53608: Update Oak to latest public release (1.68.0).
* SITES-23583: De tests van Evergreen van Sites mislukken op Java 17.
* SKYOPS-79535: Bijwerken naar rum script v2.
* SKYOPS-79816: Laat de Taak van de Analysator van de Eigenschap van de Verkoop voor de Toewijzingen van de Gebruiker van de Dienst in het Hulpmiddel van FEIT toe.
* SKYOPS-81179: AEM bouwt het testen voor bundeltogging.
* SKYOPS-81866: Rapporteer waarschuwingen voor bundels waarvan bekend is dat ze niet compatibel zijn met Java 21.
* SKYOPS-82660: Update Sling API to 2.27.6.
* SKYOPS-82961: Update aan Sling ResourceResolver 1.12.0-T20240723153354-a0270a0.
* SKYOPS-83356: Maak een globaal dashboard voor het bijhouden van JVM-versies die worden gebruikt in AEM implementaties.
* SKYOPS-83436: Java Runtime 21 rollout break creation of adaptive forms AEM Forms.
* SKYOPS-84272: Logboek de Java-versie die bij het opstarten van de aem-lancering wordt gebruikt.

### Opgeloste problemen {#fixed-issues-17569}

* CMGR-60225: uitvoeringsfout van de pijpleiding die bij een AEM Sites CS-klant wordt geïdentificeerd tijdens de validatie van een update naar AEM versie 17486.
* GRANITE-45919: landen waarvoor een embargo geldt in de lijst Land/regio in Gebruikersinstellingen bewerken.
* GRANITE-51715: de kiezer voert de selectie soms niet in het tekstveld in.
* GRANITE-53290: controleer correct het protocol wanneer het ontleden van URL in de controle XSS.
* GRANITE-53576: Verkeerde definitie van de dienstrangschikking in configuraties OSGi.
* SKYOPS-82129: Memoryleak in Sling Models.

### Bekende problemen {#known-issues-17569}

Geen.

### Kennisgeving wijzigen {#change-notice-17569}

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [ de documentatie ](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer details.

### Verouderde functies en API&#39;s {#deprecated-17569}

We zijn bezig met het bijwerken van `com.day.cq.wcm.api` en met de huidige release hebben we een aantal methoden en klassen gemarkeerd als `@Deprecated` . Deze zullen in toekomstige versies worden verwijderd, dus gelieve te overwegen aan hun voorgestelde alternatieven over te schakelen als u om het even welk van hen gebruikt.

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-17569}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 4 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-17569}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 68,0 | [ Oak API 1.68.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2.26.0. | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
