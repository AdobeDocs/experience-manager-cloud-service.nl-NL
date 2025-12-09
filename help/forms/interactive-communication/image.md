---
title: Afbeeldingscomponent in de interactieve communicatie-editor
description: De Component van het beeld in Interactieve Communicatie Redacteur in AEM Forms om auteurs toe te staan om communicatie lay-outs te verbeteren door statische beelden op te nemen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: d24e88b545a17e50c1e80e1aedbb1d0adf55f609
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# Afbeeldingscomponent in de interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met de component Afbeelding in de Interactieve communicatie-editor kunnen auteurs communicatielay-outs verbeteren door statische afbeeldingen in te voegen. Deze component is essentieel voor het maken van visueel aantrekkelijke lay-outs en het opnemen van brandingelementen zoals logo&#39;s of visuele pictogrammen. Auteurs kunnen deze zowel in de stramienpagina&#39;s als in de ontwerpweergave plaatsen om ervoor te zorgen dat de weergave in verschillende uitvoerindelingen, zoals PDF, consistent is.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/image.1.png)

## 2.Properties

De component van het Beeld verstrekt verscheidene eigenschappen helpen zijn blik, voelen, en gedrag vormen.

2.1. Beschrijving van afbeelding

Naam:
Handelt als een unieke id voor de afbeeldingscomponent, zodat u gemakkelijk kunt verwijzen in de componenthiërarchie of de regeleditor.

Selecteer Afbeelding: Hiermee kan de auteur een afbeelding uploaden of ernaar verwijzen, zoals een logo, pictogram of een ander statisch visueel bestand uit meerdere bronnen.


2.2. Positie

Beschrijving: hiermee regelt u de ruimtelijke plaatsing van de afbeelding in de lay-out.

Instellingen:

X- en Y-coördinaten

Hoogte en breedte (in mm)

2.3 Marge

De afstand rondom het tekstvak definiëren:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.4. Vorm

Vormgeving: hiermee definieert u de visuele stijl van het afbeeldingsveld, kiest u voorinstellingen zoals geordend, vlak of verhoogd, en past u deze aan met de vulkleur, lijndikte en hoekstijl (afgerond of scherp).

2.5. Aanwezigheid

Beschrijving: hiermee wordt de zichtbaarheid van de afbeeldingscomponent tijdens runtime bepaald.

- Opties:

   - Zichtbaar

   - Verborgen (ruimte behouden)

## 3.Usage

De component Image is ideaal voor:

- Logo&#39;s invoegen in documentkoppen

- Afbeeldingen van producten weergeven op facturen of aanhalingstekens

- Verbetering van de visuele betrokkenheid van communicatie

## 4.Aanbevolen praktijken

- Gebruik afbeeldingen uit een gedeelde bibliotheek voor eenvoudig hergebruik en consistentie.

- Houd de vorm van de afbeelding consistent om uitrekken of pixelvorming te voorkomen.

- Vermijd het gebruik van zeer grote afbeeldingsbestanden om het document snel en responsief te houden.

- Stel de afbeelding zo in dat deze wordt weergegeven of verborgen als dit niet altijd nodig is.

De component van het Beeld in de Interactieve Communicatie van AEM speelt een essentiële rol in het creëren van branded, gepersonaliseerde, en visueel efficiënte mededelingen. Met configureerbare eigenschappen verbetert het de gebruikerservaring terwijl het handhaven van ontwerpconsistentie over verschillende formaten.
