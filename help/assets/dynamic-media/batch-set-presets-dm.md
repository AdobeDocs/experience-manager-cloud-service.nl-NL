---
title: Voorinstellingen batchset
description: Leer hoe u afbeeldingssets kunt automatiseren en het maken van centrifuges kunt uitvoeren met behulp van voorinstellingen voor batchsets in Dynamic Media.
contentOwner: Rick Brough
feature: Image Presets,Viewer Presets
role: User
exl-id: 022ee347-54ec-4cec-b808-9eb3a9e51424
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '3200'
ht-degree: 0%

---

# Voorinstellingen batchset {#about-bsp}

Gebruiken **[!UICONTROL Batch Set Presets]** om meerdere elementen te maken en te ordenen in een afbeeldingsset of centrifugeerset op het moment dat u elementbestanden uploadt naar een map, afzonderlijk of met behulp van bulkopname. U kunt de voorinstelling laten uitvoeren naast de taken voor het importeren van elementen die u in [!DNL Dynamic Media]. Elke voorinstelling is een op zichzelf staande verzameling instructies met een unieke naam die definieert hoe de set afbeeldingen moet worden samengesteld of hoe de set moet worden gecentreerd met afbeeldingen die overeenkomen met de gedefinieerde naamgevingsconventies in het vooraf ingestelde recept.

>[!IMPORTANT]
>
>Gebruikt u voorinstellingen voor batchsets in [!DNL Dynamic Media Classic]en migreren uit [!DNL Dynamic Media Classic] naar Adobe Experience Manager as a Cloud Service? Als dat het geval is, moet u de definities van voorinstellingen voor batchets handmatig opnieuw maken binnen [!DNL Adobe Experience Manager as a Cloud Service].

**Beste praktijken** - Als u werkt met voorinstellingen voor batchsets, raadt Adobe de volgende workflow aan:

