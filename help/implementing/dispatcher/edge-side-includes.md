---
title: Inclusief Edge-zijkanten
description: De Adobe Beheerde CDN ondersteunt nu Edge Side Includes (ESI), een opmaaktaal voor dynamische webinhoud-assemblage op randniveau.
feature: Dispatcher
exl-id: 35093477-2788-4f69-80a9-899f43567cae
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Inclusief Edge-zijkanten {#edge-side-includes}

>[!NOTE]
>Deze functie is nog niet algemeen beschikbaar. Als u wilt deelnemen aan het programma voor vroegtijdige adoptie, stuurt u een e-mail `aemcs-cdn-config-adopter@adobe.com` met een beschrijving van uw gebruiksscenario.

De snelheid van de levering van inhoud profiteert van agressief caching van pagina&#39;s, die door geheim voorgeheugenkopballen met hoge tijd aan levende (TTL) waarden worden bereikt. Dit kan een uitdaging zijn wanneer pagina&#39;s dynamische inhoud bevatten, die vaak moet worden vernieuwd of mogelijk helemaal niet in cache kan worden geplaatst. Gelukkig, zijn er strategieën waar de bevattende pagina van HTML met hoge TTL in het voorgeheugen ondergebracht kan worden, die het halen van de meer dynamische inhoudsfragmenten aan een recentere tijd uitstellen, of door cliënt-kant Javascript of bij CDN. De laatste aanpak is een standaard die Edge Side Includes (ESI) wordt genoemd. Deze wordt ondersteund voor sites die worden gerenderd met AEM publicatie. De HTML bevat ESI-tags die de CDN instrueren de weergave van de pagina naar de browser uit te stellen totdat deze de tags evalueert en aanvullende, dynamischere (lagere TTL) inhoud uit de oorspronkelijke cache (of CDN-cache als de TTL niet is verlopen) ophalen.

Sommige gebruiksgevallen waarbij Edge Side Includes handig kan zijn:

* De naam van een eindgebruiker weergeven of andere informatie die uniek is voor een eindgebruiker.
* Een lijst weergeven met recente informatie, zoals nieuwsartikelen of aandelenkoersen.

## ESI-syntaxis {#esi-syntax}

De ESI-syntaxis ziet er als volgt uit als een bovenliggende pagina `/content/page.html` een fragment bevat `content/snippets/mysnippet.html` .

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

Zie de [ ESI specificatie ](https://www.w3.org/TR/esi-lang/) voor details.

### Overwegingen {#esi-syntax-considerations}

* De volgende ESI-tags worden ondersteund: include, comment, remove.
* ESI-tags worden achtereenvolgens verwerkt in plaats van gelijktijdig op de CDN, zodat veel ESI-tags op een pagina met lage TTL&#39;s latentie kunnen toevoegen aan de gebruikerservaring.
* De maximale diepte van ESI: inclusief verwerking is 5.
* De maximale totale ESI: inclusief verwerkingsfragmenten is 256.


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
| **no-gzip** | Indien ingesteld op 1, wordt de pagina HTML verzonden van apache naar de niet-gecomprimeerde CDN. Dit is noodzakelijk voor ESI aangezien de inhoud moet worden verzonden naar CDN niet gecomprimeerd zodat CDN de tags ESI kan zien en evalueren.<br/><br/> zowel de ouderpagina als de inbegrepen fragmenten zouden no-gzip aan 1 moeten plaatsen.<br/><br/> dit plaatsen treedt om het even welke compressie met voeten die Apache anders zou kunnen hebben gebruikt, die op de 1} waarden van het verzoek {wordt gebaseerd.`Accept-Encoding` |
| **x-aem-esi** | Indien ingesteld op &quot;on&quot;, evalueert de CDN de ESI-tags van de bovenliggende HTML-pagina.  Standaard is de koptekst niet ingesteld. |
| **x-a-em-compress** | Als deze optie is ingesteld op &quot;on&quot;, comprimeert de CDN de inhoud van de CDN naar de browser. Aangezien de transmissie van de ouderpagina van apache aan CDN voor ESI moet uncompressed zijn om te werken (`no-gzip` reeks aan 1), kan dit latentie verminderen.<br/><br/> als deze kopbal niet wordt geplaatst, wanneer CDN inhoud van de oorsprong niet samengeperste terugwint, zou het inhoud aan de cliënt niet samengeperste, eveneens dienen. Daarom is het nodig deze header in te stellen als `no-gzip` is ingesteld op 1 (vereist voor ESI) en als inhoud die is gecomprimeerd van de CDN naar de browser moet worden verzonden. |

## Dynamisch afspelen opnemen {#esi-sdi}

Terwijl niet vereist, [ Sling Dynamisch omvat ](https://sling.apache.org/documentation/bundles/dynamic-includes.html) (SDI) kan worden gebruikt om fragmenten te produceren ESI die bij CDN worden geïnterpreteerd.
