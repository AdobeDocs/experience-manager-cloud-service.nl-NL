---
title: Hoe maakt u een adaptief formulier?
description: Leer hoe u met de formulierbuilder van AEM Forms adaptieve formulieren maakt die reageren op mobiele apparaten. Ideaal voor ontwerpers en ontwikkelaars van formulieren die formulieren nodig hebben die zich naadloos aanpassen op verschillende apparaten.
keywords: formulierontwerper, formulierontwerper, formulieren maken, formuliermaker, adaptieve formulieren, responsieve formulieren, HTML5-formulieren, formulieren bouwen, AEM-formulieren
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
exl-id: 6f1c3fe7-b61e-47ce-b565-15b4904db092
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '2625'
ht-degree: 0%

---

# Aan de slag-handleiding voor formulierbuilder {#creating-an-adaptive-form}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html) |
| AEM as a Cloud Service | Dit artikel |

Met de formulierbuilder van AEM Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. Of u nu een maker van formulieren bent die professionele formulieren maakt of snel responsieve formulieren moet maken, AEM Forms biedt een gebruiksvriendelijke wizard. De tovenaar heeft snelle lusjenavigatie om pre-gevormde malplaatjes, het stileren, gebieden, en voorlegging opties gemakkelijk te selecteren.

![ Tovenaar om een Aangepaste Vorm ](/help/release-notes/assets/wizard.png){width="100%" align="center"} tot stand te brengen

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde gegevens vangen componenten. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. U kunt [ https://aemcomponents.dev/ ](https://aemcomponents.dev/) bezoeken om beschikbare kerncomponenten in actie **te bekijken Adobe adviseert gebruikend deze moderne en verlengbare componenten om Aangepaste Forms** te ontwikkelen.

* [ Aangepaste Componenten van de Stichting van Forms ](creating-adaptive-form.md): Dit zijn klassieke (oude) gegevens vangen componenten. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u nieuwe vormen creeert, beveelt Adobe het gebruiken van [ Aangepaste Componenten van de Kern van Forms aan om een Aangepaste Forms ](#create-an-adaptive-form-core-components) tot stand te brengen.

>[!BEGINTABS]

>[!TAB  creeer Aangepaste Forms met de Componenten van de Kern (geadviseerd) ]

U hebt het volgende nodig om een adaptief formulier te maken:

* **laat de Aangepaste Componenten van de Kern van Forms voor uw milieu** toe: Wanneer u een programma creeert, de Aangepaste Componenten van de Kern van Forms reeds toegelaten voor uw milieu. Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving. Bij het toelaten van de Componenten van de Kern voor uw milieu, wordt het **Aangepaste Forms (de Component van de Kern)** malplaatje en het canvasthema toegevoegd aan uw milieu. Als uw versie van AEM SDK ouder dan 2023.02.0, [ ervoor zorgt dat u `prerelease` vlag hebt die op uw milieu ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) wordt toegelaten aangezien de Aangepaste Componenten van de Kern van Forms deel van pre-huur vóór de versie 2023.02.0 vormden.

* **een Adaptief malplaatje van de Vorm**: Een malplaatje verstrekt een basisstructuur en bepaalt verschijning (lay-outs en stijlen) van een Aangepast Vorm. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice biedt een OOTB-sjabloon met de naam blank:

   * De sjabloon `blank` wordt opgenomen in elk nieuw AEM Forms as a Cloud Service-programma.
   * U kunt het referentiepakket installeren via Package Manager om de sjabloon `blank` toe te voegen aan uw AEM Forms as a Cloud Service-programma.
   * U kunt ook [ een Adaptief malplaatje van Forms (de Componenten van de Kern) ](template-editor.md) van kras tot stand brengen.

* **een Adaptief thema van de Vorm**: Een thema bevat het stileren details voor de componenten en de panelen. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  De sjabloon `Canvas` wordt opgenomen in elk nieuw AEM Forms as a Cloud Service-programma.
  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Toestemmingen**: Voeg uw gebruikers aan [!DNL forms-users] groep toe. De leden van de groep [!DNL forms-users] hebben machtigingen om een adaptief formulier te maken. Voor gedetailleerde lijst van vorm-specifieke gebruikersgroepen, zie [ Groepen en toestemmingen ](forms-groups-privileges-tasks.md).


## Een adaptief formulier maken {#create-an-adaptive-form-core-components}

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Voer uw referenties in op de Experience Manager-aanmeldingspagina. Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend. Selecteer op het tabblad Source een sjabloon:

   ![ Malplaatje van de Componenten van de Kern ](/help/forms/assets/core-components-template.png){width="100%" align="center"}

   Wanneer u een sjabloon selecteert, wordt de in de sjabloon opgegeven actie voor het thema en het verzenden automatisch geselecteerd en wordt de knop **[!UICONTROL Create]** ingeschakeld. U kunt naar de tabbladen **[!UICONTROL Style]** of **[!UICONTROL Submission]** gaan om een ander thema te selecteren of een actie te verzenden. Als de geselecteerde sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. U kunt naar het tabblad **[!UICONTROL Styles]** gaan om handmatig een thema te selecteren.

   >[!NOTE]
   >
   >
   > Als u niet hebt, **Aangepaste Forms (de Component van de Kern)** malplaatje op uw milieu, [ laat de Aangepaste Componenten van de Kern van Forms voor uw milieu ](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project) toe. Bij het toelaten van de Componenten van de Kern voor uw milieu, wordt het **Aangepaste Forms (de Component van de Kern)** malplaatje toegevoegd aan uw milieu.

1. Selecteer op het tabblad **[!UICONTROL Style]** een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.

   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De knop **[!UICONTROL Create]** wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) Selecteer op het tabblad Gegevens een gegevensmodel:

   * **het gegevensmodel van de Vorm**: A [ Model van de Gegevens van de Vorm (FDM) ](data-integration.md) laat u entiteiten en de diensten van ongelijksoortige gegevensbronnen aan een Aangepaste Vorm integreren. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [ JSON schema ](adaptive-form-json-schema-form-model.md) Onze op kern-Componenten-Gebaseerde Aangepaste Vorm staat voor naadloze integratie met het achterste deelsysteem van uw organisatie door de capaciteit te verstrekken om een schema te associëren JSON, dat de structuur van de gegevens vertegenwoordigt die worden geproduceerd of worden verbruikt. Met deze koppeling kunnen auteurs dynamisch inhoud toevoegen aan het adaptieve formulier met behulp van de elementen van het schema. De elementen van het schema zijn tijdens het ontwerpproces gemakkelijk toegankelijk op het tabblad Gegevensmodelobjecten van de inhoudbrowser en alle velden worden automatisch toegevoegd aan elk gemaakt adaptief formulier.

   Standaard worden alle velden van het gekoppelde JSON-schema automatisch geselecteerd en geconverteerd naar de overeenkomstige componenten van het adaptieve formulier, waardoor het ontwerpproces wordt gestroomlijnd. De wizard biedt het extra gebruiksgemak waarmee u via selectievakjes kunt kiezen welke velden in het adaptieve formulier moeten worden opgenomen.

1. Selecteer op het tabblad **[!UICONTROL Submission]** een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. Op het tabblad **[!UICONTROL  Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   * Wanneer de geselecteerde sjabloon geen verzendactie opgeeft, kunt u op het tabblad **[!UICONTROL Submission]** een verzendactie selecteren

1. (Optioneel) Op het tabblad **[!UICONTROL Delivery]** kunt u een publicatiedatum of een publicatiedatum opgeven voor een adaptief formulier.

1. Selecteer **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven:

   * **[!UICONTROL Title]** Hiermee geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in de gebruikersinterface van [!DNL Experience Manager Forms] .
   * **[!UICONTROL Name:]** Hiermee geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hiermee geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het adaptieve formulier rechtstreeks opslaan in `/content/dam/formsanddocuments` of een map maken, zoals `/content/dam/formsanddocuments/adaptiveforms` , om een adaptief formulier op te slaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. In het veld **[!UICONTROL Path]** wordt niet automatisch een map gemaakt.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje.  Op basis van het type adaptief formulier worden de formulierelementen in het gekoppelde <!--XFA form template, XML schema or --> JSON-schema of FDM (Form Data Model) weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van het **[!UICONTROL Content Browser]** in het zijpaneel.

Nu, kunt u slepen-en-daling de [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#components) of schemaelementen om uw Aangepaste Vorm te bouwen.


## Eigenschappen van formuliermodellen bewerken van een adaptief formulier {#edit-form-model-core-components-based-adaptive-forms}

1. Selecteer de Aangepaste Vorm en selecteer ![ informatie van de Pagina ](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Open Properties]**. De pagina Formuliereigenschappen wordt geopend.

1. Ga naar het tabblad **[!UICONTROL Form Model]** en kies een formuliermodel. Als het adaptieve formulier geen formuliermodel heeft, hebt u de vrijheid om een JSON-schema of een FDM-formuliergegevensmodel te kiezen. Als het adaptieve formulier echter al is gebaseerd op een formuliermodel, kunt u overschakelen op een ander formuliermodel van hetzelfde type. Als het formulier bijvoorbeeld een JSON-schema gebruikt, kunt u gemakkelijk overschakelen naar een ander JSON-schema. Op dezelfde manier kunt u overschakelen naar een ander FDM-model (Form Data Model) als het formulier een FDM-formulier gebruikt.

1. Selecteer **[!UICONTROL Save]** om de eigenschappen op te slaan.

>[!TAB  creeer Aangepaste Forms met de Componenten van de Stichting ]

U hebt het volgende nodig om een adaptief formulier te maken:

* **Toestemmingen**: Voeg uw gebruikers aan [!DNL forms-users] toe om hen toestemmingen te verstrekken om een Aangepaste Vorm tot stand te brengen. Voor gedetailleerde lijst van vorm-specifieke gebruikersgroepen, zie [ Groepen en toestemmingen ](forms-groups-privileges-tasks.md).

* **een Adaptief thema van de Vorm**: Een thema bevat het stileren details voor de componenten en de panelen. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. U kunt [ tot een thema ](themes.md) leiden of [ een bestaand thema ](import-export-forms-templates.md#uploading-a-theme) invoeren. U kunt [ recentste archetype ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html#create-project) voor sommige steekproefthema&#39;s ook opstellen.

* **een Adaptief malplaatje van de Vorm**: Een malplaatje verstrekt een basisstructuur en bepaalt verschijning (lay-outs en stijlen) van een Aangepast Vorm. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice ondersteunt twee typen sjablonen:

   * **Bewerkbaar malplaatje**: U kunt [ a ](template-editor.md) creëren of [ een bestaand editable malplaatje ](migrate-to-forms-as-a-cloud-service.md) invoeren. U kunt [ recentste archetype ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#:~:text=The%20AEM%20Archetype%20is%20made%20up%20of%20modules%3A,and%20request%20filters.%20it.tests%3A%20are%20Java-based%20integration%20tests.) ook opstellen om sommige steekproef editable malplaatjes te krijgen.

   * **Statisch malplaatje**: Dit zijn erfenismalplaatjes en worden geadviseerd slechts voor klanten die van Adobe Managed Services (AMS) en op-gebouwAEM Forms installaties (AEM 6.5 Forms of vroeger) migreren. Deze laten u uw bestaande investering in statische malplaatjes blijven gebruiken. Gebruik een bewerkbare sjabloon wanneer u een adaptief formulier maakt.


## Een adaptief formulier maken {#create-an-adaptive-form-foundation-components}

1. Open [!DNL Experience Manager Forms] Author-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Voer uw referenties in op de Experience Manager-aanmeldingspagina.

   Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend.
1. Selecteer op het tabblad Source een sjabloon:

   * Wanneer u een bewerkbare sjabloon selecteert, wordt de in de sjabloon opgegeven actie voor het thema en het verzenden automatisch geselecteerd en wordt de knop **[!UICONTROL Create]** ingeschakeld. U kunt naar de tabbladen **[!UICONTROL Style]** of **[!UICONTROL Submission]** gaan om een ander thema te selecteren of een actie te verzenden. Als de geselecteerde bewerkbare sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. U kunt naar het tabblad **[!UICONTROL Styles]** gaan om handmatig een thema te selecteren.

     >[!NOTE]
     >
     > U kunt ook een [!UICONTROL Document of Record] -sjabloon maken met een Adaptieve Forms-editor. Voor meer informatie, zie [ Document van de Steun van het Verslag in de Adaptieve Redacteur van de Vorm ](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

   * Wanneer u een statische sjabloon selecteert, zijn de opties voor gegevens, stijl, verzending, levering en voorvertoning niet beschikbaar. Als u een adaptief formulier maakt, is het raadzaam een bewerkbare sjabloon te gebruiken.

1. Selecteer op het tabblad **[!UICONTROL Style]** een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.
   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De knop **[!UICONTROL Create]** wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) Selecteer op het tabblad **[!UICONTROL Data]** een gegevensmodel:

   * **het gegevensmodel van de Vorm**: A [ Model van de Gegevens van de Vorm (FDM) ](data-integration.md) laat u entiteiten en de diensten van ongelijksoortige gegevensbronnen aan een Aangepaste Vorm integreren. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [ JSON schema ](adaptive-form-json-schema-form-model.md) vertegenwoordigt de structuur waarin het gegeven wordt geproduceerd of door het achterste deelsysteem in uw organisatie verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de inhoudbrowser wanneer u Adaptief Forms ontwerpt. Alle velden worden ook toegevoegd aan het gemaakte adaptieve formulier.

   Standaard zijn alle velden van het gegevensmodel geselecteerd. Wanneer u het adaptieve formulier maakt, worden alle geselecteerde gegevensmodelvelden geconverteerd naar de overeenkomstige adaptieve formuliercomponenten. De wizard verschaft u selectievakjes om alleen de velden te selecteren die moeten worden opgenomen in het adaptieve formulier.

   <!-- 
   
   If your JSON schema contains a fragment, the fragment is considered a single unit. You can select or deselect a complete fragment and all the fields of the fragment are selected or deselected accordingly. 
   
   -->

1. Selecteer op het tabblad **[!UICONTROL Submission]** een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. Op het tabblad **[!UICONTROL  Submission]** worden alle beschikbare verzendhandelingen weergegeven.

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

## Create an adaptive form based on XML or JSON schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

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

## Eigenschappen van formuliermodellen bewerken van een adaptief formulier {#edit-form-model-foundation-components}

U kunt het formuliermodel wijzigen voor een adaptief formulier (JSON-gebaseerd of Form Data Model (FDM)). U kunt niet van het ene formuliermodel naar het andere gaan.

1. Selecteer de Aangepaste Vorm en selecteer het **pictogram van Eigenschappen**.
1. Open het tabblad **[!UICONTROL Form Model]** en voer een van de volgende handelingen uit.

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een ander formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of FDM-formuliergegevensmodel selecteren.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u een ander <!-- form template, --> XML- of JSON-schema of Formuliergegevensmodel (FDM) kiezen voor hetzelfde formuliermodel.

1. Selecteer **[!UICONTROL Save]** om de eigenschappen op te slaan.

U kunt de eigenschappen van het formuliermodel ook wijzigen met de sjabloonconstructor Adaptief formulier of Adaptief formulier.

1. Selecteer de component **[!UICONTROL Adaptive Form container (Root)]** .
1. Klik ![ vormen pictogram van het Pictogram ](/help/forms/assets/configure-icon.svg) om **[!UICONTROL Properties]** van de Aangepaste container van de Vorm te openen.
1. Selecteer de tab **[!UICONTROL Data Model]** en voer een van de volgende handelingen uit:

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of FDM-formuliergegevensmodel selecteren.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u het formuliermodel niet wijzigen. U kunt een ander <!-- form template, --> XML- of JSON-schema of een FDM-formuliergegevensmodel kiezen voor hetzelfde formuliermodel als van toepassing is.
1. Selecteer ![ sparen ](/help/forms/assets/check-button.png) om de eigenschappen te bewaren.

![ fdm-Schema-Steun ](/help/forms/assets/fdmsupport.png){width="100%" align="center"}

>[!NOTE]
>
> U kunt een adaptief formulier ook opslaan als een sjabloon. Voor meer informatie, zie [ een malplaatje creëren gebruikend een AanpassingsVorm ](/help/forms/template-editor.md#saving-an-adaptive-form-as-template-saving-adaptive-form-as-template).

>[!ENDTABS]


## Volgende stappen

* [Adobe gebruiken om te ondertekenen met Forms](working-with-adobe-sign.md)
* [Google reCaptcha gebruiken in combinatie met Forms](captcha-adaptive-forms.md)
* [Herhaalbare sectie toevoegen aan een formulier](create-forms-repeatable-sections.md)
* [Velden van een formulier vooraf invullen](prepopulate-adaptive-form-fields.md)

>[!MORELIKETHIS]
>
>* [ creeer een Aangepast Vorm ](/help/forms/creating-adaptive-form-core-components.md)
