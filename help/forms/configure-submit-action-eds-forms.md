---
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
description: Een adaptief formulier biedt meerdere verzendhandelingen. Met een handeling Verzenden wordt gedefinieerd hoe een adaptief formulier wordt verwerkt na verzending. U kunt ingebouwde verzendhandelingen gebruiken of uw eigen handelingen maken.
keywords: hoe u verzendactie selecteert voor een adaptief formulier, een adaptief formulier koppelt aan een SharePoint-lijst, een adaptief formulier aansluit op een SharePoint-documentbibliotheek, een adaptief formulier aansluit op een formuliergegevensmodel (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# Handelingen verzenden voor Edge Delivery Services Forms

| Versie | Artikelkoppeling |
|---------|-----------------------------|
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service (Foundation Components) | [ klik hier ](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (Core Components) | [ klik hier ](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Dit artikel |

Met Verzendhandelingen wordt gedefinieerd wat er gebeurt wanneer een gebruiker een formulier verzendt, zoals gegevens opslaan, workflows activeren of integreren met systemen van derden. Het type verzendacties dat u kunt configureren, is afhankelijk van de ontwerpmethode die wordt gebruikt om Edge Delivery Services Forms te maken.

U kunt Edge Delivery Services Forms tot stand brengen gebruikend of de [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) of door [ Document Gebaseerd Forms ](/help/edge/docs/forms/overview.md) te gebruiken creeert creeert, en de vormen met verschillend vormt dienovereenkomstig voorlegt acties.

## Handelingen verzenden voor Forms die zijn gemaakt in de Universal Editor

Het volgende voorlegt acties wordt gesteund door [ Aangepaste Forms authored in de Universele Redacteur ](/help/edge/docs/forms/universal-editor/create-forms.md):

* [E-mail verzenden](/help/forms/configure-submit-action-send-email.md)
* [Een automatische stroomvoorziening aanroepen](/help/forms/forms-microsoft-power-automate-integration.md)
* [Verzenden naar SharePoint](/help/forms/configure-submit-action-sharepoint.md)
* [Workfront Fusion aanroepen](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Verzenden met gebruik van FDM (Form Data Model)](/help/forms/using-form-data-model.md)
* [Verzenden naar Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Verzenden naar REST-eindpunt](/help/forms/configure-submit-action-restpoint.md)
* [Verzenden naar OneDrive](/help/forms/configure-submit-action-onedrive.md)
* [Een AEM-workflow aanroepen](/help/forms/configure-submit-action-workflow.md)
* [Verzenden naar Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [Verzenden naar Adobe Experience Platform (AEP)](/help/forms/aem-forms-aep-connector.md)
* [Verzenden naar werkblad](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

U kunt de verzendactie voor vormen vormen vormen die in de Universele Redacteur worden gecreeerd gebruikend het **lusje van de Verzending** van **uitgeven de uitbreiding van de Eigenschappen van de Vorm**.

<!--**How to Configure Submit Action for Forms authored in Universal Editor?**
You can configure the submit action for forms created in the Universal Editor using the **Submission** tab of the **Edit Form Properties** extension.

![Form properties icon](/help/forms/assets/ue-form-properties-icon.png)

![Universal Editor Form Properties](/help/forms/assets/ue-form-properties.png)-->

>[!NOTE]
>
> * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3} uitbreiding van de Eigenschappen van de Vorm {in Extension Manager uit.**
> * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## Handelingen verzenden voor Forms op basis van document

Forms-supportverzending op basis van documenten alleen naar werkbladen. Leren hoe te opstelling uw spreadsheet om voorgelegde gegevens te ontvangen, zie de instructies in de [ Opstelling uw Bladen van Google of de dossiers van Microsoft Excel beginnen gegevens ](/help/edge/docs/forms/submit-forms.md) goed te keuren.

## Zie ook {#see-also}

{{af-submit-action}}

