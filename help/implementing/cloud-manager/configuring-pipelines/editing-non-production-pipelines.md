---
title: Een niet-productiepijplijn bewerken
description: Een niet-productiepijplijn bewerken
index: true
source-git-commit: d090329c46155d77a7b132583c777c09555a03c9
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Een niet-productiepijplijn bewerken {#edit-non-prod-pipeline}

U kunt de pijpleidingsconfiguraties van de **Pipelkaart** van **Programmaoverzicht** pagina.

>[!IMPORTANT]
>U kunt geen pijpleiding uitgeven die loopt.

Voer de onderstaande stappen uit om de geconfigureerde niet-productiepijplijn te bewerken:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Selecteer de niet-productiepijplijn en klik op **...**. Klikken op **Bewerken**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. De **Productiepijpleiding bewerken** wordt weergegeven.

   1. De **Configuratie** kunt u de **Naam pijpleiding**, **Implementatieactivering**, en **Belangrijk gedrag metrische fouten**.

      >[!NOTE]
      >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. De **Broncode** tabblad geeft u de **Bewaarplaats** en de **Git Branch**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Klikken op **Bijwerken** als u klaar bent met het bewerken van de niet-productiepijplijn.

## Aanvullende niet-productie pijplijnhandelingen {#additional-nonprod-actions}

### Een niet-productiepijpleiding uitvoeren {#run-nonprod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen in werking stellen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Uitvoeren**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

#### Schrapping van een niet-productiepijpleiding {#delete-nonprod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen schrappen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Verwijderen**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)
