---
title: Hoe maakt u een adaptief formulier?
description: 'Leer hoe u een adaptief formulier maakt met [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op het maken van een adaptief formulier op basis van een formuliergegevensmodel en een XML- of JSON-schema. '
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1444'
ht-degree: 0%

---

# Een adaptief formulier maken {#creating-an-adaptive-form}

Met Adaptieve Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. [!DNL AEM Forms] biedt een intuïtieve gebruikersinterface en kant-en-klare componenten voor het maken en werken met Adaptive Forms. U kunt desgewenst een adaptief formulier maken op basis van een formuliermodel of -schema of zonder formuliermodel. Het is belangrijk om zorgvuldig het formuliermodel te kiezen dat niet alleen aan uw vereisten voldoet, maar ook uw bestaande infrastructurele investeringen en middelen uitbreidt. U kunt uit de volgende opties kiezen om een adaptief formulier te maken:

* **Een formuliergegevensmodel gebruiken**
   [Gegevensintegratie](data-integration.md) Hiermee kunt u entiteiten en services integreren van verschillende gegevensbronnen in een formuliergegevensmodel dat u kunt gebruiken voor het maken van een adaptieve Forms. Kies Formuliergegevensmodel als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

   <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. -->

* **Een XML-schemadefinitie (XSD) of een JSON-schema gebruiken**
De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de browser Inhoud wanneer u Adaptief Forms maakt.

* **Geen of geen formuliermodel gebruiken**
Voor adaptieve Forms die met deze optie is gemaakt, wordt geen formuliermodel gebruikt. De XML-gegevens die op basis van dergelijke formulieren worden gegenereerd, hebben een vlakke structuur met velden en bijbehorende waarden.

## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* Een adaptieve formuliersjabloon. Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten U kunt [een nieuwe sjabloon maken](template-editor.md), een bestaande sjabloon importeren of een sjabloon downloaden en importeren [voorbeeldsjablonen](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:3f89abe1-0ece-492a-b5af-57c73badad52).
* Een adaptief formulierthema. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. U kunt [een nieuw thema maken](themes.md), [een bestaand thema importeren](import-export-forms-templates.md#uploading-a-theme)of download en importeer enkele [voorbeeldthema&#39;s](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:2779f80e-16ba-4cd1-a96f-8e2b53f3be25).
* Gebruikers toevoegen aan [!DNL forms-users] om hun machtigingen te verlenen voor het maken van een adaptief formulier. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

## Een adaptief formulier maken {#strong-create-an-adaptive-form-strong}

Ga als volgt te werk om een adaptief formulier te maken.

1. Toegang [!DNL Experience Manager Forms] Instantie van auteur. Dit kan een Cloud-instantie of een lokale ontwikkelingsinstantie zijn.

1. Ga uw geloofsbrieven op de Experience Manager login pagina in.

   Tik in de linkerbovenhoek nadat u bent aangemeld op **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Tikken **[!UICONTROL Create]** en selecteert u **[!UICONTROL Adaptive Form]**. Selecteer een sjabloon en tik op **[!UICONTROL Next]**.
1. Een optie voor **[!UICONTROL Add Properties]** wordt weergegeven. Geef de waarden op voor de volgende eigenschapvelden. De velden Titel en Naam zijn verplicht:

   * **[!UICONTROL Title:]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in het dialoogvenster [!DNL Experience Manager Forms] gebruikersinterface.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Description:]** Hier geeft u gedetailleerde informatie over het formulier op.
   * **[!UICONTROL Tags:]** Hiermee geeft u codes op om het adaptieve formulier op unieke wijze te identificeren. Tags helpen u bij het zoeken naar het formulier. Als u tags wilt maken, typt u nieuwe tagnamen in het dialoogvenster **[!UICONTROL Tags]** doos.

