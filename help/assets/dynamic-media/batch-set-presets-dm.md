---
title: Voorinstellingen batchset
description: Leer hoe u afbeeldingssets kunt automatiseren en het maken van centrifuges kunt uitvoeren met behulp van voorinstellingen voor batchsets in Dynamic Media.
contentOwner: Rick Brough
feature: Voorinstellingen afbeelding, voorinstellingen viewer
topic: Zakelijke praktiserer
translation-type: tm+mt
source-git-commit: 80a59a02067d478713aa7dcdb436ad1345d89c1a
workflow-type: tm+mt
source-wordcount: '3191'
ht-degree: 0%

---


# Voorinstellingen batchset {#about-bsp}

Gebruik **[!UICONTROL Batch Set Presets]** om het maken en organiseren van meerdere elementen in een set afbeeldingen te vereenvoudigen en om te draaien op het moment dat u elementbestanden uploadt naar een map, afzonderlijk of met bulkopname. U kunt de voorinstelling laten uitvoeren naast de taken voor het importeren van elementen die u in [!DNL Dynamic Media] plant. Elke voorinstelling is een op zichzelf staande verzameling instructies met een unieke naam die definieert hoe de set afbeeldingen moet worden samengesteld of hoe de set moet worden gecentreerd met afbeeldingen die overeenkomen met de gedefinieerde naamgevingsconventies in het vooraf ingestelde recept.

>[!IMPORTANT]
>
>Als u voorinstellingen voor batchsets hebt gebruikt in [!DNL Dynamic Media Classic] en als Cloud Service migreert van [!DNL Dynamic Media Classic] naar Adobe Experience Manager, moet u de definities van voorinstellingen voor batchsets handmatig opnieuw maken in [!DNL Adobe Experience Manager as a Cloud Service].

**Best Practice**  - Als u werkt met voorinstellingen voor batchsets, wordt door Adobe de volgende workflow aanbevolen:

