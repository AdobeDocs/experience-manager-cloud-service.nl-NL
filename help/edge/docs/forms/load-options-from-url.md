---
title: Opties vervolgkeuzelijst laden vanaf URL
description: De opties voor de vervolgkeuzelijst worden opgenomen in een afzonderlijk spreadsheet en vervolgens geïmporteerd in het primaire spreadsheet via de opgegeven URL.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Opties voor vervolgkeuzelijsten laden via URL

In Edge Delivery Services-formulieren kunnen gebruikers een waarde selecteren uit een vooraf gedefinieerde set opties. Auteurs van formulieren gebruiken de `select` -element, dat een keuzelijst biedt.
Bijvoorbeeld de `enquiry` het formulier bevat een vervolgkeuzemenu voor het selecteren van landen, waarin gebruikers een reeks vooraf gedefinieerde landen kunnen kiezen. Deze lijst bevat een lange lijst met landen, gescheiden door komma&#39;s.

![Vervolgkeuzemogelijkheden](/help/forms/assets/drop-down-options.png)

Het beheren van lange lijsten met opties voor vervolgkeuzemenu&#39;s kan lastig zijn wanneer u deze rechtstreeks toevoegt aan het werkblad met de definitie van het formulier. Het maken van een apart blad waarin deze vervolgkeuzemogelijkheden worden opgeslagen, kan het proces vereenvoudigen en stroomlijnen. Dit blad fungeert als een gecentraliseerde opslagplaats voor alle vervolgkeuzemogelijkheden, in een gestructureerde indeling gerangschikt. Elke optie wordt in een eigen rij vermeld, waardoor het beheer en de updates eenvoudiger worden.

Laten we het verbeteren van het formulierontwerpproces verkennen door de lijst met opties via een URL te laden vanuit een ander spreadsheet.

Aan het einde van dit artikel leert u:

* [Opties definiëren in een afzonderlijke spreadsheet](#define-options)
* [URL toevoegen om opties voor vervolgkeuzelijsten te laden](#add-url)

## Opties definiëren in een afzonderlijk blad {#define-options}

Een blad maken met twee kolommen:`Option` en `Value`om de opties te definiëren:

1. Ga naar de map met uw AEM Project in de map Microsoft® SharePoint of Google Drive.
2. Een werkblad met de naam toevoegen `shared-country` op Microsoft® SharePoint Site of in uw Google Drive-map en voeg het volgende toe:

   * **Optie**: Geeft de weergavewaarden van de opties in het keuzemenu aan.
   * **Waarde**: Geeft de verzonden waarde aan wanneer een gebruiker de optie selecteert.

   >[!NOTE]
   >
   > Als de waarde en de optie voor een vervolgkeuzemogelijkheid gelijk zijn, kan het werkblad alleen de **Optie** kolom.

   Laten we een nieuw blad toevoegen. [gezamenlijk land](/help/forms/assets/enquiry-options.xlsx) voor de opties in het dialoogvenster `Destination` vervolgkeuzelijst in de `enquiry` formulier.

   Verwijs naar de illustratie hieronder, die het `shared-country` spreadsheet:

   ![Vervolgkeuzelijst voor land](/help/forms/assets/drop-down-country-options.png)
3. De voorvertoning en de publicatie van de `shared-country` blad gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

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


