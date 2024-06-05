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

De Omzetter van de index is een nut dat wordt ontwikkeld om de Definities van de Index van een klant voor de overgang naar AEM as a Cloud Service te migreren.

## Inleiding {#introduction}

Met de indexconverter kunnen AEM ontwikkelaars bestaande definities van aangepaste eik-indexen migreren naar AEM as a Cloud Service compatibele definities van aangepaste eik-indexen.

>[!NOTE]
>Alleen transformaties voor indexconversie *luceen* Type Custom Oak Index-definities die aanwezig zijn onder `/apps` of `/oak:index`. Het verandert niet *luceen* type-indexen waarvoor `nt:base`.

U kunt op twee manieren aangepaste definities voor eik-indexen maken:

* `under /apps` (via elk aangepast inhoudspakket)
* rechtstreeks onder `/oak:index` pad

Indien [Oak-index controleren](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) is gebruikt, controleer of Definities niet worden ondersteund voor AEM as a Cloud Service. Als dusdanig moeten zij eerst in de Definities van de Index van het Eak worden omgezet, en dan gemigreerd aan de Definities van de Index van de Eik van de Douane die met AEM as a Cloud Service, zoals hieronder richtlijnen compatibel zijn:

* Als eigenschap ignore is ingesteld op `true`, negeren of overslaan van de definitie van de verzekerde
* Werk de `jcr:primaryType` tot `oak:QueryIndexDefinition`
* Verwijder om het even welke eigenschappen die moeten worden genegeerd zoals vermeld in configuraties OSGi
* Substructuur verwijderen `/facets/jcr:content` vanaf definitie van Zorg

## De indexconverter gebruiken {#using-index-converter}

* Als Adobe I/O CLI: Adobe raadt u aan de indexconverter te gebruiken als `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor de Adobe I/O CLI).

  Zie **[Git-bron: audio-cli-plugin-aem-cloud-service-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** voor informatie over het installeren en gebruiken van de plug-in.

* Als standalone nut: De Convertor van de Index kan ook als standalone nut worden uitgevoerd.

  Zie **[Git Resource: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** voor meer informatie over het gebruik van dit gereedschap.
