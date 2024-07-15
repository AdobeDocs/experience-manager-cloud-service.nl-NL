---
title: Wat zijn overwegingen, bekende kwesties en beste praktijken in AEM Forms?
description: Bekende problemen en best practices voor AEM Forms Communication API's in overweging nemen.
exl-id: e95615dd-e494-40cd-9cdf-6e9761ca3b3e
feature: Adaptive Forms
role: Admin, Developer, User
source-git-commit: 975f767e75a268a1638227ae20a533f82724c80a
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Bekende problemen en best practices {#best-practices-known-issues-and-limitations}

Voordat u de communicatie-API&#39;s gaat gebruiken, moet u de volgende overwegingen, bekende problemen en vaak gestelde vragen doornemen:

## Overwegingen  {#considerations-for-communications-apis}

### Formuliergegevens {#form-data}

Communicatie-API&#39;s accepteren zowel een formulierontwerp dat gewoonlijk in Designer en XML-formuliergegevens wordt gemaakt als invoer. Als u een document wilt vullen met gegevens, moet de XML-formuliergegevens een XML-element bevatten voor elk formulierveld dat u wilt vullen. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven. De belangrijkste factor is dat de XML-elementen met de overeenkomende waarden worden opgegeven.

Bekijk het volgende voorbeeld van een aanvraagformulier voor een lening:

![ de toepassingsVorm van de Lening ](assets/loanFormData.png)

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

### Ondersteunde documenttypen {#supported-document-types}

Voor volledige toegang tot de renderingmogelijkheden van de communicatie-API&#39;s wordt aanbevolen een XDP-bestand als invoer te gebruiken. Soms kan een PDF-bestand worden gebruikt. Het gebruik van een PDF-bestand als invoer heeft echter de volgende beperkingen:

Een PDF-document dat geen XFA-stream bevat, kan niet worden gerenderd als PostScript, PCL of ZPL. Communicatie-API&#39;s kunnen PDF-documenten met XFA-streams (dat wil zeggen, formulieren die zijn gemaakt in Designer) weergeven in laser- en labelindelingen. Als het PDF-document is ondertekend, gecertificeerd of gebruiksrechten bevat (toegepast met de AEM Forms Reader Extensions-service), kan het niet worden gerenderd naar deze afdrukindelingen.


### Afdrukbare gebieden {#printable-areas}

De standaard niet-afdrukbare marge van 0,25 inch is niet exact voor labelprinters en varieert van printer tot printer en van labelgrootte tot labelgrootte. Het is echter aan te raden de marge van 0,25 inch te behouden of te verkleinen. U wordt echter aangeraden de niet-afdrukbare marge niet te verhogen. Anders wordt de informatie in het afdrukbare gebied niet correct afgedrukt.

Zorg altijd dat u het juiste XDC-bestand voor de printer gebruikt. Vermijd bijvoorbeeld het kiezen van een XDC-bestand voor een 300 dpi-printer en het verzenden van het document naar een 200 dpi-printer.

### Scripts voor alleen XFA-formulieren (XDP/PDF) {#scripts}

Een formulierontwerp dat wordt gebruikt met de communicatie-API&#39;s kan scripts bevatten die op de server worden uitgevoerd. Zorg ervoor dat een formulierontwerp geen scripts bevat die op de client worden uitgevoerd. Voor informatie over het creëren van manuscripten van het vormontwerp, zie [ Hulp van Designer ](use-forms-designer.md).

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

### Lettertypetoewijzing {#font-mapping}

Als u een formulier wilt ontwerpen waarin printerresidente lettertypen worden gebruikt, kiest u een lettertypenaam in Designer die overeenkomt met de lettertypen die op de printer beschikbaar zijn. Een lijst met lettertypen die worden ondersteund voor PCL of PostScript, vindt u in de bijbehorende apparaatprofielen (XDC-bestanden). U kunt ook lettertypetoewijzing maken om niet-printerresidente lettertypen toe te wijzen aan printerresidente lettertypen met een andere lettertypenaam. In een PostScript-scenario kunnen verwijzingen naar het lettertype Arial® bijvoorbeeld worden toegewezen aan het printerresidente Helvetica®-lettertype.

Als een lettertype op een clientcomputer is geïnstalleerd, is het beschikbaar in de vervolgkeuzelijst in Designer. Als het lettertype niet is geïnstalleerd, moet u de lettertypenaam handmatig opgeven. De optie Niet-beschikbare lettertypen permanent vervangen in Designer kan zijn uitgeschakeld. Als het XDP-bestand in Designer wordt opgeslagen, wordt de naam van het vervangende font naar het XDP-bestand geschreven. Dit betekent dat het printerresidente lettertype niet wordt gebruikt.

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
<!-- It is not necessary to modify these files to create documents. However, you can modify them to meet your business requirements. -->

Deze bestanden zijn referentie-XDC-bestanden die de functies van specifieke printers ondersteunen, zoals residente lettertypen, papierladen en nietmachines. Het doel van deze naslaggids is om u te helpen begrijpen hoe u uw eigen printers kunt instellen met apparaatprofielen. De verwijzing is ook een uitgangspunt voor gelijkaardige printers in de zelfde productlijn.

### Werken met het XCI-configuratiebestand {#working-with-xci-files}

Communicatie APIs gebruikt een XCI configuratiedossier om taken uit te voeren, zoals het controleren of de output één enkel paneel of gepagineerd is. Hoewel dit bestand instellingen bevat die kunnen worden ingesteld, is het niet standaard om deze waarde te wijzigen. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

U kunt een gewijzigd XCI-bestand doorgeven terwijl u een communicatie-API gebruikt. Als u dit doet, maakt u een kopie van het standaardbestand, wijzigt u alleen de waarden die moeten worden gewijzigd om aan uw bedrijfsvereisten te voldoen en gebruikt u het aangepaste XCI-bestand.

Communicatie API&#39;s beginnen met het standaard XCI-bestand (of het gewijzigde bestand). Vervolgens worden waarden toegepast die zijn opgegeven met de communicatie-API&#39;s. Deze waarden overschrijven XCI-instellingen.

In de volgende tabel worden XCI-opties opgegeven.

| XCI, optie | Beschrijving |
| ------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Zie de handleiding PDF Reference voor meer informatie over dit woordenboek. |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Zie de handleiding PDF Reference voor meer informatie over dit woordenboek. |
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
| config/present/pdf/linearized | Controls whether the output PDF document is linearized. |
| config/present/script/runScripts | Hiermee bepaalt u welke set scripts AEM Forms uitvoert. |
| config/present/pdf/tagged | Controls the include of tags into the output PDF document. Codes, in de context van PDF, zijn aanvullende informatie die in een document is opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. |
| config/present/pdf/version | Hiermee geeft u de versie op van het PDF-document dat moet worden gegenereerd. |


## Bekende problemen

* U kunt een specifiek rendertype (PDF, AFDRUKKEN) slechts eenmaal gebruiken in de lijst met afdrukopties. U kunt bijvoorbeeld niet beschikken over twee PRINT-opties die elk een PCL-rendertype opgeven.

* Voor een batchconfiguratie is slechts één instantie van combinatie van waarden van OutputType (PDF, PRINT) en RenderType (PostScript, PCL, IPL, ZPL, enzovoort) toegestaan.

* Voor asynchrone API&#39;s (batchverwerking) is het standaard recordniveau ingesteld op 2. U kunt een aangepaste XCI gebruiken om het recordniveau te wijzigen in 1.

* Wanneer de standaard-XCI is geconfigureerd, bevat deze paden tot de oorspronkelijke uitvoering. Bijvoorbeeld: `/content/dam/formsanddocuments/default.xci/jcr:content/renditions/original`



## Aanbevolen procedures

* Adobe raadt u aan gegevensbestanden in de blob-containeropslag te hosten in het cloudgebied dat door AEM Cloud Service wordt gebruikt.

## Veelgestelde vragen {#faq}

**kan ik een gecontroleerde omslag of andere opslagmechanismen gebruiken om input en output op te slaan?**

Op dit moment kunt u Microsoft Azure Storage gebruiken om invoergegevens en gegenereerde documenten op te slaan. De opslag van Microsoft Azure verstrekt diverse opties om [ verrichtingen van de gegevensbeweging ](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) te automatiseren.

**is een Microsoft Azure rekening van de Opslag inbegrepen met de vergunning van de Cloud Service van Experience Manager Forms?**

Microsoft Azure Storage account is onafhankelijk van Experience Manager Forms Cloud Service license.

**slaat Communicatie APIs gegevens op de servers van de Cloud Service van Experience Manager Forms op?**

Invoer- en uitvoergegevens worden alleen opgeslagen op Microsoft Azure Storage.

**Zijn Communicatie APIs beschikbaar slechts voor de Cloud Service van Experience Manager Forms? Kan ik gelijkaardige functionaliteit op-gebouw milieu krijgen?**

U kunt de dienst van de Output van AEM Forms gebruiken om een malplaatje (XFA of PDF) met klantengegevens te combineren om documenten in PDF, PS, PCL, en formaten te produceren ZPL.

In vergelijking met een omgeving op locatie biedt de Cloud Service extra voordelen van automatisch schalen en kosteneffectiviteit.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**Kan ik veelvoudige partijverrichtingen gelijktijdig in werking stellen?**
Ja, u kunt meerdere batchbewerkingen tegelijk uitvoeren. Gebruik altijd verschillende bron- en doelmappen voor elke bewerking om conflicten te voorkomen.

>[!MORELIKETHIS]
>
>* [ Inleiding aan de as a Cloud Service Mededelingen van AEM Forms ](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [ as a Cloud Service Architectuur van AEM Forms voor Adaptieve Forms en Communicatie APIs ](/help/forms/aem-forms-cloud-service-architecture.md)
>* [ Communicatie Verwerking - Synchrone APIs ](/help/forms/aem-forms-cloud-service-communications.md)
>* [ Communicatie Verwerking - Partij APIs ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)

