---
title: Opmerkingen bij de release van Universal Editor 2024.06.28
description: Dit zijn de releaseopmerkingen voor de release 2024.06.28 van de Universal Editor.
feature: Release Information
role: Admin
source-git-commit: cc94ad2ba42707bb7541217f0225b995f64ad84f
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2024.06.28 {#release-notes}

Dit zijn de releaseopmerkingen voor de release van 28 juni 2024 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Wat is er nieuw? {#what-is-new}

* **Huis**: De recente pagina&#39;s worden getoond als lijst, zonder voorproefbeelden.
* **Bar van de Plaats**: De verbeterde bevestiging URL werd toegevoegd, die HTTPS URLs afdwingt en hashes in URLs steunt om voor hash-verpletterde toepassingen rekening te houden.
* **Navigatie van het Toetsenbord**: De selectie van de paginabedekking werd losgemaakt van de eigenschappen spoornadruk om de toetsenbordnavigatie op de pagina te verbeteren zonder nadruk te verliezen.
* **Etiketten van het Punt**: De reservewaarde voor etiketten gebruikt nu `data-aue-prop` in plaats van `data-aue-type` voor duidelijkere identificatie in overlays en de inhoudsboom.
* **Modal RTE**: A **annuleert** knoop werd toegevoegd aan de rijke modale tekstredacteur toen het openen van het eigenschappen paneel.
* **de Dienst van de UE op Knoop**: De steun van HTTP voor de Universele Dienst van de Redacteur werd opnieuw geïntroduceerd, aangezien alle verbindingen HTTPS op het niveau van Dispatcher worden geëindigd.
* **Interne Exemplaar API**: Een API aan de Universele Dienst van de Redacteur om componenten te kopiëren werd toegevoegd, toestaand toekomstige inleiding van toolbaropties om inhoud te kopiëren en te dupliceren.

## Opgeloste problemen {#bug-fixes}

* **Breadcrumb van het Comité van Eigenschappen**: Het broodcrumb menu in het eigenschappen paneel voor diep genestelde punten, die open niet bleven, werd bevestigd.
* **de Selector van het Fragment van de Inhoud**: De selecteur van het Fragment van de Inhoud werd verbeterd om ervoor te zorgen dat het de regels naleeft die in het model van het Fragment van de Inhoud of in `data-aue-filter` worden bepaald.
* **Invoeging van de Component**: De lijst om nieuwe componenten op te nemen die niet correct na het navigeren aan een andere pagina werden bijgewerkt werd verbeterd.
* **de Status van de Publicatie**: De behandeling van publicatiestatus werd verbeterd om consistenter te functioneren.
* **Diverse Oplossingen**: Deze versie bevat ook diverse minder belangrijke moeilijke situaties, technologieschuldenschoonmaakbeurt, veiligheidsverhogingen, en geconsolideerde tests voor algemene stabiliteit en prestaties.
