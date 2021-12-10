---
title: AEM Forms as a Cloud Service - Communicatie
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '2369'
ht-degree: 0%

---


# AEM Forms as a Cloud Service communicatie-API&#39;s gebruiken {#frequently-asked-questions}

**De functie Communicatie is in bèta.**

Via communicatie-API&#39;s kunt u XDP-sjablonen, op XDP gebaseerde PDF-documenten en Acrobat Forms (AcroForm) combineren met XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren en u in staat te stellen toepassingen te maken waarmee u:

- Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.

- Formulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

- Afdruk-PDF genereren op basis van XFA-formulier-PDF.

- Genereer bulksgewijs PDF-, PostScript-, PCL- en ZPL-documenten door meerdere gegevenssets samen te voegen met bronsjablonen.

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt. U kunt communicatie-API&#39;s gebruiken om een afdrukdocument te genereren voor elke record. <!-- You can also combine the records into a single document. --> Het resultaat is een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de desbetreffende velden.

De [API-naslagdocumentatie](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) biedt gedetailleerde informatie over alle API&#39;s, parameters, verificatiemethoden en diverse services die door API&#39;s worden geleverd. De API-naslagdocumentatie is ook beschikbaar in de indeling .yaml. U kunt de .yaml downloaden voor [Batch-API&#39;s](assets/batch-api.yaml) of [niet-batchAPI.yaml](assets/non-batch-api.yaml) bestand maken en uploaden naar postman om de functionaliteit van API&#39;s te controleren.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Communicatie APIs .yaml dossier aan postman uploaden om functionaliteit van APIs te controleren.

>[!NOTE]
>
>Alleen leden van een groep met formuliergebruikers hebben toegang tot communicatie-API&#39;s.

## Communicatie inschakelen

Communicatie voor uw as a Cloud Service Forms-omgeving inschakelen:

1. Meld u aan bij Cloud Manager en open de as a Cloud Service AEM Forms-instantie.

1. Open de optie Programma bewerken, ga naar het tabblad Oplossingen en invoegtoepassingen en selecteer de optie **[!UICONTROL Forms - Communications]** optie.

   <!-- ![Communications](assets\communications.png)

    If you have already enabled the **[!UICONTROL Forms - Digital Enrollment]** option, then select the **[!UICONTROL Forms - Communications Add-On]** option.  

    <!-- ![Addon](assets\add-on.png) -->

1. Klik op **[!UICONTROL Update]**.

1. Stel de bouwstijlpijpleiding in werking.

Nadat de bouwstijllijn slaagt, wordt Communicatie APIs toegelaten voor uw milieu.

## Communicatie API&#39;s gebruiken {#workflows}

Doorgaans maakt u een sjabloon met [Designer](use-forms-designer.md) en communicatie-API&#39;s gebruiken voor:

- Converteer deze sjablonen naar verschillende indelingen, zoals PDF, PostScript, ZPL en PCL.
- U kunt XML-formuliergegevens samenvoegen met een formulierontwerp om een document te genereren.
- Een document genereren zonder XML-formuliergegevens samen te voegen in het document. De primaire workflow is echter het samenvoegen van gegevens in het document.

Vervolgens wordt het uitvoerdocument opgeslagen naar een bestand. U kunt aangepaste workflows ontwerpen om het bestand naar een netwerkprinter, een lokale printer of een opslagsysteem te verzenden voor archivering. Een typisch uit de doos en de douanewerkschema&#39;s kijken als het volgende:

![Communicatieworkflow](assets/communicaions-workflow.png)

### PDF-documenten maken {#create-pdf-documents}

U kunt de _generatePDFOutput_ API om een PDF-document te maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens. De uitvoer is een niet-interactief PDF-document. Gebruikers kunnen dus geen formuliergegevens invoeren of wijzigen. Een basisworkflow is het samenvoegen van XML-formuliergegevens met een formulierontwerp om een PDF-document te maken. In de volgende afbeelding ziet u hoe een formulierontwerp en XML-formuliergegevens worden samengevoegd om een PDF-document te maken.

![PDF-documenten maken](assets/outPutPDF_popup.png)

### PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL)-document maken {#create-PS-PCL-ZPL-documents}

