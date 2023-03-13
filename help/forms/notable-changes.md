---
title: Wat is er veranderd tussen AEM 6.5 Forms en AEM Cloud Services
description: Bent u een Experience Manager Forms-gebruiker en wilt u een upgrade uitvoeren naar Adobe Experience Manager Forms as a Cloud Service? Leer de opvallendste wijzigingen voordat u gaat upgraden of migreren naar Cloud Service.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: fa8629fefe3ad29f70213b15bb31623a2f7d5420
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 0%

---

# Opvallende wijzigingen voor bestaande Adobe Experience Manager 6.5 Forms-gebruikers  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service brengt een aantal opmerkelijke veranderingen in bestaande eigenschappen in vergelijking met Adobe Experience Manager Forms On-Premise en [!DNL Adobe-Managed Service] omgevingen. De belangrijkste verschillen worden hieronder vermeld:

| Functie/mogelijkheid | [!DNL AEM Forms] as a Cloud Service | AEM 6,5 Forms |
|---|---|---|
| Systeemeigen architectuur voor cloud | ✅ | ⛌ |
| Automatisch schalen op basis van laden | ✅ | ⛌ |
| Geen downtime voor upgrades | ✅ | ⛌ |
| Uitrolfrequentie van functies | Agile* | Driemaandelijks |
| CDN (content delivery network) opgenomen | ✅ | ⛌ |
| Topologieën geoptimaliseerd voor maximale veerkracht en efficiëntie | ✅ | ⛌ |
| Eigen ontwikkelomgeving voor cloud | ✅ | ⛌ |
| Self-Service via Cloud Manager | ✅ | ⛌ |
| Geautomatiseerde upgrades met continue integratie en continue levering (CI/CD) | ✅ | ⛌ |
| Integratie met [!DNL Micosoft Power Automate] | ✅ | ⛌ |
| Integratie met [!DNL DocuSign] | ✅ | ⛌ |
| Eenvoudige connectiviteit met Microsoft Dynamics en Salesforce | ✅ | ⛌ |
| Eenvoudige connectiviteit met Microsoft Azure-gegevensopslag | ✅ | ⛌ |
| Hardened Rule Editor | ✅ | ⛌ |
| Wizard Formulier maken | ✅ | ⛌ |
| Aangepaste XCI-ondersteuning voor document of record | ✅ | ⛌ |
| Adaptieve Forms <sup>1</sup> | ✅ | ✅ |
| Communicatie-API&#39;s (Document Services) <sup>2,3</sup> | ✅ | ✅ |
| automatede form conversion Service <sup>4</sup> | ✅ | ✅ |
| Forms Portal <sup>5</sup> | ✅ | ✅ |
| Forms-gegevensmodel <sup>6</sup> | ✅ | ✅ |
| HTML5 Forms <sup>7</sup> | ⛌ | ✅ |
| Documentbeveiliging | ⛌ | ✅ |

Houd rekening met de volgende uitzonderlijke gevallen voordat u verdergaat met de dienst:

+++ 1. Adaptieve Forms

