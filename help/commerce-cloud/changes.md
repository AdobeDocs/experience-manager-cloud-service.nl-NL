---
title: Opvallende veranderingen in AEM Handel als Cloud Service
description: Opvallende veranderingen in AEM Handel als Cloud Service in vergelijking met Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: ed81d08d9775f61c0ab1e305710ac7ecf29d4229
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 5%

---


# Notable changes to AEM Commerce as a Cloud Service {#notable-changes}

Adobe Experience Manager als Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM projecten te beheren. Dit document benadrukt de belangrijke verschillen voor de mogelijkheden van de Handel tussen het Kader van de Integratie van de Handel (CIF) voor On-premise, Adobe Beheerde Dienst en Experience Manager als Cloud Service. Voor andere veranderingen, zie de generische [veranderingen in Experience Manager als Cloud Service](/help/release-notes/aem-cloud-changes.md).

De belangrijkste verschillen ten opzichte van Experience Manager 6.5 zijn op de volgende gebieden:
* [Ondersteuning voor CIF Classic](#cif-classic)
* [Implementatie van CIF-ontwerpgereedschappen](#cif-tools)
* [Overstappen van on-premise en Adobe Managed Service](#moving-cif-cs)

## Ondersteuning voor CIF Classic/Quickstart op Experience Manager als Cloud Service {#cif-classic}

Het Klassieke Kader van de Integratie van de Handel dat een Importeur van het Product omvatte om productcatalogi in Experience Manager in te voeren en op te slaan is niet meer beschikbaar in de Experience Manager als Cloud Service. Het gebruik van Klassieke CIF wordt niet in de Experience Manager gesteund als Cloud Service en projecten die Klassieke CIF gebruiken zullen de Klassieke implementatie CIF met de gesteunde versie moeten vervangen zoals die in [CIF op Experience Manager als Cloud Service wordt beschreven](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/commerce/architecture/magento.html#overview)

## Plaatsing van CIF {#deployment}

Hieronder worden de verschillende implementatiemodellen voor het framework voor de integratie van de handel voor de verschillende AEM weergegeven:

|  | AEM op locatie | AEM Managed Services | AEM Cloud Service |
|-------------     |-----------|-----------|-----------|
| Hoe te om Hulpmiddelen van de Authoring CIF voor Magento te opstellen backend | [Zie CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) die op AEM 6.5 wordt gesteund | [Zie CIF Connector](https://github.com/adobe/commerce-cif-connector/blob/master/README.md) die op AEM 6.5 wordt gesteund | AEM als Cloud Service moet worden voorzien van toe:voegen-op CIF. Neem contact op met uw verkoper voor meer informatie |
| Hoe [CIF Venia-project te implementeren](https://github.com/adobe/aem-cif-guides-venia) | AEM | Implementatie uitgevoerd via [Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) | Project verplaatst naar [Cloud Manager Git Repository](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) en implementatie uitgevoerd via [Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html) |

>[!NOTE]
>
>Voor extra documentatie over hoe te om CIF met AEM Beheerde Dienst of AEM On-premisse te gebruiken, verwijs naar het Kader van de Integratie van de [Handel](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)

>[!Nofferte]
>
>CIF Classic/Quickstart-versie van Commerce Integration Framework kan worden gebruikt voor AEM on-premise aanbieding voor zeer beperkte gebruiksgevallen. Dit is echter niet de aanbevolen oplossing.

## Het bewegen naar AEM Handel als Cloud Service van On-premise en Managed Services {#moving-cif-cs}

Klanten die van een AEM installatie op locatie of van Managed Services naar AEM gaan als Cloud Service moeten een paar kleine aanpassingen aanbrengen in het AEM project.

De eerste aanpassing, zoals hierboven beschreven, is nodig voor de CIF-connector. De CIF-aansluiting wordt vervangen door de CIF-invoegtoepassing die wordt geïmplementeerd door Adobe. Installeer daarom niet de CIF Schakelaar op AEM als Cloud Service. Bovendien wordt het gebruik met de lokale AEM Cloud SDK niet ondersteund. Adobe biedt de CIF-invoegtoepassing ook voor [lokale ontwikkeling](develop.md).

Ten tweede, begrijp de [AEM Structuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) van het Project en de kenmerken van AEM als Cloud Service. Pas de projectinstelling aan op de AEM als Cloud Service-indeling.
De belangrijkste verschillen zijn:

* De GraphQL-client OSGI-bundel **mag niet** meer in het AEM-project worden opgenomen, maar wordt via de CIF-invoegtoepassing geïmplementeerd
* OSGI-configuraties voor GraphQL-client en Graphql Data Service **mogen niet** meer in het AEM-project worden opgenomen

>[!TIP]
>
>Bekijk het project [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) op GitHub. Dit project biedt Maven-profielen voor AEM als Cloud Service en on-premise implementaties die rekening houden met de verschillende randvoorwaarden.
