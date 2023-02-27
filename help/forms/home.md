---
title: Inleiding tot [!DNL AEM Forms] as a Cloud Service
description: Ontdek AEM Forms en leer hoe u hiermee bedrijfsklare documenten en formuliercontent kunt maken. Leer meer over Platform-as-a-Service (PaaS) en hoe u digitale formulieren en bedrijfsprocessen op ondernemingsniveau beheert en hoe u Forms verbindt met actuele gegevensbronnen.
landing-page-description: Inzicht in hoe u formulieren in AEM as a Cloud Service kunt gebruiken.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: 37274b28ab2343fd3cdfb4747c9dee701c699b46
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 4%

---

# Inleiding {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] biedt bedrijven een oplossing voor cloud-native Platform als service (PaaS) voor het maken, beheren, publiceren en bijwerken van complexe digitale formulieren en het integreren van verzonden gegevens met back-endprocessen, bedrijfsregels en het opslaan van gegevens in een externe gegevensopslag. De dienst is altijd huidig, altijd beschikbaar, en altijd het leren.

Met deze service kunt u interactieve en aantrekkelijke digitale formulieren maken en implementeren. Bijvoorbeeld, neem een organisatie die zijn reis van de klanteninschrijving probeert te digitaliseren. Zij hebben veelvoudige gegevensbronnen met bestaande klantengegevens. Ze willen formulieren vooraf invullen, hun formulieren elektronisch ondertekenen en ingevulde formulieren archiveren als PDF-bestanden. Bovendien heeft de organisatie meerdere afdrukformulieren (PDF forms), maar ze zijn ook op zoek naar het converteren van al hun afdrukformulieren naar digitale formulieren.



De organisatie kan [!DNL AEM Forms] as a Cloud Service voor het maken van digitale formulieren, het verbinden van formulieren met bestaande gegevensbronnen, het integreren van formulieren met [!DNL Adobe Sign] om e-handtekeningen toe te voegen aan formulieren en om Ingesloten formulieren als PDF-bestanden te archiveren. De organisatie kan de service ook gebruiken om bestaande PDF forms om te zetten in digitale formulieren.

De organisatie kan [!DNL AEM Forms] as a Cloud Service en ontvang al deze functies in de cloud zonder dat u hiervoor een lokale infrastructuur nodig hebt. De dienst bevrijdt organisaties van complexe verbeteringscycli aangezien het altijd met de recentste eigenschappen bijgewerkt is.

## Belangrijkste kenmerken {#key-features}