Met communicatie-API&#39;s kunt u PostScript (PS)-, Printer Command Language (PCL)- en Zebra Printing Language (ZPL)-documenten maken die zijn gebaseerd op een XDP-formulierontwerp of PDF-document. De _generatePrintedOutput_ API voegt een formulierontwerp samen met formuliergegevens om een document te genereren. U kunt het document opslaan in een bestand en een aangepast proces ontwikkelen om het naar een printer te verzenden.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### Batchgegevens verwerken om meerdere documenten te maken {#processing-batch-data-to-create-multiple-documents}

U kunt aparte documenten maken voor elke record in een XML-batchgegevensbron. U kunt documenten bulksgewijs en asynchroon genereren. U kunt diverse parameters voor de omzetting vormen en dan het partijproces beginnen. <!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. -->

### Interactieve PDF-documenten afvlakken {#flatten-interactive-pdf-documents}

Met de API&#39;s voor communicatie kunt u een interactief PDF-document (bijvoorbeeld een formulier) transformeren naar een niet-interactief PDF-document. Met een interactief PDF-document kunnen gebruikers gegevens in de documentvelden van het PDF-document invoeren of wijzigen. Het transformeren van een interactief PDF-document naar een niet-interactief PDF-document wordt afvlakking genoemd. Wanneer een PDF-document wordt samengevoegd, kan een gebruiker de gegevens in de documentvelden niet wijzigen. Een reden om een PDF-document af te vlakken is ervoor te zorgen dat gegevens niet kunnen worden gewijzigd.

U kunt de volgende typen PDF-documenten samenvoegen:

- Interactieve PDF-documenten die zijn gemaakt in Designer (die XFA-streams bevatten).

- Acrobat PDF forms

Als u probeert een niet-interactief PDF-document af te vlakken, treedt een uitzondering op.

### Formulierstatus behouden {#retain-form-state}

Een interactief PDF-document bevat verschillende elementen die een formulier vormen. Deze elementen kunnen velden (voor het accepteren of weergeven van gegevens), knoppen (voor het activeren van gebeurtenissen) en scripts (voor het uitvoeren van een bepaalde handeling) bevatten. Wanneer u op een knop klikt, wordt mogelijk een gebeurtenis geactiveerd die de status van een veld wijzigt. Als u bijvoorbeeld een optie kiest voor een geslacht, kan de kleur van een veld of de weergave van het formulier veranderen. Dit is een voorbeeld van een handmatige gebeurtenis die ertoe leidt dat de formulierstatus verandert.

Wanneer een dergelijk interactief PDF-document wordt afgevlakt met behulp van de communicatie-API&#39;s, blijft de status van het formulier niet behouden. Stel de Booleaanse waarde in om ervoor te zorgen dat de status van het formulier wordt behouden, zelfs nadat het formulier is samengevoegd _preserveFormState_ op True om de status van het formulier op te slaan en te behouden.

### Overwegingen voor communicatie-API&#39;s {#considerations-for-communications-apis}

#### Formuliergegevens {#form-data}

Communicatie-API&#39;s accepteren zowel een formulierontwerp dat gewoonlijk in Designer wordt gemaakt als XML-formuliergegevens. Als u een document wilt vullen met gegevens, moet de XML-formuliergegevens een XML-element bevatten voor elk formulierveld dat u wilt vullen. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven. De belangrijkste factor is dat de XML-elementen met de overeenkomende waarden worden opgegeven.

Bekijk het volgende voorbeeld van een aanvraagformulier voor een lening:

![Toepassingsformulier laden](assets/loanFormData.png)

Als u gegevens wilt samenvoegen in dit formulierontwerp, maakt u een XML-gegevensbron die overeenkomt met het formulier. De volgende XML vertegenwoordigt een XML-gegevensbron die overeenkomt met het voorbeeld van een hypotheektoepassingsformulier.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
- <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
- <xfa:data>
- <data>
    - <Layer>
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
    - <Mortgage>
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

#### Ondersteunde documenttypen {#supported-document-types}

Voor volledige toegang tot de renderingmogelijkheden van de communicatie-API&#39;s wordt aanbevolen een XDP-bestand als invoer te gebruiken. In sommige gevallen kan een PDF-bestand worden gebruikt. Het gebruik van een PDF-bestand als invoer heeft echter de volgende beperkingen:

