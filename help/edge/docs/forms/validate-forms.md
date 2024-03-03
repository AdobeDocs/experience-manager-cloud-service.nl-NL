---
title: Van spreadsheets naar Forms - Validaties voor adaptieve formulierblokvelden beheren
description: Krachtige formulieren sneller maken met spreadsheets en Adaptieve formulierblokvelden! Deze handleiding helpt u bij het maken van aangepaste validaties voor EDS Forms Block-velden.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Validaties toevoegen aan formuliervelden

Adaptief formulierblok heeft ingebouwde validatiefuncties. Deze validaties worden automatisch toegepast in moderne browsers op basis van het gekozen veldtype en de aanvullende eigenschappen die u opgeeft.

## Veldtypen en validatie

Het adaptieve formulierblok ondersteunt diverse [HTML-5-invoertypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), inclusief tekst, e-mail, nummer, datum en meer. Het biedt ook ruimte [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), selecteren en veldset, samen met uitgebreide invoervalideringsfuncties die inherent zijn aan HTML-5.

gebruikt de het gebiedstypes van HTML om het soort gegevens te bepalen een gebruiker kan ingaan. Verschillende veldtypen hebben verschillende ingebouwde validatieregels:

E-mail: Dit veldtype bevestigt automatisch gebruikersinvoer op een gemeenschappelijke e-mailadresformaat. Gebruikers die een ongeldig e-mailbericht invoeren, zien een foutbericht.
Getal: dit veldtype staat alleen numerieke invoer toe. Gebruikers die niet-numerieke tekens invoeren, ontvangen een fout.
Datum: dit veldtype valideert de gebruikersinvoer op basis van een standaarddatumnotatie. Datums buiten een redelijk bereik kunnen ook als ongeldig worden gemarkeerd.
URL: Dit veldtype valideert de gebruikersinvoer op basis van een geldige URL-indeling. Gebruikers die een ongeldige URL invoeren, krijgen een foutbericht te zien.
Tel: Dit veldtype is specifiek ontworpen voor telefoonnummers en kan validatie op basis van specifieke landindelingen (niet universeel ondersteund) activeren.


## Meer weergeven

* [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
* [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
* [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-forms.md)
* [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
* [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)