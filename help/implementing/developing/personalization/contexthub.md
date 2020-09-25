---
title: ContextHub
description: ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens
translation-type: tm+mt
source-git-commit: b8bc27b51eefcfcfa1c23407a4ac0e7ff068081e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# ContextHub {#contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Het is primaire eigenschap de capaciteit aan om contextgegevens te [bekijken terwijl het simuleren en het schakelen tussen diverse karakters.](/help/sites-cloud/authoring/personalization/contexthub.md)

ContextHub die u toestaat:

* [Presenteer, bekijk, schakelaar personas, en simuleer gebruikerservaring](#presentation) terwijl het ontwerpen van pagina&#39;s gebruikend contextgegevens.
* [Contextgegevens](#persistence) op uw website behouden als een representatie van een gegevenslaag.
* [Segmenten](#segmentation) voor de geselecteerde context beheren.

Met de JavaScript-API aan de clientzijde hebt u toegang tot de gegevens voor het aanpassen van de inhoud.

## Presentatie {#presentation}

De [toolbar](/help/sites-cloud/authoring/personalization/contexthub.md) ContextHub laat marketers en auteurs toe om opslaggegevens te zien en te manipuleren voor het simuleren van de gebruikerservaring wanneer het ontwerpen van pagina&#39;s. De toolbar bestaat uit groepen modules UI die toegang tot opslag [ContextHub verlenen,](#persistence) die gegevens ContextHub over de cliënt voortzetten.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub verstrekt verscheidene types [van](sample-modules.md)steekproefmodule.
* Gebruik AEM consoles om UI-modules [toe te](configuring-contexthub.md#adding-a-ui-module)voegen en deze [te groeperen in UI-modi](configuring-contexthub.md#adding-a-ui-mode).
* Ontwikkelaars kunnen aangepaste moduletypen [](extending-contexthub.md#creating-contexthub-ui-module-types)maken.

De ontwikkelaars moeten de component ContextHub aan de pagina [](configuring-contexthub.md)toevoegen.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. De JavaScript API van ContextHub laat u toe om tot opslag toegang te hebben om, gegevens tot stand te brengen bij te werken en te schrappen zonodig. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub verstrekt verscheidene types [van](sample-stores.md)steekproefopslag.
* Gebruik AEM consoles om winkels te [maken](configuring-contexthub.md#creating-a-contexthub-store).
* Ontwikkelaars kunnen aangepaste winkeltypen [maken](extending-contexthub.md#creating-custom-store-candidates).
* Ontwikkelaars hebben [toegang tot opslaggegevens](adding-contexthub.md#interacting-with-contexthub-stores) via JavaScript.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt de Javascript API gebruiken om opgeloste segmenten [te](adding-contexthub.md#determining-resolved-contexthub-segments)bepalen.
