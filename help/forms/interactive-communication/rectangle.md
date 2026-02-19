---
title: Rechthoekcomponent in interactieve communicatie-editor
description: Met de Rectangle Component in Interactive Communication Editor in AEM Forms kunnen auteurs vormgegeven grafische elementen toevoegen die fungeren als lay-outscheidingslijnen, visuele accenten of inhoudscontainers.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: d2af7706-2b2a-4a40-a4a4-375b5f2b08fb
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Rechthoekcomponent in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

## &#x200B;1. Inleiding

Met de component Rectangle in de IC-editor (Interactive Communication) kunnen auteurs gevormde grafische elementen toevoegen die fungeren als lay-outscheidingslijnen, visuele accenten of inhoudscontainers. Met rechthoeken wordt de visuele hiërarchie verbeterd en wordt de aandacht van gebruikers gevestigd op gestructureerde communicatielay-outs.
Deze component is niet gekoppeld aan gegevens, maar draagt bij tot een betere ontwerphelderheid, het groeperen van verwante velden en het verbeteren van de algehele presentatie.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/rectangle.png)

## &#x200B;2. Eigenschappen

De component Rectangle bevat verschillende aanpasbare eigenschappen:

2.1. Naam

Naam: een unieke id voor de rechthoek. Wordt voornamelijk gebruikt voor het verwijzen in lay-outhiërarchieën of het consistent toepassen van stijlen.

2.2. Positie

- **Beschrijving:** bepaalt waar de rechthoek in de documentlay-out verschijnt.

- **Montages:**

   - **x en de coördinaten van Y:** bepalen horizontale en verticale plaatsing.

   - **Hoogte en Breedte (in mm):** controleert de grootte van de rechthoek.

2.3. Marge

Hiermee definieert u de afstand rondom de rechthoekcomponent om deze te scheiden van andere UI-elementen:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.4. Vorm

- **Beschrijving:** beheert het visuele stileren van de rechthoek.

- **de Opties van de Aanpassing:**

   - **Vulling:** de interne kleur van de rechthoek.

   - **Slag:** de contourkleur van de rechthoek.

   - **Breedte van de Slag:** Dikte van de grens van de rechthoek.

   - **Stijl:** vooraf ingestelde stijlen zoals vlak, begrensd, of opgeheven.

   - **Randen:** controleert hoekverschijning (b.v., afgeronde of scherpe randen).

2.5. Aanwezigheid

- **Beschrijving:** specificeert of de rechthoek wordt getoond wanneer de mededeling wordt teruggegeven.

- **Opties:**

   - **Zichtbaar:** toont de rechthoek bij runtime.

   - **Verborgen:** houdt de lay-outruimte zonder de rechthoek te tonen.

## &#x200B;3. Gebruik

De component Rectangle wordt gewoonlijk gebruikt voor lay-out- en opmaakdoeleinden in plaats van voor inhoudsinvoer. Vaak voorkomende gevallen van gebruik zijn:

- Visuele scheiding tussen secties maken

- Gegroepeerde elementen markeren

- De leesbaarheid en visuele balans verbeteren

- Kop-, voettekst- of uitroepsecties omlijnen

Rechthoeken kunnen worden gecombineerd met andere indelingselementen, zoals subformulieren of containers voor complexe visuele ontwerpstructuren.

## &#x200B;4. Beste praktijken

- Gebruik consistente opmaak voor rechthoeken in uw layout om de visuele harmonie te waarborgen.

- Pas adequate marges en spatiëring toe om te voorkomen dat aangrenzende velden overbevolkt raken.

- Kies de vul- en lijnkleuren die zijn uitgelijnd op uw merk of documentthema.

- Gebruik naar beneden afgeronde randen om de esthetiek in moderne UI-lay-outs te verbeteren.

- Verberg rechthoeken als deze alleen nodig zijn voor ontwerpdoeleinden tijdens het bewerken maar niet voor de uiteindelijke uitvoer.

De component Rectangle is een niet-interactief maar toch krachtig gereedschap in de IC-editor. Als de stijl en positie effectief zijn, verbetert deze de precisie van de layout, de visuele stroom en de gebruikerservaring zonder dat de gegevensbinding of de interactiviteit complexer wordt.
