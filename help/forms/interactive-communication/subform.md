---
title: Subformuliercomponent in interactieve communicatie-editor
description: Met de subformuliercomponent in de Interactive Communication Editor in AEM Forms kunt u meerdere formulierelementen op een flexibele en gestructureerde manier ordenen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Subformuliercomponent in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

De **component Subform** in de Interactieve Communicatie (IC) redacteur doet dienst als dynamische lay-outcontainer die u toestaat om veelvoudige vormelementen op een flexibele en gestructureerde manier te organiseren. Het wordt doorgaans gebruikt om verwante velden te groeperen, herhalende secties te maken of geneste gegevensstructuren te definiëren voor een betere gebruikerservaring en gegevensbinding.

Subformulieren kunnen zo worden geconfigureerd dat ze in verschillende indelingen lopen, zoals van boven naar beneden of van links naar rechts, waardoor ze ideaal zijn voor complexe formulierontwerpen en herbruikbare secties.

![ vind IC Docu ](/help/forms/interactive-communication/assets/subform.png)

## &#x200B;2. Eigenschappen

2.1 Basiseigenschappen

- **Naam:** een uniek herkenningsteken voor subform dat in het van verwijzingen voorzien, gegevensmodellen, en bedrijfsregels wordt gebruikt.

- **Inhoud:** bepaalt hoe de elementen binnen subform worden geschikt.

   - **Geplaatst:** Absolute plaatsing van kindelementen die x en de coördinaten van Y gebruiken.

   - **Overlopen (van boven naar onder):** schikt verticaal elementen.

   - **Overlopen (van links naar rechts):** schikt horizontaal elementen.

2.2 Positie

- **Beschrijving:** bepaalt de plaatsing van het subformulier binnen de communicatie lay-out.

- **Montages:**

   - X- en Y-coördinaten (in mm)

   - Breedte en Hoogte (in mm)

2.3 Weergave

- **Vulling:** specificeert de achtergrondkleur van het subformuliergebied.

- **Slag:** bepaalt de grenskleur.

- **Breedte:** plaatst de grensdikte.

- **Stijl:** kies van visuele voorinstellingen zoals vlak, begrensd, of opgeheven.

- **Randen:** bepaalt hoek het stileren-rond of scherp.

2.4 Aanwezigheid

- **Beschrijving:** controleert het zicht van subform tijdens runtime.

- **Opties:**

   - **Zichtbaar:** altijd getoond.

   - **Verborgen:** niet getoond maar de ruimte wordt behouden in lay-out.

2.5 Gegevensbinding

- **het Bindende Type van Gegevens:** Verbindt subform met een gegevensstructuur (typisch XML of JSON).

- **Naam van het Gebruik:** bindt gegevens gebruikend de toegewezen naam van het subformulier.

- **Globale Gegevens van het Gebruik:** verbindt het subformulier met een globaal schemapad voor gedeeld gegevensgebruik.

- **Geen Bindende Gegevens:** Subform slaat of wisselt met geen extern gegevensmodel op.

## &#x200B;3. Gebruik

Subformulieren zijn van vitaal belang in scenario&#39;s waarbij veldsets moeten worden gegroepeerd, genest of herhaald. Typische toepassingen zijn:

- Adresblokken organiseren (bijvoorbeeld Street, City, Zip)

- Secties herhalen voor regelitems of meerdere items

- Voorwaardelijke formulierlogica structureren met behulp van zichtbaarheid en regels
Subformulieren kunnen ook worden gebruikt als containers voor het uitlijnen van het ontwerp door slepen en neerzetten in zowel statische als dynamische indelingen.

## &#x200B;4. Beste praktijken

- Kies de juiste indeling (gestroomd versus gepositioneerd) op basis van ontwerp en gegevensbehoeften.

- Gebruik betekenisvolle namen voor het gemak van gegevensintegratie en regel verwijzend.

- Subformulieren opmaken om gegroepeerde secties visueel te onderscheiden.

- Wanneer u herhalende subformulieren gebruikt, moet u zorgen voor een juiste gegevensbinding met arraystructuren.

- Pas voorwaardelijke zichtbaarheidsregels toe om de gebruikerservaring in complexe formulieren te optimaliseren.

De **component Subform** in de Interactieve Communicatie redacteur verstrekt een krachtige manier om complexe vormlay-outs te structureren en te controleren. Of subformulieren nu invoervelden ordenen, dynamische inhoud beheren of modulair ontwerp mogelijk maken, ze verbeteren zowel de bruikbaarheid als de houdbaarheid in alle documentsjablonen.


