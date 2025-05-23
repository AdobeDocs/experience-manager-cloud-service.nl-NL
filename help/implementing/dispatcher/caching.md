---
title: Caching in AEM as a Cloud Service
description: Meer informatie over de basisbeginselen van Caching in AEM as a Cloud Service
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
role: Admin
source-git-commit: 4a586a0022682dadbc57bab1ccde0ba2afa78627
workflow-type: tm+mt
source-wordcount: '3071'
ht-degree: 0%

---

# Inleiding {#intro}

Het verkeer gaat door CDN tot een Apache laag van de Webserver over, die modules met inbegrip van Dispatcher steunt. Om de prestaties te verbeteren, wordt Dispatcher vooral gebruikt als cache om de verwerking op de publicatieknooppunten te beperken.
De regels kunnen op de configuratie van Dispatcher worden toegepast om het even welke montages van de standaardgeheim voorgeheugenvervalsing te wijzigen, resulterend in caching bij CDN. Dispatcher respecteert ook de resulterende headers voor het verlopen van de cache als `enableTTL` is ingeschakeld in de Dispatcher-configuratie, wat betekent dat specifieke inhoud wordt vernieuwd, zelfs buiten de inhoud die opnieuw wordt gepubliceerd.

Op deze pagina wordt ook beschreven hoe de Dispatcher-cache ongeldig wordt gemaakt en hoe caching werkt op browserniveau met betrekking tot client-side bibliotheken.

## Caching {#caching}

Het in cache plaatsen van HTTP-reacties in de CDN van AEM as a Cloud Service wordt bestuurd door de volgende HTTP-responsheaders vanaf de oorsprong: `Cache-Control`, `Surrogate-Control` of `Expires` .

Deze geheim voorgeheugenkopballen worden typisch geplaatst in de gastheerconfiguraties van AEM Dispatcher gebruikend mod_headers, maar kunnen ook in douaneJava™ code worden geplaatst die in AEM loopt publiceren zelf (zie [ hoe te CDN caching ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/caching/how-to/enable-caching) toelaten).

