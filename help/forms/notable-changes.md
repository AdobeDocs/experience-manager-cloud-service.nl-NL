---
title: Wat zijn de verschillen tussen AEM 6,5 Forms en AEM Cloud Servicen?
description: Vergelijk AEM 6.5 Forms en AEM Clouden Services en leer de belangrijkste wijzigingen voordat u een upgrade uitvoert of naar Cloud Service migreert.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
role: Admin, Developer, User
feature: Adaptive Forms
contentOwner: khsingh
source-git-commit: 9d1594e61a3ec79c0e773cac5753885684ac8a21
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 0%

---

# Verschil tussen AEM 6.5 Forms (AMS en on-Prem) en AEM Forms als Cloud Service (AEM CS Forms) {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service brengt een aantal opmerkelijke veranderingen in bestaande eigenschappen in vergelijking met Adobe Experience Manager Forms On-Premise en [!DNL Adobe-Managed Service] omgevingen. De belangrijkste verschillen worden hieronder vermeld:

## Oorspronkelijke cloudmogelijkheden

* De service beschikt over een eigen cloudarchitectuur die automatisch schalen op basis van belasting, nuldowntime voor upgrades, veelvuldig en na de implementatie van nieuwe functies en updates, en topologieën die zijn geoptimaliseerd voor maximale veerkracht en efficiëntie.

* De service omvat geen verzendacties die gegevens opslaan naar Adobe Experience Manager Cloud Service-instanties, waardoor deze superveilig zijn. Gegevens die via formulieren zijn vastgelegd, worden rechtstreeks naar geconfigureerde gegevensopslagruimten verzonden.

* Een gratis CDN (content delivery network) is ook inbegrepen om u te helpen sneller formulieren te leveren en te genereren.


## Updates voor de ontwikkelingsstroom

* De dienst verstrekt SDK om douanecode in een lokale milieu (lokale machine) te ontwikkelen en te testen alvorens de code aan een Cloud Service op te stellen. Ontwikkelaars ontwikkelen en testen aangepaste componenten, thema&#39;s, workflowtoepassingen, configuraties, sjablonen en meer met de SDK op hun lokale computers. Na het testen van de douanecode in hun lokale ontwikkelomgeving, voeren zij de douanecode in aan een [Forms CS-omgeving ontwikkelen of stadium-omgeving](/help/implementing/cloud-manager/deploy-code.md) voor verdere tests voordat deze worden bevorderd tot een productieomgeving.

