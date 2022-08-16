---
title: Hoe maakt u een adaptief formulier?
description: 'Leer hoe u een adaptief formulier maakt met [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op het maken van een adaptief formulier op basis van een formuliergegevensmodel en een XML- of JSON-schema. '
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: b29d11550ee8b7671059a1f04de37c7b79658a60
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 0%

---

# Een adaptief formulier maken {#creating-an-adaptive-form}


Met Adaptieve Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke wizard die Adaptive Forms snel ontwikkelt. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

<!-- 

You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form: 

-->

![Wizard voor het maken van een adaptief formulier](/help/release-notes/assets/wizard.png)

<!-- 

Adaptive Forms allow you to create forms that are engaging, responsive, dynamic, and adaptive. [!DNL AEM Forms] provides an intuitive wizard and out-of-the-box components to create Adaptive Forms. You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form:

* **Using a form data model**
  [Data integration](data-integration.md) lets you integrate entities and services from disparate data sources in to a Form Data Model that you can use to create Adaptive Forms. Choose Form Data Model if the Adaptive Form you are creating involves fetching and write data from and to multiple data source.

  <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. 

* **Using an XML Schema Definition (XSD) or a JSON Schema**
   XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate the schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema will be available for use in the Data Model Objects tab of the Content browser when authoring Adaptive Forms.

* **Using none or without a form model**
   Adaptive Forms created with this option don’t use any form model. The data XML generated from such forms has flat structure with fields and corresponding values. -->

## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* Een adaptieve formuliersjabloon: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. Het thema definieert de actie look and feel and submit voor het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. U kunt [een nieuwe sjabloon maken](template-editor.md) of importeer een bestaande sjabloon. U kunt ook de [nieuwste archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.) voor sommige voorbeeldsjablonen.
* Een adaptief formulierthema: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. U kunt [een nieuw thema maken](themes.md), [een bestaand thema importeren](import-export-forms-templates.md#uploading-a-theme)of download en importeer enkele [voorbeeldthema&#39;s](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:2779f80e-16ba-4cd1-a96f-8e2b53f3be25). U kunt ook de [nieuwste archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.) voor sommige voorbeeldthema&#39;s.
* Gebruikers toevoegen aan [!DNL forms-users] om hun machtigingen te verlenen voor het maken van een adaptief formulier. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

## Een adaptief formulier maken {#strong-create-an-adaptive-form-strong}

Ga als volgt te werk om een adaptief formulier te maken.

1. Toegang [!DNL Experience Manager Forms] Instantie van auteur. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in.

   Tik in de linkerbovenhoek nadat u bent aangemeld op **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Tik op **[!UICONTROL Create]**  > **[!UICONTROL Adaptive Forms]**. De wizard wordt geopend.
1. Selecteer een sjabloon op het tabblad Bron:
   * Wanneer u een sjabloon selecteert, wordt de in de sjabloon opgegeven actie voor het thema en het verzenden automatisch geselecteerd en wordt de knop Maken ingeschakeld. U kunt naar de tabbladen Stijl of Verzending gaan om een ander thema of een andere handeling Verzenden te selecteren.
   * Als de geselecteerde sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. U kunt naar het tabblad Stijlen gaan om handmatig een thema te selecteren.
1. Selecteer een thema op het tabblad Stijl:
   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt een ander thema kiezen op het tabblad Stijl.
   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De knop Maken wordt ingeschakeld nadat een thema is geselecteerd.
1. (Optioneel) Selecteer op het tabblad Gegevens een gegevensmodel:
   * Formuliergegevensmodel: A [Formuliergegevensmodel](data-integration.md) Hiermee kunt u entiteiten en services integreren van verschillende gegevensbronnen tot een adaptief formulier. Kies Formuliergegevensmodel als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.
   * JSON-schema: JSON-schema&#39;s vertegenwoordigen de structuur waarin gegevens worden geproduceerd of verbruikt door het back-end systeem in uw organisatie. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de inhoudbrowser wanneer u Adaptief Forms ontwerpt. Alle velden worden ook toegevoegd aan het nieuwe adaptieve formulier.
1. Selecteer op het tabblad Verzending een handeling Verzenden:
   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere handeling Verzenden selecteren op het tabblad Verzending. Op het tabblad Verzending worden alle beschikbare verzendacties weergegeven.
   * Als de geselecteerde sjabloon geen handeling Verzenden opgeeft, kunt u op het tabblad Verzending een handeling Verzenden selecteren

1. (Optioneel) Op het tabblad Aflevering kunt u een datum voor publicatie of publicatie opgeven voor een adaptief formulier.

1. Tik op Maken. Er wordt een dialoogvenster weergegeven waarin u de titel, de naam en de locatie kunt opgeven waar u het aangepaste formulier wilt opslaan:

   * **[!UICONTROL Title:]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in het dialoogvenster [!DNL Experience Manager Forms] gebruikersinterface.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hier geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het aangepaste formulier rechtstreeks opslaan op `/content/dam/formsanddocuments` of maak een map, zoals `/content/dam/formsanddocuments/adaptiveforms` om een adaptief formulier op te slaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. In het veld Pad wordt niet automatisch een map gemaakt.

1. Tik op **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen aan de behoeften.

   Op basis van het type adaptief formulier worden de formulierelementen in het bijbehorende formulier <!--XFA form template, XML schema or --> Het JSON-schema of het formuliergegevensmodel worden weergegeven in het **[!UICONTROL Data Model Objects]** tabblad van het dialoogvenster **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

<!-- ## Create an Adaptive Form based on a Form Data Model {#fdm}

[Data integration](data-integration.md) lets you integrate multiple data sources and bring their entities and services together to create a form data model. It is an extension of JSON schema. You can use a Form Data Model to create an Adaptive Form. The entities or data model objects configured in a Form Data Model are available as data model objects for form authoring. They are bound to respective data sources and used to prefill a form and write submitted data back to the respective data sources. You can also call services configured in a Form Data Model using Adaptive Form rules.

To use a Form Data Model for creating an Adaptive Form:

1. In Form Model tab on Add Properties screen, select **[!UICONTROL Form Data Model]** in the **[!UICONTROL Select From]** drop-down list.

   ![Create an Adaptive Form](assets/create-af-1-1.png)

1. Tap to expand **[!UICONTROL Select Form Data Model]**. All available form data models are listed.Select a from data model.

>[!NOTE]
>
>You can also change the Form Data Model for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model).

