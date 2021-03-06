---
title: Metagegevensschema van map
description: Leer hoe u een metagegevensschema voor middelenmappen maakt in [!DNL Experience Manager Assets]
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: c86760ed-169d-40f7-91a4-8aee449b286c
source-git-commit: 7ea0e6c2d277199fc5216aab70e587bd23ac6baa
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 5%

---

# Metagegevensschema van map {#folder-metadata-schema}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u metagegevensschema&#39;s maken voor middelenmappen, waarmee de lay-out en de metagegevens worden gedefinieerd die op pagina&#39;s met mapeigenschappen worden weergegeven.

## Een schema voor metagegevens van een map toevoegen {#add-a-folder-metadata-schema-form}

Met de Forms-editor voor het schema Metagegevens van map kunt u metagegevensschema&#39;s voor mappen maken en bewerken.

1. Tik/klik op de knop [!DNL Experience Manager] logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]**.
1. Tik/klik op de pagina Forms van het schema met metagegevens van de map **[!UICONTROL Create]**.
1. Geef een naam voor het formulier op en tik/klik op **[!UICONTROL Create]**. Het nieuwe schema formulier wordt weergegeven op de pagina Schema Forms.

## Formulieren met metagegevens van mappen bewerken {#edit-folder-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken, dat het volgende bevat:

* Tabs
* Formulieritems in tabbladen.

U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte. U kunt nieuwe tabbladen of formulieritems toevoegen aan het metagegevensschemaformulier.

1. Selecteer op de pagina Schema Forms het formulier dat u hebt gemaakt en tik op de knop **[!UICONTROL Edit]** op de werkbalk.
1. Tik of klik op de pagina in de Editor van het schema voor metagegevens van de map op de knop **[!UICONTROL +]** pictogram om een tabblad aan het formulier toe te voegen. Als u de naam van het tabblad wilt wijzigen, tikt u op de standaardnaam of klikt u erop en geeft u de nieuwe naam op onder **[!UICONTROL Settings]**.

   ![custom_tab](assets/custom_tab.png)

   Tik of klik op de knop **[!UICONTROL +]** pictogram. Tikken/klikken **[!UICONTROL X]** om een tabblad te verwijderen.

1. Voeg op het actieve tabblad een of meer componenten van het tabblad **[!UICONTROL Build Form]** tab.

   ![adding_components](assets/adding_components.png)

   Als u meerdere tabbladen maakt, tikt of klikt u op een bepaald tabblad om componenten toe te voegen.

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan in het dialoogvenster **[!UICONTROL Settings]** tab.

   Verwijder indien nodig een component uit het dialoogvenster **[!UICONTROL Settings]** tab.

   ![configure_properties](assets/configure_properties.png)

1. Tikken/klikken **[!UICONTROL Save]** op de werkbalk om de wijzigingen op te slaan.

### Componenten om formulieren te maken {#components-to-build-forms}

De **[!UICONTROL Build Form]** wordt een lijst weergegeven met formulieritems die u in het metagegevensschema van uw map gebruikt. De **[!UICONTROL Settings]** worden de kenmerken weergegeven van elk item dat u selecteert in het dialoogvenster **[!UICONTROL Build Form]** tab. Hier volgt een lijst met formulieritems die beschikbaar zijn in het dialoogvenster **[!UICONTROL Build Form]** tab:

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
   <td><p>Tekst met ????n regel</p> </td>
   <td><p> Voeg een teksteigenschap voor ????n regel toe. De eigenschap wordt opgeslagen als een tekenreeks.</p> </td>
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
   <td><p>Date</p> </td>
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

Als u de eigenschappen van formulieritems wilt bewerken, tikt u op de component of klikt u op de component en bewerkt u alle eigenschappen of een subset van de volgende eigenschappen in het dialoogvenster **[!UICONTROL Settings]** tab. Het wordt aanbevolen slechts ????n veld toe te wijzen aan een bepaalde eigenschap in het metagegevensschema. Anders wordt het laatst toegevoegde veld dat aan de eigenschap is toegewezen, door het systeem gekozen.

**[!UICONTROL Field Label]**: De naam van de eigenschap metadata die wordt weergegeven op de eigenschappenpagina voor de map.

