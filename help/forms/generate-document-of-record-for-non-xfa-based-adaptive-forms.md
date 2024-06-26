---
title: Hoe te om een document van verslag (DoR) voor AEM Forms te produceren?
description: Leer een sjabloon te genereren voor een Document of Record (DoR) voor Adaptive Forms.
feature: Adaptive Forms, Foundation Components
exl-id: 16d07932-3308-4b62-8fa4-88c4e42ca7b6
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '4030'
ht-degree: 0%

---

# Document met record genereren voor adaptieve Forms

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |

## Overzicht {#overview}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Deze record wordt een Document of Record (DoR) genoemd. Het is een afdrukvriendelijke kopie van het ingediende formulier. U kunt ook het document met records raadplegen voor de gegevens die klanten op een latere datum hebben ingevuld, of het document met records gebruiken om formulieren en inhoud samen te archiveren in de indeling PDF.

![Document van record](assets/document-of-record.png)

Als u een document met records wilt maken, wordt een op XFA of Acroform gebaseerde sjabloon samengevoegd met gegevens die via een adaptief formulier zijn verzameld. U kunt een Document van Verslag automatisch of op bestelling produceren.
Met de optie Op aanvraag kunt u een aangepaste op XFA of Acroform gebaseerde sjabloon opgeven voor een aangepaste weergave van uw Document of Record.

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
1. Selecteer in het venster Eigenschappen de optie **[!UICONTROL Form Model]**.
1. Op de  **[!UICONTROL Form Model]** tabblad, in de **[!UICONTROL Select From]** vervolgkeuzelijst, selecteert u **[!UICONTROL Schema]** of **[!UICONTROL None]**. U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel de optie **Formuliersjabloon koppelen als Document of Record-sjabloon**. Als u deze optie selecteert, worden alle XFA-sjablonen (XDP-bestanden) die op uw computer beschikbaar zijn, weergegeven. Selecteer het juiste bestand. Zorg er ook voor dat hetzelfde schema (gegevensschema) wordt gebruikt voor Adaptief formulier en geselecteerde XFA-sjabloon (XDP-bestand).
1. Klikken **[!UICONTROL Done.]**

Het adaptieve formulier is nu geconfigureerd voor het gebruik van een XDP-bestand als sjabloon voor het document of record. De volgende stap is: [Aangepaste formuliercomponenten binden met de bijbehorende sjabloonvelden](#bind-adaptive-form-components-with-template-fields).

## Een op acroform gebaseerd document met records genereren {#generate-an-Acroform-based-document-of-record}

Upload uw Adobe Acrobat PDF (Acroform) naar uw AEM Forms-exemplaar. Voer de volgende stappen uit om een adaptief formulier zo te configureren dat Adobe Acrobat PDF (Acroform) wordt gebruikt als sjabloon voor Document of Record:

1. Klik in de auteur van Experience Manager op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]**.
1. Selecteer in het venster Eigenschappen de optie **[!UICONTROL Form Model]**.
1. Op de  **[!UICONTROL Form Model]** tabblad, in de **[!UICONTROL Select From]** vervolgkeuzelijst, selecteert u **[!UICONTROL Schema]** of **[!UICONTROL None]**. U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel de optie **Formuliersjabloon koppelen als Document of Record-sjabloon**. Als u deze optie selecteert, worden alle Acrobat PDF (Acroform) die op uw computer beschikbaar zijn, weergegeven. Selecteer het juiste bestand.
1. Klikken **[!UICONTROL Done.]**

