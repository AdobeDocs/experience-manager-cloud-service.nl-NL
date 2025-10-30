---
title: Dynamische paginanummering in interactieve communicatie-editor
description: Met dynamische paginanummering in de interactieve communicatie-editor kunnen auteurs automatisch paginanummers weergeven in hun PDF-uitvoer.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: dae482e1f57a3504bf08926b57b89ca9266bd36a
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Dynamische paginanummering in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## Inleiding

Met de functie Dynamische paginanummering in Interactieve communicatie (IC) kunnen auteurs automatisch paginanummers weergeven in hun PDF-uitvoer. Paginanummering kan worden ingeschakeld op het niveau van de basispagina, zodat de nummering op alle bijbehorende ontwerppagina&#39;s consistent blijft. Zo blijven duidelijke paginatracering en een professionele lay-out behouden voor alle communicatie met meerdere pagina&#39;s.

## Belangrijkste mogelijkheden

- **Hoofdpaginamonfiguratie:**
Paginanummering kan op hoofdpaginaniveau worden ingeschakeld. De component kan overal op het canvas worden geplaatst nadat deze is neergezet en vrij is aangepast, aangezien deze alle eigenschappen ondersteunt die beschikbaar zijn in de tekstcomponent.

- **Automatische Plaatsing:**
Onder in het midden van elke pagina wordt een component paginanummering weergegeven met de indeling:
&quot;**Paginanummer van #**&quot;

   - Het eerste **#** staat voor het huidige paginanummer.

   - Het tweede **#** vertegenwoordigt het totale aantal pagina&#39;s in de communicatie.

- **Dynamische Vertoning op de Voorproef van PDF:**
De paginanummers worden dynamisch gerenderd tijdens de PDF-voorvertoning, waarbij de juiste paginanummering in de uiteindelijke uitvoer wordt weergegeven.

### Voorbeeld

Wanneer u een voorvertoning weergeeft van een interactieve communicatie van 5 pagina&#39;s, wordt elke pagina weergegeven:

Pagina 1 van 5

Pagina 2 van 5

... enzovoort, dynamisch bijwerken tijdens het genereren van PDF.

## Belangrijkste voordelen

- Verbetert de leesbaarheid en professionaliteit van documenten.

- Hiermee automatiseert u paginanummering zonder handmatige tussenkomst.

- Hiermee blijft consistentie behouden op alle pagina&#39;s die aan een basispagina zijn gekoppeld.
