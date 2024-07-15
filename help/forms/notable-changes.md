---
title: Wat zijn de verschillen tussen AEM 6,5 Forms en AEM Cloud Servicen?
description: Vergelijk AEM 6.5 Forms en AEM Clouden Services en leer de belangrijkste wijzigingen voordat u een upgrade uitvoert of naar Cloud Service migreert.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
role: Admin, Developer, User
feature: Adaptive Forms
contentOwner: khsingh
source-git-commit: a5179851af8ec88e23d79a74265b10cbce2d50f1
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 0%

---

# Verschil tussen AEM 6.5 Forms (AMS en on-Prem) en AEM Forms als Cloud Service (AEM CS Forms) {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service brengt een aantal opmerkelijke wijzigingen aan in bestaande functies in vergelijking met Adobe Experience Manager Forms On-Premise- en [!DNL Adobe-Managed Service] -omgevingen. De belangrijkste verschillen worden hieronder vermeld:

## Oorspronkelijke cloudmogelijkheden

* De service beschikt over een eigen cloudarchitectuur die automatisch schalen op basis van belasting, nuldowntime voor upgrades, veelvuldig en na de implementatie van nieuwe functies en updates, en topologieën die zijn geoptimaliseerd voor maximale veerkracht en efficiëntie.

* De service omvat geen verzendacties die gegevens opslaan naar Adobe Experience Manager Cloud Service-instanties, waardoor deze superveilig zijn. Gegevens die via formulieren zijn vastgelegd, worden rechtstreeks naar geconfigureerde gegevensopslagruimten verzonden.

* Een gratis CDN (content delivery network) is ook inbegrepen om u te helpen sneller formulieren te leveren en te genereren.


## Updates voor de ontwikkelingsstroom

* De dienst verstrekt SDK om douanecode in een lokale milieu (lokale machine) te ontwikkelen en te testen alvorens de code aan een Cloud Service op te stellen. Ontwikkelaars ontwikkelen en testen aangepaste componenten, thema&#39;s, workflowtoepassingen, configuraties, sjablonen en meer met de SDK op hun lokale computers. Na het testen van de douanecode in hun lokale ontwikkelomgeving, voeren zij de douanecode aan het milieu van a [ Forms CS of het werkgebiedmilieu ](/help/implementing/cloud-manager/deploy-code.md) voor het verdere testen op alvorens het aan een productiemilieu te bevorderen.

* De ontwikkelaars handhaven code voor Cloud Service en lokale ontwikkelomgeving in een gemeenschappelijke [ git bewaarplaats ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Een git-opslagplaats, gebaseerd op AEM Archetype, wordt automatisch gemaakt bij het maken van een AEM as a Cloud Service-programma.

  ![ autoverwezenlijking van git bewaarplaats op AEM als programma van de wolkendienst ](/help/forms/assets/git-repo-local-and-forms-cs.png)

* De stroom van de ontwikkeling voor Forms as a Cloud Service richt zich op AEM Archetype voor AEM Cloud Service. Er zijn echter enkele wijzigingen vereist voor Adobe Experience Manager Maven-projecten om verenigbaar te zijn met AEM Cloud Service. Op hoog niveau vereist AEM een scheiding van inhoud en code in afzonderlijke subpakketten om de splitsing tussen muteerbare en onveranderlijke inhoud te respecteren. Gebruik het [ hulpmiddel van de Modernizer van de Opslag ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) om bestaande projectpakketten te herstructureren door inhoud en code in discrete pakketten te scheiden om met de projectstructuur compatibel te zijn die voor Adobe Experience Manager as a Cloud Service wordt bepaald.

* Voordat u uw klantbundels kunt gebruiken met Forms as a Cloud Service, moet u uw aangepaste code opnieuw compileren met de nieuwste versie van adobe-aemfd-docmanager.

* Het nut van de as a Cloud Service migratie van AEM Forms van het gebruik ](/help/forms/migrate-to-forms-as-a-cloud-service.md) om uw Aangepaste Forms, thema&#39;s, malplaatjes, en wolkenconfiguraties van <!-- AEM 6.3 Forms--> AEM 6.4 Forms op OSGi en AEM 6.5 Forms op OSGi aan [!DNL AEM] as a Cloud Service voor te bereiden en te migreren. [ Gebruik de [ bewaarplaats van de Git van uw programma ](/help/implementing/cloud-manager/managing-code/managing-repositories.md) om bestaande Aangepaste malplaatjes van de Vorm in te voeren.

