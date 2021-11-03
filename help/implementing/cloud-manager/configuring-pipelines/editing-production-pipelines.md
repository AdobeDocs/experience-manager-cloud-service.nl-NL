---
title: Een productiepijpleiding bewerken
description: Een productiepijpleiding bewerken
index: false
source-git-commit: 881b4d75a15af55aaf1203e8d673059aab15b793
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Een productiepijpleiding bewerken {#edit-prod-pipeline}

U kunt de pijpleidingsconfiguraties van de **Programmaoverzicht** pagina.

>[!IMPORTANT]
>U kunt geen pijpleiding uitgeven die loopt.

Volg de stappen hieronder om de gevormde pijpleiding uit te geven:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Bewerken**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. De **Productiepijpleiding bewerken** wordt weergegeven.

   1. De **Configuratie** kunt u de **Naam pijpleiding**, **Implementatieactivering**, en **Gedrag belangrijke metrische fout**.

      >[!NOTE]
      >Zie [Opslagplaatsen toevoegen en beheren](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) voor meer informatie over het toevoegen en beheren van opslagruimten in Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. De **Bron** biedt u een optie voor het in- of uitschakelen **Pauzeren vóór implementatie naar productie** en **Gepland** opties van **Implementatieopties voor productie**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. De **Experience Audit** kunt u nieuwe pagina&#39;s bijwerken of toevoegen.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Klikken op **Bijwerken** zodra u klaar bent met het bewerken van de pijplijn.

## Aanvullende acties voor productiepijpleiding {#additional-prod-actions}

### Een productiepijpleiding uitvoeren {#run-prod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen in werking stellen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Uitvoeren**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

### Een productiepijpleiding verwijderen {#delete-prod}

U kunt de productiepijpleiding van de kaart van Pijpleidingen schrappen:

1. Navigeren naar **Pijpleidingen** kaart van **Programmaoverzicht** pagina.

1. Klikken op **...** van de **Pijpleidingen** kaart en klik op **Verwijderen**, zoals weergegeven in onderstaande afbeelding.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via **Verwijderen** optie van de kaart van de Pijpleiding.