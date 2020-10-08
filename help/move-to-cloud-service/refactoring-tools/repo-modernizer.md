---
title: Repository Modernizer
description: Repository Modernizer
translation-type: tm+mt
source-git-commit: 5da0d4cc8c6d8781dd7cce8bbbde207568a6d10b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 3%

---


# Repository Modernizer {#repo-modernizer}

Repository Modernizer is een hulpprogramma dat is ontwikkeld om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager als Cloud Service is gedefinieerd.

## Inleiding {#introduction}

Adobe Experience Manager als Cloud Service brengt vele nieuwe eigenschappen en mogelijkheden in uw AEM projecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van **inhoud** en **code** in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Raadpleeg de [AEM Projectstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) voor meer informatie over de nieuwe AEM projectstructuur voor Cloud Service.

De modernizer van de Bewaarplaats leidt tot een compatibele AEM het projectstructuur van de Cloud Service door de volgende plaatsingsstructuur te creëren:

* `ui.apps` pakket wordt geïmplementeerd naar `/apps` en bevat alle code

* `ui.content` pakketimplementaties naar runtime-schrijfbare gebieden (bijvoorbeeld `/content`, `/conf`, `/home`of iets anders `/apps`) en bevat alle inhoud en configuratie.

* `all` pakket is een containerpakket dat de subpakketten `ui.apps` en `ui.content`.

>[!NOTE]
>De projectstructuur is gebaseerd op *Archetype 24* voor pakketten en hun `pom.xml/filter.xml files`. Zie [Archetype 24](https://github.com/adobe/aem-project-archetype) voor meer informatie.

## De Repository Modernizer gebruiken {#using-repo-modernizer}

* Via Adobe I/O CLI: Aanbevolen wordt de functie Opslagfunctie Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (AEM als plug-in voor het refactoring van Cloud Service voor de Adobe I/O CLI) te gebruiken.

   Zie **[Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** voor het installeren en gebruiken van de plug-in.

* Als zelfstandig hulpprogramma: De Repository Modernizer kan ook als standalone nut worden uitgevoerd.

   Zie **[Git Resource: Modernisering](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** van opslagplaats voor informatie over het gebruik van dit gereedschap.

   >[!NOTE]
   >
   >De Repository Modernizer wordt ontwikkeld met NodeJS. Het wordt aanbevolen NodeJS 10.0+ te installeren.
