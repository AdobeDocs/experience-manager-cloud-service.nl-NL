---
Title: Authoring a Form
Description: This article provides information on various form authoring platforms, including the Universal Editor, document-based authoring, and Adaptive Forms editors (Core Components and Foundation Components).
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Adaptive Forms editors, Adaptive Forms editors for Core Components authoring, Adaptive Forms editors for Foundation Components authoring
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# Een formulier ontwerpen

Adobe Experience Manager biedt en ondersteunt meerdere editors voor het schrijven van een formulier. U kunt het volgende gebruiken:
* Universal Editor (voor WYSIWYG-authoring)
* Microsoft Excel- of Google-bladen (ook wel op document gebaseerde authoring genoemd)
* Adaptieve Forms-editors (voor op Core Components of stichting gebaseerde ontwerpfuncties)

**[toe te voegen beeld]**

## Universal Editor (voor WYSIWYG-authoring)

De Universal Editor is een veelzijdige visuele editor die een &#39;what-you-see-is-what-you-get&#39;-functie (WYSIWYG) biedt en zo een intuïtieve manier van maken van formulieren verzekert. Het wordt aanbevolen de Universal Editor te gebruiken bij het maken van nieuwe formulieren, omdat deze een modern, gebruiksvriendelijk ontwerp en een handige interface voor slepen en neerzetten biedt.

Als u formulieren wilt maken met de Universal Editor, worden sjablonen voor Edge Delivery Services gebruikt die beschikbaar zijn in de AEM-omgeving. Deze vormen erven hun blik en voelen van de configuraties in de bewaarplaats van GitHub van Edge Delivery Services. [ Een verbinding tussen uw AEM milieu en de bewaarplaats van Edge Delivery Services GitHub ](/help/edge/docs/forms/publishing-forms.md) wordt gevestigd om het publiceren van deze vormen op Edge Delivery Services toe te laten.

Voor gedetailleerde stappen op hoe te auteur gebruiken de Universele Redacteur, verwijs naar de [ Authoring Inhoud met het Universele artikel van de Redacteur ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring).

## Microsoft Excel- of Google-bladen (ook wel op document gebaseerde authoring genoemd)

U kunt de formulieren ontwerpen door ze op documenten te baseren met Microsoft Excel- of Google Sheets-bestanden, zodat u de robuuste ecosystemen en API&#39;s van Google Sheets, Microsoft Excel en Microsoft SharePoint kunt benutten. Deze aanpak is vooral handig voor het maken van eenvoudige formulieren zonder geavanceerde verzendservices.

Beginnen creërend een vorm gebruikend Microsoft Excel of de Bladen van Google, [ opstelling een AEM project gebruikend AEM Forms boilerplate ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) en kloon de overeenkomstige bewaarplaats GitHub aan uw lokale machine. AEM Forms Edge Delivery biedt de functie Adaptive Forms Block, waarmee het maken van formulieren voor het vastleggen en opslaan van gegevens wordt vereenvoudigd. Leren om vormen tot stand te brengen en te publiceren gebruikend het AanpassingsBlok van Forms op Edge Delivery Services, verwijs naar [ creeer een Vorm ](/help/edge/docs/forms/create-forms.md).

## Adaptieve Forms-editors (voor op Core Components of stichting gebaseerde ontwerpfuncties)

U kunt aantrekkelijke, responsieve en dynamische formulieren maken. De Adaptive Form Editor biedt een gebruiksvriendelijke wizard waarmee u snel Adaptive Forms kunt maken. De formulierwizard biedt eenvoudige tabnavigatie, waarmee u vooraf geconfigureerde sjablonen kunt selecteren voor basis- of kerncomponenten, thema&#39;s, gegevensmodellen en verzendopties om op efficiënte wijze een formulier te maken.

[ Authoring vormen met de Componenten van de Kern ](/help/forms/creating-adaptive-form-core-components.md) staat u toe om gestandaardiseerde gegevens te gebruiken vangen componenten die kunnen worden aangepast, die ontwikkelingstijd verminderen en onderhoudskosten voor digitale inschrijvingservaringen verminderen. Deze formulieren kunnen worden gepubliceerd met het Adaptive Forms Block op Edge Delivery Services of via het AEM Publish-exemplaar.

[ Authoring vormen met de Componenten van de Stichting ](/help/forms/create-an-adaptive-form.md) gebruikt klassieke gegevens vangen componenten. Deze formulieren kunnen alleen worden gepubliceerd met behulp van het AEM Publish-exemplaar.