* Ontwikkelaars onderhouden code voor Cloud Service en lokale ontwikkelomgeving in een gemeenschappelijke omgeving [git-opslagplaats](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Een git-opslagplaats, gebaseerd op AEM Archetype, wordt automatisch gemaakt bij het maken van een AEM as a Cloud Service programma.

  ![automatisch aanmaken van git-opslagplaats op AEM als cloudserviceprogramma](/help/forms/assets/git-repo-local-and-forms-cs.png)

* De stroom van de ontwikkeling voor as a Cloud Service Forms richt zich op AEM Archetype voor AEM Cloud Service. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van inhoud en code in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Gebruik de [Gereedschap Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) bestaande projectpakketten te herstructureren door inhoud en code te scheiden in afzonderlijke pakketten, zodat deze verenigbaar zijn met de voor Adobe Experience Manager as a Cloud Service gedefinieerde projectstructuur.

* Voordat u uw klantbundels gebruikt met as a Cloud Service Forms, moet u uw aangepaste code opnieuw compileren met de nieuwste versie van adobe-aemfd-docmanager.

* Gebruiken [AEM Forms as a Cloud Service migratiehulpprogramma](/help/forms/migrate-to-forms-as-a-cloud-service.md) om uw Adaptieve Forms, thema&#39;s, sjablonen en cloudconfiguraties voor te bereiden en te migreren vanuit <!-- AEM 6.3 Forms--> AEM 6.4 Forms op OSGi en AEM 6.5 Forms op OSGi aan [!DNL AEM] as a Cloud Service. Gebruik de [Opslagruimte van uw programma maken](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) bestaande adaptieve formuliersjablonen importeren.

* E-mail steunt slechts HTTP en protocollen van HTTP, door gebrek. [Contact opnemen met het ondersteuningsteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) om havens toe te laten om e-mail te verzenden en SMTP protocol voor uw milieu toe te laten.

## Lokalisatie

* De URL-conventie van gelokaliseerde adaptieve Forms ondersteunt nu het opgeven van een landinstelling in de URL. Met de nieuwe URL-conventie kunnen gelokaliseerde formulieren op een verzender of CDN in cache worden geplaatst. Gebruik in een Cloud Service-omgeving de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` een gelokaliseerde versie van een adaptief formulier aanvragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe raadt aan Dispatcher of CDN in cache te plaatsen. Hiermee kunt u de rendersnelheid van voorgevulde formulieren verbeteren.


## Adaptieve Forms

* **Regeleditor:** AEM Forms as a Cloud Service biedt een geharde [Regeleditor](rule-editor.md#visual-rule-editor). De code-editor is niet beschikbaar in Forms as a Cloud Service.

  De [migratiehulpprogramma](/help/forms/migrate-to-forms-as-a-cloud-service.md) helpt u bij het migreren van formulieren met aangepaste regels (gemaakt in de code-editor). Het hulpprogramma converteert dergelijke regels naar aangepaste functies die worden ondersteund op as a Cloud Service Forms. U kunt de herbruikbare functies met de redacteur van de Regel gebruiken om resultaten te blijven verkrijgen die met regelmanuscripten worden verkregen. De `onSubmitError` of `onSubmitSuccess` functies zijn nu beschikbaar als handelingen in de Editor voor regels.

<!--* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server.-->

* **Prefill-service:** Met de voorkeursservice worden gegevens opgehaald van de server en worden deze samengevoegd om de Adaptieve Forms vooraf op de client in te vullen. Met deze functie kunt u de tijd verbeteren die nodig is om een adaptief formulier in te vullen. U kunt altijd de [Prefill-service](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/adaptive-forms/prefill-service-adaptive-forms-article-use.html) om de samenvoegactie op de Adobe Experience Manager Forms-server uit te voeren.

* **Handelingen verzenden:** De **E-mail** Verzenden bevat opties voor het verzenden van bijlagen en het toevoegen van een e-maildocument (DoR) bij het document Record. U kunt het gebruiken in plaats van **E-mailen als PDF** in AEM 6.5 Forms.

* **Automatede form conversion-service**: De dienst verstrekt geen meta-model voor de Dienst van de Automatede form conversion. U kunt [download het van de documentatie van de Dienst van de Automatede form conversion](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

* **Adaptieve Forms op basis van XSD:** U kunt XDP-malplaatje gebruiken om een malplaatje voor Document voor Verslag te ontwerpen. De service biedt geen ondersteuning voor adaptieve Forms op basis van XFA

* **Componenten**: De service biedt geen ondersteuning voor ondertekeningservaring in formulieren en bevat geen componenten Overzicht en Verifiëren voor Adaptief formulier.

* **Wizard-interface:** U kunt de [Wizard-interface](/help/forms/creating-adaptive-form-core-components.md) om snel de algemene opties te configureren en eenvoudig een adaptief formulier te maken.

## Forms Portal

* De service behoudt geen metagegevens voor concepten en verzonden Adaptive Forms.

## Documentservices:

Forms as a Cloud Service biedt RESTful-API&#39;s voor het genereren en bewerken van documenten. U kunt deze API&#39;s gebruiken om documenten te genereren of te manipuleren op aanvraag of in batches, naar wens:

* **Documentservices: API&#39;s voor het genereren van documenten (uitvoerservice)**: In één API-aanroep of -batch kunt u slechts één sjabloon gebruiken met meerdere DATA XML-bestanden. Het gebruik van meerdere sjablonen met meerdere gegevensbestanden in één API-aanroep wordt niet ondersteund.

* **Document Manipulation APIs (Assembler Service)**:

   * De bewerkingen die afhankelijk zijn van documentservices of -toepassingen zijn niet beschikbaar. Microsoft® Word naar PDF, Microsoft® Excel naar PDF en HTML naar PDF, PostScript (PS) naar PDF en XDP naar PDF forms worden bijvoorbeeld niet ondersteund. Deze bewerkingen zijn respectievelijk afhankelijk van Microsoft® Office, Adobe Acrobat, Adobe Distiller en Forms Document Service.

   * Converteer documenten die een andere indeling dan PDF hebben naar een PDF-indeling voordat u de documenten gebruikt met API&#39;s voor documentanimatie voor communicatie. Als uw documenten bijvoorbeeld de indeling Microsoft® Office, HTML, PostScript (PS) of XDP hebben, zet u deze documenten om in de indeling PDF voordat u de documenten met PDF-documenten gebruikt. U kunt de [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) voor dergelijke omzettingen.

   * U kunt een AEM 6.5 Forms-omgeving gebruiken voor Digital Signature, Encryption, Reader Extension, Send to Printer, Convert PDF en Barcoded Forms-service.


## Gegevensintegratie (formuliergegevensmodel)

* De service biedt ook ondersteuning voor JDBC-connector, Microsoft® Dynamics, SalesForce, SOAP-webservices en services die OData ondersteunen.

* U kunt ook verbinding maken AEM gebruikersprofiel om gebruikersgegevens op te halen en bij te werken.

* Forms-gegevensmodel ondersteunt alleen HTTP- en HTTPS-eindpunten voor het verzenden van gegevens. De service biedt geen ondersteuning voor wederzijdse SSL voor REST-connector en op x509-certificaten gebaseerde verificatie voor SOAP-gegevensbronnen.

* Met Forms as a Cloud Service kunt u Microsoft® Azure Blob, Microsoft® Sharepoint, Microsoft® OneDrive en services die algemene CRUD-bewerkingen (Maken, Lezen, Bijwerken en Verwijderen) ondersteunen, gebruiken als gegevensopslag. Zowel de Open API-specificatie 2.0 als de Open API 3.0-specificatie worden ondersteund.


## Elektronisch ondertekenen

* De service biedt een OOTB-integratie met Adobe Sign en ondersteunt DocuSign voor e-handtekeningen.

* De service ondersteunt ook Adobe Sign-rollen. U kunt de rollen in de Adaptieve redacteur van Forms voor bedrijfsgebruikers vormen om het ondertekenen werkschema&#39;s gemakkelijk te vormen.


## HTML5 Forms

* U kunt een AEM 6.5 Forms-omgeving gebruiken om:

   * formulieren op basis van XDP weergeven als HTML5 Forms. De service biedt geen ondersteuning voor HTML5 Forms.

   * gegevens offline vastleggen en synchroniseren de volgende keer dat u online terugkeert met de [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) app.

## Interactieve communicatie

* U kunt Communicatie APIs gebruiken om gepersonaliseerde documenten op bestelling of in partijen op as a Cloud Service Forms te produceren. U kunt een AEM 6.5 milieu van Forms voor Interactieve Mededelingen en de gebruikersgevallen van de Agent gebruiken UI.

## Zie ook

* [Migreren van een AEM Forms (On-Premise- en AMS-omgeving) naar een as a Cloud Service AEM Forms](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Adaptieve Forms toevoegen aan of maken op AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Een adaptief formulier maken (kerncomponenten)](/help/forms/creating-adaptive-form-core-components.md)
* [Inleiding tot AEM Forms as a Cloud Service](/help/forms/home.md)
* [Een lokale ontwikkelomgeving en een project voor initiële ontwikkeling opzetten](/help/forms/setup-local-development-environment.md)


<!--

## Additional Information

* [Introduction to AEM Forms as a Cloud Service](/help/forms/home.md)
* [Set up a local development environment and initial development project](/help/forms/setup-local-development-environment.md)

-->
