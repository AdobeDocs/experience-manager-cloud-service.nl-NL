---
title: Wat zijn de verschillende operatortypes en de gebeurtenissen beschikbaar in regel redacteur van een adaptieve vorm die op kerncomponenten wordt gebaseerd?
description: De adaptieve Forms-regeleditor ondersteunt verschillende typen operatoren en gebeurtenissen.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: ac85ff04-25dc-4566-a986-90ae374bf383
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2252'
ht-degree: 0%

---

# De types en de gebeurtenissen van de exploitant in regelredacteur van een Adaptief Vorm die op de Componenten van de Kern wordt gebaseerd

In AEM Forms als Cloud bevat de regeleditor verschillende typen operatoren en gebeurtenissen waarmee u eenvoudig complexe voorwaarden en handelingen kunt definiëren en uitvoeren.

De operatortypen die beschikbaar zijn in de regeleditor van een adaptief formulier bieden een robuust kader voor het samenstellen van nauwkeurige voorwaarden. Hiermee kunt u gegevens manipuleren, berekeningen uitvoeren en meerdere voorwaarden op een logische en coherente manier combineren. Of u nu waarden vergelijkt, rekenkundige bewerkingen uitvoert of tekenreeksen manipuleert, deze operatoren zorgen ervoor dat uw regels zowel flexibel als krachtig zijn.

De gebeurtenissen in de regelredacteur dienen als trekkers die uw regels activeren. Zij bepalen de specifieke acties die voorkomen wanneer aan bepaalde voorwaarden wordt voldaan. Door verschillende typen gebeurtenissen te gebruiken, kunt u reacties op een groot aantal scenario&#39;s automatiseren, bijvoorbeeld gebruikersinteractie, geplande tijden, veranderingen in gegevens, en systeemstaten. Met de capaciteit om deze trekkers te specificeren, kunt u dynamische en ontvankelijke regels tot stand brengen die aan uw specifieke vereisten voldoen.

Door de beschikbare exploitanttypes en de gebeurtenissen te begrijpen en te gebruiken, kunt u het volledige potentieel van de regelredacteur ontgrendelen, die u toelaat om efficiënte, en efficiënte regels tot stand te brengen die aan uw unieke behoeften voldoen en algemene systeemfunctionaliteit te verbeteren.

## Beschikbare operatortypen en gebeurtenissen in regeleditor {#available-operator-types-and-events-in-rule-editor}

De regeleditor biedt de volgende logische operatoren en gebeurtenissen waarmee u regels kunt maken.

