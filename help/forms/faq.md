---
title: Veelgestelde vragen voor AEM Forms as a Cloud Service
description: as a Cloud Service vragen van Forms
contentOwner: khsingh
role: User
feature: Adaptive Forms
index: false
exl-id: 0b14b680-7da5-4e0b-bd6a-c379d148f9d7
source-git-commit: 5ee37f59bb959e0549c0541c6568aa8c135c330e
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 0%

---

# Veelgestelde vragen {#frequently-asked-questions}

* **Kan ik de Redacteur van de Code gebruiken om regels tot stand te brengen?**
U kunt de Visuele Redacteur gebruiken om de regels tot stand te brengen. De Code-editor is niet beschikbaar in [!DNL Forms] as a Cloud Service. Als uw AanpassingsFormulier gebruikmaakt van regel manuscripten die gebruikend coderedacteur worden ontwikkeld, gebruik het [ Nut van de Migratie ](migrate-to-forms-as-a-cloud-service.md) om uw codemanuscripten in douanefuncties om te zetten. U kunt douanefuncties met Visuele Redacteur gebruiken om de resultaten te blijven verkrijgen die met de Redacteur van de Code worden verkregen.

* **kan ik een op XFA-Gebaseerde AanpassingsVorm op de instanties van de Cloud Service tot stand brengen?**
Ja, u kunt een XFA-gebaseerd adaptief formulier maken op een Cloud Service-instantie. Ondersteuning voor adaptieve Forms op basis van XFA is echter niet beschikbaar voor AEM Forms as a Cloud Service SDK (Local Development Environment). Als u van plan bent om op XFA-Gebaseerde AanpassingsForms met AEM Forms as a Cloud Service SDK te gebruiken, contacteer de Steun van de Adobe met details van uw gebruiksgeval en specifieke vereisten.

<!-- * **Can I use an XDP as a Document of Record (DoR) template? Is Forms Designer included in AEM Forms as a Cloud Service license?** 

  Yes, you can use an XDP as a Document of Record template on Cloud Service instances. However, support to use XDP as a Document of Record template is not available for AEM Forms as a Cloud Service SDK (Local development environment). -->

* **kan ik inhoud van een op-gebouw of [!DNL Adobe-Managed Services] milieu&#39;s aan [!DNL Forms] as a Cloud Service milieu migreren?**
Ja, u kunt uw aangepaste code, inhoud en elementen migreren van [!DNL Adobe-Managed Services] -omgevingen naar [!DNL Forms] as a Cloud Service omgevingen. Voor gedetailleerde instructies, zie [ migreren aan Forms as a Cloud Service ](migrate-to-forms-as-a-cloud-service.md).

