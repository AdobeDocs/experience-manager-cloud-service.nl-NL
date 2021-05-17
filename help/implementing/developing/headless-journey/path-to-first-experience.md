---
title: Pad naar uw eerste ervaring met AEM zonder kop
description: In dit deel van de AEM Headless Developer Journey zult u de stappen begrijpen voor het implementeren van uw eerste headless ervaring in AEM met planningsoverwegingen en leert u ook best practices om uw pad zo vloeiend mogelijk te maken.
hide: true
hidefromtoc: true
index: false
exl-id: 257fc173-6bfb-4b60-b66c-6d6bdd5cf13f
source-git-commit: 3554c4a4ea1858ea5b4ffbe0fd223a540261cb5c
workflow-type: tm+mt
source-wordcount: '2019'
ht-degree: 0%

---

# Pad naar uw eerste ervaring met AEM zonder kop {#path-to-first-experience}

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Headless Developer Journey,](overview.md) zult u de stappen begrijpen om uw eerste headless ervaring in AEM met planningsoverwegingen te implementeren en zult u ook best practices leren om uw pad zo vloeiend mogelijk te maken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM zonder kop, [Aan de slag met AEM zonder kop als Cloud Service](getting-started.md) leerde u de basistheorie van wat een zonder kop CMS is en u zou nu moeten:

* Begrijp de grondbeginselen van AEM functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u moet voldoen om AEM functies zonder kop te kunnen gebruiken.
* Wees op de hoogte van AEM integratieniveaus zonder kop.
* U kunt uw project definiëren in termen van bereik.

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe te om uw eigen AEM hoofdloze project voor te bereiden.

## Doelstelling {#objective}

Dit document helpt u de stappen begrijpen nodig om uw eerste project uit te voeren. Na het lezen moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om zonder kop in AEM uit te voeren.
* Zorg dat u weet welke gereedschappen en AEM nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

## Vereisten {#requirements}

Voordat u doorgaat met dit document, moet u ervoor zorgen dat u het vorige document in de AEM Headless Developer Journey hebt gereviseerd, [Aan de slag met AEM Headless als een Cloud Service](getting-started.md). Zorg ervoor dat u:

* Voldoe aan de vermelde vereisten.
* Heb uw eigen projectdefinitie met inbegrip van werkingsgebied, rollen, en prestaties overwogen.

## Planning voor Succes {#planning-for-success}

Als u uw eerste AEM project zonder kop wilt starten, moet u ervoor zorgen dat u een inhoudsmodel hebt dat de personalisatie en updates die u op al uw kanalen wilt maken, ondersteunt.

Afzonderlijk van AEM, wilt u ook ervoor zorgen u een juiste ontwikkelomgeving opstelling hebt als u een cliënt-zijtoepassing bouwt zodat kunt u uw cliënt tegen API vraag aan AEM als Cloud Service testen.

### Inhoudsmodellen en API&#39;s definiëren {#defining-models}

U wilt een consistente ervaring opdoen en gepersonaliseerde campagnes over kanalen beheren, zodat u elk afzonderlijk kanaal en oppervlak kunt bekijken als een eigen specifieke inhoudsstructuur om aan te leveren. Nochtans heeft het hebben van elk kanaal zijn eigen inhoudsmodel uitdagend om te handhaven.

In plaats daarvan, zou u moeten overwegen hoe de inhoud op verschillende oppervlakten op het organiseren van beginsel zoals merk en producthiërarchieën, categorieën van goederen of oppervlakten, of stappen in de klantenreis verwant zijn. Als u bijvoorbeeld een reeks oppervlakken hebt die een specifiek merk auto&#39;s ondersteunen dat u maakt, kunt u beginnen met een inhoudsmodel voor algemene informatie die geldig is voor de hele auto en vervolgens meer contextspecifieke elementen hebben, zoals de inhoud die nodig is wanneer de auto wordt gestart tot wanneer er servicekwesties zijn. Een dergelijk model zal de overerving van de algemene inhoud van het automerk afdwingen en tegelijk verschuivingen mogelijk maken op basis van specifieke omstandigheden die nodig zijn. Het helpt ook bij het beheer in de toekomst van updates voor deze inhoud, aangezien u controle kunt afdwingen op basis van rollen zoals de algemene markator of productmanager voor het hele automerk tegenover een auteur die verantwoordelijk is voor de &quot;startervaring&quot;.

Zodra u het inhoudsmodel en de duidelijke mening op de diverse cliënten hebt moet de inhoud worden opgezocht aan, moet u ervoor zorgen GraphQL/APIs verbonden aan de toegang tot van diverse van het inhoudsmodel wordt gepubliceerd aan alle cliënten die deze inhoud nodig hebben. Er zijn verschillende opties voor de toegang tot bepaalde inhoud. U kunt om een specifiek stuk van inhoud verzoeken dat statisch is die caching van de inhoud en hogere prestaties toelaat. U kunt ook inhoud aanvragen die dynamisch wordt gegenereerd en waarvoor meer verwerkingstijd nodig is. Zorg ervoor dat clients gebruikmaken van de API&#39;s die het meest efficiënt zijn voor hun zakelijke behoeften.

