---
title: Inhoud leveren
description: 'Inhoud leveren '
translation-type: tm+mt
source-git-commit: 149b7dd07ff06a0053eae3c9b6c22ea612fdb4e3

---


# Inhoud leveren in AEM als cloudservice {#content-delivery}

Op de huidige pagina vindt u details van de inhoud van de publicatieservice in AEM als een Cloud Service. De levering van de de dienstinhoud van de publicatie omvat:

* CDN (wordt meestal beheerd door Adobe)
* AEM-verzender
* AEM-publicatie

De gegevensstroom is als volgt:

1. De URL wordt toegevoegd in de browser
1. Verzoek dat aan CDN wordt gemaakt die in DNS aan dat domein wordt toegewezen
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op CDN, geeft CDN deze aan de browser
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de CDN (reverse-proxy) de dispatcher aan
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op de verzender, wordt deze naar de CDN verzonden
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de verzender (reverse-proxy) de AEM-publicatie aan
1. De inhoud wordt gerenderd door de browser, die de inhoud mogelijk ook in cache plaatst, afhankelijk van de kopteksten

Het inhoudstype HTML/tekst wordt geplaatst om na 300s (5 minuten) bij de verzender laag te verlopen, een drempel die zowel het verzender geheime voorgeheugen als CDN respecteren. Tijdens herplaatsingen van de publicatiedienst, wordt het verzendechergeheime voorgeheugen ontruimd en daarna opgewarmd alvorens nieuwe publicatieknooppunten verkeer goedkeuren.

De secties hieronder verstrekken meer detail over inhoudslevering, met inbegrip van configuratie CDN en caching.

Informatie over replicatie van de auteursdienst aan de publicatieservice is [hier](/help/operations/replication.md)beschikbaar.

## CDN {#cdn}

AEM als Cloud Service wordt geleverd met een ingebouwde CDN. Het is vooral de bedoeling de latentie te verminderen door cachebare inhoud van de CDN-knooppunten aan de rand, bij de browser, te leveren. Het wordt volledig beheerd en gevormd voor optimale prestaties van toepassingen AEM.

In totaal biedt AEM twee opties:

1. AEM Beheerde CDN - AEM&#39;s &#39;out-of-box&#39; CDN. Het is een strak geïntegreerde optie en vereist geen zware klanteninvestering in het steunen van de integratie CDN met AEM.
1. Door de klant beheerde CDN verwijst naar een door AEM beheerde CDN. De klant wijst zijn eigen CDN aan een CDN die buiten de box van AEM valt. De klant zal nog hun eigen CDN moeten beheren, maar de investering in de integratie met AEM is gematigd.

De eerste optie zou aan de meeste van de klantenprestaties en veiligheidsvereisten moeten voldoen. Bovendien vereist het minimale klanteninspanning.

De tweede mogelijkheid wordt per geval toegestaan. Het besluit is gebaseerd op het voldoen aan bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun CDN verkoper heeft die moeilijk is te verlaten.

Hieronder ziet u een beslissingsmatrix waarmee de twee opties worden vergeleken. Meer gedetailleerde informatie vindt u in de volgende secties.

| Details | Door AEM beheerde CDN | Door de klant beheerde CDN verwijst naar AEM CDN |
|---|---|---|
| **Klantenservice** | Geen, het is volledig geïntegreerd. U hoeft alleen CNAME naar door AEM beheerde CDN te wijzen. | Matige klanteninvestering. De klant moet zijn eigen CDN beheren. |
| **Voorwaarden** | Geen | Bestaande CDN die te vervangen is. moet een geslaagde belastingstest aantonen voordat hij in leven wordt gehouden. |
| **CDN-expertise** | Geen | Vereist minstens één middel van de deeltijdtechniek met gedetailleerde kennis CDN die CDN van de klant kan vormen. |
| **Beveiliging** | Beheerd door Adobe. | Beheerd door Adobe (en optioneel door de klant op hun eigen CDN). |
| **Prestaties** | Geoptimaliseerd door Adobe. | Zal van sommige mogelijkheden van AEM CDN profiteren, maar potentieel een kleine prestatiesklap toe te schrijven aan de extra hop. **Opmerking**: Hops from customer CDN to Fastly CDN likely to be effective.) |
| **Caching** | Ondersteunt cachekoppen die worden toegepast op de dispatcher. | Ondersteunt cachekoppen die worden toegepast op de dispatcher. |
| **Compressiemogelijkheden voor afbeeldingen en video** | Kan werken met dynamische media van Adobe. | Kan werken met Adobe Dynamic Media of CDN-afbeelding/video-oplossing die door klanten wordt beheerd. |

### Door AEM beheerde CDN {#aem-managed-cdn}

