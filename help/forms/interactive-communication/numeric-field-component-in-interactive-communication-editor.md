---
title: Numeriek veldobject in interactieve communicatie-editor
description: Numeriek veldobject in de interactieve communicatie-editor van AEM Forms stelt auteurs in staat numerieke invoer van gebruikers in een gecontroleerde indeling te verzamelen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# Numeriek veldobject in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met de component Numeriek veld in de IC-editor (Interactive Communication) kunnen auteurs numerieke invoer van gebruikers verzamelen in een gecontroleerde indeling. Of u nu telefoonnummers, pincodes, beleids-id&#39;s of financiële cijfers vastlegt, dit veld zorgt ervoor dat alleen numerieke waarden worden geaccepteerd. De component steunt ook het stileren, het formatteren, bevestiging, en gegevensband, die het voor gestructureerde mededelingen essentieel maken.

![ vinden IC Doc ](/help/forms/interactive-communication/assets/numericfield.png)

## &#x200B;2. Eigenschappen

2.1 Basisveld

- **Naam:** bepaal een uniek herkenningsteken voor het gebied, dat in gegevensmodellen, regels, en manuscripten wordt gebruikt.

- **Titel:** Vertoning het onscreen etiket dat aan gebruikers wordt getoond (b.v., &quot;Aantal van het Contact&quot;of &quot;identiteitskaart van de Werknemer&quot;).

- **Waarde:** sta gebruikers toe om numerieke input zoals telefoonaantallen, IDs, hoeveelheden, of monetaire waarden in te gaan.

- **Reserve:** plaats de groepering van numerieke waarde-links, recht, bovenkant, of bodem-of specificeer een douanepositie gebruikend eenheden zoals millimeters (b.v., 20 mm).

- **Verschijning:** plaats de verschijning van de waardedoos als niets, Ononderbroken Doos, of Onderstrepen die op de gewenste visuele lay-out wordt gebaseerd.

2.2 Typografie

Bepaalt de visuele stijl van de numerieke tekens die door de gebruiker worden ingevoerd:

- **Bevestiging van het Doopvont:** pas beperkingen toe om slechts geldige numerieke input toe te laten wordt toegelaten-zulke zoals gehelen, decimalen, of aantal reeksen-gebaseerd op het voorgenomen gegevenstype.

- **Grootte van de Doopvont:** pas de grootte van de numerieke tekst aan gebruikend puntwaarden zoals 10 pt, 12 pt, of 20 pt om consistentie en leesbaarheid over de vorm te handhaven.

2.3 Positie

Bepaalt de ruimtelijke plaatsing van het numerieke veld op het canvas.

- **x en de coördinaten van Y:** bepaalt nauwkeurige gebiedsplaatsing.

- **Breedte en Hoogte (in mm):** bepaalt de grootte van de inputdoos.

2.4 Marge

Hiermee definieert u de ruimte rondom de grens van het numerieke veld voor een zuivere uitlijning.

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.5 Weergave

Hiermee past u de stijl van de container van het numerieke invoerveld aan aan de gewenste visuele indeling:

- **Vulling:** plaats de achtergrondkleur van het numerieke gebied. Zo kunt u het element visueel scheiden van andere elementen of aanpassen aan het algemene thema.

- **Slag:** voeg grenzen rond het numerieke gebied met de volgende klantgerichte opties toe:

- **Breedte:** bepaal de dikte van de grens om visuele nadruk aan te passen.

- **Stijl:** kies een grens patroon-vast, gestreepte, of gestippeld.

- **Edge:** Uitgezocht tussen afgeronde of scherpe hoeken voor de grens.

- **Straal:** pas de hoekracht aan gebruikend specifieke straalwaarden (b.v., 4 px, 10 px) om de verschijning van het gebied zachter of scherper te maken.

2.6 Aanwezigheid

Hiermee bepaalt u de zichtbaarheid van het numerieke veld tijdens de runtime.

- **Zichtbaar:** Standaardstaat; het gebied wordt normaal getoond.

- **Verborgen (houdt ruimte):** het Gebied is onzichtbaar maar de ruimte wordt behouden in lay-out.

2.7 Gegevensbinding

**het Bindende Type van Gegevens:** verbindt het numerieke gebied met een gegevensbron (XML of JSON) voor integratie in real time.

**Naam van het Gebruik:** bindt gebied aan zijn unieke naam voor eenvoudige waardetoewijzing.

**Globale Gegevens van het Gebruik:** gebied van Verbindingen aan een gedeeld gegevensknooppunt over vormen of fragmenten.

**Geen Gegevens die binden:** houdt het gebied statisch voor visueel-slechts gebruik of tijdelijke input.

## &#x200B;3. Gebruik

Numerieke velden zijn ideaal als alleen cijfers geldige invoer zijn. Vaak voorkomende gevallen van gebruik zijn:

- Het vangen **mobiele aantallen, OTPs, en SPELDs**

- Het invoeren van **beleidsaantallen of werknemer IDs**

- Het verzamelen van **numerieke hoeveelheden of monetaire waarden**

- Het toelaten van **op stap-gebaseerde aantalgebieden** (b.v., tellers of scoringangen)

Auteurs kunnen numerieke velden in lay-outcontainers of subformulieren plaatsen en validatie toepassen (zoals beperkingen voor lengte, minimum of maximumwaarde) om de gegevenskwaliteit te verbeteren.

## &#x200B;4. Beste praktijken

- Numerieke velden moeten duidelijk van een label worden voorzien, indien nodig (bijvoorbeeld &quot;Bedrag in ₹&quot;).

- Pas formaatbevestiging (zoals 10 cijfergrenzen voor telefoonaantallen) voor betere nauwkeurigheid toe.

- Gebruik reservewaarden als velden verplicht zijn, maar dynamische gegevens mogelijk ontbreken.

- Numerieke velden zorgvuldig binden aan schemapaden ter ondersteuning van achtergrondverwerking.

- Houd een consistent uiterlijk en typografie in overeenstemming met de richtlijnen voor merken.

Het **Numerieke voorwerp van het Gebied** in de Interactieve Communicatie redacteur is een nauwkeurig, betrouwbaar hulpmiddel voor op cijfer-gebaseerde gegevensinzameling. Met robuuste opties voor opmaak, zichtbaarheid en gegevensbinding zorgt deze ervoor dat numerieke invoer probleemloos wordt vastgelegd en naadloos wordt geïntegreerd in digitale formulieren. Als de stijl correct is ingesteld en geconfigureerd, verbetert deze aanzienlijk de bruikbaarheid van formulieren en de algehele gegevensnauwkeurigheid.


