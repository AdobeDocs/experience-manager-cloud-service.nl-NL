---
title: Technische stichtingen AEM
description: Een overzicht van de technische fundamenten van AEM, inclusief hoe AEM is gestructureerd en fundamentele technologieën zoals JCR, Sling en OSGi.
exl-id: ab6e7fe9-a25d-4351-a005-f4466cc0f40e
source-git-commit: 47910a27118a11a8add6cbcba6a614c6314ffe2a
workflow-type: tm+mt
source-wordcount: '2191'
ht-degree: 0%

---

# Technische stichtingen AEM {#aem-technical-foundations}

AEM is een robuust platform dat op bewezen, scalable, en flexibele technologieën wordt voortgebouwd. Dit document geeft een gedetailleerd overzicht van de verschillende onderdelen die AEM vormen en is bedoeld als technische bijlage voor een ontwikkelaar van een complete AEM. Het is niet bedoeld als gids aan de slag. Als u nog geen ervaring hebt met AEM ontwikkeling, raadpleegt u de [Aan de slag met het ontwikkelen van AEM Sites - WKND-zelfstudie](develop-wknd-tutorial.md) als eerste stap.

>[!TIP]
>
>Voordat Adobe naar de kerntechnologieën van AEM gaat, raadt hij aan de [Aan de slag met het ontwikkelen van AEM Sites - WKND-zelfstudie.](develop-wknd-tutorial.md)

## Grondbeginselen {#fundamentals}

Als een modern contentbeheersysteem is AEM gebaseerd op standaardwebtechnologieën:

* De aanvraagresponscyclus (XMLHttpRequest / XMLHttpResponse)
* HTML
* CSS
* JavaScript

De onderliggende inhoudopslagplaats en de bedrijfslogische lagen worden gebouwd rond technologieën van Java:

* JCR
* Sling
* OSGi

## Java Content Repository {#java-content-repository}

De JCR-standaard (Java Content Repository), [JSR 283](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/index.html), geeft een leveranciersonafhankelijke en implementatieonafhankelijke manier aan om inhoud bidirectioneel te benaderen op granulair niveau in een inhoudsopslagplaats. Het productdossier is in het bezit van Adobe Research (Zwitserland) AG.

De [JCR API 2.0](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) verpakking, `javax.jcr.*` wordt gebruikt voor directe toegang tot en manipulatie van inhoud in de repository.

AEM is gebaseerd op een JCR.

## Apache Jackrabbit Oak {#jackrabbit-oak}

[Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/) is een implementatie van een schaalbare en krachtige hiërarchische opslagplaats voor inhoud die als basis kan dienen voor moderne websites van wereldklasse en andere veeleisende toepassingen voor inhoud, conform de JCR-standaard.

Jackrabbit Oak (ook wel &quot;eikenhout&quot; genoemd) is de toepassing van de JCR-norm waarop AEM wordt gebouwd.

## Verwerking van aanvraag voor verzending {#sling-request-processing}

