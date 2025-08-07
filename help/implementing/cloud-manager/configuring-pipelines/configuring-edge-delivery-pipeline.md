---
title: Een Edge Delivery Pipeline toevoegen
description: Leer hoe u een Edge Delivery-pijplijn toevoegt om uw code te maken en te implementeren in productieomgevingen.
index: false
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Private bèta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: false
hidefromtoc: false
source-git-commit: 96a619c6ab8f71034914b72a57bdb1e7f363fbc6
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# Een Edge Delivery-pijpleiding toevoegen {#configure-production-pipeline}

Leer hoe u Edge Delivery-pijpleidingen configureert voor het maken en implementeren van uw code in productieomgevingen. Een productiepijpleiding stelt code eerst aan het werkgebiedmilieu op. Bij goedkeuring, stelt het de zelfde code aan het productiemilieu op.

Een gebruiker moet de **[rol hebben van de Manager van de Plaatsing 0} om productiepijpleidingen te vormen.](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)**

>[!NOTE]
>
>Een pijpleiding van Edge Delivery kan niet worden gevormd tot het volgende is gebeurd:
>
>* Er wordt een programma gemaakt dat één Edge Delivery Services-site en één toegewezen domein bevat. Anders, voegt de optie **de Pijpleiding van Edge Delivery** toe verschijnt gehandicapt in het gebruikersinterface, en tooltip verklaart ontbrekende vereisten. <!-- CMGR‑69680 -->
>* De Git-opslagplaats heeft minstens één vertakking.
>* De productie- en staging-omgevingen worden gemaakt.

Alvorens u begint om uw code op te stellen, vorm uw pijpleidingsmontages van [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt [ pijpleidingsmontages ](managing-pipelines.md) na de aanvankelijke configuratie uitgeven.

**om een pijpleiding van Edge Delivery toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de organisatie u wilt.

1. Voor **Mijn pagina van Programma&#39;s**, selecteer het programma u wilt.

   ![ Mijn programmapagina in Cloud Manager ](/help/implementing/cloud-manager/configuring-pipelines/assets/my-programs.png)

1. Voer een van de volgende handelingen uit:

   * **voeg een pijpleiding van Edge Delivery van de kaart van Pijpleidingen toe**

      1. In het linkerspoor, onder **Programma**, klik **![pictogram van het Overzicht ](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) [ Overzicht](/help/implementing/cloud-manager/navigation.md#my-programs)**.
      1. Op de **pagina van het Overzicht van het 0} Programma, onder de** Pijpleidingen **kaart, klik** plus teken **![toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg), dan uitgezocht** voeg de Pijpleiding van Edge Delivery toe **.**

         ![ de kaart van Pijpleidingen op de pagina van het Overzicht van het Programma ](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinescard-add-ed-pipeline.png)

   * **voeg een pijpleiding van Edge Delivery van de pagina van Pijpleidingen toe**

      1. In het linkerspoor, onder **Programma**, klik **![pictogram van het Werkschema of het pictogram van Pijpleidingen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) Pijpleidingen**.
      1. Voor de pagina van Pijpleidingen, dichtbij de hoger-juiste hoek, klik **toevoegen Pijpleiding** > **voeg de Pijpleiding van Edge Delivery** toe.

         ![ de pagina van Pijpleidingen met Add knoop van de Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinespage-add-ed-pipeline.png)

1. In **voeg de dialoogdoos van de Pijpleiding van Edge Delivery** toe, op het **de tekstgebied van de Naam van de Pijpleiding**, typ een beschrijvend pijpleidingsetiket.

   ![ voeg de dialoogdoos van de Pijpleiding van Edge Delivery toe ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-configuration.png)

1. Selecteer de optie van de trekker van de Plaatsing van de pijpleiding **** u wilt.

   * **Hand** - u begint de plaatsing.
   * **op de Veranderingen van het Git** - het begin van het Git de plaatsing automatisch. Met deze optie, kunt u de pijpleiding nog manueel, indien nodig beginnen.

1. Klik **verdergaan**.

1. Onder **Code van Source**, plaats de volgende opties:

   * **Milieu van de Plaatsing** - toont het gebied van het doelmilieu; blijft read-only.

   * **Bewaarplaats** - gebruik de drop-down lijst om de pijpleiding bij de nauwkeurige bewaarplaats van het Git te richten die de configuratie van Edge Delivery opslaat.

     Zie ook [ bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) toevoegen en beheren om te leren hoe te om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **de Tak van de Git** - gebruik de drop-down lijst om een specifieke tak binnen de gekozen bewaarplaats te selecteren. Indien noodzakelijk, klik ![ pictogram van de Recycling of verfrissen pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) om de de takdrop-down lijst van de Plaats na recente duwen opnieuw te laden
   * **Plaats van de Code** - bepaalt de omslagweg binnen de bewaarplaats waar de pijpleiding-klaar code begint ( `/` evenaart de bewaarplaatswortel).

   ![ Config pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-sourcecode.png)

1. Klik **sparen**.

U kunt nu [ uw pijpleiding ](managing-pipelines.md) op de **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** of van de **pagina van de Pijpleidingen** beheren.
