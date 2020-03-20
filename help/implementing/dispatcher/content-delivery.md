---
title: Inhoud leveren
description: 'Inhoud leveren '
translation-type: tm+mt
source-git-commit: d1c953e1caf440f18e488f07a32bcf5bc3880f67

---


# Inhoud leveren in AEM als cloudservice {#content-delivery}

De levering van de de dienstinhoud van de publicatie omvat:

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

De secties hieronder verstrekken meer detail over inhoudslevering, met inbegrip van configuratie CDN en verzender caching.

Informatie over replicatie van de auteursdienst aan de publicatieservice is [hier](/help/operations/replication.md)beschikbaar.

>[!NOTE]
>Het verkeer gaat door een apache Webserver, die modules met inbegrip van de verzender steunt. De verzender wordt vooral als cache gebruikt om de verwerking op de publicatieknooppunten te beperken, zodat de prestaties toenemen.

## CDN {#cdn}

AEM biedt drie opties:

1. Adobe Managed CDN - AEM&#39;s &#39;out-of-the-box&#39; CDN. Dit is de aanbevolen optie omdat deze volledig geïntegreerd is.
1. CDN van de klant wijst naar de Beheerde CDN van Adobe - de klant wijst hun eigen CDN aan uit-van-de-doos CDN van AEM. Als de eerste optie niet levensvatbaar is, is dit de volgende aangewezen optie aangezien het nog integratie van AEM met zijn gebrek CDN hefboomt. De klanten zullen nog verantwoordelijk zijn voor het beheren van hun eigen CDN.
1. Klant Beheerde CDN - de klant brengt hun eigen CDN en is volledig verantwoordelijk voor het beheren van het.

>[!CAUTION]
>De eerste optie wordt ten zeerste aanbevolen. Adobe kan niet verantwoordelijk worden gehouden voor het resultaat van een verkeerde configuratie als u de tweede optie kiest.

De tweede en derde mogelijkheid worden per geval toegestaan. Dit impliceert het voldoen aan bepaalde voorwaarden met inbegrip van, maar niet beperkt tot de klant die een erfenisintegratie met hun verkoper CDN heeft die moeilijk is ongedaan te maken.

### Door Adobe beheerde CDN {#adobe-managed-cdn}

Voorbereiden op de levering van inhoud met behulp van de CDN van Adobe-versie buiten de doos is eenvoudig, zoals hieronder wordt beschreven:

1. U geeft het ondertekende SSL-certificaat en de geheime sleutel aan Adobe door een koppeling te delen naar een beveiligd formulier met deze gegevens. Coördineer deze taak met de klantenondersteuning.
Opmerking: Aem als de Dienst van de Wolk steunt geen domein Gevalideerde (DV) certificaten.
1. De steun van de klant zal dan met u de timing voor een CNAME DNS verslag coördineren, richtend hun FQDN aan `adobe-aem.map.fastly.net`.
1. U wordt op de hoogte gesteld wanneer de SSL-certificaten verlopen, zodat u de nieuwe SSL-certificaten opnieuw kunt verzenden.

Standaard kan voor een CDN-installatie onder beheer van Adobe, al het openbaar verkeer zijn weg maken naar de publicatieservice, voor zowel productie- als niet-productie (ontwikkeling en stadium)-omgevingen. Als u verkeer aan de publicatiedienst voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) zou u met klantensteun moeten werken om deze beperkingen te vormen.

### CDN van klant wijst naar door Adobe beheerde CDN {#point-to-point-CDN}

Gesteund als u uw bestaande CDN wilt gebruiken, maar kan niet aan de vereisten van een Door Klant beheerde CDN voldoen. In dit geval beheert u uw eigen CDN, maar wijst u naar de beheerde CDN van Adobe.

Houd er rekening mee dat:

