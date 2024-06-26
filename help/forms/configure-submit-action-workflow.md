---
Title: How to integrate AEM workflow with an Adaptive Form?
Description: Explore the process of automated workflow initiation with AEM Forms Submit Action.
keywords: AEM workflow, Adaptief formulier integreren met AEM workflow, AEM workflow voor verzenden van handeling aanroepen
feature: Adaptive Forms, Core Components
exl-id: b7788e3d-acd8-4867-b232-f9767cf6b2f5
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Integreer AEM adaptief formulier met AEM workflow: bedrijfsprocessen stroomlijnen

De **[!UICONTROL Invoke an AEM Workflow]** Met Actie verzenden wordt een adaptief formulier gekoppeld aan een AEM workflow. Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt de gegevensbestanden, bijlagen en Document of Record opslaan op de laadlocatie van de workflow of op een variabele. Als de workflow is gemarkeerd voor externe gegevensopslag en geconfigureerd voor externe gegevensopslag, is alleen de optie Variabele beschikbaar. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

>[!NOTE]
>
>  Leer hoe u [een workflowmodel maken](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) om de reeks stappen te definiëren die worden uitgevoerd wanneer een gebruiker de workflow start. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md)  artikel.

## Voordelen

Enkele voordelen van de integratie van AEM workflow met Adaptive Forms zijn:

* AEM de integratie van het Werkschema staat voor de automatisering van complexe bedrijfsprocessen toe die vormvoorlegging impliceren.
* AEM Workflow ondersteunt voorwaardelijke logica, zodat dynamische beslissingen op basis van formuliergegevens of externe factoren mogelijk zijn.
* AEM de routetaken van het Werkschema die op vooraf bepaalde regels en voorwaarden worden gebaseerd, die taken verzekeren worden toegewezen aan de juiste individuen of groepen.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## Integreer AEM workflow met Adaptive Forms {#steps-to-integrate-workflow-with-af}

Automatisch proces instellen met [AEM](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) Voer voor een adaptief formulier de volgende stappen uit:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de knop  **[!UICONTROL Submission]** tab.
1. Van de **[!UICONTROL Submit Action]** vervolgkeuzelijst, selecteert u **[!UICONTROL Invoke an AEM Workflow]** .
   ![Actieconfiguratie van Send Email](/help/forms/assets/configure-invoke-aem-workflow.png)

1. Selecteer een workflowmodel in het menu **[!UICONTROL Workflow Model]** vervolgkeuzelijst.
1. Selecteer een optie in het menu **[!UICONTROL Store Data file using]** vervolgkeuzelijst.

   **Gegevensbestand**: Het bevat gegevens die naar het adaptieve formulier worden verzonden. U kunt de **[!UICONTROL Data File Path]** om de naam van het bestand en het pad van het bestand ten opzichte van de laadbewerking op te geven. Bijvoorbeeld de `/addresschange/data.xml` pad maakt een map met de naam `addresschange` en plaatst deze ten opzichte van de lading. U kunt ook alleen `data.xml` om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

1. Selecteer een optie in het menu **[!UICONTROL Store attachments using]** vervolgkeuzelijst.

   **Bijlagen**: U kunt de opdracht **[!UICONTROL Attachment Path]** om de mapnaam op te geven waarin de bijlagen worden opgeslagen die naar het adaptieve formulier zijn geüpload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

1. Selecteer een optie in het menu **[!UICONTROL Documents of record using]** vervolgkeuzelijst.

   **Document van record**: Het bevat het Document of Record dat is gegenereerd voor het adaptieve formulier. U kunt de **[!UICONTROL Document of Record Path]** Hiermee geeft u de naam op van het bestand Document of Record en het pad van het bestand ten opzichte van de laadbewerking. Bijvoorbeeld de `/addresschange/DoR.pdf` pad maakt een map met de naam `addresschange` ten opzichte van de lading en plaatst het `DoR.pdf` ten opzichte van de lading. U kunt ook alleen `DoR.pdf` alleen Document of Record opslaan zonder een mappenhiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.
1. Klik op **[!UICONTROL Done]**.

>[!NOTE]
>
> Meer informatie over [Forms-centric AEM Workflows - Step Reference to automatisate Business Processors](/help/forms/aem-forms-workflow-step-reference.md).

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Verwante artikelen

{{af-submit-action}}
