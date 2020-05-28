---
title: AEM Dispatcher Converter Tool
description: AEM Dispatcher Converter Tool
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter converteert bestaande AMS Dispatcher-configuraties naar AEM als een Cloud Service Dispatcher-configuraties.

## Introductie tot Dispatcher {#introduction-dispatcher}

Dispatcher is het programma voor het in cache plaatsen en/of taakverdeling van Adobe Experience Manager. Het gebruik van de Dispatcher van AEM helpt ook uw AEM-server tegen aanvallen te beschermen. Daarom kunt u de veiligheid van uw instantie verhogen AEM door de Dispatcher samen met een onderneming-klasse Webserver te gebruiken.

>[!NOTE]
>Dispatcher wordt vooral gebruikt om reacties van een **AEM-publicatie-instantie** in de cache op te slaan, zodat u sneller kunt reageren en uw externe website beter kunt beveiligen.

Raadpleeg het Overzicht [van](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html) Dispatcher voor meer informatie over de manier waarop de verzender caching uitvoert, documenten retourneert en taakverdeling uitvoert.

### Configuratie en testen van Apache en Dispatcher {#dispatcher-configurations-cloud}

U moet leren hoe u de AEM kunt structureren als Apache- en Dispatcher-configuraties voor cloudservice, en hoe u de AEM lokaal kunt valideren en uitvoeren voordat u de AEM implementeert in een cloud-omgeving.

Raadpleeg [Dispatcher in de cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html) voor meer informatie.

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter is een hulpprogramma voor het converteren van bestaande AMS Dispatcher-configuraties naar AEM als configuraties van Cloud Service Dispatcher. Dit hulpprogramma is bedoeld voor AMS-instanties.

De geïmplementeerde converter is **AEMDispatcherConfigConverter** die de transformatierichtlijnen volgt.

Raadpleeg Een AMS [converteren naar een Adobe Experience Manager als een Cloud Service Dispatcher Configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration) voor het converteren van een AMS naar een Adobe Experience Manager als een Cloud Service Dispatcher-configuratie.

## AEM Dispatcher Converter gebruiken {#using-dispatcher-converter}

In de volgende sectie worden de bronnen en informatie beschreven die vereist zijn voor het gebruik van het gereedschap AEM Dispatcher Converter.

Zie **[Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**voor meer informatie over het gebruik, de beperkingen en het oplossen van problemen voor dit programma.

>[!IMPORTANT]
>AEM Dispatcher Converter is ontwikkeld met Python 3.7.3. Het wordt aanbevolen Python 3.5 of hoger te installeren.

## Beperkingen {#limitations}

De converter van AEM Dispatcher werkt op basis van de veronderstelling dat de structuur van de meegeleverde installatiemap voor de configuratie van de verzender vergelijkbaar is met de structuur die wordt beschreven in de configuratie van de verzender van Cloud Manager.