Het adaptieve formulier is nu geconfigureerd voor het gebruik van een Acrobat-formulier als sjabloon voor het document met records. De volgende stap is: [Aangepaste formuliercomponenten binden met de bijbehorende sjabloonvelden](#bind-adaptive-form-components-with-template-fields).

## Automatisch een document met records genereren {#auto-generate-a-document-of-record}

Als een adaptief formulier is geconfigureerd om automatisch een Document of Record te genereren, wordt het document van Record van het formulier direct bijgewerkt telkens wanneer een formulier wordt gewijzigd. Als bijvoorbeeld een veld wordt verwijderd uit een bestaand adaptief formulier, wordt het bijbehorende veld ook verwijderd en is het niet zichtbaar in het Document of Record. Er zijn veel andere voordelen van het automatisch genereren van Document of Record. :

* Formulierontwikkelaars hoeven de gegevensbindingen niet handmatig bij te houden. Het automatisch gegenereerde document met records verzorgt updates met betrekking tot gegevensbinding.
* Formulierontwikkelaars hoeven velden die zijn gemarkeerd als niet opnemen in Document of Record, niet handmatig te verbergen. Automatisch gegenereerd document met record is vooraf geconfigureerd om dergelijke velden uit te sluiten.
* Met de optie Automatisch gegenereerd document van record bespaart u tijd die nodig is om een formuliersjabloon te maken voor Document of Record.
* Met de optie Automatisch gegenereerd document van record kunt u verschillende stijlen en weergaven gebruiken met verschillende basissjablonen. Het helpt de beste stijl en verschijning voor Document van Verslag voor uw organisatie selecteren. Als u geen stijlen opgeeft, worden systeemstijlen standaard ingesteld.
* Automatisch gegenereerd document van record zorgt ervoor dat elke wijziging in het formulier direct wordt weerspiegeld in het document van record.

Voer de volgende stappen uit om een adaptief formulier te configureren zodat automatisch een Document of Record wordt gegenereerd:

1. Klik in de auteur van Experience Manager op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]**.
1. Selecteer in het venster Eigenschappen de optie **[!UICONTROL Form Model]**.
1. Op de  **[!UICONTROL Form Model]** tabblad, in de **[!UICONTROL Select From]** vervolgkeuzelijst, selecteert u **[!UICONTROL Schema]** of **[!UICONTROL None]**. U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel de optie **Document van record genereren**.
1. Klikken **[!UICONTROL Done.]**

## Aangepaste formuliercomponenten binden met sjabloonvelden {#bind-adaptive-form-components-with-template-fields}

Adaptief-formuliervelden binden met sjabloonvelden om vastgelegde formuliergegevens weer te geven in het corresponderende document van het recordveld. Aangepaste formuliercomponenten binden aan het corresponderende document met recordsjabloonvelden:

1. Open het adaptieve formulier, geconfigureerd om een aangepaste formuliersjabloon te gebruiken voor bewerken.

1. Selecteer een component Adaptief formulier en klik op Configureren ![Configureren](assets/Smock_Wrench_18_N.svg) pictogram. De eigenschappenbrowser wordt geopend.

1. Blader in de eigenschappenbrowser naar een veld en selecteer dit.

   * (Voor de AcroForm-sjabloon) **[!UICONTROL Document of Record Bind Reference field]** eigenschap.
   * (Voor XFA-sjabloon) **[!UICONTROL Data Model Bind Reference]** eigenschap.

1. Klik op **[!UICONTROL Save]**.

<!-- 
In the following video, Adaptive Form components are bound with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

U kunt de verzendactie E-mail, Workflow en Experience Manager gebruiken in combinatie met [Document van de stap van het Verslag, en andere verzendacties](configuring-submit-actions.md) om een Document van Verslag te ontvangen.

## Incrementele updates van de sjabloon Document of Record {#document-of-record-template-incremental-updates}

Aangepaste formulieren en het bijbehorende document met recordsjablonen kunnen zich over een bepaalde periode ontwikkelen. U kunt velden toevoegen, verwijderen of wijzigen aan een adaptief formulier of een document met een recordsjabloon.

