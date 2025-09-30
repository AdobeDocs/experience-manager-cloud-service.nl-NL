---
title: Tekstveldobject in interactieve communicatie-editor
description: Tekstveldobject in de interactieve communicatie-editor in AEM Forms waarmee auteurs informatie zoals namen, adressen, opmerkingen of numerieke id's kunnen weergeven.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---


# Tekstveldobject in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met de component Tekstveld in de IC-editor (Interactive Communication) kunnen auteurs informatie weergeven zoals namen, adressen, opmerkingen of numerieke id&#39;s. De waarde in het tekstveld is vooraf gedefinieerd (statisch) of dynamisch gevuld met gegevensbinding. Het steunt single-line ingangen, bevestigingsregels, en flexibele het formatteren, die tot het één van de meest gebruikte en veelzijdige elementen in gepersonaliseerde mededelingen maken.

![ vinden IC Doc ](/help/forms/interactive-communication/assets/textfield.png)

## &#x200B;2. Eigenschappen

2.1 Basisveld

- **Naam:** bepaal een uniek herkenningsteken voor het gebied, dat in gegevensmodellen, regels, en manuscripten wordt gebruikt.

- **Titel:** toon het onscreen etiket dat aan gebruikers wordt getoond (b.v., &quot;Voornaam&quot;).

- **Waarde:** de tekst van de vertoning zoals namen, adressen, commentaren, of andere details. De waarde is statisch of afgeleid van gegevensbinding.

- **Reserve:** plaats de groepering van de waarde, links, recht, bovenkant, of bodem of specificeer een douanepositie gebruikend eenheden zoals millimeters (b.v., 20 mm).

- **Verschijning:** plaats de verschijning van de waardedoos als niets, Ononderbroken Doos, of Onderstrepen die op de gewenste visuele lay-out wordt gebaseerd.

2.2 Typografie

Hiermee bepaalt u de visuele stijl van de getypte tekens:

- **Bevestiging van het Doopvont:** pas facultatieve beperkingen toe om het formaat van de getoonde waarde te bevestigen, zoals het toestaan slechts alfabeten, aantallen, of specifieke douanepatronen.

- **Grootte van de Doopvont:** pas de grootte van de tekst binnen het gebied aan gebruikend puntwaarden zoals 10 pt, 12 pt, 20 pt, enz., om leesbaarheid en groepering aan ontwerpnormen te verzekeren.

2.3 Positie

Hiermee definieert u de plaatsing van het veld in de indeling:

- **X/Y coördinaten**

- **Breedte en Hoogte** (mm, px, of %)

2.4 Marge

Hiermee geeft u de ruimte rondom de veldcontainer op:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.5 Weergave

Stijlen van de veldcontainer zelf:

- **Vulling:** plaats de achtergrondkleur van het tekstvakje. Hiermee kunt u invoergebieden onderscheiden of uitlijnen met merkkleuren.

- **Slag:** voeg grenzen rond het tekstvakje met de volgende klantgerichte eigenschappen toe:

- **Breedte:** bepaal de dikte van de grens.

- **Stijl:** kies van stevige, gestormde, of gestippelde grensstijlen.

- **Edge:** selecteer de vorm van de hoeken-of rond of scherp.

- **Straal:** pas de hoekkromming aan gebruikend straalwaarden (b.v., 4 px, 10 px) voor een zachtere of meer hoekige blik.

2.6 Aanwezigheid

Hiermee wordt de zichtbaarheid bij uitvoering bepaald:

- **Zichtbaar:** getoond en bezet ruimte

- **Verborgen (houdt ruimte):** Onzichtbaar maar lay-outruimte is gereserveerd

2.7 Gegevensbinding

Koppelt het tekstveld aan een gegevensbron om waarden dynamisch of statisch in de communicatie weer te geven.

- **het Binden van Gegevens Type:** specificeert hoe het gebied met een gegevensbron of een schema verbindt.

- **Naam van het Gebruik:** bindt het tekstgebied gebruikend de gebiedsnaam die in het gegevensmodel of het schema wordt bepaald, toestaand dynamische tekstvertoning die op externe gegevens wordt gebaseerd.

- **Globale Gegevens van het Gebruik:** verbindt het gebied met globale gegevens die over de volledige mededeling voor verenigbare informatievertoning worden gedeeld.

- **Geen Gegevens die binden:** houdt het gebied losgemaakt van om het even welke achterste eindbron. Het wordt gebruikt om statische waarden of tekst te tonen die voor visuele context slechts wordt bedoeld.

## &#x200B;3. Gebruik

Veelvoorkomende scenario&#39;s zijn:

- Persoonlijke gegevens vastleggen (namen, adressen, telefoonnummers)

- Opmerkingen of feedback accepteren (meerdere regels)

- Beleidsnummers of account-id&#39;s invoeren

- Korte numerieke waarden verzamelen, zoals pincodes of OTP&#39;s

Auteurs kunnen het veld in subformulieren of indelingsrasters plaatsen voor uitlijning en validatieregels (lengtelimieten, regex-patronen) toevoegen om een schone invoer te garanderen.

## &#x200B;4. Beste praktijken

- Pas validatie (verplichte vlaggen, patrooncontroles) toe voor directe feedback.

- Geef een betekenisvolle reservetekst op voor gedrukte of alleen-lezen weergaven.

- Houd typografie in overeenstemming met de richtlijnen voor merken.

- Verminder de veldbreedte op mobiele lay-outs om kleinere schermen te passen.

- Sluit waar mogelijk rechtstreeks aan op het gegevensmodel voor eenvoudiger onderhoud.

Het tekstveldobject in de IC-editor is een veelzijdige bouwsteen die het vastleggen van gegevens stroomlijnt. Als deze optie goed is geconfigureerd, met goed gekozen typografie, duidelijke labels, correcte validatie en solide gegevensbinding, biedt deze een naadloze, gebruiksvriendelijke ervaring en betrouwbare gegevens voor downstreamverwerking.


