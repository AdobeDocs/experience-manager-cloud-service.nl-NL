---
title: Hoe te om de regelredacteur te gebruiken om regels op vormgebieden toe te passen, toelatend dynamisch gedrag en complexe logica voor vormen die met het schrijven van WYSIWYG worden gecreeerd?
description: Met de regeleditor in de Universal Editor kunt u dynamisch gedrag toevoegen en complexe logica opnemen in formulieren zonder code of scripts.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '2128'
ht-degree: 0%

---


# Inleiding tot de Redacteur van de Regel in de Authoring van WYSIWYG

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>


U kunt dynamisch formuliergedrag toevoegen met de Regeleditor, waarmee u regels kunt maken. Deze regels maken voorwaardelijke veldzichtbaarheid mogelijk, automatiseren berekeningen op basis van gebruikersinvoer en verbeteren de gebruikerservaring. Door het invullen van formulieren te stroomlijnen, zorgt de Rule Editor voor zowel nauwkeurigheid als efficiëntie.

De Redacteur van de Regel biedt een intuïtieve visuele interface voor het creëren van en het beheren van regels aan. De gebruikersvriendelijke aanpak maakt het toegankelijk voor alle gebruikers, zelfs voor gebruikers zonder uitgebreide technische expertise, zodat zij zonder problemen logica in hun formulieren kunnen implementeren.

## Een regel begrijpen

Regels zijn instructies die gebruikers begeleiden bij welke handelingen onder specifieke omstandigheden moeten worden uitgevoerd.

* **Voorwaarde**: Een voorwaarde is een controle of een regel die evalueert of iets waar of vals is. Het beantwoordt de vraag: &quot;Voldoet dit aan de vereiste?&quot;

* **Actie**: Een actie is wat gebeurt wanneer de voorwaarde waar is. Het is de taak of het gedrag die op de evaluatie van de voorwaarde wordt teweeggebracht.

Een regel volgt doorgaans een van de volgende constructies:

* **voorwaarde-actie**: Controleer eerst een voorwaarde, dan voer een actie uit. In de regeleditor dwingt het `When` -regeltype de `condition-action` -construct af.
* **actie-Voorwaarde**: Voer eerst een actie uit, dan controleer een voorwaarde. De regeltypen `Set Value Of` en `Validate` in de regeleditor dwingen de construct `action-condition` af.
* **actie-voorwaardelijk-Afwisselende Actie**: Voer een actie uit, controleer een voorwaarde, en of voer dan de belangrijkste actie of een afwisselende actie uit die op de voorwaarde wordt gebaseerd. De alternatieve handeling voor `Show` is bijvoorbeeld `Hide` en voor `Enable` is deze `Disable` .

Een voorwaarde kan bijvoorbeeld controleren of een gebruiker een bepaalde waarde in een veld heeft ingevoerd en de actie kan bestaan in het weergeven of verbergen van een veld.
* **Voorwaarde**: Controle als het inkomen groter is dan $50.000.
* **Actie**: Als de voorwaarde waar is, toon het `Additional Deduction` gebied; anders, voer de afwisselende actie uit: verberg het `Additional Deduction` gebied.

