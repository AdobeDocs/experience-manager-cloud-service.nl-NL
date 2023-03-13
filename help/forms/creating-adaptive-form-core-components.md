---
title: Hoe maakt u een adaptief formulier?
description: Leer hoe u een adaptief formulier maakt met [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op het maken van een adaptief formulier op basis van een formuliergegevensmodel en een XML- of JSON-schema.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
source-git-commit: ae208e9ac35c3c464d9beeaa3bc2bddc0ecf52bb
workflow-type: tm+mt
source-wordcount: '1423'
ht-degree: 0%

---


# Een adaptief formulier maken (kerncomponenten) {#creating-an-adaptive-form-core-components}

Met Adaptieve Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke wizard voor zakelijke gebruikers om snel een Adaptive Forms te maken. De wizard beschikt over een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde componenten voor het vastleggen van gegevens. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe raadt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [Aangepaste Forms Foundation-componenten](creating-adaptive-form.md): Dit zijn klassieke (oude) componenten voor gegevensvastlegging. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Adobe raadt u aan nieuwe formulieren te gebruiken als u nieuwe formulieren maakt  [Adaptieve Forms Core-componenten](creating-adaptive-form-core-components.md) om een Adaptieve Forms te maken.

![Wizard voor het maken van een adaptief formulier](/help/release-notes/assets/wizard.png)


## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* **Adaptieve Forms Core-componenten inschakelen voor uw omgeving**: Wanneer u een nieuw programma maakt, zijn de Adaptive Forms Core Components al ingeschakeld voor uw omgeving. Als u een as a Cloud Service Forms-omgeving hebt die is gebaseerd op Archetype 39 of eerder, [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](setup-local-development-environment.md#enable-adaptive-forms-core-components-for-an-existing-aem-archetype-based-project). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon en canvasthema worden toegevoegd aan uw omgeving.

* **Een adaptieve formuliersjabloon**: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. Bijvoorbeeld, verzendend de verzamelde gegevens naar een gegevensbron. De cloudservice biedt een OOTB-sjabloon met de naam blank:

   * De `blank` de sjabloon wordt bij elk nieuw as a Cloud Service AEM Forms-programma meegeleverd.
   * U kunt het referentiepakket installeren via Package Manager om het `blank` template naar uw as a Cloud Service AEM Forms-programma.
   * U kunt ook [een nieuwe adaptieve Forms-sjabloon maken (Core Components)](template-editor.md) helemaal niet.

* **Een adaptief formulierthema**: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  De `Canvas` de sjabloon wordt bij elk nieuw as a Cloud Service AEM Forms-programma meegeleverd.

   <!-- * You can install the reference package, via package manager, to add the `Canvas` template to your AEM Forms as a Cloud Service program.
    * You can also [create a new Adaptive Forms theme (Core Components)](template-editor.md) and deploy it to your AEM Forms as a Cloud Service program. -->

* **Machtigingen**: Gebruikers toevoegen aan [!DNL forms-users] groep. De leden van de [!DNL forms-users] groep heeft machtigingen om een adaptief formulier te maken. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).


## Een adaptief formulier maken (kerncomponenten) {#create-an-adaptive-form-core-components}

1. Aanmelden bij uw [!DNL Experience Manager Forms] Instantie van auteur. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

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

Nu kunt u de container Adaptive Forms Core Components naar Adaptive Forms slepen om het formulier te ontwerpen en te maken.

## Beschikbare adaptieve Forms Core-componenten

Adaptieve Forms Core-componenten zijn gestandaardiseerde componenten voor het vastleggen van gegevens. Deze componenten bieden aanpassingsmogelijkheden, helpen de ontwikkelingstijd te verminderen en lagere onderhoudskosten voor uw digitale inschrijving. [Adaptive Forms Core Components documentatie](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en) bevat een gedetailleerde lijst met beschikbare componenten, samen met gedetailleerde informatie over de mogelijkheden van elke component. U kunt ook [https://aemcomponents.dev/](https://aemcomponents.dev/) om beschikbare kerncomponenten in actie te bekijken.

## Eigenschappen van een formuliermodel bewerken in een adaptief formulier {#edit-form-model}

1. Selecteer het adaptieve formulier en tik op ![Pagina-informatie](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Open Properties]**. De pagina Formuliereigenschappen wordt geopend.

1. Ga naar de **[!UICONTROL Form Model]** en kiest u een formuliermodel. Als het adaptieve formulier geen formuliermodel heeft, hebt u de vrijheid om een JSON-schema of een formuliergegevensmodel te kiezen. Als het adaptieve formulier echter al is gebaseerd op een formuliermodel, kunt u overschakelen op een ander formuliermodel van hetzelfde type. Als het formulier bijvoorbeeld een JSON-schema gebruikt, kunt u eenvoudig overschakelen naar een ander JSON-schema. Op dezelfde manier kunt u overschakelen naar een ander formuliergegevensmodel als het formulier een formuliergegevensmodel gebruikt.

1. Tikken **[!UICONTROL Save]** om de eigenschappen op te slaan.
