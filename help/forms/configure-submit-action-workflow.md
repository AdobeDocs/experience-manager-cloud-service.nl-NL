---
title: Hoe te om de werkschema van AEM met een Aangepast Vorm te integreren?
description: Verken het proces van automatische werkstroominitiëring met AEM Forms Submit Action.
keywords: AEM-workflow, Adaptief formulier integreren met AEM-workflow, Invoke AEM-workflow Handeling verzenden
feature: Adaptive Forms, Core Components
exl-id: b7788e3d-acd8-4867-b232-f9767cf6b2f5
role: User, Developer
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 0%

---

# AEM Adaptief formulier integreren met AEM Workflow: bedrijfsprocessen stroomlijnen

Met de handeling **[!UICONTROL Invoke an AEM Workflow]** Verzenden wordt een adaptief formulier gekoppeld aan een AEM-workflow. Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt de gegevensbestanden, bijlagen en Document of Record opslaan op de laadlocatie van de workflow of op een variabele. Als de workflow is gemarkeerd voor externe gegevensopslag en geconfigureerd voor externe gegevensopslag, is alleen de optie Variabele beschikbaar. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

>[!NOTE]
>
>  Leer hoe te [ een werkschemamodel ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) creëren om de reeks uitgevoerde stappen te bepalen wanneer een gebruiker het werkschema begint. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

## Voordelen

Een aantal voordelen van de integratie van de AEM-workflow met Adaptive Forms zijn:

* Dankzij de AEM Workflowintegratie kunnen complexe bedrijfsprocessen worden geautomatiseerd, waarbij formulieren worden verzonden.
* AEM Workflow ondersteunt voorwaardelijke logica, zodat dynamische beslissingen mogelijk zijn op basis van formuliergegevens of externe factoren.
* AEM Workflow routeert taken die op vooraf bepaalde regels en voorwaarden worden gebaseerd, die taken verzekeren worden toegewezen aan de juiste individuen of groepen.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## AEM Workflow integreren met Adaptive Forms {#steps-to-integrate-workflow-with-af}

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Aan opstelling geautomatiseerd proces met [ het Werkschema van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) voor een Aanpassings Vorm die op de Componenten van de Stichting wordt gebaseerd, voer de volgende stappen uit:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Van de **[!UICONTROL Submit Action]** drop-down lijst, uitgezochte **legt Actie** als **[!UICONTROL Invoke an AEM workflow]** voor.
1. Selecteer het workflowmodel in de vervolgkeuzelijst **[!UICONTROL Workflow Model]** .
1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Store Data file using]** .

   **dossier van Gegevens**: Het bevat gegevens die aan de Aangepaste Vorm worden voorgelegd. Met de optie **[!UICONTROL Data File Path]** kunt u de naam van het bestand en het pad van het bestand ten opzichte van de laadbewerking opgeven. Het pad `/addresschange/data.xml` maakt bijvoorbeeld een map met de naam `addresschange` en plaatst deze relatief ten opzichte van de laadbewerking. U kunt ook alleen `data.xml` opgeven om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

   ![ aanhalen-werkschema-fc ](/help/forms/assets/invoke-workflow-fc.png)

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Store attachments using]** .

   **Gehechtheid**: U kunt de **[!UICONTROL Attachment Path]** optie gebruiken om de omslagnaam te specificeren om de gehechtheid op te slaan die aan de Aangepaste Vorm wordt geupload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Documents of record using]** .

   **Document van Verslag**: Het bevat het Document van Verslag dat voor de Adaptieve Vorm wordt geproduceerd. U kunt de optie **[!UICONTROL Document of Record Path]** gebruiken om de naam van het document van het dossier van het Verslag en weg van dossier met betrekking tot de lading te specificeren. Het pad `/addresschange/DoR.pdf` maakt bijvoorbeeld een map met de naam `addresschange` ten opzichte van de laadbewerking en plaatst de map `DoR.pdf` ten opzichte van de laadbewerking. U kunt ook alleen `DoR.pdf` opgeven om alleen Document of Record op te slaan zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.
1. Klik op **[!UICONTROL Done]**.

   >[!NOTE]
   >
   > Leer meer over [ Forms-centric de Workflows van AEM - de Verwijzing van de Stap om bedrijfsprocessen ](/help/forms/aem-forms-workflow-step-reference.md) te automatiseren.

>[!TAB  Component van de Kern ]

Aan opstelling geautomatiseerd proces met [ het Werkschema van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) voor een Aanpassings Vorm die op de Componenten van de Kern wordt gebaseerd, voer de volgende stappen uit:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer **[!UICONTROL Submit Action]** in de vervolgkeuzelijst **[!UICONTROL Invoke an AEM Workflow]** .

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
   > Leer meer over [ Forms-centric de Workflows van AEM - de Verwijzing van de Stap om bedrijfsprocessen ](/help/forms/aem-forms-workflow-step-reference.md) te automatiseren.

>[!TAB  Universele Redacteur ]

Aan opstelling geautomatiseerd proces met [ het Werkschema van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) voor een Aangepaste Vorm authored in Universele Redacteur, voer de volgende stappen uit:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3&rbrace; uitbreiding van de Eigenschappen van de Vorm &lbrace;in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0&rbrace; Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

1. Klik **Verzending** lusje en selecteer **[!UICONTROL Invoke an AEM Workflow]** voorlegt actie.


   ![ configuratie van de Actie van Send E-mail ](/help/forms/assets/invoke-service-ue.png)

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
   > Leer meer over [ Forms-centric de Workflows van AEM - de Verwijzing van de Stap om bedrijfsprocessen ](/help/forms/aem-forms-workflow-step-reference.md) te automatiseren.

>[!ENDTABS]

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Verwante artikelen

{{af-submit-action}}
