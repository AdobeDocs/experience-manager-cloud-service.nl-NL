---
title: Workflows toepassen op pagina's
description: Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina's. het is ook mogelijk meerdere werkschema's toe te passen.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Workflows toepassen op pagina&#39;s {#applying-workflows-to-pages}

Tijdens het ontwerpen kunt u workflows aanroepen om actie te ondernemen op uw pagina&#39;s. het is ook mogelijk meerdere werkstromen toe te passen .

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.
   * U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Naar keuze, een titel die helpt de werkschemainstantie in Inbox van een gebruiker identificeren.
* de workflow-lading; dit kan een of meer pagina&#39;s zijn.

Workflows kunnen worden gestart vanaf:

* [de **Sites** -console](#starting-a-workflow-from-the-sites-console).
* [bij het bewerken van een pagina, uit **Pagina-informatie **](#starting-a-workflow-from-the-page-editor).

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
>AEM-beheerders kunnen workflows starten met verschillende andere methoden.
<!--
>AEM administrators can [start workflows using several other methods](/help/sites-administering/workflows-starting.md).
-->

## Een workflow starten vanuit de siteconsole {#starting-a-workflow-from-the-sites-console}

U kunt een workflow starten vanuit:

* [de optie **Maken** van de werkbalk](#starting-a-workflow-from-the-sites-toolbar)Sites.
* [de **tijdlijn** van de Sites-console](#starting-a-workflow-from-the-timeline).

In beide gevallen moet u:

* [Geef de workflowdetails op in de wizard](#specifying-workflow-details-in-the-create-workflow-wizard)Workflow maken.

### Een workflow starten op de werkbalk Sites {#starting-a-workflow-from-the-sites-toolbar}

U kunt een workflow starten op de werkbalk van de **Sites** -console:

1. Navigeer naar de gewenste pagina en selecteer deze.

1. Met de optie **Maken** op de werkbalk kunt u nu **Workflow** selecteren.

   ![Werkstroom maken van de werkbalk](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. Met de wizard **Workflow** maken kunt u de workflowdetails [opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten vanuit de tijdlijn {#starting-a-workflow-from-the-timeline}

Vanuit de **tijdlijn** kunt u een workflow starten die op de geselecteerde bron moet worden toegepast.

1. [Selecteer de bron](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) en open [tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) (of open tijdlijn en selecteer de bron).
1. De pijlpunt door het commentaargebied kan worden gebruikt om het Werkschema **van het** Begin te onthullen:

   ![Workflow maken vanuit de tijdlijn](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. Met de wizard **Workflow** maken kunt u de workflowdetails [opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Workflowdetails opgeven in de wizard Workflow maken {#specifying-workflow-details-in-the-create-workflow-wizard}

Met de wizard **Workflow** maken kunt u de workflow selecteren en de vereiste details opgeven.

Nadat u de wizard **Workflow** maken hebt geopend vanuit:

* [de optie **Maken** van de werkbalk](#starting-a-workflow-from-the-sites-toolbar)Sites.
* [de **tijdlijn** van de Sites-console](#starting-a-workflow-from-the-timeline).

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
   >De optie Workflowpakket **** bijeenhouden is beschikbaar wanneer de workflow is geconfigureerd voor ondersteuning van meerdere bronnen en er meerdere bronnen zijn geselecteerd.
   <!--
   >The **Keep workflow package** option is available when the workflow has been configured for [Multi Resource Support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) and multiple resources have been selected.
   -->

   Als u klaar bent, gebruikt u **Volgende** om door te gaan.

   ![Eigenschappen van werkstromen opgeven](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. In de stap **Bereik** kunt u selecteren:

   * **Voeg Inhoud** toe om de [padbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) te openen en selecteer aanvullende bronnen. Klik in de browser op **Selecteren** of tik op Selecteren om de inhoud aan de werkstroominstantie toe te voegen.

   * Een bestaande bron voor het weergeven van extra handelingen:

      * **Neem onderliggende elementen** op om op te geven dat onderliggende elementen van die bron worden opgenomen in de workflow.
Er wordt een dialoogvenster geopend waarin u de selectie kunt verfijnen op basis van:

         * Alleen directe kinderen opnemen.
         * Alleen gewijzigde pagina&#39;s opnemen.
         * Alleen al gepubliceerde pagina&#39;s opnemen.
         Alle opgegeven onderliggende items worden toegevoegd aan de lijst met bronnen waarop de workflow van toepassing is.

      * **Selectie** verwijderen om die bron uit de workflow te verwijderen.
   ![Werkstroombereik definiëren](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >Als u aanvullende bronnen toevoegt, kunt u **Terug** gebruiken om de instelling voor het werkstroompakket **** Behouden aan te passen in de stap **Eigenschappen** .

1. Gebruik **Maken** om de wizard te sluiten en de instantie van de workflow te maken. Een bericht wordt getoond in de console van Plaatsen.

## Een workflow starten vanuit de Pagina-editor {#starting-a-workflow-from-the-page-editor}

Als u een pagina bewerkt, kunt u op de werkbalk **Pagina-informatie** selecteren. Het vervolgkeuzemenu heeft de optie **Start in Workflow**. Hiermee wordt een dialoogvenster geopend waarin u de vereiste workflow kunt opgeven, en desgewenst een titel:

![Een workflow starten vanuit de pagina-editor](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
