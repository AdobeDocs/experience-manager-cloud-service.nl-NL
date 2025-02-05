---
title: Aan de slag met AEM headless as a Cloud Service
description: In dit deel van de AEM Headless Developer Journey, leer over AEM Headless eerste vereisten.
exl-id: 9661e17b-fa9f-4689-900c-412b068e942c
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '3068'
ht-degree: 0%

---

# Aan de slag met AEM headless as a Cloud Service {#getting-started}

In dit deel van de [ AEM Zwaardeloze Reis van de Ontwikkelaar ](overview.md), leer over wat wordt vereist om uw eigen project te krijgen begonnen met AEM Zwaartepunt.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze reis, [ Leer over de Hoofdloze Ontwikkeling van CMS ](learn-about.md) u de basistheorie van leerde wat een headless CMS is en u zou nu moeten:

* Begrijp de basisconcepten en de terminologie van de inhoud zonder kop levering
* Begrijpen waarom en wanneer een kop zonder kop nodig is
* Op hoog niveau weten hoe concepten zonder kop worden gebruikt en hoe ze met elkaar verweven zijn

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u AEM kunt gebruiken om een headless oplossing uit te voeren.

## Doelstelling {#objective}

Dit document helpt u AEM Headless in de context van uw eigen project begrijpen. Na het lezen moet u:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te kunnen gebruiken.
* Wees op de hoogte van AEM instorting van het integratieniveau zonder kop.
* U kunt uw project definiëren in termen van bereik.

## AEM {#aem-basics}

Voordat u een project zonder kop kunt definiëren binnen AEM, is het belangrijk dat u een aantal AEM basisbegrippen begrijpt.

### Instantie van auteur {#author}

