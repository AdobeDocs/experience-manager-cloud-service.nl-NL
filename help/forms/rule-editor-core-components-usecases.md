---
title: Dit artikel schetst diverse gebruiksgevallen voor een regelredacteur in een Aangepast Vorm dat op kerncomponenten wordt gebaseerd.
description: Het artikel schetst diverse gebruiksgevallen voor een regelredacteur in een Aangepast Vorm dat op kerncomponenten wordt gebaseerd.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 8191e113-f768-4b1e-a191-e3c722f19054
source-git-commit: bcf8f9e5273819eaee09875ec81251fe4330701c
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 0%

---

# Verschillende gevallen van gebruik van de regeleditor

Het artikel verstrekt gedetailleerde voorbeelden van een Redacteur van de Regel voor een Adaptief Vorm die op kerncomponenten wordt gebaseerd, die inzichten in zijn juiste implementatie voor verschillende scenario&#39;s verstrekken. Met de regeleditor kunnen ontwikkelaars de logica voor het beheren van het gedrag van formulieren definiëren en beheren.
Nu, laten wij de verschillende implementaties voor een regelredacteur bespreken.

## Stel focus in op een ander deelvenster wanneer u op een knop klikt als het eerste deelvenster geldig is

<span class="preview"> Dit is een pre-versieeigenschap en toegankelijk door ons [ pre-vrijgavekanaal ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Met de regeleditor kunt u de lay-outs van een deelvenster valideren, zoals Horizontale tabbladen, Verticale tabbladen, Accordeons of Wizard wanneer u op een knop klikt en de focus instelt op een formulierobject in een ander deelvenster. U kunt deze functionaliteit gebruiken om de navigatie en gebruikerservaring van formulieren te verbeteren.

Stel u een toepassingsformulier met meerdere stappen voor met een wizardindeling. U moet het deelvenster `Personal Information` voltooien voordat u naar `Employment Details` gaat. Wanneer u op de knop `Next` klikt, valideert de regeleditor het deelvenster `Personal Information` . Als alle vereiste velden correct zijn ingevuld, verschuift het formulier automatisch de focus naar het deelvenster `Employment Details` . Anders wordt een foutbericht weergegeven waarin gebruikers wordt gevraagd de ontbrekende velden te voltooien.

U kunt een regel maken op de knop `Next` om het eerste deelvenster te valideren:

![ Regel voor Volgende knoop ](/help/forms/assets/next-rule.png){width=50%}

Wanneer u de **Volgende** knoop klikt, wordt het **Persoonlijke paneel van de Informatie** bevestigd. Als de ingevoerde details correct zijn, verschuift de nadruk naar het **paneel van de Veiligheid van de Rekening**; anders, veroorzaakt een foutenmelding u om de ontbrekende details in te vullen.

<!--![Video]()-->

## Navigeren tussen deelvensters met een knop

Met de regeleditor kunt u navigatieknoppen toevoegen aan uw deelvensterlay-outs, zoals Horizontale tabbladen, Verticale tabbladen, Accordeons of Wizard. Deze knoppen verbeteren de gebruikerservaring door de overgangen tussen de verschillende deelvensters in een formulier te vereenvoudigen en de focus naar het geselecteerde deelvenster te verplaatsen.

Stel dat u communiceert met het gedeelte met profielinstellingen van een toepassing waarin navigatie wordt vergemakkelijkt door knoppen in plaats van door tabbladen. Op het ingaan van de profielmontages van het belangrijkste dashboard, ontmoet u een reeks panelen gewijd aan verschillende aspecten van hun profiel: **Persoonlijke Informatie**, **de Veiligheid van de Rekening**, en **Voorkeur van het Bericht**.

Elk deelvenster bevat relevante velden en opties voor het bijwerken van specifieke informatie. Navigatieknoppen, zoals `Next` en `Back` , worden op de voorgrond geplaatst, zodat u tussen deze deelvensters kunt navigeren. Klik `Next` om de gebruiker aan het **paneel van de Veiligheid van de Rekening** te vooruit en `Back` te klikken om aan het **Persoonlijke paneel van de Informatie** terug te keren. Deze navigatiemethode zorgt voor een naadloze overgang tussen secties zonder dat de context verloren gaat, waardoor een vloeiende en intuïtieve gebruikerservaring ontstaat. Het gebruik van navigatieknoppen vereenvoudigt het proces om profielmontages te beheren, die de interactie organiseren en gebruikersvriendelijker maken.

Met de regel `Navigate among the panels` kunt u navigatieregels maken voor knoppen waarmee tussen verschillende deelvensters kan worden geschakeld.  Selecteer het kenmerk `Shift focus to the next item` om de focus naar het volgende deelvenster in de layout te verplaatsen.

![ Volgende paneelregel ](/help/forms/assets/rule-editor-navigate-in-panel-next.png){width=50%}

Wanneer op de knop `Next` wordt geklikt, gaat de focus naar het volgende deelvenster in de layout.

![ navigeer in paneel gebruikend Volgende knoop ](/help/forms/assets/navigate-in-panel.gif)

Op dezelfde manier kunt u een regel maken voor de knop `Previous` om de focus naar het vorige deelvenster te verplaatsen.

![ Vorige paneelregel ](/help/forms/assets/rule-editor-navigate-in-panel-previous.png){width=50%}

## Complexe berekeningen stroomlijnen in herhaalbare deelvensters met functies

De regelredacteur staat u toe om uit-van-de-doos functies zoals Som, Min, Max, en verbind rechtstreeks op gebieden binnen herhaalbare panelen te gebruiken. U kunt ook een waarde in een herhaalbaar deelvensterveld doorgeven aan de functie die numerieke arrays, tekenreeksarrays, Booleaanse arrays enzovoort accepteert. Dit ontgrendelt krachtige automatisering, die u toestaat om complexe bedrijfslogica zonder douanecode uit te voeren.

Stel u een formulier voor met een herhaalbaar deelvenster, waarin elke deelvensterinstantie informatie verzamelt over de gedeclareerde waarde van elementen.

![ Herhaalbare vorm ](/help/forms/assets/ootb-function-support-repeatable-panel-form.png)

Met de functie `Sum` kunt u automatisch de waarde van de totale elementen in alle deelvensters berekenen, zodat handmatige berekeningen overbodig zijn en de kans op fouten kleiner wordt.

![ Steun voor herhaalbare paneelgebieden in functies OOTB ](/help/forms/assets/ootb-function-support-repeatable-panel.png)

Wanneer u een formulier invult en exemplaren toevoegt om de elementwaarden te declareren, berekent de knop `Calculate Asset Value` de totale som van alle gedeclareerde elementwaarden en wordt het resultaat in het totaal weergegeven in `assetvalue` textbox.

![ Steun voor herhaalbare paneelgebieden in functies OOTB ](/help/forms/assets/ootb-function-support-repeatable-panel-form-preview.png)

>[!NOTE]
>
> Als de waarde van het veld van het herhaalbare deelvenster wordt doorgegeven aan een functie die geen array accepteert, wordt de veldwaarde van de laatste instantie van het herhaalbare deelvenster doorgegeven aan de functie.

Dit is slechts één voorbeeld! Onderzoek de beschikbare [ functies ](#b-form-objects-and-functions-br) om werkschema&#39;s te vereenvoudigen en gegevensnauwkeurigheid binnen uw vormen te verbeteren.

## Geneste expressies {#nestedexpressions}

De redacteur van de regel laat u veelvoudige EN en OF exploitanten gebruiken om genestelde regels tot stand te brengen. U kunt veelvoudige EN en OF exploitanten in de regels mengen.

Het volgende is een voorbeeld van een genestelde regel die een bericht aan de gebruiker over geschiktheid voor de bewaarneming van een kind toont wanneer de vereiste voorwaarden worden voldaan.

![ Complexe uitdrukking ](assets/complexexpression.png)

U kunt ook voorwaarden slepen en neerzetten in een regel om deze te bewerken. Selecteer en beweegt over het handvat ( ![ handvat ](assets/drag-handle.svg)) vóór een voorwaarde. Zodra de aanwijzer verandert in het handsymbool zoals hieronder wordt weergegeven, sleept u de voorwaarde en zet u deze neer op een willekeurige plaats binnen de lijn. De regelstructuur verandert.

![ belemmering-en-daling ](assets/drag-and-drop.png)

## Datumexpressievoorwaarden {#dateexpression}

De redacteur van de regel laat u datumvergelijkingen gebruiken om voorwaarden tot stand te brengen.

Het volgende is een voorbeeldvoorwaarde die een statisch tekstvoorwerp toont als de hypotheek op het huis reeds wordt genomen, dat de gebruiker door het datumgebied te vullen aangeeft.

Wanneer de hypotheekdatum van het onroerend goed, zoals door de gebruiker ingevuld, in het verleden ligt, geeft het Adaptief formulier een toelichting op de berekening van het inkomen. In de volgende regel wordt de datum die door de gebruiker is ingevuld, vergeleken met de huidige datum en als de datum die door de gebruiker is ingevuld eerder is dan de huidige datum, wordt in het formulier het tekstbericht (Income genoemd) weergegeven.

![ de uitdrukkingsvoorwaarde van de Datum ](assets/dateexpressioncondition.png)

Wanneer de datum waarop deze is ingevuld, eerder is dan de huidige datum, wordt het tekstbericht (Inkomsten) als volgt weergegeven:

![ Voldoet de uitdrukkingsvoorwaarde van de Datum ](assets/dateexpressionconditionmet.png)

## Aantal vergelijkingsvoorwaarden {#number-comparison-conditions}

De redacteur van de regel laat u voorwaarden tot stand brengen die twee aantallen vergelijken.

Na is een voorbeeldvoorwaarde die een statisch tekstvoorwerp toont als het aantal maanden een aanvrager op huidige adres minder dan 36 blijft.

![ de vergelijkingsvoorwaarde van het Aantal ](assets/numbercomparisoncondition.png)

Wanneer de gebruiker aangeeft minder dan 36 maanden op het huidige woonadres te wonen, wordt in het formulier gemeld dat meer bewijs van verblijf kan worden aangevraagd.

![ Meer gevraagde proef ](assets/additionalproofrequested.png)

<!-- ## Impact of rule editor on existing scripts {#impact-of-rule-editor-on-existing-scripts}

In [!DNL Experience Manager Forms] versions prior to [!DNL Experience Manager 6.1 Forms] feature pack 1, form authors and developers used to write expressions in the Scripts tab of the Edit component dialog to add dynamic behavior to Adaptive Forms. The Scripts tab is now replaced by the rule editor.

Any scripts or expressions that you must have written in the Scripts tab are available in the rule editor. While you cannot view or edit them in visual editor, if you are a part of the forms-power-users group you can edit scripts in code editor. -->

### Service Formuliergegevensmodel aanroepen {#invoke}

Bekijk een webservice `GetInterestRates` die het bedrag van de lening, de looptijd en de creditscore van de aanvrager als input gebruikt en een leningenplan retourneert met daarin het bedrag en de rentevoet van het EMI. U maakt een FDM (Form Data Model) met de webservice als gegevensbron. U voegt gegevensmodelobjecten en een `get` -service toe aan het formuliermodel. De service wordt weergegeven op het tabblad Services van het formuliergegevensmodel (FDM). Maak vervolgens een adaptief formulier dat velden van gegevensmodelobjecten bevat om de gebruikersinvoer voor het bedrag van de lening, de looptijd en de creditscore vast te leggen. Voeg een knop toe die de webservice activeert om plandetails op te halen. De uitvoer wordt ingevuld in de desbetreffende velden.

De volgende regel toont hoe u de Invoke de dienstactie vormt om het voorbeeldscenario te verwezenlijken.

![ voorbeeld-invoke-services ](assets/example-invoke-services.png)

>[!NOTE]
>
>Als de invoer van een arraytype is, zijn de velden die arrays ondersteunen zichtbaar onder de vervolgkeuzelijst Uitvoer.

### Meerdere handelingen triggeren met de regel Wanneer {#triggering-multiple-actions-using-the-when-rule}

In een aanvraagformulier voor een lening wilt u vastleggen of de aanvrager van de lening een bestaande klant is of niet. Op basis van de informatie die de gebruiker verschaft, moet het veld met de klant-id worden weergegeven of verborgen. Ook, wilt u nadruk op het gebied van identiteitskaart van de klant plaatsen als de gebruiker een bestaande klant is. Het aanvraagformulier voor de lening bestaat uit de volgende onderdelen:

* Een keuzerondje, **[!UICONTROL Are you an existing Geometrixx customer?]** , dat opties [!UICONTROL Yes] en [!UICONTROL No] biedt. De waarde voor ja is **0** en Nr is **1**.

* Een tekstveld, **[!UICONTROL Geometrixx customer ID]** , om de klant-id op te geven.

Wanneer u wanneer regel op het radioknoop schrijft om dit gedrag uit te voeren, verschijnt de regel als volgt in de visuele regelredacteur.

![ wanneer-regel-voorbeeld ](assets/when-rule-example.png)

In de voorbeeldregel, is de verklaring in wanneer sectie de voorwaarde is, die wanneer Waar terugkeert, de acties uitvoert die in de Dan sectie worden gespecificeerd.

<!-- The rule appears as follows in the code editor.

![when-rule-example-code](assets/when-rule-example-code.png) 

Rule in the code editor -->

### Een functie-uitvoer in een regel gebruiken {#using-a-function-output-in-a-rule}

In een inkooporderformulier hebt u de volgende tabel waarin gebruikers hun bestellingen invullen. In deze tabel:

* De eerste rij is herhaalbaar, zodat kunnen de gebruikers tot veelvoudige producten opdracht geven en verschillende hoeveelheden specificeren. De elementnaam is `Row1` .
* De titel van de cel in de kolom Product Quantity van de herhaalbare rij is Quantity. De elementnaam voor deze cel is `productquantity` .
* De tweede rij in de tabel is niet-herhaalbaar en de titel van de cel in de kolom Hoeveelheid product in deze rij is Totale hoeveelheid.

![ voorbeeld-functie-lijst ](assets/example-function-table.png)

**A.** Row1 **B.** Hoeveelheid **C.** Totale Hoeveelheid

Nu, wilt u gespecificeerde hoeveelheden in de kolom van de Hoeveelheid van het Product voor alle producten toevoegen en de som in de Totale cel van de Hoeveelheid tonen. U kunt deze som bereiken door een Set Waarde van regel op de Totale cel van de Hoeveelheid te schrijven zoals hieronder getoond.

![ voorbeeld-functie-output ](assets/example-function-output.png)

### Een veldwaarde valideren met expressie {#validating-a-field-value-using-expression}

In het inkooporderformulier dat in het vorige voorbeeld wordt beschreven, wilt u de gebruiker beperken om meer dan één hoeveelheid van een product te bestellen waarvan de prijs meer dan 10000 bedraagt. Voor deze validatie kunt u een validatieregel schrijven, zoals hieronder wordt weergegeven.

![ voorbeeld-validate ](assets/example-validate.png)

## Zie ook

{{see-also-rule-editor}}
