---
title: Hoe te om een Aangepast Vorm tot stand te brengen dat op de Componenten van de Kern wordt gebaseerd?
description: Leer hoe te om een Aangepast Vorm tot stand te brengen gebruikend  [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op de manier waarop u een adaptief formulier kunt maken op basis van een FDM- (Form Data Model) en XML- of JSON-schema.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: 1e812d93-4ba5-4589-b59b-2f564d754b0f
source-git-commit: 812b1e41b460783d3fa220bd24ecfcfd4208a5df
workflow-type: tm+mt
source-wordcount: '2298'
ht-degree: 0%

---

# Een adaptief formulier maken (kerncomponenten) {#creating-an-adaptive-form-core-components}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-an-adaptive-form-core-components.html) |
| AEM as a Cloud Service | Dit artikel |


Met Adaptive Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke wizard voor zakelijke gebruikers om snel een Adaptive Forms te maken. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde gegevens vangen componenten. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe beveelt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [ Aangepaste Componenten van de Stichting van Forms ](creating-adaptive-form.md): Dit zijn klassieke (oude) gegevens vangen componenten. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u nieuwe vormen creeert, adviseert de Adobe gebruikend [ Aangepaste Componenten van de Kern van Forms ](creating-adaptive-form-core-components.md) om een Aangepaste Forms tot stand te brengen.

![ Tovenaar om een Aangepaste Vorm ](/help/release-notes/assets/wizard.png) tot stand te brengen


## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* **laat de Aangepaste Componenten van de Kern van Forms voor uw milieu** toe: Wanneer u een programma creeert, de Aangepaste Componenten van de Kern van Forms reeds toegelaten voor uw milieu. Als u een as a Cloud Service milieu van Forms hebt dat op Archetype 39 of vroeger wordt gebaseerd, [ laat de Aangepaste Componenten van de Kern van Forms voor uw milieu ](enable-adaptive-forms-core-components.md) toe. Bij het toelaten van de Componenten van de Kern voor uw milieu, worden de **Aangepaste Forms (de Component van de Kern)** malplaatjes en de thema&#39;s toegevoegd aan uw milieu. Als uw AEM versie van SDK ouder dan 2023.02.0, [ ervoor zorgt dat u `prerelease` vlag hebt die op uw milieu ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#new-features) wordt toegelaten aangezien de Adaptieve Componenten van de Kern van Forms deel van pre-prelease vóór de versie 2023.02.0 vormden.

* **een Adaptief malplaatje van de Vorm**: Een malplaatje verstrekt een basisstructuur en bepaalt verschijning (lay-outs en stijlen) van een Aangepast Vorm. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice biedt een OOTB-sjabloon met de naam blank:

   * De `blank` -sjabloon wordt opgenomen in elk nieuw AEM Forms as a Cloud Service programma.
   * U kunt het referentiepakket installeren via Package Manager om de `blank` -sjabloon toe te voegen aan uw AEM Forms as a Cloud Service programma.
   * U kunt ook [ een Adaptief malplaatje van Forms (de Componenten van de Kern) ](/help/forms/template-editor-core-components.md) van kras tot stand brengen.
   * U kunt [ steekproefmalplaatjes ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) aan uw milieu ook opstellen. Hiermee kunt u snel formulieren maken.

* **een Adaptief thema van de Vorm**: Een thema bevat het stileren details voor de componenten en de panelen. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  De `Canvas` -sjabloon wordt opgenomen in elk nieuw AEM Forms as a Cloud Service programma. U kunt [ steekproefthema&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) aan uw milieu ook opstellen. Deze hulp u begint uw vormen te stileren en een basisstructuur te verstrekken om een thema tot stand te brengen of aan te passen volgens uw bedrijfsvereisten.

  <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create an Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Toestemmingen**: Voeg uw gebruikers aan [!DNL forms-users] groep toe. De leden van de groep [!DNL forms-users] hebben machtigingen om een adaptief formulier te maken. Voor gedetailleerde lijst van vorm-specifieke gebruikersgroepen, zie [ Groepen en toestemmingen ](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## Een adaptief formulier maken  {#create-an-adaptive-form-core-components}

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in. Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend. Selecteer op het tabblad Source een sjabloon:

   ![ Malplaatje van de Componenten van de Kern ](/help/forms/assets/core-components-template.png)

   Wanneer u een sjabloon selecteert, wordt de in de sjabloon opgegeven actie voor het thema en het verzenden automatisch geselecteerd en wordt de knop **[!UICONTROL Create]** ingeschakeld. U kunt naar de tabbladen **[!UICONTROL Style]** of **[!UICONTROL Submission]** gaan om een ander thema te selecteren of een actie te verzenden. Als de geselecteerde sjabloon geen thema opgeeft, blijft de knop Maken uitgeschakeld. U kunt naar het tabblad **[!UICONTROL Styles]** gaan om handmatig een thema te selecteren.

   >[!NOTE]
   >
   >
   > Als u niet hebt, **Aangepaste Forms (de Component van de Kern)** malplaatje op uw milieu, [ laat de Aangepaste Componenten van de Kern van Forms voor uw milieu ](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project) toe. Bij het toelaten van de Componenten van de Kern voor uw milieu, wordt het **Aangepaste Forms (de Component van de Kern)** malplaatje toegevoegd aan uw milieu.

1. Selecteer op het tabblad **[!UICONTROL Style]** een thema:

   * Als de geselecteerde sjabloon een thema opgeeft, wordt het thema automatisch geselecteerd in de wizard. U kunt ook een ander thema kiezen op het tabblad Stijl.

   * Als de geselecteerde sjabloon geen thema opgeeft, kunt u het tabblad Stijl gebruiken om een thema te kiezen. De knop **[!UICONTROL Create]** wordt alleen ingeschakeld nadat een thema is geselecteerd.

1. (Optioneel) Selecteer op het tabblad Gegevens een gegevensmodel:

   * **het gegevensmodel van de Vorm (FDM)**: Het Model van de Gegevens van de a [ Vorm ](data-integration.md) laat u entiteiten en de diensten van ongelijksoortige gegevensbronnen aan een AanpassingsVorm integreren. Kies Formuliergegevensmodel (FDM) als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   * **JSON Schema**: [ JSON schema ](adaptive-form-json-schema-form-model.md) Onze op kern-Componenten-Gebaseerde Aangepaste Vorm staat voor naadloze integratie met het achterste deelsysteem van uw organisatie door de capaciteit te verstrekken om een schema te associëren JSON, dat de structuur van de gegevens vertegenwoordigt die worden geproduceerd of worden verbruikt. Met deze koppeling kunnen auteurs dynamisch inhoud toevoegen aan het adaptieve formulier met behulp van de elementen van het schema. De elementen van het schema zijn tijdens het ontwerpproces gemakkelijk toegankelijk op het tabblad Gegevensmodelobjecten van de inhoudbrowser en alle velden worden automatisch toegevoegd aan elk gemaakt adaptief formulier.

   Standaard worden alle velden van het gekoppelde JSON-schema automatisch geselecteerd en geconverteerd naar de overeenkomstige componenten van het adaptieve formulier, waardoor het ontwerpproces wordt gestroomlijnd. De wizard biedt het extra gebruiksgemak waarmee u via selectievakjes kunt kiezen welke velden in het adaptieve formulier moeten worden opgenomen.

1. Selecteer op het tabblad **[!UICONTROL Submission]** een verzendactie:

   * Wanneer u een sjabloon selecteert, wordt de verzendactie die in de sjabloon is opgegeven automatisch geselecteerd. U kunt een andere verzendactie selecteren op het tabblad Verzending. Op het tabblad **[!UICONTROL &#x200B; Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   * Wanneer de geselecteerde sjabloon geen verzendactie opgeeft, kunt u op het tabblad **[!UICONTROL Submission]** een verzendactie selecteren

1. (Optioneel) Op het tabblad **[!UICONTROL Delivery]** kunt u een publicatiedatum of een publicatiedatum opgeven voor een adaptief formulier.

1. Selecteer **[!UICONTROL Create]**. Er wordt een dialoogvenster weergegeven waarin u de titel, naam en locatie voor het opslaan van het adaptieve formulier kunt opgeven:

   * **[!UICONTROL Title]** Hiermee geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in de gebruikersinterface van [!DNL Experience Manager Forms] .
   * **[!UICONTROL Name:]** Hiermee geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Path:]** Hiermee geeft u de locatie op waar het adaptieve formulier moet worden opgeslagen. U kunt het adaptieve formulier rechtstreeks opslaan in `/content/dam/formsanddocuments` of een map maken, zoals `/content/dam/formsanddocuments/adaptiveforms` , om een adaptief formulier op te slaan. Zorg ervoor dat u de map maakt voordat u deze in het pad gebruikt. In het veld **[!UICONTROL Path]** wordt niet automatisch een map gemaakt.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en geopend in de Adaptive Forms-editor. De redacteur toont de inhoud beschikbaar in het malplaatje.  Op basis van het type adaptief formulier worden de formulierelementen in het gekoppelde <!--XFA form template, XML schema or --> JSON-schema of FDM (Form Data Model) weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van het **[!UICONTROL Content Browser]** in het zijpaneel. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

Nu, kunt u slepen-en-daling de [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) aan de Aangepaste container van Forms om de vorm te ontwerpen en tot stand te brengen. U kunt [ https://aemcomponents.dev/ ](https://aemcomponents.dev/) ook bezoeken om beschikbare kerncomponenten in actie te bekijken.

>[!NOTE]
>
> U kunt ook [ Aangepaste Forms tot stand brengen gebruikend XFA vormmalplaatjes (*.XDP dossiers) ](/help/forms/create-adaptive-form-using-xfa-templates.md). Hiermee kunt u tijd besparen door velden uit XDP-bestanden rechtstreeks in Adaptive Forms te hergebruiken.

## Handeling verzenden voor een adaptief formulier configureren {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd via een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

1. Klik op de tab **[!UICONTROL Submission]** .

   ![ klik het pictogram van de Sleutel om de Adaptieve de dialoogdoos van de Container van de Vorm te openen om een verzendactie te vormen ](/help/forms/assets/adaptive-forms-submit-message.png)

1. Selecteer en configureer een **[!UICONTROL Submit action]** op basis van uw vereisten. Voor gedetailleerde informatie over Submit Acties, zie [ Aangepaste Vorm verzenden Actie ](/help/forms/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leid de gebruiker om naar een pagina of toon een dank u bericht bij de vormverzending

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de tab **[!UICONTROL Submission]** .

   ![ klik het pictogram van de Sleutel om de Aangepaste de dialoogdoos van de Container van de Vorm te openen om een omleidingspagina te vormen of u te danken bericht ](/help/forms/assets/adaptive-forms-redirect-message.png)

   * Als u een omleidings-URL wilt configureren, bijvoorbeeld bij Verzenden, selecteert u de optie **[!UICONTROL Redirect to URL]** en bladert en selecteert u een AEM Sites-pagina of geeft u de URL van een externe pagina op.

   * Als u een aangepast bericht of een bedankbericht wilt configureren, bijvoorbeeld bij Verzenden, selecteert u de optie **[!UICONTROL Show Message]** en geeft u een bericht op in het vak **[!UICONTROL Message content]** . Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.

## Een schema of formuliergegevensmodel (FDM) configureren voor een adaptief formulier{#configure-schema-or-data-model-for-form}

Met het FDM (Form Data Model) kunt u een formulier verbinden met een Data Source om gegevens te verzenden en te ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen. Gebaseerd op het vereiste, verbind uw vorm met een schema JSON of het gegevensmodel van de Vorm (FDM):

* [ creeer een Schema JSON en upload aan uw milieu ](/help/forms/adaptive-form-json-schema-form-model.md)
* [ creeer een Model van de Gegevens van de Vorm (FDM) ](/help/forms/create-form-data-models.md)

### Een JSON-schema of FDM (Form Data Model) voor uw formulier configureren

Een JSON-schema of FDM (Form Data Model) voor uw formulier configureren:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de tab **[!UICONTROL Data Model]** .

   ![ klik het pictogram van de Sleutel om de Adaptieve de dialoogdoos van de Container van de Vorm te openen om een JSON- schema of model van vormgegevens (FDM) te vormen ](/help/forms/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Selecteer en configureer een JSON-schema of FDM (Form Data Model) op basis van uw vereisten:

   * Als u de optie **[!UICONTROL Form Model]** selecteert, gebruikt u de optie **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel (FDM) te selecteren.
   * Als u de optie **[!UICONTROL Schema]** selecteert, gebruikt u de optie **[!UICONTROL Schema]** om een JSON-schema voor uw formulier te selecteren.

1. Klik op **[!UICONTROL Done]**.

## Een prefill-service configureren  {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](/help/forms/prepopulate-adaptive-form-fields.md)
* [Vooraf ingevulde service Formuliergegevensmodel gebruiken](#fdm-prefill-service)

### De service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen {#fdm-prefill-service}

U kunt de service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen met een formuliergegevensmodel of een aangepaste voorinvulservice. Het model van Gegevens van de Vorm Prefill de dienst gebruikt [ krijgt Dienst van het gevormde Model van Gegevens van de Vorm ](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens terug te winnen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![ klik het pictogram van de Sleutel om de Aangepaste de dialoogdoos van de Container van de Vorm te openen om een omleidingspagina te vormen of u te danken bericht ](/help/forms/assets/adaptive-forms-container-prefill-service.png)
1. Selecteer een formuliergegevensmodel (FDM). Open de tab **[!UICONTROL Basic]** . Selecteer **[!UICONTROL Form Data Model Prefill Service]** in de service Prefill.
1. Klik op **[!UICONTROL Done]**. Uw adaptieve formulier is nu geconfigureerd voor vooraf invullen van formuliergegevensmodel. U kunt nu, de [ regelredacteur ](rule-editor.md) gebruiken om regels tot stand te brengen om gebieden van de vorm vooraf in te vullen.

## Eigenschappen van formuliermodellen bewerken in een adaptief formulier {#edit-form-model}

1. Selecteer de Aangepaste Vorm en selecteer ![ informatie van de Pagina ](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Open Properties]**. De pagina Formuliereigenschappen wordt geopend.

1. Ga naar het tabblad **[!UICONTROL Form Model]** en kies een formuliermodel. Als het adaptieve formulier geen formuliermodel heeft, hebt u de vrijheid om een JSON-schema of een FDM-formuliergegevensmodel te kiezen. Als het adaptieve formulier echter al is gebaseerd op een formuliermodel, kunt u overschakelen op een ander formuliermodel van hetzelfde type. Als het formulier bijvoorbeeld een JSON-schema gebruikt, kunt u gemakkelijk overschakelen naar een ander JSON-schema. Op dezelfde manier kunt u overschakelen naar een ander FDM-model (Form Data Model) als het formulier een FDM-formulier gebruikt.

1. Selecteer **[!UICONTROL Save]** om de eigenschappen op te slaan.


## Hoe wijzigt u de naam van een AEM adaptief formulier? {#rename-an-AEM-Adaptive-Form}

Voer de volgende stappen uit om de naam van een adaptief formulier te wijzigen:

1. Selecteer een adaptief formulier in uw AEM Forms-gebruikersinterface.
1. Klik op **Eigenschappen** die op de hogere spoorstaaf wordt gevestigd.
1. Verander de naam van de vorm op het **lusje van de Titel**, zoals aangetoond in het hieronder beeld.
1. Klik **sparen en Sluiten**.

![ noem een AEM Aanpassings Vorm ](/help/forms/assets/change-af-name.png) anders

<!--

## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)

-->

## Zie ook {#see-also}

{{see-also}}
* [Dynamisch gedrag toevoegen aan formulieren met de regeleditor](/help/forms/rule-editor-core-components.md)
* [Formulierindeling instellen voor verschillende schermgrootten en apparaattypen](/help/sites-cloud/authoring/page-editor/responsive-layout.md)

