---
title: Opmerkingen bij de release van Universal Editor 2025.09.04
description: Dit zijn de releaseopmerkingen voor de release 2025.09.04 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 0c380e0faca1db0966d22d056dd1f824a731a7bc
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2025.09.04 {#release-notes}

Dit zijn de opmerkingen bij de release van 4 september 2025 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Wat is er nieuw? {#what-is-new}

* Het exemplaar en de deeg is beschikbaar voor [ vroege adopters ](#copy-paste)

### Ongedaan maken/Opnieuw {#undo-redo}

Ongedaan maken en opnieuw uitvoeren is nu beschikbaar voor auteurs van inhoud in de Universal Editor.

* Dit omvat bewerkingen die in de context zijn uitgevoerd, bewerkingen die zijn uitgevoerd via het deelvenster Eigenschappen, en het toevoegen (of dupliceren), verplaatsen en verwijderen van blokken.
* Ongedaan maken en opnieuw uitvoeren is beperkt tot de huidige browsersessie.

## Functies voor vroege adoptie {#early-adopter}

Als u deze functies wilt testen en feedback wilt delen, stuurt u een e-mail naar Customer Success Manager van Adobe via het e-mailadres dat bij uw Adobe ID hoort.

### Nieuwe RTE {#new-rte}

De nieuwe ProseMirror RTE, die een paginakiezer in het koppelingsdialoogvenster bevat, is nu beschikbaar in het rechterdeelvenster.

### Kopiëren/plakken {#copy-paste}

Kopiëren en plakken van componenten op dezelfde pagina is nu beschikbaar voor auteurs van inhoud.

## Overige verbeteringen {#other-improvements}

* De stijl van de redacteurstoolbar is bijgewerkt om zich beter aan aanstaande nieuwe RTE te richten.
* De filters in het dialoogvenster met de elementkiezer zijn hersteld.

## Afwijkingen {#deprecations}

* `text-input` en `text-area` componenten werden officieel verouderd met [ versie 2025.07.09.](/help/release-notes/universal-editor/2025/2025-07-09.md)
   * Gebruik in `model-definition.json` de tekstcomponent om tekstinvoer voor het deelvenster Eigenschappen te maken.
