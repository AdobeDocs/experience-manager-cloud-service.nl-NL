---
title: Een niet-productiepijpleiding configureren
description: Volg deze pagina om over het Vormen van een niet-Productiepijpleiding in de Manager van de Wolk te leren
index: true
source-git-commit: d090329c46155d77a7b132583c777c09555a03c9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Een niet-productiepijpleiding configureren {#configure-non-production-pipeline}

Naast de hoofdpijpleiding die zich naar het stadium en de productie ontwikkelt, kunnen klanten extra pijpleidingen opzetten, die niet-productiepijpleidingen worden genoemd.

Er zijn twee soorten niet-productiepijpleidingen:

1. Codekwaliteit: Hiermee wordt de codekwaliteit gescand op de code in de git-vertakking. Deze pijpleiding voert de bouw en de stappen van de codekwaliteit uit.
1. Implementatie: Naast het uitvoeren van de bouw en de stappen van de codekwaliteit, stelt deze pijpleiding de code aan geselecteerde niet-productie aan AEM as a Cloud Service milieu op.

## Een nieuwe niet-productiepijplijn toevoegen {#adding-non-production-pipeline}

Op het thuisscherm worden deze pijpleidingen op een nieuwe kaart vermeld:

1. Toegang krijgen tot **Pijpleidingen** kaart van het startscherm van Cloud Manager. Klikken op **+Toevoegen** en selecteert u **Niet-productiepijpleiding toevoegen**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Niet-productiepijpleiding toevoegen**  wordt weergegeven. Selecteer het type pijpleiding u wilt creëren, of **Codekwaliteit, pijplijn** of **Implementatiepijp**.

   >[!NOTE]
   >Voor de pijpleidingen van de Plaatsing, moet u het plaatsingsmilieu selecteren.

   Bovendien kunt u ook instellen **Implementatieactivering** en **Belangrijk gedrag metrische fouten** van **Implementatieopties**. Klikken op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. Selecteren **[Volledige stapelcode](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** of **[Code frontend](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. U kunt de **Bewaarplaats** en de **Git Branch**. Klikken op **Opslaan**.

   >[!IMPORTANT]
   >Als er al een pijplijn met volledige stapelcode bestaat voor de geselecteerde omgeving, wordt deze selectie uitgeschakeld.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-confignew1.png)

   >[!NOTE]
   >Voordat u begint met het configureren van de voorste-eindpijplijnen, raadpleegt u [Reis voor snel maken van site AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites-journey/quick-site/overview.html) voor een end-to-end workflow met het gebruiksvriendelijke AEM gereedschap Snel site maken. Met deze documentatiesite kunt u de front-end ontwikkeling van uw AEM Site stroomlijnen en uw site snel aanpassen zonder AEM kennis van de back-end.

1. De nieuwe niet-productiepijplijn wordt nu weergegeven in de **Pijpleidingen** kaart.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   De pijpleiding wordt getoond op de kaart op het huisscherm met drie acties, zoals hieronder getoond:

   * **Toevoegen** - staat toe dat een nieuwe pijpleiding wordt toegevoegd.
   * **Repo-info openen** - stelt de gebruiker in staat de informatie op te halen die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager Git.
   * **Meer informatie** - navigeert naar inzicht in de bron van de Documentatie van de CI/CD-pijpleiding.