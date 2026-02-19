---
title: Een interactief communicatiefragment maken
description: Creeer Interactieve Communicatie Fragments in AEM Forms om modulaire, herbruikbare inhoudsblokken te bouwen die consistentie verzekeren, tijd besparen, en gepersonaliseerde, gegeven-gedreven mededelingen steunen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 81779df9-c101-4c39-a779-651cafc70eb9
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Gegevensbinding in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

## &#x200B;1. Inleiding

Gegevensbinding in de Interactieve Communicatie Redacteur verbindt op-canvasgebieden met een beheerde gegevenslaag zodat de mededelingen met echte, contextafhankelijke informatie teruggeven. Door componenten aan een Model van de Gegevens van de Vorm (FDM) te verbinden, kunnen de auteurs nauwkeurigheid verzekeren, handwerk verminderen, en dynamische, gepersonaliseerde ervaringen leveren.

Naast het eenvoudig verbinden van waarden, steunt de Bindingen van Gegevens in IC visuele afbeelding, vooraf ingevulde, en synchronisatie, toelatend auteurs om sneller te ontwerpen terwijl het blijven gericht aan achterste deelsystemen en gegevensmodellen.

![ vinden IC Doc ](/help/forms/interactive-communication/assets/data-binding1.png)

## &#x200B;2. Eigenschappen

2.1 Gegevensverbindingen (FDM) beheren

- **selecteer FDM:** kies het aangewezen Model van de Gegevens van de Vorm (b.v., klanten, rekeningen, of beleid). Dit vestigt het gebiedende schema voor gebieden, series, en voorwerpen die in de mededeling worden gebruikt.

- **creeer Gegevens Bindend:** Zodra de banden worden toegelaten, kan elk gebied met wegen worden geassocieerd FDM, minimaliserend fouten en het verzekeren van verenigbare integratie.

- **Bindende Gebieden aan het Model van Gegevens:** de gebieden van het Punt aan specifieke knopen (bijvoorbeeld, customer.name, policy.holder.id) om het teruggeven met levende gegevens te drijven en bevestigingen of voorwaardelijke logica te steunen.

2.2 Gegevensbinding maken

- **Visuele Toewijzing:** belemmering-en-dalingsafbeelding tussen gebieden en FDM knopen helpt niet-technische gebruikers fouten vermijden.

- **Vereniging van het Gebied:** bepaal de doelweg, gegevenstype (tekst, aantal, datum, boolean, beeld), en facultatieve formatters (b.v., datummasker, munt).

- **Bind Voorproef:** de banden van de Test met steekproefgegevensreeksen om het formatteren en correctheid te bevestigen alvorens te publiceren.

## &#x200B;3. Gebruik

Gegevensbinding wordt doorgaans gebruikt wanneer communicatie gezaghebbende records moet weergeven of gebruikersinvoer moet vastleggen. Voorbeelden zijn:

- **Personalization:** bevolkt klantendetails zoals naam, adres, of rekeningssaldo.

- **Voorwaardelijke Inhoud:** toon/verberg secties die op modelwaarden (b.v., actieve vs inactieve klanten) worden gebaseerd.

- **Inzamelingen en Lijsten:** geef geschiedenissen, transacties, of gespecificeerde lijsten van series terug.

- **Beelden en Media:** Bind profielfoto&#39;s, bedrijflogo&#39;s, of productbeelden.

- **Overzicht en eSign:** Vul vormen met gegevens vooraf in en sta updates door tweewegssynchronisatie toe.

Auteurs selecteren doorgaans de FDM vroeg in het project, wijzen visueel velden toe tijdens het ontwerp en testen met voorbeeldgegevens voordat ze publiceren.

## &#x200B;4. Beste praktijken

- **bepaal vroeg schema:** voltooi FDM alvorens te binden om later opnieuw in kaart te brengen te vermijden.

- **visuele afbeelding van het Gebruik:** verhindert typos en onjuist aangepaste wegen door op belemmering-en-daling te vertrouwen.

- **bevestigt gegevenstypes:** pas formatters voor munt, data, of telefoonaantallen toe om consistentie te verzekeren.

- **houd uitdrukkelijk banden:** elk gebied zou duidelijk aan één enkele gegevensknoop in kaart moeten brengen.

- **Test met steekproefgegevens:** Voorproef zowel gemeenschappelijke als randgevallen (b.v., lege waarden, lange series).

- **Beperk bidirectionele synchronisatie:** Gebruik slechts wanneer uitgeeft of goedkeuringen worden vereist.

- **Modulariseer inzamelingen:** de malplaatjerijen van het Gebruik voor herhaalbare structuren.

- **Veilige gevoelige gegevens:** pas het maskeren, encryptie, en minst-voorrecht toegang voor PII of betalingsdetails toe.

Door de Bindende gegevens van Gegevens zorgvuldig te vormen, creëren de auteurs een betrouwbare brug tussen ontwerp en gegeven-versnellend communicatie creatie, die nauwkeurigheid verzekeren, en hoogst gepersonaliseerde ervaringen bij schaal leveren.
