---
title: Indexconversie
description: Indexconversie
translation-type: tm+mt
source-git-commit: 21bd9392d913369a5e8e0ebd9badbbe30fd4bba3
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Indexconverter {#index-converter}

Index Converter is een hulpprogramma dat is ontwikkeld om de indexdefinitie van een klant te migreren ter voorbereiding op de overgang naar AEM als Cloud Service.

## Inleiding {#introduction}

Met de Indexconverter kunnen AEM ontwikkelaars bestaande aangepaste ak-indexdefinities migreren naar AEM als met Cloud Servicen compatibele Custom Oak Index-definities.

>[!NOTE]
>Indexconverter transformeert alleen *lucene* type Custom Oak Index Definition die aanwezig zijn onder `/apps` of `/oak:index`. Het zet *lucene* type geen indexen om die voor `nt:base` worden gecreeerd.

## Indexconverter {#using-index-converter} gebruiken

Zie **[Git Resource: aem-cs-source-migration-index-converter](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** om te leren hoe u de plug-in installeert en gebruikt.