* **is Gelijk aan** - Controleert als een vormvoorwerp een gespecificeerde waarde aanpast.
* **is niet Gelijk aan** - Controleert als een vormvoorwerp geen gespecificeerde waarde aanpast.
* **begint met** - Controleert als een vormvoorwerp met een gespecificeerd koord begint.
* **eindigt met** - Controleert als een vormvoorwerp met een gespecificeerd koord beëindigt.
* **bevat** - controleert als een vormvoorwerp een gespecificeerd substring omvat.
* **bevat niet** - controleert als een vormvoorwerp geen gespecificeerd substring omvat.
* **is Leeg** - Controleert als een vormvoorwerp leeg is of niet verstrekt.
* **is niet Leeg** - Controleert als een vormvoorwerp aanwezig en niet leeg is.
* **heeft Geselecteerd** - Keert waar terug wanneer een gebruiker een specifieke checkbox, drop-down, of radioknoopoptie selecteert.
* **wordt geïnitialiseerd (gebeurtenis)** - keert waar terug wanneer een vormvoorwerp in browser wordt teruggegeven.
* **wordt Veranderd (gebeurtenis)** - Keert waar terug wanneer een gebruiker de waarde of de selectie van een vormvoorwerp wijzigt.
* **wordt geklikt (gebeurtenis)** - Keert waar terug wanneer een gebruiker een vormvoorwerp, bijvoorbeeld, een knoop klikt. Een gebruiker kan [&#x200B; veelvoudige voorwaarden aan de knoop toevoegen klikt &#x200B;](/help/forms/rule-editor-core-components-usecases.md#set-focus-to-another-panel-on-button-click-if-the-first-panel-is-valid).
* **is Geldig** - Controleert als een vormvoorwerp aan bevestigingscriteria voldoet.
* **is niet Geldig** - Controleert als een vormvoorwerp bevestigingscriteria ontbreekt.


<!--
* **Navigation(event):** Returns true when the user clicks a navigation object. Navigation objects are used to move between panels. 
* **Step Completion(event):** Returns true when a step of a rule completes.
* **Successful Submission(event):** Returns true on successful submission of data to a form data model.
* **Error in Submission(event):**  Returns true on unsuccessful submission of data to a form data model. -->

### Beschikbare regeltypen in regeleditor {#available-rule-types-in-rule-editor}

De regelredacteur verstrekt een reeks vooraf bepaalde regeltypes die u kunt gebruiken om regels te schrijven. Laten we elk regeltype in detail bekijken. Voor meer informatie over het schrijven van regels in de regelredacteur, zie [&#x200B; regels &#x200B;](/help/forms/rule-editor-core-components-user-interface.md#write-rules) schrijven.

#### [!UICONTROL When] {#whenruletype}

Het **[!UICONTROL When]** regeltype volgt de **voorwaarde-actie-afwisselende actie** regelconstructie, of soms, enkel de **voorwaarde-actie** constructie. In dit regeltype geeft u eerst een voorwaarde op voor evaluatie gevolgd door een actie die moet worden geactiveerd als aan de voorwaarde is voldaan ( `True`). Terwijl het gebruiken van wanneer regeltype, kunt u veelvoudige EN en OF exploitanten gebruiken om [&#x200B; genestelde uitdrukkingen &#x200B;](/help/forms/rule-editor-core-components-usecases.md#nested-expressions) tot stand te brengen.

Met het regeltype &#39;Wanneer&#39; kunt u een voorwaarde op een formulierobject evalueren en acties op een of meer objecten uitvoeren.

In duidelijke woorden, typisch wanneer de regel als volgt gestructureerd is:

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

`Action 2 on Object B;`
`AND`
`Action 3 on Object C;`

`Else, do the following:`

`Action 2 on Object C;`

Wanneer u een component met meerdere waarden hebt, zoals keuzerondjes of lijst, terwijl het creëren van een regel voor die component, worden de opties automatisch teruggewonnen en ter beschikking gesteld van de regelmaker. U hoeft de optiewaarden niet nogmaals te typen.

Een lijst heeft bijvoorbeeld vier opties: Rood, Blauw, Groen en Geel. Tijdens het creëren van de regel, worden de opties (radioknopen) automatisch teruggewonnen en ter beschikking gesteld van de regelschepper als volgt:

![&#x200B; de multi opties van waardevertoningen &#x200B;](assets/multivaluefcdisplaysoptions.png)

Tijdens het schrijven van een When-regel kunt u de Clear Value of action activeren. Met Waarde wissen wordt de waarde van het opgegeven object gewist. Met de instructie &#39;Wissen&#39; als optie kunt u complexe voorwaarden maken met meerdere velden. U kunt de instructie Else toevoegen om meer voorwaarden toe te voegen

![&#x200B; Duidelijke waarde van &#x200B;](assets/clearvalueof.png)

>[!NOTE]
>
> Wanneer het regeltype slechts single-level toen-else verklaringen steunt.

##### Meerdere velden toegestaan in [!UICONTROL When] {#allowed-multiple-fields}

In **wanneer** voorwaarde, hebt u de optie om andere gebieden behalve het gebied toe te voegen waarop de regel wordt toegepast.

Met het regeltype Wanneer kunt u bijvoorbeeld een voorwaarde evalueren voor verschillende formulierobjecten en de handeling uitvoeren:

Wanneer:

(Object A Voorwaarde 1)

EN/OF

(Voorwaarde B 2)

Voer vervolgens de volgende handelingen uit:

Actie 1 op object A

_

![&#x200B; Toegestane Meerdere gebieden binnen wanneer &#x200B;](/help/forms/assets/allowed-multiple-field-when.png)

**Overwegingen terwijl het gebruiken van Toegestane Meerdere gebieden in wanneer voorwaardelement**

* Zorg ervoor dat de [&#x200B; kerncomponent aan versie 3.0.14 of recenter &#x200B;](https://github.com/adobe/aem-core-forms-components) wordt geplaatst om deze eigenschap in de regelredacteur te gebruiken.
* Als regels worden toegepast op verschillende velden binnen de voorwaarde Wanneer, wordt de regel geactiveerd, zelfs als slechts een van deze velden wordt gewijzigd.
* U kunt de veelvoudige gebieden in **slechts toevoegen wanneer** voorwaarde voor een **EN** regel. Het is niet mogelijk voor een **OF** regel.

>[!NOTE]
>
> Om veelvoudige voorwaarden toe te voegen die een knoop omvatten klik, zorg ervoor de knoop klikgebeurtenis als eerste voorwaarde wordt geplaatst. `When button is clicked AND text input equals '5'` is bijvoorbeeld geldig, terwijl `When text input equals '5' AND button is clicked` niet wordt ondersteund.

<!--
* It is not possible to add multiple fields in the When condition while applying rules to a button.

##### To enable Allowed Multiple fields in When condition feature

Allowed Multiple fields in When condition feature is disabled by default. To enable this feature, add a custom property at the template policy:

1. Open the corresponding template associated with an Adaptive Form in the template editor.
1. Select the existing policy as **formcontainer-policy**.
1. Navigate to the **[!UICONTROL Structure]**  view and, from the **[!UICONTROL Allowed Components]** list, open the **[!UICONTROL Adaptive Forms Container]** policy.
1. Go to the **[!UICONTROL Custom Properties]** tab and to add a custom property, click **[!UICONTROL Add]**.
1. Specify the **Group Name** of your choice. For example, in our case, we added the group name as **allowedfeature**.
1. Add the **key** and **value** pair as follows:
   * key: fd:changeEventBehaviour
   * value: deps
1. Click **[!UICONTROL Done]**. -->

Als er problemen optreden in de toegestane meerdere velden in de voorwaarde &#39;Wanneer&#39;, volgt u de stappen voor het oplossen van problemen als:

1. Open het formulier in de bewerkingsmodus.
1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![&#x200B; eigenschappen van de Gids &#x200B;](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op Gereed en sla het dialoogvenster opnieuw op.

**[!UICONTROL Hide]** Verbergt het opgegeven object.

**[!UICONTROL Show]** Hiermee wordt het opgegeven object weergegeven.

**[!UICONTROL Enable]** Schakelt het opgegeven object in.

**[!UICONTROL Disable]** Schakelt het opgegeven object uit.

**[!UICONTROL Invoke service]** Roept een dienst aan die in een model van vormgegevens (FDM) wordt gevormd. Wanneer u de Invoke-service kiest, wordt een veld weergegeven. Als op het veld wordt getikt, worden alle services weergegeven die in het gehele formuliergegevensmodel (FDM) zijn geconfigureerd op uw [!DNL Experience Manager] -instantie. Als u een service Formuliergegevensmodel kiest, worden meer velden weergegeven waarin u formulierobjecten kunt toewijzen met invoerparameters voor de opgegeven service. U kunt de uitvoerparameters toewijzen via de optie voor gebeurtenislading voor de opgegeven service. U kunt regels voor de behandeling van succes en mislukkingsreacties van de Invoke de dienstverrichting ook tot stand brengen gebruikend de regelredacteur.

>[!NOTE]
>
> Meer over de Invoke dienst leren, [&#x200B; klik hier &#x200B;](/help/forms/invoke-service-enhancements-rule-editor.md).

Zie de voorbeeldregel voor het aanhalen van de diensten van het Model van de Gegevens van de Vorm (FDM).

Naast de service Formuliergegevensmodel kunt u een directe WSDL-URL opgeven om een webservice aan te roepen. Nochtans, heeft de modeldienst van de Gegevens van het Vorm vele voordelen en de geadviseerde benadering om de dienst aan te halen.

Voor meer informatie over het vormen van de diensten in het model van vormgegevens (FDM), zie {de Integratie van 0} Gegevens [[!DNL Experience Manager Forms] .](data-integration.md)

**[!UICONTROL Set value of]** Berekent en stelt de waarde van het opgegeven object in. U kunt de objectwaarde instellen op een tekenreeks, de waarde van een ander object, de berekende waarde met behulp van een wiskundige expressie of functie, de waarde van een eigenschap van een object of de uitvoerwaarde van een geconfigureerde service Formuliergegevensmodel. Wanneer u de optie Webservice kiest, worden alle services weergegeven die in het gehele FDM-formuliergegevensmodel zijn geconfigureerd op uw [!DNL Experience Manager] -instantie. Als u een service Formuliergegevensmodel kiest, worden meer velden weergegeven waarin u formulierobjecten kunt toewijzen met invoer- en uitvoerparameters voor de opgegeven service.

Voor meer informatie over het vormen van de diensten in het model van vormgegevens (FDM), zie {de Integratie van 0} Gegevens [[!DNL Experience Manager Forms] .](data-integration.md)

Met het regeltype **[!UICONTROL Set Property]** kunt u de waarde van een eigenschap van het opgegeven object instellen op basis van een voorwaardenactie. U kunt de eigenschap instellen op een van de volgende opties:

* visible (Boolean)
* label.value (String)
* label.visible (Boolean)
* description (String)
* enabled (Boolean)
* readOnly (Boolean)
* required (Boolean)
* screenReaderText (String)
* valid (Boolean)
* errorMessage (String)
* default (Number, String, Date)
* enumNames (Koord [])
* chartType (String)

U kunt bijvoorbeeld regels definiëren om het tekstvak weer te geven wanneer op een knop wordt geklikt. U kunt een aangepaste functie, een formulierobject, een objecteigenschap of een service-uitvoer gebruiken om een regel te definiëren.

![&#x200B; plaats Bezit &#x200B;](assets/set_property_rule_new.png)

Als u een regel wilt definiëren die is gebaseerd op een aangepaste functie, selecteert u **[!UICONTROL Function Output]** in de vervolgkeuzelijst en sleept u een aangepaste functie naar het tabblad **[!UICONTROL Functions]** . Als aan de voorwaarde wordt voldaan, wordt het tekstinvoervak weergegeven.

Als u een regel wilt definiëren die is gebaseerd op een formulierobject, selecteert u **[!UICONTROL Form Object]** in de vervolgkeuzelijst en sleept u een formulierobject van het tabblad **[!UICONTROL Form Objects]** . Als aan de voorwaarde is voldaan, wordt het tekstinvoervak weergegeven in het adaptieve formulier.

Met de regel Eigenschap instellen die is gebaseerd op een objecteigenschap kunt u het tekstinvoervak zichtbaar maken in een adaptief formulier op basis van een andere objecteigenschap die is opgenomen in het adaptieve formulier.

De volgende afbeelding toont een voorbeeld van het dynamisch inschakelen van het selectievakje op basis van het verbergen of weergeven van een tekstvak in een adaptieve vorm:

![&#x200B; Bezit van Objecten &#x200B;](assets/object_property_set_property_new.png)

**[!UICONTROL Clear Value Of]** Wist de waarde van het opgegeven object.

**[!UICONTROL Set Focus]** Hiermee wordt de focus op het opgegeven object ingesteld.

**[!UICONTROL Submit Form]** verzendt het formulier.

**[!UICONTROL Reset]** Hiermee wordt het formulier of het opgegeven object opnieuw ingesteld.

**[!UICONTROL Validate]** Valideert het formulier of het opgegeven object.

**[!UICONTROL Add Instance]** Hiermee wordt een instantie van het opgegeven herhaalbare deelvenster of de opgegeven tabelrij toegevoegd.

**[!UICONTROL Remove Instance]** Hiermee verwijdert u een instantie van het opgegeven herhaalbare deelvenster of de opgegeven tabelrij.

**[!UICONTROL Function Output]** Definieert een regel op basis van vooraf gedefinieerde functies of aangepaste functies.

**[!UICONTROL Navigate to]** Navigeer naar andere Adaptieve Forms, andere elementen, zoals afbeeldingen of documentfragmenten, of een externe URL. <!-- For more information, see [Add button to the Interactive Communication](create-interactive-communication.md#addbuttontothewebchannel). -->

**[!UICONTROL Dispatch Event]** Triggert de specifieke acties of gedragingen op basis van vooraf gedefinieerde voorwaarden of gebeurtenissen.

#### [!UICONTROL Set Value of] {#set-value-of}

Met het **[!UICONTROL Set Value of]** -regeltype kunt u de waarde van een formulierobject instellen, afhankelijk van het feit of aan de opgegeven voorwaarde wordt voldaan of niet. De waarde kan worden ingesteld op een waarde van een ander object, een letterlijke tekenreeks, een waarde die is afgeleid van een wiskundige expressie of een functie, een waarde van een eigenschap van een ander object of de uitvoer van een service Form Data Model. Op dezelfde manier kunt u controleren op een voorwaarde voor een component, een tekenreeks, een eigenschap of waarden die zijn afgeleid van een functie of wiskundige expressie.

De **Vastgestelde Waarde van** regeltype is niet beschikbaar voor alle vormvoorwerpen, zoals panelen en toolbarknopen. Een standaardsetwaarde van regel heeft de volgende structuur:

Stel de waarde van Object A in op:

(Tekenreeks ABC) OR
(objecteigenschap X van Object C) OR
(waarde van een functie) OR
(waarde van een wiskundige expressie) OF
(outputwaarde van een dienst van het gegevensmodel);

Indien (optioneel):

(Voorwaarde 1 EN Voorwaarde 2 EN Voorwaarde 3) is WAAR;

In het volgende voorbeeld wordt de waarde `Question2` as `True` geselecteerd en wordt de waarde `Result` ingesteld als `correct` .

![&#x200B; reeks-waarde-web-dienst &#x200B;](assets/set-value-web-service.png)

Voorbeeld van waardeceregel instellen met de service Formuliergegevensmodel.

#### [!UICONTROL Show] {#show}

Met het regeltype **[!UICONTROL Show]** kunt u een regel schrijven om een formulierobject weer te geven of te verbergen op basis van het feit of aan een voorwaarde is voldaan of niet. Het regeltype Tonen activeert ook de handeling Verbergen als de voorwaarde niet wordt vervuld of als `False` wordt geretourneerd.

Een typische Show regel is gestructureerd als volgt:

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

#### [!UICONTROL Hide] {#hide}

Net als bij het regeltype Weergeven kunt u het regeltype **[!UICONTROL Hide]** gebruiken om een formulierobject weer te geven of te verbergen op basis van het feit of aan een voorwaarde is voldaan of niet. Het regeltype Verbergen activeert ook de handeling Tonen voor het geval dat niet aan de voorwaarde wordt voldaan of dat `False` wordt geretourneerd.

Een typische regel van de Huid is gestructureerd als volgt:

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

#### [!UICONTROL Enable] {#enable}

Met het regeltype **[!UICONTROL Enable]** kunt u een formulierobject in- of uitschakelen op basis van het feit of aan een voorwaarde wordt voldaan of niet. Het regeltype Enable activeert ook de handeling Disable voor het geval dat niet aan de voorwaarde wordt voldaan of dat `False` wordt geretourneerd.

Een typisch laat regel toe is gestructureerd als volgt:

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

#### [!UICONTROL Disable] {#disable}

Net als bij het regeltype Enable kunt u met het **[!UICONTROL Disable]** -regeltype een formulierobject in- of uitschakelen op basis van het feit of aan een voorwaarde wordt voldaan of niet. Het regeltype Uitschakelen activeert ook de handeling Inschakelen als de voorwaarde niet wordt vervuld of als `False` wordt geretourneerd.

Een typisch onbruikbaar maken regel is gestructureerd als volgt:

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

#### [!UICONTROL Validate] {#validate}

Het regeltype **[!UICONTROL Validate]** valideert de waarde in een veld met behulp van een expressie. U kunt bijvoorbeeld een expressie schrijven om te controleren of het tekstvak voor het opgeven van een naam geen speciale tekens of getallen bevat.

Een typisch Validate regel is gestructureerd als volgt:

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Als de opgegeven waarde niet voldoet aan de regel Valideren, kunt u een validatiebericht voor de gebruiker weergeven. U kunt het bericht in het veld **[!UICONTROL Script validation message]** opgeven in de componenteigenschappen op de zijbalk.

![&#x200B; manuscript-bevestiging &#x200B;](assets/script-validation.png)

#### [!UICONTROL Navigate among the panels]

Met het regeltype **[!UICONTROL Navigate among the panels]** kunt u de focus verplaatsen tussen verschillende deelvensters in een formulier. U kunt bijvoorbeeld een expressie maken om de focus naar het volgende deelvenster te verplaatsen.

Een typisch **navigeert onder de panelen** regel voor het verschuiven van nadruk naar het volgende paneel is gestructureerd als volgt:

`Navigate among the panels`

`Shift focus to the next item Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

Op dezelfde manier kunt u **navigeren onder de panelen** regel voor het verschuiven van nadruk naar het vorige paneel:

`Navigate among the panels`

`Shift focus to the previous item Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

Voor meer details op hoe te om een regel tot stand te brengen om in een paneel te navigeren, [&#x200B; klik hier &#x200B;](/help/forms/rule-editor-core-components-usecases.md#navigating-between-panels-using-buttons).

#### [!UICONTROL Async Function call]

<span class="preview"> Dit is een pre-versieeigenschap en toegankelijk door ons [&#x200B; pre-vrijgavekanaal &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=nl-NL#new-features). </span>

Met het **[!UICONTROL Async Function call]** -regeltype kunt u asynchrone functies uitvoeren. Het laat u toe om een functievraag in werking te stellen die onafhankelijk van de belangrijkste uitvoeringsdraad werkt, toestaand andere processen blijven lopend zonder het wachten op de asynchrone functie te voltooien.

Een typisch Async de vraagregel van de Functie om asynchrone functie uit te voeren is gestructureerd als volgt:

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Async Function call`

`[Callback Function];`

Voor meer informatie over hoe te om de vraag van de Functie Async in de Visuele Redacteur van de Regel te gebruiken, verwijs naar [&#x200B; Gebruikend asynchrone functievraag in het artikel van de regeleditor &#x200B;](/help/forms/using-async-funct-in-rule-editor.md).

<!--
### [!UICONTROL Set Options Of] {#setoptionsof}

The **[!UICONTROL Set Options Of]** rule type enables you to define rules to add check boxes dynamically to the Adaptive Form. You can use a Form Data Model or a custom function to define the rule.

To define a rule based on a custom function, select **[!UICONTROL Function Output]** from the drop-down list, and drag-and-drop a custom function from the **[!UICONTROL Functions]** tab. The number of checkboxes defined in the custom function are added to the Adaptive Form.

![Custom Functions](assets/custom_functions_set_options_new.png)

To create a custom function, see [custom functions in rule editor](#custom-functions).

To define a rule based on a form data model:

1. Select **[!UICONTROL Service Output]** from the drop-down list.
1. Select the data model object.
1. Select a data model object property from the **[!UICONTROL Display Value]** drop-down list. The number of checkboxes in the Adaptive Form is derived from the number of instances defined for that property in the database.
1. Select a data model object property from the **[!UICONTROL Save Value]** drop-down list.

![FDM set options](assets/fdm_set_options_new.png) -->

## Volgende stap

Laten wij nu diverse [&#x200B; voorbeelden voor een Redacteur van de Regel voor een AanpassingsVorm begrijpen die op de Componenten van de Kern &#x200B;](/help/forms/rule-editor-core-components-usecases.md) wordt gebaseerd.

## Zie ook

{{see-also-rule-editor}}
