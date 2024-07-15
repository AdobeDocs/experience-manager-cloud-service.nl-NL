---
title: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
description: Leer over Verenigde Ervaring voor de Hulpmiddelen van het Refactoring van de Code.
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code {#unified-experience}

De Adobe heeft hulpmiddelen ontwikkeld om sommige code te automatiseren refactoring taken die worden vereist om met as a Cloud Service Adobe Experience Manager (AEM) compatibel te zijn. Om de ingewikkeldheid te verminderen verbonden aan de installatie en opstelling van verschillende code het refactoring hulpmiddelen, heeft de Adobe een stop-in ontwikkeld om hulpmiddelen te verenigen die op code en bewaarplaatsen werken.

## Voordelen {#benefits}

De Unified Experience plug-in biedt de volgende voordelen:

* Hiermee verenigt u gereedschappen die werken aan broncode in één `node.js` -toepassing die als `aio-cli ` -plug-in wordt weergegeven, zodat de gebruiker een consistente gebruikerservaring krijgt.

* Voert alle hulpmiddelen als één enkel bevel in werking, terwijl ook het verstrekken van de flexibiliteit om specifieke hulpmiddelen in werking te stellen zoals nodig.

* Vereenvoudigt de toevoeging van nieuwe hulpmiddelen, terwijl het houden van de ervaring verenigbaar.

## Inzicht krijgen in de insteekmodule {#understanding-plugin}

De `aio-cli-plugin-aem-cloud-service-migration` -plug-in bestaat uit twee hoofdonderdelen:

* **Gebruikersinterface**

   * `aio-cli` -opdrachten om een of meer gereedschappen voor het refactoring van code uit te voeren (door een keten van gereedschappen die opeenvolgend moeten worden uitgevoerd).
   * `config.yaml` dat de vereiste invoerparameters opneemt.

* **Onderliggende Reeks van het Hulpmiddel van het Refactoring van de Code**

  De coderefactoring hulpmiddelen voeren hun functionaliteit door uit:

   * Het scannen van de respectieve sectie van de code van de klant en het manipuleren van de code (die op code implementatie voor beste praktijken wordt gebaseerd) om de output te veroorzaken die dan kan worden bevestigd en worden opgesteld.

   * Een samenvattingsrapport maken om de tijdens de uitvoering uitgevoerde bewerkingen op te nemen.

## Beschikbaarheid {#availability}

Zie {het Middel van 0} Git: ao-cli-stop-aem-wolk-dienst-migratie ](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) waar u over gebruik kunt leren en hoe u aan deze insteekcode kunt bijdragen die in GitHub open-sourced is.[

>[!NOTE]
>De insteekmodule is momenteel geïntegreerd met AEM Dispatcher Converter en Repository Modernizer.
