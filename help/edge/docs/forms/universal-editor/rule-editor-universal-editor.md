---
title: Regeleditor voor Edge Delivery Services Forms
description: Maak dynamische, intelligente formulieren met de Rule Editor in de Universal Editor. Voorwaardelijke logica, berekeningen en interactief gedrag toevoegen zonder codering.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 0d088d4e3b4e27fac0a05ff93a7fd01535bba6af
workflow-type: tm+mt
source-wordcount: '2824'
ht-degree: 0%

---


# Regeleditor voor Edge Delivery Services Forms

De redacteur van de Regel staat auteurs toe om statische vormen in ontvankelijke, intelligente ervaringen te veranderen zonder code te schrijven. U kunt voorwaardelijk gebieden tonen, berekeningen uitvoeren, gegevens bevestigen, gebruikers door stromen begeleiden, en bedrijfslogica integreren die zich aanpast aangezien mensen typen.

## Wat u gaat leren

Aan het einde van deze handleiding kunt u het volgende doen:

- Begrijp hoe de regels werken en wanneer om verschillende regeltypes te gebruiken
- De Rule Editor in de Universal Editor inschakelen en openen
- Voorwaardelijke logica maken om velden dynamisch weer te geven of te verbergen
- Automatische berekeningen en gegevensvalidatie implementeren
- Bouw douanefuncties voor complexe bedrijfsregels
- Beste werkwijzen toepassen voor prestaties, onderhoudbaarheid en UX

## Waarom de Redacteur van de Regel gebruiken?

- **Voorwaardelijke logica**: toon relevante gebieden slechts wanneer nodig om lawaai en cognitieve lading te verminderen.
- **Dynamische berekeningen**: Verwerk automatisch waarden (totalen, tarieven, belasting) als gebruikerstype.
- **bevestiging van Gegevens**: Vermijd vroege fouten met controles in real time en duidelijke berichten.
- **Geleide ervaringen**: Laad gebruikers door logische stappen (tovenaars, vertakkend).
- **geen-code authoring**: Vorm krachtig gedrag door een visuele interface.

Veelvoorkomende scenario&#39;s zijn onder meer belastingcalculators, lening- en premieschatters, subsidiabiliteitsstromen, meerfasentoepassingen en enquêtes met voorwaardelijke vragen.

## Hoe regels werken

Een regel definieert wat er moet gebeuren als aan een voorwaarde wordt voldaan. Conceptueel bestaat een regel uit twee delen:

- **Voorwaarde**: Een verklaring die aan waar of vals evalueert.
   - Voorbeelden: &quot;Inkomen > 50.000&quot;, &quot;Dekking = &#39;Ja&#39;,&quot; &quot;Veld is leeg&quot;
- **Actie**: Wat voorkomt wanneer de voorwaarde (en naar keuze, wanneer het vals is) waar is.
   - Voorbeelden: Een veld tonen/verbergen, Een waarde instellen/wissen, Invoer valideren, Een knop inschakelen/uitschakelen

+++ Regellogische patronen

- **Voorwaarde → Actie (toen/toen)**

  ```text
  WHEN Gross Salary > 50000
  THEN Show "Additional Deduction"
  ```

  Dit is het meest geschikt voor voorwaardelijke zichtbaarheid en progressieve openbaarmaking.

- **handeling randvoorwaarde (reeks als/slechts als)**

  ```text
  SET Taxable Income = Gross Salary - Deductions
  IF Deductions are applicable
  ```

  Dit is het meest geschikt voor berekeningen en gegevenstransformaties.

- **als → toen → anders (Afwisselende actie)**

  ```text
  IF Income > 50000
  THEN Show "High Income" fields
  ELSE Show "Standard Income" fields
  ```

  Het beste voor vertakkende logica en wederzijds uitsluitende stromen.

+++

+++ Voorbeeld van een echte wereld

- **Voorwaarde**: &quot;Het bruto salaris overschrijdt $50.000&quot;
- **Primaire actie**: toon &quot;Extra Vermindering&quot;
- **Afwisselende actie**: Verberg &quot;Extra Vermindering&quot;
- **Resultaat**: De gebruikers zien slechts de gebieden die op hen van toepassing zijn

+++

## Vereisten


+++ Toegangsvereisten

**Essentiële toestemmingen en opstelling**:

- **AEM as a Cloud Service**: De auteurstoegang met vorm het uitgeven toestemmingen
- **Universele Redacteur**: Geïnstalleerd en gevormd op uw milieu
- **de uitbreiding van de Redacteur van de Regel**: Toegelaten via [&#x200B; Extension Manager &#x200B;](/help/implementing/developing/extending/extension-manager.md)
- **Vorm het uitgeven toestemmingen**: Mogelijkheid om vormcomponenten in Universele Redacteur tot stand te brengen en te wijzigen

**stappen van de Verificatie**:

1. Bevestig dat u vanuit uw AEM Sites-console toegang hebt tot Universal Editor
2. Controleren of u formuliercomponenten kunt maken en bewerken
3. Controle dat het pictogram van de Redacteur van de Regel ![&#x200B; uitgeven-regels &#x200B;](/help/forms/assets/edit-rules-icon.svg) wanneer het selecteren van vormcomponenten verschijnt

+++

+++ Technische voorschriften

**Vereiste kennis en vaardigheden**:

- **Universele vaardigheid van de Redacteur**: Ervaring creërend vormen met tekstinput, dropdowns, en basisgebiedseigenschappen
- **Bedrijfs logisch begrip**: Mogelijkheid om voorwaardelijke vereisten en bevestigingsregels voor uw specifiek gebruiksgeval te bepalen
- **de componentenvertrouwdheid van de Vorm**: Kennis van gebiedstypes (tekst, aantal, drop-down), eigenschappen (vereist, zichtbaar, read-only), en vormstructuur

**Facultatief voor geavanceerd gebruik**:

- **fundamentals van JavaScript**: Vereist slechts voor het creëren van douanefuncties (gegevenstypes, functies, basissyntaxis)
- **JSON begrip**: Nuttig voor complexe gegevensmanipulatie en API integratie

**vragen van de Beoordeling**:

- Kunt u een basisformulier maken met tekstinvoer en een verzendknop in de Universal Editor?
- Begrijp u wanneer de gebieden in uw bedrijfscontext vereist of facultatief zouden moeten zijn?
- Kunt u aangeven welke formulierelementen voorwaardelijk zichtbaar moeten zijn in uw geval van gebruik?

+++

+++ De extensie Regeleditor inschakelen

**Belangrijk**: De uitbreiding van de Redacteur van de Regel wordt niet toegelaten door gebrek in Universele milieu&#39;s van de Redacteur.

**de stappen van de Activering**:

1. Ga aan [&#x200B; Extension Manager &#x200B;](/help/implementing/developing/extending/extension-manager.md) in uw milieu van AEM
2. Zoek de extensie &quot;Regel-editor&quot; in de lijst met beschikbare extensies
3. Klik **toelaten** en bevestig de activering
4. Wacht tot het systeem is vernieuwd (kan 1-2 minuten duren)

**Verificatie**:

- Na het toelaten, verschijnt het pictogram van de Redacteur van de Regel wanneer u een vormcomponent selecteert: ![&#x200B; geef-regels uit &#x200B;](/help/forms/assets/edit-rules-icon.svg)

![&#x200B; Universele redacteur van de Regel van de Redacteur &#x200B;](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
Figuur: Het pictogram van de Redacteur van de Regel verschijnt wanneer u vormcomponenten selecteert

U opent als volgt de regeleditor:

1. Selecteer een formuliercomponent in de Universal Editor.
2. Klik op het pictogram Regeleditor.
3. De redacteur van de Regel opent in een zijpaneel.

![&#x200B; gebruikersinterface van de Redacteur van de Regel &#x200B;](/help/edge/docs/forms/assets/rule-editor-for-field.png)
Figuur: De interface van de Redacteur van de regel voor het uitgeven componentenregels

>[!NOTE]
>
> In dit artikel verwijzen &quot;formuliercomponent&quot; en &quot;formulierobject&quot; naar dezelfde elementen (bijvoorbeeld invoer, knoppen, deelvensters).

## Overzicht van de interface van Rule Editor

![&#x200B; het gebruikersinterface van de Redacteur van de Regel &#x200B;](/help/edge/docs/forms/assets/rule-editor-interface.png)
Figuur: Volledige interface van de Redacteur van de Regel met genummerde componenten

1. **de titel van de Component en regeltype**: Bevestigt de geselecteerde component en het actieve regeltype.
2. **de Voorwerpen en het paneel van Functies van de Vorm**:

   - Formulierobjecten: hiërarchische weergave van velden en containers voor verwijzing in regels
   - Functies: ingebouwde wiskunde, koord, datum, en bevestigingshelpers

3. **knevel van het Comité**: Toon/verberg de voorwerpen en functies paneel om werkruimte te verhogen
4. **Visuele regelbouwer**: belemmering-en-daling, dropdown-gedreven regelcomponist
5. **Controles**: Gedaan (sparen), annuleer (verwerp). Regels altijd testen voordat ze worden opgeslagen.

+++

+++ Bestaande regels beheren

Wanneer een component al regels heeft, kunt u:

- **Mening**: Zie regelsamenvattingen en logica
- **geef** uit: wijzig voorwaarden en acties
- **opnieuw orde**: De uitvoeringsorde van de verandering (van boven naar onder)
- **toelaten/onbruikbaar maken**: De regels van de knevel voor het testen
- **Schrapping**: Verwijder veilig regels

>[!TIP]
>
> Plaats specifieke regels voor algemene regels. De uitvoering is van boven naar beneden.

+++

## Beschikbare regeltypen

Kies het regeltype dat het meest overeenkomt met uw intentie.

+++ Voorwaardelijke logica

- **wanneer**: Primaire regel voor complex voorwaardelijk gedrag (Voorwaarde → Actie ± anders)
- **Verbergen/tonen**: De zichtbaarheid van controles die op een voorwaarde (progressieve mededeling wordt gebaseerd)
- **toelaten/onbruikbaar maken**: Controles of een gebied interactief is (bijvoorbeeld, maak Submit onbruikbaar tot de vereiste gebieden geldig zijn)

+++

+++ Gegevensmanipulatie

- **Reeks Waarde van**: Auto-bevolkt waarden (bijvoorbeeld, data, totalen, exemplaren)
- **Duidelijke Waarde van**: verwijder gegevens wanneer de voorwaarden veranderen
- **Formaat**: De vertoning die van de transformatie formatteert (munt, telefoon, datum) zonder opgeslagen waarden te veranderen

+++

+++ Validatie

- **Valideer**: De bevestigingslogica van de douane, met inbegrip van dwars-gebiedscontroles en bedrijfsregels

+++

+++ Berekening

- **Wiskundige Uitdrukking**: Verwerk waarden in echt - tijd (totalen, belasting, verhoudingen)

+++

+++ Gebruikersinterface

- **Reeks Focus**: Beweeg nadruk aan een specifiek gebied (gebruik spaarzaam)
- **Vastgesteld Bezit**: Wijzig componenteneigenschappen dynamisch (placeholder, opties, enz.)

+++

+++ Formulierbesturingselement

- **legt Vorm** voor: Programmatiatically legt de vorm voor (slechts na bevestigingspas)
- **Vorm van het Terugstellen**: Duidelijk en teruggesteld aan aanvankelijke staat (bevestig vóór gebruik)
- **sparen Vorm**: sparen als ontwerp voor later (lange vormen, multi-sessie)

+++

+++ Geavanceerd

- **roept Dienst** aan: Externe APIs/de diensten van de vraag (handvat ladend en fouten)
- **voeg/verwijder Instantie** toe: beheer herhaalbare secties (bijvoorbeeld, gebiedsdelen, adressen)
- **navigeer aan**: Route aan andere vormen/pagina&#39;s (bewaart gegevens vóór navigatie)
- **navigeer onder Panelen**: De de opstapnavigatie van de tovenaar van de controle en het overslaan
- **de Gebeurtenis van de Verzending**: De gebeurtenissen van de de douanetrekker voor integratie of analyse

+++

## Stapsgewijze zelfstudie: Een slimme belastingcalculator maken

+++ Overzicht van zelfstudie

In dit voorbeeld ziet u voorwaardelijke zichtbaarheid en automatische berekeningen.

![&#x200B; Schermafbeelding van de interface die van de Redacteur van de Regel de verwezenlijking van een voorwaardelijke regel met wanneer-toen logica voor het zicht van het vormgebied toont &#x200B;](/help/edge/docs/forms/assets/rule-editor-1.png)
Afbeelding: Formulier voor belastingberekening met intelligente voorwaardelijke velden

U maakt een formulier dat:

1. Aanpassing aan gebruikersinvoer door relevante velden weer te geven
2. Hiermee worden waarden in real-time berekend
3. Valideert gegevens om de nauwkeurigheid te verbeteren

+++

+++ Formulierstructuur

| Veldnaam | Type | Doel | Gedrag |
|-------------------------|---------------|--------------------------------|-----------------------------------------|
| Brutosalaris | Nummerinvoer | Jaarinkomen van gebruiker | Voorwaardelijke logica activeren |
| Aanvullende aftrek | Nummerinvoer | Extra aftrek (indien van toepassing) | Alleen zichtbaar wanneer Salary > $50.000 |
| Belastbaar inkomen | Nummerinvoer | Berekende waarde | Alleen-lezen, updates bij wijziging |
| Te betalen belasting | Nummerinvoer | Berekende waarde | Alleen-lezen, berekend op een vaste snelheid |

+++

+++ Bedrijfslogica

- **Regel 1: Voorwaardelijke vertoning**

  ```text
  WHEN Gross Salary > 50,000
  THEN Show "Additional Deduction"
  ELSE Hide "Additional Deduction"
  ```

- **Regel 2: De belastbare berekening van het Inkomen**

  ```text
  SET Taxable Income = Gross Salary - Additional Deduction
  (Only when Additional Deduction applies)
  ```

- **Regel 3: De belastbare berekening**

  ```text
  SET Tax Payable = Taxable Income × 10%
  (Simplified flat rate)
  ```

+++

+++ Stap 1: Maak het formulier

**Doelstelling**: Bouw de basisvorm met alle gebieden en aanvankelijke montages.

1. **Open Universele Redacteur**:
   - Navigeer aan de console van AEM Sites, selecteer uw pagina, klik **uitgeven**
   - Verzeker u de [&#x200B; Universele Redacteur &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html?lang=nl-NL) behoorlijk gevormd hebt

2. **voeg vormcomponenten in deze orde** toe:
   - Titel (H2): &quot;Formulier voor de berekening van belastingen&quot;
   - Nummer input: &quot;Bruto salaris&quot; (Vereist: Ja, tijdelijke aanduiding: &quot;Jaarloon invullen&quot;)
   - Nummer invoer: &quot;Aanvullende aftrek&quot; (Vereist: Nee, tijdelijke aanduiding: &quot;Aanvullende aftrekkingen invoeren&quot;)
   - Invoernummer: &quot;Belastbaar inkomen&quot; (alleen-lezen: Ja)
   - Nummerinvoer: &quot;Belastingplichtig&quot; (alleen-lezen: Ja)
   - Verzenden, knop: BTW berekenen

3. **vorm aanvankelijke gebiedseigenschappen**:
   - &quot;Extra aftrek&quot; verbergen (instellen op Zichtbaar: Nee in deelvenster Eigenschappen)
   - Stel &quot;Belastbaar inkomen&quot; en &quot;Belastbaar inkomen&quot; in op alleen-lezen: Ja

![&#x200B; Schermafbeelding van een vorm van de belastingberekening met inputgebieden voor bruto salaris, huwelijkse status, en afhankelijke kinderen, die de vormstructuur aantonen alvorens de regels worden toegepast &#x200B;](/help/edge/docs/forms/assets/rule-editor2.png)
Afbeelding: Oorspronkelijke formulierstructuur met basiscomponenten geconfigureerd

**Controlepunt**: U zou een vorm met alle vereiste gebieden moeten hebben waar de &quot;Extra Vermindering&quot;verborgen is en de berekende gebieden read-only zijn.

+++

+++ Stap 2: Voorwaardelijke zichtbaarheidsregel toevoegen

**Doel**: toon &quot;Extra Vermindering&quot;gebied slechts wanneer het Bruto Salaris $50.000 overschrijdt.

1. **selecteer het Bruto gebied van het Salaris** en klik het pictogram van de Redacteur van de Regel ![&#x200B; uitgeven-regels &#x200B;](/help/forms/assets/edit-rules-icon.svg)
2. **creeer een nieuwe regel**:
   - Klik **creëren**
   - Wijzig het regeltype van &quot;Waarde instellen van&quot; in **&quot;Wanneer&quot;**
3. **vorm de voorwaarde**:
   - Selecteer **&quot;is groter dan&quot;** van dropdown
   - Voer `50000` in het nummerveld in
4. **plaats toen actie**:
   - Kies **&quot;tonen&quot;** van de Uitgezochte drop-down Actie
   - Sleep of selecteer **&quot;Extra Vermindering&quot;** gebied van de Voorwerpen van de Vorm
5. **voeg de Else actie** toe:
   - Klik **&quot;voeg anders Sectie toe&quot;**
   - Kies **&quot;Verbergen&quot;** van de Uitgezochte drop-down Actie
   - Selecteer **&quot;Extra Vermindering&quot;** gebied
6. **sparen de regel**: Klik **Gedaan**

>[!NOTE]
>
> Alternatieve benadering: u kunt hetzelfde resultaat bereiken door een regel Tonen/Verbergen rechtstreeks te maken op het veld Aanvullende aftrek in plaats van een regel bij Bruto Salaris.

+++

+++ Stap 3: Berekening toevoegen

**Doel**: berekent automatisch &quot;Belastbaar Inkomen&quot;en &quot;Belastbaar die&quot;op gebruikersinput wordt verschuldigd.

**vorm de Belastbare berekening van het Inkomen**:

1. **Uitgezochte &quot;Belastbaar Inkomen&quot;gebied** en open de Redacteur van de Regel
2. **creeer Wiskundige Uitdrukking**:
   - Klik **creëren** → Uitgezochte **&quot;Wiskundige uitdrukking&quot;**
   - De uitdrukking van de bouw: **Bruto Salaris - de Extra Vermindering**
   - Sleep &quot;Bruin salaris&quot; naar het eerste veld
   - Selecteer **&quot;Min&quot;** exploitant
   - Sleep &quot;Aanvullende aftrek&quot; naar tweede veld
3. **sparen**: Klik **Gedaan**

**vorm de Belastingverschuldigde berekening**:

1. **Uitgezochte &quot;Belasting Betaalbaar&quot;gebied** en open de Redacteur van de Regel
2. **creeer Wiskundige Uitdrukking**:
   - Klik **creëren** → Uitgezochte **&quot;Wiskundige uitdrukking&quot;**
   - Bouw uitdrukking: **Belastbaar Inkomen × 10:100**
   - Sleep &quot;Belastbaar inkomen&quot; naar het eerste veld
   - Selecteer **&quot;Multiplied door&quot;** exploitant
   - Voer `10` in als getal
   - Klik **&quot;Uitbreiden Uitdrukking&quot;**
   - Selecteer **&quot;verdeeld door&quot;** exploitant
   - Voer `100` in als getal
3. **sparen**: Klik **Gedaan**

+++

+++ Stap 4: Test het formulier

**verifieer uw implementatie door de volledige stroom** te testen:

1. **Voorproef de vorm**: Klik de voorproefwijze in Universele Redacteur
2. **Test de voorwaardelijke logica**:
   - Voer Brutosalaris in = `30000` → &quot;Aanvullende aftrek&quot; moet verborgen blijven
   - Voer het brutosalaris in = `60000` → &quot;Aanvullende aftrek&quot; moet worden weergegeven
3. **berekeningen van de Test**:
   - Voer bij Brutosalaris = `60000` de optie Aanvullende aftrek = `5000` in
   - Belastbaar inkomen verifiëren = `55000` (60000 - 5000)
   - Betaalbare belasting verifiëren = `5500` (55000 × 10%)

![&#x200B; Voorproef een vorm &#x200B;](/help/edge/docs/forms/assets/rule-editor-form.png)
Afbeelding: Voltooide belastingcalculator met voorwaardelijke velden en automatische berekeningen

**criteria van het Succes**: De vorm zou velden dynamisch tonen/verbergen en waarden in real time moeten berekenen aangezien de gebruikers typen.


+++

## Geavanceerd: aangepaste functies

Voor complexe bedrijfslogica buiten de ingebouwde mogelijkheden, kunt u de functies van douaneJavaScript tot stand brengen die naadloos met de Redacteur van de Regel integreren.

+++ Wanneer kunt u aangepaste functies gebruiken

**Ideale scenario&#39;s voor douanefuncties**:

- **Complexe berekeningen**: De multi-step berekeningen worden niet gemakkelijk uitgedrukt in de Wiskundige regel van de Uitdrukking
- **zaken-specifieke bevestigingen**: De logica van de bevestiging van de douane specifiek voor uw organisatie of industrie
- **de transformaties van Gegevens**: De omzettingen van het formaat, koordmanipulaties, of gegevens het ontleden
- **Externe integraties**: Vraag aan interne APIs of derdediensten (met beperkingen)

**Voordelen van douanefuncties**:

- **Herbruikbaarheid**: Schrijf eens, gebruik over veelvoudige vormen en regels
- **handhaafbaarheid**: Gecentraliseerde logica die gemakkelijker is bij te werken en te zuiveren
- **Prestaties**: De geoptimaliseerde uitvoering van JavaScript in vergelijking met complexe regelketens
- **Flexibiliteit**: De randgevallen van de handvat en complexe scenario&#39;s die niet door standaardregels worden gericht

+++

+++ Aangepaste functies maken en implementeren

**plaats van het Dossier**: Alle douanefuncties moeten in `/blocks/form/functions.js` in uw project van Edge Delivery Services worden bepaald.

**werkschema van de Ontwikkeling**:

1. **het ontwerp van de Functie**
   - Beschrijvende, actiegerichte functienamen gebruiken
   - Definieer duidelijke parametertypen en retourwaarden
   - Afbeeldingen met randen en ongeldige invoer netjes verwerken

2. **Implementatie**
   - Schrijf schone JavaScript met goede opmerkingen
   - Inclusief invoervalidatie en foutafhandeling
   - Testfuncties onafhankelijk van elkaar vóór integratie

3. **Documentatie**
   - Uitgebreide JSDoc-opmerkingen toevoegen
   - Gebruiksvoorbeelden en parameterbeschrijvingen opnemen
   - Alle beperkingen of afhankelijkheden documenteren

4. **Plaatsing**
   - Exportfuncties met benoemde exportfuncties
   - Distribueren naar de gegevensopslagruimte van uw project
   - Voltooien van build controleren vóór testen

**implementatie van het Voorbeeld**:

```javascript
/**
 * Concatenates first and last name with proper formatting
 * @name getFullName
 * @description Combines first and last name, handles edge cases like missing values
 * @param {string} firstName - The person's first name
 * @param {string} lastName - The person's last name  
 * @returns {string} Formatted full name or empty string if both inputs are invalid
 */
function getFullName(firstName, lastName) {
  // Handle null, undefined, or empty string inputs
  const first = (firstName || '').toString().trim();
  const last = (lastName || '').toString().trim();
  
  return `${first} ${last}`.trim();
}

/**
 * Calculates the number of days between two dates
 * @name days
 * @description Computes absolute difference in days, handles various date input formats
 * @param {Date|string} endDate - End date (Date object or ISO string)
 * @param {Date|string} startDate - Start date (Date object or ISO string)
 * @returns {number} Number of days between dates, 0 if inputs are invalid
 */
function days(endDate, startDate) {
  // Convert string inputs to Date objects
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // Validate date objects
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  // Calculate absolute difference in milliseconds, then convert to days
  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// Export functions for use in Rule Editor
export { getFullName, days };
```

![&#x200B; Toevoegend douanefunctie &#x200B;](/help/edge/docs/forms/assets/create-custom-function.png)
Afbeelding: aangepaste functies toevoegen aan het bestand functions.js

+++

+++ Aangepaste functies gebruiken in de artikeleditor

**stappen van de Integratie**:

1. **voeg functie aan project** toe
   - `/blocks/form/functions.js` maken of bewerken in uw project
   - De functie opnemen in de instructie export

2. **opstellen en bouwt**
   - Wijzigingen vastleggen in uw opslagplaats
   - Ervoor zorgen dat het constructieproces met succes is voltooid
   - Tijd toestaan voor CDN-cache-updates

3. **Toegang in de Redacteur van de Regel**
   - Regeleditor openen voor formuliercomponenten
   - Selecteer **&quot;Uitvoer van de Functie&quot;** in **Uitgezochte actie** dropdown
   - Kies uw aangepaste functie in de lijst met beschikbare functies
   - Functieparameters configureren met formuliervelden of statische waarden

4. **Test grondig**
   - Geef een voorbeeld van het formulier weer om het gedrag van de functie te controleren
   - Testen met verschillende invoercombinaties, inclusief randbehuizingen
   - De invloed van prestaties op het laden van formulieren en interactie controleren

![&#x200B; Functie van de Douane in de Redacteur van de Regel &#x200B;](/help/edge/docs/forms/assets/custom-function-rule-editor.png)
Figuur: Het selecteren en het vormen van douanefuncties in de interface van de Redacteur van de Regel

>
>
> De verbeteringen aan de Redacteur van de Regel, met inbegrip van douane op gebeurtenis-gebaseerde regels, steun voor dynamische variabelen, en API integratie, zijn ook beschikbaar voor Edge Delivery Services Forms. Meer over deze verhogingen leren en hoe te om hen te gebruiken, zie de [&#x200B; Verbeteringen van de Redacteur van de Regel en het Artikel van de Gevallen van het Gebruik &#x200B;](/help/forms/rule-editor-enhancements-use-cases.md).

**Beste praktijken voor functiegebruik**:

- **de behandeling van de Fout**: Neem altijd fallback gedrag voor functiestoornissen op
- **Prestaties**: De functies van het profiel met realistische gegevensvolumes
- **Veiligheid**: Valideer alle input om veiligheidskwetsbaarheid te verhinderen
- **het Testen**: Creeer testgevallen die normale en randgevallen behandelen

+++


### Statische import voor aangepaste functies

De Algemene Editor van de Universele Editor ondersteunt statische importbewerkingen, waarmee u herbruikbare logica kunt indelen in meerdere bestanden en formulieren. In plaats van alle aangepaste functies in één bestand te plaatsen (/blocks/form/functions.js), kunt u functies uit andere modules importeren.
Bijvoorbeeld: functies importeren uit een extern bestand
Overweeg de volgende mapstructuur:

```
      form
      ┣ commonLib
      ┃ ┗ functions.js
      ┣ rules
      ┃ ┗ _form.json
      ┣ form.js
      ┗ functions.js
```

U kunt functies vanuit `commonLib/functions.js` importeren in het `functions.js` -hoofdbestand, zoals hieronder wordt weergegeven:

```
`import {days} from './commonLib/functions';
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in String format
 * @param {string} lastname in String format
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

// Export multiple functions for use in Rule Editor
export { getFullName, days};
```

### Aangepaste functies organiseren in verschillende Forms

U kunt verschillende sets functies maken in afzonderlijke bestanden of mappen en deze naar wens exporteren:

- Als u wilt dat bepaalde functies alleen beschikbaar zijn in specifieke formulieren, kunt u het pad naar het functiebestand in de formulierconfiguratie opgeven.

- Als het tekstvak voor het pad leeg blijft, worden in de Regeleditor standaardfuncties geladen van `/blocks/form/functions.js`

![&#x200B; Functie van de Douane in UE &#x200B;](/help/forms/assets/custom-function-in-ue.png){width=50%}

In de bovenstaande schermafbeelding wordt het pad van de aangepaste functie toegevoegd in het tekstvak Pad aangepaste functie. De aangepaste functies voor dit formulier worden vanuit het opgegeven bestand (`cc_function.js`) geladen.

Dit maakt flexibiliteit mogelijk door functies in meerdere formulieren te delen of ze per formulier geïsoleerd te houden.

## Aanbevolen werkwijzen voor het ontwikkelen van regels


+++ Optimalisatie van prestaties

- Minimaliseer regelcomplexiteit; verdeel grote logica in kleine, gerichte regels
- Regels sorteren op frequentie (meest gangbare eerst)
- Regelsets per component handelbaar houden
- Voorkeur voor herbruikbare aangepaste functies in plaats van logica dupliceren

+++

+++ Gebruikerservaring

- Duidelijke validatie en inlinefeedback bieden
- Vermijd schokkerige visuele wijzigingen; gebruik tonen/verbergen met het oog
- Testen op apparaten en lay-outs

+++

+++ Veiligheid

- Testen met randbehuizingen en bekende waarden
- Verifiëren in verschillende browsers
- Documentintentie achter complexe regels, niet alleen mechanica
- Regelinventarisatie bijhouden voor grote formulieren
- Gebruik consistente naamgeving voor componenten en regels
- Aangepaste versiefuncties en test in niet-productieomgevingen

+++

## Problemen met algemene problemen oplossen


+++ Regels die geen aanleiding geven

- Componentnamen en -verwijzingen verifiëren
- Uitvoervolgorde controleren (van boven naar beneden)
- Voorwaarden met bekende waarden valideren
- Browserconsole controleren op blokkeringsfouten

+++

+++ Onjuist gedrag

- Operatoren en groepering controleren (AND/OR)
- Expressiefragmenten afzonderlijk testen
- Gegevenstypen bevestigen (getallen versus tekenreeksen)

+++

+++ Prestatieproblemen

- Vereenvoudig diep geneste voorwaarden
- Aangepaste functies profiel
- Minimaliseer externe vraag binnen regels
- Specifieke kiezers en verwijzingen gebruiken

+++

+++ Aangepaste functieproblemen

- Bestandspad bevestigen: `/blocks/form/functions.js`
- Ervoor zorgen dat benoemde exportbewerkingen correct zijn
- Bevestig de build met uw wijzigingen
- Browser cache wissen na implementatie
- Parametertypen en foutafhandeling valideren

+++

+++ Integratie van Universal Editor

- Bevestig de uitbreiding van de Redacteur van de Regel wordt toegelaten
- Selecteer een ondersteunde component
- Een ondersteunde browser gebruiken (Chrome, Firefox, Safari)
- Controleer of u de vereiste machtigingen hebt

## Belangrijke beperkingen

>[!IMPORTANT]
>
> Aangepaste functiebeperkingen:
>
> - Statische/dynamische import wordt niet ondersteund
> - Alle logica moet zich bevinden in `/blocks/form/functions.js`
> - Functies moeten synchroon zijn (geen asynchroon, wacht of belofte)
> - Toegang tot browser-API is beperkt

>[!WARNING]
>
> Productieoverwegingen:
>
> - grondig testen in de halteplaats
> - Prestaties bewaken na implementatie
> - Heb een terugschroefplan voor regelkwesties
> - Denk aan langzame netwerken en apparaten met lage specificaties

## Samenvatting

De Redacteur van de Regel in Universele Redacteur zet statische vormen in intelligente, ontvankelijke ervaringen om die aan gebruikersinput in real time aanpassen. Door gebruik te maken van voorwaardelijke logica, geautomatiseerde berekeningen en aangepaste bedrijfsregels, kunt u geavanceerde formulierworkflows maken zonder toepassingscode te schrijven.

**Zeer belangrijke mogelijkheden u** hebt geleerd:

- **Voorwaardelijke logica**: toon en verberg gebieden die op gebruikersinput worden gebaseerd om geconcentreerde, relevante ervaringen tot stand te brengen
- **Dynamische berekeningen**: berekent automatisch waarden (belastingen, totalen, tarieven) aangezien de gebruikers met de vorm in wisselwerking staan
- **bevestiging van Gegevens**: Voer bevestiging in real time met duidelijke, actionable uit terugkoppelt berichten
- **de functies van de Douane**: Breid mogelijkheden met JavaScript voor complexe bedrijfslogica en integratie uit
- **optimalisering van Prestaties**: Pas beste praktijken voor handhaafbare, efficiënte regelontwikkeling toe

**Geleverde Waarde**:

- **Verbeterde gebruikerservaring**: Verminder cognitieve lading met progressieve onthulling en intelligente vormstromen
- **Verminderde fouten**: Vermijd ongeldige voorlegging door bevestiging in real time en geleide input
- **Verbeterde efficiency**: Automatiseer berekeningen en gegevensingang om gebruikersinspanning te minimaliseren
- **Handelbare oplossingen**: Creeer herbruikbare, goed gedocumenteerde regels die over uw organisatie schrapen

**Bedrijfs effect**:

Forms wordt een krachtig hulpmiddel voor gegevensverzameling, kwalificatie van leads en betrokkenheid van gebruikers. De redacteur van de Regel laat niet-technische auteurs toe om verfijnde bedrijfslogica uit te voeren, die ontwikkelingskosten vermindert terwijl het verbeteren van vormvoltooiingstarieven en gegevenskwaliteit.

+++

## Volgende stappen

**geadviseerde het leren weg**:

1. **Begin met grondbeginselen**: Creeer eenvoudige tonen/verbergen regels om de kernconcepten te begrijpen
2. **Praktijk met leerprogramma&#39;s**: Gebruik het voorbeeld van de belastingcalculator als stichting voor uw eigen vormen
3. **breid geleidelijk** uit: Voeg wiskundige uitdrukkingen en bevestigingsregels toe aangezien uw vertrouwen groeit
4. **voer douanefuncties** uit: Ontwikkel de functies van JavaScript voor gespecialiseerde bedrijfsvereisten
5. **optimaliseer en schaal**: Pas prestaties beste praktijken toe en handhaaf regeldocumentatie

**Extra middelen**:

- [&#x200B; Universele documentatie van de Redacteur &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html?lang=nl-NL) voor bredere context
- [&#x200B; de gids van Extension Manager &#x200B;](/help/implementing/developing/extending/extension-manager.md) voor het toelaten van extra mogelijkheden
- [&#x200B; de vormen van Edge Delivery Services &#x200B;](/help/edge/docs/forms/overview.md) voor uitvoerige begeleiding van de vormontwikkeling

