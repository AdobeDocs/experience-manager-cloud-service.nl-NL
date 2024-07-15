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

De rangschikking is een recursieve verrichting. Vanaf een &quot;wortelvoorwerp&quot;, herhaalt het recursief door alle in aanmerking komende voorwerpen en rangschikt hen en hun kinderen. U kunt een beschrijving vinden welke gebieden in [ dit artikel ](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not) in series worden vervaardigd.

Deze benadering serialiseert alle types van voorwerpen in JSON, en natuurlijk kan het een Sling `ResourceResolver` voorwerp ook serialiseren, als het door de rangschikkingsregels wordt behandeld. Dit is problematisch, omdat de `ResourceResolver` -service (en dus ook het serviceobject dat deze vertegenwoordigt) mogelijk gevoelige informatie bevat, die niet openbaar moet worden gemaakt. Bijvoorbeeld:

* De gebruikers-id
* De zoekpaden voor het omzetten van relatieve paden
* De `propertyMap` .

Speciaal gevoelig is `propertyMap` (zie de API documentatie van [`getPropertyMap` ](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), aangezien het een interne gegevensstructuur is, die voor vele doeleinden kan worden gebruikt - bijvoorbeeld caching voorwerpen die de zelfde levenscyclus zoals `ResourceResolver` delen. Het in series vervaardigen van deze kan implementatiedetails lekken en potentieel een veiligheidseffect hebben, aangezien de gegevens worden blootgesteld die niet leesbaar en toegankelijk aan een eindgebruiker zouden moeten zijn. Daarom moet `ResourceResolvers` niet met serienummering in JSON worden gecodeerd.

Adobe is van plan de serialisatie van `ResourceResolvers` uit te schakelen in een aanpak die uit twee stappen bestaat:

1. Vanaf AEM as a Cloud Service versie 14697 wordt een waarschuwingsbericht weergegeven als een `ResourceResolver` is geserialiseerd AEM. Alle klanten worden aangemoedigd om hun toepassingslogboeken voor deze logboekverklaringen te controleren en hun codebase dienovereenkomstig aan te passen.
1. Op een recentere punt zal de Adobe de rangschikking van ResourceResolvers als JSON onbruikbaar maken.

## Implementatie {#implementation}

Het WARN-bericht wordt zowel in AEM as a Cloud Service als in lokale AEM SDK-instanties geregistreerd en ziet er als volgt uit:

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Dit logbericht betekent dat tijdens het proces van het serialiseren van `/content/…/page` in JSON `ResourceResolver` al met serienummering is gecodeerd. Door `/content/../page.model.json` aan te vragen, kunt u controleren waar precies de velden van `ResourceResolver` worden weergegeven en kunt u dat gebruiken om de klasse Sling Model te identificeren die dit gedrag daadwerkelijk activeert.


>[!NOTE]
>
>AEM Core Components zijn gevalideerd om dit probleem niet te kunnen ondervangen.

## Aangevraagde actie {#requested-action}

De Adobe verzoekt al hun klanten om hun toepassingslogboeken en codebasis te controleren om te zien of worden zij beïnvloed door dit probleem, en de douanetoepassing waar nodig te veranderen, zodat dit WARN bericht niet meer verschijnt.

Aangenomen wordt dat deze vereiste wijzigingen in de meeste gevallen recht naar voren zijn, aangezien de `ResourceResolver` -objecten helemaal niet vereist zijn in de JSON-uitvoer, aangezien de informatie in deze objecten normaal gesproken niet vereist is voor frontendtoepassingen. Dat betekent, in de meeste gevallen zou het voldoende moeten zijn om het `ResourceResolver` voorwerp van worden overwogen door Jackson (zie de [ regels ](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)) uit te sluiten.

Als een verkoopmodel door dit probleem wordt beïnvloed maar niet wordt veranderd, zal het expliciete onbruikbaar maken van serizalization van het voorwerp `ResourceResolver` (zoals uitgevoerd door Adobe als tweede stap) een verandering in de output JSON afdwingen.
