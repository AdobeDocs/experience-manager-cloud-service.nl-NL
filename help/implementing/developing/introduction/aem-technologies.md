---
title: Technische stichtingen AEM
description: Een overzicht van de technische fundamenten van AEM, inclusief hoe AEM is gestructureerd en fundamentele technologieën zoals JCR, Sling en OSGi.
exl-id: ab6e7fe9-a25d-4351-a005-f4466cc0f40e
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2130'
ht-degree: 0%

---

# Technische stichtingen AEM {#aem-technical-foundations}

AEM is een robuust platform dat op bewezen, scalable, en flexibele technologieën wordt voortgebouwd. Dit document biedt een gedetailleerd overzicht van de verschillende onderdelen die AEM vormen en is bedoeld als een technisch aanhangsel voor een ontwikkelaar van een complete AEM. Het is niet bedoeld als gids aan de slag. Als u nog geen ervaring hebt met AEM ontwikkeling, raadpleegt u [Aan de slag met het ontwikkelen van AEM Sites - WKND-zelfstudie](develop-wknd-tutorial.md) als eerste stap.

>[!TIP]
>
>Voordat de Adobe in de kerntechnologieën van AEM gaat werken, beveelt zij aan de [Aan de slag met het ontwikkelen van AEM Sites - WKND-zelfstudie.](develop-wknd-tutorial.md)

## Grondbeginselen {#fundamentals}

Als een modern contentbeheersysteem is AEM gebaseerd op standaardwebtechnologieën:

* De aanvraagresponscyclus (XMLHttpRequest / XMLHttpResponse)
* HTML
* CSS
* JavaScript

De onderliggende inhoudopslagplaats en de bedrijfslogische lagen worden gebouwd rond technologieën Java™:

* JCR
* Sling
* OSGi

## Java™ Content Repository {#java-content-repository}

De JCR-standaard (Java™ Content Repository), [JSR 283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html), geeft een leveranciersonafhankelijke en implementatieonafhankelijke manier aan om inhoud bidirectioneel te benaderen op granulair niveau in een inhoudsopslagplaats. Het productdossier is in het bezit van Adobe Research (Zwitserland) AG.

De [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) verpakking, `javax.jcr.*` wordt gebruikt voor directe toegang tot en manipulatie van inhoud in de repository.

AEM is gebaseerd op een JCR.

## Apache Jackrabbit Oak {#jackrabbit-oak}

[Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/) is een implementatie van een schaalbare en krachtige hiërarchische opslagplaats voor inhoud die als basis kan dienen voor moderne websites van wereldklasse en andere veeleisende toepassingen voor inhoud, conform de JCR-standaard.

Jackrabbit Oak (ook wel &quot;eikenhout&quot; genoemd) is de toepassing van de JCR-norm waarop AEM wordt gebouwd.

## Verwerking van aanvraag voor verzending {#sling-request-processing}

