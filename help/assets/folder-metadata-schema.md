---
title: Metagegevensschema van map
description: Leer hoe te om meta-gegevensschema voor activaomslagen in te creëren  [!DNL Experience Manager Assets]
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: c86760ed-169d-40f7-91a4-8aee449b286c
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 3%

---

# Metagegevensschema van map {#folder-metadata-schema}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Met [!DNL Adobe Experience Manager Assets] kunt u metagegevensschema&#39;s maken voor middelenmappen, waarmee de lay-out en de metagegevens worden gedefinieerd die op de pagina&#39;s met mapeigenschappen worden weergegeven.

## Een schema voor mapmetagegevens toevoegen {#add-a-folder-metadata-schema-form}

Met de Forms-editor voor het schema Metagegevens van map kunt u metagegevensschema&#39;s voor mappen maken en bewerken.

1. Selecteer het [!DNL Experience Manager] -logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]** .
1. Selecteer **[!UICONTROL Create]** op de pagina Forms van het schema Metagegevens van map.
1. Geef een naam op voor het formulier en selecteer **[!UICONTROL Create]** . Het nieuwe schema formulier wordt weergegeven op de pagina Schema Forms.

## Formulieren met metagegevens van mappen bewerken {#edit-folder-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken, dat het volgende bevat:

* Tabs
* Formulieritems in tabbladen.

U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagplaats. U kunt nieuwe tabbladen of formulieritems toevoegen aan het metagegevensschema.

1. Selecteer op de pagina Schema Forms het formulier dat u hebt gemaakt en selecteer vervolgens het pictogram **[!UICONTROL Edit]** op de werkbalk.
1. Selecteer op de pagina van de Editor voor het metagegevensschema van de map het pictogram **[!UICONTROL +]** om een tabblad aan het formulier toe te voegen. Als u de naam van het tabblad wilt wijzigen, selecteert u de standaardnaam en geeft u de nieuwe naam op onder **[!UICONTROL Settings]** .

   ![ custom_tab ](assets/custom_tab.png)

   Selecteer het pictogram **[!UICONTROL +]** als u meer tabbladen wilt toevoegen. Selecteer **[!UICONTROL X]** om een tabblad te verwijderen.

1. Voeg op het actieve tabblad een of meer componenten toe vanaf het tabblad **[!UICONTROL Build Form]** .

   ![ adding_components ](assets/adding_components.png)

   Als u meerdere tabbladen maakt, selecteert u een bepaald tabblad om componenten toe te voegen.

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** .

   Verwijder zo nodig een component van het tabblad **[!UICONTROL Settings]** .

   ![ configure_properties ](assets/configure_properties.png)

1. Selecteer **[!UICONTROL Save]** op de werkbalk om de wijzigingen op te slaan.

### Componenten om formulieren te maken {#components-to-build-forms}

Het tabblad **[!UICONTROL Build Form]** bevat formulieritems die u in het metagegevensschema van uw map gebruikt. Op het tabblad **[!UICONTROL Settings]** worden de kenmerken weergegeven voor elk item dat u selecteert op het tabblad **[!UICONTROL Build Form]** . Hier volgt een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Build Form]** :

<table>
 <tbody>
  <tr>
   <td><p><strong>Componentnaam</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Sectiekop</p> </td>
   <td><p> Voeg een sectiekopje toe voor een lijst met gangbare componenten.</p> </td>
  </tr>
  <tr>
   <td><p>Tekst met één regel</p> </td>
   <td><p> Voeg een teksteigenschap voor één regel toe. De eigenschap wordt opgeslagen als een tekenreeks.</p> </td>
  </tr>
  <tr>
   <td><p>Meerdere waardetekst</p> </td>
   <td><p> Voeg een teksteigenschap voor meerdere waarden toe. Deze wordt opgeslagen als een tekenreeks-array.</p> </td>
  </tr>
  <tr>
   <td><p>Getal</p> </td>
   <td><p> Voeg een getalcomponent toe.</p> </td>
  </tr>
  <tr>
   <td><p>Datum</p> </td>
   <td><p> Voeg een datumcomponent toe.</p> </td>
  </tr>
  <tr>
   <td><p>Vervolgkeuzelijst</p> </td>
   <td><p> Voeg een vervolgkeuzelijst toe.</p> </td>
  </tr>
  <tr>
   <td><p>Standaardlabels</p> </td>
   <td><p> Voeg een tag toe. </p> </td>
  </tr>
  <tr>
   <td><p>Verborgen veld</p> </td>
   <td><p> Voeg een verborgen veld toe. Deze wordt als een POST-parameter verzonden wanneer het element wordt opgeslagen.</p> </td>
  </tr>
 </tbody>
</table>

### Formulieritems bewerken {#editing-form-items}

Als u de eigenschappen van formulieritems wilt bewerken, selecteert u de component en bewerkt u alle of een subset van de volgende eigenschappen op het tabblad **[!UICONTROL Settings]** . Het wordt aanbevolen slechts één veld toe te wijzen aan een bepaalde eigenschap in het metagegevensschema. Anders wordt het laatst toegevoegde veld dat aan de eigenschap is toegewezen, door het systeem gekozen.

