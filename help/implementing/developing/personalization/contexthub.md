---
title: ContextHub
description: ContextHub is een kader om, contextgegevens op te slaan te manipuleren en voor te stellen
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# ContextHub {#contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Zijn primaire eigenschap biedt de capaciteit aan [ contextgegevens te bekijken terwijl het simuleren van en het schakelen tussen diverse karakters ](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub die u toestaat:

* [ Aanwezige, mening, schakelaarpersoonlijkheden, en simuleer gebruikerservaring ](#presentation) terwijl het ontwerpen van pagina&#39;s gebruikend contextgegevens.
* [ zet contextgegevens ](#persistence) op uw website als vertegenwoordiging van de gegevenslaag voort.
* [ beheert segmenten ](#segmentation) voor de geselecteerde context.

Met de client-side JavaScript API hebt u toegang tot de gegevens voor het aanpassen van inhoud.

## Presentatie {#presentation}

De [ toolbar ContextHub ](/help/sites-cloud/authoring/personalization/contexthub.md) laat tellers en auteurs toe om opslaggegevens te zien en te manipuleren voor het simuleren van de gebruikerservaring wanneer het ontwerpen van pagina&#39;s. De toolbar bestaat uit groepen modules UI die toegang tot [ opslag ContextHub ](#persistence) verlenen, die gegevens ContextHub over de cliënt voortzetten.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub verstrekt verscheidene [ types van steekproefmodule ](sample-modules.md).
* Het gebruik AEM consoles aan [ voegt modules UI ](configuring-contexthub.md#adding-a-ui-module) toe, en aan [ groepeert hen in wijzen UI ](configuring-contexthub.md#adding-a-ui-mode).
* De ontwikkelaars kunnen [ de types van douanemodule ](extending-contexthub.md#creating-contexthub-ui-module-types) tot stand brengen.

De ontwikkelaars moeten [ de component ContextHub aan de pagina ](configuring-contexthub.md) toevoegen.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. De API van ContextHub JavaScript laat u toe om tot opslag toegang te hebben om, gegevens tot stand te brengen bij te werken en te schrappen zonodig. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub verstrekt verscheidene [ types van steekproefopslag ](sample-stores.md).
* Het gebruik AEM consoles aan [ creeert opslag ](configuring-contexthub.md#creating-a-contexthub-store).
* De ontwikkelaars kunnen [ tot de types van douaneopslag ](extending-contexthub.md#creating-custom-store-candidates) leiden.
* De ontwikkelaars kunnen [ tot opslaggegevens ](adding-contexthub.md#interacting-with-contexthub-stores) als JavaScript toegang hebben.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt JavaScript API gebruiken om [ bepaalde opgeloste segmenten ](adding-contexthub.md#determining-resolved-contexthub-segments) te bepalen.