AEM is gemaakt met [Sling](https://sling.apache.org/index.html), een toepassingskader van het Web dat op de principes van REST wordt gebaseerd die gemakkelijke ontwikkeling van inhoud-georiënteerde toepassingen verstrekken. Sling gebruikt een JCR-opslagplaats, zoals Apache Jackrabbit Oak, als gegevensopslagplaats. Sling is toegevoegd aan de Apache Software Foundation - meer informatie is te vinden op Apache.

### Inleiding tot verkoop {#introduction-to-sling}

Met Verschuiving is het type inhoud dat moet worden gerenderd niet de eerste verwerkingsoverweging. In plaats daarvan wordt vooral nagegaan of de URL wordt omgezet in een inhoudsobject waarvoor vervolgens een script kan worden gevonden om de rendering uit te voeren. Dit proces biedt uitstekende ondersteuning voor auteurs van webinhoud om pagina&#39;s samen te stellen die eenvoudig aan hun vereisten kunnen worden aangepast.

De voordelen van deze flexibiliteit worden duidelijk in toepassingen met een groot aantal verschillende inhoudselementen, of wanneer u pagina&#39;s nodig hebt die gemakkelijk kunnen worden aangepast. Met name bij de implementatie van een systeem voor webcontentbeheer, zoals AEM.

Zie [Ontdek de verkoop binnen 15 minuten](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) voor de eerste stappen voor het ontwikkelen met Sling.

In het volgende diagram wordt de resolutie van het script Sling uitgelegd. Het toont hoe te om van HTTP- verzoek aan inhoudsknoop, van inhoudsknoop aan middeltype, van middeltype aan manuscript te krijgen en welke scripting variabelen beschikbaar zijn.

![Scriptresolutie voor Apache Sling](assets/sling-cheatsheet-01.png)

Het volgende diagram verklaart de verborgen, maar krachtige, verzoekparameters die u met kunt gebruiken `SlingPostServlet`, de standaardmanager voor alle verzoeken van de POST. De manager geeft u eindeloze opties voor het creëren van, het wijzigen van, het schrappen van, het kopiëren van, en het bewegen van knopen in de bewaarplaats.

![De SlingPostServlet gebruiken](assets/sling-cheatsheet-02.png)

### Verdelen is Content Centric {#sling-is-content-centric}

Verkopen is *inhoudgericht*. Het betekent dat de verwerking op de inhoud wordt geconcentreerd aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een opslagplaats knoop) in kaart wordt gebracht:

* Het eerste doel is de bron (JCR-knooppunt) die de inhoud in zijn bezit heeft
* Ten tweede bevindt de representatie, of het script, zich in de eigenschappen resource met bepaalde onderdelen van de aanvraag (bijvoorbeeld kiezers en/of de extensie)

### RESTful Sling {#restful-sling}

Door zijn inhoud-centric filosofie, voert Sling een REST-oriented server uit en zo kenmerkt een nieuw concept in Web toepassingskaders. De voordelen zijn:

* RESTful, niet alleen op de oppervlakte; de middelen en de vertegenwoordiging worden correct gemodelleerd binnen de server
* Hiermee verwijdert u een of meer gegevensmodellen
   * Andere contentbeheerframeworks vereisen mogelijk URL-structuur, zakelijke objecten en het DB-schema voor toegang tot een bron.
   * Door Sling te gebruiken, wordt het gereduceerd tot: URL = resource = JCR-structuur

### URL-decompositie {#url-decomposition}

Bij Sling wordt de verwerking aangedreven door de URL van het gebruikersverzoek. Hiermee wordt de inhoud gedefinieerd die moet worden weergegeven met de juiste scripts en wordt informatie uit de URL geëxtraheerd.

De volgende URL analyseren:

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

U kunt het onderverdelen in zijn samengestelde delen:

| protocol | host |  | inhoudspad | kiezers | extension |  | achtervoegsel |  | param |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **protocol** - HTTPS
* **host** - Domein van de site
* **inhoudspad** - Pad met de inhoud die moet worden gerenderd en wordt gebruikt met de extensie. In dit voorbeeld wordt het vertaald naar `tools/spy.html`
* **kiezers** - Wordt gebruikt voor alternatieve methoden om de inhoud te renderen; in dit voorbeeld een printervriendelijke versie in A4-indeling
* **extension** - Inhoudsindeling; geeft ook het script op dat moet worden gebruikt voor rendering
* **achtervoegsel** - Kan worden gebruikt om aanvullende informatie op te geven
* **param** - Alle parameters die vereist zijn voor dynamische inhoud

#### Van URL naar inhoud en scripts {#from-url-to-content-and-scripts}

De beginselen van URL-decompositie gebruiken:

* In de toewijzing wordt het inhoudspad gebruikt dat uit de aanvraag is geëxtraheerd om de bron te zoeken.
* Wanneer het aangewezen middel wordt gevestigd, wordt het sling middeltype gehaald, en gebruikt om van het manuscript de plaats te bepalen dat voor het teruggeven van de inhoud moet worden gebruikt.