- Een PDF-document dat geen XFA-stream bevat, kan niet worden gerenderd als PostScript, PCL of ZPL. Communicatie-API&#39;s kunnen PDF-documenten met XFA-streams (dat wil zeggen formulieren die zijn gemaakt in Designer) weergeven in laser- en labelindelingen. Als het PDF-document is ondertekend, gecertificeerd of gebruiksrechten bevat (toegepast met de AEM Forms Reader Extensions-service), kan het niet worden gerenderd naar deze afdrukindelingen.

<!-- * Run-time options such as PDF version and tagged PDF are not supported for Acrobat forms. They are valid for PDF forms that contain XFA streams; however, these forms cannot be signed or certified. 

#### Email support {#email-support}

For email functionality, you can create a process in AEM Workflows that uses the Email Step. A workflow represents a business process that you are automating. -->

#### Afdrukbare gebieden {#printable-areas}

De standaard niet-afdrukbare marge van 0,25 inch is niet exact voor labelprinters en varieert van printer tot printer en van labelgrootte tot labelgrootte. Het wordt aanbevolen de marge van 0,25 inch te behouden of te verlagen. U wordt echter aangeraden de niet-afdrukbare marge niet te verhogen. Anders wordt de informatie in het afdrukbare gebied niet correct afgedrukt.

Zorg altijd dat u het juiste XDC-bestand voor de printer gebruikt. Vermijd bijvoorbeeld het kiezen van een XDC-bestand voor een 300 dpi-printer en het verzenden van het document naar een 200 dpi-printer.

#### Scripts {#scripts}

Een formulierontwerp dat wordt gebruikt met de communicatie-API&#39;s kan scripts bevatten die op de server worden uitgevoerd. Zorg ervoor dat een formulierontwerp geen scripts bevat die op de client worden uitgevoerd. Zie Help bij Designer voor informatie over het maken van scripts voor formulierontwerp.

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

#### Lettertypetoewijzing {#font-mapping}

Als een lettertype op een clientcomputer is geïnstalleerd, is het beschikbaar in de vervolgkeuzelijst in Designer. Als het lettertype niet is geïnstalleerd, moet u de lettertypenaam handmatig opgeven. De optie Niet-beschikbare lettertypen permanent vervangen in Designer kan zijn uitgeschakeld. Anders wordt de naam van het vervangende font geschreven naar het XDP-bestand wanneer het XDP-bestand wordt opgeslagen in Designer. Dit betekent dat het printerresidente lettertype niet wordt gebruikt.

Als u een formulier wilt ontwerpen waarin printerresidente lettertypen worden gebruikt, kiest u een lettertypenaam in Designer die overeenkomt met de lettertypen die beschikbaar zijn op de printer. Een lijst met lettertypen die worden ondersteund voor PCL of PostScript vindt u in de bijbehorende apparaatprofielen (XDC-bestanden). U kunt ook lettertypetoewijzing maken om niet-printerresidente lettertypen toe te wijzen aan printerresidente lettertypen met een andere lettertypenaam. In een PostScript-scenario kunnen verwijzingen naar het lettertype Arial® bijvoorbeeld worden toegewezen aan het printerresidente Helvetica®-lettertype.

Er zijn twee typen OpenType®-lettertypen. Eén type is een TrueType OpenType®-font dat door PCL wordt ondersteund. Het andere is CFF OpenType®. PDF- en PostScript-uitvoer ondersteunen ingesloten Type-1-, TrueType- en OpenType®-lettertypen. PCL-uitvoer ondersteunt ingesloten TrueType-fonts.

Type-1- en OpenType®-lettertypen worden niet ingesloten in PCL-uitvoer. Inhoud die is opgemaakt met Type-1- en OpenType®-lettertypen wordt gerasterd en gegenereerd als een bitmapafbeelding die groot en langzamer kan zijn om te genereren.

Gedownloade of ingesloten lettertypen worden automatisch vervangen bij het genereren van PostScript-, PCL- of PDF-uitvoer. Dit betekent dat alleen de subset van de lettertypeglyphs die vereist zijn om het gegenereerde document correct weer te geven, in de gegenereerde uitvoer wordt opgenomen.

#### Werken met apparaatprofielbestanden (XDC-bestand) {#working-with-xdc-files}