1. Maak een voorinstelling voor een batchset. Zie [Een voorinstelling voor een batch-set maken voor een afbeeldingsset of een spin-set](#creating-bsp).
1. Een elementmap maken of een bestaande elementmap gebruiken en controleren of deze is gesynchroniseerd met [!DNL Dynamic Media]. Zie [Mappen maken](/help/assets/manage-digital-assets.md#creating-folders).
1. Pas de voorinstelling voor de batchset toe op de map met elementen. Zie [Voorinstellingen voor batchsets toepassen op mappen](#apply-bsp).
1. Afbeeldingen uploaden naar de elementmap. Zie [Elementen uploaden voor afbeeldingssets](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Elementen uploaden voor centrifuges](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets), of [Digitale middelen toevoegen aan Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. Afbeeldingsset of centrifugeerset wordt automatisch gegenereerd in de gewenste map.
1. Publiceer de afbeeldingsset of de centrifugeset. Zie [Dynamic Media-middelen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Een voorinstelling voor een batch-set maken voor een afbeeldingsset of een spin-set {#creating-bsp}

Als u voorinstellingen voor batch-sets wilt maken, is het wenselijk dat u enige kennis en begrip hebt van reguliere expressies.

Idealiter heeft uw bedrijf al een naamgevingsconventie gedefinieerd voor de manier waarop elementen in een set worden gegroepeerd.
Om u te helpen het belang begrijpen van het gebruiken van een noemende overeenkomst, veronderstel de bepaalde noemende overeenkomst van uw bedrijf is `<style>-<color>-<view>`. En de basisnaam voor de set moet altijd `<style>-<color>`en de extensie van de setnaam `-SET`. Als u een afbeelding met de naam `0123-RED-01`, dan zou een reeks worden gecreeerd genoemd `0123-RED-SET`. Als u later afbeeldingen uploadt `0123-RED-03` en `0123-BLUE-01`en de `RED-03` afbeelding zou op de tweede positie aan de set worden toegevoegd omdat deze lager wordt gesorteerd dan `01`. De `BLUE-01` afbeelding maakt deel uit van een nieuwe set met de naam `0123-BLUE-SET`. Voor het volgende uploaden van elementen voegt u bestanden toe `0123-RED-02` en `0123-BLUE-02`. Elk activum zou aan zijn respectieve reeks worden toegevoegd. De `RED-02` afbeelding wordt automatisch gesorteerd tussen de bestaande `01` en `03` vanwege de sorteervolgorde.

De **[!UICONTROL Batch Set Preset]** pagina in [!DNL Dynamic Media] Hiermee kunt u voorinstellingen voor batchsets maken, bewerken of verwijderen en voorinstellingen voor batchsets toepassen op of verwijderen uit elementmappen. U kunt de vervolgkeuzelijsten voor formuliervelden gebruiken om een voorinstelling voor een batch-set te definiëren of de opdracht **[!UICONTROL Raw Code]** veld, waarin u de syntaxis van reguliere expressies kunt typen.

U kunt veel voorinstellingen voor batchsets maken, zodat u alle taken voor het opnemen van elementen die u nodig hebt, kunt afdekken.

### Info over Asset Naming Convention

De **[!UICONTROL Asset Naming Convention]** gebied op **[!UICONTROL Batch Set Preset]** pagina bevat twee elementen waarmee u de voorinstelling voor de batchset kunt definiëren: **[!UICONTROL Match]** en **[!UICONTROL Base Name]**. Met deze elementen kunt u een naamgevingsconventie definiëren en het gedeelte van de conventie identificeren dat wordt gebruikt om de set met namen te benoemen. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

De individuele noemende overeenkomst van een bedrijf gebruikt vaak één of meerdere lijnen van definitie van elk van deze twee elementen. U kunt zo vele lijnen voor uw unieke definitie gebruiken en hen groeperen in verschillende elementen, zoals voor HoofdBeeld, het element van de Kleur, het element van de Afwisselende Mening, en het element van het Monster.

De syntaxis voor een reguliere expressie van letterlijke overeenkomsten kan er bijvoorbeeld als volgt uitzien:

`(\w+)-\w+-\w+`

### Info Volgorde

U kunt desgewenst de volgorde definiëren waarin afbeeldingen worden weergegeven nadat de afbeeldingsset of de centrifugeset is gegroepeerd in [!DNL Dynamic Media]. Uw elementen worden standaard alfanumeriek geordend. U kunt echter een door komma&#39;s gescheiden lijst met reguliere expressies gebruiken om de volgorde te definiëren.

Met betrekking tot volgorde die automatisering ordent, geeft u regels op om elementen op een bepaalde manier te forceren, indien nodig. Stel dat uw eerste element altijd een naam heeft `_main` en u wilt dat het gevolgd wordt `_alt1`, `_alt2`, `_alt3`, enzovoort. In dergelijke gevallen kunt u een volgorderegel maken met de volgende syntaxis:

`.*_main,.*_alt[0-9]`

Hoewel een geforceerde sorteervolgorde mogelijk is, is het beter om zoveel mogelijk te vertrouwen op alfanumerieke nummering voor volgordevolgorde. Bovendien kunt u de gereedschappen voor de afbeeldingsset of de spin-set editor gebruiken in [!DNL Dynamic Media] om de volgorde van elementen te wijzigen of om nieuwe elementen in de set toe te voegen en te verwijderen met behulp van slepen en neerzetten.

Wanneer u klaar bent met het maken van een voorinstelling voor een batch-set, past u deze toe op een of meer mappen die u hebt gemaakt. Zie [Voorinstellingen voor batchsets toepassen op mappen](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**U kunt als volgt een voorinstelling voor een batch-set maken voor een afbeeldingsset of een centrifugeset:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Op de **[!UICONTROL Batch Set Presets]** pagina, bij de rechterbovenhoek, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Batch Set Preset]** in het dialoogvenster **[!UICONTROL Preset Name]** Typ een beschrijvende naam in het tekstveld. De naam van de voorinstelling kan niet worden bewerkt als u deze later wijzigt.

1. In de **[!UICONTROL Preset Type]** vervolgkeuzelijst, selecteert u **[!UICONTROL ImageSet]** of **[!UICONTROL SpinSet]**. Zorg ervoor dat u het juiste vooraf ingestelde type kiest. het kan later niet worden bewerkt.
1. Selecteer **[!UICONTROL Create]**.
1. Rechts van het **[!UICONTROL Edit Batch Set Preset]** pagina, stelt u de gewenste bewerkbare opties in onder de **[!UICONTROL Preset Details]** en **[!UICONTROL Set Naming Convention]** koppen.
Ga voor meer informatie over de bewerkbare opties waarover u beschikt naar [Details voorinstelling, Naamgevingsconventie instellen en Regelresultaten - RegX-opties](#features-options-bsp).

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Maak een of meer reguliere-expressiegroepen.

   * Links van de knop **[!UICONTROL Edit Batch Set Preset]** pagina, onder **[!UICONTROL Match]**, **[!UICONTROL Base Name]**, of **[!UICONTROL Sequence Ordering]**, selecteert u **[!UICONTROL Add Group]**.
   * De **[!UICONTROL Match]** is vereist. **[!UICONTROL Base Name]** is alleen verplicht als de **[!UICONTROL Match]** in het veld wordt nog geen basisnaam opgegeven met behulp van een haakjesgroep. **[!UICONTROL Sequence Ordering]** is optioneel.
   * Geef met behulp van de vervolgkeuzelijsten en tekstvakken in het groepsformulier een expressiegroep op die u wilt gebruiken voor het definiëren van de naamgevingscriteria voor de leden van de afbeeldingsset of de set elementen.
      * Terwijl u expressies voor een groep selecteert en opgeeft, ziet u dat de werkelijke syntaxis van de reguliere expressie rechtsonder op de pagina wordt weerspiegeld, onder de syntaxis **[!UICONTROL Rule Results - RegX]** kop. Als u de reguliere-expressietekenreeks rechtsonder wilt bijwerken, selecteert u deze ergens buiten het formuliergebied. Deze reguliere-expressietekenreeksen vertegenwoordigen het patroon dat u wilt afstemmen in een zoekopdracht van [!DNL Dynamic Media] elementen waarmee u een afbeeldingsset of een centrifugeset maakt.
      * Als u een groep hebt toegevoegd en deze wilt verwijderen, selecteert u **[!UICONTROL X]**.
   * Wanneer u twee of meer groepen toevoegt, kunt u **[!UICONTROL And]** vervolgkeuzelijst, selecteert u **[!UICONTROL And]** om deel te nemen aan een onlangs toegevoegde groep met om het even welke vorige uitdrukkingsgroep u hebt toegevoegd. Of selecteer **[!UICONTROL Or]** om een alternatief tussen de vorige uitdrukkingsgroep en de nieuwe groep toe te voegen u creeert. De **[!UICONTROL Or]** operand wordt gedefinieerd door het gebruik van een teken voor een verticale lijn `|` in de syntaxis van de reguliere expressie zelf.

1. Voer een van de volgende handelingen uit:

   * Een andere nieuwe groep toevoegen, onder **[!UICONTROL Match]**, **[!UICONTROL Base Name]**, of **[!UICONTROL Sequencing Order]**, selecteert u **[!UICONTROL Add Group]**. Maak een andere reguliere-expressiegroep zoals u in de vorige stap hebt gedaan.
   * Controleer de syntaxis van de reguliere expressie in het dialoogvenster **[!UICONTROL Rule Results - RegX]** gebied. Als u de syntaxis moet wijzigen, voert u de bewerkingen uit in de desbetreffende groep links op de pagina.
   * Ga door met de volgende stap als u klaar bent met het maken van expressiegroepen.

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save]**.

U kunt nu de voorinstelling voor de batchset toepassen op een elementmap. Vervolgens uploadt u elementen naar die map. Deze workflow resulteert in het automatisch genereren van uw afbeeldingsset of centrifugeset. Zie [Voorinstellingen voor batchsets toepassen op elementmappen](#apply-bsp).

### Details voorinstelling, Naamgevingsconventie instellen en Regelresultaten - RegX-opties {#features-options-bsp}

Deze opties zijn beschikbaar op het tabblad **[!UICONTROL Edit Batch Set Preset]** pagina wanneer u een voorinstelling voor een batch-set maakt of bewerkt.

Zie [Een voorinstelling voor een batch-set maken voor een afbeeldingsset of een spin-set](#creating-bsp) of [Een voorinstelling voor een batchset bewerken](#edit-bsp).

| **[!UICONTROL Preset Details]** | Beschrijving |
| --- | --- |
| Naam voorinstelling | Alleen-lezen. De naam die u hebt opgegeven toen u de batch-set voor het eerst maakte. Als u de naam van de voorinstelling moet wijzigen, kunt u de bestaande voorinstelling voor een batch-set kopiëren en een nieuwe naam opgeven. Zie [Een bestaande voorinstelling voor een batchset kopiëren](#copy-bsp). |
| Type | Alleen-lezen. Het type is opgegeven toen u de batch-set voor het eerst hebt gemaakt. Als u een bestaande voorinstelling voor een batch-set kopieert, kunt u deze niet wijzigen [!UICONTROL Type]; u moet een voorinstelling maken. |
| Afgeleide activa opnemen | Optioneel. Moet [!DNL Dynamic Media]IPS (het Systeem van de Productie van het Beeld van het Beeld omvat geproduceerde of &quot;afgeleide&quot;beelden met uw Reeks van de Rotatie of Reeks van het Beeld, uitgezocht **[!UICONTROL Yes]** (standaard). Een afgeleid element is een afbeelding die niet rechtstreeks door een gebruiker is geüpload. In plaats daarvan, werd de activa geproduceerd door IPS toen een master middel werd geupload. Bijvoorbeeld een afbeeldingselement dat IPS van een pagina in een PDF produceerde, op het tijdstip dat de PDF binnen werd geupload [!DNL Dynamic Media]wordt beschouwd als een afgeleid actief. |
| Doelmap | Optioneel. Als u grote aantallen afbeeldingssets of centrifuges definieert, raadt Adobe u aan deze sets los te houden van de mappen die de elementen zelf bevatten. Als dusdanig, denk na creërend een Reeksen van het Beeld of de omslag van de Reeksen van de Rotatie en richt de toepassing om partij te plaatsen geproduceerde reeksen hier.<br>Geef in dat geval op welke map zich in de Experience Manager Assets-mapstructuur bevindt (`/content/dam`) is de voorinstelling voor de batch-set actief. Zorg ervoor dat de map is ingeschakeld voor [!DNL Dynamic Media] synchronisatie om het als bestemmingsomslag toe te staan. Zie [Selectieve publicatie op mapniveau in Dynamic Media configureren](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br>Aan meerdere mappen kan een bepaalde voorinstelling voor een batch zijn toegewezen, als u de voorinstelling toepast via de map **[!UICONTROL Properties]**. Zie [Voorinstellingen voor batchsets toepassen vanaf de pagina Eigenschappen van een elementmap](#apply-bsp-to-folders-via-properties).<br>Als u geen map opgeeft, wordt de door de batchset gegenereerde afbeeldingsset of centrifugeset gemaakt in dezelfde map als de elementenmap waarnaar u hebt geüpload. |
| **[!UICONTROL Set Naming Convention]** |  |
| Voorvoegsel<br>of<br>Achtervoegsel | Optioneel. Voer een voor- of achtervoegsel of beide in de desbetreffende velden in.<br>Met de velden voor het voorvoegsel en het achtervoegsel kunt u een groot aantal voorinstellingen voor batchsets maken met behulp van een alternatieve naamgevingsconventie voor aangepaste bestanden voor een bepaalde set inhoud. Deze methode is vooral handig in gevallen waarin er een uitzondering is op de standaardnaamgevingsregeling van een bedrijf.<br>Het voor- of achtervoegsel wordt toegevoegd aan de **[!UICONTROL Base Name]** u definieert in het dialoogvenster **[!UICONTROL Asset Naming Convention]** gebied. Door een voor- of achtervoegsel toe te voegen, zorgt u ervoor dat de set afbeeldingen of de set met centrifuges uitsluitend en onafhankelijk van andere elementen wordt gemaakt. Het kan ook worden gebruikt om anderen te helpen dossiertypes identificeren. Als u bijvoorbeeld een gebruikte kleurmodus wilt bepalen, kunt u een voor- of achtervoegsel toevoegen `rgb` of `cmyk`.<br>Als u een naamgevingsconventie voor sets opgeeft, is het niet nodig vooraf ingestelde functies voor batchsets te gebruiken, maar aanbevolen wordt om de naamgevingsconventie voor sets te gebruiken. Op deze manier kunt u zoveel elementen van de naamgevingsconventie definiëren als u wilt groeperen in een set om het maken van batchsets te stroomlijnen. |
| **[!UICONTROL Rule Results - RegX]** |  |
| Naamgevingsconventie voor middelen - Overeenkomst | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de gekozen formulieropties of de ingevoerde onbewerkte code. |
| Naamgevingsconventie voor middelen - Basisnaam | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de basisnaamadopties die u hebt gekozen of de onbewerkte code die u hebt ingevoerd. |
| Volgorde - Overeenkomst | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de formulieropties die u hebt gekozen of de onbewerkte code die u hebt ingevoerd. |

## Voorinstellingen voor batchsets toepassen op elementmappen {#apply-bsp}

Wanneer u voorinstellingen voor batchsets toewijst aan een of meer elementmappen, nemen submappen de voorinstellingen automatisch over van de bovenliggende map.

U kunt meerdere voorinstellingen voor batchsets toepassen op een elementmap.

Mappen waaraan een voorinstelling voor een batch is toegewezen, worden in de gebruikersinterface aangegeven met de naam van de voorinstelling die wordt weergegeven in de map, in het dialoogvenster **[!UICONTROL Card]** weergeven.

Als u voorinstellingen voor batchsets wilt toepassen op elementmappen, gebruikt u een van de volgende twee methoden:

* [Voorinstellingen voor batchsets toepassen op elementmappen vanaf de pagina Voorinstelling batch instellen](#apply-bsp-to-folders-via-bsp-page) - Deze methode biedt u de meeste flexibiliteit. U kunt één voorinstelling of meerdere voorinstellingen toepassen op één map of op meerdere mappen.
* [Voorinstellingen voor batchsets toepassen vanaf de pagina Eigenschappen van een elementmap](#apply-bsp-to-folders-via-properties) - Met deze methode kunt u een of meer voorinstellingen voor batchsets toepassen op één map.

U kunt het beste de mappen met elementen synchroniseren [!DNL Dynamic Media]past u vervolgens de gewenste voorinstellingen toe.

Elementen in een map opnieuw verwerken als u een van de volgende twee situaties ervaart:

* U wilt een voorinstelling voor een batchset uitvoeren op een bestaande elementenmap waarin al elementen zijn geüpload.
* U bewerkt later een bestaande voorinstelling voor een batch-set die eerder is toegepast op een map met elementen.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Voorinstellingen voor batchsets toepassen op elementmappen vanaf de pagina Voorinstelling batch instellen {#apply-bsp-to-folders-via-bsp-page}

1. Selecteer het logo van de Experience Manager en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Op de **[!UICONTROL Batch Set Presets]** pagina, links van **[!UICONTROL Preset Name]** selecteert u het selectievakje van elke voorinstelling voor een batch-set die u op mappen wilt toepassen.
1. Selecteer in de werkbalk de optie **[!UICONTROL Apply Batch Preset to Folders]**.
1. Op de **[!UICONTROL Select Folders]** selecteert u het selectievakje van elke map waarop de voorinstellingen voor batchsets moeten worden toegepast.
1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Select Folders]** pagina, selecteert u **[!UICONTROL Apply]**.

### Voorinstellingen voor batchsets toepassen vanaf de pagina Eigenschappen van een elementmap {#apply-bsp-to-folders-via-properties}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar een map waarin u een of meer voorinstellingen voor batchsets wilt toepassen.
1. Op de pagina, links van **[!UICONTROL Name]** selecteert u het selectievakje van een map.
1. Selecteer in de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer op de pagina Eigenschappen van de map de optie **[!UICONTROL Dynamic Media Processing]** tab.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Onder **[!UICONTROL Batch Set Presets]** van de **[!UICONTROL Preset Name]** selecteert u de naam van een voorinstelling voor een batch-set die u wilt toepassen. In de bovenstaande schermafbeelding ziet u twee geselecteerde voorinstellingen voor batchsets die op de elementenmap zijn toegepast.

   Als er geen naam bestaat voor de voorinstelling voor een batch **[!UICONTROL Preset Name]** in de vervolgkeuzelijst. Dit betekent dat u nog geen voorinstellingen voor batchsets hebt gemaakt. Zie [Een voorinstelling voor een batch-set maken voor een afbeeldingsset of een spin-set](#creating-bsp).

   Selecteer **[!UICONTROL X]** rechts van het type voorinstelling.

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save & Close]**.

## Een voorinstelling voor een batchset bewerken {#edit-bsp}

U kunt een bestaande voorinstelling voor een batch-set bewerken die u hebt gemaakt. U kunt om het even welke uitdrukkingsgroepen veranderen u voor de activa noemende overeenkomst of opeenvolgingsorde creeerde. Indien nodig kunt u ook de doelmap bijwerken en naamgevingsconventies instellen.

U kunt de naam of het type voorinstelling (Afbeeldingsset of Draaiset) van de voorinstelling echter niet wijzigen. Als de naam van een voorinstelling moet worden gewijzigd, kopieert u de bestaande voorinstelling en geeft u een nieuwe naam op. Zie [Een voorinstelling voor een batchset kopiëren](#copy-bsp).

Als u een vooraf ingestelde batch-set bewerkt die eerder op een map is toegepast, wordt de opnieuw bewerkte voorinstelling voor een batch-set alleen toegepast op nieuwe elementen die naar die map zijn geüpload.

Als u de zojuist bewerkte voorinstelling opnieuw wilt toepassen op de bestaande elementen in de map, moet u de map opnieuw verwerken. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->Op deze manier zouden de bestaande elementen nu in aanmerking komen om deel uit te maken van een set afbeeldingen of een set scènes en worden toegevoegd. Bovendien worden de bestaande elementen die al waren opgenomen in de afbeeldingsset of de spin-set - op basis van de vorige batch-set die is gebruikt - niet verwijderd en weergegeven zoals ze zijn. In dit scenario wordt ervan uitgegaan dat ze niet langer in aanmerking komen op basis van de zojuist bewerkte voorinstelling.

**Een voorinstelling voor een batch-set bewerken:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Op de **[!UICONTROL Batch Set Presets]** pagina, links van **[!UICONTROL Preset Name]** de batch-set controleren die u wilt wijzigen.
1. Selecteer in de werkbalk de optie **[!UICONTROL Edit Batch Set Preset]**.
1. Bewerk de voorinstelling naar wens.
1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Batch Set Preset]** pagina, selecteert u **[!UICONTROL Save]**.

## Een bestaande voorinstelling voor een batchset kopiëren {#copy-bsp}

U kunt een bestaande voorinstelling voor een batch-set kopiëren om te voorkomen dat u handmatig een complexe voorinstelling opnieuw moet maken of om de naam van een voorinstelling te wijzigen. U kunt het gebruikte type voorinstelling (Afbeeldingsset of Spin-set) echter niet wijzigen.

Als u een bestaande voorinstelling kopieert die door elementmappen wordt gebruikt, worden deze mappen niet gewijzigd.

**Een bestaande voorinstelling voor een batchset kopiëren:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Op de **[!UICONTROL Batch Set Presets]** pagina, links van **[!UICONTROL Preset Name]** selecteert u het selectievakje van de voorinstelling voor de batchset die u wilt kopiëren.
1. Selecteer in de werkbalk de optie **[!UICONTROL Copy]**.
1. In de **[!UICONTROL Copy Batch Set Preset]** in het dialoogvenster **[!UICONTROL Title]** typt u een nieuwe naam voor de voorinstelling.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Selecteer **[!UICONTROL Copy]**.

## Voorinstellingen voor batchsets verwijderen uit mappen {#remove-bsp-from-folder}

Wanneer u voorinstellingen voor batchsets uit mappen verwijdert, wordt de batchset niet toegepast op nieuwe elementen die u uploadt naar deze mappen. Bestaande elementen in de map die al zijn toegevoegd aan de afbeeldingsset of de spint-set op basis van een batchset-voorinstelling die is toegepast op de map en die ongewijzigd worden weergegeven.

Als u wilt *delete* voorinstellingen uit mappen, zie [Voorinstellingen voor batchsets verwijderen](#delete-bsp).

Er zijn twee methoden waarmee u voorinstellingen voor batchsets kunt verwijderen uit mappen.

* [Voorinstellingen voor batchsets uit mappen verwijderen op basis van de pagina Voorinstelling voor batchset](#remove-bsp-from-folders-via-bsp-page) - Deze methode biedt u de meeste flexibiliteit. U kunt één voorinstelling of meerdere voorinstellingen uit één map of uit meerdere mappen verwijderen.
* [Voorinstellingen voor batchsets verwijderen uit de eigenschappenpagina van een map](#remove-bsp-from-folders-via-properties) - Met deze methode kunt u een of meer voorinstellingen voor batchsets uit slechts één map verwijderen.

### Voorinstellingen voor batchsets uit mappen verwijderen op basis van de pagina Voorinstelling voor batchset {#remove-bsp-from-folders-via-bsp-page}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Op de **[!UICONTROL Batch Set Presets]** pagina, links van **[!UICONTROL Preset Name]** selecteert u het selectievakje van een of meer voorinstellingen voor batchsets die u uit een of meer mappen wilt verwijderen.
1. Selecteer in de werkbalk de optie **[!UICONTROL Remove Batch Preset from Folders]**.

1. Op de **[!UICONTROL Select Folders]** selecteert u een of meer mappen waarin u de voorinstellingen van de batchset wilt verwijderen.
1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Select Folders]** pagina, selecteert u **[!UICONTROL Remove]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. In de **[!UICONTROL Remove profile]** dialoogvenster selecteert u **[!UICONTROL Remove]**.

### Voorinstellingen voor batchsets verwijderen uit de eigenschappenpagina van een map {#remove-bsp-from-folders-via-properties}

1. Selecteer het logo van de Experience Manager en navigeer naar **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar een map waarnaar u een of meer voorinstellingen voor een batch-set wilt verwijderen.
1. Op de pagina, links van **[!UICONTROL Name]** selecteert u het selectievakje van een map.
1. Selecteer in de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer op de pagina Eigenschappen van de map de optie **[!UICONTROL Dynamic Media Processing]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Onder **[!UICONTROL Batch Set Presets]**, selecteert u **[!UICONTROL X]** rechts van het type voorinstelling.

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save & Close]**.

## Voorinstellingen voor batchsets verwijderen {#delete-bsp}

U kunt voorinstellingen van batchsets verwijderen om deze permanent te verwijderen uit [!DNL Dynamic Media]. Dat wil zeggen dat ze niet meer op de [!UICONTROL Batch Set Preset] en worden niet weergegeven in de **[!UICONTROL Batch Set Presets]** vervolgkeuzelijst van de **[!UICONTROL Dynamic Media Processing]** op de map **[!UICONTROL Properties]** pagina. De voorinstelling wordt daarom niet toegepast op bestaande elementen in een map die opnieuw wordt verwerkt of wanneer nieuwe elementen in de map worden geüpload.

Als u een voorinstelling verwijdert die eerder op een of meer mappen is toegepast, worden alle sets afbeeldingen of centrifuges die op basis van elementen in die mappen zijn gemaakt, ongewijzigd weergegeven.

Als u wilt *remove* voorinstellingen uit mappen, zie [Voorinstellingen voor batchsets verwijderen uit mappen](#remove-bsp-from-folder).

**Voorinstellingen voor batchsets verwijderen:**

1. Selecteer het logo van de Experience Manager en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Op de **[!UICONTROL Batch Set Presets]** pagina, links van **[!UICONTROL Preset Name]** selecteert u het selectievakje van een of meer voorinstellingen voor batchsets die u wilt verwijderen.
1. Selecteer in de werkbalk de optie **[!UICONTROL Delete Batch Set Presets]**.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. In de **[!UICONTROL Delete Batch Set Presets]** dialoogvenster selecteert u **[!UICONTROL Delete]**.

   Als in een elementmap naar de voorinstelling die u verwijdert, wordt verwezen, selecteert u **[!UICONTROL Force Delete]** in plaats daarvan.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Image Sets](/help/assets/dynamic-media/image-sets.md)
>* [Spin Sets](/help/assets/dynamic-media/spin-sets.md)
>* [Selectieve publicatie op mapniveau in Dynamic Media configureren](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder) - Zie &#39;Synchronisatiemodus&#39; in het onderwerp als u meer wilt weten over het synchroniseren van één map naar [!DNL Dynamic Media].
>* [Een Dynamic Media-configuratie maken in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) - Zie &quot;Dynamic Media-synchronisatiemodus&quot; in het onderwerp als u meer wilt weten over het synchroniseren van alle mappen naar [!DNL Dynamic Media].

