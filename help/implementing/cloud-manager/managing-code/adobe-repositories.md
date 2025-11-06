---
title: Een Adobe-opslagplaats toevoegen in Cloud Manager
description: Leer hoe u een door Adobe beheerde opslagplaats in Cloud Manager toevoegt.
exl-id: 6c32c4ae-f48d-4440-bfc2-cdc1a3d59599
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Een Adobe-opslagplaats toevoegen in Cloud Manager {#adobe-repositories}

Leer hoe u een door Adobe beheerde opslagplaats in Cloud Manager toevoegt.

De **pagina van Bewaarplaatsen** maakt het gemakkelijk om extra Adobe-Beheerde bewaarplaatsen aan een geselecteerd programma toe te voegen.

**om een bewaarplaats van Adobe in Cloud Manager toe te voegen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie en het programma waaraan u een Adobe-Beheerde bewaarplaats wilt toevoegen.

1. Van de **pagina van het Overzicht van het Programma**, in het zijmenu, klik ![ het pictogram van de Omslag ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Bewaarplaatsen** tabel.

1. Op de **pagina van Bewaarplaatsen**, dichtbij het hoger-recht, klik **Add Bewaarplaats**.

   ![ toevoegen de knoop van de gegevensopslagplaats ](assets/add-repository.png)

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, zorg ervoor dat **de Bewaarplaats van Adobe** als bewaarplaatstype wordt geselecteerd.

1. Voer in de desbetreffende tekstvelden het volgende in:

   * **Naam van de Bewaarplaats** - een expressieve naam voor uw nieuwe bewaarplaats.
   * **Bewaarplaats URL voorproef** - u te hoeven niet om een weg in te gaan URL of de bestaande weg uit te geven omdat de bewaarplaatsinfrastructuur reeds op zijn plaats en volledig geïntegreerd en door Adobe wordt geleid.
   * **Beschrijving (facultatief)** - een gedetailleerde beschrijving van de bewaarplaats.

   ![ voeg de dialoogdoos van de Bewaarplaats ](assets/add-adobe-repository.png) toe

1. Klik **sparen**.
Uw nieuwe bewaarplaats wordt getoond in de lijst op de **pagina van Bewaarplaatsen**.

U kunt a [ CI/CD pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) met het nu associëren of het binnen de [**Opslagplaatsen** pagina ](managing-repositories.md) beheren.

>[!TIP]
>
>U kunt bewaarplaatsen ook toevoegen GitHub die u als [ privé bewaarplaatsen ](private-repositories.md) beheert.
