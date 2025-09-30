---
title: Datumveldobject in de interactieve communicatie-editor
description: Met Date Field Object in Interactive Communication Editor kunnen auteurs een op een kalender gebaseerd datumselectieveld invoegen in een document.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---


# Datumveldobject in de interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

De **component van het Gebied van de Datum** &lbrace;in de Interactieve Communicatie (IC) redacteur laat auteurs toe om een op kalender-gebaseerd gebied van de datumselectie in een document op te nemen. Op deze manier kunnen gebruikers gemakkelijk een datum uit een datumkiezer kiezen of deze handmatig invoeren in een vooraf gedefinieerde notatie.

Het datumveld is ideaal voor het vastleggen van geboortedatums, afstellingsschema&#39;s, toepassingsdatums of begin- en einddatums van het beleid. Hierdoor wordt de nauwkeurigheid verbeterd en worden invoerfouten verminderd. Deze ondersteunt opmaak, opmaak en gegevensbinding voor naadloze integratie met gegevensmodellen en back-endsystemen.

![ vind IC Docu ](/help/forms/interactive-communication/assets/date.png)

## &#x200B;2. Eigenschappen

Het object Date Field bevat verschillende configureerbare eigenschappen:

2.1. Basisveld

- **Naam:** een uniek herkenningsteken dat voor het van verwijzingen voorzien van het gebied binnen regels, manuscripten, en gegevensmodellen wordt gebruikt.

- **Titel:** het vertoningsetiket dat aan de gebruiker wordt getoond (b.v., &quot;Geboortedatum&quot;).

- **Datum:** De daadwerkelijke datumwaarde, die door gebrek of pre-bevolkt kan zijn gebruikend dynamische gegevens.

- **Reserve:** een facultatieve reservedatum (getoond als geen datum wordt geselecteerd of het gegeven niet beschikbaar is).

- **Vormgeving:** Snelle vooraf ingestelde stijl (b.v., onderstreept, vlak, begrensd) voor visuele consistentie.

2.2. Typografie

Hiermee bepaalt u hoe de datum visueel in het veld wordt weergegeven:

- **de Variatie van het Doopvont:** kies doopvontfamilie, gewicht (b.v., Normaal, Vet), en stijl (b.v., Cursief).

- **Grootte:** typisch geplaatst aan 10 pt door gebrek, maar klantgericht voor consistentie met omringende inhoud.

2.3. Positie

Definieert ruimtelijke plaatsing in de documentlayout:

- **x en de coördinaten van Y:** bepaalt horizontale en verticale plaatsing.

- **Breedte en Hoogte:** Reeks in millimeters of percentages om met andere vormelementen te richten.

2.4. Marge

Hiermee geeft u de ruimte rondom de grenzen van het veld op:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

Deze waarden helpen u bij de nauwkeurige uitlijning in subformulieren of layoutrasters.

2.5. Vorm

Hiermee definieert u de visuele opmaak van de veldcontainer:

- **Vulling:** Achtergrondkleur van het gebied (b.v., wit, lichtgrijs).

- **Slag:** kleur of overzicht van de Grens.

- **Breedte:** Dikte van de gebiedsgrens.

- **Stijl:** Ononderbroken, gestormde, of gestippelde lijnopties.

- **Randen:** pas hoeken als rond of scherp voor verschillende ontwerpvoorkeur aan.

2.6. Aanwezigheid

Hiermee bepaalt u hoe en wanneer het veld wordt weergegeven:

- **Zichtbaar:** Standaard het plaatsen waar het gebied bij runtime wordt getoond.

- **Verborgen (houdt ruimte):** het Gebied blijft onzichtbaar, maar lay-outruimte wordt bewaard.

Dit is handig wanneer u de zichtbaarheid dynamisch schakelt op basis van gebruikersinvoer of -regels.

2.7. Gegevensbinding

Verbindt het Datumveld met gegevensstructuren voor het opslaan of vooraf invullen van waarden.

**het Binden Type van Gegevens:**

- **Naam van het Gebruik:** bindt het gebied aan het schema gebruikend zijn naamattributen.

- **Globale Gegevens van het Gebruik:** bindt gebruikend een vooraf bepaald gegevensmodel of schemaelement.

- **Geen Bindende Gegevens:** het gebied blijft statisch, niet verbonden met om het even welke gegevensbron.

Hierdoor kunnen dynamische datumwaarden worden opgehaald, weergegeven of opgeslagen op basis van toepassingslogica.

## &#x200B;3. Gebruik

Het datumveld is vooral handig in de volgende gevallen:

- Vastlegdatum van de geboorte of aansluitende datum in onboarding vormen.

- Het selecteren van begin en einddata voor de diensten, abonnementen, of gebeurtenissen.

- Tijdslimieten voor de toepassing, periodes voor afspraak of verificatiedata invoeren.

Auteurs kunnen het datumveld in lay-outcontainers of subformulieren plaatsen en validatie (bijvoorbeeld datumnotatie, bereiklimieten) configureren om de gegevenskwaliteit te verbeteren.

## &#x200B;4. Beste praktijken

- Gebruik duidelijke bijschriften zoals &quot;Begindatum&quot; of &quot;Aanwijzingsdatum selecteren&quot; voor betere UX.

- Stel minimum- en maximumdatumbereiken in om ongeldige invoer te voorkomen (bijvoorbeeld toekomstige DOB).

- Pas consistente tekenstijlen toe (10 pt aanbevolen) voor leesbaarheid.

- Velden binden aan het schema waar de integratie van backendgegevens nodig is.

- Niet-relevante datumvelden dynamisch verbergen met behulp van zichtbaarheidsregels.

Het **voorwerp van het Gebied van de Datum** &lbrace;in de Interactieve Communicatie redacteur is een krachtig hulpmiddel om tijd-gevoelige gegevens met nauwkeurigheid en gemak te vangen. Als de vormgeving doordacht is en verbinding maakt met betekenisvolle gegevenspaden, biedt deze ondersteuning voor een naadloze gebruikerservaring en een efficiënte verwerking van op tijd gebaseerde items.