Bij zijn eenvoudigst, bestaat AEM uit een auteursinstantie en a [ publiceer instantie ](#publish) die samenwerken om, uw inhoud tot stand te brengen te beheren en te publiceren.

Inhoud begint op de instantie van de auteur. Op deze manier maken auteurs van inhoud hun inhoud. De auteursomgeving biedt diverse hulpmiddelen voor auteurs aan om hun inhoud tot stand te brengen, te organiseren en opnieuw te gebruiken.

### Publish Instance {#publish}

Wanneer de inhoud in de auteurinstantie is gemaakt, moet deze worden gepubliceerd om beschikbaar te zijn voor andere services. Een publicatie-instantie bevat alle inhoud die is gepubliceerd.

### Voorvertoningsservice {#preview}

Voorafgaand aan het publiceren aan de instantie van Publish kunt u uw Fragment van de Inhoud aan de **Dienst van de Voorproef** voor het testen en het herzien ook publiceren. Dit wordt gedaan van de **console van de Fragmenten van de Inhoud**.

### Replicatie {#replication}

Replicatie is het overbrengen van inhoud van de auteurinstantie naar de publicatie-instantie. Dit gebeurt automatisch AEM wanneer een auteur of andere gebruiker met de juiste rechten inhoud publiceert.

### Overzicht AEM basisbeginselen {#aem-basics-summary}

Op het eenvoudigste niveau moeten de volgende stappen worden gezet om digitale ervaringen in AEM te creëren:

1. De auteurs van de inhoud maken inhoud zonder kop in de ontwerpinstantie.
1. Wanneer deze inhoud gereed is, wordt deze gerepliceerd naar de publicatie-instantie.
1. API&#39;s kunnen vervolgens worden aangeroepen om deze inhoud op te halen.

AEM Headless bouwt van deze technische stichting door krachtige hulpmiddelen aan te bieden om hoofdloze inhoud te beheren die [ in de volgende sectie ](#aem-headless-basics) wordt beschreven.

## Grondbeginselen AEM {#aem-headless-basics}

De headless mogelijkheden van AEM zijn gebaseerd op een paar zeer belangrijke eigenschappen. Deze worden in latere delen van de reis uitgebreid toegelicht. Het is nu belangrijk om alleen maar te weten wat ze doen en wat ze noemen.

### Modellen van inhoudsfragmenten {#content-fragment-models}

Met Content Fragment Models wordt de structuur gedefinieerd van de gegevens en inhoud die u maakt en beheert in AEM. Ze dienen als een soort basisstructuur voor je inhoud. Wanneer u ervoor kiest inhoud te maken, selecteren de auteurs een van de door u gedefinieerde modellen van inhoudsfragmenten die u als hulplijnen bij het maken van inhoud gebruikt.

### Inhoudsfragmenten {#content-fragments}

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties en via meerdere kanalen.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

### GraphQL- en REST-API&#39;s {#apis}

AEM biedt twee robuuste API&#39;s om uw inhoud zonder problemen aan te passen.

* Met de GraphQL API kunt u aanvragen maken voor toegang tot en levering van inhoudsfragmenten.
* Met de Assets REST API kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

U leert over deze API&#39;s en hoe u ze kunt gebruiken in een later deel van de AEM tocht zonder kop. Of, zie [ extra middelen ](#additional-resources) hieronder sectie voor meer documentatie.

## Niveaus voor toploze integratie {#integration-levels}

AEM ondersteunt zowel de volledige koploze als de traditionele volledige stapel of topmodellen van een CMS. AEM biedt echter niet alleen deze twee exclusieve keuzes, maar ook de mogelijkheid om hybride modellen te ondersteunen die de voordelen van beide combineren en unieke flexibiliteit bieden voor uw project zonder titel.

Om uw begrip van headless concepten te verzekeren, richt deze AEM Headless Ontwikkelaarsreis zich op het zuivere headless model om u aan de slag te krijgen zo spoedig mogelijk zonder codering in AEM.

U moet echter goed op de hoogte zijn van de extra hybride mogelijkheden die voor u beschikbaar zijn als u eenmaal de AEM functies zonder kop hebt begrepen. Deze gevallen worden hieronder beschreven voor uw bewustzijn. Aan het eind van de reis, wordt u geïntroduceerd aan deze concepten in detail voor het geval dat zulk flexibiliteit voor uw project wordt vereist.

### U hebt al een externe verbruiker van inhoud zonder kop, zoals een toepassing van één pagina (SPA). {#already-have-a-spa}

Laten we ervan uitgaan dat uw basisvereiste minimaal is om inhoud te leveren van AEM naar een bestaande externe service.

#### Niveau 1: integratie van inhoudsfragmenten - traditioneel headless-model {#level-1}

Dit integratieniveau is het traditionele model zonder kop en stelt uw inhoudsauteurs in staat om inhoud in AEM te maken en deze zonder dralen te leveren aan een aantal externe services met behulp van GraphQL of om deze te bewerken van externe services met behulp van de Assets API. In AEM is geen codering vereist.

In dit model wordt AEM alleen gebruikt voor het maken en serveren van de inhoud met behulp van AEM Content Fragments. Rendering en interactie met de inhoud worden gedelegeerd aan de verbruikende externe toepassing, vaak een toepassing van één pagina (SPA).

#### Niveau 2: sluit de SPA in AEM in - hybride model {#level-2}

Dit integratieniveau bouwt voort op het eerste niveau, maar staat ook toe dat de externe toepassing (SPA) in AEM wordt ingebed zodat de inhoudsauteurs de inhoud in de context van de externe toepassing binnen AEM kunnen bekijken. De toepassing kan ook een beperkte bewerking van de externe toepassing binnen AEM ondersteunen.

Dit niveau heeft het voordeel dat ontwerpers van inhoud inhoud inhoud op een krachtige manier op flexibele wijze inhoud kunnen schrijven, waarbij hun inhoud wordt gepresenteerd in een context met een ingesloten externe SPA, terwijl de inhoud zonder problemen wordt geleverd.

#### Niveau 3: SPA insluiten en volledig inschakelen in AEM - hybride model {#level-3}

Dit integratieniveau bouwt voort op niveau twee door de meeste inhoud in de externe SPA binnen AEM bewerkbaar te maken.

### U hebt nog geen externe consument van de inhoud zonder kop, zoals een toepassing voor één pagina (SPA). {#do-not-have-a-spa}

Als u een SPA wilt maken die zonder problemen inhoud van AEM verbruikt, kunt u functies zoals Content Fragments gebruiken om uw inhoud zonder kop te beheren en ook een SPA maken met AEM SPA Editor-framework.

Met behulp van de SPA Editor verbruikt de SPA niet alleen inhoud van AEM, maar is deze ook volledig bewerkbaar binnen AEM van de auteurs van de inhoud, zodat u zowel de mogelijkheid hebt om zonder kop te leveren als in de context te bewerken binnen AEM.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verscheidene vereisten alvorens u met uw hoofd AEM project begint.

### Kennis {#knowledge}

* GraphQL
* Ervaring op het gebied van ontwikkeling die SPA maakt met React of Angular
* Basisvaardigheden AEM het creëren van de Fragmenten van de Inhoud en het gebruiken van de redacteur

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA of andere verbruiker van uw inhoud zonder kop AEM

## Uw project definiëren {#defining-your-project}

Voor elk succesvol project is het belangrijk niet alleen de eisen van het project duidelijk te definiëren, maar ook de rollen en verantwoordelijkheden.

### Scope {#scope}

Het is belangrijk dat er een duidelijk afgebakende draagwijdte voor het project is. Het bereik bevat acceptatiecriteria en u kunt een definitie van &#39;gedaan&#39; vaststellen.

De eerste vraag die je moet stellen is: &quot;Wat probeer ik te bereiken met AEM Headless?&quot; Het antwoord moet in het algemeen zijn dat u een ervaringstoepassing hebt of in de toekomst zult hebben die u met uw eigen ontwikkelingshulpmiddelen niet met AEM hebt gebouwd. Deze ervaringstoepassing kan een mobiele app, een website of een andere eindgebruiker zijn die een ervaringstoepassing moet gebruiken. Het doel om AEM Headless te gebruiken is uw ervaringstoepassing van inhoud te voorzien die wordt gecreeerd, opgeslagen, en beheerd AEM met geavanceerde APIs die AEM Headless zouden roepen om inhoud of zelfs volledig CRUD inhoud rechtstreeks van uw ervaringstoepassing te halen. Als dit niet is wat u wilt doen, wilt u waarschijnlijk [ terug naar de AEM documentatie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) gaan en de sectie vinden die beter past wat u wilt verwezenlijken.

### Rollen en verantwoordelijkheden {#roles-responsibilities}

De rollen voor om het even welk individueel project variëren, maar belangrijke die in de inhoud van AEM hoofdloze ontwikkeling moeten overwegen zijn:

* [Beheerder](#administrator)
* [Inhoudsauteur](#content-author)
* [Content Architect](#content-architect)
* [Developer](#developer)

#### Beheerder {#administrator}

De beheerder is verantwoordelijk voor de basisopstelling en configuratie van uw systeem. Bijvoorbeeld, plaatst de beheerder opstelling uw organisatie binnen het systeem van het de gebruikersbeheer van de Adobe, die naar het Systeem van Identity Management (IMS) wordt verwezen. De beheerder is de eerste gebruiker van de organisatie die een e-mailuitnodiging van de Adobe ontvangt zodra uw organisatie door Adobe binnen IMS is gecreeerd. De beheerder kan zich aanmelden bij IMS en gebruikers van andere personen toevoegen.

Zodra de gebruikers door de beheerder worden gevormd, worden zij verleend de toestemmingen om tot alle AEM middelen toegang te hebben om hun werk als contribuanten te verwezenlijken om de ervaringstoepassing te leveren die AEM Headless gebruikt.

De beheerder zou de gebruiker moeten zijn die opstelling AEM en het runtime milieu voorbereidt om [ inhoudsauteurs ](#content-author) toe te laten om inhoud tot stand te brengen en bij te werken en [ ontwikkelaars ](#developer) om APIs te gebruiken die inhoud voor hun ervaringstoepassingen halen of wijzigen.

#### Inhoudsauteur {#content-author}

Inhoudsauteurs maken en beheren de inhoud die zonder kop door AEM wordt geleverd. Auteurs van inhoud gebruiken AEM functies zoals de editor voor inhoudsfragmenten en diverse consoles om de inhoud ervan te beheren.

Inhoudsauteurs dienen de volgende aanbevolen procedures in acht te nemen.

#### Plan voor vertaling {#translation}

Plan voor vertaling aan het begin van het project. U kunt &quot;Translation Specialist&quot; beschouwen als een afzonderlijke persoon die tot taak heeft te bepalen welke inhoud moet worden vertaald en wat niet, en welke vertaalde inhoud door regionale of lokale inhoudproducenten kan worden gewijzigd.

Maak een plan voor wat u nodig hebt voor het vertalen van inhoud.

* Hebt u verschillende talen of ook taal nodig om zich aan te passen aan regionale bijzonderheden?
* Hebt u rijke media-inhoud zoals afbeeldingen of video&#39;s nodig om voor verschillende landinstellingen te kunnen verschillen?

Wis over uw workflow voor het bijwerken van inhoud. Wat is het goedkeuringsproces dat het systeem moet ondersteunen? Kunnen AEM workflows worden gebruikt om dit proces te automatiseren?

Uw [ inhoudshiërarchie ](#content-hierarchy) kan worden gebruikt om vertaling gemakkelijker te maken.

Zie de [ extra middelen ](#additional-resources) sectie voor extra documentatie over AEM werkschema&#39;s en vertaalhulpmiddelen met inbegrip van verbindingen aan de AEM Dagloze Vertaal.

##### Gebruikmaken van de inhoudshiërarchie {#content-hierarchy}

Maphiërarchie kan twee belangrijke problemen met betrekking tot inhoudsbeheer aanpakken:

* [ Vertaling ](#translation) - AEM beheert vertaling van inhoud door exemplaren van inhoud in scènespecifieke omslagen te handhaven.
* Organisatie - Mappen worden gebruikt om een inhoudshiërarchie te bepalen die wordt vereist om vertaalbehoeften te steunen en logisch inhoudsfragmenten te beheren.

AEM maakt een flexibele inhoudsstructuur mogelijk en een hiërarchie kan willekeurig groot zijn. Nochtans is het belangrijk om zich te realiseren dat om het even welke veranderingen in omslagstructuur onbedoelde gevolgen voor bestaande vragen kan hebben die [ op de inhoudspad ](#developer) baseren. Daarom kan een duidelijk gedefinieerde hiërarchie die vooraf duidelijk is ingesteld, nuttig zijn voor de auteurs van de inhoud.

Mappen kunnen ook worden beperkt tot bepaalde typen inhoud (op basis van modellen van inhoudsfragmenten). Het wordt aanbevolen altijd expliciet op te geven welke modellen zijn toegestaan voor alle mappen in de hiërarchie. Toegestane inhoud opgeven voor een bepaalde map:

* Voorkomt dat inhoudsauteurs inhoud ontwerpen die niet in de map thuishoort.
* Optimaliseert het proces voor het maken van inhoud door de typen inhoud te filteren die tijdens het maken in de map zijn toegestaan, zodat alleen geldige typen inhoud worden weergegeven.

Door een geschikte inhoudsstructuur te maken, wordt het eenvoudiger om het schrijven van inhoud zonder kop tussen kanalen te coördineren, zodat u de inhoud optimaal kunt gebruiken. De hefboomwerking van inhoud over veelvoudige kanalen verbetert zeer inhoudsproductie efficiency en veranderingsbeheer.

##### Goede naamgevingsconventies tot stand brengen {#naming-conventions}

Namen van inhoudsfragmenten moeten beschrijvend zijn voor inhoudsauteurs. AEM behandelt transparant het ontsnapen en/of het beknotten van de namen gebruikte IDs op het bewaarplaatniveau. Daarom moeten de logische namen die door de auteurs van de inhoud worden verstrekt altijd leesbaar zijn en de inhoud vertegenwoordigen.

* Ongeldige naam: `cta_btn_1`
* Goede naam: `Call To Action Button`

Zie de [ extra middelen ](#additional-resources) sectie voor extra documentatie over AEM pagina noemende overeenkomsten.

##### Inhoud niet te veel nesten {#content-nesting}

[ de Fragmenten van de Inhoud ](#content-fragments) worden gebruikt in AEM om koploze inhoud tot stand te brengen. AEM ondersteunt tot tien niveaus voor het nesten van inhoud voor Content Fragments. Het is echter belangrijk om in gedachten te houden dat AEM elke verwijzing die in het bovenliggende inhoudsfragment is gedefinieerd, moet oplossen en vervolgens moet controleren of er onderliggende verwijzingen voorkomen op alle locaties op hetzelfde niveau. Deze bewerkingen kunnen snel worden uitgevoerd en zorgen voor de prestaties.

Als algemene regel van-duim, zouden de verwijzingen van het Fragment van de Inhoud niet voorbij vijf niveaus moeten worden genesteld.

#### Content Architect {#content-architect}

Inhoudsarchitecten analyseren de vereisten voor de gegevens die zonder kop moeten worden geleverd en definiëren de structuur voor deze gegevens. Deze structuren worden genoemd [ Modellen van het Fragment van de Inhoud ](#content-fragment-models) in AEM. Modellen van inhoudsfragmenten worden gebruikt als basis voor de inhoudsfragmenten die de auteurs van de inhoud maken.

Een handige methode bij het definiëren van modellen van inhoudsfragmenten is het maken van modellen die zijn toegewezen aan de UX-componenten van de toepassingen die de inhoud gebruiken.

Omdat de makers van de inhoud voortdurend met de modellen werken terwijl ze nieuwe inhoud maken, kunnen ze de resulterende digitale ervaring visualiseren door de modellen op de UX uit te lijnen. Als u deze uitlijning verder uitlijnt, kunt u pictogrammen toewijzen aan de modellen van inhoudsfragmenten die het UX-element vertegenwoordigen, zodat de auteurs op intuïtieve wijze het juiste model kunnen selecteren op basis van visuele aanwijzingen.

#### Developer {#developer}

Ontwikkelaars zijn verantwoordelijk voor het samenvoegen van de inhoud die wordt gemaakt zonder enig AEM voor de consument van die inhoud. Dit kan vaak een toepassing van één pagina (SPA), een progressieve webapp (PWA), een webshop of een andere service buiten AEM zijn.

GraphQL fungeert als de &quot;lijm&quot; tussen AEM en de consument van inhoud zonder kop. GraphQL is de taal die AEM zoekt naar de benodigde inhoud.

De ontwikkelaars zouden een paar basisaanbevelingen in mening moeten houden aangezien zij hun vragen plannen:

* De vragen zouden niet op een vaste weg (`ByPath`) moeten vertrouwen om de Fragmenten van de Inhoud terug te winnen.
   * [ de auteurs van de Inhoud hebben volledige controle over de hiërarchie van het inhoudsfragment ](#content-hierarchy) en konden veranderingen aanbrengen die zulk een vraag zouden breken.
   * De vragen zouden in plaats daarvan voor de modelverwijzingen van het inhoudsfragment met dynamische vraagparameters moeten kiezen om de resultaten te filtreren om de gewenste nuttige lading te produceren.
* Voor beste vraagprestaties, gebruik altijd voortgeduurde vragen in AEM. Deze worden later op de reis besproken.
* GraphQL is declaratief na het motto &quot;Vraag precies wat u nodig hebt, en krijg precies dat.&quot; Dit betekent dat u bij het maken van GraphQL-query&#39;s altijd query&#39;s van het type `select *` vermijdt die u in een relationele database kunt maken.

Voor a [ typische hoofdloze implementatie gebruikend AEM ](#level-1), vereist de ontwikkelaar geen codeerkennis van AEM.

### Prestatievereisten {#performance-requirements}

Om een project tot een succes te maken, moeten de prestaties worden overwogen alvorens om het even welke inhoud wordt gecreeerd.

U moet uw gebruikers/bezoekers verwachtingen en ontwerp voor hen begrijpen. Plaats de doelstellingen van het de dienstniveau (SLOs) en meet hen om te begrijpen als u aan de verwachtingen van uw gebruiker voldoet.

#### Verkeerspatronen {#traffic-patterns}

Om verkeer en verkeerspatronen te begrijpen begin met het verzamelen van wat u van het verleden en dan project aan de verwachte groei in de komende jaren kent. Enkele van de belangrijkste te overwegen variabelen:

* Hoeveel API vraag per uur/dag/maand verwacht u en is er potentieel voor pieken en seizoensgebondenheid?
* Hoeveel verschillende inhoudsauteurs zijn er?
* Hoeveel auteurs van inhoud verwacht u gelijktijdig te werken?
* Hoe vaak wordt de inhoud bijgewerkt?
* Hoeveel inhoudsmodellen zijn nodig?
* Hoeveel exemplaren van modellen zijn nodig?

#### Frequentie bijwerken {#update-frequency}

Vaak hebben verschillende secties van ervaringen verschillende frequenties van inhoudsupdates. Het begrip van dit is belangrijk om CDN en geheim voorgeheugenconfiguraties te kunnen verfijnen. Dit is ook belangrijke input voor de [ Architecten van de Inhoud ](#content-architects) aangezien zij modellen ontwerpen om uw inhoud te vertegenwoordigen. Overweeg:

* Moeten bepaalde soorten inhoud na een bepaalde periode verlopen?
* Zijn er elementen die gebruikersspecifiek zijn en daarom niet in het voorgeheugen kunnen worden opgeslagen?

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te kunnen gebruiken.
* Wees op de hoogte van AEM instorting van het integratieniveau zonder kop.
* U kunt uw project definiëren in termen van bereik.

U zou uw AEM hoofdloze reis door het document [ Weg aan Uw Eerste Ervaring moeten voortzetten Gebruikend AEM Koploze ](path-to-first-experience.md) waar u leert hoe te opstelling de noodzakelijke hulpmiddelen en hoe te beginnen denken over het modelleren van uw gegevens in AEM.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de headless ontwikkelingstraject door het document [ Weg aan Uw Eerste Ervaring te herzien Gebruikend AEM Koploze ](path-to-first-experience.md) beweegt, zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige die concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* [ AEM Headless Vertaalreis ](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een breed inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.
* [ een Inleiding aan de Architectuur van Adobe Experience Manager as a Cloud Service ](/help/overview/architecture.md) - begrijp de structuur van AEM as a Cloud Service
* Een [ Inleiding aan AEM als Zwaarloze CMS ](/help/headless/introduction.md)
* Het [ AEM Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ AEM Tutorials zonder kop ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - gebruik deze hands-on leerprogramma&#39;s om te onderzoeken hoe te om de diverse opties te gebruiken om inhoud aan headless eindpunten met AEM te leveren en te kiezen wat voor u juist is.
* [ Beheer van de Inhoud zonder hoofd Gebruikend GraphQL APIs ](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses) - volg deze cursus voor een overzicht van GraphQL API die in AEM wordt uitgevoerd. Verificatie via AdobeID is vereist.
* [ AEM Guides WKND - GraphQL ](https://github.com/adobe/aem-guides-wknd-graphql) - Dit project GitHub omvat voorbeeldtoepassingen die AEM GraphQL APIs benadrukken.
* [ Authoring Concepts ](/help/sites-cloud/authoring/author-publish.md) - Technische documentatie voor het auteursmilieu van AEM met inbegrip van details op auteur-publiceer opstelling
* [ het Publiceren Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) - Technische documentatie voor het publiceren van inhoud op AEM
* [ Naming Conventions ](/help/implementing/developing/introduction/naming-conventions.md) - Technische documentatie van pagina noemende beperkingen in AEM
* [ de Manager en Vertaling van de Vertaling van de MultiPlaats ](/help/sites-cloud/administering/msm-and-translation.md) - Technische documentatie bij AEM krachtige vertaaleigenschappen
* [ AEM werkschema&#39;s ](/help/sites-cloud/authoring/workflows/overview.md) - Technische documentatie over hoe te om werkschema&#39;s in AEM te automatiseren
* [ de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md) - Technische documentatie voor de Fragmenten van de Inhoud.
* [ Modellen van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - Technische documentatie voor de Modellen van het Fragment van de Inhoud.
* [ GraphQL Technische Documentatie ](https://graphql.org) - de definitie van GraphQL (externe verbinding)
* [ GraphQL API ](/help/headless/graphql-api/content-fragments.md) - Technische documentatie die verklaart hoe te om verzoeken tot toegang te leiden en tevreden Fragments te leveren
* [ Assets REST API ](/help/assets/content-fragments/assets-api-content-fragments.md) - Technische documentatie die verklaart hoe te om de Fragmenten van de Inhoud (en andere activa) te creëren en te wijzigen
* [ Persisted Queries ](/help/headless/graphql-api/persisted-queries.md) - Technische documentatie op gepresteerde vragen in AEM
* [ Kopieerbaar en Hoofdloos in AEM ](/help/implementing/developing/headful-headless.md) - een volledige bespreking van de hoofdloze integratieniveaus beschikbaar in AEM
* Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.
