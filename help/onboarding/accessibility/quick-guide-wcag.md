---
title: Een snelle gids voor WCAG 2.1
seo-title: Een snelle gids voor WCAG 2.1
translation-type: tm+mt
source-git-commit: 11f0509334ebe4456612789fd415a3099687dc64

---


# Een snelle gids voor WCAG 2.1{#quick-guide-to-wcag}

Adobe Experience Manager (AEM) als Cloud Service is ontwikkeld om maximale compatibiliteit met de Web Content Accessibility Guidelines te bereiken.

De [Web Content Accessibility Guidelines versie 2.1 (WCAG)](https://www.w3.org/TR/WCAG/) zijn een reeks internationaal erkende richtsnoeren die door het [World Wide Web Consortium (W3C)](https://www.w3.org/) in het kader van hun [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/)zijn ontwikkeld.

WCAG 2.1 bestaat uit een reeks technologie-onafhankelijke richtsnoeren en succescriteria om ervoor te zorgen dat webinhoud toegankelijk is voor en bruikbaar is voor personen met een handicap. Zij adviseren auteurs, ontwerpers en ontwikkelaars van webinhoud om ervoor te zorgen dat de middelen die zij produceren zo toegankelijk mogelijk zijn voor zoveel mogelijk mensen, ongeacht hun handicap; bijvoorbeeld visuele stoornissen, gehoorverlies, leermoeilijkheden, leeftijdsgebonden beperkingen.

Als u bijvoorbeeld een afbeelding (of andere niet-tekstuele inhoud) beschrijft met het `alt` kenmerk in HTML, heeft dit grote voordelen voor blinden of slechtzienden. De tekstuele beschrijving in het `alt` kenmerk kan worden omgezet in spraakuitvoer of worden verzonden naar elektronische vernieuwbare brailleweergaven.

Daarnaast kan WCAG 2.1 voordelen opleveren voor andere begunstigden, waaronder personen die *situationeel gehandicapt* kunnen worden geacht. Personen die door omstandigheden zoals bladertechnologie, netwerkverbindingssnelheid of bladeromgeving te maken hebben met belemmeringen die vergelijkbaar zijn met mensen met een handicap.

Met Adobe Experience Manager kunnen auteurs van inhoud en/of eigenaars van websites webinhoud maken die voldoet aan de relevante succescriteria van WCAG 2.1 Niveau A en Niveau AA.

Daarom is het begrijpen van de doelstellingen van WCAG 2.1 en de structuur van de richtsnoeren een belangrijk onderdeel van het begrip van webtoegankelijkheid en van de manier waarop de richtsnoeren kunnen helpen bij het creëren van toegankelijke webinhoud.

WCAG 2.1 is voornemens richtsnoeren te verstrekken die:

* Zijn **technologie-agnostisch:**
Met andere woorden, richtlijnen die kunnen worden toegepast op een reeks webinhoud-indelingen, niet alleen op HTML. WCAG 2.1 kan dus betrekking hebben op inhoud die is gegenereerd door of wordt geleverd in PDF, Flash, JavaScript en andere huidige en toekomstige webtechnologieën. <!-- This aims to address a recognized weakness of WCAG 1.0, in that it was focused on HTML at the expense of other web content formats. -->

* kunnen worden **getest:**
Elk richtsnoer is zodanig opgesteld dat het objectief kan worden getest om te garanderen dat een groep toegankelijkheidsdeskundigen het er in het algemeen over eens is dat aan het richtsnoer is voldaan. Een van de uitdagingen van toegankelijkheidsrichtlijnen is dat sommige richtlijnen technisch getest kunnen worden, terwijl andere eisen dat mensen oordeelkundig beoordelen of het richtsnoer al dan niet succesvol is uitgevoerd. <!-- WCAG 2.1 has been written with the aim of reducing the subjectivity that was present in some of the WCAG 1.0 guidelines and checkpoints. -->

* Prioritaire en contextafhankelijke implementatie **van ondersteuning:**
   <!-- As with WCAG 1.0, --> WCAG 2.1 guidelines are given priorities, relating to the likely impact of not following a guideline on a particular group of users with disabilities. This allows authors to make an informed decision on the most important guidelines for their particular situation. In addition, the concept of *accessibility supported* is introduced. This allows authors to make decisions on how best to use web technologies that may not have full accessibility support, or may require users to have specific assistive technologies and/or browsers in order to benefit from accessibility features.

Deze doelstellingen hebben de structuur van WCAG 2.1 aanzienlijk beïnvloed.

>[!NOTE]
>
>Het is niet mogelijk om een website te maken die alle mogelijke handicaps of soorten personen behandelt. Het doel van WCAG 2.1 is om webauteurs te helpen sites te maken die, voor zover mogelijk, binnen bepaalde omstandigheden en binnen redelijke gronden toegankelijk zijn.

<!--
>[!NOTE]
>
>If you are familiar with WCAG 1.0, you will notice some changes in WCAG 2.1. These relate to scope, organization and aim.
-->

## Structuur {#structure}

WCAG 2.1 is op een manier gestructureerd die concepten van het toegankelijk maken van webinhoud geleidelijk aan in detail introduceert. Dit kan de indruk wekken dat WCAG 2.1 een zeer complexe reeks onderling gekoppelde documenten is, maar het doel is (geleidelijk) gedetailleerdere informatie te verstrekken wanneer en wanneer auteurs die nodig hebben, in plaats van deze allemaal in één zeer groot document te verstrekken.

WCAG 2.1 bestaat uit vier basisbeginselen voor toegankelijk ontwerp, die soms worden genoemd door de **afkorting POUR**. Dit zijn:

1. **Vermoedelijk**: kan een gebruiker de webinhoud in kwestie voelen?
1. **Werkbaar**: kan een gebruiker navigeren, gegevens invoeren of anderszins met de webinhoud communiceren?
1. **Begrijpbaar**: kan een gebruiker de webinhoud verwerken en begrijpen die aan hen wordt voorgesteld?
1. **Robuust**: is de webinhoud op de beoogde manier beschikbaar in een voldoende breed scala aan browseringsomgevingen , waaronder verouderde en opkomende browseromgevingen ?

Uitwerken van:
* Elk **beginsel** bestaat uit een of meer **richtsnoeren**.

* Richtlijnen worden geformuleerd als instructies, die ofwel positief (doe dit...) of negatief (doe dit niet...) zijn.
* De richtsnoeren zijn de nummers 1.1 tot en met 4.1, waar het eerste nummer overeenkomt met het moederbeginsel.
* Elk richtsnoer bestaat uit een of meer **succescriteria**.
* Succescriteria worden geschreven als instructies, die ofwel `True` ofwel `False` voor een bepaalde webpagina zijn.
* Succescriteria kunnen een keuze of keuze omvatten, of kunnen uitzonderingen omvatten; situaties waarin niet aan de succescriteria moet worden voldaan.
* Succescriteria worden genummerd volgens het richtsnoer en het beginsel van de moedermaatschappij, van 1.1.1 tot en met 4.1.1. Zij hebben ook een korte naam die de intentie van het criterium samenvat, voor gemakkelijkere verwijzing. Het succescriterium 1.1.1 is bijvoorbeeld een alternatief dat niet-tekst is.
* De succescriteria omvatten een lijst van verwante **technieken** (hieronder nader beschreven).

## Ondersteunende bronnen {#supporting-resources}

Naast de kerncomponenten van WCAG 2.1 van Beginselen, Richtsnoeren en Succescriteria, zijn er een aantal ondersteunende documenten. Sommige van hen geven specifiek advies over hoe te om aan aspecten van de richtlijnen te voldoen, andere zijn meer algemene verwijzingen die Webauteurs, ontwerpers en ontwikkelaars van alle capaciteiten helpen WCAG 2.1 zo effectief mogelijk begrijpen en gebruiken.

Hoewel WCAG 2.1 een stabiel document is en niet zal veranderen, zijn de meeste van deze ondersteunende hulpmiddelen dynamische documenten; zij zullen in de loop der tijd veranderen en groeien naarmate nieuwe technologieën zich ontwikkelen , en er zijn nieuwe voorbeelden te vinden van de wijze waarop toegankelijkheid van het web kan worden bereikt .

### WCAG 2.1-bronnen {#wcag-resources}

Deze lijst is niet bedoeld als limitatief, maar bevat een inleiding op de beschikbare middelen:
* [Een overzicht van alle WCAG-gerelateerde documenten](https://www.w3.org/WAI/standards-guidelines/wcag/)
* [Een samenvatting van de verschillende documenten](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)
* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG21/)
* [Nieuw in WCAG 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/)
* [Een snelle gids van de Verwijzing voor hoe te om WCAG 2.1 te ontmoeten](https://www.w3.org/WAI/WCAG21/quickref/)
* [WCAG 2 Veelgestelde vragen](https://www.w3.org/WAI/standards-guidelines/wcag/faq/)


### Nieuw in WCAG 2.1 {#what-is-new}

[Nieuw in WCAG 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/) verstrekt waardevolle informatie over de delta tussen WCAG en 2.0 en WCAG 2.1.

[WCAG 2.0 en 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/#versions) verduidelijken de status van hun relatie.

### Technieken voor WCAG 2.1 {#techniques-for-wcag}

Technieken voor WCAG 2.1 zijn beschikbaar op de [Technieken voor WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/) pagina.

**Technieken** vormen het niveau onder succescriteria in de hiërarchie WCAG 2.1. Ze worden door WAI geclassificeerd als informatief, niet als normatief. Met andere woorden, een specifieke techniek hoeft niet te worden gevolgd om een bron in overeenstemming te brengen met WCAG 2.1.

Omdat technieken veel specifieker zijn dan succescriteria, verwijzen ze doorgaans naar een bepaald technologie- of inhoudstype (bijvoorbeeld HTML of video) of naar een situatie (bijvoorbeeld e-commerce of e-learningtoepassing). U kunt technieken zien als bewezen voorbeelden van hoe specifieke richtlijnen en succescriteria kunnen worden vervuld, zodat ze nuttig zijn voor auteurs en ontwikkelaars die in bepaalde situaties werken.

U hebt toegang tot technieken:

* Op verzameling (technieken kunnen algemeen zijn of betrekking hebben op een specifieke technologie of indeling, zoals HTML, CSS of clientscripts), of
* Uit gerelateerde succescriteria. Technieken kunnen op meer dan één succescriterium van toepassing zijn.

Elke techniek heeft een uniek getal dat betrekking heeft op de verzameling ervan. Een van de ARIA-technieken is bijvoorbeeld *Technique ARIA2: Vereiste velden identificeren met de eigenschap*&quot;required&quot;.

Technieken kunnen Volstaan, Adviserend, of een Mislukking zijn:

* Een *toereikende techniek* is een techniek die, als ze wordt gevolgd, voldoende is om aan een bepaald succescriterium te voldoen.
* Een *adviestechniek* is een techniek die, als ze wordt gevolgd, een positief effect zal hebben op de toegankelijkheid, maar op zich misschien niet voldoende is om te garanderen dat aan een bepaald succescriterium wordt voldaan.
* Een *mislukking* is een techniek die specifiek voorbeeld beschrijft van waar een succescriterium niet zou worden vervuld.

De details voor technieken omvatten een beschrijving, toepasselijkheid, voorbeelden, middelen voor verdere informatie en details van hoe de auteurs voor succesvolle toepassing van de techniek kunnen testen.

De lijst met technieken is niet compleet en WAI werkt de lijst voortdurend bij met nieuwe voorbeelden, die de ontwikkelingen in webtechnologie, ontwerpbenaderingen en onderzoeksresultaten weerspiegelen. Het is dus goed om de lijst met technieken voor nieuwe toevoegingen regelmatig te controleren.

### WCAG 2.1 begrijpen {#understanding-wcag}

Dit betreft een reeks documenten die lezers advies geven om het doel van specifieke richtsnoeren en succescriteria te beoordelen. U kunt een inleiding [downloaden, plus verbindingen aan meer gedetailleerde informatie](https://www.w3.org/WAI/WCAG21/Understanding/).

Elk afzonderlijk richtsnoer en succescriterium heeft ook een eigen &quot;Understanding&quot;-pagina, die informatie bevat over:

* de intentie van het richtsnoer;
* specifieke succescriteria;
* Adviestechnieken die helpen te voldoen aan de vereisten van de richtsnoeren, maar die niet onder een specifiek succescriterium vallen.

De afzonderlijke pagina &quot;Understanding&quot; van elk succescriterium bevat informatie over:

* de intentie van het succescriterium;
* Algemene voorbeelden van de wijze waarop aan het succescriterium kan worden voldaan;
* gerelateerde (niet W3C) bronnen over hoe aan het succescriterium kan worden voldaan;
* Technieken en fouten: specifieke en gedetailleerde voorbeelden van de wijze waarop aan het succescriterium kan worden voldaan (hieronder nader beschreven)
* Belangrijke termen - een verklarende woordenlijst van termen die belangrijk zijn om het succescriterium te begrijpen.

Een voorbeeld is te vinden op: [Succescriterium 1.1.1 (&quot;Niet-tekstuele inhoud&quot;)](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content).

### Hoe te om WCAG 2.1 te ontmoeten {#how-to-meet-wcag}

De sectie &quot;Hoe kan ik ontmoeten&quot; is beschikbaar op de pagina [Hoe kan ik aan WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/) voldoen. Deze paragraaf biedt een alternatieve presentatie van WCAG, waardoor de inhoud van de richtsnoeren kan worden verfijnd tot de richtsnoeren die het meest relevant zijn voor de eigen belangen of omstandigheden van de lezer. Lezers kunnen de technieken met succescriteria die ze willen bekijken filteren door bepaalde webinhoud-technologieën op te geven, zoals Cascading Style Sheets of scripting, of door een bepaald prioriteitsniveau of -niveaus op te geven.

Zonder filtreren, verstrekt dit middel alle succescriteria die door richtlijn worden gegroepeerd. Voor elk succescriterium wordt het volgende verstrekt:

* de tekst van het succescriterium;
* een link naar het bijbehorende &quot;document van overeenstemming&quot;;
* een lijst van verwante technieken die toereikend zijn en die verband houden met de bijzonderheden van elke techniek;
* een lijst van verwante adviestechnieken, die verband houdt met de bijzonderheden van elke techniek (indien deze bestaat);
* Een lijst van verwante mislukkingen, die aan details van elke mislukking verbinden.
