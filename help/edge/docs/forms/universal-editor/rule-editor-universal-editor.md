---
title: Hoe te om de regelredacteur te gebruiken om regels op vormgebieden toe te passen, toelatend dynamisch gedrag en complexe logica voor vormen die met het schrijven van WYSIWYG worden gecreeerd?
description: Met de regeleditor in de Universal Editor kunt u dynamisch gedrag toevoegen en complexe logica opnemen in formulieren zonder code of scripts.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '1994'
ht-degree: 0%

---


# Inleiding tot de Redacteur van de Regel in Universele Redacteur

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

In Universele Redacteur, wordt de Redacteur van de Regel niet toegelaten door gebrek. Om de uitbreiding van de Redacteur van de Regel voor uw milieu toe te laten, verzend een e-mail van uw officieel adres aan [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) met uw verzoek.

Nadat de uitbreiding van de Redacteur van de Regel voor uw milieu wordt toegelaten, ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram verschijnt in de hoger-juiste hoek van de redacteur uit.

![ Universele redacteur van de Regel van de Redacteur ](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

Selecteer het vormvoorwerp waarvoor u een regel wilt schrijven, en ![ uitgeven-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram klikken. De gebruikersinterface van de Redacteur van de Regel verschijnt.

![ gebruikersinterface van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor-for-field.png)

Nu, kunt u beginnen regels of bedrijfslogica voor het geselecteerde vormgebied te schrijven door de [ beschikbare regeltypes in de Redacteur van de Regel ](#available-rule-types-in-rule-editor) te gebruiken.

## Werken met de gebruikersinterface van de Rule Editor

De visuele redacteur van de Redacteur van de Regel opent wanneer u klikt ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit:

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
      <td>1. Weergave van componentregelaars</td>
      <td>Hiermee wordt de titel van het formulierobject weergegeven waarmee u de regeleditor hebt gestart en het regeltype dat momenteel is geselecteerd.</td>
    </tr>
    <tr>
      <td>2. Formulierobjecten en -functies</td>
      <td>Het <b> lusje van Objecten van Forms </b> toont een hiërarchische mening van alle voorwerpen bevat in de vorm. Het <b> lusje van Functies </b> omvat een reeks ingebouwde functies.</td>
    </tr>
    <tr>
      <td>3. Schakelen tussen formulierobjecten en -functies</td>
      <td>Met de schakelknop schakelt u, wanneer hierop wordt getikt, de formulierobjecten en het deelvenster met functies in of uit.</td>
    </tr>
    <tr>
      <td>4. Visuele-regeleditor</td>
      <td>De visuele Redacteur van de Regel is het gebied op de visuele redacteurswijze van het gebruikersinterface van de Redacteur van de Regel waar u regels schrijft.</td>
    </tr>
    <tr>
      <td>5. Gereed en annuleer knoppen</td>
      <td>De <b> Gedaan </b> knoop wordt gebruikt om een regel te bewaren. De <b> annuleert </b> knoop verwerpt om het even welke veranderingen die u aan een regel aanbracht en sluit de Redacteur van de Regel.</td>
    </tr>
  </tbody>
</table>

Bestaande regels op een formulierobject worden weergegeven wanneer u het object selecteert. U kunt de titel en een voorproef de regelsamenvatting op de visuele Redacteur van de Regel bekijken. Bovendien kunt u de volgorde van regels wijzigen, regels bewerken, regels inschakelen/uitschakelen of regels verwijderen.

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
      <td>Hiermee wordt de waarde van een formulierobject ingesteld, afhankelijk van of aan de opgegeven voorwaarde wordt voldaan.</td>
    </tr>
    <tr>
      <td>Waarde wissen van</td>
      <td>Wist de waarde van het opgegeven object.</td>
    </tr>
    <tr>
      <td>Verbergen/weergeven</td>
      <td>Hiermee wordt een formulierobject verborgen of weergegeven op basis van het feit of aan een voorwaarde is voldaan.</td>
    </tr>
    <tr>
      <td>In-/uitschakelen</td>
      <td>Schakelt een formulierobject in of uit op basis van het feit of aan een voorwaarde is voldaan of niet.</td>
    </tr>
    <tr>
      <td>Valideren</td>
      <td>Valideert het formulier of een opgegeven object.</td>
    </tr>
    <tr>
      <td>Wanneer</td>
      <td>Volgt <i> voorwaarde-actie-afwisselende </i> de construct van de actieregel of <i> voorwaarde-actie </i> regelconstructie. Hiermee wordt een voorwaarde opgegeven voor evaluatie gevolgd door een actie die wordt geactiveerd als aan de voorwaarde is voldaan.</td>
    </tr>
    <tr>
      <td>Indeling</td>
      <td>Maakt een formulierobject op basis van een functie of reguliere expressie op.</td>
    </tr>
    <tr>
      <td>Invoke-service</td>
      <td>Roept de dienst aan die in een model van vormgegevens (FDM) wordt gevormd.</td>
    </tr>
    <tr>
      <td>Eigenschap instellen</td>
      <td>Stelt de waarde van een eigenschap van het opgegeven object in op basis van een voorwaarde.</td>
    </tr>
    <tr>
      <td>Focus instellen</td>
      <td>Hiermee wordt de focus op het opgegeven object ingesteld.</td>
    </tr>
    <tr>
      <td>Formulier opslaan</td>
      <td>Hiermee slaat u het formulier op.</td>
    </tr>
    <tr>
      <td>Formulier verzenden/opnieuw instellen</td>
      <td>Hiermee verzendt of herstelt u het formulier.</td>
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

Om te begrijpen hoe te om regels in de Visuele Redacteur van de Regel te schrijven, overwegen een eenvoudig voorbeeld van een vorm van de belastingberekening:

![ Voorbeeld van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor-1.png)

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

### 1. Auteur van een formulier

Een formulier maken in de universele editor:

1. Open een formulier in de Universal Editor om het te bewerken.
1. Voeg de volgende formuliercomponenten toe:
   * Formulier voor belastingberekening (titel)
   * Brutosalaris (tekstinvoer)
   * Extra aftrek (tekstinvoer)
   * Belastbaar inkomen (tekstinvoer)
   * Te betalen belasting (tekstinvoer)
   * Verzenden (knop Verzenden)
1. Verberg het formulierveld `Additional Deduction` door het `Properties` ervan te openen.

   ![ Voorbeeld van de Redacteur van de Regel ](/help/edge/docs/forms/assets/rule-editor2.png)

### 2. Een voorwaardelijke regel toevoegen voor een formulierveld

Nadat u het formulier hebt gemaakt, schrijft u de eerste regel om het veld `Additional Deduction` alleen weer te geven als het brutosalaris hoger is dan € 50.000. Een voorwaardelijke regel toevoegen:

1. Open een formulier in de Universal Editor om het te bewerken.
1. Selecteer de **[!UICONTROL Gross Salary]** component in de inhoudsboom en selecteer ![ uitgeven-regels ](/help/forms/assets/edit-rules-icon.svg).
   ![ de Redacteur example1 van de Regel ](/help/edge/docs/forms/assets/rule-editor3.png)
De visuele interface van de Redacteur van de Regel verschijnt.
1. Klik op **[!UICONTROL Create]** om de regeleditor te starten.
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
1. Selecteer **[!UICONTROL Show]** in de vervolgkeuzelijst **[!UICONTROL Select Action]** in de instructie `Then` .
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

### 3. Berekeningen toevoegen voor de formuliervelden

Vervolgens schrijft u een regel om de `Taxable Income` te berekenen. Dit is het verschil tussen `Gross Salary` en `Additional Deduction` (indien van toepassing). Voer de volgende stappen uit om een berekeningsregel toe te voegen aan het veld **[!UICONTROL Taxable Income]** :

1. Op auteurswijze, selecteer het **[!UICONTROL Taxable Income]** gebied en selecteer ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit. Selecteer vervolgens **[!UICONTROL Create]** om de regeleditor te starten.
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

1. Op auteurswijze, selecteer het **[!UICONTROL Tax Payable]** gebied en selecteer ![ geef-regels ](/help/forms/assets/edit-rules-icon.svg) pictogram uit. Selecteer vervolgens **[!UICONTROL Create]** om de regeleditor te starten.
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

### 4. Een voorbeeld van een formulier bekijken

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

1. **Voorproef de Vorm**: Voorproef uw vorm met de onlangs uitgevoerde functie.

## Verwante artikelen

{{see-also-rule-editor}}

## Zie ook

* [Aan de slag met Edge Delivery Services voor AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Een formulier maken met Google Sheets of Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Stel uw Google-werkbladen of Microsoft Excel-bestanden in om te beginnen met het accepteren van &#x200B;](/help/edge/docs/forms/submit-forms.md)
* [Publish uw formulier en begin gegevens te verzamelen](/help/edge/docs/forms/publish-forms.md)
* [De weergave van uw formulieren aanpassen &#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [Herhaalbare secties toevoegen aan een &#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [Een aangepast bedankbericht weergeven na &#x200B; verzenden van formulier](/help/edge/docs/forms/thank-you-page-form.md)
* [Aangepaste componenten van het Blok van de Vorm en hun eigenschappen](/help/edge/docs/forms/form-components.md)
* [ Echte Controle van het Gebruik ](https://www.aem.live/developer/rum#authentication)