* **Adaptieve Forms op basis van XSD:** De service biedt geen ondersteuning voor HTML5 Forms (Mobile Forms). Als u uw op XDP gebaseerde formulieren weergeeft als HTML5 Forms, kunt u de functie blijven gebruiken op AEM 6.5 Forms. U kunt XDP-malplaatje gebruiken om een malplaatje voor Document voor Verslag te ontwerpen. De service biedt geen ondersteuning voor adaptieve Forms op basis van XFA
* **Aangepaste formuliersjablonen importeren:** Gebruik de build-pijplijn en de bijbehorende Git-opslagplaats van uw programma om bestaande adaptieve formuliersjablonen te importeren.
* **Regeleditor:** AEM Forms as a Cloud Service biedt een harde [Regeleditor](rule-editor.md#visual-rule-editor). De code-editor is niet beschikbaar in Forms as a Cloud Service. Met het migratiehulpprogramma kunt u formulieren migreren die aangepaste regels hebben (die in de code-editor zijn gemaakt). Het hulpprogramma converteert dergelijke regels naar aangepaste functies die worden ondersteund op as a Cloud Service Forms. U kunt de herbruikbare functies met de redacteur van de Regel gebruiken om resultaten te blijven verkrijgen die met regelmanuscripten worden verkregen `onSubmitError` of `onSubmitSuccess` functies zijn nu beschikbaar als handelingen in de Editor voor regels.
* **Concepten en opmerkingen:** De service behoudt geen metagegevens voor concepten en verzonden Adaptive Forms.
* **Prefill-service:** Standaard voegt de Prefill-service gegevens samen met een Adaptief formulier op de client in plaats van gegevens op de server samen te voegen in AEM 6.5 Forms. De functie helpt de tijd te verbeteren die nodig is om een adaptief formulier vooraf in te vullen. U kunt altijd configureren om de samenvoegactie op de Adobe Experience Manager Forms-server uit te voeren.
* **Handelingen verzenden:** De **E-mailen als PDF** actie is niet beschikbaar. De **E-mail** Verzenden bevat opties voor het verzenden van bijlagen en het toevoegen van een e-mail aan het Document of Record (DoR).
* **Componenten**: De service biedt geen ondersteuning voor ondertekeningservaring in formulieren en bevat geen componenten Overzicht en Verifiëren voor Adaptive Forms.



+++


+++ 2. Documentservices: Document Manipulation APIs (Assembler Service)


De dienst steunt geen verrichtingen afhankelijk van andere diensten of toepassingen:

* De conversie van documenten in een andere indeling dan PDF naar een PDF-indeling wordt niet ondersteund. Microsoft Word naar PDF, Microsoft Excel naar PDF en HTML naar PDF worden bijvoorbeeld niet ondersteund. Als de documenten een andere indeling dan PDF hebben. Converteer dergelijke documenten naar de indeling PDF voordat u de documenten gebruikt met API&#39;s voor documentanimatie voor communicatie. Als uw documenten bijvoorbeeld de indeling Microsoft Office, HTML, PostScript (PS) of XDP hebben, zet u deze documenten om in de indeling PDF voordat u de documenten met PDF-documenten gebruikt.
* Op Adobe Distiller gebaseerde conversies worden niet ondersteund. PostScript(PS) bijvoorbeeld op PDF
* Op Forms Service gebaseerde conversies worden niet ondersteund. Bijvoorbeeld XDP naar PDF forms.
* De service biedt geen ondersteuning voor het converteren van een PDF van het type Signed PDF of Transparent naar een andere PDF-indeling.
* Het toepassen van gebruiksrechten met behulp van Reader Extensions Service is niet beschikbaar.
* De service biedt niet de mogelijkheid om ondertekende of transparante PDF-documenten om te zetten in de indeling PDF/A.

+++


+++ 3. Documentservices: API&#39;s voor het genereren van documenten (uitvoerservice)

In één enkele API vraag of partij, kunt u slechts één malplaatje met veelvoudige DATA dossiers van XML gebruiken. Het gebruik van meerdere sjablonen met meerdere gegevensbestanden in één API-aanroep wordt niet ondersteund.

+++

+++ 4. automatede form conversion Service

De dienst verstrekt meta-model voor de Dienst van de Automatede form conversion niet. U kunt [download het van de documentatie van de Dienst van de Automatede form conversion](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

+++

+++ 5. Forms Portal

Ondersteuning voor anoniem gebruik van Forms Portal is niet beschikbaar via de verpakking (OOTB). U kunt de Forms Portal aanpassen om de weergave van formulieren voor niet-aangemelde gebruikers in te schakelen.

+++

+++ 6. Formuliergegevensmodel

* Forms-gegevensmodel ondersteunt alleen HTTP- en HTTP-eindpunten voor het verzenden van gegevens. De service biedt geen ondersteuning voor wederzijdse SSL voor REST-connector en op x509-certificaten gebaseerde verificatie voor SOAP-gegevensbronnen.

* Met Forms as a Cloud Service kunt u Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive en services die algemene CRUD-bewerkingen (Maken, Lezen, Bijwerken en Verwijderen) ondersteunen, gebruiken als gegevensopslagsystemen. Zowel de Open API-specificatie 2.0 als de Open API-specificatie worden ondersteund. De service biedt ook ondersteuning voor JDBC-connector.

+++


+++ 7. HTML5 Forms

* De service biedt geen ondersteuning voor HTML5 Forms (Mobile Forms). Als u uw op XDP gebaseerde formulieren weergeeft als HTML5 Forms, kunt u de functie blijven gebruiken op AEM 6.5 Forms.

* Als u een gebruiksgeval hebt om gegevens offline vast te leggen en deze de volgende keer dat u online terugkeert te synchroniseren, kunt u doorgaan met het gebruik van [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) op AEM 6.5 Forms.

+++





+++ 8. Ontwikkelomgeving

* Een cloud-native omgeving heeft geen webconsole (configuratiemanager). U kunt [[!DNL AEM Forms] as a Cloud Service SDK om configuraties te genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) en CI/CD pijpleiding aan [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.
* E-mailondersteuning biedt standaard alleen HTTP- en HTTP-protocollen. [Contact opnemen met het ondersteuningsteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) om havens voor het verzenden van e-mail toe te laten en SMTP protocol voor uw milieu toe te laten.
* De service biedt geen ondersteuning voor het converteren van een PDF van het type Signed PDF of Transparent naar een andere PDF-indeling. Voordat u uw klantbundels gebruikt met as a Cloud Service Forms, kunt u uw aangepaste code opnieuw compileren met de meest recente versie van de URL-conventie adobe-aemfd-docmanager* van gelokaliseerde Adaptive Forms ondersteunt nu het opgeven van een landinstelling in de URL. Met de nieuwe URL-conventie kunnen gelokaliseerde formulieren op een verzender of CDN in cache worden geplaatst. Gebruik in een Cloud Service-omgeving de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` een gelokaliseerde versie van een adaptief formulier aanvragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe raadt u aan Dispatcher of CDN in cache te plaatsen. Het helpt de rendersnelheid van vooraf ingevulde formulieren te verbeteren
* Adobe Experience Manager Forms as a Cloud Service brengt vele nieuwe eigenschappen en mogelijkheden in uw AEMProjecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van inhoud en code in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Gebruik de [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager as a Cloud Service is gedefinieerd.


+++

<!-- 

### HTML5 Forms (Mobile Forms)

The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms.

### Adaptive Forms 

* **XSD-Based Adaptive Forms:** The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. You can use XDP-template to design a template for Document for Record. The service does not support XFA based Adaptive Forms  
* **Importing Adaptive Form templates:** Use build pipeline and corresponding Git repository of your program to import existing Adaptive Form templates. 
*  **Rule editor:** AEM Forms as a Cloud Service provides a hardened [Rule editor](rule-editor.md#visual-rule-editor). The code editor is not available on Forms as a Cloud Service. The migration utility helps you migrate your forms that have custom rules (created in code editor). The utility converts such rules into custom functions supported on Forms as a Cloud Service. You can use the reusable functions with Rule editor to continue obtaining results obtained with rule scripts  The `onSubmitError` or `onSubmitSuccess` functions are now available as actions the Rule Editor.  
* **Drafts and submissions:** The service does not retain metadata for drafts and submitted Adaptive Forms.  
* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server. 
* **Submit actions:** The **Email as PDF** action is not available. The **Email** submit action provide options to send attachments and attach Document of Record (DoR) with email. 
* **Components**:  The service does not support in-form signing experience and does not include the Summary and Verify components for Adaptive Forms.  
* **Forms portal**: Support for anonymous use of Forms portal is not available out of the box (OOTB). You can customize the forms portal to enable displaying forms for non-logged in users.

### Form Data Model

* Forms data model supports only HTTP and HTTPs endpoints to submit data. The service does not support Mutual SSL for REST connector and x509 certificate-based authentication for SOAP data sources. * Forms as a Cloud Service allows to use Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive, and services supporting general CRUD (Create, Read, Update, and Delete) operations as data stores, both Open API specification 2.0 and Open API specification are supported. The service also provides support for JDBC connector.


### Automated Forms Conversion Service     

The service does not provide meta-model for Automated Forms Conversion Service. You can [download it from Automated Forms Conversion Service documentation](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).


### Configurations

* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.  
* If you use custom bundles, recompile your code with latest version of adobe-aemfd-docmanager before using these bundles with Forms as a Cloud Service. 


### Document Services: Document Manipulation APIs (Assembler Service)

The service does not support operations dependent on other services or applications:  

* Conversion of documents in a non-PDF format to a PDF format is not supported. For example, Microsoft Word to PDF, Microsoft Excel to PDF, and HTML to PDF are not supported. If your documents are in a non-PDF format. Convert such documents to PDF format before using those with Communications Document Manipulation APIs. For example, if your documents are in Microsoft Office, HTML, PostScript (PS), XDP format, convert these documents to PDF format before using those with PDF documents. 
* Adobe Distiller-based conversions are not supported. For example, PostScript(PS) to PDF
* Forms Service-based conversions are not supported. For example, XDP to PDF Forms.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.
* Applying usage rights using Reader Extensions Service is not available. 
* The service does not provide the ability to convert signed or transparent PDF Documents to PDF/A format. 

### Document Services: Document Generation APIs (Output Service)

* In a single API call or batch, you can use one template with multiple DATA XML files. Using mutiple templates with multiple data files in a single API call is not supported. 

### Other differences

* A cloud-native environment does not have web console (configuration manager). You can use [[!DNL AEM Forms] as a Cloud Service SDK to generate configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) and CI/CD pipeline to [deploy the configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) to your Cloud Service instance.
* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.* Before using your customer bundles with Forms as a Cloud Service, recompile your custom code with the latest version of adobe-aemfd-docmanager* URL convention of localized Adaptive Forms now supports specifying a locale in the URL. New URL convention enables caching localized forms on a Dispatcher or CDN. On Cloud Service environment, use the URL format `http://host:port/content/forms/af/<afName>.<locale>.html` to request a localized version of an Adaptive Form instead of `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommends using Dispatcher or CDN caching. It helps improve rendering speed of prefilled forms 
* Adobe Experience Manager Forms as a Cloud Service brings many new features and possibilities into your AEM Projects. However, there are some changes required to Adobe Experience Manager Maven projects to be compatible with AEM Cloud Service. At a high-level, AEM requires a separation of content and code into discrete subpackages to respect the split between mutable and immutable content. Use the [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) tool to restructure existing project packages by separating content and code into discrete packages to be compatible with the project structure defined for Adobe Experience Manager as a Cloud Service.
-->




