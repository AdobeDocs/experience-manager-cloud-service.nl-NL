---
title: Hoe te om een document van verslag (DoR) voor AEM Forms te produceren?
description: Leer een sjabloon te genereren voor een Document of Record (DoR) voor Adaptive Forms.
feature: Adaptive Forms, Foundation Components
exl-id: 16d07932-3308-4b62-8fa4-88c4e42ca7b6
role: User, Developer
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '4030'
ht-degree: 0%

---

# Document met record genereren voor adaptieve Forms

>[!NOTE]
>
> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

## Overzicht {#overview}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Deze record wordt een Document of Record (DoR) genoemd. Het is een afdrukvriendelijke kopie van het ingediende formulier. U kunt ook het document met records raadplegen voor de gegevens die klanten op een latere datum hebben ingevuld of het document met records gebruiken om formulieren en inhoud samen te archiveren in PDF-indeling.

![ Document van Verslag ](assets/document-of-record.png)

Als u een document met records wilt maken, wordt een op XFA of Acroform gebaseerde sjabloon samengevoegd met gegevens die via een adaptief formulier zijn verzameld. U kunt een Document van Verslag automatisch of op bestelling produceren.
Met de optie Op aanvraag kunt u een aangepaste op XFA of Acroform gebaseerde sjabloon opgeven voor een aangepaste weergave van uw Document of Record.

U kunt:

* [Een op XFA gebaseerd document met records genereren](#generate-an-XFA-based-document-of-record)
* [Een op Acrobat gebaseerd (Acrobat Form PDF) document met records genereren](#generate-an-Acroform-based-document-of-record)
* [Automatisch een document met records genereren](#auto-generate-a-document-of-record)

## Voordat u begint {#components-to-automatically-generate-a-document-of-record}

Voordat u leert welke elementen nodig zijn voor een Document of Record:

**malplaatje van de Basis:** Een malplaatje XFA (XDP dossier) dat in Forms Designer of een Vorm van Acrobat (AcroForm) wordt gecreeerd. [ het malplaatje van de Basis ](#base-template-of-a-document-of-record) wordt gebruikt om het stileren en het brandmerken informatie voor een Document van Verslag te specificeren. Upload uw XFA-sjabloon (XDP-bestand) naar uw AEM Forms-instantie voordat

**Aangepaste Vorm:** Een AanpassingsVorm waarvoor het Document van Verslag moet worden geproduceerd.

## Een op XFA gebaseerd document met records genereren {#generate-an-XFA-based-document-of-record}

Upload uw XFA-sjabloon (XDP-bestand) naar uw AEM Forms-instantie. Voer de volgende stappen uit om een adaptief formulier te configureren voor het gebruik van XFA-sjabloon (XDP-bestand) als sjabloon voor Document of Record:

1. Klik in de Experience Manager-auteurinstantie op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]** .
1. Selecteer **[!UICONTROL Form Model]** in het venster Eigenschappen.
1. Selecteer op het tabblad **[!UICONTROL Form Model]** in de vervolgkeuzelijst **[!UICONTROL Select From]** de optie **[!UICONTROL Schema]** of **[!UICONTROL None]** . U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. In het Document van de sectie van de Configuratie van het Malplaatje van het Verslag van het Model van de Vorm, uitgezochte **Vennoot het Malplaatje van de Vorm als Document van het Malplaatje van het Verslag**. Als u deze optie selecteert, worden alle XFA-sjablonen (XDP-bestanden) die op uw computer beschikbaar zijn, weergegeven. Selecteer het juiste bestand. Zorg er ook voor dat hetzelfde schema (gegevensschema) wordt gebruikt voor Adaptief formulier en geselecteerde XFA-sjabloon (XDP-bestand).
1. Klikken **[!UICONTROL Done]**

Het adaptieve formulier is nu geconfigureerd voor het gebruik van een XDP-bestand als sjabloon voor het document of record. De volgende stap moet [ de Aangepaste componenten van de Vorm met overeenkomstige malplaatjegebieden ](#bind-adaptive-form-components-with-template-fields) binden.

## Een op acroform gebaseerd document met records genereren {#generate-an-Acroform-based-document-of-record}

Upload uw Adobe Acrobat PDF (Acrobat) naar uw AEM Forms-exemplaar. Voer de volgende stappen uit om een adaptief formulier zo te configureren dat Adobe Acrobat PDF (Acrobat) wordt gebruikt als sjabloon voor Document of Record:

1. Klik in de Experience Manager-auteurinstantie op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]** .
1. Selecteer **[!UICONTROL Form Model]** in het venster Eigenschappen.
1. Selecteer op het tabblad **[!UICONTROL Form Model]** in de vervolgkeuzelijst **[!UICONTROL Select From]** de optie **[!UICONTROL Schema]** of **[!UICONTROL None]** . U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. In het Document van de sectie van de Configuratie van het Malplaatje van het Verslag van het Model van de Vorm, uitgezochte **Vennoot het Malplaatje van de Vorm als Document van het Malplaatje van het Verslag**. Als u deze optie selecteert, worden alle Acrobat PDF (Acrobat) die op uw computer beschikbaar zijn, weergegeven. Selecteer het juiste bestand.
1. Klikken **[!UICONTROL Done]**

Het adaptieve formulier is nu geconfigureerd voor het gebruik van een Acrobat-formulier als sjabloon voor het document met records. De volgende stap moet [ de Aangepaste componenten van de Vorm met overeenkomstige malplaatjegebieden ](#bind-adaptive-form-components-with-template-fields) binden.

## Automatisch een document met records genereren {#auto-generate-a-document-of-record}

Als een adaptief formulier is geconfigureerd om automatisch een Document of Record te genereren, wordt het document van Record van het formulier direct bijgewerkt telkens wanneer een formulier wordt gewijzigd. Als bijvoorbeeld een veld wordt verwijderd uit een bestaand adaptief formulier, wordt het bijbehorende veld ook verwijderd en is het niet zichtbaar in het Document of Record. Er zijn veel andere voordelen van het automatisch genereren van Document of Record. :

* Formulierontwikkelaars hoeven de gegevensbindingen niet handmatig bij te houden. Het automatisch gegenereerde document met records verzorgt updates met betrekking tot gegevensbinding.
* Formulierontwikkelaars hoeven velden die zijn gemarkeerd als niet opnemen in Document of Record, niet handmatig te verbergen. Automatisch gegenereerd document met record is vooraf geconfigureerd om dergelijke velden uit te sluiten.
* Met de optie Automatisch gegenereerd document van record bespaart u tijd die nodig is om een formuliersjabloon te maken voor Document of Record.
* Met de optie Automatisch gegenereerd document van record kunt u verschillende stijlen en weergaven gebruiken met verschillende basissjablonen. Het helpt de beste stijl en verschijning voor Document van Verslag voor uw organisatie selecteren. Als u geen stijlen opgeeft, worden systeemstijlen standaard ingesteld.
* Automatisch gegenereerd document van record zorgt ervoor dat elke wijziging in het formulier direct wordt weerspiegeld in het document van record.

Voer de volgende stappen uit om een adaptief formulier te configureren zodat automatisch een Document of Record wordt gegenereerd:

1. Klik in de Experience Manager-auteurinstantie op **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents].**
1. Selecteer een formulier en klik op **[!UICONTROL Properties]** .
1. Selecteer **[!UICONTROL Form Model]** in het venster Eigenschappen.
1. Selecteer op het tabblad **[!UICONTROL Form Model]** in de vervolgkeuzelijst **[!UICONTROL Select From]** de optie **[!UICONTROL Schema]** of **[!UICONTROL None]** . U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.
1. In het Document van de sectie van de Configuratie van het Malplaatje van het Verslag van het Model van de Vorm, uitgezocht **produceer Document van Verslag**.
1. Klikken **[!UICONTROL Done]**

## Aangepaste formuliercomponenten binden met sjabloonvelden {#bind-adaptive-form-components-with-template-fields}

Adaptief-formuliervelden binden met sjabloonvelden om vastgelegde formuliergegevens weer te geven in het corresponderende document van het recordveld. Aangepaste formuliercomponenten binden aan het corresponderende document met recordsjabloonvelden:

1. Open het adaptieve formulier, geconfigureerd om een aangepaste formuliersjabloon te gebruiken voor bewerken.

1. Selecteer een Adaptieve component van de Vorm en klik open vormen ![ ](assets/Smock_Wrench_18_N.svg) pictogram. De eigenschappenbrowser wordt geopend.

1. Blader in de eigenschappenbrowser naar een veld en selecteer dit.

   * (Voor de sjabloon AcroForm) de eigenschap **[!UICONTROL Document of Record Bind Reference field]** .
   * (Voor XFA-sjabloon) de eigenschap **[!UICONTROL Data Model Bind Reference]** .

1. Klik op **[!UICONTROL Save]**.

<!-- 
In the following video, Adaptive Form components are bound with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

U kunt Send E-mail, het Werkschema van Experience Manager gebruiken verzendt actie samen met [ Document van de stap van het Verslag, en andere voorlegt acties ](configuring-submit-actions.md) om een Document van Verslag te ontvangen.

## Incrementele updates van de sjabloon Document of Record {#document-of-record-template-incremental-updates}

Aangepaste formulieren en het bijbehorende document met recordsjablonen kunnen zich over een bepaalde periode ontwikkelen. U kunt velden toevoegen, verwijderen of wijzigen aan een adaptief formulier of een document met een recordsjabloon.

Wanneer u een Document of Record-sjabloon wijzigt en het gewijzigde Document of Record-sjabloon uploadt naar AEM Forms, detecteert de Adaptive Forms-editor automatisch de gewijzigde bindingen en wordt u geïnformeerd over de adaptieve formuliercomponenten die nieuwe bindingen vereisen. Hiermee kunt u incrementele updates uitvoeren voor een Document of Record-sjabloon.

Bijvoorbeeld, heeft een Organisatie, *We.Retail*, een AcroForm-Gebaseerd Document van het malplaatje van het Verslag, *wij-retail-factuur.pdf*. De sjabloon ziet er als volgt uit:

![ Origineel Malplaatje ](assets/we-retail-invoice.png)

Nadat de sjabloon enige tijd is gebruikt, besluit de organisatie het veld `invoice-number` te hernoemen naar het veld `bill-number` en het e-mailadres van kopers vast te leggen. Een ontwikkelaar werkt de naam van het veld `invoice-number` bij en voegt een e-mailveld aan de sjabloon toe. Hij leidt ook tot een nieuwe versie van malplaatje genoemd *wij-retail-factuur-v2.pdf*.

![ Bijgewerkt Malplaatje ](assets/we-retail-new-invoice.png)

De ontwikkelaar uploadt en past de bijgewerkte sjabloon toe op het adaptieve formulier. Het adaptieve formulier detecteert automatisch velden waarvan de binding is gewijzigd en geeft een lijst weer.

![ Bindende Fout ](assets/we-retail-binding-error.png)

De formulierontwikkelaar bindt adaptieve Forms-velden aan het overeenkomstige Document of Record-sjabloon.

>[!VIDEO](assets/we-retail-binding.mp4)

Wanneer het adaptieve formulier wordt verzonden, wordt nu een bijgewerkt document met recordgegevens gemaakt.

![ Bijgewerkt - ](assets/we-retail-new-invoice-sent-to-customer.png)

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
   <td>Deelvenster <br /> </td>
   <td>Subform<br /> </td>
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

Volg altijd [ de overeenkomsten van het malplaatje van de Basis ](#base-template-conventions) wanneer u basissjabloon ontwerpt.

## Basissjabloonconventies {#base-template-conventions}

Een basissjabloon wordt gebruikt om de kop-, voettekst-, opmaak- en vormgeving van een Document of Record te definiëren. De kop- en voettekst kunnen informatie bevatten zoals het bedrijfslogo en de copyrighttekst. De eerste basispagina in de basissjabloon wordt gekopieerd en gebruikt als een basispagina voor het Document of Record, die koptekst, voettekst, paginanummer of andere informatie bevat die op alle pagina&#39;s in het Document of Record moet worden weergegeven. Als u een basissjabloon gebruikt dat niet voldoet aan de conventies van de basissjabloon, wordt de eerste basispagina van de basissjabloon nog steeds gebruikt in de sjabloon Document of Record. U wordt ten zeerste aangeraden de basissjabloon te ontwerpen volgens de conventies en deze te gebruiken voor het automatisch genereren van een document met Record.

**Hoofdpaginaovereenkomsten**

* Geef het basissubformulier in de basissjabloon de naam `AF_METATEMPLATE` en de basispagina de naam `AF_MASTERPAGE` .

* De basispagina met de naam `AF_MASTERPAGE` die zich onder het `AF_METATEMPLATE` basissubformulier bevindt, heeft de voorkeur voor het uitnemen van koptekst-, voettekst- en opmaakgegevens.

* Als `AF_MASTERPAGE` niet aanwezig is, wordt de eerste basispagina in de basissjabloon gebruikt.

**het Stijlen overeenkomsten voor gebieden**

* Als u stijl wilt toepassen op de velden in het document of record, bevat de basissjabloon velden in het subformulier `AF_FIELDSSUBFORM` onder het `AF_METATEMPLATE` basissubformulier.

* De eigenschappen van deze velden worden toegepast op de velden in het Document of Record. Deze velden moeten de naamgevingsconventie `AF_<name of field in all caps>_XFO` volgen. De veldnaam voor het selectievakje moet bijvoorbeeld `AF_CHECKBOX_XFO` zijn.

Ga als volgt te werk in Forms Designer om een basissjabloon te maken.

1. Klik op **[!UICONTROL File]** > **[!UICONTROL New]** .
1. Selecteer de optie **[!UICONTROL Based on a template]** .

1. Selecteer de categorie **[!UICONTROL Forms - Document of Record]** .
1. Selecteer **[!UICONTROL DoR Base Template]** .
1. Klik op **[!UICONTROL Next]** en geef de vereiste informatie op.

1. (Optioneel) Wijzig de opmaak en weergave van de velden die u wilt toepassen op de velden in het Document of Record.
1. Sla het formulier op.

U kunt het opgeslagen formulier nu gebruiken als een basissjabloon voor Document of Record. Wijzig of verwijder geen scripts in de basissjabloon.

**wijzigend basissjabloon**

* Als u geen opmaak toepast op velden in de basissjabloon, is het aan te raden deze velden uit de basissjabloon te verwijderen, zodat alle upgrades naar de basissjabloon automatisch worden opgepakt.
* Verwijder scripts niet tijdens het wijzigen van een basissjabloon, voeg ze toe of wijzig ze niet.

Volg nauwgezet bovenstaande conventies en instructies om een basissjabloon te ontwerpen.

## De brandinggegevens aanpassen in Document of Record {#customize-the-branding-information-in-document-of-record}

Tijdens het genereren van een Document of Record kunt u de brandinggegevens voor het Document of Record wijzigen op het tabblad Document of Record. Het tabblad Document of Record bevat opties zoals logo, weergave, lay-out, koptekst en voettekst, disclaimer en of u niet het selectievakje en keuzerondjes wilt inschakelen of niet.

Als u de brandinggegevens die u opgeeft op het tabblad Document of Record wilt lokaliseren, moet u controleren of de landinstelling van de browser correct is ingesteld. Voer de volgende stappen uit om de brandinggegevens van Document of Record aan te passen:

1. Selecteer een paneel (wortelpaneel) in het Document van Verslag en selecteer dan ![ vormen ](assets/configure.png).
1. Selecteer ![ dortab ](assets/dortab.png). Het tabblad Document of Record wordt weergegeven.
1. Selecteer de standaardsjabloon of een aangepaste sjabloon voor het weergeven van het Document of Record. Als u de standaardsjabloon selecteert, wordt een miniatuurvoorvertoning van het Document of Record weergegeven onder de vervolgkeuzelijst Sjabloon.
1. Afhankelijk van het feit of u een standaardsjabloon of een aangepaste sjabloon selecteert, worden enkele van de volgende eigenschappen of alle eigenschappen weergegeven op het tabblad Document of Record. Geef de onderstaande eigenschappen op om de weergave van het Document of Record te definiëren:

   1. **BasisEigenschappen**:
      * **Malplaatje**: Als u verkiest om een douanemalplaatje te selecteren, doorblader uitgezocht XDP op uw [!DNL AEM Forms] server. Als u een sjabloon wilt gebruiken die zich nog niet op uw [!DNL AEM Forms] -server bevindt, moet u de XDP eerst naar uw [!DNL AEM Forms] -server uploaden.
      * **de Kleur van de Actie**: De kleur waarin de kopbaltekst en de separatorlijnen in het document of verslag PDF worden teruggegeven.
      * **Familie van de Doopvont**: Familie van de doopvont van de tekst in het Document van Verslag PDF.

        >[!NOTE]
        >
        > AEM Forms biedt diverse ingebouwde lettertypen die naadloos kunnen worden geïntegreerd met PDF-bestanden. Om de lijst van gesteunde doopvonten te zien, [ klik hier ](/help/forms/supported-out-of-the-box-fonts.md).

      * **omvat vormvoorwerpen die niet aan gegevensmodel** verbindend zijn: Het plaatsen van het bezit omvat ongebonden gebieden van Schema gebaseerde AanpassingsVorm in Document van Verslag.
      * **sluit verborgen gebieden van het Document van Verslag** uit: Het plaatsen van het bezit identificeert de verborgen gebieden voor uitsluiting van Document van Verslag.
      * **Verberg beschrijving van panelen**: Het plaatsen van het bezit sluit beschrijving van het paneel/de lijst van Document van Verslag uit. Van toepassing op paneel en lijst.

      ![ Basiseigenschappen ](/help/forms/assets/basicpropertiesdor.png)

   2. **Eigenschappen van het Gebied van de Vorm**:
      * **voor de componenten van de Doos van de Controle en van de Keuzerondje, toon slechts de geselecteerde waarden**: Het plaatsen van het bezit toont slechts geselecteerde waarden van controledoos en radioknoop in [!UICONTROL Document of Record].
      * **Scheidingsteken voor veelvoudige waarde(s)**: U kunt om het even welk separator zoals komma of lijnonderbreking kiezen om veelvoudige waarden te tonen.
      * **Uitlijning van Opties**: U kunt de gewenste uitlijning (Horizontaal, Verticaal, Zelfde als Aangepast Vorm) selecteren om de groepering voor de gebieden zoals controledoos of radioknoop te plaatsen om op [!UICONTROL Document of Record] worden getoond. Standaard wordt de verticale uitlijning ingesteld voor de velden in [!UICONTROL Document of Record] . Als u de eigenschappen van de [!UICONTROL Form Field Properties] van DoR instelt, worden de eigenschappen overschreven die zijn ingesteld in [!UICONTROL Item Alignment] voor de velden op een adaptief formulier. Als u de optie [!UICONTROL Same as Aaptive form] selecteert, wordt de uitlijning zoals geconfigureerd in een instantie van de auteur van een adaptief formulier gebruikt voor [!UICONTROL Document of Record] -velden.
      * **Aantal opties voor horizontale groepering**:U kunt het aantal opties plaatsen dat op het Document van Verslag voor de horizontale groepering moet worden getoond.

      ![ Eigenschappen van het Gebied van de Vorm ](/help/forms/assets/formfieldpropertiesdor.png)

   3. **Hoofdpagina Eigenschappen**:
      * **Beeld van het Logo**: U kunt of verkiezen om het logobeeld van de Aangepaste Vorm te gebruiken, één van DAM te kiezen, of één van uw computer te uploaden.
      * **Titel van de Vorm**: Titel van DoR.
      * **Tekst van de Kopbal**: Tekst die bij de kopbalsectie van het Document van Verslag verschijnt.
      * **Etiket van de Disclaimer**: Etiket van ontkenning.
      * **Disclaimer**: Tekst die het werkingsgebied van rechten en verplichtingen op het Document van Verslag specificeert.
      * **Tekst van de Disclaimer**: Tekst van ontkenning.

      ![ Hoofdpagina Eigenschappen ](/help/forms/assets/masterpagepropertiesdor.png)

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

1. Selecteer **[!UICONTROL Done]** om de wijzigingen in de branding op te slaan.

## Document met ondersteuning voor records in de Adaptive Form Editor {#dor-support-in-adaptiveform}

U kunt de sjabloon [!UICONTROL Document of Record] rechtstreeks configureren vanuit de editor voor Adaptieve formulieren of de sjablooneditor voor Adaptieve formulieren.

Voer de volgende stappen uit vanuit de auteur-instantie van de Adaptieve formuliereditor:

1. Selecteer de component **[!UICONTROL Adaptive Form container (Root)]** .
1. Klik ![ vormen pictogram van het Pictogram ](/help/forms/assets/configure-icon.svg) om **[!UICONTROL Properties]** van de Aangepaste container van de Vorm te openen.
1. Open het tabblad **[!UICONTROL Document of Record Template]** en selecteer een van de volgende opties:
   * **[!UICONTROL None]**: Als deze optie is geselecteerd, wordt er geen [!UICONTROL Document of Record] -sjabloon gemaakt voor uw adaptieve formulier.

   * **[!UICONTROL Associate Form Template as Document of Record Template]**:Als deze optie is geselecteerd, wordt XFA-formulier gebruikt als sjabloon voor Document of Record.

   * **[!UICONTROL Generate Document of Record]**: Als deze optie is geselecteerd, wordt de sjabloon [!UICONTROL Document of Record] automatisch gegenereerd voor uw adaptieve formulier.

1. Selecteer ![ sparen ](/help/forms/assets/check-button.png) om de eigenschappen te bewaren.

![ Document van de Steun van het Malplaatje van het Verslag ](/help/forms/assets/dor-templatesupport.png)

>[!NOTE]
>
>Als u [!UICONTROL Document of Record] -sjabloon maakt met een adaptieve formuliersjablooneditor, zijn slechts twee opties beschikbaar onder [!UICONTROL Document of Record Template] tab as [!UICONTROL None] en [!UICONTROL Generate Document of Record] .

## Tabel- en kolomindelingen voor deelvensters in document van record {#table-and-column-layouts-for-panels-in-document-of-record}

Het adaptieve formulier kan lang zijn en meerdere formuliervelden bevatten. U kunt een Document van Verslag niet als nauwkeurige exemplaar van het AanpassingsFormulier willen bewaren. U kunt nu een tabel- of kolomindeling kiezen om een of meer deelvensters voor adaptieve formulieren op te slaan in het document van Record PDF.

Alvorens een Document van Verslag te produceren, in de montages van een paneel, uitgezochte Lay-out voor het Document van Verslag voor dat paneel als Lijst of Kolom. De velden in het deelvenster worden dienovereenkomstig ingedeeld in het document of record.

![ Gebieden in een paneel dat in een lijstlay-out in het Document van Verslag ](assets/dortablelayout.png) wordt teruggegeven

Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records

![ Gebieden in een paneel dat in een kolomlay-out in het Document van Verslag ](assets/dorcolumnlayout.png) wordt teruggegeven

Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records

## Document met recordinstellingen {#document-of-record-settings}

Met de instellingen voor Document of Record kunt u opties kiezen die u wilt opnemen in het Document of Record. Een bank accepteert bijvoorbeeld naam, leeftijd, socialezekerheidsnummer en telefoonnummer in een formulier. Het formulier genereert een bankrekeningnummer en filiaalgegevens. U kunt ervoor kiezen alleen de naam, het socialezekerheidsnummer, de bankrekening en de filiaalgegevens weer te geven in Document of Record.

De instelling van de component Document of Record is beschikbaar onder de eigenschappen. Om tot de eigenschappen toegang te hebben een component, selecteer de component en klik ![ cmp ](assets/cmppr.png) in de bekleding. De eigenschappen worden vermeld in de zijbalk en u kunt de volgende instellingen erin vinden.

**het niveaumontages van het Gebied**

* **sluit van Document van Verslag** uit: Het plaatsen van het bezit waar sluit het gebied van Document van Verslag uit. Dit is een scripteigenschap met de naam `excludeFromDoR` . Zijn gedrag hangt van **gebieden van DoR uit als verborgen** bezit van het vormniveau.

* **het paneel van de Vertoning als lijst:** plaatsend het paneel van bezitsvertoningen als lijst in Document van Verslag als het paneel minder dan 6 gebieden in het heeft. Alleen van toepassing op het deelvenster.
* **sluit titel van Document van Verslag uit:** het plaatsen van het bezit sluit titel van het paneel/de lijst van Document van Verslag uit. Alleen van toepassing op deelvenster en tabel.
* **sluit beschrijving van Document van Verslag uit:** het plaatsen van het bezit sluit beschrijving van het paneel/de lijst van Document van Verslag uit. Alleen van toepassing op deelvenster en tabel.

**het niveau van de Vorm montages**

* **omvat niet verbindende gebieden in DoR:** het plaatsen van het bezit omvat ongebonden gebieden van Schema gebaseerd Aangepast Vorm in Document van Verslag. Standaard is dit waar.
* **sluit gebieden van DoR uit als verborgen:** plaats het bezit om de verborgen gebieden van Document van Verslag bij vormvoorlegging uit te sluiten. Wanneer u [ toelaat verwerk op server ](/help/forms/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), hercompileert de server de verborgen gebieden alvorens die gebieden van het Document van Verslag uit te sluiten.

## Een aangepast XCI-bestand gebruiken

Met behulp van een XCI-bestand kunt u verschillende eigenschappen van een document instellen. Forms as a Cloud Service heeft een hoofd-XCI-bestand. U kunt een aangepast XCI-bestand gebruiken om een of meer standaardeigenschappen te overschrijven die in het hoofd-XCI-bestand zijn opgegeven. U kunt bijvoorbeeld een lettertype insluiten in een document of een gelabelde eigenschap inschakelen voor alle documenten. In de volgende tabel worden de XCI-opties aangegeven:

| XCI, optie | Beschrijving |
|--- |--- |
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Voor informatie over dit woordenboek, zie de [ gids van de Verwijzing van PDF ](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Voor informatie over dit woordenboek, zie de [ gids van de Verwijzing van PDF ](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
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
| config/present/script/exclude | Hiermee wordt Forms as a Cloud Service geïnformeerd welke gebeurtenissen moeten worden genegeerd. |
| config/present/pdf/linearized | Bepaalt of het PDF-uitvoerdocument lineair is. |
| config/present/script/runScripts | Hiermee bepaalt u welke set scripts Forms as a Cloud Service uitvoert. |
| config/present/pdf/tagged | Hiermee bepaalt u de opname van codes in het PDF-uitvoerdocument. In de context van PDF zijn codes aanvullende informatie die in een document wordt opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. |
| config/present/pdf/fontInfo/alwaysEmbed | Hiermee geeft u een lettertype op dat in het uitvoerdocument wordt ingesloten. |
| config/present/pdf/fontInfo/neverEmbed | Hiermee geeft u een lettertype op dat nooit in het uitvoerdocument mag worden ingesloten. |
| config/present/pdf/pdfa/part | Hiermee wordt het versienummer opgegeven van de PDF/A-specificatie waarmee het document compatibel is. |
| config/present/pdf/pdfa/amd | Geeft het wijzigingsniveau van de specificatie PDF/A aan. |
| config/present/pdf/pdfa/conformance | Geeft het compatibiliteitsniveau aan met de PDF/A-specificatie. |
| config/present/pdf/version | Hiermee wordt de versie van het PDF-document opgegeven die moet worden gegenereerd |
| config/present/pdf/version/map | Geeft de terugvalfonts voor het document aan |

>[!NOTE]
>
> AEM Forms biedt diverse ingebouwde lettertypen die naadloos kunnen worden geïntegreerd met PDF-bestanden. Om de lijst van gesteunde doopvonten te zien, [ klik hier ](/help/forms/supported-out-of-the-box-fonts.md).


### Een aangepast XCI-bestand gebruiken in uw Forms as a Cloud Service-omgeving

1. Voeg het aangepaste XCI-bestand toe aan uw ontwikkelingsproject.
1. Specificeer het volgende [ gealigneerde bezit ](/help/implementing/deploying/configuring-osgi.md):

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

1. Implementeer het project in uw Cloud Service-omgeving.

### Een aangepast XCI-bestand gebruiken in uw lokale Forms as a Cloud Service-ontwikkelomgeving

1. Upload het XCI-bestand naar uw lokale ontwikkelomgeving.
1. Open Cloud Service SDK Configuration Manager. De standaard-URL is: <http://localhost:4502/system/console/configMgr>.
1. Zoek en open de **[!UICONTROL Adaptive Forms and Interactive Communication Web Channel]** -configuratie.
1. Geef het pad van het XCI-bestand op en klik op **[!UICONTROL Save]** .


## Zie ook {#see-also}

{{see-also}}
