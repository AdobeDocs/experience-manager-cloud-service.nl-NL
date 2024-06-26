---
title: Hoe te om de regelredacteur te gebruiken om regels aan vormgebieden toe te voegen om dynamisch gedrag toe te voegen en complexe logica aan een adaptieve vorm te bouwen?
description: Met de Adaptive Forms-regeleditor kunt u dynamisch gedrag toevoegen en complexe logica in formulieren opnemen zonder codes of scripts.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 6fd38e9e-435e-415f-83f6-3be177738c00
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '6292'
ht-degree: 0%

---

# Regels toevoegen aan een adaptief formulier {#adaptive-forms-rule-editor}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Foundation Components) | Dit artikel |
| AEM as a Cloud Service (Core Components) | [Klik hier](/help/forms/rule-editor-core-components.md) |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html) |

## Overzicht {#overview}

Met de functie voor regeleditors kunnen zakelijke gebruikers en ontwikkelaars regels schrijven voor adaptieve formulierobjecten. Met deze regels worden acties gedefinieerd die op formulierobjecten worden geactiveerd op basis van vooraf ingestelde voorwaarden, gebruikersinvoer en gebruikersacties op het formulier. Hierdoor wordt de ervaring met het invullen van formulieren verder gestroomlijnd, zodat u nauwkeurige en snelle informatie krijgt.

De regelredacteur verstrekt een intuïtieve en vereenvoudigde gebruikersinterface om regels te schrijven. De redacteur van de regel biedt een visuele redacteur voor alle gebruikers aan.<!-- In addition, only for forms power users, rule editor provides a code editor to write rules and scripts. --> Enkele belangrijke handelingen die u met behulp van regels kunt uitvoeren op adaptieve formulierobjecten:

* Een object tonen of verbergen
* Een object in- of uitschakelen
* Een waarde instellen voor een object
* De waarde van een object valideren
* Voer functies uit om de waarde van een object te berekenen
* Een service van het formuliergegevensmodel aanroepen en een bewerking uitvoeren
* Eigenschap van een object instellen

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

Gebruikers die zijn toegevoegd aan de gebruikersgroep voor formulieren, kunnen scripts maken en bestaande scripts bewerken. Gebruikers in de [!DNL forms-users] groep kan de scripts gebruiken, maar geen scripts maken of bewerken.

## Verschillen tussen de regeleditor in de kerncomponenten en de Regeleditor in basiscomponenten

{{rule-editor-diff}}

## Een regel begrijpen {#understanding-a-rule}

Een regel is een combinatie van handelingen en voorwaarden. In de regeleditor omvatten handelingen zoals verbergen, weergeven, inschakelen, uitschakelen of de waarde van een object in een formulier berekenen. Voorwaarden zijn Booleaanse expressies die worden geëvalueerd door controles en bewerkingen uit te voeren op de status, waarde of eigenschap van een formulierobject. Handelingen worden uitgevoerd op basis van de waarde ( `True` of `False`) geretourneerd door een voorwaarde te evalueren.

De regelredacteur verstrekt een reeks vooraf bepaalde regeltypes, zoals wanneer, tonen, verbergen, toelaten, onbruikbaar maken, Vastgestelde Waarde van, en Valideren om u te helpen regels schrijven. Elk regeltype laat u voorwaarden en acties in een regel bepalen. Het document verklaart verder elk regeltype in detail.

Een regel volgt doorgaans een van de volgende constructies:

**Voorwaarde-actie** In deze constructie definieert een regel eerst een voorwaarde gevolgd door een handeling die moet worden geactiveerd. De constructie is vergelijkbaar met if-then statement in programmeertalen.

In de regeleditor **Wanneer** het regeltype dwingt de voorwaarde-actie constructie af.

**Handeling-voorwaarde** In deze constructie, bepaalt een regel eerst een actie die door voorwaarden voor evaluatie wordt gevolgd teweegbrengen. Een andere variatie van deze constructie is actie-voorwaarde-afwisselende actie, die ook een afwisselende actie bepaalt om te teweegbrengen als de voorwaarde Vals terugkeert.

Toon, verberg, laat toe, maak onbruikbaar, plaats Waarde van, en bevestig regeltypes in regelredacteur om de actie-voorwaarde regelconstructie af te dwingen. Standaard is de alternatieve actie voor Tonen Verbergen en voor Inschakelen Uitgeschakeld en de tegenovergestelde manier. U kunt de alternatieve standaardhandeling niet wijzigen.

>[!NOTE]
>
>De beschikbare regeltypen, inclusief de voorwaarden en handelingen die u in de regeleditor definieert, zijn ook afhankelijk van het type formulierobject waarop u een regel maakt. In de regeleditor worden alleen geldige regeltypen en opties weergegeven voor het schrijven van voorwaarde- en handelingsinstructies voor een bepaald type formulierobject. U ziet bijvoorbeeld geen regeltypen Valideren, Waarde instellen van, Inschakelen en Uitschakelen voor een deelvensterobject.

