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

## Introductie tot Dispatcher {#introduction-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor het in cache plaatsen, of taakverdeling, of beide. Door AEM Dispatcher te gebruiken is uw AEM-server ook beter beschermd tegen aanvallen. Daarom kunt u de veiligheid van uw AEM instantie verhogen door Dispatcher met een onderneming-klasse Webserver te gebruiken.

>[!NOTE]
>Dispatcher wordt vooral gebruikt om de respons van een **AEM Publish-instantie** in de cache op te slaan, zodat u sneller kunt reageren en uw gepubliceerde, naar buiten gerichte website beter kunt beveiligen.

Zie [Overzicht van verzending](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) Als u wilt weten hoe Dispatcher caching uitvoert, worden documenten geretourneerd en de taakverdeling uitgevoerd.

### Configuratie en testen van Apache en Dispatcher {#dispatcher-configurations-cloud}

Leer hoe u de AEM as a Cloud Service Apache- en Dispatcher-configuraties kunt structureren en hoe u deze lokaal kunt valideren en uitvoeren voordat u ze implementeert in een cloud-omgeving.

Zie [Dispatcher in de cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) voor meer informatie .

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter verstrekt het vermogen van het refactoring van bestaande op-gebouw of Adobe de configuraties van de Ontvanger van Managed Services om as a Cloud Service compatibele configuratie van de Ontvanger te AEM.

## AEM Dispatcher Converter gebruiken {#using-dispatcher-converter}

* Als Adobe Developer CLI: Adobe raadt u aan de AEM Dispatcher Converter te gebruiken als `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service code refactoring plugin voor Adobe Developer CLI).

  Zie **[Git-bron: audio-cli-plugin-aem-cloud-service-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** zodat u leert installeren en gebruiken de stop.

* Als zelfstandig hulpprogramma: het gereedschap AEM Dispatcher Converter kan ook als een zelfstandig hulpprogramma worden uitgevoerd.

  Zie **[Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** zodat u meer kunt leren over het gebruik en het oplossen van problemen voor dit hulpmiddel.

>[!IMPORTANT]
>AEM Dispatcher Converter wordt ontwikkeld met NodeJS. Adobe raadt u aan NodeJS 10.0+ te installeren.
