---
title: Opmerkingen bij de release van Universal Editor 2025.03.10
description: Dit zijn de releaseopmerkingen voor de release 2025.03.10 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b3c98f5e41dbc5e1714d0ed418a317199c735b73
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---


# Opmerkingen bij de release van Universal Editor 2025.03.10 {#release-notes}

Dit zijn de opmerkingen bij de release van 10 maart 2025 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Wat is er nieuw? {#what-is-new}

* **Bewegende Componenten:** [ Bewegende componenten tussen containers ](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) neemt nu de componentenfilter van de doelcontainer waar.
   * Er is niet meer een vereiste om de zelfde [ filterdefinitie ](/help/implementing/universal-editor/filtering.md) op zijn plaats voor zowel doel als bestemmingscontainers te hebben om de component tussen de containers te bewegen.
* **Vergrendelde Pagina&#39;s:** De Universele Dienst van de Redacteur neemt de [ vergrendelingsstatus van een pagina ](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) waar en schrijft slechts aan pagina&#39;s die niet worden gesloten of door de gebruiker worden gesloten.

## Overige verbeteringen {#other-improvements}

* Correcties zijn aangebracht voor validatie voor canvas zonder kop.

## Deprectie {#deprecation}

* De `universal-editor-cors` -bibliotheek die via npm of `https://unviersal-editor-service.experiencecloud.live/corslib/*` wordt geleverd, mag niet langer worden gebruikt.
   * In plaats daarvan moet een scripttag die `https://universal-editor-service.adobe.io/cors.js` aanwijst, worden gebruikt.
   * Zie het [ Universele Overzicht van de Redacteur voor de Ontwikkelaars van AEM ](/help/implementing/universal-editor/developer-overview.md) voor details op hoe te om uw pagina voor gebruik met de Universele Redacteur behoorlijk van een instrument te voorzien.
   * Gebruikers zien één keer per dag een afgekeurd bericht als de verkeerde methode wordt gebruikt.
