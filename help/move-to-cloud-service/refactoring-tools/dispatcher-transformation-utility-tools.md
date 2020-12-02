---
title: De tool AEM Dispatcher Converter
description: De tool AEM Dispatcher Converter
translation-type: tm+mt
source-git-commit: 50d26dbec8281afec07ca56595b4b2a7b915eca9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 53%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter zet bestaande AEM Dispatcher-configuraties om in AEM als configuraties van Cloud Service Dispatcher.

## Inleiding tot Dispatcher {#introduction-dispatcher}

Dispatcher is de Adobe Experience Manager-tool voor cache- en taakverdelingsbewerkingen. Door AEM Dispatcher te gebruiken is uw AEM-server ook beter beschermd tegen aanvallen. U kunt de veiligheid van uw AEM-instantie dus verhogen door de Dispatcher samen met een webserver van ondernemingsklasse te gebruiken.

>[!NOTE]
>Dispatcher wordt vooral gebruikt om de respons van een **AEM Publish-instantie** in de cache op te slaan, zodat u sneller kunt reageren en uw gepubliceerde, naar buiten gerichte website beter kunt beveiligen.

Raadpleeg het [Dispatcher-overzicht](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html) voor meer informatie over hoe Dispatcher werkt met caching, taakverdelingen en het retourneren van documenten.

### Configuratie en testen van Apache en Dispatcher {#dispatcher-configurations-cloud}

U moet leren hoe u de Apache- en Dispatcher-configuraties van AEM as a Cloud Service structureert, en hoe u deze lokaal kunt valideren en uitvoeren voordat u ze implementeert in een Cloud-omgeving.

Raadpleeg [Dispatcher in de cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) voor meer informatie.

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter biedt de mogelijkheid om bestaande configuraties van Dispatcher op locatie of Adobe Managed Services Dispatcher te vernieuwen en te AEM als een met Cloud Service compatibele Dispatcher-configuratie.

## AEM Dispatcher Converter gebruiken {#using-dispatcher-converter}

* Via Adobe I/O CLI: Het wordt aanbevolen de AEM Dispatcher Converter via `aio-cli-plugin-aem-cloud-service-migration` te gebruiken (AEM als een Cloud Service code refactoring plugin voor de Adobe I/O CLI).

   Zie **[Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** voor meer informatie over het installeren en gebruiken van de plug-in.

* Als zelfstandig hulpprogramma: Het gereedschap AEM Dispatcher Converter kan ook worden uitgevoerd als een zelfstandig hulpprogramma.

   Zie **[Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** voor meer informatie over het gebruik en het oplossen van problemen voor dit hulpmiddel.

>[!IMPORTANT]
>AEM Dispatcher Converter wordt ontwikkeld met NodeJS. Het wordt aanbevolen NodeJS 10.0+ te installeren.

