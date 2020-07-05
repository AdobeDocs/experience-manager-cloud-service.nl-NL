---
title: De tool AEM Dispatcher Converter
description: De tool AEM Dispatcher Converter
translation-type: ht
source-git-commit: 66cf4fc7b5a336968dd3f8757cc56a11d6e4843e
workflow-type: ht
source-wordcount: '348'
ht-degree: 100%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter converteert bestaande AMS Dispatcher-configuraties naar AEM as a Cloud Service Dispatcher-configuraties.

## Inleiding tot Dispatcher {#introduction-dispatcher}

Dispatcher is de Adobe Experience Manager-tool voor cache- en taakverdelingsbewerkingen. Door AEM Dispatcher te gebruiken is uw AEM-server ook beter beschermd tegen aanvallen. U kunt de veiligheid van uw AEM-instantie dus verhogen door de Dispatcher samen met een webserver van ondernemingsklasse te gebruiken.

>[!NOTE]
>Dispatcher wordt vooral gebruikt om de respons van een **AEM Publish-instantie** in de cache op te slaan, zodat u sneller kunt reageren en uw gepubliceerde, naar buiten gerichte website beter kunt beveiligen.

Raadpleeg het [Dispatcher-overzicht](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html) voor meer informatie over hoe Dispatcher werkt met caching, taakverdelingen en het retourneren van documenten.

### Configuratie en testen van Apache en Dispatcher {#dispatcher-configurations-cloud}

U moet leren hoe u de Apache- en Dispatcher-configuraties van AEM as a Cloud Service structureert, en hoe u deze lokaal kunt valideren en uitvoeren voordat u ze implementeert in een Cloud-omgeving.

Raadpleeg [Dispatcher in de cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) voor meer informatie.

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter is een hulpprogramma voor het converteren van bestaande AMS Dispatcher-configuraties naar AEM as a Cloud Service Dispatcher-configuraties. Dit hulpprogramma is bedoeld voor AMS-instanties.

De geïmplementeerde converter is **AEMDispatcherConfigConverter** die de transformatierichtlijnen volgt.

Raadpleeg [Een AMS converteren naar een Adobe Experience Manager as a Cloud Service Dispatcher-configuratie](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration) voor het converteren van een AMS naar een Adobe Experience Manager as a Cloud Service Dispatcher-configuratie.

## AEM Dispatcher Converter gebruiken {#using-dispatcher-converter}

In de volgende sectie worden de bronnen en informatie beschreven die vereist zijn voor het gebruik van de AEM Dispatcher Converter-tool.

Zie **[Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**voor meer informatie over het gebruik, de beperkingen en het oplossen van problemen voor deze tool.

>[!IMPORTANT]
>AEM Dispatcher Converter is ontwikkeld met Python 3.7.3. Het wordt aanbevolen Python 3.5 of hoger te installeren.

## Beperkingen {#limitations}

De AEM Dispatcher Converter-tool werkt op basis van de veronderstelling dat de structuur van de geleverde Dispatcher-configuratiemap vergelijkbaar is met de configuratiestructuur van de Cloud Manager Dispatcher.


