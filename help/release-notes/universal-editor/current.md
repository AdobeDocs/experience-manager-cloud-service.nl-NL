---
title: Opmerkingen bij de release van Universal Editor 2025.02.17
description: Dit zijn de releaseopmerkingen voor de release 2025.02.17 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: af04ad7e3f89247580c48c276cb371d78ac56a49
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2025.02.17 {#release-notes}

Dit zijn de opmerkingen bij de release van 17 februari 2025 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Wat is er nieuw? {#what-is-new}

* **publiceert aan voorproef** - wanneer het publiceren (of het unpublishing) van uw inhoud gebruikend de Universele Redacteur, kunt u nu kiezen als u aan uw voorproefmilieu naast uw publicatiemilieu wenst te publiceren
   * Zo kunt u de inhoud vóór publicatie controleren.
* **het Model en de filter kunnen in de componentendefinitie** worden bepaald - u kunt nu bepalen welk model en filter een component in de componentendefinitie gebruikt.
   * Deze informatie kan centraal in de definitie worden gehandhaafd en te hoeven niet om de instrumentatie worden gespecificeerd.
   * Op deze manier kunt u componenten over containers verplaatsen.
* **de elementen van het Kind van containers worden impliciet beschouwd als componenten** - als een punt met a `data-aue-resource` als direct kind in een container wordt geplaatst wordt het beschouwd als een component en kan worden bewogen zonder het moeten `data-aue-behavior="component"` specificeren.

## Overige verbeteringen {#other-improvements}

* **AEM 6.5 de Selecteur van Activa** - de 6.5 activaselecteur opent nu behoorlijk wanneer het runnen van de Universele Redacteur met AEM 6.5.

