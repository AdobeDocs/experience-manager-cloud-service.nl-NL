---
title: Overzicht van tests in Cloud Manager
description: Bekijk een overzicht van de drie typen tests die automatisch worden uitgevoerd in Cloud Manager om de kwaliteit van uw aangepaste code te garanderen.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
source-git-commit: a9303c659730022b7417fc9082dedd26d7cbccca
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Overzicht van tests in Cloud Manager {#overview}

Er zijn drie testcategorieën die worden ondersteund door Cloud Manager voor Cloud Services-pijpleidingen.

1. [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)

   * Testen van de codekwaliteit evalueert de kwaliteit van uw toepassingscode.
   * De pijpleiding van de codekwaliteit wordt onmiddellijk na de bouwstap uitgevoerd in alle niet-productie- en productiepijpleidingen.
   * De [aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md) uitgevoerd door Cloud Manager worden gemaakt op basis van de beste werkwijzen van AEM Engineering.

1. [Functionele tests](/help/implementing/cloud-manager/functional-testing.md)

   * Functionele tests maken deel uit van de testfase van een productiepijpleiding.

1. [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md)

   * Het testen van de ervaringscontrole is ingeschakeld in alle productiepijpleidingen van Cloud Manager en kan niet worden overgeslagen.

Deze tests kunnen:

* Door de klant geschreven
* met Adobe geschreven
* Gemaakt met opensource-gereedschappen

>[!NOTE]
>
> Zowel klant-geschreven tests als Adobe-geschreven tests worden in een containerinfrastructuur in werking gesteld die voor het runnen van dergelijke tests wordt ontworpen.
