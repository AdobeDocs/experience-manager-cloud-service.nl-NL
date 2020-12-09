---
title: Indexconversie
description: Indexconversie
translation-type: tm+mt
source-git-commit: 1117f03b2eff37f8b25726c3dc60d5a3fe98a5d1
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Indexconverter {#index-converter}

De Omzetter van de index is een nut dat wordt ontwikkeld om de Definities van de Index van een klant voor de overgang naar AEM als Cloud Service te migreren.

## Inleiding {#introduction}

Met de Indexconverter kunnen AEM ontwikkelaars bestaande definities van aangepaste eik-indexen migreren naar AEM als definities van aangepaste eik-indexdefinities die compatibel zijn met Cloud Servicen.

>[!NOTE]
>Indexconverter transformeert alleen *lucene* type Custom Oak Index Definition die aanwezig zijn onder `/apps` of `/oak:index`. Het zet *lucene* type geen indexen om die voor `nt:base` worden gecreeerd.

U kunt op twee manieren aangepaste definities voor eik-indexen maken:

* `under /apps` (via elk aangepast inhoudspakket)
* direct onder pad `/oak:index`

Als [Zorgen dat de eik-index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) is gebruikt, moet u ervoor zorgen dat de definities niet worden ondersteund op AEM als Cloud Service. Daarom moeten ze eerst worden omgezet in de definities van de eik-index en vervolgens worden gemigreerd naar de definities van de aangepaste eik-index die compatibel zijn met AEM als Cloud Service volgens onderstaande richtlijnen:

* Als de eigenschap ignore is ingesteld op `true`, negeert of slaat u de definitie van de functie Zorg aanvullen over
* `jcr:primaryType` bijwerken naar `oak:QueryIndexDefinition`
* Verwijder om het even welke eigenschappen die moeten worden genegeerd zoals vermeld in configuraties OSGi
* Substructuur `/facets/jcr:content` verwijderen uit definitie van verzekeren

## Indexconverter {#using-index-converter} gebruiken

* Via Adobe I/O CLI: Het wordt aanbevolen de indexconverter via `aio-cli-plugin-aem-cloud-service-migration` te gebruiken (AEM als een Cloud Service code refactoring plugin voor de Adobe I/O CLI).

Zie **[Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** voor meer informatie over het installeren en gebruiken van de plug-in.

* Als zelfstandig hulpprogramma: De omzetter van de Index kan ook als standalone nut worden uitgevoerd.

Zie **[Git Resource: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** leren hoe te om dit hulpmiddel te gebruiken.



