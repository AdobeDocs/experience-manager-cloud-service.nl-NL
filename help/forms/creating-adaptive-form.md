---
title: 'Formulierontwikkelaar: formulieren maken met basiscomponenten'
description: Leer hoe u AEM Forms-formulierbuilder kunt gebruiken om adaptieve formulieren met stichtingscomponenten te maken. Ideaal voor ontwerpers van formulieren die bestaande formulieren onderhouden of werken met verouderde integratie.
keywords: formulierontwerper, basiscomponenten, formulieren maken, formuliermaken, adaptieve formulieren, formulieren bouwen, AEM-formulieren, formuliermaker
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# Formulierontwikkelaar: formulieren maken met basiscomponenten {#creating-an-adaptive-form}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |


>[!NOTE]
>
> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/creating-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

Met de formulierbuilder van AEM Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. Of u nu een formulierontwerper bent die bestaande op basis van grondslagen gemaakte formulieren beheert of snel formulieren moet maken met bestaande componenten, AEM Forms biedt een gebruiksvriendelijke wizard. De tovenaar heeft snelle lusjenavigatie om pre-gevormde malplaatjes, het stileren, gebieden, en voorlegging opties gemakkelijk te selecteren.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [&#x200B; de Aangepaste Componenten van de Kern van Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) zijn gestandaardiseerde gegevens vangen componenten. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe raadt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [&#x200B; de Aangepaste Componenten van de Stichting van Forms &#x200B;](creating-adaptive-form.md) zijn klassieke (oude) gegevens vangen componenten. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u nieuwe vormen creeert, adviseert Adobe gebruikend [&#x200B; Aangepaste Componenten van de Kern van Forms &#x200B;](creating-adaptive-form-core-components.md) om een Aangepaste Forms tot stand te brengen.



<!-- 

You can choose to create an Adaptive Form based on a form model or schema or without a form model. It is important to carefully choose the form model that not only suits your requirements but extends your existing infrastructural investments and assets. You get to choose from the following options to create an Adaptive Form: 

-->

![&#x200B; Tovenaar om een Aangepaste Vorm &#x200B;](/help/release-notes/assets/wizard.png) tot stand te brengen

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

* **Toestemmingen**: Voeg uw gebruikers aan [!DNL forms-users] toe om hen toestemmingen te verstrekken om een Aangepaste Vorm tot stand te brengen. Voor gedetailleerde lijst van vormen specifieke gebruikersgroepen, zie [&#x200B; Groepen en toestemmingen &#x200B;](forms-groups-privileges-tasks.md).

* **een Adaptief thema van de Vorm**: Een thema bevat het stileren details voor de componenten en de panelen. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. U kunt [&#x200B; tot een thema &#x200B;](themes.md) leiden of [&#x200B; een bestaand thema &#x200B;](import-export-forms-templates.md#uploading-a-theme) invoeren. U kunt [&#x200B; recentste archetype &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=nl-NL#create-project) voor sommige steekproefthema&#39;s ook opstellen.

* **een Adaptief malplaatje van de Vorm**: Een malplaatje verstrekt een basisstructuur en bepaalt verschijning (lay-outs en stijlen) van een Aangepast Vorm. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice ondersteunt twee typen sjablonen:

   * **Bewerkbaar malplaatje**: U kunt [&#x200B; a &#x200B;](template-editor.md) creëren of [&#x200B; een bestaand editable malplaatje &#x200B;](migrate-to-forms-as-a-cloud-service.md) invoeren. U kunt [&#x200B; recentste archetype &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=nl-NL#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.) ook opstellen om sommige steekproef editable malplaatjes te krijgen.

   * **Statisch malplaatje**: Dit zijn erfenismalplaatjes en worden geadviseerd slechts voor klanten die van Adobe Managed Services (AMS) en op-gebouwAEM Forms installaties (AEM 6.5 Forms of vroeger) migreren. Deze laten u uw bestaande investering in statische malplaatjes blijven gebruiken. Wanneer u een adaptief formulier maakt, gebruikt u een bewerkbare sjabloon.



## Een adaptief formulier maken (basiscomponenten) {#create-an-adaptive-form-foundation-components}

1. Open [!DNL Experience Manager Forms] Author-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Voer uw referenties in op de Experience Manager-aanmeldingspagina.

   Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend.
1. Selecteer op het tabblad Source een sjabloon:

   * Wanneer u een bewerkbare sjabloon selecteert, wordt de in de sjabloon opgegeven actie voor het thema en het verzenden automatisch geselecteerd en wordt de knop **[!UICONTROL Create]** ingeschakeld. U kunt naar de tabbladen **[!UICONTROL Style]** of **[!UICONTROL Submission]** gaan om een ander thema te selecteren of een actie te verzenden. Als de geselecteerde bewerkbare sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. U kunt naar het tabblad **[!UICONTROL Styles]** gaan om handmatig een thema te selecteren.

     >[!NOTE]
     >
     > U kunt ook een [!UICONTROL Document of Record] -sjabloon maken met een Adaptieve Forms-editor. Voor meer informatie, zie [&#x200B; Document van de Steun van het Verslag in de Adaptieve Redacteur van de Vorm &#x200B;](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

   * Wanneer u een statische sjabloon selecteert, zijn de opties voor gegevens, stijl, verzending, levering en voorvertoning niet beschikbaar. Wanneer u een adaptief formulier maakt, gebruikt u een bewerkbare sjabloon.

1. Selecteer op het tabblad **[!UICONTROL Style]** een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.
   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De knop **[!UICONTROL Create]** wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) Selecteer op het tabblad **[!UICONTROL Data]** een gegevensmodel:

   * **het gegevensmodel van de Vorm**: Het Model van de Gegevens van de Vorm van A [&#128279;](data-integration.md) laat u entiteiten en de diensten van ongelijksoortige gegevensbronnen aan een Aangepaste Vorm integreren. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [&#x200B; JSON schema &#x200B;](adaptive-form-json-schema-form-model.md) vertegenwoordigt de structuur waarin het gegeven wordt geproduceerd of door het achterste deelsysteem in uw organisatie verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de inhoudbrowser wanneer u Adaptief Forms ontwerpt. Alle velden worden ook toegevoegd aan het gemaakte adaptieve formulier.

   Standaard zijn alle velden van het gegevensmodel geselecteerd. Wanneer u het adaptieve formulier maakt, worden alle geselecteerde gegevensmodelvelden geconverteerd naar de overeenkomstige adaptieve formuliercomponenten. De wizard verschaft u selectievakjes om alleen de velden te selecteren die moeten worden opgenomen in het adaptieve formulier.

   <!-- 
   
   If your JSON schema contains a fragment, the fragment is considered a single unit. You can select or deselect a complete fragment and all the fields of the fragment are selected or deselected accordingly. 
   
   -->

1. Selecteer op het tabblad **[!UICONTROL Submission]** een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. Op het tabblad **[!UICONTROL &#x200B; Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   * Wanneer de geselecteerde sjabloon geen verzendactie opgeeft, kunt u op het tabblad **[!UICONTROL Submission]** een verzendactie selecteren

1. (Optioneel) Op het tabblad Aflevering kunt u een datum voor publicatie of publicatie opgeven voor een adaptief formulier.

1. Selecteer **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven:

   * **[!UICONTROL Title]** Hiermee geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in de gebruikersinterface van [!DNL Experience Manager Forms] .
   * **[!UICONTROL Name:]** Hiermee geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hiermee geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het adaptieve formulier rechtstreeks opslaan in `/content/dam/formsanddocuments` of een map maken, zoals `/content/dam/formsanddocuments/adaptiveforms` , om een adaptief formulier op te slaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. In het veld **[!UICONTROL Path:]** wordt niet automatisch een map gemaakt.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje. De zijbalk wordt ook weergegeven om het gemaakte formulier aan te passen aan de behoeften.

   Op basis van het type adaptief formulier worden de formulierelementen in het gekoppelde <!--XFA form template, XML schema or --> JSON-schema of FDM (Form Data Model) weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van het **[!UICONTROL Content Browser]** in het zijpaneel. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

<!-- ## Create an Adaptive Form based on a Form Data Model {#fdm}

[Data integration](data-integration.md) lets you integrate multiple data sources and bring their entities and services together to create a form data model. It is an extension of JSON schema. You can use a Form Data Model to create an Adaptive Form. The entities or data model objects configured in a Form Data Model are available as data model objects for form authoring. They are bound to respective data sources and used to prefill a form and write submitted data back to the respective data sources. You can also call services configured in a Form Data Model using Adaptive Form rules.

To use a Form Data Model for creating an Adaptive Form:

1. In Form Model tab on Add Properties screen, select **[!UICONTROL Form Data Model]** in the **[!UICONTROL Select From]** drop-down list.

   ![Create an Adaptive Form](assets/create-af-1-1.png)

1. Select to expand **[!UICONTROL Select Form Data Model]**. All available form data models are listed.Select a from data model.

>[!NOTE]
>
>You can also change the Form Data Model for an Adaptive Form. For detailed steps, see [Edit Form Model properties of an Adaptive Form](#edit-form-model).

## Build an adaptive form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

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

## Eigenschappen van formuliermodellen bewerken van een adaptief formulier {#edit-form-model}

U kunt het formuliermodel wijzigen voor een adaptief formulier (op JSON gebaseerd of Formuliergegevensmodel). U kunt niet van het ene formuliermodel naar het andere gaan.

1. Selecteer de Aangepaste Vorm en selecteer het **pictogram van Eigenschappen**.
1. Open het tabblad **[!UICONTROL Form Model]** en voer een van de volgende handelingen uit.

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een ander formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of FDM-formuliergegevensmodel selecteren.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u een ander <!-- form template, --> XML- of JSON-schema of Formuliergegevensmodel (FDM) kiezen voor hetzelfde formuliermodel.

1. Selecteer **[!UICONTROL Save]** om de eigenschappen op te slaan.

U kunt de eigenschappen van het formuliermodel ook wijzigen met de sjabloonconstructor Adaptief formulier of Adaptief formulier.

1. Selecteer de component **[!UICONTROL Adaptive Form container (Root)]** .
1. Klik ![&#x200B; vormen pictogram van het Pictogram &#x200B;](/help/forms/assets/configure-icon.svg) om **[!UICONTROL Properties]** van de Aangepaste container van de Vorm te openen.
1. Selecteer de tab **[!UICONTROL Data Model]** en voer een van de volgende handelingen uit:

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of FDM-formuliergegevensmodel selecteren.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u het formuliermodel niet wijzigen. U kunt een ander <!-- form template, --> XML- of JSON-schema of een FDM-formuliergegevensmodel kiezen voor hetzelfde formuliermodel als van toepassing is.
1. Selecteer ![&#x200B; sparen &#x200B;](/help/forms/assets/check-button.png) om de eigenschappen te bewaren.

![&#x200B; fdm-Schema-Steun &#x200B;](/help/forms/assets/fdmsupport.png)

>[!NOTE]
>
> U kunt een positief formulier ook als een sjabloon opslaan. Voor meer informatie, zie [&#x200B; een malplaatje creëren gebruikend een AanpassingsVorm &#x200B;](/help/forms/template-editor.md#saving-an-adaptive-form-as-template-saving-adaptive-form-as-template).

## Hoe wijzigt u de naam van een AEM-adaptief formulier? {#rename-an-AEM-Adaptive-Form}

Voer de volgende stappen uit om de naam van een adaptief formulier te wijzigen:

1. Selecteer een adaptief formulier in uw AEM Forms-gebruikersinterface.
1. Klik op **Eigenschappen** die op de hogere spoorstaaf wordt gevestigd.
1. Verander de naam van de vorm op het **lusje van de Titel**, zoals aangetoond in het hieronder beeld.
1. Klik **sparen en Sluiten**.

![&#x200B; noem een Aangepaste Vorm van AEM &#x200B;](/help/forms/assets/change-af-name.png) anders

## Zie ook {#see-also}

{{see-also}}
