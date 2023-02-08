---
title: Opmerkingen bij de nieuwste onderhoudsrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de nieuwste onderhoudsrelease [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 76da86d31e2780c2d22419cb8a338cf37963fad8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de technische releaserotaties voor de meest recente onderhoudsrelease van as a Cloud Service Experience Manager beschreven.

## Release 10912 {#release-10912}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 10912 samengevat, die op 3 februari 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 9850.

Functie-activering voor deze onderhoudsrelease biedt u de volledige functieset. Zie de [Opmerkingen bij de huidige release](/help/release-notes/release-notes-cloud/release-notes-current.md) voor volledige informatie.

### Bekende problemen {#known-issues}

Voer geen upgrade uit als u CORS gebruikt. We hebben een probleem geïdentificeerd dat invloed heeft op GraphQL content delivery part in deze release. Een verandering in standaard AEM verzender config rond hoe GraphQL voortgeduurde vragen in het voorgeheugen ondergebracht zijn kan de de inhoudslevering van GraphQL van voortgezette vragen voor klanten breken gebruikend een configuratie CORS.

### Ingesloten technologieën {#embedded-tech}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM WCM Core-componenten | Versie 2.21.2 | [GitHub](https://github.com/adobe/aem-core-wcm-components) |
