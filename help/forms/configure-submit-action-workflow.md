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

Met de handeling **[!UICONTROL Invoke an AEM Workflow]** Verzenden wordt een adaptief formulier gekoppeld aan een AEM workflow. Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt de gegevensbestanden, bijlagen en Document of Record opslaan op de laadlocatie van de workflow of op een variabele. Als de workflow is gemarkeerd voor externe gegevensopslag en geconfigureerd voor externe gegevensopslag, is alleen de optie Variabele beschikbaar. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

>[!NOTE]
>
>  Leer hoe te [ een werkschemamodel ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) creëren om de reeks uitgevoerde stappen te bepalen wanneer een gebruiker het werkschema begint. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

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

Aan opstelling geautomatiseerd proces met [ AEM Werkschema ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) voor een AanpassingsVorm, voer de volgende stappen uit:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer **[!UICONTROL Invoke an AEM Workflow]** in de vervolgkeuzelijst **[!UICONTROL Submit Action]** .
   ![ configuratie van de Actie van Send E-mail ](/help/forms/assets/configure-invoke-aem-workflow.png)

1. Selecteer het workflowmodel in de vervolgkeuzelijst **[!UICONTROL Workflow Model]** .
1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Store Data file using]** .

   **dossier van Gegevens**: Het bevat gegevens die aan de Aangepaste Vorm worden voorgelegd. Met de optie **[!UICONTROL Data File Path]** kunt u de naam van het bestand en het pad van het bestand ten opzichte van de laadbewerking opgeven. Het pad `/addresschange/data.xml` maakt bijvoorbeeld een map met de naam `addresschange` en plaatst deze relatief ten opzichte van de laadbewerking. U kunt ook alleen `data.xml` opgeven om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Store attachments using]** .

   **Gehechtheid**: U kunt de **[!UICONTROL Attachment Path]** optie gebruiken om de omslagnaam te specificeren om de gehechtheid op te slaan die aan de Aangepaste Vorm wordt geupload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Documents of record using]** .

   **Document van Verslag**: Het bevat het Document van Verslag dat voor de Adaptieve Vorm wordt geproduceerd. U kunt de optie **[!UICONTROL Document of Record Path]** gebruiken om de naam van het document van het dossier van het Verslag en weg van dossier met betrekking tot de lading te specificeren. Het pad `/addresschange/DoR.pdf` maakt bijvoorbeeld een map met de naam `addresschange` ten opzichte van de laadbewerking en plaatst de map `DoR.pdf` ten opzichte van de laadbewerking. U kunt ook alleen `DoR.pdf` opgeven om alleen Document of Record op te slaan zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.
1. Klik op **[!UICONTROL Done]**.

>[!NOTE]
>
> Leer meer over [ Forms-centric AEM Workflows - de Verwijzing van de Stap om bedrijfsprocessen ](/help/forms/aem-forms-workflow-step-reference.md) te automatiseren.

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Verwante artikelen

{{af-submit-action}}
