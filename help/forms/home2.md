---
title: Inleiding tot AEM Forms as a Cloud Service
description: Ontdek AEM Forms-mogelijkheden voor het maken van adaptieve formulieren, het automatiseren van workflows en het beheren van digitale documenten. Complete platform voor formuliergestuurde bedrijfsprocessen.
landing-page-description: Begrijp hoe u AEM Forms as a Cloud Service kunt gebruiken voor het maken van adaptieve formulieren, het verwerken van documenten en het automatiseren van bedrijfsworkflows.
keywords: AEM Forms, adaptieve formulieren, formulierbuilder, digitale formulieren, workflowautomatisering, documentservices, formuliergegevensmodel
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
index: false
exl-id: 50d7ce19-7d76-4ea1-a54c-8ca0e5379982
source-git-commit: eca09e1bf2ba4466f54e915e01218cc89cf5b116
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---

# Inleiding tot AEM Forms as a Cloud Service {#introduction}



Adobe Experience Manager Forms as a Cloud Service biedt een uitgebreid platform voor het maken, beheren en optimaliseren van ervaringen met digitale formulieren. Organisaties gebruiken AEM Forms om processen op basis van papier te digitaliseren, responsieve webformulieren te maken, documentworkflows te automatiseren en gepersonaliseerde communicatie op schaal te leveren.

Het platform combineert mogelijkheden voor het schrijven van formulieren met robuuste back-endservices, waarmee u alles kunt bouwen, van eenvoudige contactformulieren tot complexe, uit meerdere stappen bestaande bedrijfstoepassingen. Met cloudeigen architectuur krijgt u automatische updates, elastische schaling en beveiliging op bedrijfsniveau zonder infrastructuur te beheren.

Deze handleiding introduceert de kernmogelijkheden die rond de volledige levenscyclus van het formulier worden georganiseerd, van eerste ontwerp tot continue optimalisatie.

## Nieuwe functies in AEM Forms {#whats-new}

**Latest de Hoogtepunten van de Versie:**

- **Component van de Input van de Datum &amp; van de Tijd** - Verbeterde gebruikersinput met kalender en klokinterface voor nauwkeurige datum en tijdselectie
- **Verbeterde Veiligheid van het Upload van het Dossier** - Automatische bevestiging en inhoudstype controlerend om niet gestaafde dossierformaten te verhinderen
- **Verbeterde Behandeling van de Fout** - beter het zuiveren met specifieke foutencodes voor douane voorlegt acties
- **Document van de Verbeteringen van het Verslag** - Optie om verborgen gebieden voor schonere documentgeneratie uit te sluiten

**pre-Release Eigenschappen:**

- **de Steun van het Formaat van AFP** - Onderneming-rang drukmogelijkheden met Communicatie APIs
- **de Verbeteringen van de Redacteur van 0&rbrace; - de Moderne steun van JavaScript, dynamische variabelen, en context-bewuste paneelregels**
- **Verbeterde Methoden van de Bevestiging** - Comité, gebied, en vorm-vlakke bevestiging met betere flexibiliteit

