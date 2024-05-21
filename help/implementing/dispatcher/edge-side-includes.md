---
title: Inclusief randzijde
description: De Adobe Beheerde CDN ondersteunt nu Edge Side Includes (ESI), een opmaaktaal voor dynamische webinhoud-assemblage op randniveau.
feature: Dispatcher
source-git-commit: 3aab5d3beb7bedf7a61bc557be349f2aa5ed8a7b
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Inclusief randzijde {#edge-side-includes}

>[!NOTE]
>Deze functie is nog niet algemeen beschikbaar. Als u wilt deelnemen aan het programma voor vroegtijdige adoptie, kunt u een e-mail sturen `aemcs-cdn-config-adopter@adobe.com` en beschrijf uw gebruiksgeval.

De snelheid van de levering van inhoud profiteert van agressief caching van pagina&#39;s, die door geheim voorgeheugenkopballen met hoge tijd aan levende (TTL) waarden worden bereikt. Dit kan een uitdaging zijn wanneer pagina&#39;s dynamische inhoud bevatten, die vaak moet worden vernieuwd of mogelijk helemaal niet in cache kan worden geplaatst. Gelukkig, zijn er strategieën waar de bevattende pagina van HTML met hoge TTL in het voorgeheugen ondergebracht kan worden, die het halen van de meer dynamische inhoudsfragmenten aan een recentere tijd uitstellen, of door cliënt-kant Javascript of bij CDN. De laatste aanpak is een standaard genaamd Edge Side Includes (ESI), die wordt ondersteund voor sites die worden gerenderd met AEM publicatie. De HTML bevat ESI-tags die de CDN instrueren de weergave van de pagina naar de browser uit te stellen totdat deze de tags evalueert en aanvullende, dynamischere (lagere TTL) inhoud uit de oorspronkelijke cache (of CDN-cache als de TTL niet is verlopen) ophalen.

In sommige gevallen kan het handig zijn randzijkanten op te nemen:

* De naam van een eindgebruiker weergeven of andere informatie die uniek is voor een eindgebruiker.
* Een lijst weergeven met recente informatie, zoals nieuwsartikelen of aandelenkoersen.

## ESI-syntaxis {#esi-syntax}

De ESI-syntaxis is als volgt bij een bovenliggende pagina `/content/page.html` bevat een fragment `content/snippets/mysnippet.html`.

```
<html>
  <head>
      <title>My Site</title>
  </head>
  <body>
    <div id="content">
      <esi:include src="/content/snippets/mysnippet.html" />
    </div>
  </body>
</html>
```

Zie de [ESI-specificatie](https://www.w3.org/TR/esi-lang/) voor meer informatie.

### Overwegingen (#esi-syntax-overwegingen)

* De volgende ESI-tags worden ondersteund: include, comment, remove.
* ESI-tags worden achtereenvolgens verwerkt in plaats van gelijktijdig op de CDN, zodat veel ESI-tags op een pagina met lage TTL&#39;s latentie kunnen toevoegen aan de gebruikerservaring.
* De maximale diepte van ESI:include-verwerking is 5.
* De maximale totale ESI:inclusief verwerkingsfragmenten is 256.


## Apache-configuratie {#esi-apache}

Als u pagina&#39;s met ESI-tags hebt, moet u de volgende eigenschappen in de Apache-configuratie declareren:

```
<LocationMatch "/parent-pages/*content/page.html">
   # disable dispatcher compression
   SetEnv no-gzip 1
   # enable esi processing 
   Header set x-aem-esi "on"
   # enable edgeCDN compression
   Header set x-aem-compress "on"

   # typically the main page is cached at the CDN
   Header always set Cache-Control "max-age=300"
 </LocationMatch>


<LocationMatch "/content/snippets/mysnippet.html">
  SetEnv no-gzip 1

  # typically the included page is either set to a lower TTL than the parent page, or not cached at all, as these 2 commented declarations show, respectively:
  #Header always set Cache-Control "no-cache"
  #Header always set Cache-Control "max-age=50"
 </LocationMatch> 
```

De gevormde eigenschappen hebben het volgende gedrag:

| Eigenschap | Gedrag |
|-----------|--------------------------|
| **zonder gzip** | Indien ingesteld op 1, wordt de pagina HTML verzonden van apache naar de niet-gecomprimeerde CDN. Dit is noodzakelijk voor ESI aangezien de inhoud moet worden verzonden naar CDN niet gecomprimeerd zodat CDN de tags ESI kan zien en evalueren.<br/><br/>Zowel de bovenliggende pagina als de opgenomen fragmenten moeten no-gzip instellen op 1.<br/><br/>Deze instelling overschrijft de compressie-instelling die Apache anders heeft gebruikt, op basis van de aanvraag `Accept-Encoding` waarden. |
| **x-aem-esi** | Indien ingesteld op &quot;on&quot;, evalueert de CDN de ESI-tags van de bovenliggende HTML-pagina.  Standaard is de koptekst niet ingesteld. |
| **x-aem-compress** | Als deze optie is ingesteld op &quot;on&quot;, comprimeert de CDN de inhoud van de CDN naar de browser. Aangezien de overdracht van de bovenliggende pagina van apache naar CDN moet worden gedecomprimeerd om te werken (geen gzip ingesteld op 1), kan dit de latentie verminderen.<br/><br/>Als deze kopbal niet wordt geplaatst, wanneer CDN inhoud van de oorsprong niet samengeperste terugwint, zou het inhoud aan de cliënt niet samengeperste, eveneens dienen. Daarom is het noodzakelijk om deze kopbal te plaatsen als no-gzip aan 1 (vereist voor ESI) wordt geplaatst en het wordt gewenst om inhoud te dienen die van CDN aan browser wordt gecomprimeerd. |

## Dynamisch afspelen opnemen {#esi-sdi}

Niet vereist, [Dynamisch afspelen opnemen](https://sling.apache.org/documentation/bundles/dynamic-includes.html) (SDI) kan worden gebruikt om ESI-fragmenten te genereren die op de CDN worden geïnterpreteerd.

