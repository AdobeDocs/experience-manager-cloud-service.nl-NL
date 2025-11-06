---
title: Van spreadsheets naar Forms - Aangepaste Forms-blokvalidaties uitvoeren
description: Krachtige formulieren sneller maken met spreadsheets en Adaptieve Forms Block Fields! Deze handleiding helpt u bij het maken van aangepaste validaties voor EDS Forms Block-velden.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 16e1d42a-42d0-4335-ba81-feedea7ed7d7
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Validaties toevoegen aan formuliervelden

Adaptive Forms Block heeft ingebouwde validatiefuncties. Deze validaties worden automatisch toegepast in moderne browsers op basis van het gekozen veldtype en de aanvullende eigenschappen die u opgeeft.

## Veldtypen en validatie

Het Adaptieve Blok van Forms steunt een verscheidenheid van [ HTML-5 inputtypes ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), met inbegrip van tekst, e-mail, aantal, datum, en meer. Het past ook [ textarea ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), uitgezocht, en gebiedsreeks, samen met uitvoerige eigenschappen van de inputbevestiging inherent aan HTML-5 aan.

gebruikt HTML-veldtypen om het type gegevens te definiëren dat een gebruiker kan invoeren. Verschillende veldtypen hebben verschillende ingebouwde validatieregels:

E-mail: Dit veldtype bevestigt automatisch gebruikersinvoer op een gemeenschappelijke e-mailadresformaat. Gebruikers die een ongeldig e-mailbericht invoeren, zien een foutbericht.
Getal: dit veldtype staat alleen numerieke invoer toe. Gebruikers die niet-numerieke tekens invoeren, ontvangen een fout.
Datum: dit veldtype valideert de gebruikersinvoer op basis van een standaarddatumnotatie. Datums buiten een redelijk bereik kunnen ook als ongeldig worden gemarkeerd.
URL: Dit veldtype valideert de gebruikersinvoer op basis van een geldige URL-indeling. Gebruikers die een ongeldige URL invoeren, krijgen een foutbericht te zien.
Tel: Dit veldtype is specifiek ontworpen voor telefoonnummers en kan validatie op basis van specifieke landindelingen (niet universeel ondersteund) activeren.



