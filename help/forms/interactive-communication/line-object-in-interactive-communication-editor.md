---
title: Line Object in Interactive Communication Editor
description: Met Line Object in de Interactive Communication Editor in AEM Forms kunnen auteurs horizontale of verticale lijnen invoegen in een communicatielay-out.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---


# Line Object in Interactive Communication Editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met het object Line in de editor Interactive Communication (IC) kunnen auteurs horizontale of verticale lijnen invoegen in een communicatielay-out. Deze regels helpen u bij het visueel segmenteren van inhoud, het verbeteren van de leesbaarheid of het benadrukken van de formulierstructuur. Met aanpasbare stijlen zoals ononderbroken lijnen of onderstrepingen en flexibele positionering kan het object Line zowel voor functionele als voor esthetische doeleinden worden gebruikt in formulierontwerp.

![ vind IC Docu ](/help/forms/interactive-communication/assets/line.png)

## &#x200B;2. Eigenschappen

Het object Line bevat een reeks configureerbare eigenschappen waarmee u de identiteit, weergave, plaatsing en zichtbaarheid van het object in het document kunt definiëren.

2.1. Basisveld

- **Naam:** een uniek herkenningsteken dat intern wordt gebruikt om het lijnvoorwerp in gegevensmodellen, regels, of scripting van verwijzingen te voorzien.

- **Type van Vormgeving:** selecteer hoe de lijn binnen de vorm verschijnt.

   - **niets:** Geen lijn wordt getoond.

   - **Ononderbroken Doos:** geeft de lijn als ononderbroken doos terug, gewoonlijk gebruikt als separator.

   - **onderstreping:** trekt een onderstreping typisch onder kopballen of gebieden wordt gebruikt.

2.2. Positie

- **Beschrijving:** bepaalt de fysieke plaatsing van de lijn op de vormlay-out.

- **Montages:**

   - **X en de Coördinaten van Y:** specificeert het horizontale en verticale plaatsen.

   - **Hoogte en Breedte:** plaats de lengte en de dikte van de lijn (in mm).

2.3. Marge

- **Beschrijving:** voegt het opvullen of het uit elkaar plaatsen rond het lijnvoorwerp toe om lay-outdichtheid te controleren.

- **Opties:**

   - Boven

   - Onder

   - Links

   - Rechts

2.4. Vorm

- **Beschrijving:** staat het stileren van de lijn toe om het documentontwerp aan te passen.

- **Opties:**

   - **Slag:** bepaalt de kleur en de dikte van de lijnslag.

   - **Breedte:** bepaalt hoe breed de lijn over de vorm overspant.

   - **Stijl:** kies tussen gestormde, gestippelde, of stevige lijnstijlen.

2.5. Aanwezigheid

- **Beschrijving:** controleert het zicht van het lijnvoorwerp tijdens runtime.

- **Opties:**

   - **Zichtbaar:** de lijn wordt teruggegeven op de definitieve output.

   - **Verborgen:** de lijn wordt niet getoond, maar zijn lay-outruimte wordt bewaard.

## &#x200B;3. Gebruik

Het object Line wordt vaak gebruikt om:

- Secties visueel splitsen in lange vorm

- Kop- of labels voor accenten onderstrepen

- Randen of vakken maken rond groepen velden

- De visuele hiërarchie van de communicatielay-out verbeteren

## &#x200B;4. Beste praktijken

- Gebruik consistente lijnstijlen in het formulier om een professionele weergave te behouden.

- Pas de marges aan om te voorkomen dat de weergave onoverzichtelijk wordt en om de uitlijning te garanderen.

- Kies de juiste lijn- en stijlinstellingen die overeenkomen met het merk of het documentontwerp.

- Verberg overbodige regels om afleiding te voorkomen en de ruimte tussen de layout te behouden.

Het voorwerp van de Lijn in de Interactieve Communicatie redacteur is een eenvoudig maar krachtig ontwerpelement. Wanneer strategisch gebruikt, verbetert het de visuele structuur van communicatie documenten, die gebruikers helpen om inhoud beter te navigeren en een schonere, meer gepolijste lay-out te verzekeren.