|  |  |
|---|---|
| Adaptieve Forms | Maak en beheer interactieve, dynamische, responsieve, mobiele en gegevensgestuurde formulieren voor uw websites, apps en andere digitale en afdrukkanalen. Lees het volgende om aan de slag te gaan, inzicht te krijgen en inschrijvingservaringen te implementeren: <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html"> Een adaptief formulier maken </a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/themes.html">Een adaptief formulier opmaken</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#enabling-server-side-validation-br"> Gegevens verzenden naar een gegevensopslagruimte of een workflow</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html"> Een record van het formulier maken voor langetermijnarchivering</a></li></ul> |
| Communicatie-API&#39;s | Automatiseer creatie, beheer, en levering van gepersonaliseerde, gegeven-gedreven mededelingen met RESTful APIs op bestelling of op geplande intervallen zoals maandelijkse verklaringen en rekeningsberichten. Lees het volgende om aan de slag te gaan, te begrijpen en te maken: <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#document-generation"> Persoonlijke communicatie genereren </a> </li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#document-manipulation"> PDF-documenten samenstellen of demonteren </a> </li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#convert-to-and-validate-pdf%2Fa-compliant-documents">Met PDF/A compatibele documenten maken </a></li></ul> |
| automatede form conversion Service | Converteer verouderde, op PDF gebaseerde formulieren naar Adaptieve Forms die eenvoudig online kunnen worden beheerd en gedistribueerd. Lees het volgende om aan de slag te gaan: <ul><li><a href="https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html">Automatede form conversion-service configureren</a></li><li><a href="https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html">PDF-formulieren converteren naar adaptieve formulieren</a></li></ul> |
| Forms Workflows | Automatiseer bedrijfsprocessen met formulieren en documentservices. Wijs, route, overzicht, en keur vormen en document toe aangezien deze zich door verschillende stadia van een bedrijfsproces bewegen. Lees het volgende om aan de slag te gaan:  <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-reviews-forms.html">Een formulier of document ter controle verzenden</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#assign-task-step">Maak een werkstroom voor goedkeuringstoetsing</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#generate-document-of-record-step">Document van record toevoegen </a> of <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#sign-document-step"> elektronisch ondertekenen </a> stappen naar een zakelijke werkstroom</a></li></ul> |
| E-handtekeningen | Integreer met Adobe Sign en DocuSign om eenvoudig Forms en documenten naar gebruikers te verzenden voor e-handtekeningen. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html">Een adaptief formulier elektronisch ondertekenen met Adobe Sign </a></li><li></a> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-docusign-adaptive-forms.html">Een adaptief formulier elektronisch ondertekenen met DocuSign </a></li></ul> |
| Forms Analytics | Gebruik Adobe Analytics om waardevolle inzichten in gebruikersgedrag en -voorkeuren te verkrijgen. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-aem-forms-with-adobe-analytics.html?lang=en">Een adaptief formulier verbinden met Adobe Analytics</a></li></ul> |
| Gegevensbronnen | Sluit uw formulieren en documenten eenvoudig aan op externe gegevensbronnen om gegevens op te halen en te verzenden. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources.html?lang=en">Verbind met RDBMS of Rest eindpunt</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html?lang=en">Verbinding maken met de Microsoft Dynamics 365- of Salesforce-cloudservice</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=en">Verbinding maken met Microsoft Azure Blob Storage</a></li></ul> |


<!-- 
>[!BEGINTABS]

>[!TAB Adaptive Forms]

Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>

>[!TAB Automated Forms Conversion Service]

Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>

>[!TAB Communications API (Document Services)]

Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.

>[!TAB Advanced Analytics]

The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>


>[!ENDTABS] 

| Adaptive Forms | Communications APIs  | Automated Forms Conversion Service | Forms Workflows | E-Sign | Forms Analytics | Data Model | 
|---|---|---|---|---|---| ---|
|Create and manage interactive, dynamic, responsive, mobile-friendly, and data-driven forms for your websites, apps, and other digital and Print channels. | Automate creation, management, and delivery of personalized, data-driven communications with RESTful APIs (Application Programming Interfaces) on-demand or at scheduled intervals. | Convert legacy PDF-based forms into Adaptive Forms that can be easily managed and distributed online. | Automate business processes involving forms and document services. Assign, route, review, and approve forms and document as these move through different stages of a business process.| Integrate with Adobe Sign and DocuSign to easliy send send Forms and documents to users for e-signatures. | Use Adobe Analytics to gain valuable insights into user behavior and preferences. | Easily connect your forms and documents with external data sources to retieve and send data. |
|<ul><li>Create an Adaptive Form</li><li>Style an Adaptive Form</li><li>Submit data to a data store or a workflow</li></ul>|<ul><li>Generate personalized communciations</li><li>Assemble or disassemble PDF documents</li><li>Create PDF/A-compliant documents</li></ul>|<ul><li>Configure Automated Forms Conversion Service</li><li>Convert PDF forms to adaptive forms</li></ul>|<ul><li>Send a form or document for review</li><li>Create an approval rejection Workflow</li><li>Add Document of Record or e-signatures to a business workflow</li></ul>|<ul><li>E-sign an Adaptive Form with Adobe Sign</li><li>E-sign an Adaptive Form with DocuSign</li></ul>|<ul><li>Connect an Adaptive Form with Adobe Analytics</li></ul>|<ul><li>Connect to a RDBMS or Rest endpoint</li><li>Connect to Microsoft Dynamics 365 or Salesforce cloud service</li><li>Connect to Microsoft&reg; Azure Blob Storage</li></ul>|