**[!UICONTROL Field Label]**: De naam van de eigenschap metadata die wordt weergegeven op de pagina met eigenschappen voor de map.

**[!UICONTROL Map to Property]**: Deze eigenschap geeft het relatieve pad aan van het mapknooppunt in de CRX-opslagplaats waar het wordt opgeslagen. Het begint met &quot;**./**&quot;, wat aangeeft dat het pad zich onder het knooppunt van de map bevindt.

Hier volgen voorbeelden van geldige waarden voor een eigenschap:

* `./jcr:content/metadata/dc:title`: slaat de waarde op in het metagegevensknooppunt van de map als de eigenschap `dc:title` .

* `./jcr:created`: slaat de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, wordt u aangeraden deze als [!UICONTROL Disable Edit] te markeren.

Neem geen spatie op in het eigenschapspad om ervoor te zorgen dat de component correct wordt weergegeven in het schema voor metagegevens.

**[!UICONTROL JSON Path]**: gebruik deze optie om het pad van het JSON-bestand op te geven, waarin u sleutelwaardeparen voor opties opgeeft.

**[!UICONTROL Placeholder]**: gebruik deze eigenschap om relevante plaatsaanduidingstekst op te geven met betrekking tot de eigenschap metadata.

**[!UICONTROL Choices]**: Gebruik deze eigenschap om keuzen in een lijst op te geven.

**[!UICONTROL Description]**: Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.

**[!UICONTROL Class]**: Object-klasse waaraan de eigenschap is gekoppeld.

## Formulieren met metagegevens van mappen verwijderen {#delete-folder-metadata-schema-forms}

U kunt de schemaformulieren van de omslagmeta-gegevens van het Schema Forms van de Meta-gegevens van de Omslag schrappen pagina. Als u een formulier wilt verwijderen, selecteert u het en selecteert u het pictogram Verwijderen op de werkbalk.

![ delete_form ](assets/delete_form.png)

## Een schema voor metagegevens van mappen toewijzen {#assign-a-folder-metadata-schema}

U kunt een schema van omslagmeta-gegevens aan een omslag of van de pagina van Forms van het Schema van Meta-gegevens van de Omslag toewijzen of wanneer het creëren van een omslag.

Als u een metagegevensschema voor een map configureert, wordt het pad naar het schemaformulier opgeslagen in de eigenschap `folderMetadataSchema` van het mapknooppunt onder.*/jcr:content* .

### Wijs aan een schema van de pagina van het Schema van Meta-gegevens van de Omslag toe {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Selecteer het [!DNL Experience Manager] -logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]** .
1. Selecteer op de pagina Forms van het schema Metagegevens map het schema dat u op een map wilt toepassen.
1. Selecteer **[!UICONTROL Apply to Folders]** in de werkbalk.

1. Selecteer de map waarop u het schema wilt toepassen en selecteer vervolgens **[!UICONTROL Apply]** . Als er al een metagegevensschema op de map is toegepast, verschijnt er een waarschuwingsbericht dat u het bestaande metagegevensschema wilt overschrijven. Selecteer **[!UICONTROL Overwrite]** .
1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.

   ![ folder_properties ](assets/folder_properties.png)

   Selecteer de tab **[!UICONTROL Folder Metadata]** om de velden met metagegevens van de map weer te geven.

   ![ folder_metadata_properties ](assets/folder_metadata_properties.png)

### Een schema toewijzen bij het maken van een map {#assign-a-schema-when-creating-a-folder}

U kunt een schema van omslagmeta-gegevens toewijzen wanneer het creëren van een omslag. Als het systeem ten minste één schema voor metagegevens van de map bevat, wordt een extra lijst weergegeven in het dialoogvenster **[!UICONTROL Create Folder]** . U kunt het gewenste schema selecteren. Standaard is geen schema geselecteerd.

1. Selecteer **[!UICONTROL Create]** in de werkbalk van de gebruikersinterface van [!DNL Experience Manager Assets] .
1. Geef een titel en naam voor de map op.
1. Selecteer het gewenste schema in de lijst Metagegevensschema van map. Selecteer vervolgens **[!UICONTROL Create]** .

   ![ select_schema ](assets/select_schema.png)

1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.
1. Selecteer de tab **[!UICONTROL Folder Metadata]** om de velden met metagegevens van de map weer te geven.

## Het schema voor metagegevens van de map gebruiken {#use-the-folder-metadata-schema}

Open de eigenschappen voor een map die met een mapmetadataschema is geconfigureerd. Er wordt een tabblad **[!UICONTROL Folder Metadata]** weergegeven op de pagina met mapeigenschappen. Selecteer dit tabblad om het formulier van het mapmetadataschema weer te geven.

Voer waarden in voor de metagegevens in de verschillende velden en selecteer **[!UICONTROL Save]** om de waarden op te slaan. De waarden die u opgeeft, worden opgeslagen in het mapknooppunt in de CRX-opslagplaats.

![ folder_metadata_properties-1 ](assets/folder_metadata_properties-1.png)

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
