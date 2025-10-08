---
title: Component selectievakje in interactieve communicatie-editor
description: Met de component Check Box in de Interactive Communication Editor in AEM Forms kunnen gebruikers een of meer binaire selecties maken (ja/nee, true/false).
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# Component selectievakje in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

Met de component Check Box in de Editor Interactive Communication (IC) kunnen gebruikers een of meer binaire selecties maken (ja/nee, true/false). Deze methode wordt vaak gebruikt voor voorwaarden, voorkeuren, toestemmingsvelden en opt-ins en biedt een snelle manier om Booleaanse invoer in een communicatieformulier vast te leggen.

Het selectievakje ondersteunt flexibele stijlen, opties voor gegevensbinding en zichtbaarheidsregels, waardoor het een licht maar krachtig hulpmiddel wordt voor het ontwerpen van interactieve, gebruikersvriendelijke formulieren.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/checkbox.png)

## &#x200B;2. Eigenschappen

2.1 Basisveld

- **Naam:** een uniek herkenningsteken dat voor het van verwijzingen voorzien van checkbox in gegevensmodellen, regels, of manuscripten wordt gebruikt.

- **Knevel:** staat checkbox toe om worden van een knevel te voorzien/weg wanneer geklikt. Dit kan in enige of gegroepeerde wijze worden gebruikt.

- **Titel:** het beschrijvende etiket dat naast checkbox wordt getoond, die gebruikers op begeleidt wat zij aan of het selecteren goedkeuren.

- **Reserve:** Facultatieve placeholder tekst of symbool dat in read-only of reservewijzen wordt getoond wanneer geen interactie wordt gemaakt.

2.2 Positie

Hiermee bepaalt u waar het selectievakje in de layout wordt geplaatst:

- **x en de coördinaten van Y:** plaats de plaats van checkbox binnen het lay-outnet.

- **Hoogte en Breedte:** bepaalt afmetingen van checkbox (in mm of px), vooral belangrijk wanneer het gebruiken van douane visuele stijlen of pictogrammen.

2.3 Marge

Hiermee kunt u ruimte rondom het selectievakje voor layoutaanpassingen plaatsen:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.4 Weergave

Hiermee bepaalt u de visuele opmaak van het selectievakje en het bijbehorende frame:

- **Vulling:** Achtergrondkleur van checkbox (wanneer geselecteerd of unselected).

- **Slag:** de contourkleur van de checkbox grens.

- **Breedte van de Slag:** Dikte van de grenslijn.

- **Stijl:** Ononderbroken, gestormd, of het patroon van het douaneoverzicht.

- **Randen:** bepaalt het hoekstileren van checkbox: afgeronde of scherpe randen afhankelijk van ontwerpvoorkeur.

2.5 Aanwezigheid

Hiermee bepaalt u hoe en wanneer het selectievakje bij uitvoering wordt weergegeven:

- **Zichtbaar:** normaal getoond en bezet ruimte.

- **Verborgen (houdt ruimte):** Verborgen van UI maar de lay-outruimte wordt behouden. Nuttig voor voorwaardelijk zicht zonder layoutbreuk.

2.6 Gegevensbinding

Laat checkbox toe om met externe of interne gegevensbronnen in wisselwerking te staan:

**het Binden Type van Gegevens:**

**Naam van het Gebruik:** bindt de waarde gebruikend de het gebiedsnaam van de component.

**Globale Gegevens van het Gebruik:** verbindt met een globaal gegevensmodel dat over de mededeling wordt gedeeld.

**Geen Gegevens die binden:** Checkbox blijft standalone en niet opgeslagen in het gegevensmodel.

&#x200B;3. Gebruik

De dozen van de controle worden algemeen gebruikt in scenario&#39;s zoals:

- **Toegelaten gebieden:** b.v., &quot;ik ga met de voorwaarden akkoord&quot;

- **voorkeur van de Gebruiker:** b.v., &quot;Abonneren aan nieuwsbrief&quot;

- **veelvoudige keuzeselecties:** b.v., &quot;selecteer alle toepasselijke opties&quot;

- **erkenning van de Vorm:** b.v., &quot;bevestig ik dat de bovengenoemde details correct zijn&quot;

Selectievakjes kunnen in layoutrasters of deelvensters worden geplaatst en worden gegroepeerd om formulieren beter te organiseren.

&#x200B;4. Beste praktijken

- Gebruik duidelijke, beknopte bijschriften om gebruikers te helpen begrijpen wat ze selecteren.

- Vermijd rommelig door controledozen slechts voor binaire input-gebruik radioknopen voor exclusieve opties te gebruiken.

- Zorg voor juiste spatiëring met marge- en layoutinstellingen voor een schone gebruikersinterface.

- Schakel selectievakjes in op een verwijzing naar een zinvol gegevensmodel wanneer de vastgelegde keuze moet worden opgeslagen of verwerkt.

- Gebruik zichtbaarheidsregels wanneer selectievakjes afhankelijk zijn van eerdere invoer of voorwaarden.

De component van de Doos van de Controle in de Interactieve Communicatie redacteur is een eenvoudige nog essentiële component voor binaire input. Met ondersteuning voor opmaak, voorwaardelijke aanwezigheid en flexibele gegevensbinding speelt deze functie een belangrijke rol bij het verbeteren van interactiviteit en gebruikerscontrole in slimme digitale formulieren. Als selectievakjes zijn geïmplementeerd met doordachte labels, consistente opmaak en een zinvolle gegevensintegratie, dragen ze aanzienlijk bij aan een vloeiende en intuïtieve formulierervaring.


