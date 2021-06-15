---
title: Implementatiefase in Cloud Acceleration Manager
description: Deze pagina bevat een overzicht van de implementatiefase in Cloud Acceleration Manager.
hide: true
hidefromtoc: true
index: false
source-git-commit: 5af319d30198329fd2312c11d88bf326bc4cdae7
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 3%

---


# Implementatiefase in beheer voor cloudversnelling {#implementation-phase-cam}

De uitvoeringsfase omvat:

* [Lokale ontwikkeling](#local-development)
* [Herstructurering van code](#code-refactoring)
* [AEM als Cloud Service-implementatie](#aem-as-a-cloud-service-deployment)
* [Overdracht van content](#content-transfer)

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-1.png)

## Lokale ontwikkelingskaart gebruiken {#local-development}

De kaart van de Lokale Ontwikkeling verstrekt alle relevante inhoud die u zal helpen uw lokale AEM ontwikkelomgeving opzetten aangezien u de fase van de Implementatie van uw migratiereis begint.

Volg deze sectie om de activiteitenkaart van de Lokale Ontwikkeling te onderzoeken:

1. Klik op de **View** knoop van **de Lokale kaart van de Ontwikkeling**.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-2.png)

1. Een inhoudscarrousel met relevante informatie voor deze fase van de migratiereis vertoningen.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-3.png)


## Codereflecterende kaart {#code-refactoring} gebruiken

De de activiteitenkaart van de Refactoring van de Code verstrekt alle relevante informatie en benadrukt de gebieden van de code refactoring u moet herzien wanneer het bewegen aan AEM als Cloud Service.

Volg deze sectie om de de activiteitenkaart van het Refactoring van de Code te onderzoeken:

1. Klik op **Overzicht** knoop van **Code Refactoring** activiteitenkaart.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-4.png)

1. De pagina toont de lijst van code refactoring activiteiten die door het strengheidsniveau worden georganiseerd. U kunt meer leren door op de twee gemarkeerde pictogrammen te klikken.

   >[!NOTE]
   >Lees ook de inhoud in de tabbladen op de pagina om meer inzicht te krijgen in enkele andere gebieden die niet worden bestreken door de Analysator voor beste praktijken.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)


## AEM gebruiken als implementatiekaart van de Cloud Service {#aem-as-a-cloud-service-deployment}

AEM als kaart van de Plaatsing van de Cloud Service verstrekt alle relevante inhoud die u zal helpen uw code opstellen om als Cloud Service te AEM.

Volg deze sectie om AEM als activiteitenkaart van de identiteitskaart van de Plaatsing van de Cloud Service te onderzoeken:

1. Klik op de **View** knoop van **AEM als Cloud Service Plaatsing** kaart.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-4.png)

1. Een inhoudscarrousel met relevante informatie voor deze fase van de migratiereis vertoningen.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)


## Inhoudsoverdrachtskaart {#content-transfer} gebruiken

De activiteitenkaart van de Overdracht van de Inhoud verstrekt begeleiding en overwegingen die zouden moeten worden herzien wanneer het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud om inhoud van uw huidige AEM instantie aan AEM als Cloud Service te bewegen.

Volg deze sectie om de activiteitenkaart van de Overdracht van de Inhoud te onderzoeken:

1. Klik op de **View** knoop van **de Lokale kaart van de Ontwikkeling**.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-4.png)

1. Een inhoudscarrousel met relevante informatie voor deze fase van de migratiereis vertoningen.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)

>[!NOTE]
>Controleer de [voorwaarden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) en de [beste praktijken en richtlijnen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en) alvorens het Hulpmiddel van de Overdracht van de Inhoud te gebruiken.

Er is een nieuwe calculator voor het gereedschap Inhoud overbrengen beschikbaar waarmee u kunt inschatten hoe lang het kan duren om de activiteit voor inhoudsoverdracht te voltooien. Met de schuifregelaar Grootte inhoudgegevensopslagruimte kunt u de grootte selecteren die van toepassing is op uw project. De overdrachtstijden variëren voor de extractie- en innamefasen. Als u de grootte van de AEM Repository wilt inschatten, kunt u het rapport Schijfgebruik uitvoeren onder `http://HOST:PORT/etc/reports/diskusage.html`.

U kunt ook de grootte van specifieke repository paden schatten met de parameter `path`, bijvoorbeeld `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.
