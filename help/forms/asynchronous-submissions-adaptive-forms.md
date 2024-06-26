---
title: Hoe te om Asynchrone Verzending voor AEM Aangepaste Forms te vormen?
description: Leer hoe u de asynchrone verzending voor Adaptive Forms configureert. Dig dieper in op de werking van asynchrone verzending voor Adaptive Forms.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 026f4920-f8f9-4b08-b1b0-af50229633d7
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---

# Asynchrone verzending van AEM Adaptieve Forms configureren {#asynchronous-submission-of-adaptive-forms}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/asynchronous-submissions-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |


Webformulieren zijn meestal geconfigureerd voor synchroon verzenden. Bij synchrone verzending worden gebruikers die een formulier verzenden, omgeleid naar een bevestigingspagina, een pagina om te bedanken of een pagina om een fout op te lossen bij het verzenden. De moderne webervaringen, zoals toepassingen met één pagina, worden echter steeds populairder, omdat de webpagina statisch blijft terwijl interactie tussen client en server op de achtergrond plaatsvindt. U kunt asynchrone verzending configureren om deze ervaring te bieden met Adaptive Forms.

Wanneer een gebruiker een formulier verzendt bij asynchrone verzending, voegt de ontwikkelaar een aparte ervaring in, zoals het omleiden naar een ander formulier of een aparte sectie van de website. De auteur kan ook afzonderlijke services insluiten, zoals het verzenden van gegevens naar een andere gegevensopslagruimte of het toevoegen van een aangepaste analytische engine. Bij asynchrone verzending gedraagt een adaptief formulier zich als een toepassing van één pagina, aangezien het formulier niet opnieuw wordt geladen of de URL niet verandert wanneer de verzonden formuliergegevens op de server worden gevalideerd.

Lees verder voor meer informatie over asynchrone verzending in Adaptive Forms.

## asynchrone verzending configureren {#configure}

Om asynchrone voorlegging voor een Aangepast Vorm te vormen:

1. Selecteer in de ontwerpmodus Adaptief formulier het object Form Container en selecteer ![cmppr1](assets/configure-icon.svg) om de eigenschappen te openen.
1. In de **[!UICONTROL Submission]** eigenschappensectie, inschakelen **[!UICONTROL Use asynchronous submission]**.
1. In de **[!UICONTROL On Submit]** selecteert u een van de volgende opties voor het verzenden van formulieren.

   * **[!UICONTROL Redirect to URL]**: leidt bij het verzenden van het formulier naar de opgegeven URL of pagina. U kunt een URL opgeven of bladeren naar het pad naar een pagina in het dialoogvenster **[!UICONTROL Redirect URL/Path]** veld.
   * **[!UICONTROL Show Message]**: geeft een bericht weer bij het verzenden van het formulier. U kunt een bericht schrijven in het tekstveld onder de **[!UICONTROL Show Message]** -optie. Het tekstveld ondersteunt RTF-opmaak.

1. Selecteren ![check-button1](assets/save_icon.svg) om de eigenschappen op te slaan.

## Hoe asynchrone verzending werkt {#how-asynchronous-submission-works}

[!DNL Experience Manager Forms] biedt foutafhandelaars voor het verzenden van formulieren die buiten de box vallen. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een formulier wordt verzonden, worden de gegevens voor validatie naar de server verzonden, die een reactie op de client retourneert met informatie over de gebeurtenis &#39;success&#39; of &#39;error&#39; voor de verzending. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren.

Bovendien kunnen auteurs en ontwikkelaars van formulieren regels op formulierniveau schrijven om standaardhandlers te overschrijven. Zie voor meer informatie [Standaardhandlers negeren met behulp van regels](#custom).

Laat ons eerst de serverreactie voor succes en foutengebeurtenissen herzien.

### Serverreactie voor gebeurtenis met succes voor verzending {#server-response-for-submission-success-event}

De structuur voor de serverreactie voor het indienen van succesgebeurtenissen is als volgt:

```json
{oneOf: [
{  properties : {
     contentType : {"type" : "string",  "enum" : ["xmlschema", "jsonschema"]},
    data : {type : "string", description : "Form data in XML or  JSON  format"},
   thankYouOption : {type : "string"}
   }},
  properties : {
     contentType : {"type" : "string",  "enum" : ["xmlschema", "jsonschema"]},
    data : {type : "string", description : "Form data in XML or  JSON  format"},
   thankYouContent: {type: "string"}
   }
]

}
```

De reactie van de server in het geval van een geslaagde verzending van het formulier omvat:

* Formuliergegevensindelingstype: XML of JSON
* Formuliergegevens in XML- of JSON-indeling
* Geselecteerde optie om naar een pagina om te leiden of een bericht te tonen zoals die in vorm wordt gevormd
* Pagina-URL of inhoud van bericht zoals geconfigureerd in het formulier

De succesmanager leest de serverreactie en richt dienovereenkomstig aan de gevormde pagina URL of toont een bericht opnieuw.

### Serverreactie voor verzendfoutgebeurtenis {#server-response-for-submission-error-event}

De structuur voor de serverreactie voor de gebeurtenis van de voorleggingsfout is als volgt:

```json
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

De reactie van de server in het geval van een fout bij het verzenden van het formulier omvat:

* Reden voor de fout, mislukte CAPTCHA- of servervalidatie
* Lijst met foutobjecten, die de SOM-expressie bevat van het veld waarvan de validatie is mislukt en het bijbehorende foutbericht

De fouthandler leest de serverreactie en geeft dienovereenkomstig het foutbericht op het formulier weer.

## Standaardhandlers negeren met behulp van regels {#custom}

Formulierontwikkelaars en auteurs kunnen regels schrijven op formulierniveau om standaardhandlers te overschrijven. De serverreactie voor geluids- en foutgebeurtenissen wordt weergegeven op formulierniveau, waartoe ontwikkelaars toegang hebben via `$event.data` in regels.

Voer de volgende stappen uit om regels te schrijven voor het afhandelen van geluids- en foutgebeurtenissen.

1. Open het Adaptief formulier in de ontwerpmodus, selecteer een willekeurig formulierobject en selecteer ![edit-rules1](assets/edit-rules-icon.svg) om de regeleditor te openen.
1. Selecteren **[!UICONTROL Form]** in de structuur Formulierobjecten en selecteer **[!UICONTROL Create]**.
1. Kies **[!UICONTROL is submitted successfully]** of **[!UICONTROL submission fails]** van de **[!UICONTROL Select state]** vervolgkeuzelijst.
1. Een **[!UICONTROL Then]** actie voor de geselecteerde status. Selecteer bijvoorbeeld **[!UICONTROL Navigate To]** en typ of plak vervolgens een URL. U kunt ook elke functie slepen met de **[!UICONTROL Functions]** aan de regel.

   ![geslaagde verzendhandler](assets/form-submission-handler.png)

1. Selecteren **[!UICONTROL Done]** om de regel op te slaan.