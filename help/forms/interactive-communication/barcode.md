---
title: Streepjescode-component in interactieve communicatie-editor
description: De Component van de streepjescode in Interactieve Communicatie Redacteur in AEM Forms laat auteurs toe om gecodeerde gegevens binnen communicatie malplaatjes visueel te vertegenwoordigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---


# Streepjescode-component in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

De component van de Streepjescode in de Interactieve Communicatie redacteur laat auteurs toe om gecodeerde gegevens binnen communicatie malplaatjes visueel te vertegenwoordigen. Dit is met name handig voor toepassingen die tracking, identificatie, facturering of automatisering bevatten. Met ondersteuning voor verschillende streepjescodenormen, zoals Code 128, QR en meer, biedt deze component flexibele opties voor opmaak, positionering en gegevensbinding die aansluiten bij een groot aantal zakelijke behoeften.

Of u nu klantfacturen, verzendlabels of lidmaatschapskaarten maakt, de component Barcode vereenvoudigt het proces door machineleesbare gegevens rechtstreeks in uw document in te sluiten.

![&#x200B; vind IC Docu &#x200B;](/help/forms/interactive-communication/assets/barcode.png)

## &#x200B;2. Eigenschappen

De component Barcode wordt geleverd met een uitgebreide set configureerbare opties om het gedrag en de weergave ervan te bepalen:

2.1 Basisveld

**Naam:** een uniek herkenningsteken voor de streepjescode. Het wordt gebruikt om naar de component in gegevensmodellen en regelreeksen te verwijzen.

**Plaats:** specificeert waar de streepjescodetekst met betrekking tot het streepjescodesymbool wordt getoond.

**Opties:**

- **niets:** verbergt de tekst.

- **hierboven:** toont de tekst boven de streepjescode.

- **onder:** toont de tekst onder de streepjescode.

- **boven Ingebed:** sluit de tekst binnen het hoogste gebied van de streepjescode in.

- **onder Ingebed:** sluit de tekst binnen het bodemgebied van de streepjescode in.

- **Type:** specificeert de streepjescodenorm (bijvoorbeeld, Code 128, Code 39, QR Code, enz.).

- **Gebrek:** een vooraf bepaalde waarde die verschijnt als geen gegevens wordt verstrekt.

- **Lengte van Gegevens:** wijst op het verwachte of maximumaantal karakters de streepjescode kan houden.

- **Controlesom:** bevestigt streepjescodegegevens voor nauwkeurigheid.

   - **Opties:**

      - **niets:** geen checksum bevestiging.

      - **Auto:** berekent automatisch controlesom die op het type wordt gebaseerd.

- **Brede/Nijlverhouding:** bepaalt de relatieve breedte van de brede bars aan smalle degenen (die in sommige 1D barcodes worden gebruikt).

2.2 Locatie

Hiermee bepaalt u waar de streepjescode wordt weergegeven ten opzichte van de inhoud:

- **niets:** Geen extra het plaatsen.

- **hierboven:** Plaatst de streepjescode boven de verwante inhoud.

- **onder:** Plaatst de streepjescode onder de inhoud.

- **boven Ingebed:** de Streepjescode is ingebed en drijft boven de inhoud.

- **onder Ingebed:** Ingebed onder inhoud.

2.3 Positie

Hiermee definieert u de exacte plaatsing van de streepjescode in de layout:

- **X en de Coördinaten van Y:** Plaats de streepjescode binnen de vorm gebruikend millimeter eenheden.

- **Hoogte en Breedte:** plaats de fysieke afmetingen van de streepjescode.

2.4 Marge

Hiermee voegt u ruimte toe rond de streepjescode voor een betere visuele scheiding:

- Boven

- Onder

- Links

- Rechts

Deze marges helpen u bij de consistentie en leesbaarheid van de layout.

2.5 Weergave

De visuele stijl van de streepjescode aanpassen:

- **Vulling:** Achtergrondkleur van het streepjescodegebied.

- **Slag:** kleur van de Grens.

- **Breedte:** bepaalt de dikte van de streepjescoderegels.

- **Stijl:** kies van vooraf instelt zoals vlak, begrensd, of opgeheven.

- **Randen:** besluit tussen afgeronde of scherpe hoeken voor de streepjescodedoos.

2.6 Aanwezigheid

Bepaalt of de streepjescode tijdens runtime wordt weergegeven of verborgen:

- **Zichtbaar:** de Streepjescode wordt getoond in de definitieve output.

- **Verborgen:** de ruimte is gereserveerd maar de streepjescode wordt niet getoond.

2.7 Gegevensbinding

Gegevensbinding: hiermee wordt de streepjescode verbonden met een back-end gegevensmodel (XML of JSON). Hierdoor weerspiegelt de streepjescode dynamisch unieke gegevens per documentinstantie, zoals een bestellings-id of trackingnummer.

## &#x200B;3. Gebruik

De component Streepjescode is vooral handig bij het automatiseren van processen die afhankelijk zijn van gescande gegevens. Het kan aan communicatie malplaatjes zoals worden toegevoegd:

- Facturen (voor klantenreferentie en snelle scanbetalingen)

- Verzendlabels (voor bijhouden van pakketten)

- Lidmaatschap of Loyalty-kaarten (voor identificatie op basis van scan)

- Coupons en vouchers (voor validatie op het verkooppunt)

Auteurs kunnen de streepjescode insluiten in lay-outcontainers en deze opmaken op basis van het merk of het documentthema.

## &#x200B;4. Beste praktijken

- Gebruik een geschikt streepjescodetype voor het gebruik van hoofdletters en kleine letters, bijvoorbeeld QR-code voor URL&#39;s, Code 128 voor alfanumerieke id&#39;s.

- Valideer de leesbaarheid van streepjescodes door testversies af te drukken en te scannen.

- Zorg voor gegevensintegriteit met de optie controlesom als de standaard voor streepjescodes dit ondersteunt.

- Kies leesbare grootten en lijnbreedten om scanproblemen te voorkomen.

- Houd voldoende marges aan om uitknippen te voorkomen bij het afdrukken.

Met de component Streepjescode in de interactieve communicatie-editor kunnen makers van documenten de kloof tussen digitale en fysieke systemen overbruggen. Wanneer het effectief wordt uitgevoerd, verbetert het automatisering, verbetert het gebruikersgemak, en steunt naadloze integratie met aftastenapparaten en werkschema&#39;s.
