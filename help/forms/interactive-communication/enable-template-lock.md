---
title: Sjabloonvergrendeling in interactieve communicatie-editor
description: Sjabloonvergrendeling in de interactieve communicatie-editor biedt sjabloonauteurs de mogelijkheid om de lay-out of inhoud voor documentauteurs te vergrendelen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 7c7461fe-a5d7-481e-b5f5-27fd5bcde2d0
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Sjabloonvergrendeling in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

## &#x200B;1. Inleiding

Met de functie Sjabloonvergrendeling in de Editor voor interactieve communicatie (IC) kunnen sjabloonauteurs wijzigingen beperken tot specifieke elementen van een communicatiesjabloon. Dit verzekert ontwerpconsistentie, beschermt kritieke inhoud, en handhaaft bestuur over teams die malplaatjes opnieuw gebruiken om gepersonaliseerde mededelingen tot stand te brengen.

Wanneer toegepast, verschijnen de gesloten componenten visueel verschillend en kunnen niet door stroomafwaartse auteurs of contribuanten, afhankelijk van het slottype worden gewijzigd. Deze eigenschap helpt merknormen, gegevensintegriteit, en lay-outuniformiteit over alle afgeleide mededelingen handhaven.

![&#x200B; vinden IC Doc &#x200B;](/help/forms/interactive-communication/assets/template-lock.png)

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

## &#x200B;3. Hoe te om Sjabloonslot in Interactieve Communicatie Redacteur te gebruiken

Voer de volgende stappen uit om inhoud- of lay-outsluizen toe te passen in de sjabloon Interactieve communicatie (IC):

1. Uw sjabloon openen
Open of creeer een Malplaatje, volg de gids [&#x200B; creeer een Interactief Communicatie Malplaatje &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/interactive-communication/overview/create-interactive-communication-template)

1. De component selecteren
Klik op de component (tekstvak, afbeelding of subformulier) die u wilt beperken.

1. Opties voor toegang vergrendelen
Ga in het deelvenster Eigenschappen naar de sectie Vergrendelen.

1. Vergrendelingen toepassen

   1. Inhoud vergrendelen: voorkomt tekst, stijl en gegevensbewerkingen.

   1. Lay-outvergrendeling: hiermee beperkt u de verplaatsing en het formaat.

   1. U kunt beide voor volledige bescherming inschakelen.

1. Opslaan en verifiëren
Sla de sjabloon op en maak een nieuwe IC op basis hiervan om te bevestigen dat vergrendelde elementen niet kunnen worden gewijzigd.

## &#x200B;4. Beste praktijken

- **Slot kritieke Componenten vroeg:** pas sloten op kopballen, footers, wettelijke ontkenningen, en logo&#39;s toe om naleving en merkidentiteit te bewaren.

- **de inhoudssloten van het Gebruik voor nauwkeurigheid:** beschermt gebieden gebonden aan de modellen van kerngegevens of regelgevende tekst.

- **de lay-outsloten van het Gebruik voor consistentie:** verhindert misgroepering of visuele vervorming in vaak hergebruikte malplaatjes.

- **Communiceer slotgebruik:** verzekert stroomafwaartse gebruikers zich bewust zijn van welke secties opzettelijk worden beperkt om verwarring te vermijden.
