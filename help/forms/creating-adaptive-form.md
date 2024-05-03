---
title: Hoe maak je Adaptive Forms?
description: Leer een adaptief formulier te maken om het verzamelen en verwerken van informatie te stroomlijnen. Leer ook Adaptief formulier maken op basis van een FDM (Form Data Model).
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '1457'
ht-degree: 0%

---

# Een adaptief formulier maken (basiscomponenten) {#creating-an-adaptive-form}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html) |
| AEM as a Cloud Service | Dit artikel |


<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

Met Adaptive Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke wizard die Adaptive Forms snel ontwikkelt. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en) zijn gestandaardiseerde componenten voor het vastleggen van gegevens. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe beveelt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [Aangepaste Forms Foundation-componenten](creating-adaptive-form.md) zijn klassieke (oude) componenten voor gegevensvastlegging. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u nieuwe formulieren maakt, wordt u door de Adobe aanbevolen  [Adaptieve Forms Core-componenten](creating-adaptive-form-core-components.md) om een Adaptieve Forms te maken.



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
   XML and JSON schemas represent the structure in which data is produced or consumed by the back-end system in your organization. You can associate the schema to an Adaptive Form and use its elements to add dynamic content to the Adaptive Form. The elements of the schema are available for use in the Data Model Objects tab of the Content browser when authoring Adaptive Forms.

* **Using none or without a form model**
   Adaptive Forms created with this option do not use any form model. The data XML generated from such forms has flat structure with fields and corresponding values. -->

## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* **Machtigingen**: Voeg uw gebruikers toe aan [!DNL forms-users] om hun machtigingen te verlenen voor het maken van een adaptief formulier. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

* **Een adaptief formulierthema**: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. U kunt [een thema maken](themes.md) of [een bestaand thema importeren](import-export-forms-templates.md#uploading-a-theme). U kunt ook de [nieuwste archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html#create-project) voor sommige voorbeeldthema&#39;s.

* **Een adaptieve formuliersjabloon**: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice ondersteunt twee typen sjablonen:

   * **Bewerkbare sjabloon**: U kunt [een](template-editor.md) of [een bestaande bewerkbare sjabloon importeren](migrate-to-forms-as-a-cloud-service.md). U kunt ook de [nieuwste archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.) om een aantal voorbeelden bewerkbare sjablonen te verkrijgen.

   * **Statische sjabloon**: Dit zijn verouderde sjablonen en worden alleen aanbevolen voor klanten die migreren uit Adobe Managed Services (AMS) en AEM Forms-installaties op locatie (AEM 6.5 Forms of eerder). Deze laten u uw bestaande investering in statische malplaatjes blijven gebruiken. Wanneer u een adaptief formulier maakt, gebruikt u een bewerkbare sjabloon.



## Een adaptief formulier maken (basiscomponenten) {#create-an-adaptive-form-foundation-components}

1. Toegang [!DNL Experience Manager Forms] Auteur-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in.

   Nadat u bent aangemeld, selecteert u in de linkerbovenhoek de optie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Selecteren **[!UICONTROL Create]**  > **[!UICONTROL Adaptive Forms]**. De wizard wordt geopend.
1. Selecteer een sjabloon op het tabblad Bron:

   * Wanneer u een bewerkbare sjabloon selecteert, wordt de actie voor het thema en het verzenden die in de sjabloon is opgegeven automatisch geselecteerd en wordt de opdracht **[!UICONTROL Create]** wordt ingeschakeld. Je kunt naar de **[!UICONTROL Style]** of **[!UICONTROL Submission]** tabs om een ander thema te selecteren of actie te verzenden. Als de geselecteerde bewerkbare sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. Je kunt naar de **[!UICONTROL Styles]** om handmatig een thema te selecteren.

     >[!NOTE]
     >
     > U kunt ook [!UICONTROL Document of Record] sjabloon met een Adaptieve Forms-editor. Zie voor meer informatie [Document met ondersteuning voor records in de Adaptive Form Editor](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

   * Wanneer u een statische sjabloon selecteert, zijn de opties voor gegevens, stijl, verzending, levering en voorvertoning niet beschikbaar. Wanneer u een adaptief formulier maakt, gebruikt u een bewerkbare sjabloon.

1. In de **[!UICONTROL Style]** selecteert u een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.
   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De **[!UICONTROL Create]** De knop wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) In het dialoogvenster **[!UICONTROL Data]** selecteert u een gegevensmodel:

   * **Formuliergegevensmodel**: A [Formuliergegevensmodel](data-integration.md) Hiermee kunt u entiteiten en services integreren van verschillende gegevensbronnen tot een adaptief formulier. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

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
>You can also change the schema for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model). -->

## Eigenschappen van formuliermodellen bewerken in een adaptief formulier {#edit-form-model}

U kunt het formuliermodel wijzigen voor een adaptief formulier (op JSON gebaseerd of Formuliergegevensmodel). U kunt niet van het ene formuliermodel naar het andere gaan.

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

![FDM-Schema-Support](/help/forms/assets/fdmsupport.png)

>[!NOTE]
>
> U kunt een positief formulier ook als een sjabloon opslaan. Zie voor meer informatie [Een sjabloon maken met een adaptief formulier](/help/forms/template-editor.md#saving-an-adaptive-form-as-template-saving-adaptive-form-as-template).


## Zie ook {#see-also}

{{see-also}}