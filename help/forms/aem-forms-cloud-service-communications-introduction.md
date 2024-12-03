---
title: Wat zijn Forms as a Cloud Service Communication API's?
description: Gebruik communicatie-API's om uw documenten te ondertekenen, certificeren of beveiligen, om processen voor het genereren van PDF te automatiseren en om PDF-documenten om te zetten in een andere indeling.
Keywords: How to generate document?, Generate PDF document, Manipulation PDF documents, Assembling PDF documents, Validating PDF document, APIs used in encrypting or decrypting PDFs.
feature: Adaptive Forms, APIs & Integrations
role: Admin, Developer, User
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 13c1febf55c9b15eab49d356fc1ba3f3d91ad055
workflow-type: tm+mt
source-wordcount: '2365'
ht-degree: 1%

---

# AEM Forms as a Cloud Service communicatie-API&#39;s {#frequently-asked-questions}

![ Hero Beeld ](assets/cloud-communication-apis-hero-image.jpeg)


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html) |
| AEM as a Cloud Service | Dit artikel |

Met communicatiemogelijkheden kunt u documenten maken die door uw merk zijn goedgekeurd, gepersonaliseerd en gestandaardiseerd, zoals zakelijke correspondentie, instructies, aanvraagverwerkingsbrieven, aankondigingen van voordelen, maandelijkse facturen of welkomstkits.

De mogelijkheid biedt API&#39;s om de documenten te genereren en te bewerken. U kunt een document op verzoek genereren of bewerken of een batchtaak maken om meerdere documenten met gedefinieerde intervallen te genereren. Communicatie-API&#39;s bieden:

* gestroomlijnde mogelijkheden voor het genereren van documentatie op aanvraag en batchverwerking.

* de mogelijkheid om PDF-documenten op aanvraag te combineren, opnieuw te rangschikken en te valideren.

* HTTP-API&#39;s voor eenvoudigere integratie met externe systemen. Afzonderlijke API&#39;s voor bewerkingen op aanvraag (lage latentie) en batchbewerkingen (bewerkingen met hoge doorvoer) worden opgenomen.

* een veilige toegang tot gegevens. Communicatie APIs verbindt met en heeft toegang tot gegevens slechts van klant-aangewezen gegevensbewaarplaatsen, die mededelingen hoogst veilig maken.

De [ API verwijzingsdocumentatie ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/) verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en diverse diensten die door APIs worden verleend. De API-naslagdocumentatie is ook beschikbaar in de indeling .yaml. U kunt de .yaml downloaden en uploaden naar Postman om de functionaliteit van de API&#39;s te controleren.


<!-- 
![A sample credit card statement](assets/statement.png)
A credit card statement can be created using Communications APIs. This sample statement uses same template but separate data for each customer depending on their usage of credit card.

-->

## Document genereren

Via API&#39;s voor het genereren van communicatiedocumenten kunt u een sjabloon (XFA of PDF) combineren met klantgegevens (XML) om documenten te genereren in de indelingen PDF en Afdrukken, zoals de indelingen PS, PCL, DPL, IPL en ZPL. Deze APIs gebruikt PDF en malplaatjes XFA met [ gegevens van XML ](communications-known-issues-limitations.md#form-data) om één enkel document op bestelling of veelvoudige documenten te produceren die een partijbaan gebruiken.

Typisch, creeert u een malplaatje gebruikend [ Designer ](use-forms-designer.md) en gebruikt Mededelingen APIs om gegevens met het malplaatje samen te voegen. Uw toepassing kan het uitvoerdocument naar een netwerkprinter, een lokale printer of een opslagsysteem verzenden voor archivering. Een typisch uit de doos en de douanewerkschema&#39;s kijken als het volgende:

![ Communicatie Werkschema van de documentgeneratie ](assets/communicaions-workflow.png)

Afhankelijk van het gebruiksgeval kunt u deze documenten ook beschikbaar stellen voor downloaden via uw website of een opslagserver.

Voorbeelden van API&#39;s voor het genereren van documenten zijn:

### PDF-documenten maken {#create-pdf-documents}

