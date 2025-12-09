---
title: Datum-/tijdveld in interactieve communicatie-editor
description: De Component van het Gebied van de datum/van de Tijd in Interactieve Communicatie Redacteur in AEM Forms om auteurs toe te laten om gebieden op te nemen waar de gebruikers datum en/of tijdwaarden kunnen selecteren of ingaan.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---


# Component Datum-/tijdveld in interactieve communicatie-editor

>[!NOTE]
>
> De interactieve communicatiecapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## &#x200B;1. Inleiding

De **component van het Gebied van de Datum/van de Tijd** {in de Interactieve Communicatie (IC) redacteur laat auteurs toe om gebieden op te nemen waar de gebruikers datum en/of tijdwaarden kunnen selecteren of ingaan. Deze component wordt doorgaans gebruikt voor het vastleggen van gegevens zoals geboortedatum, afstellingsschema&#39;s, boekingssleuven of datum van afgifte/vervaldatum van documenten.

Het veld ondersteunt diverse opmaakopties (bijvoorbeeld DD/MM/JJJJ, 24-uurs of 12-uursnotaties), validatiebeperkingen en aanpassing van weergave aan het communicatieontwerp. Het verbetert gebruikerservaring door handinputfouten te verminderen en consistentie in gegevensinzameling te bevorderen.

![ vind IC Docu ](/help/forms/interactive-communication/assets/datetime.png)

## &#x200B;2. Eigenschappen

De component Datum-/tijdveld bevat verschillende configureerbare eigenschappen:

2.1. Basisveld

- **Naam:** een uniek herkenningsteken voor het gebied. Wordt gebruikt voor het verwijzen in regels, expressies en gegevensbindingen.

- **Titel:** het etiket dat naast het gebied wordt getoond om zijn doel (b.v., &quot;Datum van geboorte&quot;te wijzen).

- **Datum:** staat gebruikers toe om een kalenderdatum te plukken of in te voeren.

- **Tijd:** laat ingang of selectie van specifieke tijdwaarden toe als gevormd.

- **Reserve:** een fallback waarde die wordt getoond wanneer geen input wordt verstrekt, nuttig voor read-only of drukscenario&#39;s.

- **Verschijning:** selecteer een visuele stijl zoals onderstreepte, grens, of vlakke voor verenigbare teruggeven UI.

2.2. Typografie

Hiermee bepaalt u de stijl van de tekst binnen het datum-/tijdveld:

- **de variatie van het Doopvont:** de Opties omvatten Regelmatig, Vet, Cursief afhankelijk van themavereisten.

- **de grootte van de Doopvont:** Gebrek dat aan 10 pt wordt geplaatst om consistentie met vormlay-out te handhaven.

2.3. Positie

- **Beschrijving:** bepaalt de plaatsing van het datum/tijdgebied op de vormlay-out.

- **Montages:**

   - **x en de coördinaten van Y**

   - **Hoogte en breedte** (die in mm of pixel wordt gemeten) voor het nauwkeurig rangschikken van het gebied.

2.4. Marge

Hiermee definieert u de ruimte rondom het veld voor duidelijke uitlijning en flexibiliteit van de layout:

- Boven (boven)

- Onder (omlaag)

- Links

- Rechts

2.5. Vorm

Definieert de stijl van de container om de visuele consistentie en helderheid te behouden:

- **Vulling:** Achtergrondkleur van het gebied.

- **Slag:** kleur van de Grens rond het gebied.

- **Breedte:** Dikte van de grens.

- **Stijl:** de types van Grens zoals ononderbroken, gestreepte, of niets.

- **Randen:** kies van scherpe of rond gemaakte hoeken afhankelijk van vormthema.

2.6. Aanwezigheid

Hiermee bepaalt u hoe het veld zich gedraagt bij uitvoering:

- **Zichtbaar:** het gebied wordt getoond aan gebruikers en bezet lay-outruimte.

- **Verborgen (houdt ruimte):** het gebied is niet zichtbaar maar de ruimte is nog gereserveerd voor het in de lay-out.

2.7. Gegevensbinding

Koppelt het veld aan een gegevensbron om waarden op te slaan of op te halen.

- **het Bindende Type van Gegevens:** specificeert hoe het gebied met gegevens verbindt.

- **Naam van het Gebruik:** bindt het gebied gebruikend de gebiedsnaam die in het schema wordt bepaald.

- **Globale Gegevens van het Gebruik:** verbindt het gebied met globaal-vlakke gegevens die over de mededeling worden gedeeld.

- **Geen Bindende Gegevens:** het Gebied wordt niet verbonden met om het even welke achtergrondgegevens (die voor visueel slechts of berekende waarden worden gebruikt).

## &#x200B;3. Gebruik

Het datum-/tijdveld is ideaal in situaties waarin consistente tijdgegevens vereist zijn. Vaak voorkomende gevallen van gebruik zijn:

- Vastlegdatum van geboorte, datum van benoeming of tijd van gebeurtenis

- Probleem/vervaldatum van het registratiedocument

- Leverings- of ophaalsleuven selecteren

- Tijdstempels van transacties opnemen

Auteurs kunnen het veld combineren met lay-outcontainers, validaties of voorwaardelijke regels om de indeling, vereiste velden en contextgevoelige zichtbaarheid te bepalen.

## &#x200B;4. Beste praktijken

- Gebruik duidelijke bijschriften, zoals &quot;Selecteer een datum&quot; of &quot;Benoemingstijd&quot;, als richtlijn voor gebruikers.

- Schakel datum-/tijdkiezer in voor betere UX en minder invoerfouten.

- Pas indien nodig opmaakbeperkingen toe (bijvoorbeeld alleen toekomstige datums).

- Geef een gereserveerde waarde op voor toegankelijkheid of fallback.

- Zorg dat typografie en weergave consistent blijven met het algemene formulierontwerp.

- Koppel het veld aan een geldig schemapad voor een correcte gegevensvastlegging en -verwerking.

De component van het Gebied van de Datum/van de Tijd in de Interactieve Communicatie redacteur is een krachtige en gebruikersvriendelijke component die op tijd-gebaseerde input stroomlijnt. Met de juiste configuratie van de stijlen, gegevensverwerking en lay-outbesturingselementen, biedt deze functie een schone, betrouwbare en intuïtieve ervaring voor zowel gebruikers als back-endsystemen.

