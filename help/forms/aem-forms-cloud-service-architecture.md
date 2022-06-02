---
title: Experience Manager [!DNL AEM Forms] as a Cloud Service architectuur
description: Begrijp de architectuur van [!DNL AEM Forms] as a Cloud Service om over de scalability, veerkracht, en prestatiesaspecten van het platform te leren.
source-git-commit: cb7b417b9b4898b0656e79d6f699e8d5cd611e76
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---


# [!DNL AEM] Forms as a Cloud Service architectuur {#architecture}

[!DNL Adobe Experience Manager Forms] as a Cloud Service is een cloud-native oplossing voor bedrijven om complexe digitale formulieren en communicatie te maken, beheren, publiceren en bijwerken terwijl ingediende gegevens worden geïntegreerd met back-end processen, bedrijfsregels en gegevens worden opgeslagen in een externe gegevensopslag. Het breidt zich uit [!DNL Adobe Experience Manager as a Cloud Service]. Ga voor meer informatie over schalen, implementatie, omgevingen en andere infrastructuren naar [Een inleiding tot de architectuur van [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html).

AEM Forms as a Cloud Service biedt ondersteuning voor twee belangrijke gebruiksgevallen: Digitale inschrijving en klantcommunicatie. In de volgende afbeeldingen ziet u de architectuur voor beide gebruiksgevallen.

## Architectuur- en stroomdiagrammen

**Forms Digital Enrollment**

![Forms-digitaal inschrijven](assets/forms-cloud-service-architecture-forms-digital-enrollment.svg)

**Forms Communications**

![Forms-Communication](assets/forms-cloud-service-architecture-forms-communications.svg)

## Onderdelen

Forms as a Cloud Service bestaat uit meerdere componenten:

### CDN (Content Delivery Network)

Elk as a Cloud Service AEM Forms-programma heeft toegang tot [ingebouwde CDN-service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html). Het is opgenomen in de licentie van Forms als Cloud Services.

### Auteur

Een auteur is een as a Cloud Service AEM Forms-instantie die wordt uitgevoerd in de standaardmodus Auteur. Deze is bedoeld voor interne gebruikers, formulierontwerpers en ontwikkelaars. Een auteursomgeving laat de volgende functies toe:

* Formulieren ontwerpen en beheren.
* Verbinding maken met de service Automatede form conversion om een PDF- of XDP-formulier om te zetten in een adaptief formulier.
* Forms-gecentreerde workflows maken en uitvoeren.
* Elementen van adaptieve formulieren beheren.
* Communicatieelementen beheren.
* Synchrone RESTful APIs (Echte - tijd APIs) en Partij APIs om, merkgeoriënteerde en gepersonaliseerde mededelingen tot stand te brengen samen te stellen en te leveren.
* Synchrone API&#39;s om PDF-documenten te combineren, opnieuw te rangschikken en te valideren.

### Publicatie

Een instantie Publish is een as a Cloud Service AEM Forms die in de standaard Publish loopwijze loopt. Publicatie-instanties zijn bedoeld voor eindgebruikers van formuliertoepassingen, bijvoorbeeld gebruikers die een openbare website openen en formulieren verzenden. Het maakt de volgende functies mogelijk:

* Formulieren weergeven en verzenden voor eindgebruikers.
* Vervoer van onbewerkte formuliergegevens voor verdere verwerking en opslag in het definitieve registratiesysteem.
* Verbinding maken met door de klant beheerde opslag om gegevens op te slaan.
* Verbinding maken met Adobe Sign om een adaptief formulier voor verzending elektronisch te ondertekenen.
* Synchroniseer API&#39;s om merkgeoriënteerde en gepersonaliseerde communicatie te maken, samen te stellen en te leveren.
* Synchroniseer API&#39;s om PDF-documenten te combineren, opnieuw te rangschikken en te valideren.

De omgekeerde Replicatie is niet beschikbaar op AEM as a Cloud Service om inhoud/gegevens van de Publish Dienst naar de Dienst van de Auteur te verzenden. U kunt echter wel een adaptieve Forms configureren die wordt uitgevoerd bij Publiceren om gegevens naar een workflow op een auteur te verzenden (Workflows kunnen alleen worden uitgevoerd op de auteur). Dit is handig in geval van goedkeuring.

#### Dispatcher

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) is het in cache plaatsen van Adobe Experience Manager en/of taakverdeling die kan worden gebruikt met een webserver op bedrijfsniveau.

### Adobe Services

**automatede form conversion Service**

[automatede form conversion](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html) zet uw PDF- en XFA-formulieren automatisch om in apparaatvriendelijke, responsieve en op HTML gebaseerde adaptieve formulieren.

**Adobe Sign**

Adobe Sign is een op de cloud gebaseerde e-handtekeningservice waarmee de gebruiker handtekeningprocessen kan verzenden, ondertekenen, volgen en beheren met een browser of mobiel apparaat. U kunt Adobe Sign integreren met een adaptief formulier om ondertekeningsworkflows te automatiseren, processen met één en meerdere handtekeningen te vereenvoudigen en adaptieve formulieren elektronisch te ondertekenen.