[Volledige releaseopmerkingen weergeven →](/help/release-notes/release-notes-cloud/release-notes-current.md#forms)

## Programma voor vroege toegang {#early-access}

Profiteer van exclusieve toegang tot geavanceerde AEM Forms-innovaties voordat deze algemeen beschikbaar zijn.

**Huidige Vroege Eigenschappen van de Toegang:**

- **de Medewerker van AEM Forms AI** - Generatieve AI voor geautomatiseerde vormverwezenlijking, paneelgeneratie, en optimaliseringsaanbevelingen
- **Krabbelen Component van de Handtekening** - de directe handtekening vangt binnen vormen gebruikend muis, stift, of touchscreen
- **Directe API Integratie** - verbind met APIs in de Redacteur van de Regel zonder de modelopstelling van de Gegevens van het Vorm te vereisen
- **de Optimalisering van Forms van 0&rbrace; &lbrace;- AI-Verhoging van de prestatiesanalyse en van de omzettingssnelheid**

**sluit zich aan bij het Programma:**
Wees een van de eersten om toegang te krijgen tot innovaties en de toekomst van AEM Forms te helpen vormgeven.

[ Toegang van het verzoek →](mailto:aem-forms-ea@adobe.com) | [ Leer meer → ](/help/forms/early-access-ea-features.md)


## Kernmogelijkheden {#core-capabilities}

AEM Forms ondersteunt de volledige digitale reis van formulieren, van de eerste creatie tot continue optimalisatie. Elke fase bouwt op het vorige voort, creërend een uitvoerig platform voor vorm-gedreven bedrijfsprocessen.

**de Weg van het Werkschema van AEM Forms:**

     CREATE → GOVERN → PUBLISH → CAPTURE → PROCESS → INTEGRATE → TRACK → ARCHIVE → IMPROVE
    ↓        ↓        ↓         ↓         ↓         ↓          ↓       ↓        ↓ 
     Ontwerp   Controleren   Implementeren   Verzamelen   Handgreep   Verbinden   Monitorwinkel   Optimaliseren 
     een druk op een knop                                                                              ↓
     ← ← ← ← woord ← woord- ←- verbetering van de verbetering van de verbetering van de toestand ← de verbetering van de verbetering van de toestand- en de toestand van de vlakke en de vlakke documen de vlakke documentobjectsdocumentobjecten documen documentobjecten , documentobjecten , documen , herstel :

### Maken: formulierontwerp en -ontwikkeling {#create}

Aangepaste formulieren maken met behulp van verschillende ontwerpbenaderingen die zijn afgestemd op verschillende behoeften en technische vereisten.

**Visual Form Builder**
Ontwerp ontvankelijke vormen door belemmering-en-dalingsinterfaces gebruikend [ Componenten van de Kern ](/help/forms/creating-adaptive-form-core-components.md), [ Componenten van de Stichting ](/help/forms/creating-adaptive-form.md), of [ Edge Delivery Services ](/help/edge/docs/forms/overview.md). De visuele redacteur verstrekt directe terugkoppelen terwijl het handhaven van schone, semantische prijsverhoging die over apparaten en hulptechnologieën werkt.

**op document-Gebaseerde Authoring**
Creeer vormen gebruikend vertrouwde hulpmiddelen zoals Microsoft Excel door [ Edge Delivery Services ](/help/edge/docs/forms/overview.md). Met deze aanpak kunnen auteurs van inhoud krachtige formulieren maken zonder technische expertise en tegelijkertijd uitzonderlijke Google Lighthouse-scores behalen.

**Malplaatjes en Thema&#39;s**
Versnel vormverwezenlijking gebruikend pre-gebouwde [ malplaatjes ](/help/forms/template-editor-core-components.md) die structuur en aanvankelijke inhoud bepalen. Pas verenigbare branding met [ thema&#39;s ](/help/forms/using-themes-in-core-components.md) toe die visuele het stileren over veelvoudige vormen controleren, ontwerpconsistentie verzekeren en ontwikkelingstijd verminderen.

**Integraties van Gegevens**
Sluit formulieren tijdens de ontwerpfase aan op back-endsystemen. Het [ Model van de Gegevens van de Vorm ](/help/forms/create-form-data-models.md) verstrekt een verenigde interface aan veelvoudige gegevensbronnen, toelatend [ pre-populatie ](/help/forms/prepopulate-adaptive-form-fields.md), [ bevestigingsregels ](/help/forms/rule-editor-core-components.md), en naadloze gegevensstroom tussen vormen en bedrijfssystemen.

**Bevestigingen en Voorwaardelijke Logica**
Voer [ voorwaardelijke logica ](/help/forms/rule-editor-core-components.md), progressieve onthulling, en adaptieve bevestiging uit om gebruikers door complexe processen te begeleiden. [ sparen en hervat functionaliteit ](/help/forms/save-core-component-based-form-as-draft.md) staat gebruikers toe om vormen over veelvoudige zittingen te voltooien.

**HTML5 Forms**
Render op XFA-Gebaseerde vormen als [ HTML5 vormen ](/help/forms/introductionhtml5.md) voor mobiele apparaten en erfenisbrowsers. HTML5 Forms biedt native mobiele ervaring zonder plug-ins, terwijl de formulierlogica en validatie van oorspronkelijke XDP-sjablonen behouden blijven.

**Interactieve Mededelingen**
U kunt documentafhankelijke communicatie maken met een visuele editor, zoals instructies, facturen en berichten. [ Interactieve Mededelingen ](/help/forms/interactive-communication/create-interactive-communication.md) combineren statische inhoud met dynamische gegevens om gepersonaliseerde mededelingen over druk en digitale kanalen te produceren.

### Besturen: controleren en naleven {#govern}

Toezichts- en goedkeuringsprocedures instellen om ervoor te zorgen dat formulieren voldoen aan organisatorische normen en regelgevingsvereisten.

**op werkschema-Gebaseerde Goedkeuringen**
De formulierontwerpen van de route door multi-step overzichtsprocessen met op rol-gebaseerde taken. Belanghebbenden kunnen [ herzien, ](/help/forms/create-reviews-forms.md) commentaar [, en vormen goedkeuren vóór publicatie, die kwaliteitscontrole en nalevingstoezicht handhaven gebruikend ](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) de werkschema&#39;s van AEM [.](/help/forms/aem-forms-workflow.md)

**het Beheer van de Versie**
Formulierversies bijhouden en audittrails bijhouden voor naleving van regelgeving. Ingebouwd [ versioning ](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) verzekert u veranderingen kunt terugschroeven, herhalingen vergelijken, en historische verslagen voor nalevingscontroles handhaven.

**Controle van de Toegang en Toestemmingen**
Definieer korrelige machtigingen voor het maken, bewerken en publiceren van formulieren. [ Op rol-gebaseerde toegang ](/help/forms/forms-groups-privileges-tasks.md) verzekert slechts gemachtigde gebruikers kunnen vormen wijzigen, terwijl het handhaven van scheiding van taken voor gevoelige bedrijfsprocessen.

### Publiceren: Multi-Channel Distribution {#publish}

Gebruik formulieren via meerdere kanalen en aanraakpunten om gebruikers overal te bereiken.

**Omnichannel het Publiceren**
Publiceer vormen aan [ AEM Sites ](/help/forms/embed-adaptive-form-aem-sites.md), standalone Web-pagina&#39;s, mobiele toepassingen, of [ bed in derdesystemen ](/help/forms/embed-adaptive-form-core-components-external-web-page.md) in. Publiceren met één bron zorgt voor consistentie en past zich aan de verschillende kanaalvereisten aan.

**Lokalisatie en Personalization**
Lever vormen in veelvoudige talen gebruikend [ de vertaalwerkschema&#39;s van AEM ](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md), met steun voor zowel [ links-aan-recht als van rechts-aan-linkertalen ](/help/forms/right-left-languages.md). Integreer met Adobe Target om de ervaring van formulieren aan te passen op basis van gebruikerssegmenten, gedrag of contextafhankelijke gegevens.

**Optimalisering van Prestaties**
Gebruik Edge Delivery Services voor bliksemsnel laden van formulieren en optimale SEO-prestaties. De netwerken van de levering van inhoud verzekeren globale toegankelijkheid met minimale latentie.

**Forms Portal**
Maak gecentraliseerde formulieropslagplaatsen waar gebruikers formulieren kunnen detecteren, openen en beheren. [ Forms Portal ](/help/forms/configure-forms-portal.md) verstrekt onderzoeksmogelijkheden, vorm categorisering, ontwerp beheer, en voorlegging die in een verenigde interface voor verbeterde gebruikerservaring volgen.

### Vastleggen: gebruikerservaring en gegevensverzameling {#capture}

Optimaliseer de ervaring bij het invullen van formulieren om de voltooiingssnelheden en de gegevenskwaliteit te maximaliseren.

**Responsief Ontwerp**
Forms past zich automatisch aan verschillende schermgrootten en invoermethoden aan. De aanraking-geoptimaliseerde controles, toetsenbordnavigatie, en de verenigbaarheid van de het schermlezer verzekeren [ toegankelijkheid ](/help/forms/creating-accessible-adaptive-forms.md) over alle gebruikerstypes.

**Digitale Handtekeningen**
Integreer [ Teken van Adobe ](/help/forms/working-with-adobe-sign.md) voor wettelijk bindende e-handtekeningen binnen de vormervaring. Gebruikers kunnen documenten ondertekenen zonder het formulier te verlaten, goedkeuringsprocessen te stroomlijnen en het verlaten van het formulier te beperken.

**legt Acties** voor
Vorm [ voorlegt acties ](/help/forms/configure-submit-actions-core-components.md) om te bepalen wat gebeurt wanneer de gebruikers vormen voltooien en voorleggen. De gegevens van de route aan e-mail, gegevensbestanden, werkschema&#39;s, of externe systemen terwijl het verstrekken van directe terugkoppelt en bevestiging aan gebruikers.

### Proces: Verzendverwerking en Verpletteren {#process}

Verwerk formulierverzendingen met robuuste verwerkings-, validatie- en routeringsmogelijkheden.

**Bevestiging en Verwerking van Gegevens**
Zorg voor gegevensintegriteit via validatie aan de serverzijde en automatische verwerkingsregels. Transformeer, bevestig, en route voorgelegde gegevens terwijl het produceren van ontvangstbewijzen, bevestigingen, of follow-upmaterialen voor gebruikers.

**Communicatie APIs**
Produceer, manipuleer, en beveilig documenten programmatically door [ RESTful APIs ](/help/forms/aem-forms-cloud-service-communications-introduction.md). Creeer PDFs, druk-klaar formaten, assembleer documenten, pas digitale handtekeningen toe, en proces high-volume [ partijverrichtingen ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) voor onderneming-schaal documentwerkschema&#39;s.

**Document van Verslag**
Automatisch PDF-records genereren van formulierverzendingen voor compatibiliteit en gebruikersbevestiging. [ Document van Verslag ](/help/forms/generate-document-of-record-core-components.md) leidt tot geformatteerde, bedrukbare versies van voltooide formulieren met voorgelegde gegevens, die officiële documentatie voor transacties en regelgevende vereisten verstrekken.

**Orchestratie van het Werkschema**
Groeiend complexe bedrijfsprocessen op basis van formulierverzendingen. De gegevens van de route door goedkeuringsketens, wijzen taken aan specifieke gebruikers toe, en automatiseren routine verrichtingen terwijl het handhaven van controletrails.

**de Behandeling en Terugwinning van de Fout**
De ingebouwde heruitzettingsmechanismen en fallback-verwerking zorgen ervoor dat er geen verzendingen verloren gaan. De uitvoerige registreren helpt problemen oplossen en de overeenkomsten van het de dienstniveau handhaven.

### Integreer: back-end connectiviteit {#integrate}

Sluit formulieren aan op bestaande bedrijfssystemen en gegevensbronnen voor een naadloze informatiestroom.

**pre-gebouwde Schakelaars**
De inheemse integratie met [ Salesforce ](/help/forms/configure-salesforce.md), [ Microsoft Dynamics ](/help/forms/configure-msdynamics.md), [ SharePoint ](/help/forms/connect-forms-to-sharepoint-document-library.md), en de oplossingen van Adobe Experience Cloud. Vooraf gebouwde connectors verkorten de ontwikkelingstijd en zorgen voor betrouwbare gegevenssynchronisatie.

**RESTful API Integratie**
Verbind met om het even welke web-toegankelijke dienst door RESTful APIs via [ voorlegt acties ](/help/forms/configure-submit-action-restpoint.md) of [ gegevensintegratie ](/help/forms/data-integration.md). Het model van de Gegevens van de Vorm abstracteert integratieingewikkeldheid, die een verenigbare interface ongeacht de onderliggende systeemarchitectuur verstrekken.

**Real-Time Uitwisseling van Gegevens**
Bidirectionele gegevensstroom tussen formulieren en bedrijfssystemen mogelijk maken. Vul vormen van bestaande verslagen vooraf in, bevestig tegen levende gegevens, en werk veelvoudige systemen gelijktijdig op voorlegging door uitvoerige [ gegevensintegratie ](/help/forms/data-integration.md) bij.

### Track: analyse en prestatiebewaking {#track}

Begrijp de prestaties en het gedrag van de gebruiker van het formulier via uitgebreide analyses en controle.

**Analytics van de Vorm**
De voltooiingstarieven van het spoor, verlaten patronen, en gebied-vlakke interactie door [ de integratie van Adobe Analytics ](/help/forms/integrate-aem-forms-with-adobe-analytics.md). Identificeer wrijvingspunten, meet omzettingstekens, en begrijp gebruikersgedrag over verschillende segmenten.

**Controle van Prestaties**
Volg de laadtijden van formulieren, de prestaties van de verzending en de systeemprestaties. In real time dashboards verstrekken inzicht in technische gezondheid en gebruikerservaringsmetriek.

**Business Intelligence**
Rapporten genereren over formuliergebruik, verzendingsvolumes en procesefficiëntie. Analyses informeren over capaciteitsplanning, optimalisatie van gebruikerservaring en verbeteringen in het bedrijfsproces.

**de Rapporten van de Transactie**
Het gebruik van toezicht API, de volumes van de documentgeneratie, en [ factureerbare transacties ](/help/forms/transaction-reports-billable-apis.md) over uw plaatsing van AEM Forms. Houd consumptiepatronen bij, optimaliseer de toewijzing van bronnen en houd de naleving van gebruiksgebaseerde licentievereisten in stand.

### Archief: Documentbeheer en compatibiliteit {#archive}

Sla verzonden formulieren en gegenereerde documenten veilig op en beheer ze voor langdurige bewaring en naleving.

**Opslag van het Document**
De opslag geproduceerde documenten en vormvoorlegging in het systeem van het Beheer van Digitale Activa van AEM of integreert met externe documentbewaarplaatsen zoals [ SharePoint ](/help/forms/configure-submit-action-sharepoint.md), [ OneDrive ](/help/forms/configure-submit-action-onedrive.md), of [ Azure BlobOpslag ](/help/forms/configure-submit-action-azure-blob-storage.md).

**Naleving en Behoud**
Voer beleid van het gegevensbehoud uit dat aan regelgevende vereisten met inbegrip van GDPR, CCPA, en HIPAA voldoet. [ Geautomatiseerde archiveringsprocessen ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) verzekeren de documenten voor vereiste periodes worden behouden en veilig verwijderd wanneer aangewezen.

**Veiligheid en Toegangscontrole**
Pas encryptie, digitale handtekeningen, en [ op rol-gebaseerde toegangscontroles ](/help/forms/forms-groups-privileges-tasks.md) op gearchiveerde documenten toe. Met audittrails worden de toegang tot documenten en wijzigingen voor nalevingsrapportage en veiligheidstoezicht bijgehouden.

### Verbeteren: optimalisatie en verbetering {#improve}

De prestaties en gebruikerservaring van formulieren voortdurend optimaliseren door middel van gegevensgestuurde inzichten en tests.

**A/B het Testen Integratie**
Met Adobe Target kunt u verschillende formulierindelingen, veldinstellingen en gebruikersstromen testen. Door middel van statistische analyse kunt u de meest effectieve benaderingen voor verschillende gebruikerssegmenten en gebruiksgevallen vaststellen.

**Analytics-Gedreven Optimalisering**
Analyseer gegevens over gebruikersgedrag om verbeteringsmogelijkheden te identificeren. [ Mening en begrijp analyserapporten ](/help/forms/view-understand-aem-forms-analytics-reports.md) voor warmtetoewijzing, de analyse van de gebiedsinteractie, en de herkenning van het bestemmingspatroon om iteratieve ontwerpverhogingen te informeren.

**Interactieve Verbetering**
Voer ononderbroken verbeteringsprocessen uit die op gebruiker terugkoppelen, prestatiesmetriek, en bedrijfsvereisten worden gebaseerd. [ de controle van de Versie ](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) en het terugschroeven van prijzen laten veilige experimentatie en snelle herhaling toe.

## Aan de slag {#getting-started}

De aanpak die u kiest, hangt af van uw onmiddellijke behoeften en langetermijndoelstellingen.

### Snel aan de slag: eenvoudige Forms {#quick-start}

Kies de gewenste ontwerpaanpak op basis van uw technische achtergrond en prestatie-eisen:

**Visual Form Building:**

1. **[creeer adaptieve vormen met de Componenten van de Kern](/help/forms/creating-adaptive-form-core-components.md)** voor moderne, ontvankelijke vormen
2. **[vormen voorlegt acties](/help/forms/configure-submit-actions-core-components.md)** om vormgegevens te behandelen
3. **[bedt vormen in AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md)** of aandeel via directe verbindingen in

**op document-Gebaseerde Authoring:**

1. **[bouwt vormen gebruikend Excel](/help/edge/docs/forms/create-forms.md)** met Edge Delivery Services voor krachtige vormen
2. **[publiceer aan Edge Delivery](/help/edge/docs/forms/publish-forms.md)** voor optimale ladingssnelheden en SEO

**Verouderde Steun van de Vorm:**

- **[HTML5 Forms](/help/forms/introductionhtml5.md)** voor mobiel-geoptimaliseerde XFA vorm het teruggeven

### Geavanceerde implementatie: zakelijke processen {#advanced-implementation}

Voor complexe vereisten met betrekking tot meerdere systemen, het genereren van documenten en goedkeuringswerkstromen:

**de Integratie en de Werkschema&#39;s van Gegevens:**

1. **[Modellen van de Gegevens van de Vorm van de Opstelling](/help/forms/create-form-data-models.md)** om achterste systemen te verbinden
2. **[werkschemaprocessen van het Ontwerp](/help/forms/aem-forms-workflow.md)** voor goedkeuring en het verpletteren
3. **[vorm analyses](/help/forms/integrate-aem-forms-with-adobe-analytics.md)** om prestaties te meten

**de Diensten &amp; Mededelingen van het Document:**

1. **[voer Communicatie APIs](/help/forms/aem-forms-cloud-service-communications-introduction.md)** voor geautomatiseerde documentgeneratie uit
2. **[creeer Interactieve Mededelingen](/help/forms/interactive-communication/create-interactive-communication.md)** voor gepersonaliseerde verklaringen en berichten
3. **[Poort van Forms van de opstelling](/help/forms/configure-forms-portal.md)** voor gecentraliseerd vormbeheer

### Implementatie voor bedrijven: schalen en beheren {#enterprise-deployment}

Voor implementaties voor de hele organisatie die governance, naleving en controle vereisen:

**Architectuur &amp; Bestuur:**

1. **[de architectuurpatronen van het Overzicht](/help/forms/aem-forms-cloud-service-architecture.md)** voor scalable plaatsing
2. **[vorm gebruikersbeheer](/help/forms/forms-groups-privileges-tasks.md)** en toegangscontroles
3. **[de werkschema&#39;s van de de opstellingsontwikkeling](/help/forms/setup-local-development-environment.md)** voor teamsamenwerking

**Migratie &amp; Controle:**

1. **[de migratiestrategieën van het Plan](/help/forms/migrate-to-forms-as-a-cloud-service.md)** van bestaande systemen
2. **[voer transactie controle](/help/forms/transaction-reports-billable-apis.md)** voor gebruik het volgen en naleving uit

<details>
<summary><strong> Veelgestelde vragen ❓ </strong></summary>

**wat is een vormbouwer?**
Een formulierontwerper is een hulpmiddel waarmee u digitale formulieren kunt maken zonder te coderen. U kunt formulieren ontwerpen met interfaces voor slepen en neerzetten, velden zoals tekstvakken en vervolgkeuzelijsten toevoegen en ze online publiceren om gegevens van gebruikers te verzamelen.

**hoe creeer ik een online vorm?**
Met AEM Forms kunt u adaptieve formulieren maken met behulp van Core Components via een visuele slepen-en-neerzeteditor, krachtige formulieren maken met Edge Delivery Services of Foundation Components gebruiken voor bestaande workflows. Begin door een malplaatje te selecteren, vormgebieden toe te voegen, gegevensverbindingen te vormen, en over veelvoudige kanalen te publiceren.

**wat maakt een goede online vorm?**
Goede onlineformulieren reageren op mobiele apparaten, kunnen snel worden geladen, beschikken over duidelijke labels, gebruiken de logische volgorde van velden, omvatten validatie om fouten te voorkomen en geven direct feedback aan gebruikers bij verzending.

**Kan ik vormen met andere bedrijfssystemen integreren?**
Ja, moderne formulierbuilders bieden uitgebreide integratiemogelijkheden. U kunt formulieren verbinden met CRM-systemen, e-mailmarketingplatforms, databases, cloudopslag en tools voor workflowautomatisering om uw bedrijfsprocessen te stroomlijnen.

**Zijn online formulieren veilig?**
De professionele vormbouwers omvatten onderneming-rang veiligheidseigenschappen zoals gegevensencryptie, veilige gegevenstransmissie, toegangscontroles, en naleving van verordeningen zoals GDPR, HIPAA, en CCPA om gevoelige informatie te beschermen.

**Hoe voeg ik e-handtekeningen aan mijn vormen toe?**
Digitale handtekeningen kunnen rechtstreeks in formulieren worden geïntegreerd met Adobe Sign of andere leveranciers van e-handtekeningen. Hierdoor kunnen gebruikers documenten ondertekenen binnen de formulierervaring, waardoor er geen aparte workflows voor handtekeningen nodig zijn en het verlaten van het formulier afneemt.

**kunnen de vormen automatisch PDF documenten produceren?**
Ja, moderne formulierplatforms kunnen automatisch PDF-ontvangstbewijzen, bevestigingen of registratiedocumenten genereren wanneer formulieren worden verzonden. Dit is van essentieel belang voor naleving, het bijhouden van gegevens en het geven van een onmiddellijke bevestiging aan gebruikers.

**Hoe volg ik vormprestaties en analyses?**
Met behulp van formulieranalyses hebt u meer inzicht in voltooiingssnelheden, beëindigingspatronen en gebruikersgedrag. Integratie met analyseplatforms zoals Adobe Analytics biedt inzicht in welke velden wrijving veroorzaken en hoe omrekeningskoersen kunnen worden geoptimaliseerd.

**wat is de automatisering van het vormwerkschema?**
De automatisering van het werkschema van de vorm leidt indieningen door goedkeuringsprocessen, wijst taken aan teamleden toe, en brengt acties in andere bedrijfssystemen teweeg. Hierdoor wordt handmatige verwerking voorkomen en wordt een consistente verwerking van formuliergegevens gegarandeerd.

**Hoe maak ik formulieren toegankelijk voor gebruikers met een handicap?**
[ Toegankelijke vormen ](/help/forms/creating-accessible-adaptive-forms.md) omvatten juiste etikettering, toetsenbordnavigatie, de verenigbaarheid van de schermlezer, en naleving van richtlijnen WCAG. Dit zorgt ervoor dat alle gebruikers formulieren kunnen invullen, ongeacht hun mogelijkheden of ondersteunende hulpmiddelen.

**hoeveel kosten de vormbouwers?**
De prijsstelling voor AEM Forms as a Cloud Service is afhankelijk van uw specifieke vereisten, gebruiksvolume en vereisten voor functies. Neem contact op met Adobe Sales of uw Adobe-vertegenwoordiger voor gedetailleerde prijsinformatie en om een oplossing te bespreken die is afgestemd op uw organisatie.

</details>

## Volgende stappen {#next-steps}

Verken de mogelijkheden die overeenkomen met uw huidige prioriteiten:

- **[Bouw uw eerste vorm](/help/forms/creating-adaptive-form-core-components.md)** om het auteursmilieu te ervaren
- **[de architectuuropties van het Overzicht](/help/forms/aem-forms-cloud-service-architecture.md)** voor plaatsing planning
- **[Opstelling uw ontwikkelomgeving](/help/forms/setup-local-development-environment.md)** voor teamsamenwerking
- **[Onderzoek integratieopties](/help/forms/data-integration.md)** voor het verbinden van bestaande systemen

Voor uitgebreide implementatierichtlijnen, overweeg Adobe Professional Services om uw implementatie te versnellen en best practices vanaf het begin te garanderen.