AEM is gemaakt met [Sling](https://sling.apache.org/site/index.html), een toepassingskader van het Web dat op de principes van REST wordt gebaseerd die gemakkelijke ontwikkeling van inhoud-georiënteerde toepassingen verstrekken. Sling gebruikt een JCR-opslagplaats, zoals Apache Jackrabbit Oak, als gegevensopslagplaats. Sling is toegevoegd aan de Apache Software Foundation - meer informatie is te vinden op Apache.

### Inleiding tot verkoop {#introduction-to-sling}

Met Verschuiving is het type inhoud dat moet worden gerenderd niet de eerste verwerkingsoverweging. De belangrijkste overweging is in plaats daarvan of de URL wordt omgezet in een inhoudsobject waarvoor vervolgens een script kan worden gevonden om de rendering uit te voeren. Dit biedt uitstekende ondersteuning voor auteurs van webinhoud om pagina&#39;s samen te stellen die eenvoudig aan hun vereisten kunnen worden aangepast.

De voordelen van deze flexibiliteit worden duidelijk in toepassingen met een groot aantal verschillende inhoudselementen, of wanneer u pagina&#39;s nodig hebt die gemakkelijk kunnen worden aangepast. Met name bij de implementatie van een systeem voor webcontentbeheer, zoals AEM.

Zie [Ontdek de verkoop binnen 15 minuten](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) voor de eerste stappen voor het ontwikkelen met Sling.

In het volgende diagram wordt de resolutie van het script Sling uitgelegd: het toont hoe te om van HTTP- verzoek aan inhoudsknoop, van inhoudsknoop aan middeltype, van middeltype aan manuscript te krijgen en welke scripting variabelen beschikbaar zijn.

![Scriptresolutie voor Apache Sling](assets/sling-cheatsheet-01.png)

Het volgende diagram verklaart alle verborgen, maar krachtige, verzoekparameters u kunt gebruiken wanneer het behandelen van `SlingPostServlet`, de standaardmanager voor alle verzoeken van de POST die u eindeloze opties voor het creëren van, het wijzigen van, het schrappen van, het kopiëren en het bewegen van knopen in de bewaarplaats geeft.

![De SlingPostServlet gebruiken](assets/sling-cheatsheet-02.png)

### Verdelen is Content Centric {#sling-is-content-centric}

Verkopen is *inhoudgericht*. Dit betekent dat de verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* Het eerste doel is de bron (JCR-knooppunt) die de inhoud in zijn bezit heeft
* Ten tweede, wordt de vertegenwoordiging, of het manuscript, gevestigd van de middeleigenschappen in combinatie met bepaalde delen van het verzoek (bijvoorbeeld, selecteurs en/of de uitbreiding)

### RESTful Sling {#restful-sling}

Door zijn inhoud-centric filosofie, voert Sling een REST-oriented server uit en zo kenmerkt een nieuw concept in Web toepassingskaders. De voordelen zijn:

* Zeer RESTful, niet alleen op het oppervlak; bronnen en representaties zijn op de juiste wijze gemodelleerd binnen de server
* Hiermee verwijdert u een of meer gegevensmodellen
   * Andere contentbeheerframeworks vereisen mogelijk URL-structuur, zakelijke objecten en het DB-schema voor toegang tot een bron.
   * Bij het gebruik van Verschuiven wordt dit beperkt tot: URL = resource = JCR-structuur

### URL-decompositie {#url-decomposition}

Bij Sling wordt de verwerking gestuurd door de URL van de gebruikersaanvraag. Dit bepaalt de inhoud die door de aangewezen manuscripten moet worden getoond. Hiervoor wordt informatie opgehaald uit de URL.

Als we de volgende URL analyseren:

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

We kunnen het opsplitsen in samengestelde delen:

| protocol | host |  | inhoudspad | kiezer(s) | extension |  | achtervoegsel |  | param(en) |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **protocol** - HTTPS
* **host** - Domein van de site
* **inhoudspad** - Pad waarin de inhoud wordt aangegeven die moet worden gerenderd en dat wordt gebruikt in combinatie met de extensie; in dit voorbeeld worden ze vertaald naar `tools/spy.html`
* **kiezer(s)** - Wordt gebruikt voor alternatieve methoden om de inhoud te renderen; in dit voorbeeld een printervriendelijke versie in A4-indeling
* **extension** - Inhoudsindeling; geeft ook het script op dat moet worden gebruikt voor rendering
* **achtervoegsel** - Kan worden gebruikt om aanvullende informatie op te geven
* **param(en)** - Alle parameters die vereist zijn voor dynamische inhoud

#### Van URL naar inhoud en scripts {#from-url-to-content-and-scripts}

De beginselen van URL-decompositie gebruiken:

* In de toewijzing wordt het inhoudspad gebruikt dat uit de aanvraag is geëxtraheerd om de bron te zoeken.
* Wanneer het aangewezen middel wordt gevestigd, wordt het sling middeltype gehaald, en gebruikt om van het manuscript de plaats te bepalen dat voor het teruggeven van de inhoud moet worden gebruikt.

De volgende afbeelding illustreert het gebruikte mechanisme, dat in de volgende secties nader zal worden besproken.

![URL-toewijzingsmechanisme](assets/url-mapping.png)

Met Verschuiven geeft u op welk script een bepaalde entiteit wordt gerenderd (door het `sling:resourceType` eigenschap in het knooppunt JCR). Dit mechanisme biedt meer vrijheid dan één waarin het script de gegevensentiteiten benadert (zoals een SQL-instructie in een PHP-script zou doen) omdat een resource meerdere uitvoeringen kan hebben.

#### Toewijzingsverzoeken voor bronnen {#mapping-requests-to-resources}

Het verzoek wordt uitgesplitst en de nodige informatie wordt ingewonnen. De repository wordt gezocht naar de gevraagde resource (content node):

* First Sling controleert of een knoop op de plaats bestaat die in het verzoek wordt gespecificeerd; bijvoorbeeld: `../content/corporate/jobs/developer.html`
* Als geen knoop wordt gevonden, wordt de uitbreiding gelaten vallen en het onderzoek herhaald; bijvoorbeeld: `../content/corporate/jobs/developer`
* Als er geen knooppunt wordt gevonden, retourneert Sling de http-code 404 (Not Found).

Met Sling kunnen andere zaken dan JCR-knooppunten ook bronnen zijn, maar dit is een geavanceerde functie.

### Script zoeken {#locating-the-script}

Wanneer de juiste resource (content node) is gevonden, wordt de **slingermiddeltype** wordt geëxtraheerd. Dit is een pad dat zoekt naar het script dat moet worden gebruikt voor het renderen van de inhoud.

Het pad dat door de `sling:resourceType` kunnen:

* Absoluut
* Relatief ten opzichte van een configuratieparameter

>[!TIP]
>
>Relatieve paden worden aanbevolen door Adobe omdat ze de draagbaarheid verhogen.

Alle verkoopscripts worden opgeslagen in submappen van `/apps` (veranderbaar, gebruikersmanuscripten) of `/libs` (onveranderlijk, systeemmanuscripten), die in deze orde zullen worden gezocht.

Een paar andere punten die u kunt opmerken zijn:

* Wanneer de methode (GET, POST) vereist is, wordt deze in hoofdletters opgegeven, bijvoorbeeld volgens de HTTP-specificatie. `jobs.POST.esp`
* Verschillende scriptengines worden ondersteund, maar de gebruikelijke, aanbevolen scripts zijn HTML en JavaScript.

De lijst met scriptengines die door de opgegeven AEM worden ondersteund, wordt weergegeven in de Felix Management Console ( `http://<host>:<port>/system/console/slingscripting`).

Wanneer u het vorige voorbeeld gebruikt, `sling:resourceType` is `hr/jobs` vervolgens voor:

* GET/HEAD-aanvragen en URL&#39;s die eindigen in `.html` (standaardaanvraagtypen, standaardindeling)
   * Het script wordt `/apps/hr/jobs/jobs.esp`; de laatste sectie van de `sling:resourceType` vormt de bestandsnaam.
* Aanvragen voor POSTEN (alle aanvraagtypen behalve GET/HEAD, de naam van de methode moet in hoofdletters staan)
   * POST wordt gebruikt in de scriptnaam.
   * Het script wordt `/apps/hr/jobs/jobs.POST.esp`.
* URL&#39;s in andere indelingen, die niet eindigen met `.html`
   * Bijvoorbeeld `../content/corporate/jobs/developer.pdf`
   * Het script wordt `/apps/hr/jobs/jobs.pdf.esp`; het achtervoegsel wordt toegevoegd aan de manuscriptnaam.
* URL&#39;s met kiezers
   * Kiezers kunnen worden gebruikt om dezelfde inhoud in een andere indeling weer te geven. Bijvoorbeeld een printervriendelijke versie, een rss-feed of een overzicht.
   * Als we naar een printervriendelijke versie kijken waarin de kiezer mogelijk `print`; zoals in `../content/corporate/jobs/developer.print.html`
   * Het script wordt `/apps/hr/jobs/jobs.print.esp`; de kiezer wordt toegevoegd aan de scriptnaam.
* Indien niet `sling:resourceType` is toen gedefinieerd:
   * Het inhoudspad wordt gebruikt om te zoeken naar een geschikt script (als het pad is gebaseerd op `ResourceTypeProvider` is actief).
   * Het script voor `../content/corporate/jobs/developer.html` zou een zoekopdracht genereren in `/apps/content/corporate/jobs/`.
   * Het primaire knooppunttype zal worden gebruikt.
* Als er helemaal geen script wordt gevonden, wordt het standaardscript gebruikt.
   * De standaardvertoning wordt momenteel ondersteund als onbewerkte tekst (`.txt`), HTML (`.html`) en JSON (`.json`), die allemaal de eigenschappen van de knoop (geschikt geformatteerd) zullen vermelden. De standaarduitvoering voor de extensie `.res`, of aanvragen zonder een verzoek om verlenging, de bron spool (waar mogelijk).
* Voor http-foutafhandeling (codes 403 of 404) wordt met Sling gezocht naar een script op:
   * De locatie `/apps/sling/servlet/errorhandler` voor aangepaste scripts
   * Of de locatie van het standaardscript `/libs/sling/servlet/errorhandler/404.jsp`

Als er meerdere scripts van toepassing zijn voor een bepaalde aanvraag, wordt het script met de beste overeenkomst geselecteerd. Hoe specifieker een match is, hoe beter dat is; met andere woorden, de meer selecteur past beter aan, ongeacht om het even welke verzoekuitbreiding of methodenamen.

Neem bijvoorbeeld een verzoek om toegang tot de bron

* `/content/corporate/jobs/developer.print.a4.html`

van het type

* `sling:resourceType="hr/jobs"`

Ervan uitgaande dat de volgende lijst met scripts op de juiste locatie staat:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Vervolgens zou de volgorde van voorkeur (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1) zijn.

Naast de typen bronnen (die voornamelijk worden gedefinieerd door de `sling:resourceType` eigenschap) er is ook het resource super type. Dit wordt in het algemeen door de `sling:resourceSuperType` eigenschap. Deze super types worden ook overwogen wanneer het proberen om een manuscript te vinden. Het voordeel van resource super types is dat zij een hiërarchie van middelen kunnen vormen waar het standaardmiddeltype `sling/servlet/default` (wordt gebruikt door de standaardservlets) is in feite de wortel.

Het resource super type van een middel kan op twee manieren worden bepaald:

* door de `sling:resourceSuperType` eigenschap van de bron.
* door de `sling:resourceSuperType` eigenschap van het knooppunt waaraan de `sling:resourceType` punten.

Bijvoorbeeld:

* `/`
   * `a`
   * `b`
      * `sling:resourceSuperType = a`
   * `c`
      * `sling:resourceSuperType = b`
   * `x`
      * `sling:resourceType = c`
   * `y`
      * `sling:resourceType = c`
      * `sling:resourceSuperType = a`

De typehiërarchie van:

* `/x`
   * Is `[ c, b, a, <default>]`
* While for `/y`
   * De hiërarchie is `[ c, a, <default>]`

Dit komt omdat `/y` de `sling:resourceSuperType` onroerend goed `/x` niet en daarom wordt zijn supertype genomen van zijn middeltype.

#### Sling-scripts kunnen niet rechtstreeks worden aangeroepen {#sling-scripts-cannot-be-called-directly}

Binnen Verschuiving, kunnen de manuscripten niet direct worden geroepen aangezien dit het strikte concept van een REST server zou breken; u zou middelen en vertegenwoordiging mengen.

Als u de vertegenwoordiging (het manuscript) direct roept u het middel binnen uw manuscript verbergt, zodat weet het kader (het Schrapen) niet meer over het. Zo verliest u bepaalde eigenschappen:

* Automatische afhandeling van andere http-methoden dan GET, waaronder:
   * POST, PUT, DELETE die met een sling standaardimplementatie worden behandeld
   * De `POST.jsp` script in uw `sling:resourceType` locatie
* Uw codearchitectuur is niet meer zo schoon en zo duidelijk gestructureerd als het zou moeten zijn; van primordiaal belang voor grootschalige ontwikkeling

### Verkopen-API {#sling-api}

Hiervoor wordt het Sling API-pakket gebruikt, `org.apache.sling.*`en tagbibliotheken.

### Verwijzen naar bestaande elementen met gebruik van sling:include {#referencing-existing-elements-using-sling-include}

Een laatste overweging is de noodzaak om naar bestaande elementen in de scripts te verwijzen.

Complexere scripts (samengevoegde scripts) moeten mogelijk toegang krijgen tot meerdere bronnen (bijvoorbeeld navigatie, zijbalk, voettekst, elementen van een lijst) en dit doen door de *resource*.

Hiervoor kunt u de opdracht `sling:include("/<path>/<resource>")` gebruiken. Dit zal effectief de definitie van het referenced middel omvatten.

## OSGi {#osgi}

OSGi (Open het Initiatief van de Gateway van de Diensten) bepaalt een architectuur voor het ontwikkelen en het opstellen van modulaire toepassingen en bibliotheken (het is ook genoemd geworden het Dynamische Systeem van de Module voor Java). De containers OSGi staan u toe om uw toepassing in individuele modules (zijn jar dossiers met extra meta-informatie en geroepen bundels in terminologie OSGi) te breken en de onderlinge afhankelijkheden te beheren met:

* Services geïmplementeerd in de container
* Een contract tussen de container en uw toepassing

Deze diensten en contracten verstrekken een architectuur die individuele elementen toelaat om elkaar voor samenwerking dynamisch te ontdekken.

Een OSGi-framework biedt u vervolgens dynamisch laden/verwijderen, configureren en beheren van deze bundels, zonder dat u opnieuw moet starten.

>[!NOTE]
>
>Volledige informatie over OSGi-technologie is te vinden op de website [OSGi-website](https://www.osgi.org).
>
>De pagina Basisonderwijs bevat met name een verzameling presentaties en zelfstudies.

Deze architectuur staat u toe om het Verkopen met toepassing specifieke modules uit te breiden. Bij Sling wordt, en daarom AEM, de [Apache Felix](https://felix.apache.org/) uitvoering van de OSGi. Het zijn beide inzamelingen van bundels OSGi die binnen een kader OSGi lopen.

Hierdoor kunt u de volgende handelingen uitvoeren op elk van de pakketten in uw installatie:

* Installeren
* Start
* Stoppen
* Bijwerken
* Verwijderen
* Zie de huidige status
* Meer gedetailleerde informatie (bijvoorbeeld symbolische naam, versie, locatie, enz.) over de specifieke bundels openen

Zie [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md) voor meer informatie .

## Structuur in de opslagplaats {#structure-within-the-repository}

De volgende lijst geeft een overzicht van de structuur die u in de repository zult zien.

* `/apps` - Aanvraag bevat componentdefinities die specifiek zijn voor uw website. De componenten die u ontwikkelt kunnen op uit de vakcomponenten worden gebaseerd beschikbaar bij `/libs/core/wcm/components`.
* `/content` - Inhoud die voor uw website is gemaakt.
* `/etc`
* `/home` - Informatie over gebruikers en groepen.
* `/libs` - Bibliotheken en definities die tot de kern van AEM behoren. De submappen in `/libs` vertegenwoordigen de functies voor AEM buiten het vak. De inhoud in `/libs` mogen niet worden gewijzigd. Functies die specifiek zijn voor uw website, kunt u vinden onder `/apps`.
* `/tmp` - Tijdelijke werkruimte.
* `/var` - bestanden die door het systeem worden gewijzigd en bijgewerkt; zoals auditlogboeken, statistieken, gebeurtenisafhandeling.

>[!CAUTION]
>
>Wijzigingen in deze structuur, of in de bestanden daarin, moeten met de nodige voorzichtigheid worden aangebracht. Zorg ervoor dat u de implicaties van om het even welke veranderingen volledig begrijpt u aanbrengt.
>
>U mag niets wijzigen in het dialoogvenster `/libs` pad. Voor configuratie en andere veranderingen kopieer het punt van `/libs` tot `/apps` en brengt alle wijzigingen aan in `/apps`.