1. U kunt een adaptief formulier maken op basis van een van de volgende formuliermodellen:

   * [Formuliergegevensmodel](#fdm)

   <!--* [XFA form template](#create-an-adaptive-form-based-on-an-xfa-form-template)-->
   * [XML- of JSON-schema](#create-an-adaptive-form-based-on-xml-or-json-schema)
   * Geen of geen formuliermodel

   U kunt deze configureren vanuit de **[!UICONTROL Form Model]** op het tabblad **[!UICONTROL Add Properties]** pagina. Standaard is het geselecteerde formuliermodel **[!UICONTROL None]**.

1. Tik op **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking.

1. Tikken **[!UICONTROL Open]** om het nieuwe formulier te openen op een nieuw tabblad. Het formulier wordt geopend voor bewerking en geeft de inhoud weer die beschikbaar is in de sjabloon. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen aan de behoeften.

   Op basis van het type adaptief formulier worden de formulierelementen in het bijbehorende formulier <!--XFA form template, -->XML-schema of JSON-schema worden weergegeven in het dialoogvenster **[!UICONTROL Data Model Objects]** tabblad van het dialoogvenster **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken.

## Een adaptief formulier maken op basis van een formuliergegevensmodel {#fdm}

[Gegevensintegratie](data-integration.md) Hiermee kunt u meerdere gegevensbronnen integreren en hun entiteiten en services samenbrengen om een formuliergegevensmodel te maken. Het is een uitbreiding van het JSON-schema. Met een formuliergegevensmodel kunt u een adaptief formulier maken. De entiteiten of gegevensmodelobjecten die in een formuliergegevensmodel zijn geconfigureerd, zijn beschikbaar als gegevensmodelobjecten voor het ontwerpen van formulieren. Zij zijn gebonden aan de respectieve gegevensbronnen en worden gebruikt om een formulier vooraf in te vullen en ingediende gegevens terug te schrijven naar de respectieve gegevensbronnen. U kunt de diensten ook roepen die in een Model van de Gegevens van de Vorm worden gevormd gebruikend de Adaptieve regels van de Vorm.

Een formuliergegevensmodel gebruiken voor het maken van een adaptief formulier:

1. Selecteer op het tabblad Formuliermodel in het scherm Eigenschappen toevoegen de optie **[!UICONTROL Form Data Model]** in de **[!UICONTROL Select From]** vervolgkeuzelijst.

   ![Een adaptief formulier maken](assets/create-af-1-1.png)

1. Tik om uit te breiden **[!UICONTROL Select Form Data Model]**. Alle beschikbare formuliergegevensmodellen worden weergegeven. Selecteer een gegevensmodel.

>[!NOTE]
>
>U kunt ook het formuliergegevensmodel wijzigen voor een adaptief formulier. Voor gedetailleerde stappen raadpleegt u [Eigenschappen van een formuliermodel bewerken in een adaptief formulier](#edit-form-model).

## Een adaptief formulier maken op basis van het XML- of JSON-schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt een schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar op het tabblad Gegevensmodelobject van de inhoudbrowser voor het ontwerpen van Adaptief Forms. U kunt de schema-elementen slepen en neerzetten om het formulier samen te stellen.

Raadpleeg de volgende documenten voor informatie over het ontwerpen van XML- of JSON-schema voor het ontwerpen van Adaptive Forms.

* [Adaptieve Forms maken met XML-schema](adaptive-form-xml-schema-form-model.md)
* [Adaptieve Forms maken met JSON-schema](adaptive-form-json-schema-form-model.md)

Ga als volgt te werk om het XML- of JSON-schema te gebruiken als formuliermodel voor een adaptief formulier:

1. Op de **[!UICONTROL Add Properties]** tikken op de pagina Adaptief formulier maken **[!UICONTROL Form Model]** tab.
1. Selecteer op het tabblad Formuliermodel de optie **[!UICONTROL Schema]** van de **[!UICONTROL Select From]** vervolgkeuzelijst.

1. Tikken **[!UICONTROL Select Schema]** en voer een van de volgende handelingen uit:

   * **[!UICONTROL Upload from disk]** - Selecteer deze optie en tik op Schemadefinitie uploaden om een XML-schema of JSON-schema te zoeken en te uploaden vanuit uw bestandssysteem. Het geüploade schemabestand bevindt zich bij het formulier en is niet toegankelijk voor andere adaptieve Forms.
   * **[!UICONTROL Search in repository]** - Selecteer deze optie om een keuze te maken uit de lijst met schemadefinitiebestanden in de gegevensopslagruimte. Selecteer het XML- of JSON-schemabestand als formuliermodel. Het geselecteerde schema is gekoppeld aan het formulier via verwijzing en is toegankelijk voor gebruik in andere adaptieve Forms.

      Zorg ervoor dat de bestandsnaam van het JSON-schema eindigt met **.schema.json**. Bijvoorbeeld: mySchema.schema.json
   ![XML- of JSON-schema selecteren](assets/upload-schema.png)
   **Afbeelding:** *XML- of JSON-schema selecteren*

1. (Alleen voor het XML-schema) Nadat u een XML-schema hebt geselecteerd of geüpload, geeft u een hoofdelement op van het geselecteerde XSD-bestand dat u wilt toewijzen met het adaptieve formulier.

   ![XSD-hoofdelement selecteren](assets/xsd-root-element.png)
   **Afbeelding:** *XSD-hoofdelement selecteren*

>[!NOTE]
>
>U kunt het schema ook wijzigen voor een adaptief formulier. Voor gedetailleerde stappen raadpleegt u [Eigenschappen van een formuliermodel bewerken in een adaptief formulier](#edit-form-model).

## Eigenschappen van een formuliermodel bewerken in een adaptief formulier {#edit-form-model}

Adaptieve Forms worden gemaakt zonder formuliermodel (met de optie Geen voor formuliermodel) of met een formuliermodel zoals een <!-- form template, --> XML-schema of JSON-schema of formuliergegevensmodel. U kunt het formuliermodel voor een adaptief formulier wijzigen van Geen in een ander formuliermodel. Voor Adaptief formulier op basis van een formuliermodel kunt u een ander formulier kiezen <!-- form template,--> XML-schema, JSON-schema of formuliergegevensmodel voor hetzelfde formuliermodel. U kunt echter niet van het ene formuliermodel naar het andere gaan.

1. Selecteer het adaptieve formulier en tik op de knop **Eigenschappen** pictogram.
1. Open de **[!UICONTROL Form Model]** en voert u een van de volgende handelingen uit.

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een ander formuliermodel kiezen en dienovereenkomstig <!-- a form template, --> XML- of JSON-schema of formuliergegevensmodel.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u een ander formulier kiezen <!-- form template, --> XML- of JSON-schema of Formuliergegevensmodel voor hetzelfde formuliermodel.

1. Tikken **[!UICONTROL Save]** om de eigenschappen op te slaan.
