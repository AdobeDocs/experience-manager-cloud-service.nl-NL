---
title: Component Afbeeldingsveld in interactieve communicatie-editor
description: De Component van het Gebied van het beeld in Interactieve Communicatie Redacteur in AEM Forms om auteurs toe te staan om beelden in een communicatie lay-out op te nemen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 0af73ae2-fe1d-4763-ad4d-2934691cb9e1
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Component Afbeeldingsveld in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

## &#x200B;1. Inleiding

Met de component Afbeeldingsveld in de interactieve communicatieeditor kunnen auteurs afbeeldingen invoegen in een communicatielay-out. Het is ideaal voor gebruik in gevallen zoals foto-identificatie, documentverificatie of visuele validatie, waarbij het van essentieel belang is een afbeelding aan de eindgebruiker weer te geven.

Ondersteunend gemeenschappelijke formaten zoals **JPEG** en **PNG**, biedt deze component flexibele configuratieopties aan om te bepalen hoe het beeld wordt getoond, opgeslagen, en gestileerd. De auteurs kunnen ook **een naam of een etiket** aan het beeldgebied toewijzen, die lay-outduidelijkheid en organisatie verbeteren.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/imagefield.png)

## &#x200B;2. Eigenschappen

De component van het Gebied van het Beeld omvat verscheidene configureerbare eigenschappen:

2.1. Basisveld

- **Naam:** bepaal een uniek herkenningsteken voor het gebied, dat voor het van verwijzingen voorzien van gegevensmodellen en regels wordt gebruikt.

- **Titel:** Vertoning het etiket dat aan gebruikers op de interface wordt getoond.

- **Uitgezochte Beeld:** sta de auteur toe om een beeld te uploaden gebruikend dit bezit-algemeen gebruikt voor logo&#39;s, IDs, of andere visuele elementen.

- **Beeld van de Reserve:** bepaal de groepering van het beeld, links, recht, bovenkant, of bodem of specificeer a **douanepositie** gebruikend eenheden zoals millimeters (b.v., 20 mm).

2.2. Positie

Hiermee bepaalt u de ruimtelijke plaatsing van de afbeelding in de layout.

- X- en Y-coördinaten

- Hoogte en breedte (in mm)

2.3. Marge

De afstand rondom het tekstvak definiëren:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.4. Vorm

Vormgeving: hiermee definieert u de visuele stijl van het afbeeldingsveld, kiest u voorinstellingen zoals geordend, vlak of verhoogd, en past u deze aan met de vulkleur, lijndikte en hoekstijl (afgerond of scherp).

2.5. Aanwezigheid

Hiermee wordt de zichtbaarheid van de afbeeldingscomponent tijdens runtime bepaald.

- Zichtbaar

- Verborgen (ruimte behouden)

2.6. Gegevensbinding

Koppel het afbeeldingsveld aan een gegevensbron om dynamische afbeeldingsinhoud binnen de communicatie op te halen en weer te geven.

**het Binden van Gegevens Type:** bepaalt hoe het beeldgebied met de onderliggende gegevensstructuur of het schema verbindt.

**Naam van het Gebruik:** bindt het beeldgebied gebruikend de gebiedsnaam die in het gegevensmodel of het schema wordt gespecificeerd, toestaand het beeld om dynamisch bij runtime worden bevolkt.

**Globale Gegevens van het Gebruik:** verbindt het beeldgebied met globale gegevens die over de volledige mededeling worden gedeeld, die consistentie in visuele inhoud verzekeren.

**Geen Gegevens die binden:** houdt het gebied losgemaakt van om het even welke achterste deelgegevens, ideaal voor gevallen waar een statisch beeld wordt getoond of wanneer het beeld puur door montages UI wordt gecontroleerd.

## &#x200B;3. Gebruik

Het afbeeldingsveld is handig in situaties waarin visuele inhoud moet worden verzonden. Vaak voorkomende gevallen van gebruik zijn:

- Bewijs van de geüploade identiteitskaart (paspoort, vergunning)

- Profiel of persoonlijke foto&#39;s verzenden

- Bewijsstukken visueel bijvoegen

Auteurs kunnen het veld in subformulieren of lay-outcontainers plaatsen voor uitlijning en aangepaste validatieregels gebruiken om geaccepteerde bestandstypen en -grootten te beheren.

## &#x200B;4. Beste praktijken

- Gebruik duidelijke labels of instructies wanneer u een afbeelding uploadt.

- Beperk de bestandsgrootte en indelingen via validatie voor prestaties.

- Zorg ervoor dat er fallback-afbeeldingen (reservekopieën) beschikbaar zijn.

- Het veld binden aan een betekenisvol schemapad bij integratie met back-end

De component van het Gebied van het Beeld in interactieve communicatie redacteur is een veelzijdige component die vorm interactiviteit verbetert door visuele inhoud toe te laten uploadt. Als deze optie is ontworpen met stijlen, validatie en gegevensbinding, ondersteunt deze een naadloze gebruikerservaring en efficiënte gegevensvastlegging voor op afbeeldingen gebaseerde verzendingen.
