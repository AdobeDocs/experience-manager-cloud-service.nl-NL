---
title: Rule Editor voor Dynamic Forms in Universal Editor
description: Maak dynamische, intelligente formulieren met de Rule Editor in de Universal Editor. Voorwaardelijke logica, berekeningen en interactief gedrag toevoegen zonder codering.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '3472'
ht-degree: 0%

---


# Rule Editor voor Dynamic Forms in Universal Editor

De Redacteur van de Regel in Universele Redacteur laat u toe om intelligente, dynamische vormen tot stand te brengen die op gebruikersinput in echt - tijd antwoorden. U kunt statische formulieren transformeren in interactieve ervaringen met voorwaardelijke veldzichtbaarheid, geautomatiseerde berekeningen en complexe bedrijfslogica, zonder code te schrijven.

## Wat leert u?

Aan het einde van deze handleiding zult u:

- Begrijp hoe de regels werken en wanneer om verschillende regeltypes te gebruiken
- De Rule Editor in de Universal Editor inschakelen en openen
- Voorwaardelijke logica maken om formuliervelden dynamisch weer te geven of te verbergen
- Automatische berekeningen en gegevensvalidatie implementeren
- Bouw douanefuncties voor complexe bedrijfsregels
- Beste werkwijzen toepassen voor optimale formulierprestaties

## Waarom de Regeleditor gebruiken?

**zet Statische Forms in Slimme Ervaringen om:**

- **Voorwaardelijke Logica**: Toon relevante gebieden die op gebruikersselecties worden gebaseerd
- **Dynamische Berekeningen**: Verwerk automatisch waarden als gebruikerstype
- **Bevestiging van Gegevens**: Verstrek in real time terugkoppelen en fouten verhinderen
- **Verbeterde UX**: Verminder vormingewikkeldheid en gids gebruikers door logische stromen
- **Geen Vereiste Codering**: Visuele interface toegankelijk voor niet-ontwikkelaars

**Gemeenschappelijke Gevallen van het Gebruik:**

- Formulieren voor belastingberekening met voorwaardelijke aftrek
- Meerdere wizards met vertakkende paden
- Verzekeringsformulieren met tariefberekeningen
- Formulieren onderzoeken met voorwaardelijke vragen
- E-commercevormen met dynamische prijsstelling

## Hoe regels werken

Regels zijn geautomatiseerde instructies die uw formulieren intelligent en responsief maken. Zij geven aan wat er moet gebeuren als aan bepaalde voorwaarden wordt voldaan.

### **Componenten van de Regel**

**Voorwaarde**: Een logische test die aan waar of vals evalueert.

- &quot;Is het inkomen van de gebruiker groter dan $50.000?&quot;
- &quot;Heeft de gebruiker &quot;ja&quot;voor verzekeringsdekking geselecteerd?&quot;
- &quot;Is het formulierveld leeg?&quot;

**Actie**: Het resultaat dat voorkomt wanneer de voorwaarde wordt voldaan aan.

- Formuliervelden tonen of verbergen
- Waarden automatisch berekenen
- Validatieberichten weergeven
- Componenten in- of uitschakelen

### **Logische Patronen van de Regel**

**1. Voorwaarde-actie (toen-dan)**

```
WHEN gross salary > 50000
THEN show "Additional Deduction" field
```

*Best voor:* Voorwaardelijke gebiedszicht, dynamische inhoud

**2. Handeling-Voorwaarde (reeks-als)**

```
SET taxable income = gross salary - deductions
IF deductions are applicable
```

*Best voor:* Berekeningen, gegevenstransformaties

**3. Handeling-voorwaarde-Afwisselend (als-toen-anders)**

```
IF income > 50000
THEN show "High Income" fields
ELSE show "Standard Income" fields
```

*Best voor:* Tak logica, wederzijds uitsluitende opties

### **Echte-Wereld Voorbeeld**

**Scenario**: De berekeningsvorm van de Belasting

- **Voorwaarde**: &quot;Het bruto salaris overschrijdt $50.000&quot;
- **Primaire Actie**: Toon &quot;Extra Vermindering&quot;gebied
- **Afwisselende Actie**: Verberg &quot;Extra Vermindering&quot;gebied
- **Resultaat**: De gebruikers zien slechts relevante gebieden die op hun inkomensniveau worden gebaseerd

## Vereisten

Voordat u begint te werken met de Rule Editor, moet u het volgende doen:

### **Vereisten van de Toegang**

- Authoring toegang tot **AEM as a Cloud Service**
- **Universele Redacteur** met de toegelaten uitbreiding van de Redacteur van de Regel
- Machtigingen voor het bewerken van formulieren in uw AEM-omgeving

### **Technische Vereisten**

- **Basiskennis van het vormontwerp**: Vertrouwelijkheid met vormcomponenten en hun eigenschappen
- **Vertrouwelijkheid van de Bedrijfs logica**: Mogelijkheid om voorwaardelijke vereisten te bepalen
- **Basiskennis van JavaScript** (slechts die voor douanefuncties wordt vereist)

### **laat de Uitbreiding van de Redacteur van de Regel** toe

De uitbreiding van de Redacteur van de Regel wordt niet toegelaten door gebrek in Universele Redacteur. U kunt het van [ Extension Manager ](/help/implementing/developing/extending/extension-manager.md) toelaten.

