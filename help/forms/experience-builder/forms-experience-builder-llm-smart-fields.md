---
title: Slimme velden met LLM-functionaliteit in Forms Experience Builder
description: Leer hoe u intelligente formuliervelden maakt met vooraf ingevulde opties in de AI-kennisbasis voor geografische gegevens, bedrijfsclassificaties en industriestandaarden.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 0%

---


# Slimme velden met LLM-functionaliteit in Forms Experience Builder {#llm-enhanced-smart-fields}

Forms Experience Builder maakt gebruik van de kracht van Large Language Models (LLM&#39;s) om intelligente formuliervelden te maken met kant-en-klare opties die op basis van uitgebreide kennis kunnen worden gemaakt. Met deze functie hoeft u geen uitgebreide gegevenssets handmatig te onderzoeken en in te voeren, wat de efficiëntie en nauwkeurigheid van het maken van formulieren aanzienlijk verbetert.

## Wat zijn LLM-Verbeterde slimme gebieden? {#what-are-llm-smart-fields}

Slimme velden met LLM-functionaliteit zijn formuliervelden die automatisch worden gevuld met uitgebreide, nauwkeurige gegevens op basis van de ingebouwde kennisbasis van de AI. In plaats van handmatig vervolgkeuzelijsten of optiesets te maken, kunt u velden aanvragen waarvoor uitgebreide gegevenssets vereist zijn. De AI genereert dan automatisch de juiste opties.

**Zeer belangrijke voordelen:**

* **Uitgebreide gegevensreeksen** - Toegang tot uitgebreide, bijgewerkte informatie over veelvoudige domeinen
* **Automatische bevolking** - Geen behoefte om gegevens manueel te onderzoeken en in te voeren
* **Gestandaardiseerde formaten** - gebruikt industrie-standaardcodes, classificaties, en noemende overeenkomsten
* **context-bewuste opties** - de Gebieden kunnen aanpassen gebaseerd op andere vormselecties
* **Tijd-sparen** - vermindert de tijd van de vormverwezenlijking van uren aan notulen

## Wanneer moet u met LLM verbeterde slimme velden gebruiken? {#when-to-use-smart-fields}

Gebruik slimme velden met LLM-ondersteuning wanneer dat nodig is:

* **Uitgebreide gegevensreeksen** - Gebieden die uitgebreide, gestandaardiseerde informatie vereisen
* **Normen van de Industrie** - Classificaties, codes, of regelgevende gegevens
* **Geografische informatie** - Plaats, gebieden, of administratieve afdelingen
* **Professionele gegevens** - de titels van de Baan, certificatie, of de industrieclassificaties
* **Technische normen** - de formaten van het dossier, protocollen, of systeemspecificaties

## Geografische en locatievelden {#geographic-location-fields}

Maak op locatie gebaseerde velden met uitgebreide geografische gegevens en administratieve informatie.

### Luchthavens en vervoer

**Internationale luchthavens met codes IATA:**

     voeg een drop-down voor vertrekluchthavens met alle belangrijke internationale luchthavens 
     toe toevoegt het gebied van de aankomstLuchthaven met IATA codes en volledige namen 
     creeer een gebied voor dichtstbijzijnde luchthaven aan gebruikersplaats 
     voeg een selectie van treinstations voor Europese steden 
 toe
**herinneringen van het Voorbeeld:**

* &quot;Voeg een vertrekveld toe met alle grote luchthavens wereldwijd, inclusief IATA-codes en stadsnamen.&quot;
* &quot;Maak een instapmodel voor luchthavens met internationale luchthavens georganiseerd door continent&quot;
* &quot;Inclusief selectie van stations voor grote Europese steden met stationscodes&quot;

### Administratieve regio&#39;s

**Landen, staten, en provincies:**

     voeg een volledige lijst van de staten van de V.S. met afkortingen 
     tot een landdrop-down met de codes van ISO en volledige namen 
     toe voeg een gebied voor grote wereldsteden met tijdzones 
     omvat een daling van Canadese provincies en gebieden 
     een gebied voor de districten van het VK en postgebieden 
 toe
**herinneringen van het Voorbeeld:**

* &quot;Een selectieveld voor een land maken met ISO-landcodes en volledige namen&quot;
* &quot;Voeg een vervolgkeuzelijst voor de Amerikaanse staat toe met de namen state abbrevitions en full names&quot;
* &quot;Neem een veld in de Canadese provincie op met gebieden en postcodes&quot;
* &quot;Maak een wereldstadveld met grote metropolitane gebieden en tijdzones&quot;

## Bedrijfsgegevens {#business-industry-data}

Gebruik van uitgebreide bedrijfsclassificaties en professionele gegevens voor bedrijfsformulieren.

### Bedrijfsclassificaties

**de types van Industrie en bedrijfsentiteit:**

     voeg een gebied voor de industrieclassificatie met de codes van NAICS 
     toe leidt tot een daling van bedrijfentiteit types (LLC, Bedrijf, Partnerschap, enz.)
     voeg een gebied voor de categorieën van de bedrijfgrootte (opstarten, KMO, onderneming) toe 
     omvat afdelingsselectie voor grote organisaties 
     een gebied voor de professionele diensttypes 
 toevoegen
**herinneringen van het Voorbeeld:**

* &quot;Creeer een uitvoerig industrieterrein gebruikend standaard NAICS classificatie met technologiesubcategorieën&quot;
* &quot;Voeg een soort bedrijfsentiteit vervolgkeuzelijst met juridische structuren en beschrijvingen toe&quot;
* &quot;Neem een veld voor de bedrijfsomvang op met reeksen voor het aantal werknemers en tussen inkomens&quot;

### Beroepsclassificaties

**de titels en certificaties van de Baan:**

     voeg een gebied voor baantitels met gemeenschappelijke industriefollen 
     toe leidt tot een daling van professionele certificatie door gebied 
     omvat onderwijsniveaus met gradentypen 
     voeg een gebied voor jaren van ervaringswaaiers 
     tot een selectie voor programmeertalen en kaders 

**herinneringen van het Voorbeeld:**

* &quot;Neem een professionele certificaatvervolgkeuzelijst op die wordt aangepast op basis van het geselecteerde taakveld&quot;
* &quot;Een veld voor de functie maken met gemeenschappelijke rollen in technologie, gezondheidszorg en financiën&quot;
* &quot;Voeg een onderwijsniveaugebied met graadtypes en specialisaties toe&quot;

## Normen en regelgevingsgegevens {#standards-regulatory-data}

Toegang tot gestandaardiseerde codes, classificaties en informatie over regelgeving voor formulieren die gericht zijn op naleving.

### Financiële en juridische

**Valuta, belasting, en betalingsinformatie:**

     voeg een gebied voor muntcodes met symbolen en wisselkoersen 
     toe leidt tot een daling van de types van fiscale identiteitskaart door land 
     omvat een gebied voor wettelijke documenttypes 
     toevoegt de opties van de betalingsmethode met veiligheidseigenschappen 
     tot een selectie voor bancaire instellingen door land 

**herinneringen van het Voorbeeld:**

* &quot;Een valutaselectieveld maken met ISO-codes, -symbolen en -valuta&#39;s&quot;
* &quot;Een veld van het type BTW-ID toevoegen met landspecifieke belastingidentificatieformulieren&quot;
* &quot;Neem een vervolgkeuzelijst met betalingsmethoden op met beveiligingsfuncties en verwerkingstijden&quot;

### Technische normen

**Indelingen en protocollen van het Dossier:**

     voeg een daling van dossierformaattypes met uitbreidingen 
     toe omvat netwerkprotocolopties 
     een gebied voor gegevensbestandtypes en versies 
     creeer een selectie voor API authentificatiemethodes 

**herinneringen van het Voorbeeld:**

* &quot;Een vervolgkeuzelijst met bestandsindelingen maken met algemene extensies en MIME-typen&quot;
* &quot;Een selectieveld voor een database toevoegen met versies en functievergelijkingen&quot;
* &quot;Een veld voor een API-verificatiemethode met beveiligingsniveaus opnemen&quot;

## Gezondheidszorg en medische velden {#healthcare-medical-fields}

Gespecialiseerde gegevens op het gebied van geneeskunde en gezondheidszorg voor specifieke vormen van industrie.

### Medische classificaties

**Specialty&#39;s en medische gegevens:**

     voeg een gebied voor medische specialiteiten 
     toe leidt tot een daling van gemeenschappelijke geneesmiddelen met generische namen 
     omvat een gebied voor de types van verzekeringsleverancier 
     toevoegen een selectie voor de medische verhoudingen van het noodcontact 
     tot een gebied voor dieetbeperkingen en allergieën 

**herinneringen van het Voorbeeld:**

* &quot;Een vakgebied voor medische specialiteiten maken met subspecialiteiten en certificeringen aan boord&quot;
* &quot;Voeg een veld voor geneesmiddelen toe met generieke namen, merknamen en doseringsvormen&quot;
* &quot;Neem een veld voor een verzekeringsprovider op met belangrijke vervoerders en typen plannen&quot;

## Intelligentie tijd en kalender {#time-calendar-intelligence}

De slimme datum en tijdgebieden met bedrijfscontext en het plannen van intelligentie.

### Datum- en tijdvelden

**Bedrijfsuren en het plannen:**

     voeg een gebied voor kantooruren met tijdzone behandeling 
     toe creeert een daling van openbare vakanties door land 
     seizoensgebonden opties met datumwaaiers 
     voegt een gebied voor conferentiezaal het boeken met beschikbaarheid 
     tot een selectie voor terugkomende vergaderingspatronen 
 toe
**herinneringen van het Voorbeeld:**

* &quot;Een veld voor kantooruren maken met uitzonderingen voor tijdzones en vakanties&quot;
* &quot;Een selectie voor feestdagen toevoegen met landspecifieke opmerkingen&quot;
* &quot;Neem een terugkerend veld voor een vergaderingspatroon op met frequentieopties&quot;

## Product- en servicecategorieën {#product-service-categories}

Elektronische handel en dienstgerichte gebieden met uitvoerige categorisering.

### E-handelsclassificaties

**Product en de dienstgegevens:**

     voeg een gebied voor productcategorieën met subcategorieën 
     toe leidt tot een daling van het verschepen methodes met leveringsramingen 
     omvat een gebied voor de opties van het terugkeerbeleid 
     een selectie voor klant prioritaire niveaus 
     tot een gebied voor het factureren van abonnementen cycli 

**herinneringen van het Voorbeeld:**

* &quot;Een veld voor een productcategorie maken met subcategorieën voor e-handel en SKU-patronen&quot;
* &quot;Voeg een vervolgkeuzelijst voor verzendmethoden toe met levertijden en kostenramingen.&quot;
* &quot;Neem een veld voor de factureringscyclus voor abonnementen op met betaalfrequenties&quot;

## Aanbevolen procedures voor slimme velden met LLM-functionaliteit {#best-practices-smart-fields}

### Wees specifiek in uw verzoeken

**Goede voorbeelden:**

* &quot;Een vervolgkeuzelijst voor landen toevoegen met ISO-codes, volledige namen en valutagegevens&quot;
* &quot;Een vakgebied voor medische specialiteiten maken met boordcertificeringen en subspecialiteiten&quot;
* &quot;Neem een veld voor de programmeertaal op met frameworks en vaardigheidsniveaus&quot;

**vermijd vage verzoeken:**

* &quot;Een landveld toevoegen&quot;
* &quot;Een vervolgkeuzelijst voor de functie maken&quot;
* &quot;Veld voor een productcategorie opnemen&quot;

### Combineren met voorwaardelijke logica

Slimme velden werken uitzonderlijk goed met voorwaardelijke regels:

     creeer een professioneel certificatiegebied dat relevante opties toont die op de geselecteerde industrie 
     worden gebaseerd voeg een stadsgebied toe dat de filters die op het geselecteerde land 
     worden gebaseerd een universitair gebied omvatten dat zich op het gekozen gebied van studie 
 aanpast
### Valideren en aanpassen

Hoewel velden met LLM-ondersteuning uitgebreide gegevens bieden, moet u altijd:

* **herzie de geproduceerde opties** voor nauwkeurigheid en relevantie
* **voeg douaneopties** specifiek voor uw organisatie toe
* **verwijder irrelevante opties** om gebruikerservaring te stroomlijnen
* **Test met echte gebruikers** om bruikbaarheid te verzekeren

## Geavanceerde technieken voor slimme velden {#advanced-smart-field-techniques}

### Contextgevoelige velden

Velden maken die worden aangepast op basis van andere formulierselecties:

     voeg een gebied van de universiteitsselectie met belangrijke die instituten toe door land en rangschikkend 
     worden georganiseerd leidt tot een professionele certificatiedropdown die relevante opties toont die op baantitel 
     worden gebaseerd omvatten een stadsgebied dat filters die op geselecteerd land en gebied 
 worden gebaseerd
### Classificaties op meerdere niveaus

hiërarchische gegevensstructuren maken:

     creeer een gebied van de productcategorie met belangrijkste categorieën, subcategorieën, en producttypes 
     een geografisch gebied met land, staat/provincie, en de niveaus van de stad 
     omvatten een gebied van de vaardigheidsbeoordeling met categorieën, subcategorieën, en de niveaus van de bekwaamheden 

### Integratie met externe gegevens

Combineer LLM-kennis met de gegevens van uw organisatie:

     voeg een afdelingsgebied toe dat zowel standaard collectieve afdelingen als de specifieke afdelingen van uw organisatie 
     omvat tot een productgebied leiden dat industrie-standaardcategorieën met uw productcatalogus 
     omvat een plaatsgebied dat geografische gegevens met uw bureauplaatsen 
 samenvoegt
## Problemen met slimme velden oplossen {#troubleshooting-smart-fields}

### Gemeenschappelijke problemen en oplossingen

**Uitgave: Te veel gegenereerde opties**

* **Oplossing**: Ben specifieker in uw verzoek of voeg filtrerende criteria toe
* **Voorbeeld**: In plaats van &quot;alle landen,&quot;verzoek &quot;belangrijke handelspartners&quot;

**Uitgave: Ontbrekende specifieke opties**

* **Oplossing**: Voeg douaneopties toe of verfijn uw herinnering
* **Voorbeeld**: &quot;omvat belangrijke landen plus [ uw specifieke landen ]&quot;

**Uitgave: Verouderde informatie**

* **Oplossing**: Verzoek huidige gegevens of specificeer datumwaaiers
* **Voorbeeld**: &quot;voeg huidige openbare feestdagen voor 2024 toe&quot;

### Optimalisatie van prestaties

* **de opties van de Grens**: De filters van het gebruik om het aantal geproduceerde opties te verminderen
* **Progressieve mededeling**: toon basisopties eerst, dan sta uitbreiding toe
* **Caching**: Overweeg caching vaak gebruikte slimme gebiedsgegevens

## Verwante artikelen

* [Aan de slag met Forms Experience Builder](forms-experience-builder-getting-started.md)
* [Formulier maken met AI](forms-experience-builder-prompt-examples-library.md)
* [Regels maken en bedrijfslogica](forms-experience-builder-prompt-examples-library.md#rule-creation--business-logic)
* [Formulierverzending en integratie](form-submission-integration.md)