Met de API&#39;s voor het genereren van documenten kunt u een PDF-document maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens. De uitvoer is een niet-interactief PDF-document. Met andere woorden, gebruikers kunnen de formuliergegevens niet invoeren of wijzigen. Een basisworkflow is het samenvoegen van XML-formuliergegevens met een formulierontwerp om een PDF-document te maken. In de volgende afbeelding ziet u hoe een formulierontwerp en XML-formuliergegevens worden samengevoegd om een PDF-document te maken.

![ creeer PDF documenten ](assets/outPutPDF_popup.png)
Afbeelding: Standaardworkflow voor het maken van een PDF-document

### PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL)-document maken {#create-PS-PCL-ZPL-documents}

U kunt API&#39;s voor het genereren van documenten gebruiken om een PostScript-document (PS), een PCL-document (Printer Command Language) en een ZPL-document (Zebra Printing Language) te maken dat is gebaseerd op een XDP-formulierontwerp of een PDF-document. Deze API&#39;s helpen u bij het samenvoegen van een formulierontwerp met formuliergegevens om een document te genereren. U kunt het document opslaan in een bestand en een aangepast proces ontwikkelen om het naar een printer te verzenden.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all the records.

The following illustration shows Communications APIs processing an XML data file that con tains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### Batchgegevens verwerken om meerdere documenten te maken {#processing-batch-data-to-create-multiple-documents}

Met API&#39;s voor het genereren van documenten kunt u afzonderlijke documenten maken voor elke record in een XML-batchgegevensbron. U kunt documenten bulksgewijs en asynchroon genereren. U kunt diverse parameters voor de omzetting vormen en dan het partijproces beginnen.

![ creeer de Documenten van PDF ](assets/ou_OutputBatchMany_popup.png)

<!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. 

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use document generation APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document's fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form. -->

## Documentmanipulatie

Met API&#39;s voor het manipuleren van communicatiedocumenten (Document Transformation) kunt u PDF-documenten combineren en opnieuw rangschikken. Doorgaans maakt u een DDX en verzendt u deze naar API&#39;s voor documentmanipulatie om een document samen te stellen of opnieuw te rangschikken. Het [ DDX- document ](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) verstrekt instructies op hoe te om de brondocumenten te gebruiken om een reeks vereiste documenten te veroorzaken. De DDX-referentiedocumentatie biedt gedetailleerde informatie over alle ondersteunde bewerkingen. Voorbeelden van documentmanipulatie zijn:

### PDF-documenten samenstellen

Met de API&#39;s voor documentmanipulatie kunt u twee of meer PDF- of XDP-documenten samenvoegen tot één PDF-document of PDF-Portfolio. Hier volgen enkele voorbeelden van manieren waarop u PDF-documenten kunt samenstellen:

* Een eenvoudig PDF-document samenstellen
* Een PDF-Portfolio maken
* Gecodeerde documenten samenstellen
* Documenten samenstellen met Bates-nummering
* Documenten samenvoegen en samenvoegen

![ samenstellend een eenvoudig document van PDF van veelvoudige documenten van PDF ](assets/as_document_assembly.png)
Afbeelding: Een eenvoudig PDF-document samenstellen op basis van meerdere PDF-documenten

### PDF-documenten demonteren

U kunt de API&#39;s voor documentmanipulatie gebruiken om een PDF-document te demonteren. De API&#39;s kunnen pagina&#39;s uitnemen uit het brondocument of een brondocument splitsen op basis van bladwijzers. Deze taak is meestal handig als het PDF-document oorspronkelijk is gemaakt op basis van veel afzonderlijke documenten, zoals een verzameling instructies.

* Pagina&#39;s uit een brondocument extraheren
* Een brondocument splitsen op basis van bladwijzers

![ het Verdelen van een brondocument dat op referenties in veelvoudige documenten wordt gebaseerd ](assets/as_intro_pdfsfrombookmarks.png)
Afbeelding: Een brondocument dat is gebaseerd op bladwijzers, opsplitsen in meerdere documenten

>[!NOTE]
>
> AEM Forms biedt diverse ingebouwde lettertypen die naadloos kunnen worden geïntegreerd met PDF-bestanden. Om de lijst van gesteunde doopvonten te zien, [ klik hier ](/help/forms/supported-out-of-the-box-fonts.md).

