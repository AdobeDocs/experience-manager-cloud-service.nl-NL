---
title: Sjabloonvergrendeling in interactieve communicatie-editor
description: Sjabloonvergrendeling in de interactieve communicatie-editor biedt sjabloonauteurs de mogelijkheid om de lay-out of inhoud voor documentauteurs te vergrendelen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 371838c77beafa8c67259a865b25325632bea0b0
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Sjabloonvergrendeling in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met de functie Sjabloonvergrendeling in de Editor voor interactieve communicatie (IC) kunnen sjabloonauteurs wijzigingen beperken tot specifieke elementen van een communicatiesjabloon. Dit verzekert ontwerpconsistentie, beschermt kritieke inhoud, en handhaaft bestuur over teams die malplaatjes opnieuw gebruiken om gepersonaliseerde mededelingen tot stand te brengen.

Wanneer toegepast, verschijnen de gesloten componenten visueel verschillend en kunnen niet door stroomafwaartse auteurs of contribuanten, afhankelijk van het slottype worden gewijzigd. Deze eigenschap helpt merknormen, gegevensintegriteit, en lay-outuniformiteit over alle afgeleide mededelingen handhaven.

## &#x200B;2. Vergrendeltypen

Sjabloonauteurs kunnen vergrendelingen voor inhoud en lay-out afzonderlijk of gezamenlijk toepassen om de inhoud en layoutwijzigingen in interactieve communicatiesjablonen te beheren:

### 2.1 Inhoud vergrendelen

Met een Content Lock beperkt u wijzigingen in de inhoud of eigenschappen van het geselecteerde element. Dit type van slot zorgt ervoor dat essentiële gegevens, tekst, of ontwerpeigenschappen onveranderd blijven, zelfs wanneer opnieuw gebruikt over veelvoudige mededelingen.

Auteurs kunnen bij toepassing geen wijzigingen aanbrengen:

- Tekstinhoud of bijschriften

- Weergave-instellingen (lettertype, kleur, achtergrond, randen, enz.)

- Configuraties van gegevensbinding

- Componentelementen binnen een containercomponent (zoals subformulieren)

### 2.2 Layout vergrendelen

Met een lay-outvergrendeling worden wijzigingen beperkt die betrekking hebben op de positie en de grootte van een element. Hierdoor blijven visuele uitlijning en ontwerphiërarchie consistent met merk- of documentstandaarden.

Wanneer toegepast, kunnen auteurs niet:

- Het element naar een nieuwe positie op de pagina verplaatsen

- De breedte of hoogte van het element vergroten of verkleinen

## &#x200B;3. Gedrag in afgeleide communicatie

- Wanneer een mededeling van een gesloten malplaatje wordt gecreeerd, verschijnen de gesloten elementen als read-only in de Redacteur van IC voor communicatie auteurs.

- De binneneigenschappen of bindingen van componenten met inhoudsvergrendeling kunnen niet worden gewijzigd.

- Componenten met een lay-outvergrendeling kunnen niet worden verplaatst of vergroot of verkleind.

Hierdoor kunnen sjabloonmakers het ontwerp en de structuur blijven beheren en kunnen andere gebruikers zich richten op variabele inhoud en op gegevensgestuurde aanpassing.

## &#x200B;4. Beste praktijken

- **Slot kritieke Componenten vroeg:** pas sloten op kopballen, footers, wettelijke ontkenningen, en logo&#39;s toe om naleving en merkidentiteit te bewaren.

- **de inhoudssloten van het Gebruik voor nauwkeurigheid:** beschermt gebieden gebonden aan de modellen van kerngegevens of regelgevende tekst.

- **de lay-outsloten van het Gebruik voor consistentie:** verhindert misgroepering of visuele vervorming in vaak hergebruikte malplaatjes.

- **Communiceer slotgebruik:** verzekert stroomafwaartse gebruikers zich bewust zijn van welke secties opzettelijk worden beperkt om verwarring te vermijden.