1. Maak een voorinstelling voor een batchset. Zie [Een voorinstelling voor een batchset maken voor een afbeeldingsset of een spin-set](#creating-bsp).
1. Maak een elementmap of gebruik een bestaande elementmap en zorg ervoor dat deze wordt gesynchroniseerd met [!DNL Dynamic Media]. Zie [Mappen maken](/help/assets/manage-digital-assets.md#creating-folders).
1. Pas de voorinstelling voor de batchset toe op de map met elementen. Zie [Batchsetvoorinstellingen toepassen op mappen](#apply-bsp).
1. Afbeeldingen uploaden naar de elementmap. Zie [Elementen uploaden voor afbeeldingssets](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Elementen uploaden voor centrifuges](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) of [Digitale elementen toevoegen aan Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. Maak een afbeeldingsset of centrifugeset. Zie [Afbeeldingssets](/help/assets/dynamic-media/image-sets.md) of [Spin Sets](/help/assets/dynamic-media/spin-sets.md).
1. Publiceer de afbeeldingsset of de centrifugeset. Zie [Dynamic Media-middelen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Een voorinstelling voor een batch-set maken voor een afbeeldingsset of een spin-set {#creating-bsp}

Als u voorinstellingen voor batch-sets wilt maken, is het wenselijk dat u enige kennis en begrip hebt van reguliere expressies.

Idealiter heeft uw bedrijf al een naamgevingsconventie gedefinieerd voor de manier waarop elementen in een set worden gegroepeerd.
Om u te helpen het belang begrijpen van het gebruiken van een noemende overeenkomst, veronderstel de bepaalde noemende overeenkomst van uw bedrijf `<style>-<color>-<view>` is. En, moet de basisnaam voor de reeks altijd `<style>-<color>` zijn, en de vastgestelde naamuitbreiding is `-SET`. Als u een afbeelding met de naam `0123-RED-01` uploadt, wordt een set gemaakt met de naam `0123-RED-SET`. Als u later afbeeldingen `0123-RED-03` en `0123-BLUE-01` uploadt, wordt de `RED-03` afbeelding toegevoegd aan de set op de tweede positie omdat deze lager wordt gesorteerd dan `01`. De `BLUE-01`-afbeelding zou echter deel uitmaken van een nieuwe set met de naam `0123-BLUE-SET`. Voor de volgende asset upload voegt u bestanden `0123-RED-02` en `0123-BLUE-02` toe. Elk activum zou aan zijn respectieve reeks worden toegevoegd. De `RED-02`-afbeelding wordt vanwege de sorteervolgorde automatisch gesorteerd tussen de bestaande `01`- en `03`-afbeeldingen.

Met de **[!UICONTROL Batch Set Preset]**-pagina in [!DNL Dynamic Media] kunt u voorinstellingen voor batchsets maken, bewerken of verwijderen en kunt u voorinstellingen voor batchsets toepassen op of verwijderen uit elementmappen. U kunt de vervolgkeuzelijsten voor formuliervelden gebruiken om een voorinstelling voor een batchset te definiëren of het veld **[!UICONTROL Raw Code]** gebruiken, waarmee u de syntaxis van reguliere expressies kunt typen.

U kunt zoveel voorinstellingen voor batchsets maken als nodig zijn om alle taken voor het opnemen van elementen die u nodig hebt, te kunnen uitvoeren.

**Info over Asset Naming Convention**

Het gebied **[!UICONTROL Asset Naming Convention]** op de pagina **[!UICONTROL Batch Set Preset]** bevat twee elementen die u kunt gebruiken om de voorinstelling voor de batchset te definiëren: **[!UICONTROL Match]** en **[!UICONTROL Base Name]**. Met deze elementen kunt u een naamgevingsconventie definiëren en het gedeelte van de conventie identificeren dat wordt gebruikt om de set met namen te benoemen. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

De individuele noemende overeenkomst van een bedrijf gebruikt vaak één of meerdere lijnen van definitie van elk van deze twee elementen. U kunt zo vele lijnen voor uw unieke definitie gebruiken en hen groeperen in verschillende elementen, zoals voor HoofdBeeld, het element van de Kleur, het element van de Afwisselende Mening, en het element van het Monster.

De syntaxis voor een reguliere expressie van letterlijke overeenkomsten kan er bijvoorbeeld als volgt uitzien:

`(\w+)-\w+-\w+`

**Info Volgorde**

U kunt desgewenst de volgorde definiëren waarin afbeeldingen worden weergegeven nadat de afbeeldingsset of de centrifugeset is gegroepeerd in [!DNL Dynamic Media]. Uw elementen worden standaard alfanumeriek geordend. U kunt echter een door komma&#39;s gescheiden lijst met reguliere expressies gebruiken om de volgorde te definiëren.

Met betrekking tot volgorde die automatisering ordent, geeft u regels op om elementen op een bepaalde manier te forceren, indien nodig. Stel dat uw eerste element altijd de naam `_main` heeft en u wilt dat het wordt gevolgd met `_alt1`, `_alt2`, `_alt3` enzovoort. In dergelijke gevallen kunt u een volgorderegel maken met de volgende syntaxis:

`.*_main,.*_alt[0-9]`

Hoewel een geforceerde sorteervolgorde mogelijk is, is het beter om zoveel mogelijk te vertrouwen op alfanumerieke nummering voor volgordevolgorde. Daarnaast kunt u de set afbeeldingen of de gereedschappen voor de editor van de spin-set in [!DNL Dynamic Media] gebruiken om de volgorde van elementen eenvoudig te wijzigen of nieuwe elementen in de set toe te voegen en te verwijderen met behulp van slepen en neerzetten.

Wanneer u klaar bent met het maken van een voorinstelling voor een batch-set, past u deze toe op een of meer mappen die u hebt gemaakt. Zie [Batchsetvoorinstellingen toepassen op mappen](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**U kunt als volgt een voorinstelling voor een batch-set maken voor een afbeeldingsset of een centrifugeset:**

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Tik op de pagina **[!UICONTROL Batch Set Presets]** in de rechterbovenhoek op **[!UICONTROL Create]**.
1. Voer in het dialoogvenster **[!UICONTROL Create Batch Set Preset]** in het tekstveld **[!UICONTROL Preset Name]** een beschrijvende naam in. De naam van de voorinstelling kan niet worden bewerkt als u deze later wijzigt.

1. Selecteer **[!UICONTROL ImageSet]** of **[!UICONTROL SpinSet]** in de vervolgkeuzelijst **[!UICONTROL Preset Type]**. Zorg ervoor dat u het juiste vooraf ingestelde type kiest. het kan later niet worden bewerkt.
1. Tik op **[!UICONTROL Create]**.
1. Rechts van de pagina **[!UICONTROL Edit Batch Set Preset]** stelt u de gewenste bewerkbare opties in onder de koppen **[!UICONTROL Preset Details]** en **[!UICONTROL Set Naming Convention]**.
Meer over de editable opties leren die aan u beschikbaar zijn, zie [Vooraf ingestelde Details, Vastgestelde het Noemen Overeenkomst, en de Resultaten van de Regel - opties RegX](#features-options-bsp).

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Maak een of meer reguliere-expressiegroepen.

   * Tik links van de pagina **[!UICONTROL Edit Batch Set Preset]** onder **[!UICONTROL Match]**, **[!UICONTROL Base Name]** of **[!UICONTROL Sequence Ordering]** op **[!UICONTROL Add Group]**.
   * Het veld **[!UICONTROL Match]** is vereist. **[!UICONTROL Base Name]** is alleen verplicht als in het  **[!UICONTROL Match]** veld nog geen basisnaam is opgegeven met behulp van een haakjesgroep. **[!UICONTROL Sequence Ordering]** is optioneel.
   * Geef met behulp van de vervolgkeuzelijsten en tekstvakken in het groepsformulier een expressiegroep op die u wilt gebruiken voor het definiëren van de naamgevingscriteria voor de leden van de afbeeldingsset of de set elementen.
      * Terwijl u expressies voor een groep selecteert en opgeeft, ziet u dat de werkelijke syntaxis van de reguliere expressie rechtsonder op de pagina wordt weergegeven onder de kop **[!UICONTROL Rule Results - RegX]** (tik ergens buiten het formuliergebied om de reguliere-expressietekenreeks rechtsonder te zien). Deze reguliere-expressietekenreeksen vertegenwoordigen het patroon dat u wilt afstemmen in een zoekopdracht naar [!DNL Dynamic Media]-elementen om uw afbeeldingsset of centrifugeset te maken.
      * Tik op **[!UICONTROL X]** om een toegevoegde groep te verwijderen.
   * Wanneer u twee of meer groepen toevoegt, selecteert u in de vervolgkeuzelijst **[!UICONTROL And]** **[!UICONTROL And]** om een zojuist toegevoegde groep samen te voegen met een vorige expressiegroep die u hebt toegevoegd. Of selecteer **[!UICONTROL Or]** om een alternatief tussen de vorige uitdrukkingsgroep en de nieuwe groep toe te voegen u creeert. De operand **[!UICONTROL Or]** wordt gedefinieerd door het gebruik van een verticaal lijnteken `|` in de syntaxis van de reguliere expressie zelf.

1. Voer een van de volgende handelingen uit:

   * Tik **[!UICONTROL Add Group]** onder **[!UICONTROL Match]**, **[!UICONTROL Base Name]** of **[!UICONTROL Sequencing Order]** op een andere nieuwe groep. Maak een andere reguliere-expressiegroep zoals u in de vorige stap hebt gedaan.
   * Controleer de syntaxis van de reguliere expressie in het gebied **[!UICONTROL Rule Results - RegX]**. Als u de syntaxis moet wijzigen, voert u de bewerkingen uit in de desbetreffende groep links op de pagina.
   * Ga door met de volgende stap als u klaar bent met het maken van expressiegroepen.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.

U wordt nu gelezen om de voorinstelling voor de batchset toe te passen op een of meer elementmappen, elementen te uploaden naar de map en vervolgens uw afbeeldingsset of centrifugeset te maken. Zie [Batchsetvoorinstellingen toepassen op mappen](#apply-bsp).

### Details voorinstelling, Naamgevingsconventie instellen en Regelresultaten - RegX-opties {#features-options-bsp}

Deze opties zijn beschikbaar op de pagina **[!UICONTROL Edit Batch Set Preset]** wanneer u een voorinstelling voor een batch-set maakt of bewerkt.

Zie [Een voorinstelling voor een batchset maken voor een afbeeldingsset of een spin-set](#creating-bsp) of [Een voorinstelling voor een batchset bewerken](#edit-bsp).

| **[!UICONTROL Preset Details]** | Beschrijving |
| --- | --- |
| Naam voorinstelling | Alleen-lezen. De naam die u hebt opgegeven toen u de batch-set voor het eerst maakte. Als u de naam van de voorinstelling moet wijzigen, kunt u de bestaande voorinstelling voor een batch-set kopiëren en een nieuwe naam opgeven. Zie [Een bestaande voorinstelling voor een batchset kopiëren](#copy-bsp). |
| Type | Alleen-lezen. Het type is opgegeven toen u de batch-set voor het eerst hebt gemaakt. Als u een bestaande voorinstelling voor een batch-set kopieert, kunt u de [!UICONTROL Type] niet wijzigen; u moet een voorinstelling maken. |
| Afgeleide activa opnemen | Optioneel. Als u wilt dat de IPS van [!DNL Dynamic Media] (het Systeem van de Productie van het Beeld) geproduceerde of &quot;afgeleide&quot;beelden met uw Vastgestelde Spin of Reeks van het Beeld omvat, uitgezocht **[!UICONTROL Yes]** (gebrek). Een afgeleid element is een afbeelding die niet rechtstreeks door een gebruiker is geüpload. In plaats daarvan, werd de activa geproduceerd door IPS toen een master middel werd geupload. Een afbeeldingselement dat IPS bijvoorbeeld genereert op basis van een pagina in een PDF, op het moment dat de PDF werd geüpload in [!DNL Dynamic Media], wordt beschouwd als een afgeleid element. |
| Doelmap | Optioneel. Als u grote aantallen afbeeldingssets of centrifuges definieert, raadt Adobe u aan deze sets los te houden van de mappen die de elementen zelf bevatten. Als dusdanig, denk na creërend een Reeksen van het Beeld of de omslag van de Reeksen van de Rotatie en richt de toepassing om partij te plaatsen geproduceerde reeksen hier.<br>Geef in dat geval op in welke map in de mapstructuur (`/content/dam`) van Experience Manager Assets de voorinstelling voor de batch-set actief is. Zorg ervoor dat de omslag voor [!DNL Dynamic Media] synchronisatie wordt toegelaten om het als bestemmingsomslag toe te staan. Zie [Selectieve publicatie configureren op mapniveau in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br>Aan meerdere mappen kan een bepaalde voorinstelling voor een batchset zijn toegewezen, als u de voorinstelling via de map toepast  **[!UICONTROL Properties]**. Zie [Voorinstellingen voor batchsets toepassen vanaf de pagina Eigenschappen van een elementmap](#apply-bsp-to-folders-via-properties).<br>Als u geen map opgeeft, wordt de voorinstelling van de batchset gemaakt in dezelfde map als de map voor het uploaden van middelen. |
| **[!UICONTROL Set Naming Convention]** |  |
| Voorvoegsel<br>of<br>Achtervoegsel | Optioneel. Voer een voor- of achtervoegsel of beide in de desbetreffende velden in.<br>Met de velden voor het voorvoegsel en het achtervoegsel kunt u zoveel voorinstellingen voor batchsets maken met een alternatieve naamgevingsconventie voor aangepaste bestanden voor een bepaalde set inhoud. Deze methode is vooral handig in gevallen waarin er een uitzondering is op de standaardnaamgevingsregeling van een bedrijf.<br>Het voor- of achtervoegsel wordt toegevoegd aan het  **[!UICONTROL Base Name]** kader dat u in het  **[!UICONTROL Asset Naming Convention]** gebied definieert. Door een voor- of achtervoegsel toe te voegen, zorgt u ervoor dat de set afbeeldingen of de set met centrifuges uitsluitend en onafhankelijk van andere elementen wordt gemaakt. Het kan ook worden gebruikt om anderen te helpen dossiertypes identificeren. Als u bijvoorbeeld een gebruikte kleurmodus wilt bepalen, kunt u `rgb` of `cmyk` als voor- of achtervoegsel toevoegen.<br>Als u een naamgevingsconventie voor sets opgeeft, is het niet nodig vooraf ingestelde functies voor batchsets te gebruiken, maar aanbevolen wordt om de naamgevingsconventie voor sets te gebruiken. Op deze manier kunt u zoveel elementen van uw naamgevingsconventie definiëren als u wilt groeperen in een set om het maken van batchsets te stroomlijnen. |
| **[!UICONTROL Rule Results - RegX]** |  |
| Naamgevingsconventie voor middelen - Overeenkomst | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de gekozen formulieropties of de ingevoerde onbewerkte code. |
| Naamgevingsconventie voor middelen - Basisnaam | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de basisnaamadopties die u hebt gekozen of de onbewerkte code die u hebt ingevoerd. |
| Volgorde - Overeenkomst | Alleen-lezen. Hiermee geeft u de syntaxis van de reguliere expressie weer op basis van de formulieropties die u hebt gekozen of de onbewerkte code die u hebt ingevoerd. |

## Voorinstellingen voor batchsets toepassen op mappen {#apply-bsp}

Wanneer u voorinstellingen voor batchsets toewijst aan een of meer mappen, nemen submappen de voorinstellingen automatisch over van de bovenliggende map.

U kunt meerdere voorinstellingen voor batchsets toepassen op een map.

Mappen waaraan een batchvoorinstelling is toegewezen, worden in de gebruikersinterface aangeduid met de naam van de voorinstelling die wordt weergegeven in de map, in de weergave **[!UICONTROL Card]**.

Als u voorinstellingen voor batchsets wilt toepassen op mappen, gebruikt u een van de volgende twee methoden:

* [Voorinstellingen voor batchsets toepassen op elementmappen vanaf de pagina](#apply-bsp-to-folders-via-bsp-page)  Voorinstelling voor batchset - Deze methode biedt u de meeste flexibiliteit. U kunt één voorinstelling of meerdere voorinstellingen toepassen op één map of op meerdere mappen.
* [Voorinstellingen voor batchsets toepassen vanaf de pagina](#apply-bsp-to-folders-via-properties)  Eigenschappen van een elementmap - Met deze methode kunt u een of meer voorinstellingen voor batchsets toepassen op één map.

U kunt het beste de elementmappen [!DNL Dynamic Media] synchroniseren en vervolgens de gewenste voorinstellingen toepassen.

Elementen in een map opnieuw verwerken als u een van de volgende twee situaties ervaart:

* U wilt een voorinstelling voor een batchset uitvoeren op een bestaande elementenmap waarin al elementen zijn geüpload.
* U bewerkt later een bestaande voorinstelling voor een batch-set die eerder is toegepast op een map met elementen.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Voorinstellingen voor batchsets toepassen op elementmappen vanaf de pagina Voorinstelling batch instellen {#apply-bsp-to-folders-via-bsp-page}

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van elke voorinstelling voor batch-sets die u wilt toepassen op mappen.
1. Tik op **[!UICONTROL Apply Batch Preset to Folders]** op de werkbalk.
1. Schakel op de pagina **[!UICONTROL Select Folders]** het selectievakje in van elke map waarop de voorinstellingen voor batchsets moeten worden toegepast.
1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Select Folders]** op **[!UICONTROL Apply]**.

### Voorinstellingen voor batchsets toepassen vanaf de pagina Eigenschappen van een elementmap {#apply-bsp-to-folders-via-properties}

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar een map waarop u een of meer voorinstellingen voor batchsets wilt toepassen.
1. Schakel op de pagina, links van de kolom **[!UICONTROL Name]**, het selectievakje van een map in.
1. Tik op **[!UICONTROL Properties]** op de werkbalk.
1. Tik op het tabblad **[!UICONTROL Dynamic Media Processing]** op de pagina Eigenschappen van de map.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Selecteer onder **[!UICONTROL Batch Set Presets]** in de vervolgkeuzelijst **[!UICONTROL Preset Name]** de naam van een voorinstelling voor een batch-set die u wilt toepassen. In de bovenstaande schermafbeelding ziet u twee geselecteerde voorinstellingen voor batchsets die op de map zijn toegepast.

   Als het vervolgkeuzemenu **[!UICONTROL Preset Name]** geen naam bevat voor voorinstellingen voor batchsets, hebt u nog geen voorinstellingen voor batchsets gemaakt. Zie [Een voorinstelling voor een batchset maken voor een afbeeldingsset of een spin-set](#creating-bsp).

   Tik op **[!UICONTROL X]** rechts van het type voorinstelling om een toegepaste voorinstelling voor een batch-set te verwijderen.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save & Close]**.

## Een voorinstelling voor een batchset bewerken {#edit-bsp}

U kunt een bestaande voorinstelling voor een batch-set bewerken die u hebt gemaakt. U kunt om het even welke uitdrukkingsgroepen veranderen u voor de activa noemende overeenkomst of opeenvolgingsorde creeerde. Indien nodig kunt u ook de doelmap bijwerken en naamgevingsconventies instellen.

U kunt de naam of het type voorinstelling (Afbeeldingsset of Draaiset) van de voorinstelling echter niet wijzigen. Als de naam van een voorinstelling moet worden gewijzigd, kunt u gewoon de bestaande voorinstelling kopiëren en een nieuwe naam opgeven. Zie [Een voorinstelling voor een batchset kopiëren](#copy-bsp).

Als u een vooraf ingestelde batch-set bewerkt die eerder op een map is toegepast, wordt de opnieuw bewerkte voorinstelling alleen toegepast op nieuwe elementen die naar de map zijn geüpload.

Als u de zojuist bewerkte voorinstelling opnieuw wilt toepassen op de bestaande elementen in de map, moet u de map opnieuw verwerken. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->Op deze manier zouden de bestaande elementen nu in aanmerking komen om deel uit te maken van een set afbeeldingen of een set scènes en worden toegevoegd. Bovendien worden de bestaande elementen die al waren opgenomen in de afbeeldingsset of die op basis van de vorige batch-set waren ingesteld en die werden gebruikt, niet verwijderd (ervan uitgaande dat ze niet langer in aanmerking komen op basis van de zojuist bewerkte voorinstelling) en weergeven als zijnde.

**Een voorinstelling voor een batchset bewerken:**

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets.]**
1. Controleer op de pagina **[!UICONTROL Batch Set Presets]**, links van de kolom **[!UICONTROL Preset Name]**, de batch-set die u wilt wijzigen.
1. Tik in de werkbalk op **[!UICONTROL Edit Batch Set Preset.]**
1. Bewerk de voorinstelling naar wens.
1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Batch Set Preset]** op **[!UICONTROL Save.]**

## Een bestaande voorinstelling voor een batchset kopiëren {#copy-bsp}

U kunt een bestaande voorinstelling voor een batch-set kopiëren om te voorkomen dat u handmatig een complexe voorinstelling opnieuw moet maken of om de naam van een voorinstelling te wijzigen. U kunt het gebruikte type voorinstelling (Afbeeldingsset of Spin-set) echter niet wijzigen.

Als u een bestaande voorinstelling kopieert die door elementmappen wordt gebruikt, worden deze mappen niet gewijzigd.

**Een bestaande voorinstelling voor een batchset kopiëren:**

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets.]**
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van de voorinstelling voor de batchset die u wilt kopiëren.
1. Tik op **[!UICONTROL Copy]** op de werkbalk.
1. Typ in het dialoogvenster **[!UICONTROL Copy Batch Set Preset]** een nieuwe naam voor de voorinstelling in het tekstvak **[!UICONTROL Title]**.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Tik op **[!UICONTROL Copy]**.

## Voorinstellingen voor batchsets verwijderen uit mappen {#remove-bsp-from-folder}

Wanneer u voorinstellingen voor batchsets uit mappen verwijdert, wordt de batchset niet toegepast op nieuwe elementen die u uploadt naar deze mappen. Bestaande elementen in de map die al zijn toegevoegd aan de afbeeldingsset of de spint-set op basis van een batchset-voorinstelling die is toegepast op de map en die ongewijzigd worden weergegeven.

Zie [Voorinstellingen voor batchsets verwijderen](#delete-bsp) als u voorinstellingen *uit mappen wilt verwijderen.*

Er zijn twee methoden waarmee u voorinstellingen voor batchsets kunt verwijderen uit mappen.

* [Voorinstellingen voor batchsets uit mappen verwijderen via de pagina](#remove-bsp-from-folders-via-bsp-page)  Voorinstelling voor batchset - Deze methode biedt u de meeste flexibiliteit. U kunt één voorinstelling of meerdere voorinstellingen uit één map of uit meerdere mappen verwijderen.
* [Voorinstellingen voor batchsets verwijderen uit de eigenschappenpagina](#remove-bsp-from-folders-via-properties)  van een map - Met deze methode kunt u een of meer voorinstellingen voor batchsets uit slechts één map verwijderen.

### Voorinstellingen voor batchsets verwijderen uit mappen met behulp van de pagina Voorinstelling voor batchset {#remove-bsp-from-folders-via-bsp-page}

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van een of meer voorinstellingen voor batchsets die u uit een of meer mappen wilt verwijderen.
1. Tik op **[!UICONTROL Remove Batch Preset from Folders]** op de werkbalk.

1. Selecteer op de pagina **[!UICONTROL Select Folders]** een of meer mappen waarin u de voorinstellingen van de batchset wilt verwijderen.
1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Select Folders]** op **[!UICONTROL Remove]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Tik in het dialoogvenster **[!UICONTROL Remove profile]** op **[!UICONTROL Remove]**.

### Voorinstellingen voor batchsets verwijderen uit de eigenschappenpagina van een map {#remove-bsp-from-folders-via-properties}

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar een map waarnaar u een of meer voorinstellingen voor een batch-set wilt verwijderen.
1. Schakel op de pagina, links van de kolom **[!UICONTROL Name]**, het selectievakje van een map in.
1. Tik op **[!UICONTROL Properties]** op de werkbalk.
1. Tik op **[!UICONTROL Dynamic Media Processing]** op de pagina Eigenschappen van de map.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Tik onder **[!UICONTROL Batch Set Presets]** rechts van het type voorinstelling op **[!UICONTROL X]**.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save & Close]**.

## Voorinstellingen voor batchsets {#delete-bsp} verwijderen

U kunt voorinstellingen van batchsets verwijderen om deze definitief te verwijderen uit [!DNL Dynamic Media]. Dat wil zeggen dat ze niet meer worden weergegeven op de pagina [!UICONTROL Batch Set Preset] en ook niet worden weergegeven in de vervolgkeuzelijst **[!UICONTROL Batch Set Presets]** van het tabblad **[!UICONTROL Dynamic Media Processing]** op de pagina **[!UICONTROL Properties]** van de map. De voorinstelling wordt daarom niet toegepast op bestaande elementen in een map die opnieuw wordt verwerkt of wanneer nieuwe elementen in de map worden geüpload.

Als u een voorinstelling verwijdert die eerder op een of meer mappen is toegepast, worden alle sets afbeeldingen of centrifuges die op basis van elementen in die mappen zijn gemaakt, ongewijzigd weergegeven.

Zie [Voorinstellingen voor batchsets verwijderen uit mappen *Als u voorinstellingen voor ](#remove-bsp-from-folder)verwijderen* uit mappen wilt verwijderen.

**Voorinstellingen voor batchsets verwijderen:**

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Batch Set Presets]**.
1. Schakel op de pagina **[!UICONTROL Batch Set Presets]** links van de kolom **[!UICONTROL Preset Name]** het selectievakje in van een of meer voorinstellingen voor batchsets die u wilt verwijderen.
1. Tik op **[!UICONTROL Delete Batch Set Presets]** op de werkbalk.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. Tik in het dialoogvenster **[!UICONTROL Delete Batch Set Presets]** op **[!UICONTROL Delete]**.

   Tik **[!UICONTROL Force Delete]** in plaats van op de voorinstelling die u verwijdert, door een elementmap naar de voorinstelling die u verwijdert.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Image Sets](/help/assets/dynamic-media/image-sets.md)
>* [Spin Sets](/help/assets/dynamic-media/spin-sets.md)
>* [Selectieve publicatie op mapniveau configureren in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder)  - Zie &#39;Synchronisatiemodus&#39; in het onderwerp voor meer informatie over het synchroniseren van één map naar  [!DNL Dynamic Media].
>* [Een Dynamic Media-configuratie maken in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)  - Zie &#39;Dynamic Media sync mode&#39; in het onderwerp voor meer informatie over het synchroniseren van alle mappen naar  [!DNL Dynamic Media].