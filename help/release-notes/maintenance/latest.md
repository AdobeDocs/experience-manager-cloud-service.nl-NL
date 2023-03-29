---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: c6acdd922c052d0db5bf1f05bc03329fbc44ca33
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 11382 {#release-11382}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 11382 samengevat, die op 28 maart 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 11289.

Functie-activering voor deze onderhoudsrelease biedt u de volledige functieset. Zie de [Opmerkingen bij de huidige release](/help/release-notes/release-notes-cloud/release-notes-current.md) voor volledige informatie.

### Opgeloste problemen {#fixed-issues}

- ASSETS-21023 - Fixed Smart Crop rendition, waarbij klanten een Null-aanwijzeruitzondering konden observeren op de Publisher-instantie van alle AEM omgevingen wanneer ze probeerden toegang te krijgen tot deze uitvoeringen via de API.
- SKYOPS-49280 - wanneer het installeren van een config of bundelupdate gebruikend RDE in Publish het resultaat kan niet waarneembaar zijn omdat het Publish berichtgeheime voorgeheugen niet ongeldig wordt gemaakt

#### Sites {#sites-issues}

- SITES-7796 - Mogelijkheid voor de auteur van de inhoud om het Master inhoudsfragment en de respectieve Variaties te publiceren wanneer het uitvoeren naar doel
- SITES-97 - GraphQL: Paginering en sorteren, hybride filtering

>[!NOTE]
>
> In SITES-97 zijn enkele verbeteringen aangebracht in de GraphQL-implementatie die tot onverwacht gedrag kunnen leiden. Zie [GraphQL-wijzigingen AEM met betrekking tot de verwerking van null-waarden](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-21792.html) voor meer informatie .

#### Assets {#assets-issues}

- ASSETS-20076 - Ondersteuning voor videowatermerken toevoegen die overeenkomt met de huidige ondersteuning voor watermerken voor afbeeldingen
- ASSETS-21428 - Toegevoegde uitsluitingen voor CSS-wijzigingen

#### Forms {#forms-issues}

- CQ-4351502 - Het bijwerken van de afbeelding van de de dienstgebruiker om leestoegang in Plaatsen toe te staan

#### Platform {#platform-issues}

- SITES-11040 - Voorwaardelijke enablement van GraphQL persisted query caching in dispatcher

### Ingesloten technologieën {#embedded-tech}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM OAK | 1,44-T20221206170501-6d59064 | [API 1.44.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Versie 2.27.0 | [API voor Apache Sling API 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.21.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
