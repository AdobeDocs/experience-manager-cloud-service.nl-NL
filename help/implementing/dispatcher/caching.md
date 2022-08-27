---
title: Caching in AEM as a Cloud Service
description: 'Caching in AEM as a Cloud Service '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: 42c1d4fcfef4487aca6225821c16304ccf4deb04
workflow-type: tm+mt
source-wordcount: '2591'
ht-degree: 1%

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

## Expliciete ongeldigverklaring van de verzender-cache {#explicit-invalidation}

Adobe raadt aan om de levenscyclus van de levering van inhoud te regelen op standaard cacheheaders. Indien nodig is het echter mogelijk inhoud rechtstreeks in de verzender ongeldig te maken.

De volgende lijst bevat scenario&#39;s waar u uitdrukkelijk het geheime voorgeheugen zou kunnen willen invalideren (terwijl naar keuze het luisteren naar de voltooiing van de ongeldigverklaring):

* Na het publiceren van inhoud zoals ervaringsfragmenten of inhoudsfragmenten, het ongeldig maken van gepubliceerde en in cache geplaatste inhoud die naar die elementen verwijst.
* Een extern systeem waarschuwen wanneer pagina&#39;s waarnaar wordt verwezen, zijn ongeldig gemaakt.

Er zijn twee benaderingen om het geheime voorgeheugen uitdrukkelijk ongeldig te maken:

* De voorkeursbenadering is het gebruik van de Sling Content Distribution (SCD) van de auteur.
* Door de replicatie-API te gebruiken om de publicatiedispatcher te activeren, maakt u replicatieagent leeg.

De benaderingen verschillen in termen van laagbeschikbaarheid, de capaciteit om gebeurtenissen en gebeurtenisverwerkingsgarantie te dedupliceren. In de onderstaande tabel staan de volgende opties:

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>N.v.t.</th>
    <th>Beschikbaarheid van niveaus</th>
    <th>Deduplicatie </th>
    <th>Garantie </th>
    <th>Actie </th>
    <th>Gevolgen </th>
    <th>Beschrijving </th>
  </tr>  
  <tr>
    <td>SCD-API (Sling Content Distribution)</td>
    <td>Auteur</td>
    <td>Mogelijk met de API voor detectie of het inschakelen van de <a href="https://github.com/apache/sling-org-apache-sling-distribution-journal/blob/e18f2bd36e8b43814520e87bd4999d3ca77ce8ca/src/main/java/org/apache/sling/distribution/journal/impl/publisher/DistributedEventNotifierManager.java#L146-L149">deduplicatiemodus</a>.</td>
    <td>Ten minste één keer.</td>
    <td>
     <ol>
       <li>TOEVOEGEN</li>
       <li>DELETE</li>
       <li>ONGELDIG</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiërarchisch/Stat Niveau</li>
       <li>Hiërarchisch/Stat Niveau</li>
       <li>Level Resource-Only</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiermee publiceert u inhoud en maakt u de cache ongeldig.</li>
       <li>Hiermee verwijdert u inhoud en maakt u de cache ongeldig.</li>
       <li>Hiermee wordt inhoud ongeldig gemaakt zonder deze te publiceren.</li>
     </ol>
     </td>
  </tr>
  <tr>
    <td>Replicatie-API</td>
    <td>Publicatie</td>
    <td>Niet mogelijk. De gebeurtenis wordt op elke publicatie-instantie weergegeven.</td>
    <td>Beste inspanning.</td>
    <td>
     <ol>
       <li>ACTIVEREN</li>
       <li>DEACTIVEREN</li>
       <li>DELETE</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiërarchisch/Stat Niveau</li>
       <li>Hiërarchisch/Stat Niveau</li>
       <li>Hiërarchisch/Stat Niveau</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hiermee publiceert u inhoud en maakt u de cache ongeldig.</li>
       <li>Uit auteur/publicatiereeks - hiermee verwijdert u inhoud en maakt u de cache ongeldig.</li>
       <li><p><strong>Van Auteursniveau</strong> - Verwijdert inhoud en maakt de cache ongeldig (indien geactiveerd uit de AEM-auteurscategorie in de publicatieagent).</p>
           <p><strong>Uit publicatiereeks</strong> - Maakt alleen de cache ongeldig (indien geactiveerd vanaf de AEM-publicatielaag op de Flush- of Resource-Only-flush-agent).</p>
       </li>
     </ol>
     </td>
  </tr>
  </tbody>
</table>

Houd er rekening mee dat de twee acties die rechtstreeks verband houden met de invalidatie van de cache, de API voor invalidatie en replicatie van inhoud (Sling Content Distribution, SCD)-API deactiveren zijn.

