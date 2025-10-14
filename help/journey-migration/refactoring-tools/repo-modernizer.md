---
title: Repository Modernizer
description: Leer hoe u bestaande projectpakketten kunt herstructureren en compatibel kunt maken met de projectstructuur die is gedefinieerd voor Adobe Experience Manager as a Cloud Service.
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
feature: Migration
role: Admin
source-git-commit: 6920651420da9b427510518b7add0637479adef5
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer is een hulpprogramma dat is ontwikkeld om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager as a Cloud Service is gedefinieerd.

## Inleiding {#introduction}

Adobe Experience Manager as a Cloud Service voegt veel nieuwe functies en mogelijkheden toe aan uw AEM-projecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om compatibel te zijn met AEM Cloud Service. Op een hoog niveau, vereist AEM een scheiding van **inhoud** en **code** in discrete subpackages om de scheiding tussen veranderlijke en onveranderlijke inhoud te respecteren. Zie [&#x200B; de Structuur van het Project van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=nl-NL) voor meer details over de nieuwe het projectstructuur van AEM voor Cloud Service.

Met de Repository Modernizer wordt een compatibele AEM Cloud Service-projectstructuur gemaakt door de volgende implementatiestructuur te maken:

* `ui.apps` -pakket wordt geïmplementeerd in `/apps` en bevat alle code

* `ui.content` wordt geïmplementeerd in runtime schrijfbare gebieden (bijvoorbeeld `/content` , `/conf` , `/home` of iets anders `/apps` ) en bevat alle inhoud en configuratie.

* `all` is een containerpakket dat de subpakketten `ui.apps` en `ui.content` bevat.

>[!NOTE]
>
>De structuur van het Project is gebaseerd op *Archetype 24* voor pakketten en hun `pom.xml/filter.xml files`. Zie [&#x200B; Archetype 24 &#x200B;](https://github.com/adobe/aem-project-archetype) voor meer details.

## De Repository Modernizer gebruiken {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Als Adobe I/O CLI: Adobe raadt u aan de Repository Modernizer te gebruiken via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor de Adobe I/O CLI).

  Zie **[Middel van de Git: ao-cli-stop-aem-wolk-dienst-migratie &#x200B;](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** zodat kunt u leren hoe te om de stop te installeren en te gebruiken.

* Als standalone nut: De Modernizer van de Bewaarplaats kan ook als standalone nut worden uitgevoerd.

  Zie **[Middel van de Git: Modernizer van de Bewaarplaats &#x200B;](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** zodat kunt u leren hoe te om dit hulpmiddel te gebruiken.

  >[!NOTE]
  >
  >De Repository Modernizer wordt ontwikkeld met NodeJS. Het wordt aanbevolen NodeJS 10.0+ te installeren.