<!--
| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

-->

## Nieuwste innovaties {#latest-innovations}

>[!BEGINTABS]

>[!TAB Forms-&#x200B; zonder hoofdadapter]

|| |—|—| |![](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/assets/how-headless-adaprive-forms-work.png?)| Maken en beheren [Forms zonder hoofdadapter](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) op het Adobe Experience Manager-platform. Laat uw ontwikkelaars toe om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditionele grafische gebruikersinterface kunnen worden betreden en met. communiceren. <br/> <br/> Deze formulieren zijn ontworpen om te worden ingediend zonder dat er een traditionele interface voor HTML-formulieren nodig is. Met andere woorden, hiermee kunt u formuliergegevens programmatisch verzenden via een API of code voor een backend formulier zonder dat er aan de voorkant zichtbare formulierelementen nodig zijn. <br/> <br/> Formulieren zonder kop zijn handig in verschillende scenario&#39;s, zoals bij het ontwikkelen van toepassingen van één pagina, progressieve webapps of mobiele toepassingen, waarbij een traditionele HTML-formulierinterface niet altijd nodig of praktisch is. Door ontwikkelaars toe te staan formuliergegevens rechtstreeks via API&#39;s of backendcode te verzenden, helpen eindeloze formulieren workflows te stroomlijnen en de algehele prestaties van webtoepassingen te verbeteren.|




>[!TAB Kernonderdelen]

|| |—|—| |![](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/assets/sample-core-components-based-adaptive-form.png?) | De [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) zijn 24 open-source, BEM-compatibele componenten die op de basis van de Adobe Experience Manager WCM Core Components zijn gebouwd. Deze zijn speciaal ontworpen voor het maken van Adaptief Forms. Dit zijn formulieren die worden aangepast aan het apparaat, de browser en de schermgrootte van de gebruiker. <br/> <br/> Deze componenten kunnen worden gebruikt om buitengewone ervaringen met het vastleggen en inschrijven van gegevens te maken door een groot aantal opties voor formuliervelden te bieden, zoals tekstvelden, selectievakjes, vervolgkeuzemenu&#39;s en nog veel meer. Ze bevatten ook functies zoals validatie, voorwaardelijke logica en responsief ontwerp, waarmee u formulieren kunt maken die gebruiksvriendelijk en gebruiksvriendelijk zijn. <br/> <br/>  Bovendien, aangezien deze componenten open-bron zijn, hebben de ontwikkelaars de capaciteit om de componenten gemakkelijk aan te passen en uit te breiden om aan de specifieke behoeften van hun organisatie te passen. Deze componenten zijn gebaseerd op BEM-methoden die ervoor zorgen dat ze schaalbaar en onderhoudsbaar zijn.|



>[!TAB Microsoft PowerAutomate-connector &#x200B;]

|| |—|—| |![](https://powerusers.microsoft.com/t5/image/serverpage/image-id/182924i17C4BEA1C045D731/image-size/large/is-moderation-mode/true?v=1.0&amp;px=999)| AEM Forms Power Automate Connector biedt u de mogelijkheid om Adobe Experience Manager (AEM) Forms te integreren met Microsoft Power Automate (voorheen bekend als Microsoft Flow). Power Automate is een cloudgebaseerde service waarmee u geautomatiseerde workflows kunt maken tussen verschillende toepassingen en services.  <br/> <br/> Met AEM Form Power Automate Connector kunt u workflows maken die automatisch worden geactiveerd op basis van verzending van een adaptief formulier. U kunt bijvoorbeeld een workflow maken die automatisch een e-mailbericht naar een specifieke persoon stuurt wanneer een gebruiker een formulier verzendt of een taak maakt in Microsoft Planner wanneer een gebruiker een formulier invult.  <br/> <br/> De AEM Forms Power Automate Connector is een krachtig hulpmiddel waarmee u uw Adaptive Forms kunt automatiseren en integreren met andere toepassingen en services die aansluiten op Microsoft Power Automate, zodat u met een groter aantal tools kunt werken. U kunt workflows maken die zijn afgestemd op uw specifieke behoeften, met de mogelijkheid om aangepaste handelingen, voorwaarden en triggers toe te voegen. Bovendien biedt Power Automate gedetailleerde analyses en rapportage, waarmee u uw workflows in de loop der tijd kunt controleren en optimaliseren.|


>[!TAB Microsoft Storage Connectors: OneDrive en Sharepoint]

|| |—|—| |![](/help/forms/assets/onedrive-and-sharepoint.jpg)|AEM Forms Microsoft Storage Connectors voor OneDrive en SharePoint zijn connectors waarmee u Adobe Experience Manager (AEM) Forms kunt integreren met Microsoft OneDrive en SharePoint. Met deze connector kunt u gegevensbestanden en bijlagen rechtstreeks vanaf Adaptive Forms uploaden naar OneDrive en SharePoint. |


>[!ENDTABS]

<!--

| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

Adaptive Forms enable organizations to quickly design and deploy responsive, mobile-friendly forms without the need for extensive coding or development. With Adaptive Forms, businesses can create complex, multi-step forms with conditional logic, validations, and integrations with back-end systems such as CRMs and databases.

Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development.

In addition, AEM Adaptive Forms offer several other features, including:

Advanced workflows for routing, approval, and submission of form data
Real-time validation and error checking to ensure data accuracy
Integration with third-party data sources and APIs for pre-filling form fields or validating data
Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics
Overall, AEM Adaptive Forms provide businesses with a powerful tool for creating and managing complex, interactive forms that can be easily integrated into their digital experiences. |




| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2611;  | &#x2612; |
| Auto-scaling based on load | &#x2611;  | &#x2612; |
| Zero downtime for upgrades | &#x2611;  | &#x2612; |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2611;  | &#x2612; | 
| Topologies optimized for maximum resilience and efficiency| &#x2611;  | &#x2612; | 
| Cloud-native development environment | &#x2611;  | &#x2612; | 
| Self-Service via Cloud Manager | &#x2611;  | &#x2612; | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2611;  | &#x2612; | 
| Adaptive Forms | &#x2611; | &#x2611; | 
| Data Integration with multiple data sources| &#x2611; | &#x2611; | 
| Communications APIs (Document Services) | &#x2611;* | &#x2611; | 
| Automated Forms Conversion Service | &#x2611; | &#x2611; | 
| Integration with [!DNL Micosoft Power Automate] | &#x2611; | &#x2612; | 
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; | 
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Launch] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Analytics] | &#x2611; | &#x2611; | 
| Easy connectivity with Microsoft Dynamics and Salesforce | &#x2611; | &#x2612; |
| Custom submit action for with [!DNL DocuSign] | &#x2611; | &#x2612; | 
| Microsoft Azure data store connector | &#x2611; | &#x2612; |
| Hardened Rule editor | &#x2611; | &#x2612; | 
| Forms Portal | &#x2611; | &#x2611; | 
| AEM Workflows | &#x2611; | &#x2611; | 
| Document of Record | &#x2611; | &#x2611; | 
| Adaptive Forms Wizard | &#x2611; | &#x2612; | 
| Custom XCI for Document of Record| &#x2611; | &#x2612; |
| Invisible Captcha | &#x2611; | &#x2611; |
| Reusable Form Data Model configurations | &#x2611; | &#x2611; |
| Acroform-based Document of Record | &#x2611; | &#x2611; | 
| Government ID based identity authentication for Adobe Sign enabled Adaptive Forms | &#x2611; | &#x2611; | 
| Document Security | &#x2612; | &#x2611; |


* [Notable changes in comparison to AEM 6.5 Forms](notable-changes.md)
* [Frequently asked questions](faq.md)

-->