Een apparaatprofiel (XDC-bestand) is een printerbeschrijvingsbestand in XML-indeling. Met dit bestand kunnen de communicatie-API&#39;s documenten uitvoeren als laser- of labelprinterindelingen. Communicatie-API&#39;s gebruiken de XDC-bestanden, waaronder de volgende:

- hppcl5c.xdc

- hppcl5e.xdc

- ps_plain_level3.xdc

- ps_plain.xdc

- zpl300.xdc

- zpl600.xdc

- zpl300.xdc

- ipl300.xdc

- ipl400.xdc

- tpcl600.xdc

- dpl300.xdc

- dpl406.xdc

- dpl600.xdc

U hoeft deze bestanden niet te wijzigen om documenten te maken. Nochtans, kunt u hen wijzigen om aan uw bedrijfsvereisten te voldoen.

Deze bestanden zijn voorbeeld-XDC-bestanden die de functies van specifieke printers ondersteunen, zoals residente lettertypen, papierladen en nietmachines. Het doel van deze voorbeelden is om u te helpen begrijpen hoe u uw eigen printers kunt instellen met apparaatprofielen. De steekproeven zijn ook een uitgangspunt voor gelijkaardige printers in de zelfde productlijn.

#### Werken met het XCI-configuratiebestand {#working-with-xci-files}

Communicatie APIs gebruikt een XCI configuratiedossier om taken uit te voeren, zoals het controleren of de output één enkel paneel of gepagineerd is. Hoewel dit bestand instellingen bevat die kunnen worden ingesteld, is het niet standaard om deze waarde te wijzigen. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

U kunt een gewijzigd XCI-bestand doorgeven terwijl u een communicatie-API gebruikt. Als u dit doet, maakt u een kopie van het standaardbestand, wijzigt u alleen de waarden die moeten worden gewijzigd om aan uw bedrijfsvereisten te voldoen en gebruikt u het aangepaste XCI-bestand.

Communicatie-API&#39;s beginnen met het standaard-XCI-bestand (of het gewijzigde bestand). Vervolgens worden waarden toegepast die zijn opgegeven met de communicatie-API&#39;s. Deze waarden overschrijven XCI-instellingen.

In de volgende tabel worden XCI-opties opgegeven.

| XCI, optie | Beschrijving |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Zie de handleiding PDF Reference voor informatie over dit woordenboek. |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Zie de handleiding PDF Reference voor informatie over dit woordenboek. |
| config/present/layout | Hiermee bepaalt u of de uitvoer één deelvenster is of gepagineerd. |
| config/present/pdf/compression/level | Hiermee geeft u de mate van compressie op die moet worden gebruikt bij het genereren van een PDF-document. |
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
| config/present/script/exclude | Meldt aan de server/Communicatie APIs van AEM Forms welke gebeurtenissen om te negeren. |
| config/present/pdf/linearized | Bepaalt of het PDF-uitvoerdocument lineair is. |
| config/present/script/runScripts | Hiermee bepaalt u welke set scripts AEM Forms uitvoert. |
| config/present/pdf/tagged | Controls the include of tags into the output PDF document. Codes, in de context van PDF, zijn aanvullende informatie die in een document is opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. |
| config/present/pdf/version | Hiermee geeft u de versie op van het PDF-document dat moet worden gegenereerd. |

### Bekende problemen

- Zorg ervoor dat de grootte van de sjabloon- en XCI-configuratiebestanden groter is dan 16 kB.

- Zorg ervoor dat het gegevens-xml-bestand de XML-declaratiekop niet bevat. Bijvoorbeeld, `<?xml version="1.0" encoding="UTF-8"?>`

- Voor een batchconfiguratie is slechts één instantie van een combinatie van waarden van OutputType (PDF, PRINT) en RenderType (PostScript, PCL, IPL, ZPL, enz.) is toegestaan.

- Wijzig de Configuratie van de Configuratie van de Gegevensbron USC/Azure Cloud die in een partijconfiguratie wordt gebruikt niet terwijl de partij in werking wordt gesteld. Zelfs na uitvoering, als om het even welke update wordt vereist, creeer een exemplaar van configuratie in plaats van het bijwerken van gebruikt in een bestaande partijconfiguratie.

### Best practices voor

- Adobe raadt aan gegevensbestanden op te slaan in een blob-containerarchief in het cloudgebied dat door AEM Cloud Service wordt gebruikt.

<!-- Using API

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as HTTP endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document. -->


