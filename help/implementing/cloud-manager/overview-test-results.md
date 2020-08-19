---
title: Overzicht van de testresultaten - Cloud Services
description: Overzicht van de testresultaten - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 16%

---


# Overzicht {#overview}

Cloud Manager for Cloud Services-pipeline-uitvoeringen ondersteunen de uitvoering van tests die worden uitgevoerd voor de stagingomgeving. Dit is in tegenstelling tot tests die tijdens de het Testen stap van de Bouwstijl en van de Eenheid worden in werking gesteld die offline, zonder toegang tot om het even welke lopende AEM milieu in werking worden gesteld.

Er zijn drie brede testcategorieën die worden ondersteund door Cloud Manager for Cloud Services Pipeline:

1. [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md)
1. [Functionele tests](/help/implementing/cloud-manager/functional-testing.md)
1. [Testen van content-controle](/help/implementing/cloud-manager/content-audit-testing.md)

Deze tests kunnen:

* Door de klant geschreven
* met Adobe geschreven
* Open source tool (aangedreven door Lighthouse van Google)

   >[!NOTE]
   > Zowel door de klant geschreven tests als Adobe geschreven tests worden uitgevoerd in een containerinfrastructuur die is ontworpen voor het uitvoeren van deze tests.

