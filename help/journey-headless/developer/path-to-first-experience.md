---
title: Pad naar uw eerste ervaring met AEM Headless
description: In dit deel van de AEM Headless Developer Journey zult u begrijpen hoe u uw eerste headless-ervaring in AEM kunt implementeren, inclusief planningsoverwegingen en leert u ook best practices om uw pad zo vloeiend mogelijk te maken.
exl-id: 172ad8d8-5067-4452-bf91-1eea9a39a7bc
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 46b0af152d5f297419e7d1fa372975aded803bc7
workflow-type: tm+mt
source-wordcount: '1956'
ht-degree: 0%

---

# Pad naar uw eerste ervaring met AEM Headless {#path-to-first-experience}

In dit deel van de [ Hoofdloze Reis van de Ontwikkelaar van AEM ](overview.md), zult u de stappen aan het uitvoeren van uw eerste headless ervaring in AEM met inbegrip van planningsoverwegingen begrijpen en zult ook beste praktijken leren om uw weg zo vlot mogelijk te maken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de hoofdloze reis van AEM, [ Begonnen het worden met as a Cloud Service van AEM Headless ](getting-started.md) leerde u de basistheorie van wat een headless CMS is en u zou nu moeten:

* Begrijp de basisbeginselen van de AEM-functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u de AEM-functies zonder kop moet gebruiken.
* Wees op de hoogte van AEM&#39;s instapniveau.
* U kunt uw project definiëren in termen van bereik.

Dit artikel bouwt verder op deze basisbeginselen zodat u begrijpt hoe u uw eigen AEM-project zonder kop kunt voorbereiden.

## Doelstelling {#objective}

Dit document helpt u de stappen begrijpen nodig om uw eerste project uit te voeren. Na het lezen moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen voor het uitvoeren van headless in AEM.
* Zorg dat u weet welke gereedschappen en AEM-configuraties nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

## Vereisten {#requirements}

Alvorens u met dit document verdergaat, zorg ervoor dat u het vorige document in de Journaal van de Ontwikkelaar van AEM Headless hebt herzien, [ Begonnen het worden met as a Cloud Service van AEM Headless ](getting-started.md) ervoor zorgen u:

* Voldoe aan de vermelde vereisten.
* Heb uw eigen projectdefinitie met inbegrip van werkingsgebied, rollen, en prestaties overwogen.

## Planning voor succes {#planning-for-success}

Als u uw eerste AEM-project zonder kop wilt starten, moet u ervoor zorgen dat u een inhoudsmodel hebt dat de personalisatie en updates die u via al uw kanalen wilt maken, ondersteunt.

Afzonderlijk van AEM, wilt u ook ervoor zorgen u een juiste ontwikkelomgeving opstelling hebt als u een cliënt-zijtoepassing bouwt zodat kunt u uw cliënt tegen API vraag aan AEM as a Cloud Service testen.

### Inhoudsmodellen en API&#39;s definiëren {#defining-models}

U wilt een consistente ervaring opdoen en gepersonaliseerde campagnes over kanalen beheren, zodat u elk afzonderlijk kanaal en oppervlak kunt bekijken als een eigen specifieke inhoudsstructuur om aan te leveren. Nochtans, heeft het hebben van elk kanaal zijn eigen inhoudsmodel is uitdagend om te handhaven.

In plaats daarvan, zou u moeten nadenken hoe de inhoud op verschillende oppervlakten op het organiseren van beginsel zoals merk en producthiërarchieën, categorieën van goederen of oppervlakten, of stappen in de klantenreis wordt verwant. Als u bijvoorbeeld een reeks oppervlakken hebt die een specifiek merk auto&#39;s ondersteunen dat u maakt, kunt u beginnen met een inhoudsmodel voor algemene informatie die geldt voor de hele auto en vervolgens meer - specifieke elementen hebben, zoals de inhoud die nodig is wanneer de auto wordt gestart tot wanneer er serviceproblemen zijn. Een dergelijk model zal de overerving van de algemene inhoud van het automerk afdwingen en tegelijk verschuivingen mogelijk maken op basis van de specifieke context die nodig is. Het helpt ook bij het beheer in de toekomst van updates voor deze inhoud, aangezien u controle kunt afdwingen op basis van rollen zoals de algemene markator of productmanager voor het hele automerk tegenover een auteur die verantwoordelijk is voor de &quot;startervaring&quot;.

