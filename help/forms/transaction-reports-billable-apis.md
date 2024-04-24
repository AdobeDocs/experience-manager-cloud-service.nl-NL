---
title: Transactierapporten Billable API's
description: Lijst met alle API's die als transacties worden beschouwd
feature: Adaptive Forms, Foundation Components
exl-id: 6dfcac3e-5654-4b4f-9134-0cd8be24332e
source-git-commit: 539f4bf86f0e32057b2228dc44c86120d6e8457b
workflow-type: tm+mt
source-wordcount: '1411'
ht-degree: 0%

---


# Transactierapporten Billable API&#39;s {#transaction-reports-billable-apis}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/transaction-reports/transaction-reports-billable-apis) |
| AEM as a Cloud Service | Dit artikel |


AEM Forms biedt verschillende API&#39;s voor het verzenden van formulieren, procesdocumenten en het weergeven van documenten. Sommige API&#39;s worden beschouwd als transacties en andere kunnen gratis worden gebruikt. Dit document verstrekt een lijst van alle APIs die als transacties in een transactierapport worden rekenschap gegeven. Hier volgen enkele veelvoorkomende scenario&#39;s waarbij een factureerbare API wordt gebruikt:

* Een adaptief formulier indienen
* Een document omzetten van de ene naar de andere indeling
* Een dynamisch PDF-document afvlakken
* Een document met records genereren (met Forms Service of Output Service)
* Een interactief PDF-document samenvoegen met een ander PDF-document
* De stappen voor taakstap toewijzen en communicatie-API van AEM Workflows gebruiken

Factuur-API&#39;s zijn niet geschikt voor het aantal pagina&#39;s, de lengte van een document of formulier of de uiteindelijke indeling van het gerenderde document. In een transactierapport worden de transacties in twee categorieën verdeeld: Forms verzonden en gerenderde documenten.

* **Forms verzonden:** Wanneer gegevens worden verzonden vanuit elk type formulier dat met AEM Forms is gemaakt en de gegevens worden verzonden naar een opslagplaats of database voor gegevensopslag, wordt dit beschouwd als een verzending. Het indienen van een adaptief formulier of een formulierset wordt bijvoorbeeld beschouwd als verzonden formulieren. Als een formulierset vijf formulieren heeft en de formulierset wordt verzonden, telt de service voor transactierrapportage deze als vijf verzendingen.