Wanneer u een Document of Record-sjabloon wijzigt en het gewijzigde Document of Record-sjabloon uploadt naar AEM Forms, detecteert de Adaptive Forms-editor automatisch de gewijzigde bindingen en wordt u geïnformeerd over de adaptieve formuliercomponenten die nieuwe bindingen vereisen. Hiermee kunt u incrementele updates uitvoeren voor een Document of Record-sjabloon.

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

## Belangrijkste overwegingen bij het werken met het document Record {#key-considerations-when-working-with-document-of-record}

Houd rekening met de volgende overwegingen en beperkingen wanneer u werkt aan Document of Record voor Adaptive Forms.

* Document van de malplaatjes van het Verslag steunt rijke teksten niet. Alle RTF-tekst in het statische adaptieve formulier of in de informatie die de gebruiker heeft ingevuld, wordt daarom als onbewerkte tekst weergegeven in het Document of Record.
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

### Velden {#fields}

<table>
 <tbody>
  <tr>
   <th>Component Adaptief formulier</th>
   <th>Overeenkomende XFA-component</th>
   <th>Standaard opgenomen in Document of Record Template?</th>
   <th>Notities</th>
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
   <td>Verzenden, knop</td>
   <td><p>Knop E-mail verzenden</p> <p>Knop HTTP verzenden</p> </td>
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
   <th>Notities</th>
  </tr>
  <tr>
   <td>Deelvenster<br /> </td>
   <td>Subformulier<br /> </td>
   <td>Herhalbaar deelvenster verwijst naar herhaalbaar subformulier.</td>
  </tr>
 </tbody>
</table>

### Statische componenten {#static-components}

| Component Adaptief formulier | Overeenkomende XFA-component | Notities |
|---|---|---|
| Afbeelding | Afbeelding | De componenten TextDraw en Afbeelding, zowel gebonden als niet gebonden, worden altijd in het Document of Record weergegeven voor een adaptief XSD-formulier, tenzij ze worden uitgesloten met de instellingen Document of Record. |
| Tekst | Tekst |

### Tabellen {#tables}

De Adaptive Forms tabelcomponenten zoals koptekst, voettekst en rijtoewijzing aan de overeenkomstige XFA-componenten. U kunt herhaalbare deelvensters toewijzen aan tabellen in Document of Record.

## Basissjabloon van een document van record {#base-template-of-a-document-of-record}

Basissjabloon biedt opmaak- en weergavegegevens voor het document van record. Hiermee kunt u de standaardweergave van automatisch gegenereerd document van record aanpassen. U kunt bijvoorbeeld de basissjabloon gebruiken om het bedrijfslogo toe te voegen aan de koptekst en aan de copyrightgegevens in de voettekst van het Document of Record.

De basispagina van het basissjabloon wordt gebruikt als een basispagina voor de sjabloon Document of Record. De stramienpagina kan informatie bevatten zoals paginakoptekst, voettekst en paginanummer die u kunt toepassen op het document of record. U kunt dergelijke informatie op Document van Verslag toepassen gebruikend basissjabloon voor auto het produceren van Document van Verslag. Met een basissjabloon kunt u de standaardeigenschappen van velden wijzigen.

