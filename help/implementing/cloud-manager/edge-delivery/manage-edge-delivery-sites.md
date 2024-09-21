---
title: Edge Delivery-sites beheren in Cloud Manager
description: Leer hoe u een CDN-configuratie toevoegt aan een Edge Delivery-site of een Edge Delivery-site verwijdert.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f684a52ca3b51d1aa4412122f7ad28dde3e2672f
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Edge Delivery-site beheren in Cloud Manager {#manage-edge-delivery-sites}

Leer hoe u Edge Delivery-sites in Cloud Manager beheert door een CDN-configuratie toe te voegen aan een bestaande site. Of verwijder een Edge Delivery-site.

## Een CDN-configuratie toevoegen aan een bestaande Edge Delivery-site {#add-cdn-to-edge-delivery-site}

Zie [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen.

## De naam van een Edge Delivery-site wijzigen (#rename-edge-delivery-site)

In Adobe Cloud Manager kunt u de naam van een Edge Delivery-site op verschillende manieren wijzigen:

* **Duidelijkheid en organisatie**: Om het doel van de plaats of zijn bijbehorende milieu (bijvoorbeeld, productie, het opvoeren) beter te beschrijven.
* **vermijdend verwarring**: Als de veelvoudige plaatsen in gebruik zijn, kan het anders noemen helpen tussen hen gemakkelijk onderscheiden, die de kans verminderen om configuraties of updates op de verkeerde plaats toe te passen.
* **Normalisatie**: Om een verenigbare noemende overeenkomst te volgen die zich op de richtlijnen van uw organisatie voor gemakkelijker beheer en controle richt.

**om een plaats van Edge Delivery anders te noemen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de naam wilt wijzigen.
Klik **anders noemen**.
   * Klik in de linkerbovenhoek van de pagina op het hamburgerpictogram om het linkernavigatiemenu weer te geven. Onder de **rubriek van de Diensten**, klik **de Plaatsen van Edge Delivery**.
Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de naam wilt wijzigen. Klik **anders noemen**.

1. In **geef de dialoogdoos van de Plaats van Edge Delivery** uit, op het **3} tekstgebied van de Naam van de Plaats {, ga de nieuwe naam van de plaats in.**

1. Klik **uitgeven**.

## Een Edge Delivery-site verwijderen {#delete-edge-delivery-site}

Als u een plaats van Edge Delivery Services schrapt, worden om het even welke bijbehorende configuraties CDN ook verwijderd. Met deze actie wordt de verbinding tussen aangepaste domeinen en de site verbroken. Zie CDN-configuraties voor meer informatie. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**om een plaats van Edge Delivery te schrappen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer het aangewezen programma.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma met gevormde Edge Delivery Services, waar u een plaats van Edge Delivery wilt toevoegen.
1. Voer een van de volgende handelingen uit:

   * Van de **pagina van het Overzicht van het Programma**, klik **Edge Delivery** tabel. Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de site wilt verwijderen.
Klik ![ de plaats van Edge Delivery van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Schrapping**, dan klik **Schrapping** opnieuw om de verwijdering van de plaats te bevestigen.

     ![ voeg de Plaats van Edge Delivery van het lusje van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * In de upper-left hoek van de pagina, klik ![ tonen of verbergen zijnavigatie ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) om het zijnavigatiemenu te openbaren. Onder de **rubriek van de Diensten**, klik ![ Web-pagina voor de plaatsen van Edge Delivery ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **de Plaatsen van Edge Delivery**.
Klik in de Edge Delivery-sitetabel op de ellips aan het einde van een rij waarvan u de site wilt verwijderen. Klik ![ de plaats van Edge Delivery van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Schrapping**, dan klik **Schrapping** opnieuw om de verwijdering van de plaats te bevestigen.

     ![ voeg de Plaats van Edge Delivery van de knoop van Plaatsen van Edge Delivery toe ](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Een ondersteuningsticket vastleggen {#eds-support-ticket}

{{support-ticket}}


