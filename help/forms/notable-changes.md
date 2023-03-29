---
title: Verschillen tussen AEM 6.5 Forms en AEM Cloud Services
description: Bent u een Experience Manager Forms-gebruiker en wilt u een upgrade uitvoeren naar Adobe Experience Manager Forms as a Cloud Service? Vergelijk AEM 6.5 Forms en AEM Cloud Services en leer de meest opvallende wijzigingen voordat u een upgrade uitvoert of naar Cloud Service migreert.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: dea6c266e5c10135a320f923dc77d0fd2050988e
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# Opvallende wijzigingen voor bestaande Adobe Experience Manager 6.5 Forms-gebruikers  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service brengt een aantal opmerkelijke veranderingen in bestaande eigenschappen in vergelijking met Adobe Experience Manager Forms On-Premise en [!DNL Adobe-Managed Service] omgevingen. De belangrijkste verschillen worden hieronder vermeld:

<!-- 
<table>
    <thead>
        <tr>
            <th>AEM Forms Components</th>
            <th>Feature/Capability</th>
            <th>[!DNL AEM Forms] as a Cloud Service</th>
            <th>AEM 6.5 Forms on-premise </th>
            <th>AEM 6.5 Forms Adobe Managed Services </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="6">Cloud native features</td>
            <td>Cloud-native architecture</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Auto-scaling based on load</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Zero downtime for upgrades</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Feature roll-out frequency</td>
            <td>Monthly</td>
            <td>Quarterly</td>
            <td>Quarterly</td>
        </tr>
        <tr>
            <td>CDN (content delivery network) included</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Topologies optimized for maximum resilience and efficiency</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="3">Developer environment <sup>6</sup></td>
            <td>Self-Service via Cloud Manager</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Cloud-native development environment</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        <tr>
            <td>Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="8">Third-party and Adobe integrations</td>
            <td>[!DNL Micosoft Power Automate] for business process automation</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Microsoft Dynamics] and [!DNL Salesforce] for Customer Relationship Management (CRM)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Integration with [!DNL Microsoft Azure] for data storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL DocuSign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Sign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[Adobe Launch] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Analytics] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Google reCaptcha for adaptive challenges</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="11">Adaptive Forms</td>
            <td>Automated Forms Conversion Service<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Core Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Foundation Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Form creation wizard</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Rule Editor<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Prefill Service <sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Auto-save an adaptive form</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>XSD-Based adaptive forms <sup>1</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>In-form signing experience for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Submit an adaptive form to AEM Forms on JEE Workflows (Process Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Summary, Verify, and Scribble Signature components for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="4">Forms Portal</td>
            <td>Drafts and Submission component <sup>2<sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Search & Lister component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Link component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>List forms for non-logged in users <sup>2</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="13">Data integration (Form Data Model) </td>
            <td>OData services</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Dynamics</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>SalesForce</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Azure Blob Storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 3.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 2.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>SOAP-based web services <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Microsoft SQL Server</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>MySQL</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>IBM DB2</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
                <tr>
            <td>Oracle RDBMS</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>AEM user profile</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Sybase</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="8">Communication APIs (Document Services)</td>
            <td>Document Generation (Output Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Manipulation (Assembler Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Signature Service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Encryption service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Reader Extension service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Send to printer service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Convert PDF service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Barcoded Forms service </td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Security</td>
            <td>Document Security Extension for Microsoft Office (Digital Rights Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="2">HTML5 Forms <sup>5</sup></td>
            <td>HTML5 Forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Forms Workspace</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Interactive Communications</td>
            <td>Interactive Communications</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
    </tbody>
</table>


<!-- 

## Cloud native features 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2705;  | --- |
| Auto-scaling based on load | &#x2705;  | --- |
| Zero downtime for upgrades | &#x2705;  | --- |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2705;  | --- | 
| Topologies optimized for maximum resilience and efficiency| &#x2705;  | --- | 

## Integrations 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Integration with [!DNL Micosoft Power Automate] | &#x2705; | --- | 
| Integration with [!DNL DocuSign] | &#x2705; | --- | 
| Integration with [!DNL Microsoft Dynamics] and [!DNL Salesforce] | &#x2705; | --- |  
| Integration with Microsoft Azure data stores | &#x2705; | --- | 
| Integration with [!DNL Adobe Sign] | &#x2705; | &#x2705; | 
| Integration with [!DNL AEM Sites] | &#x2705;| &#x2705; | 
| Integration with [!DNL Adobe Launch] | &#x2705; | &#x2705; | 
| Integration with [!DNL Adobe Analytics] | &#x2705; | &#x2705; |
| Data integration (Form Data Model) | &#x2705; | &#x2705; |
 
## Adaptive forms <sup> 1 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Automated Forms Conversion Service  | &#x2705; | &#x2705; |
| Forms Portal Submissions | &#x2705; | &#x2705; | 
| Google Captcha integrations | &#x2705; | &#x2705; |
| Repeatable sections in an adaptive form | &#x2705;| &#x2705; |
| Form fragments | &#x2705; | --- |
| Hardened rule editor | &#x2705; | --- | 
| Form creation wizard | &#x2705; | --- |
| Auto-save an adaptive form | --- | &#x2705; |
| Scribble Signatures | --- | &#x2705; |
| XSD-Based adaptive forms | --- | &#x2705; |
| Using Adobe Sign to add signatures within an Adaptive Form | --- | &#x2705; |
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## Communication APIs (Document Services <sup> 2 </sup>) and Document Security 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Document Generation (Output Service)| &#x2705; | &#x2705; |
| Document Manipulation (Assembler Service) | &#x2705; | &#x2705; |
| Signature service | --- | &#x2705; |
| Encryption service | --- | &#x2705; |
| Reader Extension service | --- | &#x2705; |
| Send to printer service | --- | &#x2705; |
| Convert PDF service | --- | &#x2705; |
| Barcoded Forms service | --- | &#x2705; |
| Document Security Extension for Microsoft Office (Digital Rights Management) | --- | &#x2705; | 

## Data integration (Form Data Model) <sup> 3 </sup>

| Data Sources | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| OData services | &#x2705; (Version 4.0)|  --- | 
| Microsoft Dynamics| &#x2705;  | --- | 
| SalesForce|  &#x2705; | ---| 
| Microsoft Azure Blob Storage| &#x2705;  | --- | 
| RESTful web services Open API version 3.0| &#x2705; | --- |
| RESTful web services Open API version 2.0| &#x2705; | &#x2705; |
| SOAP-based web services| &#x2705;| &#x2705; |   
| MySQL| &#x2705; | &#x2705; | 
| Microsoft SQL Server| &#x2705; | &#x2705; | 
| IBM DB2| &#x2705; | &#x2705; | 
| Oracle RDBMS| &#x2705; | &#x2705; | 
| Sybase|  ---  | &#x2705; | 
| AEM user profile| --- | &#x2705; | 

## Form-centric workflows

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## HTML5 Forms<sup> 4 </sup> and Interactive Communications 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| HTML5 Forms | --- | &#x2705; | 
| HTML5 Workspace| --- | &#x2705; | 
| Interactive Communications | --- | &#x2705; | 

## Developer environment <sup> 5 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native development environment | &#x2705;  | --- | 
| Self-Service via Cloud Manager | &#x2705;  | --- | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2705;  | --- | 


-->

## Oorspronkelijke cloudmogelijkheden

* De service beschikt over een eigen cloudarchitectuur die automatisch schalen op basis van belasting, nuldowntime voor upgrades, veelvuldig en na de implementatie van nieuwe functies en updates, en topologieën die zijn geoptimaliseerd voor maximale veerkracht en efficiëntie.

* De service biedt mogelijkheden voor gegevensexternalisatie (er worden geen gegevens op de server bewaard voor een bepaald type verwerking) en bevat geen verzendacties waarmee gegevens worden opgeslagen naar instanties van Adobe Experience Manager Cloud Service, waardoor de service superveilig wordt. Gegevens die via formulieren zijn vastgelegd, worden rechtstreeks naar geconfigureerde gegevensopslagruimten verzonden.

* Een gratis CDN (content delivery network) is ook inbegrepen om u te helpen sneller formulieren te leveren en te genereren.


## Updates voor de ontwikkelingsstroom

* De dienst verstrekt SDK om douanecode in een lokale milieu (lokale machine) te ontwikkelen en te testen alvorens de code aan een Cloud Service op te stellen. Ontwikkelaars ontwikkelen en testen aangepaste componenten, thema&#39;s, workflowtoepassingen, configuraties, sjablonen en meer met de SDK op hun lokale computers. Na het testen van de douanecode in hun lokale ontwikkelomgeving, voeren zij de douanecode in aan een [Forms CS-omgeving ontwikkelen of stadium-omgeving](/help/implementing/cloud-manager/deploy-code.md) voor verdere tests voordat deze worden bevorderd tot een productieomgeving.

* Ontwikkelaars onderhouden code voor de Cloud Service en de lokale ontwikkelomgeving in een gemeenschappelijke omgeving [git-opslagplaats](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Een git-opslagplaats, gebaseerd op AEM Archetype, wordt automatisch gemaakt bij het maken van een AEM as a Cloud Service programma.

   ![](/help/forms/assets/git-repo-local-and-forms-cs.png)


* Een cloud-native omgeving heeft geen webconsole (configuratiemanager). U kunt [[!DNL AEM Forms] as a Cloud Service SDK om configuraties te genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) en CI/CD pijpleiding aan [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.

* Adobe Experience Manager Forms as a Cloud Service brengt vele nieuwe eigenschappen en mogelijkheden in uw AEMProjecten. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van inhoud en code in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Gebruik de [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) om bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze compatibel zijn met de projectstructuur die voor Adobe Experience Manager as a Cloud Service is gedefinieerd.

* Voordat u uw klantbundels gebruikt met as a Cloud Service Forms, moet u uw aangepaste code opnieuw compileren met de nieuwste versie van adobe-aemfd-docmanager.

* Gebruiken [AEM Forms as a Cloud Service migratiehulpprogramma](/help/forms/migrate-to-forms-as-a-cloud-service.md) om uw Adaptieve Forms, thema&#39;s, sjablonen en cloudconfiguraties voor te bereiden en te migreren vanuit <!-- AEM 6.3 Forms--> AEM 6.4 Forms op OSGi en AEM 6.5 Forms op OSGi aan [!DNL AEM] as a Cloud Service. Gebruiken [Opslagruimte van uw programma](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) om bestaande adaptieve formuliersjablonen te importeren.

* E-mail steunt slechts HTTP en protocollen van HTTP, door gebrek. [Contact opnemen met het ondersteuningsteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) om havens voor het verzenden van e-mail toe te laten en SMTP protocol voor uw milieu toe te laten.

## Lokalisatie

* De URL-conventie van gelokaliseerde adaptieve Forms ondersteunt nu het opgeven van een landinstelling in de URL. Met de nieuwe URL-conventie kunnen gelokaliseerde formulieren op een verzender of CDN in cache worden geplaatst. Gebruik in een Cloud Service-omgeving de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` een gelokaliseerde versie van een adaptief formulier aanvragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe raadt u aan Dispatcher of CDN in cache te plaatsen. Hiermee kunt u de rendersnelheid van voorgevulde formulieren verbeteren.


## Adaptieve Forms

* **Regeleditor:** AEM Forms as a Cloud Service biedt een harde [Regeleditor](rule-editor.md#visual-rule-editor). De code-editor is niet beschikbaar in Forms as a Cloud Service.

   De [migratiehulpprogramma](/help/forms/migrate-to-forms-as-a-cloud-service.md) helpt u bij het migreren van formulieren met aangepaste regels (gemaakt in de code-editor). Het hulpprogramma converteert dergelijke regels naar aangepaste functies die worden ondersteund op as a Cloud Service Forms. U kunt de herbruikbare functies met de redacteur van de Regel gebruiken om resultaten te blijven verkrijgen die met regelmanuscripten worden verkregen. De `onSubmitError` of `onSubmitSuccess` functies zijn nu beschikbaar als handelingen in de Editor voor regels.

* **Prefill-service:** Standaard voegt de Prefill-service gegevens samen met een Adaptief formulier op de client in plaats van gegevens op de server samen te voegen in AEM 6.5 Forms. De functie helpt de tijd te verbeteren die nodig is om een adaptief formulier vooraf in te vullen. U kunt altijd configureren om de samenvoegactie op de Adobe Experience Manager Forms-server uit te voeren.

* **Handelingen verzenden:** De **E-mail** Verzenden bevat opties voor het verzenden van bijlagen en het toevoegen van een e-mail aan het Document of Record (DoR). U kunt het gebruiken in plaats van **E-mailen als PDF** actie beschikbaar in AEM 6.5 Forms.

* **automatede form conversion Service**: De dienst verstrekt meta-model voor de Dienst van de Automatede form conversion niet. U kunt [download het van de documentatie van de Dienst van de Automatede form conversion](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

* **Adaptieve Forms op basis van XSD:** U kunt XDP-malplaatje gebruiken om een malplaatje voor Document voor Verslag te ontwerpen. De service biedt geen ondersteuning voor adaptieve Forms op basis van XFA

* **Componenten**: De service biedt geen ondersteuning voor ondertekeningservaring in formulieren en bevat geen componenten Overzicht en Verifiëren voor Adaptive Forms.

## Forms Portal

* U kunt de componenten Zoeken en registreren, Concepten en Verzending en Koppeling van Forms Portal gebruiken om formulieren weer te geven voor aangemelde gebruikers. Ondersteuning voor anoniem gebruik van Forms Portal is niet beschikbaar via de verpakking (OOTB). U kunt de Forms Portal aanpassen om de weergave van formulieren voor niet-aangemelde gebruikers in te schakelen.

* De service behoudt geen metagegevens voor concepten en verzonden Adaptive Forms.

## Document Services:

Forms as a Cloud Service biedt RESTful-API&#39;s voor het genereren en bewerken van documenten. U kunt deze API&#39;s gebruiken om documenten te genereren of te manipuleren op aanvraag of in batches, naar wens:

* **Documentservices: API&#39;s voor het genereren van documenten (uitvoerservice)**: In één enkele API vraag of partij, kunt u slechts één malplaatje met veelvoudige DATA dossiers van XML gebruiken. Het gebruik van meerdere sjablonen met meerdere gegevensbestanden in één API-aanroep wordt niet ondersteund.

* **Document Manipulation APIs (Assembler Service)**:

   * De bewerkingen die afhankelijk zijn van documentservices of -toepassingen zijn niet beschikbaar. Microsoft Word naar PDF, Microsoft Excel naar PDF en HTML naar PDF, PostScript (PS) naar PDF en XDP naar PDF forms worden bijvoorbeeld niet ondersteund. Deze bewerkingen zijn respectievelijk afhankelijk van Microsoft Office, Adobe Acrobat, Adobe Distiller en Forms Document Service.

   * Converteer documenten die een andere indeling dan PDF hebben naar een PDF-indeling voordat u de documenten gebruikt met API&#39;s voor documentanimatie voor communicatie. Als uw documenten bijvoorbeeld de indeling Microsoft Office, HTML, PostScript (PS) of XDP hebben, zet u deze documenten om in de indeling PDF voordat u de documenten met PDF-documenten gebruikt. U kunt de [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) voor dergelijke omzettingen.

* U kunt een AEM 6.5 Forms-omgeving gebruiken voor Digital Signature, Encryption, Reader Extension, Send to Printer, Convert PDF en Barcoded Forms-service.


## Gegevensintegratie (formuliergegevensmodel)

* Met Forms as a Cloud Service kunt u Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive en services die algemene CRUD-bewerkingen (Maken, Lezen, Bijwerken en Verwijderen) ondersteunen, gebruiken als gegevensopslagsystemen. Zowel de specificatie Open API 2.0 als de specificatie Open API 3.0 worden ondersteund.

* De service biedt ook ondersteuning voor JDBC-connector, Microsoft Dynamics, SalesForce, SOAP-webservices en services die OData ondersteunen.

* U kunt ook verbinding maken AEM gebruikersprofiel om gebruikersgegevens op te halen en bij te werken.

* Forms-gegevensmodel ondersteunt alleen HTTP- en HTTPS-eindpunten voor het verzenden van gegevens. De service biedt geen ondersteuning voor wederzijdse SSL voor REST-connector en op x509-certificaten gebaseerde verificatie voor SOAP-gegevensbronnen.


## Elektronisch ondertekenen

* De service biedt een OOTB-integratie met Adobe Sign en ondersteunt DocuSign voor e-handtekeningen.


## HTML5 Forms

* U kunt een AEM 6.5 Forms-omgeving gebruiken om:

   * formulieren op basis van XDP weergeven als HTML5 Forms. De service biedt geen ondersteuning voor HTML5 Forms (Mobile Forms).

   * gegevens offline vastleggen en synchroniseren de volgende keer dat u online terugkeert met [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) app.

## Interactieve communicatie

* U kunt communicatie APIs gebruiken om gepersonaliseerde documenten op bestelling of in partijen te produceren. U kunt een AEM 6.5 Forms-omgeving gebruiken voor webkanalen en de gebruikersinterface van de Agent.

## Documentbeveiligingsextensie voor Microsoft Office

* Document Security Extension for Microsoft Office (Digital Rights Management) biedt ondersteuning voor AEM 6.5 Forms. De extensie is niet beschikbaar voor Forms as a Cloud Service.








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




