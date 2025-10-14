---
title: Componentenconsole
description: Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd
exl-id: f4949331-5302-46d3-a004-b813bb95ec2f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 12%

---

# Componentenconsole {#components-console}

Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd en sleutelinformatie voor elke component bekijken.

Het kan van **Hulpmiddelen worden betreden >** **Algemeen >** **Componenten**. Omdat er geen boomstructuur voor componenten is, is alleen de lijstweergave beschikbaar.

![&#x200B; de Console van Componenten &#x200B;](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>In de Componentenconsole worden alle componenten in het systeem weergegeven. Browser van de Component [&#128279;](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) toont componenten die aan auteurs beschikbaar zijn en verbergt om het even welke componentengroepen die met een periode ( `.`) beginnen.

## Zoeken {#search-field}

Met het pictogram **Alleen content** (linksboven) kunt u het deelvenster **Zoeken** openen om de componenten te zoeken en/of te filteren:

![&#x200B; zoekend in de Console van Componenten &#x200B;](/help/sites-cloud/authoring/assets/components-console-search.png)

### Componentdetails {#component-details}

Als u details over een bepaalde component wilt weergeven, selecteert u de gewenste bron. Drie tabbladen bieden:

* **Eigenschappen**

  ![&#x200B; eigenschappen van de Console van Componenten &#x200B;](/help/sites-cloud/authoring/assets/components-console-properties.png)

  Op het tabblad Eigenschappen kunt u het volgende doen:

   * De algemene eigenschappen van de component weergeven.
      * Geef weer hoe het pictogram of de afkorting is gedefinieerd voor de component. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Als u op de bron van het pictogram klikt, gaat u naar die component.
   * Bekijk het **Type van Middel** en **Super Type van Middel** (als bepaald) voor de component.
      * Als u op het Super Type van Middel klikt, gaat u naar die component.

  >[!NOTE]
  >
  >Omdat `/apps` niet bewerkbaar is bij uitvoering, is de Componentenconsole alleen-lezen.

* **Beleid**

  ![&#x200B; Beleid van de Console van de Component &#x200B;](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Levend Gebruik**

  ![&#x200B; Levend gebruik van componenten &#x200B;](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

  >[!CAUTION]
  >
  >Vanwege de aard van de informatie die voor deze weergave wordt verzameld, kan het enige tijd duren voordat deze wordt gesorteerd of weergegeven.

* **Documentatie**

  Als de ontwikkelaar documentatie voor de component heeft verstrekt, zal het op de **Documentatie** tabel verschijnen. Als er geen beschikbare documentatie is, zal het **Documentatie** lusje niet worden getoond. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

  ![&#x200B; documentatie van de Component &#x200B;](/help/sites-cloud/authoring/assets/components-console-documentation.png)
