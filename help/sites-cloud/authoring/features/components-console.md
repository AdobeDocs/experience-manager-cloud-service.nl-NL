---
title: Componentenconsole
description: Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd
exl-id: f4949331-5302-46d3-a004-b813bb95ec2f
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 12%

---

# Componentenconsole {#components-console}

Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd en sleutelinformatie voor elke component bekijken.

Het kan worden benaderd van **Gereedschappen >** **Algemeen >** **Componenten**. Omdat er geen boomstructuur voor componenten is, is alleen de lijstweergave beschikbaar.

![De componentenconsole](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>In de Componentenconsole worden alle componenten in het systeem weergegeven. De [Componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) toont componenten die aan auteurs beschikbaar zijn en verbergt om het even welke componentengroepen die met een periode beginnen ( `.`).

## Zoeken {#search-field}

Met het pictogram **Alleen content** (linksboven) kunt u het deelvenster **Zoeken** openen om de componenten te zoeken en/of te filteren:

![Zoeken in de componentenconsole](/help/sites-cloud/authoring/assets/components-console-search.png)

### Componentdetails {#component-details}

Als u details over een bepaalde component wilt weergeven, selecteert u de gewenste bron. Drie tabbladen bieden:

* **Eigenschappen**

  ![Eigenschappen van Componentconsole](/help/sites-cloud/authoring/assets/components-console-properties.png)

  Op het tabblad Eigenschappen kunt u het volgende doen:

   * De algemene eigenschappen van de component weergeven.
      * Geef weer hoe het pictogram of de afkorting is gedefinieerd voor de component. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * Als u op de bron van het pictogram klikt, gaat u naar die component.
   * De weergave **Resourcetype** en **Super Type resource** (indien gedefinieerd) voor de component.
      * Als u op het Super Type van Middel klikt, gaat u naar die component.

  >[!NOTE]
  >
  >Omdat `/apps` kan tijdens runtime niet worden bewerkt, is de Componentenconsole alleen-lezen.

* **Beleid**

  ![Beleid voor componentconsoles](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **Live-gebruik**

  ![Actief gebruik van componenten](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

  >[!CAUTION]
  >
  >Vanwege de aard van de informatie die voor deze weergave wordt verzameld, kan het enige tijd duren voordat deze wordt gesorteerd of weergegeven.

* **Documentatie**

  Als de ontwikkelaar documentatie voor de component heeft verstrekt, zal het op het **Documentatie** tab. Als er geen documentatie beschikbaar is, **Documentatie** wordt niet weergegeven. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

  ![Componentdocumentatie](/help/sites-cloud/authoring/assets/components-console-documentation.png)