Altijd volgen [Basissjabloonconventies](#base-template-conventions) wanneer u basissjabloon ontwerpt.

## Basissjabloonconventies {#base-template-conventions}

Een basissjabloon wordt gebruikt om de kop-, voettekst-, opmaak- en vormgeving van een Document of Record te definiëren. De kop- en voettekst kunnen informatie bevatten zoals het bedrijfslogo en de copyrighttekst. De eerste basispagina in de basissjabloon wordt gekopieerd en gebruikt als een basispagina voor het Document of Record, die koptekst, voettekst, paginanummer of andere informatie bevat die op alle pagina&#39;s in het Document of Record moet worden weergegeven. Als u een basissjabloon gebruikt dat niet voldoet aan de conventies van de basissjabloon, wordt de eerste basispagina van de basissjabloon nog steeds gebruikt in de sjabloon Document of Record. U wordt ten zeerste aangeraden de basissjabloon te ontwerpen volgens de conventies en deze te gebruiken voor het automatisch genereren van een document met Record.

**Hoofdpaginaconventies**

* Geef het basissubformulier in de basissjabloon de naam `AF_METATEMPLATE` en de basispagina als `AF_MASTERPAGE`.

* De stramienpagina met de naam `AF_MASTERPAGE` die zich onder `AF_METATEMPLATE` Het basissubformulier heeft de voorkeur voor het ophalen van koptekst-, voettekst- en opmaakgegevens.

* Indien `AF_MASTERPAGE` ontbreekt, wordt de eerste basispagina gebruikt die in het basissjabloon aanwezig is.

**Opmaakconventies voor velden**

* Als u stijl wilt toepassen op de velden in het document met records, bevat de basissjabloon velden in het dialoogvenster `AF_FIELDSSUBFORM` subfrom under the `AF_METATEMPLATE` basissubformulier.

* De eigenschappen van deze velden worden toegepast op de velden in het Document of Record. Deze velden moeten `AF_<name of field in all caps>_XFO` naamgevingsconventie. De veldnaam voor het selectievakje moet bijvoorbeeld `AF_CHECKBOX_XFO`.

Ga als volgt te werk in Forms Designer om een basissjabloon te maken.

1. Klikken **[!UICONTROL File]** > **[!UICONTROL New]**.
1. Selecteer de **[!UICONTROL Based on a template]** -optie.

1. Selecteer de **[!UICONTROL Forms - Document of Record]** categorie.
1. Selecteren **[!UICONTROL DoR Base Template]**.
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

1. Selecteer een deelvenster (hoofddeelvenster) in het document of record en selecteer vervolgens ![vormen](assets/configure.png).
1. Selecteren ![dortab](assets/dortab.png). Het tabblad Document of Record wordt weergegeven.
1. Selecteer de standaardsjabloon of een aangepaste sjabloon voor het weergeven van het Document of Record. Als u de standaardsjabloon selecteert, wordt een miniatuurvoorvertoning van het Document of Record weergegeven onder de vervolgkeuzelijst Sjabloon.
1. Afhankelijk van het feit of u een standaardsjabloon of een aangepaste sjabloon selecteert, worden enkele van de volgende eigenschappen of alle eigenschappen weergegeven op het tabblad Document of Record. Geef de onderstaande eigenschappen op om de weergave van het Document of Record te definiëren:

   1. **Basiseigenschappen**:
      * **Sjabloon**: Als u een aangepaste sjabloon wilt selecteren, bladert u door een selectie van een XDP-bestand in uw [!DNL AEM Forms] server. Als u een sjabloon wilt gebruiken die nog niet op uw [!DNL AEM Forms] server, moet u eerst de XDP naar uw [!DNL AEM Forms] server.
      * **Accentkleur**: De kleur waarin koptekst en scheidingslijnen worden gerenderd in het document of de record PDF.
      * **Lettertypefamilie**: Lettertypefamilie van de tekst in Document of Record PDF.

        >[!NOTE]
        >
        > AEM Forms biedt diverse ingebouwde lettertypen die naadloos kunnen worden geïntegreerd met PDF-bestanden. De lijst met ondersteunde lettertypen weergeven [klik hier](/help/forms/supported-out-of-the-box-fonts.md).

      * **Formulierobjecten opnemen die niet aan het gegevensmodel zijn gebonden**: Als u de eigenschap instelt, worden niet-gebonden velden van op schema gebaseerde adaptieve vorm opgenomen in Document of Record.
      * **Verborgen velden uitsluiten van het document of record**: Als u de eigenschap instelt, worden de verborgen velden aangegeven die kunnen worden uitgesloten van het document met records.
      * **Beschrijving van deelvensters verbergen**: Als u de eigenschap instelt, wordt de beschrijving van het deelvenster/de tabel niet opgenomen in Document of Record. Van toepassing op paneel en lijst.

      ![Basiseigenschappen](/help/forms/assets/basicpropertiesdor.png)

   2. **Eigenschappen van formulierveld**:
      * **Geef voor de componenten Selectievakje en Keuzerondje alleen de geselecteerde waarden weer**: Als u de eigenschap instelt, worden alleen geselecteerde waarden van selectievakje en keuzerondje weergegeven in [!UICONTROL Document of Record].
      * **Scheidingsteken voor meerdere waarden**: U kunt een scheidingsteken kiezen, zoals een komma of een regeleinde, om meerdere waarden weer te geven.
      * **Uitlijning opties**: U kunt de gewenste uitlijning (Horizontaal, Verticaal, Hetzelfde als adaptief formulier) selecteren om de uitlijning in te stellen voor velden zoals selectievakjes of keuzerondjes die moeten worden weergegeven op [!UICONTROL Document of Record]. Standaard wordt de verticale uitlijning ingesteld voor de velden in [!UICONTROL Document of Record]. Eigenschappen instellen via de [!UICONTROL Form Field Properties] van DoR overschrijft de eigenschappen die zijn ingesteld in het dialoogvenster [!UICONTROL Item Alignment] voor de velden op een adaptief formulier. In het geval dat u [!UICONTROL Same as Aaptive form] optie, wordt de groepering zoals gevormd in een Adaptief de auteursinstantie van de Vorm gebruikt voor [!UICONTROL Document of Record] velden.
      * **Aantal opties voor horizontale uitlijning**:U kunt het aantal opties instellen dat op het Document of Record moet worden weergegeven voor de horizontale uitlijning.

      ![Eigenschappen van formulierveld](/help/forms/assets/formfieldpropertiesdor.png)

   3. **Eigenschappen basispagina**:
      * **Logoafbeelding**: U kunt kiezen of u de logoafbeelding wilt gebruiken in het adaptieve formulier, een afbeelding kiezen in DAM of een afbeelding uploaden vanaf uw computer.
      * **Formuliertitel**: Titel van het Reglement
      * **Koptekst**: Tekst die wordt weergegeven in de koptekstsectie van het Document of Record.
      * **Label voor afwijzing**: Label van disclaimer.
      * **Disclaimer**: Tekst die de reikwijdte van de rechten en verplichtingen in het document van registratie aangeeft.
      * **Disclaimtekst**: Tekst van de disclaimer.

      ![Eigenschappen basispagina](/help/forms/assets/masterpagepropertiesdor.png)

   >[!NOTE]
   >
   >Als u een adaptieve formuliersjabloon gebruikt die is gemaakt met een versie van Designer die ouder is dan 6.3, werken de eigenschappen Accentkleur en Lettertypefamilie alleen als het volgende aanwezig is in de sjabloon Adaptief formulier onder het basissubformulier:

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

1. Als u de wijzigingen in de branding wilt opslaan, selecteert u **[!UICONTROL Done]**.

## Document met ondersteuning voor records in de Adaptive Form Editor {#dor-support-in-adaptiveform}

U kunt de [!UICONTROL Document of Record] rechtstreeks vanuit de editor voor adaptieve formulieren of de sjablooneditor voor adaptieve formulieren.

Voer de volgende stappen uit vanuit de auteur-instantie van de Adaptieve formuliereditor:

1. Selecteer de **[!UICONTROL Adaptive Form container (Root)]** component.
1. Klikken ![Pictogram configureren](/help/forms/assets/configure-icon.svg) pictogram om het **[!UICONTROL Properties]** van de container Adaptief formulier.
1. Open de **[!UICONTROL Document of Record Template]** en selecteert u een van de volgende opties:
   * **[!UICONTROL None]**: Wanneer deze optie is geselecteerd, is [!UICONTROL Document of Record] sjabloon gemaakt voor uw adaptief formulier.

   * **[!UICONTROL Associate Form Template as Document of Record Template]**:Als deze optie is geselecteerd, wordt XFA-formulier gebruikt als sjabloon voor Document of Record.

   * **[!UICONTROL Generate Document of Record]**: Als deze optie is geselecteerd, wordt de [!UICONTROL Document of Record] wordt automatisch gegenereerd voor uw adaptieve formulier.

1. Selecteren ![Opslaan](/help/forms/assets/check-button.png) om de eigenschappen op te slaan.

![Document met ondersteuning voor recordsjablonen](/help/forms/assets/dor-templatesupport.png)

>[!NOTE]
>
>Wanneer [!UICONTROL Document of Record] de sjabloon wordt gemaakt met een adaptieve formuliersjablooneditor en er zijn dan slechts twee opties beschikbaar onder [!UICONTROL Document of Record Template] tab as [!UICONTROL None] en [!UICONTROL Generate Document of Record].

## Tabel- en kolomindelingen voor deelvensters in document van record {#table-and-column-layouts-for-panels-in-document-of-record}

Het adaptieve formulier kan lang zijn en meerdere formuliervelden bevatten. U kunt een Document van Verslag niet als nauwkeurige exemplaar van het AanpassingsFormulier willen bewaren. U kunt nu een tabel- of kolomindeling kiezen om een of meer deelvensters voor adaptieve formulieren op te slaan in het document van Record PDF.

Alvorens een Document van Verslag te produceren, in de montages van een paneel, uitgezochte Lay-out voor het Document van Verslag voor dat paneel als Lijst of Kolom. De velden in het deelvenster worden dienovereenkomstig ingedeeld in het document of record.

![Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records](assets/dortablelayout.png)

Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records

![Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records](assets/dorcolumnlayout.png)

Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records

## Document met recordinstellingen {#document-of-record-settings}

Met de instellingen voor Document of Record kunt u opties kiezen die u wilt opnemen in het Document of Record. Een bank accepteert bijvoorbeeld naam, leeftijd, socialezekerheidsnummer en telefoonnummer in een formulier. Het formulier genereert een bankrekeningnummer en filiaalgegevens. U kunt ervoor kiezen alleen de naam, het socialezekerheidsnummer, de bankrekening en de filiaalgegevens weer te geven in Document of Record.

De instelling van de component Document of Record is beschikbaar onder de eigenschappen. Als u de eigenschappen van een component wilt openen, selecteert u de component en klikt u op ![cmppr](assets/cmppr.png) in de overlay. De eigenschappen worden vermeld in de zijbalk en u kunt de volgende instellingen erin vinden.

**Instellingen op veldniveau**

* **Uitsluiten van document van record**: Als u de eigenschap true instelt, wordt het veld niet opgenomen in Document of Record. Dit is een scriptbare eigenschap met de naam `excludeFromDoR`. Het gedrag hangt af van **Velden uitsluiten van DoR indien verborgen** eigenschap op formulierniveau.

* **Deelvenster weergeven als tabel:** Als u de eigenschap instelt, wordt het deelvenster weergegeven als tabel in Document of Record als het deelvenster minder dan 6 velden bevat. Alleen van toepassing op het deelvenster.
* **Titel van record uitsluiten:** Als u de eigenschap instelt, wordt de titel van het deelvenster/de tabel uitgesloten van Document of Record. Alleen van toepassing op deelvenster en tabel.
* **Omschrijving uitsluiten van document van record:** Als u de eigenschap instelt, wordt de beschrijving van het deelvenster/de tabel niet opgenomen in Document of Record. Alleen van toepassing op deelvenster en tabel.

**Instellingen voor formulierniveau**

* **Inclusief niet-gebonden velden in DoR:** Als u de eigenschap instelt, worden niet-gebonden velden van op schema gebaseerde adaptieve vorm opgenomen in Document of Record. Standaard is dit waar.
* **Velden uitsluiten van DoR indien verborgen:** Stel de eigenschap in om de verborgen velden bij het verzenden van het formulier uit te sluiten van Document of Record. Wanneer u [Revalidate op server](/help/forms/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), worden de verborgen velden opnieuw berekend voordat deze worden uitgesloten van het Document of Record.

## Een aangepast XCI-bestand gebruiken

Met behulp van een XCI-bestand kunt u verschillende eigenschappen van een document instellen. Forms as a Cloud Service heeft een hoofd-XCI-bestand. U kunt een aangepast XCI-bestand gebruiken om een of meer standaardeigenschappen te overschrijven die in het hoofd-XCI-bestand zijn opgegeven. U kunt bijvoorbeeld een lettertype insluiten in een document of een gelabelde eigenschap inschakelen voor alle documenten. In de volgende tabel worden de XCI-opties aangegeven:

| XCI, optie | Beschrijving |
|--- |--- |
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Voor informatie over dit woordenboek raadpleegt u de [PDF Referentiehandleiding](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Voor informatie over dit woordenboek raadpleegt u de [PDF Referentiehandleiding](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
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
| config/present/pdf/linearized | Controls whether the output PDF document is linearized. |
| config/present/script/runScripts | Hiermee bepaalt u welke set scripts Forms as a Cloud Service uitvoert. |
| config/present/pdf/tagged | Controls the include of tags into the output PDF document. Codes, in de context van PDF, zijn aanvullende informatie die in een document is opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. |
| config/present/pdf/fontInfo/alwaysEmbed | Hiermee geeft u een lettertype op dat in het uitvoerdocument wordt ingesloten. |
| config/present/pdf/fontInfo/neverEmbed | Hiermee geeft u een lettertype op dat nooit in het uitvoerdocument mag worden ingesloten. |
| config/present/pdf/pdfa/part | Hier geeft u het versienummer op van de PDF/A-specificatie waarmee het document compatibel is. |
| config/present/pdf/pdfa/amd | Geeft het wijzigingsniveau van de specificatie PDF/A aan. |
| config/present/pdf/pdfa/conformance | Hiermee wordt het compatibiliteitsniveau opgegeven met de PDF/A-specificatie. |
| config/present/pdf/version | Hiermee wordt de versie van het te genereren PDF-document opgegeven |
| config/present/pdf/version/map | Geeft de terugvalfonts voor het document aan |

>[!NOTE]
>
> AEM Forms biedt diverse ingebouwde lettertypen die naadloos kunnen worden geïntegreerd met PDF-bestanden. De lijst met ondersteunde lettertypen weergeven [klik hier](/help/forms/supported-out-of-the-box-fonts.md).


### Een aangepast XCI-bestand gebruiken in uw Forms as a Cloud Service omgeving

1. Voeg het aangepaste XCI-bestand toe aan uw ontwikkelingsproject.
1. Geef het volgende op [inline, eigenschap](/help/implementing/deploying/configuring-osgi.md):

   ```JSON
    {
     "xciFilePath": "[path of XCI file]"
    }
   ```

   Bijvoorbeeld:

   ```JSON
    {
     "xciFilePath": "/content/dam/formsanddocuments/customMinionProBoldAndTagged.xci"
    }
   ```

1. Implementeer het project in de omgeving van uw Cloud Service.

### Een aangepast XCI-bestand gebruiken in uw lokale Forms as a Cloud Service-ontwikkelomgeving

1. Upload het XCI-bestand naar uw lokale ontwikkelomgeving.
1. Open Cloud Service SDK configuratiemanager. De standaard-URL is: <http://localhost:4502/system/console/configMgr>.
1. Zoek en open de **[!UICONTROL Adaptive Forms and Interactive Communication Web Channel]** configuratie.
1. Geef het pad van het XCI-bestand op en klik op **[!UICONTROL Save]**.


## Zie ook {#see-also}

{{see-also}}
