---
title: Implementatiefase in Cloud Acceleration Manager
description: Deze pagina bevat een overzicht van de implementatiefase in Cloud Acceleration Manager.
source-git-commit: b1a2b7b78349524e842e30f69729fb3351765582
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 2%

---


# Implementatiefase in Cloud Acceleration Manager {#implementation-phase-cam}

De uitvoeringsfase omvat:

* [Lokale ontwikkeling](#local-development)
* [Herstructurering van code](#code-refactoring)
* [AEM als Cloud Service-implementatie](#aem-as-a-cloud-service-deployment)
* [Overdracht van content](#content-transfer)


Klik op uw projectkaart om de bestemmingspagina van het project te openen en aan de **sectie van de Implementatie**, zoals aangetoond in het hieronder cijfer te navigeren.

![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Raadpleeg [Een project maken en beheren in Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en#create-project) voor meer informatie.


## Lokale ontwikkelingskaart gebruiken {#local-development}

De kaart van de Lokale Ontwikkeling verstrekt alle relevante inhoud die u zal helpen uw lokale AEM ontwikkelomgeving opzetten aangezien u de fase van de Implementatie van uw migratiereis begint.

Volg deze sectie om de activiteitenkaart van de Lokale Ontwikkeling te onderzoeken:

1. Klik op de **View** knoop van **de Lokale kaart van de Ontwikkeling**.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-2.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-3.png)


## Code Refactoring Card gebruiken {#code-refactoring}

De de activiteitenkaart van de Refactoring van de Code verstrekt alle relevante informatie en benadrukt de gebieden van de code refactoring u moet herzien en oplossen wanneer het bewegen zich aan AEM als Cloud Service.

Volg deze sectie om de de activiteitenkaart van het Refactoring van de Code te onderzoeken:

1. Klik op **Overzicht** knoop van **Code Refactoring** activiteitenkaart.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-4.png)

1. De pagina toont de lijst van code refactoring activiteiten die door het strengheidsniveau worden georganiseerd. U kunt meer leren door op de twee gemarkeerde pictogrammen te klikken.

   >[!NOTE]
   >Lees ook de inhoud in de tabbladen op de pagina om meer inzicht te krijgen in enkele andere gebieden die niet worden bestreken door de Analysator voor beste praktijken.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/readiness-5.png)


## Het gebruiken van AEM als Kaart van de Plaatsing van de Cloud Service {#aem-as-a-cloud-service-deployment}

AEM als kaart van de Plaatsing van de Cloud Service verstrekt alle relevante inhoud die u zal helpen uw code opstellen om als Cloud Service te AEM.

Volg deze sectie om AEM als activiteitenkaart van de identiteitskaart van de Plaatsing van de Cloud Service te onderzoeken:

1. Klik op de **View** knoop van **AEM als Cloud Service Plaatsing** activiteitenkaart.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-6.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Inhoudsoverdrachtkaart gebruiken {#content-transfer}

De activiteitenkaart van de Overdracht van de Inhoud verstrekt begeleiding en overwegingen die zouden moeten worden herzien wanneer het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud om inhoud van uw huidige AEM instantie aan AEM als Cloud Service te bewegen.

Volg deze sectie om de activiteitenkaart van de Overdracht van de Inhoud te onderzoeken:

1. Klik op de **View** knoop van **Content Overdracht** activiteitenkaart.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/implementation-8.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/move-to-cloud-service/cloud-acceleration-manager/assets/content-transfertool-card.png)

   >[!NOTE]
   >Controleer de [voorwaarden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) en de [beste praktijken en richtlijnen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en) alvorens het Hulpmiddel van de Overdracht van de Inhoud te gebruiken.

### De tijd van de inhoudsoverdracht schatten {#calculating}

Er is een nieuwe calculator voor het gereedschap Inhoud overbrengen beschikbaar waarmee u kunt inschatten hoe lang het kan duren om de activiteit voor inhoudsoverdracht te voltooien. Met de schuifregelaar Grootte inhoudgegevensopslagruimte kunt u de grootte selecteren die van toepassing is op uw project. De overdrachtstijden variëren voor de extractie- en innamefasen.

>[!NOTE]
>Deze tijden zijn slechts schattingen. Factor zoals netwerksnelheden en tijd aan schaalinstanties zijn niet rekenschap gegeven in deze ramingen.

Als u de grootte van de AEM Repository wilt inschatten, kunt u het rapport Schijfgebruik uitvoeren onder `http://HOST:PORT/etc/reports/diskusage.html`.

U kunt ook de grootte van specifieke repository paden schatten met de parameter `path`, bijvoorbeeld `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.

## Volgende functies {#whats-next}

Als u eenmaal hebt geleerd hoe u zich kunt aanmelden bij Cloud Acceleration Manager en hoe u de Implementatiefase gebruikt, kunt u nu verdergaan met het evalueren van de volgende stap in de [Live fase gaan](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=en).