* **Gerenderde documenten:** Het genereren van een document door een sjabloon en gegevens te combineren, een document digitaal te ondertekenen of te certificeren, met behulp van een factureerbare API&#39;s voor documentservices of door een document van de ene naar de andere indeling te converteren, wordt beschouwd als documenten die worden gerenderd.

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_submission_graph_en"
>title="Formulierverzendingenbeheer"
>abstract="Volg eenvoudig formulierverzendingen op uw AEM Forms Publish-exemplaar met ons intuïtieve trackingdashboard. De grafiek geeft gegevens die specifiek zijn voor het huidige exemplaar, zodat u trends snel kunt analyseren en geïnformeerde beslissingen kunt nemen. Voor verzendgegevens van andere instanties hebt u eenvoudig toegang tot het dashboard van het betreffende exemplaar."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_conversions_graph_en"
>title="Formulieromzettingsbeheer"
>abstract="Blijf op de hoogte van formulierconversies met een overzicht van het totale aantal conversies. De grafiek bevat specifieke gegevens voor de huidige AEM Forms-instantie Publish, waarmee u trends snel kunt analyseren en geïnformeerde beslissingen kunt nemen. Als u conversiegegevens van andere instanties wilt weergeven, opent u het dashboard van de desbetreffende instantie."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formCreationAvgDuration_graph_en"
>title="Gemiddelde duur voor genereren van formulieren"
>abstract="De grafiek toont de gemiddelde tijd die nodig is om een formulier te maken. Elke balk in de grafiek vertegenwoordigt een specifiek formulier en de hoogte van de balk geeft de gemiddelde duur aan die tijdens dat tijdframe voor het maken van het formulier is gebruikt."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formPublishAvgDuration_en"
>title="Gemiddelde duur voor het maken van formulieren"
>abstract="In de grafiek wordt de gemiddelde tijd weergegeven die nodig is om een formulier te maken en te publiceren, gemeten vanaf de eerste dag waarop het formulier is geopend voor bewerking. De grafiek bevat specifieke gegevens voor de huidige AEM Forms-auteur. Als u gegevens van andere instanties wilt weergeven, opent u het dashboard van de desbetreffende instantie."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_newForms_graph_en"
>title="Nieuw Forms-beheer"
>abstract="De grafiek geeft informatie over het aantal of de frequentie van nieuwe formulieren tijdens specifieke tijdsperiodes. De grafiek bevat specifieke gegevens voor de huidige AEM Forms Author-instantie. Als u gegevens van andere instanties wilt weergeven, opent u het dashboard van de desbetreffende instantie."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_publishedForms_graph_en"
>title="Gepubliceerd Forms-beheer"
>abstract="De grafiek geeft informatie over het aantal of de frequentie van formulieren die tijdens specifieke tijdsperioden met succes zijn gepubliceerd. De grafiek bevat specifieke gegevens voor de huidige AEM Forms-instantie Publish. Als u conversiegegevens van andere instanties wilt weergeven, opent u het dashboard van de desbetreffende instantie."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formFragments_graph_en"
>title="Gepubliceerd Forms-beheer"
>abstract="Met deze grafiek kunt u zien hoeveel formulierfragmenten mensen in hun formulieren gebruiken. De grafiek bevat specifieke gegevens voor de huidige AEM Forms-instantie Publish. Als u conversiegegevens van andere instanties wilt weergeven, opent u het dashboard van de desbetreffende instantie."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_avgFormPerFragments_graph_en"
>title="Gepubliceerd Forms-beheer"
>abstract="In de grafiek wordt de gemiddelde tijd weergegeven die nodig is om een formulierfragment te maken, gemeten vanaf de eerste dag dat het formulierfragment voor bewerking is geopend. De grafiek bevat specifieke gegevens voor de huidige AEM Forms-instantie Publish. Als u conversiegegevens van andere instanties wilt weergeven, opent u het dashboard van de desbetreffende instantie."

<!-- 

>[!NOTE]
>
>Transaction Reports UI displays three categories: Forms Submitted, Documents Rendered, and Documents Processed. Both Documents Rendered and Documents Processed are accounted as Documents Rendered.
-->


<!--

## Billable Document Services APIs {#billable-document-services-apis}

### Generate PDF Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->


<!--
### Distiller Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## Billable Document Services API&#39;s {#billable-document-services-apis}

### PDF-service genereren {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#section/Before-you-start" target="_blank">createPDF</a></td>
   <td>Hiermee genereert u een PDF-document op basis van een sjabloon en voegt u er gegevens aan toe.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePrintedOutput/post" target="_blank">exportPDF</a></td>
   <td>Hiermee converteert u XDP-bestand of PDF-document naar ondersteunde bestandstypen.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

### Uitvoerservice {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutput" target="_blank">generatePDFOutput</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutputOptions" target="_blank">generatePDFOutput (PDFOutputOptions)</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePDFOutputBatch</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een set PDF-documenten te maken.</td>
   <td>Verwerkte documenten</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutput" target="_blank">generatePrintedOutput</a></td>
   <td>XDP- en PDF-documenten worden omgezet in de bestandsindelingen PostScript (PS), Printer Command Language (PCL) en ZPL. </td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutputOptions" target="_blank">generatePrintedOutput (PrintedOutputOptions)</a></td>
   <td>XDP- en PDF-documenten worden omgezet in de bestandsindelingen PostScript (PS), Printer Command Language (PCL) en ZPL. </td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePrintedOutputBatch</a></td>
   <td>Hiermee converteert u een set XDP- en PDF-documenten naar een set PostScript- (PS), Printer Command Language (PCL)- en ZPL-bestandsindelingen. </td>
   <td>Verwerkte documenten</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
 </tbody>