De volgende afbeelding illustreert het gebruikte mechanisme, dat in de volgende secties nader wordt besproken.

![URL-toewijzingsmechanisme](assets/url-mapping.png)

Met Verschuiven geeft u op welk script een bepaalde entiteit wordt gerenderd (door het dialoogvenster `sling:resourceType` eigenschap in het knooppunt JCR). Dit mechanisme biedt meer vrijheid dan één waarin het script de gegevensentiteiten benadert (zoals een SQL-instructie in een PHP-script zou doen) omdat een resource meerdere uitvoeringen kan hebben.

#### Toewijzingsverzoeken voor bronnen {#mapping-requests-to-resources}

Het verzoek wordt uitgesplitst en de nodige informatie wordt ingewonnen. De repository wordt gezocht naar de gevraagde resource (content node):

* First Sling controleert of een knooppunt bestaat op de locatie die in de aanvraag is opgegeven, bijvoorbeeld `../content/corporate/jobs/developer.html`
* Als er geen knooppunt wordt gevonden, wordt de extensie verwijderd en wordt de zoekopdracht herhaald, bijvoorbeeld `../content/corporate/jobs/developer`
* Als er geen knooppunt wordt gevonden, retourneert Sling de http-code 404 (Not Found).

Met Sling kunnen andere zaken dan JCR-knooppunten ook bronnen zijn, maar deze functionaliteit is een geavanceerde functie.

### Script zoeken {#locating-the-script}

Wanneer de juiste resource (content node) is gevonden, wordt de **slingermiddeltype** wordt geëxtraheerd. Dit pad zoekt naar het script dat moet worden gebruikt voor het renderen van de inhoud.

Het pad dat wordt opgegeven door de `sling:resourceType` kunnen:

* Absoluut
* Relatief ten opzichte van een configuratieparameter

>[!TIP]
>
>Relatieve paden worden door de Adobe aanbevolen omdat ze de draagbaarheid verhogen.

Alle verkoopscripts worden opgeslagen in submappen van `/apps` (veranderbaar, gebruikersmanuscripten) of `/libs` (onveranderlijk, systeemmanuscripten), die in deze orde wordt gezocht.

Een paar andere punten die u kunt opmerken zijn:

* Wanneer de methode (GET, POST) vereist is, wordt deze in hoofdletters opgegeven, bijvoorbeeld volgens de HTTP-specificatie. `jobs.POST.esp`
* Verschillende scriptengines worden ondersteund, maar de gebruikelijke, aanbevolen scripts zijn HTML en JavaScript.

De lijst met scriptengines die door de opgegeven AEM worden ondersteund, wordt weergegeven in de Felix Management Console ( `http://<host>:<port>/system/console/slingscripting`).

Wanneer u het vorige voorbeeld gebruikt, `sling:resourceType` is `hr/jobs` vervolgens voor:

* GET/HEAD-aanvragen en URL&#39;s die eindigen in `.html` (standaardaanvraagtypen, standaardindeling)
   * Het script is `/apps/hr/jobs/jobs.esp`; de laatste sectie van de `sling:resourceType` vormt de bestandsnaam.
* Aanvragen voor POSTEN (alle aanvraagtypen behalve GET/HEAD, de naam van de methode moet in hoofdletters staan)
   * POST wordt gebruikt in de manuscriptnaam.
   * Het script is `/apps/hr/jobs/jobs.POST.esp`.
* URL&#39;s in andere indelingen, die niet eindigen met `.html`
   * Bijvoorbeeld: `../content/corporate/jobs/developer.pdf`
   * Het script is `/apps/hr/jobs/jobs.pdf.esp`; het achtervoegsel wordt toegevoegd aan de scriptnaam.