**[!UICONTROL Map to Property]**: This property specifies the relative path of the folder node in the CRX repository where it is saved. Het begint met &quot;**./**&quot;, hetgeen aangeeft dat het pad zich onder het knooppunt van de map bevindt.

Hier volgen voorbeelden van geldige waarden voor een eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metagegevensknooppunt van de map opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: Hiermee slaat u de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, raadt Adobe u aan ze als [!UICONTROL Disable Edit].

Neem geen spatie op in het eigenschapspad om ervoor te zorgen dat de component correct wordt weergegeven in het schema voor metagegevens.

**[!UICONTROL JSON Path]**: Gebruik deze optie om het pad van het JSON-bestand op te geven waarin u sleutelwaardeparen voor opties opgeeft.

**[!UICONTROL Placeholder]**: Gebruik deze eigenschap om relevante plaatsaanduidingstekst met betrekking tot de eigenschap metadata op te geven.

**[!UICONTROL Choices]**: Gebruik deze eigenschap om keuzen in een lijst op te geven.

**[!UICONTROL Description]**: Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.

**[!UICONTROL Class]**: Objectklasse waaraan de eigenschap is gekoppeld.

## Formulieren met metagegevens van mappen verwijderen {#delete-folder-metadata-schema-forms}

U kunt de schemaformulieren van de omslagmeta-gegevens van het Schema Forms van de Meta-gegevens van de Omslag schrappen pagina. Als u een formulier wilt verwijderen, selecteert u het en tikt of klikt u op het pictogram Verwijderen op de werkbalk.

![delete_form](assets/delete_form.png)

## Een schema voor metagegevens van mappen toewijzen {#assign-a-folder-metadata-schema}

U kunt een schema van omslagmeta-gegevens aan een omslag of van de pagina van Forms van het Schema van Meta-gegevens van de Omslag toewijzen of wanneer het cre??ren van een omslag.

Als u een metagegevensschema voor een map configureert, wordt het pad naar het schema opgeslagen in het dialoogvenster `folderMetadataSchema` eigenschap van het mapknooppunt onder .*/jcr:content*.

### Wijs aan een schema van de pagina van het Schema van Meta-gegevens van de Omslag toe {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Tik/klik op de knop [!DNL Experience Manager] logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]**> **[!UICONTROL Folder Metadata Schemas]**.
1. Selecteer op de pagina Forms van het schema Metagegevens map het schema dat u op een map wilt toepassen.
1. Tik/klik op de werkbalk **[!UICONTROL Apply to Folder(s)]**.

1. Selecteer de map waarop u het schema wilt toepassen en klik/tik op **[!UICONTROL Apply]**. Als er al een metagegevensschema op de map is toegepast, verschijnt er een waarschuwingsbericht dat u het bestaande metagegevensschema wilt overschrijven. Tik of klik op **[!UICONTROL Overwrite]**.
1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.

   ![folder_properties](assets/folder_properties.png)

   Tik of klik op het tabblad **[!UICONTROL Folder Metadata]** om de velden met metadata van de map weer te geven.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Een schema toewijzen bij het maken van een map {#assign-a-schema-when-creating-a-folder}

U kunt een schema van omslagmeta-gegevens toewijzen wanneer het cre??ren van een omslag. Als het systeem ten minste ????n schema voor metagegevens van de map bevat, wordt een extra lijst weergegeven in het dialoogvenster **[!UICONTROL Create Folder]** . U kunt het gewenste schema selecteren. Standaard is geen schema geselecteerd.

1. Van de [!DNL Experience Manager Assets] gebruikersinterface, tikken/klikken **[!UICONTROL Create]** op de werkbalk.
1. Geef een titel en naam voor de map op.
1. Selecteer het gewenste schema in de lijst Metagegevensschema van map. Tik vervolgens/klik op **[!UICONTROL Create]**.

   ![select_schema](assets/select_schema.png)

1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.
1. Tik of klik op het tabblad **[!UICONTROL Folder Metadata]** om de velden met metadata van de map weer te geven.

## Het schema voor metagegevens van de map gebruiken {#use-the-folder-metadata-schema}

Open de eigenschappen voor een map die met een mapmetadataschema is geconfigureerd. Er wordt een tabblad **[!UICONTROL Folder Metadata]** weergegeven op de pagina met mapeigenschappen. Selecteer dit tabblad om het formulier van het mapmetadataschema weer te geven.

Geef waarden voor metagegevens op in de verschillende velden en tik/klik op **[!UICONTROL Save]** om de waarden op te slaan. De waarden die u opgeeft, worden opgeslagen in het mapknooppunt in de CRX-opslagruimte.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)
