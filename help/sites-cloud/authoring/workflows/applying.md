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

* [de Sites-console](#starting-a-workflow-from-the-sites-console).
* [bij het bewerken van een pagina, uit paginagegevens](#starting-a-workflow-from-the-page-editor).

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

* [De optie Maken op de werkbalk Sites](#starting-a-workflow-from-the-sites-toolbar).
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

In beide gevallen moet u [Geef de workflowdetails op in de wizard Workflow maken](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten op de werkbalk Sites {#starting-a-workflow-from-the-sites-toolbar}

U kunt een workflow starten op de werkbalk van het dialoogvenster **Sites** console:

1. Navigeer naar de gewenste pagina en selecteer deze.

1. Van de **Maken** in de werkbalk die u nu kunt selecteren **Workflow**.

   ![Werkstroom maken van de werkbalk](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. De **Workflow maken** wizard helpt u [de workflowdetails opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Een workflow starten vanuit de tijdlijn {#starting-a-workflow-from-the-timeline}

Van de **Tijdlijn** u kunt een workflow starten die op de geselecteerde bron moet worden toegepast.

1. [Selecteer de bron](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) en open [Tijdlijn](/help/sites-cloud/authoring/basic-handling.md#timeline) (U kunt Tijdlijn openen en vervolgens de bron selecteren).
1. De pijlpunt op het veld Opmerking kan worden gebruikt om **Workflow starten**:

   ![Workflow maken vanuit de tijdlijn](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. De **Workflow maken** wizard helpt u [de workflowdetails opgeven](#specifying-workflow-details-in-the-create-workflow-wizard).

### Workflowdetails opgeven in de wizard Workflow maken {#specifying-workflow-details-in-the-create-workflow-wizard}

De **Workflow maken** De wizard helpt u de workflow te selecteren en de vereiste details op te geven.

Na het openen van de **Workflow maken** wizard van:

* [De optie Maken op de werkbalk Sites](#starting-a-workflow-from-the-sites-toolbar).
* [de tijdlijnrail van de Sites-console](#starting-a-workflow-from-the-timeline).

U kunt details specificeren:

1. In de **Eigenschappen** De basisopties van de workflow worden nu gedefinieerd:

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

   Na voltooiing gebruiken **Volgende** om verder te gaan.

   ![Eigenschappen van werkstromen opgeven](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. In de **Toepassingsgebied** stap die u kunt selecteren:

   * **Inhoud toevoegen** om de [padbrowser](/help/sites-cloud/authoring/path-selection.md) en selecteer aanvullende bronnen; selecteer in de browser de optie **Selecteren** om de inhoud aan de werkstroominstantie toe te voegen.

   * Een bestaande bron voor het weergeven van extra handelingen:

      * **Inclusief onderliggende items** om te specificeren dat de kinderen van die bron in het werkschema inbegrepen zijn.
Er wordt een dialoogvenster geopend waarin u de selectie kunt verfijnen op basis van:

         * Alleen directe kinderen opnemen.
         * Alleen gewijzigde pagina&#39;s opnemen.
         * Alleen al gepubliceerde pagina&#39;s opnemen.

        Alle opgegeven onderliggende items worden toegevoegd aan de lijst met bronnen waarop de workflow van toepassing is.

      * **Selectie verwijderen** om die bron uit de workflow te verwijderen.

   ![Werkstroombereik definiëren](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >Als u aanvullende resources toevoegt, kunt u **Terug** gebruiken om de instelling voor **Workflowpakket behouden** aan te passen in de stap **Eigenschappen**.

1. Gebruiken **Maken** om de wizard te sluiten en de instantie van de workflow te maken. Een bericht wordt getoond in de console van Plaatsen.

## Een workflow starten vanuit de Pagina-editor {#starting-a-workflow-from-the-page-editor}

Als u een pagina bewerkt, kunt u **Pagina-informatie** op de werkbalk. Het vervolgkeuzemenu heeft de optie **Starten in workflow**. Hiermee wordt een dialoogvenster geopend waarin u de vereiste workflow kunt opgeven, zo nodig met een titel:

![Een workflow starten vanuit de pagina-editor](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