De geheim voorgeheugensleutel voor middelen CDN bevat het volledige verzoek url, met inbegrip van vraagparameters, zodat zal elke verschillende vraagparameter een verschillende geheim voorgeheugeningang veroorzaken. Overweeg het verwijderen van ongewenste vraagparameters; [ zie hieronder ](#marketing-parameters) voor het verbeteren van de verhouding van de geheim voorgeheugenhit.

Oorspronkelijke reacties die `private`, `no-cache` of `no-store` in `Cache-Control` bevatten, worden niet in de cache geplaatst door de CDN van de AEM as a Cloud Service (zie [&#128279;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/caching/how-to/disable-caching) CDN-caching uitschakelen
 voor meer informatie).  Reacties die cookies instellen, d.w.z. een `Set-Cookie` reactie header hebben, worden niet in cache geplaatst door de CDN.

### HTML/Tekst {#html-text}

Dispatcher-configuratie stelt een aantal standaardcaching-headers in voor het inhoudstype `text/html` .

* standaard wordt deze gedurende vijf minuten in de cache geplaatst op basis van de `cache-control` -header die door de Apache-laag wordt uitgestraald. De CDN neemt deze waarde ook in acht.
* U kunt de standaardinstelling HTML/Text in cache plaatsen uitschakelen door de variabele `DISABLE_DEFAULT_CACHING` in `global.vars` te definiëren:

```
Define DISABLE_DEFAULT_CACHING
```

Deze methode is bijvoorbeeld handig wanneer uw bedrijfslogica een nauwkeurige afstemming van de paginakoptekst vereist (met een waarde die op kalenderdag is gebaseerd), omdat de paginakoptekst standaard op 0 is ingesteld. Dat gezegd, **oefening voorzichtigheid wanneer het uitzetten van gebrek caching.**

* U kunt de waarde `EXPIRATION_TIME` variabele in `global.vars` definiëren met de AEM as a Cloud Service SDK Dispatcher-gereedschappen.
* U kunt de volgende Apache `mod_headers` -instructies negeren op fijner korrelig niveau, inclusief het onafhankelijk beheren van de CDN en de cache van de browser:

  ```
  <LocationMatch "^/content/.*\.(html)$">
       Header set Cache-Control "max-age=200"
       Header set Surrogate-Control "max-age=3600"
       Header set Age 0
  </LocationMatch>
  ```

  >[!NOTE]
  >De header Surrogate-Control is van toepassing op de door Adobe beheerde CDN. Als het gebruiken van a [ klant-geleide CDN ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=nl-NL#point-to-point-CDN), kan een verschillende kopbal afhankelijk van uw CDN leverancier worden vereist.

  Wees voorzichtig bij het instellen van algemene cachebeheerkoppen of vergelijkbare cachekoppen die overeenkomen met een brede regex, zodat deze niet worden toegepast op inhoud die u privé moet houden. Overweeg meerdere richtlijnen te gebruiken om ervoor te zorgen dat regels op een fijnkorrelige manier worden toegepast. Met dat gezegd, verwijdert AEM as a Cloud Service de geheim voorgeheugenkopbal als het ontdekt dat het is toegepast op wat het ontdekt om uncacheable te zijn door Dispatcher, zoals die in de documentatie van Dispatcher wordt beschreven. Als u AEM wilt dwingen om altijd de headers in de cache toe te passen, kunt u de optie **`always`** als volgt toevoegen:

  ```
  <LocationMatch "^/content/.*\.(html)$">
       Header unset Cache-Control
       Header unset Expires
       Header always set Cache-Control "max-age=200"
       Header set Age 0
  </LocationMatch>
  ```

  Zorg ervoor dat een bestand onder `src/conf.dispatcher.d/cache` de volgende regel heeft (in de standaardconfiguratie):

  ```
  /0000
  { /glob "*" /type "allow" }
  ```

* Om specifieke inhoud te verhinderen **bij CDN** in het voorgeheugen onder te brengen, plaats de geheime voorgeheugen-Controle kopbal aan *privé*. Bijvoorbeeld, zou het volgende HTML- inhoud onder een folder genoemd **veilige** verhinderen in het voorgeheugen onder CDN worden opgeslagen:

  ```
     <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
     Header unset Cache-Control
     Header unset Expires
     Header always set Cache-Control "private"
    </LocationMatch>
  ```

* Hoewel HTML-inhoud die is ingesteld op privé, niet in de cache wordt opgeslagen op het CDN, kan deze wel in de cache worden opgeslagen bij de Dispatcher als [Permission Sensitive Caching](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=nl-NL) is geconfigureerd, zodat alleen geautoriseerde gebruikers de inhoud kunnen krijgen.

  >[!NOTE]
  >De andere methoden, waaronder het [Dispatcher-ttl AEM ACS Commons-project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), kunnen waarden niet overschrijven.

  >[!NOTE]
  >De Dispatcher kan nog steeds inhoud cachen volgens zijn eigen [caching-regels](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html?lang=nl-NL). Als u de inhoud echt privé wilt maken, moet u ervoor zorgen dat deze niet in de cache wordt opgeslagen door de Dispatcher.

### Bibliotheken aan de clientzijde (js,css) {#client-side-libraries}

* Wanneer u AEM Client-Side Library Framework gebruikt, worden JavaScript- en CSS-code zodanig gegenereerd dat browsers deze oneindig in cache kunnen plaatsen, aangezien elke wijziging zich voordoet als nieuwe bestanden met een uniek pad. Met andere woorden, HTML dat verwijzingen naar de cliëntbibliotheken worden geproduceerd zoals nodig zodat de klanten nieuwe inhoud kunnen ervaren aangezien het wordt gepubliceerd. Het cache-control wordt ingesteld op &#39;onveranderlijk&#39; of op 30 dagen voor oudere browsers die de waarde &#39;onveranderlijk&#39; niet respecteren.
* zie de sectie [ cliënt-zijbibliotheken en versieconsistentie ](#content-consistency) voor extra details.

### Images and any content large enough to be stored in blob storage {#images}

The default behavior for programs created after mid-May 2022 (specifically, for program ids that are higher than 65000) is to cache by default,while also respecting the request&#39;s authentication context. Older programs (program ids equal or lower than 65000) do not cache blob content by default.

In beide gevallen kunnen de caching-headers op een fijnmaziger niveau op de Apache/Dispatcher-laag worden overschreven met behulp van de Apache-richtlijnen `mod_headers` , bijvoorbeeld:

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Wanneer het wijzigen van de caching kopballen bij de laag van Dispatcher, ben voorzichtig om niet te wijd in het voorgeheugen onder te brengen. Zie de bespreking in de HTML/tekstsectie [ hierboven ](#html-text). Zorg er ook voor dat elementen die bedoeld zijn om privé te blijven (in plaats van in cache te worden geplaatst) geen deel uitmaken van de richtingsfilters van `LocationMatch` .

JCR-bronnen (groter dan 16 kB) die zijn opgeslagen in een blob-opslag, worden doorgaans aangeboden als 302 omleidingen door AEM. Deze omleidingen worden onderschept en door CDN gevolgd en de inhoud wordt direct geleverd van de blob opslag. Op deze reacties kan slechts een beperkte set kopteksten worden aangepast. Als u bijvoorbeeld `Content-Disposition` wilt aanpassen, moet u de verzendinstructies als volgt gebruiken:

```
<LocationMatch "\.(?i:pdf)$">
  ForceType application/pdf
  Header set Content-Disposition inline
  </LocationMatch>
```

The list of headers that can be be customised on blob responses are:

```
content-security-policy
x-frame-options
x-xss-protection
x-content-type-options
x-robots-tag
access-control-allow-origin
content-disposition
permissions-policy
referrer-policy
x-vhost
content-disposition
cache-control
vary
```

#### New default caching behavior {#new-caching-behavior}

The AEM layer sets cache headers depending on whether the cache header has already been set and the value of the request type. If no cache control header is set, public content is cached, and authenticated traffic is set to private. Als een kopbal van de geheim voorgeheugencontrole wordt geplaatst, worden de geheim voorgeheugenkopballen verlaten onveranderd.

| Besturingsheader voor cache bestaat? | Type aanvraag | AEM stelt cachekoppen in op |
|------------------------------|---------------|------------------------------------------------|
| Nee | publiek | Cache-control: public, max-age=600, onveranderlijk |
| Nee | geverifieerd | Cache-control: private, max-age=600, onveranderlijk |
| Ja | alle | ongewijzigd |

Hoewel dit niet wordt aanbevolen, is het mogelijk om het nieuwe standaardgedrag te wijzigen om het oude gedrag te volgen (programma-id&#39;s gelijk aan of lager dan 65000) door de Cloud Manager-omgevingsvariabele `AEM_BLOB_ENABLE_CACHING_HEADERS` in te stellen op false.

#### Oudere standaardcaching, gedrag {#old-caching-behavior}

In de AEM-laag wordt blob-inhoud niet standaard in de cache opgeslagen.

>[!NOTE]
>Wijzig het oudere standaardgedrag om consistent te zijn met het nieuwe gedrag (programma-id&#39;s die hoger zijn dan 65000) door de Cloud Manager-omgevingsvariabele AEM_BLOB_ENABLE_CACHING_HEADERS in te stellen op true. Als het programma al actief is, controleert u of de inhoud zich na de wijzigingen gedraagt zoals u verwacht.

Nu, kunnen de beelden in blob opslag die duidelijk privé zijn niet in het voorgeheugen ondergebracht bij Dispatcher gebruikend [ Gevoelige Caching van de Toestemming ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=nl-NL). De afbeelding wordt altijd opgevraagd bij de AEM-oorsprong en wordt weergegeven als de gebruiker geautoriseerd is.

>[!NOTE]
>De andere methodes, met inbegrip van het [ verzender-ttl AEM ACS- Commons project ](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), met succes treden niet de waarden met voeten.

### Andere inhoudstypen in nodenarchief {#other-content}

* geen standaardcaching
* standaard kan niet worden ingesteld met de variabele `EXPIRATION_TIME` die wordt gebruikt voor bestandstypen html/text
* cache-vervaldatum kan worden ingesteld met dezelfde LocationMatch-strategie die in de html/text-sectie wordt beschreven door de juiste regex op te geven

### Verdere optimalisaties {#further-optimizations}

* Gebruik `User-Agent` niet als onderdeel van de header van `Vary` . Oudere versies van de standaard Dispatcher-instelling (vóór archetype versie 28) hebben deze opgenomen en Adobe raadt u aan deze versie te verwijderen door de onderstaande stappen uit te voeren.
   * De hostbestanden zoeken in `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`
   * Verwijder of verwijder de regel: `Header append Vary User-Agent env=!dont-vary` uit alle hostbestanden, behalve default.vhost, die alleen-lezen is
* Met de header `Surrogate-Control` kunt u CDN-caching onafhankelijk van browsercaching instellen
* U kunt overwegen [`stale-while-revalidate` ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) en [`stale-if-error` ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) instructies toe te passen om achtergrond toe te staan verfrist zich en geheim voorgeheugenmissen te vermijden, die uw inhoud snel en vers voor gebruikers houden.
   * Er zijn vele manieren om deze richtlijnen toe te passen, maar het toevoegen van een 30 minuten `stale-while-revalidate` aan alle kopballen van de geheim voorgeheugencontrole is een goed uitgangspunt.
* Hier volgen enkele voorbeelden voor verschillende inhoudstypen, die u kunt gebruiken als richtlijn bij het instellen van uw eigen regels voor het in cache plaatsen. Overweeg en test zorgvuldig uw specifieke instellingen en vereisten:

   * Mogelijke clientbibliotheekbronnen gedurende 12 uur in cache opslaan en de achtergrond na 12 uur vernieuwen.

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

   * HTML-pagina&#39;s gedurende vijf minuten in cache plaatsen, waarbij de achtergrond één uur in de browser en 12 uur in de CDN wordt vernieuwd. De cache-Control headers worden altijd toegevoegd, dus het is belangrijk om ervoor te zorgen dat overeenkomende HTML-pagina&#39;s onder /content/* openbaar moeten zijn. Als niet, overweeg het gebruiken van een specifiekere regex.

     ```
     <LocationMatch "^/content/.*\.html$">
        Header unset Cache-Control
        Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
        Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Cache content services/Sling model exporter json reacties gedurende vijf minuten met achtergrondverversing, één uur in de browser en 12 uur op CDN.

     ```
     <LocationMatch "^/content/.*\.model\.json$">
        Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
        Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Cache onveranderlijke URL&#39;s van de kernafbeeldingscomponent op lange termijn (30 dagen) met vernieuwing op de achtergrond om MISS te voorkomen.

     ```
     <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
        Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Cache veranderlijke bronnen van de DAM, zoals afbeeldingen en video&#39;s, gedurende 24 uur en verversing van de achtergrond na 12 uur om MISS te voorkomen.

     ```
     <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
        Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

### Analyse van de CDN-cachehitratio {#analyze-chr}

Zie de tutorial[&#128279;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/caching/cdn-cache-hit-ratio-analysis.html?lang=nl-NL) over de analyse van de cachehitratio voor informatie over het downloaden van CDN-logboeken en het analyseren van de cache-hitratio&#39;s van uw site, met behulp van een dashboard.

### Gedrag van HEAD-aanvragen {#request-behavior}

Wanneer een HEAD-verzoek wordt ontvangen op het Adobe CDN voor een bron die niet **in de cache is** opgeslagen, wordt het verzoek getransformeerd en ontvangen door de verzender en/of AEM instantie als een GET-verzoek. Als het antwoord in de cache kan worden opgeslagen, worden volgende HEAD-verzoeken verzonden vanuit het CDN. Als het antwoord niet in de cache kan worden opgeslagen, worden volgende HEAD-verzoeken doorgegeven aan de Dispatcher, of AEM instantie, of beide, voor een tijd die afhankelijk is van de `Cache-Control` TTL.

### Parameters van marketingcampagnes {#marketing-parameters}

Website-URL&#39;s bevatten vaak parameters voor marketingcampagnes die worden gebruikt om het succes van een campagne bij te houden.

Voor milieu&#39;s die in Oktober 2023 of recenter worden gecreeerd, aan betere geheim voorgeheugenverzoeken, zal CDN gemeenschappelijke marketing verwante vraagparameters, specifiek die verwijderen die het volgende regex patroon aanpassen:

```
^(utm_.*|gclid|gdftrk|_ga|mc_.*|trk_.*|dm_i|_ke|sc_.*|fbclid|msclkid|ttclid)$
```

Deze functionaliteit kan worden van een knevel voorzien en van het gebruiken van a `requestTransformations` vlag in [ CDN configuratie ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#request-transformations).

Als u bijvoorbeeld wilt ophouden met het verwijderen van marketingparams op CDN-niveau, moet u `removeMarketingParams: false` implementeren met een config die de volgende sectie bevat.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  requestTransformations:
    removeMarketingParams: false
```

Als `removeMarketingParams`-functionaliteit op CDN-niveau is uitgeschakeld, wordt het nog steeds aanbevolen om de eigenschap `ignoreUrlParams` van de Dispatcher-configuratie te configureren; zie [Dispatcher configureren - URL-parameters negeren](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL#ignoring-url-parameters).

There are two possibilities to ignore marketing parameters. (Where the first one is preferred to ignore cache busting via query parameters):

1. Negeer alle parameters en sta selectief parameters toe die worden gebruikt.
In het volgende voorbeeld worden alleen de parameters `page` en `product` niet genegeerd en worden de aanvragen doorgestuurd naar de uitgever.

```
/ignoreUrlParams {
   /0001 { /glob "*" /type "allow" }
   /0002 { /glob "page" /type "deny" }
   /0003 { /glob "product" /type "deny" }
}
```

1. Alle parameters behalve de marketingparameters toestaan. Het dossier [ marketing_query_parameters.any ](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/dispatcher.cloud/src/conf.dispatcher.d/cache/marketing_query_parameters.any) bepaalt een lijst van algemeen gebruikte marketing parameters die zullen worden genegeerd. Adobe werkt dit bestand niet bij. Deze kan door gebruikers afhankelijk van hun marketingproviders worden uitgebreid.

```
/ignoreUrlParams {
   /0001 { /glob "*" /type "deny" }
   $include "../cache/marketing_query_parameters.any"
}
```


## Dispatcher Cache-validatie {#disp}

In general, it is not necessary to invalidate the Dispatcher cache. In plaats daarvan moet u erop vertrouwen dat de Dispatcher de cache vernieuwt wanneer inhoud opnieuw wordt gepubliceerd en dat de CDN de headers voor het verlopen van de cache respecteert.

### Dispatcher Cache Invalidation during Activation/Deactivation {#cache-activation-deactivation}

Like previous versions of AEM, publishing or unpublishing pages clears the content from the Dispatcher cache. Als een cacheprobleem wordt vermoed, moet u de pagina&#39;s in kwestie opnieuw publiceren en zorgen dat er een virtuele host beschikbaar is die overeenkomt met de localhost van `ServerAlias` , die vereist is voor ongeldigverklaring van het Dispatcher-cachegeheugen.

>[!NOTE]
>Voor een correcte Dispatcher-validatie moet u ervoor zorgen dat aanvragen van &quot;127.0.0.1&quot;, &quot;localhost&quot;, &quot;\*.local&quot;, &quot;\*.adobeaemcloud.com&quot; en &quot;\*.adobeaemcloud.net&quot; allemaal overeenkomen en worden afgehandeld door een hostconfiguratie zodat de aanvraag kan worden uitgevoerd. U kunt deze taak door globale aanpassing &quot;*&quot;in een catch-all gastheerconfiguratie na het patroon in het referentie [ AEM archetype ](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/dispatcher.cloud/src/conf.d/available_vhosts/default.vhost) doen. U kunt er ook voor zorgen dat de eerder vermelde lijst wordt afgevangen door een van de hosts.

Wanneer de publicatieinstantie een nieuwe versie van een pagina of element van de auteur ontvangt, gebruikt deze de agent flush om de juiste paden op de Dispatcher ongeldig te maken. De bijgewerkte weg wordt verwijderd uit het geheime voorgeheugen van Dispatcher, samen met zijn ouders, tot een niveau (u kunt dit niveau met [ statfileslevel ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL#invalidating-files-by-folder-level) vormen).

## Expliciete ongeldigmaking van de Dispatcher-cache {#explicit-invalidation}

Adobe raadt u aan om de levenscyclus van de levering van inhoud te regelen met behulp van standaard cacheheaders. Indien nodig is het echter mogelijk inhoud rechtstreeks in Dispatcher ongeldig te maken.

De volgende lijst bevat scenario&#39;s waar u uitdrukkelijk het geheime voorgeheugen zou kunnen willen invalideren (terwijl naar keuze het luisteren naar de voltooiing van de ongeldigverklaring):

* Na het publiceren van inhoud zoals ervaringsfragmenten of inhoudsfragmenten, het ongeldig maken van gepubliceerde en in de cache opgeslagen inhoud die naar die elementen verwijst.
* Een extern systeem waarschuwen wanneer pagina&#39;s waarnaar wordt verwezen, zijn ongeldig gemaakt.

Er zijn twee benaderingen om het geheime voorgeheugen uitdrukkelijk ongeldig te maken:

* De voorkeursbenadering is het gebruik van de Sling Content Distribution (SCD) van de auteur.
* De andere aanpak is om de Replicatie-API te gebruiken om de publiceer Dispatcher flush-replicatieagent aan te roepen.

De benaderingen verschillen in termen van laagbeschikbaarheid, de capaciteit om gebeurtenissen en gebeurtenisverwerkingsgarantie te dedupliceren. De onderstaande tabel geeft een overzicht van de volgende opties:

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>NVT</th>
    <th>Beschikbaarheid van niveaus</th>
    <th>Deduplicatie </th>
    <th>Garantie </th>
    <th>Handeling </th>
    <th>Gevolgen </th>
    <th>Beschrijving </th>
  </tr>  
  <tr>
    <td>SCD-API (Sling Content Distribution)</td>
    <td>Auteur</td>
    <td>Mogelijke gebruikend of Ontdekking API of toelatend de <a href="https://github.com/apache/sling-org-apache-sling-distribution-journal/blob/e18f2bd36e8b43814520e87bd4999d3ca77ce8ca/src/main/java/org/apache/sling/distribution/journal/impl/publisher/DistributedEventNotifierManager.java#L146-L149"> deduplicatiemodus </a>.</td>
    <td>Ten minste één keer.</td>
    <td>
     <ol>
       <li>TOEVOEGEN</li>
       <li>VERWIJDEREN</li>
       <li>ANNULEREN</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiërarchisch/stat-niveau</li>
       <li>Hiërarchisch/stat-niveau</li>
       <li>Niveau Alleen bronnen</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiermee publiceert u inhoud en wordt de cache ongeldig gemaakt.</li>
       <li>Hiermee verwijdert u inhoud en maakt u de cache ongeldig.</li>
       <li>Maakt inhoud ongeldig zonder deze te publiceren.</li>
     </ol>
     </td>
  </tr>
  <tr>
    <td>Replicatie-API</td>
    <td>Uitgeven</td>
    <td>Niet mogelijk, gebeurtenis wordt bij elke publicatie-instantie aangekaart.</td>
    <td>Beste inspanning.</td>
    <td>
     <ol>
       <li>ACTIVEREN</li>
       <li>DEACTIVEREN</li>
       <li>VERWIJDEREN</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiërarchisch/stat-niveau</li>
       <li>Hiërarchisch/stat-niveau</li>
       <li>Hiërarchisch/stat-niveau</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiermee publiceert u inhoud en wordt de cache ongeldig gemaakt.</li>
       <li>Uit auteur/publicatiereeks - hiermee verwijdert u inhoud en maakt u de cache ongeldig.</li>
       <li><p><strong> van de Rij van de Auteur </strong> - verwijdert inhoud en maakt het geheime voorgeheugen ongeldig (als teweeggebracht van de rij van de Auteur van AEM op de Publish agent).</p>
           <p><strong>Van publicatielaag</strong> - Hiermee wordt alleen de cache ongeldig (indien geactiveerd vanaf AEM Publish-laag op de flush-agent of de flushagent met alleen resources).</p>
       </li>
     </ol>
     </td>
  </tr>
  </tbody>
</table>

The two actions directly related to cache invalidation are Sling Content Distribution (SCD) API Invalidate and Replication API Deactivate.

Also, from the table, you can observe that:

* SCD API is nodig wanneer elke gebeurtenis moet worden gegarandeerd, bijvoorbeeld synchroniseren met een extern systeem dat nauwkeurige kennis vereist. Als er een publicatielaag upscaling-gebeurtenis is op het moment van de validatieaanroep, wordt een extra gebeurtenis weergegeven wanneer elke nieuwe publicatie de validatie verwerkt.

* Het gebruik van de API voor replicatie is niet gebruikelijk, maar kan worden gebruikt in gevallen waarin de trigger voor het ongeldig maken van de cache afkomstig is uit de publicatielaag en niet uit de auteurslaag. Deze methode kan nuttig zijn als Dispatcher TTL wordt gevormd.

Als u het Dispatcher-cachegeheugen wilt invalideren, kunt u het beste de handeling voor invalidatie van de SCD API van de auteur gebruiken. U kunt ook luisteren naar de gebeurtenis, zodat u vervolgens verdere downstreamacties kunt activeren.

### Verdelen van inhoud (SCD) {#sling-distribution}

>[!NOTE]
>Wanneer u de onderstaande instructies gebruikt, test u de aangepaste code in een AEM Cloud Service Dev-omgeving en niet lokaal.

Bij gebruik van de SCD-actie van Auteur ziet het implementatiepatroon er als volgt uit:

1. [&#128279;](https://sling.apache.org/documentation/bundles/content-distribution.html)

```
@Reference
private Distributor distributor;

ResourceResolver resolver = ...; // the resource resolver used for authorizing the request
String agentName = "publish";    // the name of the agent used to distribute the request

String pathToInvalidate = "/content/to/invalidate";
DistributionRequest distributionRequest = new SimpleDistributionRequest(DistributionRequestType.INVALIDATE, false, pathToInvalidate);
distributor.distribute(agentName, resolver, distributionRequest);
```

* (Optionally) Listen for an event that reflects the resource being invalidated for all Dispatcher instances:


```
package org.apache.sling.distribution.journal.shared;

import org.apache.sling.discovery.DiscoveryService;
import org.apache.sling.distribution.journal.impl.event.DistributionEvent;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import static org.apache.sling.distribution.DistributionRequestType.INVALIDATE;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_PATHS;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_TYPE;
import static org.apache.sling.distribution.event.DistributionEventTopics.AGENT_PACKAGE_DISTRIBUTED;
import static org.osgi.service.event.EventConstants.EVENT_TOPIC;

@Component(immediate = true, service = EventHandler.class, property = {
        EVENT_TOPIC + "=" + AGENT_PACKAGE_DISTRIBUTED
})
public class InvalidatedHandler implements EventHandler {
    private static final Logger LOG = LoggerFactory.getLogger(InvalidatedHandler.class);

    @Reference
    private DiscoveryService discoveryService;

    @Override
    public void handleEvent(Event event) {

        String distributionType = (String) event.getProperty(DISTRIBUTION_TYPE);

        if (INVALIDATE.name().equals(distributionType)) {
            boolean isLeader = discoveryService.getTopology().getLocalInstance().isLeader();
            // process the OSGi event on the leader author instance
            if (isLeader) {
                String[] paths = (String[]) event.getProperty(DISTRIBUTION_PATHS);
                String packageId = (String) event.getProperty(DistributionEvent.PACKAGE_ID);
                invalidated(paths, packageId);
            }
        }
    }

    private void invalidated(String[] paths, String packageId) {
        // custom logic
        LOG.info("Successfully applied package with id {}, paths {}", packageId, paths);
    }
}
```

<!-- Optionally, instead of using the isLeader approach, one could add an OSGi configuration for the PID org.apache.sling.distribution.journal.impl.publisher.DistributedEventNotifierManager and property deduplicateEvent=true. But we'll stick with just one strategy and not mention it (double-check this).**review this**-->

* (Optioneel) Voer bedrijfslogica uit in de bovenstaande methode `invalidated(String[] paths, String packageId)` .

>[!NOTE]
>
>De Adobe CDN wordt niet leeggemaakt wanneer Dispatcher ongeldig wordt gemaakt. De door Adobe beheerde CDN respecteert TTL&#39;s en het is dus niet nodig deze te verwijderen.

### Replicatie-API {#replication-api}

Hieronder ziet u het implementatiepatroon bij gebruik van de API-deactivering voor replicatie:

1. Roep in de publicatielijst de API voor replicatie aan om de publicatieagent voor Dispatcher flush te activeren.

Het uitlijnende agenteneindpunt is niet configureerbaar maar eerder preconfigured om aan Dispatcher te richten, die met de publicatieservice wordt aangepast die naast de uitlijningsagent loopt.

De spoelagent kan typisch door douanecode worden teweeggebracht die op gebeurtenissen OSGi of werkschema&#39;s wordt gebaseerd.

```
String[] paths = …
ReplicationOptions options = new ReplicationOptions();
options.setSynchronous(true);
options.setFilter( new AgentFilter {
  public boolean isIncluded (Agent agent) {
   return agent.getId().equals("flush");
  }
});

Replicator.replicate (session,ReplicationActionType.DELETE,paths, options);
```

<!-- In general, it will not be necessary to manually invalidate content in the dispatcher, but it is possible if needed.

>[!NOTE]
>Prior to AEM as a Cloud Service, there were two ways of invalidating the dispatcher cache.
>
>1. Invoke the replication agent, specifying the publish dispatcher flush agent
>2. Directly calling the `invalidate.cache` API (for example, `POST /dispatcher/invalidate.cache`)
>
>The dispatcher's `invalidate.cache` API approach will no longer be supported since it addresses only a specific dispatcher node. AEM as a Cloud Service operates at the service level, not the individual node level and so the invalidation instructions in the [Invalidating Cached Pages From AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=nl-NL) page are not longer valid for AEM as a Cloud Service.

The replication flush agent should be used. This can be done using the [Replication API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). The flush agent endpoint is not configurable but pre-configured to point to the dispatcher, matched with the publish service running the flush agent. The flush agent can typically be triggered by OSGi events or workflows.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 

The diagram presented below illustrates this.

![CDN](assets/cdnd.png "CDN")

If there is a concern that the dispatcher cache is not clearing, contact [customer support](https://helpx.adobe.com/nl/support.ec.html) who can flush the dispatcher cache if necessary.

The Adobe-managed CDN respects TTLs and thus there is no need fo it to be flushed. If an issue is suspected, [contact customer support](https://helpx.adobe.com/nl/support.ec.html) support who can flush an Adobe-managed CDN cache as necessary. -->

## Client-Side bibliotheken en consistentie van versies {#content-consistency}

Pagina&#39;s bestaan uit HTML, JavaScript, CSS en afbeeldingen. De klanten worden aangemoedigd om het [ cliënt-KantBibliotheek (clientlibs) kader ](/help/implementing/developing/introduction/clientlibs.md) te gebruiken om JavaScript en CSS middelen in de pagina&#39;s van HTML in te voeren, rekenend voor gebiedsdelen tussen bibliotheken JS.

Het clientlibs-framework biedt automatisch versiebeheer. Dit houdt in dat ontwikkelaars wijzigingen in JS-bibliotheken in broncontrole kunnen inchecken en dat de nieuwste versie beschikbaar wordt gesteld wanneer een klant zijn release onder druk zet. Zonder deze workflow moeten ontwikkelaars HTML handmatig wijzigen met verwijzingen naar de nieuwe versie van de bibliotheek. Dit is vooral lastig als dezelfde bibliotheek veel HTML-sjablonen deelt.

Wanneer de nieuwe versies van bibliotheken worden vrijgegeven voor productie, worden de HTML-pagina&#39;s waarnaar wordt verwezen, bijgewerkt met nieuwe koppelingen naar die bijgewerkte bibliotheekversies. Nadat de browsercache voor een bepaalde HTML-pagina is verlopen, hoeft u zich geen zorgen te maken dat de oude bibliotheken uit de cache van de browser worden geladen. De reden hiervoor is dat de vernieuwde pagina (vanuit AEM) nu gegarandeerd verwijst naar de nieuwe versies van de bibliotheken. Een vernieuwde HTML-pagina bevat dus alle nieuwste bibliotheekversies.

Het mechanisme achter deze mogelijkheid is een geserialiseerde hash, die aan de verbinding van de cliëntbibliotheek wordt toegevoegd. It ensures a unique, versioned url for the browser to cache the CSS/JS. The serialized hash is only updated when the contents of the client library changes. Dit houdt in dat als er niet-gerelateerde updates optreden (dat wil zeggen dat er geen wijzigingen zijn aangebracht in de onderliggende css/js van de clientbibliotheek) zelfs met een nieuwe implementatie, de verwijzing ongewijzigd blijft. Hierdoor wordt de browsercache minder verstoord.

### Longcache-versies van Client-Side Libraries inschakelen - AEM as a Cloud Service SDK Quickstart {#enabling-longcache}

De standaardopname van clientlib op een HTML-pagina ziet er als volgt uit:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Wanneer strikt clientlib-versiebeheer is ingeschakeld, wordt een hash-sleutel voor de lange termijn als selector toegevoegd aan de clientbibliotheek. Dientengevolge, ziet de cliëntlib verwijzing als dit:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Strikte clientlib-versioning is standaard ingeschakeld in alle AEM as a Cloud Service-omgeving.

Ga als volgt te werk om strikte clientlib-versioning in te schakelen in de lokale SDK Quickstart:

1. Ga naar de OSGi Configuration Manager `<host>/system/console/configMgr`
1. Zoek naar de OSGi Config voor Adobe Granite HTML Library Manager:
   * Vink het selectievakje aan zodat u Strikt versiebeheer inschakelt
   * Voer in het veld met **de naam Long term client side cachekey** de waarde /.*; hekje
1. Sla de wijzigingen op. Het is niet nodig om deze configuratie op te slaan in broncodebeheer, aangezien AEM as a Cloud Service deze configuratie automatisch inschakelt in ontwikkel-, fase- en productieomgevingen.
1. Telkens wanneer de inhoud van de clientbibliotheek wordt gewijzigd, wordt een nieuwe hash-sleutel gegenereerd en wordt de HTML-referentie bijgewerkt.
