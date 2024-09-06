---
title: Cloud Manager Tests - overzicht
description: Bekijk een overzicht van de drie typen tests die Cloud Manager automatisch uitvoert om de kwaliteit van uw aangepaste code te garanderen.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cfaa3be31195929b80310610120a779a20537c61
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Cloud Manager Tests - overzicht {#overview}

Cloud Manager ondersteunt drie categorieën tests voor Cloud Servicen-pijpleidingen.

1. [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)

   * Testen van de codekwaliteit evalueert de kwaliteit van uw toepassingscode.
   * De pijpleiding van de codekwaliteit wordt onmiddellijk na de bouwstap uitgevoerd in alle niet-productie- en productiepijpleidingen.
   * De [ de kwaliteitsregels van de douanecode ](/help/implementing/cloud-manager/custom-code-quality-rules.md) die door Cloud Manager worden uitgevoerd worden gecreeerd gebaseerd op beste praktijken van AEM Techniek.

1. [Functionele tests](/help/implementing/cloud-manager/functional-testing.md)

   * Het functionele testen is een deel van de stadium het testen fase van a [ productiepijplijn ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) en naar keuze deel van het testen fase van a [ niet-productiepijplijn ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

1. [Ervaring controleren testen](/help/implementing/cloud-manager/experience-audit-dashboard.md)

   * In alle Cloud Manager-productiepijpleidingen is het uitvoeren van een ervaringscontrole mogelijk en deze controle kan niet worden overgeslagen.

Deze tests kunnen:

* Door de klant geschreven
* Adobe geschreven
* Gemaakt met opensource-gereedschappen

>[!NOTE]
>
> Zowel klant-geschreven tests als Adobe-geschreven tests worden in een containerinfrastructuur in werking gesteld die voor het runnen van dergelijke tests wordt ontworpen.
