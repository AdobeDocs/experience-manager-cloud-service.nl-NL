---
title: De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan
description: De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# De serialisatie van ResourceResolvers via Sling Model Exporter niet toestaan {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Met de functie Sling Model Exporter kunt u Sling Model-objecten serialiseren in JSON-indeling. Deze eigenschap wordt wijd gebruikt aangezien het SPAs (enige paginatoepassingen) toelaat om tot gegevens van AEM gemakkelijk toegang te hebben. Aan de implementatiezijde wordt de bibliotheek Jackson Databind gebruikt om deze objecten van een serienummer te voorzien.

De rangschikking is een recursieve verrichting. Vanaf een &quot;wortelvoorwerp,&quot;herhaalt het recursief door alle in aanmerking komende voorwerpen en rangschikt hen en hun kinderen. U kunt een beschrijving vinden van welke gebieden in het artikel [&#x200B; worden in series vervaardigd Jackson - besluit welke Gebieden in series vervaardigd/Deserialized &#x200B;](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not) krijgen.

Deze benadering serialiseert alle soorten voorwerpen in JSON. Het kan natuurlijk ook een Sling `ResourceResolver` -object serialiseren, als dit onder de serialisatieregels valt. Dit is problematisch, omdat de `ResourceResolver` -service (en dus ook het serviceobject dat deze vertegenwoordigt) mogelijk gevoelige informatie bevat, die niet openbaar moet worden gemaakt. Bijvoorbeeld:

* De gebruikers-id
* De zoekpaden voor het omzetten van relatieve paden
* De `propertyMap`

Speciaal gevoelig is `propertyMap` (zie de API documentatie van [`getPropertyMap` &#x200B;](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), aangezien het een interne gegevensstructuur is, die voor vele doeleinden kan worden gebruikt, bijvoorbeeld caching voorwerpen die de zelfde levenscyclus zoals `ResourceResolver` delen. Het serialiseren van deze gegevens kan implementatiedetails lekken en kan een effect op de beveiliging hebben, omdat gegevens worden weergegeven die niet leesbaar en toegankelijk moeten zijn voor een eindgebruiker. Daarom moet `ResourceResolvers` niet met serienummering in JSON worden gecodeerd.

Adobe is van plan de serialisatie van `ResourceResolvers` uit te schakelen in twee stappen:

1. Vanaf AEM as a Cloud Service versie 14697 registreert AEM een waarschuwingsbericht wanneer een `ResourceResolver` -bestand met serienummering wordt gecodeerd. Alle klanten worden aangemoedigd om hun toepassingslogboeken voor deze logboekverklaringen te controleren en hun codebase dienovereenkomstig aan te passen.
1. Op een later punt zal Adobe de rangschikking van `ResourceResolver` s als JSON onbruikbaar maken.

## Implementatie {#implementation}

Het WARN-bericht wordt zowel in AEM as a Cloud Service als in lokale AEM SDK-instanties geregistreerd en ziet er als volgt uit:

```text
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Dit logbericht betekent dat tijdens het proces van het serialiseren van `/content/…/page` in JSON `ResourceResolver` al met serienummering is gecodeerd. Door `/content/../page.model.json` aan te vragen, kunt u controleren waar precies de velden van `ResourceResolver` worden weergegeven en kunt u dat gebruiken om de klasse Sling Model te identificeren die dit gedrag daadwerkelijk activeert.


>[!NOTE]
>
>{de Componenten van de Kern van 0} AEM [&#x200B; zijn bevestigd om niet door dit probleem worden beïnvloed.](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/introduction)

## Aangevraagde actie {#requested-action}

Adobe vraagt alle klanten om hun toepassingslogboeken en codebasis te controleren om te zien of zij door dit probleem worden beïnvloed, en de douanetoepassing waar nodig te veranderen, zodat dit waarschuwingsbericht niet meer in logboeken verschijnt.

Er wordt aangenomen dat deze vereiste wijzigingen in de meeste gevallen rechtuit zijn. De `ResourceResolver` voorwerpen worden vereist in de output JSON helemaal niet, aangezien de informatie bevat daar normaal niet door frontend toepassingen wordt vereist, die in de meeste gevallen het zou moeten voldoende zijn om het `ResourceResolver` voorwerp van worden uitgesloten dat (zie de [&#x200B; regels &#x200B;](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).)

Als dit probleem van toepassing is op een Sling-model, maar dit niet wordt gewijzigd, wordt door het expliciet uitschakelen van de serialisatie van het `ResourceResolver` -object (zoals uitgevoerd door Adobe als de tweede stap) een wijziging in de JSON-uitvoer afgedwongen.
