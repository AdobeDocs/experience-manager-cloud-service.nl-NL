---
Title: How Edge Delivery Services Forms work?
Description: This article provides information on how Edge Delivery Services Forms work. It also provides information on various form authoring platforms, including the Universal Editor and document-based authoring.
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Working of Edge Delivery Services Forms, How Edge Delivery Services Forms work?
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
exl-id: db58ce85-139a-4cc1-8e18-73da76357299
source-git-commit: bb01a76ae2bfd78ae648e91545f34f20fabebd10
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---


# Edge Delivery Services Forms

Adobe Edge Delivery Services Forms transformeert de manier waarop formulieren worden gemaakt, uitgevoerd en verwerkt. Door gebruik te maken van Edge Delivery Services kunnen organisaties snelle, veilige en hoogst beschikbare digitale formulieren maken, waardoor de gebruikerservaring en de operationele efficiëntie worden verbeterd in een snelle ontwikkelomgeving. Met Edge Delivery Services Forms kunt u conversies stimuleren, kosten verlagen en de levering van inhoud versnellen.

## Voordelen van Edge Delivery Services Forms

* **Snellere creatie van de Vorm**: Bouw krachtige vormen met een perfecte Score van de Lithouse en onophoudelijk hun prestaties in de praktijk gebruikend de Echte Controle van de Gebruiker (RUM).

* **Gestroomlijnd het Authoring Proces**: Beheer gemakkelijk inhoud uit veelvoudige bronnen voor grotere flexibiliteit. U kunt formulieren maken in het tekstvak, zowel met WYSIWYG als door documenten, zodat verschillende indelingen naadloos kunnen worden geïntegreerd.

* **Gemak van Gebruik voor Niet-Technische Gebruikers**: Edge Delivery Services machtigt niet-programmeurs om vormen gemakkelijk te beheren en te publiceren zonder uitgebreide programmeringskennis te vereisen.

* **Verbeterde Ervaring van de Gebruiker**: Verzeker snelle ladingstijden en vlotte interactie, die gebruikers van minimale wachttijden en een intuïtieve vorm-vullende ervaring voorzien.

* **Serverless Uitvoering**: Edge Delivery Services laat serverloze uitvoering van vormlogica toe. Dit omvat:

   * **Cliënt-zijBevestiging**: De gebiedsbevestiging van de vorm komt bij de cliëntkant voor, verminderend round-trip vertragingen.

   * **pre-fill &amp; Personalization**: De gegevens van de vorm pre-vullen worden behandeld bij de cliëntkant voor een naadloze gebruikerservaring.

   * **Verwerking van de Verzending**: De voorlegging van de vorm wordt bevestigd en door:sturen veilig zonder centrale server

## Hoe werkt Edge Delivery Services Forms?

Gebruikers kunnen Edge Delivery Services Forms schrijven met behulp van op documenten gebaseerde ontwerpgereedschappen, zoals Google Drive, SharePoint of de Universal Editor (WYSIWYG authoring), terwijl ze de basisopmaak, functionaliteit en componenten gebruiken die beschikbaar zijn in de GitHub-opslagplaats. Als de gegevens eenmaal zijn geschreven, kan Edge Delivery Services Forms gegevens naar elk platform verzenden via de Forms-verzendservice.

![ hoe Edge Delivery Services Forms ](/help/edge/docs/forms/assets/eds-forms-working.png) werkt

### Belangrijke onderdelen van Edge Delivery Services Forms

De belangrijkste onderdelen van Edge Delivery Services Forms zijn:

* **Bewaarplaats GitHub**: De bewaarplaats GitHub dient als boilerplate voor het creëren van Edge Delivery Services Forms. De formulieren maken gebruik van de standaardstijlen en -functionaliteit van de gegevensopslagruimte en stellen gebruikers in staat aanpassingen en aangepaste componenten toe te voegen aan de Edge Delivery Services Forms.