1. U moet een bestaande CDN hebben.
1. U zult het beheren.
1. U moet CDN kunnen vormen om met Aem als Dienst van de Wolk te werken - zie de configuratieinstructies hieronder.
1. U hebt ingenieurs CDN die op vraag zijn in geval de verwante kwesties zich voordoen.
1. U moet een ladingstest uitvoeren en met succes overgaan alvorens aan productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host` koptekst in met de domeinnaam.
1. Stel de Hostkop in met het oorspronkelijke domein. Dit is de invoer van de CDN van Adobe. De waarde moet afkomstig zijn van Adobe.
1. Verzend de kopbal SNI naar de oorsprong. Net als de Hostkop moet de sni-header het oorspronkelijke domein zijn.
1. Plaats `X-Edge-Key`, die nodig is om verkeer aan de servers van AEM correct te leiden. De waarde moet afkomstig zijn van Adobe.

### Door de klant beheerde CDN {#customer-managed-cdn}

Ondersteund als u de bestaande CDN moet gebruiken.  In dit geval beheert u uw eigen CDN en wijst u deze naar AEM.

U kunt uw eigen CDN beheren, op voorwaarde:

1. U hebt een bestaande CDN.
1. Dit moet een ondersteunde CDN zijn. Akamai wordt momenteel ondersteund. Neem contact op met de klantenondersteuning als uw organisatie een CDN wil beheren die momenteel niet wordt ondersteund.
1. U zult het beheren.
1. U moet CDN kunnen vormen om met Aem als Dienst van de Wolk te werken - zie de configuratieinstructies hieronder.
1. U hebt ingenieurs CDN die op vraag zijn in geval de verwante kwesties zich voordoen.
1. U moet whitelists of CDN-knooppunten opgeven voor Cloud Manager, zoals wordt beschreven in configuratieinstructies.
1. U moet een ladingstest uitvoeren en met succes overgaan alvorens aan productie te gaan.

Configuratieinstructies:

1. Geef de whitelist van de CDN-leverancier aan Adobe door de omgeving aan te roepen voor het maken/bijwerken van API&#39;s met een lijst van CIDR&#39;s voor whitelist.
1. Stel de `X-Forwarded-Host` koptekst in met de domeinnaam.
1. Stel de Hostkop in met het oorspronkelijke domein. Dit is de naam als een Cloud Service-adres. De waarde moet afkomstig zijn van Adobe.
1. Verzend de kopbal SNI naar de oorsprong. De SNI-header moet het oorspronkelijke domein zijn.
1. Plaats `X-Edge-Key` wat nodig is om verkeer aan de servers van AEM correct te leiden. De waarde moet afkomstig zijn van Adobe.

Voorafgaand aan het goedkeuren van levend verkeer, zou u met de klantensteun van Adobe moeten bevestigen dat het verkeer van begin tot eind het verpletteren correct functioneert.

### Caching {#caching}

Het cacheproces volgt de onderstaande regels.

### HTML/Text {#html-text}

* standaard 5 minuten in cache geplaatst door de browser, op basis van de cachebesturingsheader die door de apache-laag wordt weergegeven. De CDN neemt deze waarde ook in acht.
* U kunt overschrijven voor alle HTML/Text-inhoud door de `EXPIRATION_TIME` variabele te definiëren in het `global.vars` gebruik van de AEM als hulpprogramma&#39;s van de SDK van de Cloud Service.

U moet ervoor zorgen dat een bestand onder `src/conf.dispatcher.d/cache` de volgende regel heeft:

```
/0000
{ /glob "*" /type "allow" }
```

* kan op een fijner korrelig niveau door apache mod_headers richtlijnen worden met voeten getreden. Bijvoorbeeld:

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200 s-maxage=200"
</LocationMatch>
```

U moet ervoor zorgen dat een bestand onder `src/conf.dispatcher.d/cache` de volgende regel heeft:

```
/0000
{ /glob "*" /type "allow" }
```

* Merk op dat andere methodes, met inbegrip van het [verzender-ttl AEM ACS-Commons project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), geen waarden met succes zullen met voeten treden.

### Client-Side bibliotheken (js, css) {#client-side-libraries}