</table>

### DocAssurance Service {#DocAssurance-Service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/docassurance/#tag/DocAssurance" target="_blank">secureDocument</a><br /> </td>
   <td>Met deze API kunt u uw document beveiligen. Met de API kunt u een PDF-document ondertekenen, certificeren, lezen of uitbreiden.</td>
   <td>Verwerkte documenten</td>
   <td>Alleen de bewerking voor ondertekenen en certificeren van het SecureDocument wordt in rekening gebracht.</td>
  </tr>
 </tbody>
</table>

### Document of Record (DOR)-service {#document-of-record-dor-forms-service-and-output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Generate-DoR/operation/generateDoR" target="_blank">renderen</a></td>
   <td>Roept de opgegeven rendermethode aan om een document met een record te genereren met behulp van opgegeven parameters.</td>
   <td>Documenten die zijn verwerkt met Forms Service</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="" target="_blank">render</a></td>
   <td>Invokes the specified render method to generate a document of record using provided parameters.</td>
   <td>Documents Processed using Output Service</td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

<!--

### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Renders PDF Form from XDP templates. The XP templates are created in Forms Designer.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extracts data from a PDF Form or XDP templates</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Convert PDF Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Converts a PDF document to a list of image documents. Supported image formats are JPEG, JPEG2K, PNG, and TIFF.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td>
   <td>Converts a Flat PDF file to PostScript format using the options specified in the option spec.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Barcoded Forms Service {#barcoded-forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Decodes all the barcodes in a Document object and returns an org.w3c.dom.Document object that contains data that was retrieved from the barcode.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

### Assembler-service {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX">oproepen</a></td>
   <td>Hiermee wordt de DDX uitgevoerd op de opgegeven invoerdocumenten en wordt een object met de resultaatdocumenten geretourneerd</td>
   <td>Verwerkte documenten</td>
   <td>De volgende transacties worden niet administratief verwerkt als transacties:
    <ul>
     <li>Pakketten of portfolio maken</li>
     <li>Meerdere XDP's vastleggen </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX" target="_blank">oproepen</a></td>
   <td>Hiermee wordt de DDX uitgevoerd op de opgegeven invoerdocumenten en wordt een object met de resultaatdocumenten geretourneerd</td>
   <td>Verwerkte documenten</td>
   <td>Alle invoerbestandsindelingen die door PDF Generator-, Forms- en Output-services worden ondersteund, worden door de Assembler-service ondersteund voor al die indelingen als uitvoerbestandsindelingen. </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA">toPDFA</a></td>
   <td>Zet een opgegeven document om in PDF/A met de opgegeven opties.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

Het gebruik van de API voor aanroepen wordt als een transactie geteld wanneer u een of meer van de volgende bewerkingen uitvoert:

1. Conversie van niet-PDF-indelingen naar PDF-indelingen. <!--For instance, the conversion from XDP format to PDF format, catering to both interactive and non-interactive forms of communication, and the conversion from Word to PDF.-->
1. Omzetten van PDF-indeling naar PDF/A-indeling.
1. Conversie van PDF-indeling naar niet-PDF-indeling. Voorbeelden hiervan zijn de transformatie van de indeling PDF naar Afbeelding of de conversie van de indeling PDF naar tekst.


>[!NOTE]
>
>* De invoke API van de assemblageservice kan intern een factureerbare API van een andere service oproepen, afhankelijk van de invoer. De aanroepAPI kan dus worden beschouwd als geen, enkele of meerdere transacties. Het aantal transacties dat wordt geteld, is afhankelijk van de invoer en de interne API&#39;s die worden aangeroepen.
>* Eén enkel PDF-document dat met de assembleerservice wordt gemaakt, kan worden beschouwd als geen, enkele of meerdere transacties. Het aantal getelde transacties is afhankelijk van de opgegeven code.
>

<!--
### PDF Utility Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Converts a PDF document into an XDP file. In order for a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the AcroForm dictionary.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## Billable Data Capture API&#39;s {#billable-data-capture-apis}

Alle verzendingen van adaptieve formulieren worden administratief verwerkt als transacties. Door gebrek, wordt de voorlegging van een Vorm van de PDF niet administratief verwerkt als transactie. Gebruik de opgegeven [transactie recorder-API](record-transaction-custom-implementation.md) om een PDF forms te registreren die als transactie wordt voorgelegd.

### Adaptieve Forms {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Hoofdletters gebruiken</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een adaptief formulier indienen</td>
   <td>Hiermee wordt een adaptief formulier verzonden voor een geconfigureerde verzendactie. </td>
   <td>Forms verzonden</td>
   <td>
    <ul>
     <li>Een of twee transacties worden verwerkt met geslaagde verzendingen. Het aantal transacties dat wordt meegeteld, is afhankelijk van het type verzendactie dat wordt gebruikt voor verzending. Bijvoorbeeld, verzendend PDF door e-mail verzend actierekeningen voor twee tellingen van transacties. Eén transactie voor het verzenden van formulieren en een andere voor PDF die is gegenereerd met de service Document of Record (DOR). </li>
     <li>Met het adaptieve formulier in een adaptief formulier (adaptief formulierformaat) wordt slechts één transactie verwerkt. U kunt een willekeurig aantal adaptieve formulieren in een adaptief formulier gebruiken.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

<!--

### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an HTML5 Form</td>
   <td>Submits an HTML5 Form to submit URL configured in the form.</td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Form set {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting a form set</td>
   <td>Submits form set to the submit URL configured in the form set.</td>
   <td>Forms Submitted</td>
   <td>
    <ul>
     <li>Using the adaptive form within an adaptive form (Adaptive form formset) accounts only single transaction. You can have any number of adaptive forms within an adaptive form.</li>
     <li>Every form in an HTML5 Forms form set accounts as a separate transaction. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

-->

## Billable Form-centric AEM Workflows {#billable--form-centric-aem-workflows}

Taken en documentservicestappen toewijzen van Form-centric AEM Workflows worden als transacties geboekt. Als een workflowstap een transactie verwerkt en de workflow niet wordt voltooid, wordt het aantal transacties niet teruggedraaid.

<!--
Assign task and document services steps of Form-centric AEM Workflows on OSGi and all the renditions of interactive communication and are accounted as transactions. Previewing an interactive communication on the author instance and previewing on the publish instance using Agent UI are not accounted as transactions. If a workflow step accounts a transaction and the workflow fails to complete, the transaction count is not reversed.
-->


<!--

### Interactive Communication - Web Channel {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Rendering a web channel</td>
   <td>Opens the web version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactive Communication - Print Channel {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (convert to PDF)</td>
   <td>Generates the PDF version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

-->

### Formuliergerichte AEM Workflows {#form-centric-aem-workflows}

<table>
 <tbody>
  <tr>
   <td><p>Hoofdletters gebruiken</p> </td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een taakstap toewijzen verzenden</td>
   <td>Forms verzonden</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Een startpunt voor een workflowtoepassing indienen </td>
   <td>Forms verzonden</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Infactureerbare API&#39;s opnemen als transacties voor aangepaste code {#recording-billable-apis-as-transactions-for-custom-code}

Handelingen zoals het verzenden van een PDF-formulier, het gebruik van de gebruikersinterface van de om een voorvertoning van een interactieve communicatie weer te geven, met behulp van niet-standaardformulierverzending, en aangepaste implementaties worden niet als transacties beschouwd. AEM Forms biedt een API om dergelijke handelingen op te nemen, zoals transacties. U kunt de API vanuit uw aangepaste implementaties aanroepen naar [een transactie opnemen](/help/forms/record-transaction-custom-implementation.md).

## Verwante artikelen {#related-articles}

* [Een transactie opnemen voor aangepaste implementaties](/help/forms/record-transaction-custom-implementation.md)
