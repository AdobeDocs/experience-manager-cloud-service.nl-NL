---
title: 'Belangrijke functies en mogelijkheden van Adobe Experience Manager (AEM) Forms as a Cloud Service '
description: '[!DNL AEM Forms] as a Cloud Service is een platform voor het maken, beheren en publiceren van formulieren en bedrijfsprocessen op bedrijfsniveau.'
exl-id: 3a90b0aa-369a-4350-9904-79ef656b0f9a
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

<!-- # Introduction to [!DNL AEM Forms] as a Cloud Service {#overview}

Adobe Experience Manager Forms as a Cloud Service offers a cloud-native, Platform as a Service (PaaS) solution for businesses to create, manage, publish, and update complex digital forms while integrating submitted data with back-end processes, business rules, and saving data in an external data store. The service is always current, always available, and always learning.

You can use the service to create and rollout  interactive and engaging digital forms. For example, an organization is looking to digitize their customer enrollment journey. They have multiple data sources with existing customer data, they are looking to pre-populate forms, add e-sign their forms, and archive filled forms as PDF files. Besides, the organization has multiple print forms (PDF forms), they are also looking to convert all of their print forms to digital forms.

The organization can use [!DNL AEM Forms] as a Cloud Service to create digital forms, connect forms to existing data sources, integrate forms with [!DNL Adobe Sign] to add e-signatures to forms, and generate Document of Record (DoR) to archive filled forms as PDF files. The organization can also use the service to convert their existing PDF forms to digital forms. 

An organization can sign up for [!DNL AEM Forms] as a Cloud Service and start using all these features without waiting to buy and set up a local infrastructure. The service also frees the organizations from the cycle of upgrades as it is always up to date and always offers the latest feature.  -->

# Belangrijke functies en mogelijkheden {#key-features}

[!DNL AEM Forms] as a Cloud Service biedt verschillende mogelijkheden in de cloud, zoals een eigen architectuur in de cloud, automatisch schalen, geen downtime voor upgrades, een CDN (Content Delivery Network), een ontwikkelomgeving in de cloud en de mogelijkheid om de omgevingen via Cloud Manager zelf te onderhouden. U kunt de service gebruiken om:

