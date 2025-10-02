---
title: Cloud Manager Tests - overzicht
description: Bekijk een overzicht van de drie typen tests die Cloud Manager automatisch uitvoert om de kwaliteit van uw aangepaste code te controleren.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ac918008c3f99d74e01be59c9841083abf3604aa
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Cloud Manager Tests - overzicht {#overview}

Er zijn drie testcategorieën die worden ondersteund door Cloud Manager for Cloud Services-pijpleidingen.

1. [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)

   * Testen van de codekwaliteit evalueert de kwaliteit van uw toepassingscode.
   * De pijpleiding van de codekwaliteit wordt onmiddellijk na de bouwstap uitgevoerd in alle niet-productie- en productiepijpleidingen.
   * De [ de kwaliteitsregels van de douanecode ](/help/implementing/cloud-manager/custom-code-quality-rules.md) die door Cloud Manager worden uitgevoerd worden gecreeerd gebaseerd op beste praktijken van de Techniek van AEM.

1. [Functionele tests](/help/implementing/cloud-manager/functional-testing.md)

   * De functionele testende looppas tijdens de stadium testende fase van a [ productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md). Het kan ook, naar keuze, tijdens de het testen fase van a [ niet-productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) lopen.

1. [Ervaring controleren testen](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   * In alle Cloud Manager-productiepijpleidingen is het uitvoeren van een ervaringscontrole mogelijk en deze controle kan niet worden overgeslagen.

Deze tests kunnen:

* Door de klant geschreven
* Adobe geschreven
* Gemaakt met opensource-gereedschappen

>[!NOTE]
>
> Zowel klant-geschreven tests als Adobe-geschreven tests worden in een containerinfrastructuur in werking gesteld die voor het runnen van dergelijke tests wordt ontworpen.