## Uw omgevingen {#understanding-environments}

Binnen AEM zijn er drie soorten omgevingen: ontwikkeling, staging en productie.

De ontwikkelomgevingen (u kunt meerdere omgevingen hebben) zijn een veilige plek om te experimenteren en ideeën uit te proberen. Tijdens de eerste fase van het project raadt Adobe aan de ontwikkelomgevingen te gebruiken om variaties van inhoudsmodellen te proberen en te zien welke de beoogde uitvoer voor de oppervlakken opleveren.

De het opvoeren omgeving voor hoofdloze projecten wordt gebruikt voor het bevestigen van nieuwe AEM productreleases alvorens zij aan productie uitrollen. Een bijgewerkte lijst van de modellen van de productie inhoud daar en een ondergroep van de inhoud houden, zodat kunt u teruggegeven dossiers JSON hebben om van hen te vergelijken nog de zelfde output verstrekken, aangezien u veranderingen aanbrengt of de AEM versie veranderingen introduceert

Productie is de plaats waar inhoudsauteurs hun werkelijke inhoud maken en beheren. Modelwijzigingen in de productie moeten met zorg en met achterwaartse compatibiliteit worden uitgevoerd.

Tijdens de ontwikkelingsfase wordt u aangeraden met een ontwikkelings- en testomgeving te werken. Als u overschakelt naar het testen van de prestaties, wilt u overschakelen naar de productieomgeving.

### Samenwerking tussen ontwikkelaars en makers van inhoud {#cooperation}

Ontwikkelaars hebben een AEM ontwikkelomgeving nodig die is ingesteld met de populaire inhoudsmodellen. De ontwikkelaar ontwikkelt de client die inhoud vanuit AEM headless zal verbruiken terwijl de makers van de inhoud de inhoud nog steeds maken. Daarom zijn de API-definities heel belangrijk. Door gebruik te maken van de AEM SDK kan de ontwikkelaar een testhaak maken, zodat client- en eenheidstests kunnen worden gemaakt om ervoor te zorgen dat de client de inhoud correct kan renderen.

Inhoudsauteurs maken inhoud op basis van de inhoudsmodellen die zijn gedefinieerd in de testomgeving. Met het ontwerpgereedschap voor inhoudsfragmenten zou de auteur een nieuw inhoudsfragment maken of een bestaand inhoudsfragment bewerken. Alvorens het te publiceren, kan de auteur voorproef hoe het in de cliënt door met de ontwikkelaar te werken om het inhoudsmodel op ontwikkeling te duwen of opstelling een ontwikkelaarmilieu enkel voor auteurs aan voorproef hoe het in de cliënt zou kijken.

## Instellen {#setup}

