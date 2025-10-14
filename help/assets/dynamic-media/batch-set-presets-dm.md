---
title: Voorinstellingen batchset
description: Leer hoe u de afbeeldingsset automatiseert en het maken van een centrifugeset maakt met behulp van voorinstellingen voor batchsets in Dynamic Media.
contentOwner: Rick Brough
feature: Image Presets,Viewer Presets
role: User
exl-id: 022ee347-54ec-4cec-b808-9eb3a9e51424
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '3192'
ht-degree: 0%

---

# Voorinstellingen batchset {#about-bsp}

Gebruik **[!UICONTROL Batch Set Presets]** om meerdere elementen te maken en te ordenen in een afbeeldingsset of centrifugeerset op het moment dat u elementbestanden uploadt naar een map, afzonderlijk of met behulp van bulkopname. U kunt de voorinstelling laten uitvoeren naast de taken voor het importeren van elementen die u in [!DNL Dynamic Media] plant. Elke voorinstelling is een op zichzelf staande verzameling instructies met een unieke naam die definieert hoe de set afbeeldingen moet worden samengesteld of hoe de set moet worden gecentreerd met afbeeldingen die overeenkomen met de gedefinieerde naamgevingsconventies in het vooraf ingestelde recept.

>[!IMPORTANT]
>
>Gebruikt u voorinstellingen voor batchsets in [!DNL Dynamic Media Classic] en migreert u van [!DNL Dynamic Media Classic] naar Adobe Experience Manager as a Cloud Service? Als dat het geval is, moet u de definities van de voorinstellingen voor batchsets handmatig opnieuw maken in [!DNL Adobe Experience Manager as a Cloud Service] .

**Beste praktijken** - wanneer het werken met partijreeks vooraf instelt Adobe adviseert het volgende werkschema:

