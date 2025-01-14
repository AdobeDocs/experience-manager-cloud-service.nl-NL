---
title: De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan
description: De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Architect, Developer
source-git-commit: a64c17943332782814bdacd7484e056cd445d3a9
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Met de functie Sling Model Exporter kunt u Sling Model-objecten serialiseren in JSON-indeling. Deze functie wordt op grote schaal gebruikt omdat SPA (toepassingen van één pagina) gemakkelijk toegang hebben tot gegevens van AEM. Aan de implementatiezijde wordt de bibliotheek Jackson Databind gebruikt om deze objecten van een serienummer te voorzien.

De rangschikking is een recursieve verrichting. Vanaf een &quot;wortelvoorwerp,&quot;herhaalt het recursief door alle in aanmerking komende voorwerpen en rangschikt hen en hun kinderen. U kunt een beschrijving vinden van welke gebieden in het artikel [ worden geserialiseerd Jackson - besluit welke Gebieden in series vervaardigd/Deserialized krijgen.](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)

Deze benadering serialiseert alle soorten voorwerpen in JSON. Het kan natuurlijk ook een Sling `ResourceResolver` -object serialiseren, als dit onder de serialisatieregels valt. Dit is problematisch, omdat de `ResourceResolver` -service (en dus ook het serviceobject dat deze vertegenwoordigt) mogelijk gevoelige informatie bevat, die niet openbaar moet worden gemaakt. Bijvoorbeeld:

* De gebruikers-id
* De zoekpaden voor het omzetten van relatieve paden
* De `propertyMap`

Speciaal gevoelig is `propertyMap` (zie de API documentatie van [`getPropertyMap` ](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), aangezien het een interne gegevensstructuur is, die voor vele doeleinden kan worden gebruikt, bijvoorbeeld caching voorwerpen die de zelfde levenscyclus zoals `ResourceResolver` delen. Het serialiseren van deze gegevens kan implementatiedetails lekken en kan een effect op de beveiliging hebben, omdat gegevens worden weergegeven die niet leesbaar en toegankelijk moeten zijn voor een eindgebruiker. Daarom moet `ResourceResolvers` niet met serienummering in JSON worden gecodeerd.

Adobe is van plan de serialisatie van `ResourceResolvers` uit te schakelen in een tweestapige aanpak:

1. Vanaf AEM as a Cloud Service versie 14697, wanneer een `ResourceResolver` geserialiseerd is, AEM een waarschuwingsbericht wordt geregistreerd. Alle klanten worden aangemoedigd om hun toepassingslogboeken voor deze logboekverklaringen te controleren en hun codebase dienovereenkomstig aan te passen.
1. Op een later punt zal de Adobe de rangschikking van `ResourceResolver` s als JSON onbruikbaar maken.

## Implementatie {#implementation}

Het WARN-bericht wordt zowel in AEM as a Cloud Service als in lokale AEM SDK-instanties geregistreerd en ziet er als volgt uit:

```text
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Dit logbericht betekent dat tijdens het proces van het serialiseren van `/content/…/page` in JSON `ResourceResolver` al met serienummering is gecodeerd. Door `/content/../page.model.json` aan te vragen, kunt u controleren waar precies de velden van `ResourceResolver` worden weergegeven en kunt u dat gebruiken om de klasse Sling Model te identificeren die dit gedrag daadwerkelijk activeert.


>[!NOTE]
>
>[ AEM de Componenten van de Kern ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction) zijn bevestigd om niet door dit probleem worden beïnvloed.

## Aangevraagde actie {#requested-action}

De Adobe verzoekt alle klanten om hun toepassingslogboeken en codebasis te controleren om te zien of worden zij beïnvloed door dit probleem, en de douanetoepassing waar nodig te veranderen, zodat dit waarschuwingsbericht niet meer in logboeken verschijnt.

Er wordt aangenomen dat deze vereiste wijzigingen in de meeste gevallen rechtuit zijn. De `ResourceResolver` voorwerpen worden vereist in de output JSON helemaal niet, aangezien de informatie bevat daar normaal niet door frontend toepassingen wordt vereist, die in de meeste gevallen het zouden moeten voldoende zijn om het `ResourceResolver` voorwerp van worden uitgesloten die door Jackson (zie de [ regels worden overwogen.](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not))

Als een Sling Model door dit probleem wordt beïnvloed maar niet veranderd, zal het expliciete onbruikbaar maken van rangschikking van het voorwerp `ResourceResolver` (zoals uitgevoerd door Adobe als tweede stap) een verandering in de output afdwingen JSON.
