---
title: Inleiding tot [!DNL AEM Forms] as a Cloud Service
description: Ontdek AEM Forms en leer hoe u hiermee bedrijfsklare documenten en formuliercontent kunt maken. Leer meer over Platform-as-a-Service (PaaS) en hoe u digitale formulieren en bedrijfsprocessen op ondernemingsniveau beheert en hoe u Forms verbindt met actuele gegevensbronnen.
landing-page-description: Inzicht in hoe u formulieren in AEM as a Cloud Service kunt gebruiken.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: f8e229820bb7aef3923e955c928033ef7d3d9460
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 4%

---

# Inleiding {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] biedt bedrijven een oplossing voor cloud-native Platform als service (PaaS) voor het maken, beheren, publiceren en bijwerken van complexe digitale formulieren en het integreren van verzonden gegevens met back-endprocessen, bedrijfsregels en het opslaan van gegevens in een externe gegevensopslag. De dienst is altijd huidig, altijd beschikbaar, en altijd het leren.

Met deze service kunt u interactieve en aantrekkelijke digitale formulieren maken en implementeren. Bijvoorbeeld, neem een organisatie die zijn reis van de klanteninschrijving probeert te digitaliseren. Zij hebben veelvoudige gegevensbronnen met bestaande klantengegevens. Ze willen formulieren vooraf invullen, hun formulieren elektronisch ondertekenen en ingevulde formulieren archiveren als PDF-bestanden. Bovendien heeft de organisatie meerdere afdrukformulieren (PDF forms), maar ze zijn ook op zoek naar het converteren van al hun afdrukformulieren naar digitale formulieren.

De organisatie kan [!DNL AEM Forms] as a Cloud Service voor het maken van digitale formulieren, het verbinden van formulieren met bestaande gegevensbronnen, het integreren van formulieren met [!DNL Adobe Sign] om e-handtekeningen toe te voegen aan formulieren en om Ingesloten formulieren als PDF-bestanden te archiveren. De organisatie kan de service ook gebruiken om bestaande PDF forms om te zetten in digitale formulieren.

De organisatie kan [!DNL AEM Forms] as a Cloud Service en ontvang al deze functies in de cloud zonder dat u hiervoor een lokale infrastructuur nodig hebt. De dienst bevrijdt organisaties van complexe verbeteringscycli aangezien het altijd met de recentste eigenschappen bijgewerkt is.

## Belangrijkste kenmerken {#key-features}

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


>[!ENDTABS] -->

| Adaptieve Forms | automatede form conversion Service | Communicatie-API&#39;s | Forms Analytics |
|---|---|---|---|
| Met Adaptive Forms kunnen bedrijven interactieve, gegevensgestuurde formulieren maken en beheren voor hun websites en andere digitale kanalen die reageren op mobiele formulieren. | Met automatede form conversion Service kunnen bedrijven formulieren op basis van oudere PDF omzetten in interactieve, digitale formulieren die eenvoudig online kunnen worden beheerd en gedistribueerd. | Communicatie APIs is een reeks RESTful APIs (de Interfaces van de Programmering van de Toepassing) die ondernemingen toelaten om de verwezenlijking, het beheer, en de levering van gepersonaliseerde, gegeven-gedreven mededelingen te automatiseren. | De service biedt OOTB-ondersteuning voor verbinding met Adobe Analytics. Het verbinden van formulieren met Adobe Analytics biedt verschillende voordelen voor bedrijven, zoals een beter begrip van het gebruikersgedrag, een betere gerichtheid op marketing, een verminderde foutstatus en een beter rendement. |

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

[Forms zonder hoofdadapter](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) is een oplossing voor het maken en beheren van webformulieren zonder hoofd binnen het Adobe Experience Manager-platform. Met deze functie kunnen organisaties interactieve formulieren maken, publiceren en beheren die via API&#39;s kunnen worden benaderd en waarmee interactie mogelijk is, in plaats van via een traditionele grafische gebruikersinterface. AEM Headless Adaptive Forms biedt meer flexibiliteit en schaalbaarheid bij de ontwikkeling en implementatie van formulieren en een verbeterde gebruikerservaring doordat het formulierontwerp en de functionaliteit op specifieke behoeften kunnen worden afgestemd. Door gebruik te maken van de mogelijkheden van AEM en technologie zonder kop, biedt deze oplossing een robuust platform voor het maken, beheren en implementeren van webformulieren voor verschillende gebruiksgevallen en -toepassingen.


>[!TAB Kernonderdelen]