Nadat u het inhoudsmodel en een duidelijke mening op de diverse cliënten hebt de inhoud aan moet worden opgezocht, moet u ervoor zorgen de GraphQL/APIs verbonden aan de toegang tot diverse van het inhoudsmodel aan alle cliënten worden gepubliceerd die deze inhoud nodig hebben. Er zijn verschillende opties voor de toegang tot bepaalde inhoud. U kunt om een specifiek stuk van inhoud verzoeken dat statisch is die caching van de inhoud en hogere prestaties toelaat. U kunt ook inhoud aanvragen die dynamisch wordt gegenereerd en waarvoor meer verwerkingstijd nodig is. Zorg ervoor dat de cliënten APIs gebruiken die voor hun bedrijfsbehoeften het meest efficiënt zijn.

## Inzicht krijgen in uw omgevingen {#understanding-environments}

Binnen AEM zijn er drie soorten omgevingen: ontwikkeling, staging en productie.

De ontwikkelomgevingen (u kunt meerdere omgevingen hebben) zijn een veilige plek om te experimenteren en ideeën uit te proberen. Tijdens de beginfase van het project raadt Adobe aan de ontwikkelomgevingen te gebruiken om variaties van inhoudsmodellen te proberen en te zien welke de beoogde uitvoer voor de oppervlakken opleveren.

De testomgeving voor projecten zonder kop wordt gebruikt voor het valideren van nieuwe AEM-productreleases voordat deze worden geïmplementeerd. Een bijgewerkte lijst van de modellen van de productie inhoud daar en een ondergroep van de inhoud houden, zodat kunt u teruggegeven dossiers JSON hebben om van hen te vergelijken nog de zelfde output verstrekken, aangezien u veranderingen aanbrengt of de versie van AEM veranderingen introduceert

Productie is de plaats waar inhoudsauteurs hun werkelijke inhoud maken en beheren. Modelwijzigingen in de productie moeten met zorg en met achterwaartse compatibiliteit worden uitgevoerd.

Tijdens de ontwikkelingsfase wordt u aangeraden met een ontwikkelings- en testomgeving te werken. Als u overschakelt naar het testen van de prestaties, wilt u overschakelen naar de productieomgeving.

### Samenwerking tussen ontwikkelaars en makers van inhoud {#cooperation}

Ontwikkelaars hebben een AEM-ontwikkelomgeving nodig die is ingesteld met de populaire inhoudsmodellen. De ontwikkelaar ontwikkelt de client die inhoud vanuit AEM zonder kop gaat gebruiken terwijl de makers van de inhoud de inhoud nog steeds maken. Daarom zijn de API-definities heel belangrijk. Met de AEM SDK kan de ontwikkelaar een testhaak maken, zodat client- en eenheidstests kunnen worden gemaakt om ervoor te zorgen dat de client de inhoud correct kan renderen.

Inhoudsauteurs maken inhoud op basis van de inhoudsmodellen die zijn gedefinieerd in de testomgeving. Met het ontwerpgereedschap voor inhoudsfragmenten zou de auteur een inhoudsfragment maken of een bestaand inhoudsfragment bewerken. Alvorens het te publiceren, kan de auteur voorproef hoe het in de cliënt door met de ontwikkelaar te werken om het inhoudsmodel op ontwikkeling te duwen of opstelling een ontwikkelaarmilieu enkel voor auteurs aan voorproef hoe het in de cliënt zou kijken.

## Instellen {#setup}

