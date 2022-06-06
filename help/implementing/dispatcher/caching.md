---
title: Caching in AEM as a Cloud Service
description: 'Caching in AEM as a Cloud Service '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: 91a88cb02192defdd651ecb6d108d4540186d06e
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 0%

---

# Inleiding {#intro}

Het verkeer gaat door CDN tot een laag van de apacheWebserver over, die modules met inbegrip van de verzender steunt. Om de prestaties te verbeteren, wordt de verzender vooral gebruikt als cache om de verwerking op de publicatieknooppunten te beperken.
De regels kunnen op de dispatcherconfiguratie worden toegepast om het even welke montages van de standaardgeheim voorgeheugenvervalsing te wijzigen, resulterend in caching bij CDN. Merk op dat de verzender ook de resulterende kopballen van de geheim voorgeheugenvervalsing eerbiedigt als `enableTTL` is ingeschakeld in de configuratie van de verzender, wat betekent dat specifieke inhoud zelfs buiten opnieuw te publiceren inhoud wordt vernieuwd.

Op deze pagina wordt ook beschreven hoe de cachegeheugen van de verzender ongeldig wordt gemaakt en hoe caching werkt op browserniveau met betrekking tot bibliotheken aan de clientzijde.

## Caching {#caching}

### HTML/Tekst {#html-text}

* standaard gedurende vijf minuten in cache geplaatst op basis van de `cache-control` de door de apache laag uitgestraalde header. De CDN neemt deze waarde ook in acht.
* de standaardinstelling voor het in cache plaatsen van HTML of tekst kan worden uitgeschakeld door de instelling `DISABLE_DEFAULT_CACHING` variabele in `global.vars`:

```
Define DISABLE_DEFAULT_CACHING
```

Dit kan nuttig zijn, bijvoorbeeld, wanneer uw bedrijfslogica het verfijnen van de leeftijdskopbal (met een waarde die op kalenderdag wordt gebaseerd) vereist omdat door gebrek de leeftijdskopbal aan 0 wordt geplaatst. Dat gezegd hebbende, **Wees voorzichtig bij het uitschakelen van standaardcaching.**

