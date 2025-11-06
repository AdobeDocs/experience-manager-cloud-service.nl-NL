---
title: Een Edge Delivery Pipeline toevoegen
description: Leer hoe u een Edge Delivery-pijplijn toevoegt om uw code te maken en te implementeren in productieomgevingen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
hide: false
index: false
hidefromtoc: false
exl-id: 5ad342fa-dd71-4105-a9cb-2d999d402780
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Een Edge Delivery-pijpleiding toevoegen {#configure-production-pipeline}

<!--badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket" -->

Leer hoe u Edge Delivery-pijpleidingen configureert voor het maken en implementeren van uw code in productieomgevingen. De pijpleidingen van Edge Delivery laten u eigenschappen met inbegrip van logboek het door:sturen en Adobe-Beheerde CDN vormen.

Voor een lijst van gesteunde configuratie, zie [&#x200B; Gebruik config pijpleidingen - gesteunde configuraties &#x200B;](/help/operations/config-pipeline.md#configurations).

Een gebruiker moet de **[rol hebben van de Manager van de Plaatsing 0&rbrace; om productiepijpleidingen te vormen.](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)**

>[!IMPORTANT]
>
>Een pijpleiding van Edge Delivery kan niet worden gevormd tot het volgende is gebeurd:
>
>* Er wordt een programma gemaakt dat één Edge Delivery Services-site en één toegewezen domein bevat. Anders, verschijnt de geroepen optie **voegt de Pijpleiding van Edge Delivery** gehandicapt in het gebruikersinterface toe, en tooltip verklaart ontbrekende vereisten. Zie [&#x200B; een plaats van Edge Delivery in Cloud Manager &#x200B;](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md) creëren
>* De Git-opslagplaats heeft minstens één vertakking. Zie [&#x200B; Beheers Bewaarplaatsen in Cloud Manager &#x200B;](/help/implementing/cloud-manager/managing-code/managing-repositories.md).
>* De productie- en staging-omgevingen worden gemaakt. Zie [&#x200B; Inleiding aan CI/CD Pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

<!-- CMGR‑69680 -->

Alvorens u begint om uw code op te stellen, vorm uw pijpleidingsmontages van [!UICONTROL Cloud Manager].

>[!NOTE]
>
>U kunt [&#x200B; pijpleidingsmontages &#x200B;](managing-pipelines.md) na de aanvankelijke configuratie uitgeven.

**om een pijpleiding van Edge Delivery toe te voegen:**

1. Teken in Cloud Manager bij [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com).
1. In de **Snelle toegang** sectie, klik **Experience Manager**.
1. In het linkerzijpaneel, klik **Cloud Manager**.
1. Selecteer de gewenste organisatie.
1. Op de **Mijn console van Programma&#39;s**, klik een programma.

   ![&#x200B; Mijn programmapagina in Cloud Manager &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/my-programs.png)

1. Voer een van de volgende handelingen uit:

   * **voeg een pijpleiding van Edge Delivery van de kaart van Pijpleidingen toe**

      1. In het linkerspoor, onder **Programma**, klik **![pictogram van het Overzicht &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) [&#x200B; Overzicht](/help/implementing/cloud-manager/navigation.md#my-programs)**.
      1. Op de **pagina van het Overzicht van het 0&rbrace; Programma, onder de** Pijpleidingen **kaart, klik** plus teken **![toevoegen &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg), dan uitgezocht** voeg de Pijpleiding van Edge Delivery toe **.**

         ![&#x200B; de kaart van Pijpleidingen op de pagina van het Overzicht van het Programma &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinescard-add-ed-pipeline.png)

         >[!TIP]
         >
         >Naast het gebruiken van de **kaart van de Pijpleiding** zoals die in het scherm hierboven wordt gezien, kunt u uw pijpleiding van de **Pijpleidingen** pagina ook beheren.
         >
         >![&#x200B; Edge Delivery pijpleiding widget die pijpleidingsnaam, status, bewaarplaats, en tak tonen &#x200B;](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

   * **voeg een pijpleiding van Edge Delivery van de pagina van Pijpleidingen toe**

      1. In het linkerspoor, onder **Programma**, klik **![pictogram van het Werkschema of het pictogram van Pijpleidingen &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) Pijpleidingen**.
      1. Voor de pagina van Pijpleidingen, dichtbij de hoger-juiste hoek, klik **toevoegen Pijpleiding** > **voeg de Pijpleiding van Edge Delivery** toe.

         ![&#x200B; de pagina van Pijpleidingen met Add knoop van de Pijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinespage-add-ed-pipeline.png)

         >[!TIP]
         >
         >Vlak de upper-left hoek, klik **Filters**, dan onder de **het type van Levering** sectie, selecteer **de levering van Edge** checkbox om de lijst aan slechts de pijpleidingen van Edge Delivery (namelijk pijpleidingen te filtreren die Edge Delivery Services gebruiken). <!-- (CMGR-69682) -->
         >
         >![&#x200B; paneel die van de Filter het nieuwe type van Levering van Edge toont levering en publiceert levering &#x200B;](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

1. In **voeg de dialoogdoos van de Pijpleiding van Edge Delivery** toe, op het **de tekstgebied van de Naam van de Pijpleiding**, typ een beschrijvend pijpleidingsetiket.

   ![&#x200B; voeg de dialoogdoos van de Pijpleiding van Edge Delivery toe &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-configuration.png)

1. Selecteer de optie van de trekker van de Plaatsing van de pijpleiding **&#x200B;**&#x200B;die u wilt.

   * **Hand** - u begint de plaatsing.
   * **op de Veranderingen van het Git** - het begin van het Git de plaatsing automatisch. Met deze optie, kunt u de pijpleiding nog manueel, indien nodig beginnen.

1. Klik **verdergaan**.

1. Onder **Code van Source**, plaats de volgende opties:

   * **Milieu van de Plaatsing** - toont het gebied van het doelmilieu; blijft read-only.

   * **Bewaarplaats** - gebruik de drop-down lijst om de pijpleiding bij de nauwkeurige bewaarplaats van het Git te richten die de configuratie van Edge Delivery opslaat.

     Zie ook [&#x200B; bewaarplaatsen &#x200B;](/help/implementing/cloud-manager/managing-code/managing-repositories.md) toevoegen en beheren om te leren hoe te om bewaarplaatsen in Cloud Manager toe te voegen en te beheren.

   * **de Tak van de Git** - gebruik de drop-down lijst om een specifieke tak binnen de gekozen bewaarplaats te selecteren. Indien noodzakelijk, klik ![&#x200B; pictogram van de Recycling of verfrissen pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) om de de takdrop-down lijst van de it na recente duwen opnieuw te laden.
   * **Plaats van de Code** - bepaalt de omslagweg binnen de bewaarplaats waar de pijpleiding-klaar code begint ( `/` evenaart de bewaarplaatswortel).

   ![&#x200B; Config pijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-sourcecode.png)

1. Klik **sparen**.

U kunt nu [&#x200B; uw pijpleiding &#x200B;](managing-pipelines.md) van de **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma**, of van de **pagina van de Pijpleidingen** beheren.


![&#x200B; Edge Delivery pijpleiding widget die pijpleidingsnaam, status, bewaarplaats, en tak tonen &#x200B;](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)



