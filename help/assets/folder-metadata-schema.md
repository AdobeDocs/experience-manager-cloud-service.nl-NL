---
title: Metagegevensschema van map
description: Leer hoe u een metagegevensschema voor elementmappen maakt in [!DNL Experience Manager Assets]
contentOwner: AG
translation-type: tm+mt
source-git-commit: 3207151a76c51637551907d15a34f1a6b7450d02
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 5%

---


# Metagegevensschema van map {#folder-metadata-schema}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u metagegevensschema&#39;s maken voor middelenmappen, waarmee de lay-out en de metagegevens worden gedefinieerd die op pagina&#39;s met mapeigenschappen worden weergegeven.

## Een schema voor metagegevens van een map toevoegen {#add-a-folder-metadata-schema-form}

Met de Forms-editor voor het schema Metagegevens van map kunt u metagegevensschema&#39;s voor mappen maken en bewerken.

1. Tik/klik op het [!DNL Experience Manager]-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]**.
1. Tik/klik op **[!UICONTROL Create]** in de pagina Forms van het schema Metagegevens map.
1. Geef een naam voor het formulier op en tik/klik op **[!UICONTROL Create]**. Het nieuwe schema formulier wordt weergegeven op de pagina Schema Forms.

## Schema-formulieren voor mapmetagegevens bewerken {#edit-folder-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken, dat het volgende bevat:

* Tabs
* Formulieritems in tabbladen.

U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte. U kunt nieuwe tabbladen of formulieritems toevoegen aan het metagegevensschemaformulier.

1. Selecteer op de pagina Schema Forms het formulier dat u hebt gemaakt en tik op het pictogram **[!UICONTROL Edit]** op de werkbalk.
1. Tik of klik op het pictogram **[!UICONTROL +]** op de pagina Editor van het metagegevensschema van de map om een tabblad aan het formulier toe te voegen. Als u de naam van het tabblad wilt wijzigen, tikt u op de standaardnaam of klikt u erop en geeft u de nieuwe naam op onder **[!UICONTROL Settings]**.

   ![custom_tab](assets/custom_tab.png)

   Tik op het pictogram **[!UICONTROL +]** om meer tabbladen toe te voegen. Tik/klik op **[!UICONTROL X]** om een tab te verwijderen.

1. Voeg op het actieve tabblad een of meer componenten toe vanaf het tabblad **[!UICONTROL Build Form]**.

   ![adding_components](assets/adding_components.png)

   Als u meerdere tabbladen maakt, tikt of klikt u op een bepaald tabblad om componenten toe te voegen.

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**.

   Verwijder zo nodig een component van het tabblad **[!UICONTROL Settings]**.

   ![configure_properties](assets/configure_properties.png)

1. Tik/klik op **[!UICONTROL Save]** op de werkbalk om de wijzigingen op te slaan.

### Componenten voor het samenstellen van formulieren {#components-to-build-forms}

Het tabblad **[!UICONTROL Build Form]** bevat formulieritems die u in het schema voor metagegevens van uw map gebruikt. Het **[!UICONTROL Settings]** lusje toont de attributen voor elk punt dat u op **[!UICONTROL Build Form]** tabel selecteert. Hier volgt een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Build Form]**:

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

Als u de eigenschappen van formulieritems wilt bewerken, tikt u op de component of klikt u op de component en bewerkt u alle of een subset van de volgende eigenschappen op het tabblad **[!UICONTROL Settings]**.

**[!UICONTROL Field Label]**: De naam van de eigenschap metadata die wordt weergegeven op de eigenschappenpagina voor de map.

