---
title: Indexconversie
description: Leer hoe u uw indexdefinities kunt migreren ter voorbereiding op de overgang naar AEM as a Cloud Service.
exl-id: ac02ca41-eb35-4f24-bf17-d00ce318423d
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Indexconversie {#index-converter}

Index Converter is een hulpprogramma dat is ontwikkeld om indexdefinities van een klant te migreren ter voorbereiding op de overgang naar AEM as a Cloud Service.

## Inleiding {#introduction}

Met de Indexconverter kunnen AEM ontwikkelaars bestaande aangepaste Oak-indexdefinities migreren naar met AEM as a Cloud Service compatibele aangepaste Oak-indexdefinities.

>[!NOTE]
>De Omzetter van de index transformeert slechts *lucene* de Definities van de Index van het typeAangepaste Oak die onder `/apps` of `/oak:index` aanwezig zijn. Het transformeert *geen lucene* typeindexen die voor `nt:base` worden gecreeerd.

Er zijn twee manieren om aangepaste Oak-indexdefinities te maken:

* `under /apps` (via een willekeurig aangepast inhoudspakket)
* direct onder `/oak:index` pad

Als [&#x200B; verzekert de Index van Oak &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) werd gebruikt, verzeker de Definities niet op AEM as a Cloud Service worden gesteund. Daarom moeten ze eerst worden omgezet in Oak Index Definition en vervolgens worden gemigreerd naar Custom Oak Index Definition die compatibel zijn met AEM as a Cloud Service, zoals hieronder beschreven:

* Als de eigenschap ignore is ingesteld op `true` , negeert of slaat u de definitie van de functie voor het controleren van de selectie over
* De lus `jcr:primaryType` to `oak:QueryIndexDefinition` bijwerken
* Verwijder om het even welke eigenschappen die moeten worden genegeerd zoals vermeld in configuraties OSGi
* Substructuur `/facets/jcr:content` verwijderen uit definitie van verzekering

## De indexconverter gebruiken {#using-index-converter}

* Als Adobe I/O CLI: Adobe raadt u aan om de indexconverter te gebruiken als `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor de Adobe I/O CLI).

  Zie **[Middel van de Git: ao-cli-stop-aem-wolk-dienst-migratie &#x200B;](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** leren om de stop te installeren en te gebruiken.

* Als standalone nut: De Convertor van de Index kan ook als standalone nut worden uitgevoerd.

  Zie **[Middel van de Git: aem-cs-bron-migratie-index-omzetter &#x200B;](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** leren hoe te om dit hulpmiddel te gebruiken.
