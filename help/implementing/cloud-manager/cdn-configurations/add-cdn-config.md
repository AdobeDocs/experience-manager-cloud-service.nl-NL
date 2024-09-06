---
title: Een CDN-configuratie toevoegen
description: Leer over hoe te om een configuratie CDN voor een plaats van Edge Delivery of een milieu van Cloud Manager toe te voegen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: e57a6ceb2482e61acabe928da0f539d26989985c
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Een CDN-configuratie toevoegen {#add-cdn}

Het toevoegen van een configuratie CDN moet worden voltooid om een domein met SSL te vormen.

>
>
>Voor Adobe-geleide CDNs, wanneer het gebruiken van DV certificaten, slechts worden de plaatsen met de bevestiging van ACME toegelaten.

**om een configuratie toe te voegen CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik **configuraties CDN**.

1. Bij de hoger-juiste hoek van de CDN pagina van Configuraties, voegt de klik **** toe.

   ![ vorm CDN dialoogdoos ](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

1. In **vorm CDN** dialoogdoos, verstrek de noodzakelijke informatie.

   * Van de **drop-down lijst van de Oorsprong 0}, doe één van het volgende:**
      * **Plaatsen:** selecteer een plaats van Edge Delivery Services.
      * **Milieu&#39;s:** selecteer een milieu van de Cloud Service.
         * **Rij:** selecteer a **Publish** of **Voorproef** Webrij voor het geselecteerde milieu.
   * Selecteer uw type CDN: **beheerde Adobe CDN** of **Andere leverancier CDN**.
   * Selecteer het domein.
   * Selecteer het SSL-certificaat. Slechts vereist als u **Adobe beheerde CDN** als uw type CDN selecteerde.

1. Klik **sparen**.




