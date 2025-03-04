---
title: Aan de slag met Edge Delivery Services for AEM Forms. Maak een formulier.
description: Creëer snelle perfecte formulieren! ⚡ op AEM Forms Edge Delivery gebaseerde authoring = razendsnelheid en SEO-vriendelijke formulieren voor gelukkige gebruikers en zoekmachines.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 04fb65b4ec2d8bf6f54e1927469cda4bf94cbec8
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Een formulier maken met Adaptief Forms-blok

>[!VIDEO](https://video.tv.adobe.com/v/3427881?quality=12&learn=on)

AEM Forms Edge Delivery biedt een blok, Adaptive Forms Block genaamd, waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. U kunt [ tot een nieuw project van AEM leiden dat met het AanpassingsBlok van Forms ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) wordt gevormd of [ het Aangepaste Blok van Forms aan een bestaand project van AEM ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) toevoegt.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft SharePoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

![ op document-gebaseerde het Authoring ecosysteem ](/help/edge/assets/document-based-authoring-workflow-create-form.png)


## Vereisten

Controleer voordat u begint of u de volgende stappen hebt uitgevoerd:

* Opstelling een [ project van AEM gebruikend AEM Forms boilerplate ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [ toevoegde Aangepast Blok van Forms aan uw bestaand Project van AEM ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) en kloon de overeenkomstige bewaarplaats GitHub op uw lokale machine.
<!--In this document, the local folder of your Edge Delivery Services (EDS) project is referred as `[EDS Project repository]`.  -->
* Zorg ervoor dat u toegang hebt tot Google Sheets of Microsoft SharePoint. Aan opstelling Microsoft SharePoint als uw inhoudsbron, zie [ hoe te SharePoint ](https://www.aem.live/docs/setup-customer-sharepoint) gebruiken.



## Een formulier maken

<!--
+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery Service Site. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
2. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

3. on your local machine and copy the `form` folder. 
4. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

* **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

* **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project. -->

+++ Stap 1: Een formulier ontwerpen met Microsoft Excel of Google Sheet.

In plaats van door complexe processen te navigeren, kunt u zonder problemen een formulier maken met behulp van een spreadsheet. U kunt de rijen en kolommen definiëren die de formulierstructuur vormen. Elke rij vertegenwoordigt een individueel [ vormgebied ](/help/edge/docs/forms/form-components.md#available-components) en de kolomkopballen bepalen de overeenkomstige [ gebiedseigenschappen ](/help/edge/docs/forms/form-components.md#components-properties).

Bijvoorbeeld, overweeg het volgende spreadsheet waar de rijen gebieden voor a [ vraag ](/help/edge/assets/enquiry.xlsx) spreadsheet en kolomkopballen hun eigenschappen bepalen:

![ Opiniepeiling spreadsheet ](/help/edge/assets/enquiry-form-spreadsheet.png)

Ga als volgt te werk om het formulier te maken:

1. Open uw AEM Edge Delivery-projectmap op Microsoft SharePoint of Google Drive.

1. Maak overal in uw AEM Edge Delivery-projectmap een Microsoft Excel-werkboek of Google-werkblad. Maak bijvoorbeeld een werkblad met de naam `enquiry` in de AEM Edge Delivery-projectmap op Google Drive.

   <!-- ![Sample Content on Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)-->

1. Zorg ervoor dat het blad met de aangewezen gebruiker van AEM (bijvoorbeeld `forms@adobe.com`) [ zoals per de configuraties wordt gedeeld die voor uw project ](https://www.aem.live/docs/setup-customer-sharepoint) worden gespecificeerd. Hiermee geeft u de gebruiker bewerkingsmachtigingen voor het blad.

1. Open het gemaakte werkblad en wijzig de naam van het standaardwerkblad in &quot;shared-name&quot;.

   ![ anders noem standaardblad aan &quot;gedeeld-gebrek&quot;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Als u formuliervelden wilt toevoegen, voegt u rijen en kolomkoppen in het &#39;shared-name&#39; blad in. Elke rij zou a [ vormgebied ](/help/edge/docs/forms/form-components.md#available-components), met kolomkopballen moeten vertegenwoordigen die de overeenkomstige gebied [ eigenschappen ](/help/edge/docs/forms/form-components.md#components-properties) bepalen.


   Voor een snel begin, overweeg het kopiëren van de inhoud van het [ Onderzoek spreadsheet ](/help/edge/assets/enquiry.xlsx) in uw spreadsheet. Sla het werkblad op nadat u de inhoud hebt gekopieerd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Het gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef het blad.

   ![ Gebruik AEM Sidekick om voorproef het blad ](/help/edge/assets/preview-form.png)

   Als u een voorbeeld bekijkt, wordt de inhoud van het blad op de tabbladen van de nieuwe browser in JSON-indeling weergegeven. Zorg ervoor dat u de voorbeeld-URL vastlegt, zoals dit is vereist voor het weergeven van het formulier in de volgende sectie. De URL-indeling is als volgt:


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Bijvoorbeeld, als de bewaarplaats van uw project &quot;wefinance&quot;wordt genoemd, is het gevestigd onder de rekening &quot;wkndform&quot;, en u gebruikt de &quot;belangrijkste&quot;tak, kijkt URL als het volgende:

`https://main--wefinance--wkndform.aem.page/enquiry.json`
&lt;!— (https://main—wefinance—wkndform.aem.page/inquiry.json)—>


+++

+++ Stap 2: Geef een voorbeeld van het formulier weer met uw Edge Delivery Services-pagina.


Tot nu toe hebt u de structuur van het formulier voorbereid. Nu een voorbeeld van het formulier weergeven:

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar de AEM Edge Delivery-projectmap.



1. Open een documentbestand (bijvoorbeeld een indexbestand) om het formulier in te sluiten. Alternatief, kunt u [ tot een nieuw document ](/help/edge/assets/enquiry-form.docx) leiden.

1. Ga naar de gewenste locatie in het document waar u het formulier wilt toevoegen.

1. Een formulierblok maken om het formulier te genereren. Selecteer Invoegen > Tabel en maak een tabel met één kolom en twee rijen. Geef de tabel een naam &quot;Formulier&quot; en plak de voorbeeld-URL in de tweede rij. Zorg ervoor dat de URL is opgemaakt als een hyperlink, niet als onbewerkte tekst, zoals hieronder wordt geïllustreerd:

   | Formulier |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |


   ![ voeg Aangepast Forms Blok aan uw webpagina toe ](/help/edge/assets/enquiry-doc-to-embed-form.png)

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de voorbeeld-URL van het `<form>.json` -bestand toe als hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.


1. Gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om het document voor te vertonen. Het formulier wordt nu weergegeven op de pagina. Bijvoorbeeld, hier is de vorm die op [ wordt gebaseerd onderzoeksspreadsheet ](/help/edge/assets/enquiry-form.docx):


   [![ de vorm van steekproefEDS van A ](/help/edge/assets/updated-form.png) ](https://main--wefinance--wkndform.aem.page/enquiry-form)

   Vul nu het formulier in en klik op de knop Verzenden. Er treedt een fout op, die lijkt op het volgende, omdat het werkblad nog niet is ingesteld op het accepteren van de gegevens.

   ![ fout op vormvoorlegging ](/help/edge/assets/form-error.png)

+++


## Volgende stap

[ bereidt uw spreadsheet ](/help/edge/docs/forms/submit-forms.md) voor beginnen goedkeurend gegevens op vormvoorlegging.


## Zie ook

{{see-more-forms-eds}}
