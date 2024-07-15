---
title: Pad naar uw eerste ervaring met AEM zonder kop
description: In dit deel van de AEM Headless Developer Journey zult u de stappen begrijpen voor het implementeren van uw eerste headless ervaring in AEM met planningsoverwegingen en leert u ook best practices om uw pad zo vloeiend mogelijk te maken.
exl-id: 172ad8d8-5067-4452-bf91-1eea9a39a7bc
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1956'
ht-degree: 0%

---

# Pad naar uw eerste ervaring met AEM zonder kop {#path-to-first-experience}

In dit deel van de [ AEM Zwaardeloze Reis van de Ontwikkelaar, ](overview.md) u zult de stappen begrijpen aan het uitvoeren van uw eerste headless ervaring in AEM met inbegrip van planningsoverwegingen en zult ook beste praktijken leren om uw weg zo vlot mogelijk te maken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze reis, [ Begonnen het worden met AEM as a Cloud Service zonder hoofd ](getting-started.md) u de basistheorie van leerde wat een hoofd CMS is en u zou nu moeten:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te kunnen gebruiken.
* Wees op de hoogte van AEM instorting van het integratieniveau zonder kop.
* U kunt uw project definiëren in termen van bereik.

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe te om uw eigen AEM hoofdloze project voor te bereiden.

## Doelstelling {#objective}

Dit document helpt u de stappen begrijpen nodig om uw eerste project uit te voeren. Na het lezen moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om zonder kop in AEM uit te voeren.
* Zorg dat u weet welke gereedschappen en AEM nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

## Vereisten {#requirements}

Alvorens u met dit document verdergaat, zorg ervoor dat u het vorige document in de Reis van de Ontwikkelaar van de AEM Zwaartepunt hebt herzien, [ Begonnen het worden met AEM as a Cloud Service Zwaartepunt ](getting-started.md) ervoor zorgen u:

* Voldoe aan de vermelde vereisten.
* Heb uw eigen projectdefinitie met inbegrip van werkingsgebied, rollen, en prestaties overwogen.

## Planning voor succes {#planning-for-success}

Als u uw eerste AEM project zonder kop wilt starten, moet u ervoor zorgen dat u een inhoudsmodel hebt dat de personalisatie en updates die u op al uw kanalen wilt maken, ondersteunt.

Afzonderlijk van AEM, wilt u ook ervoor zorgen u een juiste ontwikkelomgeving opstelling hebt als u een cliënt-zijtoepassing bouwt zodat kunt u uw cliënt tegen API vraag aan AEM as a Cloud Service testen.

### Inhoudsmodellen en API&#39;s definiëren {#defining-models}

U wilt een consistente ervaring opdoen en gepersonaliseerde campagnes over kanalen beheren, zodat u elk afzonderlijk kanaal en oppervlak kunt bekijken als een eigen specifieke inhoudsstructuur om aan te leveren. Nochtans, heeft het hebben van elk kanaal zijn eigen inhoudsmodel is uitdagend om te handhaven.

In plaats daarvan, zou u moeten nadenken hoe de inhoud op verschillende oppervlakten op het organiseren van beginsel zoals merk en producthiërarchieën, categorieën van goederen of oppervlakten, of stappen in de klantenreis wordt verwant. Als u bijvoorbeeld een reeks oppervlakken hebt die een specifiek merk auto&#39;s ondersteunen dat u maakt, kunt u beginnen met een inhoudsmodel voor algemene informatie die geldt voor de hele auto en vervolgens meer - specifieke elementen hebben, zoals de inhoud die nodig is wanneer de auto wordt gestart tot wanneer er serviceproblemen zijn. Een dergelijk model zal de overerving van de algemene inhoud van het automerk afdwingen en tegelijk verschuivingen mogelijk maken op basis van de specifieke context die nodig is. Het helpt ook bij het beheer in de toekomst van updates voor deze inhoud, aangezien u controle kunt afdwingen op basis van rollen zoals de algemene markator of productmanager voor het hele automerk tegenover een auteur die verantwoordelijk is voor de &quot;startervaring&quot;.

Nadat u het inhoudsmodel en een duidelijke mening op de diverse cliënten hebt de inhoud aan moet worden opgezocht, moet u ervoor zorgen de GraphQL/APIs verbonden aan de toegang tot diverse van het inhoudsmodel aan alle cliënten worden gepubliceerd die deze inhoud nodig hebben. Er zijn verschillende opties voor de toegang tot bepaalde inhoud. U kunt om een specifiek stuk van inhoud verzoeken dat statisch is die caching van de inhoud en hogere prestaties toelaat. U kunt ook inhoud aanvragen die dynamisch wordt gegenereerd en waarvoor meer verwerkingstijd nodig is. Zorg ervoor dat de cliënten APIs gebruiken die voor hun bedrijfsbehoeften het meest efficiënt zijn.

## Inzicht krijgen in uw omgevingen {#understanding-environments}

Binnen AEM zijn er drie soorten omgevingen: ontwikkeling, staging en productie.

