---
title: Tabelobject in interactieve communicatie-editor
description: Het Voorwerp van de lijst in Interactieve Communicatie Redacteur in AEM Forms laat auteurs toe om klantgerichte lijsten in communicatie malplaatjes met gemak op te nemen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---


# Tabelobject in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met het tabelobject in de IC-editor (Interactive Communication) kunnen auteurs eenvoudig aanpasbare tabellen invoegen in communicatiesjablonen. Dit object ondersteunt tabelgegevensrepresentatie voor gebruik in gevallen zoals samenvattingen, itemlijsten, gestructureerde invoer of vergelijkingsindelingen.

Auteurs kunnen de tabelcomponent naar het canvas slepen, het aantal rijen en kolommen configureren en opties kiezen, zoals kop- en voettekstrijen, of de lay-outrichting instellen. De lijsten kunnen als standaardmalplaatjes voor consistentie over veelvoudige mededelingen worden bepaald.

![ vind IC Docu ](/help/forms/interactive-communication/assets/table.png)

## &#x200B;2. Eigenschappen

Het tabelobject bevat verschillende configureerbare eigenschappen waarmee auteurs het gedrag en de vormgeving van de tabel kunnen aanpassen:


2.1 Basisveld

- **Naam:** een uniek herkenningsteken voor de lijst. Deze naam wordt gebruikt intern voor het van verwijzingen voorzien van de lijst in gegevensmodellen en logica.

- **Rijen:** specificeert het aantal inhoudsrijen (exclusief kopbal en footer).

- **Kolommen:** bepaalt het aantal kolommen in de lijst.

- **de Rij van de Kopbal:** Optie om een kopbalrij bij de bovenkant van de lijst voor kolometiketten te omvatten.

- **Voettekstrij:** Optie om een voettekstrij voor totalen of samenvattingswaarden te omvatten.

- **Reeks als Gebrek:** staat gebruikers toe om de huidige configuratie als standaardlijstmalplaatje voor toekomstig gebruik te bewaren.

- **Richting van de Lay-out:** bepaalt hoe de rijen bevolkt zijn — typisch reeks aan Links aan Rechts.

2.2 Positie

- **Beschrijving:** controleert de plaatsing van de lijst binnen de lay-out.

- **Montages:**

   - **X en de Coördinaten van Y:** plaatst de horizontale (X) en verticale (Y) posities van de lijst op het canvas.

   - **Hoogte en Breedte:** bepaalt de algemene grootte van de lijst (in mm), toestaand flexibele ruimtetoewijzing.

2.3 Weergave

**Vormgeving:** plaatst het visuele stileren van de lijst. Auteurs kunnen een keuze maken uit vooraf gedefinieerde voorinstellingen, zoals geordend, vlak of verhoogd.

- **Vulling:** Achtergrondkleur van de lijst of de cellen.

- **Slag:** kleur van de Grens rond de lijst of specifieke cellen.

- **Breedte:** Dikte van de grenslijnen.

- **Stijl:** kies randtypes - afgeronde hoeken of scherpe hoeken.

- **Randen:** vorm zicht van celgrenzen en hoekstraal.

2.4 Aanwezigheid

- **Beschrijving:** bepaalt het zicht van de lijst bij runtime.

- **Opties:**

   - **Zichtbaar:** toon normaal de lijst in de output.

   - **Verborgen:** verberg de lijst maar behoudt ruimte binnen de lay-out.

2.5 Gegevensbinding

**Binding van Gegevens:** verbind de lijst met een gegevensbron (b.v., JSON, het schema van XML) om rijen en kolommen tijdens generatie dynamisch te bevolken met waarden. Dit is handig voor gedetailleerde facturering, transactiegegevens of productaanbiedingen.

## &#x200B;3. Gebruik

Het tabelobject is ideaal voor het weergeven van gestructureerde of herhaalde gegevens. De meest gangbare gebruiksgevallen zijn:

- Facturen en rekeningen met artikelrijen

- Beleid of plannen

- Overzicht van profiel- of accountgegevens

- Productcatalogi of functiematrices

Auteurs kunnen het aantal rijen en kolommen configureren, voorwaardelijke zichtbaarheid toepassen of gegevens binden om dynamische informatie weer te geven.

## &#x200B;4. Beste praktijken

- Gebruik koptekstrijen om elke kolom duidelijk te labelen voor betere leesbaarheid.

- Pas indien van toepassing voettekstrijen toe voor totalen of belangrijke notities.

- Gegevensbinding gebruiken om rijen dynamisch te vullen op basis van gestructureerde invoer.

- Houd consistente opmaak en spatiëring aan de hand van de weergave- en marge-instellingen.

- Zorg bij het verbergen van een tabel voor de continuïteit van de indeling door op te geven of u ruimte wilt behouden.

- Standaardsjablonen gebruiken om tabelinhoud in alle documenten te standaardiseren.

Het voorwerp van de Lijst in de redacteur IC is een flexibele, gegeven-vriendelijke component die wordt ontworpen om gestructureerde inhoud in uw mededelingen te steunen. Met aanpasbare layoutopties, opmaakfuncties en krachtige gegevensbinding kunnen auteurs informatie duidelijk en effectief presenteren.


