---
title: Opmerkingen bij de release van Universal Editor 2024.12.02
description: Dit zijn de releaseopmerkingen voor de release 2024.12.02 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 2aae8c63358680758e4f5324f38dea1bc2c47155
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2024.12.02 {#release-notes}

Dit zijn de releaseopmerkingen voor de release van 2 december 2024 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nieuwe functies {#what-is-new}

* **Navigatie van het Toetsenbord van de Boom van de Inhoud**: [ de inhoudsboom, ](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) beschikbaar in het zijpaneel, is nu volledig toegankelijk via toetsenbord.
   * De auteurs kunnen met de punten van de boommening navigeren en in wisselwerking staan gebruikend standaardtoetsenbordcontroles, die aan [ WCAG 2.1 richtlijnen ](/help/sites-cloud/authoring/page-editor/accessible-content.md) voor toegankelijkheid volgen.
   * Deze verbetering zorgt ervoor dat alle interactieve elementen in de structuur met het toetsenbord kunnen worden bediend, waardoor gebruikers die op toetsenbordnavigatie vertrouwen, meer insluiting krijgen.
* **Deselection van Editables**: De auteurs kunnen eerder geselecteerde editable elementen op de pagina nu schrappen.
   * Hiermee voorkomt u afleidingen wanneer auteurs de pagina zonder actieve selectiekaders willen weergeven.
* **de Selector van het Fragment**: Op de instanties van AEM as a Cloud Service, openen de fragmentverwijzingen nu de fragmentselecteur als inhoudkiezer, leverend verbeterde functionaliteit zoals het gehoorzamen van toegestane modellen van het Fragment van de Inhoud, onderzoek van de Fragmenten van de Inhoud, en een betere algemene ervaring.
   * Dit richt zich op andere Adobe UIs en verbetert consistentie.
   * [ voor AEM 6.5 milieu&#39;s, ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) blijft de bestaande inhoudkiezer in gebruik.
* **Beschrijving van de Container**: [ de containercomponent ](/help/implementing/universal-editor/field-types.md#container) die in het [ eigenschappen paneel wordt gebruikt, ](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-panel-properties-rail) aan verwijzingsinhoud, steunt nu een beschrijvingsattribuut, boven de containergebieden wordt getoond.
   * Deze toevoeging vergroot de duidelijkheid doordat auteurs context krijgen over de gegroepeerde velden die ze bewerken.

## Overige verbeteringen {#other-improvements}

* **Rich Text Field Synchronization**: De synchronisatie van ruwe en teruggegeven inhoud binnen rijke tekstgebieden in het eigenschappenpaneel werd verbeterd, richtend kwesties binnen Edge Delivery Services projecten waar de rijke tekstinhoud en de teruggegeven vertegenwoordiging kunnen verschillen.
* **het Uitgeven de Gebeurtenissen van de Wijze**: De Universele Redacteur zendt nu betrouwbaar het uitgeven wijzegebeurtenissen uit, met inbegrip van na het herladen van verre apps.