Voor gedetailleerde geleidelijke instructies, zie [ een voorwaardelijke regel ](#2-add-a-conditional-rule) toevoegen.

## Hoe te om de uitbreiding van de Redacteur van de Regel toe te laten?

In Universele Redacteur, wordt de uitbreiding van de Redacteur van de Regel niet toegelaten door gebrek. Om de uitbreiding van de Redacteur van de Regel toe te laten schrijven aan ons in [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) van uw officiële e-mailidentiteitskaart

Nadat de uitbreiding van de Redacteur van de Regel voor uw milieu wordt toegelaten, ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram verschijnt in de hoger-juiste hoek van de redacteur uit.

![ Universele redacteur van de Regel van de Redacteur ](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

Selecteer de vormcomponent waarvoor u een regel wilt schrijven, en ![ uitgeven-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram klikken. De gebruikersinterface van de Redacteur van de Regel verschijnt.

![ gebruikersinterface van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor-for-field.png)

In dit artikel worden `form object` en `form component` door elkaar gebruikt.

Nu, kunt u beginnen regels of bedrijfslogica voor het geselecteerde vormgebied te schrijven door de [ beschikbare regeltypes in de Redacteur van de Regel ](#available-rule-types-in-rule-editor) te gebruiken.

## Werken met de gebruikersinterface van de Rule Editor

De redacteur van de Redacteur van de Regel opent wanneer u ![ uitgeeft-lijnen ](/help/forms/assets/edit-rules-icon.svg) pictogram klikt:

![ het gebruikersinterface van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor-interface.png)

<table border="1">
  <thead>
    <tr>
      <th>Component of Rule Editor</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Titel</td>
      <td>Hiermee geeft u de titel van de formuliercomponent en het geselecteerde regeltype weer. 'Voer het brutosalaris in' is bijvoorbeeld een tekstvakcomponent waarvoor het regeltype 'Wanneer' is geselecteerd. </td>
    </tr>
    <tr>
      <td>2. Formulierobjecten en -functies</td>
      <td>Het <b> Forms bezwaar heeft </b> lusje toont een hiërarchische mening van alle componenten in de vorm. Het <b> lusje van Functies </b> omvat een reeks ingebouwde functies in de regelredacteur.</td>
    </tr>
    <tr>
      <td>3. Schakelen tussen formulierobjecten en -functies</td>
      <td>Met de schakelknop kunt u het deelvenster Formulierobjecten en -functies afwisselend weergeven of verbergen. </td>
    </tr>
    <tr>
      <td>4. Visuele-regeleditor</td>
      <td>De visuele Redacteur van de Regel is de interface waar u regels voor de vormcomponenten kunt tot stand brengen.</td>
    </tr>
    <tr>
      <td>5. Gereed en annuleer knoppen</td>
      <td>De <b> Gedaan </b> knoop wordt gebruikt om een regel te bewaren. De <b> annuleert </b> knoop verwerpt om het even welke veranderingen die u aan een regel aanbracht en sluit de Redacteur van de Regel.</td>
    </tr>
  </tbody>
</table>

Bestaande regels voor een formuliercomponent worden weergegeven wanneer u de component selecteert. U kunt de titel en een voorproef de regelsamenvatting op de Redacteur van de Regel bekijken. Bovendien kunt u de volgorde van regels wijzigen, regels bewerken, regels inschakelen/uitschakelen of regels verwijderen.

![ toon de beschikbare regels van vormvoorwerp ](/help/edge/docs/forms/assets/rule-editor15.png)

## Beschikbare regeltypen

De Redacteur van de Regel verstrekt een reeks vooraf bepaalde regeltypes die u kunt gebruiken om regels te schrijven, zoals getoond in hieronder lijst:

<table border="1">
  <thead>
    <tr>
      <th>Type regel</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Waarde instellen van</td>
      <td>Hiermee wordt de waarde van een formuliercomponent ingesteld, afhankelijk van of aan de opgegeven voorwaarde wordt voldaan of niet.</td>
    </tr>
    <tr>
      <td>Waarde wissen van</td>
      <td>Wist de waarde van de opgegeven formuliercomponent.</td>
    </tr>
    <tr>
      <td>Verbergen/weergeven</td>
      <td>Hiermee wordt een formuliercomponent verborgen of weergegeven op basis van het feit of aan een voorwaarde is voldaan.</td>
    </tr>
    <tr>
      <td>In-/uitschakelen</td>
      <td>Schakelt een formuliercomponent in of uit op basis van het feit of aan een voorwaarde is voldaan of niet.</td>
    </tr>
    <tr>
      <td>Valideren</td>
      <td>Controleert de formuliercomponent op basis van een voorwaarde en geeft een fout weer als niet aan de voorwaarde wordt voldaan. </td>
    </tr>
    <tr>
      <td>Wanneer</td>
      <td>Hiermee wordt een voorwaarde opgegeven voor evaluatie gevolgd door een actie die wordt geactiveerd als aan de voorwaarde is voldaan. Het volgt de <i> voorwaarde-actie-afwisselende </i> constructie van de actieregel of <i> voorwaarde-actie </i> regelconstructie. </td>
    </tr>
    <tr>
      <td>Indeling</td>
      <td> Wijzigt de weergavewaarde van de formuliercomponent met de opgegeven expressie wanneer de waarde ervan verandert.</td>
    </tr>
    <tr>
      <td>Invoke-service</td>
      <td>Roept de dienst aan die gebruikend externe APIs, het Model van de Gegevens van de Vorm of de Webdiensten RESTful wordt gevormd.</td>
    </tr>
    <tr>
      <td>Eigenschap instellen</td>
      <td>Hiermee wordt de waarde van een eigenschap van de opgegeven formuliercomponent ingesteld op basis van een voorwaarde.</td>
    </tr>
    <tr>
      <td>Focus instellen</td>
      <td>Hiermee wordt de focus op de opgegeven formuliercomponent ingesteld.</td>
    </tr>
    <tr>
      <td>Formulier opslaan</td>
      <td>Hiermee kan de gebruiker het formulier opslaan als concept met de component Concepten en verzendingen van Forms Portal. </td>
    </tr>
    <tr>
      <td>Formulier verzenden</td>
      <td>Hiermee verzendt u het formulier.</td>
    </tr>
    <tr>
      <td>Formulier opnieuw instellen</td>
      <td>Hiermee herstelt u het formulier.</td>
    </tr>
    <tr>
      <td>Instantie toevoegen/verwijderen</td>
      <td>Hiermee wordt een instantie van het opgegeven herhaalbare deelvenster of de opgegeven tabelrij toegevoegd of verwijderd.</td>
    </tr>
    <tr>
      <td>Navigeren naar</td>
      <td>Navigeert naar andere Adaptieve Forms, andere elementen zoals afbeeldingen of documentfragmenten of een externe URL.</td>
    </tr>
    <tr>
      <td>Dispatch-gebeurtenis</td>
      <td>Hiermee worden specifieke acties geactiveerd op basis van vooraf gedefinieerde voorwaarden of gebeurtenissen.</td>
    </tr>
    <tr>
      <td>Navigeren tussen de deelvensters</td>
      <td>Hiermee kunt u de focus verplaatsen tussen verschillende deelvensters in een formulier.</td>
    </tr>
  </tbody>
</table>


Nu, onderzoeken hoe te [ regels in de Redacteur van de Regel ](#write-rules) schrijven.

## Regels schrijven

Om te begrijpen hoe te om regels in de Visuele Redacteur van de Regel te schrijven, denken een eenvoudig voorbeeld van een vorm van de belastingberekening:

![ Schermafbeelding van de interface die van de Redacteur van de Regel de verwezenlijking van een voorwaardelijke regel met wanneer-toen logica voor het zicht van het vormgebied toont ](/help/edge/docs/forms/assets/rule-editor-1.png)

In het hierboven beschreven formulier voert de gebruiker het brutosalaris in. Op basis van deze invoer wordt het voorwaardelijke veld weergegeven en wordt de verschuldigde belasting berekend.

**Gebieden van de Vorm:**
* Brutosalaris (gebruikersinvoer)
* Aanvullende aftrek (voorwaardelijk veld)
* Belastbaar inkomen (berekend veld)
* Belasting verschuldigd (berekend veld)

**Voorwaardelijke Regel:**
* Toestand: Brutosalaris > 50.000
* Actie: het veld Aanvullende aftrek tonen

**Regels van de Berekening:**

* Belastbaar inkomen = Brutosalaris - Aanvullende aftrek (indien van toepassing)
* Belastingplichtig = Belastbaar inkomen * Belastingtarief (voor de eenvoud wordt uitgegaan van een vast tarief van 10%)

Voer de volgende stappen uit om regels te schrijven:

### &#x200B;1. Auteur van een formulier

Een formulier maken in de universele editor:

1. Open een formulier in de Universal Editor om het te bewerken.
1. Voeg de volgende formuliercomponenten toe:
   * Formulier voor belastingberekening (titel)
   * Brutosalaris (invoer getal)
   * Extra aftrek (invoer getal)
   * Belastbaar inkomen (invoer van getal)
   * Te betalen belasting (invoer aantal)
   * Verzenden (knop Verzenden)
1. Verberg het formulierveld `Additional Deduction` door het `Properties` ervan te openen.

   ![ Schermafbeelding van een vorm van de belastingberekening met inputgebieden voor bruto salaris, huwelijkse status, en afhankelijke kinderen, die de vormstructuur aantonen alvorens de regels worden toegepast ](/help/edge/docs/forms/assets/rule-editor2.png)

### &#x200B;2. Een voorwaardelijke regel toevoegen voor een formulierveld

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

### &#x200B;3. Berekeningen toevoegen voor de formuliervelden

Vervolgens schrijft u een regel om de `Taxable Income` te berekenen. Dit is het verschil tussen `Gross Salary` en `Additional Deduction` (indien van toepassing). Voer de volgende stappen uit om een berekeningsregel toe te voegen aan het veld **[!UICONTROL Taxable Income]** :

1. Op auteurswijze, selecteer het **[!UICONTROL Taxable Income]** gebied en selecteer ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit. U kunt het veld **[!UICONTROL Taxable Income]** ook rechtstreeks in het deelvenster **[!UICONTROL Forms Object]** selecteren.
1. Selecteer vervolgens **[!UICONTROL Create]** om de regel te maken.
   ![ de Redacteur example13 van de Regel ](/help/edge/docs/forms/assets/rule-editor16.png)
1. Selecteer **[!UICONTROL Select Option]** en selecteer **[!UICONTROL Mathematical Expression]** . Er wordt een veld voor het schrijven van wiskundige expressies geopend.
   ![ de Redacteur example14 van de Regel ](/help/edge/docs/forms/assets/rule-editor17.png)

1. In het veld Wiskundige expressie:

   * Selecteer of sleep-daling van het lusje van de Objecten van Forms het **[!UICONTROL Gross Salary]** gebied in het eerste **[!UICONTROL Drop object or select here]** gebied.

   * Selecteer **[!UICONTROL Minus]** in het veld **[!UICONTROL Select Operator]** .

   * Selecteer of sleep-daling van het lusje van de Objecten van Forms het **[!UICONTROL Additional Deduction]** gebied in het andere **[!UICONTROL Drop object or select here]** gebied.

     ![ de Redacteur example15 van de Regel ](/help/edge/docs/forms/assets/rule-editor18.png)

1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.

   Voeg nu een regel voor het veld `Tax Payable ` toe, die wordt bepaald door het belastbare inkomen te vermenigvuldigen met het belastingtarief. Veronderstel voor eenvoud een vast belastingtarief van `10%`.

1. Op auteurswijze, selecteer het **[!UICONTROL Tax Payable]** gebied en selecteer ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit. Selecteer vervolgens **[!UICONTROL Create]** om regels te maken.
   ![ de Redacteur example16 van de Regel ](/help/edge/docs/forms/assets/rule-editor19.png)
1. Selecteer **[!UICONTROL Select Option]** en selecteer **[!UICONTROL Mathematical Expression]** . Er wordt een veld voor het schrijven van wiskundige expressies geopend.
   ![ de Redacteur example17 van de Regel ](/help/edge/docs/forms/assets/rule-editor20.png)
1. In het veld Wiskundige expressie:

   * Selecteer of sleep-daling van het lusje van de Objecten van Forms het **[!UICONTROL Taxable Income]** gebied in het eerste **[!UICONTROL Drop object or select here]** gebied.

   * Selecteer **[!UICONTROL Multiplied by]** in het veld **[!UICONTROL Select Operator]** .

   * Selecteer **Aantal** van het **[!UICONTROL Select Option]** gebied en ga de waarde als `10` op het **[!UICONTROL Enter a Number]** gebied in.

     ![ de Redacteur example18 van de Regel ](/help/edge/docs/forms/assets/rule-editor21.png)
1. Selecteer vervolgens in het gemarkeerde gebied rond het expressieveld en selecteer **[!UICONTROL Extend Expression]** .
   ![ de Redacteur example19 van de Regel ](/help/edge/docs/forms/assets/rule-editor22.png)
1. Selecteer in het veld Uitgebreide expressie **[!UICONTROL divided by]** in het **[!UICONTROL Select Operator]** veld en **[!UICONTROL Number]** in het **[!UICONTROL Select Option]** veld. Geef vervolgens `100` op in het nummerveld.
   ![ de Redacteur example20 van de Regel ](/help/edge/docs/forms/assets/rule-editor23.png)
1. Selecteer **[!UICONTROL Done]** om de regel op te slaan.

### &#x200B;4. Een voorbeeld van een formulier bekijken

Nu, wanneer u voorproef de vorm en **Bruto Salaris** als `60,000` ingaat, verschijnt het **Extra Vermindering** gebied, en **Belastbaar Inkomen** en **Betaalbare Belasting** worden dienovereenkomstig berekend.

![ Voorproef een vorm ](/help/edge/docs/forms/assets/rule-editor-form.png)

Naast de uit-van-de-doos functies zoals Som, Gemiddelde die onder de Output van Functies vermeld zijn, kunt u [ douanefuncties ](#create-a-custom-function) schrijven om complexe bedrijfslogics uit te voeren.

## Aangepaste functie in regeleditor

Edge Delivery Services Forms ondersteunt aangepaste functies waarmee gebruikers JavaScript-functies kunnen definiëren voor het implementeren van complexe bedrijfsregels. De aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken om aan bepaalde vereisten te voldoen.

### Een aangepaste functie maken

Als u aangepaste functies wilt maken, bewerkt u het bestand `../[blocks]/form/functions.js` . Het aanmaakproces omvat doorgaans de volgende stappen:

* **Verklaring van de Functie**: Bepaal de functienaam en zijn parameters (de input die het goedkeurt).
* **Logische Implementatie**: Schrijf de code die de specifieke berekeningen of de manipulaties beschrijft die door de functie worden uitgevoerd.
* **Uitvoer van de Functie**: Maak de functie toegankelijk binnen uw regels door het van het relevante dossier uit te voeren.


In dit voorbeeld worden twee aangepaste functies getoond als `getFullName` en `days` :

```JavaScript
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in Stringformat
 * @param {string} lastname in Stringformat
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 * Calculate the number of days between two dates.
 * @param {*} endDate
 * @param {*} startDate
 * @name days Calculates the numebr of days between two dates
 * @returns {number} returns the number of days between two dates
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

U kunt als volgt de aangepaste functie in de regeleditor gebruiken:

1. **voeg de Functie** toe: Omvat uw douanefunctie in het `../[blocks]/form/functions.js` dossier. Vergeet niet deze toe te voegen aan de instructie `export` in het bestand.
1. **stel het Dossier** op: Stel het bijgewerkte `functions.js` dossier aan uw project GitHub op en verifieer een succesvolle bouwstijl.
1. **Gebruik van de Functie**: Heb toegang tot de functie binnen de Redacteur van de Regel van uw vorm door de `Function Output` optie op het **[!UICONTROL Select Action]** gebied te selecteren.

   ![ Functie van de Douane in de Redacteur van de Regel ](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **Voorproef de vorm**: Voorproef uw vorm met de onlangs uitgevoerde functie.

## Aanvullende informatie

>[!NOTE]
>
> In de Universal Editor wordt statische en dynamische import niet ondersteund in aangepaste functiescripts. U moet de volledige code toevoegen in het `../[blocks]/form/functions.js` -bestand.

Dit artikel bevat beperkte informatie over de Rule Editor die beschikbaar is in de Universal Editor. Meer over de Redacteur van de Regel en douanefuncties leren, verwijs naar de volgende artikelen:

{{see-also-rule-editor}}

## Zie ook

{{universal-editor-see-also}}
