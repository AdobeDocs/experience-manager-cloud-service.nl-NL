---
title: Een opslagplaats voor Adoben toevoegen in Cloud Manager
description: Leer hoe u een opslagplaats met beheerde Adobe in Cloud Manager toevoegt.
exl-id: 6c32c4ae-f48d-4440-bfc2-cdc1a3d59599
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f2364de6237ca9f0285815b581bcf3881488188d
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Een opslagplaats voor Adoben toevoegen in Cloud Manager {#adobe-repositories}

Leer hoe u een opslagplaats met beheerde Adobe in Cloud Manager toevoegt.

De **pagina van Bewaarplaatsen** maakt het gemakkelijk om extra Adobe-geleide bewaarplaatsen aan een geselecteerd programma toe te voegen.

**om een bewaarplaats van de Adobe in Cloud Manager toe te voegen:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie en het programma waaraan u een Adobe-beheerde bewaarplaats wilt toevoegen.

1. Van de **pagina van het Overzicht van het Programma**, in het zijmenu, klik ![&#x200B; het pictogram van de Omslag &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Bewaarplaatsen** tabel.

1. Op de **pagina van Bewaarplaatsen**, dichtbij het hoger-recht, klik **Add Bewaarplaats**.

   ![&#x200B; toevoegen de knoop van de gegevensopslagplaats &#x200B;](assets/add-repository.png)

1. In **voeg de dialoogdoos van de Bewaarplaats** toe, zorg ervoor dat **Repository van de Adobe** als bewaarplaatstype wordt geselecteerd.

1. Voer in de desbetreffende tekstvelden het volgende in:

   * **Naam van de Bewaarplaats** - een expressieve naam voor uw nieuwe bewaarplaats.
   * **Bewaarplaats URL voorproef** - u te hoeven niet om een weg in te gaan URL of de bestaande weg uit te geven omdat de gegevensopslaginfrastructuur reeds op zijn plaats is en volledig geïntegreerd en door Adobe wordt geleid.
   * **Beschrijving (facultatief)** - een gedetailleerde beschrijving van de bewaarplaats.

   ![&#x200B; voeg de dialoogdoos van de Bewaarplaats &#x200B;](assets/add-adobe-repository.png) toe

1. Klik **sparen**.
Uw nieuwe bewaarplaats wordt getoond in de lijst op de **pagina van Bewaarplaatsen**.

U kunt a [&#x200B; CI/CD pijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) met het nu associëren of het binnen de [**Opslagplaatsen** pagina &#x200B;](managing-repositories.md) beheren.

>[!TIP]
>
>U kunt bewaarplaatsen ook toevoegen GitHub die u als [&#x200B; privé bewaarplaatsen &#x200B;](private-repositories.md) beheert.