De [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) zijn 24 open-source, BEM-compatibele componenten die op de basis van de Adobe Experience Manager WCM Core Components zijn gebouwd. Deze zijn speciaal ontworpen voor het maken van Adaptief Forms. Dit zijn formulieren die worden aangepast aan het apparaat, de browser en de schermgrootte van de gebruiker.

Deze componenten kunnen worden gebruikt om buitengewone ervaringen met het vastleggen en inschrijven van gegevens te maken door een groot aantal opties voor formuliervelden te bieden, zoals tekstvelden, selectievakjes, vervolgkeuzemenu&#39;s en nog veel meer. Ze bevatten ook functies zoals validatie, voorwaardelijke logica en responsief ontwerp, waarmee u formulieren kunt maken die gebruiksvriendelijk en gebruiksvriendelijk zijn.

Bovendien, aangezien deze componenten open-bron zijn, hebben de ontwikkelaars de capaciteit om de componenten gemakkelijk aan te passen en uit te breiden om aan de specifieke behoeften van hun organisatie te passen. Deze componenten zijn gebaseerd op BEM-methoden die ervoor zorgen dat ze schaalbaar en onderhoudsbaar zijn.


>[!TAB Microsoft PowerAutomate-connector &#x200B;]

Microsoft Power Automate Connector voor AEM Forms is een connector waarmee u Adobe Experience Manager (AEM) Forms kunt integreren met Microsoft Power Automate (voorheen bekend als Microsoft Flow). Power Automate is een cloudgebaseerde service waarmee u geautomatiseerde workflows kunt maken tussen verschillende toepassingen en services.

Met de Power Automate Connector voor AEM formulier kunt u workflows maken die automatisch worden geactiveerd op basis van verzending van een adaptief formulier. U kunt bijvoorbeeld een workflow maken die automatisch een e-mailbericht naar een specifieke persoon stuurt wanneer een gebruiker een formulier verzendt of een taak maakt in Microsoft Planner wanneer een gebruiker een formulier invult.

Het gebruik van de Power Automate Connector voor AEM Forms biedt vele voordelen, zoals:

* **Automatisering**: U kunt routinetaken automatiseren en processen stroomlijnen, tijd besparen en fouten verminderen.

* **Integratie**: Met de aansluiting kunt u Adobe Experience Manager Forms integreren met andere toepassingen en services, zodat u met een groter aantal tools kunt werken.

* **Aanpassing**: U kunt workflows maken die zijn afgestemd op uw specifieke behoeften, met de mogelijkheid om aangepaste handelingen, voorwaarden en triggers toe te voegen.

* **Analyse**: Power Automate biedt gedetailleerde analyses en rapportage, waarmee u uw workflows in de loop der tijd kunt controleren en optimaliseren.

Over het algemeen is de Power Automate Connector voor AEM Forms een krachtig hulpmiddel waarmee u uw AEM Forms kunt automatiseren en integreren met andere toepassingen en services, waardoor de efficiëntie en productiviteit worden verbeterd.

>[!TAB Microsoft Storage Connectors: OneDrive en Sharepoint]

AEM Forms Microsoft Storage Connectors voor OneDrive en SharePoint zijn connectors waarmee u Adobe Experience Manager (AEM) Forms kunt integreren met Microsoft OneDrive en SharePoint. Met deze connectors kunt u AEM Forms-gegevens en -documenten opslaan en beheren in Microsoft cloud-gebaseerde opslagoplossingen.

Met deze connectors kunt u AEM Forms-gegevens en -documenten opslaan en beheren in Microsoft OneDrive. Met deze connector kunt u gegevensbestanden en bijlagen rechtstreeks vanuit AEM Forms uploaden naar OneDrive en SharePoint.

Het gebruik van AEM Forms Microsoft Storage Connectors voor OneDrive en SharePoint biedt verschillende voordelen:

* **Integratie**: Met deze connectors kunt u AEM Forms integreren met Microsoft-oplossingen voor cloudopslag, zodat u de kracht van deze platforms kunt benutten.

* **Samenwerking**: OneDrive en SharePoint zijn samenwerkingsplatforms waarmee teamleden kunnen samenwerken aan bestanden en documenten. Door AEM Forms met deze platforms te integreren, kunt u de samenwerking en het teamwerk verbeteren.

* **Beveiliging**: OneDrive en SharePoint bieden robuuste beveiligingsfuncties en zorgen ervoor dat uw gegevens en documenten veilig worden opgeslagen en geopend.

AEM Forms Microsoft Storage Connectors voor OneDrive en SharePoint zijn over het algemeen krachtige tools waarmee u AEM Forms-gegevens en -documenten kunt opslaan en beheren in Microsoft-oplossingen voor cloudopslag, waardoor de samenwerking en beveiliging worden verbeterd.

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