Voordat u aan de slag gaat met headless in AEM, moet u ervoor zorgen dat alle vereiste functies zijn ingeschakeld. In deze sectie wordt beschreven wat er nodig is. De daadwerkelijke stappen om deze stappen te vervullen zijn gedetailleerd later in [AEM Headless Developer Journey.](#overview.md)

U kunt naar keuze ook naar [extra middelen](#additional-resources) voor meer informatie over de individuele onderwerpen verwijzen.

### Configuratie {#configuration}

1. Inhoudsfragmenten inschakelen
1. GraphQL inschakelen
1. De Headless SDK instellen

## Uw eerste AEM headless-app implementeren

Dit is een overzicht van wat nodig is om uw eerste app zonder koppen te implementeren met AEM om uw inhoud te leveren. Hoe u deze stappen uitvoert, wordt in latere delen van de Headless Developer Journey gedetailleerd beschreven.

1. Modellen voor inhoudsfragmenten maken
1. Inhoudsfragmenten maken
1. Inhoud query met GraphQL

## Best practices voor {#best-practices}

Een project zonder kop is niet alleen succesvol vanwege de geïmplementeerde technologie, maar ook vanwege goede planning en projectbestuur. Hieronder volgt een aantal aanbevolen procedures voor auteurs en ontwikkelaars van inhoud om hiermee rekening te houden wanneer u uw project plant.

### Uw inhoud ordenen {#organizing-content}

* Maak uw structuur zo complex als nodig maar houd deze zo eenvoudig mogelijk. Eenvoudigere inhoudsstructuren helpen het beheer van inhoud te stroomlijnen en de systeemprestaties te verbeteren.
* Prioriteit geven aan het hergebruik van inhoud in uw strategie. Maak submodellen en inhoudsverwijzingen die opnieuw kunnen worden gebruikt op meerdere modellen en kanalen op een hoger niveau.
* Maak inhoudsstructuren zo duidelijk mogelijk, zodat de auteurs van de inhoud snel kunnen leren en zich kunnen aanpassen aan ontwerptaken.
* Als u toegangsbeperkingen hebt, probeert u het inhoudsmodel uit te lijnen met de toegangsvereisten.
* Wanneer u toegangsvereisten hebt, zouden zij uw inhoudshiërarchie moeten drijven. Groepeer de inhoud die door dezelfde groep personen wordt bewerkt.
* Groepeer vergelijkbare inhoud in een map.
   * Het is waarschijnlijker dat een auteur van inhoud bestaande inhoud kopieert en plakt om nieuwe inhoud te maken. Als u dit in dezelfde map doet, wordt het efficiënter.
   * AEM staat toe om toegestane modellen per omslag te plaatsen zodat zal de **Create nieuwe** knoop slechts de modellen tonen die in die plaats worden gesteund.
* Het maken van nieuwe inhoudsfragmenten in de In-line Content Fragment Editor kan worden vereenvoudigd als de hoofdmap is ingesteld in het model. Dan moet de arts geen plaats kiezen, maar enkel een naam verstrekken en kan beginnen de nieuwe verwijzing uit te geven.

### Inhoud ontwerpen {#authoring}

* Voor kanaalspecifieke versies van uw inhoud kunt u overwegen variaties in inhoudsfragmenten te gebruiken. Variaties worden gesynchroniseerd met de inhoud die is master om het beheer van inhoudswijzigingen te stroomlijnen.
* Andere inhoudsproducenten uitnodigen om inhoud te beoordelen en feedback te geven met annotaties en opmerkingen, die beschikbaar zijn in de inhoudsfragmenteditor en wereldwijd voor fragmenten in de beheerconsole van inhoudsfragmenten.
* Houd de zaken met zo weinig mogelijk verplichte elementen in beweging. Verplichte elementen kunnen de workflow blokkeren.

### Globale inhoud ontwerpen {#localization}

* Vaststellen van regels en bestuur voor het vertalen van inhoud. Om systeemlading te verminderen, vertaal als asynchroon proces dat in langere intervallen kan worden in werking gesteld. Zorg ervoor dat u tijd hebt voor de kwaliteitscontrole voor lokalisatie en voor het corrigeren van fouten.
* Maak gebruik van alle mogelijkheden die uw vertaaltechnologie biedt en die u kunt integreren met AEM, zoals vertaalgeheugen.
* Begrijp als rijke media inhoud, zoals beelden en video&#39;s, localisatie vereist.

## Volgende {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om zonder kop in AEM uit te voeren.
* Zorg dat u weet welke gereedschappen en AEM nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

Wij willen dat u op deze grondkennis voortbouwt om de kracht en de flexibiliteit van AEM Headless volledig te begrijpen zodat u ervan kunt profiteren voor uw eigen projecten. Hiervoor hebt u opties.

### Kies uw eigen avontuur {#choose-your-path}

Wat uw het leren stijl ook maakt, Adobe wil u slagen aangezien u met uw project zonder AEM wordt begonnen.

* Als u liever **meer wilt leren over concepten zonder kop en AEM technologieën zonder kop**, kunt u de AEM doorlopen door het document [How to Model Your Content Model as AEM Content Models](model-your-content.md) te bekijken, waarin u leert hoe u de inhoudstructuur in AEM modelleert.
* Als u verkiest om **te leren door te doen**, kunt u aan [Aan de slag met AEM Hoofdloze hands-on leerprogramma](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) springen waar u direct in AEM Ontwikkelt zonder Titel door een eenvoudig project uit te voeren om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u op het volgende deel van de headless ontwikkelingsreis door het document [te herzien hoe te Model Uw Inhoud als Modellen van de Inhoud,](model-your-content.md) het volgende zijn enkele extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document worden vermeld, maar zij worden vereist niet om op de headless reis verder te gaan.

* [Headless Development voor AEM Sites als Cloud Service](/help/implementing/developing/headless/introduction.md)  - Een korte inleiding om de ontwikkelaar van AEM Headless de nodige functies te geven
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)  zonder kop - Gebruik deze praktische zelfstudies om te bekijken hoe u de verschillende opties kunt gebruiken om inhoud aan eindpunten zonder kop met AEM te leveren en te kiezen wat bij u past.
* [Koploos inhoudsbeheer met GraphQL APIs](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  - Volg deze cursus voor een overzicht van de GraphQL API die in AEM wordt uitgevoerd. Verificatie via AdobeID is vereist.
* [AEM Gidsen WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Dit project GitHub omvat voorbeeldtoepassingen die AEM GraphQL APIs benadrukken.
* [Inleiding tot de Architectuur van Adobe Experience Manager als Cloud Service](/help/core-concepts/architecture.md)  - Een volledig overzicht van AEM architectuur
* [Headless Getting Started Guide](/help/implementing/developing/headless/introduction.md#getting-started)  - Een korte inleiding tot AEM headless-functies voor gebruikers die al bekend zijn met AEM.
* [Modellen](/help/assets/content-fragments/content-fragments-models.md)  voor inhoudsfragmenten maken - Technische documentatie over modellen voor inhoudsfragmenten
* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)  maken - Technische documentatie over inhoudsfragmenten
* [Inhoud query met GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Technische documentatie op de GraphQL API
