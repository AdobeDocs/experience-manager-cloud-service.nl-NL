---
title: Herhaalbare secties toevoegen aan een formulier
description: Herhaalbare secties toevoegen aan een EDS-formulier
feature: Edge Delivery Services
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Herhaalbare secties toevoegen aan een formulier

Met Adaptief Forms-blok kunt u een sectie of een component van een formulier herhaalbaar maken of toevoegen. Hierdoor kunnen gebruikers meerdere keren informatie invoeren voor hetzelfde type gegevens, waardoor het gemakkelijker wordt om informatie te verzamelen, zoals werkervaring of educatieve achtergrond.

Neem bijvoorbeeld een formulier dat wordt gebruikt om informatie over iemands werkervaring te verzamelen. U hebt mogelijk een herhaalbare sectie voor het vastleggen van details van elke vorige taak. De herhaalbare sectie zou doorgaans velden bevatten zoals de naam van het bedrijf, de functie, de datum van tewerkstelling en de verantwoordelijkheden op het gebied van de functie. De gebruiker kan veelvoudige instanties van de herhaalbare sectie toevoegen om informatie over elke baan in te gaan zij hebben gehouden.

Aan het einde van dit artikel leert u:

* [Een herhaalbare sectie in een formulier maken](#add-repeatable-sections-to-a-form)
* [Minimum- of maximumaantal herhalingen instellen in een formulier](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## Een herhaalbare sectie maken

Door een herhaalbare sectie in een formulier te maken, kunnen gebruikers meerdere exemplaren van dezelfde set gegevens invoeren, zodat herhalende informatie efficiënt kan worden verzameld. Een herhaalbare sectie maken in een formulier:

1. Ga naar uw Edge Deliver-projectmap op de Microsoft SharePoint- of Google Workspace en open uw spreadsheet.

1. Voeg een formulierveld toe met de `type` eigenschap ingesteld op `fieldset`
1. Opgeven `Name` van het veld. De eigenschap name wordt gebruikt om een herhaalbare sectie te maken.
1. herhaalbaarheid inschakelen door deze in te stellen `repeatable` tot `true`.
1. Een beschrijvende waarde opgeven `label` voor het veld. Het fungeert als kop voor de herhaalbare sectie.

   Zie de onderstaande afbeelding voor een illustratie van een sectie over de arbeidsgeschiedenis in een sollicitatieformulier.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. Voor elk veld dat u in de sectie wilt opnemen, stelt u de `Fieldset` aan de naam die u in stap 3 hebt gekozen.

   Wijs bijvoorbeeld `experience` in de veldseteigenschap van alle relevante velden die in de `employment history` sectie.

   ![voorbeeld van een herhaalbaar sectieveld en de bijbehorende eigenschappen](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het blad weer te geven en het te publiceren. De herhaalbare sectie wordt toegevoegd aan het formulier.

   Onder de herhaalbare sectie vinden gebruikers een intuïtief **Toevoegen** gemakkelijk meerdere secties toe te voegen.

   ![herhaalbare sectie, knop Toevoegen, om meerdere secties toe te voegen ](/help/edge/assets/repeatable-section-example.png)


## Minimale en maximale herhalingen instellen

In formulierontwerp is het nuttig minimale en maximale herhalingen voor herhaalbare secties in te stellen. Op deze manier kunt u controle en consistentie instellen en gebruikers effectief begeleiden. Het minimum- of maximumaantal herhalingen instellen:

1. Ga naar uw Edge Deliver-projectmap op de Microsoft SharePoint- of Google Workspace en open uw spreadsheet.

1. Voor een veld van `type` `fieldset` en `repeatable` eigenschap ingesteld op `true`:

   * instellen `min` eigenschap om het minimale aantal keren op te geven dat de sectie kan worden herhaald.

   * instellen `max` eigenschap om het maximale aantal keren op te geven dat de sectie kan worden herhaald.

   ![Stel de eigenschap min en max in om op te geven hoe vaak de sectie kan worden herhaald](/help/edge/assets/repeatable-section-set-min-max.png)

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het blad weer te geven en het te publiceren.

   Bij het toevoegen van een herhaalbare sectie, vinden de gebruikers intuïtief **Verwijderen** pictogram, zodat secties die u kunt herhalen, gemakkelijker kunnen worden verwijderd. Als deze secties eenmaal zijn toegevoegd, kunnen ze niet worden verkleind tot minder exemplaren dan opgegeven door de `min` eigenschap. Op die manier wordt voldaan aan de minimumvereisten die voor het invullen van het formulier zijn ingesteld.

<!--

For example, consider a form used to collect information from users applying for a loan. . You may have a repeatable section for capturing details of each co-applicant. The repeatable section would typically contain fields such as co-co-applicant

The form allows users to provide personal information, including details of the co-applicants. Users can enter details for co-applicants, with this section being repeatable.

![Repeatable sections in forms](/help/forms/assets/eds-repeatable.png)

## Prerequisites

The [Adaptive Forms Block is enabled](/help/edge/docs/forms/create-forms.md) for your Edge Delivery Services project. 

## Add a repeatable section to a form 

Let's take an example of a loan application form. The form enables users to submit personal information. You can include co-applicant details using repeatable sections, with the option to add a minimum and maximum of three co-applicant sections.

"_You can use a Microsoft Excel file on your SharePoint Site or Google Sheet file on Google Drive to develop a form. Examples in this document are based on a [Microsoft Excel file on your SharePoint Site](https://www.aem.live/docs/setup-customer-SharePoint)._" 


To add repeatable sections in Edge Delivery:

1. [Author a form using Microsoft Excel](#author-form)
2. [Preview and publish the form](#preview-form)

### Author a form using Microsoft Excel {#author-form}

1. Go to your Edge Deliver project folder on Microsoft SharePoint or Google Workspace and open your spreadsheet. For example, open an a spreadsheet named `loan-application.xlsx`.

1. Add a new columns labeled `Repeatable` to the sheet contaning your form fields. By default, the `shared-default` sheet contains the form fields.  

1. Add new columns labeled as `Repeatable`, `Min`, and `Max` in your Microsoft Excel file.
1. Specify the value for the `Repeatable` column as `True` for the fieldset that you want to make repeatable.
1. Specify the values for the `Min` and `Max` columns. The `Min` value represents the minimum number of occurrences for which the panel repeats, while the `Max` value represents the maximum number of occurrences for which the panel repeats.
1. Save your Microsoft Excel file.
     
>[!NOTE]
>
> Here is the [Loan application](/help/forms/assets/loan-application.xlsx) excel sheet for your reference. 

### Preview/Publish the form using your Edge Delivery Service

1. Open or create new document file in a Microsft SharePoint Site to embed the Excel sheet  in it using a `Form Block`. For example, open the `index` file and add a `Form Block`.
2. Open the command prompt, navigate to your AEM Edge Delivery project directory on your local machine, and execute the command as `aem up`.

The form is accessible at `https://localhost:3000`, where clicking the `Add` button adds new repeatable section for entering co-applicant details. You can also delete the the repeatable section by clicking the `Delete` button. 

>[!NOTE]
>
> If you encounter a "Page Not Found" error while accessing your form at localhost, add the directory name of the Microsoft SharePoint Site in front of the URL where your form is located. For example, `http://localhost:3000/<dir-name>/`

-->


## Zie ook

{{see-more-forms-eds}}
