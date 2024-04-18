---
title: Opties vervolgkeuzelijst laden vanaf URL
description: De opties voor de vervolgkeuzelijst worden opgenomen in een afzonderlijk spreadsheet en vervolgens geïmporteerd in het primaire spreadsheet via de opgegeven URL.
feature: Edge Delivery Services
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# Opties voor vervolgkeuzelijsten laden via URL

Forms bevat vaak vervolgkeuzemenu&#39;s die gebruikers kunnen selecteren op basis van vooraf gedefinieerde opties. Deze opties worden doorgaans in het formulier zelf gedefinieerd, maar het beheren van lange lijsten kan lastig zijn. In deze handleiding wordt beschreven hoe u het ontwerpen van formulieren kunt verbeteren door meerkeuzeopties te laden vanuit een afzonderlijk spreadsheet via een URL.


De voordelen van het laden van een meerkeuzeoptie uit een afzonderlijk spreadsheet zijn:

* Vereenvoudigd beheer: houd meerkeuzeopties op een gecentraliseerde locatie voor eenvoudigere updates en toevoegingen.
* Verbeterde efficiëntie: u hoeft lange optielijsten niet handmatig toe te voegen aan de formulierdefinitie.




![Vervolgkeuzemogelijkheden](/help/forms/assets/drop-down-options.png)


Aan het einde van dit artikel leert u:

* [Opties definiëren in een afzonderlijke spreadsheet](#define-options)
* [URL toevoegen om opties voor vervolgkeuzelijsten te laden](#add-url)

## Opties definiëren in een afzonderlijk blad {#define-options}

Opties definiëren in een afzonderlijk werkblad

1. Een werkblad maken:
   1. Zoek de AEM projectmap in Microsoft® SharePoint of Google Drive.
   1. Voeg een nieuw blad toe. Bijvoorbeeld &#39;gezamenlijk-land&#39;.
1. Optie-kolommen definiëren: twee kolommen toevoegen: &quot;Optie&quot; en &quot;Waarde&quot;.
   * Met Option wordt de tekst gedefinieerd die in het vervolgkeuzemenu wordt weergegeven.
   * &quot;Waarde&quot; definieert de verzonden waarde wanneer een gebruiker de optie selecteert.

   >[!NOTE]
   >
   >Als zowel de optie als de waarde identiek zijn, is alleen de kolom &quot;Optie&quot; vereist.

1. Vul het werkblad: voer uw landopties in de kolom &quot;Optie&quot; (en &quot;Waarde&quot;, indien nodig).

   Zie het onderstaande voorbeeld voor structuur.

   ![Vervolgkeuzelijst voor land](/help/forms/assets/drop-down-country-options.png)

1. De voorvertoning en de publicatie van de `shared-country` blad gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Raadpleeg de URL die de `shared-country` sheet: https://main—wefinance—wkndforms.hlx.live/inquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` is een queryparameter die aan de URL is toegevoegd. Deze parameter geeft de JSON aan die is gefilterd op basis van de `shared-country` blad. Het wordt doorgestuurd naar het JSON-bestand met informatie over verschillende landen.

## URL toevoegen om opties voor vervolgkeuzelijsten te laden{#add-url}

De `Options` eigenschap van een `select` -veld accepteert een URL. De URL retourneert een JSON-array die wordt gebruikt als opties voor de `Destination` vervolgkeuzelijst. U voegt als volgt de URL toe voor het laden van opties in de vervolgkeuzelijst:

1. Ga naar de map AEM Project op Microsoft® SharePoint of Google Drive en open uw spreadsheet. U kunt ook een nieuw werkblad voor een formulier maken.
1. De URL kopiëren van `shared-country` blad en plak het in het `Options` kolom voor de `Destination` veld.

   ![Opzoekblad](/help/forms/assets/drop-down-enquiry.png)

1. Het blad voorvertonen en publiceren met [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Vervolgkeuzelijst voor land](/help/forms/assets/load-dropdown-options-form.png)

U kunt verwijzen naar de [spreadsheet vragen](/help/forms/assets/enquiry-options.xlsx) om de URL toe te voegen voor het laden van opties in de vervolgkeuzelijst.

Nadat u de URL in de formulierdefinitie hebt geïntegreerd om vervolgkeuzelijstopties te laden, kunt u de opties voor de `Destination` drop-down begin verschijnt van URL.

Raadpleeg de onderstaande URL, die de `enquiry` formulier met de opties die op het afzonderlijke blad zijn opgeslagen:

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## Zie ook

{{see-more-forms-eds}}


