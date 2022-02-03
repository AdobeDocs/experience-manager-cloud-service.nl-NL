---
title: Een inleiding tot as a Cloud Service communicatie in Forms
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: a6b6a190a59d1c2f0001fe1f28d8d7bc8353d464
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 1%

---

# AEM Forms as a Cloud Service communicatie gebruiken {#frequently-asked-questions}

**Documentmanipulatie-API&#39;s bevinden zich in de pre-releasefase en kunnen worden gewijzigd voordat ze daadwerkelijk worden uitgebracht.**

Met communicatiemogelijkheden kunt u documenten maken die door uw merk zijn goedgekeurd, gepersonaliseerd en gestandaardiseerd, zoals zakelijke correspondentie, instructies, aanvraagverwerkingsbrieven, aankondigingen van voordelen, maandelijkse facturen of welkomstkits.

De mogelijkheid biedt API&#39;s om de documenten te genereren en te bewerken. U kunt een document op verzoek genereren of bewerken of een batchtaak maken om meerdere documenten met gedefinieerde intervallen te genereren. Communicatie-API&#39;s bieden:

* gestroomlijnde mogelijkheden voor het genereren van documentatie op aanvraag en batchverwerking.

* de mogelijkheid om PDF-documenten op aanvraag te combineren, opnieuw te rangschikken en te valideren.

* HTTP-API&#39;s voor eenvoudigere integratie met externe systemen. Afzonderlijke API&#39;s voor bewerkingen op aanvraag (lage latentie) en batchbewerkingen (bewerkingen met hoge doorvoer) worden opgenomen.

* een veilige toegang tot gegevens. Communicatie APIs verbindt met en heeft toegang tot gegevens slechts van klant aangewezen gegevensbewaarplaatsen, die mededelingen hoogst veilig maken.

![Een voorbeeld van een creditcardformulier](assets/statement.png)
Een creditcardverklaring kan worden gecreeerd gebruikend Communicatie APIs. Deze voorbeeldinstructie gebruikt dezelfde sjabloon maar afzonderlijke gegevens voor elke klant, afhankelijk van het gebruik van de creditcard.

## Documentgeneratie

Via API&#39;s voor het genereren van communicatiedocumenten kunt u een sjabloon (XFA of PDF) combineren met klantgegevens ([XML-gegevens](#form-data)) om documenten te genereren in de indelingen PDF en Afdrukken, zoals PS, PCL, DPL, IPL en ZPL. Deze API&#39;s gebruiken [PDF- en XFA-sjablonen](#supported-document-types) with [XML-gegevens](communications-known-issues-limitations.md#form-data) om één document op bestelling of meerdere documenten te produceren die een partijbaan gebruiken.

Doorgaans maakt u een sjabloon met [Designer](use-forms-designer.md) en gebruik Communicatie APIs om gegevens met het malplaatje samen te voegen. Uw toepassing kan het uitvoerdocument naar een netwerkprinter, een lokale printer of een opslagsysteem verzenden voor archivering. Een typisch uit de doos en de douanewerkschema&#39;s kijken als het volgende:

![Workflow voor het genereren van communicatiedocumenten](assets/communicaions-workflow.png)

Afhankelijk van het gebruiksgeval kunt u deze documenten ook beschikbaar stellen voor downloaden via uw website of een opslagserver.

Voorbeelden van API&#39;s voor het genereren van documenten zijn:

### PDF-documenten maken {#create-pdf-documents}

Met de API&#39;s voor het genereren van documenten kunt u een PDF-document maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens. De uitvoer is een niet-interactief PDF-document. Met andere woorden, gebruikers kunnen de formuliergegevens niet invoeren of wijzigen. Een basisworkflow is het samenvoegen van XML-formuliergegevens met een formulierontwerp om een PDF-document te maken. In de volgende afbeelding ziet u hoe een formulierontwerp en XML-formuliergegevens worden samengevoegd om een PDF-document te maken.

![PDF-documenten maken](assets/outPutPDF_popup.png)
Afbeelding: Standaardworkflow voor het maken van een PDF-document

### PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL)-document maken {#create-PS-PCL-ZPL-documents}

Met API&#39;s voor het genereren van documenten kunt u PostScript- (PS), PCL-documenten (Printer Command Language) en ZPL-documenten (Zebra Printing Language) maken die zijn gebaseerd op een XDP-formulierontwerp of PDF-document. Deze API&#39;s helpen u bij het samenvoegen van een formulierontwerp met formuliergegevens om een document te genereren. U kunt het document opslaan in een bestand en een aangepast proces ontwikkelen om het naar een printer te verzenden.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that con tains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### Batchgegevens verwerken om meerdere documenten te maken {#processing-batch-data-to-create-multiple-documents}

Met API&#39;s voor het genereren van documenten kunt u afzonderlijke documenten maken voor elke record in een XML-batchgegevensbron. U kunt documenten bulksgewijs en asynchroon genereren. U kunt diverse parameters voor de omzetting vormen en dan het partijproces beginnen.

