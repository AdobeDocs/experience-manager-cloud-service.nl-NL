---
title: Implementatiefase in Cloud Acceleration Manager
description: Deze pagina bevat een overzicht van de implementatiefase in Cloud Acceleration Manager.
source-git-commit: a6d225943c5d23ebd960fda0b0912a81f1f80014
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 2%

---

# Implementatiefase in Cloud Acceleration Manager {#implementation-phase-cam}

De uitvoeringsfase omvat:

* [Lokale ontwikkeling](#local-development)
* [Herstructurering van code](#code-refactoring)
* [as a Cloud Service implementatie AEM](#aem-as-a-cloud-service-deployment)
* [Overdracht van content](#content-transfer)


Klik op uw projectkaart om de bestemmingspagina van het project te openen en naar het project te navigeren **Implementatie** in de onderstaande afbeelding.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Zie [Een project maken en beheren in Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en#create-project) voor meer informatie.


## Lokale ontwikkelingskaart gebruiken {#local-development}

De kaart van de Lokale Ontwikkeling verstrekt alle relevante inhoud die u zal helpen uw lokale AEM ontwikkelomgeving opzetten aangezien u de fase van de Implementatie van uw migratiereis begint.

Volg deze sectie om de activiteitenkaart van de Lokale Ontwikkeling te onderzoeken:

1. Klik op de knop **Weergave** van de knop **Lokale ontwikkeling** kaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Code Refactoring Card gebruiken {#code-refactoring}

De de activiteitenkaart van de Refactoring van de Code verstrekt alle relevante informatie en benadrukt de gebieden van de code refactoring u moet herzien en oplossen wanneer zich het bewegen aan AEM as a Cloud Service.

Volg deze sectie om de de activiteitenkaart van het Refactoring van de Code te onderzoeken:

1. Klik op de knop **Controleren** van de knop **Code Refactoring** activiteitenkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. De pagina toont de lijst van code refactoring activiteiten die door het strengheidsniveau worden georganiseerd. U kunt meer leren door op de twee gemarkeerde pictogrammen te klikken.

   Op de pagina worden de overwegingen voor het wijzigen van code in drie verschillende tabbladen weergegeven:

   * Overzicht
   * Dispatcher
   * Testen

>[!NOTE]
>Controleer de inhoud op deze tabbladen om een aantal extra gebieden te begrijpen die niet worden bestreken door de Analysator voor beste praktijken.

De **Dispatcher** biedt informatie over hoe u de AEM as a Cloud Service Apache- en Dispatcher-configuraties kunt structureren en hoe u deze lokaal kunt valideren en uitvoeren voordat u ze implementeert in Cloud-omgevingen. Hierin wordt ook foutopsporing in Cloud-omgevingen beschreven.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

De **Testen** biedt informatie over het testen van functies, Experience Audit en UI.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM as a Cloud Service implementatiekaart gebruiken {#aem-as-a-cloud-service-deployment}

AEM de as a Cloud Service kaart van de Plaatsing verstrekt alle relevante inhoud die u zal helpen uw code opstellen om as a Cloud Service te AEM.

Volg deze sectie om AEM activiteitenkaart van de Kaart van de Plaatsing te onderzoeken as a Cloud Service:

1. Klik op de knop **Weergave** van de knop **as a Cloud Service implementatie AEM** activiteitenkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Inhoudsoverdrachtkaart gebruiken {#content-transfer}

De activiteitenkaart van de Overdracht van de Inhoud verstrekt begeleiding en overwegingen die zouden moeten worden herzien wanneer het gebruiken van het Hulpmiddel van de Overdracht van de Inhoud om inhoud van uw huidige AEM as a Cloud Service te bewegen aan AEM.

Volg deze sectie om de activiteitenkaart van de Overdracht van de Inhoud te onderzoeken:

1. Klik op de knop **Weergave** van de knop **Inhoud overbrengen** activiteitenkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-8.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/content-transfertool-card.png)

   >[!NOTE]
   >Controleer de [voorwaarden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en) en de [beste praktijken en richtsnoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en) voordat u het gereedschap Inhoud overbrengen gebruikt.

### De tijd van de inhoudsoverdracht schatten {#calculating}

Er is een nieuwe calculator voor het gereedschap Inhoud overbrengen beschikbaar waarmee u kunt inschatten hoe lang het kan duren om de activiteit voor inhoudsoverdracht te voltooien. Met de schuifregelaar Grootte inhoudgegevensopslagruimte kunt u de grootte selecteren die van toepassing is op uw project. De overdrachtstijden variëren voor de extractie- en innamefasen.

>[!NOTE]
>Deze tijden zijn slechts schattingen. Factor zoals netwerksnelheden en tijd aan schaalinstanties zijn niet rekenschap gegeven in deze ramingen.

Als u de grootte van de AEM Repository wilt inschatten, kunt u het rapport Schijfgebruik uitvoeren onder `http://HOST:PORT/etc/reports/diskusage.html`.

U kunt ook de grootte van specifieke repository paden schatten met behulp van de `path` parameter, bijvoorbeeld `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`.

## Volgende functies {#whats-next}

Als u eenmaal hebt geleerd hoe u zich kunt aanmelden bij Cloud Acceleration Manager en hoe u de Implementatiefase gebruikt, kunt u nu verdergaan met het evalueren van de volgende stap in het dialoogvenster [Actieve fase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-golive-phase.html?lang=en).
