---
title: Opties vervolgkeuzelijst laden vanaf een URL of een ander blad voor Edge Delivery Services voor AEM Forms as a Cloud Service
description: De opties voor de vervolgkeuzelijst worden opgenomen in een afzonderlijk spreadsheet en vervolgens geïmporteerd in het primaire spreadsheet via de opgegeven URL.
feature: Edge Delivery Services
exl-id: 5b0bc1b6-6e33-41f3-b7c1-4d997787b6cd
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---


# Opties van een URL of een ander blad voor Edge Delivery Services for AEM Forms as a Cloud Service

Forms bevat vaak vervolgkeuzemenu&#39;s die gebruikers kunnen selecteren op basis van vooraf gedefinieerde opties. Deze opties worden doorgaans in het formulier zelf gedefinieerd, maar het beheren van lange lijsten kan lastig zijn. In deze handleiding wordt beschreven hoe u het ontwerpen van formulieren kunt verbeteren door meerkeuzeopties te laden vanuit een afzonderlijk spreadsheet via een URL.


De voordelen van het laden van een meerkeuzeoptie uit een afzonderlijk spreadsheet zijn:

- Vereenvoudigd beheer: houd meerkeuzeopties op een gecentraliseerde locatie voor eenvoudigere updates en toevoegingen.
- Verbeterde efficiëntie: u hoeft lange optielijsten niet handmatig toe te voegen aan de formulierdefinitie.

![&#x200B; drop-down opties &#x200B;](/help/forms/assets/drop-down-options.png)


Aan het einde van dit artikel leert u:

- [Opties definiëren in een afzonderlijke spreadsheet](#define-options)
- [URL toevoegen om opties voor vervolgkeuzelijsten te laden](#add-url)

## Opties definiëren in een afzonderlijk blad {#define-options}

Opties definiëren in een afzonderlijk werkblad

1. Een werkblad maken:
   1. Zoek de AEM-projectmap in Microsoft® SharePoint of Google Drive.
   1. Voeg een nieuw blad toe. Bijvoorbeeld &#39;gezamenlijk-land&#39;.
1. Optie-kolommen definiëren:
Voeg twee kolommen toe: &quot;Optie&quot; en &quot;Waarde&quot;.
   - Met Option wordt de tekst gedefinieerd die in het vervolgkeuzemenu wordt weergegeven.
   - &quot;Waarde&quot; definieert de verzonden waarde wanneer een gebruiker de optie selecteert.

   >[!NOTE]
   >
   >Als zowel de optie als de waarde identiek zijn, is alleen de kolom &quot;Optie&quot; vereist.

1. Werkblad vullen:
Voer uw landopties in de kolom &quot;Optie&quot; (en &quot;Waarde&quot;, indien nodig) in.

   Zie het onderstaande voorbeeld voor structuur.

   ![&#x200B; drop-down voor land &#x200B;](/help/forms/assets/drop-down-country-options.png)

1. Voorproef en publiceer het `shared-country` blad gebruikend [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndform&#39; en gebruikt u de &#39;main&#39;-vertakking, de URL die het `shared-country` -blad toont:
   `https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country`
   <!--(https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country)  -->

>[!NOTE]
>
> `?sheet=country` is een queryparameter die aan de URL is toegevoegd. Deze parameter geeft aan welke JSON is gefilterd op basis van het `shared-country` sheet. Het wordt doorgestuurd naar het JSON-bestand met informatie over verschillende landen.

## URL toevoegen om opties voor vervolgkeuzelijsten te laden{#add-url}

De eigenschap `Options` van een `select` -veld accepteert een URL. De URL retourneert een JSON-array die wordt gebruikt als opties voor de vervolgkeuzelijst `Destination` . U voegt als volgt de URL toe voor het laden van opties in de vervolgkeuzelijst:

1. Ga naar de map AEM Project op Microsoft® SharePoint of Google Drive en open uw spreadsheet. U kunt ook een nieuw werkblad voor een formulier maken.
1. Kopieer de URL van `shared-country` sheet en plak deze in de `Options` kolom voor het `Destination` veld.

   ![&#x200B; Opiniepeiling spreadsheet &#x200B;](/help/forms/assets/drop-down-enquiry.png)

1. Voorproef en publiceer het blad gebruikend [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![&#x200B; drop-down voor land &#x200B;](/help/forms/assets/load-dropdown-options-form.png)

U kunt naar [&#x200B; onderzoeksspreadsheet &#x200B;](/help/edge/assets/enquiry.xlsx) verwijzen om URL toe te voegen om drop-down lijstopties te laden.

Nadat u de URL in de formulierdefinitie hebt geïntegreerd om vervolgkeuzelijstopties te laden, worden de opties voor de vervolgkeuzelijst `Destination` weergegeven via de URL.

Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndform&#39; en gebruikt u de &#39;main&#39;-vertakking, geeft de onderstaande URL het `enquiry` -formulier weer met de opties die in het afzonderlijke blad zijn opgeslagen:

`https://main--wefinance--wkndform.aem.live/enquiry-form`



