---
title: Opmerkingen bij de release Universal Editor Preview
description: Dit zijn de releaseopmerkingen voor de voorvertoningsversie van de Universal Editor.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: 374c8045043f67f06d4ae68aef499bb594f1c08c
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Opmerkingen bij de release Universal Editor Preview {#preview}

Dit zijn de versienota&#39;s voor de **voorproefversie** van de Universele Redacteur. Deze eigenschappen zijn momenteel beschikbaar in het 0&rbrace; voorproefmilieu van uw Universele Redacteur **.** Deze functies zullen naar verwachting op 19 februari 2026 beschikbaar komen.

Deze **voorproef** versienota&#39;s worden verstrekt als gemak zodat weet u welke veranderingen in de Universele Redacteur aanstaande zijn en u kunt hen testen door [&#x200B; omschakeling aan uw voorproefversie.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Voor de **huidige versienota&#39;s** voor de Universele Redacteur, zie gelieve de Nota&#39;s van de Versie van de Redacteur van het document [&#x200B; Universele &#x200B;](/help/release-notes/universal-editor/current.md).

>[!NOTE]
>
>De inhoud van de feitelijke release en de releasedatum kunnen worden gewijzigd.

## Nieuwe functies {#what-is-new}

* De RTE is verbeterd.
   * Het verbergen van werkbalkitems in de context RTE wordt nu ondersteund.
   * Het overvullen van tekst in tabellen met alinea&#39;s wordt nu ondersteund.
   * Niet-ondersteunde RTE-tags blijven nu behouden.
   * De logica van RTE wordt nu gediend van een afzonderlijk dossier.
   * De lijsten kunnen nu worden gecreeerd evenals worden uitgegeven gebruikend RTE.
* Wanneer geen label is ingesteld, wordt de componenttitel uit de componentdefinitie nu gebruikt.
* `setEditorMode` is nu beschikbaar via extensies.

## Aankomende verbeteringen {#other-improvements}

* De kopiëren-en-plakken functionaliteit tussen pagina&#39;s is hersteld.
* `universal-editor-extensibility` is verschoven naar `universal-editor` .
* Het aantal verzoeken aan het eindpunt van uitbreidingen is verminderd.
* RemoteApp-ontkoppelen is teruggebracht van drie naar één.
* De eindpunten van RTE worden nu gediend voor de op zijn plaats redacteur.
* Het bewerken van geneste velden leidt niet langer tot het overschrijven van gelijkwaardige items uit die structuren.
* Verplichte RTE-velden kunnen niet meer als leeg worden opgeslagen.
* De opmaak op de plaats wordt niet meer onjuist toegepast wanneer u koppelingen na de opmaak toevoegt.
