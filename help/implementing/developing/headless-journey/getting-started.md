---
title: Aan de slag met AEM Headless als Cloud Service
description: In dit deel van de AEM Headless Developer Journey, leer over AEM Headless eerste vereisten.
hide: true
hidefromtoc: true
index: false
exl-id: a39877d9-f5a1-48f0-a021-cc9849bd8ecb
source-git-commit: 9e06419f25800199dea92b161bc393e6e9670697
workflow-type: tm+mt
source-wordcount: '3073'
ht-degree: 0%

---

# Aan de slag met AEM Headless als een Cloud Service {#getting-started}

>[!CAUTION]
>
>OUTDATED - Deze conceptinhoud is vervangen door de nieuwe [documentatie voor Headless Developer Journey.](/help/journey-headless/developer/overview.md)

In dit deel van [AEM Headless Developer Journey,](overview.md) leert u wat nodig is om uw eigen project met AEM Headless te starten.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [Leer over CMS Headless Development](learn-about.md) leerde u de basistheorie van wat een headless CMS is en u zou nu moeten:

* Begrijp de basisconcepten en de terminologie van de inhoud zonder kop levering
* Begrijpen waarom en wanneer een kop zonder kop nodig is
* Op hoog niveau weten hoe concepten zonder kop worden gebruikt en hoe ze met elkaar verweven zijn

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u AEM kunt gebruiken om een headless oplossing uit te voeren.

## Doelstelling {#objective}

Dit document helpt u AEM Headless in de context van uw eigen project begrijpen. Na het lezen moet u:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te kunnen gebruiken.
* Wees op de hoogte van AEM integratieniveaus zonder kop.
* U kunt uw project definiëren in termen van bereik.

## Basisbeginselen AEM {#aem-basics}

Voordat u een project zonder kop kunt definiëren binnen AEM, is het belangrijk dat u een aantal AEM basisbegrippen begrijpt.

### Instantie van auteur {#author}

