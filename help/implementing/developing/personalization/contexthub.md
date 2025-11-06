---
title: ContextHub
description: ContextHub is een kader om, contextgegevens op te slaan te manipuleren en voor te stellen
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
feature: Developing, Personalization
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# ContextHub {#contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Zijn primaire eigenschap biedt de capaciteit aan [&#x200B; contextgegevens te bekijken terwijl het simuleren van en het schakelen tussen diverse karakters &#x200B;](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub die u toestaat:

* [&#x200B; Aanwezige, mening, schakelaarpersoonlijkheden, en simuleer gebruikerservaring &#x200B;](#presentation) terwijl het ontwerpen van pagina&#39;s gebruikend contextgegevens.
* [&#x200B; zet contextgegevens &#x200B;](#persistence) op uw website als vertegenwoordiging van de gegevenslaag voort.
* [&#x200B; beheert segmenten &#x200B;](#segmentation) voor de geselecteerde context.

Met de client-side JavaScript API hebt u toegang tot de gegevens voor het aanpassen van inhoud.

## Presentatie {#presentation}

De [&#x200B; toolbar ContextHub &#x200B;](/help/sites-cloud/authoring/personalization/contexthub.md) laat tellers en auteurs toe om opslaggegevens te zien en te manipuleren voor het simuleren van de gebruikerservaring wanneer het ontwerpen van pagina&#39;s. De toolbar bestaat uit groepen modules UI die toegang tot [&#x200B; opslag ContextHub &#x200B;](#persistence) verlenen, die gegevens ContextHub over de cliënt voortzetten.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub verstrekt verscheidene [&#x200B; types van steekproefmodule &#x200B;](sample-modules.md).
* De consoles van AEM van het gebruik aan [&#x200B; voegen modules UI &#x200B;](configuring-contexthub.md#adding-a-ui-module) toe, en aan [&#x200B; groeperen hen in wijzen UI &#x200B;](configuring-contexthub.md#adding-a-ui-mode).
* De ontwikkelaars kunnen [&#x200B; de types van douanemodule &#x200B;](extending-contexthub.md#creating-contexthub-ui-module-types) tot stand brengen.

De ontwikkelaars moeten [&#x200B; de component ContextHub aan de pagina &#x200B;](configuring-contexthub.md) toevoegen.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. De API van ContextHub JavaScript laat u toe om tot opslag toegang te hebben om, gegevens tot stand te brengen bij te werken en te schrappen zonodig. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub verstrekt verscheidene [&#x200B; types van steekproefopslag &#x200B;](sample-stores.md).
* De consoles van AEM van het gebruik aan [&#x200B; creëren opslag &#x200B;](configuring-contexthub.md#creating-a-contexthub-store).
* De ontwikkelaars kunnen [&#x200B; tot de types van douaneopslag &#x200B;](extending-contexthub.md#creating-custom-store-candidates) leiden.
* De ontwikkelaars kunnen [&#x200B; tot opslaggegevens &#x200B;](adding-contexthub.md#interacting-with-contexthub-stores) als JavaScript toegang hebben.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt JavaScript API gebruiken om [&#x200B; bepaalde opgeloste segmenten &#x200B;](adding-contexthub.md#determining-resolved-contexthub-segments) te bepalen.
