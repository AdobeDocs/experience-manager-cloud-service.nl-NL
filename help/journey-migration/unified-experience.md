---
title: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
description: Leer over Verenigde Ervaring voor de Hulpmiddelen van het Refactoring van de Code.
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code {#unified-experience}

Wij hebben hulpmiddelen ontwikkeld om sommige code te automatiseren refactoring taken die worden vereist om met AEM as a Cloud Service compatibel te zijn. Om de ingewikkeldheid te verminderen verbonden aan installatie en opstelling van verschillende code refactoring hulpmiddelen, hebben wij een stop ontwikkeld om hulpmiddelen te verenigen die op code en bewaarplaatsen werken.

## Voordelen {#benefits}

De Unified Experience plug-in biedt de volgende voordelen:

* Hiermee verenigt u gereedschappen die werken aan broncode in één code `node.js` toepassing blootgesteld aan `aio-cli ` om de gebruiker een consistente gebruikerservaring te bieden.

* Biedt de mogelijkheid om alle gereedschappen uit te voeren via één opdracht en biedt tegelijkertijd de flexibiliteit om desgewenst specifieke gereedschappen uit te voeren.

* Verstrekt rekbaarheid om toevoeging van nieuwe hulpmiddelen te vereenvoudigen, terwijl het houden van de ervaring verenigbaar.

## Inzicht krijgen in de insteekmodule {#understanding-plugin}

De `aio-cli-plugin-aem-cloud-service-migration` insteekmodule bestaat uit twee hoofdonderdelen:

* **Gebruikersinterface**

   * `aio-cli` opdrachten voor het uitvoeren van een of meer gereedschappen voor het vernieuwen van code (via een keten van gereedschappen die opeenvolgend moeten worden uitgevoerd).
   * `config.yaml` die de vereiste invoerparameters in beslag neemt.

* **De onderliggende Reeks van het Hulpmiddel van de Refactoring van de Code**

  De coderefactoring hulpmiddelen voeren hun functionaliteit door uit:

   * Het scannen van de respectieve sectie van de code van de klant en het manipuleren van de code (die op code implementatie voor beste praktijken wordt gebaseerd) om de output te veroorzaken die dan kan worden bevestigd en worden opgesteld.

   * Een samenvattingsrapport maken om de tijdens de uitvoering uitgevoerde bewerkingen op te nemen.

## Beschikbaarheid {#availability}

Zie [Git-bron: audio-cli-plugin-aem-cloud-service-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) om over het gebruik te leren en hoe u aan deze plugin code kunt bijdragen die open gesourced in GitHub is.

>[!NOTE]
>De plug-in is momenteel geïntegreerd met AEM Dispatcher Converter en Repository Modernizer.