Het eenvoudigst bestaat AEM uit een auteur-instantie en een [publish-instantie](#publish) die samenwerken om inhoud te maken, te beheren en te publiceren.

Inhoud begint op de instantie van de auteur. Dit is waar u tevreden auteurs hun inhoud creeert. De auteursomgeving biedt diverse hulpmiddelen voor auteurs aan om hun inhoud tot stand te brengen, te organiseren en opnieuw te gebruiken.

### Exemplaar publiceren {#publish}

Wanneer de inhoud in de auteur is gemaakt, moet deze worden gepubliceerd om beschikbaar te zijn voor andere services. Een publicatie-instantie bevat alle inhoud die is gepubliceerd.

### Replicatie {#replication}

Replicatie is het overbrengen van inhoud van de auteurinstantie naar de publicatie-instantie. Dit gebeurt automatisch AEM wanneer een auteur of andere gebruiker met de juiste rechten inhoud publiceert.

### Overzicht van AEM basisbeginselen {#aem-basics-summary}

Op het eenvoudigste niveau moeten de volgende stappen worden gezet om digitale ervaringen in AEM te creëren:

1. De makers van de inhoud zullen uw inhoud zonder kop maken in de ontwerpinstantie.
1. Wanneer deze inhoud gereed is, wordt deze gerepliceerd naar de publicatie-instantie.
1. API&#39;s kunnen vervolgens worden aangeroepen om deze inhoud op te halen.

AEM headless bouwt van deze technische stichting door krachtige hulpmiddelen aan te bieden om inhoud zonder kop te beheren die [in de volgende sectie wordt beschreven.](#aem-headless-basics)

## Basisprincipes zonder koppen AEM {#aem-headless-basics}

De headless mogelijkheden van AEM zijn gebaseerd op een paar zeer belangrijke eigenschappen. Deze zullen in latere delen van de reis uitvoerig worden toegelicht. Het is nu belangrijk om alleen maar te weten wat ze doen en wat ze noemen.

### Modellen van contentfragmenten {#content-fragment-models}

Met Content Fragment Models wordt de structuur gedefinieerd van de gegevens en inhoud die u in AEM maakt en beheert. Ze dienen als een soort basisstructuur voor je inhoud. Wanneer u ervoor kiest inhoud te maken, selecteren de auteurs een model voor inhoudsfragmenten dat u definieert en dat hen bij het maken van inhoud begeleidt.

### Contentfragmenten {#content-fragments}

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties en via meerdere kanalen.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

### GraphQL- en REST-API&#39;s {#apis}

AEM biedt twee robuuste API&#39;s om uw inhoud zonder problemen te wijzigen.

* Met de GraphQL API kunt u aanvragen maken voor toegang tot en levering van inhoudsfragmenten.
* Met de REST API voor middelen kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

U leert over deze API&#39;s en hoe u deze kunt gebruiken in een later deel van de AEM headless-tocht. Of raadpleeg de sectie [Aanvullende bronnen](#additional-resources) hieronder voor aanvullende documentatie.

## Niveaus voor naadloze integratie {#integration-levels}

AEM ondersteunt zowel de volledige koploze als de traditionele volledige stapel of topmodellen van een CMS. AEM biedt echter niet alleen deze twee exclusieve keuzes, maar ook de mogelijkheid om hybride modellen te ondersteunen die de voordelen van beide combineren en unieke flexibiliteit bieden voor uw project zonder titel.

Om uw begrip van headless concepten te verzekeren, richt deze AEM Headless Ontwikkelaarsreis zich op het zuivere headless model om u zo snel mogelijk aan de slag te krijgen zonder codering in AEM.

U moet echter goed op de hoogte zijn van de extra hybride mogelijkheden die voor u beschikbaar zijn als u AEM functies zonder kop begrijpt. Deze zaken worden hieronder beschreven voor uw aandacht. Aan het eind van de reis zult u aan deze concepten in detail worden geïntroduceerd voor het geval dat zulk flexibiliteit voor uw project wordt vereist.

### U hebt al een externe verbruiker van inhoud zonder kop, zoals één paginatoepassing (SPA). {#already-have-a-spa}

Laten we ervan uitgaan dat uw basisvereiste minimaal is om inhoud te leveren van AEM naar een bestaande externe service.

#### Niveau 1: Integratie van inhoudsfragmenten - traditioneel headless-model {#level-1}

Dit integratieniveau is het traditionele model zonder kop en stelt uw inhoudsauteurs in staat om inhoud in AEM te creëren en het aan om het even welk aantal externe diensten te leveren gebruikend GraphQL of om hen van externe diensten uit te geven gebruikend de activa API. In AEM is geen codering vereist.

In dit model wordt AEM alleen gebruikt voor het maken en leveren van de inhoud via het gebruik van AEM inhoudsfragmenten. Rendering en interactie met de inhoud worden gedelegeerd aan de verbruikende externe toepassing, vaak een toepassing van één pagina (SPA).

#### Niveau 2: De SPA insluiten in AEM - hybride model {#level-2}

Dit integratieniveau bouwt voort op het eerste niveau, maar staat ook toe dat de externe toepassing (SPA) in AEM wordt ingebed zodat de inhoudsauteurs de inhoud in de context van de externe toepassing binnen AEM kunnen bekijken. De toepassing kan ook een beperkte bewerking van de externe toepassing binnen AEM ondersteunen.

Dit niveau heeft het voordeel dat ontwerpers van inhoud inhoud inhoud op een krachtige manier op flexibele wijze inhoud kunnen schrijven, waarbij hun inhoud wordt gepresenteerd in een context met een ingesloten externe SPA, terwijl de inhoud zonder problemen wordt geleverd.

#### Niveau 3: SPA insluiten en volledig inschakelen in AEM - hybride model {#level-3}

Dit integratieniveau bouwt voort op niveau twee door de meeste inhoud in de externe SPA binnen AEM bewerkbaar te maken.

### U hebt nog geen externe consument van de inhoud zonder kop, zoals een toepassing voor één pagina (SPA). {#do-not-have-a-spa}

Als u een nieuwe SPA wilt maken die zonder problemen inhoud van AEM verbruikt, kunt u functies zoals Content Fragments gebruiken om uw inhoud zonder kop te beheren en ook een SPA maken met AEM Editor-framework.

Met behulp van de SPA Editor verbruikt de SPA niet alleen inhoud van AEM, maar is deze ook volledig bewerkbaar binnen AEM van de auteurs van de inhoud, zodat u zowel de mogelijkheid hebt om zonder kop te leveren als in de context te bewerken binnen AEM.

## Vereisten en voorwaarden {#requirements-prerequisites}

Er zijn een aantal vereisten voordat u begint met een project zonder kop AEM.

### Kennis {#knowledge}

* GraphQL
* Ervaring op het gebied van ontwikkeling die SPA maakt met React of Angular
* Basisvaardigheden AEM het creëren van de Fragmenten van de Inhoud en het gebruiken van de redacteur

### Opties {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA of andere verbruiker van uw inhoud zonder kop AEM

## Uw project {#defining-your-project} definiëren

Voor elk succesvol project is het belangrijk niet alleen de eisen van het project duidelijk te definiëren, maar ook de rollen en verantwoordelijkheden.

### Scope {#scope}

Het is van groot belang dat er een duidelijk afgebakend toepassingsgebied voor het project is. Het bereik bevat acceptatiecriteria en u kunt een definitie van &#39;gedaan&#39; vaststellen.

De eerste vraag die je jezelf moet stellen is: &quot;Wat probeer ik te bereiken met AEM Headless?&quot; Het antwoord moet in het algemeen zijn dat u een ervaringstoepassing hebt of zult hebben die u met uw eigen ontwikkelingsprogramma&#39;s hebt gebouwd, niet in combinatie met AEM. Deze ervaringstoepassing kan een mobiele app, een website of een andere eindgebruiker zijn die een ervaringstoepassing moet gebruiken. Het doel om AEM Headless te gebruiken is uw ervaringstoepassing van inhoud te voorzien die wordt gecreeerd, opgeslagen, en beheerd AEM met geavanceerde APIs die AEM Headless zouden roepen om inhoud of zelfs volledig CRUD inhoud rechtstreeks van uw ervaringstoepassing te halen. Als u dit niet wilt doen, wilt u waarschijnlijk [terug naar de AEM documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) en de sectie vinden die beter past wat u wilt verwezenlijken.

### Rollen en verantwoordelijkheden {#roles-responsibilities}

De rollen voor om het even welk individueel project zullen variëren, maar belangrijke die in de inhoud van AEM hoofdloze ontwikkeling moeten overwegen zijn:

* [Beheerder](#administrator)
* [Inhoudsauteur](#content-author)
* [Content Modeler](#content-modeler)
* [Developer](#developer)

#### Beheerder {#administrator}

De beheerder is verantwoordelijk voor de basisopstelling en configuratie van uw systeem. De beheerder zal bijvoorbeeld uw organisatie instellen binnen het Adobe-gebruikersbeheersysteem, waarnaar wordt verwezen met Identity Management System (IMS). De beheerder zal de eerste gebruiker van de organisatie zijn om een e-mailuitnodiging van Adobe te ontvangen zodra uw organisatie door Adobe binnen IMS is gecreeerd. De beheerder kan zich aanmelden bij IMS en gebruikers van andere personen toevoegen.

Zodra de gebruikers door de beheerder worden gevormd, zullen zij de toestemmingen worden verleend om tot alle AEM middelen toegang te hebben om hun werk als contribuanten te verwezenlijken om de ervaringstoepassing te leveren die AEM Headless gebruikt.

De beheerder zou de gebruiker moeten zijn die opstelling AEM en de runtime milieu voorbereidt om [inhoudsauteurs ](#content-author) toe te laten om inhoud tot stand te brengen en bij te werken en [ontwikkelaars](#developer) om APIs te gebruiken die of inhoud voor hun ervaringstoepassingen halen wijzigen.

#### Inhoudsauteur {#content-author}

Inhoudsauteurs maken en beheren de inhoud die zonder kop door AEM wordt geleverd. Inhoudsauteurs gebruiken AEM functies zoals Inhoudsfragmenten en de Console Elementen om de inhoud ervan te beheren.

Inhoudsauteurs dienen de volgende aanbevolen procedures in acht te nemen.

#### Plan voor lokalisatie {#localization}

Plan voor vertaling en localisatie bij het allereerste begin van het project. &quot;Projectmanager voor internationalisering&quot; beschouwen als een afzonderlijke persoon die tot taak heeft te bepalen welke inhoud moet worden vertaald en wat niet, en welke vertaalde inhoud kan worden gewijzigd door regionale of lokale inhoudproducenten.

Maak een plan voor de lokalisatie van de inhoud die u nodig hebt.

* Hebt u alleen maar verschillende talen of ook taal nodig om zich aan te passen aan regionale bijzonderheden?
* Hebt u rijke media-inhoud zoals afbeeldingen of video&#39;s nodig om voor verschillende landinstellingen te kunnen verschillen?

Wis over de workflow voor het bijwerken van inhoud. Wat is het goedkeuringsproces dat het systeem moet ondersteunen? Kunnen AEM workflows worden gebruikt om dit proces te automatiseren?

Houd er rekening mee dat uw [inhoudshiërarchie](#content-hierarchy) kan worden gebruikt om lokalisatie te vereenvoudigen.

Zie de sectie [Aanvullende bronnen](#additional-resources) voor aanvullende documentatie over AEM workflows en lokalisatiehulpmiddelen.

##### Gebruikmaken van de inhoudshiërarchie {#content-hierarchy}

De maphiërarchie kan twee belangrijke problemen met betrekking tot inhoudsbeheer aanpakken:

* [Lokalisatie](#localization)  - AEM beheert de lokalisatie van inhoud door kopieën van inhoud in landspecifieke mappen te onderhouden.
* Organisatie - Mappen worden gebruikt om een inhoudshiërarchie te definiëren die nodig is om lokalisatiebehoeften te ondersteunen en om inhoudsfragmenten logisch te beheren.

AEM biedt een zeer flexibele inhoudsstructuur en een hiërarchie kan willekeurig groot zijn. Het is echter belangrijk om te beseffen dat wijzigingen in de mapstructuur ongewenste gevolgen kunnen hebben voor bestaande query&#39;s die [afhankelijk zijn van het inhoudspad.](#developer) Daarom kan een duidelijk gedefinieerde hiërarchie die vooraf duidelijk wordt uiteengezet, bijzonder nuttig zijn voor de auteurs van de inhoud.

Mappen kunnen ook worden beperkt tot bepaalde typen inhoud (op basis van modellen van inhoudsfragmenten). Over het algemeen wordt aanbevolen altijd expliciet op te geven welke modellen zijn toegestaan voor alle mappen in de hiërarchie. Toegestane inhoud opgeven voor een bepaalde map:

* Voorkomt dat inhoudsauteurs inhoud ontwerpen die niet in de map thuishoort.
* Optimaliseert het proces voor het maken van inhoud door de typen inhoud te filteren die tijdens het maken in de map zijn toegestaan, zodat alleen geldige typen inhoud worden weergegeven.

Door een geschikte inhoudsstructuur te maken, wordt het eenvoudiger om het schrijven van inhoud zonder kop tussen kanalen te coördineren om het hergebruik van inhoud te maximaliseren. Het gebruik van inhoud via meerdere kanalen zal de efficiëntie van de inhoudsproductie en het wijzigingsbeheer aanzienlijk verbeteren.

##### Goede naamgevingsconventies vaststellen {#naming-conventions}

Namen van inhoudsfragmenten moeten beschrijvend zijn voor inhoudsauteurs. AEM behandelt transparant het ontsnapen en/of het beknotten van de namen gebruikte IDs op het bewaarplaatniveau. Daarom moeten de logische namen die door de auteurs van de inhoud worden verstrekt altijd leesbaar zijn en de inhoud vertegenwoordigen.

* Ongeldige naam: `cta_btn_1`
* Goede naam: `Call To Action Button`

Zie de sectie [Aanvullende bronnen](#additional-resources) voor aanvullende documentatie over AEM conventies voor paginanamen.

##### Inhoud nesten {#content-nesting} niet te veel uitbreiden

[Inhoud ](#content-fragments) fragmenteert wordt gebruikt in AEM om inhoud zonder kop te maken. AEM ondersteunt tot tien niveaus voor het nesten van inhoud voor Content Fragments. Het is echter belangrijk om in gedachten te houden dat AEM elke verwijzing die in het bovenliggende inhoudsfragment is gedefinieerd, herhaaldelijk moet oplossen en vervolgens moet controleren of er onderliggende verwijzingen voorkomen op alle locaties op hetzelfde niveau. Deze bewerkingen kunnen snel worden uitgevoerd en zorgen voor de prestaties.

Als algemene regel van-duim, zouden de verwijzingen van het Fragment van de Inhoud niet voorbij vijf niveaus moeten worden genesteld.

#### Content Modeler {#content-modeler}

Inhoudsmodellen analyseren de vereisten voor de gegevens die zonder kop moeten worden geleverd en definiëren de structuur voor deze gegevens. Deze structuren worden [Content Fragment Models](#content-fragment-models) in AEM genoemd. Modellen van inhoudsfragmenten worden gebruikt als basis voor de inhoudsfragmenten die de auteurs van de inhoud maken.

Een handige methode bij het definiëren van modellen van inhoudsfragmenten is het maken van modellen die zijn toegewezen aan de UX-componenten van de toepassing(en) die de inhoud zullen gebruiken.

Omdat de makers van de inhoud voortdurend met de modellen werken terwijl ze nieuwe inhoud maken, kunnen ze de resulterende digitale ervaring visualiseren door de modellen op de UX uit te lijnen. Als u deze uitlijning verder uitlijnt, kunt u pictogrammen toewijzen aan de modellen van inhoudsfragmenten die het UX-element vertegenwoordigen, zodat de auteurs op intuïtieve wijze het juiste model kunnen selecteren op basis van visuele aanwijzingen.

#### Ontwikkelaar {#developer}

Ontwikkelaars zijn verantwoordelijk voor het samenvoegen van de inhoud die wordt gemaakt zonder enig AEM voor de consument van die inhoud. Dit kan vaak een toepassing van één pagina (SPA), een progressieve webapp (PWA), een webshop of een andere service buiten AEM zijn.

GraphQL fungeert als de &quot;lijm&quot; tussen AEM en de consumenten van inhoud zonder kop. GraphQL is de taal die voor de noodzakelijke inhoud AEM vragen.

De ontwikkelaars zouden een paar basisaanbevelingen in mening moeten houden aangezien zij hun vragen plannen:

* De vragen zouden niet op een vaste weg (`ByPath`) moeten vertrouwen om de Fragmenten van de Inhoud terug te winnen.
   * [Inhoudsauteurs hebben volledige controle over de ](#content-hierarchy) hiërarchie van inhoudsfragmenten en kunnen wijzigingen aanbrengen die een dergelijke query zouden verbreken.
   * De vragen zouden in plaats daarvan voor de modelverwijzingen van het inhoudsfragment met dynamische vraagparameters moeten kiezen om de resultaten te filtreren om de gewenste nuttige lading te produceren.
* Voor beste vraagprestaties, gebruik altijd voortgeduurde vragen in AEM. Deze worden later op de reis besproken.
* GraphQL is ontworpen om declaratief te zijn na het motto &quot;Vraag om precies wat u nodig hebt, en krijg precies dat.&quot; Dit betekent dat wanneer het creëren van vragen GraphQL, altijd `select *`-type vragen vermijdt die u in een relationele gegevensbestand zou kunnen creëren.

Voor een [typische implementatie zonder kop die AEM gebruikt,](#level-1) vereist de ontwikkelaar geen coderingskennis van AEM.

### Prestatievereisten {#performance-requirements}

Om een project tot een succes te maken, moeten de prestaties worden overwogen alvorens om het even welke inhoud wordt gecreeerd.

U moet uw gebruikers/bezoekers verwachtingen en ontwerp voor hen begrijpen. Plaats de doelstellingen van het de dienstniveau (SLOs) en meet hen om te begrijpen als u aan de verwachtingen van uw gebruiker voldoet.

#### Verkeerspatronen {#traffic-patterns}

Om verkeer en verkeerspatronen te begrijpen begin met het verzamelen van wat u van het verleden en dan project aan de verwachte groei in de komende jaren kent. Enkele van de belangrijkste te overwegen variabelen:

* Hoeveel API vraag per uur/dag/maand verwacht u en is er potentieel voor pieken en seizoensgebondenheid?
* Hoeveel verschillende inhoudsauteurs zijn er?
* Hoeveel inhoudsauteurs verwacht u gelijktijdig te werken?
* Hoe vaak wordt de inhoud bijgewerkt?
* Hoeveel inhoudsmodellen zijn nodig?
* Hoeveel exemplaren van modellen zullen nodig zijn?

#### Frequentie {#update-frequency} bijwerken

Vaak hebben verschillende secties van ervaringen verschillende frequenties van inhoudsupdates. Het begrip van dit is belangrijk om CDN en geheim voorgeheugenconfiguraties te kunnen verfijnen. Dit is ook belangrijke input voor [Content Modelers](#content-modeler) aangezien zij modellen ontwerpen om uw inhoud te vertegenwoordigen. Overweeg:

* Moeten bepaalde soorten inhoud na een bepaalde periode verlopen?
* Zijn er elementen die user-specific zijn en zo kunnen niet in het voorgeheugen ondergebracht worden?

## Volgende {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te kunnen gebruiken.
* Wees op de hoogte van AEM integratieniveaus zonder kop.
* U kunt uw project definiëren in termen van bereik.

U zou uw AEM onophoudelijke reis moeten voortzetten door het document [Weg aan Uw Eerste Ervaring te herzien Gebruikend AEM Headless](path-to-first-experience.md) waar u zult leren hoe te opstelling de noodzakelijke hulpmiddelen en hoe te beginnen te denken over het modelleren van uw gegevens in AEM.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd om op het volgende deel van de headless ontwikkelingsreis over te gaan door het document [Weg aan Uw Eerste Ervaring te herzien Gebruikend AEM Headless,](path-to-first-experience.md) zijn het volgende enkele extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* [Inleiding tot de Architectuur van Adobe Experience Manager als Cloud Service](/help/core-concepts/architecture.md)  - Begrijp AEM als structuur van een Cloud Service
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)  zonder kop - Gebruik deze praktische zelfstudies om te bekijken hoe u de verschillende opties kunt gebruiken om inhoud aan eindpunten zonder kop met AEM te leveren en te kiezen wat bij u past.
* [Koploos inhoudsbeheer met GraphQL APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  - Volg deze cursus voor een overzicht van de GraphQL API die in AEM wordt uitgevoerd. Verificatie via AdobeID is vereist.
* [AEM Gidsen WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Dit project GitHub omvat voorbeeldtoepassingen die AEM GraphQL APIs benadrukken.
* [Concepten](/help/sites-cloud/authoring/getting-started/concepts.md)  ontwerpen - Technische documentatie voor de ontwerpomgeving van AEM, inclusief informatie over de instelling voor publicatie door de auteur
* [Pagina&#39;s](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  publiceren - Technische documentatie voor het publiceren van inhoud op AEM
* [Naamgevingsconventies](/help/implementing/developing/introduction/naming-conventions.md)  - Technische documentatie van naamgevingsbeperkingen voor pagina&#39;s in AEM
* [Beheer en vertaling](/help/sites-cloud/administering/msm-and-translation.md)  van meerdere sites - Technische documentatie over AEM krachtige vertaalfuncties
* [AEM workflows](/help/sites-cloud/authoring/workflows/overview.md)  - Technische documentatie over het automatiseren van workflows in AEM
* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)  - Technische documentatie voor inhoudsfragmenten.
* [Modellen](/help/assets/content-fragments/content-fragments-models.md)  voor inhoudsfragmenten - Technische documentatie voor modellen van inhoudsfragmenten.
* [GraphQL Technische Documentatie](https://graphql.org)  - de definitie GraphQL (externe verbinding)
* [GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Technische documentatie die verklaart hoe te om verzoeken tot toegang te creëren en tevreden Fragments te leveren
* [Assets REST API](/help/assets/content-fragments/assets-api-content-fragments.md)  - Technische documentatie die verklaart hoe te om tot Inhoudsfragmenten (en andere activa) te leiden en te wijzigen
* [Gestelde Vragen](/help/assets/content-fragments/graphql-api-content-fragments.md#persisted-queries-caching)  - Technische documentatie over gepresteerde vragen in AEM
* [Zwaarlijk en zonder kop in AEM](/help/implementing/developing/headful-headless.md)  - Een volledige discussie over de niveaus van de ontelbare integratie die beschikbaar zijn in AEM
