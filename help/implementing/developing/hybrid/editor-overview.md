---
title: Overzicht SPA Editor
description: In dit artikel wordt een uitgebreid overzicht gegeven van de SPA Editor en van de manier waarop dit werkt. In dit artikel zijn gedetailleerde workflows opgenomen van interactie tussen de SPA Editor in AEM.
exl-id: 9814d86e-8d87-4f7f-84ba-6943fe6da22f
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1632'
ht-degree: 0%

---

# Overzicht SPA Editor {#spa-editor-overview}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van dergelijke frameworks.

De SPA Editor biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Deze pagina geeft een overzicht van hoe SPA ondersteuning is gestructureerd in AEM, hoe de SPA Editor werkt en hoe het SPA framework en de AEM synchroon blijven.

## Inleiding {#introduction}

De plaatsen die gebruikend gemeenschappelijke SPA zoals React en Angular worden gebouwd laden hun inhoud via dynamische JSON en verstrekken niet de structuur van de HTML die voor de AEM Redacteur van de Pagina noodzakelijk is om bewerkingscontroles te kunnen plaatsen.

Om het bewerken van SPA binnen AEM mogelijk te maken, is een toewijzing tussen de JSON-uitvoer van de SPA en het inhoudsmodel in de AEM opslagplaats nodig om wijzigingen in de inhoud op te slaan.

SPA ondersteuning in AEM introduceert een dunne JS-laag die communiceert met de SPA JS-code wanneer deze wordt geladen in de Pagina-editor waarmee gebeurtenissen kunnen worden verzonden en de locatie voor de bewerkingsbesturingselementen kan worden geactiveerd om in-context bewerken mogelijk te maken. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van de SPA door als Diensten van de Inhoud moet worden geladen.

Raadpleeg de volgende bronnen voor meer informatie over SPA in AEM:

* [SPA](blueprint.md) voor de technische voorschriften van een SPA.
* [Aan de slag met SPA in AEM met Reageren](getting-started-react.md) voor een snelle rondleiding van een eenvoudige SPA die React gebruiken.
* [Aan de slag met SPA in AEM met Angular](getting-started-angular.md) voor een snelle rondleiding van een eenvoudige SPA die Angular gebruiken.

## Ontwerp {#design}

De paginacomponent voor een SPA biedt de HTML-elementen van de onderliggende componenten niet via het JSP- of HTML-bestand. Deze bewerking wordt gedelegeerd aan het SPA. De representatie van onderliggende componenten of modellen wordt opgehaald als een JSON-gegevensstructuur van het JCR. De SPA componenten worden vervolgens volgens die structuur aan de pagina toegevoegd. Dit gedrag onderscheidt de aanvankelijke lichaamssamenstelling van de paginacomponent van niet-SPA tegenhangers.

### Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven `PageModel` bibliotheek. De SPA moet de bibliotheek Paginamodel gebruiken, zodat deze kan worden geïnitialiseerd en geschreven door de SPA Editor. De bibliotheek Paginamodel die indirect via de `aem-react-editable-components` npm. Het paginamodel is een tolk tussen AEM en de SPA en moet daarom altijd aanwezig zijn. Wanneer de pagina is gemaakt, voegt u een extra bibliotheek toe `cq.authoring.pagemodel.messaging` moet worden toegevoegd om communicatie met de paginaeditor mogelijk te maken.

Als de SPA paginacomponent overerft van de hoofdcomponent van de pagina, zijn er twee opties voor het maken van `cq.authoring.pagemodel.messaging` beschikbare categorie voor clientbibliotheek:

* Als de sjabloon bewerkbaar is, voegt u deze toe aan het paginabeleid.
* U kunt ook de categorieën toevoegen met de opdracht `customfooterlibs.html`.

Voor elke bron in het geëxporteerde model wijst de SPA een werkelijke component toe die de rendering uitvoert. Het model, dat als JSON wordt vertegenwoordigd, wordt dan teruggegeven gebruikend de componentenafbeeldingen binnen een container.

![Model- en componenttoewijzing in SPA](assets/model-component-mapping.png)

>[!CAUTION]
>
>De opneming van de `cq.authoring.pagemodel.messaging` Deze categorie moet beperkt blijven tot de context van de SPA-editor.

### Gegevenstype communicatie {#communication-data-type}

