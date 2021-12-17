---
title: Indexconversie
description: Indexconversie
source-git-commit: a6d225943c5d23ebd960fda0b0912a81f1f80014
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Indexconversie {#index-converter}

De Omzetter van de index is een nut dat wordt ontwikkeld om de Definities van de Index van een klant voor de overgang naar AEM as a Cloud Service te migreren.

## Inleiding {#introduction}

Met de indexconverter kunnen AEM ontwikkelaars bestaande definities van aangepaste eik-indexen migreren naar AEM as a Cloud Service compatibele definities van aangepaste eik-indexen.

>[!NOTE]
>Alleen transformaties voor indexconversie *luceen* Type Custom Oak Index-definities die aanwezig zijn onder `/apps` of `/oak:index`. Het verandert niet *luceen* type-indexen waarvoor `nt:base`.

U kunt op twee manieren aangepaste definities voor eik-indexen maken:

* `under /apps` (via elk aangepast inhoudspakket)
* rechtstreeks onder `/oak:index` pad

Indien [Oak-index controleren](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) Er is gebruik van gemaakt. Zorg ervoor dat de definities niet worden ondersteund op AEM as a Cloud Service, en daarom moeten ze eerst worden omgezet in de definities van de eiken-indexen en vervolgens worden gemigreerd naar de definities van de aangepaste eik-index die compatibel zijn met AEM as a Cloud Service volgens onderstaande richtlijnen:

* Als eigenschap ignore is ingesteld op `true`, negeren of overslaan van de definitie van de verzekerde
* Werk de `jcr:primaryType` tot `oak:QueryIndexDefinition`
* Verwijder om het even welke eigenschappen die moeten worden genegeerd zoals vermeld in configuraties OSGi
* Substructuur verwijderen `/facets/jcr:content` vanaf definitie van Zorg

## De indexconverter gebruiken {#using-index-converter}

* Via Adobe I/O CLI: U wordt aangeraden de indexconverter te gebruiken via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor de Adobe I/O CLI).

   Zie **[Git-bron: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** voor informatie over het installeren en gebruiken van de plug-in.

* Als zelfstandig hulpprogramma: De omzetter van de Index kan ook als standalone nut worden uitgevoerd.

   Zie **[Git-bron: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** voor meer informatie over het gebruik van dit gereedschap.
