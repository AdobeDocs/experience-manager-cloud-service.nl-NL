---
title: Opmerkingen bij de nieuwste onderhoudsrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de nieuwste onderhoudsrelease [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: edb8949b532b80a55106e706a49e2ada68722a67
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de technische releaserotaties voor de meest recente onderhoudsrelease van as a Cloud Service Experience Manager beschreven.

## Release 11289 {#release-11289}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 11289 samengevat, die op 7 maart 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 10912.

Functie-activering voor deze onderhoudsrelease biedt u de volledige functieset. Zie de [Opmerkingen bij de huidige release](/help/release-notes/release-notes-cloud/release-notes-current.md) voor volledige informatie.

### Bekende problemen {#known-issues}

Voer geen upgrade uit als u CORS gebruikt. Er is een probleem geïdentificeerd dat invloed heeft op de functionaliteit voor het leveren van GraphQL-inhoud. Een wijziging in de standaard AEM dispatcherconfiguratie betreffende hoe GraphQL persisted query&#39;s in de cache worden opgeslagen, kan de levering van GraphQL-inhoud van dergelijke query&#39;s onderbreken. Dit probleem wordt opgelost in onze volgende onderhoudrelease.

### Opgeloste problemen {#fixed-issues}

#### Sites {#sites-issues}

- SITES-11584 Correctie van uitgave met Actieve kopieën die niet kon worden gemaakt voor pagina&#39;s met annotaties
- SITES-11683 Gehandicapte Levende Kopieën MSM met gedeeltelijk gebroken overerving

#### Assets {#assets-issues}

- ASSETS-20879 Vaste regressie om te voorkomen dat de gebruikersinterface voor activarapporten correct werkte en resulteerde in onjuiste resultaten in gegenereerde rapporten.
- ASSETS-21020 Probleem opgelost met gedownloade middelen - Afbeeldingsprofiel bestaat niet na het verplaatsen van middelen
- ASSETS-21023 Correctie van het probleem met afbeeldingsuitvoeringen in Dynamic Media waardoor toegang via de API werd voorkomen

#### Forms {#forms-issues}

- Geen

#### Platform {#platform-issues}

- GRANITE-44467 - Het probleem dat ertoe leidde dat het importeren mislukte, bij het bijwerken van een bestaand knooppunt, bleef FileVault onder bepaalde instanties de typen en onderliggende knooppunten niet in evenwicht.

### Ingesloten technologieën {#embedded-tech}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,44-T20221206170501-6d59064 | [API 1.44.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Versie 2.27.0 | [API voor Apache Sling API 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.21.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
