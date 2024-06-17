---
title: Trapsgewijze metagegevens
description: In dit artikel wordt beschreven hoe u trapsgewijze metagegevens voor elementen definieert.
contentOwner: AG
feature: Metadata
role: Admin, User
exl-id: 1d3ad496-a964-476e-b1da-4aa6d8ad53b7
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 4%

---

# Trapsgewijze metagegevens {#cascading-metadata}

Wanneer gebruikers de metagegevens van een element vastleggen, verschaffen ze informatie in de verschillende beschikbare velden. U kunt specifieke metagegevensvelden of veldwaarden weergeven die afhankelijk zijn van de opties die in de andere velden zijn geselecteerd. Een dergelijke voorwaardelijke weergave van metagegevens wordt trapsgewijze metagegevens genoemd. Met andere woorden, u kunt een afhankelijkheid maken tussen een bepaald metagegevensveld/een bepaalde waarde en een of meer velden en/of hun waarden.

Gebruik schema&#39;s voor metagegevens om regels voor de weergave van trapsgewijze metagegevens te definiëren. Als uw metagegevensschema bijvoorbeeld een elementtypeveld bevat, kunt u een relevante set velden definiëren die moet worden weergegeven op basis van het type element dat de gebruiker selecteert.

Hier volgen enkele gebruiksgevallen waarvoor u trapsgewijze metagegevens kunt definiëren:

* Indien een gebruikerslocatie is vereist, relevante plaatsnaam weergeven op basis van de keuze van het land en de staat van de gebruiker.
* Laad relevante merknamen in een lijst op basis van de door de gebruiker gekozen productcategorie.
* Schakel de zichtbaarheid van een bepaald veld in of uit op basis van de waarde die in een ander veld is opgegeven. Geef bijvoorbeeld afzonderlijke velden voor het verzendadres weer als de gebruiker de verzending op een ander adres wil laten uitvoeren.
* Wijs een veld aan als verplicht op basis van de waarde die in een ander veld is opgegeven.
* Opties wijzigen die voor een bepaald veld worden weergegeven op basis van de waarde die in een ander veld is opgegeven.
* Stel de standaardwaarde voor metagegevens in een bepaald veld in op basis van de waarde die in een ander veld is opgegeven.

## Metagegevens met trapsgewijze opmaak configureren in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Overweeg een scenario waarin u trapsgewijze metagegevens wilt weergeven op basis van het geselecteerde type element. Enkele voorbeelden

* Geef voor een video toepasselijke velden weer, zoals indeling, codec, duur, enzovoort.
* Voor een Word- of PDF-document geeft u velden weer, zoals het aantal pagina&#39;s, de auteur, enzovoort.

Geef de copyrightinformatie, ongeacht het gekozen elementtype, weer als een verplicht veld.

1. Selecteer de [!DNL Experience Manager] logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. In de **[!UICONTROL Schema Forms]** pagina, selecteert u een schema en selecteert u vervolgens **[!UICONTROL Edit]** op de werkbalk om het schema te bewerken.

   ![select_form](assets/select_form.png)

1. (Optioneel) Maak in de Schema-editor voor metagegevens een veld dat u wilt conditionaliseren. Geef een naam- en eigenschappenpad op in het dialoogvenster **[!UICONTROL Settings]** tab.

   Als u een tabblad wilt maken, selecteert u `+` om een tabblad toe te voegen en vervolgens een metagegevensveld toe te voegen.

   ![add_tab](assets/add_tab.png)

1. Voeg een vervolgkeuzeveld toe voor het elementtype. Geef een naam- en eigenschappenpad op in het dialoogvenster **[!UICONTROL Settings]** tab. Voeg een optionele beschrijving toe.

   ![asset_type_field](assets/asset_type_field.png)

