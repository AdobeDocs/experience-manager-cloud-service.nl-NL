---
title: Een adaptief formulier maken
description: Leer hoe u een adaptief formulier maakt met [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op het maken van een adaptief formulier op basis van een formuliergegevensmodel en een XML- of JSON-schema.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: 8d40f259e70ef73285aafcb736e1f9d720380f7d
workflow-type: tm+mt
source-wordcount: '2178'
ht-degree: 0%

---

# Een adaptief formulier maken (kerncomponenten) {#creating-an-adaptive-form-core-components}

Met Adaptive Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke wizard voor zakelijke gebruikers om snel een Adaptive Forms te maken. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde componenten voor het vastleggen van gegevens. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe raadt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [Aangepaste Forms Foundation-componenten](creating-adaptive-form.md): Dit zijn klassieke (oude) componenten voor gegevensvastlegging. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Adobe raadt u aan nieuwe formulieren te gebruiken als u nieuwe formulieren maakt  [Adaptieve Forms Core-componenten](creating-adaptive-form-core-components.md) om een Adaptieve Forms te maken.

![Wizard voor het maken van een adaptief formulier](/help/release-notes/assets/wizard.png)


## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* **Adaptieve Forms Core-componenten inschakelen voor uw omgeving**: Wanneer u een nieuw programma maakt, zijn de Adaptive Forms Core Components al ingeschakeld voor uw omgeving. Als u een as a Cloud Service Forms-omgeving hebt die is gebaseerd op Archetype 39 of eerder, [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](enable-adaptive-forms-core-components.md). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon en canvasthema worden toegevoegd aan uw omgeving. Als uw AEM SDK-versie ouder is dan 2023.02.0, [zorg ervoor dat u `prerelease` markering ingeschakeld in uw omgeving](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) omdat Adaptive Forms Core Components deel uitmaakten van de pre-lease vóór de release van 2023.02.0.

* **Een adaptieve formuliersjabloon**: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice biedt een OOTB-sjabloon met de naam blank:

   * De `blank` de sjabloon wordt bij elk nieuw as a Cloud Service AEM Forms-programma meegeleverd.
   * U kunt het referentiepakket installeren via Package Manager om het `blank` template naar uw as a Cloud Service AEM Forms-programma.
   * U kunt ook [een nieuwe adaptieve Forms-sjabloon maken (Core Components)](template-editor.md) helemaal niet.

* **Een adaptief formulierthema**: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  De `Canvas` de sjabloon wordt bij elk nieuw as a Cloud Service AEM Forms-programma meegeleverd.
  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Machtigingen**: Gebruikers toevoegen aan [!DNL forms-users] groep. De leden van de [!DNL forms-users] groep heeft machtigingen om een adaptief formulier te maken. Voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen gaat u naar [Groepen en machtigingen](forms-groups-privileges-tasks.md).


## Een adaptief formulier maken (kerncomponenten) {#create-an-adaptive-form-core-components}

1. Meld u aan bij uw [!DNL Experience Manager Forms] Instantie van auteur. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in. Tik in de linkerbovenhoek nadat u bent aangemeld op **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Tik op **[!UICONTROL Create]**  > **[!UICONTROL Adaptive Forms]**. De wizard wordt geopend. Selecteer een sjabloon op het tabblad Bron:

   ![Sjabloon voor kerncomponenten](/help/forms/assets/core-components-template.png)

   Wanneer u een sjabloon selecteert, wordt de actie voor het thema en het verzenden die in de sjabloon is opgegeven automatisch geselecteerd en wordt de opdracht **[!UICONTROL Create]** wordt ingeschakeld. Je kunt naar de **[!UICONTROL Style]** of **[!UICONTROL Submission]** tabs om een ander thema te selecteren of actie te verzenden. Als de geselecteerde sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. Je kunt naar de **[!UICONTROL Styles]** om handmatig een thema te selecteren.

   >[!NOTE]
   >
   >
   > Als u dat niet doet, **Adaptieve Forms (Core Component)** sjabloon op uw omgeving, [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon wordt toegevoegd aan uw omgeving.

1. In de **[!UICONTROL Style]** selecteert u een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.

   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De **[!UICONTROL Create]** De knop wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) Selecteer op het tabblad Gegevens een gegevensmodel:

   * **Formuliergegevensmodel**: A [Formuliergegevensmodel](data-integration.md) Hiermee kunt u entiteiten en services integreren van verschillende gegevensbronnen tot een adaptief formulier. Kies Formuliergegevensmodel als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [JSON-schema](adaptive-form-json-schema-form-model.md) Met ons adaptieve formulier op basis van Core-Components kunt u naadloze integratie tot stand brengen met het back-end systeem van uw organisatie door de mogelijkheid te bieden om een JSON-schema te koppelen, dat de structuur vertegenwoordigt van de gegevens die worden geproduceerd of verbruikt. Met deze koppeling kunnen auteurs dynamisch inhoud toevoegen aan het adaptieve formulier met behulp van de elementen van het schema. De elementen van het schema zijn tijdens het ontwerpproces gemakkelijk toegankelijk op het tabblad Gegevensmodelobjecten van de inhoudbrowser en alle velden worden automatisch toegevoegd aan elk nieuw gemaakt adaptief formulier.

   Standaard worden alle velden van het gekoppelde JSON-schema automatisch geselecteerd en geconverteerd naar de overeenkomstige componenten van het adaptieve formulier, waardoor het ontwerpproces wordt gestroomlijnd. De wizard biedt het extra gebruiksgemak waarmee u via selectievakjes kunt kiezen welke velden in het adaptieve formulier moeten worden opgenomen.

1. In de **[!UICONTROL Submission]** selecteert u een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. De **[!UICONTROL  Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   * Als de geselecteerde sjabloon geen verzendactie opgeeft, kunt u de opdracht **[!UICONTROL Submission]** tabblad om een verzendactie te selecteren

1. (Optioneel) In het dialoogvenster **[!UICONTROL Delivery]** kunt u een publicatiedatum of een publicatiedatum opgeven voor een adaptief formulier.

1. Tik op **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven:

   * **[!UICONTROL Title]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in het dialoogvenster [!DNL Experience Manager Forms] gebruikersinterface.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hier geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het adaptieve formulier rechtstreeks opslaan op `/content/dam/formsanddocuments` of maak een map, zoals `/content/dam/formsanddocuments/adaptiveforms` om een adaptief formulier op te slaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. De **[!UICONTROL Path]** wordt niet automatisch een map gemaakt.

1. Tik op **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje.  Op basis van het type adaptief formulier worden de formulierelementen in het bijbehorende formulier <!--XFA form template, XML schema or --> Het JSON-schema of het formuliergegevensmodel worden weergegeven in het **[!UICONTROL Data Model Objects]** tabblad van het dialoogvenster **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

Nu kunt u de [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) naar Adaptive Forms-container om het formulier te ontwerpen en te maken. U kunt ook [https://aemcomponents.dev/](https://aemcomponents.dev/) om beschikbare kerncomponenten in actie te bekijken.

## Handeling verzenden voor een adaptief formulier configureren {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd via een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

1. Klik op de knop  **[!UICONTROL Submission]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een verzendactie te configureren](/help/forms/assets/adaptive-forms-submit-message.png)

1. Selecteer en vorm een **[!UICONTROL Submit action]**, op basis van uw vereisten. Zie voor meer informatie over Handelingen verzenden [Handeling Adaptief verzenden van formulier](/help/forms/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leid de gebruiker om naar een pagina of toon een dank u bericht bij de vormverzending

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Submission]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een omleidingspagina of een bedankbericht te configureren](/help/forms/assets/adaptive-forms-redirect-message.png)

   * Als u een omleidings-URL wilt configureren, selecteert u bij Verzenden de optie **[!UICONTROL Redirect to URL]** en bladert u naar een AEM Sites-pagina en selecteert u deze. U kunt ook een URL van een externe pagina opgeven.

   * Als u een aangepast bericht of een bedankbericht wilt configureren, selecteert u bij Verzenden de optie **[!UICONTROL Show Message]** en geef een bericht op in het dialoogvenster **[!UICONTROL Message content]** doos. Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems met tekstopmaak weer te geven.

## Een schema of formuliergegevensmodel configureren voor een adaptief formulier{#configure-schema-or-data-model-for-form}

Met het formuliergegevensmodel kunt u een formulier verbinden met een gegevensbron om gegevens te verzenden en te ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen. Afhankelijk van de vereiste verbinding, sluit uw formulier aan op een JSON-schema of formuliergegevensmodel:

* [Een JSON-schema maken en uploaden naar uw omgeving](/help/forms/adaptive-form-json-schema-form-model.md)
* [Een formuliergegevensmodel maken](/help/forms/create-form-data-models.md)

### Een JSON-schema of formuliergegevensmodel voor uw formulier configureren

Een JSON-schema of formuliergegevensmodel configureren voor uw formulier:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Data Model]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een JSON-schema of formuliergegevensmodel te configureren](/help/forms/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Selecteer en configureer een JSON-schema of formuliergegevensmodel op basis van uw vereisten:

   * Wanneer u **[!UICONTROL Form Model]** gebruiken **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel te selecteren.
   * Wanneer u **[!UICONTROL Schema]** gebruiken **[!UICONTROL Schema]** Selecteer een JSON-schema voor uw formulier.

1. Klik op **[!UICONTROL Done]**.

## Een prefill-service configureren  {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](/help/forms/prepopulate-adaptive-form-fields.md)
* [Vooraf ingevulde service Formuliergegevensmodel gebruiken](#fdm-prefill-service)

### De service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen {#fdm-prefill-service}

U kunt de service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen met een formuliergegevensmodel of een aangepaste voorinvulservice. De service Vooraf invullen formuliergegevensmodel gebruikt de [De service van het geconfigureerde formuliergegevensmodel ophalen](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens op te halen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de eigenschappen van de container van het adaptieve formulier ![Eigenschappen van adaptieve formuliercontainers](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een omleidingspagina of een bedankbericht te configureren](/help/forms/assets/adaptive-forms-container-prefill-service.png)
1. Selecteer een formuliergegevensmodel. Open de **[!UICONTROL Basic]** tab. Selecteer in de service Prefill de optie **[!UICONTROL Form Data Model Prefill Service]**.
1. Klik op **[!UICONTROL Done]**. Uw adaptieve formulier is nu geconfigureerd voor het vooraf invullen van het formuliergegevensmodel. U kunt nu de [regeleditor](rule-editor.md) om regels te maken voor het vooraf invullen van velden van het formulier.

## Eigenschappen van een formuliermodel bewerken in een adaptief formulier {#edit-form-model}

1. Selecteer het adaptieve formulier en tik op ![Pagina-informatie](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Open Properties]**. De pagina Formuliereigenschappen wordt geopend.

1. Ga naar de **[!UICONTROL Form Model]** en kiest u een formuliermodel. Als het adaptieve formulier geen formuliermodel heeft, hebt u de vrijheid om een JSON-schema of een formuliergegevensmodel te kiezen. Als het adaptieve formulier echter al is gebaseerd op een formuliermodel, kunt u overschakelen op een ander formuliermodel van hetzelfde type. Als het formulier bijvoorbeeld een JSON-schema gebruikt, kunt u eenvoudig overschakelen naar een ander JSON-schema. Op dezelfde manier kunt u overschakelen naar een ander formuliergegevensmodel als het formulier een formuliergegevensmodel gebruikt.

1. Tikken **[!UICONTROL Save]** om de eigenschappen op te slaan.


## Zie volgende

* [Stijlen of thema&#39;s maken voor uw formulieren](using-themes-in-core-components.md)
* [Dynamisch gedrag toevoegen aan formulieren met de regeleditor](rule-editor.md)
* [Formulierindeling instellen voor verschillende schermgrootten en apparaattypen](/help/sites-cloud/authoring/features/responsive-layout.md)


## Verwante artikelen {#related-article}

* [Een op zichzelf staand adaptief formulier voor kerncomponenten maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)
