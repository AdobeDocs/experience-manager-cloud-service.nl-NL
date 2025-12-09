---
title: De Behandeling van de Overstroming van de inhoud in Interactieve Communicatie Redacteur
description: De verwerking van de Overloop van de inhoud in Interactieve Communicatie Redacteur verbetert hoe de tekst zich binnen Stroomde en Geplaatste lay-outs gedraagt.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 9adc7a5669d8bf1e64cc93998cb2f91ffa9d3dd6
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# De Behandeling van de Overstroming van de inhoud in Interactieve Communicatie Redacteur

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## Inleiding

Met de functie voor de afhandeling van overloop bij inhoud in de Interactieve communicatie-editor kunt u beter bepalen hoe tekst zich gedraagt binnen de indelingen Overlopen en Geplaatst. Het zorgt voor vloeiende inhoudscontinuïteit voor stroombare lay-outs en biedt visuele waarschuwingen voor gepositioneerde lay-outs, waardoor auteurs beter controle en flexibiliteit hebben bij het ontwerpen van communicatie.

![&#x200B; vinden IC Doc &#x200B;](/help/forms/interactive-communication/assets/content-overflow.png)

## Hoe te om de Behandeling van de Overloop van de Inhoud in Interactieve Communicatie Redacteur te gebruiken

1. De interactieve communicatie-editor openen
Open uw communicatie in de Editor van IC om de lay-out en inhoud te bewerken.

1. Selecteer het type layout
Kies de gewenste indeling voor het subformulier, de optie Overlopen of de optie Geplaatst op basis van het gedrag van de inhoud.

1. Voor stroombare indelingen

   1. Zorg ervoor dat de bovenliggende subformulierhiërarchie is ingesteld op Overlopen.

   1. Schakel in het deelvenster Eigenschappen de optie Pagina-einden binnen inhoud toestaan in (alleen zichtbaar als de optie Pagina-einden toestaan van het bovenliggende subformulier is ingeschakeld).

   1. Voeg of plak tekst toe wanneer de inhoud groter is dan één pagina, dan gaat deze automatisch door op de volgende pagina.

1. Voor gepositioneerde layouts

   1. Voeg tekst toe of bewerk tekst in een vaste container.

   1. Als de inhoud de containerhoogte overschrijdt, wordt onderaan een rode rand weergegeven om overloop aan te geven.

   1. Wijzig de grootte van de container handmatig om ruimte te maken voor de extra inhoud.

1. Voorbeeld van communicatie bekijken
Met de optie PDF-voorbeeld kunt u controleren hoe de inhoud over pagina&#39;s loopt of hoe deze over beide lay-outtypen loopt.

## Belangrijkste mogelijkheden

### Stroomindeling

- **Nieuwe Optie:**
Voegt een bezit **toe pagina einden** binnen inhoud om overloopgedrag te controleren. Deze optie is zichtbaar slechts wanneer het oudersubform aan Overlopen wordt geplaatst en het **staat pagina paginaeinden** bezit toe wordt toegelaten.

- **Automatische Voortzetting van de Pagina:**
Wanneer de inhoud de beschikbare ruimte overschrijdt, wordt automatisch een nieuwe pagina gemaakt en wordt de bewerking naadloos voortgezet.

- **kopiëren-Deeg Steun:**
Grote tekst die in de editor wordt geplakt, loopt automatisch door de pagina&#39;s heen en behoudt de consistentie van de layout.

### Geplaatste indeling

- **Indicator van de Overstroming:**
Als de inhoud de container (subformulier of pagina) overschrijdt, wordt de teksteditor uitgebreid voor bewerking, maar blijft de hoogte van het element ongewijzigd.

- **Visuele Alarm:**
Onder aan de container wordt een rode rand weergegeven om overloop aan te geven.

- **Handmatige Aanpassing:**
Auteurs passen de grootte van de container handmatig aan de aanvullende inhoud aan.

>[!NOTE]
>
> Voor deze functie moet de volledige bovenliggende hiërarchie (zoals subformulieren) zijn ingesteld op Overlopen. Als om het even welk oudersubform in de hiërarchie wordt gepositioneerd, **paginaeinden** binnen inhoudsoptie toestaat zal niet werken zoals verwacht.

## Voordelen

- Hiermee verbetert u de efficiëntie en controle bij het schrijven van inhoud.

- Hiermee blijven de indeling en leesbaarheid op alle pagina&#39;s consistent.

- Hiermee kunt u overloop snel herkennen aan de hand van visuele indicatoren.

- Verbetert de flexibiliteit van het communicatie ontwerp voor beide lay-outtypes.