* kan worden overschreven voor alle HTML-/tekstinhoud door het definiëren van de `EXPIRATION_TIME` variabele in `global.vars` met de AEM as a Cloud Service SDK Dispatcher-gereedschappen.
* kan op een fijner korrelig niveau, met inbegrip van het controleren van CDN en browser geheim voorgeheugen onafhankelijk worden met de volgende richtlijnen apache mod_headers met voeten getreden:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Surrogate-Control "max-age=3600"
        Header set Age 0
   </LocationMatch>
   ```

   >[!NOTE]
   >De header Surrogate-Control is van toepassing op de door Adobe beheerde CDN. Als u een [door klant beheerde CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=en#point-to-point-CDN), kan een verschillende kopbal afhankelijk van uw leverancier CDN worden vereist.

   Wees voorzichtig bij het instellen van algemene cachebesturingskoppen of koppen die overeenkomen met een brede regex, zodat deze niet worden toegepast op inhoud die u privé wilt houden. Overweeg meerdere richtlijnen te gebruiken om ervoor te zorgen dat regels op een fijnkorrelige manier worden toegepast. Met dat gezegd, AEM as a Cloud Service zal de geheim voorgeheugenkopbal verwijderen als het ontdekt dat het is toegepast op wat het ontdekt om door verzender oncacheable te zijn, zoals die in de documentatie van de verzender wordt beschreven. Als u wilt dat AEM altijd de in cache opgeslagen koppen toepast, kunt u de opdracht **altijd** optie als volgt:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header unset Cache-Control
        Header unset Expires
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   U moet ervoor zorgen dat een bestand onder `src/conf.dispatcher.d/cache` heeft de volgende regel (die in de standaardconfiguratie is):

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* Om te voorkomen dat specifieke inhoud in cache wordt geplaatst **bij de CDN**, stelt u de header Cache-control in op *privé*. Het volgende voorkomt bijvoorbeeld HTML-inhoud onder een map met de naam **beveiligen** van in cache worden geplaatst bij de CDN:

   ```
      <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
      Header unset Cache-Control
      Header unset Expires
      Header always set Cache-Control “private”
     </LocationMatch>
   ```

   >[!NOTE]
   >De andere methoden, waaronder de [verzender-ttl AEM ACS-Commons-project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), overschrijft de waarden niet.

   >[!NOTE]
   >Houd er rekening mee dat de verzender nog steeds inhoud in cache plaatst volgens zijn eigen [caching-regels](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html). Als u de inhoud echt privé wilt maken, moet u ervoor zorgen dat deze niet in de cache wordt opgeslagen door de verzender.

### Client-Side bibliotheken (js,css) {#client-side-libraries}

* door gebruik te maken van AEM clientbibliotheekframework worden JavaScript- en CSS-code zodanig gegenereerd dat browsers deze oneindig in cache kunnen plaatsen, aangezien elke wijziging zich voordoet als nieuwe bestanden met een uniek pad.  Met andere woorden, HTML dat verwijzingen de cliëntbibliotheken zullen worden geproduceerd zoals nodig zodat de klanten nieuwe inhoud kunnen ervaren aangezien het wordt gepubliceerd. Het cache-control wordt ingesteld op &#39;onveranderlijk&#39; of op 30 dagen voor oudere browsers die de waarde &#39;onveranderlijk&#39; niet respecteren.
* zie de sectie [Bibliotheken aan de clientzijde en consistentie van versies](#content-consistency) voor meer informatie.

### Afbeeldingen en inhoud die groot genoeg is om in blokopslag te worden opgeslagen {#images}

Het standaardgedrag voor programma&#39;s die na medio mei 2022 worden gemaakt (met name voor programma-id&#39;s van meer dan 65000), is standaard in cache plaatsen, terwijl ook de verificatiecontext van het verzoek wordt gerespecteerd. Oudere programma&#39;s (programma-id&#39;s van 65000 of lager) plaatsen standaard geen blob-inhoud in de cache.

In beide gevallen kunnen de in de cache geplaatste koppen op een fijnere korreligheid in de apache/verzender-laag worden overschreven met behulp van de apache `mod_headers` richtlijnen , bijvoorbeeld :

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Wanneer het wijzigen van de caching kopballen bij de verzender laag, gelieve voorzichtig te zijn om niet te wijd in het voorgeheugen onder te brengen, zie de bespreking in de HTML/tekstsectie [boven](#html-text). Zorg er ook voor dat elementen die bedoeld zijn om privé te blijven (in plaats van in cache te worden geplaatst), geen deel uitmaken van de `LocationMatch` richtingsfilters.

#### Nieuw standaardgedrag voor in cache plaatsen {#new-caching-behavior}

De AEM laag zal geheim voorgeheugenkopballen plaatsen afhankelijk van of de geheim voorgeheugenkopbal reeds is geplaatst en de waarde van het verzoektype. Merk op dat als geen kopbal van de geheim voorgeheugencontrole is geplaatst, openbare inhoud in het voorgeheugen wordt opgeslagen en voor authentiek verklaard verkeer wordt geplaatst aan privé. Als een kopbal van de geheim voorgeheugencontrole is geplaatst, zullen de geheim voorgeheugenkopballen ongewijzigd zijn.

| Besturingsheader voor cache bestaat? | Type aanvraag | AEM stelt cachekoppen in op |
|------------------------------|---------------|------------------------------------------------|
| Nee | publiek | Cachebeheer: public, max-age=600, onveranderlijk |
| Nee | geverifieerd | Cachebeheer: private, max-age=600, onveranderlijk |
| Ja | alle | ongewijzigd |

Hoewel niet aanbevolen, is het mogelijk om het nieuwe standaardgedrag te wijzigen om het oude gedrag te volgen (programma-id&#39;s gelijk aan of lager dan 65000) door de omgevingsvariabele van Cloud Manager in te stellen `AEM_BLOB_ENABLE_CACHING_HEADERS` naar false.

#### Oudere standaardcaching, gedrag {#old-caching-behavior}

De AEM laag plaatst blob-inhoud niet standaard in het cachegeheugen.

>[!NOTE]
>Het wordt aanbevolen het oudere standaardgedrag te wijzigen om consistent te zijn met het nieuwe gedrag (programma-id&#39;s die hoger zijn dan 65000) door de omgevingsvariabele AEM_BLOB_ENABLE_CACHING_HEADERS van Cloud Manager in te stellen op true. Als het programma al actief is, controleert u of de inhoud zich na de wijzigingen gedraagt zoals u verwacht.

>[!NOTE]
>De andere methoden, waaronder de [verzender-ttl AEM ACS-Commons-project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), worden de waarden niet overschreven.

### Andere inhoudstypen in nodenarchief {#other-content}

* geen standaardcaching
* standaard kan niet worden ingesteld met de `EXPIRATION_TIME` variabele die wordt gebruikt voor html/text-bestandstypen
* cache-vervaldatum kan worden ingesteld met dezelfde LocationMatch-strategie die in de html/text-sectie wordt beschreven door de juiste regex op te geven

### Verdere optimalisaties {#further-optimizations}

* Vermijd het gebruik `User-Agent` als onderdeel van de `Vary` header. Oudere versies van de standaarddispatcheropstelling (vóór archetype versie 28) omvatten dit en wij adviseren u dat gebruikend de hieronder stappen te verwijderen.
   * Zoek de hostbestanden in `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`
   * Verwijder of verwijder de regel: `Header append Vary User-Agent env=!dont-vary` van alle vhost-bestanden, met uitzondering van default.vhost, dat alleen-lezen is
* Gebruik de `Surrogate-Control` header om CDN in cache te plaatsen onafhankelijk van browser caching
* Overweeg toepassing toe te passen [`stale-while-revalidate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) en [`stale-if-error`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) richtlijnen waarmee u op de achtergrond kunt vernieuwen en cachefouten kunt voorkomen, zodat uw inhoud snel en vers blijft voor gebruikers.
   * Er zijn veel manieren om deze richtlijnen toe te passen, maar er wordt een minuut toegevoegd `stale-while-revalidate` aan alle kopballen van de geheim voorgeheugencontrole is een goed uitgangspunt.