## Create an Adaptive Form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate a schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available in the Data Model Object tab of the content browser for authoring Adaptive Forms. You can drag-drop the schema elements to build the form.

See the following documents to understand how to design XML or JSON schema for authoring Adaptive Forms.

* [Creating Adaptive Forms using XML schema](adaptive-form-xml-schema-form-model.md)
* [Creating Adaptive Forms using JSON schema](adaptive-form-json-schema-form-model.md)

Do the following to use XML or JSON schema as form model for an Adaptive Form:

1. On the **[!UICONTROL Add Properties]** step of Adaptive Form creation page, tap on the **[!UICONTROL Form Model]** tab.
1. In the Form Model tab, select **[!UICONTROL Schema]** from the **[!UICONTROL Select From]** drop-down field.

1. Tap **[!UICONTROL Select Schema]** and do one of the following:

    * **[!UICONTROL Upload from disk]** - Select this option and tap Upload Schema Definition to browse and upload an XML schema or JSON schema from your file system. The uploaded schema file resides with the form and is not accessible to other Adaptive Forms.
    * **[!UICONTROL Search in repository]** - Select this option to select from the list of schema definition files available in the repository. Select the XML or JSON schema file as form model. The selected schema is associated with the form by reference and is accessible for use in other Adaptive Forms.

      Ensure that the JSON schema filename ends with **.schema.json**. For example: mySchema.schema.json

   ![Selecting XML or JSON schema](assets/upload-schema.png)
**Figure:** *Selecting XML or JSON schema*

1. (For XML schema only) After you select or upload an XML Schema, specify a root element of the selected XSD file to map with the Adaptive Form.

   ![Selecting XSD root element](assets/xsd-root-element.png)
**Figure:** *Selecting XSD root element*

>[!NOTE]
>
>You can also change the schema for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model). -->

## Eigenschappen van een formuliermodel bewerken in een adaptief formulier {#edit-form-model}

U kunt het formuliermodel wijzigen voor een adaptief formulier (op JSON gebaseerd of Formuliergegevensmodel). U kunt niet van het ene formuliermodel naar het andere gaan.

1. Selecteer het adaptieve formulier en tik op de knop **Eigenschappen** pictogram.
1. Open de **[!UICONTROL Form Model]** en voert u een van de volgende handelingen uit.

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een ander formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of formuliergegevensmodel.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u een ander formulier kiezen <!-- form template, --> XML- of JSON-schema of Formuliergegevensmodel voor hetzelfde formuliermodel.

1. Tikken **[!UICONTROL Save]** om de eigenschappen op te slaan.
