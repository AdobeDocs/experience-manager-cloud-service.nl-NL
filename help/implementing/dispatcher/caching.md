---
title: Caching in AEM as a Cloud Service
description: 'Caching in AEM as a Cloud Service '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: a6e0b19fae56328a587cf2fb8fdca29fe373b084
workflow-type: tm+mt
source-wordcount: '1568'
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
* kan op een fijner korrelig niveau door de volgende richtlijnen worden met voeten getreden apache mod_headers:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

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
   >Houd er rekening mee dat de verzender nog steeds inhoud in cache plaatst volgens zijn eigen [caching-regels](https://helpx.adobe.com/experience-manager/kb/find-out-which-requests-does-aem-dispatcher-cache.html). Als u de inhoud echt privé wilt maken, moet u ervoor zorgen dat deze niet in de cache wordt opgeslagen door de verzender.

### Client-Side bibliotheken (js,css) {#client-side-libraries}

* door gebruik te maken van AEM clientbibliotheekframework worden JavaScript- en CSS-code zodanig gegenereerd dat browsers deze oneindig in cache kunnen plaatsen, aangezien elke wijziging zich voordoet als nieuwe bestanden met een uniek pad.  Met andere woorden, HTML dat verwijzingen de cliëntbibliotheken zullen worden geproduceerd zoals nodig zodat de klanten nieuwe inhoud kunnen ervaren aangezien het wordt gepubliceerd. Het cache-control wordt ingesteld op &#39;onveranderlijk&#39; of op 30 dagen voor oudere browsers die de waarde &#39;onveranderlijk&#39; niet respecteren.
* zie de sectie [Bibliotheken aan de clientzijde en consistentie van versies](#content-consistency) voor meer informatie.

### Afbeeldingen en inhoud die groot genoeg is en in blokopslag is opgeslagen {#images}

* standaard niet in cache geplaatst
* kan op een fijner korrelig niveau worden ingesteld door de volgende pijn `mod_headers` richtlijnen:

   ```
      <LocationMatch "^/content/.*\.(jpeg|jpg)$">
        Header set Cache-Control "max-age=222"
        Header set Age 0
      </LocationMatch>
   ```

   Zie de bespreking in de html/tekstsectie hierboven voor het uitoefenen van voorzichtigheid om niet te wijd in het voorgeheugen onder te brengen en ook hoe te om AEM te dwingen altijd caching met de &quot;altijd&quot;optie toe te passen.

   Er moet voor worden gezorgd dat een `src/conf.dispatcher.d/`het geheime voorgeheugen heeft de volgende regel (die in de standaardconfiguratie is):

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

   Zorg ervoor dat elementen die bedoeld zijn om privé te blijven in plaats van in cache te worden opgeslagen, geen deel uitmaken van de LocationMatch-instructiefilters.

   >[!NOTE]
   >De andere methoden, waaronder de [verzender-ttl AEM ACS-Commons-project](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), overschrijft de waarden niet.

### Andere inhoudstypen in nodenarchief {#other-content}

* geen standaardcaching
* standaard kan niet worden ingesteld met de `EXPIRATION_TIME` variabele die wordt gebruikt voor html/text-bestandstypen
* cache-vervaldatum kan worden ingesteld met dezelfde LocationMatch-strategie die in de html/text-sectie wordt beschreven door de juiste regex op te geven

## Ongeldige validatie van cache-verzending {#disp}

Over het algemeen is het niet nodig om de cachegeheugen van de verzender ongeldig te maken. In plaats daarvan moet u erop vertrouwen dat de verzender de cache vernieuwt wanneer de inhoud opnieuw wordt gepubliceerd en de CDN de headers voor het verlopen van de cache respecteert.

### Validatie van cache-verzender tijdens activering/deactivering {#cache-activation-deactivation}

Net als bij eerdere versies van AEM wordt de inhoud van de verzendingscache gewist wanneer u pagina&#39;s publiceert of de publicatie ervan ongedaan maakt. Als een cacheprobleem wordt vermoed, moeten klanten de pagina&#39;s in kwestie opnieuw publiceren.

Wanneer de publicatieinstantie een nieuwe versie van een pagina of element van de auteur ontvangt, gebruikt deze de agent flush om de juiste paden op de dispatcher ongeldig te maken. Het bijgewerkte pad wordt samen met de bovenliggende elementen uit de cache van de verzender verwijderd tot een niveau (u kunt dit configureren met de [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level).

### Expliciete cachevalidatie van verzender {#explicit-invalidation}

Over het algemeen hoeft de inhoud in de verzender niet handmatig ongeldig te worden gemaakt, maar dit is mogelijk als dat nodig is.

>[!NOTE]
>Voorafgaand aan AEM as a Cloud Service, waren er twee manieren om het berichtchergeheime voorgeheugen ongeldig te maken.
>
>1. Roep de replicatieagent aan, die de publicatiedispatcher spoelagent specificeert
>2. Het direct roepen van `invalidate.cache` API (bijvoorbeeld `POST /dispatcher/invalidate.cache`)

>
>De verzender `invalidate.cache` API-benadering wordt niet meer ondersteund omdat deze alleen betrekking heeft op een specifiek verzendingsknooppunt. AEM as a Cloud Service werkt op het de dienstniveau, niet het individuele knoopniveau en zo de ongeldigingsinstructies in [In cache geplaatste pagina&#39;s ongeldig maken van AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) is niet langer geldig voor AEM as a Cloud Service.

De replicatie spoelmiddel zou moeten worden gebruikt. Dit kan worden gedaan gebruikend de Replicatie API. De [Replicatie-API-documentatie is beschikbaar](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html)en voor een voorbeeld van het leegmaken van de cache raadpleegt u de [API voorbeeldpagina](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (in het bijzonder `CustomStep` voorbeeld die een replicatieactie van type ACTIVATE aan alle beschikbare agenten uitgeven). Het uitlijnmiddeleindpunt is niet configureerbaar maar pre-gevormd om aan de dispatcher te richten, die met de publicatieservice wordt aangepast die de uitlijningsagent in werking stelt. De spoelagent kan typisch door gebeurtenissen OSGi of werkschema&#39;s worden teweeggebracht.

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