Uit de tabel blijkt ook dat:

* SCD API is nodig wanneer elke gebeurtenis moet worden gegarandeerd, bijvoorbeeld synchroniseren met een extern systeem dat nauwkeurige kennis vereist. Merk op dat als er een publiceer rij upscaling gebeurtenis op het tijdstip van de ongeldigingsvraag is, een extra gebeurtenis zal worden opgeheven wanneer elk nieuw publiceert de ongeldigverklaring verwerkt.

* Het gebruik van de API voor replicatie is niet gebruikelijk, maar moet worden gebruikt in gevallen waarin de trigger voor het ongeldig maken van de cache afkomstig is uit de publicatielaag en niet uit de auteurslaag. Dit zou nuttig kunnen zijn als de verzender TTL wordt gevormd.

Als u de verzender-cache wilt invalideren, wordt u aangeraden de handeling voor invalidatie van de SCD API van de auteur te gebruiken. Bovendien kunt u ook naar de gebeurtenis luisteren, zodat u vervolgens verdere downstreamacties kunt activeren.

### Verdelen van inhoud (SCD) {#sling-distribution}

>[!NOTE]
>Houd er rekening mee dat u de aangepaste code in een AEM Cloud Service Dev-omgeving en niet lokaal moet testen wanneer u de onderstaande instructies gebruikt.

Bij gebruik van de SCD-actie van Auteur ziet het implementatiepatroon er als volgt uit:

1. Schrijf aangepaste code van Auteur om de distributie van de inhoud van de regel aan te roepen [API](https://sling.apache.org/documentation/bundles/content-distribution.html)De handeling voor ongeldig maken wordt doorgegeven met een lijst met paden:

```
@Reference
private Distributor distributor;

ResourceResolver resolver = ...; // the resource resolver used for authorizing the request
String agentName = "publish";    // the name of the agent used to distribute the request

String pathToInvalidate = "/content/to/invalidate";
DistributionRequest distributionRequest = new SimpleDistributionRequest(DistributionRequestType.INVALIDATE, false, pathToInvalidate);
distributor.distribute(agentName, resolver, distributionRequest);
```

* (Optioneel) Luister naar een gebeurtenis die de bron weergeeft die ongeldig wordt gemaakt voor alle verzendersinstanties:


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

* (Optioneel) Voer bedrijfslogica uit in de `invalidated(String[] paths, String packageId)` hierboven beschreven methode.

>[!NOTE]
>
>De Adobe CDN wordt niet leeggemaakt wanneer de verzender ongeldig wordt gemaakt. De Adobe-beheerde CDN respecteert TTLs en zo is er geen behoefte aan het worden gespoeld.

### Replicatie-API {#replication-api}

Hieronder ziet u het implementatiepatroon bij gebruik van de API-deactivering voor replicatie:

1. Voor publiceer rij, roep de Replicatie API om publicatieverzender te teweegbrengen leegmaken replicatieagent.

Het uitlijnmiddeleindpunt is niet configureerbaar maar eerder preconfigured om aan dispatcher te richten, die met de publicatieservice wordt aangepast die naast de uitlijningsagent loopt.

De spoelagent kan typisch door douanecode worden teweeggebracht die op gebeurtenissen OSGi of werkschema&#39;s wordt gebaseerd.

```
String[] paths = …
ReplicationOptions options = new ReplicationOptions();
options.setSynchronous(true);
options.setFilter( new AgentFilter {
  public boolean isIncluded (Agent agent) {
   return agent.getId().equals(“flush”);
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
>The dispatcher's `invalidate.cache` API approach will no longer be supported since it addresses only a specific dispatcher node. AEM as a Cloud Service operates at the service level, not the individual node level and so the invalidation instructions in the [Invalidating Cached Pages From AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) page are not longer valid for AEM as a Cloud Service.

The replication flush agent should be used. This can be done using the [Replication API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). The flush agent endpoint is not configurable but pre-configured to point to the dispatcher, matched with the publish service running the flush agent. The flush agent can typically be triggered by OSGi events or workflows.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 

The diagram presented below illustrates this.

![CDN](assets/cdnd.png "CDN")

If there is a concern that the dispatcher cache isn't clearing, contact [customer support](https://helpx.adobe.com/support.ec.html) who can flush the dispatcher cache if necessary.

The Adobe-managed CDN respects TTLs and thus there is no need fo it to be flushed. If an issue is suspected, [contact customer support](https://helpx.adobe.com/support.ec.html) support who can flush an Adobe-managed CDN cache as necessary. -->

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
