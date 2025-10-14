---
title: De tool AEM Dispatcher Converter
description: Leer hoe u bestaande configuraties op AEM Dispatcher omzet in configuraties op AEM as a Cloud Service Dispatcher.
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 13%

---

# AEM Dispatcher Converter {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="AEM Dispatcher Converter"
>abstract="Adobe Experience Manager Dispatcher Converter zet bestaande configuraties op AEM Dispatcher om in configuraties op AEM as a Cloud Service Dispatcher."

Adobe Experience Manager Dispatcher Converter zet bestaande configuraties op AEM Dispatcher om in configuraties op AEM as a Cloud Service Dispatcher.

## Inleiding tot Dispatcher {#introduction-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor caching, ofwel taakverdeling, of beide. Door AEM Dispatcher te gebruiken is uw AEM-server ook beter beschermd tegen aanvallen. Daarom kunt u de veiligheid van uw AEM instantie verhogen door Dispatcher met een onderneming-klasse Webserver te gebruiken.

>[!NOTE]
>Dispatcher wordt vooral gebruikt om de respons van een **AEM Publish-instantie** in de cache op te slaan, zodat u sneller kunt reageren en uw gepubliceerde, naar buiten gerichte website beter kunt beveiligen.

Zie [&#x200B; het Overzicht van Dispatcher &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) leren hoe Dispatcher caching uitvoert, documenten terugkeert en het in evenwicht brengen van de Lading uitvoert.

### Configuratie en tests voor Apache en Dispatcher {#dispatcher-configurations-cloud}

Leer hoe u de AEM as a Cloud Service Apache- en Dispatcher-configuraties kunt structureren en hoe u deze lokaal kunt valideren en uitvoeren voordat u ze implementeert in een cloud-omgeving.

Zie [&#x200B; Dispatcher in de Wolk &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=nl-NL) voor meer informatie.

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter biedt de mogelijkheid bestaande Managed Services Dispatcher-configuraties op locatie of in Adobe te verfijnen naar Dispatcher-compatibele configuraties die compatibel zijn met AEM as a Cloud Service.

## AEM Dispatcher Converter gebruiken {#using-dispatcher-converter}

* Adobe Developer CLI: Adobe raadt u aan de AEM Dispatcher Converter te gebruiken via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor de Adobe Developer CLI).

  Zie **[Middel van de Git: ao-cli-stop-aem-wolk-dienst-migratie &#x200B;](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** zodat kunt u leren hoe te om de stop te installeren en te gebruiken.

* Als een zelfstandig hulpprogramma: het gereedschap AEM Dispatcher Converter kan ook als een zelfstandig hulpprogramma worden uitgevoerd.

  Zie **[Middel van de Git: De Convertor van AEM Cloud Service Dispatcher &#x200B;](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** zodat kunt u over het gebruik en het oplossen van problemen voor dit hulpmiddel leren.

>[!IMPORTANT]
>AEM Dispatcher Converter wordt ontwikkeld met NodeJS. Adobe raadt u aan NodeJS 10.0+ te installeren.
