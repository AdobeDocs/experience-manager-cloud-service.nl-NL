---
title: Document met record genereren voor adaptieve Forms
description: Verklaart hoe u een malplaatje voor een Document van Verslag (DoR) voor Aangepast Forms kunt produceren.
exl-id: 15540644-c0c3-45ce-97d3-3bdaa16fb4b6
source-git-commit: f75636c1b964c9edbc3e1dee937f3807e194c311
workflow-type: tm+mt
source-wordcount: '3603'
ht-degree: 1%

---

# Document met record genereren voor adaptieve Forms

## Overzicht {#overview}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Deze record wordt een Document of Record (DoR) genoemd. Het is een afdrukvriendelijke kopie van het ingediende formulier. U kunt ook het document met records raadplegen voor de gegevens die klanten op een latere datum hebben ingevuld, of het document met records gebruiken om formulieren en inhoud samen te archiveren in de indeling PDF.

![Document van record](assets/document-of-record.png)

Als u een document met records wilt maken, wordt een op XFA of Acroform gebaseerde sjabloon samengevoegd met gegevens die via een adaptief formulier zijn verzameld. U kunt een Document van Verslag automatisch of op bestelling produceren.
Met de optie Op aanvraag kunt u een aangepaste XFA- of Acrobat-sjabloon opgeven die een aangepaste weergave biedt voor uw Document of Record.

U kunt:

