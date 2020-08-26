---
title: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
description: Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code
translation-type: tm+mt
source-git-commit: c00b10b4d564e05099740b9ff991624db4f37a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code {#unified-experience}

Meerdere gereedschappen met verschillende interactiepunten voor klanten zorgen voor een ongekoppelde ervaring en vergroten de complexiteit van het gebruik van gereedschappen, waarbij elk gereedschap verschillende uitvoeringsvereisten heeft wat betreft installatie, installatie en uitvoering.

## Voordelen {#benefits}

De verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code roept en voert alle hulpmiddelen uit van het coderefactoring die aan de broncode van de zelfde plaats werken.

De Verenigde Ervaring voor de Hulpmiddelen van de Refactoring van de Code samen met de bijbehorende bewaarplaatsen staat toe:

* Alle gereedschappen die werken aan de migratie van broncode naar één `node.js` toepassing die wordt weergegeven, verenigen `aio-cli plugin` om de gebruiker een consistente gebruikerservaring te bieden.

* Voorziening voor het uitvoeren van de algehele migratie via één opdracht, waarbij tevens flexibiliteit wordt geboden om één bepaald gereedschap naar behoefte uit te voeren.

* Voor het vereenvoudigen van toekomstige toevoegingen van nieuwe gereedschappen, zoals het toevoegen van een nieuw gereedschap aan de plug-in, is gewoon de toevoeging van een nieuwe opdracht voor ontwikkelaars en een eenvoudige plug-inupdate voor de gebruiker nodig. De ervaring blijft dus consistent met een hogere toegevoegde waarde.

### Het toepassingsontwerp begrijpen

Deze hulpmiddelen verenigt alle code refactoring hulpmiddelen in één die knoop.js toepassing zoals `aio-cli plugin` wordt blootgesteld om een verenigbare gebruikerservaring aan de gebruiker te verstrekken.

De insteekmodule bestaat uit twee hoofdonderdelen:

* **Gebruikersinterface**

   `aio-cli` opdrachten om een of meer migratiehulpmiddelen uit te voeren (via een keten van gereedschappen die opeenvolgend moeten worden uitgevoerd)`config.yaml` . Hierbij worden de vereiste invoerparameters gebruikt

* **Onderliggende versie van migratiehulpprogramma**

   De migratiehulpmiddelen voeren hun functionaliteit uit door:

   * Het scannen van de respectieve sectie van de code van de klant en het uitvoeren van de migratie (gebaseerd op code-implementatie voor beste praktijken) om de output te produceren die dan kan worden bevestigd en worden opgesteld.

   * De tijdens de migratie uitgevoerde bewerkingen in een consistente volgorde opnemen om een samenvattingsrapport te maken.

## De insteekmodule gebruiken {#using-plugin}

De `aio-cli-plugin-aem-cloud-service-migration` reactoren klanten coderen, de opslagstructuur of configuraties op de lokale computer van de klant. Op deze pagina worden de gedetailleerde vereisten en ontwerpbeslissingen voor een uniforme ervaring vastgelegd.
Het is beschikbaar als een open bron voor gemeenschap om voor douanetoepassingen uit te breiden.

## Beschikbaarheid {#availability}

U kunt de software installeren en gebruiken `aio-cli-plugin-aem-cloud-service-migration` via `aio-cli` (momenteel alleen geïntegreerd met de verzendingsconverter).

Zie [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer informatie over het gebruik en de manier waarop u een bijdrage kunt leveren voor dit gereedschap.

De insteekmodulecode is geopend in Github.