**na het toelaten van de uitbreiding:**
Het ![ uitgeven-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram verschijnt in de hoger-juiste hoek wanneer u vormcomponenten selecteert.

![ Universele redacteur van de Regel van de Redacteur ](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
*Figuur: Het pictogram van de Redacteur van de Regel verschijnt wanneer u vormcomponenten* selecteert

**om tot de Redacteur van de Regel toegang te hebben:**

1. Selecteer een formuliercomponent in de Universal Editor.
2. Klik het ![ uitgeven-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram dat verschijnt.
3. De interface van de Redacteur van de Regel opent in een nieuw paneel.

![ gebruikersinterface van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor-for-field.png)
*Figuur: De interface van de Redacteur van de Regel voor het uitgeven van componentenregels*

>[!NOTE]
>
> In dit artikel verwijzen &quot;formuliercomponent&quot; en &quot;formulierobject&quot; naar dezelfde elementen (zoals invoervelden, knoppen, deelvensters, enz.).

## Interface van de Redacteur van de regel Overzicht

De Redacteur van de Regel biedt een gebruikersvriendelijke visuele interface voor het creëren van en het beheren van regels aan:

![ het gebruikersinterface van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor-interface.png)
*Cijfer: Volledige interface van de Redacteur van de Regel met genummerde componenten*

### **Componenten van de Interface**

**1. Component Title &amp; Rule Type**

- **doel**: Toont de naam van de geselecteerde component en het huidige regeltype.
- **Voorbeeld**: &quot;Ga Bruto Salaris&quot;(de Input van de Tekst) met de &quot;Wanneer&quot;geselecteerde regel in.
- **Uiteinde**: Bevestig altijd dat u de correcte component uitgeeft.

**2. Het paneel van Objecten en van Functies van de vorm**

- **het Lusje van Objecten van de Vorm**: Verstrekt een hiërarchische mening van alle vormcomponenten.
   - Gebruik voor: Verwijzen naar andere velden in uw regels.
   - Navigatie: uit- of samenvouwen om specifieke componenten te zoeken.
- **het Lusje van Functies**: Bevat ingebouwde wiskundige en logische functies.
   - Wordt gebruikt voor: complexe berekeningen en gegevensbewerkingen uitvoeren.
   - Categorieën: functies Math, String, Date en Validation.

**3. Knop voor schakelen tussen deelvensters**

- **doel**: Toont of verbergt de voorwerpen en functies paneel.
- **Uiteinde**: Knevel van het paneel om de regel te verhogen die werkruimte uitgeeft.
- **kortere weg van het Toetsenbord**: Nuttig wanneer het werken met complexe regels.

**4. Visual Rule Builder**

- **Doel**: Het belangrijkste gebied voor het construeren van regellogica.
- **Eigenschappen**: belemmering-en-dalingsinterface en dropdown selecteurs.
- **Werkschema**: Selecteer regeltype → Bepaal voorwaarden → Vastgestelde acties.

**5. Besturingsknoppen**

- **Gedaan**: Slaat de regel op en sluit de redacteur.
- **annuleert**: De veranderingen van de verwerping en sluit de redacteur zonder sparen.
- **Uiteinde**: Test altijd uw regels alvorens Gedaan te klikken.

### **Beheer van de Regel**

Wanneer u de Redacteur van de Regel voor een component opent die reeds regels heeft:

![ toon de beschikbare regels van vormvoorwerp ](/help/edge/docs/forms/assets/rule-editor15.png)
*Cijfer: Het beheren van bestaande regels voor een vormcomponent*

**Beschikbare Acties:**

- **Mening**: De overzichten van de de regelregel van het overzicht en logica.
- **geef** uit: wijzig bestaande regelvoorwaarden of acties.
- **herordenen**: Verander de uitvoeringsorde van regels (de regels lopen van boven naar onder).
- **toelaten/onbruikbaar maken**: Tijdelijk draai regels voor het testen doeleinden.
- **Schrapping**: Verwijder permanent regels.

>[!TIP]
>
> **de Orde van de Uitvoering van de Regel van de Orde van de Rij**: De regels worden uitgevoerd van boven naar onder. Plaats meer specifieke voorwaarden vóór algemene voorwaarden.

## Beschikbare regeltypen

De Redacteur van de Regel biedt een uitvoerige reeks regeltypes aan die door functionaliteit worden georganiseerd. Selecteer het gewenste type op basis van uw specifieke gebruiksscenario:

### **Voorwaardelijke Logische Regels**

**wanneer**

- **Doel**: Werkt als primaire voorwaardelijke regel voor het uitvoeren van complexe logica.
- **Geval van het Gebruik**: Bijvoorbeeld, &quot;wanneer de gebruiker &quot;Gehuwd&quot;selecteert, de gebieden van de showmuisinformatie toont.&quot;
- **Logische patroon**: Voorwaarde → Actie (met een facultatieve afwisselende actie)

**Verbergen/tonen**

- **Doel**: Het gebiedszicht van controles die op gespecificeerde voorwaarden wordt gebaseerd.
- **geval van het Gebruik**: Verberg irrelevante secties of laat progressieve onthulling toe.
- **Beste praktijken**: Gebruik om een schone, geconcentreerde gebruikerservaring tot stand te brengen.

**toelaten/onbruikbaar maken**

- **Doel**: Controles of een gebied met, kan worden in wisselwerking gestaan gebaseerd op voorwaarden.
- **Geval van het Gebruik**: maak de verzendknoop onbruikbaar tot alle vereiste gebieden worden voltooid.
- **Beste praktijken**: Verstrek duidelijke visuele terugkoppelen aan gebruikers.

### **Regels van de Manipulatie van Gegevens**

**vastgestelde waarde van**

- **Doel**: bevolkt automatisch gebiedswaarden.
- **Geval van het Gebruik**: Plaats de datum van vandaag, bereken totalen, of kopieer waarden tussen gebieden.
- **Beste praktijken**: Gebruik om gebruikersinspanning te verminderen en nauwkeurigheid te verzekeren.

**duidelijke waarde van**

- **Doel**: Verwijdert gegevens uit gebieden wanneer de voorwaarden veranderen.
- **Geval van het Gebruik**: Duidelijke afhankelijke gebieden wanneer een ouderselectie verandert.
- **Beste praktijken**: Handhaaf gegevensintegriteit en verhinder zwevende waarden.

**Formaat**

- **Doel**: Transformeert hoe de waarden worden getoond.
- **geval van het Gebruik**: De munt van het formaat, telefoonaantallen, of data.
- **Beste praktijken**: Verbeter leesbaarheid zonder de onderliggende gegevens te veranderen.

### **Regels van de Bevestiging**

**bevestigt**

- **Doel**: Implementeert de logica van de douanebevestiging.
- **geval van het Gebruik**: Dwingt complexe bedrijfsregels of dwars-gebiedsbevestiging.
- **Beste praktijken**: Verstrek duidelijke en uitvoerbare foutenmeldingen.

### **Regels van de Berekening**

**Wiskundige Uitdrukking**

- **Doel**: Voert geautomatiseerde berekeningen uit.
- **geval van het Gebruik**: De berekeningen van de Belasting, totalen, of percentages.
- **Beste praktijken**: De berekeningen van de update in echt - tijd zoals gebruikerstype.

### **Regels van het Gebruikersinterface**

**plaats Focus**

- **Doel**: Richt gebruikersaandacht op specifieke gebieden.
- **Geval van het Gebruik**: Nadruk op foutengebieden of gids gebruikers door tovenaarsstappen.
- **Beste praktijken**: Gebruik spaarzaam om het verstoren van de gebruikersstroom te vermijden.

**plaats Bezit**

- **doel**: wijzigt dynamisch componenteneigenschappen.
- **Geval van het Gebruik**: De placeholder tekst van de verandering of wijzigt opties in een dropdown.
- **Beste praktijken**: Verbeter de gebruikerservaring met contextafhankelijke veranderingen.

### **Regels van de Controle van de Vorm**

**legt Vorm** voor

- **Doel**: Triggers vorm voorlegging programmatically.
- **geval van het Gebruik**: auto-voorlegt nadat de specifieke voorwaarden worden voldaan aan.
- **Beste praktijken**: Bevestig altijd de vorm vóór voorlegging.

**Vorm van het Terugstellen**

- **Doel**: ontruimt alle vormgegevens en stelt de vorm aan zijn aanvankelijke staat opnieuw in.
- **geval van het Gebruik**: &quot;Begin over&quot;functionaliteit.
- **Beste praktijken**: Bevestig de actie met de gebruiker alvorens terug te stellen.

**sparen Vorm**

- **Doel**: Slaat de vorm als ontwerp voor recentere voltooiing op.
- **geval van het Gebruik**: Nuttig voor lange vormen of multi-zittingswerkschema&#39;s.
- **Beste praktijken**: Verstrek duidelijke terugkoppelen op sparen status.

### **Geavanceerde Regels**

**roept Dienst** aan

- **Doel**: Vraag externe APIs of de diensten.
- **geval van het Gebruik**: De raadpleging van het adres, bevestiging in real time, of gegevensverrijking.
- **Beste praktijken**: Verwerk ladende staten en foutenscenario&#39;s geschikt.

**voeg/verwijder Instantie** toe

- **Doel**: Beheert dynamisch herhaalbare secties.
- **geval van het Gebruik**: Voeg familieleden of veelvoudige adressen toe.
- **Beste praktijken**: Verstrek duidelijke controles voor het toevoegen van of het verwijderen van instanties.

**navigeer aan**

- **Doel**: Richt gebruikers aan andere vormen of pagina&#39;s opnieuw.
- **geval van het Gebruik**: De werkschema&#39;s van de multi-vorm of voorwaardelijk het verpletteren.
- **Beste praktijken**: Behoud vormgegevens vóór navigatie.

**navigeer onder Comités**

- **Doel**: De navigatie van controles in tovenaar-stijl vormen.
- **geval van het Gebruik**: De vormen van de multi-stap of voorwaardelijk stap het overslaan.
- **Beste praktijken**: De duidelijke voortgangsindicatoren van de vertoning.

**de Gebeurtenis van de Verzending**

- **Doel**: De gebeurtenissen van de trekkers van de douanevorm voor geavanceerde integratie.
- **Geval van het Gebruik**: Het volgen van Analytics of derdeintegratie.
- **Beste praktijken**: Gebruik slechts voor niet-blokkerende acties.


## Stapsgewijze zelfstudie: een slimme belastingcalculator maken

Deze sectie verstrekt een praktisch voorbeeld om de mogelijkheden van de Redacteur van de Regel aan te tonen. Het voorbeeld leidt u door het bouwen van een vorm van de belastingberekening die voorwaardelijke logica en geautomatiseerde berekeningen gebruikt.

![ Schermafbeelding van de interface die van de Redacteur van de Regel de verwezenlijking van een voorwaardelijke regel met wanneer-toen logica voor het zicht van het vormgebied toont ](/help/edge/docs/forms/assets/rule-editor-1.png)
*Figuur: De berekeningsvorm van de Belasting met intelligente voorwaardelijke gebieden*

### **Overzicht van het Leerprogramma**

In deze zelfstudie maakt u een formulier dat:

1. **past zich aan gebruikersinput** aan: Vertoningen relevante gebieden die op het inkomensniveau worden gebaseerd.
2. **berekent automatisch**: Berekent belastingverplichting in echt - tijd.
3. **bevestigt gegevens**: Zorgt nauwkeurige berekeningen en gegevensingang.

### **Structuur van de Vorm**

| Veldnaam | Type | Doel | Gedrag |
|------------|------|---------|----------|
| **Bruto Salaris** | Nummerinvoer | De gebruiker gaat jaarlijks inkomen in | Voorwaardelijke logica activeren |
| **Extra Vermindering** | Nummerinvoer | Extra aftrek (indien van toepassing) | Geeft weer wanneer salaris > $50.000 |
| **Belastbaar Inkomen** | Nummerinvoer | Automatisch berekend | Updates voor invoerwijzigingen |
| **Betaalbare Belasting** | Nummerinvoer | Definitief belastingbedrag | Berekent met een snelheid van 10% |

### **BedrijfsLogica om uit te voeren**

**Regel 1: Voorwaardelijke Vertoning van het Gebied**

```
WHEN Gross Salary > 50,000
THEN Show "Additional Deduction" field
ELSE Hide "Additional Deduction" field
```

**Regel 2: De Belastbare Berekening van het Inkomen**

```
SET Taxable Income = Gross Salary - Additional Deduction
(When Additional Deduction is applicable)
```

**Regel 3: De Berekening van de Belasting**

```
SET Tax Payable = Taxable Income × 10%
(Simplified flat rate for demonstration)
```

### **Stappen van de Implementatie**

Voer de volgende stappen uit om uw intelligente belastingformulier te maken:



+++ 1: Maak het basisformulier

**Doelstelling**: Bouw de basisvormstructuur met alle vereiste componenten

Uw formulier voor belastingberekening maken in de Universal Editor:

1. **Open Universele Redacteur**
   - Ga naar uw AEM Sites-console
   - Selecteer de pagina waaraan u het formulier wilt toevoegen
   - Klik **uitgeven** om Universele Redacteur te openen

2. **voeg de Componenten van de Vorm toe**

   Voeg deze componenten in volgorde toe:

   | Component | Type | Label | Instellingen |
   |-----------|------|-------|----------|
   | Titel | Titel | &quot;Formulier voor belastingberekening&quot; | Kop niveau H2 |
   | Nummerinvoer | Nummerinvoer | &quot;Brutosalaris&quot; | Vereist: Ja, tijdelijke aanduiding: &quot;Voer jaarsalaris in&quot; |
   | Nummerinvoer | Nummerinvoer | &quot;Aanvullende aftrek&quot; | Vereist: Nee, tijdelijke aanduiding: &quot;Voer aanvullende aftrekkingen in&quot; |
   | Nummerinvoer | Nummerinvoer | &quot;Belastbaar inkomen&quot; | Vereist: Nee, alleen-lezen: Ja |
   | Nummerinvoer | Nummerinvoer | &quot;Te betalen belasting&quot; | Vereist: Nee, alleen-lezen: Ja |
   | Verzendknop | Verzenden | &quot;BTW berekenen&quot; | Type: verzenden |

3. **vorm Eerste Montages**

   - **verberg het Extra gebied van de Vermindering**:
      - Selecteer de component &quot;Extra aftrek&quot;
      - In het paneel van Eigenschappen, plaats **Zichtbaar** aan **Nr**
      - Dit veld wordt voorwaardelijk weergegeven op basis van regels

   - **maak berekende gebieden read-only**:
      - Selecteer de velden &quot;Belastbaar inkomen&quot; en &quot;Belastbaar inkomen&quot;
      - Plaats **Gelezen slechts** aan **ja** in Eigenschappen

     ![ Schermafbeelding van een vorm van de belastingberekening met inputgebieden voor bruto salaris, huwelijkse status, en afhankelijke kinderen, die de vormstructuur aantonen alvorens de regels worden toegepast ](/help/edge/docs/forms/assets/rule-editor2.png)
     *Cijfer: De aanvankelijke vormstructuur met basisgevormde componenten*

**Controlepunt**: U zou nu een vorm met alle vereiste gebieden moeten hebben, waar de &quot;Extra Vermindering&quot;verborgen is en de berekende gebieden read-only zijn.

+++

+++ &#x200B;2. Een voorwaardelijke regel toevoegen voor een formulierveld

Nadat u het formulier hebt gemaakt, schrijft u de eerste regel om het veld `Additional Deduction` alleen weer te geven als het brutosalaris hoger is dan € 50.000. Een voorwaardelijke regel toevoegen:

1. Open een vorm in Universele Redacteur voor het uitgeven en selecteer het **[!UICONTROL Gross Salary]** gebied in de inhoudsboom en selecteer ![ uitgeven-regels ](/help/forms/assets/edit-rules-icon.svg). U kunt het veld **[!UICONTROL Gross Salary]** ook rechtstreeks in het deelvenster **[!UICONTROL Forms Object]** selecteren.
   ![ de Redacteur example1 van de Regel ](/help/edge/docs/forms/assets/rule-editor3.png)
De visuele interface van de Redacteur van de Regel verschijnt.
1. Klik op **[!UICONTROL Create]** om regels te maken.
   ![ de Redacteur example2 van de Regel ](/help/edge/docs/forms/assets/rule-editor4.png)
Standaard is het regeltype `Set Value Of` geselecteerd. U kunt het geselecteerde object niet wijzigen of wijzigen, maar u kunt de regelvervolgkeuzelijst gebruiken om een ander regeltype te selecteren.\
   ![ de Redacteur example3 van de Regel ](/help/edge/docs/forms/assets/rule-editor5.png)
1. Open de vervolgkeuzelijst met regeltypen en selecteer **[!UICONTROL When]** regeltype.
   ![ voorbeeld4 van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor6.png)
1. Selecteer **[!UICONTROL Select State]** vervolgkeuzelijst en selecteer **[!UICONTROL is greater than]** . Het veld **[!UICONTROL Enter a Number]** wordt weergegeven.
   ![ de Redacteur example5 van de Regel ](/help/edge/docs/forms/assets/rule-editor7.png)
1. Typ `50000` in het **[!UICONTROL Enter a Number]** -veld in de regel.
   ![ de Redacteur example6 van de Regel ](/help/edge/docs/forms/assets/rule-editor8.png)
U hebt de voorwaarde gedefinieerd als `When Gross Salary is greater than 50000` . Definieer vervolgens de actie die moet worden uitgevoerd als deze voorwaarde `True` is.
1. Selecteer `Then` in de vervolgkeuzelijst **[!UICONTROL Show]** in de instructie **[!UICONTROL Select Action]** .
   ![ de Redacteur example7 van de Regel ](/help/edge/docs/forms/assets/rule-editor9.png)
1. Sleep het veld **[!UICONTROL Additional Deduction]** naar het tabblad Formulierobjecten in het veld **[!UICONTROL Drop object or select here]** . U kunt ook het veld **[!UICONTROL Drop object or select here]** selecteren en het veld **[!UICONTROL Additional Deduction]** in het pop-upmenu selecteren, waarin alle formulierobjecten in het formulier worden vermeld.
   ![ de Redacteur example8 van de Regel ](/help/edge/docs/forms/assets/rule-editor10.png)
1. Klik op **[!UICONTROL Add Else Section]** om een andere voorwaarde voor het veld **[!UICONTROL Gross Salary]** toe te voegen, voor het geval u een salaris invoert dat lager is dan `50000` .
   ![ de Redacteur example9 van de Regel ](/help/edge/docs/forms/assets/rule-editor11.png)
1. Selecteer **[!UICONTROL Hide]** in de vervolgkeuzelijst **[!UICONTROL Select Action]** in de instructie `Else` .
   ![ de Redacteur example10 van de Regel ](/help/edge/docs/forms/assets/rule-editor12.png)
1. Sleep het veld **[!UICONTROL Additional Deduction]** naar het tabblad Formulierobjecten in het veld **[!UICONTROL Drop object or select here]** . U kunt ook het veld **[!UICONTROL Drop object or select here]** selecteren en het veld **[!UICONTROL Additional Deduction]** in het pop-upmenu selecteren, waarin alle formulierobjecten in het formulier worden vermeld.
   ![ de Redacteur example11 van de Regel ](/help/edge/docs/forms/assets/rule-editor13.png)
1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.
De regel verschijnt als volgt in de Redacteur van de Regel.
   ![ de Redacteur example12 van de Regel ](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Alternatief, kunt u een Show regel op het Extra gebied van de Aftrek, in plaats van een wanneer regel op het Bruto gebied van de Salaris schrijven, om het zelfde gedrag uit te voeren.

+++

+++ &#x200B;3. Berekeningen toevoegen voor de formuliervelden

Vervolgens schrijft u een regel om de `Taxable Income` te berekenen. Dit is het verschil tussen `Gross Salary` en `Additional Deduction` (indien van toepassing). Voer de volgende stappen uit om een berekeningsregel toe te voegen aan het veld **[!UICONTROL Taxable Income]** :

1. Op auteurswijze, selecteer het **[!UICONTROL Taxable Income]** gebied en selecteer ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit. U kunt het veld **[!UICONTROL Taxable Income]** ook rechtstreeks in het deelvenster **[!UICONTROL Forms Object]** selecteren.
1. Selecteer vervolgens **[!UICONTROL Create]** om de regel te maken.
   ![ de Redacteur example13 van de Regel ](/help/edge/docs/forms/assets/rule-editor16.png)
1. Selecteer **[!UICONTROL Select Option]** en selecteer **[!UICONTROL Mathematical Expression]** . Er wordt een veld voor het schrijven van wiskundige expressies geopend.
   ![ de Redacteur example14 van de Regel ](/help/edge/docs/forms/assets/rule-editor17.png)

1. In het veld Wiskundige expressie:

   - Selecteer of sleep-daling van het lusje van de Objecten van Forms het **[!UICONTROL Gross Salary]** gebied in het eerste **[!UICONTROL Drop object or select here]** gebied.

   - Selecteer **[!UICONTROL Minus]** in het veld **[!UICONTROL Select Operator]** .

   - Selecteer of sleep-daling van het lusje van de Objecten van Forms het **[!UICONTROL Additional Deduction]** gebied in het andere **[!UICONTROL Drop object or select here]** gebied.
     ![ de Redacteur example15 van de Regel ](/help/edge/docs/forms/assets/rule-editor18.png)

1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.

   Voeg nu een regel voor het veld `Tax Payable ` toe, die wordt bepaald door het belastbare inkomen te vermenigvuldigen met het belastingtarief. Veronderstel voor eenvoud een vast belastingtarief van `10%`.

1. Op auteurswijze, selecteer het **[!UICONTROL Tax Payable]** gebied en selecteer ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit. Selecteer vervolgens **[!UICONTROL Create]** om regels te maken.
   ![ de Redacteur example16 van de Regel ](/help/edge/docs/forms/assets/rule-editor19.png)
1. Selecteer **[!UICONTROL Select Option]** en selecteer **[!UICONTROL Mathematical Expression]** . Er wordt een veld voor het schrijven van wiskundige expressies geopend.
   ![ de Redacteur example17 van de Regel ](/help/edge/docs/forms/assets/rule-editor20.png)
1. In het veld Wiskundige expressie:

   - Selecteer of sleep-daling van het lusje van de Objecten van Forms het **[!UICONTROL Taxable Income]** gebied in het eerste **[!UICONTROL Drop object or select here]** gebied.

   - Selecteer **[!UICONTROL Multiplied by]** in het veld **[!UICONTROL Select Operator]** .

   - Selecteer **Aantal** van het **[!UICONTROL Select Option]** gebied en ga de waarde als `10` op het **[!UICONTROL Enter a Number]** gebied in.
     ![ de Redacteur example18 van de Regel ](/help/edge/docs/forms/assets/rule-editor21.png)
1. Selecteer vervolgens in het gemarkeerde gebied rond het expressieveld en selecteer **[!UICONTROL Extend Expression]** .
   ![ de Redacteur example19 van de Regel ](/help/edge/docs/forms/assets/rule-editor22.png)
1. Selecteer in het veld Uitgebreide expressie **[!UICONTROL divided by]** in het **[!UICONTROL Select Operator]** veld en **[!UICONTROL Number]** in het **[!UICONTROL Select Option]** veld. Geef vervolgens `100` op in het nummerveld.
   ![ de Redacteur example20 van de Regel ](/help/edge/docs/forms/assets/rule-editor23.png)
1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.

+++

+++ &#x200B;4. Een voorbeeld van een formulier bekijken

Nu, wanneer u voorproef de vorm en **Bruto Salaris** als `60,000` ingaat, verschijnt het **Extra Vermindering** gebied, en **Belastbaar Inkomen** en **Betaalbare Belasting** worden dienovereenkomstig berekend.

![ Voorproef een vorm ](/help/edge/docs/forms/assets/rule-editor-form.png)

+++

Naast ingebouwde functies zoals Som en Gemiddeld, kunt u douanefuncties tot stand brengen om complexe bedrijfslogica uit te voeren die aan uw specifieke vereisten wordt aangepast.

## Geavanceerd: aangepaste functies

**wanneer om de Functies van de Douane te gebruiken:**

- Voor complexe berekeningen die verder gaan dan de mogelijkheden van ingebouwde functies
- Bedrijfsspecifieke validatieregels implementeren
- Voor gegevenstransformaties en -opmaak
- Integreren met externe systemen of API&#39;s

**Voordelen:**

- **Herbruikbaarheid**: Schrijf de functie eens en gebruik het over veelvoudige vormen en regels
- **Handhaving**: Gecentraliseerde logica die gemakkelijk is bij te werken
- **Prestaties**: Geoptimaliseerde uitvoering van JavaScript
- **Flexibiliteit**: Mogelijkheid om complexe scenario&#39;s te behandelen die niet door standaardregels worden gericht

### **Creërend de Functies van de Douane**

**Plaats van het Dossier**: `/blocks/form/functions.js` in uw project van AEM

**Werkschema van de Ontwikkeling:**

1. **Verklaring van de Functie**
   - Duidelijke en beschrijvende functienamen en parameters definiëren
   - Namen gebruiken die het doel van de functie aangeven
   - Documentparameters en retourneringstypen

2. **Logische Implementatie**
   - Onbewerkte en efficiënte JavaScript-code schrijven
   - Omgaan met randproblemen en foutscenario&#39;s
   - Beste werkwijzen voor codering volgen

3. **de Uitvoer van de Functie**
   - Exporteer functies om deze beschikbaar te maken in de Editor voor regels
   - Benoemde exportfuncties gebruiken voor een betere organisatie
   - Functies testen vóór implementatie

4. **Documentatie**
   - JSDoc-opmerkingen toevoegen voor functiedocumentatie
   - Gebruiksvoorbeelden opnemen
   - Parametertypen en retourwaarden opgeven

In het volgende voorbeeld worden twee aangepaste functies getoond: `getFullName` en `days` .

```JavaScript
/**
 - Get Full Name
 - @name getFullName Concats first name and last name
 - @param {string} firstname in Stringformat
 - @param {string} lastname in Stringformat
 - @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 - Calculate the number of days between two dates.
 - @param {*} endDate
 - @param {*} startDate
 - @name days Calculates the numebr of days between two dates
 - @returns {number} returns the number of days between two dates
 */
function days(endDate, startDate) {
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // return zero if dates are valid
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// eslint-disable-next-line import/prefer-default-export
export { getFullName, days };
```

![ Toevoegend douanefunctie ](/help/edge/docs/forms/assets/create-custom-function.png)

### Een aangepaste functie gebruiken in de regeleditor

Een aangepaste functie gebruiken in de Rule Editor:

1. **voeg de Functie** toe: Voeg uw douanefunctie aan het `../[blocks]/form/functions.js` dossier toe. Zorg ervoor dat u deze component opneemt in de instructie `export` in het bestand.
2. **stel het Dossier** op: Stel het bijgewerkte `functions.js` dossier aan uw project GitHub op en bevestig dat de bouwstijl met succes voltooit.
3. **Gebruik van de Functie**: In de Redacteur van de Regel van uw vorm, heb toegang tot de functie door de `Function Output` optie op het **[!UICONTROL Select Action]** gebied te selecteren.

   ![ Functie van de Douane in de Redacteur van de Regel ](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

4. **Voorproef de Vorm**: Voorproef uw vorm om te verifiëren dat de onlangs uitgevoerde functie zoals verwacht werkt.

## Beste praktijken voor Regelontwikkeling

### **Optimalisering van Prestaties**

**minimaliseer de Complexiteit van de Regel**

- Houd afzonderlijke regels eenvoudig en gefocust.
- Breek complexe logica in veelvoudige kleinere regels.
- Vermijd indien mogelijk diep geneste omstandigheden.

**optimaliseer de Uitvoering van de Regel**

- Plaats eerst de meestgetriggerde regels.
- Gebruik specifieke voorwaarden om onnodige evaluaties te voorkomen.
- Houd rekening met het effect van regels op de laadtijd van formulieren.

**Beheer van het Middel**

- Beperk het aantal regels per formuliercomponent.
- Gebruik aangepaste functies voor herhaalde logica in plaats van dubbele regels.
- Testprestaties met realistische gegevensvolumes.

### **de Richtlijnen van de Ervaring van de Gebruiker**

**verstrekken Duidelijke Terugkoppeling**

- Gebruik validatieberichten die gebruikers naar juiste invoer leiden.
- Ladingsindicatoren tonen voor regels die externe services omvatten.
- Implementeer progressieve openbaarmaking om cognitieve belasting te verminderen.

**handhaaf de Reactie van de Vorm**

- Vermijd regels die abrupte visuele wijzigingen veroorzaken.
- Hiermee implementeert u vloeiende overgangen voor tonen/verbergen-bewerkingen.
- Testregels voor verschillende apparaten en schermgrootten.

**de Behandeling van de Fout**

- Voorzie fallback gedrag wanneer de regels ontbreken.
- Gebruikersvriendelijke foutberichten weergeven.
- Logfouten voor foutopsporing terwijl een positieve gebruikerservaring behouden blijft.

### **Beste praktijken van de Ontwikkeling**

**het Testen Strategie**

- Testregels met randgevallen en grenswaarden.
- Verifieer regelgedrag over verschillende browsers.
- Functionaliteit van formulier testen, zowel met als zonder JavaScript ingeschakeld.

**Documentatie**

- Documenteer de bedrijfslogica achter complexe regels.
- Een overzicht van regels bijhouden voor grote formulieren.
- Gebruik consistente naamconventies voor componenten en regels.

**Controle van de Versie**

- Wijzigingen bijhouden in aangepaste functies in versiebeheer.
- Testregels in een ontwikkelomgeving vóór de productie.
- Back-ups van werkregelconfiguraties bijhouden.

## Veelvoorkomende problemen oplossen

### **De Problemen van de Uitvoering van de Regel**

**Regels niet teweegbrengen**

- **de componentennamen van de Controle**: Verzeker referenced componenten bestaan en hebben correcte namen.
- **verifieer regelorde**: De regels voeren van boven aan onder uit; reorder indien nodig.
- **bevestigt voorwaarden**: De voorwaarden van de test met bekende waarden om logica te verifiëren.
- **Browser console**: Controle voor de fouten van JavaScript die uitvoering zouden kunnen blokkeren.

**Onjuist Gedrag van de Regel**

- **logische exploitanten van het Overzicht**: Bevestig EN/OF de voorwaarden zijn correct gestructureerd.
- **Test met steekproefgegevens**: Gebruik bekende waarden om kwesties te isoleren.
- **de gegevenstypes van de Controle**: Verzeker numerieke vergelijkingen aantallen, niet koorden gebruiken.
- **bevestigt uitdrukkingen**: Test afzonderlijk wiskundige uitdrukkingen.

### **De Kwesties van Prestaties**

**Langzame Reactie van de Vorm**

- **Verminder regelingewikkeldheid**: Vereenvoudig complexe voorwaardelijke logica.
- **optimaliseer douanefuncties**: Profiel en optimaliseer de code van JavaScript.
- **de externe vraag van de grens**: Minimaliseer de dienstaanroepen in regels.
- **Gebruik efficiënte selecteurs**: verzeker de verwijzingen van vormobjecten specifiek zijn.

**Gebruik van het Geheugen**

- **Schoon gebeurtenisluisteraars** op: verwijder ongebruikte regelbanden.
- **optimaliseer douanefuncties**: Vermijd geheugenlekken in de code van JavaScript.
- **het regelwerkingsgebied van de Beperking**: Gebruik gerichte regels in plaats van globale voorwaarden.

### **De Kwesties van de Functie van de Douane**

**niet Beschikbare Functies**

- **de dossierweg van de Controle**: verifieer `functions.js` is in de correcte plaats: `/blocks/form/functions.js`.
- **verifieer de uitvoer**: Zorg ervoor de functies behoorlijk worden uitgevoerd.
- **bouwt proces**: Bevestig het project bouwt omvat het bijgewerkte functiedossier.
- **Geheime voorgeheugen ontruimen**: Wis het browser geheime voorgeheugen na het opstellen van nieuwe functies.

**de Fouten van de Functie**

- **bevestiging van de Parameter**: Controle dat de functieparameters verwachte types aanpassen.
- **de behandeling van de Fout**: Voeg poging-vangstblokken toe om uitzonderingen netjes te behandelen.
- **Logboek van de Console**: Gebruik console.log voor het zuiveren functieuitvoering.
- **JSDoc bevestiging**: Verzeker functiedocumentatie de implementatie aanpast.

### **Universele Integratie van de Redacteur**

**de Redacteur van de Regel verschijnt niet**

- **toegelaten Uitbreiding**: Verifieer de uitbreiding van de Redacteur van de Regel wordt geactiveerd.
- **de selectie van de Component**: Zorg ervoor u een gesteunde vormcomponent hebt geselecteerd.
- **Browser verenigbaarheid**: Test in gesteunde browsers (Chrome, Firefox, Safari).
- **toestemmingen van de Toegang**: Bevestig de gebruiker de noodzakelijke toestemmingen van AEM heeft.

**Kwesties van de Interface**

- **zicht van het Comité**: Gebruik de knevelknoop om het paneel van vormvoorwerpen te tonen of te verbergen.
- **Opslag van de Regel**: Zorg ervoor de regels worden bewaard alvorens de redacteur te sluiten.
- **Browser zoom**: Het browser van het terugstellen zoom aan 100% voor optimale interfacevertoning.

## Belangrijke beperkingen

>[!IMPORTANT]
>
> **Beperkingen van de Functie van de Douane**:
>
> - Statische en dynamische import wordt niet ondersteund in scripts voor aangepaste functies.
> - Alle code moet rechtstreeks in het `/blocks/form/functions.js` -bestand worden opgenomen.
> - Functies moeten synchroon zijn (geen asynchroon, wacht of belofte).
> - De toegang tot browser APIs is beperkt om veiligheidsredenen.

>[!WARNING]
>
> **Overwegingen van de Productie**:
>
> - Test alle regels grondig in een testomgeving.
> - De prestaties van formulieren controleren na het implementeren van complexe regels.
> - Heb een terugschroeven van prijzen voor regel-verwante kwesties.
> - Houd rekening met de gevolgen voor gebruikers met trage netwerkverbindingen.

## Samenvatting

De Redacteur van de Regel in Universele Redacteur laat u toe om intelligente, dynamische vormen tot stand te brengen die uitzonderlijke gebruikerservaring verstrekken. Door voorwaardelijke logica, geautomatiseerde berekeningen, en douanebedrijfsregels uit te voeren, kunt u:

**Transformeer Statische Forms**:

- Voeg voorwaardelijke gebiedszicht voor schonere, meer geconcentreerde interfaces toe.
- Berekeningen en gegevensvalidatie in real time implementeren.
- Maak geavanceerde bedrijfslogica zonder codes.

**verbeter de Ervaring van de Gebruiker**:

- Gebruikers door logische formulierstromen begeleiden.
- Verminder fouten met intelligente validatie.
- Geef onmiddellijk feedback en hulp.

**verbeter Efficiëntie**:

- Hiermee automatiseert u herhaalde berekeningen en gegevensinvoer.
- Complexe workflows stroomlijnen met slimme routering.
- Verminder supportlasten met mogelijkheden voor zelfbediening.

### **Volgende Stappen**

Nu u de grondbeginselen van de Redacteur van de Regel begrijpt:

1. **Begin Eenvoudig**: Begin met basis tonen/verbergen regels alvorens aan complexe berekeningen vooruit te gaan.
1. **Praktijk met Voorbeelden**: Gebruik het leerprogramma van de belastingcalculator als stichting.
1. **onderzoek Geavanceerde Eigenschappen**: Experimenteer met douanefuncties voor gespecialiseerde vereisten.
1. **Test grondig**: Bevestig altijd regels over verschillende scenario&#39;s en apparaten.
1. **Prestaties van de Monitor**: Verzeker regels verbeteren eerder dan belemmerend gebruikerservaring.
