---
title: Onderdelenconsole
description: Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 17%

---


# Onderdelenconsole {#components-console}

Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd en sleutelinformatie voor elke component bekijken.

U kunt deze openen via **Gereedschappen ->** **Algemeen ->** **Componenten**. Omdat er geen boomstructuur voor componenten is, is alleen de lijstweergave beschikbaar.

![De componentenconsole](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>In de Componentenconsole worden alle componenten in het systeem weergegeven. In de [Componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) worden componenten weergegeven die beschikbaar zijn voor auteurs en worden componentgroepen verborgen die met een punt ( `.`) beginnen.

## Zoeken {#search-field}

Met het pictogram **Alleen content** (linksboven) kunt u het deelvenster **Zoeken** openen om de componenten te zoeken en/of te filteren:

![Zoeken in de componentenconsole](/help/sites-cloud/authoring/assets/components-console-search.png)

### Componentdetails {#component-details}

Als u details over een bepaalde component wilt weergeven, tikt u op de gewenste bron of klikt u op deze. Drie tabbladen bieden:

* **Eigenschappen**

   ![Eigenschappen van Componentconsole](/help/sites-cloud/authoring/assets/components-console-properties.png)

   Op het tabblad Eigenschappen kunt u het volgende doen:

   * De algemene eigenschappen van de component weergeven.
      * Geef weer hoe het pictogram of de afkorting is gedefinieerd voor de component. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Als u op de bron van het pictogram klikt, gaat u naar die component.
   * Bekijk het Type **van** Middel en het Type **van Super van het** Middel (als bepaald) voor de component.
      * Als u op het Super Type van Middel klikt, gaat u naar die component.
   >[!NOTE]
   >
   >Omdat `/apps` de Componentenconsole niet bewerkbaar is bij uitvoering, is deze alleen-lezen.

* **Beleid**

   ![Beleid voor componentconsoles](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Live-gebruik**

   ![Actief gebruik van componenten](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

   >[!CAUTION]
   >
   >Vanwege de aard van de informatie die voor deze weergave wordt verzameld, kan het enige tijd duren voordat deze wordt gesorteerd of weergegeven.

* **Documentatie**

   Als de ontwikkelaar documentatie voor de component heeft verstrekt, zal het op het **Documentatie** lusje verschijnen. Als er geen documentatie beschikbaar is, zal het lusje van de **Documentatie** niet worden getoond. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

   ![Componentdocumentatie](/help/sites-cloud/authoring/assets/components-console-documentation.png)
