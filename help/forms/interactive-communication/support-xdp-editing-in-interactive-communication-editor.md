---
title: Ondersteuning voor XDP-bewerking in de Interactive Communication Editor
description: Dankzij de ondersteuning voor XDP-bewerking in de Interactive Communication Editor kunnen bestaande xdps worden bewerkt in de Interactive Communication Editor.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 957944da363b506c34c2630aeedbe984442f34b8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Ondersteuning voor XDP-bewerking in de Interactive Communication Editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## Inleiding

De Interactieve Communicatie (IC) Redacteur biedt nu naadloze **steun voor het uitgeven van XDP (het Pakket van Gegevens van XML) dossiers** binnen het auteursmilieu aan. Dankzij deze uitbreiding kunnen auteurs XDP-sjablonen moeiteloos beheren, wijzigen en onderhouden, zonder dat ze hiervoor externe tools nodig hebben. Met deze mogelijkheid kunnen gebruikers XDP-bestanden rechtstreeks uploaden, weergeven en bewerken in de IC Editor, waardoor een uniforme en efficiënte workflow voor ontwerp en levering mogelijk wordt.

## Hoe te om Steun XDP het Uitgeven in Interactieve Communicatie Redacteur te gebruiken

![ vinden IC Doc ](/help/forms/interactive-communication/assets/support-xdp.png)

1. Navigeer aan **Forms > Forms &amp; Documenten**.

1. Upload uw .xdp- dossier gebruikend **creeer > Dossier uploadt** optie.

1. Open XDP in **Interactieve Communicatie Redacteur**.

1. Maak noodzakelijk **ontwerp of gegeven-bindende** veranderingen.

1. Sla uw wijzigingen op. Updates worden automatisch weergegeven in het XDP-bronbestand.

## Belangrijkste mogelijkheden

- **uploadt en beheert XDP Dossiers:**
Upload XDP malplaatjes door **Manager van Forms**. Zodra geüpload, worden zij beschikbaar voor direct het uitgeven in de Interactieve Communicatie Redacteur.

- **geef het Gebruiken van de Redacteur van IC uit:**
Open en bewerk XDPs gebruikend de Redacteur van IC met volledige toegang tot bestaande het uitgeven eigenschappen, met inbegrip van lay-outaanpassingen, gegevensband, het stileren, en componentenconfiguratie.

- **sparen terug naar Source:**
Eventuele wijzigingen die zijn aangebracht via de IC Editor, worden rechtstreeks opgeslagen in het oorspronkelijke XDP-bestand, waarbij de versieintegriteit behouden blijft en de ontwerpworkflow wordt vereenvoudigd.

## Fragmentondersteuning

- **Verwijzingen van het fragment:**
Als een XDP verwijzingen een fragment, dat fragment in **AEM bij de zelfde relatieve weg** moet bestaan zoals die in het XDP dossier wordt bepaald.
Als een fragment mist, toont de redacteur a **waarschuwend bericht** erop wijzend dat het vereiste fragment niet aanwezig is.

- **hergebruik van het fragment in Redacteur:**
Alle bestaande fragmenten XDP verschijnen in het **Comité van Fragmenten** van de Redacteur van IC.
De auteurs kunnen **slepen en** deze fragmenten direct op het canvas laten vallen. De verwijzingen worden bewaard, ervoor zorgend dat de updates aan fragmenten zich over alle XDPs gebruikend hen verspreiden.

## Voordelen

- Elimineert gebiedsdeel op externe hulpmiddelen voor wijziging XDP.

- Behoudt bestaande gegevensbindingen en fragmentrelaties.

- Maakt consistent ontwerp en snellere iteratiecycli mogelijk.

## Aanbevolen procedures

- Zorg ervoor dat alle fragmenten waarnaar wordt verwezen, aanwezig zijn in het juiste relatieve pad voordat u gaat bewerken.

- Gebruik versiebeheer voor het beheer van updates voor XDP- en fragmentafhankelijkheden.

- Valideer gegevensbindingen na bewerking om de juiste rendering te bevestigen.

