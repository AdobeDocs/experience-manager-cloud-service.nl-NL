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
>Voor de opmerkingen bij de huidige release voor Adobe Experience Manager as a Cloud Service raadpleegt u [deze pagina.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Wat is er nieuw? {#what-is-new}

* **Home**: De recente pagina&#39;s worden weergegeven als een lijst, zonder voorvertoningsafbeeldingen.
* **Locatiebalk**: Verbeterde URL-validatie is toegevoegd, HTTPS-URL&#39;s zijn afgedwongen en hashes in URL&#39;s worden ondersteund voor toepassingen die door hashes zijn omgeleid.
* **Toetsenbordnavigatie**: De selectie van de paginabedekking is losgekoppeld van de eigenschappen en de focus van het spoor om de toetsenbordnavigatie op de pagina te verbeteren zonder de focus te verliezen.
* **Itemlabels**: De terugvalwaarde voor labels wordt nu gebruikt `data-aue-prop` in plaats van `data-aue-type` voor een duidelijkere identificatie in overlays en in de inhoudsstructuur.
* **RTE Modal**: A **Annuleren** De knop is toegevoegd aan het modale tekstbewerkingsmodel met tekstopmaak wanneer deze vanuit het deelvenster Eigenschappen wordt geopend.
* **UE-service op knooppunt**: HTTP-ondersteuning voor de Universal Editor Service is opnieuw geïntroduceerd, aangezien alle HTTPS-verbindingen op Dispatcher-niveau worden beëindigd.
* **Interne kopiëren-API**: Er is een API aan de Universal Editor-service toegevoegd om componenten te kopiëren, zodat u in de toekomst werkbalkopties kunt gebruiken om inhoud te kopiëren en te dupliceren.

## Opgeloste problemen {#bug-fixes}

* **Venster Eigenschappen, Broodkruimel**: Het menu van de broodkruimel in het deelvenster Eigenschappen voor diepgeneste items, die niet open bleven, is hersteld.
* **Selector inhoudfragment**: De kiezer voor Inhoudsfragment is verbeterd en voldoet aan de regels die zijn gedefinieerd in het model Inhoudsfragment of in het dialoogvenster `data-aue-filter`.
* **Component-invoeging**: De lijst voor het invoegen van nieuwe componenten die niet correct zijn bijgewerkt nadat naar een andere pagina was genavigeerd, is gecorrigeerd.
* **Status van publicatie**: De verwerking van publicatiestatussen is verbeterd om consistenter te werken.
* **Diverse correcties**: Deze release bevat ook verschillende kleine correcties, het opschonen van technische schulden, beveiligingsverbeteringen en geconsolideerde tests voor algemene stabiliteit en prestaties.