* URL&#39;s met kiezers
   * Kiezers kunnen worden gebruikt om dezelfde inhoud in een andere indeling weer te geven. Bijvoorbeeld een printervriendelijke versie, een rss feed of een samenvatting.
   * Als u een printervriendelijke versie bekijkt waarin de kiezer mogelijk `print`; zoals in `../content/corporate/jobs/developer.print.html`
   * Het script is `/apps/hr/jobs/jobs.print.esp`; de kiezer wordt aan de scriptnaam toegevoegd.
* Zo nee, `sling:resourceType` wordt dan gedefinieerd:
   * Het inhoudspad wordt gebruikt om te zoeken naar een geschikt script (als het pad is gebaseerd op `ResourceTypeProvider` is actief).
   * Het script voor bijvoorbeeld `../content/corporate/jobs/developer.html` zou een zoekopdracht genereren in `/apps/content/corporate/jobs/`.
   * Het primaire knooppunttype wordt gebruikt.
* Als er geen script wordt gevonden, wordt het standaardscript gebruikt.
   * De standaardvertoning wordt ondersteund als onbewerkte tekst (`.txt`), HTML (`.html`), en JSON (`.json`), die allemaal de eigenschappen van de knoop (behoorlijk geformatteerd) een lijst maken. De standaarduitvoering voor de extensie `.res`, of aanvragen zonder een verzoek om verlenging, de bron spool (waar mogelijk).
* Bij http-foutafhandeling (codes 403 of 404) zoekt Sling naar een script op:
   * De locatie `/apps/sling/servlet/errorhandler` voor aangepaste scripts
   * Of de locatie van het standaardscript `/libs/sling/servlet/errorhandler/404.jsp`

Als er meerdere scripts van toepassing zijn voor een bepaalde aanvraag, wordt het script met de beste overeenkomst geselecteerd. Hoe specifieker een overeenkomst is, des te beter deze is. Met andere woorden, hoe meer kiezer het beste aanpast, ongeacht of de aanvraagextensie of methodenamen overeenkomen.

Neem bijvoorbeeld een verzoek om toegang tot de bron

* `/content/corporate/jobs/developer.print.a4.html`

Van type

* `sling:resourceType="hr/jobs"`

Ervan uitgaande dat u de volgende lijst met scripts op de juiste locatie hebt:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Vervolgens zou de volgorde van voorkeur (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1) zijn.

Naast de typen bronnen (die voornamelijk worden gedefinieerd door de `sling:resourceType` eigenschap), is er ook het resource super type. Dit type wordt aangegeven door de `sling:resourceSuperType` eigenschap. Deze super types worden ook overwogen wanneer het proberen om een manuscript te vinden. Het voordeel van resource super types is dat zij een hiërarchie van middelen kunnen vormen waar het standaardmiddeltype `sling/servlet/default` (wordt gebruikt door de standaardservlets) is in feite de wortel.

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

De reden is dat `/y` heeft de `sling:resourceSuperType` eigendom, `/x` niet en daarom wordt zijn supertype genomen van zijn middeltype.

#### Sling-scripts kunnen niet rechtstreeks worden aangeroepen {#sling-scripts-cannot-be-called-directly}

Binnen Verschuiving, kunnen de manuscripten niet direct worden geroepen omdat het het strikte concept van een server van het SPEL zou breken; u zou middelen en vertegenwoordiging mengen.

Als u de vertegenwoordiging (het manuscript) direct roept u het middel binnen uw manuscript verbergt, zodat weet het kader (het Schrapen) niet meer over het. Zo verliest u bepaalde eigenschappen:

* Automatische afhandeling van andere http-methoden dan GET, waaronder:
   * POST, PUT, DELETE die met een sling standaardimplementatie wordt behandeld
   * De `POST.jsp` script in uw `sling:resourceType` locatie
* Uw codearchitectuur is niet meer zo schoon en zo duidelijk gestructureerd als het zou moeten zijn; van primordiaal belang voor grootschalige ontwikkeling

### Verkopen-API {#sling-api}

Gebruikt het Sling API-pakket, `org.apache.sling.*`en tagbibliotheken.

