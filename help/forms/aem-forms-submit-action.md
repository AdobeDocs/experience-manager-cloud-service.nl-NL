---
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
description: Een adaptief formulier biedt meerdere verzendhandelingen. Met een handeling Verzenden wordt gedefinieerd hoe een adaptief formulier wordt verwerkt na verzending. U kunt ingebouwde verzendhandelingen gebruiken of uw eigen handelingen maken.
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---


# Handelingen verzenden die worden ondersteund door Adaptive Forms

Met Adaptieve Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. Ze bieden een intuïtieve gebruikersinterface en een set van kant-en-klare componenten voor het efficiënt ontwerpen en beheren van formulieren. U kunt verschillende verzendacties configureren om formuliergegevens te verzenden naar services zoals OneDrive, SharePoint, Workfront Fusion en meer.

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop **[!UICONTROL Submit]** op een adaptief formulier klikt. Forms as a Cloud Service bevat verschillende verzendacties uit het tekstvak. Met de ingebouwde verzendacties kunt u:

* Formuliergegevens eenvoudig verzenden via e-mail
* Start Microsoft® Power Automate-stromen of AEM Workflows tijdens het verzenden van de gegevens.
* Verzend de formuliergegevens rechtstreeks naar Microsoft® SharePoint Server, Microsoft® Azure Blob Storage of Microsoft® OneDrive.
* Verzend naadloos de gegevens naar een gevormde gegevensbron gebruikend het Model van de Gegevens van de Vorm (FDM).
* Verzend de gegevens gemakkelijk naar een REST-eindpunt.

## Handelingen verzenden die worden ondersteund door Adaptive Forms

AEM-formulieren bieden de volgende verzendacties uit de verpakking:

* [E-mail verzenden](/help/forms/configure-submit-action-send-email.md)
* [Een automatische stroomvoorziening aanroepen](/help/forms/forms-microsoft-power-automate-integration.md)
* [Verzenden naar SharePoint](/help/forms/configure-submit-action-sharepoint.md)
* [Een Workfront Fusion aanroepen](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Verzenden met gebruik van FDM (Form Data Model)](/help/forms/using-form-data-model.md)
* [Verzenden naar Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Verzenden naar REST-eindpunt](/help/forms/configure-submit-action-restpoint.md)
* [Verzenden naar OneDrive](/help/forms/configure-submit-action-onedrive.md)
* [Een AEM-workflow aanroepen](/help/forms/configure-submit-action-workflow.md)
* [Verzenden naar Marketo-pagina](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [&#x200B; voorleggen aan Adobe Experience Platform (AEP) &#x200B;](/help/forms/aem-forms-aep-connector.md)
* [Verzenden naar werkblad](/help/forms/forms-submission-service.md)

U kunt ook een adaptief formulier verzenden naar andere opslagconfiguraties:

* [Aangepast formulier verbinden met Salesforce-toepassing](/help/forms/aem-forms-salesforce-integration.md)
* [Een adaptief formulier verbinden met Microsoft](/help/forms/ms-dynamics-odata-configuration.md)

## Ondersteuning voor handelingen verzenden voor alle ontwerptypen

In de volgende tabel wordt aangegeven welke verzendacties worden ondersteund op basis van de in AEM Forms gebruikte methode voor het schrijven van formulieren:

| Handeling verzenden | [&#x200B; Componenten van de Stichting &#x200B;](/help/forms/configuring-submit-actions.md) | [&#x200B; Componenten van de Kern &#x200B;](/help/forms/configure-submit-actions-core-components.md) | [&#x200B; Universele Redacteur &#x200B;](/help/forms/configure-submit-action-eds-forms.md#submit-actions-supported-by-adaptive-forms-created-in-universal-editor) | [&#x200B; op document-Gebaseerde Forms &#x200B;](/help/forms/configure-submit-action-eds-forms.md#supported-submit-actions-for-document-based-forms) |
|----------------------------|------------------------|------------------|------------------|------------------------|
| E-mail verzenden | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Power Automated Flow | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden naar SharePoint | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Workfront Fusion | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden met FDM | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden naar AEP | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Azure Blob Storage | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden naar REST-eindpunt | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden naar Marketo Engage | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden naar OneDrive | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| AEM-workflow aanroepen | ✅ Ondersteund | ✅ Ondersteund | ✅ Ondersteund |                        |
| Verzenden naar werkblad |                        |                  | ✅ Ondersteund | ✅ Ondersteund |


## Revalidatie op de server in adaptieve vorm

In elk onlinesysteem voor gegevensvastlegging plaatsen ontwikkelaars doorgaans bepaalde JavaScript-validaties op de client om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Deze technieken gelden ook voor Adaptive Forms. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor validatie aan de serverzijde kunt u ook de validaties uitvoeren die een Adaptive Forms-auteur heeft verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.


### Wat moet u op de server valideren?

Alle OOTB-veldvalidaties (out-of-box) van een adaptief formulier die opnieuw worden uitgevoerd op de server zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

Gebruik de **[!UICONTROL Revalidate on server]** onder Adaptief formuliercontainer in de zijbalk om validatie op de server in of uit te schakelen voor het huidige formulier.

![&#x200B; toelatend server-zijBevestiging &#x200B;](assets/revalidate-on-server.png)

**toelatend server-zijBevestiging**

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie aan het einde van de server mislukt, wordt de verzendtransactie gestopt. De gebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

>[!NOTE]
>
>Servervalidatie valideert het formuliermodel. U wordt aangeraden een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML styling en DOM manipulation in dezelfde clientbibliotheek.

<!--### Supporting Custom functions in Validation Expressions {#supporting-custom-functions-in-validation-expressions-br}

At times, if there are **complex validation rules**, the exact validation script reside in custom functions and author calls these custom functions from field validation expression. To make this custom function library known and available while performing server-side validations, the form author can configure the name of AEM client library under the **[!UICONTROL Basic]** tab of Adaptive Form Container properties as shown below.

![Supporting Custom functions in Validation Expressions](assets/clientlib-cat.png)

Supporting Custom functions in Validation Expressions

Author can configure customJavaScript library per Adaptive Form. In the library, only keep the reusable functions, which have dependency on jquery and underscore.js third-party libraries.

Refer to the following articles to learn how to create custom functions for:

* [Adaptive Forms based on Foundation Components](/help/forms/rule-editor.md#custom-functions-in-rule-editor)
* [Adaptive Forms based on Core Components](/help/forms/create-and-use-custom-functions.md)
* [Adaptive Forms authored using Document-Based Authoring](/help/edge/docs/forms/rules-forms.md#create-a-custom-function)
* [Adaptive Forms created using the Universal Editor](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#create-a-custom-function)

## Error handling on Submit Action {#error-handling-on-submit-action}

As a part of AEM security and hardening guidelines, configure custom error pages such as 400.jsp, 404.jsp, and 500.jsp. These handlers are called, when on submitting a form 400, 404, or 500 errors appear. The handlers are also called when these error codes are triggered on the Publish node. You can also create JSP pages for other HTTP error codes.

When you prefill a form data model (FDM), or schema based Adaptive Form with XML or JSON data complaint to a schema that is data does not contain `<afData>`, `<afBoundData>`, and `</afUnboundData>` tags, then the data of unbounded fields of the Adaptive Form is lost. The schema can be an XML schema, JSON schema, or a Form Data Model (FDM). Unbounded fields are Adaptive Form fields without the `bindref` property.-->

## Zie ook

{{af-submit-action}}

