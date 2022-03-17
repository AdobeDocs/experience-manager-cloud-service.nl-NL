---
title: Caching in AEM as a Cloud Service
description: 'Caching in AEM as a Cloud Service '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: b490d581532576bc526f9bd166003df7f2489495
workflow-type: tm+mt
source-wordcount: '1549'
ht-degree: 1%

---

# Inleiding {#intro}

Traffic passes through the CDN to an apache web server layer, which supports modules including the dispatcher. Om de prestaties te verbeteren, wordt de verzender vooral gebruikt als cache om de verwerking op de publicatieknooppunten te beperken.
De regels kunnen op de dispatcherconfiguratie worden toegepast om het even welke montages van de standaardgeheim voorgeheugenvervalsing te wijzigen, resulterend in caching bij CDN. Note that dispatcher also respects the resulting cache expiration headers if `enableTTL` is enabled in the dispatcher configuration, implying that it will refresh specific content even outside of content being republished.

Op deze pagina wordt ook beschreven hoe de cachegeheugen van de verzender ongeldig wordt gemaakt en hoe caching werkt op browserniveau met betrekking tot bibliotheken aan de clientzijde.

## Caching {#caching}

### HTML/Tekst {#html-text}

* standaard gedurende vijf minuten in cache geplaatst op basis van de `cache-control` de door de apache laag uitgestraalde header. The CDN also respects this value.
* de standaardinstelling voor het in cache plaatsen van HTML of tekst kan worden uitgeschakeld door de instelling `DISABLE_DEFAULT_CACHING` variabele in `global.vars`:

```
Define DISABLE_DEFAULT_CACHING
```

Dit kan nuttig zijn, bijvoorbeeld, wanneer uw bedrijfslogica het verfijnen van de leeftijdskopbal (met een waarde die op kalenderdag wordt gebaseerd) vereist omdat door gebrek de leeftijdskopbal aan 0 wordt geplaatst. Dat gezegd hebbende, **Wees voorzichtig bij het uitschakelen van standaardcaching.**

* can be overridden for all HTML/Text content by defining the `EXPIRATION_TIME` variable in `global.vars` using the AEM as a Cloud Service SDK Dispatcher tools.
* kan op een fijner korrelig niveau door de volgende richtlijnen worden met voeten getreden apache mod_headers:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   Wees voorzichtig bij het instellen van algemene cachebesturingskoppen of koppen die overeenkomen met een brede regex, zodat deze niet worden toegepast op inhoud die u privé wilt houden. Overweeg meerdere richtlijnen te gebruiken om ervoor te zorgen dat regels op een fijnkorrelige manier worden toegepast. Met dat gezegd, AEM as a Cloud Service zal de geheim voorgeheugenkopbal verwijderen als het ontdekt dat het is toegepast op wat het ontdekt om door verzender oncacheable te zijn, zoals die in de documentatie van de verzender wordt beschreven. In order to force AEM to always apply the caching headers, one can add the **always** option as follows:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header unset Cache-Control
        Header unset Expires
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   You must ensure that a file under `src/conf.dispatcher.d/cache` has the following rule (which is in the default configuration):

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* To prevent specific content from being cached **at the CDN**, set the Cache-Control header to *private*. For example, the following would prevent html content under a directory named **secure** from being cached at the CDN:

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

### Client-Side libraries (js,css) {#client-side-libraries}