De ontwikkelomgevingen (u kunt meerdere omgevingen hebben) zijn een veilige plek om te experimenteren en ideeën uit te proberen. Tijdens de beginfase van het project, adviseert de Adobe het gebruiken van de ontwikkelomgevingen om variaties van inhoudsmodellen te proberen en te zien die de voorgenomen output voor de oppervlakten verstrekken.

De het opvoeren omgeving voor hoofdloze projecten wordt gebruikt voor het bevestigen van nieuwe AEM productreleases alvorens zij aan productie uitrollen. Een bijgewerkte lijst van de modellen van de productie inhoud daar en een ondergroep van de inhoud houden, zodat kunt u teruggegeven dossiers JSON hebben om van hen te vergelijken nog de zelfde output verstrekken, aangezien u veranderingen aanbrengt of de AEM versie veranderingen introduceert

Productie is de plaats waar inhoudsauteurs hun werkelijke inhoud maken en beheren. Modelwijzigingen in de productie moeten met zorg en met achterwaartse compatibiliteit worden uitgevoerd.

Tijdens de ontwikkelingsfase wordt u aangeraden met een ontwikkelings- en testomgeving te werken. Als u overschakelt naar het testen van de prestaties, wilt u overschakelen naar de productieomgeving.

### Samenwerking tussen ontwikkelaars en makers van inhoud {#cooperation}

Ontwikkelaars hebben een AEM ontwikkelomgeving nodig die is ingesteld met de populaire inhoudsmodellen. De ontwikkelaar ontwikkelt de client die inhoud vanuit AEM headless zal verbruiken terwijl de makers van de inhoud de inhoud nog steeds maken. Daarom zijn de API-definities heel belangrijk. Door de AEM SDK te gebruiken, kan de ontwikkelaar een testhaak tot stand brengen zodat de cliënt en de eenheidstests kunnen worden gecreeerd om ervoor te zorgen de cliënt de inhoud behoorlijk kan teruggeven.

Inhoudsauteurs maken inhoud op basis van de inhoudsmodellen die zijn gedefinieerd in de testomgeving. Met het ontwerpgereedschap voor inhoudsfragmenten zou de auteur een inhoudsfragment maken of een bestaand inhoudsfragment bewerken. Alvorens het te publiceren, kan de auteur voorproef hoe het in de cliënt door met de ontwikkelaar te werken om het inhoudsmodel op ontwikkeling te duwen of opstelling een ontwikkelaarmilieu enkel voor auteurs aan voorproef hoe het in de cliënt zou kijken.

## Instellen {#setup}

