---
title: Overzicht van SPA-editor
description: Dit artikel geeft een uitvoerig overzicht van de Redacteur van het KUUROORD en hoe het werkt omvat gedetailleerde werkschema's van interactie van de Redacteur van het KUUROORD binnen AEM.
exl-id: 9814d86e-8d87-4f7f-84ba-6943fe6da22f
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '1633'
ht-degree: 0%

---


# Overzicht van SPA-editor {#spa-editor-overview}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen de inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend dergelijke kaders wordt gebouwd.

De redacteur van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Deze pagina geeft een overzicht van hoe de steun van het KUUROORD in AEM gestructureerd is, hoe de Redacteur van het KUUROORD werkt, en hoe het kader van het KUUROORD en AEM in synch houden.

{{ue-over-spa}}

## Inleiding {#introduction}

De plaatsen die gebruikend gemeenschappelijke kaders van het KUUROORD zoals React en Angular worden gebouwd laden hun inhoud via dynamische JSON en verstrekken niet de structuur van HTML die voor de Redacteur van de Pagina van AEM noodzakelijk is om bewerkingscontroles te kunnen plaatsen.

Om het uitgeven van SPAs binnen AEM toe te laten, is een afbeelding tussen de output JSON van het KUUROORD en het inhoudsmodel in de bewaarplaats van AEM nodig om veranderingen in de inhoud te bewaren.

De steun van het KUUROORD in AEM introduceert een dunne laag JS die met de code van het KUUROORD JS wanneer geladen in de Redacteur van de Pagina interactie heeft waarmee de gebeurtenissen kunnen worden verzonden en de plaats voor uitgeeft controles kunnen worden geactiveerd om in-context het uitgeven toe te staan. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van het KUUROORD als Diensten van de Inhoud moet worden geladen.

Voor meer details over SPAs in AEM, zie het volgende:

* [&#x200B; Vervaging van het KUUROORD &#x200B;](blueprint.md) voor de technische vereisten van een KUUROORD.
* [&#x200B; Begonnen het Worden met SPAs in AEM die Reageren &#x200B;](getting-started-react.md) voor een snelle tour van een eenvoudig KUUROORD gebruiken Reageert.
* [&#x200B; Begonnen het Worden met SPAs in AEM gebruikend Angular &#x200B;](getting-started-angular.md) voor een snelle reis van een eenvoudige KUUROORD die Angular gebruikt.

## Ontwerp {#design}

De paginacomponent voor een SPA verstrekt niet de elementen van HTML van zijn kindcomponenten via het JSP of HTML- dossier. Deze verrichting wordt gedelegeerd aan het kader van het KUUROORD. De representatie van onderliggende componenten of modellen wordt opgehaald als een JSON-gegevensstructuur van het JCR. De componenten van het KUUROORD worden dan toegevoegd aan de pagina volgens die structuur. Dit gedrag onderscheidt de aanvankelijke lichaamcompositie van de paginacomponent van niet-SPA tegenhangers.

### Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven `PageModel` -bibliotheek. Het KUUROORD moet de bibliotheek van het Model van de Pagina gebruiken zodat kan het door de Redacteur van het KUUROORD worden geïnitialiseerd en worden authored. De bibliotheek Paginamodel die indirect via de `aem-react-editable-components` npm wordt geleverd aan de component AEM Page. Het paginamodel is een tolk tussen AEM en de SPA en moet daarom altijd aanwezig zijn. Wanneer de pagina is gemaakt, moet er een extra bibliotheek `cq.authoring.pagemodel.messaging` worden toegevoegd om communicatie met de pagina-editor mogelijk te maken.

Als de de paginacomponent van het KUUROORD van de component van de paginaconnecorrectie erft, zijn er twee opties om de `cq.authoring.pagemodel.messaging` categorie van de cliëntbibliotheek beschikbaar te maken:

* Als de sjabloon bewerkbaar is, voegt u deze toe aan het paginabeleid.
* U kunt ook de categorieën toevoegen met de `customfooterlibs.html` .

Voor elk middel in het uitgevoerde model zal SPA een daadwerkelijke component in kaart brengen die zal doen
renderen. Het model, dat als JSON wordt vertegenwoordigd, wordt dan teruggegeven gebruikend de componentenafbeeldingen binnen een container.

![&#x200B; Model en componentenafbeelding in SPAs &#x200B;](assets/model-component-mapping.png)

>[!CAUTION]
>
>Het opnemen van de categorie `cq.authoring.pagemodel.messaging` moet worden beperkt tot de context van de SPA-editor.

### Gegevenstype communicatie {#communication-data-type}

Wanneer de categorie `cq.authoring.pagemodel.messaging` aan de pagina wordt toegevoegd, wordt een bericht naar de Pagina-editor verzonden om het gegevenstype voor JSON-communicatiegegevens vast te stellen. Wanneer het gegevenstype voor communicatie is ingesteld op JSON, communiceren de GET-aanvragen met de eindpunten van een component in het Sling Model. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. De bibliotheek van het Model van de Pagina informeert dan het KUUROORD van updates.

![&#x200B; mededeling van het KUUROORD &#x200B;](assets/communication.png)

## Workflow {#workflow}

U kunt de stroom van de interactie tussen SPA en AEM begrijpen door van de Redacteur van het KUUROORD als bemiddelaar tussen twee te denken.

* De communicatie tussen de paginaredacteur en het KUUROORD wordt gemaakt gebruikend JSON in plaats van HTML.
* De paginaredacteur verstrekt de recentste versie van het paginamodel aan het KUUROORD via iframe en overseinen API.
* De manager van het paginamodel brengt de redacteur op de hoogte het klaar voor uitgave is en gaat het paginamodel als structuur JSON over.
* De editor wijzigt de DOM-structuur van de pagina die wordt gemaakt niet of opent deze zelfs niet, maar biedt wel het nieuwste paginamodel.

![&#x200B; het werkschema van het KUUROORD &#x200B;](assets/workflow.png)

### Basis SPA Editor-workflow {#basic-spa-editor-workflow}

Rekening houdend met de belangrijkste elementen van de Redacteur van het KUUROORD, verschijnt het werkschema op hoog niveau van het uitgeven van een KUUROORD binnen AEM aan de auteur als volgt.

![&#x200B; Geanimeerde het werkschema van het KUUROORD &#x200B;](assets/workflow.gif)

1. De redacteur van het KUUROORD laadt.
1. SPA wordt geladen in een afzonderlijk kader.
1. SPA vraagt JSON-inhoud aan en rendert componenten client-side.
1. De Redacteur van het KUUROORD ontdekt teruggegeven componenten en produceert overlays.
1. De auteur klikt op bedekking en toont de bewerkingswerkbalk van de component.
1. De Redacteur van het KUUROORD persisteert uitgeeft met een POST- verzoek aan de server.
1. De redacteur van het KUUROORD verzoekt bijgewerkte JSON aan de Redacteur van het KUUROORD, die naar het KUUROORD met een DOM Gebeurtenis wordt verzonden.
1. SPA geeft de betrokken component opnieuw terug, die zijn DOM bijwerkt.

>[!NOTE]
>
>Houd rekening met:
>
>* Het KUUROORD is altijd verantwoordelijk voor zijn vertoning.
>* De redacteur van het KUUROORD wordt geïsoleerd van het KUUROORD zelf.
>* In productie (publiceer), wordt de redacteur van het KUUROORD nooit geladen.

### Workflow voor paginabewerking op client-server {#client-server-page-editing-workflow}

Dit is een meer gedetailleerd overzicht van de cliënt-server interactie wanneer het uitgeven van een KUUROORD.

![&#x200B; Cliënt-server het uitgeven werkschema &#x200B;](assets/client-server-editing.png)

1. Het KUUROORD initialiseert zich en verzoekt het paginamodel van de Verschuivende ModelExporter.
1. De verkoper ModelExporter verzoekt om de middelen die de pagina van de bewaarplaats samenstellen.
1. De opslagplaats retourneert de bronnen.
1. De verkoper van het ModelExporter keert het model van de pagina terug.
1. Het KUUROORD concretiseert zijn componenten die op het paginamodel worden gebaseerd.
1. **6a** de inhoud deelt de redacteur mee dat het voor creatie klaar is.

   **6b** de paginaredacteur verzoekt de componentenauteursconfiguraties.

   **6c** de paginaredacteur ontvangt de componentenconfiguraties.
1. Wanneer de auteur een component bewerkt, wordt in de pagina-editor een wijzigingsverzoek naar de standaard POST-servlet gepost.
1. De bron wordt bijgewerkt in de gegevensopslagruimte.
1. De bijgewerkte bron wordt geleverd aan de POST-servlet.
1. De standaard POST servlet deelt de paginaredacteur mee dat het middel is bijgewerkt.
1. De paginaeditor vraagt om het nieuwe paginamodel.
1. De bronnen waaruit de pagina bestaat, worden opgevraagd bij de opslagplaats.
1. De bronnen waaruit de pagina bestaat, worden door de gegevensopslagruimte aan de Verkoopmodel Exporter verschaft.
1. Het bijgewerkte paginamodel wordt geretourneerd aan de editor.
1. De paginaredacteur werkt de verwijzing van het paginamodel van SPA bij.
1. Het KUUROORD werkt zijn componenten bij die op de nieuwe verwijzing van het paginamodel worden gebaseerd.
1. De componentconfiguraties van de paginaeditors worden bijgewerkt.

   **17a** het KUUROORD signaleert de paginaredacteur dat de inhoud klaar is.

   **17b** de paginaredacteur verstrekt het KUUROORD met componentenconfiguraties.

   **17c** SPA verstrekt bijgewerkte componentenconfiguraties.

### Ontwerpworkflow {#authoring-workflow}

Dit is een gedetailleerder overzicht dat is toegespitst op de ontwerpervaring.

![&#x200B; SPA auteurswerkschema &#x200B;](assets/authoring-workflow.png)

1. Het SPA haalt het paginamodel.
1. **2a** het paginamodel voorziet de redacteur van de gegevens die voor het ontwerpen worden vereist.

   **2b** wanneer op de hoogte gebracht, werkt de componentenorganisator de inhoudsstructuur van de pagina bij.
1. De componentenbeheerder vraagt de afbeelding tussen een het middeltype van AEM en een component van het KUUROORD.
1. De componentenorganisator concretiseert dynamisch de component van het KUUROORD die op het paginamodel en componentenafbeelding wordt gebaseerd.
1. De paginaeditor werkt het paginamodel bij.
1. **6a** het paginamodel verstrekt bijgewerkte auteursgegevens aan de paginaredacteur.

   **6b** het paginamodel verzendt veranderingen in de componentenorganisator.
1. De componentorchestrator haalt de componenttoewijzing op.
1. De componentbeheerder werkt de inhoud van de pagina bij.
1. Wanneer SPA voltooit het bijwerken van de inhoud van de pagina, laadt de paginaredacteur het auteursmilieu.

## Vereisten en beperkingen {#requirements-limitations}

Om de auteur toe te laten om de paginaredacteur te gebruiken om de inhoud van een KUUROORD uit te geven, moet uw toepassing van het KUUROORD worden uitgevoerd om met de Redacteur SDK van AEM te communiceren SPA. Zie [&#x200B; Begonnen het Worden met SPAs in AEM die Reageer &#x200B;](getting-started-react.md) document voor minimum gebruiken dat u moet weten om van u het lopen te krijgen.

### Ondersteunde kaders {#supported-frameworks}

De redacteur SDK van het KUUROORD steunt de volgende minimale versies:

* 16.x en hoger reageren
* Angular 6.x en hoger

Eerdere versies van deze frameworks werken mogelijk samen met de AEM SPA Editor SDK, maar worden niet ondersteund.

### Aanvullende kaders {#additional-frameworks}

De extra kaders van het KUUROORD kunnen worden uitgevoerd om met de Redacteur SDK van AEM te werken SPA. Zie het [&#x200B; document van het Vervagen van het KUUROORD &#x200B;](blueprint.md) voor de vereisten dat een kader moet vervullen om een kader-specifieke laag tot stand te brengen die uit modules, componenten, en de diensten wordt samengesteld om met de Redacteur van AEM te werken SPA.

### Meerdere kiezers gebruiken {#multiple-selectors}

De extra douanekiezers kunnen als deel van een SPA worden bepaald en worden gebruikt die voor AEM SPA SDK wordt ontwikkeld. Voor deze ondersteuning is echter vereist dat de `model` -kiezer de eerste kiezer is en dat de extensie `.json` is, zoals de JSON Exporter vereist.

### Vereisten voor teksteditor {#text-editor-requirements}

Als u op zijn plaats redacteur van een tekstcomponent wilt gebruiken die in KUUROORD wordt gecreeerd is er extra vereiste configuratie.

1. Stel een willekeurig kenmerk in op het containerelement dat de tekst HTML bevat. In het geval van het Project van het KND SPA, is het een `<div>` element en de selecteur die is gebruikt is `data-rte-editelement`.
1. Stel de configuratie `editElementQuery` in voor de overeenkomende AEM-tekstcomponent `cq:InplaceEditingConfig` die bijvoorbeeld naar die kiezer wijst `data-rte-editelement` . Hierdoor weet de editor welk HTML-element de HTML-tekst omsluit.

Voor extra informatie over het `editElementQuery` bezit en de configuratie van de rijke tekstredacteur, zie [&#x200B; de Rijke Redacteur van de Tekst &#x200B;](/help/implementing/developing/extending/rich-text-editor.md) vormen.

### Beperkingen {#limitations}

De AEM SPA Editor SDK wordt volledig ondersteund door Adobe en wordt verder uitgebreid en uitgebreid. De volgende eigenschappen van AEM worden nog niet gesteund door de Redacteur van het KUUROORD:

* Doelmodus
* ContextHub
* Inline-afbeeldingen bewerken
* Configs bewerken (bijvoorbeeld listeners)
* Ongedaan maken/Opnieuw
* Pagina diff en Tijd verdraaien
* Eigenschappen die HTML uitvoeren die server-kant zoals [&#x200B; controleren van de Verbinding herschrijven, &#x200B;](/help/operations/link-checker.md) CDN herschrijvingsdienst, verkorting URL etc.
* Modus Ontwikkelaar
* AEM Launches
