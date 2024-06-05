---
title: Repository Modernizer
description: Leer hoe u bestaande projectpakketten kunt herstructureren en compatibel kunt maken met de projectstructuur die is gedefinieerd voor Adobe Experience Manager as a Cloud Service.
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer is een hulpprogramma dat is ontwikkeld om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager as a Cloud Service is gedefinieerd.

## Inleiding {#introduction}

Adobe Experience Manager as a Cloud Service voegt veel nieuwe functies en mogelijkheden toe aan uw AEM. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van **content** en **code** in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Zie [AEM projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) voor meer informatie over de nieuwe AEM projectstructuur voor Cloud Service.

Met Repository Modernizer wordt een compatibele AEM Cloud Service-projectstructuur gemaakt door de volgende implementatiestructuur te maken:

* `ui.apps` pakket implementeert naar `/apps` en bevat alle code

* `ui.content` pakketten worden geïmplementeerd in runtime-schrijfbare gebieden (bijvoorbeeld `/content`, `/conf`, `/home`of iets anders `/apps`) en bevat alle inhoud en configuratie.

* `all` pakket is een containerpakket dat de subpakketten bevat `ui.apps` en `ui.content`.

>[!NOTE]
>De projectstructuur is gebaseerd op *Archetype 24* voor verpakkingen en hun `pom.xml/filter.xml files`. Zie [Archetype 24](https://github.com/adobe/aem-project-archetype) voor meer informatie .

## De Repository Modernizer gebruiken {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Als Adobe I/O CLI: Adobe raadt aan de Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor de Adobe I/O CLI).

  Zie **[Git-bron: audio-cli-plugin-aem-cloud-service-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** zodat u leert installeren en gebruiken de stop.

* Als standalone nut: De Modernizer van de Bewaarplaats kan ook als standalone nut worden uitgevoerd.

  Zie **[Git Resource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** zodat u kunt leren hoe u dit gereedschap kunt gebruiken.

  >[!NOTE]
  >
  >De Repository Modernizer wordt ontwikkeld met NodeJS. Het wordt aanbevolen NodeJS 10.0+ te installeren.