1. Maak een voorinstelling voor een batchset. Zie [&#x200B; een partijreeks tot stand brengen vooraf ingesteld voor een beeldreeks of een spin reeks &#x200B;](#creating-bsp).
1. Maak een elementmap of gebruik een bestaande elementmap en zorg ervoor dat deze is gesynchroniseerd met [!DNL Dynamic Media] . Zie [&#x200B; omslagen &#x200B;](/help/assets/manage-digital-assets.md#creating-folders) creëren.
1. Pas de voorinstelling voor de batchset toe op de map met elementen. Zie [&#x200B; Ongeveer het toepassen van partij vastgestelde vooraf instelt op omslagen &#x200B;](#apply-bsp).
1. Afbeeldingen uploaden naar de elementmap. Zie [&#x200B; activa voor de Reeksen van het Beeld &#x200B;](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets) uploaden, [&#x200B; activa voor de Reeksen van de Rotatie &#x200B;](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets), of [&#x200B; voeg digitale activa aan Adobe Experience Manager &#x200B;](/help/assets/add-assets.md#add-assets-to-experience-manager) toe.
1. Afbeeldingsset of centrifugeerset wordt automatisch gegenereerd in de gewenste map.
1. Publiceer de afbeeldingsset of de centrifugeset. Zie [&#x200B; Dynamische Media Assets &#x200B;](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) publiceren.

## Een voorinstelling voor een batch-set maken voor een afbeeldingsset of een spin-set {#creating-bsp}

Als u voorinstellingen voor batch-sets wilt maken, is het wenselijk dat u enige kennis en begrip hebt van reguliere expressies.

Idealiter heeft uw bedrijf al een naamgevingsconventie gedefinieerd voor de manier waarop elementen in een set worden gegroepeerd.
Om u te helpen het belang begrijpen van het gebruiken van een noemende overeenkomst, veronderstel de bepaalde het noemen overeenkomst van uw bedrijf `<style>-<color>-<view>` is. En de basisnaam voor de set moet altijd `<style>-<color>` zijn en de extensie van de setnaam moet `-SET` zijn. Als u een afbeelding met de naam `0123-RED-01` uploadt, wordt een set gemaakt met de naam `0123-RED-SET` . Als u later afbeeldingen `0123-RED-03` en `0123-BLUE-01` uploadt, wordt de afbeelding `RED-03` op de tweede positie aan de set toegevoegd omdat deze lager wordt gesorteerd dan `01` . De afbeelding `BLUE-01` maakt echter deel uit van een nieuwe set met de naam `0123-BLUE-SET` . Voor het volgende uploaden van elementen voegt u bestanden `0123-RED-02` en `0123-BLUE-02` toe. Elk activum zou aan zijn respectieve reeks worden toegevoegd. De `RED-02` -afbeelding wordt vanwege de sorteervolgorde automatisch gesorteerd tussen de bestaande `01` - en `03` -afbeeldingen.

Met de pagina **[!UICONTROL Batch Set Preset]** in [!DNL Dynamic Media] kunt u voorinstellingen voor batchsets maken, bewerken of verwijderen en kunt u voorinstellingen voor batchsets toepassen op of verwijderen uit elementmappen. U kunt de vervolgkeuzelijsten voor formuliervelden gebruiken om een voorinstelling voor een batch-set te definiëren of het veld **[!UICONTROL Raw Code]** gebruiken, waarmee u de syntaxis van reguliere expressies kunt typen.

U kunt een groot aantal voorinstellingen voor batchsets maken, zodat u alle taken voor het opnemen van elementen die u nodig hebt, kunt afdekken.

### Info over Asset Naming Convention

Het gebied **[!UICONTROL Asset Naming Convention]** op de pagina **[!UICONTROL Batch Set Preset]** bevat twee elementen die u kunt gebruiken om de voorinstelling voor de batchset te definiëren: **[!UICONTROL Match]** en **[!UICONTROL Base Name]** . Met deze elementen kunt u een naamgevingsconventie definiëren en het gedeelte van de conventie identificeren dat wordt gebruikt om de set met namen te benoemen. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

De individuele noemende overeenkomst van een bedrijf gebruikt vaak één of meerdere lijnen van definitie van elk van deze twee elementen. U kunt zo vele lijnen voor uw unieke definitie gebruiken en hen groeperen in verschillende elementen, zoals voor HoofdBeeld, het element van de Kleur, het element van de Afwisselende Mening, en het element van het Monster.

De syntaxis voor een reguliere expressie van letterlijke overeenkomsten kan er bijvoorbeeld als volgt uitzien:

`(\w+)-\w+-\w+`

### Info Volgorde

U kunt desgewenst de volgorde definiëren waarin afbeeldingen worden weergegeven nadat de afbeeldingsset of de centrifugeset is gegroepeerd in [!DNL Dynamic Media] . Uw elementen worden standaard alfanumeriek geordend. U kunt echter een door komma&#39;s gescheiden lijst met reguliere expressies gebruiken om de volgorde te definiëren.

Met betrekking tot volgorde die automatisering ordent, geeft u regels op om elementen op een bepaalde manier te forceren, indien nodig. Stel dat het eerste element altijd de naam `_main` heeft en u wilt dat het wordt gevolgd door `_alt1` , `_alt2` , `_alt3` , enzovoort. In dergelijke gevallen kunt u een volgorderegel maken met de volgende syntaxis:

`.*_main,.*_alt[0-9]`

Hoewel een geforceerde sorteervolgorde mogelijk is, is het beter om zoveel mogelijk te vertrouwen op alfanumerieke nummering voor volgordevolgorde. Bovendien kunt u de set afbeeldingen of de gereedschappen voor de editor van de spin-set in [!DNL Dynamic Media] gebruiken om de volgorde van elementen te wijzigen, of nieuwe elementen aan de set toevoegen en verwijderen met behulp van slepen en neerzetten.

Wanneer u klaar bent met het maken van een voorinstelling voor een batch-set, past u deze toe op een of meer mappen die u hebt gemaakt. Zie [&#x200B; Ongeveer het toepassen van partij vastgestelde vooraf instelt op omslagen &#x200B;](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**om een partijreeks tot stand te brengen vooraf ingesteld voor een beeldreeks of een spin reeks:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]** .

   ![&#x200B; bsp-create1.png &#x200B;](/help/assets/assets-dm/bsp-create1.png)

1. Selecteer **[!UICONTROL Create]** op de pagina **[!UICONTROL Batch Set Presets]** in de rechterbovenhoek.
1. Voer in het tekstveld **[!UICONTROL Preset Name]** in het dialoogvenster **[!UICONTROL Create Batch Set Preset]** een beschrijvende naam in. De naam van de voorinstelling kan niet worden bewerkt als u deze later wijzigt.

1. Selecteer **[!UICONTROL ImageSet]** of **[!UICONTROL SpinSet]** in de vervolgkeuzelijst **[!UICONTROL Preset Type]** . Zorg ervoor dat u het juiste type voorinstelling kiest; het kan later niet worden bewerkt.
1. Selecteer **[!UICONTROL Create]** .
1. Rechts van de pagina **[!UICONTROL Edit Batch Set Preset]** stelt u de gewenste bewerkbare opties in onder de koppen **[!UICONTROL Preset Details]** en **[!UICONTROL Set Naming Convention]** .
Meer over de editable opties leren die aan u beschikbaar zijn, zie [&#x200B; vooraf ingestelde Details, Vastgestelde het Noemen Overeenkomst, en de Resultaten van de Regel - opties RegX &#x200B;](#features-options-bsp).

   ![&#x200B; bsp-create4.png &#x200B;](/help/assets/assets-dm/bsp-create4.png)

1. Maak een of meer reguliere-expressiegroepen.

   * Selecteer links van de pagina **[!UICONTROL Edit Batch Set Preset]** onder **[!UICONTROL Match]** , **[!UICONTROL Base Name]** of **[!UICONTROL Sequence Ordering]** **[!UICONTROL Add Group]** .
   * Het veld **[!UICONTROL Match]** is vereist. **[!UICONTROL Base Name]** is alleen verplicht als het veld **[!UICONTROL Match]** nog geen basisnaam opgeeft met behulp van een haakjesgroep. **[!UICONTROL Sequence Ordering]** is optioneel.
   * Geef met behulp van de vervolgkeuzelijsten en tekstvakken in het groepsformulier een expressiegroep op die u wilt gebruiken voor het definiëren van de naamgevingscriteria voor de leden van de afbeeldingsset of de set elementen.
      * Terwijl u expressies voor een groep selecteert en opgeeft, ziet u dat de werkelijke syntaxis van de reguliere expressie rechtsonder op de pagina wordt weergegeven onder de kop **[!UICONTROL Rule Results - RegX]** . Als u de reguliere-expressietekenreeks rechtsonder wilt bijwerken, selecteert u deze ergens buiten het formuliergebied. Deze reguliere-expressietekenreeksen vertegenwoordigen het patroon dat u wilt afstemmen in een zoekopdracht naar [!DNL Dynamic Media] -elementen om een afbeeldingsset of centrifugeset te maken.
      * Selecteer **[!UICONTROL X]** als u een groep hebt toegevoegd en deze wilt verwijderen.
   * Wanneer u twee of meer groepen toevoegt in de vervolgkeuzelijst **[!UICONTROL And]** , selecteert u **[!UICONTROL And]** om een zojuist toegevoegde groep samen te voegen met een vorige expressiegroep die u hebt toegevoegd. U kunt ook **[!UICONTROL Or]** selecteren om een alternatief toe te voegen tussen de vorige expressiegroep en de nieuwe groep die u maakt. De operand **[!UICONTROL Or]** wordt gedefinieerd door het gebruik van een verticale-lijnteken `|` in de syntaxis van de reguliere expressie zelf.

1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Add Group]** onder **[!UICONTROL Match]** , **[!UICONTROL Base Name]** of **[!UICONTROL Sequencing Order]** om nog een nieuwe groep toe te voegen. Maak een andere reguliere-expressiegroep zoals u in de vorige stap hebt gedaan.
   * Controleer de syntaxis van de reguliere expressie in het gebied **[!UICONTROL Rule Results - RegX]** . Als u de syntaxis moet wijzigen, voert u de bewerkingen uit in de desbetreffende groep links op de pagina.
   * Ga door met de volgende stap als u klaar bent met het maken van expressiegroepen.

1. Selecteer **[!UICONTROL Save]** rechtsboven op de pagina.

U kunt nu de voorinstelling voor de batchset toepassen op een elementmap. Vervolgens uploadt u elementen naar die map. Deze workflow resulteert in het automatisch genereren van uw afbeeldingsset of centrifugeset. Zie [&#x200B; Ongeveer het toepassen van batch plaatste vooraf instelt op activa omslagen &#x200B;](#apply-bsp).

### Details voorinstelling, Naamgevingsconventie instellen en Regelresultaten - RegX-opties {#features-options-bsp}

Deze opties zijn beschikbaar op de pagina **[!UICONTROL Edit Batch Set Preset]** wanneer u een voorinstelling voor een batch-set maakt of bewerkt.

Zie [&#x200B; een batch tot stand brengen vooraf ingesteld voor een beeld of een spin reeks &#x200B;](#creating-bsp) of [&#x200B; een vooraf ingestelde partijreeks &#x200B;](#edit-bsp) uitgeven.

| **[!UICONTROL Preset Details]** | Beschrijving |
| --- | --- |
| Naam voorinstelling | Alleen-lezen. De naam die u hebt opgegeven toen u de batch-set voor het eerst maakte. Als u de naam van de voorinstelling moet wijzigen, kunt u de bestaande voorinstelling voor een batch-set kopiëren en een nieuwe naam opgeven. Zie [&#x200B; Exemplaar een bestaande vooraf ingestelde partijreeks &#x200B;](#copy-bsp). |
| Type | Alleen-lezen. Het type is opgegeven toen u de batch-set voor het eerst hebt gemaakt. Als u een bestaande voorinstelling voor een batch-set kopieert, kunt u de [!UICONTROL Type] ervan niet wijzigen. In plaats daarvan moet u een voorinstelling maken. |
| Inclusief afgeleide Assets | Optioneel. Als u wilt dat [!DNL Dynamic Media]&#39;s IPS (Image Production System) gegenereerde of &#39;afgeleide&#39; afbeeldingen met uw Spin-set of Afbeeldingsset bevat, selecteert u **[!UICONTROL Yes]** (standaard). Een afgeleid element is een afbeelding die niet rechtstreeks door een gebruiker is geüpload. In plaats daarvan, werd de activa geproduceerd door IPS toen een hoofdactiva werd geupload. Een afbeeldingselement dat IPS bijvoorbeeld genereert op basis van een pagina in een PDF, op het moment dat de PDF werd geüpload in [!DNL Dynamic Media] , wordt beschouwd als een afgeleid element. |
| Doelmap | Optioneel. Als u grote aantallen afbeeldingssets of centrifuges definieert, raadt Adobe u aan deze sets los te houden van de mappen die de elementen zelf bevatten. Als dusdanig, denk na creërend een Reeksen van het Beeld of de omslag van de Reeksen van de Rotatie en richt de toepassing om partij te plaatsen geproduceerde reeksen hier.<br> in zulk geval, specificeer welke omslag binnen de de omslagstructuur van Experience Manager Assets (`/content/dam`) vooraf ingestelde partij actief heeft. Zorg ervoor dat de map is ingeschakeld voor [!DNL Dynamic Media] -synchronisatie om deze als doelmap toe te staan. Zie [&#x200B; selectieve het publiceren op het omslagniveau in Dynamische Media &#x200B;](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder) vormen.<br> meer dan één omslag kan een bepaalde vooraf ingestelde partijreeks hebben die aan het wordt toegewezen, als u vooraf ingesteld door de omslag **[!UICONTROL Properties]** toepast. Zie [&#x200B; partij toepassen vooraf instelt van de Eigenschappen van een activaomslag &#x200B;](#apply-bsp-to-folders-via-properties) vooraf instelt.<br> als u geen omslag specificeert, wordt de vooraf ingestelde partij geproduceerde beeld wordt geplaatst of de spin reeks gecreeerd in de zelfde omslag zoals de activaomslag u uploadde aan. |
| **[!UICONTROL Set Naming Convention]** |  |
| Prefix <br> of <br> Achtervoegsel | Optioneel. Voer een voor- of achtervoegsel of beide in de desbetreffende velden in.<br> de prefix en achtervoegselgebieden laten u vele partijreeks tot stand brengen vooraf instelt gebruikend een afwisselende, douanedossier noemende overeenkomst voor een bepaalde reeks inhoud. Deze methode is vooral handig in gevallen waarin er een uitzondering is op de standaardnaamgevingsregeling van een bedrijf.<br> het voor- of achtervoegsel wordt toegevoegd aan **[!UICONTROL Base Name]** u in het **[!UICONTROL Asset Naming Convention]** gebied bepaalt. Door een voor- of achtervoegsel toe te voegen, zorgt u ervoor dat de set afbeeldingen of de set met centrifuges uitsluitend en onafhankelijk van andere elementen wordt gemaakt. Het kan ook worden gebruikt om anderen te helpen dossiertypes identificeren. Als u bijvoorbeeld een gebruikte kleurmodus wilt bepalen, kunt u een voor- of achtervoegsel `rgb` of `cmyk` toevoegen.<br> terwijl het specificeren van een vastgestelde noemende overeenkomst niet wordt vereist om partij te gebruiken vooraf ingestelde functionaliteit, adviseren de beste praktijken dat u de reeks noemende overeenkomst gebruikt. Op deze manier kunt u zoveel elementen van uw naamgevingsconventie definiëren als u wilt groeperen in een set om het maken van batchsets te stroomlijnen. |
| **[!UICONTROL Rule Results - RegX]** |  |
| Naamgevingsconventie voor middelen - Overeenkomst | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de gekozen formulieropties of de ingevoerde onbewerkte code. |
| Naamgevingsconventie voor middelen - Basisnaam | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de basisnaamadopties die u hebt gekozen of de onbewerkte code die u hebt ingevoerd. |
| Volgorde - Overeenkomst | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de formulieropties die u hebt gekozen of de onbewerkte code die u hebt ingevoerd. |

## Voorinstellingen voor batchsets toepassen op elementmappen {#apply-bsp}

Wanneer u voorinstellingen voor batchsets toewijst aan een of meer elementmappen, nemen submappen de voorinstellingen automatisch over van de bovenliggende map.

U kunt meerdere voorinstellingen voor batchsets toepassen op een elementmap.

Mappen waaraan een voorinstelling voor een batch is toegewezen, worden in de gebruikersinterface aangegeven met de naam van de voorinstelling die wordt weergegeven in de map, in de weergave **[!UICONTROL Card]** .

Als u voorinstellingen voor batchsets wilt toepassen op mappen met elementen, gebruikt u een van de volgende twee methoden:

* [&#x200B; pas partijreeks vooraf instelt op activaomslagen van de Reeks van de Partij vooraf ingestelde pagina &#x200B;](#apply-bsp-to-folders-via-bsp-page) toe - Deze methode biedt u de meeste flexibiliteit aan. U kunt één voorinstelling of meerdere voorinstellingen toepassen op één map of op meerdere mappen.
* [&#x200B; pas partijreeks vooraf instelt van de Pagina van Eigenschappen van een activa omslag &#x200B;](#apply-bsp-to-folders-via-properties) toe - Deze methode laat u één of meerdere partijreeks vooraf instelt op één enkele omslag toepassen.

U kunt het beste controleren of de mappen met elementen zijn gesynchroniseerd [!DNL Dynamic Media] en vervolgens de gewenste voorinstellingen toepassen.

Elementen in een map opnieuw verwerken als u een van de volgende twee situaties ervaart:

* U wilt een voorinstelling voor een batchset uitvoeren op een bestaande elementenmap waarin al elementen zijn geüpload.
* U bewerkt later een bestaande voorinstelling voor een batch-set die eerder is toegepast op een map met elementen.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Voorinstellingen voor batchsets toepassen op elementmappen vanaf de pagina Voorinstelling batch instellen {#apply-bsp-to-folders-via-bsp-page}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]** .
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van elke voorinstelling voor batchsets die u op mappen wilt toepassen.
1. Selecteer **[!UICONTROL Apply Batch Preset to Folders]** in de werkbalk.
1. Schakel op de pagina **[!UICONTROL Select Folders]** het selectievakje in van elke map waarop de voorinstellingen voor batchsets moeten worden toegepast.
1. Selecteer **[!UICONTROL Apply]** in de rechterbovenhoek van de pagina **[!UICONTROL Select Folders]** .

### Voorinstellingen voor batchsets toepassen vanaf de pagina Eigenschappen van een elementmap {#apply-bsp-to-folders-via-properties}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Navigeer naar een map waarin u een of meer voorinstellingen voor batchsets wilt toepassen.
1. Schakel op de pagina links van de kolom **[!UICONTROL Name]** het selectievakje van een map in.
1. Selecteer **[!UICONTROL Properties]** in de werkbalk.
1. Selecteer de tab **[!UICONTROL Dynamic Media Processing]** op de pagina Eigenschappen van de map.

   ![&#x200B; bsp-apply-via-properties2.png &#x200B;](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Selecteer onder **[!UICONTROL Batch Set Presets]** in de vervolgkeuzelijst **[!UICONTROL Preset Name]** de naam van een voorinstelling voor een batch-set die u wilt toepassen. In de bovenstaande schermafbeelding ziet u twee geselecteerde voorinstellingen voor batchsets die op de elementenmap zijn toegepast.

   Als het vervolgkeuzemenu **[!UICONTROL Preset Name]** geen naam bevat voor voorinstellingen van batchsets, betekent dit dat u nog geen voorinstellingen van batchsets hebt gemaakt. Zie [&#x200B; een partijreeks tot stand brengen vooraf ingesteld voor een beeldreeks of een spin reeks &#x200B;](#creating-bsp).

   Als u een toegepaste voorinstelling voor een batch-set wilt verwijderen, selecteert u **[!UICONTROL X]** rechts van het type voorinstelling.

1. Selecteer **[!UICONTROL Save & Close]** rechtsboven op de pagina.

## Een voorinstelling voor een batchset bewerken {#edit-bsp}

U kunt een bestaande voorinstelling voor een batch-set bewerken die u hebt gemaakt. U kunt om het even welke uitdrukkingsgroepen veranderen u voor de activa noemende overeenkomst of opeenvolgingsorde creeerde. Indien nodig kunt u ook de doelmap bijwerken en naamgevingsconventies instellen.

U kunt de naam of het type voorinstelling (Afbeeldingsset of Draaiset) echter niet wijzigen. Als de naam van een voorinstelling moet worden gewijzigd, kopieert u de bestaande voorinstelling en geeft u een nieuwe naam op. Zie [&#x200B; vooraf ingesteld exemplaar van een partijreeks &#x200B;](#copy-bsp).

Als u een vooraf ingestelde batch-set bewerkt die eerder op een map is toegepast, wordt de opnieuw bewerkte voorinstelling voor een batch-set alleen toegepast op nieuwe elementen die naar die map zijn geüpload.

Als u de zojuist bewerkte voorinstelling opnieuw wilt toepassen op de bestaande elementen in de map, moet u de map opnieuw verwerken. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). --> Op deze manier, zouden de bestaande activa nu om deel van een beeldreeks of een spin reeks worden gekwalificeerd en worden toegevoegd. Bovendien worden de bestaande elementen die al waren opgenomen in de afbeeldingsset of de spin-set - op basis van de vorige batch-set die is gebruikt - niet verwijderd en weergegeven zoals ze zijn. In dit scenario wordt ervan uitgegaan dat ze niet langer in aanmerking komen op basis van de zojuist bewerkte voorinstelling.

**om een vooraf ingestelde partijreeks uit te geven:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]** .
1. Controleer op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** de voorinstelling voor batchsets die u wilt wijzigen.
1. Selecteer **[!UICONTROL Edit Batch Set Preset]** in de werkbalk.
1. Bewerk de voorinstelling naar wens.
1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina **[!UICONTROL Batch Set Preset]** .

## Een bestaande voorinstelling voor een batchset kopiëren {#copy-bsp}

U kunt een bestaande voorinstelling voor een batch-set kopiëren om te voorkomen dat u handmatig een complexe voorinstelling opnieuw moet maken of om de naam van een voorinstelling te wijzigen. U kunt het gebruikte type voorinstelling (Afbeeldingsset of Spin-set) echter niet wijzigen.

Als u een bestaande voorinstelling kopieert die door elementmappen wordt gebruikt, heeft dit geen invloed op deze mappen.

**Exemplaar een bestaande partijreeks vooraf ingesteld:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]** .
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van de batch-set met voorinstellingen die u wilt kopiëren.
1. Selecteer **[!UICONTROL Copy]** in de werkbalk.
1. Typ in het tekstvak **[!UICONTROL Title]** van het dialoogvenster **[!UICONTROL Copy Batch Set Preset]** een nieuwe naam voor de voorinstelling.

   ![&#x200B; bsp-copy2.png &#x200B;](/help/assets/assets-dm/bsp-copy2.png)

1. Selecteer **[!UICONTROL Copy]** .

## Voorinstellingen voor batchsets verwijderen uit mappen {#remove-bsp-from-folder}

Wanneer u voorinstellingen voor batchsets uit mappen verwijdert, wordt de batchset niet toegepast op nieuwe elementen die u uploadt naar deze mappen. Bestaande elementen in de map die al zijn toegevoegd aan de afbeeldingsset of de spint-set op basis van een batchset-voorinstelling die is toegepast op de map en die ongewijzigd worden weergegeven.

Als u *wilt schrappen* vooraf instelt van omslagen in plaats daarvan, zie [&#x200B; partij plaatsen schrappen vooraf instelt &#x200B;](#delete-bsp).

Er zijn twee methoden waarmee u voorinstellingen voor batchsets kunt verwijderen uit mappen.

* [&#x200B; verwijdert partijreeks vooraf instelt van omslagen als de Reeks van de Partij vooraf instelt pagina &#x200B;](#remove-bsp-from-folders-via-bsp-page) - Deze methode biedt u de meeste flexibiliteit aan. U kunt één voorinstelling of meerdere voorinstellingen uit één map of uit meerdere mappen verwijderen.
* [&#x200B; verwijdert partijreeks vooraf instelt van de pagina van Eigenschappen van een omslag &#x200B;](#remove-bsp-from-folders-via-properties) - Deze methode laat u één of meerdere partijreeks verwijderen vooraf instelt van één enkele omslag slechts.

### Voorinstellingen voor batchsets uit mappen verwijderen op basis van de pagina Voorinstelling voor batchset {#remove-bsp-from-folders-via-bsp-page}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]** .
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van een of meer voorinstellingen voor batchsets die u uit een of meer mappen wilt verwijderen.
1. Selecteer **[!UICONTROL Remove Batch Preset from Folders]** in de werkbalk.

1. Selecteer op de pagina **[!UICONTROL Select Folders]** een of meer mappen waarin u de voorinstellingen van de batchset wilt verwijderen.
1. Selecteer **[!UICONTROL Remove]** in de rechterbovenhoek van de pagina **[!UICONTROL Select Folders]** .

   ![&#x200B; bsp-remove-from-folders3.png &#x200B;](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Selecteer **[!UICONTROL Remove]** in het dialoogvenster **[!UICONTROL Remove profile]** .

### Voorinstellingen voor batchsets verwijderen uit de eigenschappenpagina van een map {#remove-bsp-from-folders-via-properties}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Navigeer naar een map waarnaar u een of meer voorinstellingen voor een batch-set wilt verwijderen.
1. Schakel op de pagina links van de kolom **[!UICONTROL Name]** het selectievakje van een map in.
1. Selecteer **[!UICONTROL Properties]** in de werkbalk.
1. Selecteer **[!UICONTROL Dynamic Media Processing]** op de pagina Eigenschappen van de map.

   ![&#x200B; bsp-apply-via-properties2.png &#x200B;](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Selecteer onder **[!UICONTROL Batch Set Presets]** de optie **[!UICONTROL X]** rechts van het type voorinstelling.

1. Selecteer **[!UICONTROL Save & Close]** rechtsboven op de pagina.

## Voorinstellingen voor batchsets verwijderen {#delete-bsp}

U kunt voorinstellingen van batchsets verwijderen om deze permanent uit [!DNL Dynamic Media] te verwijderen. Dat wil zeggen dat ze niet meer worden weergegeven op de pagina [!UICONTROL Batch Set Preset] en ook niet worden weergegeven in de vervolgkeuzelijst **[!UICONTROL Batch Set Presets]** van het tabblad **[!UICONTROL Dynamic Media Processing]** op de pagina **[!UICONTROL Properties]** van de map. De voorinstelling wordt daarom niet toegepast op bestaande elementen in een map die opnieuw wordt verwerkt of wanneer nieuwe elementen in de map worden geüpload.

Als u een voorinstelling verwijdert die eerder op een of meer mappen is toegepast, worden alle sets afbeeldingen of centrifuges die op basis van elementen in die mappen zijn gemaakt, ongewijzigd weergegeven.

Als u *wilt verwijderen* vooraf instelt van omslagen in plaats daarvan, zie [&#x200B; partij verwijderen vooraf instelt van omslagen &#x200B;](#remove-bsp-from-folder).

**om partijreeks te schrappen vooraf instelt:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]** .
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van een of meer voorinstellingen voor batchsets die u wilt verwijderen.
1. Selecteer **[!UICONTROL Delete Batch Set Presets]** in de werkbalk.

   ![&#x200B; bsp-delete2.png &#x200B;](/help/assets/assets-dm/bsp-delete2.png)

1. Selecteer **[!UICONTROL Delete]** in het dialoogvenster **[!UICONTROL Delete Batch Set Presets]** .

   Als in een elementmap naar de voorinstelling die u verwijdert, wordt verwezen, selecteert u **[!UICONTROL Force Delete]** .

   ![&#x200B; bsp-delete3.png &#x200B;](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Image Sets](/help/assets/dynamic-media/image-sets.md)
>* [Spin Sets](/help/assets/dynamic-media/spin-sets.md)
>* [&#x200B; vorm selectief het publiceren op het omslagniveau in Dynamische Media &#x200B;](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder) - zie &quot;Wijze van de Synchronisatie&quot;in het onderwerp als u meer over het synchroniseren van één enkele omslag aan [!DNL Dynamic Media] wilt leren.
>* [&#x200B; creeer een Dynamische Configuratie van Media in de Diensten van de Wolk &#x200B;](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) - zie &quot;Dynamische de synchronisatiemodus van Media&quot;in het onderwerp als u meer over het synchroniseren van alle omslagen aan [!DNL Dynamic Media] wilt leren.