<!-- **PDF Service API**
Adobe’s PDF Services API lets create, combine, export, and extract data from PDFs through powerful and flexible cloud-based APIs. -->

### Door de klant beheerde opslag

Forms as a Cloud Service biedt opties voor het opslaan van inhoud in een extern opslagsysteem, zoals een blob Store, database of een opslagservice. U kunt ook werkstroomgegevens (AEM gegevens van de Variabelen van het Werkschema) opslaan die de gevoelige elementen van Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. Adobe raadt aan gevoelige gegevens alleen op door klanten beheerde opslagruimten op te slaan.

U kunt de **Unified Storage Connector** om verbinding te maken met Blob Storage en **Formuliergegevensmodel** verbinding maken met databases of back-endservices (RESTful, SOAP, Azure Blob Storage, enzovoort).

### Document Services

Documentdiensten zijn:

* **Uitvoerservice (communicatie - API&#39;s voor het genereren van documenten)** helpt bij het maken van merkgebonden, gepersonaliseerde en gestandaardiseerde documenten, zoals zakelijke correspondentie, instructies, aanvraagverwerkingsbrieven, aankondigingen van voordelen, maandelijkse facturen of welkomstkits.

* **Assembler Service (Communicatie - Document Manipulation APIs)** Hiermee kunt u PDF-documenten combineren, opnieuw rangschikken en valideren.

* **Document of Record (DoR)-service** Help Document of Record (DoR) genereren. De service wordt in een eigen pod uitgevoerd, waarbij de instanties Auteur en Publiceren van Forms as a Cloud Service worden gescheiden. Hierdoor worden de prestaties verbeterd en worden de pods onafhankelijk van de laadbewerking geschaald.

### Cloud Manager

Cloud Manager is een essentieel onderdeel van [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html). Het is het enig-ingangspunt voor de verrichtingen en ontwikkelaarspersoonlijkheid van onze klanten. Het is de plaats van waar de AEM programma&#39;s en milieu&#39;s kunnen worden beheerd. Cloud Manager is geëvolueerd als een zelfbedieningsportal waar de belangrijkste componenten van de AEM as a Cloud Service kunnen worden gecreeerd en worden gevormd:

* Programma&#39;s maken en beheren
* De AEM omgevingen binnen de programma&#39;s maken en beheren
* Het creëren van en het leiden van de pijpleidingen voor het opstellen van de klantencode en configuratie aan een bepaalde milieu
* Informatie over belangrijke levenscyclusgebeurtenissen voor deze componenten (bijvoorbeeld productupdates) Voor meer informatie over Cloud Manager raadpleegt u [Adobe Cloud Manager begrijpen](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) en [Inleiding tot Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

### Developer Console

Een ontwikkelaarsconsole biedt verschillende details over elke Forms die wordt uitgevoerd als een Cloud Service-omgeving. Deze details zijn nuttig in het zuiveren van het milieu. Zie voor meer informatie [Foutopsporing AEM as a Cloud Service met de ontwikkelaarsconsole](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html).

<!--

+++CDN (Content Delivery Network):

Every AEM Forms as a Cloud Service program has access to Fastly CDN service. It is included in the licence of Forms as a Cloud Services.

+++

+++Adaptive Forms
Adaptive Forms enable customers to author web-friendly reflowable web forms and fragments that are used by the customers for their data capture needs. This feature enables customers to manage their complex data capture needs easily, by leveraging multiple integrations with Adobe Sign, Document Services, Form Data Model, Automated Forms Conversion service, and more.

+++

+++Automated Forms Conversion Service (AFCS)
Automated Forms Conversion service helps accelerate digitization and modernization of data capture experience through automated conversion of PDF forms to adaptive forms. The service, powered by Adobe Sensei, automatically converts your PDF forms to device-friendly, responsive, and HTML5-based adaptive forms. While leveraging the existing investments in PDF Forms and XFA, the service also applies appropriate validations, styling, and layout to adaptive form fields during conversion.

+++

+++Form Data Model
The Form Data Model (FDM) feature is the standard way of creating data integrations with external/internal data sources and using them across the different Forms as a Cloud Service features. FDM provides a rich editor for customers to integrate, define, and manage relationships between the different entities and data sources and perform operations on them. Form data is stored in a data store hosted on the customer premises. Organizations can also use blob store hosted by the cloud provider and Adobe Experince Platform to store data.

+++

+++Forms Workflows
Forms-centric workflows is an extension to the default AEM Workflow and provides our customers with additional workflow capabilities like Form Data review, task assignment, and document services invocation.

+++

+++Communications
Forms as a Cloud Service offering consists of multiple services tailored specifically for document processing.

+++

+++Document of Record
A Document of Record is a PDF version of a form. It provides an ability to keep a record of the information  that you provide and submit in an Adaptive Form in PDF fromat. The service provides a default DoR template and tools to develop a custom template.

+++

## Terminologies

<!-- ## Cloud Manager{#cloud-manager}

Cloud Manager is an essential component to [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en). Each new tenant of the [!DNL AEM Forms] as a Cloud Service is first provisioned for Cloud Manager access. Cloud Manager is the single-entry point for the operations and developer persona of our customers. It is the place from where the AEM programs and environments can be managed. Cloud Manager has evolved as a self-service portal where the main components of the AEM as a Cloud Service can be created and configured:

* Creating and managing programs
* Creating and managing the AEM environments within the programs
* Creating and managing the pipelines for deploying the customer code and configuration to a particular environment
* Getting notified of important lifecycle events for these components (e.g. product updates)
For more information about Cloud Manager, see [Understand Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) and [Introduction to Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

## Users and Authentication {#users-and-authentication}

AEM as a Cloud Service includes Admin Console support for AEM instances and Adobe Identity Management System (IMS) based authentication. The Admin Console allows administrators to centrally manage all Experience Cloud users. Users and Groups can be assigned to product profiles associated with AEM as a Cloud Service instances, allowing them to log in to that instance. For more information about users, authentication, and, and accessing an instance of AEM as a Cloud Service, see [IMS Support for [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#introduction).

Various personas are involved in a typical [!DNL AEM Forms] project. After you log in to your [!DNL AEM Forms] as a Cloud Service instance, you can [add users in admin console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html) for personas applicable to your organization or project and [assign users to built-in groups](forms-groups-privileges-tasks.md) to provide them required privileges.

To learn various in-built [!DNL AEM Forms] specific user groups and privileges available on [!DNL AEM Forms] as a Cloud Services instance, see [Configure, user, roles and groups](forms-groups-privileges-tasks.md). 

## Developer Experience {#developer-experience}

The new architecture supporting AEM as a Cloud Service brings some key changes to the overall developer experience. One of the major goals for the changes to developer experience is to allow migration to AEM as a Cloud Service as quickly as possible, with little modifications to existing custom code.

## Cloud development {#cloud-development}

Here are the guidelines to run your existing code smoothly on AEM as a Cloud Service environment:

* Store your code and configurations to the Git repository of the associated Cloud Manager program. It makes managing and integrating code with CI/CD a breeze.  
* Make application code and configuration compatible with the baseline [!DNL AEM Forms] images. Using the latest APIs helps to build faster and secure applications.
* Use the Cloud Manager pipeline associated with the Cloud Manager environment to build and deploy applications. It helps you bring the latest features and bug fixed for [!DNL AEM Forms] as a Cloud Service to your environment.
* Try that your custom applications pass all the code quality, security, and performance gates enforced in the pipeline. It helps build secure and better performing applications which leads to better customer experience. You can always use Cloud Manager UI to skip some checks.
This process is commonly referred to as cloud-first development. [!DNL AEM Forms] as a Cloud Service also provides an SDK to support rapid development before the pending code and configuration changes are attempted in the cloud.
Some interfaces that were previously part of the AEM QuickStart are no longer available to the users of the AEM as a Cloud Service environment. For instance, the Web Console where OSGI bundles and their associated configuration are managed. The CRXDE Lite content repository browser becomes only accessible on non-production environment types. A subset of the Web Console functionalities that developers require, especially when it comes to diagnostics and status purposes, is made available via a new developer console.
Also, one of the most common requirements for developers is quick access to the log files of the various environments. With [!DNL AEM Cloud Service], the log files of the different nodes in the Author, Publish are made available via the Cloud Manager, either in the form of files that can be downloaded or via APIs for tailing the logs. Due to the clear separation of code and content, developers can leverage a particular process for updating content as part of a deployment. The typical use cases for mutable content are:
* Standard “default” content that is part of the customer project (e.g. folders, templates, workflows...)
* Search index definitions
* ACLs and permissions
* Service users and user groups
Set up your development environment, [Configure your CI/CD Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html), and learn to [deploy your code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) on the environment. -->

### Adaptief ontwerpen van formulieren {#local-development}

Wanneer u opstelling en vormt [!DNL AEM Forms] as a Cloud Service omgeving, stelt u ontwikkelings-, staging- en productieomgevingen in. Bovendien moet u een lokale ontwikkelomgeving instellen en configureren voor snelle iteraties en ontwikkeling. U kunt SDK downloaden en instellen AEM [!DNL AEM Forms] add-on functiearchief om een lokale [!DNL Forms] as a Cloud Service ontwikkelomgeving.  Zie voor gedetailleerde instructies [Een lokale ontwikkelomgeving instellen](setup-local-development-environment.md).

## Foutopsporing {#debugging}

AEM as a Cloud Service runnen op zelfbediening, schaalbare cloudinfrastructuur. Het vereist AEM ontwikkelaars om diverse facetten van AEM as a Cloud Service te begrijpen en te zuiveren, van bouw, en op te stellen aan het verkrijgen van details van het runnen van AEM toepassingen. Zie voor meer informatie [Foutopsporing AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html).