### Verwijzen naar bestaande elementen met gebruik van sling:include {#referencing-existing-elements-using-sling-include}

Een laatste overweging is de noodzaak om naar bestaande elementen in de scripts te verwijzen.

Complexere scripts (samengevoegde scripts) hebben toegang tot meerdere bronnen (bijvoorbeeld navigatie, zijbalk, voettekst, elementen van een lijst) en doen dit door de *resource*.

In dit geval kunt u de opdracht `sling:include("/<path>/<resource>")` gebruiken. Het omvat effectief de definitie van het referenced middel.

## OSGi {#osgi}

OSGi (Open Services Gateway Initiative) definieert een architectuur voor het ontwikkelen en implementeren van modulaire toepassingen en bibliotheken (dit wordt ook wel het Dynamic Module System voor Java™ genoemd). De containers OSGi staan u toe om uw toepassing in individuele modules (zijn jar dossiers met extra meta-informatie en geroepen bundels in terminologie OSGi) te breken en de onderlinge afhankelijkheden te beheren met:

* Services geïmplementeerd in de container
* Een contract tussen de container en uw toepassing

Deze diensten en contracten verstrekken een architectuur die individuele elementen toelaat om elkaar voor samenwerking dynamisch te ontdekken.

Een OSGi-framework biedt u vervolgens dynamisch laden/verwijderen, configureren en beheren van deze bundels, zonder dat u opnieuw moet starten.

>[!NOTE]
>
>Volledige informatie over OSGi-technologie is te vinden op de website [OSGi-website](https://www.osgi.org).
>
>De pagina Basisonderwijs bevat met name een verzameling presentaties en zelfstudies.

Deze architectuur laat u het Verkopen met toepassing-specifieke modules uitbreiden. Bij Sling wordt, en daarom AEM, de [Apache Felix](https://felix.apache.org/documentation/index.html) uitvoering van de OSGi. Het zijn beide inzamelingen van bundels OSGi die binnen een kader OSGi lopen.

Met deze functionaliteit kunt u de volgende handelingen uitvoeren op elk van de pakketten in uw installatie:

* Installeren
* Start
* Stoppen
* Bijwerken
* Verwijderen
* Zie laatste status
* Meer gedetailleerde informatie over specifieke bundels, bijvoorbeeld symbolische naam, versie en locatie, bekijken

Zie [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md) voor meer informatie .

## Structuur in de opslagplaats {#structure-within-the-repository}

De volgende lijst geeft een overzicht van de structuur die u in de repository ziet.

* `/apps` - Toepassingsgerelateerd; bevat componentdefinities die specifiek zijn voor uw website. De componenten die u ontwikkelt kunnen op uit de vakcomponenten worden gebaseerd beschikbaar bij `/libs/core/wcm/components`.
* `/content` - Inhoud gemaakt voor uw website.
* `/etc`
* `/home` - Informatie over gebruikers en groepen.
* `/libs` - Bibliotheken en definities die tot de kern van AEM behoren. De submappen in `/libs` vertegenwoordigen de functies voor AEM buiten het vak. De inhoud in `/libs` mogen niet worden gewijzigd. Functies die specifiek zijn voor uw website, kunt u vinden onder `/apps`.
* `/tmp` - Tijdelijke werkruimte.
* `/var` - Bestanden die door het systeem worden gewijzigd en bijgewerkt, zoals auditlogboeken, statistieken, gebeurtenisafhandeling.

>[!CAUTION]
>
>Wijzigingen in deze structuur, of in de bestanden daarin, moeten met de nodige voorzichtigheid worden aangebracht. Zorg ervoor dat u de implicaties van om het even welke veranderingen volledig begrijpt u aanbrengt.
>
>Wijzig niets in de `/libs` pad. Voor configuratie en andere veranderingen, kopieer het punt van `/libs` tot `/apps` en brengt alle wijzigingen aan in `/apps`.
