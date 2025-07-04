---
title: Opmerkingen bij de release van Universal Editor 2025.06.19
description: Dit zijn de releaseopmerkingen voor de release 2025.06.19 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 5ffae9e548ca952975b3ea805808e227102ec99f
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2025.06.19 {#release-notes}

Dit zijn de opmerkingen bij de release van 19 juni 2025 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Wat is er nieuw? {#what-is-new}

* **Steun voor multi-fields in het Spoorwegverkeer van Eigenschappen** -
  [ de containercomponent ](/help/implementing/universal-editor/field-types.md#container) kan nu worden gebruikt om multi-gebiedseigenschappen tot stand te brengen.
* **Steun voor genestelde eigenschappen** - het [`name` gebied ](/help/implementing/universal-editor/field-types.md#nesting) steunt nu wegen om bezit het nesten toe te laten.
* **resizable juist paneel** - het zijpaneel kan nu resized aan betere rekening voor langere die inhoud in het zijpaneel wordt getoond.

## Functies voor vroege adoptie {#early-adopter}

U kunt bepaalde functies testen door deel uit te maken van het Adobe-programma voor vroegtijdige adoptie.

### **ongedaan maken/opnieuw** {#undo-redo}

Ongedaan maken en opnieuw uitvoeren is nu beschikbaar voor auteurs van inhoud in de Universal Editor.

* Dit omvat bewerkingen die in de context zijn uitgevoerd, bewerkingen die zijn uitgevoerd via het deelvenster Eigenschappen, en het toevoegen (of dupliceren), verplaatsen en verwijderen van blokken.
* Ongedaan maken en opnieuw uitvoeren is beperkt tot de huidige browsersessie.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar Customer Success Manager van Adobe via het e-mailadres dat bij uw Adobe ID hoort.

## Overige verbeteringen {#other-improvements}

* De zeer belangrijke botsingsfouten van het middel toen het bewegen van blokken tussen containers werden bevestigd.
* Er is een probleem opgelost waardoor het dupliceren van het laatste blok van een container mislukt.
* In de vervolgkeuzelijst Handeling toevoegen worden nu alleen componenten weergegeven waarvoor een geschikte plug-in is gedefinieerd in het `component-definition.json` -bestand.
* De wijzigingsdatum die in het dialoogvenster Publiceren wordt gebruikt, is vastgesteld op het moment dat pagina&#39;s in sommige gevallen niet als gewijzigd werden herkend en niet opnieuw werden gepubliceerd.
* Het overervingsgedrag MSM waarbij het bewerken van een container geannuleerde overerving voor onderliggende knooppunten. Dit gedrag is nu opgelost.
* `fetchUrl` is hersteld, waardoor bewegende blokken van de ene container naar de andere worden hersteld.
