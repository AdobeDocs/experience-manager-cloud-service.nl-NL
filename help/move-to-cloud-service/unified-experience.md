---
title: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
description: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
translation-type: tm+mt
source-git-commit: c554506aea99518c94666f5d2e6151a3dce3b91e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code {#unified-experience}

De Verenigde Ervaring voor de hulpmiddelen van het Refactoring van de Code verenigt de ervaring voor uitvoering van AEM als de hulpmiddelen van het refactoring van de code van de Cloud Service die op de dossiers, de code, en bewaarplaatsen van de verzender werken.

Dit hulpmiddel vermindert de ingewikkeldheid van het gebruiken van code refactoring hulpmiddelen, met elk die verschillende uitvoeringsvereisten in termen van installatie, opstelling en uitvoering hebben.

## Voordelen {#benefits}

De verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code roept en voert alle hulpmiddelen uit van het coderefactoring die aan de broncode van de zelfde plaats werken.

De Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code samen met de bijbehorende bewaarplaatsen staat toe:

* Alle gereedschappen die werken aan de migratie van broncode naar één `node.js` toepassing die wordt weergegeven, verenigen `aio-cli plugin` om de gebruiker een consistente gebruikerservaring te bieden.

* Voorziening voor het uitvoeren van de algehele migratie via één opdracht, waarbij tevens flexibiliteit wordt geboden om één bepaald gereedschap naar behoefte uit te voeren.

* Voor het vereenvoudigen van toekomstige toevoegingen van nieuwe gereedschappen, zoals het toevoegen van een nieuw gereedschap aan de plug-in, is gewoon de toevoeging van een nieuwe opdracht voor ontwikkelaars en een eenvoudige plug-inupdate voor de gebruiker nodig. De ervaring blijft dus consistent met een hogere toegevoegde waarde.

## Inzicht krijgen in de insteekmodule {#understanding-plugin}

De `aio-cli-plugin-aem-cloud-service-migration` reactoren klanten coderen, de opslagstructuur of configuraties op de lokale computer van de klant. Op deze pagina worden de gedetailleerde vereisten en ontwerpbeslissingen voor een uniforme ervaring vastgelegd.
Het is beschikbaar als een open bron voor gemeenschap om voor douanetoepassingen uit te breiden.

Deze hulpmiddelen verenigt alle code refactoring hulpmiddelen in één die knoop.js toepassing zoals `aio-cli plugin` wordt blootgesteld om een verenigbare gebruikerservaring aan de gebruiker te verstrekken. De plug-in scant de lokale codebasis van de klant en produceert AEM als code, configuraties en pakketten die compatibel zijn met de Cloud Service en die vervolgens kunnen worden geïmplementeerd in Cloud Service-omgevingen.

De insteekmodule bestaat uit twee hoofdonderdelen:

* **Gebruikersinterface**

   `aio-cli` opdrachten om een of meer migratiehulpmiddelen uit te voeren (via een keten van gereedschappen die opeenvolgend moeten worden uitgevoerd)`config.yaml` . Hierbij worden de vereiste invoerparameters gebruikt

* **Onderliggende versie van migratiehulpprogramma**

   De migratiehulpmiddelen voeren hun functionaliteit uit door:

   * Het scannen van de respectieve sectie van de code van de klant en het uitvoeren van de migratie (gebaseerd op code-implementatie voor beste praktijken) om de output te produceren die dan kan worden bevestigd en worden opgesteld.

   * De tijdens de migratie uitgevoerde bewerkingen in een consistente volgorde opnemen om een samenvattingsrapport te maken.

## Beschikbaarheid {#availability}

U kunt de software installeren en gebruiken `aio-cli-plugin-aem-cloud-service-migration` via `aio-cli`.

>[!NOTE]
>Dit gereedschap is momenteel alleen geïntegreerd met de Dispatcher Converter.

Zie [Git Resource: aio-cli-plugin-aem-wolk-dienst-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) om over het gebruik te leren en hoe u voor deze plugin code kunt bijdragen die open-sourced in GitHub is.

