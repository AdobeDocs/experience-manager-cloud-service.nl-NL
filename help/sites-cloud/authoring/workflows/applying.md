---
title: Workflows toepassen op pagina's
description: Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina's. het is ook mogelijk meerdere werkschema's toe te passen.
translation-type: tm+mt
source-git-commit: b551a0b0d85d264feabf78942a381c4239fdbadb
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 11%

---


# Workflows toepassen op pagina&#39;s {#applying-workflows-to-pages}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina&#39;s. het is ook mogelijk meerdere werkstromen toe te passen .

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
   * U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* de workflow-lading; dit kan een of meer pagina&#39;s zijn.

Workflows kunnen worden gestart vanaf:

* [de Sites-console](#starting-a-workflow-from-the-sites-console).
* [bij het bewerken van een pagina, vanuit Pagina-informatie](#starting-a-workflow-from-the-page-editor).

>[!NOTE]
>
>Zie ook:
>
>* Hoe te om werkschema&#39;s op activa toe te passen DAM.
>* [Werken met projectworkflows](/help/sites-cloud/authoring/projects/workflows.md).


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

* [Kies de optie Maken op de werkbalk](#starting-a-workflow-from-the-sites-toolbar) Sites.
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

In beide gevallen moet u:

* [Geef de workflowdetails op in de wizard](#specifying-workflow-details-in-the-create-workflow-wizard) Workflow maken.

### Een workflow starten op de werkbalk Sites {#starting-a-workflow-from-the-sites-toolbar}

U kunt een werkschema van de toolbar van **Sites** console beginnen:

1. Navigeer naar de gewenste pagina en selecteer deze.

1. Met de optie **Maken** op de werkbalk kunt u **Workflow** nu selecteren.

   ![Werkstroom maken van de werkbalk](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. Met de wizard **Workflow maken** kunt u [de workflowdetails opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten vanuit de tijdlijn {#starting-a-workflow-from-the-timeline}

Vanuit de **tijdlijn** kunt u een workflow starten die op de geselecteerde bron moet worden toegepast.

1. [Selecteer de ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) bron en open  [Tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)  (of open Chronologie en selecteer dan de middel).
1. De pijlpunt door het commentaargebied kan worden gebruikt om **Workflow van het Begin** te openbaren:

   ![Workflow maken vanuit de tijdlijn](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. Met de wizard **Workflow maken** kunt u [de workflowdetails opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Workflowdetails opgeven in de wizard Workflow maken {#specifying-workflow-details-in-the-create-workflow-wizard}

Met de wizard **Workflow maken** kunt u de workflow selecteren en de vereiste details opgeven.

Na het openen van **Create Workflow** tovenaar van of:

* [Kies de optie Maken op de werkbalk](#starting-a-workflow-from-the-sites-toolbar) Sites.
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

U kunt details opgeven:

1. In de stap **Eigenschappen** worden de basisopties van de workflow gedefinieerd:

   * **Workflowmodel**
   * **Titel werkstroom**

      * U kunt een titel voor dit exemplaar specificeren, om u te helpen het in een later stadium identificeren.

   Afhankelijk van het workflowmodel zijn ook de volgende opties beschikbaar. Hierdoor kan het pakket dat als lading is gemaakt, worden bewaard nadat de workflow is voltooid.

   * **Workflowpakket behouden**
   * **Pakkettitel**

      * U kunt een titel voor het pakket opgeven om het te identificeren.
   >[!NOTE]
   >
   >De optie **Workflowpakket bijhouden** is beschikbaar wanneer de workflow is geconfigureerd voor ondersteuning van meerdere resources en er meerdere resources zijn geselecteerd.

   <!--
   >The **Keep workflow package** option is available when the workflow has been configured for [Multi Resource Support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) and multiple resources have been selected.
   -->

   Wanneer volledig, gebruik **Volgende** om te werk te gaan.

   ![Eigenschappen van werkstromen opgeven](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. In de stap **Scope** kunt u selecteren:

   * **Voeg** Inhoud toe om  [wegbrowser ](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) te openen en extra middelen te selecteren; Als u in de browser op Selecteren klikt of tikt  **** om de inhoud aan de werkstroominstantie toe te voegen.

   * Een bestaande bron voor het weergeven van extra handelingen:

      * **Neem** kinderen op om op te geven dat onderliggende elementen van die bron worden opgenomen in de workflow.
Er wordt een dialoogvenster geopend waarin u de selectie kunt verfijnen op basis van:

         * Alleen directe kinderen opnemen.
         * Alleen gewijzigde pagina&#39;s opnemen.
         * Alleen al gepubliceerde pagina&#39;s opnemen.

         Alle opgegeven onderliggende items worden toegevoegd aan de lijst met bronnen waarop de workflow van toepassing is.

      * **Verwijder** Selectie om die bron uit de workflow te verwijderen.

   ![Werkstroombereik definiëren](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >Als u aanvullende resources toevoegt, kunt u **Terug** gebruiken om de instelling voor **Workflowpakket behouden** aan te passen in de stap **Eigenschappen**.

1. Gebruik **Maken** om de wizard te sluiten en de werkstroominstantie te maken. Een bericht wordt getoond in de console van Plaatsen.

## Een workflow starten vanuit de Pagina-editor {#starting-a-workflow-from-the-page-editor}

Wanneer u een pagina bewerkt, kunt u **Pagina-informatie** op de werkbalk selecteren. Het drop-down menu heeft de optie **Begin in Werkschema**. Hiermee wordt een dialoogvenster geopend waarin u de vereiste workflow kunt opgeven, en desgewenst een titel:

![Een workflow starten vanuit de pagina-editor](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