* by using AEM&#39;s Client-Side library framework, JavaScript and CSS code is generated in such a way that browsers can cache it indefinitely, since any changes manifest as new files with a unique path.  In other words, HTML that references the client libraries will be produced as needed so customers can experience new content as it is published. Het cache-control wordt ingesteld op &#39;onveranderlijk&#39; of op 30 dagen voor oudere browsers die de waarde &#39;onveranderlijk&#39; niet respecteren.
* zie de sectie [Bibliotheken aan de clientzijde en consistentie van versies](#content-consistency) voor meer informatie.

### Images and any content large enough stored in blob storage {#images}

* by default, not cached
* kan op een fijner korrelig niveau worden ingesteld door de volgende pijn `mod_headers` richtlijnen:

   ```
      <LocationMatch "^/content/.*\.(jpeg|jpg)$">
        Header set Cache-Control "max-age=222"
        Header set Age 0
      </LocationMatch>
   ```

   See the discussion in the html/text section above for exercising caution to not cache too widely and also how to force AEM to always apply caching with the &quot;always&quot; option.

   It is necessary to ensure that a file under `src/conf.dispatcher.d/`cache has the following rule (which is in the default configuration):

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

   Zorg ervoor dat elementen die bedoeld zijn om privé te blijven in plaats van in cache te worden opgeslagen, geen deel uitmaken van de LocationMatch-instructiefilters.

   >[!NOTE]
   >De andere methoden, waaronder de [verzender-ttl AEM ACS-Commons-project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), overschrijft de waarden niet.

### Andere inhoudstypen in nodenarchief {#other-content}

* no default caching
* default cannot be set with the `EXPIRATION_TIME` variable used for html/text file types
* cache expiration can be set with the same LocationMatch strategy described in the html/text section by specifying the appropriate regex

## Dispatcher Cache Invalidation {#disp}

Over het algemeen is het niet nodig om de cachegeheugen van de verzender ongeldig te maken. In plaats daarvan moet u erop vertrouwen dat de verzender de cache vernieuwt wanneer de inhoud opnieuw wordt gepubliceerd en de CDN de headers voor het verlopen van de cache respecteert.

### Validatie van cache-verzender tijdens activering/deactivering {#cache-activation-deactivation}

Net als bij eerdere versies van AEM wordt de inhoud van de verzendingscache gewist wanneer u pagina&#39;s publiceert of de publicatie ervan ongedaan maakt. Als een cacheprobleem wordt vermoed, moeten klanten de pagina&#39;s in kwestie opnieuw publiceren en ervoor zorgen dat er een virtuele host beschikbaar is die overeenkomt met ServerAlias localhost, wat vereist is voor de ongeldigverklaring van het cachegeheugen van de verzender.


Wanneer de publicatieinstantie een nieuwe versie van een pagina of element van de auteur ontvangt, gebruikt deze de agent flush om de juiste paden op de dispatcher ongeldig te maken. Het bijgewerkte pad wordt samen met de bovenliggende elementen uit de cache van de verzender verwijderd tot een niveau (u kunt dit configureren met de [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level).

### Explicit dispatcher cache invalidation {#explicit-invalidation}

Over het algemeen hoeft de inhoud in de verzender niet handmatig ongeldig te worden gemaakt, maar dit is mogelijk als dat nodig is.

>[!NOTE]
>Voorafgaand aan AEM as a Cloud Service, waren er twee manieren om het berichtchergeheime voorgeheugen ongeldig te maken.
>
>1. Roep de replicatieagent aan, die de publicatiedispatcher spoelagent specificeert
>2. Directly calling the `invalidate.cache` API (for example, `POST /dispatcher/invalidate.cache`)

>
>De verzender `invalidate.cache` API-benadering wordt niet meer ondersteund omdat deze alleen betrekking heeft op een specifiek verzendingsknooppunt. AEM as a Cloud Service werkt op het de dienstniveau, niet het individuele knoopniveau en zo de ongeldigingsinstructies in [In cache geplaatste pagina&#39;s ongeldig maken van AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) is niet langer geldig voor AEM as a Cloud Service.

The replication flush agent should be used. Dit kan worden gedaan gebruikend [Replicatie-API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). Het uitlijnmiddeleindpunt is niet configureerbaar maar pre-gevormd om aan de dispatcher te richten, die met de publicatieservice wordt aangepast die de uitlijningsagent in werking stelt. De spoelagent kan typisch door gebeurtenissen OSGi of werkschema&#39;s worden teweeggebracht.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 
-->

Dit wordt geïllustreerd in het onderstaande diagram.

![CDN](assets/cdnd.png "CDN")

Als er een probleem is dat de verzender cache niet wordt gewist, neemt u contact op met [klantenondersteuning](https://helpx.adobe.com/support.ec.html) die de verzendingscache zo nodig kunnen leegmaken.

The Adobe-managed CDN respects TTLs and thus there is no need fo it to be flushed. If an issue is suspected, [contact customer support](https://helpx.adobe.com/support.ec.html) support who can flush an Adobe-managed CDN cache as necessary.

## Client-Side bibliotheken en consistentie van versies {#content-consistency}

Pagina&#39;s bestaan uit HTML, JavaScript, CSS en afbeeldingen. Customers are encouraged to leverage the [Client-Side Libraries (clientlibs) framework](/help/implementing/developing/introduction/clientlibs.md) to import Javascript and CSS resources into HTML pages, taking into account dependencies between JS libraries.

Het clientlibs-framework biedt automatisch versiebeheer, wat betekent dat ontwikkelaars wijzigingen in JS-bibliotheken kunnen inchecken in broncontrole en dat de nieuwste versie beschikbaar wordt gesteld wanneer een klant zijn release opdringt. Zonder dit, zouden de ontwikkelaars HTML met verwijzingen naar de nieuwe versie van de bibliotheek manueel moeten veranderen, wat vooral bezwaarlijk is als vele malplaatjes van HTML de zelfde bibliotheek delen.

When the new versions of libraries are released to production, the referencing HTML pages are updated with new links to those updated library versions. Als de browsercache voor een bepaalde HTML-pagina is verlopen, is het niet van belang dat de oude bibliotheken worden geladen uit de browsercache, aangezien de vernieuwde pagina (van AEM) nu gegarandeerd naar de nieuwe versies van de bibliotheken verwijst. Met andere woorden, een vernieuwde HTML-pagina bevat alle meest recente bibliotheekversies.

Het mechanisme hiervoor is een geserialiseerde hash, die aan de verbinding van de cliëntbibliotheek wordt toegevoegd, die een unieke, versioned url voor browser verzekert om CSS/JS in het voorgeheugen onder te brengen. De geserialiseerde hash wordt alleen bijgewerkt wanneer de inhoud van de clientbibliotheek wordt gewijzigd. Dit betekent dat als er niet-verwante updates optreden (dat wil zeggen geen wijzigingen in de onderliggende css/js van de clientbibliotheek), zelfs met een nieuwe implementatie, de verwijzing ongewijzigd blijft, waardoor de browsercache minder wordt verstoord.

### Longcache-versies van Client Side Libraries inschakelen - AEM as a Cloud Service SDK QuickStart {#enabling-longcache}

Default clientlib includes on an HTML page look like the following example:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

When strict clientlib versioning is enabled, a long term hash key is added as a selector to the client library. Dientengevolge, ziet de cliëntlib verwijzing als dit:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Strikte clientlib-versioning is standaard ingeschakeld in alle AEM as a Cloud Service omgevingen.

Om strikte clientlib versioning in lokale SDK toe te laten voert QuickStart de volgende acties uit:

1. Navigate to the OSGi Configuration manager `<host>/system/console/configMgr`
1. Vind OSGi Config voor de Manager van de Bibliotheek van de HTML van Adobe Granite:
   * Check the checkbox to enable Strict Versioning
   * In the field labeled Long term client side cache key, enter the value of /.*;hash
1. Sla de wijzigingen op. Merk op dat het niet noodzakelijk is om deze configuratie in broncontrole te bewaren aangezien AEM as a Cloud Service deze configuratie automatisch in dev, stadium en productiemilieu&#39;s zal toelaten.
1. Telkens wanneer de inhoud van de clientbibliotheek wordt gewijzigd, wordt een nieuwe hash-toets gegenereerd en wordt de HTML-verwijzing bijgewerkt.