<!-- You can use package manager or Experience Manager UI to [export and import Forms and related assets](import-export-forms-templates.md), use the migration utility to make your existing assets compatible with [!DNL Forms] as a Cloud Service, use the [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=nl-NL#best-practices-analyzer) tool to find the features and APIs that require changes and updated before migration, and use the [Content Transfer Tools](https://docs.adobe.com/content/help/nl-NL/experience-manager-cloud-service/moving/home.html) to move your custom code without refactoring it. -->

* **Waar kan ik AEM [!DNL Forms] as a Cloud Service [!DNL Java™] API verwijzingsdocumentatie krijgen?**
U kunt de referentiedocumentatie voor Java™ API downloaden van [!DNL Maven Central Repository] . Downloaden:
   1. Ga naar [[!DNL Maven Central Repository] ](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. Zoek en open de pagina met de nieuwste versie van [!DNL Experience Manager Forms] SDK.
   1. Klik op Alles weergeven om alle bestanden weer te geven.
   1. Download en extraheer de `aem-forms-sdk-api-<version>-javadocs` .jar.
   1. Open het bestand index.html om de API-naslagdocumentatie te bekijken.

* **Waar kan ik [!DNL JavaScript™] API verwijzing voor Adaptive Forms krijgen?**
U kunt de [!DNL JavaScript™] API-naslagdocumentatie downloaden van [!DNL &#x200B; Maven Central Repository] . Downloaden:
   1. Openen [[!DNL Maven Central Repository] ](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api) .
   1. Zoek en open de pagina met de nieuwste versie van [!DNL Experience Manager Forms] SDK.
   1. Klik op Alles weergeven om alle bestanden weer te geven.
   1. Download en extraheer de `aem-forms-sdk-api-<version>-jsdoc.jar` .
   1. Open het bestand index.html om de API-naslagdocumentatie te bekijken.

* **Kan ik bestaande thema&#39;s en malplaatjes blijven gebruiken?**
Ja, kunt u blijven gebruikend thema&#39;s die met AEM 6.4 Forms en AEM 6.5 Forms worden gecreeerd nadat u het [ Nut van de Migratie ](migrate-to-forms-as-a-cloud-service.md) gebruikt om hen naar [!DNL AEM Forms] as a Cloud Service te bewegen.

  U kunt een project ook tot stand brengen dat op [!DNL AEM Forms] as a Cloud Service [ wordt gebaseerd Archetype ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) en gebruik inbegrepen steekproefthema&#39;s en malplaatjes.

* **Kan ik schema-volgzame gegevens veroorzaken?**
Ja, u kunt Adaptive Forms maken om schemaconforme gegevens te produceren.

<!-- * **Can I pass custom parameters to the prefill service?**
Custom parameters are planned for an upcoming release. -->

* **Kan ik beveiligde inhoud in cache plaatsen?**
Functies voor beveiligde inhoud die in de cache worden geplaatst, zijn standaard uitgeschakeld. Om de eigenschap toe te laten, kunt u de instructies uitvoeren die bij [ in het voorgeheugen onderbrengend Beveiligde Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=nl-NL) worden verstrekt.

* **ik heb een gelokaliseerde Aangepaste Vorm; het geeft gelokaliseerde versie niet terug? Wat zou de oorzaak en hoe te om het op te lossen kunnen zijn?**

  De URL-conventie van gelokaliseerde adaptieve Forms ondersteunt nu het opgeven van een landinstelling in de URL. Met de nieuwe URL-conventie kunnen gelokaliseerde formulieren op een Dispatcher of CDN in cache worden geplaatst. In een Cloud Service-omgeving gebruikt u de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` om een gelokaliseerde versie van een adaptief formulier aan te vragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` . Adobe raadt u aan Dispatcher- of CDN-caching te gebruiken. Hiermee kunt u de rendersnelheid van voorgevulde formulieren verbeteren.

* **ik heb een Aangepast Vorm bijgewerkt; de bijgewerkte versie is niet beschikbaar voor klanten aan gebruik?**
CDN vernieuwt de cache standaard na elke 5 minuten, wacht 5 minuten en controleert vervolgens op de bijgewerkte versie.

* **kan ik de stap van de Handtekening in een Aangepast Vorm gebruiken om een in-browser ondertekenende ervaring tot stand te brengen?**
Nee, de stap Handtekening is niet beschikbaar voor [!DNL Forms] as a Cloud Service. Verwijder de stap Handtekening in de Adaptieve Forms. In plaats van de stap Handtekening kunnen gebruikers na verzending een adaptief formulier ondertekenen. Hiermee kunt u een ondertekeningservaring in de browser blijven gebruiken.

* **kan ik de Verify stap in een Aangepast Vorm gebruiken?**
Nee, de stap Verifiëren is niet beschikbaar voor [!DNL Forms] as a Cloud Service. Verwijder de stap Verifiëren uit uw bestaande Adaptief Forms voordat u dergelijke formulieren naar een Cloud Service-omgeving verplaatst.

* **Kan ik grafieken aan een Aangepast Vorm toevoegen?**
Ja, u kunt grafieken toevoegen aan Adaptive Forms. Adaptive Forms biedt een diagramcomponent. U kunt hiermee grafieken toevoegen aan een adaptief formulier.

* **Kan ik een Model van de Gegevens van de Vorm met een relationeel gegevensbestandmodel verbinden?**
U kunt een formuliergegevensmodel verbinden met een gebruikersprofiel voor [!DNL RESTful web services] , [!DNL SOAP-based web services] , [!DNL OData services] en Experience Managers als gegevensbronnen. <!--Support to connect a Form Data Model with a relational database is not available.-->

* **Kan ik douanecertificaten met het Model van de Gegevens van de Vorm (FDM) voor authentificatie gebruiken?**
FDM (Form Data Model) biedt geen methode om aangepaste certificaten voor verificatie te gebruiken. De aangepaste certificaten zoals x509 en 2-way SSL worden dus niet ondersteund.

* **Kan ik Forms Portal gebruiken om actie Aangepaste Forms voor te leggen?**

  U kunt uw bestaande Aangepaste Forms wijzigen om [ te gebruiken voorleggen aan REST eindpunt ](configuring-submit-actions.md#submit-to-rest-endpoint), [ verzendt e-mail ](configuring-submit-actions.md#send-email), [ voorlegt gebruikend het Model van de Gegevens van de Vorm (FDM) ](configuring-submit-actions.md#submit-using-form-data-model), en [ roept een AEM Werkschema ](configuring-submit-actions.md#invoke-an-aem-workflow) acties voor. Handeling Forms Portal en Forms Portal verzenden is nog niet beschikbaar. Houd de maandelijkse opmerkingen bij de release in de gaten voor de beschikbaarheid van de functies.

* **Kan ik [!DNL AEM Forms] app met [!DNL AEM Forms] as a Cloud Service gebruiken?**

  Adaptive Forms biedt een responsief ontwerp. Deze formulieren wijzigen de weergave, het ontwerp en de interactiviteit op basis van het onderliggende apparaat. U kunt Adaptive Forms blijven gebruiken op een mobiel apparaat terwijl u de maandelijkse opmerkingen over de release bijhoudt voor de beschikbaarheid van de functies.

* **Welke eigenschappen maken geen deel uit van de aanvankelijke versie GA?**
Forms Portal, [!DNL AEM Forms] -app, integratie met Adobe Analytics en integratie met Adobe Target maken geen deel uit van de eerste GA-release. Raadpleeg de maandelijkse releaseopmerkingen voor meer informatie over de nieuwe functies.

* **ik heb a [ schema JSON ontworpen om een adaptieve vorm ](adaptive-form-json-schema-form-model.md) tot stand te brengen. Het JSON-schema definieert gebeurtenissen voor bepaalde componenten van adaptieve formulieren. Biedt AEM Forms as a Cloud Service ondersteuning voor gebeurtenissen?**
Creeer de Adaptieve Vorm die op het schema JSON op Experience Manager 6.5 het milieu van Forms wordt gebaseerd en gebruik het [ nut van de Migratie ](migrate-to-forms-as-a-cloud-service.md) om zulk Aangepast Forms aan AEM Forms as a Cloud Service te migreren. Het hulpprogramma converteert dergelijke gebeurtenissen naar clientbibliotheken en u kunt Adaptive Forms blijven gebruiken voor gebeurtenissen in een Cloud Service-omgeving.

<!-- 

* **Is there any AEM Forms as a Cloud Service connector for Microsoft Power Automate?**

  Yes, Adobe provides an Adobe Experience Manager connector to access [Adobe Experience Manager Forms - Communication capabilities](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?lang=nl-NL) through Microsoft Power Automate. You can create a PDF document that is based on a form design and XML form data or create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) and other Printer Definition Language documents. 

  You can get started with Adobe Experience Manager easily with just a few steps:

  1. Generate the Service credentials: Use Adobe Experience Manager Developer Console to [generate](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=nl-NL&#generate-service-credentials) the service credentials.  
  
  1. Setup your connection: Add your service credentials to the Adobe Experience Manager Connector. You can get crdential from service credential JSON and copy these credential details to your one-time connection setup:

    * AEM Server
    * Organization ID 
    * Client ID
    * Client Secret
    * Technical Account ID
    * Meta Scopes
    * Private Key - base64 encoded keys are accepted
    * Adobe IMS Host URL

    <br> 
    
    ![Use your Service Credential JSON for credential details](assets/forms-aem-pa-connector-connection.png)

    A sample Service Credential JSON file fields mapped to Adobe Experience Manager connector for Microsoft Power Automate.

    -->
