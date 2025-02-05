---
title: Maak uw eerste interactieve communicatie
description: Ontwerp dynamische, gegevensgestuurde communicatie met eenvoudige interactieve AEM Forms-communicatie
feature: Release Information
role: Admin
hide: true
hidefromtoc: true
source-git-commit: a771aa7e683cfbcacc8a9d5765c63d50169a2756
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---


# Maak uw eerste interactieve communicatie


>[!VIDEO](https://video.tv.adobe.com/v/3444094/)

## Stap 1: Plan de interactieve communicatie

De eerste stap in het plannen van een Interactieve Mededeling is de inhoud van de Interactieve Mededeling te voltooien. Nadat de inhoud wordt voltooid, moet u het analyseren om de diverse activatypes te identificeren die worden vereist om de Interactieve Mededeling tot stand te brengen.

### Planning

Een interactieve communicatie omvat de volgende elementen:

* **Statische tekst** omvat meestal de delen van de interactieve mededeling die algemeen in aard zijn en in mededeling aan alle klanten inbegrepen zijn. Bijvoorbeeld kop-, voettekst-, aanhef- of disclaimers.

* **gegevens die van een achterste deelsysteem (model van vormgegevens)** worden gesourced is klant-specifiek en dynamisch met de interactieve mededeling samengevoegd. Het beleidsnummer of adres kan bijvoorbeeld worden opgehaald met het formuliergegevensmodel.

* **Lay-out of malplaatjes** voor de versie van de Druk en van het Web van de Interactieve Mededeling.

* **Orde** waarin de diverse tekstparagrafen in de Interactieve Mededeling verschijnen.

* **Voorwaardelijke gegevens** die bevolkt worden gebaseerd op vooraf bepaalde voorwaarden. Bijvoorbeeld de datum waarop de interactieve communicatie wordt gegenereerd.

* **Beelden die in een bewaarplaats** worden opgeslagen, zoals logo&#39;s en handtekeningsbeelden. Afbeeldingen zoals bedrijfslogo&#39;s worden in de meeste of alle interactieve communicatie weergegeven.

* **Grafieken en lijsten** die worden vereist om de vertegenwoordiging van complexe gegevens in een Interactieve Mededeling te vereenvoudigen

### Anatomie van de interactieve communicatie

Zodra u de inhoud en de elementen hebt voltooid die worden gebruikt om uw Interactieve Mededeling tot stand te brengen, kunt u een anatomie van de Interactieve Communicatie tot stand brengen. De anatomie moet de details hebben die in de sectie van de Overwegingen van de Planning worden vermeld. Bijvoorbeeld, een anatomie van de maandelijkse rekening die een telecomexploitant aan zijn klanten verzendt.

De anatomie bevat gegevens met de volgende invoermodi:

* Statische tekst
* Formuliergegevensmodel
* Voorwaardelijke gegevens
* Afbeeldingen


## Stap 2: Een formuliergegevensmodel maken

Met een formuliergegevensmodel kunt u een interactieve communicatie verbinden met verschillende gegevensbronnen. Bijvoorbeeld AEM gebruikersprofiel, RESTful-webservices, SOAP-gebaseerde webservices, OData-services en relationele databases. Een model van vormgegevens is een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten beschikbaar in verbonden gegevensbronnen. U kunt het model van formuliergegevens met een interactieve communicatie gebruiken om gegevens op te halen uit verbonden gegevensbronnen. Voor meer informatie over het model van vormgegevens, zie [ de Integratie van Gegevens van AEM Forms ](/help/forms/data-integration.md).

## Stap 3: fragmenten maken

Documentfragmenten zijn herbruikbare componenten van een correspondentie die worden gebruikt om een interactieve communicatie samen te stellen. De documentfragmenten zijn van het type Tekst, Lijst en Voorwaarde.


## Stap 4: Sjablonen maken

De interactieve Communicatie redacteur verstrekt veelvoudige malplaatjes OOTB. U kunt deze sjablonen naar wens van uw organisatie wijzigen of een geheel nieuwe sjabloon maken.


## Stap 5: Maak een interactieve communicatie

Zodra u alle bouwstenen zoals het model van vormgegevens, documentfragmenten, en malplaatjes voor de Webversie creeert, kunt u beginnen tot een Interactieve Mededeling te leiden. Een interactieve communicatie beginnen maken:

1. Meld u aan bij uw as a Cloud Service AEM Forms-omgeving.
1. Ga naar Forms > Forms &amp; Documents
1. Klik **creëren** en selecteren **Communicatie Document**. Er wordt een configuratiescherm weergegeven waarin u de volgende opties kunt instellen:

   | Veld | Beschrijving | Verplicht |
   |-------|-------------|----------|
   | Naam | Unieke identificatiecode voor de communicatie | Ja |
   | Titel | Naam van uw communicatie weergeven | Ja |
   | Beschrijving | Korte beschrijving van het doel van de communicatie | Nee |
   | Sjabloon | Een vooraf geconfigureerde sjabloon selecteren of helemaal opnieuw beginnen | Ja |
   | Tags | Metagegevenstags toevoegen voor een betere organisatie | Nee |

1. Ga naar het tabblad Voorinstellingen en configureer de volgende opties:

   | Veld | Beschrijving |
   |-------|-------------|
   | Lijst met voorinstellingen | Selecteer een vooraf geconfigureerde voorinstelling voor de documentgrootte. Veelvoorkomende opties zijn A4, Letter en meer. |
   | Vooraf ingestelde breedte | Hiermee geeft u de vooraf ingestelde breedte voor de geselecteerde lijst met voorinstellingen weer. |
   | Hoogte voorinstelling | Hiermee geeft u de vooraf ingestelde hoogte voor de geselecteerde lijst met voorinstellingen weer. |
   | Eenheid voorinstelling | Selecteer de maateenheid voor de afmetingen van het document (bijvoorbeeld Millimeters, Inches). |
   | Afdrukstand voorinstelling | Kies de richting van het document: Staand of Liggend. |

1. Klik **creëren**. De mededeling opent in de redacteur.
1. Sleep componenten en fragmenten om de interactieve communicatie te ontwerpen.

   * Het gebruik **HoofdPagina** voor de inhoud gemeenschappelijk over pagina&#39;s. Stramienpagina&#39;s zijn bedoeld voor het opmaken van pagina&#39;s en helpen de consistentie van het ontwerp te verbeteren, omdat ze een achtergrond en indeling kunnen bieden voor meer dan één pagina in een documentontwerp.

   * Gebruik **Pagina&#39;s** aan lay-out inhoud en lay-out van uw document. Elke pagina leidt zijn grootte en richtlijn van een hoofdpagina af en, door gebrek, wordt elke pagina geassocieerd met de standaardhoofdpagina die Designer creeert.


1. Gebruik de notatie `@` om gegevensvelden automatisch aan te vullen op basis van het aangesloten gegevensmodel.
1. Gebruik de optie `PDF Preview` om een voorvertoning van het document weer te geven, samen met gegevens. U hebt het gegevensbestand in JSON-indeling nodig.
