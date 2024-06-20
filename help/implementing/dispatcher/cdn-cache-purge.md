---
title: De CDN-cache leegmaken
description: Leer hoe te om caching voorwerpen uit het geheime voorgeheugen van de Adobe CDN te verwijderen door het zuiveren API Symbolisch te vormen dat dan in API vraag kan worden gebruikt.
feature: CDN Cache
exl-id: 4d091677-b817-4aeb-b131-7a5407ace3e0
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# De CDN-cache leegmaken {#cdn-purge-cache}

>[!NOTE]
>Deze functie is nog niet algemeen beschikbaar. Als u wilt deelnemen aan het programma voor vroegtijdige adoptie, kunt u een e-mail sturen `aemcs-cdn-config-adopter@adobe.com`.

Het zuiveren verwijdert een voorwerp uit het geheime voorgeheugen van de Adobe CDN, resulterend in toekomstige verzoeken die aan de oorsprong als geheim voorgeheugenmissen, eerder dan worden gediend van geheim voorgeheugen.
AEM as a Cloud Service staat u toe om een Schrapping API Token te vormen, die dan in API vraag kan worden gebruikt. Lees de [CDN-referenties en verificatieartikel configureren](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) om te leren hoe te om dit teken te vormen gebruikend de richtlijnen van de Authentificatie van de Pijl van de Configuratie van de Manager van de Wolk.

Er zijn drie ondersteunde variaties voor het wissen:

* [Eén URL leegmaken](#single-purge) - één bron tegelijk leegmaken.
* [Leegmaken met vervangende sleutel](#surrogate-key-purge) - meerdere bronnen tegelijk verwijderen.
* [Volledige zuivering](#full-purge) - alle bronnen zuiveren.

Alle variaties van de purge delen het volgende:

* De HTTP-methode moet worden ingesteld op `PURGE`.
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

Zoals in het bovenstaande voorbeeld wordt getoond, kunt u **optioneel** opgeven of de CDN een **hard** leegmaken (standaard) of een **zacht** leegmaken op de objecten in de cache.

De standaard harde purge maakt de inhoud onmiddellijk ontoegankelijk voor nieuwe verzoeken tot de inhoud van de oorsprong wordt teruggewonnen. Met de optie Zacht leegmaken wordt de inhoud als verouderd gemarkeerd, maar blijft deze aan de klanten toekomen, zodat ze niet hoeven te wachten totdat de inhoud uit de oorsprong wordt opgehaald.

## Verwijderen van vervangingstoets {#surrogate-key-purge}

Surrogaatsleutels zijn unieke id&#39;s die u gebruikt om een set inhoud te wissen. Ze worden toegepast op inhoud door een `Surrogate-Key` aan de reactie. In een purge API-aanroep kan naar een of meer vervangingstoetsen worden verwezen.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "Surrogate-Key: my-surrogate-key"
-H "X-AEM-Purge: soft" #optional
```

De `Surrogate-Key`s) worden gescheiden door spaties. Op dezelfde manier als het enige zuiveren URL, kunt u of hard of een zachte zuivering vormen.

## Volledige zuivering {#full-purge}

U kunt alle in de cache opgeslagen bronnen als volgt volledig leegmaken:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "X-AEM-Purge: all"
```

Houd er rekening mee dat de `X-AEM-Purge` header must include the &#39;all&#39; value.

## Interacties met de laag Apache/Dispatcher {#apache-layer}

Zoals beschreven in het [Artikel Inhoudslevering stroom](/help/implementing/dispatcher/overview.md), haalt CDN inhoud van de Apache/Dispatcher laag terug, als het geheime voorgeheugen is verlopen. Dit impliceert dat alvorens een middel bij CDN te zuiveren, u zou moeten ervoor zorgen dat een nieuwe versie van de inhoud ook bij de Dispatcher beschikbaar is. Zie voor meer informatie ook [Ongeldige validatie van cache-verzending](/help/implementing/dispatcher/caching.md#disp).
