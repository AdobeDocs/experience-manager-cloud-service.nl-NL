---
title: Opmerkingen bij de release van Universal Editor 2025.07.31
description: Dit zijn de releaseopmerkingen voor de release 2025.07.31 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 91799e32f363aca268a89a7eebcb5001c5295cc5
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2025.07.31 {#release-notes}

Dit zijn de opmerkingen bij de release van 31 juli 2025 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Wat is er nieuw? {#what-is-new}

* [ de optie van de authentificatiekopbal ](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings) blijft achter een eigenschapknevel zoals geïntroduceerd in [ versie 2025.07.09.](/help/release-notes/universal-editor/2025/2025-07-09.md)
   * Deze optie is nu echter standaard ingeschakeld.
* Nieuwe eigenschappen voor [ vroege adopters van RTE ](#new-rte)
   * Ondersteuning voor de donkere modus is toegevoegd.
   * Ondersteuning voor tekstuitlijning is toegevoegd.
      * Standaard uitgeschakeld en alleen beschikbaar voor projecten zonder kop
   * Ondersteuning voor inspringing is toegevoegd.
      * Standaard uitgeschakeld en alleen beschikbaar voor projecten zonder kop
   * Onderbrekingen (`<br>`) worden nu ingevoegd op shift+enter.

## Functies voor vroege adoptie {#early-adopter}

Als u deze functies wilt testen en feedback wilt delen, stuurt u een e-mail naar Customer Success Manager van Adobe via het e-mailadres dat bij uw Adobe ID hoort.

### Nieuwe RTE {#new-rte}

De nieuwe ProseMirror RTE, die een paginakiezer in het koppelingsdialoogvenster bevat, is nu beschikbaar in het rechterdeelvenster.

### Ongedaan maken/Opnieuw {#undo-redo}

Ongedaan maken en opnieuw uitvoeren is nu beschikbaar voor auteurs van inhoud in de Universal Editor.

* Dit omvat bewerkingen die in de context zijn uitgevoerd, bewerkingen die zijn uitgevoerd via het deelvenster Eigenschappen, en het toevoegen (of dupliceren), verplaatsen en verwijderen van blokken.
* Ongedaan maken en opnieuw uitvoeren is beperkt tot de huidige browsersessie.

## Overige verbeteringen {#other-improvements}

* Correcties voor RTE voor vroegtijdige adoptie
   * Wanneer u op Enter drukt, wordt er een nieuw lijstitem (`<li>`) gemaakt in een lijst.
* Video&#39;s worden nu correct bijgewerkt wanneer externe DAM wordt gebruikt.
* Servicesupport toegevoegd voor 6.5 LTS.

## Afwijkingen {#deprecations}

* `text-input` en `text-area` componenten werden officieel verouderd met [ versie 2025.07.09.](/help/release-notes/universal-editor/2025/2025-07-09.md)
   * Gebruik in `model-definition.json` de tekstcomponent om tekstinvoer voor het deelvenster Eigenschappen te maken.