Voordat u aan de slag gaat met headless in AEM, moet u ervoor zorgen dat alle vereiste functies zijn ingeschakeld. In deze sectie wordt beschreven wat er nodig is. De daadwerkelijke stappen om deze stappen te vervullen zijn gedetailleerd later in de [ AEM Headless Reis van de Ontwikkelaar.](#overview.md)

U kunt naar keuze [ extra middelen ](#additional-resources) voor meer informatie over de individuele onderwerpen ook zien.

### Configuratie {#configuration}

1. Inhoudsfragmenten inschakelen
1. GraphQL inschakelen
1. De Headless SDK instellen

## Uw eerste AEM headless-app implementeren

Dit is een overzicht van wat nodig is om uw eerste app zonder koppen te implementeren met AEM om uw inhoud te leveren. Hoe deze stappen moeten worden uitgevoerd, wordt in latere delen van de Headless Developer Journey gedetailleerd beschreven.

1. Modellen voor inhoudsfragmenten maken
1. Inhoudsfragmenten maken
1. Query-inhoud uitvoeren met GraphQL

## Aanbevolen procedures {#best-practices}

Een project zonder kop is niet alleen succesvol vanwege de geïmplementeerde technologie, maar ook vanwege goede planning en projectbestuur. Hier volgt een aantal aanbevolen procedures voor auteurs en ontwikkelaars van inhoud om hiermee rekening te houden wanneer u uw project plant.

### Uw inhoud ordenen {#organizing-content}

* Maak uw structuur zo complex als nodig maar houd deze zo eenvoudig mogelijk. Eenvoudigere inhoudsstructuren helpen het beheer van inhoud te stroomlijnen en de systeemprestaties te verbeteren.
* Prioriteit geven aan het hergebruik van inhoud in uw strategie. Maak submodellen en inhoudsverwijzingen die opnieuw kunnen worden gebruikt op meerdere modellen en kanalen op een hoger niveau.
* Maak inhoudsstructuren zo duidelijk mogelijk, zodat de auteurs van de inhoud snel kunnen leren en zich kunnen aanpassen aan ontwerptaken.
* Als u toegangsbeperkingen hebt, probeert u het inhoudsmodel uit te lijnen met de toegangsvereisten.
* Wanneer u toegangsvereisten hebt, zouden zij uw inhoudshiërarchie moeten drijven. Groepeer de inhoud die door dezelfde groep personen wordt bewerkt.
* Groepeer vergelijkbare inhoud in een map.
   * Het is waarschijnlijker dat een auteur van inhoud bestaande inhoud kopieert en plakt om nieuwe inhoud te maken. Als u dit in dezelfde map doet, wordt het efficiënter.
   * AEM laat modellen toe om per omslag worden geplaatst zodat zal de **nieuwe** knoop creëren slechts de modellen tonen die in die plaats worden gesteund.
* Het maken van nieuwe inhoudsfragmenten in de In-line Content Fragment Editor kan worden vereenvoudigd als de hoofdmap is ingesteld in het model. Dan moet de arts geen plaats kiezen, maar enkel een naam verstrekken en kan de nieuwe verwijzing beginnen uit te geven.

### Inhoud ontwerpen {#authoring}

* Voor kanaalspecifieke versies van uw inhoud kunt u overwegen variaties in inhoudsfragmenten te gebruiken. Variaties worden gesynchroniseerd met de hoofdinhoud om het beheer van wijzigingen in de inhoud te stroomlijnen.
* Andere producenten van inhoud uitnodigen om inhoud te beoordelen en feedback te geven.
* Houd de zaken met zo weinig mogelijk verplichte elementen in beweging. Verplichte elementen kunnen de workflow blokkeren.

### Globale inhoud ontwerpen {#localization}

* Vaststellen van regels en bestuur voor het vertalen van inhoud. Om systeemlading te verminderen, vertaal als asynchroon proces dat in langere intervallen kan worden in werking gesteld. Zorg ervoor dat u tijd hebt voor de kwaliteitscontrole voor lokalisatie en voor het corrigeren van fouten.
* Maak gebruik van alle mogelijkheden die uw vertaaltechnologie biedt en die u kunt integreren met AEM, zoals vertaalgeheugen.
* Begrijp als rijke media inhoud, zoals beelden en video&#39;s, localisatie vereist.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om zonder kop in AEM uit te voeren.
* Zorg dat u weet welke gereedschappen en AEM nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

Wij willen dat u op deze grondkennis voortbouwt om de kracht en de flexibiliteit van AEM Headless volledig te begrijpen zodat u ervan kunt profiteren voor uw eigen projecten. Hiervoor hebt u opties.

### Kies uw eigen avontuur {#choose-your-path}

Wat uw het leren stijl ook moge zijn, de Adobe wil dat u slaagt als u aan de slag gaat met uw AEM headless project.

* Als u verkiest om **over headless concepten en AEM te blijven leren zonder kop technologieën**, zou u uw AEM zonder kop reis moeten voortzetten door het document [ te herzien hoe te Uw Inhoud als Modellen van de Inhoud te modelleren ](model-your-content.md) waar u leert hoe te om uw inhoudsstructuur in AEM te modelleren.
* Als u verkiest om **te leren door** te doen, kunt u aan [ springen Begonnen met AEM Hoofdloze hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u direct in AEM Ontwikkelt zonder Titel door een eenvoudig project uit te voeren om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de headless ontwikkelingstraject door het document [ te herzien hoe te Model Uw Inhoud als Modellen van de Inhoud, ](model-your-content.md) het volgende is enkele extra, facultatieve middelen die een diepere duik op sommige die concepten uitvoeren in dit document worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* [ AEM Headless Vertaalreis ](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een breed inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.
* [ Zwaarloze Ontwikkeling voor AEM Sites as a Cloud Service ](/help/headless/introduction.md) - een snelle inleiding om de ontwikkelaar van de Zwaarteloze AEM met de noodzakelijke eigenschappen te richten
* [ AEM het Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ AEM Tutorials zonder kop ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - gebruik deze hands-on leerprogramma&#39;s om te onderzoeken hoe te om de diverse opties te gebruiken om inhoud aan headless eindpunten met AEM te leveren en te kiezen wat voor u juist is.
* [ Beheer van de Inhoud zonder hoofd Gebruikend GraphQL APIs ](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses) - volg deze cursus voor een overzicht van GraphQL API die in AEM wordt uitgevoerd. Verificatie via AdobeID is vereist.
* [ AEM Guides WKND - GraphQL ](https://github.com/adobe/aem-guides-wknd-graphql) - Dit project GitHub omvat voorbeeldtoepassingen die AEM GraphQL APIs benadrukken.
* [ Inleiding aan de Architectuur van Adobe Experience Manager as a Cloud Service ](/help/overview/architecture.md) - een volledig overzicht van AEM architectuur
* [ Hoofdloze Opstelling ](/help/headless/introduction.md#getting-started) - een snelle inleiding aan AEM koploze eigenschappen voor gebruikers reeds vertrouwd van AEM.
* [ creeer de Modellen van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - Technische documentatie over de Modellen van het Fragment van de Inhoud
* [ creeer de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) - Technische documentatie over de Fragmenten van de Inhoud
* [ inhoud van de Vraag met GraphQL ](/help/headless/graphql-api/content-fragments.md) - Technische documentatie op GraphQL API
