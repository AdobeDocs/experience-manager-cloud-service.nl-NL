---
title: De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan
description: De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Met de functie Sling Model Exporter kunt u Sling Models-objecten serialiseren in een JSON-indeling. Deze functie wordt op grote schaal gebruikt omdat SPA (toepassingen van één pagina) gemakkelijk toegang hebben tot gegevens van AEM. Op de implementatiezijde wordt de bibliotheek van het Gegevensbestand van Jacson gebruikt om deze voorwerpen in series te vervaardigen.

De rangschikking is een recursieve verrichting. Vanaf een &quot;wortelvoorwerp&quot;, herhaalt het recursief door alle in aanmerking komende voorwerpen en rangschikt hen en hun kinderen. U kunt een beschrijving vinden waarin de velden zijn geserialiseerd [dit artikel](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Deze benadering serialiseert alle types van voorwerpen in JSON, en natuurlijk kan het ook Sling serialiseren `ResourceResolver` object, als deze onder de serialisatieregels valt. Dit is een probleem, zoals de `ResourceResolver` de dienst (en bijgevolg ook het de dienstvoorwerp die het vertegenwoordigt) bezit potentieel gevoelige informatie, die niet zou moeten worden openbaar gemaakt. Bijvoorbeeld:

* De gebruikers-id
* De zoekpaden voor het omzetten van relatieve paden
* De `propertyMap`.

Vooral gevoelig is het `propertyMap` (zie de API-documentatie van [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), aangezien het een interne gegevensstructuur is, die voor vele doeleinden kan worden gebruikt - bijvoorbeeld het in cache plaatsen van voorwerpen die de zelfde levenscyclus zoals `ResourceResolver`. Het in series vervaardigen van deze kan implementatiedetails lekken en potentieel een veiligheidseffect hebben, aangezien de gegevens worden blootgesteld die niet leesbaar en toegankelijk aan een eindgebruiker zouden moeten zijn. Daarom `ResourceResolvers` mag niet met een serienummer in JSON worden ingevoerd.

Adobe is van plan de serialisatie van `ResourceResolvers` in twee stappen:

1. Vanaf AEM as a Cloud Service release 14697, telkens als een `ResourceResolver` is geserialiseerd AEM zal een waarschuwingsbericht registreren. Alle klanten worden aangemoedigd om hun toepassingslogboeken voor deze logboekverklaringen te controleren en hun codebase dienovereenkomstig aan te passen.
1. Op een recentere punt zal de Adobe de rangschikking van ResourceResolvers als JSON onbruikbaar maken.

## Implementatie {#implementation}

Het WARN bericht wordt geregistreerd zowel in AEM as a Cloud Service als lokale AEMinstanties SDK, en het kijkt als dit:

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Dit logboekbericht betekent dat tijdens het proces in series vervaardigen van `/content/…/page` in JSON a `ResourceResolver` is al geserialiseerd. Op aanvraag `/content/../page.model.json` u kunt controleren waar precies de gebieden van `ResourceResolver` worden getoond, en gebruik dat om de Sling Model klasse te identificeren die eigenlijk dit gedrag teweegbrengt.


>[!NOTE]
>
>AEM Core Components zijn gevalideerd om dit probleem niet te kunnen ondervangen.

## Aangevraagde actie {#requested-action}

De Adobe verzoekt al hun klanten om hun toepassingslogboeken en codebasis te controleren om te zien of worden zij beïnvloed door dit probleem, en de douanetoepassing waar nodig te veranderen, zodat dit WARN bericht niet meer verschijnt.

Aangenomen wordt dat deze vereiste wijzigingen in de meeste gevallen recht naar voren zijn, aangezien de `ResourceResolver` objecten zijn helemaal niet vereist in de JSON-uitvoer, omdat de informatie in deze objecten gewoonlijk niet vereist is voor frontend-toepassingen. Dat betekent in de meeste gevallen dat het voldoende is de `ResourceResolver` door Jackson overwogen object (zie [regels](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)).

Als een verkoopmodel door dit probleem wordt beïnvloed maar niet wordt veranderd, het uitdrukkelijk onbruikbaar maken van serizalization van `ResourceResolver` -object (zoals uitgevoerd door Adobe als de tweede stap) een wijziging in de JSON-uitvoer afdwingen.
