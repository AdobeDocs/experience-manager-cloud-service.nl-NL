---
title: Hoe kunnen wij het Model van de Gegevens van het Vorm voor een Aangepast Vorm tot stand brengen?
description: Leer Adaptieve Forms en Fragments maken op basis van een formuliergegevensmodel (FDM). Voorbeeldgegevens voor gegevensmodelobjecten in de FDM genereren en bewerken.
feature: Form Data Model
role: User
level: Beginner, Intermediate
exl-id: 827ce457-6585-46fb-8e28-1d970a40d949
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---

# Formuliergegevensmodel gebruiken {#use-form-data-model}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/using-form-data-model.html) |
| AEM as a Cloud Service | Dit artikel |


![gegevensintegratie](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Met gegevensintegratie kunt u verschillende bronnen van backendgegevens gebruiken om een formuliergegevensmodel te maken dat u als schema kunt gebruiken in verschillende adaptieve Forms <!--and interactive communications--> workflows. Het vereist het vormen van gegevensbronnen en het creëren van het Model van de Gegevens van de Vorm dat op de voorwerpen en de diensten van het gegevensmodel beschikbaar in gegevensbronnen wordt gebaseerd. Raadpleeg de volgende secties voor meer informatie:

* [[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md)
* [Gegevensbronnen configureren](configure-data-sources.md)
* [Formuliergegevensmodel maken](create-form-data-models.md)
* [Werken met formuliergegevensmodel](work-with-form-data-model.md)

Een formuliergegevensmodel is een uitbreiding van het JSON-schema waarmee u:

* [Adaptieve Forms en fragmenten maken](#create-af)
  <!--* [Create interactive communications and building blocks like text, list, and condition fragments](#create-ic)-->
* [Voorvertonen met voorbeeldgegevens](#preview-ic)
* [met de service Formuliergegevensmodel](#prefill)
* [Verzonden adaptieve formuliergegevens terugschrijven naar gegevensbronnen](#write-af)
* [Services aanroepen met behulp van adaptieve formulierregels](#invoke-services)

## Adaptieve Forms en fragmenten maken {#create-af}

U kunt [Adaptieve Forms](creating-adaptive-form.md) en Adaptieve formulierfragmenten <!-- [Adaptive Form Fragments](adaptive-form-fragments.md) --> op basis van een formuliergegevensmodel. Ga als volgt te werk om een formuliergegevensmodel te gebruiken bij het maken van een adaptief formulier of een adaptief formulierfragment:

1. Selecteer op het tabblad Formuliermodel in het scherm Eigenschappen toevoegen de optie **[!UICONTROL Form Data Model]** in de **[!UICONTROL Select From]** vervolgkeuzelijst.

   ![create-af-1-1](assets/create-af-1-1.png)

1. Tik om uit te breiden **[!UICONTROL Select Form Data Model]**. Alle beschikbare formuliergegevensmodellen worden weergegeven.

   Selecteer een gegevensmodel.

   ![create-af-2-1](assets/create-af-2-1.png)

1. (**Alleen adaptieve formulierfragmenten**) U kunt een adaptief formulierfragment maken op basis van slechts één gegevensmodelobject in een formuliergegevensmodel. Uitbreiden **[!UICONTROL Form Data Model Definitions]** vervolgkeuzelijst. Hiermee worden alle gegevensmodelobjecten in het opgegeven formuliergegevensmodel weergegeven. Selecteer een gegevensmodelobject in de lijst.

   ![create-af-3](assets/create-af-3.png)

   Nadat het adaptieve formulier- of adaptief formulierfragment op basis van een formuliergegevensmodel is gemaakt, worden formuliergegevensmodelobjecten weergegeven in het dialoogvenster **[!UICONTROL Data Sources]** van de inhoudbrowser in de Adaptieve formuliereditor.

   >[!NOTE]
   >
   >Bij een adaptief formulierfragment worden alleen het gegevensmodelobject dat is geselecteerd op het moment van ontwerpen en de bijbehorende gegevensmodelobjecten weergegeven op het tabblad Gegevensbronnen.

   ![data-model-objects-tab](assets/data-model-objects-tab.png)

   U kunt gegevensmodelobjecten naar het adaptieve formulier of fragment slepen om formuliervelden toe te voegen. De toegevoegde formuliervelden behouden de eigenschappen van de metagegevens en de binding met de eigenschappen van gegevensmodelobjecten. De binding zorgt ervoor dat de veldwaarden bij het verzenden van het formulier worden bijgewerkt in de bijbehorende gegevensbronnen en dat deze worden voorgevuld wanneer het formulier wordt gegenereerd.

<!-- ## Create interactive communications {#create-ic}

You can create an interactive communication based on a Form Data Model that you can use to prefill interactive communication with data from configured data sources. In addition, the building blocks of an interactive communication, such as text, list, and condition document fragments can be based on a form data model.

You can choose a Form Data Model when creating an interactive communication or a document fragment. The following image shows the General tab of the Create Interactive Communication dialog.

![create-ic](assets/create-ic.png)

General tab of Create Interactive Communication dialog

For more information, see:

[Create an interactive communication](create-interactive-communication.md)

[Text in Interactive Communications](texts-interactive-communications.md)

[Conditions in Interactive Communications](conditions-interactive-communications.md)

[List fragments](lists.md) -->

## Voorvertonen met voorbeeldgegevens {#preview-ic}

Met de formuliergegevensmodeleditor kunt u voorbeeldgegevens voor gegevensmodelobjecten genereren en bewerken in het formuliergegevensmodel. U kunt deze gegevens gebruiken om een voorvertoning weer te geven en te testen <!--interactive communications and--> Adaptieve Forms. U moet de voorbeeldgegevens genereren voordat u een voorvertoning weergeeft zoals beschreven in [Werken met formuliergegevensmodel](work-with-form-data-model.md#sample).

<!--To preview an interactive communication with sample Form Data Model data:

1. On [!DNL  Experience Manager] author instance, navigate to **[!UICONTROL Forms > Forms & Documents]**.
1. Select an interactive communication and tap **[!UICONTROL Preview]** in the toolbar to select **[!UICONTROL Web Channel]**, **[!UICONTROL Print Channel]**, or **[!UICONTROL Both Channels]** to preview the interactive communication.
1. In the Preview [*channel*] dialog, ensure that **[!UICONTROL Test Data of Form Data Model]** is selected and tap **[!UICONTROL Preview]**.

The interactive communication opens with prefilled sample data.

![web-preview](assets/web-preview.png)-->

Als u een voorbeeld van een adaptief formulier wilt bekijken met voorbeeldgegevens, opent u het adaptieve formulier in de modus Ontwerpen en tikt u op **[!UICONTROL Preview]**.

## Vooraf invullen met service Formuliergegevensmodel {#prefill}

[!DNL Experience Manager Forms] biedt de vooraf ingevulde service voor het out-of-the-box formuliergegevensmodel die u kunt inschakelen voor Adaptive Forms <!--and interactive communications--> op basis van het formuliergegevensmodel. De prefill dienst vraagt gegevensbronnen voor gegevensmodelvoorwerpen in de Aangepaste Vorm <!--and interactive communication--> en voegt daarom gegevens vooraf in tijdens het genereren van het formulier of de communicatie.

Open de eigenschappen van de container van de Adaptief formulier en selecteer **[!UICONTROL Form Data Model Prefill service]** van de **[!UICONTROL Prefill Service]** in de Basis accordeon. Sla vervolgens de eigenschappen op.

![Prefill-service](assets/prefill-service.png)

<!--To configure Form Data Model prefill service in an interactive communication, you can select Form Data Model Prefill Service in the Prefill Service drop-down while creating it or later by modifying the properties.

![edit-ic-props](assets/edit-ic-props.png)

Edit Properties dialog for an interactive communication-->

## Verzonden adaptieve formuliergegevens naar gegevensbronnen schrijven {#write-af}

Wanneer een gebruiker een formulier verzendt dat is gebaseerd op een formuliergegevensmodel, kunt u het formulier zo configureren dat de verzonden gegevens voor een gegevensmodelobject naar de bijbehorende gegevensbronnen worden geschreven. Om dit te bereiken, [!DNL Experience Manager Forms] verstrekken [Formuliergegevensmodel Handeling verzenden](configuring-submit-actions.md), alleen beschikbaar buiten de verpakking voor Adaptive Forms op basis van een formuliergegevensmodel. Het schrijft voorgelegde gegevens voor een voorwerp van het gegevensmodel in zijn gegevensbron.

Als u het formuliergegevensmodel voor het verzenden van een handeling wilt configureren, opent u de eigenschappen van de adaptieve formuliercontainer en selecteert u **[!UICONTROL Submit using Form Data Model]** in de vervolgkeuzelijst Handeling verzenden onder de verzendaccordeon. Blader vervolgens naar een gegevensmodelobject en selecteer dit in het menu **[!UICONTROL Name of the data model object to submit]** vervolgkeuzelijst. Sla de eigenschappen op.

Bij het verzenden van formulieren worden gegevens voor het geconfigureerde gegevensmodelobject naar de desbetreffende gegevensbron geschreven.

<!--![data-submission](assets/data-submission.png)-->

U kunt ook formulierbijlagen verzenden naar een gegevensbron met binaire objecteigenschappen van gegevensmodellen. Ga als volgt te werk om bijlagen naar een JDBC-gegevensbron te verzenden:

1. Voeg een gegevensmodelobject dat een binaire eigenschap bevat toe aan het formuliergegevensmodel.
1. Sleep de knop **[!UICONTROL File Attachment]** van de browser Components naar het adaptieve formulier.
1. Tik om de toegevoegde component te selecteren en tik ![settings_icon](assets/configure-icon.svg) om de browser van Eigenschappen voor de component te openen.
1. Tik in het veld Bindverwijzing op ![mapSearch_18](assets/folder-search-icon.svg) en navigeer om de binaire eigenschap te selecteren die u in het formuliergegevensmodel hebt toegevoegd. Configureer desgewenst andere eigenschappen.

   Tikken ![knop controleren](assets/save_icon.svg) om de eigenschappen op te slaan. Het bijslagveld is nu gebonden aan de binaire eigenschap van het formuliergegevensmodel.

1. Schakel in het gedeelte Verzending van de eigenschappen van de container van adaptieve formulieren de optie **[!UICONTROL Submit Form Attachments]**. De bijlage in het binaire-eigenschapveld wordt naar de gegevensbron verzonden bij het verzenden van het formulier.

## Services aanroepen in Adaptive Forms met behulp van regels {#invoke-services}

In een adaptief formulier op basis van een formuliergegevensmodel kunt u [regels maken](rule-editor.md) om de diensten aan te halen die in het model van vormgegevens worden gevormd. De **[!UICONTROL Invoke Services]** bewerking in een regel bevat een lijst met alle beschikbare services in het formuliergegevensmodel en u kunt invoer- en uitvoervelden voor de service selecteren. U kunt ook de opdracht **[!UICONTROL Set Value]** regeltype om de service Form Data Model aan te roepen en de waarde van een veld in te stellen op de uitvoer die door de service wordt geretourneerd.

Bijvoorbeeld, haalt de volgende regel de dienst aan die Werknemeridentiteitskaart als input neemt en de teruggekeerde waarden in overeenkomstige Afhankelijke identiteitskaart, Familienaam, Voornaam, en Gendergebieden in de vorm worden bevolkt.

![oproepdienst](assets/invoke-service.png)

Daarnaast kunt u de opdracht `guidelib.dataIntegrationUtils.executeOperation` API om een JavaScript in de coderedacteur voor de regelredacteur te schrijven. <!-- For API details, see [API to invoke Form Data Model service](invoke-form-data-model-services.md).-->

### Een formuliergegevensmodel aanroepen met behulp van aangepaste functies {#invoke-form-data-model-using-custom-functions}

U kunt [een formuliergegevensmodel aanroepen vanuit een regeleditor met behulp van aangepaste functies](/help/forms/rule-editor.md#custom-functions-in-rule-editor-custom-functions). Als u het gegevensmodel van het formulier wilt aanroepen, voegt u een formuliergegevensmodel toe aan de lijst van gewenste personen. Een formuliergegevensmodel toevoegen aan een toegestane lijst:

1. Ga naar Experience Manager webconsole op `https://server:host/system/console/configMgr`.
1. Zoeken **[!UICONTROL Adaptive Form-Level Whitelisting of Form Data Model for Service Invocation - Configuration Factory]**.
1. Klikken ![pluspictogram](/help/forms/assets/Smock_Add_18_N.svg) pictogram om de configuratie toe te voegen.
1. Toevoegen **[!UICONTROL Content path pattern]** om de locatie van uw Adaptieve Forms op te geven.  De standaardwaarde is `/content/forms/af/(.*)` die alle adaptieve Forms omvat. U kunt ook het pad opgeven voor een specifiek adaptief formulier.
1. Toevoegen **[!UICONTROL Form Data Model path pattern]** om de locatie van het formuliergegevensmodel op te geven. De standaardwaarde is `/content/dams/formsanddocuments-fdm/(.*)` Dit omvat het gegevensmodel van het formulier. U kunt ook het pad opgeven voor een specifiek formuliergegevensmodel.
1. Sla de instellingen op.

De toegevoegde configuratie wordt opgeslagen onder de **[!UICONTROL Adaptive Form-Level Whitelisting of Form Data Model for Service Invocation - Configuration Factory]** -optie.

>[!VIDEO](https://video.tv.adobe.com/v/3423977/adaptive-forms-custom-function-rule-editor)

>[!NOTE]
>
> Om een model van vormgegevens van de regelredacteur aan te halen gebruikend douanefuncties door een AEM archetype project:
>
>1. [Een configuratiebestand maken](https://github.com/adobe/aem-core-forms-components/blob/master/it/config/src/main/content/jcr_root/apps/system/config/com.adobe.aemds.guide.factory.impl.AdaptiveFormFDMConfigurationFactoryImpl~core-components-it.cfg.json).
>1. Stel eigenschappen van getContentPathPattern en getFormDataModelPathPattern in.
>1. Implementeer het project.