1. Sleutelwaardeparen zijn de opties die aan een gebruiker van een formulier worden verstrekt. U kunt de sleutel-waardeparen of manueel of van een JSON- dossier verstrekken.

   * Als u de waarden handmatig wilt opgeven, selecteert u **[!UICONTROL Add Manually]** en selecteert u **[!UICONTROL Add Choice]** en geeft u de optietekst en -waarde op. U kunt bijvoorbeeld de elementtypen Video, PDF, Word en Afbeelding opgeven.

   * Selecteer **[!UICONTROL Add Through JSON Path]** en geef het pad van het JSON-bestand op. [!DNL Experience Manager] Hiermee haalt u de sleutelwaardeparen op in real-time wanneer het formulier aan de gebruiker wordt gepresenteerd.

   Beide opties sluiten elkaar uit. U kunt de opties niet importeren uit een JSON-bestand en handmatig bewerken.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >Wanneer u een JSON-bestand toevoegt, worden de sleutel-waardeparen niet weergegeven in de Schema-editor voor metagegevens, maar wel in het gepubliceerde formulier.

   >[!NOTE]
   >
   >Als u keuzen toevoegt en op het pop-upveld klikt, wordt de interface vervormd en werkt het verwijderpictogram voor de keuzen niet meer. Klik niet op de vervolgkeuzelijst totdat u de wijzigingen opslaat. Sla het schema op en open het opnieuw om door te gaan met bewerken als dit probleem zich voordoet.

1. (Optioneel) Voeg de andere vereiste velden toe. U kunt bijvoorbeeld de indeling, codec en duur van de video met het elementtype opgeven.

   Op dezelfde manier voegt u afhankelijke velden toe voor andere elementtypen. Voeg bijvoorbeeld het aantal velden en de auteur van de pagina toe voor documentelementen, zoals PDF- en Word-bestanden.

   ![video_dependent_fields](assets/video_dependent_fields.png)

1. Als u een afhankelijkheid wilt maken tussen het veld voor het type element en andere velden, kiest u het afhankelijke veld en opent u het dialoogvenster **[!UICONTROL Rules]** tab.

   ![select_dependentfield](assets/select_dependentfield.png)

1. Kies onder **[!UICONTROL Requirement]** de optie **[!UICONTROL Required, based on new rule]**.
1. Selecteren **[!UICONTROL Add Rule]** en kiest u **[!UICONTROL Asset Type]** veld om een afhankelijkheid te maken. Kies ook de veldwaarde waarop u de afhankelijkheid wilt maken. Kies in dit geval **[!UICONTROL Video]**. Selecteren **[!UICONTROL Done]** om de wijzigingen op te slaan

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >U kunt regels gebruiken voor vervolgkeuzelijsten met handmatig vooraf gedefinieerde waarden. Vervolgkeuzemenu&#39;s met geconfigureerd JSON-pad kunnen niet worden gebruikt met regels die vooraf gedefinieerde waarden gebruiken om voorwaarden toe te passen. Als de waarden bij uitvoering vanuit JSON worden geladen, is het niet mogelijk een vooraf gedefinieerde regel toe te passen.

1. Kies onder **[!UICONTROL Visibility]** de optie **[!UICONTROL Visible, based on new rule]**.

1. Selecteren **[!UICONTROL Add Rule]** en kiest u **[!UICONTROL Asset Type]** veld om een afhankelijkheid te maken. Kies ook de veldwaarde waarop u de afhankelijkheid wilt maken. Kies in dit geval **[!UICONTROL Video]**. Selecteren **[!UICONTROL Done]** om de wijzigingen op te slaan

   ![define_visibilityrule](assets/define_visibilityrule.png)

   >[!CAUTION]
   >
   >Als u de waarden opnieuw wilt instellen, selecteert u op een willekeurige plaats in de interface behalve de waarden. Als de waarden opnieuw zijn ingesteld, selecteert u de waarden opnieuw.

   >[!NOTE]
   >
   >U kunt de voorwaarde **[!UICONTROL Requirement]** en de voorwaarde **[!UICONTROL Visibility]** onafhankelijk van elkaar toepassen.

1. Maak op dezelfde manier een afhankelijkheid tussen de waarde Video in het veld Type element en andere velden, zoals Codec en Duur.
1. Herhaal de stappen om documentelementen (PDF en Word) in het dialoogvenster [!UICONTROL Asset Type] veld en velden, zoals [!UICONTROL Page Count] en [!UICONTROL Author].
1. Klik op **[!UICONTROL Save]**. Pas het metagegevensschema toe op een map.

1. Navigeer naar de map waarop u het metagegevensschema hebt toegepast en open de pagina met eigenschappen van een element. Afhankelijk van uw keuze in het veld Type element worden relevante trapsgewijze metagegevensvelden weergegeven.

   ![Trapsgewijze metagegevens voor video-elementen](assets/video_asset.png)
   *Afbeelding: Trapsgewijze metagegevens voor video-elementen*

   ![Trapsgewijze metagegevens voor documentelementen](assets/doc_type_fields.png)
   *Afbeelding: Trapsgewijze metagegevens voor documentelementen*

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
