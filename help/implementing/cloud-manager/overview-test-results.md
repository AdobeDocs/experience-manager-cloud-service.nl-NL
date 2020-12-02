---
title: Overzicht van de testresultaten - Cloud Services
description: Overzicht van de testresultaten - Cloud Services
translation-type: tm+mt
source-git-commit: d03ef0afe91760e35ef4e8fb3e3f2c833cbf945c
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Overzicht {#overview}

Er zijn drie brede testcategorieën die worden ondersteund door Cloud Manager for Cloud Services Pipeline:

1. [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)

   Het testen van de Kwaliteit van de Code evalueert de kwaliteit van uw toepassingscode. De code-Kwaliteit pijpleiding wordt uitgevoerd onmiddellijk na de bouwstap in alle niet-productie en productiepijpleidingen.

   De [Custom Code Quality Rules](/help/implementing/cloud-manager/custom-code-quality-rules.md) die door Cloud Manager worden uitgevoerd, worden gemaakt op basis van de beste werkwijzen van AEM Engineering.

1. [Functionele tests](/help/implementing/cloud-manager/functional-testing.md)

   De functionele tests maken deel uit van de testfase van het werkgebied van een productiepijpleiding.

1. [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md)

   Het testen van de Controle van de Ervaring wordt toegelaten in alle de productiepijpleidingen van de Manager van de Wolk en kan niet worden overgeslagen.

Deze tests kunnen:

* Door de klant geschreven
* met Adobe geschreven
* Brongereedschap openen

   >[!NOTE]
   > Zowel door de klant geschreven tests als Adobe geschreven tests worden uitgevoerd in een containerinfrastructuur die is ontworpen voor het uitvoeren van deze tests.

