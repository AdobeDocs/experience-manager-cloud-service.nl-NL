---
title: Publish en AEM Forms-Edge Delivery Services
description: Publish en AEM Forms-Edge Delivery Services
feature: Edge Delivery Services
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Publish uw formulier en begin gegevens te verzamelen

Als u klaar bent om uw formulier met uw klanten te delen voor gegevensverzameling of verzending, kunt u het gewoon publiceren, zodat het formulier direct beschikbaar is voor uw klanten.

![ op document-gebaseerde het Authoring ecosysteem ](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Voorwaarden

* U hebt een AEM Project dat op [ wordt gebaseerd AEM Forms boilerplate ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) of [ toegevoegd Aangepast Forms Blok aan uw bestaand AEM Project ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)
* Uw formulier is volledig getest en klaar voor gebruik.
* Uw [ spreadsheet wordt gevormd ](/help/edge/docs/forms/submit-forms.md) om gegevens goed te keuren.


## Publish uw formulier

+++ 1. Publish uw spreadsheet

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw AEM Edge Delivery-projectmap.

1. Open het werkblad met het formulier. Bijvoorbeeld het werkboek `enquiry` form Microsoft Excel.

1. Gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef het blad.

   ![ AEM Sidekick van het Gebruik aan voorproef het blad ](/help/edge/assets/preview-form.png)

   Wanneer de voorvertoningsbewerking met succes is voltooid, wordt de spreadsheetinhoud omgezet in de JSON-indeling. De voorvertoningspagina presenteert deze inhoud vervolgens in een gestructureerde tabelindeling. Het bijhorende beeld illustreert bijvoorbeeld de inhoud van een &#39;enquêteformulier&#39;.

   ![ het Formaat van JSON van de Voorproef van Forms ](/help/edge/assets/forms-preview-json-format.png)

1. Gebruik AEM Sidekick om het blad te publiceren. Zorg ervoor dat u de publicatie-URL vastlegt, zoals is vereist voor het weergeven van het formulier in de volgende sectie. De URL-indeling is als volgt:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Bijvoorbeeld, als de bewaarplaats van uw project &quot;portaal&quot;wordt genoemd, is het gevestigd onder de rekening &quot;wkndforms&quot;, en u gebruikt de &quot;belangrijkste&quot;tak, kijkt URL als het volgende:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`

+++

+++ 2. Voeg het formulier toe aan uw webpagina

Voeg de `<form>.json` toe aan een webpagina om de interactie van de klant te vergemakkelijken, zodat invullers het formulier moeiteloos kunnen invullen en verzenden.


Het formulier toevoegen aan uw webpagina:

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw `[AEM Edge Delivery project directory]` .

1. Open een documentbestand waarin u het formulier wilt insluiten. U kunt bijvoorbeeld het `index.docx` -bestand openen of een nieuw document maken.

1. Bepaal de gewenste sectie in het document waar u het formulier wilt invoegen en navigeer naar de gewenste sectie.

1. Voeg een blok met de naam &#39;Form&#39; toe aan het bestand, vergelijkbaar met het onderstaande voorbeeld:

   | Formulier |
   |---|
   | [ https://main—wefinance—wkndforms.hlx.live/inquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |

   ![ voeg een blok genoemd &quot;Vorm&quot;aan het dossier ](/help/edge/assets/enquiry-doc-to-embed-form.png) toe

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de URL van het `<form>.json` -bestand toe als een hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.

   Gebruik de URL van de voorvertoning (.page URL) voor ontwikkelings- of testdoeleinden of de URL van de publicatie (.live) voor productiedoeleinden. Hier volgen enkele voorbeelden van URL&#39;s voor voorvertonen en publiceren:

   **Voorproef URL**

   | Formulier |
   |---|
   | [ https://main—wefinance—wkndforms.hlx.page/inquiry.json](https://main--wefinance--wkndforms.hlx.page/enquiry.json) |


   **Publish URL**

   | Formulier |
   |---|
   | [ https://main—wefinance—wkndforms.hlx.live/inquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |

1. Gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef de webpagina. Het formulier wordt nu weergegeven op de pagina. Bijvoorbeeld, hier is de vorm die op [ wordt gebaseerd onderzoeksspreadsheet ](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   ![ de vorm van steekproefEDS van A ](/help/edge/assets/eds-form.png)

1. Gebruik AEM Sidekick om het formulier te publiceren. Uw klanten kunnen het formulier nu invullen en verzenden.

+++

## Problemen oplossen

+++ Kan gegevens niet naar formulier verzenden

Als u een fout die op het volgende bericht lijkt ontmoet, wijst het erop dat spreadsheet niet wordt gevormd om [ de voorgelegde ](/help/edge/docs/forms/submit-forms.md) gegevens nog goed te keuren.

![ fout op vormvoorlegging ](/help/edge/assets/form-error.png)

+++


## Zie ook

{{see-more-forms-eds}}