* Hier volgen enkele voorbeelden voor verschillende inhoudstypen, die u kunt gebruiken als richtlijn bij het instellen van uw eigen regels voor het in cache plaatsen. Overweeg en test zorgvuldig uw specifieke instellingen en vereisten:

   * Mogelijke clientbibliotheekbronnen voor 12 uur in cache opslaan en de achtergrond vernieuwen na 12 uur.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:json|png|gif|webp|jpe?g|svg)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200,public" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * De onveranderlijke middelen van de cliëntbibliotheek van het geheime voorgeheugen op lange termijn (30 dagen) met achtergrond verfrist zich om MISS te vermijden.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:js|css|ttf|woff2)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Plaats HTML-pagina&#39;s voor 5 minuten in cache, waarbij de achtergrond 1 uur in de browser en 12 uur in de CDN vernieuwt. De geheime voorgeheugen-controle kopballen zullen altijd worden toegevoegd zodat is het belangrijk om ervoor te zorgen dat de aanpassing van HTML- pagina&#39;s onder /content/* bestemd zijn om openbaar te zijn. Zo niet, gebruik dan een specifiekere regex.

      ```
      <LocationMatch "^/content/.*\.html$">
         Header unset Cache-Control
         Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Cache content services/Sling model exporter json responses for 5min met background refresh 1h op browser en 12h op CDN.

      ```
      <LocationMatch "^/content/.*\.model\.json$">
         Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Plaats onveranderlijke URL&#39;s van de centrale afbeeldingscomponent in de cache op lange termijn (30 dagen) en vernieuw de achtergrond om MISS te voorkomen.

      ```
      <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mutabele bronnen van de DAM in de cache opslaan, zoals afbeeldingen en video voor 24 uur en de achtergrond vernieuwen na 12 uur om MISS te voorkomen

      ```
      <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

