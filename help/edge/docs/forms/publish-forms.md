---
title: Een AEM Forms-formulier voor Edge Delivery Services publiceren
description: Een AEM Forms-formulier voor Edge Delivery Services publiceren
feature: Edge Delivery Services
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
source-git-commit: 708b63aca6b1613dbedf193edd07aadc510ff859
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Uw formulier publiceren en gegevens verzamelen

Als u klaar bent om uw formulier met uw klanten te delen voor gegevensverzameling of verzending, kunt u het gewoon publiceren, zodat het formulier direct beschikbaar is voor uw klanten.

![Ontwerpecosysteem op basis van documenten](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Voorwaarden

* U hebt een AEM project gebaseerd op [AEM Forms boilerplate](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) of [Aangepast Forms-blok toegevoegd aan uw bestaande AEM-project](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)
* Uw formulier is volledig getest en klaar voor gebruik.
* Uw [spreadsheet is geconfigureerd](/help/edge/docs/forms/submit-forms.md) om gegevens te accepteren.


## Uw formulier publiceren

+++ 1. Uw spreadsheet publiceren

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw AEM Edge Delivery-projectdirectory.

1. Open het werkblad met het formulier. Bijvoorbeeld de `enquiry` formulier Microsoft Excel-werkmap.

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het blad weer te geven.

   ![AEM Sidekick gebruiken om een voorvertoning van het blad weer te geven](/help/edge/assets/preview-form.png)

   Wanneer de voorvertoningsbewerking met succes is voltooid, wordt de spreadsheetinhoud omgezet in de JSON-indeling. De voorvertoningspagina presenteert deze inhoud vervolgens in een gestructureerde tabelindeling. Het bijhorende beeld illustreert bijvoorbeeld de inhoud van een &#39;enquêteformulier&#39;.

   ![Forms Preview JSON-indeling](/help/edge/assets/forms-preview-json-format.png)

1. Gebruik AEM Sidekick om het blad te publiceren. Zorg ervoor dat u de publicatie-URL vastlegt, zoals is vereist voor het weergeven van het formulier in de volgende sectie. De URL-indeling is als volgt:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` Verwijst naar de tak van uw bewaarplaats GitHub.
   * `<repository>` duidt uw bewaarplaats GitHub aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Bijvoorbeeld, als de bewaarplaats van uw project &quot;portaal&quot;wordt genoemd, is het gevestigd onder de rekening &quot;wkndforms&quot;, en u gebruikt de &quot;belangrijkste&quot;tak, kijkt URL als het volgende:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`

+++

+++ 2. Voeg het formulier toe aan uw webpagina

Voeg de `<form>.json` naar een webpagina om interactie met de klant te vergemakkelijken, zodat invullers het formulier moeiteloos kunnen invullen en verzenden.


Het formulier toevoegen aan uw webpagina:

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw `[AEM Edge Delivery project directory]`.

1. Open een documentbestand waarin u het formulier wilt insluiten. U kunt bijvoorbeeld het dialoogvenster `index.docx` of maak een nieuw document.

1. Bepaal de gewenste sectie in het document waar u het formulier wilt invoegen en navigeer naar de gewenste sectie.

1. Voeg een blok met de naam &#39;Form&#39; toe aan het bestand, vergelijkbaar met het onderstaande voorbeeld:

   | Formulier |
   |---|
   | [https://main—wefinance—wkndforms.hlx.live/inquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |

   ![Voeg een blok met de naam &#39;Form&#39; toe aan het bestand](/help/edge/assets/enquiry-doc-to-embed-form.png)

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de URL van de `<form>.json` bestand als hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.

   Gebruik de URL van de voorvertoning (.page URL) voor ontwikkelings- of testdoeleinden of de URL van de publicatie (.live) voor productiedoeleinden. Hier volgen enkele voorbeelden van URL&#39;s voor voorvertonen en publiceren:

   **Voorbeeld-URL**

   | Formulier |
   |---|
   | [https://main—wefinance—wkndforms.hlx.page/inquiry.json](https://main--wefinance--wkndforms.hlx.page/enquiry.json) |


   **URL publiceren**

   | Formulier |
   |---|
   | [https://main—wefinance—wkndforms.hlx.live/inquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van de webpagina weer te geven. Het formulier wordt nu weergegeven op de pagina. Hier ziet u bijvoorbeeld het formulier dat is gebaseerd op de [spreadsheet vragen](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   ![Een voorbeeld-EDS-formulier](/help/edge/assets/eds-form.png)

1. Gebruik AEM Sidekick om het formulier te publiceren. Uw klanten kunnen het formulier nu invullen en verzenden.

+++

## Problemen oplossen

+++ Kan gegevens niet naar formulier verzenden

Als u een fout die op het volgende bericht lijkt ontmoet, wijst het erop dat spreadsheet niet aan wordt gevormd [de ingediende](/help/edge/docs/forms/submit-forms.md) nog gegevens.

![fout bij het verzenden van formulier](/help/edge/assets/form-error.png)

+++


## Zie ook

{{see-more-forms-eds}}
