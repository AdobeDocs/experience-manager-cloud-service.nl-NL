---
title: 'Formulierontwikkelaar: kies uw aanpak'
description: Vergelijk formulierbuilders en zoek de juiste aanpak voor het maken van adaptieve formulieren. Of u nu sjablonen of complexe formulieren nodig hebt voor de maker van formulieren, kies de beste formulierbuilder voor uw behoeften.
keywords: formulierontwerper, AEM-formulieren, maker van formulieren, formulieren maken, formuliermaker, adaptieve formulieren, kerncomponenten, basiscomponenten, services voor randlevering, formulieren maken
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer, Admin
level: Beginner
exl-id: choose-form-builder-guide
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---


# Formulierontwikkelaar: kies uw aanpak {#choose-your-form-builder}

Adobe Experience Manager (AEM) Forms biedt drie krachtige methoden voor het maken van formulieren, elk ontworpen voor verschillende gebruiksgevallen, technische vereisten en publicatiebestemmingen. Of u nu sjablonen zoekt of een ontwikkelaar die complexe formulieren samenstelt, deze handleiding helpt u de juiste formulierontwikkelaar voor uw project te kiezen.

## Handleiding voor snelle besluitvorming

Gebruik deze korte naslaggids om aan te geven wat de beste formulierbuilder voor uw behoeften is:

| **als u nodig hebt...** | **kiezen** |
|-------------------|------------|
| **Moderne, scalable vormen met recentste eigenschappen** | Kernonderdelen |
| **bliksemsnelle vormen voor hoog-verkeerswebsites** | Universele editor |
| **handhaaf bestaande vormen of erfenisintegraties** | Elementaire componenten |
| **Visuele belemmering-en-dalingsauthoring** | Core Components or Universal Editor |
| **Spreadsheet-Gebaseerde vormverwezenlijking** | Authoring op basis van documenten |
| **Omnichannel levering (Web, mobiel, kiosken)** | Core Components (met headless API&#39;s) |
| **Eigen frontend toepassingen (Reageren, Angular)** | Core Components (met headless API&#39;s) |
| **Volledige controle over vorm teruggevend** | Core Components (met headless API&#39;s) |

## Opties voor het samenstellen van formulieren

AEM Forms biedt drie hoofdbenaderingen voor het maken van formulieren, elk ontworpen voor verschillende typen ontwerpers van formulieren en gebruiksgevallen. Of u nu een eenvoudige formuliermaker nodig hebt voor snelle taken of geavanceerde mogelijkheden voor het maken van formulieren voor complexe projecten, er is een aanpak die aan uw behoeften voldoet:

### De componentenbouwer van de Stichting

Elementaire componenten vertegenwoordigen de klassieke AEM Forms-ontwerpervaring. Hoewel ze nog steeds worden ondersteund, wordt het vooral aanbevolen bestaande formulieren te onderhouden in plaats van nieuwe formulieren te maken.

**Zeer belangrijke kenmerken:**

- Traditionele AEM-ontwerpinterface
- Bewezen stabiliteit voor bestaande workflows
- Beperkt tot alleen AEM-publicaties
- Basiscomponentbibliotheek

### Samensteller van kerncomponentformulieren

Core Components bieden de nieuwste AEM Forms-mogelijkheden met verbeterde prestaties, toegankelijkheid en flexibiliteit. Deze formulierontwerper is ideaal voor ontwerpers van formulieren die professionele resultaten met moderne functies nodig hebben. Deze functie ondersteunt het publiceren van zowel AEM als Edge Delivery Services en produceert automatisch headless formulieren voor API-gestuurde levering op meerdere platforms.

**Zeer belangrijke kenmerken:**

- Moderne, gestandaardiseerde onderdelen
- Verbeterde prestaties en toegankelijkheid
- Flexibele publicatieopties (AEM + Edge Delivery)
- Geavanceerde aanpassingsmogelijkheden
- Toekomstbestendige architectuur
- Automatisch zonder kop genereren voor levering in omnichannel

### Universele editor (Edge Delivery Services)

De Universal Editor biedt twee krachtige ontwerpbenaderingen voor Edge Delivery Services: visuele authoring in WYSIWYG en op documenten gebaseerde authoring met behulp van spreadsheets. Deze methode van het maken van formulieren is ideaal voor gebruikers die snel formulieren met uitzonderlijke prestaties willen maken.

**Zeer belangrijke kenmerken:**

- Uitzonderlijke prestaties (hoge Lighthouse-scores)
- Twee ontwerpmethoden: WYSIWYG en op documenten gebaseerd
- Geoptimaliseerd voor Edge Delivery Services
- Uitzonderlijke prestaties en SEO
- Snelle ontwikkeling en implementatie


## Gedetailleerde vergelijking

### Technische mogelijkheden

| **Capability** | **Stichting** | **Kern** | **Universele Redacteur** | **op document-Gebaseerd** |
|----------------|----------------|----------|---------------------|-------------------|
| **De ingewikkeldheid van de Vorm** | Basis | Geavanceerd | Geavanceerd | Eenvoudig tot matig |
| **motor van Regels** | Geavanceerd | Geavanceerd | Geavanceerd | Beperkt |
| **de componenten van de Douane** | ✅ | ✅ | ✅ | ✅ |
| **Thema&#39;s** | ✅ | ✅ | Projectniveau | Projectniveau |
| **Malplaatjes** | ✅ | ✅ | Alleen initiële inhoud |  |
| **Fragments** | ✅ | ✅ | ✅ | ✅ |
| **Localization** | ✅ | ✅ | Via AEM Sites | Handmatig/functies |

### Integratie en indiening

| **Eigenschap** | **Stichting** | **Kern** | **Universele Redacteur** | **op document-Gebaseerd** |
|-------------|----------------|----------|---------------------|-------------------|
| **modellen van Gegevens** | FDM, aangepast | FDM, aangepast | FDM, aangepast | Aangepast |
| **voorlegt acties** | Meerdere opties | Meerdere opties | Meerdere opties | Alleen werkblad |
| **pre-fill** | ✅ | ✅ | Via Wizard | ✅ |
| **CAPTCHA** | Meerdere typen | reCAPTCHA, hCaptcha | reCAPTCHA Enterprise | reCAPTCHA Enterprise |
| **Bijlagen** | ✅ | ✅ | ✅ | Vroegtijdige toegang |
| **Digitale handtekeningen** | ✅ |  |  |  |

### Publiceren en prestaties

| **Verhouding** | **Stichting** | **Kern** | **Universele Redacteur** | **op document-Gebaseerd** |
|------------|----------------|----------|---------------------|-------------------|
| **het Publiceren** | Alleen AEM | AEM + Edge Delivery + headless API&#39;s | Edge Delivery | Edge Delivery |
| **Prestaties** | Standaard | Verbeterd | Hoge Lighthoudesscores | Hoge Lighthoudesscores |
| **optimalisering SEO** | Basis | Goed | Uitstekend | Uitstekend |
| **Mobiele ontvankelijkheid** | Goed | Uitstekend | Uitstekend | Uitstekend |

## De juiste builder kiezen

### Kies de basiscomponenten als:

- U handhaaft bestaande op stichting-Gebaseerde vormen
- Integratie van digitale handtekeningen
- Uw werkschema hangt van gevestigde eigenschappen van de Stichting af
- U werkt met alleen AEM-publicatie-vereisten

**Ideaal voor:** het onderhoud van de vorm, de integratie van het erfenissysteem, gevestigde werkschema&#39;s

### Kies kerncomponenten als:

- Je bouwt nieuwe, moderne vormen
- U hebt flexibiliteit nodig om te publiceren op AEM of Edge Delivery Services
- U wilt de nieuwste functies
- U hebt geavanceerde aanpassingen en thema&#39;s nodig
- Toegankelijkheid en prestaties zijn prioriteiten
- U wilt toekomstbestendige technologie

**Ideaal voor:** Nieuwe projecten, scalable oplossingen, moderne Webervaringen

### Kies een universele editor als:

- U hebt uitzonderlijke prestaties en SEO nodig
- U bouwt voor Edge Delivery Services-sites
- U hebt complexe formulieren met aangepaste handelingen nodig
- Integratie met externe systemen is vereist

**Ideaal voor:** Krachtige plaatsen, Edge Delivery Services, visuele auteurswerkschema&#39;s

### Kies op documenten gebaseerde ontwerpen als:

- Zakelijke gebruikers geven de voorkeur aan ontwerpen op basis van werkbladen
- U hebt snelle prototypen en implementatie nodig
- Forms is relatief eenvoudig (enquêtes, registraties, feedback)
- Gegevensverzameling in spreadsheets voldoet aan uw behoeften
- Geen geavanceerde verzendworkflows vereist

**Ideaal voor:** Snelle plaatsing, bedrijfsgebruiker creatie, eenvoudige gegevensinzameling


## Migratieoverwegingen

### Van stichting tot kerncomponenten

- **Geadviseerde benadering:** gebruik het [ hulpmiddel van het migratienut ](/help/forms/migration-utility-tool-for-af-core-components.md)
- **Voordelen:** Moderne eigenschappen, betere prestaties, dubbel het publiceren vermogen
- **inspanning:** Gematigd aan hoog, afhankelijk van vormingewikkeldheid

### Van traditionele naar universele editor

- **Benadering:** herbouwt vormen gebruikend WYSIWYG of op document-Gebaseerde authoring in Universele Redacteur
- **Voordelen:** Uitzonderlijke prestaties, moderne ontwikkelervaring, de hoge scores van SEO
- **inspanning:** Hoog voor complexe vormen, laag voor eenvoudige vormen

## Aan de slag

Nadat u de formulierbuilder hebt gekozen:

### Elementen van de Stichting

1. [Een adaptief formulier maken (basiscomponenten)](/help/forms/creating-adaptive-form.md)
2. [Ontwerphandleiding voor basis-componenten](/help/forms/introduction-forms-authoring.md)

### Basiscomponenten

1. [Een adaptief formulier maken (kerncomponenten)](/help/forms/creating-adaptive-form-core-components.md)
2. [Overzicht van de functie Core Components](/help/forms/adaptive-form-core-components-json-schema-form-model.md)

### Universele editor (Edge Delivery Services)

1. **WYSIWYG Authoring:** [ Begonnen worden met Universele Redacteur ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
2. **op document-Gebaseerde Authoring:** [ bouwt uw eerste vorm met spreadsheets ](/help/edge/docs/forms/tutorial.md)


## Hebt u hulp nodig om te beslissen?

Nog steeds onzeker welke formulierontwerper moet worden gekozen? Houd rekening met de volgende factoren:

- **deskundigheid van het Team:** wat is het technische vaardigheidsniveau van uw team?
- **chronologie van het Project:** Hoe snel moet u opstellen?
- **de vereisten van Prestaties:** zijn snelheid en SEO kritiek?
- **Toekomstige scalability:** zult u vormen vaak moeten uitbreiden of wijzigen?
- **het Publiceren bestemming:** Waar zullen uw vormen worden gepubliceerd?

Neem contact op met uw AEM Forms-implementatieteam of Adobe-ondersteuning voor gepersonaliseerde hulp.

## Verwante artikelen

- [Gedetailleerde vergelijking van formulierontwerpen](/help/edge/docs/forms/authoring-a-form.md)
- [ overzicht van de Componenten van de Kern van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL)
- [Overzicht Edge Delivery Services for Forms](/help/edge/docs/forms/overview.md)
- [ Zwaarloze Adaptieve Forms met de Componenten van de Kern ](https://experienceleague.adobe.com/nl/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service)