Voor meer informatie over regeltypes beschikbaar in de regelredacteur, zie [Beschikbare regeltypen in regeleditor](rule-editor.md#p-available-rule-types-in-rule-editor-p).

### Richtlijnen voor het kiezen van een regelconstructie {#guidelines-for-choosing-a-rule-construct}

Hoewel u de meeste gebruiksgevallen kunt bereiken door om het even welke regelconstructie te gebruiken, zijn hier sommige richtlijnen om één constructie over een andere te kiezen. Voor meer informatie over de beschikbare regels in regelredacteur, zie [Beschikbare regeltypen in regeleditor](rule-editor.md#p-available-rule-types-in-rule-editor-p).

* Een typische regel van het duim wanneer het creëren van een regel is het denken over het in de context van het voorwerp waarop u een regel schrijft. Denk eraan dat u veld B wilt verbergen of weergeven op basis van de waarde die een gebruiker in veld A heeft opgegeven. In dit geval evalueert u een voorwaarde in veld A en activeert u een actie in veld B op basis van de waarde die de voorwaarde retourneert.

  Daarom als u een regel op gebied B (het voorwerp schrijft waarop u een voorwaarde) evalueert, gebruik de voorwaarde-actie constructie of het wanneer regeltype. Op dezelfde manier gebruikt u de handeling-voorwaarde constructie of toont of verbergt regeltype op gebied A.

* Soms moet u meerdere handelingen uitvoeren op basis van één voorwaarde. In dergelijke gevallen wordt aangeraden de voorwaarde-actieconstruct te gebruiken. In deze constructie, kunt u een voorwaarde eens evalueren en veelvoudige actieverklaringen specificeren.

  Als u bijvoorbeeld velden B, C en D wilt verbergen op basis van de voorwaarde die controleert of de waarde is opgegeven in veld A, schrijft u één regel met een construct voor voorwaarde-actie of wanneer-regeltype op veld A en geeft u handelingen op om de zichtbaarheid van velden B, C en D te bepalen. Anders hebt u drie aparte regels nodig voor de velden B, C en D, waar elke regel de voorwaarde controleert en het desbetreffende veld weergeeft of verbergt. In dit voorbeeld is het efficiënter om het Wanneer regeltype op één object te schrijven in plaats van Regeltype tonen of verbergen op drie objecten.

* Als u een actie wilt activeren op basis van meerdere voorwaarden, wordt aangeraden een handeling-voorwaardenconstructie te gebruiken. Als u bijvoorbeeld veld A wilt weergeven en verbergen door de voorwaarden in de velden B, C en D te evalueren, gebruikt u Regeltype tonen of verbergen in veld A.
* Gebruik een voorwaarde-handeling of handeling als de regel één handeling voor één voorwaarde bevat.
* Als een regel op een voorwaarde controleert en een actie onmiddellijk bij het verstrekken van een waarde op een gebied of het weggaan van een gebied uitvoert, wordt het geadviseerd om een regel met voorwaarde-actie constructie of het wanneer regeltype op het gebied te schrijven waarop de voorwaarde wordt geëvalueerd.
* De voorwaarde in wanneer regel wordt geëvalueerd wanneer een gebruiker de waarde van het voorwerp verandert waarop wanneer regel wordt toegepast. Als u echter wilt dat de actie wordt geactiveerd wanneer de waarde aan de serverzijde verandert, bijvoorbeeld bij het vooraf invullen van de waarde, kunt u het beste een When-regel schrijven die de actie activeert wanneer het veld wordt geïnitialiseerd.
* Wanneer u regels schrijft voor vervolgkeuzelijsten, keuzerondjes of selectievakjes, worden de opties of waarden van deze formulierobjecten in het formulier vooraf ingevuld in de regeleditor.

## Beschikbare operatortypen en gebeurtenissen in regeleditor {#available-operator-types-and-events-in-rule-editor}

De regeleditor biedt de volgende logische operatoren en gebeurtenissen waarmee u regels kunt maken.

* **Is gelijk aan**
* **Is niet gelijk aan**
* **Begint met**
* **Eindigt met**
* **Bevat**
* **Is leeg**
* **Is niet leeg**
* **Heeft geselecteerd:** Retourneert true wanneer de gebruiker een bepaalde optie voor een selectievakje, vervolgkeuzelijst of keuzerondje selecteert.
* **Is geïnitialiseerd (gebeurtenis):** Retourneert true wanneer een formulierobject in de browser wordt weergegeven.
* **Is gewijzigd (gebeurtenis):** Retourneert true wanneer de gebruiker de ingevoerde waarde of de geselecteerde optie voor een formulierobject wijzigt.
* **Navigatie (gebeurtenis):** Retourneert true wanneer de gebruiker op een navigatieobject klikt. Navigatieobjecten worden gebruikt om tussen deelvensters te navigeren.
* **Stap voltooid (gebeurtenis):** Retourneert true wanneer een stap van een regel is voltooid.
* **Verzending geslaagd (gebeurtenis):** Retourneert true bij het succesvol verzenden van gegevens naar een formuliergegevensmodel.
* **Fout in Submission(event):**  Retourneert true als gegevens niet naar een formuliergegevensmodel zijn verzonden.

## Beschikbare regeltypen in regeleditor {#available-rule-types-in-rule-editor}

De regelredacteur verstrekt een reeks vooraf bepaalde regeltypes die u kunt gebruiken om regels te schrijven. Laten we elk regeltype in detail bekijken. Voor meer informatie over het schrijven van regels in regelredacteur, zie [Schrijfregels](rule-editor.md#p-write-rules-p).

### [!UICONTROL When] {#whenruletype}

Het **[!UICONTROL When]** type regel volgt de constructie van de **voorwaarde-actie-alternatieve handelingsregel** , of soms alleen de **voorwaarde-actieconstructie** . In dit regeltype geeft u eerst een evaluatievoorwaarde op, gevolgd door een actie die moet worden geactiveerd als aan de voorwaarde wordt voldaan ( `True`). Tijdens het gebruik van het type Wanneer-regel kunt u meerdere OPERATORen en/of operatoren gebruiken om geneste expressies](#nestedexpressions) te maken[.

Met het type Wanneer-regel kunt u een voorwaarde voor een formulierobject evalueren en handelingen uitvoeren op een of meer objecten.

In eenvoudige woorden, een typische When-regel is als volgt gestructureerd:

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

Handeling 2 op object B;
EN
Handeling 3 voor Object C;

_

Wanneer u een component met meerdere waarden hebt, zoals keuzerondjes of lijst, terwijl het creëren van een regel voor die component, worden de opties automatisch teruggewonnen en ter beschikking gesteld van de regelmaker. U hoeft de optiewaarden niet nogmaals te typen.

Een lijst heeft bijvoorbeeld vier opties: Rood, Blauw, Groen en Geel. Tijdens het maken van de regel worden de opties (keuzerondjes) automatisch opgehaald en als volgt beschikbaar gemaakt voor de maker van de regel:

![Multi-waarde geeft opties weer](assets/multivaluefcdisplaysoptions1.png)

Tijdens het schrijven van een Wanneer-regel kunt u de waarde van handeling wissen activeren. Waarde wissen van handeling wist de waarde van het opgegeven object. Met de instructie &#39;Wissen&#39; als optie kunt u complexe voorwaarden maken met meerdere velden.

![Waarde wissen van](assets/clearvalueof1.png)

**[!UICONTROL Hide]** Verbergt het opgegeven object.

**[!UICONTROL Show]** Hiermee wordt het opgegeven object weergegeven.

**[!UICONTROL Enable]** Hiermee wordt het opgegeven object ingeschakeld.

**[!UICONTROL Disable]** Hiermee wordt het opgegeven object uitgeschakeld.

**[!UICONTROL Invoke service]** Roept de dienst aan die in een model van vormgegevens (FDM) wordt gevormd. Wanneer u de Invoke-service kiest, wordt een veld weergegeven. Bij het tikken van het gebied, toont het alle diensten die in al model van vormgegevens (FDM) op uw worden gevormd [!DNL Experience Manager] -instantie. Als u een FDM-service (Form Data Model) kiest, worden meer velden weergegeven waarin u formulierobjecten kunt toewijzen met invoer- en uitvoerparameters voor de opgegeven service. Zie voorbeeldregel voor het aanroepen van de diensten van het Model van de Gegevens van de Vorm.

Naast de service Formuliergegevensmodel kunt u een directe WSDL-URL opgeven om een webservice aan te roepen. Nochtans, heeft de modeldienst van de Gegevens van het Vorm vele voordelen en de geadviseerde benadering om de dienst aan te halen.

Voor meer informatie over het vormen van de diensten in het model van vormgegevens (FDM), zie [[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md).

**[!UICONTROL Set value of]** Berekent en stelt de waarde van het opgegeven object in. U kunt de objectwaarde instellen op een tekenreeks, de waarde van een ander object, de berekende waarde met wiskundige expressie of functie, de waarde van een eigenschap van een object of de uitvoerwaarde van een geconfigureerde service Formuliergegevensmodel. Wanneer u de optie Webservice kiest, worden alle services weergegeven die in het FDM-model (Form Data Model) zijn geconfigureerd [!DNL Experience Manager] -instantie. Als u een service Formuliergegevensmodel kiest, worden meer velden weergegeven waarin u formulierobjecten kunt toewijzen met invoer- en uitvoerparameters voor de opgegeven service.

Voor meer informatie over het vormen van de diensten in het model van vormgegevens (FDM), zie [[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md).

De **[!UICONTROL Set Property]** Met regeltype kunt u de waarde van een eigenschap van het opgegeven object instellen op basis van een voorwaardenactie. U kunt eigenschap instellen op een van de volgende opties:
* visible (Boolean)
* dorExclusion (Boolean)
* chartType (String)
* title (String)
* enabled (Boolean)
* mandatory (Boolean)
* validationsDisabled (Boolean)
* validateExpMessage (String)
* value (Number, String, Date)
* items (lijst)
* valid (Boolean)
* errorMessage (String)

Zo kunt u bijvoorbeeld regels definiëren om selectievakjes dynamisch toe te voegen aan het adaptieve formulier. U kunt een regel definiëren met behulp van een aangepaste functie, een formulierobject of een objecteigenschap.

![Eigenschap instellen](assets/set_property_rule_new1.png)

Als u een regel wilt definiëren op basis van een aangepaste functie, selecteert u **[!UICONTROL Function Output]** in de vervolgkeuzelijst en een aangepaste functie slepen en neerzetten vanuit de **[!UICONTROL Functions]** tab. Als aan de voorwaarde wordt voldaan, wordt het aantal selectievakjes dat in de aangepaste functie is gedefinieerd, toegevoegd aan het adaptieve formulier.

Als u een regel wilt definiëren op basis van een formulierobject, selecteert u **[!UICONTROL Form Object]** in de vervolgkeuzelijst en een formulierobject slepen en neerzetten vanuit de **[!UICONTROL Form Objects]** tab. Als aan de voorwaarde is voldaan, wordt het aantal selectievakjes dat in het formulierobject is gedefinieerd, toegevoegd aan het adaptieve formulier.

Met de regel Eigenschap instellen die is gebaseerd op een objecteigenschap kunt u het aantal selectievakjes toevoegen in een adaptief formulier. Dit is gebaseerd op een andere objecteigenschap die is opgenomen in het adaptieve formulier.

In de volgende afbeelding ziet u een voorbeeld van het dynamisch toevoegen van selectievakjes op basis van het aantal vervolgkeuzelijsten in het adaptieve formulier:

![Objecteigenschap](assets/object_property_set_property_new1.png)

**[!UICONTROL Clear Value Of]** Wist de waarde van het opgegeven object.

**[!UICONTROL Set Focus]** Hiermee wordt de focus op het opgegeven object ingesteld.

**[!UICONTROL Save Form]** Hiermee slaat u het formulier op.

**[!UICONTROL Submit Forms]** Hiermee verzendt u het formulier.

**[!UICONTROL Reset Form]** Hiermee herstelt u het formulier.

**[!UICONTROL Validate Form]** Hiermee valideert u het formulier.

**[!UICONTROL Add Instance]** Hiermee wordt een instantie van het opgegeven herhaalbare deelvenster of de opgegeven tabelrij toegevoegd.

**[!UICONTROL Remove Instance]** Hiermee wordt een instantie van het opgegeven herhaalbare deelvenster of de opgegeven tabelrij verwijderd.

**[!UICONTROL Navigate to]** Navigeert naar andere <!--Interactive Communications,--> Adaptieve Forms, andere elementen, zoals afbeeldingen of documentfragmenten, of een externe URL. <!-- For more information, see [Add button to the Interactive Communication](create-interactive-communication.md#addbuttontothewebchannel). -->

### [!UICONTROL Set Value of] {#set-value-of}

De **[!UICONTROL Set Value of]** met regeltype kunt u de waarde van een formulierobject instellen, afhankelijk van het feit of aan de opgegeven voorwaarde wordt voldaan of niet. De waarde kan worden ingesteld op een waarde van een ander object, een letterlijke tekenreeks, een waarde die is afgeleid van een wiskundige expressie of een functie, een waarde van een eigenschap van een ander object of de uitvoer van een service Form Data Model. Op dezelfde manier kunt u controleren op een voorwaarde voor een component, een tekenreeks, een eigenschap of waarden die zijn afgeleid van een functie of wiskundige expressie.

De **Waarde instellen van** Regeltype is niet beschikbaar voor alle formulierobjecten, zoals deelvensters en werkbalkknoppen. Een standaardsetwaarde van regel heeft de volgende structuur:

Waarde van Object A instellen op:

(tekenreeks ABC) OF
(objecteigenschap X van Object C) OF
(waarde van een functie) OF
(waarde van een wiskundige uitdrukking) OF
(uitvoerwaarde van een datamodelservice of webservice);

Wanneer (optioneel):

(Voorwaarde 1 EN Voorwaarde 2 EN Voorwaarde 3) is TRUE;

In het volgende voorbeeld wordt de waarde in `dependentid` het veld als invoer gebruikt en wordt de waarde van het `Relation` veld ingesteld op de uitvoer van het `Relation` argument van de `getDependent` service Form Data Model.

![Webservice instellen](assets/set-value-web-service1.png)

Voorbeeld van waardenregel instellen met de service Formuliergegevensmodel

>[!NOTE]
>
>Bovendien kunt u de Vastgestelde Waarde van regel gebruiken om alle waarden in een drop-down lijstcomponent van de output van de modeldienst van de Gegevens van het Vorm of een Webdienst te bevolken. Zorg er echter voor dat het uitvoerargument dat u kiest van een arraytype is. Alle waarden die in een array worden geretourneerd, worden beschikbaar in de opgegeven vervolgkeuzelijst.

### [!UICONTROL Show] {#show}

Met de **[!UICONTROL Show]** regeltype, kunt u een regel schrijven om een formulierobject weer te geven of te verbergen op basis van het feit of aan een voorwaarde is voldaan of niet. Het regeltype Tonen activeert ook de handeling Verbergen als de voorwaarde niet wordt vervuld of wordt geretourneerd `False`.

Een typische Show regel is gestructureerd als volgt:

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

### [!UICONTROL Hide] {#hide}

Net als het regeltype Tonen kunt u de opdracht **[!UICONTROL Hide]** regeltype om een formulierobject weer te geven of te verbergen op basis van het feit of aan een voorwaarde is voldaan of niet. Het regeltype Verbergen activeert ook de handeling Tonen als de voorwaarde niet wordt vervuld of wordt geretourneerd `False`.

Een typische regel van de Huid is gestructureerd als volgt:

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

### [!UICONTROL Enable] {#enable}

De **[!UICONTROL Enable]** met regeltype kunt u een formulierobject in- of uitschakelen op basis van het feit of aan een voorwaarde wordt voldaan of niet. Het Enable regeltype activeert ook de Disable-actie voor het geval dat de voorwaarde niet wordt vervuld of wordt geretourneerd `False`.

Een typisch laat regel toe is gestructureerd als volgt:

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

### [!UICONTROL Disable] {#disable}

Gelijkaardig aan het Enable regeltype, **[!UICONTROL Disable]** met regeltype kunt u een formulierobject in- of uitschakelen op basis van het feit of aan een voorwaarde wordt voldaan of niet. Het regeltype Uitschakelen activeert ook de handeling Enable voor het geval dat de voorwaarde niet wordt vervuld of wordt geretourneerd `False`.

Een typisch onbruikbaar maken regel is gestructureerd als volgt:

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### [!UICONTROL Validate] {#validate}

De **[!UICONTROL Validate]** regeltype valideert de waarde in een veld met een expressie. U kunt bijvoorbeeld een expressie schrijven om te controleren of het tekstvak voor het opgeven van de naam geen speciale tekens of getallen bevat.

Een typisch Validate regel is gestructureerd als volgt:

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Als de opgegeven waarde niet voldoet aan de regel Valideren, kunt u een validatiebericht voor de gebruiker weergeven. U kunt het bericht opgeven in het dialoogvenster **[!UICONTROL Script validation message]** in de componenteigenschappen in de zijbalk.

![Scriptvalidatie](assets/script-validation.png)

### [!UICONTROL Set Options Of] {#setoptionsof}

De **[!UICONTROL Set Options Of]** met regeltype kunt u regels definiëren om selectievakjes dynamisch toe te voegen aan het adaptieve formulier. U kunt de regel definiëren met behulp van een Form Data Model (FDM) of een aangepaste functie.

Als u een regel wilt definiëren op basis van een aangepaste functie, selecteert u **[!UICONTROL Function Output]** in de vervolgkeuzelijst en een aangepaste functie slepen en neerzetten vanuit de **[!UICONTROL Functions]** tab. Het aantal selectievakjes dat is gedefinieerd in de aangepaste functie, wordt toegevoegd aan het adaptieve formulier.

![Aangepaste functies](assets/custom_functions_set_options_new.png)

Ga voor het maken van een aangepaste functie naar [aangepaste functies in regeleditor](#custom-functions).

Een regel definiëren op basis van een FDM (Form Data Model):

1. Selecteren **[!UICONTROL Service Output]** in de vervolgkeuzelijst.
1. Selecteer het gegevensmodelobject.
1. Selecteer een objecteigenschap voor een gegevensmodel in het menu **[!UICONTROL Display Value]** vervolgkeuzelijst. Het aantal selectievakjes in het adaptieve formulier wordt afgeleid van het aantal instanties dat voor die eigenschap is gedefinieerd in de database.
1. Selecteer een objecteigenschap voor een gegevensmodel in het menu **[!UICONTROL Save Value]** vervolgkeuzelijst.

![FDM-setopties](assets/fdm_set_options_new.png)

## Het begrip van de regel redacteur gebruikersinterface {#understanding-the-rule-editor-user-interface}

De redacteur van de regel verstrekt een uitvoerige maar eenvoudige gebruikersinterface om regels te schrijven en te beheren. U kunt de gebruikersinterface van de regeleditor starten vanuit een adaptief formulier in de ontwerpmodus.

Om het gebruikersinterface van de regelredacteur te lanceren:

1. Open een adaptief formulier in de ontwerpmodus.
1. Selecteer het formulierobject waarvoor u een regel wilt schrijven en selecteer op de werkbalk Component de optie ![bewerkingsregels](assets/edit-rules-icon.svg). De gebruikersinterface van de regeleditor wordt weergegeven.

   ![regels creëren](assets/create-rules1.png)

   Eventuele bestaande regels voor de geselecteerde formulierobjecten worden in deze weergave weergegeven. Voor informatie over het beheren van bestaande regels raadpleegt u [Regels beheren](rule-editor.md#p-manage-rules-p).

1. Selecteren **[!UICONTROL Create]** om een nieuwe regel te schrijven. De visuele redacteur van het gebruikersinterface van de regelredacteur opent door gebrek wanneer u de regelredacteur de eerste keer lanceert.

   ![Gebruikersinterface van regeleditor](assets/rule-editor-ui1.png)

Laten wij elke component van de regelredacteur UI in detail bekijken.

### A. Component-rule display {#a-component-rule-display}

Hiermee geeft u de titel weer van het object Adaptief formulier waarmee u de regeleditor hebt gestart en het regeltype dat momenteel is geselecteerd. In het bovenstaande voorbeeld wordt de regeleditor gestart vanuit een adaptief formulierobject met de naam Salary en is het geselecteerde regeltype When.

### B. Formulierobjecten en -functies {#b-form-objects-and-functions-br}

De ruit op de linkerzijde in het gebruikersinterface van de regelredacteur omvat twee lusjes — **[!UICONTROL Forms Objects]** en **[!UICONTROL Functions]**.

Op het tabblad Formulierobjecten ziet u een hiërarchische weergave van alle objecten in het adaptieve formulier. De titel en het type van de objecten worden weergegeven. Bij het schrijven van een regel kunt u formulierobjecten naar de regeleditor slepen. Wanneer u een regel maakt of bewerkt en een object of functie naar een tijdelijke aanduiding sleept, neemt de tijdelijke aanduiding automatisch het juiste waardetype.

De formulierobjecten waarop een of meer geldige regels zijn toegepast, worden gemarkeerd met een groene stip. Als een van de regels die op een formulierobject zijn toegepast ongeldig is, wordt het formulierobject gemarkeerd met een gele stip.

Het tabblad Functies bevat een set ingebouwde functies, zoals som van, min of meer, max van, gemiddelde van, aantal en validerende vorm. U kunt deze functies gebruiken om waarden in herhaalbare deelvensters en tabelrijen te berekenen en deze tijdens het schrijven van regels te gebruiken in instructies voor handelingen en voorwaarden. U kunt echter wel [aangepaste functies](#custom-functions) ook.

![Het tabblad Functies](assets/functions1.png)

>[!NOTE]
>
>U kunt tekstzoekopdrachten uitvoeren op namen en titels van objecten en functies op de tabbladen Objecten en Functies van Forms.

In de linkerstructuur van de formulierobjecten kunt u de formulierobjecten selecteren om de regels weer te geven die op elk object zijn toegepast. U kunt niet alleen door de regels van de verschillende formulierobjecten navigeren, u kunt ook regels kopiëren en plakken tussen de formulierobjecten. Zie voor meer informatie [Regels kopiëren en plakken](rule-editor.md#p-copy-paste-rules-p).

### C. Schakelen tussen formulierobjecten en -functies {#c-form-objects-and-functions-toggle-br}

Met de schakelknop schakelt u, wanneer hierop wordt getikt, de formulierobjecten en het deelvenster met functies in of uit.

### D. Visuele regeleditor {#visual-rule-editor}

De visuele regelredacteur is het gebied op de visuele redacteurswijze van het gebruikersinterface van de regelredacteur waar u regels schrijft. Hiermee kunt u een regeltype selecteren en voorwaarden en handelingen definiëren. Wanneer u voorwaarden en handelingen in een regel definieert, kunt u formulierobjecten en -functies slepen en neerzetten vanuit het deelvenster Formulierobjecten en -functies.

Voor meer informatie over het gebruiken van visuele regelredacteur, zie [Schrijfregels](rule-editor.md#p-write-rules-p).
<!-- 
### E. Visual-code editors switcher {#e-visual-code-editors-switcher}

Users in the forms-power-users group can access code editor. For other users, code editor is not available. If you have the rights, you can switch from visual editor mode to code editor mode of the rule editor, and conversely, using the switcher right above the rule editor. When you launch rule editor the first time, it opens in the visual editor mode. You can write rules in the visual editor mode or switch to the code editor mode to write a rule script. However, note that if you modify a rule or write a rule in code editor, you cannot switch back to the visual editor for that rule unless you clear the code editor.

[!DNL Experience Manager Forms] tracks the rule editor mode you used last to write a rule. When you launch the rule editor next time, it opens in that mode. However, you can also configure a default mode to open the rule editor in the specified mode. To do so:

1. Go to [!DNL Experience Manager] web console at `https://[host]:[port]/system/console/configMgr`.
1. Click to edit **[!UICONTROL Adaptive Form Configuration Service]**.
1. choose **[!UICONTROL Visual Editor]** or **[!UICONTROL Code Editor]** from the **[!UICONTROL Default Mode for Rule Editor]** drop-down

1. Click **[!UICONTROL Save]**.
-->

### E. Gereed en annuleer knoppen {#done-and-cancel-buttons}

De **[!UICONTROL Done]** wordt gebruikt om een regel op te slaan. U kunt een onvolledige regel opslaan. Onvolledig zijn echter ongeldig en worden niet uitgevoerd. Opgeslagen regels voor een formulierobject worden weergegeven wanneer u de regeleditor de volgende keer start vanuit hetzelfde formulierobject. U kunt bestaande regels in die weergave beheren. Zie voor meer informatie [Regels beheren](rule-editor.md#p-manage-rules-p).

De **[!UICONTROL Cancel]** de knoop verwerpt om het even welke veranderingen u aan een regel aanbracht en sluit de regelredacteur.

## Schrijfregels {#write-rules}

U kunt regels schrijven gebruikend de visuele regelredacteur &lt;!>— of de code-editor>. Wanneer u de regelredacteur de eerste keer lanceert, opent het op de visuele redacteurswijze. U kunt op de wijze van de coderedacteur schakelen en regels schrijven. Nochtans, als u schrijft of een regel in coderedacteur wijzigt, kunt u niet op de visuele redacteur voor die regel schakelen tenzij u de coderedacteur ontruimt. Wanneer u de regelredacteur de volgende keer lanceert, opent het op de wijze die u het laatst gebruikte om regel tot stand te brengen.

Laten we eerst bekijken hoe u regels schrijft met een visuele editor.

### Visuele editor gebruiken {#using-visual-editor}

Laten we begrijpen hoe u een regel maakt in een visuele editor met behulp van het volgende voorbeeldformulier.

![Create-rule-example](assets/create-rule-example.png)

In het gedeelte met vereisten voor leningen in het voorbeeldformulier voor het aanvragen van leningen moeten aanvragers hun echtelijke staat, salaris en indien gehuwd, het salaris van hun echtgenoot vermelden. Op basis van de gebruikersinput wordt het bedrag dat voor de lening in aanmerking komt, berekend door de regel en wordt dit weergegeven in het veld Beleenbaarheid van de lening. Pas de volgende regels toe om het scenario uit te voeren:

* Het veld Salaris van de echtgenoot wordt alleen weergegeven wanneer de huwelijksstatus wordt gehuwd.
* De beleenbaarheid van de lening bedraagt 50% van het totale salaris.

Voer de volgende stappen uit om regels te schrijven:

1. Eerst schrijft u de regel om de zichtbaarheid van het veld Sjabloon bij echtgeno(o)t(e) in te stellen op basis van de optie die de gebruiker selecteert voor het keuzerondje Genderstatus.

   Open het aanvraagformulier voor de lening in de ontwerpmodus. Selecteer de **[!UICONTROL Marital Status]** en selecteert u ![bewerkingsregels](assets/edit-rules-icon.svg). Selecteer vervolgens **[!UICONTROL Create]** om de regeleditor te starten.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   Wanneer u de regelredacteur lanceert, wanneer de regel door gebrek wordt geselecteerd. Bovendien wordt het formulierobject (in dit geval de huwelijksstatus) waaruit u de regeleditor hebt gestart, opgegeven in de instructie When.

   U kunt het geselecteerde object niet wijzigen of wijzigen, maar u kunt een ander regeltype selecteren met de vervolgkeuzelijst Regel, zoals hieronder wordt weergegeven. Als u een regel voor een ander object wilt maken, selecteert u Annuleren om de regeleditor af te sluiten en opnieuw te starten vanuit het gewenste formulierobject.

1. Selecteren **[!UICONTROL Select State]** vervolgkeuzelijst en selecteer **[!UICONTROL is equal to]**. De **[!UICONTROL Enter a String]** wordt weergegeven.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   In het keuzerondje Burgerlijke staat **[!UICONTROL Married]** en **[!UICONTROL Single]** opties worden toegewezen **0** en **1** respectievelijk. U kunt toegewezen waarden verifiëren op het tabblad Titel van het dialoogvenster Keuzerondje bewerken, zoals hieronder wordt weergegeven.

   ![Waarden voor keuzerondjes in regeleditor](assets/radio-button-values.png)

1. In de **[!UICONTROL Enter a String]** veld in de regel, geef **0**.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   U hebt de voorwaarde gedefinieerd als `When Marital Status is equal to Married`. Definieer vervolgens de actie die moet worden uitgevoerd als deze voorwaarde Waar is.

1. Selecteer in de instructie Vervolgens de optie **[!UICONTROL Show]** van de **[!UICONTROL Select Action]** vervolgkeuzelijst.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. Sleep de **[!UICONTROL Spouse Salary]** veld op het tabblad Formulierobjecten in het dialoogvenster **[!UICONTROL Drop object or select here]** veld. U kunt ook de **[!UICONTROL Drop object or select here]** en selecteer de **[!UICONTROL Spouse Salary]** in het pop-upmenu waarin alle formulierobjecten in het formulier worden vermeld.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   De regel wordt als volgt weergegeven in de regeleditor.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

1. Selecteren **[!UICONTROL Done]** om de regel op te slaan.

1. Herhaal de stappen 1 tot en met 5 om een andere regel te definiëren waarmee het veld Echtloon wordt verborgen als de staat van het huwelijk een enkele regel is. De regel wordt als volgt weergegeven in de regeleditor.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >Alternatief, kunt u één Show regel op het gebied van de Salaris van de Echtgenote, in plaats van twee schrijven wanneer de regels op het gebied van de Burgerlijke Status, om het zelfde gedrag uit te voeren.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. Vervolgens schrijft u een regel om het beleenbare bedrag van de lening te berekenen, dat 50% van het totale salaris is, en geeft u dit weer in het veld Beleenbaarheid van de lening. Om dit resultaat te bereiken, kunt u **[!UICONTROL Set value Of]** regels betreffende het veld voor de toelaatbaarheid van leningen.

   Selecteer in de ontwerpmodus de optie **[!UICONTROL Loan Eligibility]** veld en selecteer ![bewerkingsregels](assets/edit-rules-icon.svg). Selecteer vervolgens **[!UICONTROL Create]** om de regeleditor te starten.

1. Selecteren **[!UICONTROL Set Value Of]** van de regeldrop-down.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. Selecteren **[!UICONTROL Select Option]** en selecteert u **[!UICONTROL Mathematical Expression]**. Er wordt een veld voor het schrijven van wiskundige expressies geopend.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. In het expressieveld:

   * Selecteer of sleep een neerzetbewerking op het tabblad Forms Object **[!UICONTROL Salary]** veld in de eerste **[!UICONTROL Drop object or select here]** veld.

   * Selecteren **[!UICONTROL Plus]** van de **[!UICONTROL Select Operator]** veld.

   * Selecteer of sleep een neerzetbewerking op het tabblad Forms Object **[!UICONTROL Spouse Salary]** veld in het andere **[!UICONTROL Drop object or select here]** veld.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. Selecteer vervolgens in het gemarkeerde gebied rond het expressieveld en selecteer **[!UICONTROL Extend Expression]**.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   Selecteer in het veld Uitgebreide expressie de optie **[!UICONTROL divided by]** van de **[!UICONTROL Select Operator]** veld en **[!UICONTROL Number]** van de **[!UICONTROL Select Option]** veld. Geef vervolgens **[!UICONTROL 2]** in het nummerveld.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >U kunt complexe expressies maken met behulp van componenten, functies, wiskundige expressies en eigenschapwaarden in het veld Optie selecteren.

   Maak vervolgens een voorwaarde die, wanneer True wordt geretourneerd, de expressie uitvoert.

1. Selecteren **[!UICONTROL Add Condition]** om een instructie When toe te voegen.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   In de instructie When:

   * Selecteer of sleep een neerzetbewerking op het tabblad Forms Object **[!UICONTROL Marital Status]** veld in de eerste **[!UICONTROL Drop object or select here]** veld.

   * Selecteren **[!UICONTROL is equal to]** van de **[!UICONTROL Select Operator]** veld.

   * Tekenreeks selecteren in het andere **[!UICONTROL Drop object or select here]** veld en specificeren **[!UICONTROL Married]** in de **[!UICONTROL Enter a String]** veld.

   De regel wordt uiteindelijk als volgt weergegeven in de regeleditor.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

1. Selecteer **[!UICONTROL Done]**. Het bespaart de regel.

1. Herhaal stap 7 tot en met 14 om een andere regel te definiëren om de beleenbaarheid van de lening te berekenen als de burgerlijke stand eenmalig is. De regel wordt als volgt weergegeven in de regeleditor.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>U kunt ook de regel Waarde instellen van gebruiken om de beleenbaarheid van leningen te berekenen in de regel When die u hebt gemaakt om het veld Salaris van de echtgenoot weer te geven en te verbergen. De resulterende gecombineerde regel wanneer de Status van het Samenhang Enige is verschijnt als volgt in de regelredacteur.
>
>Op dezelfde manier kunt u een gecombineerde regel schrijven om de zichtbaarheid van het veld Echtgendag te bepalen en de beleenbaarheid van leningen berekenen wanneer de huwelijksstatus wordt gehuwd.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

<!-- ### Using code editor {#using-code-editor}

Users added to the forms-power-users group can use code editor. The rule editor auto generates the JavaScript code for any rule you create using visual editor. You can switch from visual editor to the code editor to view the generated code. However, if you modify the rule code in the code editor, you cannot switch back to the visual editor. If you prefer writing rules in code editor rather than visual editor, you can write rules afresh in the code editor. The visual-code editors switcher helps you switch between the two modes.

The code editor JavaScript is the expression language of Adaptive Forms. All the expressions are valid JavaScript expressions and use Adaptive Forms scripting model APIs. These expressions return values of certain types. For the complete list of Adaptive Forms classes, events, objects, and public APIs, see [JavaScript Library API reference for Adaptive Forms](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/index.html).

For more information about guidelines to write rules in the code editor, see [Adaptive Form Expressions](adaptive-form-expressions.md).

While writing JavaScript code in the rule editor, the following visual cues help you with the structure and syntax:

* Syntax highlights

* Auto Indentation

* Hints and suggestions for Form objects, functions, and their properties

* Auto completion of form component names and common JavaScript functions

![javascriptruleeditor](assets/javascriptruleeditor.png)
-->

#### Aangepaste functies in regeleditor {#custom-functions}

Naast de functies die buiten de box vallen, zoals *Som van* die onder Uitvoer van Functies worden vermeld, kunt u douanefuncties schrijven die u vaak nodig hebt. Zorg ervoor dat de functie die u schrijft, vergezeld gaat van de `jsdoc` boven.

Begeleidend `jsdoc` is vereist:

* Als u aangepaste configuratie en beschrijving wilt
* Omdat er meerdere manieren zijn om een functie in te declareren `JavaScript,` Met opmerkingen kunt u de functies bijhouden.

De redacteur van de regel steunt de syntaxis van JavaScript ES2015 voor manuscripten en douanefuncties.
Zie voor meer informatie [jsdoc.app](https://jsdoc.app/).

Ondersteund `jsdoc` tags:

* **Persoonlijk**
Syntaxis: `@private`
Een functie van het type private is niet opgenomen als een aangepaste functie.

* **Naam**
Syntaxis: `@name funcName <Function Name>`
Alternatief `,` u kunt gebruiken: `@function funcName <Function Name>` **of** `@func` `funcName <Function Name>`.
  `funcName` is de naam van de functie (geen spaties toegestaan).
  `<Function Name>` is de weergavenaam van de functie.

* **Lid**
Syntaxis: `@memberof namespace`
Koppelt een naamruimte aan de functie.

* **Parameter**
Syntaxis: `@param {type} name <Parameter Description>`
U kunt ook het volgende gebruiken: `@argument` `{type} name <Parameter Description>` **of** `@arg` `{type}` `name <Parameter Description>`.
Geeft parameters weer die door de functie worden gebruikt. Een functie kan meerdere parametertags hebben, één tag voor elke parameter in de volgorde waarin deze voorkomt.
  `{type}` vertegenwoordigt parametertype. Toegestane parametertypen zijn:

   1. string
   1. getal
   1. boolean
   1. bereik

  Bereik verwijst naar velden van een adaptief formulier. Wanneer in een formulier het laden is vertraagd, kunt u `scope` om de velden te openen. U kunt velden openen wanneer de velden worden geladen of als de velden algemeen zijn gemarkeerd.

  Alle parametertypen worden in een van de bovenstaande categorieën ingedeeld. Geen wordt niet ondersteund. Selecteer een van de bovenstaande typen. Typen zijn niet hoofdlettergevoelig. Spaties zijn niet toegestaan in de parameter `name`. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Retourtype**
Syntaxis: `@return {type}`
U kunt ook `@returns {type}`.
Voegt informatie over de functie toe, zoals zijn doel.
{type} vertegenwoordigt het terugkeertype van de functie. Toegestane retourtypen zijn:

   1. string
   1. getal
   1. boolean

  Alle andere retourneringstypen worden in een van de bovenstaande categorieën ingedeeld. Geen wordt niet ondersteund. Selecteer een van de bovenstaande typen. De types van terugkeer zijn niet case-sensitive.

   * **Dit**
Syntaxis: `@this currentComponent`

  Gebruik @this om te verwijzen naar de component Adaptief formulier waarop de regel is geschreven.

  Het volgende voorbeeld is gebaseerd op de veldwaarde. In het volgende voorbeeld verbergt de regel een veld in het formulier. De `this` deel van `this.value` verwijst naar de onderliggende component Adaptief formulier waarop de regel is geschreven.

  ```
     /**
     * @function myTestFunction
     * @this currentComponent
     * @param {scope} scope in which code inside function is run.
     */
     myTestFunction = function (scope) {
        if(this.value == "O"){
              scope.age.visible = true;
        } else {
           scope.age.visible = false;
        }
     }
  ```

  >[!NOTE]
  >
  >Opmerkingen vóór aangepaste functie worden gebruikt voor overzicht. Samenvatting kan tot veelvoudige lijnen worden uitgebreid tot een markering wordt ontmoet. Beperk de grootte tot één voor een beknopte beschrijving in de regelbouwer.

**Een aangepaste functie toevoegen**

U wilt bijvoorbeeld een aangepaste functie toevoegen die het gebied van een vierkant berekent. De zijlengte is de gebruikersinvoer naar de aangepaste functie, die wordt geaccepteerd met een numeriek vak in het formulier. De berekende uitvoer wordt weergegeven in een ander numeriek vak in het formulier. Als u een aangepaste functie wilt toevoegen, moet u eerst een clientbibliotheek maken en deze vervolgens toevoegen aan de CRX-opslagplaats.

Voer de volgende stappen uit om een clientbibliotheek te maken en deze toe te voegen in de CRX-opslagplaats:

1. Maak een clientbibliotheek. Zie voor meer informatie [Client-Side bibliotheken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).
1. In CRXDE, voeg een bezit toe `categories`met tekenreekstype als waarde `customfunction` aan de `clientlib` map.

   >[!NOTE]
   >
   >`customfunction`is een voorbeeldcategorie. U kunt elke naam kiezen voor de categorie die u maakt in het dialoogvenster `clientlib`map.

Nadat u de clientbibliotheek in de CRX-opslagplaats hebt toegevoegd, gebruikt u deze in uw adaptieve formulier. Hiermee kunt u uw aangepaste functie als regel in uw formulier gebruiken. Voer de volgende stappen uit om de clientbibliotheek toe te voegen aan uw adaptieve formulier:

1. Open het formulier in de bewerkingsmodus.
Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Open]**.
1. Selecteer in de bewerkingsmodus een component en selecteer vervolgens ![op veldniveau](assets/select_parent_icon.svg) > **[!UICONTROL Adaptive Form Container]** en selecteer vervolgens ![cmppr](assets/configure-icon.svg).
1. Voeg in het zijpaneel, onder Naam van clientbibliotheek, uw clientbibliotheek toe. ( `customfunction` in het voorbeeld.)

   ![De aangepaste clientbibliotheek van de functie toevoegen](assets/clientlib.png)

1. Selecteer het invoervak en selecteer ![bewerkingsregels](assets/edit-rules-icon.svg) om de regeleditor te openen.
1. Selecteer **[!UICONTROL Create Rule]**. Maak met de opties hieronder een regel om de kwadratwaarde van de invoer op te slaan in het veld Uitvoer van het formulier.

   [![Aangepaste functies gebruiken om een regel te maken](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)

1. Selecteer **[!UICONTROL Done]**. Uw aangepaste functie wordt toegevoegd.

   >[!NOTE]
   >
   > Om een model van vormgegevens (FDM) van regelredacteur aan te halen gebruikend douanefuncties, [hier zien](/help/forms/using-form-data-model.md#invoke-services-in-adaptive-forms-using-rules-invoke-services).

#### Ondersteunde typen functiedeclaratie {#function-declaration-supported-types}

**Functie, instructie**

```javascript
function area(len) {
    return len*len;
}
```

Deze functie is opgenomen zonder `jsdoc` opmerkingen.

**Functie-expressie**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Functie-expressie en -instructie**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Functiedeclaratie als variabele**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Beperking: een aangepaste functie kiest alleen de eerste functiedeclaratie uit de lijst met variabelen, indien bijeengevoegd. U kunt functie-expressie gebruiken voor elke gedeclareerde functie.

**Functiedeclaratie als object**

```javascript
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```

>[!NOTE]
>
>Zorg ervoor dat u `jsdoc` voor elke aangepaste functie. Hoewel `jsdoc`opmerkingen worden aangemoedigd, inclusief lege `jsdoc`om uw functie als aangepaste functie te markeren. Het laat standaardbehandeling van uw douanefunctie toe.

## Regels beheren {#manage-rules}

Eventuele bestaande regels voor een formulierobject worden weergegeven wanneer u het object selecteert en ![edit-rules1](assets/edit-rules-icon.svg). U kunt de titel en een voorvertoning van het regeloverzicht weergeven. Voorts laat UI u de volledige regelsamenvatting uitbreiden en bekijken, de orde van regels veranderen, regels uitgeven, en regels schrappen.

![Lijstregels](assets/list-rules.png)

U kunt de volgende handelingen op regels uitvoeren:

* **Uitvouwen/samenvouwen**: De kolom Inhoud in de lijst met regels geeft de inhoud van de regel weer. Als de volledige regelinhoud niet zichtbaar is in de standaardweergave, selecteert u ![expandRule-content](assets/Smock_ChevronDown.svg) om het uit te breiden.

* **Opnieuw**: Nieuwe regels die u maakt, worden onder aan de lijst met regels gestapeld. De regels worden van boven naar beneden uitgevoerd. De regel bij de bovenkant voert eerst gevolgd door andere regels van het zelfde type uit. Bijvoorbeeld, als u hebt wanneer, tonen, toelaten, en wanneer de regels bij eerste, tweede, derde, en vierde posities van bovenkant, respectievelijk, wanneer de regel bij de bovenkant eerst wordt uitgevoerd gevolgd door wanneer de regel bij de vierde positie. Vervolgens worden de regels Tonen en Inschakelen uitgevoerd.
U kunt de volgorde van een regel wijzigen door te tikken ![sorteerregels](assets/sort-rules.svg) of sleep het naar de gewenste volgorde in de lijst.

* **Bewerken**: Als u een regel wilt bewerken, schakelt u het selectievakje naast de regeltitel in. Er worden opties weergegeven voor het bewerken en verwijderen van de regel. Selecteren **[!UICONTROL Edit]** om de geselecteerde regel in de regeleditor te openen <!-- in visual  or code editor mode depending on the mode used to create the rule -->.

* **Verwijderen**: Als u een regel wilt verwijderen, selecteert u de regel en selecteert u **[!UICONTROL Delete]**.

* **In-/uitschakelen**: Wanneer u het gebruik van een regel tijdelijk moet onderbreken, kunt u een of meer regels selecteren en **[!UICONTROL Disable]** in de werkbalk Handelingen om deze uit te schakelen. Als een regel is uitgeschakeld, wordt deze niet uitgevoerd tijdens de runtime. Als u een uitgeschakelde regel wilt inschakelen, selecteert u deze en selecteert u Inschakelen op de werkbalk Handelingen. De statuskolom van de regel geeft aan of de regel is ingeschakeld of uitgeschakeld.

![Regel uitschakelen](assets/disablerule.png)

## Regels kopiëren en plakken {#copy-paste-rules}

U kunt een regel kopiëren-kleven van één gebied aan andere gelijkaardige gebieden om tijd te besparen.

Ga als volgt te werk om regels te kopiëren en te plakken:

1. Selecteer het formulierobject waaruit u een regel wilt kopiëren en selecteer op de werkbalk van het onderdeel ![regel bewerken](assets/edit-rules-icon.svg). De gebruikersinterface van de regeleditor wordt weergegeven terwijl het formulierobject is geselecteerd en de bestaande regels worden weergegeven.

   ![kopieerregel](assets/copyrule.png)

   Voor informatie over het beheren van bestaande regels raadpleegt u [Regels beheren](rule-editor.md#p-manage-rules-p).

1. Schakel het selectievakje naast de titel van de regel in. Er worden opties voor het beheer van de regel weergegeven. Selecteren **[!UICONTROL Copy]**.

   ![copyrule2](assets/copyrule2.png)

1. Selecteer een ander formulierobject waarop u de regel wilt plakken en selecteer **[!UICONTROL Paste]**. Bovendien kunt u de regel bewerken om er wijzigingen in aan te brengen.

   >[!NOTE]
   >
   >U kunt een regel alleen in een ander formulierobject plakken als dat formulierobject de gebeurtenis van de gekopieerde regel ondersteunt. Een knop ondersteunt bijvoorbeeld de gebeurtenis click. U kunt een regel met een klikgebeurtenis aan een knoop maar niet aan een controledoos kleven.

1. Selecteren **[!UICONTROL Done]** om de regel op te slaan.

## Geneste expressies {#nestedexpressions}

De redacteur van de regel laat u veelvoudige EN en OF exploitanten gebruiken om genestelde regels tot stand te brengen. U kunt veelvoudige EN en OF exploitanten in regels mengen.

Hieronder ziet u een voorbeeld van een geneste regel die een bericht weergeeft aan de gebruiker dat hij of zij in aanmerking komt voor de voogdij van een kind als aan de vereiste voorwaarden is voldaan.

![Complexe expressie](assets/complexexpression.png)

U kunt ook voorwaarden slepen en neerzetten in een regel om deze te bewerken. Selecteren en boven de greep plaatsen ( ![handgreep](assets/drag-handle.svg)) vóór een voorwaarde. Zodra de aanwijzer verandert in het handsymbool zoals hieronder wordt weergegeven, sleept u de voorwaarde en zet u deze neer op een willekeurige plaats binnen de lijn. De regelstructuur verandert.

![Slepen en neerzetten](assets/drag-and-drop.png)

## Datumexpressievoorwaarden {#dateexpression}

De redacteur van de regel laat u datumvergelijkingen gebruiken om voorwaarden tot stand te brengen.

Na is een voorbeeldvoorwaarde die een statisch tekstvoorwerp toont als de hypotheek op het huis reeds wordt genomen, dat de gebruiker door het datumgebied te vullen aangeeft.

Wanneer de hypotheekdatum van het onroerend goed, zoals door de gebruiker ingevuld, in het verleden ligt, geeft het Adaptief formulier een toelichting op de berekening van het inkomen. In de volgende regel wordt de datum die door de gebruiker is ingevuld, vergeleken met de huidige datum en als de datum die door de gebruiker is ingevuld eerder is dan de huidige datum, wordt in het formulier het tekstbericht (Income genoemd) weergegeven.

![Toestand datumexpressie](assets/dateexpressioncondition.png)

Wanneer de datum waarop deze is ingevuld, eerder is dan de huidige datum, wordt het tekstbericht (Inkomsten) als volgt weergegeven:

![Voldoet aan voorwaarde voor datumexpressie](assets/dateexpressionconditionmet.png)

## Aantal vergelijkingsvoorwaarden {#number-comparison-conditions}

De redacteur van de regel laat u voorwaarden tot stand brengen die twee aantallen vergelijken.

Na is een voorbeeldvoorwaarde die een statisch tekstvoorwerp toont als het aantal maanden een aanvrager op huidige adres minder dan 36 blijft.

![Vergelijkingsvoorwaarde voor nummers](assets/numbercomparisoncondition.png)

Wanneer de gebruiker aangeeft minder dan 36 maanden op het huidige woonadres te wonen, wordt in het formulier gemeld dat meer bewijs van verblijf kan worden aangevraagd.

![Meer bewijs aangevraagd](assets/additionalproofrequested.png)

<!-- ## Impact of rule editor on existing scripts {#impact-of-rule-editor-on-existing-scripts}

In [!DNL Experience Manager Forms] versions prior to [!DNL Experience Manager 6.1 Forms] feature pack 1, form authors and developers used to write expressions in the Scripts tab of the Edit component dialog to add dynamic behavior to Adaptive Forms. The Scripts tab is now replaced by the rule editor.

Any scripts or expressions that you must have written in the Scripts tab are available in the rule editor. While you cannot view or edit them in visual editor, if you are a part of the forms-power-users group you can edit scripts in code editor. -->

## Voorbeelden van regels {#example}

### Service Formuliergegevensmodel aanroepen {#invoke}

Een webservice overwegen `GetInterestRates` die het bedrag van de lening, de looptijd en de kredietscore van de aanvrager als input neemt en een leningsprogramma retourneert met inbegrip van het bedrag en de rentevoet van het EMI. U maakt een FDM (Form Data Model) met de webservice als gegevensbron. U voegt gegevensmodelobjecten en een `get` service aan het formuliermodel. De service wordt weergegeven op het tabblad Services van het formuliergegevensmodel (FDM). Maak vervolgens een adaptief formulier dat velden van gegevensmodelobjecten bevat om de gebruikersinvoer voor het bedrag van de lening, de looptijd en de creditscore vast te leggen. Voeg een knop toe die de webservice activeert om plandetails op te halen. De uitvoer wordt ingevuld in de desbetreffende velden.

De volgende regel toont hoe u de Invoke de dienstactie vormt om het voorbeeldscenario te verwezenlijken.

![Example-invoke-services](assets/example-invoke-services.png)

>[!NOTE]
>
>Als de invoer van een arraytype is, zijn de velden die arrays ondersteunen zichtbaar onder de vervolgkeuzelijst Uitvoer.

### Meerdere handelingen triggeren met de regel Wanneer {#triggering-multiple-actions-using-the-when-rule}

In een aanvraagformulier voor een lening wilt u vastleggen of de aanvrager van de lening een bestaande klant is of niet. Op basis van de informatie die de gebruiker opgeeft, moet het veld met de klant-id worden weergegeven of verborgen. Ook, wilt u nadruk op het gebied van identiteitskaart van de klant plaatsen als de gebruiker een bestaande klant is. Het aanvraagformulier voor de lening bestaat uit de volgende onderdelen:

* een keuzerondje, **[!UICONTROL Are you an existing Geometrixx customer?]**, die [!UICONTROL Yes] en [!UICONTROL No] opties. De waarde voor Ja is **0** en Nee is **1**.

* Een tekstveld, **[!UICONTROL Geometrixx customer ID]** om de klant-id op te geven.

Wanneer u wanneer regel op het radioknoop schrijft om dit gedrag uit te voeren, verschijnt de regel als volgt in de visuele regelredacteur.

![When-rule-example](assets/when-rule-example.png)

Regel in de visuele editor

In de voorbeeldregel, is de verklaring in wanneer sectie de voorwaarde is, die wanneer Waar terugkeert, de acties uitvoert die in de Dan sectie worden gespecificeerd.

<!-- The rule appears as follows in the code editor.

![when-rule-example-code](assets/when-rule-example-code.png) 

Rule in the code editor -->

### Een functie-uitvoer in een regel gebruiken {#using-a-function-output-in-a-rule}

In een inkooporderformulier hebt u de volgende tabel waarin gebruikers hun bestellingen invullen. In deze tabel:

* De eerste rij is herhaalbaar, zodat kunnen de gebruikers tot veelvoudige producten opdracht geven en verschillende hoeveelheden specificeren. De elementnaam is `Row1`.
* De titel van de cel in de kolom Product Quantity van de herhaalbare rij is Quantity. De elementnaam voor deze cel is `productquantity`.
* De tweede rij in de tabel is niet-herhaalbaar en de titel van de cel in de kolom Hoeveelheid product in deze rij is Totale hoeveelheid.

![Example-function-table](assets/example-function-table.png)

**A.** Rij1 **B.** Aantal **C.** Totale hoeveelheid

Nu, wilt u gespecificeerde hoeveelheden in de kolom van de Hoeveelheid van het Product voor alle producten toevoegen en de som in de Totale cel van de Hoeveelheid tonen. U kunt deze som bereiken door een Set Waarde van regel op de Totale cel van de Hoeveelheid te schrijven zoals hieronder getoond.

![Example-function-output](assets/example-function-output.png)

Regel in de visuele editor

<!-- he rule appears as follows in the code editor.

![example-function-output-code](assets/example-function-output-code.png)

Rule in the code editor -->

### Een veldwaarde valideren met expressie {#validating-a-field-value-using-expression}

In het inkooporderformulier dat in het vorige voorbeeld wordt beschreven, wilt u de gebruiker beperken om meer dan één hoeveelheid van een product te bestellen waarvan de prijs hoger is dan 10000. Voor deze validatie kunt u een validatieregel schrijven, zoals hieronder wordt weergegeven.

![Voorbeeld-validate](assets/example-validate.png)

Regel in de visuele editor

<!-- The rule appears as follows in the code editor.

![example-validate-code](assets/example-validate-code.png)

Rule in the code editor -->