<!-- 

## Document utilities

Document utilities synchronous APIs helps you convert documents between PDF and XDP file formats, and query information about a PDF document. For example, you can determine whether a PDF document contains comments or attachments.

### Retrieve PDF document properties

You can [query a PDF document](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/pdf-utility-sync/#tag/Document-Extraction/) for the following information:

* Is a PDF Document: Check whether the source document is a PDF document.
* Is a fillable form: Check whether the source PDF document is a fillable form.
* Form Type: Retrieve the form type of the document.
* Check for Attachments: Check whether the source PDF document has any attachments.
* Check for Comments: Check whether the source PDF document has any review comments.
* Is a PDF Package: Check whether the document is a PDF package.
* Get the PDF Version: Retrieve the [version of the PDF document](https://en.wikipedia.org/wiki/History_of_PDF).
* Recommended Acrobat Version: Retrieve the required version of Acrobat (Reader) to open the PDF document.
* Is an XFA Document: Check whether the source PDF document is an XFA-based PDF document.
* Is Shell PDF: Check whether the source PDF document is shell PDF. A shell PDF contains only an XFA stream, font and image resources, and one page that is either blank or contains a warning that the document must be opened using Acrobat or Adobe Reader. The shell PDF is used with PDF transformation to optimize delivery of PDFForm transformations only.
* Get the XFA Version: Retrieve the [XFA Version for an XFA-based PDF document](https://en.wikipedia.org/wiki/XFA#XFA_versions).

### Convert PDF Documents into XDP Documents

The [PDF to XDP API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/pdf-utility-sync/#tag/Document-Conversion) converts a PDF document to an XDP file. For a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the dictionary. -->

## Document uitnemen

<span class="preview"> De functie voor het uitnemen van documenten valt onder het programma voor vroegtijdige adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Met de service Documentextractie kunt u de eigenschappen van een PDF-document ophalen, zoals gebruiksrechten, PDF-eigenschappen en metagegevens. De mogelijkheden voor het uitnemen van documenten zijn:

* Hiermee worden de eigenschappen van een PDF-document opgehaald, bijvoorbeeld als de PDF bijlagen, opmerkingen, de Acrobat-versie en nog veel meer bevat.
* Haal de gebruiksrechten uit die in een PDF-document zijn ingeschakeld, gebruikers halen de gebruiksrechten op die zijn in- of uitgeschakeld voor Adobe Acrobat Reader-uitbreidbaarheid naar een PDF-document.
* Haal de metagegevens op die aanwezig zijn in een PDF-document. De metagegevens zijn gegevens over het document (die verschillen van de inhoud van het document, zoals tekst en afbeeldingen). Het Adobe Extensible Metadata Platform (XMP) is een standaard voor de verwerking van documentmetagegevens. Met de XMP Utilities kunt u XMP metagegevens ophalen uit PDF-documenten en XMP metagegevens exporteren naar PDF-documenten.

De [ API verwijzingsdocumentatie ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/) verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en de diensten die door APIs worden verleend. De API-naslagdocumentatie is ook beschikbaar in de indeling .yaml. U kunt de .yaml downloaden en uploaden naar Postman om de functionaliteit van API&#39;s te controleren.

<!--

<span class="preview"> The XMP Utilities Service capability is under Early Adopter Program. You can write to aem-forms-ea@adobe.com from your official email id to join the early adopter program and request access to the capability. </span>

### XMP Utilities {#XMP-utilities}

<span class="preview"> The XMP Utilities Service capability is under Early Adopter Program. You can write to aem-forms-ea@adobe.com from your official email id to join the early adopter program and request access to the capability. </span>

PDF documents contain metadata, which is information about the document (as distinguished from the contents of the document, such as text and graphics). The Adobe Extensible Metadata Platform (XMP) is a standard for handling document metadata. The XMP Utilities service can retrieve and save XMP metadata from PDF documents and import XMP metadata into PDF documents.

-->

## Documentconversie

### Converteren naar en valideren van documenten die voldoen aan PDF/A

Via API&#39;s voor documentconversie kunt u een PDF-document converteren naar PDF/A. U kunt de API&#39;s gebruiken om een PDF-document te converteren naar een document dat voldoet aan de PDF/A-standaard en ook om te bepalen of een PDF-document voldoet aan de PDF/A-standaard. PDF/A is een archiefindeling die is bedoeld voor het op lange termijn bewaren van de inhoud van het document. De lettertypen worden ingesloten in het document en het bestand wordt niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud. De ondersteunde PDF/A-compatibiliteitsnormen omvatten PDF/A-1a, 1b, 2a, 2b, 3a en 3b.

### PDF omzetten in XDP {#convert-pdf-to-xdp}

<span class="preview"> De functie PDF omzetten in XDP valt onder het programma Vroege adopter. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Zet een PDF-document om in een XDP-bestand. Een PDF-document kan alleen met succes worden geconverteerd naar een XDP-bestand als het PDF-document een XFA-stroom bevat in het woordenboek.

## Document Assurance {#doc-assurance}

De DocAssurance-service bevat de API&#39;s voor handtekening en versleuteling:

### Handtekening-API&#39;s

Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. <!--This service uses digital signatures and certification to ensure that only intended recipients can alter documents. --> De beveiligingsfuncties worden toegepast op het document zelf. Het document blijft gedurende de gehele levenscyclus beveiligd en beheerd. Het document blijft beveiligd buiten de firewall, wanneer het offline wordt gedownload en wanneer het wordt teruggestuurd naar uw organisatie. U kunt de volgende taken uitvoeren met de handtekening-API&#39;s:

* Voeg een zichtbaar handtekeningveld toe aan een PDF-document.
* Voeg een onzichtbaar handtekeningveld toe aan een PDF-document.
* Onderteken het opgegeven handtekeningveld in een PDF-document.
* Een PDF-document certificeren
* De handtekening verwijderen uit het opgegeven handtekeningveld in een PDF-document
* Het opgegeven handtekeningveld uit een PDF-document verwijderen

<span class="preview"> Verwijder de handtekening uit het opgegeven handtekeningveld en verwijder het opgegeven handtekeningveld uit een PDF-document dat beschikbaar is in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>


<!--

### Remove Signature APIs

The Remove Signature API helps to remove an existing digital signatures from a PDF document. This API is useful when you need to update or revise a signed document and reapply signatures. It maintains document integrity while effectively clearing signatures from specific pages or the entire file. Use cases include re-signing documents with updated data or clearing previous approvals for revised versions.


### Remove Signature Field APIs

The Remove Signature Field API is tailored for removing signature fields from a PDF document. This is ideal when you need to delete empty or unused signature fields to streamline document presentation. It enables users to eliminate signature fields without impacting other form fields or the document structure, making it easier to create cleaner, final versions of a document that no longer require signatures.

-->

### Coderings-API&#39;s

Met de API&#39;s voor versleuteling kunt u documenten versleutelen en ontsleutelen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord voor openen opgeven voordat het document in Adobe Reader of Adobe Acrobat kan worden weergegeven. <!-- Likewise, if a PDF document is encrypted with a certificate, the user must decrypt the PDF document with the public key that corresponds to the certificate (private key) that was used to encrypt the PDF document.-->

U kunt deze taken uitvoeren met de API&#39;s voor codering:

* Codeer een PDF-document met een wachtwoord.
* Verwijder op wachtwoord gebaseerde versleuteling uit een PDF-document.
* Hiermee haalt u het type beveiliging op dat op een PDF-document is toegepast.
* Retourneer het beveiligingstype dat op een PDF-document is toegepast.

Zowel handtekening APIs als encryptie APIs zijn [ Synchrone APIs ](#types-of-communications-apis-types).


### Documenthulpprogramma {#doc-utility}

Met behulp van documenthulpprogramma&#39;s met synchrone API&#39;s kunt u documenten omzetten tussen PDF- en XDP-bestandsindelingen. Pas gebruiksrechten toe op een document en extraheer de ingeschakelde gebruiksrechten uit een document. Vraag informatie over een document van PDF. <!-- determines whether a PDF document contains comments or attachments and more, and use document transformation services for XMP utilities--> Meer informatie over de gebruiksrechten-API&#39;s vindt u hieronder:


#### Gebruiksrechten-API&#39;s (extensie Reader)

<span class="preview"> De mogelijkheid Gebruiksrechten (extensie Reader) valt onder het programma Vroege adopter. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Met de functie Gebruiksrechten kan uw organisatie eenvoudig interactieve PDF-documenten delen door de functionaliteit van Adobe Reader uit te breiden met extra gebruiksrechten. De service werkt met Adobe Reader 7.0 of hoger en voegt gebruiksrechten toe aan een PDF-document. Met deze actie activeert u functies die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document.

Wanneer voor PDF-documenten de juiste gebruiksrechten zijn toegevoegd, kunnen ontvangers de volgende activiteiten uitvoeren vanuit Adobe Reader:

* Voltooi PDF-documenten en -formulieren online of offline, zodat ontvangers kopieën lokaal kunnen opslaan voor hun records en de toegevoegde gegevens intact kunnen houden.
* Sla PDF-documenten op een lokale vaste schijf op om het originele document en eventuele aanvullende opmerkingen, gegevens of bijlagen te behouden.
* Bestanden en mediaclips aan PDF-documenten koppelen.
* Onderteken, certificeer en authenticeer PDF-documenten door digitale handtekeningen toe te passen met PKI-technologieën (Public Key Infrastructure) die industriestandaard zijn.
* Ingevulde of geannoteerde PDF documenten elektronisch verzenden.
* Gebruik PDF-documenten en -formulieren als intuïtieve ontwikkelvoorkant van interne databases en webservices.
* Deel PDF-documenten met anderen, zodat revisoren opmerkingen kunnen toevoegen met intuïtieve opmaakgereedschappen. Deze gereedschappen zijn onder andere elektronische notities, stempels, hooglichten en doorhalen van tekst. Dezelfde functies zijn beschikbaar in Acrobat.
* Ondersteuning voor gestreepte Forms-decodering.

Deze mogelijkheden voor speciale gebruiksrechten worden automatisch geactiveerd wanneer een PDF-document met ingeschakelde rechten wordt geopend in Adobe Reader. Wanneer de gebruiker klaar is met het werken met een document waarvoor rechten zijn ingeschakeld, worden deze functies weer uitgeschakeld in Adobe Reader. Ze blijven uitgeschakeld totdat de gebruiker een ander PDF-document met ingeschakelde rechten ontvangt.

#### Gebruiksrechten in- of uitschakelen

De verschillende mogelijkheden van gebruiksrechten voor het uitbreiden van de diensten van de Reader van de PDF zijn:

* **Decodering van Streepjescodes**: Om streepjescodes binnen het document van de PDF te decoderen.

* **Commentaren**: Om off-line op het document van de PDF commentaar te geven.

* **Online Commentaren**: Om online op het document van de PDF commentaar te geven.

* **Digitale Handtekening**: Om digitale handtekeningen aan een document van de PDF toe te voegen.

* **Dynamische Gebieden van de Vorm**: Om vormgebieden aan een document van de PDF toe te voegen.

* **Dynamische Pagina&#39;s van de Vorm**: Om vormpagina&#39;s aan een document van de PDF toe te voegen.

* **Ingebedde Dossiers**: Om dossiers binnen een document van PDF in te bedden.

* **de Invoer van de Gegevens van de Vorm**: Om vormgegevens in een document van de PDF in te voeren.

* **de Uitvoer van de Gegevens van de Vorm**: Om vormgegevens in een document van de PDF in te voeren.

* **Vulling van de Vorm**: Om vormgebieden binnen een document van de PDF te vullen.

* **Online Forms**: Om tot een Webdienst of gegevensbestand van een document van PDF toegang te hebben.

* **legt Zelfstandig** voor: Om formuliergegevens off-line van een document van PDF voor te leggen.


#### Andere mogelijkheden

* **Bericht**: Het bericht dat binnen Adobe Acrobat Reader wordt getoond bij het openen van een document van de PDF met één of meerdere toegepaste gebruiksrechten.
* **Ontgrendel Wachtwoord**: Het wachtwoord dat voor het openen van een gecodeerd document van PDF wordt vereist. Dit is doorgaans het wachtwoord voor het openen van het document, maar als het PDF-document extra wordt beveiligd door een wachtwoord voor machtigingen, kan een van beide worden gebruikt om het document te openen.

## Typen communicatie-API&#39;s {#types}

Communicatie biedt HTTP-API&#39;s voor het genereren van documenten op aanvraag en in batches:

* **[Synchrone APIs ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)** zijn geschikt voor op bestelling, lage latentie, en enige scenario&#39;s van de verslagdocumentgeneratie. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op handelingen van gebruikers. Als u bijvoorbeeld een document genereert nadat een gebruiker een formulier heeft ingevuld.

* **[Partij APIs (Asynchrone APIs) ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)** is geschikt voor geplande, hoge productie, en veelvoudige scenario&#39;s van de documentgeneratie. Met deze API&#39;s worden documenten batchgewijs gegenereerd. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

## Onboarding

Communicatiecapaciteit is beschikbaar als zelfstandige en add-on module voor Forms as a Cloud Service gebruikers. U kunt contact opnemen met het verkoopteam van de Adobe of uw Adobe om toegang aan te vragen. Adobe maakt toegang voor uw organisatie mogelijk en biedt de vereiste rechten aan de persoon die is aangewezen als beheerder in uw organisatie. De beheerder kan toegang verlenen aan uw Forms as a Cloud Service ontwikkelaars (gebruikers) van uw organisatie om APIs te gebruiken.

Na het instappen, om Communicatie vermogen voor uw as a Cloud Service milieu van Forms toe te laten:

1. Meld u aan bij Cloud Manager en open AEM Forms as a Cloud Service Instance.

1. Open de optie Programma bewerken, ga naar het tabblad Oplossingen en invoegtoepassingen en selecteer de optie **[!UICONTROL Forms - Communications]** .

   ![ Mededelingen ](assets/communications.png)

   Als u de optie **[!UICONTROL Forms - Digital Enrollment]** al hebt ingeschakeld, selecteert u de optie **[!UICONTROL Forms - Communications Add-On]** .

   ![ Addon ](assets/add-on.png)

1. Klik op **[!UICONTROL Update]**.

1. Stel de bouwstijlpijpleiding in werking. Nadat de bouwstijlpijpleiding slaagt, Communicatie APIs wordt toegelaten voor uw milieu.

>[!NOTE]
>
> Om documentmanipulatie APIs toe te laten en te vormen, voeg de volgende regel aan de [ configuratie van Dispatcher ](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) toe:
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

<!--

Communication help you combine a template and XML data to generate print documents in various formats. The service lets you generate documents in synchronous and batch modes. The APIs enables you to create applications that let you:

  * Generate documents by populating template files (PDF and XDP) with XML data.
  * Generate output forms in various formats, including non-interactive PDF print streams.

Consider a scenario where you have one or more templates and multiple records of XML data for each template. You can use Communications APIs to generate a print document for each record.  You can also combine the records into a single document.  The result is a non-interactive PDF document. A non-interactive PDF document does not let users enter data into its fields.

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as REST endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example, ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document.  

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

You can use Communications APIs to create PostScript (PS), Printer Command Language (PCL), and Zebra Printing Language (ZPL) document that are based on an XDP form design or PDF document. The _generatePrintedOutput_ API merges a form design with form data to generate a document. You can save the document to a file and develop a custom process to send it to a printer.

 ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

### Processing batch data to create multiple documents {#processing-batch-data-to-create-multiple-documents}

You create separate documents for each record within an XML batch data source. You can can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents.

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents.

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use the Communications APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document's fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form.  -->

## Zie ook {#see-also}

* [Communicatieverwerking - synchrone API&#39;s](/help/forms/aem-forms-cloud-service-communications.md)
* [Communicatieverwerking - Batch-API&#39;s](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
* [AEM Forms as a Cloud Service architectuur voor adaptieve Forms- en communicatie-API&#39;s](/help/forms/aem-forms-cloud-service-architecture.md)