Voorbereiden op de levering van inhoud met behulp van de CDN van Adobe-versie buiten de doos is eenvoudig, zoals hieronder wordt beschreven:

1. U geeft het ondertekende SSL-certificaat en de geheime sleutel aan Adobe door een koppeling te delen naar een beveiligd formulier met deze gegevens. Coördineer deze taak met de klantenondersteuning.
   **Opmerking:** Aem als de Dienst van de Wolk steunt geen domein Gevalideerde (DV) certificaten.
1. U moet de klantenondersteuning op de hoogte stellen:
   * welk aangepast domein moet worden gekoppeld aan een bepaalde omgeving, zoals gedefinieerd door de programma-id en de omgeving-id.
   * als om het even welk IP fluitend nodig is om verkeer tot een bepaald milieu te beperken.
1. De steun van de klant zal dan met u de timing voor een CNAME DNS verslag coördineren, richtend hun FQDN aan `adobe-aem.map.fastly.net`.
1. U wordt op de hoogte gesteld wanneer de SSL-certificaten verlopen, zodat u de nieuwe SSL-certificaten opnieuw kunt verzenden.

**Beperking van het verkeer**

Standaard kan voor een CDN-installatie onder beheer van Adobe, al het openbaar verkeer zijn weg maken naar de publicatieservice, voor zowel productie- als niet-productie (ontwikkeling en stadium)-omgevingen. Als u verkeer aan de publicatiedienst voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) zou u met klantensteun moeten werken om deze beperkingen te vormen.

### CDN van klant wijst naar door AEM beheerde CDN {#point-to-point-CDN}

Gesteund als u uw bestaande CDN wilt gebruiken, maar kan niet aan de vereisten van een Door Klant beheerde CDN voldoen. In dit geval beheert u uw eigen CDN, maar wijst u naar de beheerde CDN van Adobe.

Houd er rekening mee dat:

1. U moet een bestaande CDN hebben.
1. Je moet het beheren.
1. U moet CDN kunnen vormen om met Aem als Dienst van de Wolk te werken - zie de configuratieinstructies hieronder.
1. U moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
1. U moet een ladingstest uitvoeren en met succes overgaan alvorens aan productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host` koptekst in met de domeinnaam.
1. Stel de Hostkop in met het oorspronkelijke domein. Dit is de invoer van de CDN van Adobe. De waarde moet afkomstig zijn van Adobe.
1. Verzend de kopbal SNI naar de oorsprong. Net als de Hostkop moet de sni-header het oorspronkelijke domein zijn.
1. Plaats `X-Edge-Key`, die nodig is om verkeer aan de servers van AEM correct te leiden. De waarde moet afkomstig zijn van Adobe.

Voorafgaand aan het goedkeuren van levend verkeer, zou u met de klantensteun van Adobe moeten bevestigen dat het verkeer van begin tot eind het verpletteren correct functioneert.

## Caching {#caching}

Caching bij CDN kan worden gevormd door dispatcherregels te gebruiken. Merk op dat de verzender ook de resulterende kopballen van de geheim voorgeheugenvervalsing naleeft als in de verzender configuratie `enableTTL` wordt toegelaten, die impliceert dat het specifieke inhoud zelfs buiten inhoud zal verfrissen die opnieuw wordt gepubliceerd.

### HTML/Text {#html-text}

* door gebrek, caching door browser voor vijf minuten, die op de geheim voorgeheugen-controle kopbal wordt gebaseerd door de apache laag. De CDN neemt deze waarde ook in acht.
* U kunt overschrijven voor alle HTML/Text-inhoud door de `EXPIRATION_TIME` variabele te definiëren in het `global.vars` gebruik van de AEM als hulpprogramma&#39;s van de SDK van de Cloud Service.

U moet ervoor zorgen dat een bestand onder `src/conf.dispatcher.d/cache` de volgende regel heeft:

```
/0000
{ /glob "*" /type "allow" }
```

* kan op een fijner korrelig niveau door de volgende richtlijnen worden met voeten getreden apache mod_headers:

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200"
</LocationMatch>
```

U moet ervoor zorgen dat een bestand onder `src/conf.dispatcher.d/cache` de volgende regel heeft (in de standaardconfiguratie):

```
/0000
{ /glob "*" /type "allow" }
```

* Merk op dat andere methodes, met inbegrip van het [verzender-ttl AEM ACS-Commons project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), geen waarden met succes zullen met voeten treden.

### Client-Side bibliotheken (js, css) {#client-side-libraries}