![PDF-documenten maken](assets/ou_OutputBatchMany_popup.png)

<!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. 

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use document generation APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form. -->


## (Pre-release) Documentmanipulatie

Via API&#39;s voor documentmanipulatie kunt u PDF-documenten combineren, opnieuw rangschikken en valideren. Doorgaans maakt u een DDX en verzendt u deze naar API&#39;s voor documentmanipulatie om een document samen te stellen of opnieuw te rangschikken. Het DDX-document bevat instructies voor het gebruik van de brondocumenten om een set vereiste documenten te maken. De DDX-referentiedocumentatie biedt gedetailleerde informatie over alle ondersteunde bewerkingen. Voorbeelden van documentmanipulatie zijn:

### PDF-documenten samenstellen

Met de API&#39;s voor documentproductie kunt u twee of meer PDF- of XDP-documenten samenvoegen tot één PDF-document of PDF Portfolio. Hier volgen enkele voorbeelden van manieren waarop u PDF-documenten kunt samenstellen:

* Een eenvoudig PDF-document samenstellen
* Een PDF-Portfolio maken
* Gecodeerde documenten samenstellen
* Documenten samenstellen met Bates-nummering
* Documenten samenvoegen en samenvoegen

![Een eenvoudig PDF-document samenstellen op basis van meerdere PDF-documenten](assets/as_document_assembly.png)
Afbeelding: Een eenvoudig PDF-document samenstellen op basis van meerdere PDF-documenten

### PDF-documenten demonteren

U kunt de API&#39;s voor documenthandleiding gebruiken om een PDF-document te demonteren. De API&#39;s kunnen pagina&#39;s uitnemen uit het brondocument of een brondocument splitsen op basis van bladwijzers. Deze taak is meestal handig als het PDF-document oorspronkelijk is gemaakt op basis van veel afzonderlijke documenten, zoals een verzameling instructies.

* Pagina&#39;s uit een brondocument extraheren
* Een brondocument splitsen op basis van bladwijzers

![Een brondocument dat is gebaseerd op bladwijzers, opsplitsen in meerdere documenten](assets/as_intro_pdfsfrombookmarks.png)
Afbeelding: Een brondocument dat is gebaseerd op bladwijzers, opsplitsen in meerdere documenten

### Converteren naar documenten die voldoen aan de PDF/A-standaard en deze valideren

Met de API&#39;s voor documentproductie kunt u een PDF-document converteren naar een document dat voldoet aan de PDF/A-standaard en bepalen of een PDF PDF/A-compatibel is. PDF/A is een archiefindeling die is bedoeld voor het op lange termijn bewaren van de inhoud van het document. De lettertypen worden ingesloten in het document en het bestand wordt niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud.

>[!NOTE]
>
> Als u API&#39;s voor documentmanipulatie wilt inschakelen en configureren, voegt u de volgende regel toe aan [Dispatcher-configuratie](setup-local-development-environment.md#forms-specific-rules-to-dispatcher):
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`


## Typen communicatie-API&#39;s

Communicatie biedt HTTP-API&#39;s voor het genereren van documenten op aanvraag en in batches:

* **[Synchrone API&#39;s](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/)** zijn geschikt voor on-demand, lage latentie en scenario&#39;s voor het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op gebruikersacties. Als u bijvoorbeeld een document genereert nadat een gebruiker een formulier heeft ingevuld.

* **[Batch-API&#39;s (Asynchrone API&#39;s)](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/)** zijn geschikt voor geplande, hoge productie, en veelvoudige scenario&#39;s van de documentgeneratie. Deze API&#39;s genereren documenten batchgewijs. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

## Onboarding

Communicatiecapaciteit is beschikbaar als zelfstandige en add-on module voor as a Cloud Service Forms-gebruikers. U kunt contact opnemen met het verkoopteam van Adobe of uw Adobe om toegang aan te vragen. Adobe maakt toegang voor uw organisatie mogelijk en biedt de vereiste rechten aan de persoon die is aangewezen als beheerder in uw organisatie. De beheerder kan toegang verlenen aan uw as a Cloud Service Forms-ontwikkelaars (gebruikers) van uw organisatie om de API&#39;s te gebruiken.

Na het instappen, om Communicatie vermogen voor uw as a Cloud Service milieu van Forms toe te laten:

1. Meld u aan bij Cloud Manager en open de as a Cloud Service AEM Forms-instantie.

1. Open de optie Programma bewerken, ga naar het tabblad Oplossingen en invoegtoepassingen en selecteer de optie **[!UICONTROL Forms - Communications]** optie.

   ![Communicatie](assets/communications.png)

   Als u al **[!UICONTROL Forms - Digital Enrollment]** en selecteert u vervolgens de optie **[!UICONTROL Forms - Communications Add-On]** optie.

   ![Addon](assets/add-on.png)

1. Klik op **[!UICONTROL Update]**.

1. Stel de bouwstijlpijpleiding in werking. Nadat de bouwstijlpijpleiding slaagt, Communicatie APIs wordt toegelaten voor uw milieu.


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
