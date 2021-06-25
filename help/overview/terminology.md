---
title: Inleiding tot Adobe Experience Manager as a Cloud Service - Terminologie
description: Inleiding tot Adobe Experience Manager as a Cloud Service - Terminologie.
exl-id: a76f68f1-4f84-4844-a099-0952707cd96d
source-git-commit: 4067db2234b29e4ffbe3e76f25afd9d8642a1973
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 97%

---

# Adobe Experience Manager as a Cloud Service - Terminologie {#adobe-experience-manager-as-a-cloud-service-terminology}

De volgende termen gebruikt in relatie tot Adobe Experience Manager (AEM) as a Cloud Service:

## Producten {#products}

| Product | Beschrijving |
|---|---|
| AEM as a Cloud Service | De &#39;cloud-native&#39; manier om de AEM-applicaties te benutten |
| AEM Assets as a Cloud Service | DAM-mogelijkheden (Digital Asset Management) als cloud-native, schaalbare oplossing voor het opnemen, verwerken en beheren van uw digitale assets, en tegelijk integreren met het bredere ecosysteem van Adobe Experience Cloud en Adobe Creative Cloud. |
| AEM Sites as a Cloud Service | Een instantie van AEM as a Cloud Service met de applicatie AEM Sites. |

## Instanties en pijplijnen {#instances-and-pipelines}

| Instantie | Beschrijving |
|---|---|
| Adobe Pipeline | Het mechanisme voor contentpublicatie vanaf auteur tot aan publicatie. |
| AEM-auteurlaag | Beschrijft de authoringomgeving voor Sites en Assets. |
| AEM | Beschrijft de voorvertoningsomgeving voor sites. |
| AEM-publicatielaag | Beschrijft de publicatieomgeving voor Sites. |


<!-- This section of the table must be alphabetic -->

## Terminologie {#terminology}

| Term | Beschrijving |
|---|---|
| AEM Image | Een implementeerbaar artefact dat de AEM-productcode samen met de klantcode bevat. |
| Asset-microservices | Cloudgebaseerde verwerkingsservices voor digitale assets die verschillende gebruiksgevallen voor assetverwerking bedienen, zoals het genereren van weergaven, PDF-verwerkingen, verwerking van subassets, tekstextractie, enzovoort. Zie [Asset-microservices - Overzicht](/help/assets/asset-microservices-overview.md) voor meer informatie. |
| Git-repository voor Cloud Manager | Waar klanten hun code en configuratie-instellingen opslaan. |
| Cloudprovider | AEM as a Cloud Service biedt momenteel ondersteuning voor Azure. Ondersteuning voor AWS is een van de punten in onze roadmap voor de toekomst. |
| Content Delivery Network (CDN) | AEM as a Cloud Service wordt geleverd met een standaard-CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties. |
| Content-repository | Waar de content wordt bewaard. |
| Enterprise Isolation | Elke instantie van de AEM as a Cloud Service is gescheiden van de andere instanties. |
| Golden Master | De AEM-publicatielaag. |
| Orkestratie-engine | AEM as a Cloud Service gebruikt een orkestratie-engine om ervoor te zorgen dat alle authoring- en publicatieservices naar behoefte worden geschaald. |
