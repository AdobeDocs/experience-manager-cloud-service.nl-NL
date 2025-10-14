---
title: Herhaalbare secties toevoegen aan een formulier
description: Herhaalbare secties toevoegen aan een EDS-formulier
feature: Edge Delivery Services
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Herhaalbare secties toevoegen aan een formulier

Met Adaptief Forms-blok kunt u een sectie of een component van een formulier herhaalbaar maken of toevoegen. Hierdoor kunnen gebruikers meerdere keren informatie invoeren voor hetzelfde type gegevens, waardoor het gemakkelijker wordt om informatie te verzamelen, zoals werkervaring of educatieve achtergrond.

Neem bijvoorbeeld een formulier dat wordt gebruikt om informatie over iemands werkervaring te verzamelen. U hebt mogelijk een herhaalbare sectie voor het vastleggen van details van elke vorige taak. De herhaalbare sectie zou doorgaans velden bevatten zoals de naam van het bedrijf, de functie, de datum van tewerkstelling en de verantwoordelijkheden op het gebied van de functie. De gebruiker kan veelvoudige instanties van de herhaalbare sectie toevoegen om informatie over elke baan in te gaan zij hebben gehouden.

Aan het einde van dit artikel leert u:

- [Een herhaalbare sectie in een formulier maken](#add-repeatable-sections-to-a-form)
- [Minimum- of maximumaantal herhalingen instellen in een formulier](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## Een herhaalbare sectie maken

Door een herhaalbare sectie in een formulier te maken, kunnen gebruikers meerdere exemplaren van dezelfde set gegevens invoeren, zodat herhalende informatie efficiënt kan worden verzameld. Een herhaalbare sectie maken in een formulier:

1. Ga naar uw Edge Deliver-projectmap op Microsoft SharePoint of Google Workspace en open uw spreadsheet.

1. Voeg een formulierveld toe met de eigenschap `type` ingesteld op `fieldset`
1. Geef `Name` van het veld op. De eigenschap name wordt gebruikt om een herhaalbare sectie te maken.
1. Schakel herhaalbaarheid in door `repeatable` in te stellen op `true` .
1. Geef een beschrijving `label` voor het veld op. Het fungeert als kop voor de herhaalbare sectie.

   Zie de onderstaande afbeelding voor een illustratie van een sectie over de arbeidsgeschiedenis in een sollicitatieformulier.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. Stel voor elk veld dat u in de sectie wilt opnemen, de eigenschap `Fieldset` ervan in op dezelfde naam die u in stap 3 hebt gekozen.

   Wijs bijvoorbeeld `experience` aan in de eigenschap Veldset van alle relevante velden die moeten worden opgenomen in de sectie `employment history` .

   ![&#x200B; voorbeeld van een herhaalbaar sectieveld en zijn eigenschappen &#x200B;](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. Het gebruik [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef en publiceert het blad. De herhaalbare sectie wordt toegevoegd aan het formulier.

   Onder de herhaalbare sectie, vinden de gebruikers intuïtieve **toevoegen** knoop, die de toevoeging van veelvoudige secties met gemak vergemakkelijkt.

   ![&#x200B; herhaalbare sectie, voegt knoop toe, om veelvoudige secties toe te voegen &#x200B;](/help/edge/assets/repeatable-section-example.png)


## Minimale en maximale herhalingen instellen

In formulierontwerp is het nuttig minimale en maximale herhalingen voor herhaalbare secties in te stellen. Op deze manier kunt u controle en consistentie instellen en gebruikers effectief begeleiden. Het minimum- of maximumaantal herhalingen instellen:

1. Ga naar uw Edge Deliver-projectmap op Microsoft SharePoint of Google Workspace en open uw spreadsheet.

1. Voor een veld van de eigenschappen `type` `fieldset` en `repeatable` ingesteld op `true` :

   - Stel de eigenschap `min` in om het minimale aantal keren op te geven dat de sectie kan worden herhaald.

   - Stel de eigenschap `max` in om het maximale aantal keren op te geven dat de sectie kan worden herhaald.

   ![&#x200B; plaats min en max bezit om het aantal tijden te specificeren de sectie kan worden herhaald &#x200B;](/help/edge/assets/repeatable-section-set-min-max.png)

1. Het gebruik [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef en publiceert het blad.

   Bij het toevoegen van een herhaalbare sectie, vinden de gebruikers een intuïtief **pictogram van de Schrapping**, makend het gemakkelijker om herhaalbare secties te verwijderen. Nadat deze secties zijn toegevoegd, kunnen ze niet worden verkleind tot minder instanties dan opgegeven door de eigenschap `min` . Op die manier wordt voldaan aan de minimumvereisten die voor het invullen van het formulier zijn ingesteld.