**[!UICONTROL Map to Property]**: This property specifies the relative path of the folder node in the CRX repository where it is saved. Het begint met &quot;**./**&quot;, wat aangeeft dat het pad zich onder het knooppunt van de map bevindt.

Hier volgen de geldige waarden voor deze eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metagegevensknooppunt van de map opgeslagen als de eigenschap  `dc:title`.

* `./jcr:created`: Hiermee slaat u de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, raadt Adobe u aan deze als [!UICONTROL Disable Edit] te markeren.

Neem geen spatie op in het eigenschapspad om ervoor te zorgen dat de component correct wordt weergegeven in het schema voor metagegevens.

**[!UICONTROL JSON Path]**: Gebruik deze optie om het pad van het JSON-bestand op te geven waarin u sleutelwaardeparen voor opties opgeeft.

**[!UICONTROL Placeholder]**: Gebruik deze eigenschap om relevante plaatsaanduidingstekst met betrekking tot de eigenschap metadata op te geven.

**[!UICONTROL Choices]**: Gebruik deze eigenschap om keuzen in een lijst op te geven.

**[!UICONTROL Description]**: Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.

**[!UICONTROL Class]**: Objectklasse waaraan de eigenschap is gekoppeld.

## Schema-formulieren {#delete-folder-metadata-schema-forms} voor mapmetagegevens verwijderen

U kunt de schemaformulieren van de omslagmeta-gegevens van het Schema Forms van de Meta-gegevens van de Omslag schrappen pagina. Als u een formulier wilt verwijderen, selecteert u het en tikt of klikt u op het pictogram Verwijderen op de werkbalk.

![delete_form](assets/delete_form.png)

## Schema {#assign-a-folder-metadata-schema} voor metagegevens van mappen toewijzen

U kunt een schema van omslagmeta-gegevens aan een omslag of van de pagina van Forms van het Schema van Meta-gegevens van de Omslag toewijzen of wanneer het creëren van een omslag.

Als u een metagegevensschema voor een map configureert, wordt het pad naar het schemaformulier opgeslagen in de eigenschap `folderMetadataSchema` van het mapknooppunt onder.*/jcr:content*.

### Wijs aan een schema van de pagina {#assign-to-a-schema-from-the-folder-metadata-schema-page} van het Schema van Meta-gegevens van de Omslag toe

1. Tik/klik op het [!DNL Experience Manager]-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** **[!UICONTROL Folder Metadata Schemas]**.
1. Selecteer op de pagina Forms van het schema Metagegevens map het schema dat u op een map wilt toepassen.
1. Tik/klik op **[!UICONTROL Apply to Folder(s)]** op de werkbalk.

1. Selecteer de map waarop u het schema wilt toepassen en klik op **[!UICONTROL Apply]**. Als er al een metagegevensschema op de map is toegepast, verschijnt er een waarschuwingsbericht dat u het bestaande metagegevensschema wilt overschrijven. Tik of klik op **[!UICONTROL Overwrite]**.
1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.

   ![folder_properties](assets/folder_properties.png)

   Tik of klik op het tabblad **[!UICONTROL Folder Metadata]** om de velden met metadata van de map weer te geven.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Schema toewijzen bij het maken van een map {#assign-a-schema-when-creating-a-folder}

U kunt een schema van omslagmeta-gegevens toewijzen wanneer het creëren van een omslag. Als het systeem minstens één schema van omslagmeta-gegevens bevat, wordt een extra lijst getoond in **[!UICONTROL Create Folder]** dialoog. U kunt het gewenste schema selecteren. Standaard is geen schema geselecteerd.

1. Tik in de gebruikersinterface [!DNL Experience Manager Assets] op **[!UICONTROL Create]** op de werkbalk.
1. Geef een titel en naam voor de map op.
1. Selecteer het gewenste schema in de lijst Metagegevensschema van map. Tik vervolgens op **[!UICONTROL Create]** of klik op &lt;a0/>.

   ![select_schema](assets/select_schema.png)

1. Open de eigenschappen van de metagegevens voor de map waarop u het metagegevensschema hebt toegepast.
1. Tik of klik op het tabblad **[!UICONTROL Folder Metadata]** om de velden met metadata van de map weer te geven.

## Het schema {#use-the-folder-metadata-schema} voor metagegevens van de map gebruiken

Open de eigenschappen voor een map die met een mapmetadataschema is geconfigureerd. Er wordt een tabblad **[!UICONTROL Folder Metadata]** weergegeven op de pagina met mapeigenschappen. Selecteer dit tabblad om het formulier van het mapmetadataschema weer te geven.

Voer waarden voor metagegevens in de verschillende velden in en tik/klik op **[!UICONTROL Save]** om de waarden op te slaan. De waarden die u opgeeft, worden opgeslagen in het mapknooppunt in de CRX-opslagruimte.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)
