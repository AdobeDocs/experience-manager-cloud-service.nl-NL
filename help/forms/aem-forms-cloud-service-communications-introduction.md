---
title: Een inleiding tot as a Cloud Service communicatie in Forms
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 1%

---

# AEM Forms as a Cloud Service gebruiken * Communicatie {#frequently-asked-questions}

**AEM Forms as a Cloud Service * Communicatie eigenschap is in bèta.**

Met communicatiemogelijkheden kunt u merkgeoriënteerde, gepersonaliseerde en gestandaardiseerde documenten maken, zoals zakelijke correspondentie, instructies, aanvraagverwerkingsbrieven, voordeelberichten, maandelijkse facturen of welkomstkits.


U kunt een document op verzoek genereren of een batchtaak maken om meerdere documenten met gedefinieerde intervallen te genereren. Communicatie-API&#39;s bieden:

* gestroomlijnde mogelijkheden voor het genereren van documentatie op aanvraag en batchverwerking

* HTTP-API&#39;s bieden om de integratie met bestaande systemen te vergemakkelijken

* een veilige toegang tot gegevens. Communicatie APIs verbindt met en heeft toegang tot gegevens slechts van klant aangewezen gegevensbewaarplaatsen, maakt geen lokale exemplaren van gegevens, die mededelingen hoogst veilig maken.

* afzonderlijke API&#39;s voor bewerkingen met lage latentie en hoge doorvoer, waardoor het genereren van documenten een efficiënte taak wordt.

![Een voorbeeld van een creditcardformulier](assets/statement.png)

## Hoe werkt het?

