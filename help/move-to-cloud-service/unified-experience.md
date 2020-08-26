---
title: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
description: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
translation-type: tm+mt
source-git-commit: ae60d0b472ed6368aeb5806329ff1d5c689e0827
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code {#unified-experience}

Wij hebben hulpmiddelen ontwikkeld om sommige code te automatiseren refactoring taken die worden vereist om met AEM als Cloud Service compatibel te zijn. Om de ingewikkeldheid te verminderen verbonden aan installatie en opstelling van verschillende code refactoring hulpmiddelen, hebben wij een stop ontwikkeld om hulpmiddelen te verenigen die op code en bewaarplaatsen werken.

## Voordelen {#benefits}

De Unified Experience plug-in biedt de volgende voordelen:

* Hiermee verenigt u gereedschappen die werken aan broncode in één `node.js` toepassing die als `aio-cli ` plug-in wordt weergegeven, zodat de gebruiker een consistente gebruikerservaring krijgt.

* Biedt de mogelijkheid om alle gereedschappen uit te voeren via één opdracht en biedt tegelijkertijd de flexibiliteit om desgewenst specifieke gereedschappen uit te voeren.

* Verstrekt rekbaarheid om toevoeging van nieuwe hulpmiddelen te vereenvoudigen, terwijl het houden van de ervaring verenigbaar.

## Inzicht krijgen in de insteekmodule {#understanding-plugin}

De `aio-cli-plugin-aem-cloud-service-migration` insteekmodule bestaat uit twee hoofdonderdelen:

* **Gebruikersinterface**

   * `aio-cli` opdrachten voor het uitvoeren van een of meer gereedschappen voor het vernieuwen van code (via een keten van gereedschappen die opeenvolgend moeten worden uitgevoerd).
   * `config.yaml` waarbij de vereiste invoerparameters worden gebruikt.

* **De onderliggende Reeks van het Hulpmiddel van de Refactoring van de Code**

   De coderefactoring hulpmiddelen voeren hun functionaliteit door uit:

   * Het scannen van de respectieve sectie van de code van de klant en het manipuleren van de code (die op code implementatie voor beste praktijken wordt gebaseerd) om de output te veroorzaken die dan kan worden bevestigd en worden opgesteld.

   * Een samenvattingsrapport maken om de tijdens de uitvoering uitgevoerde bewerkingen op te nemen.

## Beschikbaarheid {#availability}

Zie [Git Resource: aio-cli-plugin-aem-wolk-dienst-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) om over het gebruik te leren en hoe u aan deze plugin code kunt bijdragen die open-sourced in GitHub is.

>[!NOTE]
>Momenteel is alleen de Dispatcher Converter geïntegreerd met de plug-in.
