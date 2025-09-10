---
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
description: Een adaptief formulier biedt meerdere verzendhandelingen. Met een handeling Verzenden wordt gedefinieerd hoe een adaptief formulier wordt verwerkt na verzending. U kunt ingebouwde verzendhandelingen gebruiken of uw eigen handelingen maken.
keywords: hoe u verzendactie selecteert voor een adaptief formulier, een adaptief formulier koppelt aan een SharePoint-lijst, een adaptief formulier aansluit op een SharePoint-documentbibliotheek, een adaptief formulier aansluit op een formuliergegevensmodel (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Handeling Adaptief verzenden van formulier

| Versie | Artikelkoppeling |
|---------|-----------------------------|
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service (Foundation Components) | [ klik hier ](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (Core Components) | [ klik hier ](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Dit artikel |


De voorlegging van de vorm is de kritieke definitieve stap in de gebruikersreis-het is waar de verzamelde gegevens worden verwerkt en de acties worden genomen. Dit document bevat een uitgebreide handleiding voor het configureren en beheren van verzendhandelingen voor Adaptive Forms in Universal Editor.

## Wat leert u?

Aan het einde van dit document leert u hoe u:

- Verschillende typen verzendacties configureren voor uw formulieren
- REST-eindpuntindieningen instellen voor integratie met externe systemen
- E-mailverzendingen voor formulierreacties configureren
- Implementeer aangepaste verzendacties voor specifieke bedrijfsbehoeften
- Formuliervalidatie en foutscenario&#39;s tijdens verzending verwerken

## Doelpubliek

Deze handleiding is ontworpen voor:

- **de ontwikkelaars van de Vorm** die voorleggingslogica uitvoeren
- **integrators van het Systeem** verbindend vormen met achterste systemen
- **Bedrijfs analisten** die vormwerkschema&#39;s bepalen
- **Technische architecten** ontwerpend processen van de vormvoorlegging

## Handelingen verzenden voor Forms die zijn gemaakt in de Universal Editor

Het volgende voorlegt acties wordt gesteund door [ Aangepaste Forms authored in de Universele Redacteur ](/help/edge/docs/forms/universal-editor/create-forms.md):

- [E-mail verzenden](/help/forms/configure-submit-action-send-email.md)
- [Een automatische stroomvoorziening aanroepen](/help/forms/forms-microsoft-power-automate-integration.md)
- [Verzenden naar SharePoint](/help/forms/configure-submit-action-sharepoint.md)
- [Workfront Fusion aanroepen](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Verzenden met gebruik van FDM (Form Data Model)](/help/forms/integrate-adaptive-form-with-fdm.md)
- [Verzenden naar Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Verzenden naar REST-eindpunt](/help/forms/configure-submit-action-restpoint.md)
- [Verzenden naar OneDrive](/help/forms/configure-submit-action-onedrive.md)
- [Een AEM-workflow aanroepen](/help/forms/configure-submit-action-workflow.md)
- [Verzenden naar Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)
- [Verzenden naar Adobe Experience Platform (AEP)](/help/forms/aem-forms-aep-connector.md)
- [Verzenden naar werkblad](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

U kunt de verzendactie voor vormen vormen vormen die in de Universele Redacteur worden gecreeerd gebruikend het **lusje van de Verzending** van **uitgeven de uitbreiding van de Eigenschappen van de Vorm**.

**hoe te vormen verzend Actie voor Forms authored in Universele Redacteur?**
U kunt de verzendactie voor vormen vormen vormen die in de Universele Redacteur worden gecreeerd gebruikend het **Verzending** lusje van **uitgeven de uitbreiding van de Eigenschappen van de Vorm**.

![ de eigenschappen van de Vorm pictogram ](/help/forms/assets/ue-form-properties-icon.png)

![ tovenaar van de Eigenschappen van 0} Vorm](/help/edge/docs/forms/universal-editor/assets/form-properties-ue.png)

>[!NOTE]
>
> - Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3} uitbreiding van de Eigenschappen van de Vorm {in Extension Manager uit.**
> - Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)
