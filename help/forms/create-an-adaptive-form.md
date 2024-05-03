---
title: Hoe maakt u een adaptief formulier?
description: Leer hoe u Adaptieve Forms met responsieve mobiele apparaten kunt maken met onze stapsgewijze zelfstudie. Deze formulieren worden naadloos aangepast op verschillende apparaten, zodat u een vloeiende ervaring hebt.
keywords: Adaptive Forms, responsieve Forms, HTML5 Forms
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
exl-id: 6f1c3fe7-b61e-47ce-b565-15b4904db092
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '2609'
ht-degree: 0%

---

# Een adaptief formulier maken {#creating-an-adaptive-form}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html) |
| AEM as a Cloud Service | Dit artikel |

Met Adaptive Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke wizard voor zakelijke gebruikers om snel een Adaptive Forms te maken. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

![Wizard voor het maken van een adaptief formulier](/help/release-notes/assets/wizard.png){width="100%" align="center"}

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde componenten voor het vastleggen van gegevens. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. U kunt [https://aemcomponents.dev/](https://aemcomponents.dev/) beschikbare kerncomponenten in actie weergeven **Adobe beveelt aan deze moderne en uitbreidbare componenten te gebruiken voor de ontwikkeling van Adaptive Forms**.

* [Aangepaste Forms Foundation-componenten](creating-adaptive-form.md): Dit zijn klassieke (oude) componenten voor gegevensvastlegging. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u nieuwe formulieren maakt, wordt u door de Adobe aanbevolen  [Adaptieve Forms Core-componenten om een adaptieve Forms te maken](#create-an-adaptive-form-core-components).

>[!BEGINTABS]

>[!TAB Adaptieve Forms maken met kerncomponenten (aanbevolen)]

U hebt het volgende nodig om een adaptief formulier te maken:

* **Adaptieve Forms Core-componenten inschakelen voor uw omgeving**: Wanneer u een programma maakt, zijn de Adaptive Forms Core Components al ingeschakeld voor uw omgeving. Als u een as a Cloud Service Forms-omgeving hebt gebaseerd op Archetype 39 of eerder, [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](enable-adaptive-forms-core-components.md). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon en canvasthema worden toegevoegd aan uw omgeving. Als uw AEM SDK-versie ouder is dan 2023.02.0, [zorg ervoor dat u `prerelease` markering ingeschakeld in uw omgeving](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) omdat Adaptive Forms Core Components deel uitmaakten van de pre-lease vóór de release van 2023.02.0.

* **Een adaptieve formuliersjabloon**: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice biedt een OOTB-sjabloon met de naam blank:

   * De `blank` De sjabloon wordt bij elk nieuw as a Cloud Service AEM Forms-programma geleverd.
   * U kunt het referentiepakket installeren via Package Manager om het `blank` template naar uw as a Cloud Service AEM Forms-programma.
   * U kunt [een adaptieve Forms-sjabloon maken (Core Components)](template-editor.md) helemaal niet.

* **Een adaptief formulierthema**: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  De `Canvas` De sjabloon wordt bij elk nieuw as a Cloud Service AEM Forms-programma geleverd.
  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Machtigingen**: Voeg uw gebruikers toe aan [!DNL forms-users] groep. De leden van de [!DNL forms-users] groep heeft machtigingen om een adaptief formulier te maken. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).


## Een adaptief formulier maken {#create-an-adaptive-form-core-components}

1. Aanmelden bij uw [!DNL Experience Manager Forms] Auteur-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in. Nadat u bent aangemeld, selecteert u in de linkerbovenhoek de optie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Selecteren **[!UICONTROL Create]**  > **[!UICONTROL Adaptive Forms]**. De wizard wordt geopend. Selecteer een sjabloon op het tabblad Bron:

   ![Sjabloon voor kerncomponenten](/help/forms/assets/core-components-template.png){width="100%" align="center"}

   Wanneer u een sjabloon selecteert, wordt de actie voor het thema en het verzenden die in de sjabloon is opgegeven automatisch geselecteerd en wordt de opdracht **[!UICONTROL Create]** wordt ingeschakeld. Je kunt naar de **[!UICONTROL Style]** of **[!UICONTROL Submission]** tabs om een ander thema te selecteren of actie te verzenden. Als de geselecteerde sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. Je kunt naar de **[!UICONTROL Styles]** om handmatig een thema te selecteren.

   >[!NOTE]
   >
   >
   > Als u dat niet doet, **Adaptieve Forms (Core Component)** sjabloon op uw omgeving, [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon wordt toegevoegd aan uw omgeving.

1. In de **[!UICONTROL Style]** selecteert u een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.

   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De **[!UICONTROL Create]** De knop wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) Selecteer op het tabblad Gegevens een gegevensmodel:

   * **Formuliergegevensmodel**: A [Formuliergegevensmodel (FDM)](data-integration.md) Hiermee kunt u entiteiten en services integreren van verschillende gegevensbronnen tot een adaptief formulier. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [JSON-schema](adaptive-form-json-schema-form-model.md) Met ons adaptieve formulier op basis van Core-Components kunt u naadloze integratie tot stand brengen met het back-end systeem van uw organisatie door de mogelijkheid te bieden om een JSON-schema te koppelen, dat de structuur vertegenwoordigt van de gegevens die worden geproduceerd of verbruikt. Met deze koppeling kunnen auteurs dynamisch inhoud toevoegen aan het adaptieve formulier met behulp van de elementen van het schema. De elementen van het schema zijn tijdens het ontwerpproces gemakkelijk toegankelijk op het tabblad Gegevensmodelobjecten van de inhoudbrowser en alle velden worden automatisch toegevoegd aan elk gemaakt adaptief formulier.

   Standaard worden alle velden van het gekoppelde JSON-schema automatisch geselecteerd en geconverteerd naar de overeenkomstige componenten van het adaptieve formulier, waardoor het ontwerpproces wordt gestroomlijnd. De wizard biedt het extra gebruiksgemak waarmee u via selectievakjes kunt kiezen welke velden in het adaptieve formulier moeten worden opgenomen.

1. In de **[!UICONTROL Submission]** selecteert u een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. De **[!UICONTROL  Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   * Als de geselecteerde sjabloon geen verzendactie opgeeft, kunt u de opdracht **[!UICONTROL Submission]** tabblad om een verzendactie te selecteren

1. (Optioneel) In het dialoogvenster **[!UICONTROL Delivery]** kunt u een publicatiedatum of een publicatiedatum opgeven voor een adaptief formulier.

1. Selecteer **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven:

   * **[!UICONTROL Title]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in het dialoogvenster [!DNL Experience Manager Forms] gebruikersinterface.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hier geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het adaptieve formulier rechtstreeks opslaan op `/content/dam/formsanddocuments` of maak een map, zoals `/content/dam/formsanddocuments/adaptiveforms` een adaptief formulier opslaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. De **[!UICONTROL Path]** wordt niet automatisch een map gemaakt.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje.  Op basis van het type adaptief formulier worden de formulierelementen in het bijbehorende formulier <!--XFA form template, XML schema or --> Het JSON-schema of FDM (Form Data Model) worden weergegeven in het dialoogvenster **[!UICONTROL Data Model Objects]** tabblad van het **[!UICONTROL Content Browser]** in de zijbalk.

Nu kunt u de [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#components) of schema-elementen om uw Adaptief formulier te maken.


## Eigenschappen van formuliermodellen bewerken in een adaptief formulier {#edit-form-model-core-components-based-adaptive-forms}

1. Selecteer het adaptieve formulier en selecteer ![Pagina-informatie](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Open Properties]**. De pagina Formuliereigenschappen wordt geopend.

1. Ga naar de **[!UICONTROL Form Model]** en kiest u een formuliermodel. Als het adaptieve formulier geen formuliermodel heeft, hebt u de vrijheid om een JSON-schema of een FDM-formuliergegevensmodel te kiezen. Als het adaptieve formulier echter al is gebaseerd op een formuliermodel, kunt u overschakelen op een ander formuliermodel van hetzelfde type. Als het formulier bijvoorbeeld een JSON-schema gebruikt, kunt u gemakkelijk overschakelen naar een ander JSON-schema. Op dezelfde manier kunt u overschakelen naar een ander FDM-model (Form Data Model) als het formulier een FDM-formulier gebruikt.

1. Selecteren **[!UICONTROL Save]** om de eigenschappen op te slaan.

>[!TAB Aangepaste Forms maken met Foundation-componenten]

U hebt het volgende nodig om een adaptief formulier te maken:

* **Machtigingen**: Voeg uw gebruikers toe aan [!DNL forms-users] om hun machtigingen te verlenen voor het maken van een adaptief formulier. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

* **Een adaptief formulierthema**: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. U kunt [een thema maken](themes.md) of [een bestaand thema importeren](import-export-forms-templates.md#uploading-a-theme). U kunt ook de [nieuwste archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html#create-project) voor sommige voorbeeldthema&#39;s.

* **Een adaptieve formuliersjabloon**: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice ondersteunt twee typen sjablonen:

   * **Bewerkbare sjabloon**: U kunt [een](template-editor.md) of [een bestaande bewerkbare sjabloon importeren](migrate-to-forms-as-a-cloud-service.md). U kunt ook de [nieuwste archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.) om een aantal voorbeelden bewerkbare sjablonen te verkrijgen.

   * **Statische sjabloon**: Dit zijn verouderde sjablonen en worden alleen aanbevolen voor klanten die migreren uit Adobe Managed Services (AMS) en AEM Forms-installaties op locatie (AEM 6.5 Forms of eerder). Deze laten u uw bestaande investering in statische malplaatjes blijven gebruiken. Gebruik een bewerkbare sjabloon wanneer u een adaptief formulier maakt.


## Een adaptief formulier maken {#create-an-adaptive-form-foundation-components}

1. Toegang [!DNL Experience Manager Forms] Auteur-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in.

   Nadat u bent aangemeld, selecteert u in de linkerbovenhoek de optie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Selecteren **[!UICONTROL Create]**  > **[!UICONTROL Adaptive Forms]**. De wizard wordt geopend.
1. Selecteer een sjabloon op het tabblad Bron:

   * Wanneer u een bewerkbare sjabloon selecteert, wordt de actie voor het thema en het verzenden die in de sjabloon is opgegeven automatisch geselecteerd en wordt de opdracht **[!UICONTROL Create]** wordt ingeschakeld. Je kunt naar de **[!UICONTROL Style]** of **[!UICONTROL Submission]** tabs om een ander thema te selecteren of actie te verzenden. Als de geselecteerde bewerkbare sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. Je kunt naar de **[!UICONTROL Styles]** om handmatig een thema te selecteren.

     >[!NOTE]
     >
     > U kunt ook [!UICONTROL Document of Record] sjabloon met een Adaptieve Forms-editor. Zie voor meer informatie [Document met ondersteuning voor records in de Adaptive Form Editor](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

   * Wanneer u een statische sjabloon selecteert, zijn de opties voor gegevens, stijl, verzending, levering en voorvertoning niet beschikbaar. Als u een adaptief formulier maakt, is het raadzaam een bewerkbare sjabloon te gebruiken.

1. In de **[!UICONTROL Style]** selecteert u een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.
   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De **[!UICONTROL Create]** De knop wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) In het dialoogvenster **[!UICONTROL Data]** selecteert u een gegevensmodel:

   * **Formuliergegevensmodel**: A [Formuliergegevensmodel (FDM)](data-integration.md) Hiermee kunt u entiteiten en services integreren van verschillende gegevensbronnen tot een adaptief formulier. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [JSON-schema](adaptive-form-json-schema-form-model.md) vertegenwoordigt de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de inhoudbrowser wanneer u Adaptief Forms ontwerpt. Alle velden worden ook toegevoegd aan het gemaakte adaptieve formulier.

   Standaard zijn alle velden van het gegevensmodel geselecteerd. Wanneer u het adaptieve formulier maakt, worden alle geselecteerde gegevensmodelvelden geconverteerd naar de overeenkomstige adaptieve formuliercomponenten. De wizard verschaft u selectievakjes om alleen de velden te selecteren die moeten worden opgenomen in het adaptieve formulier.

   <!-- 
   
   If your JSON schema contains a fragment, the fragment is considered a single unit. You can select or deselect a complete fragment and all the fields of the fragment are selected or deselected accordingly. 
   
   -->

1. In de **[!UICONTROL Submission]** selecteert u een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. De **[!UICONTROL  Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   * Als de geselecteerde sjabloon geen verzendactie opgeeft, kunt u de opdracht **[!UICONTROL Submission]** tabblad om een verzendactie te selecteren

1. (Optioneel) Op het tabblad Aflevering kunt u een datum voor publicatie of publicatie opgeven voor een adaptief formulier.

1. Selecteer **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven:

   * **[!UICONTROL Title]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in het dialoogvenster [!DNL Experience Manager Forms] gebruikersinterface.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hier geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het adaptieve formulier rechtstreeks opslaan op `/content/dam/formsanddocuments` of maak een map, zoals `/content/dam/formsanddocuments/adaptiveforms` een adaptief formulier opslaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. De **[!UICONTROL Path:]** wordt niet automatisch een map gemaakt.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje. De zijbalk wordt ook weergegeven om het gemaakte formulier aan te passen aan de behoeften.

   Op basis van het type adaptief formulier worden de formulierelementen in het bijbehorende formulier <!--XFA form template, XML schema or --> Het JSON-schema of FDM (Form Data Model) worden weergegeven in het dialoogvenster **[!UICONTROL Data Model Objects]** tabblad van het **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

<!-- ## Create an Adaptive Form based on a Form Data Model {#fdm}

[Data integration](data-integration.md) lets you integrate multiple data sources and bring their entities and services together to create a form data model. It is an extension of JSON schema. You can use a Form Data Model to create an Adaptive Form. The entities or data model objects configured in a Form Data Model are available as data model objects for form authoring. They are bound to respective data sources and used to prefill a form and write submitted data back to the respective data sources. You can also call services configured in a Form Data Model using Adaptive Form rules.

To use a Form Data Model for creating an Adaptive Form:

1. In Form Model tab on Add Properties screen, select **[!UICONTROL Form Data Model]** in the **[!UICONTROL Select From]** drop-down list.

   ![Create an Adaptive Form](assets/create-af-1-1.png)

1. Select to expand **[!UICONTROL Select Form Data Model]**. All available form data models are listed.Select a from data model.

>[!NOTE]
>
>You can also change the Form Data Model for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model).

## Create an Adaptive Form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate a schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available in the Data Model Object tab of the content browser for authoring Adaptive Forms. You can drag-drop the schema elements to build the form.

See the following documents to understand how to design XML or JSON schema for authoring Adaptive Forms.

* [Creating Adaptive Forms using XML schema](adaptive-form-xml-schema-form-model.md)
* [Creating Adaptive Forms using JSON schema](adaptive-form-json-schema-form-model.md)

Do the following to use XML or JSON schema as form model for an Adaptive Form:

1. On the **[!UICONTROL Add Properties]** step of Adaptive Form creation page, select on the **[!UICONTROL Form Model]** tab.
1. In the Form Model tab, select **[!UICONTROL Schema]** from the **[!UICONTROL Select From]** drop-down field.

1. Select **[!UICONTROL Select Schema]** and do one of the following:

    * **[!UICONTROL Upload from disk]** - Select this option and select Upload Schema Definition to browse and upload an XML schema or JSON schema from your file system. The uploaded schema file resides with the form and is not accessible to other Adaptive Forms.
    * **[!UICONTROL Search in repository]** - Select this option to select from the list of schema definition files available in the repository. Select the XML or JSON schema file as form model. The selected schema is associated with the form by reference and is accessible for use in other Adaptive Forms.

      Ensure that the JSON schema filename ends with **.schema.json**. For example: mySchema.schema.json

   ![Selecting XML or JSON schema](assets/upload-schema.png)
**Figure:** *Selecting XML or JSON schema*

1. (For XML schema only) After you select or upload an XML Schema, specify a root element of the selected XSD file to map with the Adaptive Form.

   ![Selecting XSD root element](assets/xsd-root-element.png)
**Figure:** *Selecting XSD root element*

>[!NOTE]
>
>You can also change the schema for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model2). -->

## Eigenschappen van formuliermodellen bewerken in een adaptief formulier {#edit-form-model-foundation-components}

U kunt het formuliermodel wijzigen voor een adaptief formulier (JSON-gebaseerd of Form Data Model (FDM)). U kunt niet van het ene formuliermodel naar het andere gaan.

1. Selecteer het adaptieve formulier en selecteer de optie **Eigenschappen** pictogram.
1. Open de **[!UICONTROL Form Model]** en voert u een van de volgende handelingen uit.

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een ander formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of FDM (Form Data Model).
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u een ander formulier kiezen <!-- form template, --> XML- of JSON-schema of FDM (Form Data Model) voor hetzelfde formuliermodel.

1. Selecteren **[!UICONTROL Save]** om de eigenschappen op te slaan.

U kunt ook de eigenschappen van het formuliermodel wijzigen in de editor voor adaptieve formulieren of de sjablooneditor voor adaptieve formulieren.

1. Selecteer de **[!UICONTROL Adaptive Form container (Root)]** component.
1. Klikken ![Pictogram configureren](/help/forms/assets/configure-icon.svg) pictogram om het **[!UICONTROL Properties]** van de container Adaptief formulier.
1. Selecteer de **[!UICONTROL Data Model]** en voert u een van de volgende handelingen uit:

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of FDM (Form Data Model).
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u het formuliermodel niet wijzigen. U kunt een andere optie kiezen <!-- form template, --> XML- of JSON-schema of FDM (Form Data Model) voor hetzelfde formuliermodel als van toepassing.
1. Selecteren ![Opslaan](/help/forms/assets/check-button.png) om de eigenschappen op te slaan.

![FDM-Schema-Support](/help/forms/assets/fdmsupport.png){width="100%" align="center"}

>[!NOTE]
>
> U kunt een adaptief formulier ook opslaan als een sjabloon. Zie voor meer informatie [Een sjabloon maken met een adaptief formulier](/help/forms/template-editor.md#saving-an-adaptive-form-as-template-saving-adaptive-form-as-template).

>[!ENDTABS]


## Volgende stappen

* [Adobe Sign gebruiken met Forms](working-with-adobe-sign.md)
* [Google reCaptcha gebruiken in combinatie met Forms](captcha-adaptive-forms.md)
* [Herhaalbare sectie toevoegen aan een formulier](create-forms-repeatable-sections.md)
* [Velden van een formulier vooraf invullen](prepopulate-adaptive-form-fields.md)

>[!MORELIKETHIS]
>
>* [Een adaptief formulier maken](/help/forms/creating-adaptive-form-core-components.md)