* E-mail steunt slechts HTTP en protocollen van HTTP, door gebrek. [ contacteer het steunteam ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) om havens toe te laten om e-mail te verzenden en protocol SMTP voor uw milieu toe te laten.

## Lokalisatie

* De URL-conventie van gelokaliseerde adaptieve Forms ondersteunt nu het opgeven van een landinstelling in de URL. Met de nieuwe URL-conventie kunnen gelokaliseerde formulieren op een Dispatcher of CDN in cache worden geplaatst. In een Cloud Service-omgeving gebruikt u de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` om een gelokaliseerde versie van een adaptief formulier aan te vragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` .

* Adobe raadt u aan Dispatcher- of CDN-caching te gebruiken. Hiermee kunt u de rendersnelheid van voorgevulde formulieren verbeteren.


## Adaptieve Forms

* **de redacteur van de Regel:** as a Cloud Service van AEM Forms verstrekt een geharde [ redacteur van de Regel ](rule-editor.md#visual-rule-editor). De code-editor is niet beschikbaar in Forms as a Cloud Service.

  Het [ migratienut ](/help/forms/migrate-to-forms-as-a-cloud-service.md) helpt u uw vormen migreren die douaneregels (die in de coderedacteur worden gecreeerd) hebben. Het hulpprogramma converteert dergelijke regels naar aangepaste functies die worden ondersteund op Forms as a Cloud Service. U kunt de herbruikbare functies met de redacteur van de Regel gebruiken om resultaten te blijven verkrijgen die met regelmanuscripten worden verkregen. De functies `onSubmitError` of `onSubmitSuccess` zijn nu beschikbaar als handelingen in de Regeleditor.

<!--* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server.-->

* **Prefill de Dienst:** Prefill haalt de dienst gegevens van de server en voegt samen om uw Aangepaste Forms op de cliëntkant vooraf in te vullen. Met deze functie kunt u de tijd verbeteren die nodig is om een adaptief formulier in te vullen. U kunt de [ prefill dienst ](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/adaptive-forms/prefill-service-adaptive-forms-article-use.html) altijd vormen om de fusieactie op de Server van Adobe Experience Manager Forms in werking te stellen.

* **legt acties voor:** E-mail **** voorlegt actie verstrekt opties om gehechtheid te verzenden en Document van Verslag (DoR) met e-mail vast te maken. U kunt het in plaats van **E-mail als PDF** actie gebruiken beschikbaar in AEM 6.5 Forms.

* **Dienst van de Automatede form conversion**: De dienst verstrekt geen meta-model voor de Dienst van de Automatede form conversion. U kunt [ het van de documentatie van de Dienst van de Automatede form conversion ](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model) downloaden.

* **op XSD-Gebaseerde Adaptieve Forms:** u kunt XDP-malplaatje gebruiken om een malplaatje voor Document voor Verslag te ontwerpen. De service biedt geen ondersteuning voor adaptieve Forms op basis van XFA

* **Componenten**: De dienst steunt in-vorm het ondertekenen ervaring niet en omvat niet de Samenvatting en verifieert componenten voor AanpassingsVorm.

* **interface van de Tovenaar:** u kunt de [ interface van de Tovenaar ](/help/forms/creating-adaptive-form-core-components.md) gebruiken om de gemeenschappelijke opties snel te vormen en gemakkelijk een AanpassingsVorm tot stand te brengen.

## Forms Portal

* De service behoudt geen metagegevens voor concepten en verzonden Adaptive Forms.

## Documentservices:

Forms as a Cloud Service biedt RESTful-API&#39;s voor het genereren en bewerken van documenten. U kunt deze API&#39;s gebruiken om documenten te genereren of te manipuleren op aanvraag of in batches, naar wens:

* **de Diensten van het Document: De Generatie APIs van het Document (de Dienst van de Output)**: In één enkele API vraag of partij, kunt u slechts één malplaatje met veelvoudige dossiers van DATA XML gebruiken. Het gebruik van meerdere sjablonen met meerdere gegevensbestanden in één API-aanroep wordt niet ondersteund.

* **Manipulation APIs van het Document (de Dienst van de Assembler)**:

   * De bewerkingen die afhankelijk zijn van documentservices of -toepassingen zijn niet beschikbaar. Microsoft® Word naar PDF, Microsoft® Excel naar PDF en HTML naar PDF, PostScript (PS) naar PDF, XDP naar PDF forms worden bijvoorbeeld niet ondersteund. Deze bewerkingen zijn respectievelijk afhankelijk van Microsoft® Office, Adobe Acrobat, Adobe Distiller en Forms Document Service.

   * Converteer documenten die een andere indeling dan PDF hebben naar een PDF-indeling voordat u de documenten gebruikt met API&#39;s voor documentanimatie voor communicatie. Als uw documenten bijvoorbeeld de indeling Microsoft® Office, HTML, PostScript (PS) of XDP hebben, zet u deze documenten om in de indeling PDF voordat u de documenten met PDF-documenten gebruikt. U kunt de {](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) dienst 0} gebruiken ConvertPDF voor dergelijke omzettingen.[

   * U kunt een AEM 6.5 Forms-omgeving gebruiken voor Digital Signature, Encryption, Reader Extension, Send to Printer, Convert PDF en Barcoded Forms-service.


## Gegevensintegratie (formuliergegevensmodel)

* De service biedt ook ondersteuning voor JDBC-connector, Microsoft® Dynamics, SalesForce, SOAP webservices en services die OData ondersteunen.

* U kunt ook verbinding maken AEM gebruikersprofiel om gebruikersgegevens op te halen en bij te werken.

* Forms-gegevensmodel ondersteunt alleen HTTP- en HTTPS-eindpunten voor het verzenden van gegevens. De service biedt geen ondersteuning voor wederzijdse SSL voor REST-connector en op x509-certificaten gebaseerde verificatie voor SOAP gegevensbronnen.

* Forms as a Cloud Service maakt het mogelijk om Microsoft® Azure Blob, Microsoft® Sharepoint, Microsoft® OneDrive en services die algemene CRUD-bewerkingen (Maken, Lezen, Bijwerken en Verwijderen) ondersteunen als gegevensopslagsystemen te gebruiken. Zowel de specificatie Open API Specification 2.0 als de specificatie Open API 3.0 worden ondersteund.


## Elektronisch ondertekenen

* De service biedt een OOTB-integratie met Adobe Sign en ondersteunt DocuSign voor e-handtekeningen.

* De service ondersteunt ook Adobe Sign-rollen. U kunt de rollen in de Adaptieve redacteur van Forms voor bedrijfsgebruikers vormen om het ondertekenen werkschema&#39;s gemakkelijk te vormen.


## HTML5 Forms

* U kunt een AEM 6.5 Forms-omgeving gebruiken om:

   * formulieren op basis van XDP weergeven als HTML5 Forms. De service biedt geen ondersteuning voor HTML5 Forms.

   * gevangen off-line gegevens en synchroniseer het de volgende tijd u online met [ AEM Forms Workspace ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) app terugkeert.

## Interactieve communicatie

* U kunt communicatie APIs gebruiken om gepersonaliseerde documenten op bestelling of in partijen op Forms as a Cloud Service te produceren. U kunt een AEM 6.5 milieu van Forms voor Interactieve Mededelingen en de gebruikersgevallen van de Agent gebruiken UI.

## Zie ook

* [Migreren van een AEM Forms (On-Premise- en AMS-omgeving) naar AEM Forms as a Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Adaptieve Forms toevoegen aan of maken op AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Een adaptief formulier maken (kerncomponenten)](/help/forms/creating-adaptive-form-core-components.md)
* [Inleiding tot AEM Forms as a Cloud Service](/help/forms/home.md)
* [Een lokale ontwikkelomgeving en een project voor initiële ontwikkeling opzetten](/help/forms/setup-local-development-environment.md)


<!--

## Additional Information

* [Introduction to AEM Forms as a Cloud Service](/help/forms/home.md)
* [Set up a local development environment and initial development project](/help/forms/setup-local-development-environment.md)

-->
