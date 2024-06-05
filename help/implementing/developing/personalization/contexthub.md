---
title: ContextHub
description: ContextHub is een kader om, contextgegevens op te slaan te manipuleren en voor te stellen
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# ContextHub {#contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. De belangrijkste functie is de mogelijkheid om [contextgegevens weergeven tijdens het simuleren en schakelen tussen verschillende personen](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub die u toestaat:

* [Presenteren, weergeven, schakelen tussen personen en simuleren van gebruikerservaring](#presentation) tijdens het ontwerpen van pagina&#39;s met contextgegevens.
* [Contextgegevens behouden](#persistence) op uw website als een representatie van een gegevenslaag.
* [Segmenten beheren](#segmentation) voor de geselecteerde context.

Met de client-side JavaScript API hebt u toegang tot de gegevens voor het aanpassen van inhoud.

## Presentatie {#presentation}

De [ContextHub-werkbalk](/help/sites-cloud/authoring/personalization/contexthub.md) stelt marketers en auteurs in staat om opslaggegevens te bekijken en te manipuleren om de gebruikerservaring bij het ontwerpen van pagina&#39;s te simuleren. De werkbalk bestaat uit groepen UI-modules die toegang bieden tot [ContextHub-winkels,](#persistence) die gegevens ContextHub over de cliënt voortzetten.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub biedt verschillende [voorbeeldmoduletypen](sample-modules.md).
* Consoles AEM gebruiken voor [UI-modules toevoegen](configuring-contexthub.md#adding-a-ui-module), en [groeperen hen in wijzen UI](configuring-contexthub.md#adding-a-ui-mode).
* Ontwikkelaars kunnen [aangepaste moduletypen maken](extending-contexthub.md#creating-contexthub-ui-module-types).

Ontwikkelaars moeten [Voeg de component ContextHub aan de pagina toe](configuring-contexthub.md).

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. Met de JavaScript-API van ContextHub hebt u toegang tot opslagruimten om gegevens te maken, bij te werken en te verwijderen. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub biedt verschillende [voorbeeldwinkeltypen](sample-stores.md).
* Consoles AEM gebruiken voor [opslaan maken](configuring-contexthub.md#creating-a-contexthub-store).
* Ontwikkelaars kunnen [aangepaste winkeltypen maken](extending-contexthub.md#creating-custom-store-candidates).
* Ontwikkelaars kunnen [toegang opslaggegevens](adding-contexthub.md#interacting-with-contexthub-stores) in JavaScript.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt de JavaScript-API gebruiken om [omgezette segmenten bepalen](adding-contexthub.md#determining-resolved-contexthub-segments).
