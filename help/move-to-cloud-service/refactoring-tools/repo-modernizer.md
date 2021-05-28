---
title: Repository Modernizer
description: Repository Modernizer
exl-id: b89156a8-3d7d-4d36-89a2-beeda35bbc01
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Modernizer opslagplaats {#repo-modernizer}

Repository Modernizer is een hulpprogramma dat is ontwikkeld om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager als Cloud Service is gedefinieerd.

## Inleiding {#introduction}

Adobe Experience Manager als Cloud Service brengt vele nieuwe eigenschappen en mogelijkheden in uw AEM projecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van **content** en **code** in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Raadpleeg [AEM Projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) voor meer informatie over de nieuwe AEM projectstructuur voor Cloud Service.

De modernizer van de Bewaarplaats leidt tot een compatibele AEM het projectstructuur van de Cloud Service door de volgende plaatsingsstructuur te creëren:

* `ui.apps` pakket implementeert naar  `/apps` en bevat alle code

* `ui.content` pakketten worden geïmplementeerd in runtime-schrijfbare gebieden (bijvoorbeeld  `/content`,  `/conf`,  `/home`of iets anders  `/apps`) en bevat alle inhoud en configuratie.

* `all` pakket is een containerpakket dat de subpakketten  `ui.apps` en  `ui.content`bevat.

>[!NOTE]
>De projectstructuur is gebaseerd op *Archetype 24* voor pakketten en hun `pom.xml/filter.xml files`. Raadpleeg [Archetype 24](https://github.com/adobe/aem-project-archetype) voor meer informatie.

## De Repository Modernizer {#using-repo-modernizer} gebruiken

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Via Adobe I/O CLI: Het wordt aanbevolen de Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` te gebruiken (AEM als insteekmodule voor het refactoring van de Cloud Service voor de Adobe I/O CLI).

   Zie **[Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** voor meer informatie over het installeren en gebruiken van de plug-in.

* Als zelfstandig hulpprogramma: De Repository Modernizer kan ook als standalone nut worden uitgevoerd.

   Zie **[Git Resource: Modernizer opslagplaats](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** om te leren hoe u dit gereedschap kunt gebruiken.

   >[!NOTE]
   >
   >De Repository Modernizer wordt ontwikkeld met NodeJS. Het wordt aanbevolen NodeJS 10.0+ te installeren.
