---
title: HTML-e-mailsjablonen in Adaptive Forms op Forms as a Cloud Service
description: Leer e-mailsjablonen te gebruiken met adaptieve formulieren.
feature: Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: eb2c451019e1c9d6f48558154ee58598bd1f2e02
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# E-mailsjablonen in Adaptieve Forms

Met Adaptive Forms kunt u e-mailsjablonen voor HTML en normale tekst gebruiken. Met e-mailsjablonen voor HTML kunt u rijke, persoonlijke en visueel aantrekkelijke e-mails verzenden wanneer een formulier wordt verzonden. Deze e-mailberichten kunnen worden aangepast met formuliergegevens en uitgebreid met behulp van verschillende e-mailtags, zoals afbeeldingen en koppelingen. Met Adaptief Forms kunt u een bestand uploaden dat een HTML-sjabloon bevat of een normale teksteditor gebruiken om deze sjablonen te maken.

![ HTML e-mailmalplaatjes ](/help/forms/assets/html-email.png)

Met dit artikel kunt u e-mailsjablonen configureren en gebruiken in Adaptive Forms. Tegen het einde kunt u het volgende doen:

* [Een HTML-sjabloon configureren voor een adaptief formulier](#configure-an-html-template-for-an-adaptive-form)
* [Een e-mailsjabloon met normale tekst configureren voor een adaptief formulier](#configure-a-plain-text-template-for-an-adaptive-form)
* [Formuliergegevens gebruiken in uw e-mailsjablonen](#use-form-data-in-your-email-templates)


Hier volgt een kort overzicht van de betrokken stappen:

1. Open het adaptieve formulier voor bewerking.
1. Vorm [ verzenden E-mail ](/help/forms/configure-submit-action-send-email.md) voorlegt actie.
1. Selecteer of upload een HTML-sjabloon of voer de e-mailsjabloon handmatig in.
1. Test uw e-mailconfiguratie.

## Een HTML-sjabloon configureren voor een adaptief formulier

U kunt opstelling een Aangepast Vorm om een e-mail op voorlegging te verzenden gebruikend [**verzendt e-mail** voorlegt actie ](/help/forms/configure-submit-action-send-email.md). De actie verstrekt twee methodes om een malplaatje van HTML te vormen:

### Optie 1: Een bestand selecteren dat de HTML-sjabloon bevat

Voordat u verdergaat, moet u ervoor zorgen dat u de HTML-sjabloon hebt geüpload naar uw AEM Forms-omgeving.

1. Open het adaptieve formulier voor bewerking.
1. Ga naar **Browser van de Inhoud**, selecteer de **Container van de Gids**, en tik het eigenschappen pictogram. Er wordt een dialoogvenster met de titel `Adaptive Form Container` weergegeven.
1. Ga naar het **lusje van de Verzending** en selecteer **verzenden e-mail** voorlegt actie.

   ![ verzend e-mail verzendt actie ](/help/forms/assets/send-email-action.png)

1. Laat de **externe malplaatje van het Gebruik** optie toe.
1. Laat de **HTML malplaatje van het Gebruik** optie toe.
1. Klik op het mappictogram voor de optie Extern sjabloonpad en blader naar de gewenste HTML-sjabloon.
1. Klik **Gedaan** om de configuratie te bewaren.

Uw HTML-sjabloon is nu geconfigureerd voor het adaptieve formulier.

### Optie 2: Een HTML-sjabloon handmatig invoeren of plakken

1. Open het adaptieve formulier voor bewerking.
1. Ga naar **Browser van de Inhoud**, selecteer de **Container van de Gids**, en tik het eigenschappen pictogram. Er wordt een dialoogvenster met de titel `Adaptive Form Container` weergegeven.
1. Ga naar het **lusje van de Verzending** en selecteer **verzenden e-mail** voorlegt actie.
1. Laat de **HTML malplaatje van het Gebruik** optie toe.
1. Type of deeg direct uw code van HTML in de verstrekte **E-mailMalplaatje** doos.


## Een sjabloon voor normale tekst configureren voor een adaptief formulier

U kunt opstelling een Aangepast Vorm om een e-mail op voorlegging te verzenden gebruikend [**verzendt e-mail** voorlegt actie ](/help/forms/configure-submit-action-send-email.md). De actie verstrekt twee methodes om een onbewerkte-tekstmalplaatje te vormen:

### Optie 1: Een bestand selecteren dat de sjabloon bevat

Voordat u verdergaat, moet u ervoor zorgen dat u de HTML-sjabloon hebt geüpload naar uw AEM Forms-omgeving.

1. Open het adaptieve formulier voor bewerking.
1. Ga naar **Browser van de Inhoud**, selecteer de **Container van de Gids**, en tik het eigenschappen pictogram. Er wordt een dialoogvenster met de titel `Adaptive Form Container` weergegeven.
1. Ga naar het **lusje van de Verzending** en selecteer **verzenden e-mail** voorlegt actie.
1. Laat de **externe malplaatje van het Gebruik** optie toe.
1. Klik het omslagpictogram voor de **Externe optie van de Weg van het Malplaatje** en doorblader om uw onbewerkt-tekstmalplaatje te selecteren.
1. Klik op Gereed om de configuratie op te slaan.

Uw sjabloon is nu geconfigureerd voor het adaptieve formulier.

### Optie 2: Een HTML-sjabloon handmatig invoeren of plakken

1. Open het adaptieve formulier voor bewerking.
1. Ga naar **Browser van de Inhoud**, selecteer de **Container van de Gids**, en tik het eigenschappen pictogram. Er wordt een dialoogvenster met de titel `Adaptive Form Container` weergegeven.
1. Ga naar het **lusje van de Verzending** en selecteer **verzenden e-mail** voorlegt actie.
1. Type of deeg direct uw onbewerkte-tekstmalplaatjecode in het verstrekte **E-mailvakje van het Malplaatje**.

## Formuliergegevens gebruiken in uw e-mailsjablonen

U kunt formuliergegevens in uw e-mailsjablonen opnemen met plaatsaanduidingen. Deze plaatsaanduidingen worden dynamisch vervangen door de werkelijke waarden van formuliervelden wanneer het e-mailbericht wordt verzonden. Bijvoorbeeld:

* $ {name}: De waarde van het gebied genoemd &quot;naam.&quot;
* $ {email}: De waarde van het gebied genoemd &quot;e-mail.&quot;
* $ {message}: De waarde van het gebied genoemd &quot;bericht.&quot;

### Voorbeeld van HTML-e-mailsjabloon

Hier is een voorbeeld van een HTML e-mailsjabloon waarin plaatsaanduidingen voor formuliergegevens worden gebruikt:

```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <title>Form Submission</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                line-height: 1.6;
                color: #333;
            }
            h2 {
                color: #0056b3;
            }
        </style>
    </head>
    <body>
        <h2>Thank You for Your Submission</h2>
        <p>Dear ${name},</p>
        <p>We have received your submission with the following details:</p>
        <ul>
            <li><strong>Email:</strong> ${email}</li>
            <li><strong>Phone Number:</strong> ${phone_number}</li>
            <li><strong>Message:</strong> ${message}</li>
        </ul>
        <p>We will get back to you soon!</p>
        <p>Best regards,</p>
        <p>Your Team</p>
    </body>
    </html>
```

### Voorbeeldsjabloon voor normale tekst

Hier volgt een voorbeeld van een sjabloon voor normale e-mail:

```TXT
    
    Subject: Thank You for Your Submission
    
    Dear ${name},
    
    We have received your submission with the following details:
    
    - Email: ${email}
    - Phone Number: ${phone_number}
    - Message: ${message}
    
    We will get back to you soon!
    
    Best regards,
    Your Team
```

## Aanbevolen procedures voor HTML-e-mailsjablonen

* Zorg ervoor dat uw stijlen inline zijn voor betere compatibiliteit met e-mailclients.
* Laat uw sjabloon reageren voor een betere ervaring op mobiele apparaten.
* Gebruik gereedschappen zoals Litmus of E-mail op zuur om een voorbeeld van uw e-mail te bekijken voor verschillende e-mailclients.
* Zorg ervoor dat de namen van de plaatsaanduidingen exact overeenkomen met de namen van de formuliervelden.
* Controleer of er ontbrekende of onjuiste tags voorkomen in uw HTML-sjabloon.
* Verifieer dat [ verzendt e-mail ](/help/forms/configure-submit-action-send-email.md) verzendt actie correct wordt gevormd.
