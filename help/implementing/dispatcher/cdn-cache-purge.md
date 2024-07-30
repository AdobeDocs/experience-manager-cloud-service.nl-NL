---
title: De CDN-cache leegmaken
description: Leer hoe te om caching voorwerpen uit het geheime voorgeheugen van de Adobe CDN te verwijderen door het zuiveren API Symbolisch te vormen dat dan in API vraag kan worden gebruikt.
feature: CDN Cache
exl-id: 4d091677-b817-4aeb-b131-7a5407ace3e0
role: Admin
source-git-commit: 3b55f3094b7154b7723ef7ae2230d7ae01eb4abc
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# De CDN-cache leegmaken {#cdn-purge-cache}

Het zuiveren verwijdert een voorwerp uit het geheime voorgeheugen van de Adobe CDN, resulterend in toekomstige verzoeken die aan de oorsprong als geheim voorgeheugenmissen, eerder dan worden gediend van geheim voorgeheugen.
Met AEM as a Cloud Service kunt u een token voor de paars-API configureren. Deze token kan vervolgens worden gebruikt in opschoonAPI-aanroepen. Lees het [ Vormen CDN Credentials en artikel van de Authentificatie ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) om te leren hoe te om dit teken te vormen gebruikend de richtlijnen van de Authentificatie van de Pijpleiding van Cloud Manager Config.

Er zijn drie ondersteunde variaties voor het wissen:

* [ Enige zuivering URL ](#single-purge) - zuiveren één enkel middel tegelijkertijd.
* [ wis door vervangings sleutel ](#surrogate-key-purge) - wis veelvoudige middelen in één keer.
* [ Volledige zuivering ](#full-purge) - zuivering alle middelen.

Alle variaties van de purge delen het volgende:

* De HTTP-methode moet worden ingesteld op `PURGE` .
* De URL kan elk domein zijn dat is gekoppeld aan de AEM-service waarvoor het verwijderingsverzoek is bedoeld.
* De `X-AEM-Purge-Key` moet in een HTTP-header worden opgegeven.

>[!CAUTION]
>Het leegmaken van het CDN geheime voorgeheugen, vooral met de harde vlag, zal verkeer bij de oorsprong verhogen en tot een stroomonderbreking leiden wanneer niet behoorlijk uitgevoerd.

## Eén URL leegmaken {#single-purge}

U kunt één bron tegelijkertijd als volgt wissen:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com/resource-path" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H 'X-AEM-Purge: soft'
```

Zoals aangetoond in het voorbeeld hierboven, kunt u **** naar keuze specificeren als CDN a **hard** (gebrek) of a **zachte** zuivering op de caching voorwerpen zou moeten uitvoeren.

De standaard harde purge maakt de inhoud onmiddellijk ontoegankelijk voor nieuwe verzoeken tot de inhoud van de oorsprong wordt teruggewonnen. Met de optie Zacht leegmaken wordt de inhoud als verouderd gemarkeerd, maar blijft deze aan de klanten toekomen, zodat ze niet hoeven te wachten totdat de inhoud uit de oorsprong wordt opgehaald.

## Verwijderen van vervangingstoets {#surrogate-key-purge}

Surrogaatsleutels zijn unieke id&#39;s die u gebruikt om een set inhoud te wissen. Ze worden toegepast op de inhoud door een `Surrogate-Key` -koptekst toe te voegen aan de reactie. In een purge API-aanroep kan naar een of meer vervangingstoetsen worden verwezen.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "Surrogate-Key: my-surrogate-key"
-H "X-AEM-Purge: soft" #optional
```

De `Surrogate-Key`(s) worden gescheiden door spaties. Op dezelfde manier als het enige zuiveren URL, kunt u of hard of een zachte zuivering vormen.

## Volledige zuivering {#full-purge}

U kunt alle in de cache opgeslagen bronnen als volgt volledig leegmaken:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "X-AEM-Purge: all"
```

Houd er rekening mee dat de header `X-AEM-Purge` de waarde &#39;all&#39; moet bevatten.

## Interacties met de laag Apache/Dispatcher {#apache-layer}

Zoals die in het [ artikel van de Stroom van de Levering van de Inhoud ](/help/implementing/dispatcher/overview.md) wordt beschreven, terugwint CDN inhoud van de laag Apache/Dispatcher, als het geheime voorgeheugen is verlopen. Dit houdt in dat u, voordat u een bron op de CDN wist, ervoor moet zorgen dat er ook een nieuwe versie van de inhoud beschikbaar is op de Dispatcher. Voor verdere details zie ook [ de Invalidatie van het Geheime voorgeheugen van Dispatcher ](/help/implementing/dispatcher/caching.md#disp).