Wanneer de `cq.authoring.pagemodel.messaging` wordt toegevoegd aan de pagina. Er wordt een bericht naar de Pagina-editor verzonden om het JSON-communicatietype vast te stellen. Wanneer het gegevenstype van communicatiegegevens aan JSON wordt geplaatst, zullen de verzoeken van de GET met de Sling Model eindpunten van een component communiceren. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. De bibliotheek Paginamodel stelt vervolgens de SPA van updates op de hoogte.

![SPA](assets/communication.png)

## Workflow {#workflow}

U kunt de stroom van de interactie tussen de SPA en AEM begrijpen door de SPA Redacteur als bemiddelaar tussen twee te denken.

* De communicatie tussen de pagina-editor en de SPA wordt gemaakt met JSON in plaats van met HTML.
* De pagina-editor biedt de meest recente versie van het paginamodel aan de SPA via de iframe- en messaging-API.
* De manager van het paginamodel brengt de redacteur op de hoogte het klaar voor uitgave is en gaat het paginamodel als structuur JSON over.
* De editor wijzigt de DOM-structuur van de pagina die wordt gemaakt niet of opent deze zelfs niet, maar biedt wel het nieuwste paginamodel.

![SPA](assets/workflow.png)

### Basic SPA Editor Workflow {#basic-spa-editor-workflow}

Met inachtneming van de belangrijkste elementen van de SPA Editor, ziet de auteur de workflow op hoog niveau voor het bewerken van een SPA binnen AEM er als volgt uit.

![SPA workflow met animaties](assets/workflow.gif)

1. SPA Editor wordt geladen.
1. SPA wordt in een afzonderlijk frame geladen.
1. SPA vraagt JSON-inhoud aan en rendert componenten client-side.
1. SPA Editor detecteert gerenderde componenten en genereert overlays.
1. De auteur klikt op bedekking en toont de bewerkingswerkbalk van de component.
1. SPA de Redacteur met een verzoek van de POST aan de server voortduurt uitgeeft.
1. SPA Editor vraagt bijgewerkte JSON naar de SPA Editor, die met een DOM-gebeurtenis naar de SPA wordt verzonden.
1. SPA geeft de betrokken component opnieuw weer, waarbij het DOM wordt bijgewerkt.

>[!NOTE]
>
>Houd rekening met:
>
>* De SPA is altijd verantwoordelijk voor de weergave.
>* De SPA Editor staat los van de SPA zelf.
>* In productie (publiceren), wordt de SPA redacteur nooit geladen.

### Workflow voor paginabewerking op client-server {#client-server-page-editing-workflow}

Dit is een gedetailleerder overzicht van de interactie tussen client en server bij het bewerken van een SPA.

![Workflow voor het bewerken van clientservers](assets/client-server-editing.png)

1. De SPA initialiseert zichzelf en vraagt het paginamodel aan bij Sling Model Exporter.
1. De verkoper ModelExporter verzoekt om de middelen die de pagina van de bewaarplaats samenstellen.
1. De opslagplaats retourneert de bronnen.
1. De verkoper van het ModelExporter keert het model van de pagina terug.
1. De SPA instantieert zijn componenten die op het paginamodel worden gebaseerd.
1. **6 bis.** De inhoud informeert de editor dat deze gereed is voor ontwerpen.

   **6 ter** De paginaeditor vraagt om configuraties voor componentontwerp.

   **6 quater** De paginaeditor ontvangt de componentconfiguraties.
1. Wanneer de auteur een component bewerkt, wordt in de pagina-editor een wijzigingsverzoek naar de standaard POST servlet gepost.
1. De bron wordt bijgewerkt in de gegevensopslagruimte.
1. De bijgewerkte bron wordt doorgegeven aan het servlet van de POST.
1. De standaard server van de POST deelt de paginaredacteur mee dat het middel is bijgewerkt.
1. De paginaeditor vraagt om het nieuwe paginamodel.
1. De bronnen waaruit de pagina bestaat, worden opgevraagd bij de opslagplaats.
1. De bronnen waaruit de pagina bestaat, worden door de gegevensopslagruimte aan de Verkoopmodel Exporter verschaft.
1. Het bijgewerkte paginamodel wordt geretourneerd aan de editor.
1. De paginaredacteur werkt de verwijzing van het paginamodel van de SPA bij.
1. De SPA werkt zijn componenten bij die op de nieuwe verwijzing van het paginamodel worden gebaseerd.
1. De componentconfiguraties van de paginaeditors worden bijgewerkt.

   **17 bis** De SPA geeft aan dat de inhoud klaar is voor de pagina-editor.

   **17 ter** De paginaredacteur voorziet de SPA van componentenconfiguraties.

   **17 quater** De SPA biedt bijgewerkte componentconfiguraties.