U kunt vormen ook publiceren die gebruikend de AanpassingsRedacteurs van Forms op Edge Delivery Services worden gecreeerd door [ verbinding tussen uw AEM milieu en de bewaarplaats van GitHub van Edge Delivery Services te vestigen ](/help/edge/docs/forms/publishing-forms.md).

## Hoe te om tussen diverse types vorm creatie te kiezen?

In de volgende tabel worden de functies en gebruiksscenario&#39;s voor elke ontwerpeditor beschreven, zodat u op basis van uw vereisten en vereisten voor het verzenden van formulieren de juiste keuze kunt maken.

| **de Schrijver van de Vorm** | **Zeer belangrijke Benadering** | **Eigenschappen** | **het Publiceren Methode** | **Gevallen van het Gebruik** |
|--------|-----------|-------|-------|------------------------------------------------|
| **op document-gebaseerde Authoring** | Gebruikt vertrouwde tools zoals Google Docs en Microsoft Office voor het maken van formulieren. | Forms is ontworpen met behulp van spreadsheets, met gegevens die rechtstreeks worden verzonden naar Google Sheets of Microsoft Excel-werkbladen. </br> </br> Deze formulieren zijn sneller te maken en te implementeren. U hebt geen voorafgaande kennis van AEM nodig om aangepaste componenten en stijlen voor deze formulieren te ontwikkelen. | Deze formulieren worden gepubliceerd op Edge Delivery Services en hebben een zeer hoge Google Lighthouse score. </br> </br> De hoge score resulteert in snellere rendering en betere SEO. | Deze formulieren zijn ideaal voor snelle prototypen of basisformulieren waarbij geavanceerde verzendservices niet nodig zijn. </br> </br> Deze zijn zeer geschikt voor enquêtes, registratieformulieren of feedbackformulieren die gegevensopslag in spreadsheets vereisen. Deze formulieren worden gepubliceerd op Edge Delivery-services |
| **Universele Redacteur** </br> </br> Als u een nieuw formulier maakt, gebruikt u de Universal Editor om formulieren te maken. | Biedt een WYSIWYG-interface voor het maken van intuïtieve formulieren. | Forms is ontworpen met een intuïtieve interface voor slepen en neerzetten. </br> </br> Deze vormen lenen blik en voelen van gevormde bewaarplaats GitHub van Edge Delivery Services voor de overeenkomstige vorm. | Deze formulieren worden gepubliceerd op Edge Delivery Services en hebben een zeer hoge Google Lighthouse score. </br> </br> De hoge score resulteert in snellere rendering en betere SEO. | Deze formulieren zijn ideaal om formulieren te maken voor Edge Delivery Service-sites en -pagina&#39;s. Deze formulierscenario&#39;s omvatten complexe formulieren, complexe workflows, aangepaste acties of integratie met externe systemen |
| **AanpassingsForms redacteurs** | Biedt een wizardgestuurde aanpak voor het snel starten van het ontwerpen van formulieren met behulp van sjablonen, opmaak en vooraf gedefinieerde velden. | Gebruik deze redacteurs om de op componenten gebaseerde vormen van de Kern te creëren of van de Stichting Componenten gebaseerde vormen. | Deze formulieren kunnen op Edge Delivery Services of via AEM Publish-exemplaren worden gepubliceerd. | Gebruik deze redacteurs om de op componenten gebaseerde vormen van de Kern te creëren of van de Stichting Componenten gebaseerde vormen. Ideaal voor scenario&#39;s met complexe formulieren, complexe workflows, aangepaste acties of integratie met externe systemen. |


>[!NOTE]
>
>
> Als er functies ontbreken in de Universal Editor die voorheen beschikbaar waren in de Adaptive Forms Editor, kunt u deze aanvragen via e-mail naar mailto:aem-forms-ea@adobe.com via uw officiële e-mailadres.

## Verwant artikel

* [Op documenten gebaseerde authoring met Microsoft Excel of Google Sheets](/help/edge/docs/forms/create-forms.md)
* [ Universele Redacteur voor het auteursrecht van WYSIWYG ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [Een adaptief formulier maken (basiscomponenten)](/help/forms/creating-adaptive-form.md)
* [Een adaptief formulier maken (kerncomponenten)](/help/forms/create-an-adaptive-form.md)

## Zie ook

{{see-more-forms-eds}}