### HEAD-aanvraaggedrag {#request-behavior}

Wanneer een verzoek van HEAD bij Adobe CDN voor een middel wordt ontvangen dat **niet** in cache wordt geplaatst, wordt het verzoek getransformeerd en door de verzender en/of AEM instantie ontvangen als een GET- verzoek. Als de reactie cacheable is dan zullen de verdere verzoeken van HEAD van CDN worden gediend. Als de reactie niet in cache kan worden geplaatst, worden de volgende HEAD-aanvragen doorgegeven aan de verzender en/of AEM instantie gedurende een periode die afhankelijk is van de `Cache-Control` TTL.

## Ongeldige validatie van cache-verzending {#disp}

Over het algemeen is het niet nodig om de cachegeheugen van de verzender ongeldig te maken. In plaats daarvan moet u erop vertrouwen dat de verzender de cache vernieuwt wanneer de inhoud opnieuw wordt gepubliceerd en de CDN de headers voor het verlopen van de cache respecteert.

### Validatie van cache-verzender tijdens activering/deactivering {#cache-activation-deactivation}

Net als bij eerdere versies van AEM wordt de inhoud van de verzendingscache gewist wanneer u pagina&#39;s publiceert of de publicatie ervan ongedaan maakt. Als een cacheprobleem wordt vermoed, moeten klanten de pagina&#39;s in kwestie opnieuw publiceren en ervoor zorgen dat er een virtuele host beschikbaar is die overeenkomt met ServerAlias localhost, wat vereist is voor de ongeldigverklaring van het cachegeheugen van de verzender.


Wanneer de publicatieinstantie een nieuwe versie van een pagina of element van de auteur ontvangt, gebruikt deze de agent flush om de juiste paden op de dispatcher ongeldig te maken. Het bijgewerkte pad wordt samen met de bovenliggende elementen uit de cache van de verzender verwijderd tot een niveau (u kunt dit configureren met de [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)).

### Expliciete cachevalidatie van verzender {#explicit-invalidation}

Over het algemeen hoeft de inhoud in de verzender niet handmatig ongeldig te worden gemaakt, maar dit is mogelijk als dat nodig is.

>[!NOTE]
>Voorafgaand aan AEM as a Cloud Service, waren er twee manieren om het berichtchergeheime voorgeheugen ongeldig te maken.
>
>1. Roep de replicatieagent aan, die de publicatiedispatcher spoelagent specificeert
>2. Het direct roepen van `invalidate.cache` API (bijvoorbeeld `POST /dispatcher/invalidate.cache`)