### Ontwerpworkflow {#authoring-workflow}

Dit is een gedetailleerder overzicht dat is toegespitst op de ontwerpervaring.

![SPA ontwerpworkflow](assets/authoring-workflow.png)

1. De SPA haalt het paginamodel op.
1. **2 bis.** Het paginamodel voorziet de redacteur van de gegevens die voor creatie worden vereist.

   **2 ter** Wanneer deze op de hoogte wordt gesteld, werkt de componentbeheerder de inhoudsstructuur van de pagina bij.
1. De componentenbeheerder vraagt de afbeelding tussen een AEM middeltype en een SPA component.
1. De componentorchestrator instantieert dynamisch de SPA component op basis van het paginamodel en de componenttoewijzing.
1. De paginaeditor werkt het paginamodel bij.
1. **6 bis.** Het paginamodel verstrekt bijgewerkte auteursgegevens aan de paginaredacteur.

   **6 ter** Het paginamodel verzendt wijzigingen naar de componentorchestrator.
1. De componentorchestrator haalt de componenttoewijzing op.
1. De componentbeheerder werkt de inhoud van de pagina bij.
1. Wanneer de SPA klaar is met het bijwerken van de inhoud van de pagina, laadt de pagina-editor de ontwerpomgeving.

## Vereisten en beperkingen {#requirements-limitations}

Om de auteur in staat te stellen om de paginaredacteur te gebruiken om de inhoud van een SPA uit te geven, moet uw SPA toepassing worden uitgevoerd om met de AEM SPA Redacteur SDK in wisselwerking te staan. Zie de [Aan de slag met SPA in AEM met Reageren](getting-started-react.md) -document voor minimale informatie die u nodig hebt om die van u te kunnen gebruiken.

### Ondersteunde kaders {#supported-frameworks}

De SPA Editor SDK ondersteunt de volgende minimale versies:

* 16.x en hoger reageren
* Angular 6.x en hoger

Eerdere versies van deze frameworks werken mogelijk met de AEM SPA Editor SDK, maar worden niet ondersteund.

### Aanvullende kaders {#additional-frameworks}

Er kunnen aanvullende SPA worden geïmplementeerd om te werken met de AEM SPA Editor SDK. Zie de [SPA](blueprint.md) document voor de vereisten die een kader moet vervullen om tot een kader-specifieke laag te leiden die uit modules, componenten, en de diensten wordt samengesteld om met de Redacteur van de SPA van de AEM te werken.

### Meerdere kiezers gebruiken {#multiple-selectors}

Aanvullende aangepaste kiezers kunnen worden gedefinieerd en gebruikt als onderdeel van een SPA die is ontwikkeld voor de AEM SPA SDK. Deze ondersteuning vereist echter dat de `model` selector is de eerste kiezer en de extensie is `.json` zoals vereist door de JSON Exporter.

### Vereisten voor teksteditor {#text-editor-requirements}

Als u de op plaats-editor wilt gebruiken van een tekstcomponent die in SPA is gemaakt, is er aanvullende configuratie vereist.

1. Stel een willekeurig kenmerk in op het containerelement dat de tekst HTML bevat. In het geval van het WKND SPA Project, is het een `<div>` element en de kiezer die is gebruikt, `data-rte-editelement`.
1. De configuratie instellen `editElementQuery` op de overeenkomstige AEM tekstcomponent `cq:InplaceEditingConfig` dat bijvoorbeeld naar die kiezer wijst, `data-rte-editelement`. Dit laat de redacteur weten welk element van HTML de HTML tekst verpakt.

Voor meer informatie over de `editElementQuery` eigenschap en de configuratie van de teksteditor met opmaak, raadpleegt u [De Rich Text Editor configureren](/help/implementing/developing/extending/rich-text-editor.md).

### Beperkingen {#limitations}

De AEM SPA Editor SDK wordt volledig ondersteund door Adobe en wordt verder uitgebreid en uitgebreid. De volgende AEM worden nog niet ondersteund door de SPA Editor:

* Doelmodus
* ContextHub
* Inline-afbeeldingen bewerken
* Configs bewerken (bijvoorbeeld listeners)
* Ongedaan maken/Opnieuw
* Pagina diff en Tijd verdraaien
* Functies die HTML herschrijven aan de serverzijde uitvoeren, zoals Koppelingencontrole, CDN-herschrijfservice, URL-verkorting enzovoort.
* Modus Ontwikkelaar
* AEM starten
