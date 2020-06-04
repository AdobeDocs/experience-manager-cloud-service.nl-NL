---
title: Caching in AEM als Cloud Service
description: 'Caching in AEM als Cloud Service '
translation-type: tm+mt
source-git-commit: 0080ace746f4a7212180d2404b356176d5f2d72c
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---


# Inleiding {#intro}

Caching bij CDN kan worden gevormd door dispatcherregels te gebruiken. Merk op dat de verzender ook de resulterende kopballen van de geheim voorgeheugenvervalsing naleeft als in de verzender configuratie `enableTTL` wordt toegelaten, die impliceert dat het specifieke inhoud zelfs buiten inhoud zal verfrissen die opnieuw wordt gepubliceerd.

## Caching {#caching}

### HTML/Text {#html-text}

* door gebrek, caching door browser voor vijf minuten, die op de geheim voorgeheugen-controle kopbal wordt gebaseerd door de apache laag. De CDN neemt deze waarde ook in acht.
* U kunt overschrijven voor alle HTML/Text-inhoud door de `EXPIRATION_TIME` variabele te definiëren in het `global.vars` gebruik van de AEM als hulpprogramma&#39;s van de SDK van de Cloud Service.
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

### Client-Side bibliotheken (js,css) {#client-side-libraries}

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

![](assets/cdnd.png "CDNCDN")

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
