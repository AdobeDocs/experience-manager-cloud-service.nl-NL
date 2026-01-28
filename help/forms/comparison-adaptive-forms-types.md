---
title: Aangepaste Forms Core Components vs Edge Delivery Services Forms vs Foundation Components
description: Technische vergelijking van AEM Forms-ontwerpbenaderingen - Core Components, Edge Delivery Services Forms en Foundation Components. Architectuur, het teruggeven, eigenschappen, en gebruiksgevallen.
keywords: vergelijking van adaptieve formulieren, kerncomponenten, basiscomponenten, formulieren voor randlevering, vergelijking van AEM-formulieren, vergelijking van formulierbuilder
role: Architect, Developer, Admin
level: Intermediate
feature: Adaptive Forms, Core Components, Edge Delivery Services
exl-id: adaptive-forms-comparison
source-git-commit: 37799555babb15809409ec5cda8a1c46ceff24f2
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 0%

---


# Adaptieve Forms: Core Components vs Edge Delivery Services Forms vs Foundation Components

Adobe Experience Manager (AEM) Forms biedt drie verschillende benaderingen voor het maken van ervaringen met gegevensvastlegging: adaptieve Forms op basis van Core Components, Edge Delivery Services Forms en Adaptive Forms op basis van Foundation Components. Elke benadering heeft een andere architectuur, het teruggeven model, en het geval van het doelgebruik. Dit artikel verstrekt een technische vergelijking om oplossingsarchitecten, ontwikkelaars, en de klanten van AEM te helpen de aangewezen benadering voor hun vereisten selecteren.

## Overzicht

Alle drie formuliertypen dienen voor het vastleggen van gebruikersgegevens en het integreren met back-endsystemen. Ze verschillen echter in hun onderliggende architectuur, waar formulieren worden gegenereerd, hoe ze worden geleverd en welke mogelijkheden ze ondersteunen.

| Benadering | Status | Hoofd-/kleine letters |
|----------|--------|------------------|
| **Componenten van de Kern** | Aanbevolen voor nieuwe formulieren | Moderne, schaalbare formulieren die AEM-authoring vereisen met flexibele publicatieopties |
| **Edge Delivery Services Forms** | Aanbevolen voor prestatiekritieke sites | Krachtige formulieren die van de rand worden geleverd met snelle implementatie |
| **Componenten van de Stichting** | Onderhoudsmodus | Bestaande formulieren waarvoor ondersteuning voor oudere functies vereist is |

## Adaptieve Forms gebaseerd op kerncomponenten

### Definitie

Adaptieve Forms Core-componenten zijn een set van 30 opensource, BEM-compatibele componenten die zijn gebaseerd op de basis van Adobe Experience Manager WCM Core-componenten. Ze vertegenwoordigen de door Adobe aanbevolen aanpak voor het maken van een nieuwe Adaptieve Forms, die een moderne architectuur, verbeterde prestaties en automatische, zonder kop vorm biedt.

### Architectuur

De Componenten van de kern gebruiken een gestandaardiseerde, modulaire componentenarchitectuur:

- **Stichting van de Component**: Voortgebouwd op de Componenten van de Kern van AEM WCM
- **het Stijlen Methodologie**: BEM (de Modifier van het Element van het Blok) CSS overeenkomsten
- **Opslag van de Inhoud**: Opslag JCR met gestructureerde inhoudsknopen
- **teruggevend**: Server-kant teruggevend in AEM met facultatieve cliënt-zij hoofdloze teruggeven
- **Source**: Open-source (beschikbaar op [&#x200B; GitHub &#x200B;](https://github.com/adobe/aem-core-forms-components))

### Rendermodel

De Componenten van de kern steunen veelvoudige het teruggeven modellen:

1. **Server-zij het Teruggeven (SSR)**: Forms geeft op de server van AEM terug en levert volledige HTML aan browser
2. **Koploze Rendering**: Forms stelt vertegenwoordiging JSON via APIs voor cliënt-kant het teruggeven in React, Angular, of andere kaders bloot
3. **Hybride Rendering**: Combinatie van server en cliënt die voor optimale prestaties teruggeven

### Publicatieopties

- AEM-publicatie-instanties
- Edge Delivery Services (indien geconfigureerd)
- Koploze API&#39;s voor aangepaste frontendtoepassingen

### Belangrijkste kenmerken

| Categorie | Mogelijkheden |
|----------|-------------|
| **Onderdelen** | 30 gestandaardiseerde componenten, waaronder Tekstvak, Numeriek vak, Datumkiezer, Vervolgkeuzelijst, Selectievakjesgroep, Keuzerondje, Bestandsbijlage, Wizard, Accordeon, Horizontale/Verticale tabbladen |
| **Modellen van de Vorm** | JSON-schema (v4 en 2020-12), formuliergegevensmodel (FDM), XDP/XFA-sjablonen (beperkt) |
| **Motor van Regels** | Visuele regelredacteur met voorwaardelijke logica, bevestiging, de dienstaanroeping, douanefuncties |
| **legt Acties** voor | REST-eindpunt, e-mail, AEM Workflow, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion, Form Data Model |
| **pre-fill** | Prefill-service formuliergegevensmodel, aangepaste Prefill-services |
| **CAPTCHA** | reCAPTCHA, hCaptcha, Turnstile |
| **Document van Verslag** | PDF genereren met aangepaste of OTB-sjablonen |
| **Toegankelijkheid** | WCAG-compatibel, ARIA-labels, toetsenbordnavigatie, ondersteuning voor schermlezers |
| **Localization** | Ondersteuning voor meerdere talen via AEM-vertaalworkflow |
| **Versioning** | Inhoud versieren die is overgenomen van AEM Sites |

### Vereisten

- **AEM Forms as a Cloud Service**: De Componenten van de Kern die door gebrek worden toegelaten
- **AEM 6.5 Forms**: Vereist toelatend via AEM Archetype
- **Toestemmingen van de Gebruiker**: De gebruiker moet in `forms-users` groep zijn
- **Malplaatje**: Het adaptieve malplaatje van de Vorm (de Component van de Kern) wordt vereist
- **Thema**: het thema van het Canvas (OTB) of douanethema

### Beperkingen

- **Beperkingen van het Schema JSON**: Het type van Null, verenigingstypes (om het even welk), OneOf/AnyOf/AllOf/NOT constructies niet gesteund
- **de Kaarten van de Component**: Het Blok van het Onderteken van Adobe, Krabbelen Handtekening, Grafiek, de Keuze van het Beeld niet beschikbaar (beschikbaar in de Componenten van de Stichting)
- **Functies van de Douane**: De functies van de generator, async/wacht, klassenmethodes niet gesteund
- **Digitale Handtekeningen**: Niet beschikbaar binnen (in tegenstelling tot de Componenten van de Stichting)

### Wanneer gebruiken

**geadviseerd voor:**

- Nieuwe projecten voor formulierontwikkeling
- Organisaties die behoefte hebben aan moderne, onderhoudsbare architectuur
- Projecten waarvoor een flexibele publicatie vereist is (AEM + Edge Delivery + Headless)
- Aangepaste frontend-toepassingen (React, Angular) via headless API&#39;s
- Projecten die prioriteit geven aan prestaties en toegankelijkheid
- Vereisten voor Omnichannel-levering (web, mobiel, kiosken)

**niet geadviseerd voor:**

- Forms waarvoor integratie met Adobe Sign vereist is (gebruik Foundation Components)
- Eenvoudige formulieren waarbij Edge Delivery Services-prestaties essentieel zijn
- Bestaande op componenten gebaseerde vormen van de Stichting (handhaven in Stichting tenzij het migreren)

## Edge Delivery Services Forms

### Definitie

Edge Delivery Services (EDS) Forms is een samenstellbare reeks services voor het maken en leveren van formulieren via Adobe Experience Manager Edge Delivery Services. Ze maken een snelle ontwikkeling van formulieren met uitzonderlijke prestaties mogelijk via levering op afstand, weergave op de client en meerdere ontwerpmethoden.

### Architectuur

EDS Forms gebruikt een ontkoppelde, edge-first architectuur:

- **Inhoudsbronnen**: Microsoft SharePoint, Google Aandrijving (op document-Gebaseerd), of Universele Redacteur (WYSIWYG)
- **Bewaarplaats van de Code**: GitHub
- **Inhoudslevering**: Edge Delivery Services CDN
- **teruggevend**: Cliënt-kant teruggevend gebruikend vanilla JavaScript
- **Blok van de Vorm**: Het adaptieve Blok van Forms verwerkt vormdefinities en produceert HTML

### Rendermodel

EDS Forms gebruikt alleen renderen op de client:

1. Formulierdefinitie opgeslagen als JSON (geconverteerd vanuit spreadsheet of geschreven in Universal Editor)
2. JSON opgehaald van rand: `https://<branch>--<repo>--<owner>.aem.live/<form>.json`
3. Adaptive Forms Block JavaScript-processen JSON
4. HTML-structuur dynamisch gegenereerd in de browser
5. CSS toegepast op stijl

**het Patroon van de Structuur van HTML:**

```html
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required="{Required}">
   <label for="{FieldId}" class="field-label">Label</label>
   <input type="{Type}" id="{FieldId}" name="{Name}">
   <div class="field-description" id="{FieldId}-description">Help text</div>
</div>
```

### Ontwerpmethoden

EDS Forms ondersteunt twee ontwerpmethoden:

#### Universele editor (WYSIWYG)

- Visuele interface voor slepen en neerzetten
- Real-time voorvertoning met apparaatsimulatie
- Geavanceerde regeleditor voor voorwaardelijke logica
- Integratie van het formuliergegevensmodel (FDM)
- Integratie van AEM Workflows
- Ondersteuning voor aangepaste componenten
- Maken op basis van sjablonen

#### Authoring op basis van documenten

- Microsoft Excel of Google Sheets authoring
- Formulierdefinitie op basis van werkblad
- Meteen publiceren (wijzigingen worden direct doorgevoerd)
- Geschikt voor eenvoudige tot matige complexe formulieren

### Verzendopties

**de Verzenddienst van Forms (FSS):**

- Verzenden naar Google-bladen
- Verzenden naar Microsoft Excel (OneDrive/SharePoint)
- E-mailmeldingen

**AEM publiceert voorleggen Acties:**

- REST-eindpunt
- AEM-mailservices
- Formuliergegevensmodel
- AEM Workflow
- SharePoint/OneDrive
- Azure Blob Storage
- Microsoft Power Automate
- Adobe Workfront Fusion
- Adobe Marketo Engage

### Belangrijkste kenmerken

| Categorie | Mogelijkheden |
|----------|-------------|
| **Onderdelen** | Alle HTML5-invoertypen, Checkbox-groepen, Radiogroepen, Dropdown, Panels, Herhalbare secties, Bestandsbijlage, Accordeon, Wizard, Modal |
| **Bevestiging** | Validatie op veldniveau (vereist, min/max, patroon), aangepaste validatieberichten |
| **Regels** | Voorwaardelijke zichtbaarheid, waardeexpressies, gebeurtenisgestuurde regels |
| **Integraties** | Adobe-ondertekening, Salesforce, Microsoft Dynamics, A/B-tests |
| **Veiligheid** | reCAPTCHA Enterprise, hCaptcha, CORS-configuratie |
| **Analytics** | Adobe Experience Platform Web SDK, formulierweergaven en verzending bijhouden |

### Vereisten

**voor op document-Gebaseerde Authoring:**

- GitHub-account
- Google Drive- of Microsoft SharePoint-account
- Knooppunt/npm voor lokale ontwikkeling
- AEM-project met Adaptive Forms Block geconfigureerd
- Map delen met `forms@adobe.com` (bewerkingsmachtigingen)

**voor Universele Redacteur:**

- AEM Forms as a Cloud Service-exemplaar
- Edge Delivery Services-project geconfigureerd
- Vereiste machtigingen voor doeldoelen

**voor AEM publiceer voorlegging:**

- Instantie-URL van AEM Cloud Service geconfigureerd
- Configuratie OSGi-referentiefilter
- CORS-configuratie voor Edge Delivery-sitedomeinen

### Beperkingen

**op document-Gebaseerde Authoring:**

- Naamgeving van werkbladen beperkt tot `helix-default` en `shared-aem`
- Het meest geschikt voor formulieren met een lage complexiteit
- Beperkte regelmogelijkheden
- Geen AEM Workflows (zonder publicatie door AEM)
- Geen integratie van formuliergegevensmodellen

**Universele Redacteur:**

- Statische/dynamische import wordt niet ondersteund in aangepaste functies
- Formulierfragmenten kunnen alleen op zichzelf worden bewerkt
- Functionaliteit voor insluiten van formulieren in ontwikkeling

**Algemeen:**

- `shared-aem` bladen mogen geen PII bevatten (openbaar toegankelijk)
- Vereist de configuratie van CORS voor verzending tussen verschillende oorsprong
- OSGi Referrer-filter vereist voor publicatie door AEM

### Wanneer gebruiken

**geadviseerd voor:**

- Krachtige websites die hoge Lightroom-scores vereisen
- Sites worden al gebruikt met Edge Delivery Services
- Snelle ontwikkeling en implementatie van formulieren
- Gegevens van eenvoudige tot matige complexiteit vastleggen
- Teams die de voorkeur geven aan ontwerpbewerkingen op basis van werkbladen (op basis van document)
- Projecten die snelle tijd-aan-markt vereisen

**niet geadviseerd voor:**

- Forms vereist uitgebreide verwerking op de server
- Diepe integratie met oudere systemen zonder REST API&#39;s
- Offline formuliervereisten
- Organisaties die specifieke JavaScript-frameworks (React, Angular) met volledige controle nodig hebben

## Adaptieve Forms op basis van Foundation-componenten

### Definitie

De Componenten van de stichting vertegenwoordigen de klassieke het auteursbenadering van AEM Forms. Het zijn de oorspronkelijke adaptieve Forms-componenten die al vele jaren in AEM Forms beschikbaar zijn. Hoewel nog steeds ondersteund, raadt Adobe Foundation Components voornamelijk aan voor het onderhouden van bestaande formulieren in plaats van nieuwe te maken.

### Architectuur

Foundation Components gebruikt traditionele AEM-architectuur:

- **Model van de Inhoud**: `cq:Page` component WCM met JCR inhoudsstructuur
- **Hoofdstructuur**: `guideContainer` (wortel) → `rootPanel` → `items` (vormgebieden)
- **teruggevend**: Server-kant teruggevend met cliënt-kant JavaScript
- **Uitdrukkingen SOM**: Het Model van Objecten Scripting voor het van verwijzingen voorzien van vormvoorwerpen

### Rendermodel

De Componenten van de stichting gebruiken server-zijrendering:

1. Formulierinhoud opgeslagen in de JCR-opslagplaats
2. AEM-server verwerkt formulierstructuur
3. HTML volledig gerenderd en verzonden naar browser
4. JavaScript aan de clientzijde verwerkt interactiviteit en validatie

### Belangrijkste kenmerken

| Categorie | Mogelijkheden |
|----------|-------------|
| **Onderdelen** | 40+ componenten inclusief alle Core Component equivalents plus: Adobe Sign Block, Chart, Scribble Signature, Image Choice, Summary Step, File Attachment Listing |
| **Modellen van de Vorm** | Formuliergegevensmodel (FDM), XDP/XFA-sjablonen, XML-schema (XSD), JSON-schema |
| **Motor van Regels** | Visuele redacteur + coderedacteur (voor vorm-macht-gebruikers groep) |
| **Digitale Handtekeningen** | Integratie met Adobe-handtekening, scripthandtekening |
| **legt Acties** voor | Meerdere OTB-acties vergelijkbaar met Core Components |

### Componenten die exclusief zijn voor Stichting

De volgende componenten zijn **slechts beschikbaar** in de Componenten van de Stichting:

- Adobe Sign Block
- Diagram
- Lijst met bestandsbijlagen
- Plaatsaanduiding voetnoot
- Afbeeldingskeuze
- Krabbelhandtekening
- Samenvattingsstap
- Turnstile Captcha

### Vereisten

- AEM Forms as a Cloud Service of AEM 6.5 Forms
- Adaptief formuliersjabloon (Foundation)
- Gebruiker in groep `forms-users`

### Beperkingen

- **het Publiceren**: AEM-slechts (geen Edge Delivery Services of Headless APIs)
- **Prestaties**: Standaardprestaties (niet geoptimaliseerd voor de scores van Lighthouse)
- **Architectuur**: Verouderde architectuur zonder naleving BEM
- **Open Source**: Niet open-source
- **Toekomstige Ontwikkeling**: De wijze van het onderhoud; nieuwe eigenschappen die hoofdzakelijk aan de Componenten van de Kern worden toegevoegd

### Wanneer gebruiken

**geadviseerd voor:**

- Bestaande op stichting gebaseerde formulieren onderhouden
- Forms vereist integratie met Adobe Sign of Scribble Signature
- Werkstromen die afhankelijk zijn van gevestigde elementfuncties
- Projecten met alleen AEM-publicatievereisten
- Forms die Foundation-exclusieve componenten vereist (Grafiek, Keuze van Beeld)

**niet geadviseerd voor:**

- Nieuwe formulierontwikkeling (gebruik kerncomponenten)
- Projecten waarvoor Edge Delivery Services-publicatie vereist is
- Formulier-API&#39;s zonder koppen
- Prestatie-kritieke implementaties
- Projecten die prioriteit geven aan toekomstbestendige architectuur

## Vergelijkingstabel

| Parameter | Kernonderdelen | Edge Delivery Services Forms | Elementaire componenten |
|-----------|-----------------|-----------------------------|-----------------------|
| **Status** | Aanbevolen voor nieuwe formulieren | Aanbevolen voor sites met hoge prestaties | Onderhoudsmodus |
| **Architectuur** | Modulair, BEM-compatibel | Edge-first, ontkoppeld | Traditionele WCM |
| **teruggevend** | Server-kant + headless | Alleen client | Server-kant |
| **het Publiceren** | AEM + Edge Delivery + headless API&#39;s | Alleen Edge Delivery Services | Alleen AEM |
| **Authoring** | AEM Forms Editor | Universele editor of spreadsheets | AEM Forms Editor |
| **Prestaties** | Goed (verbeterd ten opzichte van de Stichting) | Uitstekend (hoge Lighthouse-scores) | Standaard |
| **Aantal van de Component** | 30 | 20+ (alle HTML5-invoertypen) | 40+ |
| **Open Source** | Ja (GitHub) | Ja | Nee |
| **Model van de Gegevens van de Vorm** | ✅ | ✅ (Alleen Universal Editor) | ✅ |
| **JSON Schema** | ✅ | Beperkt | ✅ |
| **XDP/XFA Steun** | Beperkt | ❌ | ✅ |
| **Schema van XML** | ❌ | ❌ | ✅ |
| **Motor van Regels** | Geavanceerde visuele editor | Geavanceerd (Universal Editor) / Beperkt (op basis van document) | Geavanceerd visueel + code-editor |
| **Digitale Handtekeningen** | ❌ | ❌ | ✅ |
| **Teken van Adobe** | ❌ | Via integratie | ✅ (native blok) |
| **Document van Verslag** | ✅ | ✅ | ✅ |
| **opties CAPTCHA** | reCAPTCHA, hCaptcha | reCAPTCHA Enterprise, hCaptcha | reCAPTCHA, hCaptcha, Turnstile |
| **Werkschema van AEM** | ✅ | ✅ (via AEM Publish) | ✅ |
| **Headless APIs** | ✅ (automatisch) | ❌ | ❌ |
| **Toegankelijkheid** | WCAG-compatibel | WCAG-compatibel | Basis |
| **Snelheid van de Plaatsing** | Op pijplijn gebaseerd | Instant (toewijzen aan live) | Op pijplijn gebaseerd |
| **het Stijlen** | BEM CSS, thema&#39;s | CSS, thema&#39;s op projectniveau | CSS, thema&#39;s |
| **Versioning** | ✅ (overgeërfd van sites) | Op basis van git | ✅ |
| **Localization** | AEM-vertaalworkflow | Handmatig / AEM Sites-workflow | AEM-vertaalworkflow |

## Beslissingsmatrix

| Vereiste | Aanbevolen aanpak |
|-------------|---------------------|
| Nieuwe formulierontwikkeling | Kernonderdelen |
| Bestaande formulieren onderhouden | Elementaire componenten (tot migratie) |
| Krachtig (hoge Lighthouse-scores) | Edge Delivery Services Forms |
| Levering zonder kop/omnichannel | Kernonderdelen |
| Adobe-integratie voor ondertekenen | Elementaire componenten |
| Authoring op basis van werkbladen | Edge Delivery Services (op document gebaseerd) |
| Visual WYSIWYG authoring met randlevering | Edge Delivery Services (Universal Editor) |
| Complexe bedrijfsintegraties | Core Components or Foundation Components |
| Snel prototypen maken | Edge Delivery Services (op document gebaseerd) |
| XFA/XDP sjabloonondersteuning | Elementaire componenten |
| Aangepaste reactie/voorzijde Angular | Core Components (Headless API&#39;s) |

## Overwegingen bij migratie

### Elementaire componenten omzetten naar kerncomponenten

- **Hulpmiddel**: Moderniseer Hulpmiddelen van AEM (het Nut van de Omzetting van Forms)
- **inspanning**: Matig tot hoog afhankelijk van vormingewikkeldheid
- **Overwegingen**:
   - Regels vereisen handmatige recreatie
   - Elementaire exclusieve componenten (Adobe Sign Block, Scribble Signature, Chart) worden tijdens de migratie verwijderd
   - Vertaalinstellingen niet overgedragen
   - Aangepaste functies moeten worden herschreven

### Traditioneel in Edge Delivery Services

- **Benadering**: Bouw vormen opnieuw gebruikend Universele Redacteur of op document-Gebaseerd creatie
- **inspanning**: Hoog voor complexe vormen, laag voor eenvoudige vormen
- **Voordelen**: De significante prestatiesverbetering, moderne ontwikkelervaring

## Documentatiekaarten en dubbelzinnigheden

De volgende gebieden hebben onvolledige of dubbelzinnige documentatie:

1. **Componenten XDP/XFA van de Kern van Componenten XDP/XFA Steun**: De documentatie wijst op &quot;beperkte&quot;steun maar specificeert geen nauwkeurige beperkingen
2. **Vorm Embedding van Edge Delivery Services**: Gemarkeerd als &quot;Binnenkort&quot;in documentatie; huidige status onduidelijk
3. **de Componenten van de Stichting Toekomstige**: Geen expliciete verfchronologie; beschreven als &quot;onderhoudswijze&quot;
4. **Koploze API Coverage**: Exacte eigenschappariteit tussen server-teruggegeven en zonder kop vormen niet gedocumenteerd
5. **Benchmarks van Prestaties**: De specifieke de scorevergelijkingen van Lighthouse tussen benaderingen niet verstrekte

## Gerelateerde bronnen

- [Een adaptief formulier maken (kerncomponenten)](/help/forms/creating-adaptive-form-core-components.md)
- [Een adaptief formulier maken (basiscomponenten)](/help/forms/creating-adaptive-form.md)
- [Edge Delivery Services Forms - Overzicht](/help/edge/docs/forms/overview.md)
- [Aan de slag met de universele editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
- [Zelfstudie over ontwerpen op basis van documenten](/help/edge/docs/forms/tutorial.md)
- [Hulpprogramma voor migratie](/help/forms/migration-utility-tool-for-af-core-components.md)
- [&#x200B; de Componenten van de Kern van AEM Forms op GitHub &#x200B;](https://github.com/adobe/aem-core-forms-components)
