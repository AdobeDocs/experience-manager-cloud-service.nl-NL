---
title: Een Edge Delivery Services voor AEM Forms publiceren
description: Een Edge Delivery Services voor AEM Forms publiceren
feature: Edge Delivery Services
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# Uw formulier publiceren en gegevens verzamelen

Als u klaar bent om uw formulier met uw klanten te delen voor gegevensverzameling of verzending, kunt u het gewoon publiceren, zodat het formulier direct beschikbaar is voor uw klanten.

![ op document-gebaseerde het Authoring ecosysteem ](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Voorwaarden

- U hebt een Project van AEM dat op [ wordt gebaseerd AEM Forms boilerplate ](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) of [ toegevoegd Aangepast Forms Blok aan uw bestaand Project van AEM ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)
- Uw formulier is volledig getest en klaar voor gebruik.
- Uw [ spreadsheet wordt gevormd ](/help/edge/docs/forms/submit-forms.md) om gegevens goed te keuren.


## Uw formulier publiceren

+++ &#x200B;1. Uw spreadsheet publiceren

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar de AEM Edge Delivery-projectmap.

1. Open het werkblad met het formulier. Bijvoorbeeld, het [ vraag ](/help/edge/assets/enquiry.xlsx) van het werkboek van Microsoft Excel.

1. Het gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef het blad.

   ![ Gebruik AEM Sidekick om voorproef het blad ](/help/edge/assets/preview-form.png)

   Wanneer de voorvertoningsbewerking met succes is voltooid, wordt de spreadsheetinhoud omgezet in de JSON-indeling. De voorvertoningspagina presenteert deze inhoud vervolgens in een gestructureerde tabelindeling. Het bijhorende beeld illustreert bijvoorbeeld de inhoud van een &#39;enquêteformulier&#39;.

   ![ het Formaat van JSON van de Voorproef van Forms ](/help/edge/assets/forms-preview-json-format.png)

1. Gebruik AEM Sidekick om het blad te publiceren. Zorg ervoor dat u de publicatie-URL vastlegt, zoals is vereist voor het weergeven van het formulier in de volgende sectie. De URL-indeling is als volgt:


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form>.json
   ```

   - `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   - `<repository>` geeft uw GitHub-opslagplaats aan.
   - `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Bijvoorbeeld, als de bewaarplaats van uw project &quot;wefinance&quot;wordt genoemd, is het gevestigd onder de rekening &quot;wkndform&quot;, en u gebruikt de &quot;belangrijkste&quot;tak en vorm als &quot;onderzoek&quot;, kijkt URL als het volgende:

   `https://main--wefinance--wkndform.aem.live/enquiry.json`
&lt;!— (https://main—wefinance—wkndform.aem.live/inquiry.json)—>

+++

+++ &#x200B;2. Voeg het formulier toe aan uw webpagina

Voeg de `<form>.json` toe aan een webpagina om de interactie van de klant te vergemakkelijken, zodat invullers het formulier moeiteloos kunnen invullen en verzenden.


Het formulier toevoegen aan uw webpagina:

1. Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw `[AEM Edge Delivery project directory]` .

1. Open een documentbestand waarin u het formulier wilt insluiten. Bijvoorbeeld, kunt u het {[ dossier openen 0} vraag-form.docx, of anders, tot een nieuw document leiden.](/help/edge/assets/enquiry-form.docx)

1. Bepaal de gewenste sectie in het document waar u het formulier wilt invoegen en navigeer naar de gewenste sectie.

1. Voeg een blok met de naam &#39;Form&#39; toe aan het bestand. Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndform&#39; en gebruikt u de &#39;main&#39;-vertakking.

   | Formulier |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |

   ![ voeg een blok genoemd &quot;Vorm&quot;aan het dossier ](/help/edge/assets/enquiry-doc-to-embed-form.png) toe

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de URL van het `<form>.json` -bestand toe als een hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.

   Gebruik de URL van de voorvertoning (.page URL) voor ontwikkelings- of testdoeleinden of de URL van de publicatie (.live) voor productiedoeleinden.

   Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndform&#39; en gebruikt u de &#39;main&#39;-vertakking.

   Hier volgen enkele voorbeelden van URL&#39;s voor voorvertonen en publiceren:

   **Voorproef URL**

   | Formulier |
   |---|
   | `https://main--wefinance--wkndform.aem.page/enquiry.json` |


   **publiceer URL**

   | Formulier |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |

1. Het gebruik [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef de webpagina. Het formulier wordt nu weergegeven op de pagina. Bijvoorbeeld, hier is de vorm die op [ wordt gebaseerd onderzoeksspreadsheet ](/help/edge/assets/enquiry-form.docx):


   ![ de vorm van steekproefEDS van A ](/help/edge/assets/updated-form.png)

1. Gebruik AEM Sidekick om het formulier te publiceren. Uw klanten kunnen het formulier nu invullen en verzenden.

+++ 

## Problemen oplossen

+++ Kan gegevens niet naar formulier verzenden

Als u een fout die op het volgende bericht lijkt ontmoet, wijst het erop dat spreadsheet niet wordt gevormd om [ de voorgelegde ](/help/edge/docs/forms/submit-forms.md) gegevens nog goed te keuren.

![ fout op vormvoorlegging ](/help/edge/assets/form-error.png)

+++