* [Een op XFA gebaseerd document met records genereren](#generate-an-XFA-based-document-of-record)
* [Een op acroform gebaseerd (Acrobat Form PDF) document met records genereren](#generate-an-Acroform-based-document-of-record)
* [Automatisch een document met records genereren](#auto-generate-a-document-of-record)

## Voordat u begint {#components-to-automatically-generate-a-document-of-record}

Voordat u leert welke elementen nodig zijn voor een Document of Record:

**Basissjabloon:** Een XFA-sjabloon (XDP-bestand) gemaakt in Forms Designer of een Acrobat-formulier (AcroForm). [Basissjabloon](#base-template-of-a-document-of-record) wordt gebruikt om opmaak- en brandinggegevens op te geven voor een Document of Record. Upload uw XFA-sjabloon (XDP-bestand) naar uw AEM Forms-instantie voordat

**Adaptief formulier:** Een adaptief formulier waarvoor het document of record moet worden gegenereerd.

## Een op XFA gebaseerd document met records genereren {#generate-an-XFA-based-document-of-record}

Upload uw XFA-sjabloon (XDP-bestand) naar uw AEM Forms-instantie. Voer de volgende stappen uit om een adaptief formulier te configureren voor het gebruik van XFA-sjabloon (XDP-bestand) als sjabloon voor Document of Record:

1. Klik in de auteur van Experience Manager op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]**.
1. Tik in het venster Eigenschappen op **[!UICONTROL Form Model]**.
1. Op de  **[!UICONTROL Form Model]** tabblad, in het dialoogvenster **[!UICONTROL Select From]** vervolgkeuzelijst, selecteert u **[!UICONTROL Schema]** of **[!UICONTROL None]**. U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel de optie **Formuliersjabloon koppelen als Document of Record-sjabloon**. Als u deze optie selecteert, worden alle XFA-sjablonen (XDP-bestanden) die op uw computer beschikbaar zijn, weergegeven. Selecteer het juiste bestand. Zorg er ook voor dat hetzelfde schema (gegevensschema) wordt gebruikt voor Adaptief formulier en geselecteerde XFA-sjabloon (XDP-bestand).
1. Klik op **[!UICONTROL Done.]**

Het adaptieve formulier is nu geconfigureerd voor het gebruik van een XDP-bestand als sjabloon voor het document of record. De volgende stappen zijn: [Aangepaste formuliercomponenten binden met de bijbehorende sjabloonvelden](#bind-adaptive-form-components-with-template-fields).

## Een op acroform gebaseerd document met records genereren {#generate-an-Acroform-based-document-of-record}

Upload uw Adobe Acrobat PDF (Acroform) naar uw AEM Forms-exemplaar. Voer de volgende stappen uit om een adaptief formulier zo te configureren dat Adobe Acrobat PDF (Acroform) wordt gebruikt als sjabloon voor Document of Record:

1. Klik in de auteur van Experience Manager op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]**.
1. Tik in het venster Eigenschappen op **[!UICONTROL Form Model]**.
1. Op de  **[!UICONTROL Form Model]** tabblad, in het dialoogvenster **[!UICONTROL Select From]** vervolgkeuzelijst, selecteert u **[!UICONTROL Schema]** of **[!UICONTROL None]**. U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel de optie **Formuliersjabloon koppelen als Document of Record-sjabloon**. Als u deze optie selecteert, worden alle Acrobat PDF (Acroform) die op uw computer beschikbaar zijn, weergegeven. Selecteer het juiste bestand.
1. Klik op **[!UICONTROL Done.]**

Het adaptieve formulier is nu geconfigureerd voor het gebruik van een Acrobat-formulier als sjabloon voor het document met records. De volgende stappen zijn: [Aangepaste formuliercomponenten binden met de bijbehorende sjabloonvelden](#bind-adaptive-form-components-with-template-fields).

## Automatisch een document met records genereren {#auto-generate-a-document-of-record}

Als een adaptief formulier is geconfigureerd om automatisch een Document of Record te genereren, wordt het document van Record van het formulier direct bijgewerkt telkens wanneer een formulier wordt gewijzigd. Als bijvoorbeeld een veld wordt verwijderd uit een bestaand adaptief formulier, wordt het bijbehorende veld ook verwijderd en is het niet zichtbaar in het Document of Record. Er zijn veel andere voordelen van het automatisch genereren van Document of Record. :

* Formulierontwikkelaars hoeven de gegevensbindingen niet handmatig bij te houden. Het automatisch gegenereerde document met records verzorgt de aan gegevensbinding gerelateerde updates.
* Formulierontwikkelaars hoeven velden die zijn gemarkeerd als niet opnemen in Document of Record, niet handmatig te verbergen. Automatisch gegenereerd document met record is vooraf geconfigureerd om dergelijke velden uit te sluiten.
* Met de optie Automatisch gegenereerd document van record bespaart u tijd die nodig is om een formuliersjabloon te maken voor Document of Record.
* Met de optie Automatisch gegenereerd document van record kunt u verschillende stijlen en weergaven gebruiken met verschillende basissjablonen. Het helpt de beste stijl en verschijning voor Document van Verslag voor uw organisatie selecteren. Als u geen stijlen opgeeft, worden systeemstijlen standaard ingesteld.
* Automatisch gegenereerd document van record zorgt ervoor dat elke wijziging in het formulier direct wordt weerspiegeld in het document van record.

Voer de volgende stappen uit om een adaptief formulier te configureren zodat automatisch een Document of Record wordt gegenereerd:

1. Klik in de auteur van Experience Manager op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]**.
1. Tik in het venster Eigenschappen op **[!UICONTROL Form Model]**.
1. Op de  **[!UICONTROL Form Model]** tabblad, in het dialoogvenster **[!UICONTROL Select From]** vervolgkeuzelijst, selecteert u **[!UICONTROL Schema]** of **[!UICONTROL None]**. U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel de optie **Document van record genereren**.
1. Klik op **[!UICONTROL Done.]**

## Aangepaste formuliercomponenten binden met sjabloonvelden {#bind-adaptive-form-components-with-template-fields}

Adaptief-formuliervelden binden met sjabloonvelden om vastgelegde formuliergegevens weer te geven in het corresponderende document van het recordveld. Aangepaste formuliercomponenten binden aan het corresponderende document met recordsjabloonvelden:

1. Open het adaptieve formulier, geconfigureerd om een aangepaste formuliersjabloon te gebruiken voor bewerken.

1. Selecteer een component Adaptief formulier en klik op Configureren ![Configureren](assets/Smock_Wrench_18_N.svg) pictogram. De eigenschappenbrowser wordt geopend.

1. Blader in de eigenschappenbrowser naar een veld en selecteer dit.

   * (Voor de AcroForm-sjabloon) **[!UICONTROL Document of Record Bind Reference field]** eigenschap.
   * (Voor XFA-sjabloon) **[!UICONTROL Data Model Bind Reference]** eigenschap.

1. Klik op **[!UICONTROL Save]**.

<!-- 
In the following video Adaptive Form components are binded with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

U kunt de verzendactie E-mail, Workflow en Experience Manager gebruiken in combinatie met [Document van de stap van het Verslag, en andere voorgelegde acties](configuring-submit-actions.md) om een Document van Verslag te ontvangen.

## Incrementele updates van de sjabloon Document of Record {#document-of-record-template-incremental-updates}

Aangepaste formulieren en het bijbehorende document met recordsjablonen kunnen zich over een bepaalde periode ontwikkelen. U kunt velden toevoegen, verwijderen of wijzigen aan een adaptief formulier of een document met een recordsjabloon.

Wanneer u wijzigingen aanbrengt in een Document of Record-sjabloon en het gewijzigde Document of Record-sjabloon uploadt naar AEM Forms, detecteert de Adaptive Forms-editor automatisch de gewijzigde bindingen en wordt u geïnformeerd over de adaptieve formuliercomponenten die nieuwe bindingen vereisen. Hiermee kunt u incrementele updates uitvoeren voor een Document of Record-sjabloon.

Een organisatie, *Wij.Detailhandel*, een op AcroForm gebaseerd Document met een Record-sjabloon heeft, *we-retail-factuur.pdf*. De sjabloon ziet er als volgt uit:

![Oorspronkelijke sjabloon](assets/we-retail-invoice.png)

Na enige tijd het gebruiken van het malplaatje, besluit de organisatie anders te noemen `invoice-number` veld naar `bill-number` e-mailadres van kopers in het veld en vastleggen. Een ontwikkelaar werkt de naam van de `invoice-number` en voegt een e-mailveld toe aan de sjabloon. Hij creeert ook een nieuwe versie van malplaatje genoemd  *we-retail-factuur-v2.pdf*.

![Bijgewerkte sjabloon](assets/we-retail-new-invoice.png)

De ontwikkelaar uploadt en past de bijgewerkte sjabloon toe op het adaptieve formulier. Het adaptieve formulier detecteert automatisch velden waarvan de binding is gewijzigd en geeft een lijst weer.

![Bindingsfout](assets/we-retail-binding-error.png)

De formulierontwikkelaar bindt adaptieve Forms-velden aan het overeenkomstige Document of Record-sjabloon.
>[!VIDEO](assets/we-retail-binding.mp4)

Wanneer het adaptieve formulier wordt verzonden, wordt nu een bijgewerkt document met recordgegevens gemaakt.

![Bijgewerkt-](assets/we-retail-new-invoice-sent-to-customer.png)

## Belangrijke overwegingen bij het werken met het document Record {#key-considerations-when-working-with-document-of-record}

Houd rekening met de volgende overwegingen en beperkingen wanneer u werkt aan Document of Record voor Adaptive Forms.

* Document van de malplaatjes van het Verslag steunt rijke teksten niet. Alle RTF-tekst in het statische adaptieve formulier of in de informatie die door de eindgebruiker is ingevuld, wordt daarom als onbewerkte tekst weergegeven in het Document of Record.
* Documentfragmenten in een adaptief formulier worden niet weergegeven in het Document of Record. Adaptieve formulierfragmenten worden echter wel ondersteund.
* Inhoudbinding in Document of Record gegenereerd voor adaptief formulier op basis van een XML-schema wordt niet ondersteund.
* De gelokaliseerde versie van Document van Verslag wordt gecreeerd op bestelling voor een scène wanneer de gebruiker om de teruggave van het Document van Verslag verzoekt. De lokalisatie van Document of Record vindt plaats samen met de lokalisatie van het adaptieve formulier. <!-- For more information on localization of Document of Record and Adaptive Forms see Using AEM translation workflow to localize Adaptive Forms and Document of Record.-->

<!-- ## Configure an adaptive form to generate  Document of Record {#adaptive-form-types-and-their-documents-of-record}

While creating an adaptive form, in the Form Model tab of Adaptive Form properties, select one the following option: 

* **None**
  Select the option to create an Adaptive Form without a form model. When the option is selected, the Document of Record is automatically generated for your Adaptive Form.

* **[Associate form template as a Document of Record template](creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template)**
  
  Select the option to use an XFA Form as a template for Document of Record. 

* **[Generate Document of Record](creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema)**
  Select the option to use an XFA Form as a template. When the option is selected, the Document of Record is automatically generated for your Adaptive Form. When you use an XML schema as a template for an Adaptive Form, ensure that the adaptive form and associated XFA Form use the same XML schema as your Adaptive Form
  

When you select a form model, configure Document of Record using options available under Document of Record Template Configuration. See [Document of Record Template Configuration](#document-of-record-template-configuration). -->

## Toewijzing van adaptieve formulierelementen {#mapping-of-adaptive-form-elements}

In de volgende tabel worden de componenten Adaptief formulier en de corresponderende XFA-componenten beschreven en wordt aangegeven of deze in een Document of Record worden weergegeven.

### Fields {#fields}

<table>
 <tbody>
  <tr>
   <th>Component Adaptief formulier</th>
   <th>Overeenkomende XFA-component</th>
   <th>Standaard opgenomen in Document of Record Template?</th>
   <th>Opmerkingen</th>
  </tr>
  <tr>
   <td>Knop</td>
   <td>Knop</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Selectievakje</td>
   <td>Selectievakje</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumkiezer</td>
   <td>Datum-/tijdveld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Vervolgkeuzelijst</td>
   <td>Vervolgkeuzelijst</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Krabbelhandtekening</td>
   <td>Krabbelen op handtekening</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeriek vak</td>
   <td>Numeriek veld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Wachtwoordvak</td>
   <td>Wachtwoordveld</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Keuzerondje</td>
   <td>Keuzerondje</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Tekstvak</td>
   <td>Tekstveld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Knop Opnieuw instellen</td>
   <td>Knop Opnieuw instellen</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Verzendknop</td>
   <td><p>Knop Verzenden via e-mail</p> <p>Knop HTTP verzenden</p> </td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Voorwaarden en bepalingen</td>
   <td> </td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Bestandsbijlage</td>
   <td> </td>
   <td>false</td>
   <td>Niet beschikbaar in de sjabloon Document of Record. Alleen beschikbaar in Document of Record via bijlagen.</td>
  </tr>
 </tbody>
</table>

### Containers {#containers}

<table>
 <tbody>
  <tr>
   <th>Component Adaptief formulier</th>
   <th>Overeenkomende XFA-component</th>
   <th>Opmerkingen</th>
  </tr>
  <tr>
   <td>Deelvenster<br /> </td>
   <td>Subformulier<br /> </td>
   <td>Herhalbaar deelvenster verwijst naar herhaalbaar subformulier.</td>
  </tr>
 </tbody>
</table>

### Statische componenten {#static-components}

| Component Adaptief formulier | Overeenkomende XFA-component | Opmerkingen |
|---|---|---|
| Afbeelding | Afbeelding | De componenten TextDraw en Afbeelding, zowel gebonden als niet gebonden, worden altijd in het Document of Record weergegeven voor een adaptief XSD-formulier, tenzij ze worden uitgesloten met de instellingen Document of Record. |
| Tekst | Tekst |

### Tabellen {#tables}

De Adaptive Forms tabelcomponenten zoals koptekst, voettekst en rijtoewijzing aan de overeenkomstige XFA-componenten. U kunt herhaalbare deelvensters toewijzen aan tabellen in Document of Record.

## Basissjabloon van een document van record {#base-template-of-a-document-of-record}

Basissjabloon biedt opmaak- en weergavegegevens voor het document van record. Hiermee kunt u de standaardweergave van automatisch gegenereerd document van record aanpassen. U kunt bijvoorbeeld de basissjabloon gebruiken om het bedrijfslogo toe te voegen aan de koptekst en aan de copyrightgegevens in de voettekst van het Document of Record.

De master pagina van het basissjabloon wordt gebruikt als een master pagina voor de sjabloon Document of Record. De master pagina kan informatie bevatten, zoals paginakoptekst, voettekst en paginanummer, die u kunt toepassen op het document of record. U kunt dergelijke informatie op Document van Verslag toepassen gebruikend basissjabloon voor auto het produceren van Document van Verslag. Met een basissjabloon kunt u de standaardeigenschappen van velden wijzigen.

Altijd volgen [Basissjabloonconventies](#base-template-conventions) wanneer u basissjabloon ontwerpt.

## Basissjabloonconventies {#base-template-conventions}

Een basissjabloon wordt gebruikt om de kop-, voettekst-, opmaak- en vormgeving van een Document of Record te definiëren. De kop- en voettekst kunnen informatie bevatten zoals het bedrijfslogo en de copyrighttekst. De eerste master pagina in de basissjabloon wordt gekopieerd en gebruikt als een master pagina voor het Document of Record. Deze pagina bevat koptekst, voettekst, paginanummer of andere informatie die op alle pagina&#39;s in het Document of Record moet worden weergegeven. Als u een basissjabloon gebruikt dat niet voldoet aan de conventies voor basissjablonen, wordt de eerste master pagina van de basissjabloon nog steeds gebruikt in de sjabloon Document of Record. U wordt ten zeerste aangeraden de basissjabloon te ontwerpen volgens de conventies en deze te gebruiken voor het automatisch genereren van een document met Record.

**Master paginaconventies**

* Geef het basissubformulier in de basissjabloon de naam `AF_METATEMPLATE` en de master pagina als `AF_MASTERPAGE`.

* De master pagina met de naam `AF_MASTERPAGE` die zich onder `AF_METATEMPLATE` Het basissubformulier heeft de voorkeur voor het ophalen van koptekst-, voettekst- en opmaakgegevens.

* Indien `AF_MASTERPAGE` is afwezig, wordt de eerste master pagina gebruikt die in het basissjabloon aanwezig is.

**Opmaakconventies voor velden**

* Als u stijl wilt toepassen op de velden in het document met records, bevat de basissjabloon velden in het dialoogvenster `AF_FIELDSSUBFORM` subfrom under the `AF_METATEMPLATE` basissubformulier.

* De eigenschappen van deze velden worden toegepast op de velden in het Document of Record. Deze velden moeten `AF_<name of field in all caps>_XFO` naamgevingsconventie. De veldnaam voor het selectievakje moet bijvoorbeeld `AF_CHECKBOX_XFO`.

Ga als volgt te werk in Forms Designer om een basissjabloon te maken.

1. Klik op **[!UICONTROL File]** > **[!UICONTROL New]**.
1. Selecteer **[!UICONTROL Based on a template]** optie.

1. Selecteer **[!UICONTROL Forms - Document of Record]** categorie.
1. Selecteer **[!UICONTROL DoR Base Template]**.
1. Klikken **[!UICONTROL Next]** en verstrekt de vereiste informatie.

1. (Optioneel) Wijzig de opmaak en weergave van de velden die u wilt toepassen op de velden in het Document of Record.
1. Sla het formulier op.

U kunt het opgeslagen formulier nu gebruiken als een basissjabloon voor Document of Record. Wijzig of verwijder geen scripts in de basissjabloon.

**Basissjabloon wijzigen**

* Als u geen opmaak toepast op velden in de basissjabloon, is het aan te raden deze velden uit de basissjabloon te verwijderen, zodat alle upgrades naar de basissjabloon automatisch worden opgepakt.
* Verwijder scripts niet tijdens het wijzigen van een basissjabloon, voeg ze toe of wijzig ze niet.

Volg nauwgezet bovenstaande conventies en instructies om een basissjabloon te ontwerpen.

## De brandinggegevens aanpassen in Document of Record {#customize-the-branding-information-in-document-of-record}

Tijdens het genereren van een Document of Record kunt u de brandinggegevens voor het Document of Record wijzigen op het tabblad Document of Record. Het tabblad Document of Record bevat opties zoals logo, weergave, lay-out, koptekst en voettekst, disclaimer en of u niet het selectievakje en keuzerondjes wilt inschakelen of niet.

Als u de brandinggegevens die u opgeeft op het tabblad Document of Record wilt lokaliseren, moet u controleren of de landinstelling van de browser correct is ingesteld. Voer de volgende stappen uit om de brandinggegevens van Document of Record aan te passen:

1. Selecteer een deelvenster (hoofddeelvenster) in het document of Record en tik vervolgens op ![vormen](assets/configure.png).
1. Tikken ![dortab](assets/dortab.png). Het tabblad Document of Record wordt weergegeven.
1. Selecteer de standaardsjabloon of een aangepaste sjabloon voor het weergeven van het Document of Record. Als u de standaardsjabloon selecteert, wordt een miniatuurvoorvertoning van het Document of Record weergegeven onder de vervolgkeuzelijst Sjabloon.

   ![brandingsjabloon](assets/brandingtemplate.png)

   Als u een aangepaste sjabloon wilt selecteren, bladert u door een selectie van een XDP-bestand in uw [!DNL AEM Forms] server. Als u een sjabloon wilt gebruiken die nog niet op uw [!DNL AEM Forms] server, moet u de XDP eerst uploaden naar uw [!DNL AEM Forms] server.

1. Afhankelijk van het feit of u een standaardsjabloon of een aangepaste sjabloon selecteert, worden enkele of alle volgende eigenschappen weergegeven op het tabblad Document of Record. Geef deze op de juiste manier op:

   * **Logoafbeelding**: U kunt kiezen of u de afbeelding met het logo wilt gebruiken in het adaptieve formulier, een afbeelding kiezen in het DAM-model of een afbeelding uploaden vanaf uw computer.
   * **Formuliertitel**
   * **Koptekst**
   * **Label voor afwijzing**
   * **Disclaimer**
   * **Disclaimtekst**
   * **Accentkleur**: De kleur waarin koptekst en scheidingslijnen worden gerenderd in het document of de record PDF
   * **Lettertypefamilie**: Lettertypefamilie van de tekst in het document van Record PDF
   * **Geef voor de componenten Selectievakje en Keuzerondje alleen de geselecteerde waarden weer**
   * **Scheidingsteken voor meerdere geselecteerde waarden**
   * **Formulierobjecten opnemen die niet aan het gegevensmodel zijn gebonden**
   * **Verborgen velden uitsluiten van het document of record**
   * **Beschrijving van deelvensters verbergen**

   >[!NOTE]
   >
   >Als u een adaptieve formuliersjabloon gebruikt dat is gemaakt met een versie van Designer die ouder is dan versie 6.3, werken de eigenschappen Accentkleur en Lettertypefamilie alleen als het volgende aanwezig is in de sjabloon Adaptief formulier onder het basissubformulier:

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Tik op Gereed om de wijzigingen in de branding op te slaan.

## Tabel- en kolomindelingen voor deelvensters in document van record {#table-and-column-layouts-for-panels-in-document-of-record}

Het adaptieve formulier kan lang zijn en meerdere formuliervelden bevatten. U kunt een Document van Verslag niet als nauwkeurige exemplaar van het AanpassingsFormulier willen bewaren. U kunt nu een tabel- of kolomindeling kiezen om een of meer deelvensters voor adaptieve formulieren op te slaan in het document van Record PDF.

Alvorens een Document van Verslag te produceren, in de montages van een paneel, uitgezochte Lay-out voor het Document van Verslag voor dat paneel als Lijst of Kolom. De velden in het deelvenster worden dienovereenkomstig ingedeeld in het document of record.

![Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records](assets/dortablelayout.png)

Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records

![Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records](assets/dorcolumnlayout.png)

Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records

## Document met recordinstellingen {#document-of-record-settings}

Met de instellingen voor Document of Record kunt u opties kiezen die u wilt opnemen in het Document of Record. Een bank accepteert bijvoorbeeld naam, leeftijd, socialezekerheidsnummer en telefoonnummer in een formulier. Het formulier genereert een bankrekeningnummer en filiaalgegevens. U kunt ervoor kiezen alleen de naam, het socialezekerheidsnummer, de bankrekening en de filiaalgegevens weer te geven in Document of Record.

De instelling van de component Document of Record is beschikbaar onder de eigenschappen. Als u toegang wilt krijgen tot de eigenschappen van een component, selecteert u de component en klikt u op ![cmppr](assets/cmppr.png) in de overlay. De eigenschappen worden vermeld in de zijbalk en u kunt de volgende instellingen erin vinden.

**Instellingen op veldniveau**

* **Uitsluiten van document van record**: Als u de eigenschap true instelt, wordt het veld niet opgenomen in Document of Record. Dit is een scriptbare eigenschap met de naam `excludeFromDoR`. Het gedrag hangt af van **Velden uitsluiten van DoR indien verborgen** eigenschap op formulierniveau.

* **Deelvenster weergeven als tabel:** Als u de eigenschap instelt, wordt het deelvenster weergegeven als tabel in Document of Record als het deelvenster minder dan 6 velden bevat. Alleen van toepassing op het deelvenster.
* **Titel van document of record uitsluiten:** Als u de eigenschap instelt, wordt de titel van het deelvenster/de tabel uitgesloten van Document of Record. Alleen van toepassing op het deelvenster en de tabel.
* **Beschrijving uitsluiten van document van record:** Als u de eigenschap instelt, wordt de beschrijving van het deelvenster/de tabel niet opgenomen in Document of Record. Alleen van toepassing op het deelvenster en de tabel.

**Instellingen voor formulierniveau**

* **Inclusief niet-gebonden velden in DoR:** Als u de eigenschap instelt, worden niet-gebonden velden van op schema gebaseerde adaptieve vorm opgenomen in Document of Record. Standaard is dit waar.
* **Velden uitsluiten van DoR indien verborgen:** Als u de eigenschap instelt, wordt de werking van de veldeigenschap &#39;Uitsluiten van document van record&#39; genegeerd als deze niet true is. Als velden verborgen zijn op het moment dat het formulier wordt verzonden, worden ze uitgesloten van Document of Record als de eigenschap is ingesteld op true, op voorwaarde dat de eigenschap &#39;Uitsluiten van document van record&#39; niet is ingesteld.

## Een aangepast XCI-bestand gebruiken

>[!NOTE]
>
> Deze functie is beschikbaar in het prereleasekanaal. Zie [Prerelease Channel-documentatie](/help/release-notes/prerelease.md#enable-prerelease) voor informatie om de functie in te schakelen voor uw omgeving.

Met behulp van een XCI-bestand kunt u verschillende eigenschappen van een document instellen. Forms as a Cloud Service heeft een master XCI-bestand. U kunt een aangepast XCI-bestand gebruiken om een of meer standaardeigenschappen te overschrijven die in het master XCI-bestand zijn opgegeven. U kunt bijvoorbeeld een lettertype insluiten in een document of een gelabelde eigenschap inschakelen voor alle documenten. In de volgende tabel worden de XCI-opties aangegeven:

| XCI, optie | Beschrijving |
|--- |--- |
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Voor informatie over dit woordenboek raadpleegt u de [PDF Referentiehandleiding](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/pdf_reference_archives/PDFReference.pdf). |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Voor informatie over dit woordenboek raadpleegt u de [PDF Referentiehandleiding](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/pdf_reference_archives/PDFReference.pdf). |
| config/present/layout | Hiermee bepaalt u of de uitvoer één deelvenster is of gepagineerd. |
| config/present/pdf/compression/level | Hiermee geeft u de mate van compressie op die moet worden gebruikt bij het genereren van een PDF-document. |
| config/present/pdf/fontInfo/embed | Bepaalt het insluiten van lettertypen in het uitvoerdocument. |
| config/present/pdf/scriptModel | Bepaalt of XFA-specifieke informatie wordt opgenomen in het PDF-uitvoerdocument. |
| config/present/common/data/adjustData | Bepaalt of de XFA-toepassing de gegevens na het samenvoegen aanpast. |
| config/present/pdf/renderPolicy | Bepaalt of het genereren van pagina-inhoud wordt uitgevoerd op de server of uitgesteld aan de client. |
| config/present/common/locale | Geeft de standaardlandinstelling aan die in het uitvoerdocument wordt gebruikt. |
| config/present/destination | Wanneer deze elementen zich in een huidig element bevinden, geeft u de uitvoerindeling op. Wanneer deze zich in een element openAction bevindt, geeft dit de handeling op die moet worden uitgevoerd wanneer het document wordt geopend in een interactieve client. |
| config/present/output/type | Hiermee geeft u het type compressie op dat u wilt toepassen op een bestand of het type uitvoer dat u wilt maken. |
| config/present/common/temp/uri | Hier geeft u de URI van het formulier op. |
| config/present/common/template/base | Hiermee wordt een basislocatie voor URI&#39;s in het formulierontwerp opgegeven. Wanneer dit element ontbreekt of leeg is, wordt de locatie van het formulierontwerp als basis gebruikt. |
| config/present/common/log/to | Controls the location that log data or output data is written to. |
| config/present/output/to | Controls the location that log data or output data is written to. |
| config/present/script/currentPage | Hiermee geeft u de eerste pagina op wanneer het document wordt geopend. |
| config/present/script/exclude | Informeert Forms as a Cloud Service welke gebeurtenissen moeten worden genegeerd. |
| config/present/pdf/linearized | Bepaalt of het PDF-uitvoerdocument lineair is. |
| config/present/script/runScripts | Hiermee bepaalt u welke set scripts Forms as a Cloud Service uitvoert. |
| config/present/pdf/tagged | Controls the include of tags into the output PDF document. Codes, in de context van PDF, zijn aanvullende informatie die in een document is opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. |
| config/present/pdf/fontInfo/alwaysEmbed | Hiermee geeft u een lettertype op dat in het uitvoerdocument wordt ingesloten. |
| config/present/pdf/fontInfo/neverEmbed | Hiermee geeft u een lettertype op dat nooit in het uitvoerdocument mag worden ingesloten. |
| config/present/pdf/pdfa/part | Hier geeft u het versienummer op van de PDF/A-specificatie waarmee het document compatibel is. |
| config/present/pdf/pdfa/amd | Geeft het wijzigingsniveau van de specificatie PDF/A aan. |
| config/present/pdf/pdfa/conformance | Hiermee wordt het compatibiliteitsniveau opgegeven met de PDF/A-specificatie. |
| config/present/pdf/version | Hiermee wordt de versie van het te genereren PDF-document opgegeven |
| config/present/pdf/version/map | Geeft de terugvalfonts voor het document aan |

### Een aangepast XCI-bestand gebruiken in uw as a Cloud Service Forms-omgeving

1. Voeg het aangepaste XCI-bestand toe aan uw ontwikkelingsproject.
1. Geef het volgende op [inline, eigenschap](/help/implementing/deploying/configuring-osgi.md):

   ```JSON
    {
     "xciFilePath": "[path of XCI file]"
    }
   ```

   Bijvoorbeeld,

   ```JSON
    {
     "xciFilePath": "/content/dam/formsanddocuments/customMinionProBoldAndTagged.xci"
    }
   ```

1. Implementeer het project in de omgeving van uw Cloud Service.

### Een aangepast XCI-bestand gebruiken in uw lokale as a Cloud Service Forms-ontwikkelomgeving

1. Upload het XCI-bestand naar uw lokale ontwikkelomgeving.
1. Open Cloud Service SDK Configuration Manager. De standaard-URL is: <http://localhost:4502/system/console/configMgr>.
1. Zoek en open de **[!UICONTROL Adaptive Forms and Interactive Communication Web Channel]** configuratie.
1. Geef het pad van het XCI-bestand op en klik op **[!UICONTROL Save]**.