* door het clientbibliotheekframework van AEM te gebruiken, worden JavaScript- en CSS-code zodanig gegenereerd dat browsers deze oneindig in cache kunnen plaatsen, aangezien eventuele wijzigingen zich manifesteren als nieuwe bestanden met een uniek pad.  Met andere woorden, HTML-code die verwijst naar de clientbibliotheken, wordt naar wens geproduceerd, zodat klanten nieuwe inhoud kunnen ervaren terwijl deze wordt gepubliceerd. Het cache-control wordt ingesteld op &#39;onveranderlijk&#39; of op 30 dagen voor oudere browsers die de waarde &#39;onveranderlijk&#39; niet respecteren.
* Zie de sectie Bibliotheken aan de [clientzijde en de consistentie](#content-consistency) van de versie voor meer informatie.

### Afbeeldingen en inhoud die groot genoeg is en in blokopslag is opgeslagen {#images}

* standaard niet in cache geplaatst
* kan op fijner korrelig niveau worden ingesteld door de volgende `mod_headers` richtlijnen van apache:

```
<LocationMatch "^.*.jpeg$">
    Header set Cache-Control "max-age=222"
</LocationMatch>
```

U moet ervoor zorgen dat een bestand onder src/conf.dispatcher.d/cache de volgende regel heeft (in de standaardconfiguratie):

```
/0000
{ /glob "*" /type "allow" }
```

Zorg ervoor dat elementen die bedoeld zijn om privé te blijven in plaats van in cache te worden opgeslagen, geen deel uitmaken van de LocationMatch-instructiefilters.

* Merk op dat andere methodes, met inbegrip van het [verzender-ttl AEM ACS-Commons project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), geen waarden met succes zullen met voeten treden.

### Andere inhoudstypen in nodenarchief {#other-content}

* geen standaardcaching
* standaard kan niet worden ingesteld met de `EXPIRATION_TIME` variabele die wordt gebruikt voor bestandstypen html/text
* cache-vervaldatum kan worden ingesteld met dezelfde LocationMatch-strategie die in de html/text-sectie wordt beschreven door de juiste regex op te geven

## Dispatcher {#disp}

Het verkeer gaat door een apache Webserver, die modules met inbegrip van de verzender steunt. De verzender wordt vooral als cache gebruikt om de verwerking op de publicatieknooppunten te beperken, zodat de prestaties toenemen.

Zoals beschreven in het cachegeheugen van de CDN, kunnen regels worden toegepast op de configuratie van de verzender om de standaardinstellingen voor de vervaldatum van het cachegeheugen te wijzigen.

In de rest van deze sectie worden overwegingen beschreven met betrekking tot de invalidatie van de cachegeheugen van de verzender. Voor de meeste klanten, zou het niet noodzakelijk moeten zijn om het verzender geheime voorgeheugen ongeldig te maken, in plaats daarvan afhankelijk van de verzender die zijn geheime voorgeheugen verfrist wanneer de inhoud opnieuw wordt gepubliceerd, en CDN die de kopballen van de geheim voorgeheugenvervalsing respecteert.

### Validatie van cache-verzender tijdens activering/deactivering {#cache-activation-deactivation}

Net als bij eerdere versies van AEM wordt de inhoud gewist uit de cache van de verzender wanneer u pagina&#39;s publiceert of verwijdert. Als een cacheprobleem wordt vermoed, moeten klanten de pagina&#39;s in kwestie opnieuw publiceren.

Wanneer de publicatieinstantie een nieuwe versie van een pagina of element van de auteur ontvangt, gebruikt deze de agent flush om de juiste paden op de dispatcher ongeldig te maken. Het bijgewerkte pad wordt samen met de bovenliggende items uit de cachegeheugen van de verzender verwijderd tot een niveau (u kunt dit configureren met het [statusniveau](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)).

### Expliciete cachevalidatie van verzender {#explicit-invalidation}

Over het algemeen hoeft u de inhoud in de verzender niet handmatig ongeldig te maken, maar dit is mogelijk, zoals hieronder beschreven.

Voorafgaand aan AEM als Cloud Service waren er twee manieren om het cachegeheugen van de verzender ongeldig te maken.

1. Roep de replicatieagent aan, die de publicatiedispatcher spoelagent specificeert
2. De `invalidate.cache` API rechtstreeks aanroepen (bijvoorbeeld `POST /dispatcher/invalidate.cache`)

De API-benadering van de verzender `invalidate.cache` wordt niet meer ondersteund omdat deze alleen geldt voor een specifiek verzender-knooppunt. AEM als Cloud Service werkt op het serviceniveau, niet op het niveau van afzonderlijke knooppunten. De instructies voor validatie in de pagina Pagina&#39;s in de cache [ongeldig maken vanaf AEM](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html) zijn daarom niet langer geldig voor AEM als Cloud Service.
In plaats daarvan, zou de replicatie flush agent moeten worden gebruikt. Dit kan worden gedaan gebruikend de Replicatie API. De documentatie van de Replicatie API is beschikbaar [hier](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) en voor een voorbeeld van het spoelen van het geheime voorgeheugen, zie de [API voorbeeldpagina](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) specifiek het `CustomStep` voorbeeld dat een replicatieactie van type ACTIVATE aan alle beschikbare agenten uitgeeft. Het uitlijnmiddeleindpunt is niet configureerbaar maar pre-gevormd om aan de dispatcher te richten, die met de publicatieservice wordt aangepast die de uitlijningsagent in werking stelt. De spoelagent kan typisch door gebeurtenissen OSGi of werkschema&#39;s worden teweeggebracht.

Dit wordt geïllustreerd in het onderstaande diagram.

![](assets/cdnc.png "CDNCDN")

Als er een probleem is dat de verzender cache niet wordt gewist, neemt u contact op met de [klantenondersteuning](https://helpx.adobe.com/support.ec.html) die de verzender cache indien nodig kan leegmaken.

De door Adobe beheerde CDN respecteert TTL&#39;s en het is dus niet nodig deze te verwijderen. Als er een probleem wordt vermoed, [neemt u contact op met de klantenondersteuning](https://helpx.adobe.com/support.ec.html) die zo nodig een CDN-cache met Adobe-beheer kan leegmaken.

## Client-Side bibliotheken en consistentie van versies {#content-consistency}

Pagina&#39;s bestaan uit HTML, JavaScript, CSS en afbeeldingen. Klanten worden aangeraden het clientlibs-framework (Client-Side Libraries) te gebruiken om Javascript- en CSS-bronnen in HTML-pagina&#39;s te importeren, rekening houdend met afhankelijkheden tussen JS-bibliotheken.

Het clientlibs-framework biedt automatisch versiebeheer, wat betekent dat ontwikkelaars wijzigingen in JS-bibliotheken kunnen inchecken in broncontrole en dat de nieuwste versie beschikbaar wordt gesteld wanneer een klant zijn release opdringt. Zonder deze optie moeten ontwikkelaars HTML handmatig wijzigen met verwijzingen naar de nieuwe versie van de bibliotheek. Dit is vooral lastig als veel HTML-sjablonen dezelfde bibliotheek delen.

Wanneer de nieuwe versies van bibliotheken worden vrijgegeven voor productie, worden de HTML-pagina&#39;s waarnaar wordt verwezen, bijgewerkt met nieuwe koppelingen naar die bijgewerkte bibliotheekversies. Als de browsercache voor een bepaalde HTML-pagina is verlopen, is het niet van belang dat de oude bibliotheken worden geladen vanuit de browsercache, aangezien de vernieuwde pagina (van AEM) nu gegarandeerd naar de nieuwe versies van de bibliotheken verwijst. Met andere woorden, een vernieuwde HTML-pagina bevat alle meest recente bibliotheekversies.

Het mechanisme hiervoor is een geserialiseerde hash, die aan de verbinding van de cliëntbibliotheek wordt toegevoegd, die een unieke, versioned url voor browser verzekert om CSS/JS in het voorgeheugen onder te brengen. De geserialiseerde hash wordt alleen bijgewerkt wanneer de inhoud van de clientbibliotheek wordt gewijzigd. Dit betekent dat als er niet-verwante updates optreden (dat wil zeggen geen wijzigingen in de onderliggende css/js van de clientbibliotheek), zelfs met een nieuwe implementatie, de verwijzing ongewijzigd blijft, waardoor de browsercache minder wordt verstoord.

### Longcache-versies van Client Side Libraries inschakelen - AEM als Cloud Service SDK QuickStart {#enabling-longcache}

De standaard clientlib-include-bestanden op een HTML-pagina zien er als volgt uit:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Wanneer strikte clientlib-versioning is ingeschakeld, wordt een lange-termijnhash-toets toegevoegd als kiezer aan de clientbibliotheek. Dientengevolge, ziet de cliëntlib verwijzing als dit:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Strikte clientlib-versioning is standaard ingeschakeld in alle AEM-omgevingen als cloudservice.

Om strikte clientlib versioning in lokale SDK toe te laten voert QuickStart de volgende acties uit:

1. Navigeer aan de Manager van de Configuratie OSGi `<host>/system/console/configMgr`
1. Zoek naar OSGi Config voor Adobe Granite HTML Library Manager:
   * Schakel het selectievakje in om Strikte versie in te schakelen
   * Voer in het veld met het label Long-term client side cache key de waarde /.*;hash
1. Sla de wijzigingen op. Merk op dat het niet noodzakelijk is om deze configuratie in broncontrole te bewaren aangezien AEM als de Dienst van de Wolk deze configuratie automatisch in dev, stadium en productiemilieu&#39;s zal toelaten.
1. Telkens wanneer de inhoud van de clientbibliotheek wordt gewijzigd, wordt een nieuwe hash-toets gegenereerd en wordt de HTML-verwijzing bijgewerkt.