* door het clientbibliotheekframework van AEM te gebruiken, worden JavaScript- en CSS-code zodanig gegenereerd dat browsers deze oneindig in cache kunnen plaatsen, aangezien eventuele wijzigingen zich manifesteren als nieuwe bestanden met een uniek pad.  Met andere woorden, HTML-code die verwijst naar de clientbibliotheken, wordt naar wens geproduceerd, zodat klanten nieuwe inhoud kunnen ervaren terwijl deze wordt gepubliceerd. Het cache-control wordt ingesteld op &#39;onveranderlijk&#39; of op 30 dagen voor oudere browsers die de waarde &#39;onveranderlijk&#39; niet respecteren.
* Zie de sectie Bibliotheken aan de [clientzijde en de consistentie](#content-consistency) van de versie voor meer informatie.

### Afbeeldingen {#images}

* niet in cache geplaatst

### Andere inhoudstypen {#other-content}

* geen standaardcaching
* kan worden overschreven door apache `mod_headers`. Bijvoorbeeld:

```
<LocationMatch "\.(css|js)$">
    Header set Cache-Control "max-age=500 s-maxage=500"
</LocationMatch>
```

*Andere methoden voor het instellen van cacheheaders werken mogelijk ook

Voorafgaand aan het goedkeuren van levend verkeer, zouden de klanten met de klantensteun van Adobe moeten bevestigen dat het verkeer dat van begin tot eind correct functioneert.

## Dispatcher {#disp}

Het verkeer gaat door een apache Webserver, die modules met inbegrip van de verzender steunt. De verzender wordt vooral als cache gebruikt om de verwerking op de publicatieknooppunten te beperken, zodat de prestaties toenemen.

Inhoud van het type HTML/tekst wordt ingesteld met cachekoppen die overeenkomen met een vervaldatum van 300 (5 minuten).

In de rest van deze sectie worden overwegingen beschreven met betrekking tot de invalidatie van de cachegeheugen van de verzender.

### Validatie van cache-verzender tijdens activering/deactivering {#cache-activation-deactivation}

Net als bij eerdere versies van AEM wordt de inhoud gewist uit de cache van de verzender wanneer u pagina&#39;s publiceert of verwijdert. Als een cacheprobleem wordt vermoed, moeten klanten de pagina&#39;s in kwestie opnieuw publiceren.

Wanneer de publicatieinstantie een nieuwe versie van een pagina of element van de auteur ontvangt, gebruikt deze de agent flush om de juiste paden op de dispatcher ongeldig te maken. Het bijgewerkte pad wordt samen met de bovenliggende items uit de cachegeheugen van de verzender verwijderd tot een niveau (u kunt dit configureren met het [statusniveau](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)).

### Expliciete cachevalidatie van verzender {#explicit-invalidation}

Over het algemeen hoeft u de inhoud in de verzender niet handmatig ongeldig te maken, maar dit is mogelijk, zoals hieronder beschreven.

Voorafgaand aan AEM als Cloud Service waren er twee manieren om het cachegeheugen van de verzender ongeldig te maken.

1. Roep de replicatieagent aan, die de publicatiedispatcher spoelagent specificeert
2. De `invalidate.cache` API rechtstreeks aanroepen (bijvoorbeeld `POST /dispatcher/invalidate.cache`)

De `invalidate.cache` benadering wordt niet meer ondersteund omdat deze alleen geldt voor een specifiek verzendingsknooppunt.
AEM als Cloud Service werkt op het serviceniveau, niet op het niveau van afzonderlijke knooppunten. De instructies voor validatie in de pagina Pagina&#39;s in de cache [ongeldig maken vanaf AEM](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html) zijn daarom niet geldig voor AEM als Cloud Service.
In plaats daarvan, zou de replicatie flush agent moeten worden gebruikt. Dit kan worden gedaan gebruikend de Replicatie API. De documentatie van de Replicatie API is beschikbaar [hier](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) en voor een voorbeeld van het spoelen van het geheime voorgeheugen, zie de [API voorbeeldpagina](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) specifiek het `CustomStep` voorbeeld dat een replicatieactie van type ACTIVATE aan alle beschikbare agenten uitgeeft. Het uitlijnmiddeleindpunt is niet configureerbaar maar pre-gevormd om aan de dispatcher te richten, die met de publicatieservice wordt aangepast die de uitlijningsagent in werking stelt. De spoelagent kan typisch door gebeurtenissen OSGi of werkschema&#39;s worden teweeggebracht.

Dit wordt geïllustreerd in het onderstaande diagram.

![](assets/cdnc.png "CDNCDN")

Als er een probleem is dat de verzender cache niet wordt gewist, neemt u contact op met de klantenondersteuning die de verzender cache indien nodig kan leegmaken.

De door Adobe beheerde CDN respecteert TTL&#39;s en het is dus niet nodig deze te verwijderen. Als een probleem wordt vermoed, neemt u contact op met de klantenondersteuning die zo nodig een CDN-cache met Adobe-beheer kan leegmaken.

## Client-Side bibliotheken en consistentie van versies {#content-consistency}

Pagina&#39;s bestaan natuurlijk uit HTML, JavaScript, CSS en afbeeldingen. Klanten worden aangeraden het clientlibs-framework (Client-Side Libraries) te gebruiken om Javascript- en CSS-bronnen in HTML-pagina&#39;s te importeren, rekening houdend met afhankelijkheden tussen JS-bibliotheken.

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

1. Navigeer aan de Manager van de Configuratie OSGi <host>/system/console/configMgr
1. Zoek naar OSGi Config voor Adobe Granite HTML Library Manager:
   * Schakel het selectievakje in om Strikte versie in te schakelen
   * Voer in het veld met het label Long-term client side cache key de waarde /.*;hash
1. Sla de wijzigingen op. Merk op dat het niet noodzakelijk is om deze configuratie in broncontrole te bewaren aangezien AEM als de Dienst van de Wolk deze configuratie automatisch in dev, stadium en productiemilieu&#39;s zal toelaten.
1. Telkens wanneer de inhoud van de clientbibliotheek wordt gewijzigd, wordt een nieuwe hash-toets gegenereerd en wordt de HTML-verwijzing bijgewerkt.