Voordat u in AEM aan de slag gaat met headless, moet u ervoor zorgen dat alle vereiste functies zijn ingeschakeld. In deze sectie wordt beschreven wat er nodig is. De daadwerkelijke stappen om deze stappen te vervullen zijn gedetailleerd later in de [ Hoofdloze Reis van de Ontwikkelaar van AEM ](#overview.md).

U kunt naar keuze [ extra middelen ](#additional-resources) voor meer informatie over de individuele onderwerpen ook zien.

### Configuratie {#configuration}

1. Inhoudsfragmenten inschakelen
1. GraphQL inschakelen
1. De SDK zonder koppen instellen

## Uw eerste AEM Headless-app implementeren

Dit is een overzicht van wat er nodig is om uw eerste app zonder koppen te implementeren met AEM om uw inhoud te leveren. Hoe deze stappen moeten worden uitgevoerd, wordt in latere delen van de Headless Developer Journey gedetailleerd beschreven.

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
   * AEM laat modellen toe om per omslag worden geplaatst zodat zal **nieuwe** knoop creëren slechts de modellen tonen die in die plaats worden gesteund.
* Het maken van nieuwe inhoudsfragmenten in de In-line Content Fragment Editor kan worden vereenvoudigd als de hoofdmap is ingesteld in het model. Dan moet de arts geen plaats kiezen, maar enkel een naam verstrekken en kan de nieuwe verwijzing beginnen uit te geven.

### Inhoud ontwerpen {#authoring}

* Voor kanaalspecifieke versies van uw inhoud kunt u overwegen variaties in inhoudsfragmenten te gebruiken. Variaties worden gesynchroniseerd met de hoofdinhoud om het beheer van wijzigingen in de inhoud te stroomlijnen.
* Andere producenten van inhoud uitnodigen om inhoud te beoordelen en feedback te geven.
* Houd de zaken met zo weinig mogelijk verplichte elementen in beweging. Verplichte elementen kunnen de workflow blokkeren.

### Globale inhoud ontwerpen {#localization}

* Vaststellen van regels en bestuur voor het vertalen van inhoud. Om systeemlading te verminderen, vertaal als asynchroon proces dat in langere intervallen kan worden in werking gesteld. Zorg ervoor dat u tijd hebt voor de kwaliteitscontrole voor lokalisatie en voor het corrigeren van fouten.
* Maak gebruik van alle mogelijkheden die uw vertaaltechnologie biedt en die u met AEM kunt integreren, zoals vertaalgeheugen.
* Begrijp als rijke media inhoud, zoals beelden en video&#39;s, localisatie vereist.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen voor het uitvoeren van headless in AEM.
* Zorg dat u weet welke gereedschappen en AEM-configuraties nodig zijn.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

We willen dat u op deze basiskennis voortbouwt om volledig inzicht te krijgen in de kracht en flexibiliteit van AEM Headless, zodat u ervan kunt profiteren voor uw eigen projecten. Hiervoor hebt u opties.

### Kies uw eigen avontuur {#choose-your-path}

Hoe je ook leert, Adobe wil dat je slaagt als je aan de slag gaat met je AEM Headless-project.

* Als u verkiest om **over headless concepten en AEM te blijven leren zonder kop technologieën**, zou u uw reis zonder kop van AEM moeten voortzetten door het document [ te herzien hoe te Uw Inhoud als Modellen van de Inhoud van AEM te modelleren ](model-your-content.md) waar u leert hoe te om uw inhoudsstructuur in AEM te modelleren.
* Als u verkiest om **te leren door** te doen, kunt u aan [ springen Begonnen het Worden met AEM Headless hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u direct in de Zwaarloze ontwikkeling van AEM zult springen door een eenvoudig project uit te voeren om de inhoud van AEM zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van de headless ontwikkelingstraject door het document [ te herzien hoe te Model Uw Inhoud als Modellen van de Inhoud van AEM ](model-your-content.md) beweegt, zijn het volgende enkele extra, facultatieve middelen die een diepere duik op sommige die concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* ](/help/journey-headless/translation/overview.md) de Vertaalreis van 0} AEM Headless [ - Deze documentatietraject geeft u een breed inzicht in headless technologie, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.
* [ Hoofdloze Ontwikkeling voor AEM Sites as a Cloud Service ](/help/headless/introduction.md) - een snelle inleiding om de Ontwikkelaar van AEM Headless met de noodzakelijke eigenschappen te richten
* [ AEM Developer Portal ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ Hoofdloze Leerprogramma&#39;s van AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - gebruik deze hands-on leerprogramma&#39;s om te onderzoeken hoe te om de diverse opties te gebruiken om inhoud aan headless eindpunten met AEM te leveren en te kiezen wat voor u juist is.
* [ het Beheer van de Inhoud zonder hoofd Gebruikend GraphQL APIs ](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses) - volg deze cursus voor een overzicht van GraphQL API die in AEM wordt uitgevoerd. Verificatie via AdobeID is vereist.
* [ AEM Guides WKND - GraphQL ](https://github.com/adobe/aem-guides-wknd-graphql) - Dit project GitHub omvat voorbeeldtoepassingen die AEM GraphQL APIs benadrukken.
* [ Inleiding aan de Architectuur van Adobe Experience Manager as a Cloud Service ](/help/overview/architecture.md) - een volledig overzicht van de architectuur van AEM
* [ Hoofdloze Opstelling ](/help/headless/introduction.md#getting-started) - een snelle inleiding aan de hoofdloze eigenschappen van AEM voor gebruikers reeds wetend van AEM.
* [ creeer de Modellen van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) - Technische documentatie over de Modellen van het Fragment van de Inhoud
* [ creeer de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) - Technische documentatie over de Fragmenten van de Inhoud
* [ inhoud van de Vraag met GraphQL ](/help/headless/graphql-api/content-fragments.md) - Technische documentatie op GraphQL API