* **Authoring van de Vorm**: Edge Delivery Services Forms steunt twee soorten creatie: WYSIWYG en op document-gebaseerd creatie. Met op documenten gebaseerde ontwerpen kunnen gebruikers formulieren maken met vertrouwde gereedschappen, zoals Google Docs en Microsoft Office. Met WYSIWYG-authoring kunnen gebruikers formulieren visueel ontwerpen met de Universal Editor, waardoor niet-technische gebruikers gemakkelijk formulieren kunnen maken en beheren. De Universal Editor biedt een gebruiksvriendelijke ervaring voor het maken van formulieren en biedt toegang tot een groot aantal formuliermogelijkheden.

* **de Dienst van de Verzending van Forms**: De dienst van de Verzending van Forms staat u toe om gegevens van vormverzendingen op om het even welk platform, zoals OneDrive, SharePoint, of Bladen van Google op te slaan, makend het gemakkelijk om tot vormgegevens binnen uw aangewezen systeem toegang te hebben en te beheren.

## Een formulier ontwerpen

Adobe Experience Manager biedt en ondersteunt meerdere editors voor het schrijven van een formulier. U kunt het volgende gebruiken:
* [Universal Editor (voor WYSIWYG-authoring)](#universal-editor-for-wysiwyg-authoring)
* [Microsoft Excel- of Google-bladen (ook wel op document gebaseerde authoring genoemd)](#microsoft-excel-or-google-sheets-known-as-document-based-authoring)

### Universal Editor (voor WYSIWYG-authoring)

De Universal Editor is een veelzijdige visuele editor die een &#39;what-you-see-is-what-you-get&#39;-functie (WYSIWYG) biedt en zo een intuïtieve manier van maken van formulieren verzekert. Het wordt aanbevolen de Universal Editor te gebruiken bij het maken van nieuwe formulieren, omdat deze een modern, gebruiksvriendelijk ontwerp en een handige interface voor slepen en neerzetten biedt.

Als u formulieren wilt maken met de Universal Editor, worden Edge Delivery Services-sjablonen gebruikt die beschikbaar zijn in de AEM-omgeving. Deze vormen erven hun blik en voelen van de configuraties in de bewaarplaats van Edge Delivery Services GitHub. [ Een verbinding tussen uw milieu van AEM en de bewaarplaats van Edge Delivery Services GitHub ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) wordt gevestigd om het publiceren van deze vormen op Edge Delivery Services toe te laten.

Voor gedetailleerde stappen op hoe te auteur gebruiken de Universele Redacteur, verwijs naar de [ Authoring Inhoud met het Universele artikel van de Redacteur ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring).

### Microsoft Excel- of Google-bladen (ook wel op document gebaseerde authoring genoemd)

U kunt de formulieren ontwerpen door ze op documenten te baseren met Microsoft Excel- of Google Sheets-bestanden, zodat u de robuuste ecosystemen en API&#39;s van Google Sheets, Microsoft Excel en Microsoft SharePoint kunt benutten. Deze aanpak is vooral handig voor het maken van eenvoudige formulieren zonder geavanceerde verzendservices.

Beginnen creërend een vorm gebruikend Microsoft Excel of de Bladen van Google, [ opstelling een project van AEM gebruikend AEM Forms boilerplate ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) en kloon de overeenkomstige bewaarplaats GitHub aan uw lokale machine. AEM Forms Edge Delivery biedt de functie Adaptive Forms Block, waarmee het maken van formulieren voor het vastleggen en opslaan van gegevens wordt vereenvoudigd. Leren om vormen tot stand te brengen en te publiceren gebruikend het AanpassingsBlok van Forms op Edge Delivery Services, verwijs naar [ creeer een Vorm ](/help/edge/docs/forms/create-forms.md).

<!--
## Adaptive Forms editors (for Core Components or foundation components based authoring)

You can author forms that are engaging, responsive and dynamic. The Adaptive Form editor provides a user-friendly wizard that allows you to quickly create Adaptive Forms. The form wizard features easy tab navigation, enabling you to select pre-configured templates for foundation or core components, themes, data models, and submission options to create a form efficiently. 

[Authoring forms with Core Components](/help/forms/creating-adaptive-form-core-components.md) allows you to leverage standardized data capture components that can be customized, reducing development time and lowering maintenance costs for digital enrollment experiences. These forms can be published using the Adaptive Forms Block on Edge Delivery Services or through the AEM Publish instance. 

[Authoring forms with Foundation Components](/help/forms/create-an-adaptive-form.md) uses classic data capture components. These forms can only be published using the AEM Publish instance. 

You can also publish forms created using Adaptive Forms Editors on Edge Delivery Services by establishing [connection between your AEM environment and the Edge Delivery Services GitHub repository](/help/edge/docs/forms/publishing-forms.md).


| **Adaptive Forms editors** | Provides a wizard-driven approach to quickly start forms authoring using templates, styling, and predefined fields. | Use these editors to create Core Components based forms or Foundation Components based forms. | These forms can be published on Edge Delivery Services or via AEM Publish instances.  | Use these editors to create Core Components based forms or Foundation Components based forms. Ideal for scenarios involving complex forms, complex workflows, custom actions, or integrations with external systems. |  



## Types of Publishing for Edge Delivery Services Forms

You can publish Edge Delivery Services Forms on one of the following:

* **Edge Delivery Services Form Submission**: Edge Delivery Services Form Submissions ensure that form interactions, including submission and data processing, are handled efficiently and securely. This enables a faster and more reliable user experience, particularly during high traffic periods. By processing form submissions at the edge, Edge Delivery Services minimizes the reliance on a centralized server.

* **AEM Publish instance**: The AEM Forms server offers a publish instance that manages the forms and related assets available to end users.
-->

### Hoe te om tussen diverse types vorm creatie te kiezen?

In de volgende tabel worden de functies en gebruiksscenario&#39;s voor elke ontwerpeditor beschreven, zodat u op basis van uw vereisten en vereisten voor het verzenden van formulieren de juiste keuze kunt maken.

| **de Schrijver van de Vorm** | **Zeer belangrijke Benadering** | **Eigenschappen** | **het Publiceren Methode** | **Gevallen van het Gebruik** |
|--------|-----------|-------|-------|------------------------------------------------|
| **op document-gebaseerde Authoring** | Gebruikt vertrouwde tools zoals Google Docs en Microsoft Office voor het maken van formulieren. | Forms is ontworpen met behulp van spreadsheets, met gegevens die rechtstreeks worden verzonden naar Google Sheets of Microsoft Excel-werkbladen. </br> </br> Deze formulieren zijn sneller te maken en te implementeren. U hebt geen voorafgaande kennis van AEM nodig om aangepaste componenten en stijlen voor deze formulieren te ontwikkelen. | Deze formulieren worden gepubliceerd op Edge Delivery Services en hebben een zeer hoge score voor Google Lighthouse. </br> </br> De hoge score resulteert in snellere rendering en betere SEO. | Deze formulieren zijn ideaal voor snelle prototypen of basisformulieren waarbij geavanceerde verzendservices niet nodig zijn. </br> </br> Deze zijn zeer geschikt voor enquêtes, registratieformulieren of feedbackformulieren die gegevensopslag in spreadsheets vereisen. Deze formulieren worden gepubliceerd op Edge Delivery-services |
| **Universele Redacteur** </br> </br> Als u een nieuw formulier maakt, gebruikt u de Universal Editor om formulieren te maken. | Biedt een WYSIWYG-interface voor het maken van intuïtieve formulieren. | Forms is ontworpen met een intuïtieve interface voor slepen en neerzetten. </br> </br> Deze formulieren lenen look and feel vanuit de geconfigureerde Edge Delivery Services GitHub-opslagruimte voor het corresponderende formulier. | Deze formulieren worden gepubliceerd op Edge Delivery Services en hebben een zeer hoge score voor Google Lighthouse. </br> </br> De hoge score resulteert in snellere rendering en betere SEO. | Deze formulieren zijn ideaal om formulieren te maken voor Edge Delivery Service-sites en -pagina&#39;s. Deze formulierscenario&#39;s omvatten complexe formulieren, complexe workflows, aangepaste acties of integratie met externe systemen |

>[!NOTE]
>
>
> Als er functies ontbreken in de Universal Editor die voorheen beschikbaar waren in de Adaptive Forms Editor, kunt u deze aanvragen via e-mail naar mailto:aem-forms-ea@adobe.com via uw officiële e-mailadres.

## Zie ook

{{see-more-forms-eds}}
