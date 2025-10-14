---
title: Workflows toepassen op pagina's
description: Tijdens het ontwerpen kunt u workflows aanroepen om op uw pagina's te reageren. Het is ook mogelijk om meerdere workflows toe te passen.
exl-id: 86e71f0e-e53e-40bc-901d-2a1ab347bd0a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 9%

---

# Workflows toepassen op pagina&#39;s {#applying-workflows-to-pages}

Tijdens het ontwerpen kunt u workflows aanroepen om op uw pagina&#39;s te reageren. Het is ook mogelijk om meerdere workflows toe te passen.

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
   * U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* De nuttige werkstroom. Dit kunnen een of meer pagina&#39;s zijn.

Workflows kunnen worden gestart vanaf:

* [&#x200B; de console van Plaatsen &#x200B;](#starting-a-workflow-from-the-sites-console).
* [&#x200B; wanneer het uitgeven van een pagina, van de Informatie van de Pagina &#x200B;](#starting-a-workflow-from-the-page-editor).

>[!NOTE]
>
>Zie ook:
>
>* Hoe te om werkschema&#39;s op activa toe te passen DAM.
>* [&#x200B; Werkend met de Werkschema&#39;s van het Project &#x200B;](/help/sites-cloud/authoring/projects/workflows.md).

<!-- 
>* [How to apply workflows to DAM assets](/help/assets/assets-workflow.md).
>* [Working with Project Workflows](/help/sites-cloud/authoring/projects/workflows.md).
-->

>[!NOTE]
>
>AEM beheerders kunnen workflows starten met verschillende andere methoden.

<!-- 
>AEM administrators can [start workflows using several other methods](/help/sites-administering/workflows-starting.md).
-->

## Een workflow starten vanuit de siteconsole {#starting-a-workflow-from-the-sites-console}

U kunt een workflow starten vanuit:

* [&#x200B; creeer optie van de toolbar van Plaatsen &#x200B;](#starting-a-workflow-from-the-sites-toolbar).
* [&#x200B; de spoorstaaf van de Chronologie van de console van Plaatsen &#x200B;](#starting-a-workflow-from-the-timeline).

In beide gevallen, moet u [&#x200B; de Details van het Werkschema in de Create Tovenaar van het Werkschema specificeren &#x200B;](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten op de werkbalk Sites {#starting-a-workflow-from-the-sites-toolbar}

U kunt een werkschema van de toolbar van de **console van Plaatsen** beginnen:

1. Navigeer naar de gewenste pagina en selecteer deze.

1. Van **creeer** optie in de toolbar u **Werkschema** kunt nu selecteren.

   ![&#x200B; creeer werkschema van de toolbar &#x200B;](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. **creeer de tovenaar van het Werkschema** u [&#x200B; zal helpen de werkschemadetails &#x200B;](#specifying-workflow-details-in-the-create-workflow-wizard) specificeren.

### Een workflow starten vanuit de tijdlijn {#starting-a-workflow-from-the-timeline}

Van de **Chronologie** kunt u een werkschema beginnen dat op uw geselecteerde middel moet worden toegepast.

1. [&#x200B; selecteer het middel &#x200B;](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) en open [&#x200B; Chronologie &#x200B;](/help/sites-cloud/authoring/basic-handling.md#timeline) (of open Chronologie en selecteer dan het middel).
1. De pijlpunt door het commentaargebied kan worden gebruikt om **Werkschema van het Begin** te openbaren:

   ![&#x200B; creeer werkschema van de chronologie &#x200B;](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. **creeer de tovenaar van het Werkschema** u [&#x200B; zal helpen de werkschemadetails &#x200B;](#specifying-workflow-details-in-the-create-workflow-wizard) specificeren.

### Workflowdetails opgeven in de wizard Workflow maken {#specifying-workflow-details-in-the-create-workflow-wizard}

**creeer de tovenaar van het Werkschema** u zal helpen het werkschema selecteren en de vereiste details specificeren.

Na het openen van **creeer de tovenaar van het Werkschema** van of:

* [&#x200B; creeer optie van de toolbar van Plaatsen &#x200B;](#starting-a-workflow-from-the-sites-toolbar).
* [&#x200B; de spoorstaaf van de Chronologie van de console van Plaatsen &#x200B;](#starting-a-workflow-from-the-timeline).

U kunt details specificeren:

1. In de **stap van Eigenschappen**, worden de basisopties van het werkschema bepaald:

   * **model van het Werkschema**
   * **titel van het Werkschema**

      * U kunt een titel voor dit exemplaar specificeren, om u te helpen het in een later stadium identificeren.

   Afhankelijk van het workflowmodel zijn ook de volgende opties beschikbaar. Hierdoor kan het pakket dat als lading is gemaakt, worden bewaard nadat de workflow is voltooid.

   * **houd werkschemapakket**
   * **Titel van het Pakket**

      * U kunt een titel voor het pakket opgeven om het te identificeren.

   >[!NOTE]
   >
   >De optie **Workflowpakket bijhouden** is beschikbaar wanneer de workflow is geconfigureerd voor ondersteuning van meerdere resources en er meerdere resources zijn geselecteerd.

   <!--
   >The **Keep workflow package** option is available when the workflow has been configured for [Multi Resource Support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) and multiple resources have been selected.
   -->

   Wanneer volledig, gebruik **daarna** om te werk te gaan.

   ![&#x200B; specificerend werkschemaeigenschappen &#x200B;](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. In de **stap van het Bereik** kunt u selecteren:

   * **voeg Inhoud** toe om [&#x200B; wegbrowser &#x200B;](/help/sites-cloud/authoring/path-selection.md) te openen en extra middelen te selecteren; wanneer in browser, selecteer **Uitgezocht** om de inhoud aan de werkschemainstantie toe te voegen.

   * Een bestaande bron voor het weergeven van extra handelingen:

      * **omvat kinderen** om te specificeren dat de kinderen van dat middel in het werkschema inbegrepen zijn.
Er wordt een dialoogvenster geopend waarin u de selectie kunt verfijnen op basis van:

         * Alleen directe kinderen opnemen.
         * Alleen gewijzigde pagina&#39;s opnemen.
         * Alleen al gepubliceerde pagina&#39;s opnemen.

        Alle opgegeven onderliggende items worden toegevoegd aan de lijst met bronnen waarop de workflow van toepassing is.

      * **verwijder Selectie** om dat middel uit het werkschema te verwijderen.

   ![&#x200B; bepaalt werkschemawerkingsgebied &#x200B;](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >Als u aanvullende resources toevoegt, kunt u **Terug** gebruiken om de instelling voor **Workflowpakket behouden** aan te passen in de stap **Eigenschappen**.

1. Het gebruik **creeert** om de tovenaar te sluiten en de werkschemainstantie tot stand te brengen. Een bericht wordt getoond in de console van Plaatsen.

## Een workflow starten vanuit de Pagina-editor {#starting-a-workflow-from-the-page-editor}

Wanneer het uitgeven van een pagina kunt u **Informatie van de Pagina** van de toolbar selecteren. Het drop-down menu heeft het optie **Begin in Werkschema**. Hiermee wordt een dialoogvenster geopend waarin u de vereiste workflow kunt opgeven, zo nodig met een titel:

![&#x200B; Beginnend een werkschema van de paginaredacteur &#x200B;](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
