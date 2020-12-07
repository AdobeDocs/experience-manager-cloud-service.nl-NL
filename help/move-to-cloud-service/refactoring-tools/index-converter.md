---
title: Indexconversie
description: Indexconversie
translation-type: tm+mt
source-git-commit: adfc453729b88a9cc457783806eb7b4d69150b21
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# Indexconverter {#index-converter}

Index Converter is een hulpprogramma dat is ontwikkeld om de indexdefinitie van een klant te migreren ter voorbereiding op de overgang naar AEM als Cloud Service.

## Inleiding {#introduction}

Met de Indexconverter kunnen AEM ontwikkelaars bestaande aangepaste ak-indexdefinities migreren naar AEM als met Cloud Servicen compatibele Custom Oak Index-definities.

>[!NOTE]
>Indexconverter transformeert alleen *lucene* type Custom Oak Index Definition die aanwezig zijn onder `/apps` of `/oak:index`. Het zet *lucene* type geen indexen om die voor `nt:base` worden gecreeerd.

U kunt op twee manieren aangepaste definities voor eik-indexen maken:

* `under /apps` (via elk aangepast inhoudspakket)
* direct onder pad `/oak:index`

>[!NOTE]
>Verwijs naar [Zorgt voor eik-index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) om te leren hoe u eik-definities definieert en maakt

## Indexconverter {#using-index-converter} gebruiken

>[!NOTE]
>Het wordt aangeraden het gereedschap Index-converter te gebruiken via [AIO CLI-plug-in voor bronmigratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration), maar het kan ook zelfstandig worden uitgevoerd.

Zie **[Git Resource: aem-cs-source-migration-index-converter](https://git.corp.adobe.com/vavarshn/aem-cloud-service-source-migration/blob/master/packages/index-converter/README.md)** om te leren hoe u de plug-in installeert en gebruikt.