* [Adaptieve Forms maken](creating-adaptive-form.md#strong-create-an-adaptive-form-strong) die automatisch worden weergegeven voor het apparaat en de browser van een gebruiker.

   ![Adaptieve Forms](assets/rule-editor-example.gif)

* [Pixelperfecte PDF forms maken](use-forms-designer.md#create-an-adaptive-form) dat lijkt bijna op papier .

* Gebruiken [automatede form conversion](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html) Hiermee converteert u een PDF-formulier naar een adaptief formulier. Het helpt u de digitalisering en de modernisering van gegevens versnellen vangt ervaringen van uw organisatie.

   ![automatede form conversion](assets/pdf-to-adaptive-form-gitx50.gif)

* [Bedrijfsprocessen maken](aem-forms-workflow-step-reference.md#create-form-centric-workflows). U kunt bijvoorbeeld een goedkeurings- en afwijzingsworkflow maken en activeren bij het verzenden van een adaptief formulier.

Naast het bovenstaande [!DNL AEM Forms] as a Cloud Service biedt de volgende functies en mogelijkheden:

* Een gebruiksvriendelijke grafische gebruikersinterface waarmee zakelijke gebruikers eenvoudig formulieren kunnen importeren, beheren, voorvertonen en publiceren
* Een responsieve formuliermap met krachtige zoekfuncties die trefwoorden, tags en metagegevens gebruiken
* Dynamische detectie van het apparaat en de locatie van een gebruiker om het formulier op de juiste wijze te genereren via internet en mobiele kanalen
* [Integratie met Adobe Sign](adobe-sign-integration-adaptive-forms.md) diensten of krabbelen om documenten met vertrouwelijke informatie elektronisch te ondertekenen
* Vermogen [verbind de dienst met diverse types van gegevensbronnen](data-integration.md#create-an-adaptive-form) om gegevens te verzenden en op te halen. De service ondersteunt het verzenden en ophalen van gegevens van RESTful-webservices, SOAP-webservices en OData-services.
* Integratie met AEM Sites. Hiermee kunt u een adaptief formulier insluiten in een AEM Sites-pagina. U kunt ook een adaptief formulier integreren met elke webpagina.
* Mogelijkheid om een Document of Record (DoR) te maken om een record bij te houden van de gegevens die u opgeeft en verzendt in een adaptief formulier, zodat u er later naar kunt verwijzen. Een DoR is een PDF-versie van een formulier. Dit omvat zowel een sjabloon als gegevens. De dienst verstrekt een malplaatje standaardDoR en hulpmiddelen om een douanemalplaatje te ontwikkelen.
* Mogelijkheid om adaptieve Forms te maken voor het produceren van schema-compatibele gegevens. Hierdoor kunt u vastgelegde gegevens zonder enige of minimale wijziging verzenden naar bestaande processen en gegevensbronnen.
* Mogelijkheid om een vooraf ingevulde service te maken en een formulier in te vullen met bestaande klantgegevens op basis van criteria. Hiermee kunt u het invullen van het formulier versnellen en de snelheid waarmee het formulier wordt verlaten, verlagen.


<!-- 

## Enterprise-class forms {#enterprise-class-forms}

You can create enterprise class forms (Adaptive Forms) and deliver beautiful, interactive, responsive, and personalized experiences to your customers. These forms change behavior and appearance based on the underlying device. You can also use themes and templates with Adaptive Forms to mandate a uniform structure and appearance for all the forms of an organization or a department.

![Creating custom patterns for fields in CrxDe](assets/adaptive-form.png)

## Automatic conversion of PDF forms to Adaptive Forms {#automatic-conversion-of-pdf-forms-to-adaptive-forms}

You can use Automated Forms Conversion service to convert a PDF Form to an Adaptive Form. It helps you accelerate digitization and modernization of data capture experiences of your organization.

![Creating custom patterns for fields in CrxDe](assets/pdf-to-adaptive-form-gitx50.gif)

## Data Integration {#data-integration}

You can connect the service to various types of data sources to send and retrieve data. The service supports sending and retrieving data from RESTful web services, SOAP-based web services, and OData enabled services.

![Build dynamism and interactivity to Adaptive Forms](assets/rule-editor-example.gif)

## Integration with [!DNL Adobe Sign] {#integration-with-adobe-sign}

 You can integrate the service with [!DNL Adobe Sign] and add [!DNL Adobe Sign] fields to an Adaptive Form. It allows your users to e-sign an Adaptive Form and use [!DNL Adobe Sign] with AEM Workflows. You can use AEM Workflows to develop a business logic and send forms and documents to recipients for signatures based on the business logic.

![Creating custom patterns for fields in CrxDe](assets/adobe-sign.png)


## Integration with [!DNL AEM Sites] {#integration-with-aem-sites}

You can embed an adaptive form in an AEM Sites or an external webpage. The service provides a component out of the box to integrate an adaptive forms to an AEM Sites page.

![integrate an adaptive forms to an AEM Sites page](assets/integrate.png)

## Business Processes Automation {#bpa}

You can use AEM Workflows to create business processes and automate operations. For example, You can create and trigger an approval and rejection workflow on submission of an Adaptive Form. 

![Create and trigger an approval and rejection workflow](assets/workflow.png)

## Document of Record {#dor}

You can create a Document of Record (DoR) to keep a record of the information that you provide and submit in an Adaptive Form so that you can refer to it later. A DoR is a PDF version of a form. It includes both a template and data. The service provides a default DoR template and tools to develop a custom template.

![Build dynamism and interactivity to Adaptive Forms](assets/designer.png)

## Rule editor {#rule-editor}

Rule editor empowers you to build dynamism and interactivity to Adaptive Forms. These rules define actions to trigger on form objects based on preset conditions, user inputs, and user actions on the form. It helps  streamline the form filling experience while ensuring accuracy and speed.
  
![Creating custom patterns for fields in CrxDe](assets/form-data-model.png)


## WYSIWYG editors {#wysiwyg-editor} 

The service provides several WYSIWYG editors: Adaptive Forms editor, Theme editor, and Template editor. These help you create and edit forms and related assets in WYSIWYG manner. The editors also provide out-of-the-box options to simulate views for popular mobile devices, tablets, and desktop screen configurations.

![Creating custom patterns for fields in CrxDe](assets/emulators.png)

## Schema-compliant data {#schema-complaint-data}

You can create Adaptive Forms to produce schema-compliant data. It helps you submit captured data to existing processes and data sources without any or minimal modifications.

![Build dynamism and interactivity to Adaptive Forms](assets/display-validation-error.gif)

## Prefill a form

You can create a prefill service to fill a form with existing customer data based on a criteria. It helps fasten the form filling process and reduce the abandon rate.

## Submit Actions

A Submit Action allows you to persist and process captured data. The service provides several Submit Actions out-of-the-box. You can use these Submit Actions to send submitted data to a REST endpoint, database, or an AEM Workflow. You can also email submitted data along with attachments and Document of Record(DoR). You can also develop a custom Submit Action to perform an action specific to your business.

* **Emulators:** You can view an Adaptive Form in an in-built emulator. It helps you simulate how an Adaptive Form appears on different devices to an end user. It provides out-of-the-box options to simulate views for popular mobile devices, tablets, and desktop screen configurations. 

In addition to standard [!DNL AEM Forms] features, [!DNL AEM Forms] as a Cloud Service provides several cloud-native capabilities such as a cloud-native architecture, auto-scaling, zero downtime for upgrades, a CDN (Content Delivery Network), cloud-native development environment, and ability to self-Service the environments via Cloud Manager. -->