>
>De verzender `invalidate.cache` API-benadering wordt niet meer ondersteund omdat deze alleen betrekking heeft op een specifiek verzendingsknooppunt. AEM as a Cloud Service werkt op het de dienstniveau, niet het individuele knoopniveau en zo de ongeldigingsinstructies in [In cache geplaatste pagina&#39;s ongeldig maken van AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) is niet langer geldig voor AEM as a Cloud Service.

De replicatie spoelmiddel zou moeten worden gebruikt. Dit kan worden gedaan gebruikend [Replicatie-API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). Het uitlijnmiddeleindpunt is niet configureerbaar maar pre-gevormd om aan de dispatcher te richten, die met de publicatieservice wordt aangepast die de uitlijningsagent in werking stelt. De spoelagent kan typisch door gebeurtenissen OSGi of werkschema&#39;s worden teweeggebracht.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 
-->

Dit wordt geïllustreerd in het onderstaande diagram.

![CDN](assets/cdnd.png "CDN")

Als er een probleem is dat de verzender cache niet wordt gewist, neemt u contact op met [klantenondersteuning](https://helpx.adobe.com/support.ec.html) die de verzendingscache zo nodig kunnen leegmaken.

Adobe-beheerde CDN respecteert TTLs en zo is er geen behoefte aan het om worden gespoeld. Als een probleem wordt vermoed, [contact opnemen met klantenondersteuning](https://helpx.adobe.com/support.ec.html) ondersteuning die een CDN-cache met Adobe-beheer indien nodig kan leegmaken.

## Client-Side bibliotheken en consistentie van versies {#content-consistency}

Pagina&#39;s bestaan uit HTML, JavaScript, CSS en afbeeldingen. Klanten worden aangemoedigd om de [Client-Side Libraries (clientlibs)-framework](/help/implementing/developing/introduction/clientlibs.md) om Javascript en CSS middelen in HTML pagina&#39;s in te voeren, rekening houdend met gebiedsdelen tussen bibliotheken JS.

Het clientlibs-framework biedt automatisch versiebeheer, wat betekent dat ontwikkelaars wijzigingen in JS-bibliotheken kunnen inchecken in broncontrole en dat de nieuwste versie beschikbaar wordt gesteld wanneer een klant zijn release opdringt. Zonder dit, zouden de ontwikkelaars HTML met verwijzingen naar de nieuwe versie van de bibliotheek manueel moeten veranderen, wat vooral bezwaarlijk is als vele malplaatjes van HTML de zelfde bibliotheek delen.

Wanneer de nieuwe versies van bibliotheken worden vrijgegeven voor productie, worden de HTML-pagina&#39;s waarnaar wordt verwezen, bijgewerkt met nieuwe koppelingen naar die bijgewerkte bibliotheekversies. Als de browsercache voor een bepaalde HTML-pagina is verlopen, is het niet van belang dat de oude bibliotheken worden geladen uit de browsercache, aangezien de vernieuwde pagina (van AEM) nu gegarandeerd naar de nieuwe versies van de bibliotheken verwijst. Met andere woorden, een vernieuwde HTML-pagina bevat alle meest recente bibliotheekversies.

Het mechanisme hiervoor is een geserialiseerde hash, die aan de verbinding van de cliëntbibliotheek wordt toegevoegd, die een unieke, versioned url voor browser verzekert om CSS/JS in het voorgeheugen onder te brengen. De geserialiseerde hash wordt alleen bijgewerkt wanneer de inhoud van de clientbibliotheek wordt gewijzigd. Dit betekent dat als er niet-verwante updates optreden (dat wil zeggen geen wijzigingen in de onderliggende css/js van de clientbibliotheek), zelfs met een nieuwe implementatie, de verwijzing ongewijzigd blijft, waardoor de browsercache minder wordt verstoord.

### Longcache-versies van Client Side Libraries inschakelen - AEM as a Cloud Service SDK QuickStart {#enabling-longcache}

De standaard clientlib omvat op een pagina van HTML kijkt als het volgende voorbeeld:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Wanneer strikte clientlib-versioning is ingeschakeld, wordt een lange-termijnhash-toets toegevoegd als kiezer aan de clientbibliotheek. Dientengevolge, ziet de cliëntlib verwijzing als dit:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Strikte clientlib-versioning is standaard ingeschakeld in alle AEM as a Cloud Service omgevingen.

Om strikte clientlib versioning in lokale SDK toe te laten voert QuickStart de volgende acties uit:

1. Navigeer aan de Manager van de Configuratie OSGi `<host>/system/console/configMgr`
1. Vind OSGi Config voor de Manager van de Bibliotheek van de HTML van Adobe Granite:
   * Schakel het selectievakje in om Strikte versie in te schakelen
   * Voer in het veld met het label Long-term client side cache key de waarde /.*;hash
1. Sla de wijzigingen op. Merk op dat het niet noodzakelijk is om deze configuratie in broncontrole te bewaren aangezien AEM as a Cloud Service deze configuratie automatisch in dev, stadium en productiemilieu&#39;s zal toelaten.
1. Telkens wanneer de inhoud van de clientbibliotheek wordt gewijzigd, wordt een nieuwe hash-toets gegenereerd en wordt de HTML-verwijzing bijgewerkt.