Communicatiegebruik [PDF- en XFA-sjablonen](#supported-document-types) with [XML-gegevens](#form-data) om één document op bestelling of veelvoudige documenten te produceren gebruikend een partijbaan bij bepaalde interval.

Met behulp van een communicatie-API kunt u een sjabloon (XFA of PDF) combineren met klantgegevens ([XML-gegevens](#form-data)) om documenten te genereren in de indelingen PDF en Afdrukken, zoals PS, PCL, DPL, IPL en ZPL.

Doorgaans maakt u een sjabloon met Designer en gebruikt u communicatie-API&#39;s om gegevens samen te voegen met de sjabloon. Uw toepassing kan het uitvoerdocument naar een netwerkprinter, een lokale printer of een opslagsysteem verzenden voor archivering. Een typisch uit de doos en de douanewerkschema&#39;s kijken als het volgende:

![Communicatieworkflow](assets/communicaions-workflow.png)

Afhankelijk van het gebruiksgeval kunt u deze documenten ook beschikbaar stellen voor downloaden via uw website of een opslagserver.

## Communicatie-API&#39;s

Communicatie biedt HTTP-API&#39;s voor het genereren van documenten op aanvraag en in batches:

* **Synchrone API&#39;s** zijn geschikt voor on-demand, lage latentie en scenario&#39;s voor het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op gebruikersacties. Als u bijvoorbeeld een document genereert nadat een gebruiker een formulier heeft ingevuld.

* **Batch-API&#39;s (Asynchrone API&#39;s)** zijn geschikt voor geplande, hoge productie, en veelvoudige scenario&#39;s van de documentgeneratie. Deze API&#39;s genereren documenten batchgewijs. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

## Onboarding

De mededelingen zijn beschikbaar als standalone en toe:voegen-op module voor as a Cloud Service gebruiker van Forms. U kunt contact opnemen met het verkoopteam van Adobe of uw Adobe om toegang aan te vragen.

Adobe maakt toegang voor uw organisatie mogelijk en biedt de vereiste rechten aan de persoon die is aangewezen als beheerder in uw organisatie. De beheerder kan toegang verlenen aan uw AEM Forms-ontwikkelaars (gebruikers) van uw organisatie om de API&#39;s te gebruiken.

<!--

Communication help you combine a template and XML data to generate print documents in various formats. The service allows you to generate documents in synchronous and batch modes. The APIs enables you to create applications that let you:

  * Generate documents by populating template files (PDF and XDP) with XML data.
  * Generate output forms in various formats, including non-interactive PDF print streams.

Consider a scenario where you have one or more templates and multiple records of XML data for each template. You can use Communications APIs to generate a print document for each record.  You can also combine the records into a single document.  The result is a non-interactive PDF document. A non-interactive PDF document does not let users enter data into its fields.

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as REST endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document.  

The [API reference documentation](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) provides detailed information about all the parameters, authentication methods, and various services provided by APIs. The API reference documentation is also available in the .yaml format. You can download the .yaml for [Batch APIs](assets/batch-api.yaml) or [non-Batch API.yaml](assets/non-batch-api.yaml) file and upload it to postman to check functionality of APIs.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Uploading Communication APIs .yaml file to postman to check functionality of APIs.

## Using the Communications APIs {#workflows}

Typically, you create a template using [Designer](use-forms-designer.md) and use communications APIs ( generatePDFOutput and generatePrintedOutput) to:

* Convert these templates to various formats, including PDF, PostScript, ZPL, and PCL.
* Merge XML form data with a form design to generate a document.
* Generate a document without merging XML form data into the document. However, the primary workflow is merging data into the document.

Then, the output document is stored to a file. You can design custom workflows to send the file to a network printer, a local printer, or to a storage system for archival. A typical out of the box and custom workflows look like the following:

![Communications Workflow](assets/communicaions-workflow.png)

### Create PDF documents {#create-pdf-documents}

You can use the _generatePDFOutput_ API to create PDF document that is based on a form design and XML form data. The output is a non-interactive PDF document. That is, users cannot enter or modify form data. A basic workflow is to merge XML form data with a form design to create a PDF document. The following illustration shows the merging of a form design and XML form data to produce a PDF document.

![Create PDF Documents](assets/outPutPDF_popup.png)

### Create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) document {#create-PS-PCL-ZPL-documents}

You can use Communications APIs to create PostScript (PS), Printer Command Language (PCL), and Zebra Printing Language (ZPL) document that are based on a XDP form design or PDF document. The _generatePrintedOutput_ API merges a form design with form data to generate a document. You can save the document to a file and develop a custom process to send it to a printer.

 ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.



### Processing batch data to create multiple documents {#processing-batch-data-to-create-multiple-documents}

You create separate documents for each record within an XML batch data source. You can can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents.

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents.

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use the Communications APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form.  -->

## Overwegingen {#considerations-for-communications-apis}

Voordat u begint met het genereren van documenten met communicatie-API&#39;s, moet u het volgende in overweging nemen:

### Formuliergegevens {#form-data}

Communicatie-API&#39;s accepteren een formulierontwerp dat gewoonlijk in Designer en XML-formuliergegevens wordt gemaakt als invoer. Als u een document wilt vullen met gegevens, moet de XML-formuliergegevens een XML-element bevatten voor elk formulierveld dat u wilt vullen. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven. De belangrijkste factor is dat de XML-elementen met de overeenkomende waarden worden opgegeven.

Bekijk het volgende voorbeeld van een aanvraagformulier voor een lening:

![Toepassingsformulier laden](assets/loanFormData.png)

Als u gegevens wilt samenvoegen in dit formulierontwerp, maakt u een XML-gegevensbron die overeenkomt met het formulier. De volgende XML vertegenwoordigt een XML-gegevensbron die overeenkomt met het voorbeeld van een hypotheektoepassingsformulier.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
* <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
* <xfa:data>
* <data>
    * <Layer>
        <closeDate>1/26/2007</closeDate>
        <lastName>Johnson</lastName>
        <firstName>Jerry</firstName>
        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
        <city>New York</city>
        <zipCode>00501</zipCode>
        <state>NY</state>
        <dateBirth>26/08/1973</dateBirth>
        <middleInitials>D</middleInitials>
        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
        <phoneNumber>5555550000</phoneNumber>
    </Layer>
    * <Mortgage>
        <mortgageAmount>295000.00</mortgageAmount>
        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
        <purchasePrice>300000</purchasePrice>
        <downPayment>5000</downPayment>
        <term>25</term>
        <interestRate>5.00</interestRate>
    </Mortgage>
</data>
</xfa:data>
</xfa:datasets>
```

### Ondersteunde documenttypen {#supported-document-types}

Voor volledige toegang tot de renderingmogelijkheden van de communicatie-API&#39;s wordt aanbevolen een XDP-bestand als invoer te gebruiken. Soms kan een PDF-bestand worden gebruikt. Het gebruik van een PDF-bestand als invoer heeft echter de volgende beperkingen:

Een PDF-document dat geen XFA-stream bevat, kan niet worden gerenderd als PostScript, PCL of ZPL. Communicatie-API&#39;s kunnen PDF-documenten met XFA-streams (dat wil zeggen formulieren die zijn gemaakt in Designer) weergeven in laser- en labelindelingen. Als het PDF-document is ondertekend, gecertificeerd of gebruiksrechten bevat (toegepast met de AEM Forms Reader Extensions-service), kan het niet worden gerenderd naar deze afdrukindelingen.

&lt;!-* * Uitvoeropties zoals PDF-versie en gecodeerde PDF worden niet ondersteund voor Acrobat-formulieren. Ze zijn geldig voor PDF forms die XFA-streams bevatten. deze formulieren kunnen echter niet worden ondertekend of gecertificeerd.

### E-mailondersteuning {#email-support}

Voor e-mailfunctionaliteit kunt u een proces in de Workflows van de Experience Manager maken dat de E-mailstap gebruikt. Een workflow vertegenwoordigt een bedrijfsproces dat u automatiseert. —>

### Afdrukbare gebieden {#printable-areas}

De standaard niet-afdrukbare marge van 0,25 inch is niet exact voor labelprinters en varieert van printer tot printer en van labelgrootte tot labelgrootte. Het wordt aanbevolen de marge van 0,25 inch te behouden of te verlagen. U wordt echter aangeraden de niet-afdrukbare marge niet te verhogen. Anders wordt de informatie in het afdrukbare gebied niet correct afgedrukt.

Zorg altijd dat u het juiste XDC-bestand voor de printer gebruikt. Vermijd bijvoorbeeld het kiezen van een XDC-bestand voor een 300 dpi-printer en het verzenden van het document naar een 200 dpi-printer.

### Scripts {#scripts}

Een formulierontwerp dat wordt gebruikt met de communicatie-API&#39;s kan scripts bevatten die op de server worden uitgevoerd. Zorg ervoor dat een formulierontwerp geen scripts bevat die op de client worden uitgevoerd. Zie Help bij Designer voor informatie over het maken van scripts voor formulierontwerp.

&lt;!-* ##### Werken met overwegingen voor lettertypedocument voor het werken met lettertypen>> —>

### Lettertypetoewijzing {#font-mapping}

Als u een formulier wilt ontwerpen waarin printerresidente lettertypen worden gebruikt, kiest u een lettertypenaam in Designer die overeenkomt met de lettertypen die beschikbaar zijn op de printer. Een lijst met lettertypen die worden ondersteund voor PCL of PostScript vindt u in de bijbehorende apparaatprofielen (XDC-bestanden). U kunt ook lettertypetoewijzing maken om niet-printerresidente lettertypen toe te wijzen aan printerresidente lettertypen met een andere lettertypenaam. In een PostScript-scenario kunnen verwijzingen naar het lettertype Arial® bijvoorbeeld worden toegewezen aan het printerresidente Helvetica®-lettertype.

Als een lettertype op een clientcomputer is geïnstalleerd, is het beschikbaar in de vervolgkeuzelijst in Designer. Als het lettertype niet is geïnstalleerd, moet u de lettertypenaam handmatig opgeven. De optie Niet-beschikbare lettertypen permanent vervangen in Designer kan zijn uitgeschakeld. Anders wordt de naam van het vervangende font geschreven naar het XDP-bestand wanneer het XDP-bestand wordt opgeslagen in Designer. Dit betekent dat het printerresidente lettertype niet wordt gebruikt.

Er zijn twee typen OpenType®-lettertypen. Eén type is een TrueType OpenType®-font dat door PCL wordt ondersteund. Het andere is CFF OpenType®. PDF- en PostScript-uitvoer ondersteunen ingesloten Type-1-, TrueType- en OpenType®-lettertypen. PCL-uitvoer ondersteunt ingesloten TrueType-fonts.

Type-1- en OpenType®-lettertypen worden niet ingesloten in PCL-uitvoer. Inhoud die is opgemaakt met Type-1- en OpenType®-lettertypen wordt gerasterd en gegenereerd als een bitmapafbeelding die groot en langzamer kan zijn om te genereren.

Gedownloade of ingesloten lettertypen worden automatisch vervangen bij het genereren van PostScript-, PCL- of PDF-uitvoer. Dit betekent dat alleen de subset van de lettertypeglyphs die vereist zijn om het gegenereerde document correct weer te geven, in de gegenereerde uitvoer wordt opgenomen.

### Werken met apparaatprofielbestanden (XDC-bestand) {#working-with-xdc-files}

Een apparaatprofiel (XDC-bestand) is een printerbeschrijvingsbestand in XML-indeling. Met dit bestand kunnen de communicatie-API&#39;s documenten uitvoeren als laser- of labelprinterindelingen. Communicatie-API&#39;s gebruiken de XDC-bestanden, waaronder de volgende:

* hppcl5c.xdc

* hppcl5e.xdc

* ps_plain_level3.xdc

* ps_plain.xdc

* zpl300.xdc

* zpl600.xdc

* zpl300.xdc

* ipl300.xdc

* ipl400.xdc

* tpcl600.xdc

* dpl300.xdc

* dpl406.xdc

* dpl600.xdc

U kunt de meegeleverde XDC-bestanden gebruiken om afdrukdocumenten te genereren of deze naar wens aan te passen.
&lt;!-* Het is niet nodig deze bestanden te wijzigen om documenten te maken. Nochtans, kunt u hen wijzigen om aan uw bedrijfsvereisten te voldoen. —>

Deze bestanden zijn referentie-XDC-bestanden die de functies van specifieke printers ondersteunen, zoals residente lettertypen, papierladen en nietmachines. Het doel van deze verwijzing is om u te helpen begrijpen hoe u uw eigen printers kunt instellen met apparaatprofielen. De verwijzing is ook een uitgangspunt voor gelijkaardige printers in de zelfde productlijn.

### Werken met het XCI-configuratiebestand {#working-with-xci-files}

Communicatie APIs gebruikt een XCI configuratiedossier om taken uit te voeren, zoals het controleren of de output één enkel paneel of gepagineerd is. Hoewel dit bestand instellingen bevat die kunnen worden ingesteld, is het niet standaard om deze waarde te wijzigen. &lt;!-* Het bestand default.xci bevindt zich in de map svcdata\XMLFormService. —>

U kunt een gewijzigd XCI-bestand doorgeven terwijl u een communicatie-API gebruikt. Als u dit doet, maakt u een kopie van het standaardbestand, wijzigt u alleen de waarden die moeten worden gewijzigd om aan uw bedrijfsvereisten te voldoen en gebruikt u het aangepaste XCI-bestand.

Communicatie-API&#39;s beginnen met het standaard-XCI-bestand (of het gewijzigde bestand). Vervolgens worden waarden toegepast die zijn opgegeven met de communicatie-API&#39;s. Deze waarden overschrijven XCI-instellingen.

In de volgende tabel worden XCI-opties opgegeven.

| XCI, optie | Beschrijving | | —* | —* | | config/present/pdf/creator | Identificeert de maker van het document met behulp van het item Maker in het documentinformatiewoordenboek. Zie de handleiding PDF Reference voor informatie over dit woordenboek.                                                                                                                                                                                                                                                                                                                                         | | config/present/pdf/producer | Identificeert de documentproducent met behulp van het Producent-item in het documentinformatiewoordenboek. Zie de handleiding PDF Reference voor informatie over dit woordenboek.                                                                                                                                                                                                                                                                                                                                       | | config/present/layout | Hiermee bepaalt u of de uitvoer één venster is of gepagineerd.                                                                                                                                                                                                                                                                                                                                                                                                                                                 | | config/present/pdf/compression/level | Hiermee geeft u de mate van compressie op die moet worden gebruikt bij het genereren van een PDF-document.                                                                                                                                                                                                                                                                                                                                                                                                                                  | | config/present/pdf/scriptModel | Hiermee wordt bepaald of XFA-specifieke informatie wordt opgenomen in het PDF-uitvoerdocument.                                                                                                                                                                                                                                                                                                                                                                                                                           | | config/present/common/data/adjustData | Hiermee bepaalt u of de XFA-toepassing de gegevens na het samenvoegen aanpast.                                                                                                                                                                                                                                                                                                                                                                                                                                        | | config/present/pdf/renderPolicy | Bepaalt of het genereren van pagina-inhoud op de server wordt uitgevoerd of uitgesteld aan de client.                                                                                                                                                                                                                                                                                                                                                                                                            | | config/present/common/locale | Geeft de standaardlandinstelling aan die in het uitvoerdocument wordt gebruikt.                                                                                                                                                                                                                                                                                                                                                                                                                                                   | | config/present/destination | Wanneer het element een huidig element bevat, geeft dit de uitvoerindeling op. Wanneer deze zich in een element openAction bevindt, geeft dit de handeling op die moet worden uitgevoerd wanneer het document wordt geopend in een interactieve client.                                                                                                                                                                                                                                                                                                              | | config/present/output/type | Hiermee geeft u het type compressie op dat u wilt toepassen op een bestand of het type uitvoer dat u wilt maken.                                                                                                                                                                                                                                                                                                                                                                                                               | | config/present/common/temp/uri | Hier geeft u de URI van het formulier op.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | | config/present/common/template/base | Hiermee wordt een basislocatie voor URI&#39;s in het formulierontwerp opgegeven. Wanneer dit element ontbreekt of leeg is, wordt de locatie van het formulierontwerp als basis gebruikt.                                                                                                                                                                                                                                                                                                                                                            | | config/present/common/log/to | Hiermee bepaalt u de locatie waarnaar loggegevens of uitvoergegevens worden geschreven.                                                                                                                                                                                                                                                                                                                                                                                                                                           | | config/present/output/to | Hiermee bepaalt u de locatie waarnaar loggegevens of uitvoergegevens worden geschreven.                                                                                                                                                                                                                                                                                                                                                                                                                                           | | config/present/script/currentPage | Hiermee geeft u de eerste pagina op wanneer het document wordt geopend.                                                                                                                                                                                                                                                                                                                                                                                                                                                     | | config/present/script/exclude | Informeert de AEM Forms API&#39;s voor server/communicatie welke gebeurtenissen moeten worden genegeerd.                                                                                                                                                                                                                                                                                                                                                                                                                                     | | config/present/pdf/linearied | Hiermee wordt bepaald of het PDF-uitvoerdocument lineair is.                                                                                                                                                                                                                                                                                                                                                                                                                                                     | | config/present/script/runScripts | Hiermee bepaalt u welke set scripts AEM Forms uitvoert.                                                                                                                                                                                                                                                                                                                                                                                                                                                           | | config/present/pdf/tagged | Hiermee regelt u het opnemen van codes in het PDF-uitvoerdocument. Codes, in de context van PDF, zijn aanvullende informatie die in een document is opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. | | config/present/pdf/version | Hiermee geeft u de versie op van het PDF-document dat moet worden gegenereerd.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
