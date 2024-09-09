---
title: Aan de slag met Edge Delivery Services voor AEM Forms. Maak een formulier.
description: Creëer snelle perfecte formulieren! ⚡ op AEM Forms Edge Delivery gebaseerde authoring = razendsnelheid en SEO-vriendelijke formulieren voor gelukkige gebruikers en zoekmachines.
feature: Edge Delivery Services
exl-id: 0cf881a2-3784-45eb-afe8-3435e5e95cf4
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# Een formulier maken met Adaptief Forms-blok

>[!VIDEO](https://video.tv.adobe.com/v/3427881?quality=12&learn=on)

AEM Forms Edge Delivery biedt een blok, Adaptive Forms Block genaamd, waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. U kunt [ tot een nieuw AEM project leiden dat met het AanpassingsBlok van Forms ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) wordt gevormd of [ het AanpassingsBlok van Forms aan een bestaand AEM ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) toevoegt.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft SharePoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

![ op document-gebaseerde het Authoring ecosysteem ](/help/edge/assets/document-based-authoring-workflow-create-form.png)


## Vereisten

Controleer voordat u begint of u de volgende stappen hebt uitgevoerd:

* Opstelling een [ AEM project gebruikend AEM Forms boilerplate ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) of [ toegevoegd Aangepast Forms Blok aan uw bestaand AEM Project ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) en kloon de overeenkomstige bewaarplaats GitHub op uw lokale machine.
In dit document wordt de lokale map van het EDS-project (Edge Delivery Services) `[EDS Project repository]` genoemd.
* Zorg ervoor dat u toegang hebt tot Google Sheets of Microsoft SharePoint. Aan opstelling Microsoft SharePoint als uw inhoudsbron, zie [ hoe te SharePoint ](https://www.aem.live/docs/setup-customer-sharepoint) gebruiken.



## Een formulier maken

<!-- 

+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery Service Site. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
1. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

1. on your local machine and copy the `form` folder. 
1. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

* **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

* **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project.

+++

-->

+++ Stap 1: Een formulier ontwerpen met Microsoft Excel of Google Sheet.

In plaats van door complexe processen te navigeren, kunt u zonder problemen een formulier maken met behulp van een spreadsheet. U kunt de rijen en kolommen definiëren die de formulierstructuur vormen. Elke rij vertegenwoordigt een individueel [ vormgebied ](/help/edge/docs/forms/form-components.md#available-components) en de kolomkopballen bepalen de overeenkomstige [ gebiedseigenschappen ](/help/edge/docs/forms/form-components.md#components-properties).

Neem bijvoorbeeld het volgende spreadsheet waar rijomtrekvelden voor een `enquiry` -formulier en kolomkoppen hun eigenschappen definiëren:

![ Opiniepeiling spreadsheet ](/help/edge/assets/enquiry-form-spreadsheet.png)

Ga als volgt te werk om het formulier te maken:

1. Open uw AEM Edge Delivery-projectmap op Microsoft SharePoint of Google Drive.

1. Maak een Microsoft Excel-werkboek of Google-werkblad in de AEM Edge Delivery-projectmap. Maak bijvoorbeeld een werkblad met de naam `enquiry` in AEM Edge Delivery-projectmap op Google Drive.

   ![ Inhoud van de Steekproef op de Aandrijving van Google ](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

1. Zorg ervoor dat het blad met de aangewezen AEM gebruiker (bijvoorbeeld `helix@adobe.com`) [ zoals per de configuraties wordt gedeeld die voor uw project ](https://www.aem.live/docs/setup-customer-sharepoint) worden gespecificeerd. Hiermee geeft u de gebruiker bewerkingsmachtigingen voor het blad.

1. Open het gemaakte werkblad en wijzig de naam van het standaardwerkblad in &#39;shared-default&#39;.

   ![ anders noem standaardblad aan &quot;gedeeld-gebrek&quot;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Als u formuliervelden wilt toevoegen, voegt u rijen en kolomkoppen in het &#39;standaard-gedeelde&#39; blad in. Elke rij zou a [ vormgebied ](/help/edge/docs/forms/form-components.md#available-components), met kolomkopballen moeten vertegenwoordigen die de overeenkomstige gebied [ eigenschappen ](/help/edge/docs/forms/form-components.md#components-properties) bepalen.


   Voor een snel begin, overweeg het kopiëren van de inhoud van het [ Onderzoek spreadsheet ](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) in uw spreadsheet. Sla het werkblad op nadat u de inhoud hebt gekopieerd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef het blad.

   ![ AEM Sidekick van het Gebruik aan voorproef het blad ](/help/edge/assets/preview-form.png)

   Als u een voorbeeld bekijkt, wordt de inhoud van het blad op de tabbladen van de nieuwe browser in JSON-indeling weergegeven. Zorg ervoor dat u de voorbeeld-URL vastlegt, zoals dit is vereist voor het weergeven van het formulier in de volgende sectie. De URL-indeling is als volgt:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Bijvoorbeeld, als de bewaarplaats van uw project &quot;portaal&quot;wordt genoemd, is het gevestigd onder de rekening &quot;wkndforms&quot;, en u gebruikt de &quot;belangrijkste&quot;tak, kijkt URL als het volgende:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ Stap 2: Geef een voorbeeld van het formulier weer met de pagina EDS (Edge Delivery Services).


Tot nu toe hebt u de structuur van het formulier voorbereid. Nu een voorbeeld van het formulier weergeven:

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw AEM Edge Delivery-projectmap.



1. Open een documentbestand (bijvoorbeeld een indexbestand) om het formulier in te sluiten. U kunt ook een nieuw document maken.

1. Ga naar de gewenste locatie in het document waar u het formulier wilt toevoegen.

1. Een formulierblok maken om het formulier te genereren. Selecteer Invoegen > Tabel en maak een tabel met één kolom en twee rijen. Geef de tabel een naam &quot;Formulier&quot; en plak de voorbeeld-URL in de tweede rij. Zorg ervoor dat de URL is opgemaakt als een hyperlink, niet als onbewerkte tekst, zoals hieronder wordt geïllustreerd:

   | Formulier |
   |---|
   | [ https://main—wefinance—wkndforms.hlx.live/inquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |


   ![ voeg Aangepast Forms Blok aan uw webpagina toe ](/help/edge/assets/add-adaptive-forms-block.png)

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de voorbeeld-URL van het `<form>.json` -bestand toe als hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.


1. Gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef het document. Het formulier wordt nu weergegeven op de pagina. Bijvoorbeeld, hier is de vorm die op [ wordt gebaseerd onderzoeksspreadsheet ](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![ de vorm van steekproefEDS van A ](/help/edge/assets/eds-form.png) ](https://main--portal--wkndforms.hlx.live/)

   Vul nu het formulier in en klik op de knop Verzenden. Er treedt een fout op, die lijkt op het volgende, omdat het werkblad nog niet is ingesteld op het accepteren van de gegevens.

   ![ fout op vormvoorlegging ](/help/edge/assets/form-error.png)

+++


## Volgende stap

[ bereidt uw spreadsheet ](/help/edge/docs/forms/submit-forms.md) voor beginnen goedkeurend gegevens op vormvoorlegging.


## Zie ook

{{see-more-forms-eds}}
