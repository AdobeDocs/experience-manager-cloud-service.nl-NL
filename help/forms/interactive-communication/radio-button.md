---
title: Component Radio Button in Interactive Communication Editor
description: Met de component RadioButton in de Interactive Communication Editor in AEM Forms kunnen auteurs een set opties presenteren die elkaar wederzijds uitsluiten. Dit houdt in dat slechts één optie tegelijk kan worden geselecteerd.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---


# Component Radio Button in Interactive Communication Editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

De **component van de Keuzerondje** in de Interactieve Communicatie (IC) redacteur staat auteurs toe om een reeks wederzijds exclusieve keuzen aan gebruikers-betekenis slechts één optie voor te stellen kan tegelijkertijd worden geselecteerd. Dit maakt het ideaal voor gebruiksgevallen zoals ja/neen vragen, geslachtsselectie, beoordelingsniveaus of vooraf gedefinieerde categoriale reacties.
Keuzerondjes zijn intuïtief, eenvoudig te configureren en kunnen worden gebonden aan back-end gegevensmodellen voor naadloze gegevensvastlegging en -integratie.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/radio.png)

## &#x200B;2. Eigenschappen

De component RadioButton bevat verschillende configureerbare eigenschappen:

2.1. Basisveld

- **Naam:** een uniek herkenningsteken voor het gebied. Het wordt gebruikt voor het van verwijzingen voorzien binnen gegevensmodellen, regels, en bedrijfslogica.

- **Knevel:** staat het bepalen van elke selecteerbare keus in de knoopgroep toe. Elke schakeloptie vertegenwoordigt een mogelijke waarde.

- **Titel:** het etiket verbonden aan de radioknoopgroep om de gebruiker te begeleiden.

- **Reserve:** Facultatieve reservewaarde als geen selectie wordt gemaakt of de gegevensband leeg is.

2.2. Positie

Beschrijving: hiermee wordt de ruimtelijke plaatsing van de groep keuzerondjes in de lay-out geregeld.

**Montages:**

- **x en de coördinaten van Y**

- **Hoogte en Breedte** (die in mm of % voor ontvankelijk lay-outontwerp wordt bepaald)

2.3. Marge

De afstand rondom het tekstvak definiëren:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.4. Aanwezigheid

- **Beschrijving:** bepaalt het zicht van de radioknoopcomponent bij runtime.

- **Opties:**

   - **Zichtbaar:** aan gebruikers wordt getoond en bezet ruimte.

   - **Verborgen (houdt ruimte):** niet zichtbaar maar behoudt lay-out het uit elkaar plaatsen.



2.5. Gegevensbinding

- **Beschrijving:** verbindt de radioknoopgroep met een gegevensmodel voor het vangen van de geselecteerde optie.

- **Bindende Types:**

   - **Naam van het Gebruik:** gebruikt de toegewezen gebiedsnaam als verwijzing voor band.

   - **Globale Gegevens van het Gebruik:** bindt het gebied aan een globaal gegevensmodel of schemaelement.

   - **Geen Binding van Gegevens:** de radioknoopselectie is niet gebonden aan om het even welke gegevensbron; gebruikt voor UI-slechts gedrag.

## &#x200B;3. Gebruik

De component Keuzerondje is geschikt voor scenario&#39;s waarbij gebruikers slechts één waarde in een lijst moeten kiezen. De meest gangbare gebruiksgevallen zijn:

- Een voorkeurscommunicatiemethode selecteren (e-mail / telefoon / sms)

- Bevestigend binaire besluiten (ja/Neen)

- Kiezen uit beperkte opties (bv. geslacht, burgerlijke staat)

- Vermeld de mate van tevredenheid of de schaal van de overeenkomst (bijv. Afwijzen / Neutraal / Akkoord)

Auteurs kunnen gerelateerde keuzerondjes groeperen en deze in lay-outcontainers plaatsen voor een consistente uitlijning. De etiketten kunnen worden geplaatst inline of boven de knopen afhankelijk van visuele ontwerpvereisten.

## &#x200B;4. Beste praktijken

- Beperk het aantal opties tot 5 of minder om te voorkomen dat de gebruiker overweldigt.

- Gebruik duidelijke en beknopte bijschriften om te beschrijven wat de gebruiker selecteert.

- Selecteer desgewenst de meest gebruikelijke of veilige keuze.

- Gebruik geen keuzerondjes als gebruikers meerdere opties mogen kiezen. Gebruik in plaats daarvan selectievakjes.

- Keuzerondjes rechtstreeks binden aan schemaknooppunten bij het integreren met back-end gegevensmodellen.

- Pas consistente spatiëring en uitlijning toe voor meer visuele duidelijkheid, met name in mobiele lay-outs.

De component RadioButton in de Interactieve Communicatie redacteur is een fundamentele inputcomponent die schone, gestructureerde besluitvorming voor eind - gebruikers aanbiedt. Als deze optie is geconfigureerd met duidelijke labels, doordachte spatiëring en gegevensbinding, zorgt deze voor een betrouwbare gegevensverzameling en een vloeiender gebruikerservaring voor formulieren, enquêtes en instapworkflows.


